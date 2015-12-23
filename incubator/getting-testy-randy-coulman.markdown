# [Getting testy], by Randy Coulman

Dando una vuelta por Twitter descubrí una serie de artículos sobre testing titulados [Getting testy], de [Randy Coulman]. Parecían artículos interesantes, pero era mucha lectura para ser tratada como un blog. Así que decidí leerlo como si fuera un libro. Aunque un libro cortito.

Es una serie de artículos muy recomendable sobre TDD y cómo escribir buen software. Trata muchísimos temas relacionados con escribir tests para nuestro código. Conceptos sencillos y conceptos avanzados. Diferencias entre los dos estilos principales de hacer TDD. Qué hacer y qué no hacer a la hora de escribir tests. Y un sinfín de cosas más. Todas interesantísimas.

<!-- more -->

## Frases a destacar

- A la hora de tomar decisiones entre dos extremos, el autor se fija en los más y en los menos de cada extremo y trata de sintetizar las mejores partes de cada uno en algo sobre lo que pueda trabajar
- Los problemas a la hora de testear son una buena indicación de los problemas que encontrará el código cliente de esos mismos APIs

## Notas tomadas

**Historia y mecanismos**

*Dobles de tests* es una analogía de la idea de la situación en la que en una película de acción, un doble suplanta al actor profesional en una escena peligrosa

**Filosofía**

A la hora de tomar decisiones entre dos extremos, el autor se fija en los más y en los menos de cada extremo y trata de sintetizar las mejores partes de cada uno en algo sobre lo que pueda trabajar.

Dos escuelas fundamentales de hacer TDD:

1. Statist, Detroit: se enfocan en los objetos de tu sistema, lo que lleva a escribir tests basados en estado.
2. Mockist, Londres: se enfocan en los mensajes enviados en el sistema, lo que lleva a escribir tests basados en mocks (o dobles de tests).

Nota: existe un vídeo, de [Justin Searls], donde compara detalladamente estas dos escuelas: [Comparación escuelas TDD]

Un proceso ingenioso para añadir tests a código que existe actualmente:

1. Comenta el codigo que quieres probar
2. Escribe un test que falle
3. descomenta el mínimo código que haga que ese test pase
4. Refactorizar y repetir

No tengas miedo a borrar tests. Es más, hay ocasiones en las que querrás escribir tests para después borrarlos. En ocasiones, cuando estás escribiendo un algoritmo complejo, querrás escribir tests para las partes que más tarde serán privadas, necesitas probar esos pasos intermedios que te lleven a la solución. Más tarde, cuando hagas esas partes privadas, podrás borrar los tests *temporales*.

**Funciones**

Deja que los tests guien tu diseño, especialmente la API pública de tus objetos. Los problemas a la hora de testear son una buena indicación de los problemas que encontrará el código cliente de esos mismos APIs.

Haz que cada test pague por sí mismo. Los tests cuestan tiempo y dinero de ejecutar y mantener. No escribas tests que no añadan suficiente valor para sobrepasar esos costes. O escribelos hasta que consigas tener el código que buscas. Luego, bórralos.

**Abstraction**

when creating abstractions in any code, it's important to choose abastraction that are helpful, many tiemes we choose, the wrong ones and it makes our code more confusing to those coming after us. Esto me recuerda a una charla de Sandi Metz, en la que recomendaba algo de duplicación en lugar de una mala abstracción o mala legibilidad ([All the little things])

**Layers**

acceptance tests determine if we are buildign teh right sysytem. the lower-level tests hep us determine whether we are building the system right.

**Acceptance**

in most systems, the tests at the outer layer are the slowest of any tests we have in our system , so we want relatively fewer of them (cuantes menos tests de integración, mejor)

when we use a tool like cucumer or fitnesse, we should be able to port our appli ation to acompletely different programming language and kep the same specs. es decir, los tests de aceptación deben tener su propio lenguaje, el del negocio, el del dominio del cliente que va a usar el software

when you are writing tests for the outermost layer of your system, continually ask yourself "would these specs survive if i significantly changed the underlying implementeation of the system?"

**Learning**

**Outside-in**

if i feel like I need tot test internal details, there's probably an object that is trying to get out

I try not to constrain my thinking to the objects I already have. I'm not scared to introduce new objects if it improves my desing. Tú tampoco deberías tenerlo

**APIs part I**

in order to isolate us from external third party systems, we will hide the external service behind an inerface that we define and control

no se recomiendan tests que prueben métodos espec´ficos: test the responsibilities, not the methods. implementation details should be out of the specs.

**APIs part II**

**Steps**

it is generally best to do all input sanitizing and normalizing at the system boundaries. "Guard the borders, not the hinterlands"

**Why?**

for every assertion you want to write, ask why you care about that assertion. does that reason have to do with implementation details, or abouth the essential responsiblidiites of teh code you're testing? if the former, take a step back and re-evaluate. if the latter, then you're probably on the right track

by making assertions about the state of the world before performing teh action bein tested, we are communicatin something to the reader. i'd much rather communicate this fact in a separate test and not make the redundant assertions over and over again (que nos llevaría a tener duplicación en muchos tests)

the other case where I've seen some value in asserting setup is in legacy code.

don't write a test that forces you to write the code you want. write a test that forces your object to do what you want it to do (its responsabilities)

**Doubles**

Peers Vs Internal: is the other object at the same level of abstraction as the object I'm testing? Does it have a life of its own? If so, then it's likely a peer and I'm OK with using a test double. Otherwise, it might be an inernal implementation detail, where I think hard about whether to use a test double.

**Anti-patterns**

A good unit test shoudl be: [FIRST]. Fast, Isolated, Repeatable, Self-verifying, Timely.

**Bonus**

**Legacy**

al escribir tests para código legacy, we don't really care if he code is giving the **right answers**. we only care that we keep getting the **same** answers as we start making changes.

[Getting testy]: http://randycoulman.com/blog/2015/08/04/getting-testy-redux/
[All the little things](http://rchavarria.github.io/blog/2015/10/18/charla-tecnica-all-the-little-things/)
[FIRST]: http://agileinaflash.blogspot.de/2009/02/first.html
[Comparación escuelas TDD]: https://www.youtube.com/watch?v=aeX5OXO-w30
