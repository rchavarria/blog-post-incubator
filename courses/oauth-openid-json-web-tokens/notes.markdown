# [Introduction to OAuth2, OpenID Connect and JSON Web Tokens (JWT)]
##### by Dominick Baier

## Tabla de contenidos

1. Overview
2. The security stack for modern applications
3. JSON Web Tokens (JWT)
4. Introduction to OAuth2
5. OAuth2 Flows
6. OpenID Connect
7. OAuth2 Concerns
8. Resources

## Overview

## The security stack for modern applications

Seguridad en la empresa: Kerberos (autenticación y autorización), LDAP, Active Directory. Funciona muy bien, porque todo está contenido *dentro* de la empresa. El problema viene cuando sales de ella (B2B). 

Para conectar servicios/empresas a través de internet, existen otros protocolos: SOAP, Web Services, XML/SAML,... Por ahora, también todo bien, porque al menos los actores implicados en el B2B se conocían y confiaban el uno en el otro.

Luego vino *the mobile revolution*. Ellos pasan del enterprise. No SOAP, no SAML, no WS. *Solo* HTTP y JSON.

Exceptiones: aplicaciones empresariales para el móvil, serían aplicaciones usadas solamente dentro de la empresa. Sería similar al primer escenario (todo dentro de la empresa)

Pero, ¿qué pasa cuando el móvil sale de la empresa? ¿que pasa si accede desde una red de fuera de la empresa?

OAuth2: está bien para una autorización delegada. Delegada porque puede conectar distintos clientes con distintos servidores, y ellos no tienen porqué estar desarrollados por la misma empresa, quizá por una que ni siquiera confias. OAuth2 serviría como el punto de confianza.

OAuth2 sería algo así: tú le pides un token de autorización, y ese token se lo mandas al servicio/servidor al que te quieres conectar.

OpenID Connect: utilizado para autenticación. De forma que el cliente pide un token al servidor OpenID, y es el cliente el que valida el token (autenticación). No confundir OpenID con el uso de OAuth (autorización). Quizá, los dos se usan conjuntamente para proporcionar servicios de seguridad.

JSON Web Token es el formato utilizado en los tokens enviados en estos casos

## JSON Web Tokens (JWT)

Los tokens son estructuras (protegidas) de datos: aparte de los datos en sí, contiene información sobre el *issuer*, están firmados (*tamper proof* -no puedes modificar el contenido- y autenticidad), suelen tener una fecha de caducidad

Un cliente pide un token

Un *issuer* *¿crea?* un token

Un recurso (una API web, por ejemplo) consume un token: tiene una relación de confianza con el *issuer*

Historia: SAML 1.1/2.0, Simple Web Token, JSON Web Token (firmas y encriptación simétricas y asimétricas, distintos algoritmos). JWT es mucho más simple que SAML pero más avanzado y flexible que SWT.

**Estructura y formato**

Cabecera: metadata, algoritmos y claves usadas
*Claims*: issuer, audience, issued at, expiration, subject, y otros campos definidos por aplicación

<cabecera>.<claims>.<firma>

## Introduction to OAuth2

¿qué es? es un protocolo abierto para permitir autorizaciones seguras a través de la web. Controla el acceso a determinados recursos

Empezó en 2007. OAuth 2.0 salió en 2010.

En 2012, el principal autor y editor lo dejó y quiso que borraran su nombre de las especificaciones (demasiadas empresas querían participar y cada una proponía *su* forma de hacer las cosas)

Hay 32 revisiones del estándar, y no todo el mundo implementa la última revisión, por lo que es fácil encontrarse dos implementaciones que no son compatibles 100% porque implementan distintas revisiones

Uno de los propósitos de OAuth es el de crear distintas claves para proteer distintos recursos que son propiedad del *Resource Owner*. El dueño tiene una clave para acceder a todos los recursos (la clave de tu cuenta de twitter, p.e.). Pero hay sub-recursos y OAuth controlaría el acceso a ellos (lista de seguidos en twitter). Con esas claves no se puede acceder a todos los recursos, no son claves/llaves maestras.

**Actores**

1. Dueño del recurso
2. Servidor del recurso
3. Servidor de autorización
4. Cliente (hardware/software usado por una persona para acceder a un recurso)

El dueño posee un recurso en un servidor de recursos. Y éste confía en un servidor de autorización.

El dueño del recurso **usa** un cliente. El cliente se registra en el servidor de autorización y éste autoriza al cliente pasándole un token. Con ese token, el cliente accede al servidor del recurso.

**Flujos**

Hay interacción por parte del usuario:

