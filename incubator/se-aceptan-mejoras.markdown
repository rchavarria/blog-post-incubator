# Se aceptan mejoras

Existe una cosa maravillosa en el mundo de open source, y es que personas de las que ni siquiera sabes que existen, usan tu trabajo, lo mejoran con su trabajo, y te lo donan a tí para que otra gente se beneficie del trabajo de ambos.

Imagina que tienes una librería y tienes una base de usuarios. Ningún software se adapta a todos sus usuarios, así que lo más seguro es que los usuarios de tu librería encuentren algún detalle que no funciona perfecto para sus necesidades. ¿No sería incríble que tus propios usuarios mejorarn la librería y te dieran su trabajo así como les das tú el tuyo? Pues eso es lo que pasa precisamente con el open source.

Y algo parecido pasa cuando contribuyes a algún proyecto open source. Tus contribuciones son usadas por los usuarios del proyecto. Y algunos de ellos proponen nuevas mejoras al proyecto. Quizá algunas de estas mejoras sean sobre el trabajo que tú has realizado. Gente que ni conoces está aportando su experiencia para mejorar tu trabajo. Hay que ser muy tonto para no aprovechar esta oportunidad para aprender.

<!-- more -->

Este artículo describe el proceso a seguir para aceptar mejoras en un proyecto publicado en [Github], donde [git] es usada como herramienta de control de versiones. Estas mejoras son propuestas por usuarios externos al proyecto a través de [Pull Requests] (o también PR). Github te ayuda a la hora de incorporar esas mejoras a tu proyecto, pero hacerlo así deja la historia de tu control de versiones hecha unos zorros (en [Best way to merge a pull request] lo cuentan más detalladamente).

Ésta es la secuencia de comandos mediante los cuales se incoroporarían los cambios propuestos en un Pull Request con número `pr-number` desde una rama creada por el autor llamada `user-working-branch`:

```
rchavarria@proyect$ git checkout master
rchavarria@proyect$ git fetch origin
rchavarria@proyect$ git reset --hard origin/master

rchavarria@proyect$ git fetch origin refs/pull/<pr-number>/head
rchavarria@proyect$ git checkout -b <user-working-branch> FETCH_HEAD
rchavarria@proyect$ git rebase master

rchavarria@proyect$ git checkout master
rchavarria@proyect$ git merge --no-ff <user-working-branch>
rchavarria@proyect$ git push origin master
```

## Limpiar el espacio de trabajo

```
rchavarria@proyect$ git checkout master
Already on 'master'
Your branch is up-to-date with 'origin/master'.
rchavarria@proyect$ git fetch origin
remote: Counting objects: 66, done.
remote: Compressing objects: 100% (43/43), done.
remote: Total 66 (delta 14), reused 6 (delta 6), pack-reused 17
Unpacking objects: 100% (66/66), done.
From https://github.com/exercism/xecmascript
   9b32d79..de450d0  master     -> origin/master
 * [new branch]      new-exercise-raindrops -> origin/new-exercise-raindrops
```

Con estos comandos simplemente se cambia a la rama `master` y se descargan los cambios que existan en el repositorio remoto (sin aplicar los cambios a ningún archivo todavía). En este caso, el repositorio es uno de Github. En el código anterior se puede ver cómo existe una nueva rama en remoto, `new-exercise-raindrops`, que se corresponde con el Pull Request que vamos a incorporar al repositorio.

```
rchavarria@proyect$ git reset --hard origin/master
HEAD is now at de450d0 Merge pull request #78 from rchavarria/new-exercise-roman-numerals
```

Este comando elimina cualquier cambio en local y lo sobreescribe exactamente con los cambios que ha tomado del repositorio remoto. De esta forma **se tiene en local exactamente lo mismo que en remoto**, y es un punto de partida seguro.

## Descargar las mejoras

Anteriormente git ha avisado de que hay una nueva rama, un nuevo Pull Request.

```
rchavarria@proyect$ git fetch origin refs/pull/80/head
From https://github.com/exercism/xecmascript
 * branch            refs/pull/80/head -> FETCH_HEAD
```

El anterior comando descarga los cambios contenido en el Pull Request con número `<pr-number>`, que podría ser por ejemplo el `80`.

