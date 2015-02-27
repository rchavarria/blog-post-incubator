# Learning JavaScript design patterns, by Addy Osmani

## What is a pattern?

- Patterns are as templates for how you solve problems

## Pattern-ity Testing, proto-patterns & the rule of three

## Structure of a design pattern

## Writing design patterns

- Es muy dificil, por no decir imposible, saber si un determinado código implementa un patrón determinado. Te puede parecer simplemente que sigue buenas prácticas y que quizá sigue unas reglas que se solapan con algún patrón.

## Anti-patterns

Examples of anti-patterns:

1. Defining a large number of variables in the global context
2. Passing strings rather than functions to either `setTimeout` or `setInterval`
3. Modifying the `Object` class prototype
4. Using JavaScript in an inline form
5. The use of `document.write` instead of `document.createElement`

## Categories of design pattersn

- Creational: they focus on handling object creation mechanisms. Constructor, Factory, Abstract, Prototype, Singleton, Builder.
- Structural: they are concerned with object composition and identify relatinoships between different objects. Decorator, Facade, Flyweight, Adapter, Proxy.
- Behavioral: they focus on improving or streamlining the communication between desparate objects. Iterator, Mediator, Observer, Visitor.

## Design pattern categorization

## JavaScript design patterns

### Creational

- It deals with the idea of creating new things, specifically new objects. 3 common ways to create them:

    // 1.
    var newObject = {}; 
    // 2.
    var newObject = Object.create(null);
    // 3.
    var newObject = new Object();

- Four ways to assign keys and values to an object:

    // 1. Dot syntax
    newObject. someKey = 'Hello World' ; // Write properties
    var key = newObject. someKey; // Access properties

    // 2. Square bracket syntax
    newObject[ 'someKey' ] = 'Hello World' ; // Write properties
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

### Constructor

Are used to create specific types of objects.

**Basic Constructor**

- You have a constructor function simply by prefixing a call to a constructor function with the keyword `new`. The keyword `this` references teh new object that's being created.
- Problems: it makes inheritance difficult, functions are redefined for each new object but they should ideally be shared between all of te instances

**Constructors with prototypes**

Este patrón resuelve el problema de redefinir funciones.

    function Car(model, year, miles) {
        this.model = model;
        this.year = year;
        this.miles = miles;
    }

    // Note here that we are using Object.prototype.newMethod rather than
    // Object.prototype so as to avoid redefining the prototype object
    Car.prototype.toString = function () {
        return this.model + " has done " + this.miles + " miles";
    };

## The singleton pattern

- Traditionally it restricts instantiation of a class to a single object
- In its simplest form it can be an object literal
- You could add your own private members and methods to the singleton by encapsulating variable and function declarations inseide a closure
- Eso puede ser usado para controlar que solo existe una instancia del objeto que se quiere crear

``` javascript
var Singleton = ( function () {
    var instantiated;

    function init() {
        // singleton here
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

// calling public methods is then as easy as:
Singleton. getInstance(). publicMethod();
```

- it's quite useful when exactly one object is needed to coordinate patterns across the system

## The module pattern

- it is used to further emulate the concept of classes in such a away that we're able to include both public/private methods and variables inse a single object, thus shielding particular parts from the global scope, reducing the likelihood of your function names conflicting
with this pattern only a public api is returnd, keeping everything else within the closure private

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
testModule. incrementCounter();
``` 

- Disadvantages: you alse cant access private members in methods that are added to the object at a later point. it's not simply not possible to patch privates. instead, one must override all public methods which interact with bth buggy privates

## The observer pattern

- allows and object (known as a subscriber) to watch another object (the publisher)
- subscribers are able to register (subscribe) to receive notifications. publishers broadcasts (publishes) a notification
- **the general idea here is the promotion of the loose coupling**
- advantages: dynamic relationships may exist. this provides a great deal of flexibility
- decoupling applications: por ejemplo, cuando el usuario clica un boton, en lugar de actualizar el UI directamente, el click-handler puede publicar uno/varios evetnos y el UI afecgtado escucharlos (puede haber un UI o varios escuchando)
- decoupling ajax requests: con peticiones ajax, lo mismo. podemos tener un componente que hace la peticion ajax y publica eventos antes y después de la request (con los datos incluso). varios componentes de la aplicación pueden reaccionar de forma distinta a esos eventos

## The mediator pattern

it's a behavioural design pattern that allows us to expose a unified interface through which the fdiffferent parts of a system may communicate. promotes loose coupling by ensuring that instead of modules referring to each other explicitly, their interaction is handled through this central point.
it's essentialy a shared subject in the observer pattern
- perhaps the bigggest downside of using the mediator pattern is that it can introduce a single point of failure

*mediator Vs observer* the mediator pattern centralizes rather than simply just distributing. Es el mediador quien tiene la responsabilidad.

## The prototype pattern

- creates objects based on a template of an existing object through cloning
- `Object.create` creates an object which has a specified prototype and which optionally contains specified properties (por ejemplo: `Object.create(prototype, optionalDescriptorObjects)`

## The command pattern

It provides you means to separate the responsibilities o fisuuing commands from anything, delegating this responsibility to different objects
Si tenemos un objeto con métodos, implementamos uno nuevo, 'execute', al que le pasamos el nombre del método y los argumentos -> decoupling. De forma que podríamos hacer algo similar a esto:

``` javascript
CarManager.execute('buyVehicle', 'Ford Escort', '4332234');
```

## The facade pattern

Provides a convenient higher-level interface to a larger body o fcode, hiding its tru underlying complexity
- this gives us the ability to indirectly interact with subsystmems in a way that can sometimes be less prone to error than accessing the subsystem directly

## The factory pattern

- Deals with the problem of creating objects whithout the need to specify the exact class of object being created

## The mixin pattern

- Los mixins son un mecanismos para permitir la herencia múltiple

## The decorator pattern

- A structural design pattern that promotes code reuse and is fexlible alternative to sub classing

### Decorators

- Are used when it's necessary to delegate responsibilities to an objet where it doesn't make sense to subclass it
- Rather than just using inheritance, where we're used to extending objects linearly, we work with a single base objcet and pregressively add decorator objects which provide the additional capapbiliteies. 
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

# Bonus: jQuery plugin design patterns



















