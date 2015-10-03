
La **deuda técnica** es un concepto que fue usado por primera vez por [Ward Cunningham] en la [OOPSLA 1992](http://c2.com/doc/oopsla92.html). He estado buscando una definicón del término, pero parece que no hay una definición clara. Lo más parecido a una es:

>   DEFINICION ENCONTRADA EN ALGUN LADO, AUNQUE SEA EN EL ENLACE DEL 92, SI NO LO HAY, PONER CAUSAS MÁS COMUNES Y CONSECUENCIAS MÁS COMUNES Y DESPUÉS DE ESTA CABECERA DESARROLLAR MI PROPIA DEFINICIÓN

<!-- more -->

Aunque parezca que no hay una definición clara, en algo en lo que sí está de acuerdo la gente es en varias causas y consecuencias.

La principal causa en la que está de acuerdo la gente es en fechas de entrega excesivamente cortas y no realistas.

- También describir por encima el cuadrante de la deuda técnica de Martin Fowler

# Referencias:

- [Wikipedia en español sobre la deuda técnica](https://es.wikipedia.org/wiki/Deuda_t%C3%A9cnica)
- [Javier Garzás sobre la deuda](http://www.javiergarzas.com/2012/11/deuda-tecnica-2.html)
- [Wikipedia en inglés](https://en.wikipedia.org/wiki/Technical_debt)
- [Martin Fowler sobre la deuda](http://martinfowler.com/bliki/TechnicalDebt.html)
- [Martin Fowler y su cuadrante](http://martinfowler.com/bliki/TechnicalDebtQuadrant.html)
- [Deuda técnica en Cunningham & Cunningham wiki](http://www.c2.com/cgi/wiki?TechnicalDebt)

# Charlas y artículos interesantes sobre la deuda técnica

## [Technical debt 101](https://medium.com/@joaomilho/festina-lente-e29070811b84)

> every time you don’t write software based on the best possible practices and understanding of the business domain, you incur it in a technical debt. This debt keeps increasing over time, just like an interest. If you ignore it long enough, you can go technically bankrupt

> creator of the analogy, Ward Cunningham

> The main misconception of this analogy is that technical debt is what you get when you write bad code. This is completely wrong. Technical debt is a way to make design trade-off decisions in a clear, manageable way.  **la deuda técnica no es escribir mal código, es una decisión de diseño**

> Technical debt can be paid by refactoring. But when code is just bad, refactoring is way, way harder.

> So, the only realistic solution to legacy code is about radically improving the current code base in cycles, not a *big rewrite*. Big rewrites don't work as expected

Varias formas de decir lo mismo:

1. Festina Lente, Augustus, first emperor of Rome
2. Vísteme despacio que tengo prisa, Napoleon?
3. More haste, less speed (cuanta más prisa, menos velocidad)
4. The only way to go fast is to go well, Robert C. Martin
5. That is done quickly enough which is done well enough.

## [Good naming is a process, not a single step](http://arlobelshee.com/good-naming-is-a-process-not-a-single-step/)

Artículo que habla de la importancia del *naming* y de su relación con la deuda técnica. Quizá es interesante incluir este enlace en el post.

Describe 7 fases en el nombrado:

1. Missing
2. Nonsense
3. Honest
4. Honest and Complete
5. Does the Right Thing
6. Intent
7. Domain Abstraction

El proceso al que se refiere tendría los siguientes pasos:

1. Look at something.
2. Have an insight.
3. Write it down (name something).
4. Check it in.

## [To manage technical debt all we need is discipline](https://blog.svpino.com/2015/09/04/to-manage-technical-debt-all-we-need-is-discipline)

Artículo de **svipino** que dice que la lucha contra la deuda técnica es sobretodo **diciplina**. También comenta cómo luchan contra ella en su equipo, y parece una buena idea. Difícil de llevar a cabo, pero buena idea.

## [Cómo explicar la deuda técnica a un cliente](https://twitter.com/khellang/status/626716128379830273)


Una imagen muy clara de qué visión tienen los clientes de un producto software y qué visión tienen los desarrolladores del mismo. Puede servir para explicar a un cliente qué es la deuda técnia, más o menos.

## [Tweet de Gregory Brown](https://twitter.com/practicingruby/status/644259978337869824)

> We throw around the term "technical debt" but rarely do I hear "technical overinvestment". Both are real.

Otros usuarios lo relacionan con el concepto YAGNI (overinvestment === YAGNI).

