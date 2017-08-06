---
layout: post
title: "99 bottles of OOP"
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

##### by [Sandi Metz](https://www.sandimetz.com/) and [Katrina Owen](http://www.kytrinyx.com/)

{% img left images/2017/99-bottles-of-oop.jpg %}

## Por qué lo he leído

No conozco personalmete a ninguna de las 2 autoras, pero soy un fan de Sandi y colaboro en un proyecto open source de Katrina, ¿cómo no iba a leer [99 bottles of OOP](https://www.sandimetz.com/99bottles)?

Ya había leído con anterioridad el libro de Sandi, [Programming OODR] y me gustó muchísimo, así que este libro prometía. También había visto alguna charla de Katrina sobre refactorizaciones, y me asombraron muchísimo, por su claridad y por su calidad.

<!-- more -->

## Qué esperaba

Considero que ambas autoras son un referente en el mundo del desarrollo de software, por lo que esperaba que el libro me enseñara nuevos temas o ideas sobre los que aprender y profundizar.

Según había escuchado en algunas entrevistas a las autoras, el libro basa sus *enseñanzas* en un caso real, solucionando un problema sencillo, ideal para realizar en katas, por lo que esperaba que todos los conceptos serían fáciles (o al menos más fáciles) de entender ya que estarían ilustrados con código real y ejecutable (mira, como si fueran tests).

## Qué encontre

## Conclusiones

Es impresionante cómo va describiendo la refactorización línea a línea. Elimina multitud de code smells, muchas veces de línea en línea, apoyándose en tests. Es ukna gozada ver cómo va quedando el código

[...] es un acto de bondad hacia el lector de tu código. El código que revela su intención está construido en base a la acumulación de actos así de intencionados. Programa intencionadamente (escribe un `case` en lugar de un `if` para indicar que las condiciones están relacionadas). **Es una pasada como el libro racionaliza estas decisiones y las explica**

Resulta interesante cómo nombra las cosas, conceptos, clases, variables,... Nombrado es una de las cosas más difíciles en Computer Science.

## Qué he aprendido

Una forma de ser mejor identificando olores en el código es practicar describiendo las características del código, tomando nota de las cosas que te llaman la atención: incluye cualquier patŕon que veas, y cosas que te gustan, odias o que simplemente no entiendes.

## Frases que me gustaría recordar

Escribir código es el proceso de encontrar el camino hasta el siguiente punto estable, no el punto final en sí mismo. No es el resultado final, si no el camino.

El código como el método `pluralize` (que devuelve `bottle` o `bottles` dependiendo de un número) se escribe cuando los programadores se llevan el principio DRY al extremo. Cuando te encuentres en una situación como esta, hazte las siguientes preguntas. Estas mismas preguntas también te ayudarán a saber si tu código es bueno o costoso.
1. El cambio voy a hacer, hace el código más difícil de entender? Cuando las abstraciones son las correctas, el código es fácil de entender.
2. Cuál es el coste futuro de no hacer nada ahora? Si no hacer nada no incrementa los costes, retrasa los cambios.
3. Cuando llegará ese momento, o cuándo tardaré en obtener más información? Tolera pacientemente la duplicación si haciéndolo the ayudará a descubrir la abstracción correcta.

Kent Beck describe difrentes formas de hacer que tus tests pasen. 3 de sus *Green Bar Patterns* son:
1. Fake It ("Til You Make It"): este estilo de TDD puede parecer extraño y tedioso, pero con práctica puede llegar a ser natural y rápido
2. Obvious Implementation: cuidado con ir directamenye a la solucion obvia te puede llevar por el camino equivocado. Desarrollar el hábito de escribir solamente el código suficiente para hacer que el test pase te fuerza a escribir mejores tests.
3. Triangulate: dirigir las abstracciones conservativamente con los tests. La triangulación requiere escribir varios test de una sola vez, lo que significa que tendrás varios test fallando simultáneamente. La idea es escribir el código necesario para hacer que todos esos tests pasen de forma simultánea.

Si el código no está abierto a modificaciones y no sabes por dónde empezar... empieza eliminando olores en el código. No sabes cómo hacer que el código esté abierto a modificaciones, así que empiezas a eliminar olores, con la esperanz de encontrarlo por el camino

Hacer que el código existente esté abierto a nuevos requisitos requiere normalmente de identificar y nombrar abstracciones. Las *Flocking Rules* se centran en hacer que las diferencias parezcan similitudes, y por eso son una herramienta muy útil para descubrir abstracciones. Las Flocking Rules seleccionan las cosas más parecidas, encuentran la menor diferencia entre ellas y hacen el cambio más simple para eliminar esa diferencia (evalúa el código, evalúa y ejecuta, evalúa y usa el código, evalúa, y finalmente borra el código no usado)

Cuando estés sufriendo por encontrar un buen nombre pero sólo tienes unas cuantas ocurrencias para guiarte, puede ser de ayuda imaginarte otras cosas que podrían encajar en la misma catergoría, y luego construir una tabla con los conceptos.

El Principio de Sustitución de Liskov también aplica a los tipos dinámicos (o *duck types*). Las violaciones de Liskov fuerzan a los que envían mensajes a tener conocimiento sobre varios tipos devueltos, y tratar con ellos de forma distinta o convertirlos en algo consistente.

No todos los condicionales son malos en la Programación Orientada a Objectos, hay un lugar para ellos. Algún objeto, en algún lugar, debe elegir qué objetos crear para las composiciones, y eso normalmente involucra condicionales.

Tener un **data clump** significa normalmente que estás necesitando un concepto. Cuando esta acumulación se envía como un conjunto de parámetros, el método que recibe el *clump* se puede ver inundado con facilidad con lógica para gestionarlo. Alguna de esta lógica inevitablemente acabará duplicándose en distintos lugares. Si dos cosas aparecen siempre juntas, es una señal de que esa pareja representa un concepto más profundo y que necesitamos darle un nombre.

Los programadores añaden líneas en blanco para acentuar cambios en la temática. La presencia de múltiples temas sugiere la existencia de múltiples responsabilidades, lo que hace el código más difícil de entender y leer, mientras que hace más fácil causar daños cuando haya que hacer algún cambio.

Los programadores habilidosos hacen lo correcto cuando intuyen la verdad. Cuando no la intuyen, se embarcan en experimentos cuidadosos, precisos, reproducibles y reversibles.

El truco para avanzar usando cambios de una sola línea es alterar temporalmente la factoría para tolerar varios tipos de entrada. A veces, a la hora de cambiar condicionnales con polimorfismo, hay momentos en los que algún código debe soportar varios tipos, hasta que todo el código está adaptado. Especialemente, si vamos haciendo cambios de una sóla línea

Corregir violaciones de Liskov es importante, porque en lenguajes orientados a objectos (sobretodo los tipados dinámicamente), se basan en la confianza explícita en los contratos implícitos entre los objetos. Se trabaja muy bien con objetos de confianza, porque siempre se comportan como se espera de ellos. Los objetos que a veces fallan en responder a un mensaje que les envías, o que ocasionalmente devuelven algo que no esperas, son un dolor, y requieren que los objetos que les llamen deban conocer demasiadas cosas.

Los atajos demasiado inteligentes son una falsa economía. Invierte en código que diga la verdad. Simplemente escríbelo. Di no a los atajos, di no a las chapuzas y ñapas.

Unos consejos que podrían resumir el libro completo serían: busca la simplicidad, no crees abstracciones demasiado pronto, enfócate en los olores del código, anda en pasos pequeños, sigue las Flocking rules, refactoriza siempre en verde, arregla los problemas sencillos primero, trabaja horizontalmente (cambios horizontales, nunca verticales), buscar puntos de estabilidad, sé disciplinado, no persigas las cosas brillantes/famosas/de moda

## Recursos relacionados

- [Notas sobre 99 bottles of OOP]
- Nuevo libro, [Refactoring to patterns], de Joshua Kerievsky, donde habla de *Gradual Cutover Refactoring*

[Notas sobre 99 bottles of OOP]: foo-bar-foo-bar
[Refactoring to patterns]: foo/bar/bar/foo.html


