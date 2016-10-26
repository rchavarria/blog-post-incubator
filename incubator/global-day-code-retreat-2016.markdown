# Global Day of Code Retreat 2016

Siento que el título esté inglés, no he encontrado una traducción que suene bien
en español: ¿*Día global del retiro del código*? Uff, no lo veo.

A lo que vamos, el pasado día (*day*) sábado 22 se celebró a nivel mundial (*global*)
un evento en el que programadores se reúnen (*retreat*) para... programar (*code*).

Sí, como lo oyes. Hay gente a la que le chirría que unas personas que se dedican
profesionalmente a programar se reúnan con compañeros de profesión para seguir
programando un día no laborable. Pero es que este evento no tiene nada que ver con
lo laboral, aunque sí con la profesión. Una definición tirando a formal sería:

> Un Coderetreat es un evento de un día, de intensa práctica, enfocado en los
> fundamentos del diseño y desarrollo de software. El formato ha demostrado ser
> un medio efectivo de mejora de habilidades dado que proporciona a los
> desarrolladores la oportunidad de tomar parte en prácticas focalizadas,
> dejando de lado las presiones de tener un que terminar un trabajo.

(traducción libre de la definición de [Codretreat])

{% img center img/2016/gdcr16.png %}

Crédito: Global Day of Code Retreat 2016, por [Eduardo Ferro]

<!-- more -->

Más concretamente, en el Global Day of Code Retreat, se trata de resolver el
problema del [Juego de la vida de Conway]. La definición habla de práctica
intensa y focalizada, de fundamentos de diseño y desarrollo. Para potenciar
esta práctica, el día está dividido en *iteraciones* de duración relativamente
corta. Y en cada iteración, el facilitador propone una serie de restricciones.
Así fué nuestro [día].

# Restricciones

Nuestro día consistió de seis iteraciones, y cada una de ellas contó con las
siguientes restricciones:

1. Ping-pong: en estos eventos siempre se programa en parejas y haciendo TDD.
   Programar en modo ping-pong significa que una persona escribe el primer test
y la otra escribe la mínima implementación para pasar el test y vuelve a
escribir el siguiente test. La primera persona hace pasar el test y vuelve a
escribir uno nuevo. Ping. Pong.

2. Nada de primitivas: esta comienza a ser divertida, está prohibido el uso de
   primitivas. ¿Que necesitas pasar un entero para indicar una posición en un
array? No, no. ¿Que quieres usar `true` como flag para controlar el flujo?
Nanai. Esta restricción te obliga a crear abstracciones, a nombrar todas esas
primitivas que pueden significar cualquier cosa. Esta restricción es una de mis
favoritas.

3. No se puede usar el ratón, y se limitan las *discusiones* a 3 minutos: menos
   mal que esta la realizé con herramientas que uso en mi día a día (porque
esto no te lo explica nadie, quizá te toque de pareja a alguien que no programa
en tu amado lenguaje, o ni siquiera en tu mismo entorno, divertido ¿verdad?) y
me gusta usar atajos de teclado. Si no, lo hubiera pasado mal. Como curiosidad,
existe el plugin [Key promoter] para los IDEs de JetBrains que te interrumpe
cada vez que usas el ratón.

4. Prohibidos las sentencias condicionales: esta restricción siempre me marca
   mucho. Está prohibido utilizar `if`s, `switch`es, operadores ternarios,...
«Muy fácil, utiliza polimorfismo» diría uno. «Eso lo solucionas con un mapa»,
pero no es tan fácil, lo siento. La primera vez me parecía imposible de
conseguir. Desde entonces, continuamente veo oportunidades para aplicar lo que
aprendo cada vez que juego con esta restricción.

5. No se puede hablar: una de las más complicadas, sobre todo si tienes de
   pareja a alguien a quien has conocido este día, lo cual suele ser bastante
habitual. El objetivo de esta restricción es hacer nuestro código lo más
expresivo posible, de forma que no tengamos que explicar nuestras intenciones.
También consigue que te pongas a escribir código desde el minuto cero y te
dejes de discusiones.

6. Intercambio de código: se trata de intercambiar, no sólo el código, si no el
   ordenador al completo con otra pareja. Por lo cual puedes encontrarte
cualquier cosa: un fichero en blanco, ningún test, la solución muy bien
encaminada, un código sobredimensionado,... Me pareció muy divertida, y una
forma muy dinámica de hacer la última iteración, donde las fuerzas ya flaquean.
Me pareció muy interesante, porque nada más cambiar de código (entorno,
ordenador, lenguaje,...) te encuentras como perdido. Pero luego empiezas a
darte cuenta de que los tests son muy parecidos a los que llevas en la cabeza.
Empiezas a hacer conexiones, a reconocer objetos, relaciones. Y ¡BUM! En cinco
minutos ya estás en marcha otra vez. Cuando cambié de código me encontré con
que debía programar en C++, que no veía desde la universidad (qué miedo,
incluir ficheros `.h` y manejar punteros), con un IDE que no conocía para nada,
y encima ¿escribir test automáticos?. Pues sí, lo conseguimos mis compañeros de
iteración y yo. Muy, muy revelador.

# Personas y agradecimientos

Y porque el software no es sólo unos y ceros, si no también personas... No sólo
es el qué, si no a quién me he *llevado* de allí:

- [Juan D. Vega], facilitador del evento. Muchas gracias por guiarnos, por las
  restricciones y por conectarnos con otros grupos que también celebraban el
coderetreat.
- [Luis Rovirosa], co-facilitador, co-organizador. Generando intensas y sanas
  discusiones con sus incisivas preguntas.
- [Eduardo Ferro], me alegró poder conocerle en persona, soy seguidor de su
  [blog] desde hace un tiempecillo.
- [Álvaro Fidalgo], no sabía nada de él, pero me pareció un gran profesional.
- [Helder de Oliveira], otra persona a la que quería conocer en persona, y no
  me equivocaba.
- [Ludo Bermejo], estuvo muy interesante la discusión que partío de él sobre
  optimizaciones en el código, y nos recordó que no en todos los contextos la
memoria y la CPU son *gratis*.
- [Ángel Sanz], no pude programar con él, pero hablamos un rato en las
  cervezas, y me cayó muy muy bien.
- [Javier García], con quien tampoco pude programar, pero charlamos durante las
  cervezas.

Y por supuesto, agradecer a [idealista.com] por el espacio y la comida.

# Recursos

- [Key promoter]. El enlace es un fork de un plugin que parece descontinuado:
  [Key promoter plugin].
- Github del [Software Craftmanship Madrid].

[Coderetreat]: http://coderetreat.org/about
[día]: https://github.com/SoftwareCraftsmanshipMadrid/global-day-of-coderetreat-2016/blob/master/presentation/theday.md
[Key promoter]: https://github.com/athiele/key-promoter-fork
[Key promoter plugin]: https://plugins.jetbrains.com/plugin/4455
[Software Craftmanship Madrid]: https://github.com/SoftwareCraftsmanshipMadrid/global-day-of-coderetreat-2016
[Juan D. Vega]: https://twitter.com/juandvegarguez
[Luis Rovirosa]: https://twitter.com/luisrovirosa
[Eduardo Ferro]: https://twitter.com/eferro
[Álvaro Fidalgo]: https://twitter.com/dmj200
[Helder de Oliveira]: https://twitter.com/helderdoliveira
[Ludo Bermejo]: https://twitter.com/ludobermejo
[Ángel Sanz]: https://twitter.com/gelsanz
[Javier García]: https://es.linkedin.com/in/garciajavier
[idealista.com]: http://idealista.com

