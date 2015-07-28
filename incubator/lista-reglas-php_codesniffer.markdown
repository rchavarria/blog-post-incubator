# Lista de reglas de PHP_CodeSniffer

- ¿has conducido alguna vez en el extranjero? o si has ido de acompañante, ¿has prestado atención a la carretera?
- es todo tan distinto. pero a la vez es prácticamente igual a conducir en tu propio país (quitando alguna excepción como Inglaterra o Japón, que conducen por la izquierda).
- seguro que encuentras los mismos elementos: semáforos, cruces, rotondas, carreteras de doble sentido, autovías, y **normas**.
- las normas de circulación no son las mismas en todos los lugares, pero podríamos encontrar algunas normas básicas que sí lo son
- esas normas básicas son las que nos permiten conducir en otros países con una cierta confianza

- escribiendo código dentro de nuestro equipo de trabajo ocurre algo similar
- cada uno tenemos nuestro estilo a la hora de escribir código: nombrar las variables, espaciado, paréntesis, indentación,...
- si tuviéramos total libertad para desarrollar como nos apeteciera, el trabajo en equipo sería mucho más duro
- por eso conviene tener unas ciertas normas, unas **reglas** básicas de cómo escribir código, para que todos los miembros del equipo escriban código acorde a un cierto *estándar*.

- Aquí es donde aparece [PHP_CodeSniffer], una herramienta de análisis estático de código PHP que genera informes sobre qué partes del código de nuestro equipo violan las reglas o el estándar que previamente definió el equipo

<!-- more -->

## Reglas

- cada una de esas reglas puede hacer referencia a aspectos muy distintos de nuestro código: indentación con espacios o tabuladores, apertua de llaves (`{`) en la misma línea o en la siguiente, sintaxis a la hora de manipular arrays (`array()` o `[]`),... 
- las reglas a utilizar en nuestro proyecto, las definiermos en un fichero llamado `ruleset.xml` que pasaremos como parámetro a la herramienta `phpcs`.

- a la hora de poder definir un conjunto de reglas a utilizar en el equipo, sería conveniente tener una lista de todas ellas y una breve descripción
- lamentablemente, la documentación de la herramienta no proporciona esa lista
- pero existen algunas posibilidades que nos pueden facilitar este trabajo

### Opción `-s`

- El comando `phpcs` se puede ejecutar con la opción `-s`, con la cual la herramienta indica qué regla (o *sniff*) estamos incumpliendo en cada violación que aparece en el informe de la herramienta

```bash
$ phpcs -s blablablalbalbablababalbalbal
...

<informe generado en modo texto, ea>

```

### Código fuente

- al final, la documentación más fiable, más actualizada, más detallada y más de todo es el código fuente
- puede asustar un poco tener que mirar el código fuente, pero [el código de PHP_CodeSniffer] es código abierto y se puede navegar en Github de forma sencilla
- además, no tendrás que consultarlo de arriba a abajo, aquí encontrarás unas pistas de donde encontrar las reglas

- el código está organizado en varios directorios, en `CodeSniffer/Standards` encontraremos el código fuente que nos interesa
- aquí, cada subdirectorio predefine un estándar: Generic, PEAR, PSR1, PSR2,...
- dentro de cada uno de estos directorios, encontramos un fichero llamado `ruleset.xml`, donde podemos encontrar las reglas importadas de aquellos estándares que las definen
- por ejemplo, `PSR2/ruleset.xml`:

```xml
<?xml version="1.0"?>
<ruleset name="PSR2">
 <description>The PSR-2 coding standard.</description>
 <arg name="tab-width" value="4"/>

 <!-- Include the whole PSR-1 standard -->
 <rule ref="PSR1"/>

 <!-- The soft limit on line length MUST be 120 characters; automated style checkers MUST warn but MUST NOT error at the soft limit. -->
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

- en este fichero podemos ver que se importan todas las reglas definidas en el estándar *PSR1* con `<rule ref="PSR1">`
- y que se importan reglas individuales de otros estándares, por ejemplo `<rule ref="Squiz.Scope.MethodScope"/>
- o que incluso se pueden pasar parámetros a algunas reglas, como se hace con `Generic.Files.LineLengh`

### Guía definitiva

- si con todo esto todavía no has dado con las reglas que quieres, o si necesitas conocer alguna regla más en profundidad, podemos echar un vistazo a cómo se generan las referencias de las reglas para poder incluirlas, excluirlas, parametrizarlas,... en nuestro `ruleset.xml`.

- tomemos como ejemplo las reglas *Generic*, ya que son las más utilizadas, más concretamente la regla `Generic.Files.LineLength`
- las reglas del estándar *Generic* están definidas en el directorio: `CodeSniffer/Standards/Generic`
- y dentro de él, en el directorio `Sniffs`
- el siguiente token, `Files`, indica un nuevo subdirectorio dentro de `Sniffs` con el mismo nombre
- y por último, `LineLength`, indica una clase PHP con ese mismo nombre más el sufijo `Sniff`.

- así pues, para la regla `Generic.Files.LineLength`, encontraremos una clase PHP en 
`CodeSniffer/Standards/Generic/Sniffs/Files/LineLengthSniff.php` [[[ ¿¿¿¿¿ SE PODRÍA CONSEGUIR ESTO CON FORMATO DE CÓDIGO PERO CON LETRA NEGRITA Y DEMÁS ????  ]]]]

Otros ejemplos podrían ser:

- `PEAR.Commenting.InlineComment`: clase `CodeSniffer/Standards/PEAR/Sniffs/Commenting/InlineCommentSniff.php`
- `PSR1.Classes.ClassDeclaration`: clase `CodeSniffer/Standards/PSR1/Sniffs/Classes/ClassDeclarationSniff.php`
- `Zend.Debug.CodeAnalyzer`: clase `CodeSniffer/Standards/Zend/Sniffs/Debug/CodeAnalyzerSniff.php`

- Pero aún hay más. En el `ruleset.xml` de ejemplo, veíamos cómo se pasaban parámetros a la regla `Generic.Files.LineLength` 
- ahora ya conocemos la clase PHP que cnotiene el código que ejecuta esa regla: `CodeSniffer/Standards/Generic/Sniffs/Files/LineLengthSniff.php` 
- dicha clase tiene dos variables públicas: `lineLimit` y `absoluteLineLimit`.
- que precismanete son los parámetros que se pueden configurar
- así pues, variables públicas en las clases `*Sniff` no son más que posibles parámetros a usar en el `ruleset.xml` de nuestro proyecto

### Referencias y enlaces relacionados

- [Mejora contínua y análisis estático de código]
- [Documentación de las reglas de PHP_CodeSniffer] en Stack Overflow



[el código de PHP_CodeSniffer]: https://github.com/squizlabs/PHP_CodeSniffer
[Mejora contínua y análisis estático de código]: http://rchavarria.github.io/blog/2014/05/05/mejora-continua-y-analisis-estatico-de-codigo
[Documentación de las reglas de PHP_CodeSniffer]: http://stackoverflow.com/questions/16427207/php-codesniffer-rules-documentation

