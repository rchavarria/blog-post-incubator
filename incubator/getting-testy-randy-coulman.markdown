# Getting testy, by Randy Coulman

Dando una vuelta por Twitter descubrí una serie de artículos sobre testing titulados [Getting testy], de [Randy Coulman]. Parecían artículos interesantes, pero era mucha lectura para ser tratada como un blog. Así que decidí leerlo como si fuera un libro. Aunque un libro cortito.

Es una serie de artículos muy recomendable sobre TDD y cómo escribir buen software. Trata muchísimos temas relacionados con escribir tests para nuestro código. Conceptos sencillos y conceptos avanzados. Diferencias entre los dos estilos principales de hacer TDD. Qué hacer y qué no hacer a la hora de escribir tests. Y un sinfín de cosas más. Todas interesantísimas.

<!-- more -->

## Frases a destacar

- A la hora de tomar decisiones entre dos extremos, el autor se fija en los más y en los menos de cada extremo y trata de sintetizar las mejores partes de cada uno en algo sobre lo que pueda trabajar
- Los problemas a la hora de testear son una buena indicación de los problemas que encontrará el código cliente de esos mismos APIs
- Los tests de aceptación nos dicen si vamos a **construir el sistema correcto**. Los tests de más bajo nivel nos dicen si vamos a **construir el sistema correctamente** (build the right thing, build the thing right)
- No se recomiendan tests que prueben métodos específicos: se deberían testear las responsabilidades, no los métodos
- Guard the borders, not the hinterlands
- No escribas el test que te fuerza a escribir el código que tu quieres. Escribe el test que fuerza a tu objeto a tener las responsabilidades que quieres que tenga

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

No tengas miedo a borrar tests. Es más, hay ocasiones en las que querrás escribir tests para después borrarlos. En ocasiones, cuando estás escribiendo un algoritmo complejo, querrás escribir tests para las partes que más tarde serán privadas. Necesitas probar esos pasos intermedios que te lleven a la solución. Más tarde, cuando hagas esas partes privadas, podrás borrar los tests *temporales*.

**Funciones**

Deja que los tests guíen tu diseño, especialmente la API pública de tus objetos. Los problemas a la hora de testear son una buena indicación de los problemas que encontrará el código cliente de esos mismos APIs.

Haz que cada test *se pague* a sí mismo. Los tests cuestan tiempo y dinero de ejecutar y mantener. No escribas tests que no añadan suficiente valor para sobrepasar esos costes. O escríbelos hasta que consigas tener el código que buscas. Luego, bórralos.

**Abstracciones**

Cuando crees abstracciones en tu código, es importante elegir aquellas que son de alguna utilidad. Muchas veces escogemos las abstracciones equivocadas y eso hace nuestro código más confuso para los que vendrán después de nosotros. Esto me recuerda a una charla de Sandi Metz, en la que recomendaba algo de duplicación en lugar de una mala abstracción o mala legibilidad ([All the little things])

**Capas**

Los tests de aceptación nos dicen si vamos a **construir el sistema correcto**. Los tests de más bajo nivel nos dicen si vamos a **construir el sistema correctamente** (build the right thing, build the thing right)

**Aceptación**

En la mayoría de los sistemas, los tests de la capa más externa son los tests más lentos que tenemos. Así pues, queremos cuantos menos de ellos mejor, que no es lo mismo que decir que no los queremos en absoluto.

Cuando usamos una herramienta como Cucumber of Fitnesse, deberíamos ser capaces de portar nuestra aplicación a un lenguaje de programación completemante diferente y seguir manteniendo estos tests. Es decir, los tests de aceptación deben tener su propio lenguaje, el del negocio, el del dominio del cliente que va a usar el software.

Cuando estés escribiendo tests para la capa más externa de tu sistema, pregúntate continuamente si esos tests sobrevivirian si cambias signficativamente la implementación del sistema que están probando.

**Outside-in**

Si sientes la necesidad de testear detalles internos de una clase, probablemente es que hay un objeto que está intentando *salir*.

Trata de no limitar tus pensamientos a los objetos que ya tienes. No tengas miedo de introducir nuevos objectos si eso mejora el diseño.

**APIs**

Para aislarnos de sistemas externos (normalmente escritos por terceros), debemos ocultar el servicio detrás de un interfaz que definamos y controlemos nosotros.

No se recomiendan tests que prueben métodos específicos: se deberían testear las responsabilidades, no los métodos. Los detalles de implementación deberían estar fuera de los tests.

**Pasos**

Generalmente, es mejor hacer todo el saneamiento, validaciones y normalizaciones en los bordes del sistema. Protege las fronteras, no el interior (Guard the borders, not the hinterlands).

**¿Por qué?**

Por cada verificación que quieras escribir, pregúntate el por qué de dicha verificación. ¿La razón tiene que ver con detalles de implementación o tiene que ver con responsabilidades esenciales del código que estás probando? Si es la primera, párate un poco y recapacita. Si es la segunda, probablemente vayas en la buena dirección.

Cuando realizamos verificaciones sobre el estado de la aplicaión antes de hacer nada en nuestros tests, estamos comunicando algo al lector del código. Es preferible hacer esa comunicación en un tests separado antes que hacer esas verificaciones una y otra vez, lo que nos llevaría a tener duplicación en muchos tests

Otro caso en el que puede haber valor al realizar *verificaciones de setup* (verificaciones antes de hacer el propio test) es en código legacy.

No escribas el test que te fuerza a escribir el código que tu quieres. Escribe el test que fuerza a tu objeto a tener las responsabilidades que quieres que tenga.

**Dobles de tests**

¿Cómo saber si un doble de test es un colaborador o un detalle interno? Podemos hacernos las siguientes preguntas: ¿está al mismo nivel de abstracción que el objeto que estoy probando? ¿tiene su propio ciclo de vida? Si es así, probablemente es un colaborador y estaría bien utilizar un doble de tests. En otro caso, podría ser un detalle interno de implementación, donde deberíamos plantearnos seriamente si usar el doble de test o no.

**Antipatrones**

Un buen test unitario debería responder a las siglas en inglés [F.I.R.S.T.]: Fast, Isolated, Repeatable, Self-verifying, Timely.

**Legacy**

Al escribir tests para código legacy, no nos debería importar si el código está dando la respuesa correcta. Solo nos interesa si el código está dando la **misma** respuesta que antes de realizar los cambios.

[Getting testy]: http://randycoulman.com/blog/2015/08/04/getting-testy-redux/
[Randy Coulman]: http://randycoulman.com/
[All the little things]: http://rchavarria.github.io/blog/2015/10/18/charla-tecnica-all-the-little-things/
[Justin Searls]: https://twitter.com/searls
[Comparación escuelas TDD]: https://www.youtube.com/watch?v=aeX5OXO-w30
[F.I.R.S.T.]: http://agileinaflash.blogspot.de/2009/02/first.html

