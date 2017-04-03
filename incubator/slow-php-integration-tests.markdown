Es una sensación extraña, pero me pasa a veces. Se supone que las máquinas, los ordenadores, son más rápidos que nosotros haciendo según qué cosas. Aún así, hay muchas veces que me desespero. Seguro que más de una vez te has puesto de los nervios porque tu ordenador tardaba mucho en finalizar una tarea: copiar un fichero, abrir un documento, cargar una página web,... Pues una cosa que me exaspera mientras estoy trabajando es esperar a que los tests terminen de ejecutarse.

El post de hoy va de una historia de abuelo cebolleta: hace un tiempo, tuvimos una *discusión* en la oficia, dentro del equipo con el que trabajo. Estuvimos discutiendo sobre cómo hacer nuestros tests de integración más rápidos.

Por aquel momento teníamos un gran número de tests de integración, más o menos emparejado con el número de tests unitarios. Bueno, sí, ya empezamos mal. Estoy de acuerdo con la teoría de que es mucho mejor tener una *pirámide* de tests, no un cucurucho de tests. Pero esa era nuestra realidad. La verdad es que a día de hoy, hemos conseguido tener muchos más tests unitarios que de integración, pero esa es otra historia.

<!-- more -->

Evidentemente, cuantos más tests de integración tenemos, más tiempo tardan éstos en ejecutarse. Pero eso no es excusa para quedarnos de brazos cruzados y esperar un cuarto de hora a que terminen de pasar los tests. La verdad es que sí, que tardan un rato en completarse. Son de integración, y el que no accede a la base de datos, accede a disco, y el que no hace una petición HTTP, el que no... Coges la idea ¿verdad? Integración. Acceso a sistemas externos. Len ti tud. ¡Ay!

J.B. Rainsberger ya lo lleva diciendo mucho tiempo: los [tests de integración son un dolor], y además, hacen que cada vez vayas más lento. Pero eso no quita que no sea necesario un cierto número de tests de integración.

<!-- imagen gif animado de alguna chorrada de test unitario pero no de integración -->
<iframe src='https://gfycat.com/ifr/HotOrangeCoypu' frameborder='0' scrolling='no' width='640' height='640' allowfullscreen></iframe>

Y entonces... ¿qué puntos se discutían?

Por una lado cada tests individual se encarga de dejar la base de datos tal y como estaba antes de ejecutarse (propiedad de *aislamiento* de los tests). Pero, ¿por qué? ¿Qué tal si al lanzar los tests se crea una nueva base de datos? Limpia, desde cero, y los tests la dejan en un estado cualquiera, no necesariamente limpia. De esta forma, los tests serán más rápidos, ya que se ahorran unas cuantas llamadas para limpiar datos. Por supuesto, utilizaríamos una base de datos distinta a la de cualquier entorno existente, no queremos que los tests interfieran con ellos.

Pero había algunos problemas. Los datos *basura* de unos tests podrían interferir en otros tests. O los últimos en ejecutarse podrían depender de tests anteriores y no darnos cuenta.

Por otro lado, si descuidamos los tests y no hacemos que limpien todo, terminaremos por ser vagos y hacer malos tests. Podemos incluso tener errores al borrar algunos registros. Total, nos da igual, en la siguiente ejecución, los tests van a empezar con una base de datos limpia.

También, utilizando la misma base de datos que en desarrollo, nos aseguramos que testeamos algo real, algo que usamos en nuestro día a día (aunque tenga sus diferencias con la de producción, por supuesto). Si lo hacemos contra otra base de datos, podemos estar desactualizados en algunas configuraciones, podemos estar falseando algunas características.

Además de todo eso, también surgieron ideas curiosas, por ejemplo, paralelizar la ejecución de los tests. Quizá así podríamos acelerar su ejecución. Por lo pronto, lo que sí hicimos para mejorar el tiempo de ejecución fue minimizar al máximo en número de conexiones a la base de datos desde los tests. No recuerdo la cifra, pero redujimos por lo menos un tercio el tiempo de ejecución de los tests de integración.

Y tú, ¿qué crees? ¿qué sería mejor? ¿utilizar una base de datos nuevecita para cada ejecución de los tests?

## Referencias

- [Pirámide de tests]
- Los [tests de integración son un dolor]
- [Propiedades FIRST] de los tests

[Pirámide de tests]: https://martinfowler.com/bliki/TestPyramid.html
[tests de integración son un dolor]: http://blog.thecodewhisperer.com/permalink/integrated-tests-are-a-scam
[Propiedades FIRST]: http://agileinaflash.blogspot.com.es/2009/02/first.html

