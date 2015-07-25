# (Julio 2015) [My first Vim plugin](https://www.youtube.com/watch?v=lwD8G1P52Sk)

- `:set spell`: activa la corrección ortográfica
- `]s`: lleva el cursor al primer error ortográfico que encuentre
- `z=`: muestra un menú con las opciones para corregir el error ortográfico
- `1z=`: selecciona (sin abrir el menú) la primera opción de correción 
- `m<letra>`: establece un marcador en la posición donde está el cursor ahora mismo.
- `<backtic><backtic><letra>`: mueve el cursor hasta el marcador que diga `<letra>`
- `:normal! <comando>`: ejecuta tal cual el comando que le escribamos. Por
ejemplo, si escribimos `:normal! mm]s1z=<back-tick>m`, ejecuta lo siguiente:
establece un marcador en `m` (`mm`), va al primer error ortográfico (`]s`),
lo corrige con la primera opción (`1z=`), vuelve el cursor a la posición donde
estábamos (`<back-tick>m`)
- En un fichero de configuración de Vim:

```
nnoremap <leader>sp :normal! mm]s1z=`m<cr>
# no olvidar <cr> al final, es como pulsar <enter>
```

- Lo que hace es asignar la sequencia de comandos `<leader>sp` para que ejecute
el comando que hemos estado hablando. Y qué tecla es `<leader>`? Dice que
normalemente es `\`, pero que el la tiene mapeada a `<spacebar>`.
- Ahora, lo englobamos en una función:

```
function! FixLastSpellingError() {
    normal! mm]s1z=`m
}
nnoremap <leader>sp :call FixLastSpellingError
```

- `{` mueve el cursor al inicio del párrafo, `}` lo mueve al final
- con `kmmjdd{p<back-tick>m` podemos mover una línea arriba del todo del párrafo (al principio
de una lista, por ejemplo): sube una línea, pone un marcador, baja, borra la línea,
se mueve al principio del párrafo, pega y vuelve al marcador. 
- `yypVr=<cr>`: marca una línea como el primer título de Markdown: 
copia la línea, la pega debajo, se mueve debajo, selecciona
visualmente la línea completa, reemplaza todo con `=`.

**Plugins**
- quicklink: para visitar enlaces que tengas en un fichero Markdown
- text-obj-indent: son objectos de texto adicionales, como por ejemplo un nivel 
de indentación
- sort-motion: permite ordenar con comandos de movimiento: palabra, linea, párrafo,...
- tmux_nav y tmux_runner: para manejar sessiones de tmux desde Vim, abriendo
ventanas en Vim y enviando comandos a ellas
- 


