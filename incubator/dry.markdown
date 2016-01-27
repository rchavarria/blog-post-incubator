# D.R.Y., evita duplicidades, seco, zipi y zape, gemelos, copy&paste, prohibido, principios,...

{% right /images/2016/mitosis.png %}

En biología, el concepto de repetirse a uno mismo es fundamental. Ninguno de
nosotros existiríamos si los primeros organismos unicelulares no hubieran sido
capaces de desarrollar el mecanismo de mitosis, la capacidad de multiplicarse,
de crear réplicas de sí mismos. Para los niños, la repetición también es
importante. Aprenden por imitación, repitiendo lo que observan en el
comportamiento de los demás.

A la hora de desarrollar software, la repetición no está vista con tan buenos
ojos. Por ejemplo, se ha dado un nombre despectivo a los programas que crean
copias de sí mismos, como los *virus*. Por otro lado, la duplicidad de código
de una aplicación produce muchos quebraderos de cabeza a aquellos de nosotros
que nos dedicamos al software. Para recordárnoslo, contamos con el principio
*D.R.Y., don't repeat yourself*, o, no te repitas a tí mismo.

<!-- more -->

> Cada pieza de conocimiento debe tener una representación dentro de un sistema
  única, inequívoca y acreditada ~ Traducción libre de *C2 Wiki*

Normalmente este concepto se cumple cuando hay dos segmentos de código con el
mismo texto, pero no se limita a ello. Puede que existan dos clases que hace
exactamente lo mismo, pero los métodos o las variables tienen distinto nombre.
También puede haber duplicidades en ficheros de configuración, o en la
documentación. Por lo tanto, hay que tener en cuenta que **D.R.Y. no es
duplicidad de texto, si no de conceptos**.

Debemos prestar atención a duplicidades en los tests, por ejemplo a la hora de
realizar las verificaciones. En muchas herramientas de testing existen los
*custom matchers*, que nos ayudan precisamente a reducir estas duplicidades.

J.B.Rainsberger ha escrito mucho sobre el tema, muy relacionado con el libro
*[4 rules of simple design]*, quien al final las reduce a dos reglas básicas:
dar nombre a las abstracciones y eliminar duplicidades creando nuevas
abstracciones. Pero también existen otras técnicas para reducir conceptos
duplicados, como las refactorizaciones **extraer método** y **extraer clase**,
sin olvidar la más usada, la **herencia**, aunque no está muy bien considerada.

Menos duplicaciones puede significar mayores niveles de indirección, lo que
puede hacer que el código sea algo más difícil de leer y seguir la pista,
porque para no duplicar, los detalles están dispersos en distintos lugares. La
**metaprogramación** puede ser también una técnica para eliminar duplicados,
pero hace el código mucho más difícil de leer. Más incluso que la indirección.

En contraposición al principio D.R.Y., está el principio W.E.T. Pensabe que
significaba **W**rite **E**verything **T**wice (escríbelo todo dos veces), pero
también he visto que las siglas pueden significar: **W**e **E**dit
**T**erribly, o **W**e **E**njoy **T**yping (mucho más divertidos, ¿verdad?).

Por último, algo que me ha parecido fabulosa, una frase que describe la
programación orientada a objetos, donde recuerda los conceptos de encapsulación
(*shy*), no duplicados (*dry*) y paso de mensajes entre objetos (*tell, don't
ask*):

> Keep it shy, dry, and tell the other guy

## Recursos

- Charla [Mantaining balance while reducing duplication], de David Chelimsky
- Dave Thomas en CodeNewbie podcast: en la [parte 1] cuenta la historia de cómo
  nació el libro *The pragmatic programmer*, sobre cómo decidieron hacer todo
  ellos mismos y cómo de ahí nació su editorial. En la [parte 2] me ha llamado la
  atención su opinión sobre las Katas. Comenta que lo importante de la kata no es
  el ejercicio en sí, sino la repetición, hacer el ejercicio sin pensar en la
  solución. De esta forma hacemos que nuestro cerebro reconozca patrones y
  aprendamos sin darnos cuenta.
- [DontRepeatYourself] en la C2 Wiki
- [Los 4 elementos del diseño simple], de J.B.Rainsberger
- [Economía del software y dependencias], de Luis Artola y Guillermo Gutiérrez

[4 rules of simple design]: https://leanpub.com/4rulesofsimpledesign
[Mantaining balance while reducing duplication]: https://www.youtube.com/watch?v=Is8ThG6Fetg
[parte 1]: http://www.codenewbie.org/podcast/the-pragmatic-programmer-i
[parte 2]: http://www.codenewbie.org/podcast/the-pragmatic-programmer-part-ii
[DontRepeatYourself]: http://www.c2.com/cgi/wiki?DontRepeatYourself
[Los 4 elementos del diseño simple]: http://blog.thecodewhisperer.com/2013/12/07/putting-an-age-old-battle-to-rest/
[Economía del software y dependencias]: http://www.slideshare.net/programania/software-economics-tradeoffs-of-decoupled-softwre

