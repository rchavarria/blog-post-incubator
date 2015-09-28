# Charla técnica: Follow my leader

Estas notas podrían encajar perfectamente en el post que voy actualizando
regularmente [Aprendiendo Vim], pero creo que esta la charla de Drew Neail se
desmarca ya un poco del proceso de aprendizaje. En esta charla no se busca
enseñar nuevos comandos de Vim, si no que se trata más de un tema cultural
acerca del editor. Drew trata de animar a la gente a que busque nuevas
combinaciones de teclas que se conviertan en nuevos comandos y de esta forma
hacer Vim más potente todavía.

<!-- more -->

## Notas tomadas de la charla [Follow my leader]

<iframe src="https://player.vimeo.com/video/85343734"
        width="500"
        height="281"
        frameborder="0"
        webkitallowfullscreen mozallowfullscreen allowfullscreen>
</iframe>
<p>
  <a href="https://vimeo.com/85343734">Follow my leader, by Drew Neil</a> from
  <a href="https://vimeo.com/vimlondon">Vim London</a> on
  <a href="https://vimeo.com">Vimeo</a>.
</p>

- `let mapleader = ","` para mapear `,` como tecla `<leader>` en Vim
- `nnoremap <leader><space> :noh<cr>` : remapea la secuencia de teclas
`<leader><space>` para que se ejecute el comando `:nohlsearch`, que desactiva
el resaltado de términos de búsqueda.
- la tecla `<leader>` te permite crear mapeos personalizados, es donde los
usuarios pueden crear sus mapeos sin interferir con Vim
- en lugar de usar `leader`, algunos plugins, como los que escribe [Tim Pope]
siguen otro patrón. hay teclas que son *operadores*, por ejemplo la **d**
para borrar, o la **y** para copiar. a estos operadores le puede seguir el
mismo operador o una movimiento. teclas que producen un movmiento son **j**
para ir hacia abajo, **$** para ir al final de la línea, ... Pero, qué pasa si
despues de unoperador pulsamos una tecla de *no movimiento*? NO pasa nada. Y
ahí están las combinaciones de teclas dsiponibles para tus plugins.
- en la imagen de la cheat sheet the vim, los naranjas son operadores, los
verdes movimientos y los amarillos no se qué
- unimpaired.vim plugin añade mapeos como `con` para habilitar/deshabilitar los
nuḿeros de línea, o `cos` para habilitar/desh. spell checking. Son `c` + `o` +
otras teclas
- también hay disponibles combinaciones como operador + operador : `d` + `c`
- los *text objects* (`i` y `a`) tamibén tienen vacantes.
- los *namespaced mappings* también tienen vacantes. por ejemplo, `g` es como
un prefijo para muchos mapeos. `z` es otro, y `[` y `]` son más
- `:help g` te muestra todos los mapeos que siguen a `g`. te puede servir para
ver huecos donde poner tus mapeos
- useless commands, hay algunos comandos que no usa nadie. sobreescríbelo. por
ejemplo, `g` + `s`. ¿Qué hace ese comando?
- sobreescribir, sobrecargar comandos que ya existen, vamos, ampliar los
existentes

[Follow my leader]: https://vimeo.com/85343734
[Aprendiendo Vim]: /blog/2014/10/11/aprendiendo-vim/
[Tim Pope]: http://tpo.pe/

