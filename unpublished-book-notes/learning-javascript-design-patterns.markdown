--
layout: post
title: "Learning JavaScript design patterns"
date: 
author: Rubén Chavarría
comments: true
categories: 
- personal
- book reviews
published: true
footer: false
sidebar: true
---

##### de Addy Osmany

{% img right http://www.addyosmani.com/resources/essentialjsdesignpatterns/cover/cover.jpg %}

## Por qué lo he leído

Ya llevo un tiempo programando con JavaScript de forma profesional, y empiezo
a sentir que necesito ir un paso más allá con el lenguaje. No creo que conozca
todo lo que ofrece el lenguaje, todo lo contrario, a veces siento que me queda
mucho por aprender y que necesito profundizar en muchos y muchos temas. Con
este libro pretendía trasladar mis conocimientos sobre patrones de diseño con
Java a JavaScript.

<!-- more -->

## Qué esperaba

Esperaba grandes cosas de este libro. Ya tenía referencias anteriores del autor,
creo que es un profesional como la copa de un pino. Así que un libro escrito
por él, pues tenía buena pinta.

Supongo que esperar encontrar una estructura de libro muy parecido a otros:
clasificaciones, descripciones, catalogaciones,...

## Qué encontré

Encontré un libro con mucho código, cosa que no tiene que ser ni bueno, ni malo.
En el caso de este libro, es una ayuda muy buena. Las explicaciones de Addy son
clarísimas y hay multitud de ejemplos y casos reales.

## Conclusiones

Aunque es un libro que no miente, trata sobre patrones de diseño, el libro me
ha defraudado un poco. Esperaba más del autor. Quizá no he sabido aprovechar
el contenido del libro, pero me ha parecido superficial en algunos capítulos,
y en otros ha entrado a describir con mucho detalle librerías como jQuery o
plugins para él.

En realidad, el libro que andaba buscando era [JavaScript patterns], de
Stoyan Stefanov, pero me daba más confianza Addy porque era un autor que ya
conocía. Toca ponerle remedio y ya me he puesto con el libro de Stoyan.

Eso sí, tengo que reconocer que es el primer lugar donde he encontrado una buena
descripción de lo que son cada una de las arquitecturas MVx (MVC, MVP, MVVM,...)

## Qué he aprendido

- Se pueden añadir propiedades a objetos a través del método
`Object.defineProperties()`
- Los métodos de un objeto, no se deben declarar en la función constructor, sino
modificando el prototipo de la misma
- Se debe intentar conseguir un bajo acoplamiento, algunos patrones (Observer,
Mediator,...) ayudan a ello
- Mixins
- Patrón Flyweight, consiste en agrupar o manejar conjuntamente funcionalidades
que pueden compartir un subconjunto de sus datos
- Diferencias entre los distintos MVx

    - En MVC, las Vistas tienen acceso directo al Modelo
    - En MVP, los Presentadores escuchan eventos de la Vista y del Modelo y median en la acciones entre ellos
    - MVVM nos permite crear partes específicas de las Vistas de un Modelo en concreto

- Expresiones de Función Inmediatamente Invocadas (IIFE - Immediately-Invoked Function Expressions)

## Recursos relacionados

- [Learning JavaScript design patterns] book, by Addy Osmani
- [Sintaxis definitiva de módulos]
- [Notas tomadas]
- [JavaScript patterns]

[Learning JavaScript design patterns]: http://www.addyosmani.com/resources/essentialjsdesignpatterns/book
[Sintaxis definitiva de módulos]: http://www.2ality.com/2014/09/es6-modules-final.html
[Notas tomadas]: foo-bar-foo-bar
[JavaScript patterns]: stoyan stefanov

# Notas tomadas

# Learning JavaScript design patterns, by Addy Osmani

## ¿Qué es un patrón?

- Los patrones son como plantillas sobre cómo resolver problemas

## Escribiendo código con patrones de diseño

- Es muy dificil, por no decir imposible, saber si un determinado código implementa un patrón determinado. Te puede parecer simplemente que sigue buenas prácticas y que quizá sigue unas reglas que se solapan con algún patrón.

## Antipatrones

Ejemplos de antipatrones:

1. Definir un gran número de variables en el contexto global
2. Pasar cadenas en lugar de funciones a los métodos `setTimeout()` o `setInterval()`
3. Modificar el prototipo de `Object`
4. Usar JavaScript directamente en los formularios
5. Usar `document.write` en lugar de `document.createElement`

## Categorías de los patrones de diseño

- Creacionales: se enfocan en el manejo de mecanismos de creación de objectos. Ejemplos de estos patrones son: Constructor, Factory, Abstract, Prototype, Singleton, y Builder
- Estructurales: tratan sobre la composición de los objetos y de identificar relaciones entre diferentes objectos. En esta categoría estarían: Decorator, Facade, Flyweight, Adapter y Proxy
- De comportamiento: se enfocan en mejorar o facilitar la comunicación entre distinto objetos. Ejemplos de estos patrones: Iterator, Mediator, Observer o Visitor

## Creacional

- Trata sobre la idea de crear nuevas cosas, específicamente objectos. Podemos encontrar 3 formas comunes de crearlos en JavaScript:

``` javascript
// 1.
var newObject = {}; 
// 2.
var newObject = Object.create(null);
// 3.
var newObject = new Object();
```

- Y podemos encontrar otras tantas formas de asignar claves y valores a un objeto:

``` javascript
// 1. Dot syntax
newObject.someKey = 'Hello World' ; // Write properties
var key = newObject.someKey; // Access properties

// 2. Square bracket syntax
newObject[ 'someKey' ] = 'Hello World'; // Write properties
var key = newObject[ 'someKey' ]; // Access properties

// 3. Object.defineProperty
Object.defineProperty(newObject, "someKey", {
    value: "for more control of the property's behavior",
    writable: true,
    enumerable: true,
    configurable: true
});

// 4. Object.defineProperties
Object.defineProperties(newObject, {
    "someKey": {
        value: "Hello World", 
        writable: true
    }, 
    "anotherKey": {
        value: "Foo bar", 
        writable: false
    }
});
```

### Constructor

Son usados para crear tipos específicos de objetos.

**Constructor Básico**

- Se tiene una función constructora simplemente llamándola poniendo antes la palabra reservada `new`. La palabra reservada `this` referencia al nuevo objeto que está siendo creado
- Problemas: esto hace la herencia algo difícil, las funciones declaradas son redefinidas en cada nuevo objeto creado, mientras que éstas podrían ser compartidas entre todas las instancias

**Constructores con prototipos**

Este patrón resuelve el problema de redefinir funciones.

``` javascript
function Car(model, year, miles) {
    this.model = model;
    this.year = year;
    this.miles = miles;
}

Car.prototype.toString = function () {
    return this.model + " has done " + this.miles + " miles";
};
```

## El patrón Singleton

- Tradicionalmente este patrón restringe la instanciación de una clase a un solo objeto
- En JavaScript, la forma má simple la encontramos en un objeto literal
- Se pueden añadir miembros y métodos privados al objeto singleton encapsulándolos dentro de una *closure*
- Eso puede ser usado para controlar que solo existe una instancia del objeto que se quiere crear
- Este patrón es muy útil cuando se necesita exactamente un único objeto para coordinar distintos patrones en nuestro sistema

``` javascript
var Singleton = ( function () {
    var instantiated;

    function init() {
        // éste sería el objeto singleton
        return {
            publicMethod: function () {
                console. log('hello world' );
            },
            publicProperty: 'test'
        };
    }

    return {
        getInstance: function () {
            if (! instantiated) {
                instantiated = init();
            }
            return instantiated;
        }
    };
})();

// llamar a los métodos públicos del singleton sería tan fácil como:
Singleton.getInstance().publicMethod();
```

## El patrón Módulo

- Se usa para emular el concepto de clases más allá de la posibilidad de incluir métodos y variables públicas y privadas en un único objeto, aislando ciertas partes del ámbito global, reduciendo la posibilidad de conflictos en los nombres de las funciones y variables
- con este patrón, sólo se devuelve la API pública, manteniendo todo lo demás privado dentro del *closure*
- desventajas:

    - tampoco se pueden acceder a miembros y métodos privados que se añadan al objeto en algún momento posterior
    - no es posible parchear variables privadas, en su lugar, hay que sobreescribir todos los métodos públicos que interaccionan con aquellos elementos privados que no funcionan como deberían

``` javascript
var testModule = ( function () {
    var counter = 0;
    return {
        incrementCounter: function () {
            return counter++;
        }
    };
})();
// test
testModule.incrementCounter();
``` 

## El patrón observador

- Permite a un objeto (conocido como el *suscriptor*) *escuchar* a otro objeto (el *emisor*)
- Los suscriptores pueden registrarse (suscribirse) para recibir notificaciones. Los emisores lanzan (publican) notificaciones
- **La idea general es promover un bajo acoplamiento**
- Ventajas: 

    - Permite relaciones dinámicas
    - Proporciona un gran grado de flexibilidad
    - Desacoplando aplicaciones: por ejemplo, cuando el usuario pulsa un boton, en lugar de actualizar el UI directamente, el método que responde ante clicks del usuario puede publicar uno/varios eventos y el UI afectado escucharlos (puede haber un UI o varios escuchando)
    - Desacoplando peticiones AJAX: con peticiones ajax, lo mismo. Podemos tener un componente que hace la peticion AJAX y publica eventos antes y después de la petición (con los datos incluso). Varios componentes de la aplicación pueden reaccionar de forma distinta a esos eventos

## El patrón mediador

Es un patrón de diseño de comportamiento que nos permite exponer una interfaz unificada a través de la cual diferentes partes del sistema se pueden comunicar. Promueve el bajo acoplamiento de la siguiente forma: en lugar de que los módulos referencien explícitamente a los demás, lo hagan a través de este punto central. En esencia, es como un *subject* (una cadena de texto que se usa para identificar un canal de comunicación) dentro del patrón Observador.

Quizá la peor desventaja de usar este patrón es que introduce un único punto de fallo.

Mediador Vs Observador: el patrón Mediador centraliza en lugar de distribuir. Es el Mediador quien tiene la responsabilidad.

## El patrón prototipo

- Crea objetos basado en la plantilla de un objeto existente clonando sus propiedades y métodos
- `Object.create` crea un objeto con un prototipo especificado y que opcionalmente contiene propiedades especificadas (por ejemplo: `Object.create(prototype, optionalDescriptorObjects)`)

## El patrón comando

Este patrón me ha sorprendido bastante, no se parece en nada al patrón con el mismo nombre que conocía para Java y otros lenguajes orientados a objetos.

Proporciona medios para separar los resultados de la ejecución de un comando del resto de responsabilidades, delegando la responsabilidad del comando a diferentes objetos.

La implementación sería algo así: supongamos que tenemos un objeto con varios métodos, debemos implementar uno nuevo, al que llamaremos `execute`. Este método acepta como primer parámetro el nombre del método que queremos ejecutar y el resto de parámetros son los parámetros de dicho método. Esto ayuda a desacoplar los métodos ejecutados de sus clientes.

Un código cliente podría ser algo parecido a esto:

``` javascript
CarManager.execute('buyVehicle', 'Ford Escort', '4332234');
```

## El patrón fachada

Proporciona una interfaz de más alto nivel para acceder a un cuerpo de código más grande, escondiendo de esta forma la complejidad subyacente.

Esto nos da la posibilidad de interactuar indirectamente con subsystemas de una forma que suele ser menos propensa a errores que acceder al subsystema directamente, con los datos correctos y en el orden correcto.

## El patrón factoría

- Gestiona el problema de crear objectos sin la necesidad de especificar la clase exacta de objeto que va a ser creado

## El patrón mixin

- Los mixins son un mecanismos para permitir la herencia múltiple

## El patrón decorador

- Es un patrón estructural que promueve la reutilización de código y es una buena y flexible alternativa a la herencia

### Decoradores

- Son usados cuando es necesario delegar responsabilidades a un objeto donde no tiene sentido usar herencia (herencia clásica de clases)
- En lugar de usar herencia, donde estamos acostumbrados a extender objectos linealmente, aquí trabajamos con un objeto sencillo y progresivamente añadimos objetos decoradores que proporcionan capacidades adicionales (metáfora de la tienda de helados, o del código que calcula los impuestos de un producto)
- JavaScript incorpora este patŕon en el lenguaje, ya que permite añadir propiedades y métodos dinámicamente

# Patrón peso-mosca (Flyweight)

- Es considerado una buena clásica solución para código que es repetitivo, lento e ineficiente
- Básicamente, toma varios objetos similares y pone la información compartida entre ellos en un único objeto o estructura externo
- En este patrón, existe el concepto de dos estados: intrínseco y extrínseco. Los datos intrínsecos son requeridos por métodos internos. Los datos extrínsecos, por otro lado, pueden ser eliminados y almacenados externamente.
- Los objetos con los mismos datos intrínsecos pueden ser reemplazados por un único objeto compartido
- El patrón usa un *manager* para manejar los estados extrínsecos

## Flyweight y el DOM (manejo centralizado de eventos)

- Normalmente, lo que quizá necesites para crear un menú, una lista de componentes, es enlazar el evento del click a cada enlace in el contenedor padre. En lugar de enlazar el evento click a múltiples elementos, podemos enlazar uno que use este patrón en el nivel superior, el cual quedará escuchando todos los eventos que provengan de niveles inferiores.

# Patrones MV<algo>

## MVP (modelo - vista - presentador)

- Presentador: es un componente que contiene la lógica de negocio para la vista relativa a la interfaz de usuario
- La diferencia con MVC es que en MVP la vista es pasiva. En MVC, la vista escucha cambios en el modelo y tiene lógica de negocio. En MVP no hay enlazado de datos (data binding), hay que hacerlo manualmente

## MVVM

- Este patrón hace uso de enlazado de datos de forma declarativa para permitir la separación de trabajo en las Vistas con el resto de capas

### Modelo

- Los modelos contienen información, pero típicamente no contienen nada de comportamiento. No formatean la información. El formateo de datos se lleva a cabo en la vista
- Lógica que valide los datos se considera aceptable para estar incluída en el modelo

### View

- Se considera activa. Contiene enlazado de datos (data binding), eventos y comportamientos que requieren un entendimiento del Modelo y la VistaModelo

### VistaModelo

- Se puede considerar como un controlador especializado que actura como un conversor de datos. Convierte información del Modelo en información de la Vista, pasando comandos desde al Vista al Modelo
- Vista y VistaModelo se comunican utilizando enlazado de datos y eventos

## MVC vs. MVP vs. MVVM

- En MVC, las Vistas tienen acceso directo al Modelo
- En MVP, los Presentadores escuchan eventos de la Vista y del Modelo y median en la acciones entre ellos
- MVVM nos permite crear partes específicas de las Vistas de un Modelo en concreto
- No es necesario que VistaModelo referencie a una Vista. La abstracción de la Vista significa que hay menos lógica requerida por el código detrás de ella
- Uno de los inconvenientes de esto es que es necesario un cierto nivel de interpretación entre la Vista y el VistaModelo

# Patrones de espacio de nombres

## Espacios de nombres anidados y automatizados

- Para crear el siguiente namespace: `application.utilities.drawing.canvas.2d`

```
var application = {
    utilities: {
        drawing: {
            canvas: {
                2d: {
                    //...
                }
            }
        }
    }
};
```

- Es posible crear esto automáticamente, por ejemplo parseando cadenas como `"myApp.ns1.module"`

## Patrón de declaración de dependencias

- Trata de *cachear* un modulo, para no acceder a él navegando todos los namespaces. Se supone que gana en rendimiento, porque el motor de JavaScript no tiene que estar buscando propiedades en objetos contínuamente

``` javascript
// en lugar de:
myApp.utilities.math.fibonacci(25);

// mejor
var maths = myApp.utilities.math;
maths.fibonacci(25);
// seguir usando maths
```

## Fundamentos de espacios de nombres

Desde lo más sencillo hasta lo más complejo:

1. Variables globales únicas
2. Espacios de nombres mediante prefijos: para evitar que otros desarrolladores interfieran con nuestro trabajo, añadimos un prefijo

```
var myprefix_MyApplication = ...
```

3. Notación literal de objetos: existen varias formas de intentar evitar colisiones:

```
// estas opciones chequean si ya existe un modulo o variable
var myApplication = myApplication || {}; // la más usada
if(!myApplication) MyApplication = {};
var myApplication = myApplication = myApplication || {}; // mejor que la primera opcion
myApplication || (myApplication = {});  // se considera una buena práctica
var myApplication = myApplication === undefined ? {} : myApplication; // la preferida
```

4. Espacios de nombres anidados

```
var myApp = myApp || {};
myApp.routers = myApp.routers || {};
...
```

5. Expresiones de Función Inmediatamente Invocadas (IIFE - Immediately-Invoked Function Expressions)

La versión más simple

```
// anonymous
(function () { /*...*/ })();
// named
(function foobar() { /*..*/ }());
```

6. Injección de espacio de nombres

La injección de espacio de nombres es una variación en IIFE donde se inyectan los métodos y propiedades de un espacio de nombres específico desde una envoltura de la función usando `this` (y el método `apply`, presente en todos los objetos)

```
(function() {
//...
this.methodForUtils = function() {};
}).apply(myApp.utils);
```

# Patrones de diseño moderno de un JavaScript modular

## AMD (Asynchronous Module Definition)

El formato de módulos de AMD es una proposición de definición de módulos donde tanto los módulos como las dependencias pueden ser cargado asíncronamente.

Los dos conceptos que necesitamos tener en cuenta son la idea de un método `define`, que proporciona las definiciones de los módulos, y un método `require`, para el manejo de la carga de dependencias.

```
define(
    module_id,
    [dependencies],
    definition function
);
```

## CommonJS

Esta proposición de módulos especifica una API simple para declarar módulos en el lado servidor.

- Un módulo CommonJS es una pieza de código JavaScript reusable que exporta ciertos objectos que van a estar disponibles para el código que dependa del módulo
- Contiene básicamente dos partes principales: la variable global `exports` y un método `require` que los módulos pueden usar para importar lo que el resto de módulos exportan a través de `exports`

## ECMAScript 6

La siguiente versión de JavaScript vendrá con posibilidades de importar y exportar módulos. 

Lo expuesto en el libro parece algo desactualizado, posiblemente porque el estándard del lenguaje estaría en fase borrador cuando fue escrito. La propuesta del libro es el siguiente código, pero se puede consultar la [sintaxis definitiva de módulos] en el artículo de [Axel Rauschmayer].

```
module skills {
    export var specialty = 'foo bar';
    export var other = ...
}

module cakes {
    import * from skills;
    // ...
}
```

# Referencias

- [Learning JavaScript design patterns] book, by Addy Osmani
- [sintaxis definitiva de módulos]
- [Axel Rauschmayer]

[Learning JavaScript design patterns]: http://www.addyosmani.com/resources/essentialjsdesignpatterns/book
[sintaxis definitiva de módulos]: http://www.2ality.com/2014/09/es6-modules-final.html
[Axel Rauschmayer]: http://rauschma.de/

