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

> Los [buildpacks] son los encargados de transformar el código desplegado en un *slug*, el cual puede ser ejecutado en un *dyno*.

Y después de toda esa jerga de Heroku, en cristiano quiere decir algo así: los *buildpacks* son un conjunto de herramientas que convierten y empaquetan tu código de forma que puedan ser ejecutados por la infraestructura de Heroku.

Heroku proporciona buildpacks por defecto: Java, Python, PHP, JavaScript,... Pero afortunadamente, también existen para Elixir y Phoenix, aunque no están mantenidos por Heroku.

Primero, debemos añadir el buildpack para Phoenix, conocido como [Phoenix static buildpack]:

    $ heroku buildpacks:set https://github.com/gjaldon/phoenix-static-buildpack
    Buildpack set. Next release on dry-anchorage-96713 will use https://github.com/gjaldon/phoenix-static-buildpack.
    Run git push heroku master to create a new release using this buildpack.

Después, añadimos el [buildpack de Elixir], configurándolo en primera posición:

    $ heroku buildpacks:add --index 1 https://github.com/HashNuke/heroku-buildpack-elixir
    Buildpack added. Next release on dry-anchorage-96713 will use:
      1. https://github.com/HashNuke/heroku-buildpack-elixir
      2. https://github.com/gjaldon/phoenix-static-buildpack
    Run git push heroku master to create a new release using these buildpacks.

## Ultimando los detalles del despliegue

Si intentamos realizar ahora el despliegue, obtendremos un error:

    $ git push heroku master
    [ ... ]
    remote: -----> Fetching app dependencies with mix
    remote:     ** (Code.LoadError) could not load [...]/config/prod.secret.exs
    [ ... ]
    remote: ! Push rejected to dry-anchorage-96713.
    [ ... ]

Para poder desplegar, necesitamos subir el fichero `prod.secret.exs`. Pero ese fichero está ignorado en `.gitignore`, por lo que no será subido mediante el comando `git push heroku master`. Y está ignorado por una buena razón. Ese fichero suele contener información sensible.

Pero tiene solución. Debemos sustituir la información sensible por valores tomados de variables de entorno. Editamos `prod.secret.exs`, de forma que quede parecido a:

    use Mix.Config

    # In this file, we keep production configuration that
    # you likely want to automate and keep it away from
    # your version control system.
    #
    # You should document the content of this
    # file or create a script for recreating it, since it's
    # kept out of version control and might be hard to recover
    # or recreate for your teammates (or you later on).
    config :rchavarria_deploys_phoenix_heroku, RchavarriaDeploysPhoenixHeroku.Endpoint,
      secret_key_base: System.get_env("SECRET_KEY_BASE")

    # Configure your database
    config :rchavarria_deploys_phoenix_heroku, RchavarriaDeploysPhoenixHeroku.Repo,
      adapter: Ecto.Adapters.Postgres,
      username: System.get_env("DATABASE_USERNAME"),
      password: System.get_env("DATABASE_PASSWORD"),
      database: "rchavarria_deploys_phoenix_heroku_prod",
      pool_size: 20

También debemos editar `.gitignore`, para dejar de ignorar `prod.secret.exs`.

No olvides hacer commit de estos cambios:

    $ git add .
    $ git commit -m "Incluir prod.secret.exs, sustituyendo secretos por variables de entorno"

## Desplegando

Ahora sí, ya podemos desplegar.

El despliegue no debería dar ningún problema, porque aunque no hemos creado ninguna variable de entorno, la aplicación básica de Phoenix no accede a la base de datos, por lo que la configuración de `prod.secret.exs` no debería tener ningún efecto todavía.

    $ git push heroku master
    remote: -----> Elixir app detected
    remote: -----> Installing Erlang 18.3 (changed)
    remote: -----> Installing Elixir v1.3.4 (changed)
    remote: -----> Compiling
    remote: Generated rchavarria_deploys_phoenix_heroku app
    remote:        Installing Node 6.9.2...
    remote: -----> Building dependencies
    remote: -----> Finalizing build
    remote: -----> Launching...
    remote:        https://dry-anchorage-96713.herokuapp.com/ deployed to Heroku
    remote: Verifying deploy... done.
    To https://git.heroku.com/dry-anchorage-96713.git

Y se puede ver la aplicación accediendo a [https://dry-anchorage-96713.herokuapp.com/] (si es que todavía existe como aplicación Heroku).

## Completando la configuración

Tarde o temprano, vamos a necesitar que nuestra aplicación acceda a la base de datos. Por lo que tendremos que configurar nuestras variables de entorno. Para ello, son necesarios dos pasos:

1. Configurarlas y exportarlas en Heroku (documentación sobre [variables de configuración de Heroku])

    $ heroku config:set SECRET_KEY_BASE=<y aquí mi secreto>
    $ heroku config:set SOME_VAR=<el valor para esta variable>

2. Editar (o crear) `elixir_buildpack.config` en la raíz del proyecto. Aquí deberemos configurar qué variables queremos exportar. Cuidado, porque estos valores sobreescriben los exportados por los buildpacks, por lo que deberemos incluir aquellas que incluyan los buildpacks de Elixir y Phoenix. Un ejemplo de `elixir_buildpack.config` podría ser tan sencillo como:

    configu_vars_to_export=(DATABASE_URL SECRET_KEY_BASE)

## Agradecimientos

Todo el mérito de esta información no es mío, es gracias a [Wendy Smoak], autora del post sobre el que se basa este, [HashNuke], autor del buildpack para Elixir; [gjaldon], autor del buildpack para Phoenix; y otros que ayudaron a Wendy con sus dudas.

[Heroku]: http://heroku.com/
[Wendy Smoak]: http://wsmoak.net/about.html
[el framework Phoenix]: http://www.phoenixframework.org/
[Deploying a Phoenix app to Heroku]: http://wsmoak.net/2015/07/05/phoenix-on-heroku.html
[Creative Commons CC-BY-NC]: http://creativecommons.org/licenses/by-nc/3.0/
[buildpacks]: https://devcenter.heroku.com/articles/buildpacks
[Phoenix static buildpack]: https://github.com/gjaldon/heroku-buildpack-phoenix-static
[buildpack de Elixir]: https://github.com/HashNuke/heroku-buildpack-elixir
[variables de configuración de Heroku]: https://devcenter.heroku.com/articles/config-vars
[HashNuke]: http://hashnuke.com/
[gjaldon]: http://gabrieljaldon.com/

