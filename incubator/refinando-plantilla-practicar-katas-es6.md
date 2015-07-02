# Ejecutar tests de mocha con ES6

Me gusta resolver puzzles, pero no puzzles de miles de piezas, si no más bien el
tipo de puzzle en el que hay unas piezas de madera encajadas y hay que desencajarlas,
o en el que hay una cuerdecita con una bola y tienes que sacar la bola y volverla
a meter. Ese tipo de puzzles.

Creo que de ahí me viene también el gusto de resolver pequeños problemas de
programación. Me gusta programar. Me gusta aprender. Y qué mejor para aprender
que practicar. En el mundo de la programación existe un concepto al que llamamos
[kata] (el concepto ha sido copiado de las artes marciales), el cual significa
la realización de pequeños ejercicios focalizados en la solución a un pequeño
problema muy concreto. Así que me gusta realizar katas de vez en cuando en algún
lenguaje de programación para practicar.

<!-- more -->

Hace un tiempo publiqué un tutorial sobre [cómo crear un módulo NodeJS], el cual
me servía de base para realizar algunas de estas katas. En este artículo me
gustaría llevarlo un poco más allá. A ese proyecto, a esa plantilla, voy a
añadirle lo siguiente:

- [Babel]: voy a añadir un paso en la construcción del proyecto y ejecución de los
tests, voy a transpilar código JavaScript ECMAScript 6 a ECMAScript 5. Esto me
permite practicar con la nueva versión de JavaScript.
- [ESLint]: estoy convencido de que este tipo de herramientas ayudan en el día a
día en el desarrollo con JavaScript. Me ayudan a detectar errores tontos a la
hora de escribir mi código.
- [Travis CI]: todos los tests serán ejecutados en un servidor de integración
contínua, para eliminar para siempre la excusa de *En mi ordenador funciona*

## Babel

[Babel] es una herramienta para transformar código escrito en ECMAScript 6 en
código ECMAScript 5, es decir, para transformar código JavaScript de una versión
que todavía no está soportada completamente por los navegadores a una versión
que sí lo está.

Instalarlo es sencillísimo mediante `npm`:

    npm install --save-dev babel gulp-babel

Con este comando instalaremos la herramienta en sí, y un plugin para `gulp` que
nos permitirá usar Babel desde nuestro script gulp. Modificaremos este script
para que transforme nuestro código justo antes de ejecutar nuestros tests:

    gulp.task('test', function () {
        return gulp
            .src([ 'test/bootstrap.js', 'test/scripts/**/*.js' ])
            .pipe(mocha({
                reporter: 'spec',
                compilers: 'js:babel/register'  // tell mocha to compile with babel
            }));
    });

La parte diferente de otras configuraciones para lanzar los tests con mocha es
la parte donde configuramos mocha para que use Babel como compilador de código
JavaScript.

## ESLint

[ESLint] es una herramienta que analiza nuestro código JavaScript y nos avisa de
violaciones de reglas que tengamos configuradas. Estas reglas nos permiten
definir patrones para detectar posibles fallos en nuestro código así como forzar
a que todos los integrantes de nuestro equipo sigan el mismo estilo de programación.

También utilizaremos `nmp` para instalarlo, esta vez instalaremos solamente el
plugin de `gulp`, que como depende de ESLint directamente, éste se instalará 
automáticamente:

    npm install --save-dev gulp-eslint

Y podemos crear una nueva tarea en gulp para analizar nuestro código:

    gulp.task('eslint', function () {
        return gulp
            .src([ 'gulpfile.js', 'src/scripts/**/*.js', 'test/scripts/**/*.js' ])
            .pipe(eslint())
            .pipe(eslint.format())
            .pipe(eslint.failOnError());
    });

Ahora, si queremos analizar todo nuestro código antes de lanzar nuestros tests,
podemos hacer que la tarea `test` dependa de la nueva tarea `eslint`:

    gulp.task('test', [ 'eslint' ], function () {
        // ...
    }

## TravisCI

[Travis CI] es una herramienta de integración contínua. La herramienta recupera
nuestro código del repositorio de GitHub que le digamos y ejecuta todos los
tests.

Para ello debemos darnos de alta en la página. Podemos hacerlo con nuestra
cuenta de GitHub. Luego, podemos ir a nuestro perfil e indicar a Travis CI
qué repositorios debe *vigilar* para ejecutar los tests cada vez que hagamos
un push al repositorio.

Debemos indicar a Travis CI qué lenguaje y plataforma queremos testear, en
nuestro caso se trata de NodeJS. Como configuración, añadimos simplemente un
fichero llamado `.travis.yml` en el directorio raiz del proyecto con este
contenido:

    language: node_js
    node_js:
        - "0.12"

De esta forma, cuando hagamos un push a nuestro repositorio en GitHub, Travis CI
recuperará el código, instalará paquetes Node con `npm` y ejecutará el comando
`npm test`. 

Para que Travis CI lanze nuestros tests, debemos configurar la respuesta al
comando `npm test`. Para ello, modificaremos el fichero `package.json`:

    //...
    "scripts": {
        "test": "gulp test"
    },
    //...

[kata]: https://en.wikipedia.org/wiki/Kata_%28programming%29
[cómo crear un módulo NodeJS]: http://rchavarria.github.io/blog/2014/09/24/plantilla-para-modulos-nodejs
[Babel]: http://babeljs.io
[ESLint]: http://eslint.org
[Travis CI]: https://travis-ci.org

