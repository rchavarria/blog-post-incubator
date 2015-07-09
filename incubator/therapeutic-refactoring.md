# Charla técnica: Therapeutical Refactoring, de Katrina Owen

Acabo de visualizar la charla [Therapeutical Refactoring], de [Katrina Owen],
creadora de [exercism.io], y me ha encantado.

Es una charla donde nos cuenta la historia de una refactorización. Me ha
gustado especialmente cómo cuenta la refactorización. Ocultando las partes
del código que no interesan en el paso actual y resaltando aquellas que
sí.

Me ha recordado mucho a cómo vemos los desarrolladores el código,
focalizándonos en pequeños detalles, entremezclados en líneas y líneas de
código.

<!-- more -->

<iframe width="560"
        height="315"
        src="https://www.youtube.com/embed/J4dlF0kcThQ"
        frameborder="0"
        allowfullscreen></iframe>

En el repositorio [therapeutic-refactoring] se pueden ver todos los pasos
que Katrina ha dado en la refactorización.

## Notas

Alrededor del minuto 19 nos habla del término *codejunk*. Codejunk trata
sobre ruido, ruido que nos molesta para entender el código, pequeños detalles
que hacen que gastemos más energía de la necesaria para entender qué hace
el código. Algunos no son errores en sí, pero son como pequeños picores
que no te dejan disfrutar.

Describe 10 (de menos a más molestos):

10. Comentarios penosos
9. Espacios en blanco al final de las líneas
8. Código comentado
7. Paréntesis innecesarios
6. Parámetros explícitos por defecto
5. `import`s o `require`s (dependiendo del lenguaje) innecesarios
4. `string`s hechas de `string`s
3. Demasiado trabajo `manual` (deja que el pc haga el trabajo, no lo hagas tú)
2. Tests duplicados, hay que poner el mismo mimo en el código de tests
que en el de producción
1. Una combinación de todos los anteriores

## Moral de la historia

Refactorizar te da como un cerebro externo (exobrain).
Cada uno de nosotros podemos retener una cantidad finita de detalles en la
memoria (me recuerda al post de J.B.Rainsberger
[Your tests are dragging you down]). Programar es sobretodo, mantener en
mente todos esos detalles. Nuestra memoria trabaja peor bajo condiciones
de miedo o estrés. Refactorizar pone a salvo muchos de estos detalles,
permitiéndonos trabajar más relajadamente y más confiados en que estamos
haciendo un buen trabajo.

[Therapeutical Refactoring]: https://www.youtube.com/watch?v=J4dlF0kcThQ
[Katrina Owen]: https://twitter.com/kytrinyx
[exercism.io]: http://exercism.io
[therapeutic-refactoring]: https://github.com/kytrinyx/therapeutic-refactoring
[Your tests are dragging you down]: http://blog.thecodewhisperer.com/2015/03/28/your-tests-are-dragging-you-down

