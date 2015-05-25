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