```
rchavarria@proyect$ git checkout -b new-exercise-raindrops FETCH_HEAD
Switched to a new branch 'new-exercise-raindrops'
```

Así, se crea una nueva rama, llamada `new-exercise-raindrops` que contiene los cambios del Pull Request.

Y ahora llega un momento delicado. Se debe hacer que el commit por el que comienza la rama recién creada sea el último commit que existía en `master`. De esta forma se consigue que la historia del control de versiones sea la más legible. En este punto es posible que se produzcan conflictos. Ese es otro tema que daría para muchas explicaciones. Si se quiere profundizar, se puede echar un vistazo a [XXXX ENLACE SUPER INTERSANTE ACERCA DE GIT REBASE].

```
rchavarria@proyect$ git rebase master
Current branch new-exercise-raindrops is up to date.
```

Si no hay conflictos, perfecto, ya está.

## Comprobar las mejoras

Ahora es el momento de hacer comprobaciones:

- Se deberían ejecutar los tests del proyecto
- Chequear los cambios, comparándolos con versiones anteriores
- Comprobar que se siguen las reglas de estilo en el código
- En general, asegurarse de que el código a incorporar es un código con el que estamos contentos

En esta fase se pueden hacer nuevos cambios o pedir al programador que contribuye que realice algunos cambios por sí mismo y que actualize el Pull Request.

XXXXXXXXXXXXXXXXXXXXXXX inserta pantallazo de un diff de github xXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX

## Incorporar los cambios

Una vez está todo comprobado y se está de acuerdo con los cambios, ha llegado la hora de incorporar los cambios a la rama `master` para que finalmente formen parte del código del proyecto.

```
rchavarria@proyect$ git checkout master
Switched to branch 'master'
Your branch is up-to-date with 'origin/master'.
rchavarria@proyect$ git merge --no-ff new-exercise-raindrops
Merge made by the 'recursive' strategy.
 config.json                 |  3 ++-
 raindrops/example.js        | 17 +++++++++++++++++
 raindrops/gulpfile.js       | 42 ++++++++++++++++++++++++++++++++++++++++++
 raindrops/package.json      | 24 ++++++++++++++++++++++++
 raindrops/raindrops.spec.js | 38 ++++++++++++++++++++++++++++++++++++++
 5 files changed, 123 insertions(+), 1 deletion(-)
 create mode 100644 raindrops/example.js
 create mode 100644 raindrops/gulpfile.js
 create mode 100644 raindrops/package.json
 create mode 100644 raindrops/raindrops.spec.js
```

Los comandos cambian el espacio de trabajo a la rama `master` e incorporan los cambios a la misma. Se deberá proporcionar un mensaje para el commit que va a generar `git merge`. Un ejemplo sería:

```
Merge pull request #80 from matthewmorgan/new-exercise-raindrops

Closes #80
```

Donde `80` es el número del Pull Request, `matthewmorgan` es el nombre del programador que contribuye y `new-exercise-raindrops` es el nombre de la rama que le dió el programador y el que se ha utilizado para la incorporación de los cambios.

Finalmente, se suben los cambios al repositorio remoto y ...

```
rchavarria@proyect$ git push origin master
Username for 'https://github.com': rchavarria
Password for 'https://rchavarria@github.com': 
Counting objects: 1, done.
Writing objects: 100% (1/1), 273 bytes | 0 bytes/s, done.
Total 1 (delta 0), reused 0 (delta 0)
To https://github.com/exercism/xecmascript.git
   de450d0..eae366a  master -> master
```

... ¡magia!

XXXXXXXXXXXXXXXXXXXXXXXXX inserta imagen de mergeado   XXXXXXXXXXXXXXXXXXXXXXXXXXXXXX

## Referencias

- [Best way to merge a pull request](http://blog.differential.com/best-way-to-merge-a-github-pull-request/)
- [Git for 4 and up](https://www.youtube.com/watch?v=1ffBJ4sVUb4)
- [Better commit messages](http://tbaggery.com/2008/04/19/a-note-about-git-commit-messages.html)
- [Do your commits suck?](https://www.youtube.com/watch?v=8YjSty6bfog)


