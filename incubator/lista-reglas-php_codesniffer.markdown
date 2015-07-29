# Lista de reglas de PHP_CodeSniffer

¿Has conducido alguna vez en el extranjero? Si has ido de acompañanate, ¿has
prestado atención a la carretera?. Es todo tan distinto, pero a la vez es
prácticamente igual a conducir en tu propio país (quitando alguna excepción
como Inglaterra o Japón, que lo hacen por la izquierda). Seguro que encuentras
los mismos elementos: semáforos, cruces, rotondas, carreteras de doble sentido,
autovías,... y **normas**. Las normas de circulación no son las mismas en todos
los lugares, pero podríamos encontrar algunas normas básicas que sí lo son.
Esas normas básicas son las que nos permiten conducir en otros países con una
cierta confianza.

Cuando escribimos código dentro de un equipo de trabajo ocurre algo similar.
Cada uno tenemos nuestro esilo a la hora de escribir código: nombrado de
variables, espaciado, paréntesis, indentación,... Si tuviéramos total libertad
para desarrollar como nos apeteciera, el trabajo en equipo sería mucho más
duro, ya que tendríamos que *entender* el estilo de cada uno de nuestros
compañeros. Por curiosidad, ¿no te ha pasado nunca que has leído una clase e
inmediatamente sabes quién la ha escrito? Para evitar esta sobrecarga conviene
tener ciertas normas, unas **reglas** básicas de cómo escribir código, para
que todos los miembros del equipo escriban código acorde a un cierto *estándar*.

Aquí es donde aparece [PHP_CodeSniffer], una herramienta de análisis estático
de código PHP que genera informes sobre qué partes del código de nuestro equipo
violan las reglas del estándar que previamente definió el equipo.

<!-- more -->

## Reglas

Cada una de esas reglas puede hacer referencia a aspectos muy distintos de
nuestro código: indentación con espacios o tabuladores, apertura de llaves (`{`)
en la misma línea o en la siguiente, sintaxis a la hora de manipular arrays
(`array()` o `[]`),... Las reglas a utilizar deben ser consensuadas en el equipo
y suelen estar definidas en un fichero llamado `ruleset.xml` que se pasará como
parámetro a la herramienta `phpcs`. Aquí nos estamos centrando en código PHP,
pero también se puede hacer análisis de código JavaScript y CSS.

A la hora de poder definir un conjunto de reglas a utilizar dentro del equipo,
sería conveniente tener una lista de todas ellas y una breve descripción de cada
una para facilitar la discusión y la toma de decisiones. Lamentablemente, la
documentation de la herramienta no proporciona esa lista, pero existe algunas
posibilidades que nos pueden facilitar el trabajo.

### Opción `-s`

El comando `phpcs` se puede ejecutar con la opción `-s`, con la cual la
herramienta indica qué regla (o *sniff*) estamos incumpliendo en cada
violación que aparece en el informe de la herramienta. El siguiente comando
ejecuta `phpcs` mostrando el progreso (`-p`), analizando solo archivos con la
extensión `.php` y por supuesto que nos muestre las reglas que no se cumplen
(`-s`), como por ejemplo `Generic.Commenting.Todo.TaskFound`.

```bash
$ phpcs -p -s --extensions=php <directory or file>

...E...E....W.....W..E.............W........................  60 / 723 (8%)
.......................W.................................... 120 / 723 (17%)
.............................W..W....E..................E..E 180 / 723 (25%)

----------------------------------------------------------------------
 44 | ERROR   | Function's cyclomatic complexity (21) exceeds allowed
    |         | maximum of 20
    |         | (Generic.Metrics.CyclomaticComplexity.MaxExceeded)
----------------------------------------------------------------------
 60 | ERROR | [x] Line indented incorrectly; expected at least 2 spaces,
    |       |     found 0 (Generic.WhiteSpace.ScopeIndent.Incorrect)
----------------------------------------------------------------------
 59 | WARNING | The method parameter $connectorGuid is never used
    |         | (Generic.CodeAnalysis.UnusedFunctionParameter.Found)
----------------------------------------------------------------------
 61 | WARNING | Comment refers to a TODO task "Limits number of
    |         | information got in log off mode"
    |         | (Generic.Commenting.Todo.TaskFound)
----------------------------------------------------------------------

... output has been truncated
Time: 2 mins, 9.46 secs; Memory: 25.5Mb
```

### Código fuente

Al final, la documentación más fiable, más actualizada, más detallada y más de
todo es el código fuente. Puede asustar un poco tener que mirar el código fuente,
pero [el código de PHP_CodeSniffer] es código abierto y se puede navegar en
Github de forma sencilla. Además, no tendrás que consultarlo de arriba a abajo,
aquí encontrarás unas pistas de donde encontrar las reglas.

