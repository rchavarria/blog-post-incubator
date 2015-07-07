ALGUNOS LINKS E IDEAS PARA INCLUIR EN MI POST SOBRE VIM

# [Mastering the Vim language], Chris Toomey

- prefer text objects frente a movimientos (`iw` frente a `w`), hacen que los comandos sean más repetibles, ya que seleccionan mejor. el movimiento `w` sólo selecciona la palabra si el cursor está al inicio de la misma
- [repeat.vim] or plugin repeating, visit the website
- relative number (:set relativenumber, :set norelativenumber), para ver el número de líneas relativas respecto a la que está el cursor

### some plugins

- surround plugin: 
  - `ds"` : delete surrounding double quotes
  - `cs"'` : change surrounding double quotes with single quotes
  - and a few more, such as `cst<text>` to change the surrounding tag in HTML
- commentary plugin: parece mucho más potente que el que proporciona comandos `gcc` y demás. éste proporciona `cm<motion>`, por ejemplo: `cml` (comenta línea), `cm4j` (commenta 4 líneas hacia abajo)
- replace with register plugin. con el comando `gr<motion>`, por ejemplo, si tengo copiada una palabra, puedo hacer `griw` para *go replace inner word*
- sort-motion plugin. con el comando `gs<motion>` lo que hace es ordenar líneas alfabéticamente (para imports, requires,...)
- system-copy plugin, to copy to the system clipboard

### custom text objects

- indent: `cmii`, `cmni``
- entire: `cmae` (comment all entire, comments all document)
- line: 

[Mastering the Vim language]: https://www.youtube.com/watch?v=wlR5gYd6um0
