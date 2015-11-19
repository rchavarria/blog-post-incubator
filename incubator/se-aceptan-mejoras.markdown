# Se aceptan mejoras

Existe una cosa maravillosa en el mundo de open source, y es que personas de las que ni siquiera sabes que existen, usan tu trabajo, lo mejoran con su trabajo, y te lo donan a tí para que otra gente se beneficie del trabajo de ambos.

Imagina que tienes una librería y tienes una base de usuarios. Ningún software se adapta a todos sus usuarios, así que lo más seguro es que los usuarios de tu librería encuentren algún detalle que no funciona perfecto para sus necesidades. ¿No sería incríble que tus propios usuarios mejorarn la librería y te dieran su trabajo así como les das tú el tuyo? Pues eso es lo que pasa precisamente con el open source.

Y algo parecido pasa cuando contribuyes a algún proyecto open source. Tus contribuciones son usadas por los usuarios del proyecto. Y algunos de ellos proponen nuevas mejoras al proyecto. Quizá algunas de estas mejoras sean sobre el trabajo que tú has realizado. Gente que ni conoces está aportando su experiencia para mejorar tu trabajo. Hay que ser muy tonto para no aprovechar esta oportunidad para aprender.

<!-- more -->

- a continuación se describirá el proceso para aceptar mejoras en un proyecto publicado en Github, usando git como herraienta cnotrol versions
- comandos git

```
foo bar
...
```

## Limpiar tu espacio de trabajo

git co master
git fetch origin
git reset --hard

- ir explicando cada comando

## Descargar las mejoras

git fetch origin refs/pull/#pr/head
git co -b pr-branch-name FETCH_HEAD
git rebase: cuidado con los conflictos, daría apra varios posts

- ir explicando cada comando

## Comprobar las mejoras

- ejecuta tus tests, comprueba las differencas
- inserta pantallazo de un diff de github
- bla bla

## Incorporar los cambios

git merge --no-ff pr-branch-name
git push origin master

- inserta imagen de mergeado

## Referencias

- [Best way to merge a pull request](http://blog.differential.com/best-way-to-merge-a-github-pull-request/)
- [Git for 4 and up](https://www.youtube.com/watch?v=1ffBJ4sVUb4)
- [Better commit messages](http://tbaggery.com/2008/04/19/a-note-about-git-commit-messages.html)
- [Do your commits suck?](https://www.youtube.com/watch?v=8YjSty6bfog)