- Authorization code flow: pide autorización, pide token, accede al recurso
- Implicit flow: pide autorización y token, accede al recurso

No ha interacción del usuario:

- Resource owner password credential flow: pide un token con las credenciales del dueño del recurso para accder a un recurso
- Client credential flow: pide un token con las credenciales del cliente para acceder a un recurso

## OAuth2 Flows

Este es el módulo que merece la pena

### Authorization code flow

El dueño del recurso usa una aplicación web (cliente) para acceder al recurso (que está en el servidor de recursos).

El dueño es redirigido a servidor de autorización (una petición GET HTTP) con ciertos parámetros que incluyen el id del cliente (nombre de la app web), una url donde la respuesta del servidor de autorización será *enviada* (callback URI o redirect URI le llaman) y el tipo de respuesta (como por ejemplo un código de autorización - response_type=authorization code)

Lo primero que va a hacer el servidor de autorización es identificar al usuario/dueño del recurso, o pedir un login/password si no lo tiene identficado ya.

El siguiente paso es la página de consentimiento, donde se informa al usuario de los elementos a los que va a tener acceso el cliente cuando se le de el token. El usuario puede permitir/denegar el acceso al recurso por parte del cliente (aplicación web)

Si todo va bien, el cliente recibe una petición, la de callback, con un código (que servirá para pedir el token) y algún parámetro más.

El cliente debe autenticarse ante el servidor de autorización, para ello le pasa el código recibido por el callback. Si es autenticado, el cliente obtendrá un token de acceso y otro token para refrescar el de acceso.

Finalmente, el cliente puede conectarse al servidor de recursos y pedir el recurso deseado.

Algo bueno que tiene es que el token no llega nunca al navegador que usa el dueño del recurso, si no que se queda en la aplicación cliente, no en la aplicación que usa el usuario para acceder a la aplicación cliente.

### Implicit flow

Usado en clientes locales o nativos

Como dueño del recurso tú no quieres darle tu contraseña a la aplicación (un cliente de twitter de terceros).

Funciona muy parecido a *code flow*. Aquí, el cliente pide directamente el token al servidor de autorización (en lugar de pedir un código para luego pedir el token).

En esta ocasión no tenemos un token de refresco, simplemente el token de acceso.

El token se expone al navegador, a la aplicación que usa el dueño del recurso. La aplicación cliene no se autentica frente al servidor de autorización.

El cliente no se tiene por qué autenticar, porque ya confiamos en él

### Resource owner password credential flow

Aquí confías tanto en la aplicación cliente que es la aplicación quien guarda tu contraseña, de forma que es capaz de autenticarse frente al servidor de autorización automáticamente, sin preguntar nada al dueño del recurso.

Este caso se puede implementar en entornos donde se confía en la aplicación cliente.

El servidor de autorización responde con una respuesta con un token de acceso y uno de refresco.

De todas formas, es mejor almacenar los tokens en lugar de las credenciales del dueño del recurso.

### Client credential flow

Es adecuado para comunicaciones máquina-a-máquina (machine-to-machine).

La aplicación cliente no puede actuar en nombre de un usuario.

## OpenID Connect

Es un protocolo/estándar/mecanismo que se construye por encima de OAuth2 y sirve para proporcionar autenticación. OAuth2 está muy bien para autorización, pero tiene sus fallos a la hora de autenticar.

OAuth2 sirve para autorización *delegada*. La autentciación es un prerequisito para ello (si no, cómo vas a autorizar si todavía no has autenticado a la persona). A veces, simplemente se necesita la autenticación (hacer login), y muchas aplicaciones abusan de OAuth2  simplemente para autenticar (p.e.: dáte de alta con tu cuenta de Facebook, simplemente para tener un usuario/contraseña)

### Problemas en OAuth2 con la autenticación

Digamos que se intenta acceder a un recurso. Con OAuth2 estamos suponiendo que si el cliente, hablando con el Servidor de Autorización, es capaz de conseguir un token para acceder a ese recurso, es porque el Dueño del Recurso ha sido autenticado. Estamos **suponiendo** que el acceso a un recurso sólo lo puede hacer el Dueño del Recurso.

Problema: digamos que un usuario es engañado y está usando una aplicación maliciosa. E introduce sus credenciales. La applicación maliciosa consigue un token de acceso. El señor malo destrás de esa aplicación, usa ese token en una aplicación real. Así consigue usar esa aplicación real como el usuario al que le han *robado* el token de acceso. Este problema existe porque las aplicaciones no tienen una forma de relacionar el token de acceso con el usuario.

Solución: cada proveedor de servicios modifica un poquito el proceso de autenticación, y cada vez más se parece a OpenID Connect. Bueno, quizá sea que OpenID Connect toma lo mejor de cada una de estas modificaciones y las pone en común

