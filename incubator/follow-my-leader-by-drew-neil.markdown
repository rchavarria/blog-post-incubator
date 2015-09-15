Estas notas podrían ir en el post de aprendizaje de Vim, aunque ya está siendo muy largo, bueno, no lo sé, echarle un vistazo a ver si encaja, y echar un vistazo a otros post sobre Vim a ver dónde encaja mejor

# Follow my leader, by Drew Neil

Notas tomadas de la charla [Follow my leader](https://vimeo.com/85343734) de Drew Neil

- `let mapleader = "1"` para mapear `,` como tecla `<leader>` en vim
- `nnoremap <leader><space> :noh<cr>` hace algo, pero no sé el qué. A buscar

- la tecla `<leader>` te permite crear mapeos personalizados, es donde los usuarios pueden crear sus mapeos sin interferir con Vim

- en lugar de usar `leader`, algunos plugins, como los que escribe [tpope] siguen otro patrón. hay teclas que son *operadores*, por ejemplo la **d** para borrar, o la **y** para copiar. a estos operadores le puede seguir el mismo operador o una movimiento. teclas que producen un movmiento son **j** para ir hacia abajo, **$** para ir al final de la línea, ... Pero, qué pasa si despues de unoperador pulsamos una tecla de *no movimiento*? NO pasa nada. Y ahí están las combinaciones de teclas dsiponibles para tus plugins.

- en la imagen de la cheat sheet the vim, los naranjas son operadores, los verdes movimientos y los amarillos no se qué

- unimpaired.vim plugin añade mapeos como `con` para habilitar/deshabilitar los nuḿeros de línea, o `cos` para habilitar/desh. spell checking. Son `c` + `o` + otras teclas

- también hay disponibles combinaciones como operador + operador : `d` + `c`

- los *text objects* (`i` y `a`) tamibén tienen vacantes.

- los *namespaced mappings* también tienen vacantes. por ejemplo, `g` es como un prefijo para muchos mapeos. `z` es otro, y `[` y `]` son más

- `:help g` te muestra todos los mapeos que siguen a `g`. te puede servir para ver huecos donde poner tus mapeos

- useless commands, hay algunos comandos que no usa nadie. sobreescríbelo. por ejemplo, `g` + `s`. Qué hace ese comando?

- sobreescribir, sobrecargar comandos que ya existen, vamos, ampliar los existetnes

- 

