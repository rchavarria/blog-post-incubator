# Se aceptan mejoras

- lo bueno del OSS es que ajenos pueden mejorar tu trabajo
- ¿no estaría bien que tuvieras una libreria, la gente la usara, la mejorara, y te lo dijera?
- algo parecido pasa cuando te conviertes en contributor de un OS project y te llegan mejoras de gente que ni conoces

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


