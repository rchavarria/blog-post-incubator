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



## Recursos

- [Introduction to OAuth2, OpenID Connect and JSON Web Tokens (JWT)]

[Introduction to OAuth2, OpenID Connect and JSON Web Tokens (JWT)]: https://app.pluralsight.com/library/courses/oauth2-json-web-tokens-openid-connect-introduction/table-of-contents

