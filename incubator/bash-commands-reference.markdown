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

