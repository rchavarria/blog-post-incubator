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

XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX

        ESTE COMANDO ME HA SORPRENDIDO BASTANTE

XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX

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

# Flyweight

- Is considered a usefull classicla solution for code that's repetivtive, slow and inefficient
- taking several similar objects and placing that shared information into a single external object or structure
- In the pattern, there's a concept of two states - intrinsic and extrinsic. Intrinsic data is required by internal methods. Extrinsic data can however be removed and stored externally
- Object with same intrinsic data can be replaced with a single hsared object. 
- it uses a amanger to handle the extrinsic states

## Flyweight and the DOM

### Centralized event handling

- normally what you might do to build menu, list components, is bind a click event to each link element in the parent container. instead of binding the click to multiple elementes, we can easily attach a flyweight to the top of our container which can listen for events coming fro below.

# MV<something> patterns

## MVP (model - view - presenter)

- Presenter: is a component which contains the usr-interface business logic for the view
- la diferencia con MVC es que en MVP la vista es pasiva. En MVC, la vista escucha cambios en el model y tiene lógica de negocio. En MVP no hay data binding, hay que hacerlo manualmente

## MVVM

- this pattern make use of declarative data bindidngs to allow a separation of work on Views from other layers

### Model

- models hold information, but typically don't handle behavior. they don't format information. Formattin of data is ahndled by the View
- validation is considered acceptable for the models

/!\ NOTA, CONCULSIÓN PARA EL LIBRO: EXPLICA MUY BIEN LAS DIFERENCIAS ENTRE MVC, MVP, MVVM,... /!\ 

### View

- Is considrered active
- it contains the data-bindings, evetns, and behaviors which require an understanding of the model and viewmodel

### ViewModel

- can be considered a specialized controller that acts as a data converter. it changes model infromation into view information, passing commands from the view to the model
- View and ViewModel communicate using data-bindings and events

## MVC vs. MVP vs. MVVM

- In MVC, Views have direct access to Models
- In MVP, Presenters listen to evetns from both the View AND Model and mediating the actions between them
- MVVM allows us to create View-specific subsets of a Model
- ViewModel is not requeired to referenca a View. the abstraction of the View means there is less logic requiered in the code behind it
- One of the downsides to this however is that a level of interpreations is needed between the ViewModel and the View

# Namespacing patterns

## Automated nested namespacing

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

- Es posible crear esto automáticamente, por ejemplo parseando cadenas como `"myApp.ns1.module"`.

## Dependency declaration pattern

- Trata de *cachear* un modulo, para no acceder a él navegando todos los namespaces. Se supone que gana en rendimiento

``` javascript
// en lugar de:
myApp.utilities.math.fibonacci(25);

// mejor
var maths = myApp.utilities.math;
maths.fibonacci(25);
// seguir usando maths
```

## Namespacing fundamentals

Desde lo más sencillo hasta lo más complejo:

1. Single global variables
2. Prefix namespacing: para evitar que otros desarrolladores interfieran con nuestro trabajo, añadimos un prefijo

```
var myprefix_MyApplication = ...
```

3. Object literal notation: existen varias formas de intentar evitar colisiones:

```
// estas opciones chequean si ya existe un modulo o variable
var myApplication = myApplication || {}; // la más usada
if(!myApplication) MyApplication = {};
var myApplication = myApplication = myApplication || {}; // mejor que la primera opcion
myApplication || (myApplication = {});  // se considera una buena práctica
var myApplication = myApplication === undefined ? {} : myApplication; // la preferida
```

4. Nested spacing

```
var myApp = myApp || {};
myApp.routers = myApp.routers || {};
...
```

5. Immediately-invoked Function Expressions (IIFE)s

Simplest version

```
// anonymous
(function() { /*...*/ })();
// named
(function foobar() { /*..*/ })());
```

6. Namespace injection

- Namespace injection is another variation on the IIFE where we inject the methods and properties for a specific namespace fro within a funciton wrapper using *this*.

```
(function() {
//...
this.methodForUtils = function() {};
}).apply(myApp.utils);
```

# Design Patterns in jQuery Core

Un capitulo dedicado a jQuery, vaya full de estambul

# Modern Modular JavaScript Design Patterns

## AMD

The AMD module format itself is aproposal fo rdefining modules where both the module and dependencies can be asynchronously loaded
- the two key concepts you need to be aware of there are the idea of a **define** method, facilitating module definitions, and a **require** mehtod, for handling dependency loading.

```
define(
    module_id,
    [dependencies],
    definition function
);
```

## CommonJS

This module proposal specifies a simple API for declaring modules in the server side.
- A CommonJS module is a reusable piece of JavaScript which exports specific objects made available to any dependent code
- they basically contains two primary parts: free varialbe named **exports** and a **require** function that modules can use to import the `exports` of other modules

## ES Harmony

The next version of JavaScript will come with **import** and **export** modules.

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

