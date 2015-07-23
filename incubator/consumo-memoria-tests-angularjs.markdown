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

## Aplicación completa

{% img center /images/2015/memory-benchmark-big.thumbnail.png %}

Podemos apreciar como la ejecución de la batería de tests dura aproximadamente
unos 8 segundos (desde 4.5s hasta 12.25s). En cuanto a consumo de memoria, el
rango va de un mínimo de 10Mb a un máximo de 108Mb.

Se puede apreciar cómo el consumo de memoria va dibujando unos dientes de sierra.
Éste dibujo es muy típico en los análisis de memoria (hay momentos en los que
se reserva memoria y el consumo aumenta, pasado un pequeño espacio de tiempo,
objetos en memoria se dejan de usar y ésta es liberada, que es cuando la gráfica
baja de golpe). Pero la mala noticia es que el consumo va cada vez a más, no se
libera la misma cantidad que se reserva, lo que indica que hay muchas referencias
a objectos que no se eliminan correctamente. Incluso después de haber terminado
la ejecución de los tests, el navegador no considera que deba liberar memoria.

## Módulo pequeño

{% img center /images/2015/memory-benchmark-small.thumbnail.png %}

El tiempo de ejecución de esta batería de tests es de 1s, de 3.25s a 4.25s,
(esta gráfica muestra intervalos de 500ms). El consumo de memoria sube
rápidamente, con un mínimo de 11Mb y un máximo de 42.5Mb.

Esta vez, casi no se aprecian los dientes de sierra, quizá porque la ejecución
es mucho más rápida y el navegador no considera que haya que liberar memoria de
forma agresiva durante el tiempo que dura la ejecución. Aquí se puede observar
claramente cómo después de que los tests hayan terminado, pasado un tiempo, el
navegador es capaz de liberar prácticamente toda la memoria consumida por los
tests. Esto es muy buena señal.

## Conclusiones

Con este pequeño análisis queda bastante claro que tener módulos pequeños hace
que nuestros tests se ejecuten mucho más rápido (el tiempo de ejecución baja de
8s a 1s) y consuman mucha menos memoria (el máximo baja de 108Mb a 42.5Mb).
También se puede deducir que en módulos pequeños hay un riesgo más bajo de sufrir *memory leaks*.

En este caso, al usar un módulo muy pequeño y no observar *memory leaks*, se
deduce que los *leaks* que se observan en la aplicación en su conjunto deben de
estar en otro módulo. Esto nos ayuda a aislar partes de nuestra aplicación y
poder reducir la cantidad de código a analizar para encontrar el problema.

Estábamos en lo cierto con nuestra hipótesis, módulos pequeños hacen que los
tests sean más rápidos y más eficientes en el consumo de memoria. Por lo tanto,
parece buena idea *modularizar una aplicación* con un tamaño considerable, y al
ejecutar los tests *cargar sólo los módulos necesarios* para que se ejecute esa
suite de tests, no cargar módulos redundantes.

