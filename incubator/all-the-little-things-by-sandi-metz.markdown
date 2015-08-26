# Notas tomadas sobre la charla técnica [All the little things](https://www.youtube.com/watch?v=8bZh5LMaSmE), de Andi Metz

Conocí esta charla a través del blog [Garajeando](http://garajeando.blogspot.com.es/2015/08/interesting-talk-all-little-things.html).

[Andi Metz]() es autora del libro [Practical OOP]() y ya he visto algunas de sus charlas, por lo que la calidad estaba asegurada. Andi es muy defensora de la OOP y es una profesional excelente.

La charla trata de una refactorización siguiendo la kata [The Gilded Rose](). La refactorización parte de un método gigante lleno de `if`s y lleva el código hacia clases pequeñas, métodos pequeños.

## Notas

> Es preferible algo de duplicación a una mala abstracción

La duplicación es fácil de detectar y de eliminar llegado el caso. Una mala abstracción al arrastraremos toda la vida del proyecto.

> Que tu objetivo sea llegar a Open/Closed

Uno de los principios de la OOP, es el Open/Closed Principle. Que para añadir nueva funcionalidad, no tengas que modificar código existente (abierto a expansión, cerrado a modificación). Lo ideal es que toda la aplicación siguiera este principio, no vas a llegar nunca, pero cuanto más lo sigas, más fácil será añadir nueva funcionalidad sin romper la existente.

> Crea cosas pequeñas

Clases pequeñas, métodos pequeños,...

> Refactoriza basándote en la complejidad, mediante la complejidad

Uno de los objetivos de las refactorizaciones es hacer el código más sencillo. Puedes utilizar métricas de complejidad para hacer un seguimiento de la refactorización. En pasos intermedios, ésta puede crecer, pero debes tener confianza en que la refactorización dará sus frutos y conseguirás un código más sencillo y limpio.

> Refactoriza hacia la simplicidad

> La herencia no siempre es mala

Se habla mucho de composición en lugar de herencia, pero para Sandi hay una ocasión, donde si se dan las siguientes circunstancias, la herencia es la mejor solución:

1. La jerarquía no es profunda ni ancha, es poco profunda y estrecha (no involucra muchas clases hijas)
2. Las subclases son hojas dentro de tu árbol de clases, las subclases están en los extremos de tu árbol de clases, no entre medias
3. Las subclases usan todo el código de la clase padre

