# Practical Vim
## de Drew Neil

[![Practical Vim](img/practical-vim.jpg)](https://pragprog.com/book/dnvim/practical-vim)

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

## Chapter 11 - Macros

### Consejo 64 - Graba y ejecuta una macro

### Consejo 65 - Normalizar, alcanzar, abortar

- Normaliza la posición del cursor
- Alcanza a tu objetivo con un movimiento repetible
- Aborta cuando el movimiento falla
- Si un movimiento fall cuando una macro se está ejecutando, Vim aborta el resto de la macro

### Consejo 66 - Volver a ejecutar la macro con un contador

### Consejo 67 - Repetir una macro en líneas contínuas

Para ejecutar una macro en paralelo, selecciona las líneas con `VG` y luego ejecuta la macro con `:normal @q`

### Consejo 68 - Añade comandos a una macro

Si tecleamos `qa`, Vim guardará lo siguiente que tecleemos en el registro `a`, sobreescribiendo el contenido de dicho registro. Si tecleamos `qA`, Vim guardará lo que teclees, pero lo añadirá al contenido del registro `a`.

### Consejo 69 - Actuar sobre una colección de ficheros

El comando `:argdo` permite ejecutar un comando Ex una vez para cada buffer en la lista de argumentos. `:argdo normal @a` ejecutará la macro guardada en el registro `a`.

Si quieres hacer que actúe en varios búfferes, puedes añadir un paso final a la macro de forma que te avance al siguiente buffer, con `:next`.

Otro comando muy útil es `:wnext`, que es equivalente a la combinación de `:write` y `:next`. 

### Consejo 70 - Evalúa un iterador para crear el índice de una lista numerada

Usando la palabra reservada `let`, puedes crear una variable llamada `i` y asignarle el valor `0`, el cual podrás incrementar luego paso a paso. Puedes insertar el valor de la variable `i` escribiendo `<C-r>=i<CR>`

### Consejo 71 - Editar los contenidos de una macro

El comando `~` intercambia mayúsculas a minúsculas y viceversa.

Los registros donde se guardan las macros son los mismos registros que se pueden usar a la hora de copiar y pegar. Por lo tanto, si quieres editar la macro guardada en el registro `a`, simplemente tienes que copiar dicho registro en el documento con `"ap`. Edita la macro como si fuera un texto normal y corriente y actualiza el contenido del registro con `"ay$`

## Chapter 12 - Coincidiendo con patrones y literales

### Consejo 72 - Retoca la sensibilidad mayúsculas/minúsculas de los patrones de búsqueda

Con la opción `ignorecase` podemos hacer que Vim ignore mayúsculas y minúsculas

Puedes sobreescribir dicha opción con `\c` y `\C`, las cuales hace que Vim ignore o fuerce que coincidan mayúsculas con mayúsculas respectivamente.

Cuando está activada, la opción `smartcase` tiene el efecto de cancelar la opción `ignorecase` cuando usamos una mayúscula en el patrón de búsqueda.

### Consejo 73 - Usa el flag `\v` en los patrones de búsqueda

El flag `\v` habilita la búsqueda mágica, donde todos los carácteres toman un significado especial a excepción de `_`, letras y dígitos.

### Consejo 74 - Usa el flag `\V` para búsquedas literales

El flag *nada de magia* cancela la mayoría de los significados especiales a carácteres como `.`, `*` y `?`

### Consejo 75 - Usa paréntesis para capturar partes del patrón

Cuando especifiques un patrón, puedes capturar partes del patron y referenciarlos en otro lugar. Cada cosa que coincide con el interior de los paréntesis es asignado a un silo. Puedes hacer referencia a las capturas con `\1` o `\5`. `\0` hace referencia siempre a la coincidencia al completo.

Los símbolos `<` y `>` seleccionan los límites de las palabras, mientras que `\_s` selecciona espacios en blanco y saltos de línea.

### Consejo 76 - Fija los límites de una palabra

Si buscas la palabra `the`, puedes hacerlo con `/\v<the> <CR>`. De otro modo seleccionarás palabras como `their`, `these` o `tthey`. 

`\w` selecciona carácteres de una palabra (letras, números y `_`), mientras que `\W` selecciona todo menos dichos caracteres.

### Consejo 77 - Fija los límites de una coincidencia

Normalmente se corresponden con el inicio y el final de patrón, pero se pueden cambiar. Usa `\zs` y `\ze` para recortar la coincidencia, haciéndola un subconjunto del patrón completo

### Consejo 78 - Escapa carácteres problemáticos

## Chapter 13 - Búsquedas

### Consejo 79 - Conoce el comando búsqueda

Si ejecutas una búsqueda sin proporcionar un patŕon, Vim usará el último patrón usado

### Consejo 80 - Subraya coincidencias

### Consejo 81 - Previsualiza la primera coincidencia de la búsqueda

`<C-r><C-w>` autocompleta el campo de búsqueda usando el resto de la previsualización de la ocurrencia

### Consejo 82 - Cuenta las coincidencias del patrón actual

`:%s///gn`

### Consejo 83 - Lleva el cursor hasta el final de la coincidencia

Si buscas con `/lang/e`, el flag `e` situará el cursor al final de la coincidencia de búsqueda

### Consejo 84 - Opera en la coincidencia completa de búsqueda

Este es el truco, `gU//e`. Se usa `//e` como movimiento, el cual te lleva desde el inicio hasta el final de la coincidencia de búsqueda.

La solución favorita del autor es el plugin `textobj-lastpat`, de Kana Natsuno, que añade el objeto textual `i/` para operar en coincidencias de búsqueda. Así pues, un comando equivalente al anterior sería `gUi/`.

### Consejo 85 - Crea patrones complejos iterando por el historial de búsquedas

Pulsa `q/` para abrir al ventana de búsquedas. Actúa más o menos como un buffer normal de Vim, pero está relleno con el historial de búsquedas, una por línea. Podemos utilizar todo el poder de Vim para corregir el último patrón.

### Consejo 86 - Busca la actual selección visual

Echa un vistazo al plugin *visual star search*

## Chapter 14 - Sustitución

### Consejo 87 - Conoce el comando sustitución

- `g`: hace que el comando actúe globalmente, cambiando todas las coincidencias en una fila, no solo la primera
- `c`: pide confirmación antes de sustituir el valor
- `n`: sirve para contar las ocurrencias
- `&`: indica a Vim volver a usar los flags utilizados en la última sustitución
- `\={Vim script}`: es muy poderoso, permite ejecutar un código y utilizar el resultado como el texto del reemplazo

### Consejo 88 - Busca y reemplaza todas las ocurrencias en un fichero

### Consejo 89 - Supervisa cada sustitución

Recuerda el flag `c`

### Consejo 90 - Reutiliza el último patrón de búsqueda

### Consejo 91 - Reemplaza con los contenidos de un registro

Paso por valor, insertando el contenido directamente mediante `<C-r>{register}`. Paso por referencia: `:%s//\=@0/g`

En el campo de reemplazo, `\=` indica a Vim que evalúe una expresión Vim. En vimscript, puedes referenciar los contenidos de un registro con `@{register}`

Crea un registro en el histórico de comandos que sea `:%s//\=@a/g`. Podrás hacer muy distintas cosas, dependiendo de los contenidos de los registros `/` y `a`. Lo puede amar, o lo puedes odiar, pero no puedes negar que no es un truco genial.

### Consejo 92 - Repite el comando de repetición anterior

Puedes repetir el comando a lo largo del fichero con `g&`, que es equivalente a ejecutar `:%s//~/&`

Puedes crear un mapeo muy interesante, mapeando `&` a `:&&`, tanto en modo normal como en el visual:

    nnoremap & :&&<CR>
    xnoremap & :&&<CR>

### Consejo 93 - Reordena campos CSV usado sub-coincidencias

### Consejo 94 - Realiza cálculos en el reemplazo

### Consejo 95 - Intercambia dos o más palabras

### Consejo 96 - Busca y reemplaza a lo largo de múltiples ficheros

Ejecutando `:args **/*.txt` carga todos los ficheros de texto del proyecto en la lista de argumentos. Si ejecutamos `:argdo %s//Practical/ge`, Vim ejecutará el comando de sustitución en cada uno de los ficheros

Para realizar una búsqueda, podemos utilizar `:vimgrep`

    :vimgrep {pattern} {files pattern}
    :vimgrep /<C-r>// **/*.txt

Cada coincidencia queda grabada en la lista quickfix

Con el plugin [vim-quargs plugin](https://github.com/nelstrom/vim-qargs), puedes ejecutar `:Qargs`, y rellenará la lista de argumentos con los elementos de la lista quickfix

## Chapter 15 - Comandos globales

### Consejo 97 - Conoce el comando global

`:global` te permite ejecutar un comando Ex por cada línea que coincide con un patrón en particular

### Consejo 98 - Borrar líneas que contienen un patrón

Borrar las líneas coincidentes con `:g/{regular expression}/d`

Mantener las líneas coincidentes con `:v/{regular expression}/d`

### Consejo 99 - Collecciona elementos de TODO en un fichero

Limpia primero el registro con `qaq`. Copia todos los comentarios `TODO` en un registro `:g/TODO/yank A`

### Consejo 100 - Ordena alfabéticamente las propiedades de cada clase en un fichero CSS

Echa un vistazo a `:sort`

## Chapter 16 - Indexa y navega tu código fuente con `ctags`

### Consejo 101 - Conoce `ctags`

Mozilla tiene un proyecto, llamado DoctorJS que incluye el programa `jsctags`, el cual produce una salida con el mismo formato que `ctags`, por lo que funciona perfectamente con Vim

### Consejo 102 - Configura Vim para funcionar con `ctags`

Crea un mapeo para ello: `:nnoremap <f5> :!ctags -R<CR>`

Ejecuta `ctags` automáticamente cada vez que un fichero se guarda: `:autocmd BufWritePost * call system("ctags -R")`

Ejecuta `ctags` mediante un *hook* al control de versiones: [Effortless Ctags with Git, by Tim Pope](http://tbaggery.com/2011/08/08/effortless-ctags-with-git.html)

### Consejo 103 - Navega por palabras reservadas

Con `<C-]>`, Vim salta a la definición de la palabra que se haya bajo el cursor. `<C-t>` actúa como el botón de retorno, volviendo atrás en la historia `ctags`. Si hay varias ocurrencias, `g<C-]>` presenta una lista de posibilidades tomada de la lista de tags coincidentes. Estos comandos Ex aceptan expresiones regulares si se usan de la forma `:tag /{pattern}` o `:tjump /{pattern}`

## Chapter 17 Compila el código y navega los errores con la lista quickfix

### Consejo 104 - Compila sin abandonar Vim

Desde dentro de Vim, puedes ejecutar `:make`. En lugar de mostrar la salida de `make`, Vim parsea cada línea, extrae el nombre del fichero, la línea y el mensaje de error. Para cada advertencia, Vim crea un registro en la lista quickfix.

### Consejo 105 - Navega la lista quickfix

- `:cnext` salta al siguiente elemento
- `:cprev` salta al elemento anterior
- `:cfirst` salta al primer elemento
- `:clast` al último
- `:cnfile` salta al primer elemento del siguiente fichero
- `:cpfile` al último
- `:cc N` salta al elemento número `N`
- `:copen` abre la ventana de la lista de quickfix
- `:cclose` cierra dicha ventana

La lista de localización tiene los equivalentes a estos comandos, pero empezando por `:l`, por ejemplo, `:lnext`, `:lprev`,...

Para cada comando que rellena la lista quickfix, existe una variante que lleva los resultados a una lista de localización. `:make`, `:grep` y `:vimgrep` usan la lista quickfix; `:lmake`, `:lgrep` y `:lvimgrep` usan la lista de localización.

Solo puede haber una lista quickfix, pero puedes tener tantas de localización como quieras

Cualquier comando que manipule la lista de localización, actuará solamente a lo que aparezca en la ventana activa actual.

### Consejo 106 - Recuerda resultados de una lista quickfix anterior

Puedes recordar una versión anterior de una lista quickfix con `:colder`. Para volver a la más nueva, `:cnewer`

### Consejo 107 - Personaliza el compilador externo

La opción `makeprg` te permite especificar qué programa se ejecutará al llamar `:make`

La opción `errorformat` permite enseñar a Vim a parsear la salida del programa anterior. Es recomendable no almacenar esto en memoria, si no en disco. Crea un fichero con la configuración y vuélvelo a activar con `:compiler`

## Chapter 18 - Busca en todo el proyecto con `grep`, `vimgrep` y otros

### Consejo 108 - Ejecuta `grep` sin dejar Vim

### Consejo 109 - Personaliza el programa `grep`

Muy parecido a la lista quickfix: `grepprg` and `grepformat`.

### Consejo 110 - Usa `grep` con los patrones de búsqueda de Vim

    :vim[grep][!] /{pattern}/[g][j] {file}

Puedes componer una expresión regular buscando en el fichero actual. Cuando estés de acuerdo en las coincidencias que vas a tener, puedes ejecutar `vimgrep` en cualquier momento

## Chapter 19 - Autocompletado

### Consejo 111 - Conoce el autocompletado

- `<C-n>`, `<C-p>` palabras en general
- `<C-x><C-n>` palabras de búffer actual
- `<C-x><C-i>` palabras dentro de los ficheros importados
- `<C-x><C-]>` palabras en el fichero `ctags`
- `<C-x><C-k>` búsqueda en el diccionario
- `<C-x><C-l>` trata de hacer coincidir la línea al completo
- `<C-x><C-f>` nombres de ficheros
- `<C-x><C-o>` Omni-completion  

### Consejo 112 - Trabaja con el menú contextual de autocompletado

- <C-n> usa la siguiente coincidencia (**n**ext match) para autocompletar
- <C-p> usa la anterior coincidencia (**p**previous match) para autocompletar
- <Down> selecciona la siguiente coincidencia
- <Up> selecciona la coincidencia anterior
- <C-y> acepta la selección actual dentro del menú (**y**es)
- <C-e> vuelta otra vez al texto tecleado (exit from autocompletion)
- <C-h> (y <BS>) borra un carácter de la coincidencia actual
- <C-l> añade un carácter siguiendo la coincidencia actual
- {char} para el autompletado e inserta {char}

### Consejo 113 - Conoce la fuente de las palabras reservadas

Vim entiende la forma de C de incluir ficheros, pero puede ser configurado para otros lenguajes personalizando la opción `include`

### Consejo 114 - Autocompleta palabras desde el diccionario

La forma más fácil es con `:set spell`, para habilitar el corrector de Vim. Todas las palabras del diccionario están disponibles con `<C-x><C-k>`

### Consejo 115 - Autocompleta líneas enteras

Lo mejor del autocompletado de línea es que no tienes que saber la localizacióne exacta de la línea, simplemente debes saber que existe

### Consejo 116 - Autocompleta nombres de ficheros

Comando `<C-x><C-f>`

`cd -` nos devuelve al directorio de trabajo anterior, igual que la shell

### Consejo 117 - Autocompleta con noción del contexto

Omni-completion es la respuesta a Intellisense

## Chapter 20 - Busca y corrige errores ortográficos

### Consejo 118 - Comprueba la ortografiá de tu trabajo

Puedes navegar palabras con errores ortográficos con `[s` o `]s`.

Puedes pedirle a Vim una lista de posibles opciones con `z=`

- `]s` salta al siguiente error
- `[s` salta al anterior error
- `z=` muestra correcciones para la palabra bajo el cursor
- `zg` añade la palabra actual al diccionario
- `zw` la borra
- `zug` revierte `zg` or `zw` para la palabra actual

### Consejo 119 - Usa diccionarios alternativos

Se hace a través de la opción `spelllang`. `spelllang` es siempre local al buffer

### Consejo 120 - Añade palabras al diccionario

### Consejo 121 - Corrige errores desde el modo de inerción

`<C-x>s`

## Chapter 21 - Sabías que?

Aplica personalizaciones a cierto tipo de ficheros

    if has("autocmd")
      filetype on
      autocmd FileType ruby setlocal ts=2 sts=2 sw=2 et
      autocmd FileType javascript setlocal ts=4 sts=4 sw=4 noet 

Puede haber varios autocomandos escuchando el mismo evento.

En lugar de declarar nuestras preferencias JavaScript en `vimrc` , podemos guardarlas en `~/.vim/after/ftplugin/javascript.vim`


