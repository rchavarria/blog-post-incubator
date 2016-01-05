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
- [Guía de estilo] para programar en Elixir. De obligado conocimiento para que tu código sea más legible por la comunidad.

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

- ¿Es eficiente devolver una copia de los datos? En los lenguajes funcionales, no se modifican los datos, se devuelve una copia de ellos transformados. Parece ineficiente, pero es todo lo contrario. Al no modificarse los originales, éstos pueden compartirse por muchas variables, y están tranquilos, que no se va a modificar. En los lenguajes no funcionales, se devuelve una copia (no eficiente), en los funcionales, en realidad no se devuelve una copia, se comparte todo lo que se puede. Por lo que es más eficiente
- ¿Qué pasa con el recolector de basura? ¿Consume muchos recursos para deshacerse de todos esos datos transformados que ya no se utilizan? No consume mucho, en Elixir (en Erlan en realidad), hay muchos procesos, cada uno con un *heap* distinto, por lo que el heap es más pequeño que en otros lenguajes, y el recolector de basura se ejecuta bastante más rápido.
- Tipos de datos:

  - (tipos de valor) Entero: `1234`, `0xcafe`, `0o765`, `0b01010`, `1_000_000`. No tienen límite superior.
  - (tipos de valor) Coma flotante: `1.0`, `0.245`, `.324` (error), `314159.0e-5`.
  - (tipos de valor) *Atoms*: son constantes representando el nombre de algo. Todos comienzan con `:`. Su nombre es su valor. Dos Atoms son iguales si tienen el mismo nombre, vengan de donde vengan (incluso de máquinas diferentes). Atoms válidos serían: `:fred`, `:is_binary?`, `:var@32`, `:<>`, `:"lo john silver"`
  - (tipos de valor) Rangos: `start..end`. Por ejemplo, `1..100`.
  - (tipos de valor) Expresiones regulares: `~r{regexp}options`
  - (tipos de sistema) PIDs: referencias a procesos, locales (`self`) o remotos
  - (tipos de sistema) Puertos: referencias a recursos sobre los cuales leeremos o escribiremos
  - (tipos de sistema) Referencias: `make_ref` crea referencias únicas.
  - (collecciones) Tuplas: colección ordenada de valores. `{ :ok, 42, "next" }`
  - (collecciones) Listas: `[1, 2, 3]`. Se parecen a los arrays de otros lenguajes, pero no lo son. Son estructuras enlazadas. Una lista está vacía o contiene un *head* y un *tail*, donde tail es otra lista. Algunos operadores sobre listas: concadenar `++`, diferencia `--`, pertenencia `in`.
  - (collecciones) Mapas: lista de parejas clave/valor. `%{ key => value, key => value }`. Si las claves son Atoms, existe un atajo: `%{ red: 0xFF0000, green: 0x00FF00, blue: 0x0000FF }` en lugar de `%{ :red => 0xFF0000, ... }`. Para acceder a un mapa, se usan los corchetes: `map[key]`. Si las claves son Atoms, se puede usar punto: `map.key`.
  - (collecciones) Binarios: para acceder a datos como una secuencia de bits y bytes (para muy bajo nivel).

Hay dos estructuras muy similares, la lista de palabras clave: `[red: 0xFF000, green: 0x00FF00]`, que se transforma en `[{:red, 0xFF0000}, {:green, 0x00FF00}]` y un mapa `%{red: 0xFF000, green: 0x00FF00}`. Se recomienda usar la lista de palabras clave para pasar parámetros y usar los mapas cuando se necesite un array asociativo.

- Funciones anónimas. Se definen con `fn`, terminando en `end`. Para separar los parámetros del cuerpo de la función, se usa `->`. `sum = fn (a, b) -> a + b end`. Para llamar a la función, hay que hacerlo poniendo un `.` antes de los parámetros. `sum.(1, 2)`.
- Interpolación de valores en cadenas. Si dentro de una cadena, ponemos `#{...}`, se evalúa el código de dentro y se formatea la cadena con el valor obtenido.
- Las funciones pueden devolver otras funciones. Las funciones recuerdan su entorno original (forman lo que se llaman *closures*, parecido a JavaScript)


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
[Guía de estilo]: https://github.com/niftyn8/elixir_style_guide