### OpenID Connect

OAuth2 por sí solo no es lo suficientemente bueno para autenticación.

OpenID Connect se construye encima de OAuth2, usando los flujos Código de Autorización o el Implícito. Añade algunos conceptos nuevos: ID Token, UserInfo endpoint (punto de acceso para obtener información de usuario, de forma que sea común a todos los proveedores). 

### Flujo: Código OpenID

Actores:

- User Agent: normalmente el navegador
- Client: aplicación cliente
- Authorization endpoint: el mismo que en OAuth2, estaría en el Servidor de Autorización
- Token endpoint: el mismo que en OAuth2, también en el Servidor de Autorización
- UserInfo endpoint: introducido por OpenID
- Identity Provider: introducido por OpenID

1. Al Authorization endpoint el User Agent le pide el perfil del usuario (scope=openid profile)
2. Con esa información, el User Agent contacta con el Identity Provider
3. Éste te pregunta si das acceso a tu perfil. Si es que sí, el User Agent recibe el código a través de la URI de callback
4. Con ese código, la aplicación pide el token al Token endpoint
5. Token endpoint devuelve un token de acceso y uno de refresco. También, devuelve un **ID Token**. El cliente **debe** validar este ID Token. JWT contiene campos para la autenticación: issuer, subject, audience, expiration,...
6. Con esta validación, la aplicación cliente sabe quién es el usuario
7. Una vez autenticado el usuario, ya puede acceder al UserInfo endpoint

### Conclusión

El objetivo es que los clientes puedan usar cualquier proveedor para autenticar usuarios, en lugar de tener que mantener muchas formas de conectar con proveedores (una aplicación que permita conectar con twitter, fb, gg,...)

## OAuth2 criticism and concerns

### Eran Hammer

El autor de la especificación que en 2010/2012 dejó de formar parte del consorcio

- [Blog de Eran]
- [OAuth2: looking back and moving on]

### Specification Bloat

Todo empezó como un protocolo. Un protocolo tiene unas reglas estrictas a cumplir. Luego, se fueron añadiendo más y más empresas, y cada vez se parecía menos a un protocolo. Incluso llegaron a cambiar el nombre del estándar, de protocolo a framework. 

Al final, lo que ha pasado, es que hay muchos puntos que son opcionales, y distintas implementaciones no son 100% compatibles entre sí.

Así que no hay una forma de tener una implementación estándar. Cada uno tendrá su *versión* de OAuth2.

### Bearer tokens

El token no está ligado a la petición HTTP, de forma que cualquiera que tenga el token (lo pueden robar escuchando el canal) podrá hacer todo lo que el token permita. El token no contiene material criptográfico, algo así como *prueba de posesión* (proof-of-possession)

Bearer: aquel que posee el token, que no tiene porqué ser el usuario legítimo

### Security theater

Hacer como que hay seguridad, por ejemplo, después del 11/9, había militares apatrullando por Nueva York con armas que no tenían munición, pero la gente veía al ejército, y se quedaba más tranquilo.

Pues lo mismo pasa con todas las pantallas que aparecen al usar OAuth2: página de login, de consentimiento,...

Eso no evita que gente maliciosa te presente pantallas con la misma apariencia que Google o Facebook.

### Attack surface

Mucha información de la petición de autorización va en claro en la URL, como parámetros (id de cliente, scope, redirect URI,...). Todo eso puede ser espiado y manipulado por terceros.

SSL tampoco soluciona mucho el problema, porque no es un protocolo que esté correctamente implementado en muchos sitios. Bueno, en mi opinión, eso creo que está cambiando.

Una solución sería, cuando se registra la aplicación (antes de ser usada), requires ciertos campos, que tendrán que coincidir con los campos en la petición HTTP de autorización.

Facebook ha sido hackeado varias veces

### Conclusión

Las implementaciones que hay por ahí, dejan un poco que desear (incluso la de los grandes), así que imagínate la de los pequeños.

## Recursos

Hechar un vistazo al fichero `oauth2-json-web-tokens-openid-connect-introduction.zip` con todas las diapositivas del curso

- Curso: [Introduction to OAuth2, OpenID Connect and JSON Web Tokens (JWT)]

[Introduction to OAuth2, OpenID Connect and JSON Web Tokens (JWT)]: https://app.pluralsight.com/library/courses/oauth2-json-web-tokens-openid-connect-introduction/table-of-contents
[Blog de Eran]: http://hueniverse.com
[OAuth2: looking back and moving on]: https://vimeo.com/52882780

