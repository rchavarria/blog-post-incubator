# Aprendiendo Elixir

No es una propósito de año nuevo ni nada, pero me apetece aprender un lenguaje puramente funcional por el simple hecho de aprender. He estado dudando entre Clojure y Elixir. Al final me he decidido por Elixir porque lo *venden* como divertido y porque sigo a varias personas en Twitter que están haciendo lo mismo, por lo que podré compartir lo aprendido. Dicen de Elixir que se parece mucho a Ruby, y que es un lenguaje moderno para la máquina virtual de Erlang. Con esos *hermanos mayores* promete mucho, la verdad.

Voy a poner en práctica el proceso de aprendizaje que descubrí leyendo el libro [Soft Skills], de John Sonmetz:

1. Entender la habilidad que se quiere aprender
2. Delimitar el ámbito
3. Definir qué se va a considerar como éxito
4. Encontrar recursos
5. Crear un plan de aprendizaje
6. Filtrar los recursos
7. Aprender lo suficiente para comenzar
8. Experimentar, jugar, buscar puntos desconocidos, hacerse preguntas
9. Aprender lo suficiente para hacer algo de utilidad
10. Enseñar lo aprendido, y repetir desde el paso 7

## ¿Qué habilidad quiero aprender?

Quiero aprender a programar en Elixir. La frase es sencilla, pero ¿qué significa? ¿Significa que solamente quiero aprender la sintaxis? No, eso no es aprender un lenguaje de programación. ¿Significa que debo aprender todas las herramientas, frameworks, librerías, sistemas,...? Tampoco. Eso es imposible. He programado durante años en Java o JavaScript y lo que desconozco de ellos es mucho más de lo que conozco.

Así pues, delimitaré el aprendizaje a conocer lo suficientemente el lenguaje y su ecosistema para ser capaz de escribir la parte servidora de una aplicación web.

## ¿Qué voy a considerar éxito?

Tengo que poner algún límite. Creo que algo realmente interesante sería considerar un éxito poder desarrollar la parte servidora de una aplicación web, una API REST o algo así, que gestionara algún tipo de recurso (usuarios, tareas, ... todavía no lo se). Si además soy capaz de desplegar la aplicación en alguna plataforma como Heroku o similar, el éxito sería rotundo. 

No me planteo nada de conectarlo a una base de datos, porque por ahora no he leído nada acerca de ello. Supongo que habrá alguna posibilidad, pero por ahora lo voy a dejar fuera.

## Recursos

- Web [elixir-lang.org]. Web oficial. Creo que me puede servir para tener documentación rápida de forma online.
- Libro [Programming Elixir, de Dave Thomas]. Parece ser el libro de referencia, así que es un recurso indispensable. [Foros de discusión del libro].
- [Código elixir en GitHub]. Código, código, código. 
- Screencasts [elixir sips]. Videos sobre Elixir, muchos de ellos bajo suscripción.
- [LearnElixitTV]. Más videos sobre Elixir, en este caso son de pago pero no de suscripción.
- [Elixir Dose]. Un blog sobre este lenguaje de programación.
- Blog de [Benjamin Tan]. Un blog sobre Ruby y Elixir del autor de un libro sobre Elixir. Parece venir del mundo Ruby. Tiene una charla en una conferencia de Ruby que hay que ver.
- Track de Elixir de [exercism.io], una plataforma social donde resolver problemas y comentar las soluciones del resto de usuarios.

También espero que poco a poco, según vaya necesitando saber más sobre cómo hacer cosas con el lenguaje, vaya descubriendo blogs y autores acerca del lenguaje.

## Plan de aprendizaje

Por ahora no tengo ningún plan. El más básico que tengo es empezar a leer el libro Programming Elixir y cuando sea capaz de escribir algún programa más complejo que un *Hola mundo* empezar a resolver problemas en exercism.io.

## Recursos filtrados

Creo que no tengo tantos recursos como para filtrarlos. Empezando con el libro, con exercism.io y de vez en cuando la web oficial del lenguaje puede ser suficiente para ir cogiendo ritmo.

## Primer bucle pasos 7-10

### Aprende lo suficiente para comenzar

- Instalar Erlang VM y Elixir.

```
$ wget https://packages.erlang-solutions.com/erlang-solutions_1.0_all.deb && sudo dpkg -i erlang-solutions_1.0_all.deb
$ sudo apt-get update
$ sudo apt-get install esl-erlang
$ sudo apt-get install elixir
```

- Pattern matching. El operador `=` es muy diferente a lo que conocía hasta ahora.

```
a = 2
[a, b, a] = [1, 2, 1]
[^a, b] = [2, 3]
[^a, c] = [1, 2]  # Error
[a, b, c] = [1, 2, [3, 4, 5]]   # c vale [3, 4, 5]
```

### Experimenta, juega, busca lo desconocido, hazte preguntas

### Aprende lo suficiente para hacer algo de utilidad

### Enseña/Comparte lo aprendido, y comienza otro bucle












[Soft Skills]: http://rchavarria.github.io/blog/2015/11/08/soft-skills/
[elixir-lang.org]: http://elixir-lang.org/
[Programming Elixir, de Dave Thomas]: https://pragprog.com/book/elixir/programming-elixir
[Foros de discusión del libro]: https://forums.pragprog.com/forums/322
[Código elixir en GitHub]: https://github.com/elixir-lang/elixir
[elixir sips]: http://elixirsips.com/
[LearnElixitTV]: https://www.learnelixir.tv/episodes
[Elixir Dose]: http://elixirdose.com/
[Benjamin Tan]: http://benjamintan.io/blog/
[exercism.io]: http://exercism.io/languages/elixir

