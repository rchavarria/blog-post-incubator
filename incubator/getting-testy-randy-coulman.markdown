# [Getting testy], by Randy Coulman

## Introduction

## History and mechanics

Test doubles: an analog of the idea of a stunt double that stands in for an actor in a movie
(stunt: escena peligrosa)

## Philosophy

Donde habla de distintas elecciones que hay que tomar a la hora de escribir tests.

I look at the pluses and minuses of both sides and try to synthesize the best parts of each approach into something workable: tomarlo para justificar mi posición intermedia la mayoría de las veces

Dos escuelas: statist Vs mockist, detroit Vs london, basado en estado Vs basado en mocks. (Justin Searls habla sobre las dos escuelas (https://www.youtube.com/watch?v=aeX5OXO-w30)).

If you are focused on the objects in your system,  you will tend to write state-based tests. If you are focused on the messages in your system, you will tend to write mock-based tests

Duplicación de código frente a legibilidad

Un proceso ingenioso para añadir tests a código que existe actualmente:

1. comenta el codigo que quieres probar
2. escribe un test que falle
3. descomenta el mínimo código que haga que ese test pase
4. refactorizar y repetir

No tengas miedo a borrar tests. Es más, hay ocasiones en las que querrás escribir tests para después borrarlos. En ocasiones, cuando estás escribiendo un algoritmo complejo, querrás escribir tests para las partes que más tarde serán privadas, necesitas probar esos pasos intermedios que te lleven a la solución. Más tarde, cuando hagas esas partes privadas, podrás borrar los tests *temporales*

## Functions

Let the tests drive teh design of your code, especially the public api of your objects. testing pain is a good indication of pain that the clients will face

make each test pay for itself. tests cost time and money to run and to maintain. don't write tests that don't add enough value to offset their cost. or write the util you have the code in place, then delete them

## Abstraction

when creating abstractions in any code, it's important to choose abastraction that are helpful, many tiemes we choose, the wrong ones and it makes our code more confusing to those coming after us. Esto me recuerda a una charla de Sandi Metz, en la que recomendaba algo de duplicación en lugar de una mala abstracción ([All the little things](http://rchavarria.github.io/blog/2015/10/18/charla-tecnica-all-the-little-things/))

## Layers

acceptance tests determine if we are buildign teh right sysytem. the lower-level tests hep us determine whether we are building the system right.

## Acceptance

in most systems, the tests at the outer layer are the slowest of any tests we have in our system , so we want relatively fewer of them (cuantes menos tests de integración, mejor)

when we use a tool like cucumer or fitnesse, we should be able to port our appli ation to acompletely different programming language and kep the same specs. es decir, los tests de aceptación deben tener su propio lenguaje, el del negocio, el del dominio del cliente que va a usar el software

when you are writing tests for the outermost layer of your system, continually ask yourself "would these specs survive if i significantly changed the underlying implementeation of the system?"

## Learning

## Outside-in

if i feel like I need tot test internal details, there's probably an object that is trying to get out

I try not to constrain my thinking to the objects I already have. I'm not scared to introduce new objects if it improves my desing. Tú tampoco deberías tenerlo

## APIs part I

in order to isolate us from external third party systems, we will hide the external service behind an inerface that we define and control

no se recomiendan tests que prueben métodos espec´ficos: test the responsibilities, not the methods. implementation details should be out of the specs.

## APIs part II

## Steps

it is generally best to do all input sanitizing and normalizing at the system boundaries. "Guard the borders, not the hinterlands"

## Why?

for every assertion you want to write, ask why you care about that assertion. does that reason have to do with implementation details, or abouth the essential responsiblidiites of teh code you're testing? if the former, take a step back and re-evaluate. if the latter, then you're probably on the right track

by making assertions about the state of the world before performing teh action bein tested, we are communicatin something to the reader. i'd much rather communicate this fact in a separate test and not make the redundant assertions over and over again (que nos llevaría a tener duplicación en muchos tests)

the other case where I've seen some value in asserting setup is in legacy code.

don't write a test that forces you to write the code you want. write a test that forces your object to do what you want it to do (its responsabilities)

## Doubles

Peers Vs Internal: is the other object at the same level of abstraction as the object I'm testing? Does it have a life of its own? If so, then it's likely a peer and I'm OK with using a test double. Otherwise, it might be an inernal implementation detail, where I think hard about whether to use a test double.

## Anti-patterns

A good unit test shoudl be: [FIRST]. Fast, Isolated, Repeatable, Self-verifying, Timely.

## Bonus

## Legacy

al escribir tests para código legacy, we don't really care if he code is giving the **right answers**. we only care that we keep getting the **same** answers as we start making changes.

[Getting testy]: http://randycoulman.com/blog/2015/08/04/getting-testy-redux/
[FIRST]: http://agileinaflash.blogspot.de/2009/02/first.html
