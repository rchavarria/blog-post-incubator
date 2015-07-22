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

- eso justo es lo que ha pasado en mi equipo en nuestro proyecto
- el proyecto ya está en un estado avanzado de desarrollo, y comenzamos a tneer un número considerable de tests automáticos en el front end
- utilizamos PhantomJS para ejecutar los tests en el servidor CI
- y debido a algunos problemillas que tiene PhatomJS con la gestión de memoria, hemos sobrepasado su límite
- con lo que hemos empezado a plantearnos que quizá son nuestros tests quien tienen al´gun problema con la memoria
- así que tenemos que probar varias ideas para solucionarlo

- HIPOTESIS
- una de estas ideas es reducir la cantidad de código JS a cargar y ejecutar en cada test
- en lugar de cargar el módulo AngularJS completo, con todo el codigo de la aplicación, cargar solamente aquel módulo que contenga la funcionalidad a probrar en el test
- pero esto es solo una hipótesis, no vamos a modularizar toda la aplicación en módulos minúsculos sin tener ningún dato sobre el que apyarnos
- por lo tanto, vamos a realizar la siguiente prueba: añadiremos un nuevo módulo, minúsculo. y en ese módulo crearemos una factoría, con un método al que llamaremos unas cuantas veces para hacer que los tests consuman una cantidad apreciable de memoria y CPU. ejecutaremos dos baterías de tests, una cargando el módulo que contiene toda la aplicación, una cargando solamente el módulo minúsculo

- TODO EL MODULO
> imagen con el consumo de memoria y tiempo de los tests
- algún comentario sobre la imagen

- MODULO PEQUEÑO
> imagen con el cosnumo de memorioa y tpo de tests
- comentarios

- CONCLUSIONES
- gana por goleada (memoria y cpu) el módulo pequeñito)
- recomendación: modulariza tu aplicación cuando vaya creciendo de tamaño. al ejecutar los tests, carga solo los módulos necesarios para que se ejecute esa suite de tests

