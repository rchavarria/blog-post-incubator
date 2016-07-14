# Practical Vim
## de Drew Neil

[![Practical Vim](img/practical-vim.jpg)](https://pragprog.com/book/dnvim/practical-vim)

### Por qué lo he leído

Hace un tiempo decidí que quería [aprender a utilizar Vim](http://rchavarria.github.io/blog/2014/10/11/aprendiendo-vim/). Entre los muchos recursos para aprender se encontraba este libro, pero encontré más prácticos una serie de videos. Pero más adelante, escuchando el podcast [Giant Robots](http://giantrobots.fm/), hablaron de este libro, y cuando recibes varias señales, quiere decir algo.

<!-- more -->

### De qué trata el libro

El libro no es un manual desde cero. Tampoco es un manual avanzado. Es un conjunto de trucos, de sugerencias, que trata de explicar y convencer al lector de la filosofía y bondades del editor. Entre estos trucos encontrarás muchos que te sean de utilidad, y otros tantos tan extraños que ni te molestarás en entenderlos. Pero lo más importante es que describe una *forma de pensar en Vim*. A la hora de editar ficheros de texto no hay una única forma de hacer las cosas, ni tampoco una forma superior a otras alternativas, pero en Vim sí que hay una filosofía, una idea de atacar cada edición. Este libro te sumerge en ella.

### Conclusiones y valoración

El libro es una maravilla. Está lleno de trucos. Muchos de ellos los conocía, y otros ni siquiera sabía que existían. En cambio, otros, después de llevar un tiempo usando Vim, tenía una ligera sospecha de que se podrían hacer, pero no había invertido el tiempo en averiguar cómo.

Si tienes ganas de incarle el diente a un editor que sobrevive al paso del tiempo, échale un vistazo al libro.

Debería echar un vistazo al proyecto de Mozilla [Doctor JS], que contiene la herramienta `jsctags`, para generar ficheros ctags de proyectos JavaScript.

### Frases que me gustaría recordar

> La fórmula del punto: una pulsación de tecla para mover, una pulsación de tecla para ejecutar la edición

> La estrategia óptima de edición es hacer que tanto el cambio como el movimiento sean repetibles

> Podemos hacer que el comando deshacer opere en palabras, frases o párrafos enteros solamente haciendo un uso corrrecto de la tecla `Esc`

> La combinación de operadores con movimientos forman una especie de gramática. Aprender nuevos movimientos y operadores is como aprender el vocabulario de Vim. Si seguimos las reglas sencillas de la gramática, podremos expresar más y mejores ideas según vaya creciendo nuestro vocabulario

> Una buena forma de trabajar con macros sería: normalizar la posición del cursor, llegar hasta el objetivo con un movimiento repetible, hacer que la macro aborte cuando el movimiento falle y no encuentre el objetivo

> La sintaxis para definir un rango en los Ex commands es muy flexible. Se pueden mezclar números de línea, marcas y patrones de búsqueda. Y se puede aplicar un offset a cada uno de ellos

> Intenta crear el hábito de crear una marca global (`m{capital letter}`) antes de usar cualquier comando que interacciones con la lista de arreglos rápidos, lista de buffers o lista de argumentos

> Para editar una macro grabada en el registro `q`, simplemente podemos pegar el contenido de dicho registro con `"qy`, editar la línea y modificar el registro `q` con `"qy$`

### Qué he aprendido

Hay toda una serie de nuevos comandos, combinaciones de ellos y herramientas que todavía no conocía o que he encontrado muy útiles:

- `~`: intercambia el carácter actual de mayúsculas a minúsculas y viceversa
- `g~`, `gu`, `gU`: intercambia mayúsculas/minúsculas en la selección, pasa a minúsculas, pasa a mayúsculas, respectivamente.
- `<C-h>`, `<C-w>`, `<C-u>`: en modo inserción o modo comando, borra hacia atrás un carácter, una palabra o la línea completa, respectivamente.
- `<C-r>{register}`: en modo inserción, inserta el texto desde el registro `register`
- `<C-r><C-p>{register}`: idem, pero más inteligentemente, ya que arregla cualquier error de indentación por descuido
- `<C-v>{code}`: en modo inserción, inserta un carácter especial por su código `code`
- `R`: nos lleva del modo normal al *modo de reemplazo*, donde cada carácter insertado reemplaza a un carácter existente
- `v`, `V`, `<C-v>`: entra en los distintos modos visuales: de carácter, de línea o de bloque.
- `o`: dentro del modo visual, la selección tiene dos extremos, con este comando intercambiamos entre ellos, de forma que podemos expandir la selección hacia adelante o hacia atrás
- `.`, `%`: en el modo comando tienen significado especial cuando se especifica un rango. Significan la línea actual y todas las líneas, respectivamente.
- `:t`: comando para duplicar líneas. `:3t 5` copia la línea 3 y la pega en la 5. `:.+2t .` copia dos líneas más abajo y la pega en la línea actual
- `:m`: comando para mover líneas
- `@:`: repite el último Ex Command, lo cual es muy útil cuando estamos haciendo cambios en múltiples ficheros, o vamos recorriendo la lista de búferes
- en modo comando, se pueden ejecutar comandos del modo normal, con el Ex Command `normal`. Por ejemplo, `:%normal A;` hace lo siguiente: `:` entramos en modo comando, `%` indica que afectará a todas las líneas del fichero, `normal` indica que introduciremos un comando del modo normal, `A;` es un comando del modo normal, y lo que hace es añadir al final de la línea el carácter `;`.
- `<C-o>`: vuelve atrás en la lista de saltos (cambios de buffer, grandes saltos de líneas, búsquedas,...)
- `<Tab>`, `<C-n>`, `<Left>` y `<S-Tab>`, `<C-p>`, `<Right>`: para movernos adelante y atrás durante el autocompletado
- `<C-r><C-w>`: en modo comando, copia la palabra debajo del cursor y la pega en la línea de comandos
- `<C-p>`, `<C-n>`: después de entrar en el modo comando con `:` o `/`, podemos pulsarlos para ir hacia adelante o atrás en el historial de comandos o búsquedas
- `q/`: abre la ventana *línea de comandos* con el historial de búsquedas
- `q:`: abre la ventana *línea de comandos* con el historial de comandos
- `<C-f>`: en modo comando, cambia a la ventana de línea de comandos
- `:read !{shell command}`: pone el resultado del comando shell en el buffer actual
- `:write !{shell command}`: usa el contenido del buffer actual como entrada para el comando shell
- `:bnext`, `:bprevious`, `:bfirst`, `:blast`: para moverse por los buffers
- `:edit {path to a dir}`: abre el contenido del directorio en un buffer, de forma que podemos navegar el sistema de ficheros sin necesidad de ningún plugin. `.` significa el actual directorio de trabajo. `:explore` o `:E` hace lo mismo. `:Sexplore` divide los buffers horizontalmente, `:Vexplore` divide los buffers verticalmente
- igual que existen `w`, `b`, `e` y `ge` (mueve al final de la palabra anterior), existen `W`, `B`, `E` y `gE` para hacerlo con PALABRAS, no con palabras
- `is`, `as`, `ip`, `ap`: son movimientos (que se pueden usar con los comandos `d`, `c`, `y`,...) que engloban la actual frase (sentencia) o párrafo
- `<C-o>`, `<C-i>`: para movernos adelante y atrás en los saltos que vamos dando
- `:changes`: muestra el historial de cambios
- `g;`, `g,`: para movernos adelante y atrás por el historial de cambios
- `gi`: vuelve al último punto donde abandonamos el modo de inserción, entrando en dicho modo
- `"_d{motion}`: borra lo indicado pero no copia el contenido en ningún sitio (bueno, sí, en el registro `_`, pero éste no guarda el contenido). Si no se indica nada, los comandos `x`, `s`, `d` y `c` modifican el registro sin nombre, con lo que pueden eliminar el contenido que hayamos copiado con `y`.
- el registro de copiado es el `0`, y éste no es modificado nunca por los comandos `x`, `s`, `d` y `c`.
- si al copiar o borrar nombramos un registro con mayúsculas, el contenido se añadirá a lo que contenga el registro
- `\v`: activa la magia en los patrones de búsqueda. Hace que todos los carácteres excepto los alfanuméricos y `_` tengan un significado especial
- `:%s///gn`: cuenta las ocurrencias del patrón actual de búsqueda
- flags del comando de sustitución: `g` reemplaza todas las ocurrencias en una línea, no solo la primera; `c` pide confirmación, `n` cuenta las ocurrencias, `&` reusa los últimos flags 
- `:%s//\=@0/g`: sustituye todas las ocurrencias (flag `g`) de todas las filas (rango `%`) del último patrón buscado (`//`) con el contenido del registro `0` (`\=` evalúa una expresión, `@0` accede al registro `0`)
- `&`: repite los cambios hechos por el último comando de sustitución `:s/pattern/.../`
- `g&`: repite el último comando de sustitución en todo el fichero
- `:vimgrep {pattern} {file pattern}`: busca el patrón en la lista de ficheros y rellena la lista *quickfix*. Luego podemos pasar el resultado a la lista de argumentos con el plugin *qargs*
- `:global/{pattern}/{command}` o `:g`: permite ejecutar un comando en cada línea que cumpla con el patrón
- `<C-]>`: mover hasta la definición de la palabra clave (tag) donde se encuentra el cursor
- `<C-t>`: vuelve atrás en la última tag visitada
- `:copen`, `:cclose`: abre/cierra la ventana de lista *quickfix*
- `:cnext`, `:cprevious`, `:cfirst`, `:clast`: para moverse por los marcadores de la lista quickfix
- `:colder`, `:cnewer`: para pasar de listas quickfix más nuevas a las más viejas y viceversa

### Recursos relacionados

Debería echar un vistazo al proyecto de Mozilla [Doctor JS], que contiene la herramienta `jsctags`, para generar ficheros ctags de proyectos JavaScript.

### Notas tomadas

Echar un vistazo a `vimtutor`, dentro de Vim. Quizá es una buena forma de empezar, aunque uno ya haya dado algunos pasos con Vim.

## Capítulo 1 - La forma de hacer las cosas en Vim

Vim está optimizado para la repetición

### Consejo 1 - Te presento el comando punto

El comando *punto* (`.`) permite repetir el último cambio

### Consejo 2 - No te repitas

Vim provides dedicated commands that combines two steps into one. `A` command compounds two actions `$a` into a single keystroke

## Consejo 3 - Muévete un paso atrás, luego tres hacia adelante

El comando `s` se compone de dos pasos en uno: primero borra el carácter bajo el cursos, luego entra en el modo inserción

### Consejo 4 - Actúa, repite, revierte

La estrategia óptima de edición es hacer repetible tanto el movimiento como el cambio en sí.

Por ejemplo, `@:` repite cualquier comando *Ex*. O podemos repetir el último comando `:substitute` pulsando `&`

### Consejo 5 - Busca y reemplaza a mano

Cambia la primera ocurrencia a mano. Luego busca y reemplaza cada ocurrencia una a una

Sé vago: busca sin escribir la palabra con el comando `*`

### Consejo 6 - Te presento la fórmula punto

Una pulsación de tecla para mover, una pulsación de tecla para ejecutar el cambio

## Chapter 2 - Modo Normal

### Consejo 7 - Pausa tu pincel fuera del óleo

Así como los pintores pasan una fracción de su tiempo aplicando pintura, los programadores emplean una fracción de su tiempo componiendo el código

### Consejo 8 - Agrupa tus comandos deshacer

Podemos hacer que el comando deshacer opere con palabras, frases o párrafos, solo tenemos que adecuar nuestro uso de la tecla `<Esc>`

### Consejo 9 - Compón cambios repetibles

Hay que prestar atención a la forma en que componemos nuestros cambios, de esta manera nos aprovecharemos del comando `.`, de deshacer y todo de lo que estamos hablando hasta ahora

### Consejo 10 - Usa las cuentas para hacer aritmética simple

`<C-a>`, `<C-x` para sumar o restar uno. `4<C-a>` para sumar cuatro veces uno.

### Consejo 11 - No cuentes si puedes repetir

Considera los pros y los contras de contar frente a repetir. Especialmente a la hora de deshacer. Es más fácil deshacer cambios repetibles que los no repetibles. `2dw` contra `dw` + `.`

### Consejo 12 - Combina y conquista

Gran parte del poder de Vim radica en la forma en la que operadores y movimientos se pueden combinar. Su combinación forma una especie de gramática. Aprender nuevos movimientos y operadores es cmoo aprender el vocabulario de Vim. Si sigues unas cuantas reglas gramáticas simples, podrás expresar más ideas conforme tu vocabulario vaya creciendo.

## Chapter 3 Modo Inserción

### Consejo 13 - Corrige instantáneamente desde el modo inserción

Los comandos `<C-h>`, `<C-w>`, `<C-u>` borran un carácter, palabra o línea

### Consejo 14 - Vuelta al modo normal

El modo *inserción normal* es una versión especial del modo normal, que te da una sola oportunidad. Puedes ejecutar un único comando, después del cual volverás al modo inserción.

Reconfigura la tecla `Bloq Mayus`. Muchos usuarios la reconfiguran para hacer que se comporte como `<Esc>` o `<Ctrl>`. Lo mejor es hacerlo a nivel del sistema.

### Consejo 15 - Pega el contenido de un registro sin abandonar el modo inserción

El formato general del sistema es: `<C-r>{register}`

El comando `<C-r><C-p>{register}` es mejor. Inserta el texto literalmente y corrige indentaciones no deseadas

### Consejo 16 - Haz pequeños cálculos de forma rápida

El registro de expresión (con nombre `=`) te permite hacer pequeños cálculos e insertar el resultado directamente en el documento. Desde el modo inserción, podemos acceder a él a través de `<C-r>=`

### Consejo 17 - Inserta carácteres poco habituales a través de su código

Desde el modo inserción, teclea `<C-v>{code}`

### Consejo 18 - Inserta carácteres por *digrafo*

### Consejo 19 - Sobreescribe texto existente en el modo de reemplazo

Desde el modo normal, puedes entra al modo reemplazo mediante el comando `R`. Al modo de reemplazo virtual se entra con `gR` y éste trata el tabulador como espacios.

## Chapter 4 Modo visual

### Consejo 20 - Entendiendo el modo visual

El modo visual es otro modo, lo que significa que cada tecla realiza una función diferente. Según la documentación, el modo *recuerda al modo de selección de Windows*. Podemos pasar del modo visual al modo de selección tecleando `<C-g>`. Si tecleamos cualquier carácter imprimible en el modo selección, reemplazará la selección y entrará en modo inserción.

### Consejo 21 - Definiendo una selección visual

Existen tres tipos de modos visuales:

- de carácter: se entra con el comando `v`
- de línea: se entra con el comando `V`
- de bloque: se entra con el comando `<C-v>`

`gv` selecciona la última selección visual

El rango de una selección visual está delimitado por dos extremos: uno fijo y el otro móvil. Podemos usar el comando `o` (en modo visual) para intercambiar el extremo móvil.

### Consejo 23 - Prioriza operadores frente a comandos visuales siempre que sea posible

El modo visual es más intuitivo que el modo noraml, pero tiene sus debilidades: no funciona bien con el comando `.`

### Consejo 24 - Edita datos tabulares con el modo visual de bloque

### Consejo 25 - Cambia columnas de texto

Puedes usar el modo visual de bloque para insertar texto en varias líneas de texto simultáneamente

### Consejo 26 - Añade al final de un bloque visual

El modo visual de bloque no está limitado a regiones rectangulares de texto.

Los comandos `I` y `A` posicionan el cursor al inicio y al final de la selección.

En modo visual o en modo espera de operador, las teclas `i` y `a` siguen una convención diferente: son la primera mitad de un *objecto textual*

## Chapter 5 - El modo de línea de comandos

### Consejo 27 - Te presento el modo de línea de comandos

El modo de línea de comandos te permite escribir un comando Ex, un patrón de búsqueda o una expresión. Cuando pulsamos `:` entramos en el modo de línea de comandos. El modo de línea de comandos también se habilita con `/` o con `<C-r>=`

Igual que en modo de inserción, `<C-w>`, `<C-u>` y `<C-r>{register}` también funcionan

Lo mejor de los comandos Ex es que pueden ser ejecutados en múltiples líneas a la vez

### Consejo 28 - Ejecuta un comando en una o más líneas consecutivas

Muchos comandos Ex aceptan un rango de líneas sobre las que acutar. Si el rango consiste en solo un número, éste se interpreta como un número de línea. Por ejemplo, `:3d` borra la línea 3. Mientras que `:2,5d` borra las líneas de la 2 a la 5

`.` es el número de la línea donde se encuentra el cursor. `%` significa todas las líneas del fichero actual

Los rangos también se pueden especificar mediante una selección visual, o por patrones. `:{inicio},{fin}`. La dirección de inicio puede ser el patrón `/<html>/`, y la dirección final puede ser `/<\/html>/`.

También se pueden usar desplazamientos: `:/<html>/+1,/<\html/>/-1`

### Consejo 29 - Duplica o mueve líneas con los comandos `:t` o `:m`

Una diferencia notable en la forma de copiar líneas es que `yyp` utiliza un registro, mientras que `:t` no. A la hora de duplicar una línea lejana, el comando `:t` es mucho más eficiente.

### Consejo 30 - Ejecuta comandos del modo normal en un rango de líneas

Si quieres ejecutar un comando del modo normal en un rango de líneas puedes utilizar el comando `:normal`.

Por ejemplo, `:%normal A;` añade el carácter `;` a cada línea.

Esto es muy útil, especialmente en combinación con uno de los comandos de repetición: `:normal .` o `:normal @@`

### Consejo 31 - Repite el último comando Ex

`@:` puede ser muy útil si estamos iterando por la lista de búfferes. Podemos movernos por ellos con `:bn[ext]` y `:bp[revious]`.

Después de ejecutar `@:` una vez, podemos volver a repetirlo con `@@`. Usa `<C-o>` para volver al lugar anterior antes de dar un salto.

### Consejo 32 - Autocompleta tus comandos Ex

Usa `<Tab>`, como en una shell, para autocompletar comandos Ex. `<C-d>` muestra una lista de las posibles opciones. 

Se puede personalizar este comportamiento con la opción `wildmode`:

    wildmode=longest,list
    wildmenu
    set wildmode=full

Se puede navegar por ellas con `<Tab>` y `<S-Tab>`, `<C-n>` y `<C-p>` o `<Right>` y `<Left>`

### Consejo 33 - Inserta la palabra actual en el prompt de comandos

Escribiendo un comando Ex, `<C-r><C-w>` copia la palabra bajo el cursor y la copia en el prompt de comandos. `<C-r><C-a>` copia la PALABRA

### Consejo 34 - Rellamar comandos del histórico

Vim recuerda por defecto los últimos 20 comandos. Se puede cambiar con 

    set history=200

Igual que recuerda comandos, Vim también recuerda patrones de búsqueda.

Tanto en modo comando, como en modo de búsqueda (escribiendo un patrón de búsqueda), podemos usar `<C-n>` y `<C-p>` o `<Up>` y `<Down>` para movernos por el histórico.

Las flechas tienen una ventaja, y es que ellas filtran la búsqueda por el texto que haya introducido el usuario hasta el momento. Podemos tener lo mejor de ambas opciones si remapeamos:

    cnoremap <C-p> <Up>
    cnoremap <C-n> <Down>

`q/` abre una ventana con el histórico de búsquedas, `q:` hace lo propio con un histórico de comandos. `<C-f>` pasa del modo comando a la ventana de histórico

### Consejo 35 - Ejecutar comandos en la shell

Desde el modo de línea de comandos, podemos invocar comandos de la shel escribiendo primero la exclamación, así: `:!`

En modo de línea de comandos, `%` se sustituye por el nombre del fichero actual.

¿Y si queremos ejecutar varios comandos? Podemos hacerlo con la order `:shell`.

Puedes usar `:read !{cmd}` para leer la salida del comando `cmd` en el buffer actual. De la misma forma, se puede utilizar `:write !{cmd}` para lo inverso: usa los contenidos del buffer actual como entrada para el comando `cmd`.

Por ejemplo, los comandos `make` y `grep` tienen envoltorios. No solo son más fáciles de ejecutar desde Vim, sino que su salida se parsea y se usa para rellenar la lista *quickfix*.

## Chapter 6 - Gestionar múltiples ficheros

### Consejo 36 - Gestionar ficheros abiertos con la lista de búfferes

Los ficheros se almacenan en disco, mientras que los búfferes se almacenan en memoria. Se puede navegar entre ficheros pulsando `<C-^>`. El autor usa estos mapeos del plugin the Tim Pope, unimpared.vim:

    nnoremap <silent> [b :bprevious <CR>
    nnoremap <silent> ]b :bnext <CR>
    nnoremap <silent> [B :bfirst <CR>
    nnoremap <silent> ]B :blast <CR>

### Consejo 37 - Agrupa búfferes en una colección con la lista de argumentos

Puedes consultar la lista de argumentos con `:args`. Esta lista representa la lista de ficheros que fue pasada como argumento cuando se ejecutó el comando `vim` para abrir el editor.

Podemos cambiar el contenido de esta lista con `:args {arg list}`.

Podemos navegar la lista con `:next` y `:prev`. Puedes usar `:argdo` para ejecutar el mismo comando en cada buffer de la lista.

### Consejo 38 - Gestionar ficheros ocultos

Si quieres descartar los cambios, puedes ejecutar `:edit!`, que recarga el fichero desde disco, sobreescribiendo el contenido del buffer. Si quieres salir de Vim sin revisar ficheros sin guardar, ejecuta `:qall!`. Si quieres escribir todos los cambios, `:wall`.

Si habilitas la opción `hidden`, si el buffer activo está modificado, Vim lo ocultará automáticamente cuando navegues fuera del fichero.

### Consejo 39 - Divide tu espacio de trabajo en ventanas

`:sp[lit] {file}` divide horizontalmente, cargando el fichero `file` en la nueva ventana
`:vsp[lit] {file}` igual, pero verticalmente
`<C-w>w` or `<C-w><C-w>` navega entre ventanas
`:cl[ose]` or `<C-w>c` cierra la ventana activa
`:on[ly]` or `<C-w>o` cierra todas las ventanas menos la activa

### Consejo 40 - Organiza tus ventanas con pestañas

Piensa en una pestaña como un contenedor que puede contener una colección de ventanas. Las pestañas pueden usarse para partir el trabajo en distintos espacios de trabajo. El comando `:lcd {path}` te permite cambiar el directorio de trabajo local (*local current directory*) para la ventana actual. Si creas una nueva pestaña y usamos el comando `:lcd`, podrás usar cada pestaña para trabajar en un directorio diferente.

Si tienes una pestaña con 2 o más ventanas, puedes establecer el directorio local para todas ellas con `:window lcd {path}`

Puedes abrir una nueva pestaña con `:tabedit {file}`. El comando `<C-w>T` mueve la ventana actual a una nueva pestaña.

`:tabclose` cierra la pestaña. Para cerrar todas menos la actual, usa `:tabonly`.

`:tabn[ext] {N}` o `{N}gt` navega a la pestaña con número `N`
`:tabn[ext]` o `gt` navega a la siguiente pestaña
`:tabp[revious]` o `gT` vuelve a la pestaña anterior

## Chapter 7 - Abrir ficheros y guardarlos en disco

### Consejo 41 - Abre un fichero a partir de su ruta con `:edit`

Prueba a insertar esta línea en tu Vim: `cnoremap <expr> %%  getcmdtype() == ':' ? expand('%:h').'/' : '%%'`

Ahora, cuando teclees `%%` en la línea de comandos de Vim, se expandirá automáticamente por la ruta del buffer activo, como si hubieras tecleado `%:h <Tab>`

### Consejo 42 - Abre un fichero a partir de su nombre con `:find`

La opción `path` permite especificar una serie de directorios donde Vim buscará cuando se invoque el comando `:find`. Se puede modificar, por ejemplo, con `:set path+=app/**`

### Consejo 43 - Explora el sistema de ficheros con `netrw`

Si ejecutas Vim pasándole un directorio en lugar de un fichero, se abrirá una ventana con el explorardor de ficheros.

Puede abrir el directorio padre de donde te encuentres pulsando `-`, o navegando hasta el directorio `..` y pulsando `<CR>`.

También se puede abrir el explorador con `:edit {path to dir}`.

El símbolo `.` representa el directorio actual, por lo que ejecutando `:edit .` abre el explorador de ficheros en la raiz del proyecto.

`:Explore` tiene el mismo efecto que `:edit .`, pero puede ser comprimido como `:E`. `:Sexplore` y `:Vexplore` abren el explorador en una nueva ventana dividiendola horizontal o verticalmente.

### Consejo 44 - Guarda ficheros en directorios inexistentes

# Part 3 - Muévete más rápido

## Chapter 8 - Navega por dentro de los ficheros con *movimientos*

### Consejo 46 - Mantén tus dedos en la fila central del teclado

Vim está optimizado para quienes no miran el teclado (*touch typist*)

### Consejo 47 - Distigue entre líneas reales o líneas visuales

Vim distingue entre líneas reales y líneas visuales, que son aquellas líneas que no caben en pantalla y son partidas)

Los comandos `gj` y `gk` mueven el cursor arriba y abajo por líneas visuales. `0` mueve al primer carácter de la línea real, mientras que `g0` hace lo mismo con líneas visuales. `^` mueve el cursor al primer carácter *no vacío* de la línea real.

### Consejo 48 - Muévete por palabras

`ge` mueve el cursor al final de la palabra anterior.

Cada moviento de palabra, tiene su correspondiente con PALABRA, lo que incluye `W`, `B`, `E` y `gE`. La definicón de PALABRA es sencilla: consiste en una secuencia de carácteres no vacíos separados de espacios en blanco.

### Consejo 49 - Encontrar por carácter con `f`

### Consejo 50 - Busca para navegar

Las búsquedas no solo funcionan en el modo normal, también lo hacer en modo visual y en modo *espera de operador*

### Consejo 51 - Objetos textuales

Cada vez que veas `{motion}` como parte de la sintaxis de un comando, puedes usar también objetos textuales.

### Consejo 52 - Borra alrededor o cambia dentro

- `is` frase actual (*current sentence*)
- `as` frase actual mas un espacio adicional
- `ip` párrafo actual
- `ap` párrafo actual

Se puede decir que `d{motion}` trabaja bien con `aw`, `as` y `ap`, mientras que `c{motion}` lo hace con `iw` y similares.

### Consejo 53 - Marca el lugar donde estás

El comando `m{a-zA-Z}` marca la posición actual del cursor con la letra seleccionada. Las letras minúsculas son locales a un buffer individual, mientras que las mayúsculas son accesibles de forma global. `'{mark}` te lleva al marcador designado por la letra `mark`.

Vim usa algunos marcadores automáticos:

- `“` la posición antes del último salto en el fichero actual
- `‘.` posición del último cambio
- `‘^` última inserción
- `‘[` último cambio o copiado
- `‘]` final del último cambio o copiado
- `‘<` comienzo de la última selección visual
- `‘>` final de la última selección visual

### Consejo 54 - Salta entre parejas de paréntesis

El comando `%` es parte del plugin incorporado a Vim, *matchit*, el cual salta entre parejas de palabras clave. Por ejemplo, en HTML saltaría entre parejas de etiquetas, en Ruby entre inicio y final de bloque `class/end`, `def/end`,...

## Chapter 9 - Navega entre ficheros con saltos

### Consejo 55 - Muévete por la lista de saltos

Vim guarda tu localización antes y despues de hacer un salto, y puedes moverte por ellos con `<C-o>` y `<C-i>`.

### Consejo 56 - Muévete por la lista de cambios

Vim guarda tu localización antes y despues de hacer un cambio. Puedes ver su contenido con `:changes`.

Con los comandos `g;` y `g,` puedes moverte por ellos. Para volver al último sitio donde estuviste en modo inserción, entrando en dicho modo, usa `gi`.

### Consejo 57 - Salta al fichero que tienes bajo el cursor

Vim trata los nombres de los ficheros del documento como hipervínculos. Si está bien configurado, `gf` abrirá el fichero cuyo nombre está debajo del cursor.

La opción `suffixesadd` te permite especificar una o más extensiones que Vim intentará encontrar con el comando `gf`. `gf` busca en cada uno de los directorios que se encuentren en la variable `path`.

### Consejo 58 - Muévete entre ficheros con marcas globales

Intenta crear el hábito de crear una marca global antes de usar ningún comando que interactúe con la lista *quickfix*, los búfferes o la lista de argumentos.

# Part 4 - Registros

## Chapter 10 - Copia y pega

### Consejo 59 - Borra, copia y pega usando el registro sin nombre

El comando `diw` no solo borra la palabra, también la copia en el registro sin nombre (*unnamed*).

¿Cómo puedes borrar contenido sin modificar el contenido de dicho registro? Existe un registro especial, llamado el *agujero negro*, porque de él, nada retorna. Al registro agujero negro se accede con `_`, por ejemplo `"_d{motion}` realiza un borrado de verdad.

### Consejo 60 - Domina los registros

Puedes especificar qué registros quieres usar prefijando el comando con `"{register}`. Si no se especifica ninguno, se usa el registro sin nombre.

Vim también tiene comandos Ex para borrar, copiar y pegar. Podemos cortar la línea actual en el registro `c` con el comando `:delete c`.

El comando `y{motion}` no solo copia el texto en el registro sin nombre, sino que lo copia también en el registro de pegado (*yank register*), al cual se accede con `0`. Este registro no es modificado por los comandos `x`, `s`, `c{motion}` o `d{motion}`.

Cuando nombramos un registro con minúsculas, el contenido se reemplaza, mientras que si lo nombramos con mayúsculas, el contenido se añade.

Cuando copies o peges contenido fuera de Vim, debes utilizar el registro del portapapeles, accesible mediante `+`. Por ejemplo, para pegar el contenido del portapapeles en Vim usa `"+p` o `<C-r>+` si estás en modo inserción.

- `"=`: el registro de expresiones
- `"%`: nombre del fichero actual
- `"#`: nombre del fichero alternativo
- `".`: último texto insertado
- `":`: último comando Ex
- `"/`: último patrón de búsqueda

### Consejo 61 - Reemplaza una selección visual con el contenido de un registro

Usa el comando `p` en el modo visual para reemplazar la selección con el contenido del registro que desees.

### Consejo 62 - Pega desde un registro

`gp` y `gP` pegan el contenido de un registro, pero en lugar de dejar el cursor al inicio del contenido pegado, lo mueven al final del mismo.

### Consejo 63 - Interactúa con el portapapeles del sistema

## Chapter 11 Macros

### Consejo 64 -   Record and Execute a Macro

### Consejo 65 -   Normalize, Strike, Abort

- Normalize the Cursor Position
- Strike Your Target with a Repeatable Motion
- Abort When a Motion Fails
- If a motion fails while a macro is executing, then Vim aborts the rest of the macro.

### Consejo 66 -   Play Back with a Count

### Consejo 67 -   Repeat a Change on Contiguous Lines

To execute macro in parallel, select lines with `VG` and then execute the macro with `:normal @q`

### Consejo 68 -   Append Commands to a Macro

If we type `qa`, then Vim will record our keystrokes, saving them into register `a` by overwriting the existing contents of that register. If we type `qA`, then Vim will record our keystrokes, appending them to the existing contents of register `a`.

### Consejo 69 -   Act Upon a Collection of Files

The `:argdo` command allows us to execute an Ex command once for each buffer in the argument list. `:argdo normal @a` will run the macro saved on register `a`

If we want to make it act upon multiple buffers, we could append a final step that advances to the next buffer in the list with `:next`

Another useful command is `:wnext` which is equivalent to running `:write` followed by `:next`. If you are executing a macro in series across several files in the argument list, you may prefer to use this.

### Consejo 70 -   Evaluate an Iterator to Number Items in a List

Using the `let` keyword, we can create a variable called `i` and assign it a value of `0`. We can insert the value stored in variable `i` just by running `<C-r>=i<CR>` in Insert mode.

### Consejo 71 -   Edit the Contents of a Macro

the `~` command, which toggles the case of the letter under the cursor

The registers that we use for recording macros are the very same with which the yank and put operations interact. So if we want to make changes to the macro saved in register `a`, we simply have to paste it into the document. Now we can edit the macro as plain text. So we can yank it from the document back into a register: `"ay$`

## Chapter 12 Matching Patterns and Literals

### Consejo 72 -   Tune the Case Sensitivity of Search Patterns

We can make Vim’s search patterns case insensitive by enabling the `ignorecase` setting.

We can override Vim’s default case sensitivity using the `\c` and `\C` items. Lowercase `\c` causes the search pattern to ignore case, while the uppercase `\C` item forces case sensitivity

When enabled, `smartcase` has the effect of canceling out the `ignorecase` setting any time that we include an uppercase character in our search pattern.

### Consejo 73 -   Use the \v Pattern Switch for Regex Searches

the `\v` pattern switch. This enables very magic search, where all characters assume a special meaning, with the exception of `_`, uppercase and lowercase letters, and the digits `0` through `9`

### Consejo 74 -   Use the \V Literal Switch for Verbatim Searches

Using the `verynomagic` literal switch, we can cancel out most of the special meanings attached to characters such as `.`, `*`, and `?`.

### Consejo 75 -   Use Parentheses to Capture Submatches

When specifying a pattern, we can capture submatches and then reference them elsewhere. Anything that matches inside of parentheses is automatically assigned to a temporary silo. We can reference the captured text as `\1`. The `\0` item always refers to the entire match

The `<` and `>` symbols match word boundaries, the `\_s` item matches whitespace or a line break

### Consejo 76 -   Stake the Boundaries of a Word

In very magic searches, these are represented by the `<` and `>` symbols. So if we amended our search to `/\v<the> <CR>`, otherwise, we would select text such as `their`, `these`, `tthey`,...

`\w` matches word characters, including letters, numbers, and the `_` symbol, while `\W` matches everything except for word characters.

### Consejo 77 -   Stake the Boundaries of a Match

The boundaries of a match normally correspond to the start and end of a pattern. But we can use the `\zs` and `\ze` items to crop the match, making it a subset of the entire pattern

### Consejo 78 -   Escape Problem Characters

## Chapter 13 Search

### Consejo 79 -   Meet the Search Command

If we execute a search without providing a pattern, Vim will just reuse the pattern from the previous search

### Consejo 80 -   Highlight Search Matches

### Consejo 81 -   Preview the First Match Before Execution

`<C-r><C-w>` autocompletes the search field using the remainder of the current preview match.

### Consejo 82 -   Count the Matches for the Current Pattern

`:%s///gn`

### Consejo 83 -   Offset the Cursor to the End of a Search Match

Here, we search for `/lang/e <CR>`, which places the cursor at the end of the search match,

### Consejo 84 -   Operate on a Complete Search Match

Here’s the trick: `gU //e <CR>`. We’re using `//e <CR>` as a motion, which reaches from the start to the end of the search match.

My favorite solution is the textobj-lastpat plugin, by Kana Natsuno, which adds an `i/` text object for operating on search matches. Using this, we can make the same change as before just by running `gUi/`.

### Consejo 85 -   Create Complex Patterns by Iterating upon Search History

Press `q/` to summon the command-line window. This acts more or less like a regular Vim buffer, but it’s prepopulated with our search history, one item per line. We can use the full power of Vim’s modal editing to amend the last pattern.

### Consejo 86 -   Search for the Current Visual Selection

You can either paste this into your vimrc file directly or install the *visual star search* plugin.

## Chapter 14 Substitution

### Consejo 87 -   Meet the Substitute Command

- `g` flag makes the substitute command act globally, causing it to change all matches within a line rather than just changing the first one.
- `c` flag gives us the opportunity to confirm or reject each change.
- `n` flag suppresses the usual substitute behavior, causing the command to report the number of occurrences
- `&` flag simply tells Vim to reuse the same flags from the previous substitute command.
- `\={Vim script}` token is very powerful. It allows us to execute code and use the result as our replacement {string}.

### Consejo 88 -   Find and Replace Every Match in a File

### Consejo 89 -   Eyeball Each Substitution

The `c` flag causes Vim to show us each match and ask “Replace with copy?” We can then say `y` to perform the change or `n` to skip it.

### Consejo 90 -   Reuse the Last Search Pattern

### Consejo 91 -   Replace with the Contents of a Register

Pass by value: we can insert the contents of a register by typing `<C-r>{register}`. Pass by reference: `:%s//\=@0/g`

In the replacement field, the `\=` item tells Vim to evaluate a Vim script expression. In Vim script, we can reference the contents of a register as `@{register}`.

We create a record in our command history that reads `:%s//\=@a/g`. It can do very different things, depending on the contents of the `/` and `a` register. You might love it or you might hate it. But either way, it’s a pretty neat trick!

### Consejo 92 -   Repeat the Previous Substitute Command

We can repeat the command across the entire file just by pressing `g&`, which is equivalent to running the following: `:%s//~/&``

Making `&` trigger the `:&&` command is more useful. These mappings fix the `&` command in Normal mode and create a Visual mode equivalent: 

    nnoremap & :&&<CR>
    xnoremap & :&&<CR>

### Consejo 93 -   Rearrange CSV Fields Using Submatches

### Consejo 94 -   Perform Arithmetic on the Replacement

### Consejo 95 -   Swap Two or More Words

### Consejo 96 -   Find and Replace Across Multiple Files

Running `:args **/*.txt` loads all files from the current project into the argument list. Then when we run `:argdo %s//Practical/ge`, Vim proceeds to execute the substitute command in every one of those files.

To perform a project-wide search, we’ll reach for the `:vimgrep` command

    :vimgrep {pattern} {files pattern}
    :vimgrep /<C-r>// **/*.txt

Each match returned by vimgrep is recorded in the quickfix list

With [vim-quargs plugin](https://github.com/nelstrom/vim-qargs), we can run `:Qargs`, and it will populate the argument list with each of the files named in the quickfix list.

## Chapter 15 Global Commands

### Consejo 97 -   Meet the Global Command

The `:global` command allows us to run an Ex command on each line that matches a particular pattern.

### Consejo 98 -   Delete Lines Containing a Pattern

Delete Matching Lines with `:g/{regular expression}/d`

Keep Only Matching Lines with ‘:v/{regular expression}/d’

### Consejo 99 -   Collect TODO Items in a Register

First we’ll need to clear it by running qaq. Now we can go ahead and yank the TODO comments into the register: `:g/TODO/yank A`

### Consejo 100 -   Alphabetize the Properties of Each Rule in a CSS File

Suppose that we want to sort the properties of each rule into alphabetical order. We could do so using Vim’s built-in `:sort` command

## Chapter 16 Index and Navigate Source Code with ctags

### Consejo 101 -   Meet ctags

Mozilla runs a project called Doctor JS which includes a `jsctags` program. `jsctags` produces output in the same format as ctags, so it works seamlessly with Vim.

### Consejo 102 -   Configure Vim to Work with ctags

Creating a mapping for it: `:nnoremap <f5> :!ctags -R<CR>`

Automatically execute ctags each time a file is saved with `:autocmd BufWritePost * call system("ctags -R")`

Automatically execute ctags with version control hooks: [Effortless Ctags with Git, by Tim Pope](http://tbaggery.com/2011/08/08/effortless-ctags-with-git.html)

### Consejo 103 -   Navigate Keyword Definitions with Vim’s Tag Navigation Commands

Pressing `<C-]>` makes our cursor jump from the keyword under the cursor to the definition. The `<C-t>` command acts as the back button for our tag history. But if it has multiple matches, then the `g<C-]>` command presents us with a list of choices from the tag match list. These Ex commands can accept a regular expression when used in the form `:tag /{pattern}` or `:tjump /{pattern}`

## Chapter 17 Compile Code and Navigate Errors with the Quickfix List

### Consejo 104 -   Compile Code Without Leaving Vim

From inside Vim, we can now run the `:make` command. Instead of just echoing the output from make, Vim parses each line, extracting the filename, line number, and error message. For each warning, Vim creates a record in the quickfix list.

### Consejo 105 -   Browse the Quickfix List

- `:cnext` jump to next item
- `:cprev` jump to previous item
- `:cfirst` jump to first item
- `:clast` jump to last item
- `:cnfile` jump to first item in next file
- `:cpfile` jump to last item in previous file
- `:cc` N jump to   nth item
- `:copen` open the quickfix window
- `:cclose` close the quickfix window  

The location list has equivalents for all of these commands, each beginning with `:l`, such as `:lnext`, `:lprev`, and so on.

For every command that populates the quickfix list, there’s a variant that places the results in a location list instead. While `:make`, `:grep`, and `:vimgrep` use the quickfix list, `:lmake`, `:lgrep`, and `:lvimgrep` use the location list.

There can be only one quickfix list, but we can create as many location lists as we want.

Any commands that interact with a location list (`:lnext`, `:lprev`, and so on) will act on the list that is bound to the currently active window.

### Consejo 106 -   Recall Results from a Previous Quickfix List

We can recall an older version of the quickfix list (Vim holds onto the last ten lists) by running the `:colder` command. To revert from an old quickfix list back to a newer one, we run `:cnewer`

### Consejo 107 -   Customize the External Compiler

The `makeprg` setting allows us to specify the program that will be called when we run `:make`

The `errorformat` setting allows us to teach Vim how to parse the output generated by running `:make`. This `errorformat` string is not something we would want to commit to memory. Instead, we can save it to a file and then activate it with the `:compiler` command

## Chapter 18 Search Project-Wide with grep, vimgrep, and Others

### Consejo 108 -   Call grep Without Leaving Vim

### Consejo 109 -   Customize the grep Program

Two settings: `grepprg` and `grepformat`.

### Consejo 110 -   Grep with Vim’s Internal Search Engine

    :vim[grep][!] /{pattern}/[g][j] {file}

We can compose a regular expression by searching in the current file. When we’re satisfied that it matches where it should, we execute `:vimgrep` using the exact same pattern.

## Chapter 19 Dial X for Autocompletion

### Consejo 111 -   Meet Vim’s Keyword Autocompletion

- `<C-n>` Generic keywords
- `<C-x><C-n>` Current buffer keywords
- `<C-x><C-i>` Included file keywords
- `<C-x><C-]>` tags file keywords
- `<C-x><C-k>` Dictionary lookup
- `<C-x><C-l>` Whole line completion
- `<C-x><C-f>` Filename completion
- `<C-x><C-o>` Omni-completion  

### Consejo 112 -   Work with the Autocomplete Pop-Up Menu

- <C-n> Use the next match from the word list (  next match)
- <C-p> Use the previous match from the word list (  previous match)
- <Down> Select the next match from the word list
- <Up> Select the previous match from the word list
- <C-y> Accept the currently selected match (  yes)
- <C-e> Revert to the originally typed text (  exit from autocompletion)
- <C-h> (and <BS>) Delete one character from current match
- <C-l> Add one character from current match
- {char} Stop completion and insert   {char}

### Consejo 113 -   Understand the Source of Keywords

Vim understands the C way of including files, but it can be taught to follow the corresponding directives in other languages by tweaking the `include` setting (see `include`

### Consejo 114 -   Autocomplete Words from the Dictionary

The easiest way to do this is by running `:set spell` to enable Vim’s spell checker. All of the words in the spelling dictionary become available through the `<C-x><C-k>` command.

### Consejo 115 -   Autocomplete Entire Lines

The beauty of line-wise autocompletion is that we don’t have to know the location of the line we’re duplicating. We need to know only that it exists.

### Consejo 116 -   Autocomplete Filenames

Filename autocompletion is triggered by the `<C-x><C-f>` command. Just like in the shell, `cd -` switches to the previous working directory

### Consejo 117 -   Autocomplete with Context Awareness

Omni-completion is Vim’s answer to intellisense.

## Chapter 20 Find and Fix Typos with Vim’s Spell Checker

### Consejo 118 -   Spell Check Your Work

We can jump backward and forward between flagged words with the `[s` and `]s` commands

we can ask Vim for a list of suggested corrections by invoking the `z=` command.

- `]s` Jump to next spelling error
- `[s` Jump to previous spelling error
- `z=` Suggest corrections for current word
- `zg` Add current word to spell file
- `zw` Remove current word from spell file
- `zug` Revert `zg` or `zw` command for current word

### Consejo 119 -   Use Alternate Spelling Dictionaries

We can change this by tweaking the `spelllang` option. This isn’t a global setting; `spelllang` is always local to the buffer.

### Consejo 120 -   Add Words to the Spell File

### Consejo 121 -   Fix Spelling Errors from Insert Mode

Alternatively, we could fix the error from Insert mode using the `<C-x>s` command,

## Chapter 21 Now What?

Apply Customizations to Certain Types of Files

    if has("autocmd")
      filetype on
      autocmd FileType ruby setlocal ts=2 sts=2 sw=2 et
      autocmd FileType javascript setlocal ts=4 sts=4 sw=4 noet 

We can have more than one autocommand listening for the same event.

Instead of declaring our JavaScript preferences in the vimrc using autocommands, we could place them in a file called ~/.vim/after/ftplugin/javascript.vim:


