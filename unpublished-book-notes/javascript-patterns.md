--
layout: post
title: "JavaScript patterns"
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

##### de Stoyan Stefanov

{% img left http://s1.hubimg.com/u/11789820_f260.jpg 260 392 Stop stealing dreams %}

## Por qué lo he leído

<!-- more -->

## Qué esperaba

## Qué encontre

## Conclusiones

## Qué he aprendido

## Frases que me gustaría recordar

## Recursos relacionados

[titulo sobre el enlace a las notas]: foo-bar-foo-bar

# Notas tomadas

## Essentials

### writing maintainable code

maintainable code means code that is readable, consistent, predictable, looks as if it was written by the same person and it's docuemtned

### minimizing globals

#### problem with globals

they're shared among all the code, there is always a chance of naming collisisions (same name, different purposes)
the most important pattern for having fewer globals is to always use `var` to declare variables, para que no se declaren por defecto como globales

#### single `var` pattern

- prevents logical errors when a variable is used before it is defined
- it minimizes globals

#### hoisting: a problem with scattered vars

- el problema de no declarar todas las variables al principio: they all act as if the variables were declared at the top of the functions (esto se conoce como *hoisting*), as long as a variable is in the same scope it is considered declared, even when it is used before the `var` declaration 

```
// antipattern
myname = "global"; // global variable
function func() {
    alert(myname); // "undefined"
    var myname = "local";
    alert(myname); // "local"
}
func();
```

#### `for` loops

- cachear `length` porque ciertos arrays (más bien, algunas implementaciones que se ven como arrays: DOM,...) calculan la longitud cada vez que se accede a la propiedad

#### `for-in` loops

- use the method `hasOwnProperty` filter out properties that come down the prototype chain

### (not) augmenting built-in prototypes

Añadir métodos a `Object`, `Array` o `Function` daña la mantenibilidad, porque hace el código menos predecible para otros desarrolladores

### Avoiding implied typecasting

#### avoiding `eval()`

- `eval()` is evil
- there is often a better way to achieve the goal without `eval()`, for example, using square bracket notation to access properties
- it is also impotant to remember that passing strings to `setInterval()`, `setTimeout()` and the `Function` constructor is similar to using `eval()`.
- if you absolutely must use `eval()``, you can consider using `new Function()` instead. The code evaluated will be running in a local funciton scope, lo que significa que no va a inerferir con el objeto global y tampoco va a tener acceso a vbles locales

### Number conversions with `parseInt()`

- Pasar siempre el parámetro `radix`: `parseInt('1234', 10)`
- otras formas de convertir a número: `+'08'`, `Number('08')`

### Coding conventions

- it is important to establish and follow coding conventions within the team
- jslint y otras herramientas ayudan muchos
- indentation: tabs, 2 spaces, 4 spaces,...
- curly braces: should always be used
- opening brace location: normalement da igual donde se pongan, pero en JavaScript puede dar problema debido a la inserción automática de `;`

```
// warning: unexpected return value
function func() {
    return
    {
        name: "Batman"
    };
}
```

- white space: tambies es cuestión de gustos, pero espaciar elementeso de un array, o antes de `{` y despues de `}` deja *respirar* al código

### Naming conventions

- significa escoger nombres para variables, métodos, clases,.. de una forma consistente
- tener una convención y seguirla de forma consistente es mucho más importante que la convención en sí misma

- Capitalizing constructors
- separating words: [camel case](https://en.wikipedia.org/wiki/CamelCase)

#### other naming patterns

- all caps for naming varialbes that should not change values
- use capital letters fro names of global variables
- underscore prefix to denote a private method ro property

### writing comments

- you have to comment your code
- you should not go overboard commenting the obvious

### writing api docs

- api documentation can be auto-generated from comments in the code

### Peer reviews

- tener herramientas que ayuden está bien para integrar las *code reviews* en el proceso de desarrollo
- pero no tener tiempo para investigar algunas de estas herramientas no es excusa para no hacer *code reviews*, simplemente pide a un compañero que revise tu c´dogio (en persona, por email,...)

### Minify... in production

- no intentes escribir código pre-minificado

### Run JSLint

- Hay otras herramientas a parte de [JSLint](http://jslint.com): [JSHint](http://jshint.com), [ESLint](http://eslint.org),...

## Literals and Constructurs

### Object literal

- the *object literal notation* is ideal for on-demand object creation

#### `Object()` constructor catch

- existe una funcionalidad en el constructor `Object()` que admite un parámetro, y dependiendo de ese parámetro, `Object` delega la cración del objeto a otro constructor:

```
// Warning: antipatterns ahead
// an empty object
var o = new Object();
console.log(o.constructor === Object); // true
// a number object
var o = new Object(1);
console.log(o.constructor === Number); // true
// normal object don't have toFixed() method
console.log(o.toFixed(2)); // "1.00"
// a string object
var o = new Object("I am a string");
console.log(o.constructor === String); // true
// normal objects don't have a substring()
// method but string objects do
console.log(typeof o.substring); // "function"
// a boolean object
var o = new Object(true);
console.log(o.constructor === Boolean); // true
```

### Custom constructor functions

```
var Person = function (name) {
    this.name = name;
    this.say = function () {
        return "I am " + this.name;
    };
};
var adam = new Person("Adam");
adam.say(); // "I am Adam"
```

- cada vez que se llama a `new Person("Adam")`, la función `say()` se crea en memoria

#### constructor's return values

- Constructors implicitly retun `this`, even when you don't have a `return` statement, but you can return whatever you want

### Array literal

```
// array of three elements
// warning: antipattern
var a = new Array("itsy", "bitsy", "spider");
// the exact same array
var a = ["itsy", "bitsy", "spider"];
```

#### Array constructor curiousness

- when you pass a single number to the Array(), it sets the length of the array. por eso es algo a evitar

### Regular expression literal

```
// regular expression literal
var re = /\\/gm;
// constructor
var re = new RegExp("\\\\", "gm");
```

- modificadores de la expresión regular

    1. `g`: global matching
    2. `m`: multiline
    3. `i`: case insensitive matching

### Primitive wrappers

- JavaScript have five primitive value types: number, string, boolean, null and undefined
- *primitive wrapper objects*: Number(), String() and Boolean()
- wrapper objects have some useful properties and methods. but methods work on primitives too, where primitives are converted to objects temporarily
- there is no reason to use more verbose wrapper constructors
- one reason to use wrapper objects is when you want to augment with properties

### Error objects

- `throw` works with any object
- pueden tener las propiedades `name` and `message` u otras que sean gestionadas por tus bloques `catch`

## Functions

### Terminology

```
// function expression, a.k.a. anonymous function
var add = function (a, b) {
    return a + b;
};

// named function expression
var add = function add(a, b) {
    return a + b;
};

// function declaration
function foo() {
    // function body goes here
}
```

### Declaration Vs Expression: names and hoisting

#### function hoisting

- all variables, no matter where in the funciton body they are declared, get hoisted to the top of the function
- in a function declaration, the definition of the function also gets hoisted, not only its declaration

```
function hoistMe() {
    console.log(typeof foo); // "function"
    console.log(typeof bar); // "undefined"

    foo(); // "local foo"
    bar(); // TypeError: bar is not a function

    // function declaration: variable 'foo' and its implementation both get hoisted
    function foo() { }
    // function expression: only variable 'bar' gets hoisted, not the implementation
    var bar = function () { };
}
```

### Returning functions

- function are objects, so they can be used as return values
- becasue `setup()` wraps the returned function, it creates a closure, and you can use this closere to store some private data

```
var setup = function () {
    var count = 0;
    return function () {
        return (count += 1);
    };
};
```

### Immediate functions

- is a syntax that enables you to execute a function as soon as it is defined
- it provides a scope sandbox for your initialization code
- commonly, the global object is passed as an argument

```
(function (global) {
 // some initialization with the global object
}(this));
```

- an immediate function can return any type of value, including another function, and its scope can be used to store some private data
- también puede usarse para asignar valores a propiedades de objetos que requeisran varias operaciones

```
var o = {
    message: (function () {
        var who = "me",
            what = "call";
        return what + " " + who;
    }())
};
alert(o.message); // call me
```

### Immediate object initialization

- this pattern uses an object with an `init()` method, which is executed immediately after the object is craeted. the ``init()` function takes care of all initialization tasks

```
({
    // initialize
    init: function () {
        // more init tasks...
    }
}).init();
```

### Init-time branching

- when you know that a certain condition will not change throughout the life of the program, it makes sense to test the condition only once. browser snifffin (or feature detection) is a typical example, figuring out the computed styles of a DOM elementnt or attaching event handlers are other

### Function properties - a memoization pattern

- one use case for suctom properties is to cache the results (the return value) so the next time the funciton is called, it does not ahve to redo petentially heavy computations. this is called **memoization**

```
var myFunc = function (param) {
    if (!myFunc.cache[param]) {
        // ... expensive operation ...
        myFunc.cache[param] = result;
    }
    return myFunc.cache[param];
};
// cache storage
myFunc.cache = {};
```

### Curry

#### Function application

- in functional programming, a function is not called or invoked, it is **applied**.
- `Function.prototype.apply()` has two arguments: object to bind to `this` and an array of arguments

#### Partial application (currying)

- currying is a transformation process, where we transform a function

```
// accepts partial list of arguments
function add(x, y) {
    if (typeof y === "undefined") { // partial
        return function (y) {
            return x + y;
        };
    }
    // full application
    return x + y;
}
```

## Object creation patterns

### Namespace pattern

- insttead of polluting the global scope, you can create one global object for your application or library
- before creating a property or creating a namespace, it is best to check first that it does not already exist: `typeof MYAPP === "undefined"`, `var MYAPP = MYAPP || {}`

#### Declaring dependencies

- it is a god idea to declare the modules your code relies on at the top of your function or module
- it is an exremely simple pattern, pero sobretodo sirve para hacer explícitas las dependencias

### Private properties and methods

#### Private members

- although the language does not have special syntax for private members, you can implement them using a closure
- *privileged method* is just a name given to the public methods that have access to the private members

```
function Gadget() {
    // private member
    var name = 'iPod';
    // public function
    this.getName = function () {
        return name;
    };
}
var toy = new Gadget();
console.log(toy.name); // undefined
```

#### Object literals privacy

- para tener atributos privados en objetos, you can use the closure created by and additional anonymous immediate function. this example is also the bare bones of what is known as *module pattern*
- el prototype de un objecto también puede ser creado de esta forma, ya que prototype es un objeto y este patrón crea objectos. En el ejemplo, en lugar de asignar el objeto a `myobj` lo asignaríamos a `Gadget.prototype`.

```
var myobj = (function () {
    // private members
    var name = "my, oh my";
    // implement the public part
    return {
        getName: function () {
            return name;
        }
    };
}());
```

### Module pattern

- provides the tools to create self-contained decoupled pieces of code, which can be treated as balck boxes of functionality 
- the first step is setting up a namespace
- define the module withaq n immediate function that will provide private scope. the immediate funciton returns an object (the actual module with its public interface)
- otras veces, en lugar de devolver un objeto, se puede devolver una función. De ete modo tenemos un patrón módulo que devuelve funciones constructoras
- you can pass arguments to the immediate function that wraps teh module to *import* globals into the module

## Sandbox pattern

- it addresses teh drawbacks of the namespacing pattern:

    1. reliance on a single global varialbe
    2. long, dotted names

### A global constructor

- in the sandbox pattern the single global is a constructor, you create object using that constructor, and you also pass a callback function, which becmoes the isolated sandboxed environment for your code.


```
Sandbox(['ajax', 'event'], function (box) {
    // console.log(box);
});
```

### Static members

#### Private static members

- you can have the same syntax as in a classy language by using a constructor function and adding properties to it


```
// constructor
var Gadget = function () {};
// a static method
Gadget.isShiny = function () {
    return "you bet";
};
// a normal method added to the prototype
Gadget.prototype.setPrice = function (price) {
    this.price = price;
};
// calling a static method
Gadget.isShiny(); // "you bet"
```

#### Private static members

- el truco aquí está en devolver una nueva función en nuestra implementación de una función constructora


```
// constructor
var Gadget = (function () {
    // static variable/property
    var counter = 0,
        NewGadget;
    // this will become the new constructor implementation
    NewGadget = function () {
        counter += 1;
    };
    // a privileged method
    NewGadget.prototype.getLastId = function () {
        return counter;
    };
    // overwrite the constructor
    return NewGadget;
}()); // execute immediately
```

## Code reuse patterns

### Classical Vs Modern inheritance patterns

#### Classical pattern #1 - the default pattern

- the mot commonly used method is to create an object using the Parent() constructor and assign this object to the Child()'s prototype

```
// the parent constructor
function Parent(name) {
    this.name = name || 'Adam';
}
// adding functionality to the prototype
Parent.prototype.say = function () {
    return this.name;
};
// empty child constructor
function Child(name) {}
// inheritance magic happens here
inherit(Child, Parent);

function inherit(C, P) {
    C.prototype = new P();
}
```

- using this pattern, you inherit both own properties (using `this` in the constructor parent) and prototype properties and methods
- el problema de esto es que la propiedad `name` es heredada, pero se encuentra en el prototipo de `Child`. Cuando creamos un nuevo objeto de `Child`, cuando se ejecuta el constructor de `Parent`, la propiedad `name` (que no se encuentra en `Child`) se crea en `Child`, por lo que la propiedad se *duplica* en ambos objectos (`Parent` y `Child`)

#### Classical pattern #2 - rent a constructor


```
function Child(a, c, b, d) {
    Parent.apply(this, arguments);
}
// or, you can also do
function Child() {
    Parent.call(this);
}
```

- this way you can only inherit properties added to `this` inside the parent constructor. you do not inherit members that were added to the prototype
- lo que hace este método, es llamar a la función constructora de `Parent` pasándole el `this` de `Child` como parámetro
- una ventaja que tiene este método, es que se puede *heredar* de varias clases

### Classical pattern #3 - rent and set prototype

- you first borrow the constructor and then also set the child's prottoype to point to a new instance of the constructor

```
function Child(a, c, b, d) {
    Parent.apply(this, arguments);
}
Child.prototype = new Parent();
```

- a drawback is that the parent constructor is called twice. at the end, the own properties get inherited twice

#### Classical pattern #4 - share the prototype

/!\ /!\ /!\  /!\  /!\  /!\  /!\  /!\  /!\  /!\  /!\  /!\  /!\  /!\  /!\  /!\  
- una regla que se repite en muchos patrones: **reusable members should go to the prototype and not `this`**
/!\ /!\ /!\  /!\  /!\  /!\  /!\  /!\  /!\  /!\  /!\  /!\  /!\  /!\  /!\  /!\  

- lo que se hace es establecer el prototipo de `Child` al prototipo de `Parent`

```
function inherit(C, P) {
    C.prototype = P.prototype;
}
```

#### Classical pattern #5 - a temporary constructor

- en lugar de llamar al constructor de `Parent`, creamos `F`, que es como `Parent` pero sin las propiedades en `this`
- the child only inherits propteries of the prototype
- incluso se puede almacenar una referencia al padre
- you must reset the pointer to the constructor, otherwise, all children objects will report that `Parent` was their constructor

```
function inherit(C, P) {
    var F = function () {};
    F.prototype = P.prototype;
    C.prototype = new F();
    C.uber = P.prototype; // store a reference to parent
    C.prototype.constructor = C;  // reset constructor reference
}
```

### Prototypal inheritance

- you would use an empty temporary constructor funciton `F()`. you then set the prototype of `F()` to be the parent object, finally, you return a new instance of the temporary constructor

```
function object(o) {
    function F() {}
    F.prototype = o;
    return new F();
}
```

- este tipo de herencia se ha implementado en ES5 mediante `Object.create()`

### Inheritance by copying properties

- simplemente, se recorren las propiedades del objeto padre is se crean en el hijo mediante un bucle `for-in`
- también se pueden hacer *copias profundas* para copiar las propiedades dentro de las propiedades si se tratan de objectos (array, object,...)

### Mixins

- instead of copying from one object, you can copy from any number of objects and mix them all into a new object

### Borrowing methods

- utiliza los métodos `call()` y `apply()` de las funciones
- la única diferencia es que uno toma los parámetros de uno en uno y el otro en array

```
// call() example
notmyobj.doStuff.call(myobj, param1, p2, p3);
// apply() example
notmyobj.doStuff.apply(myobj, [param1, p2, p3]);
```

### Function.prototype.bind()

- hay veces que se utilizan funciones, pero desacopladas de un objeto (bueno, acopladas al objeto global). esto suele pasar mucho cuando usamos callbacks


```
var one = {
    name: "object",
    say: function (greet) {
        return greet + ", " + this.name;
    }
};
// test
one.say('hi'); // "hi, object"
// assigning to a variable
// `this` will point to the global object
var say = one.say;
say('hoho'); // "hoho, undefined"
// passing as a callback
var yetanother = {
    name: "Yet another object",
    method: function (callback) {
        return callback('Hola');
    }
};
yetanother.method(one.say); // "Holla, undefined"
```

- ECMAScript 5 adds a method `bind()` to `Function.prototype`, making it easy to use as `apply()` and `call()`:

```
var newFunc = obj.someFunc.bind(myobj, 1, 2, 3);
newFunc();
```

- this binds toghether `someFunc()` and `myobj` and also prefill the first three arguments that `someFunc` expects. this is also an example of partial funcitona applicaton (see Chapter 4 of the bok)

## Desing patterns












