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



