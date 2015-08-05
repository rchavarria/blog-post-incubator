# Navegando el código fuente con Vim

- ¿qué son los tags?

## Instalar `ctags`

En Linux: `apt-get install exuberant-ctags`.
En Windows: descargar el binario desde la página del proyecto
[Exuberant Ctags][2]

## Generar fichero de tags

```bash
$ ctags -R .
```

## Usar el fichero generado en Vim

```
:set tags=/path/to/tags/file
```

## Navegar

`CTRL + ]`: en modo normal, te lleva a la definición del *tag* donde está el cursor. Con el teclado español, para mostrar el carácter `]` es necesario pulsar `AlgGr` + `]`, pero para ejecutar este comando de Vim no se debe pulsar `AltGr`, es suficiente con pulsar la tecla que contiene los carácteres `+`, `*` y `]`.
`CTRL + t`: en modo normal, te lleva de vuelta al punto antes de navegar al tag.
`CTRL + w` + `CTRL + ]`: en modo normal, divide la pantalla horizontalmente y abre el fichero donde se encuentra la definición del tag.
`:tag <tag name>` para ir directamente a la definición de una tag cualquiera
`:tnext` y `:tprevious` (`:tprev`) te llevan a la tag siguiente o anterior
`:ltag` carga las tags en la ventana de lista de localizaciones (como `:ls` cuando lista los búfferes abiertos)
`:lopen` abre dicha ventana

## Referencias y enlaces relacionados

- [Vim and Ctags][1]

[1]: http://andrewradev.com/2011/06/08/vim-and-ctags
[2]: http://ctags.sourceforge.net

