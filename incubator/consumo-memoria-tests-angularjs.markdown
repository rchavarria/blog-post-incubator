Hoy en día no concibo desarrollar una aplicación sin una batería de tests
automáticos (unitarios, de integración, end-to-end, del tipo que sean). 
Da igual el tamaño del proyecto. Pero además, si se trata de una aplicación
JavaScript, tener tests es una obligación.

[AngularJS] es un framework que pone las cosas fáciles para comenzar a escribir
tests. Incluso la propia aplicación de ejemplo ya viene preparada para
escribir tests con [Jasmine] y ejecutarlos con [Karma] en tu navegador.

Si el proyecto es muy grande, llegará un punto en el que haya cientos de tests
automáticos, quizá miles, por lo que ejecutar todos los tests en el navegador
se puede considerar como la ejecución de una gran aplicación. Por lo tanto
habrá que tener en cuenta aspectos de rendimiento, consumo de memoria (y
liberación de la misma), posibles *memory leaks*,...

<!-- more -->

Eso justo es lo que está pasando en mi equipo. Nuestro proyecto está en un
estado avanzado de desarrollo, y comenzamos a tener un número considerable de
tests automáticos en la parte cliente. Para ejecutar los tests en el servidor
de integración contínua utilizamos [PhantomJS]. Pero parece ser que PhantomJS
tiene algunos problemillascon la gestión de memoria, y hemos sobrepasado su
límite. PhantomJS no puede ejecutar toda nuestra batería de tests de una sola
vez. Así que nos estamos planteando si quizá son nuestros tests quienes tienen
algún problema con la memoria, quizá podríamos hacer algo para no consumir
tantos recursos.

## Hipótesis

Una idea para solucionarlo pasa por reducir la cantidad de código JavaScript a
cargar y ejecutar en cada test. ¿Qué tal si en lugar de cargar el módulo
principal de AngularJS completo (donde está contenida toda nuestra aplicación),
cargamos solamente aquel módulo que contenga la funcionalidad a probar en el
test?

Pero esto es sólo una hipótesis, no vamos a modularizar toda la aplición en
módulos minúsculos sin tener ningún dato sobre el que apoyarnos. Por lo tanto,
vamos a realizar la siguiente prueba: añadiremos un nuevo módulo, minúsculo. En
este módulo crearemos una factoría, con un método al que llamaremos tantas veces
sea necesario para hacer que los tests consuman una cantidad apreciable de
memoria y CPU. Ejecutaremos dos baterías de tests, con los mismos tests: una
cargando el módulo que contiene toda la aplicación, otra cargando solamente el
módulo pequeño.

- TODO EL MODULO
> imagen con el consumo de memoria y tiempo de los tests
- algún comentario sobre la imagen

- MODULO PEQUEÑO
> imagen con el cosnumo de memorioa y tpo de tests
- comentarios

- CONCLUSIONES
- gana por goleada (memoria y cpu) el módulo pequeñito)
- recomendación: modulariza tu aplicación cuando vaya creciendo de tamaño. al ejecutar los tests, carga solo los módulos necesarios para que se ejecute esa suite de tests

