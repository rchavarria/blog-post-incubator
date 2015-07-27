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

- a la hora de poder definir un conjunto de reglas a utilizar en el equipo, sería conveniente tener una lista de todas ellas y una breve descripción
- lamentablemente, la documentación de la herramienta no proporciona esa lista
- pero existen algunas posibilidades que nos pueden facilitar este trabajo

**Opción `-s`**

- El comando `phpcs` se puede ejecutar con la opción `-s`, con la cual la herramienta indica qué regla (o *sniff*) estamos incumpliendo en cada violación que aparece en el informe de la herramienta

```bash
$ phpcs -s blablablalbalbablababalbalbal
...

<informe generado en modo texto, ea>

```

**Código fuente**

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



[el código de PHP_CodeSniffer]: https://github.com/squizlabs/PHP_CodeSniffer

