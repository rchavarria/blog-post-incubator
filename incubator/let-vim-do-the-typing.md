# (Julio 2015) [Let Vim do the typing](https://www.youtube.com/watch?v=3TX3kV3TICU), by George Brocklehurst

- `"a` + `p`: pega lo que hay en el registro `a`
- ¿por qué no funciona `CTRL + r` para insertar de un registro?, creo que es `CTRL + r` + `<letra del registro>`
- `CTRL + a`, en *insert mode*, pega el último texto insertado
- `CTRL + p`, `CTRL + SHIFT + p`, `CTRL + n`, para autocompletar palabras en los documentos abiertos de Vim
- con un fichero CTAGS, si escribo el nombre de una clase y presiono `CTRL + }`, Vim me lleva a la declaración de esa clase
- con un fichero CTAGS, con `CTRL + x` entra en una especie de *completion mode*
- Después de un `CTRL + }`, puedes volver a navegar hacia atrás con `CTRL + o`
- `CTRL + x` seguido de `CTRL + f` entra en el modo autocompletar nombres de ficheros
- con `CTRL + x` seguido de `CTRL + p` puedes ir autocompletando palabras de una frase. Cada vez que pulsas los dos, puedes ir autocompletando una palabra
- con `CTRL + x` seguido de `CTRL + n` lo mismo pero en el otro sentido
- con `CTRL + x` seguido de `CTRL + l` se autocompletan líneas. Si sigues con `CTRL + x` -> `CTRL + l` te va autocompletando siguientes líneas
- con `CTRL + x` -> `CTRL + o`, qué tal si te puede autocompletar métodos en tu lenguaje de programación. no necesita plugin
- `:set complete` muestra tu configuración de autocompletado. el valor por defecto que muestra es: `.,w,b,u,t,i,kspell`. `.` del buffer actual, `w` de las ventanas abiertas, `b` de los buffers abiertos, `u` de los buffers no activos, `t` de los ficheros CTAGS, `i` de los includes/requires, `kspell` en los diccionarios cuando tengas activado el chequeo de ortografía (`:set spell`)
- [repo de george](https://georgebrock.github.io/talks/vim-completion)
