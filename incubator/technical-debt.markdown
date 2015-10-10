
Cuando hay que implementar una funcionalidad nueva en una aplicación software existen básicamente dos maneras de hacerlo: la rápida (el *hack*, la *ñapa*) y la correcta. Esta última más costosa y generalmente más compleja de llevar a cabo.

La *deuda técnica* es una metáfora en el mundo del software que nos permite discutir sobre este problema. Mediante la cual, se establece que implementar rápidamente una funcionalidad es como pedir un préstamo, el cual genera unos intereses que habría que pagar en el futuro en forma de un trabajo extra para mejorar o arreglar los atajos tomados al no haber hecho la funcionalidad de una forma más correcta.

<!-- more -->

La metáfora fue propuesta por Ward Cunningham en un informe para la [OOPSLA 1992]. Se suele utilizar para explicar a la gente *no técnica* la necesidad de refactorizar. Ya ha llovido desde entonces, y se ha discutido mucho sobre el tema. Así que también hay gente que no está de acuerdo con la metáfora. Yo creo que como todas las metáforas, flaquea si uno empieza a profundizar en el tema. Martin Fowler responde a los contrarios a la metáfora documentando que hay más de una forma de deuda técnica en su famoso [cuadrante de la deuda técnica].

Mucho antes que Cunningham, Meir Manny Lehman, en el 1980 ya comentaba conceptos relacionados:

> Un programa en evolución está en contínuo cambio, por lo tanto, su complejidad (reflejada en una estructura que se deteriora) se incrementa a no ser que se haga un trabajo para mantenerla o reducirla

## Causas

La principal culpable en la generación de deuda técnica, y así coinciden muchos autores, es en la presión en plazos y planes de entrega que el departamento de desarrollo se *deja* imponer por parte de negocio (marketing, ventas,...). Estas presiones ocasionan que se publiquen versiones del software sin que se implementen correctamente las funcionalidades.

Casi todas las causas se pueden derivar de esta primera, por ejemplo: recortes en procesos de pruebas, incluso eliminación de pruebas automáticas, lo cual hace muy difícil y extremadamente caro la detección y corrección de errores. Los procesos de aseguramiento de la calidad también se ven recortados, así como la documentación.

Las prisas también ocasionan que se pospongan trabajos necesarios o que se retrasen refactorizaciones en el tiempo, ya que para adaptarse a los cambios, a veces hay que refactorizar. Cuanto más se retrasa esta refactorización, más cambios habrá que hacer y más caro será el cambio. Esto puede llevar a que ciertas partes del código sean confusas.

También existe quien le echa la culpa a la cultura de la empresa: procesos pobres, falta de entendimiento, falta de educación, de cuidado y de colaboración con otros departamentos. Mientras existen otras causas maś atribuibles a individuos: incompetencia y falta de profesionalidad.

Hablando de profesionalidad, hay una cita Robert C. Martin que me encanta:

> La única forma de ir rápido, es hacer las cosas bien

> The only way to go fast is to go well

## Consecuencias

- Un desarrollo previsiblemente corto puede llevar mucho más tiempo de lo previsto
- Muy relacionado con el anterior, es una de las causas más comunes de que los proyectos no se entreguen a tiempo
- El mayor coste de la deuda técnica es el hecho de que ralentiza el desarrollo de futuras funcionalidades
- Documentación desactualizada, escasa o inservible
- Errores no subsanados o desconocidos
- Problemas al incorporar nuevas funcionalidades
- Inestabilidad del producto desarrollado
- Compromete la viabilidad del proyecto a largo plazo

## Soluciones

- (reescribir con mis palabras) Las herramientas de análisis de código no son suficientes para la identificación de la deuda técnica. La mayoría de las veces, la deuda técnica no e relaciona con ccódigo y sus cualidades intrínsecas, sino a opciones estructurarales, arquitecturales o brechas tecnológicas
- La única forma de pagar la deuda contraída es completando el trabajo que no se hizo correctamente
- Refactorizar, para mejorar el trabajo que se dejó pendiente. El mejor momento para refactorizar es justo antes de comenzar una nueva funcionalidad, adaptando el código a los nuevos requerimientos
- Hacer la deuda visible. Mantener una lista explícita sobre tareas necesarias para reducir la deuda
- Hacer entender a marketing y otros departamentos de negocio que si no se planifica cierto tiempo para reducir la deuda técnica se corre el riesgo de que no sea posible entregar todas las funcionalidades que ellos quieren

## Referencias:

- [Wikipedia en español sobre la deuda técnica](https://es.wikipedia.org/wiki/Deuda_t%C3%A9cnica)
- [Javier Garzás sobre la deuda](http://www.javiergarzas.com/2012/11/deuda-tecnica-2.html)
- [OOPSLA 1992]
- [Wikipedia en inglés](https://en.wikipedia.org/wiki/Technical_debt)
- [Martin Fowler sobre la deuda](http://martinfowler.com/bliki/TechnicalDebt.html)
- [Deuda técnica en Cunningham & Cunningham wiki](http://www.c2.com/cgi/wiki?TechnicalDebt)
- [Cálculo de la deuda técnica basado en fórmulas](http://docs.sonarqube.org/display/SONARQUBE44/Technical+Debt+Calculation)
- [Technical Debt: From Metaphor to Theory and Practice](http://www.computer.org/csdl/mags/so/2012/06/mso2012060018.html)

[cuadrante de la deuda técnica]: http://martinfowler.com/bliki/TechnicalDebtQuadrant.html
[OOPSLA 1992]: http://c2.com/doc/oopsla92.html

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

