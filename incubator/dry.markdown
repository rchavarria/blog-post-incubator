# DRY, evita duplicidades, seco, zipi y zape, gemelos, copy&paste, prohibido, principios,...

{% img de una célula clonándose %}

# introducción

En biología, el concepto de repetirse a uno mismo es fundamental. Ninguno de nosotros existiríamos si los primeros organismos unicelulares no hubieran sido capaces de desarrollar el mecanismo de **XXXXXX**, la capacidad de multiplicarse, de crear réplicas de sí mismos. 

Los niños pequeños aprenden por imitación, repitiendo lo que observan en los demás

A la hora de desarrollar software, la repetición no está vista con tan buenos ojos. Por ejemplo, se ha dado un nombre despectivo a los programas que crean copias de sí mismos, como los *virus*. Por otro lado, la duplicidad de código de una aplicación produce muchos quebraderos de cabeza a aquellos de nosotros que nos dedicamos al software. Para recordárnoslo, contamos con el principio *DRY, don't repeat yourself*, o, no te repitas a tí mismo.

<!-- more -->

> Definición de DRY ~ Martin Fowler

# definición
# que es duplicaciión y qué no lo es
# duplicaiones en los tests
# 4 reglas del diseño simple, por J.B.Rainsberger, que al final resume en dos: nombrar y eliminar duplicidades
# metodos para eliminar duplicidades: extract method, extract class, metaprogramación, añadir indirección
# en contraposición a DRY, está el principio WET


### recursos

- charla de artolamola y ggalmanzor, economía del software, eliminar duplicados introduce abstracciones que añade dependencias. eliminar duplicidades horizontales y/o verticales?

- Mantaining balance while reducing duplication

- Dave Thomas en CodeNewbie podcast


# (01-10-2015) Mantaining Balance while reducing duplication

https://www.youtube.com/watch?v=Is8ThG6Fetg&feature=youtu.be

Mantaining Balance while reducing duplication

comentarios sobre esta charla?

- en los tests, existen los custom matchers, ellos te ayudan a reducir duplicidad en el código. deberían seguir el principio DRY?
- everytime you reduce duplication you increase coupling by introducing new dependencies
- DRY is not about the same characters written twice, is about duplicated CONCEPTS
- una refactorzacón básica para eliminar dupliccidad es "extract method"
- less duplicaton can mean more indirection, and can make code more difficult to read (y más difícil de seguir la pista, porque, para no duplicar, los detalles están dispersos en varios sitios)
- en Ruby, la metaprogramación tamibén puede ayudar a eliminar duplicidad, pero la metaprogramaicón hace el código mucho más difícil de leer
- posible definicón de DRY: "every *piece of knowledge* must have a *single*, *unambiguous*, *authorative representation* within a system
- depend on things which are less likely to change (or abstractions, but abstractions can be everywhere, for example, in ruby)
- OOP in one sentence: "keep it *shy*, *dry* and *tell* the other guy" (shy por lo de encapsulación, y lo de *tell* por lo de *tell don't ask*)
- 

# Dave Thomas en CodeNewbie podcast

Parte I : http://www.codenewbie.org/podcast/the-pragmatic-programmer-i
Parte II: http://www.codenewbie.org/podcast/the-pragmatic-programmer-part-ii

En la parte I, Dave cuenta la historia de cómo nació el libro The Pragmatic Programmer (alargar esto un poquejo, para ocupar un parrafete, todo texto, diferente de otras editoras, cuando lo enviaron esperaban que les corrigieran, ...

En la parte II;
 - Sobre el minuto 8 habla sobre las Katas. Recurso excepcional. Comenta que lo importante de la kata no es el ejercicio en sí, sino la repetición, hacer el ejercicio sin pensar en la solución (sin pensar mjcho vamos), y reflexionar en la evolución que vamos consiguiendo. De esta forma hacemos que nuestro cerebro haga 'pattern matching' (tan de moda ahora) y *aprendamos* sin saber porqué.
- Luego habla sobre el principio DRY, y su contrario WET (write everything twice) XD
- Consejos para los nuevos : comenzar a programar "sin reglas", con la experiencia ya la irás aprendiendo. Es como conducir, tienes que ir poco a poco (conducir rally, cambiar doble embrague, no pegar en los bolardos,...)

