# Elixir: primer asalto (tipos, funciones anónimas, módulos)

Éste es el primer asalto de mi aprendizaje de [Elixir]. En él, no espero resolver problemas súper complicados, me conformaré con ser capaz de escribir un programa algo más complicado que un simple hola mundo.

## Aprender lo suficiente para comenzar

**Instalación**

Instalar la máquina virtual de Erlang y el entorno de Elixir es extremadamente sencillo. Aquí están los comandos para hacerlo en una máquina con Ubuntu como sistema operativo.

```
$ wget https://packages.erlang-solutions.com/erlang-solutions_1.0_all.deb
$ sudo dpkg -i erlang-solutions_1.0_all.deb
$ sudo apt-get update
$ sudo apt-get install esl-erlang
$ sudo apt-get install elixir
```

**Editores**

La comunidad Elixir ha creado plugins para los editores de código más famosos, entre ellos [Vim], que utilizo para mis [proyectos personales].

Instalar plugin [vim-elixir] en vim es facilísimo si instalas plugins con pathogen:

```
$ git clone https://github.com/elixir-lang/vim-elixir.git ~/.vim/bundle/vim-elixir
```

**Pattern matching**

El operador `=` es muy diferente a lo que esperamos de él en la programación orientada a objetos. Tiene una apariencia similar, pero no se comporta de la misma forma. Con este operador, Elixir trata de *casar* los valores de la izquierda con los valores de la derecha.

```
a = 2
[a, b, a] = [1, 2, 1]
[^a, b] = [2, 3]
[a, b, c] = [1, 2, [3, 4, 5]]   # c vale [3, 4, 5]
```

**Inmutabilidad**

¿Es eficiente devolver una copia de los datos? En los lenguajes funcionales, no se modifican los datos, se devuelve una copia de ellos transformados. Parece ineficiente, pero es todo lo contrario. Al no modificarse los originales, éstos pueden compartirse por muchas variables, y están tranquilos, que no se va a modificar. En los lenguajes no funcionales, se devuelve una copia (no eficiente), en los funcionales, en realidad no se devuelve una copia, se comparte todo lo que se puede. Por lo que es más eficiente


¿Qué pasa con el recolector de basura? ¿Consume muchos recursos para deshacerse de todos esos datos transformados que ya no se utilizan? No consume mucho, en Elixir (en Erlang en realidad), hay muchos procesos, cada uno con un *heap* distinto, por lo que el heap es más pequeño que en otros lenguajes, y el recolector de basura se ejecuta bastante más rápido.

**Tipos de datos**

```
# enteros
this_is_an_int = 1234
this_is_an_int = 0xcafe    # admite hexadecimal
this_is_an_int = 0o765     # octal
this_is_an_int = 0b01010   # binario
this_is_an_int = 1_000_000

# en coma flotante
this_is_a_float = 1.0
this_is_a_float = 0.245
this_is_a_float = .342        # error
this_is_a_float = 314159.0e-5

# rangos
this_is_a_range = 1..100

# expresiones regulares
this_is_a_regexp = ~r{regexp}options

# tuplas
this_is_a_tuple = { :ok, 42, "next" }

# listas: se parecen a los arrays de otros lenguajes, pero no
#lo son. Son estructuras enlazadas. Una lista o está vacía, o
#contiene un head y un tail, donde tail es otra lista
this_is_a_list = [ 1, 2, 3 ]

# mapas: lista de parejas clave/valor 
this_is_a_map = %{ key => value, key => value }
# si las claves son Atoms, se puede escribir
this_is_a_map = %{ red: 0xFF0000, green: 0x00FF00, blue: 0x0000FF }

# binarios: para acceder a datos como una secuencia de bits y bytes (para muy bajo nivel)
```

Hay otros tipos de datos, como los PIDs (referencias a procesos locales o remotos) o los puertos (referencias a recursos sobre los cuales leeremos o escribiremos).

Un tipo de datos muy interesante (y que yo personalmente no conocía) son los *Atoms*: constantes representando el nombre de algo. Su nombre es su valor. Dos Atoms son igules si tienen el mismo nombre, vengan de donde vengan (incluso de máquinas diferentes)

```
# atoms
this_is_an_atom = :fred
this_is_an_atom = :is_binary?
this_is_an_atom = :var@32
this_is_an_atom = :<>
this_is_an_atom = :"lo john silver"
```

Hay dos estructuras muy similares, la lista de palabras clave: `[red: 0xFF000, green: 0x00FF00]`, que se transforma en `[{:red, 0xFF0000}, {:green, 0x00FF00}]` y un mapa `%{red: 0xFF000, green: 0x00FF00}`. Se recomienda usar la lista de palabras clave para pasar parámetros y usar los mapas cuando se necesite un array asociativo.

No hemos dicho nada de las cadenas. Pertenecen al tipo *Binario*. Existe interpolación de cadenas, con `#{...}` se evalúa el código de dentro y se formatea la cadena con el valor obtenido.

**Funciones anónimas**

```
sum = fn (a, b) -> a + b end
sum.(2, 3)   # devuelve 5
```

Las funciones pueden devolver otras funciones. Las funciones recuerdan su entorno original. Forman lo que se conoce como *closures*. Me recuerda mucho a las funciones de JavaScript en este aspecto.

- Operador `&`. Con él se pueden crear funciones anónimas de una forma muy concisa: `&(&1 + &2)` (suma el primer y el segundo paràmetro, idéntica a `fn a, b -> a + b end`). Si queremos que devuelva una lista: `&[&1 * 2, &1 * &1]` (devuelve una lista con dos elementos, el doble del primer parámetro de la función y el cuadrado del mismo). Esta notación es muy buena para pasar funciones por parámetro: `Enum.map [1, 2, 3, 4] &(&1 * &1)`, devuelve `[1, 4, 9, 16]`
- *arity* (inglés): número de parámetros de una función
- `iex <fichero.exs>` compila un script de Elixir y lo carga en REPL. Si ya estamos dentro de `iex`, el comando sería `c "<fichero exs>"`
- Las funciones con nombre (*named functions*), también pueden tener varios cuerpos. Eso ayuda a utilizar *pattern matching* a la hora de implementar una solución.
- Claúsulas de guarda: en la definición de una named function, se puede utilizar una claúsula `when` con una condición, lo que ayuda a tener un patter matching más específico
- El operador `|>`. Toma el resultado de una función y lo pasa como primer parámetro de la segunda función. `String.reverse "foobar" |> String.capitalize`

## Experimentar, jugar, buscar puntos desconocidos, hacerse preguntas

- ¿Qué hace `^` en el pattern matching?

```
a = 2
[^a, b] = [2, 3]
[^a, b] = [1, 3]  ## error
```

## Aprender lo suficiente para hacer algo de utilidad

## Enseñar lo aprendido, y repetir desde el paso 7

[vim-elixir]: https://github.com/elixir-lang/vim-elixir

