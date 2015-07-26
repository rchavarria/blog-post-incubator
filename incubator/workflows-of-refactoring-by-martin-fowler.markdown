# (Julio 2015) Charla técnica: [Workflows of refactorings], de Martin Fowler

- La primera vez que la gente escucha hablar de *refactoring* es cuando oye hablar
del ciclo de TDD: red > green > refactor.

- ¿Por qué separar los dos pasos que incluyen el código en TDD? ¿Uno para escribir
el código y otro para refactorizar? Puede que para los junior, que antes de nada
quieren tener algo funcionando. Kent Beck hablaba de dos modos de trabajar, dos
sombreros: añadiendo funcionalidad y modo mantenimiento (refactorizando). Se
puede cambiar entre ellos, pero no se puede andar mezclándolos.

- Otros modos, otros sombreros: mejoras de rendimiento, donde el rendimiento
prima sobre la legibilidad; experimentos (donde el resultado va a ser descartado).

- **TDD refactoring**: el refactoring que pasa cuando estás haciendo TDD, o tienes
una batería de tests en la que apoyarte

- **Litter-pickup refactoring**: similar a la regla del Boy Scout. Se trata de que
tienes que trabajar con una base de código que no está escrita como a tí te gustaría
(aunque lo más probable es que hayas sido tú quien la haya escrito). Vas navegando
por el código, y de repente ves algún detalle que no te encaja. Paras todo, y lo
arreglas. En definitiva, como el Boy Scout, dejas el campo un poquito mejor de lo
que te lo encontraste. No quires pasar mucho tiempo limpiándolo, pero sí dejarlo
un poquito mejor.

- Cuando encuentras alguna pieza de código en la que tienes que invertir cierto
tiempo entendiendo qué es lo que hace. Cuando terminas entendiéndolo, ¿qué
haces? ¿Lo dejas como está? ¿Y si la próxima vez vuelves a perder tanto tiempo?
Tendrás que refactorizarlo. **Comprehension refactoring**.

- Hay situaciones en las que después de un tiempo, vuelves a ver código y piensas:
"hey! Ahora conozco una nueva y mejor forma de hacer esto". Esto tiene mucho que
ver con el *diseño evolutivo*. Por ejemplo, refactorizar un poquito antes de
añadir una nueva funcionalidad. Normalmente, el refactoring es beneficioso en el
largo y medio plazo. Este en concreto, es beneficioso para la tarea en la que
estás trabajando en este mismo momento.

- **Planned refactoring**. Un buen equipo necesitaría poco de este tipo de
refactoring. Para el resto de mortales, un poco de refactorizaciones planificadas
no hace daño.

- **Long-term refactoring**. Por ejemplo, cuando tienes un montón de módulos que
tienen dependencias caóticas. En lugar de parar el desarrollo y dedicar 2 o 3
semanas refactorizando todo esto, ¿qué tal si vas refactorizando poco a poco,
sin romper nada, gradualmente,... hasta que lo consigas? Quizá no tengas del
todo claro cómo llegar al final, pero si vas poco a poco, lo más seguro es que
al final encuentres el camino.

[Workflows of refactorings]: https://www.youtube.com/watch?v=vqEg37e4Mkw

