# Navegando el código fuente con Vim

- últimamente se están popularizando muchos editores de código (Atom, Brakets, Sublime Text,...)
- pero mucho antes que ellos existieron al menos otros dos: Emacs y Vim
- no se muy bien la razón, quizá fue por el placer de aprender, me decidí a aprender a utilizar [Vim][3]
- ya llevo un tiempo [aprendiendo Vim][4], aunque el aprendizaje va despacio

- hay muchas cosas que me encantan de Vim, pero echo de menos algunas cosas que me dan ciertos IDEs: refactorizaciones sencillas, búsqueda en múltiples ficheros, integración con otras herramientas,... 
- en este post voy a contar cómo se puede solucionar le problema de la navegación de código

<!-- more -->

- Vim lo soluciona con un fichero de *tags*
- Dentro de un lenguaje de programación, un tag es simplemente el nombre de una fución, método, clase,... 
- Cada tag va acompañado de una referencia para localizar dónde aparece, básicamente fichero y número de línea
- con la herramienta [ctags][2] es posible generar un fichero que sirve a Vim a conocer todas las tags de nuestro proyecto, y mediante comandos de Vim, podemos movernos entre las tags

## Uso de la herramienta `ctags`

- Lo primero es instalar la herramienta. Para Linux es tan sencillo como ejecutar un simple comando. Para otros sistemas operativos es también bastante sencillo, pero se recomienda visitar la página del proyecto [Exuberant Ctags][2].

```bash
$ sudo apt-get install exuberant-ctags
```

- el siguiente paso es generar el fichero de tags de nuestro proyecto:

```bash
$ cd /home/rchavarria/my-super-interesting-project
$ ctags -R .
```

- y por último, debemos indicar a Vim dónde está el fichero de tags que queremos usar. Para ello, una vez el editor está abierto, introducir el comando:

```
:set tags=/path/to/tags/file
```

- para facilitar las cosas y no tener que recordar cómo cargar el fichero de tags manualmente, es recomendable poner el comando anterior en el fichero `.vimrc`, de forma que al abrir Vim cargue siempre el fichero de tags

## Navegar

Ahora, veamos cómo podemos movernos entre tags. Estos movimientos permiten movernos dentro del mismo fichero, entre ficheros abiertos, o incluso ficheros que no estén abiertos (pero están referenciados en el fichero de tags claro).

- `CTRL + ]`: en modo normal, te lleva a la definición del *tag* donde está el cursor. Con el teclado español, para mostrar el carácter `]` es necesario pulsar `AlgGr` + `]`, pero para ejecutar este comando de Vim no se debe pulsar `AltGr`, es suficiente con pulsar la tecla que contiene los carácteres `+`, `*` y `]`.
- `CTRL + t`: en modo normal, te lleva de vuelta al punto antes de navegar al tag.
- `CTRL + w` + `CTRL + ]`: en modo normal, divide la pantalla horizontalmente y abre el fichero donde se encuentra la definición del tag.
- `:tag <tag name>` para ir directamente a la definición de una tag cualquiera
- `:tnext` y `:tprevious` (`:tprev`) te llevan a la tag siguiente o anterior. hay quien recomienda mapear estos comandos a otra secuencia de carácteres, como por ejemplo: `]t` y `[t`.
- `:ltag` carga las tags en la ventana de lista de localizaciones (como `:ls` cuando lista los búfferes abiertos)
- `:lopen` abre dicha ventana

## Referencias y enlaces relacionados

- [Vim and Ctags][1]
- [Aprendiendo Vim][4], en este mismo blog

[1]: http://andrewradev.com/2011/06/08/vim-and-ctags
[2]: http://ctags.sourceforge.net
[3]: http://www.vim.org
[4]: /blog/2014/10/11/aprendiendo-vim

