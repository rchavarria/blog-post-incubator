---
layout: post
title: "Practical Vim"
date: 2016-07-17 16:49
author: Ruben Chavarria
comments: true
categories: 
- personal
- book reviews
- vim
published: true
footer: false
sidebar: true
---

###### de Drew Neil

### Por qué lo he leído

{% img left https://raw.githubusercontent.com/rchavarria/blog-post-incubator/master/published-book-notes/img/practical-vim.jpg %}

Hace un tiempo decidí que quería [aprender a utilizar Vim]. Entre los muchos
recursos para aprender se encontraba este libro, pero encontré más prácticos
una serie de videos. Pero más adelante, escuchando el podcast [Giant Robots],
hablaron de este libro, y cuando recibes varias señales, quiere decir algo.

<!-- more -->

### De qué trata el libro

El libro no es un manual desde cero. Tampoco es un manual avanzado. Es un
conjunto de trucos, de sugerencias, que trata de explicar y convencer al lector
de la filosofía y bondades del editor. Entre estos trucos encontrarás muchos
que te sean de utilidad, y otros tantos tan extraños que ni te molestarás en
entenderlos. Pero lo más importante es que describe una *forma de pensar en
Vim*. A la hora de editar ficheros de texto no hay una única forma de hacer las
cosas, ni tampoco una forma superior a otras alternativas, pero en Vim sí que
hay una filosofía, una idea de atacar cada edición. Este libro te sumerge en
ella.

### Conclusiones y valoración

El libro es una maravilla. Está lleno de trucos. Muchos de ellos los conocía, y
otros ni siquiera sabía que existían. En cambio, otros, después de llevar un
tiempo usando Vim, tenía una ligera sospecha de que se podrían hacer, pero no
había invertido el tiempo en averiguar cómo.

Si tienes ganas de incarle el diente a un editor que sobrevive al paso del
tiempo, échale un vistazo al libro.

Debería echar un vistazo al proyecto de Mozilla [Doctor JS], que contiene la
herramienta `jsctags`, para generar ficheros ctags de proyectos JavaScript.

### Frases que me gustaría recordar

> La fórmula del punto: una pulsación de tecla para mover, una pulsación de
> tecla para ejecutar la edición

> La estrategia óptima de edición es hacer que tanto el cambio como el
> movimiento sean repetibles

> Podemos hacer que el comando deshacer opere en palabras, frases o párrafos
> enteros solamente haciendo un uso corrrecto de la tecla `Esc`

> La combinación de operadores con movimientos forman una especie de gramática.
> Aprender nuevos movimientos y operadores is como aprender el vocabulario de
> Vim. Si seguimos las reglas sencillas de la gramática, podremos expresar más
> y mejores ideas según vaya creciendo nuestro vocabulario

> Una buena forma de trabajar con macros sería: normalizar la posición del
> cursor, llegar hasta el objetivo con un movimiento repetible, hacer que la
> macro aborte cuando el movimiento falle y no encuentre el objetivo

> La sintaxis para definir un rango en los Ex commands es muy flexible. Se
> pueden mezclar números de línea, marcas y patrones de búsqueda. Y se puede
> aplicar un offset a cada uno de ellos

> Intenta crear el hábito de crear una marca global (`m{capital letter}`) antes
> de usar cualquier comando que interacciones con la lista de arreglos rápidos,
> lista de buffers o lista de argumentos

> Para editar una macro grabada en el registro `q`, simplemente podemos pegar
> el contenido de dicho registro con `"qy`, editar la línea y modificar el
> registro `q` con `"qy$`

### Qué he aprendido

Hay toda una serie de nuevos comandos, combinaciones de ellos y herramientas
que todavía no conocía o que he encontrado muy útiles:

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

- [Notas tomadas sobre Practical Vim], y en [inglés] también
- Debería echar un vistazo al proyecto de Mozilla [Doctor JS], que contiene la
  herramienta `jsctags`, para generar ficheros ctags de proyectos JavaScript.

[Notas tomadas sobre Practical Vim]: https://github.com/rchavarria/blog-post-incubator/blob/master/published-book-notes/practical-vim-by-drew-neil.markdown
[inglés]: https://github.com/rchavarria/blog-post-incubator/blob/master/published-book-notes/practical-vim-by-drew-neil.en.markdown
[Doctor JS]: https://github.com/mozilla/doctorjs
[aprender a utilizar Vim]: http://rchavarria.github.io/blog/2014/10/11/aprendiendo-vim/
[Giant Robots]: http://giantrobots.fm/

