# Compilación de comandos de consola

Aquí me gustaría ir compilando comandos de consola (mayormente para Linux) útiles.
Podrán ser comandos de distintas herramientas, y contendrán una pequeña descripción
de lo que se pretende hacer con el comando.

## Bash - `find`

Buscar un texto en unos ficheros:

```bash
$ find . -name '*.php' | xargs grep <some-text>
$ find . -name '*.js' | xargs grep <some-text>
$ find . -name '*' | xargs grep <some-text>
$ find . -path '*/any-depth/*' -exec grep <some-text> {} +
```

## Bash - `grep`

## Bash - `tar`

Empaqueta un directorio en un fichero `.tar`, incluso permite comprimirlo en
formato gzip. También permite descomprimirlo.

```bash
$ tar -zvcf compressed-file.tar.gz /path/to/directory
$ tar -xvcf compressed-file-to-extract.tar.gz
```

Y como regla mnemotécnica:

<blockquote class="twitter-tweet" lang="es"><p lang="en" dir="ltr">how to remember tar flags 🎏&#10;&#10;tar -xzf 👈 eXtract Ze Files!&#10;tar -czf 👈 Compress Ze Files!</p>&mdash; Tess Rinearson (@_tessr) <a href="https://twitter.com/_tessr/status/626076327133577216">julio 28, 2015</a></blockquote>
<script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>

## Bash - `du`

*Disk usage*, informa del uso del disco, es decir, del tamaño que ocupan ficheros
o directorios en disco. La opción `-s` hace un resumen (**s**ummary) y la opción
`-h` lo formatea para **h**umanos.

```bash
$ du -sh /path/to/directory
```

## Git

Pasar al área de *stage* algunos cambios de un fichero en concreto (entra en un
modo interactivo):

```bash
$ git add -p <file>
```

Sacar del área de *stage* algunos cambios de un fichero, para evitar comitearlos
(entra en un modo interactivo):

```bash
$ git reset -p <file>
```

Cambia la plantilla que aparece en el editor al introducir un mensaje de commit:

```bash
$ git config --global commit.template /path/to/git-commit-template.txt
```

Borrar una rama del repositorio remoto y limpiar las referencias en local del
*remote*:

```bash
$ git push origin --delete <feature-branch>
$ git remote prune <remote-name>
```

Borrar una rama en local:

```bash
$ git branch -d <local-branch>
```

