Me gusta resolver puzzles, pero no puzzles de miles de piezas, si no más bien el
tipo de puzzle en el que hay unas piezas de madera encajadas y hay que desencajarlas,
o en el que hay una cuerdecita con una bola y tienes que sacar la bola y volverla
a meter. Ese tipo de puzzles.

Creo que de ahí me viene también el gusto de resolver pequeños problemas de
programación. Me gusta programar. Me gusta aprender. Y qué mejor para aprender
que practicar. En el mundo de la programación existe un concepto al que llamamos
[kata] (el concepto ha sido copiado de las artes marciales), el cual significa
la realización de pequeños ejercicios focalizados en un aspecto concreto. Así
que me gusta realizar katas de vez en cuando en algún lenguaje de programación
para practicar.

<!-- more -->

Hace un tiempo publiqué un tutorial sobre [cómo crear un módulo NodeJS], el cual
me servía de base para realizar algunas de estas katas. En este artículo me
gustaría llevarlo un poco más allá. A ese proyecto, a esa plantilla, voy a
añadirle lo siguiente:

- [Babel]: voy a añadir un paso en la construcción del proyecto y ejecución de los
tests, voy a transpilar código JavaScript ECMAScript 6 a ECMAScript 5. Esto me
permite practicar con la nueva versión de JavaScript.
- [ESLint]: estoy convencido de que este tipo de herramientas ayudan en el día a
día en el desarrollo con JavaScript. Me ayudan a detectar errores tontos a la
hora de escribir mi código.
- [TravisCI]: todos los tests serán ejecutados en un servidor de integración
contínua, para eliminar para siempre la excusa de *En mi ordenador funciona*

## Babel

- instalarlo
- configurarlo
- modificar gulp para lanzarlo

## ESLint

- instalarlo
- configurarlo
- que gulp lo ejecute

## TravisCI

- darte de alta en travis-ci.org
- añadir repo
- añadir .travis.yml para node