El código está organizado en varios directorios, en `CodeSniffer/Standards`
encontraremos el código fuente que nos interesa. Aquí, cada subdirectorio
contiene las reglas definidas por cada estándar: Generic, PEAR, PSR1, PSR2,...
Dentro de cada uno de estos directorios, encontramos un fichero llamado
`ruleset.xml`, donde podemos encontrar las reglas importadas de aquellos
estándares que las definen. Por ejemplo, en el fichero `PSR2/ruleset.xml`
podemos encontrar:

```xml
<?xml version="1.0"?>
<ruleset name="PSR2">
 <description>The PSR-2 coding standard.</description>
 <arg name="tab-width" value="4"/>

 <!-- Include the whole PSR-1 standard -->
 <rule ref="PSR1"/>

 <!-- The soft limit on line length MUST be 120 characters;
      automated style checkers MUST warn but MUST NOT error at the soft limit. -->
 <rule ref="Generic.Files.LineLength">
  <properties>
   <property name="lineLimit" value="120"/>
   <property name="absoluteLineLimit" value="0"/>
  </properties>
 </rule>

 <!-- ... -->

 <!-- Visibility MUST be declared on all methods. -->
 <rule ref="Squiz.Scope.MethodScope"/>

 <!-- Method arguments with default values MUST go at the end of the argument list. -->
 <rule ref="PEAR.Functions.ValidDefaultValue"/>

 <!-- ... -->

</ruleset>
```

En este fichero podemos ver que se importan todas las reglas definidas en el
estándar *PSR1* con `<rule ref="PSR1">`. Y que se importan reglas individuales
de otros estándares, por ejemplo `<rule ref="Squiz.Scope.MethodScope"/>. O que
incluso se pueden pasar parámetros a algunas reglas, como se hace con
`Generic.Files.LineLengh`.

### Guía definitiva

Si con todo esto todavía no has dado con las reglas que quieres, o si necesitas
conocer alguna regla más en profundidad, podemos echar un vistazo a cómo se
generan las referencias de las reglas para poder incluirlas, excluirlas,
parametrizarlas,... en nuestro `ruleset.xml`.

Tomemos como ejemplo las reglas *Generic*, ya que son las más utilizadas, más
concretamente la regla `Generic.Files.LineLength`. Las reglas del estándar
*Generic* están definidas en el directorio: `CodeSniffer/Standards/Generic`.
Y dentro de él, en el directorio `Sniffs`. El siguiente token, `Files`, indica
un nuevo subdirectorio dentro de `Sniffs` con el mismo nombre. Y por último,
`LineLength`, indica una clase PHP con ese mismo nombre más el sufijo `Sniff`.

Así pues, para la regla `Generic.Files.LineLength`, encontraremos una clase PHP
en `CodeSniffer/Standards/Generic/Sniffs/Files/LineLengthSniff.php` [[[ ¿¿¿¿¿ SE PODRÍA CONSEGUIR ESTO CON FORMATO DE CÓDIGO PERO CON LETRA NEGRITA Y DEMÁS ????  ]]]]

Otros ejemplos podrían ser:

- `PEAR.Commenting.InlineComment`: clase `CodeSniffer/Standards/PEAR/Sniffs/Commenting/InlineCommentSniff.php`
- `PSR1.Classes.ClassDeclaration`: clase `CodeSniffer/Standards/PSR1/Sniffs/Classes/ClassDeclarationSniff.php`
- `Zend.Debug.CodeAnalyzer`: clase `CodeSniffer/Standards/Zend/Sniffs/Debug/CodeAnalyzerSniff.php`

Pero aún hay más. En el `ruleset.xml` de ejemplo, veíamos cómo se pasaban
parámetros a la regla `Generic.Files.LineLength`. Ahora ya conocemos la clase
PHP que cnotiene el código que ejecuta esa regla:
`CodeSniffer/Standards/Generic/Sniffs/Files/LineLengthSniff.php`. Dicha clase
tiene dos variables públicas: `lineLimit` y `absoluteLineLimit`. Que precisamente
son los parámetros que se pueden configurar. Así pues, variables públicas en
las clases `*Sniff` no son más que posibles parámetros a usar en el
`ruleset.xml` de nuestro proyecto.

### Referencias y enlaces relacionados

- Página de [PHP_CodeSniffer]
- [Mejora contínua y análisis estático de código] en este mismo blog
- [Documentación de las reglas de PHP_CodeSniffer] en Stack Overflow

[PHP_CodeSniffer]: https://github.com/squizlabs/PHP_CodeSniffer
[el código de PHP_CodeSniffer]: https://github.com/squizlabs/PHP_CodeSniffer
[Mejora contínua y análisis estático de código]: http://rchavarria.github.io/blog/2014/05/05/mejora-continua-y-analisis-estatico-de-codigo
[Documentación de las reglas de PHP_CodeSniffer]: http://stackoverflow.com/questions/16427207/php-codesniffer-rules-documentation

