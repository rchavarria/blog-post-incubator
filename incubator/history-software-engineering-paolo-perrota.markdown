# Charla técnica: A short history of software engineering

Estas son las notas de una charla técnica titulada [A short history of software engineering][1], por Paolo Perrota. La charla, creo que la encontré por un tweet de [J.B.Rainsberger][2] recomendándola.

La charla trata sobre la historia de la Ingeniería del Software. Un poco lo de siempre, que la Ingeniería de Software quizá no debiera llamarse *Ingeniería*, similitudes y diferencias con otras ingenierías,... Pero Paolo hace una presentación muy amena y divertida, sin duda merece la pena ver la charla para saber un poco más sobre nuestra pasión: el desarrollo de software.

<!-- more -->

INSERTAR VÍDEO AQUÍ

## Notas

**1968** fue la primera vez que alguien (la OTAN) dijo que el software se entregaba tarde, fuera de presupuesto, con baja calidad y que no hacía exactamente lo que tenía que hacer (es decir, que contenía bugs)

La solucion propuesta fue una nueva disciplina, que llamaron **Ingeniería del Software**, para tratar de salir de esa crisis de proyectos fallidos. Despues de más de 20 años, decidieron que ya no era una crisis, que era el estado del arte, que una crisis no dura 20 años.

La Ingeniería del Software trata de solucionar 3 problemas:

1. Eliminar complejidad interna: si no hay código fuente, no hay complejidad interna, no hay problema. De ahí que hayan intentado crear *lenguajes* con los que no se necesitarían progrmadores. Empezaron diciéndolo en los años 50, con Cobol. Lo vendían como que era un lenguaje que hasta los managers podrían entender. El problema es que el desarrollo de software no es solamente **complejidad accidental** (no toda la complejidad es introducida por los programadores), sino también **complejidad esencial**, existe en el problema mismo.
2. Eliminar errores humanos: intentaron utilizar las matemáticas, para probar que el software era correcto. Y vinieron los *formal methods*, pero es muy caro. Aparentemente, un monton de matemáticas no pueden reemplazar los tests. Las matemáticas no pueden solucionar todos los problemas humanos.
3. Eliminar variabilidad en el proyecto: otras ingenierías lo hacen: Ingeniería Civil, Ingeniería mecánica,... En Ingeniería Civil dicen que hay dos tipos de proyectos: los repetibles y los únicos. Adivinas qué tipo de proyectos no van tan bien, adivinas qué tipo se pasan de presupuesto. Si vas a hacer algo único, va a llover dentro (anécdota de aquella casa única que hicieron, con tantas goteras).

En Ingeniería Civil hay dos fases: proyecto y construcción. Similarmente, en Ingeniería del Software podríamos traducirlas a: diseño e implementación. ¡Pues no! Las fases, en realidad, son: desarrollo y compilación.

Las economías de ambas ingenierías son muy distintas. En la charla hace referencia a otra charla, creo que es ésta: [][3], donde habla precisamente de éstas diferencias económicas. Mientras que en Ingeniería Civil el mayor coste es el de construcción, en Ingeniería del Software, el mayor coste es el desarrollo, el diseño.

Si en un proyecto software tienes 100 programadores, por analogías anticuadas, quizá creas que tienes 100 albañiles, pero en realidad es como si tuvieras 100 arquitectos para diseñar el mismo edificio. ¿A que eso ya parece algo más complejo de gestionar?

A continuación, pasa a hablar de metodologías (RUP, DSDM, Prince2, CMMI,...). Al final, no pudieron eliminar ninguna de las 3 cosas. Pero, y si en lugar de eliminarlas, ¿las aceptamos?

Las metodologías Agile se basan en 3 puntos:

1. Observa, mira alrededor
2. Haz una hipótesis
3. Haz un experimento

Estos 3 puntos no son más que el método científico. Por lo que el desarrollo de software es empírico, no es *Ingeniería*.

## Referencias

- [A short history of software engineering][1]
- [FALTA ENLACE AL VÍDEO AQUEL DE QUE EL SW SÍ QUE ERA ING, PERO ERA UNA INGENIERÁI DIFERENTE][3]

[1]: https://www.youtube.com/watch?v=9IPn5Gk_OiM
[2]: https://twitter.com/jbrains

