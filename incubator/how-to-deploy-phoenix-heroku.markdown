# Cómo desplegar una aplicación Elixir/Phoenix en Heroku

[Heroku] es una plataforma donde los desarrolladores pueden desplegar sus aplicaciones (en principio de lado servidor) y hacerlas públicas de forma gratuita o por un pequeño precio. Yo he utilizado a veces este servicio para hacer pruebas con servidores en JavaScript (NodeJS) o PHP, pero también admite muchos otros lenguages de programación: Ruby, Java, Python, Go,...

<!-- imagen con los logos de Heroku, Elixir y Phoenix -->

No es ningún secreto que estoy tonteando con Elixir], y [el framework Phoenix] es el framework por referencia para crear aplicaciones web en Elixir. Pero ese no es un lenguaje soportado por Heroku, así que parecía un poco complejo poder hacer unas pruebas desplegando una aplicación Elixir/Phoenix en Heroku.

Por suerte, [Wendy Smoak] escribió un artículo hace un tiempo hablando de esto mismo: [Deploying a Phoenix app to Heroku]. Dicho artículo tiene licencia [Creative Commons CC-BY-NC]. Este post no es una traducción en sí, pero como está basado en él me parece justo y obligatorio respetarla. Así que este post está basado en el artículo [Deploying a Phoenix app to Heroku], de [Wendy Smoak], y también está licenciado bajo la [Creative Commons CC-BY-NC], digan lo que digan el resto de posts de este blog.

<!-- more -->

## Requisitos

Para poder llevar a cabo el despliegue, necesitamos todas estas herramientas. Yo lo he probado con estas versiones:

- Elixir, versión 1.3.1. El cuál, necesita Erlang/OTP, por ejemplo la versión 19
- Phoenix, versión 1.2.1
- Phoenix necesita de NodeJS, yo tengo instalada la versión 5.12.0; y también necesita (normalmente) de una base de datos, comúnmente, PostgreSQL, yo he utilizado la versión 9.5, que viene mi distribución Ubuntu
- Git, versión 2.7.4
- Heroku toolbelt, versión 3.43.14; Heroku CLI, versión 5.6.31; este post también asume que nos hemos dado de alta en Heroku y hemos configurado estas herramientas.

## Creando una aplicación Phoenix

Crear el esqueleto de una aplicación Phoenix es ridículamente sencillo, simplemente un comando:

    $ mix phoenix.new rchavarria_deploys_phoenix_heroku
    [ ... ]
    Fetch and install dependencies? [Yn] Y
    [ ... ]

Para poder llevar un control de lo que hacemos o dejamos de hacer, pondremos la aplicación bajo un control de versiones. Además, Heroku está pensado para funcionar con aplicación donde el control de versiones es `git`, así que...

    $ cd rchavarria_deploys_phoenix_heroku
    $ git init
    $ git add .
    $ git commit -m "Primera piedra de la aplicación Phoenix desplegada en Heroku"

Si queremos, podemos subir esta aplicación a GitHub u otro servicio que nos permita tener nuestras aplicación bajo `git`.

## Creando una aplicación Heroku

También es muy sencillo:

    $ heroku create
    Creating app... done, ⬢ dry-anchorage-96713
    https://dry-anchorage-96713.herokuapp.com/ | https://git.heroku.com/dry-anchorage-96713.git
    Git remote heroku added

También se puede indicar el nombre de nuestra app en el comando `heroku create`. Heroku nos ha dado un nombre aleatorio, y podremos acceder a ella a través de la URL [https://dry-anchorage-96713.herokuapp.com/].

Heroku habrá añadido un nuevo *remote* a nuestro repositorio de `git`:

    $ git remote -v
    heroku  https://git.heroku.com/dry-anchorage-96713.git (fetch)
    heroku  https://git.heroku.com/dry-anchorage-96713.git (push)

## Añadiendo *buildpacks* a la applicación Heroku

¿Qué es un buildpack, slug y un dino?

Cómo configurar el buildpack adecuado

Añadir otro buildpack, para Elixir, y que se ejecute antes que el buildpack de Phoenix

## Ultimando los detalles del despliegue

## Desplegando

## Completando la configuración

