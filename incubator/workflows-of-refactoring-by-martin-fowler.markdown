---
layout: post
title: "Charla técnica: Workflows of refactorings"
date: 
author: Rubén Chavarría
comments: true
categories: 
- technical talks
published: true
footer: false
sidebar: true
---

Esta semana el post trata sobre las notas que he tomado de una charla técnica
titulada [Workflows of refactorings]. El autor de la charla, hablando de
*refactoring*, no podría ser otro que [Martin Fowler]. En la charla, Martin
comienza hablando de distintos modos de trabajar, dependiendo de la situación,
por ejemplo, nos encontraremos añadiendo funcionalidad o limpiando el código.
Después, Martin describe distintos tipos de refactorizaciones, más allá del
típico paso en TDD o de la refactorización cambiando unos cuantos nombres a las
variables.

<!-- more -->

<iframe width="560"
        height="315"
        src="https://www.youtube.com/embed/vqEg37e4Mkw"
        frameborder="0"
        allowfullscreen></iframe>

## Notas tomadas

> La primera vez que la gente escucha hablar de *refactoring* es cuando oye hablar
del ciclo de TDD: red > green > refactor.

<!-- comment to separate ideas -->

> ¿Por qué separar los dos pasos que incluyen el código en TDD? ¿Uno para escribir
el código y otro para refactorizar? Puede que para los junior, que antes de nada
quieren tener algo funcionando. Kent Beck hablaba de dos modos de trabajar, dos
sombreros: añadiendo funcionalidad y modo mantenimiento (refactorizando). Se
puede cambiar entre ellos, pero no se puede andar mezclándolos.

<!-- comment to separate ideas -->

> Otros modos, otros sombreros: mejoras de rendimiento, donde el rendimiento
prima sobre la legibilidad; experimentos (donde el resultado va a ser descartado).

<!-- comment to separate ideas -->

> **TDD refactoring**: el refactoring que pasa cuando estás haciendo TDD, o tienes
una batería de tests en la que apoyarte

<!-- comment to separate ideas -->

> **Litter-pickup refactoring**: similar a la regla del Boy Scout. Se trata de que
tienes que trabajar con una base de código que no está escrita como a tí te gustaría
(aunque lo más probable es que hayas sido tú quien la haya escrito). Vas navegando
por el código, y de repente ves algún detalle que no te encaja. Paras todo, y lo
arreglas. En definitiva, como el Boy Scout, dejas el campo un poquito mejor de lo
que te lo encontraste. No quires pasar mucho tiempo limpiándolo, pero sí dejarlo
un poquito mejor.

<!-- comment to separate ideas -->

> Cuando encuentras alguna pieza de código en la que tienes que invertir cierto
tiempo entendiendo qué es lo que hace. Cuando terminas entendiéndolo, ¿qué
haces? ¿Lo dejas como está? ¿Y si la próxima vez vuelves a perder tanto tiempo?
Tendrás que refactorizarlo. **Comprehension refactoring**.

<!-- comment to separate ideas -->

> Hay situaciones en las que después de un tiempo, vuelves a ver código y piensas:
"hey! Ahora conozco una nueva y mejor forma de hacer esto". Esto tiene mucho que
ver con el *diseño evolutivo*. Por ejemplo, refactorizar un poquito antes de
añadir una nueva funcionalidad. Normalmente, el refactoring es beneficioso en el
largo y medio plazo. Este en concreto, es beneficioso para la tarea en la que
estás trabajando en este mismo momento.

<!-- comment to separate ideas -->

> **Planned refactoring**. Un buen equipo necesitaría poco de este tipo de
refactoring. Para el resto de mortales, un poco de refactorizaciones planificadas
no hace daño.

<!-- comment to separate ideas -->

> **Long-term refactoring**. Por ejemplo, cuando tienes un montón de módulos que
tienen dependencias caóticas. En lugar de parar el desarrollo y dedicar 2 o 3
semanas refactorizando todo esto, ¿qué tal si vas refactorizando poco a poco,
sin romper nada, gradualmente,... hasta que lo consigas? Quizá no tengas del
todo claro cómo llegar al final, pero si vas poco a poco, lo más seguro es que
tarde o temprano encuentres el camino.

## Conclusión

Me parece una charla interesantísima, recomendada 100%. Y no sólo echarle un
vistazo por encima, sino profundizar en los conceptos que Martin Fowler expone.
La charla es la keynote de una conferencia sobre Programación Orientada a
Objectos bastante conocida.

No estoy seguro, pero tiene pinta de que todos estos conceptos y nombres que
Martin da a los distintos tipos de refactorizaciones los vamos a ir viendo y
desarrollando en años venideros.

Así que ya sabes, haz un hueco en la agenda, y ¡a visualizar la charla!

[Workflows of refactorings]: https://www.youtube.com/watch?v=vqEg37e4Mkw
[Martin Fowler]: http://www.martinfowler.com/
