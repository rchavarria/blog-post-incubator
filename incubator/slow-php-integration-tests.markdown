Hoy el post va de una historia de abuelo cebolleta: hace un tiempo, tuvimos una *discusión* en la oficia, dentro del equipo con el que trabajo. Estuvimos discutiendo sobre cómo hacer nuestros tests de integración más rápidos.

Por aquel momento teníamos un gran número de tests de integración, más o menos emparejado con el número de tests unitarios. Bueno, sí, ya empezamos mal. Estoy de acuerdo con la teoría de que es mucho mejor tener una *pirámide* de tests, no un cucurucho de tests. Pero esa era nuestra realidad. La verdad es que a día de hoy, hemos conseguido tener muchos más tests unitarios que de integración, pero esa es otra historia.

<!-- more -->

Evidentemente, cuantos más tests de integración tenemos, más tiempo tardan éstos en ejecutarse. Pero eso no es excusa para quedarnos de brazos cruzados y esperar un cuarto de hora a que terminen de pasar los tests. La verdad es que sí, que tardan un rato en completarse. Son de integración, y el que no accede a la base de datos, accede a disco, y el que no hace una petición HTTP, el que no... Coges la idea ¿verdad? Integración. Acceso a sistemas externos. Len ti tud. ¡Ay!

J.B. Rainsberger ya lo lleva diciendo mucho tiempo: los [tests de integración son un dolor], y además, hacen que cada vez vayas más lento. Pero eso no quita que no sea necesario un cierto número de tests de integración.

<!-- imagen gif animado de alguna chorrada de test unitario pero no de integración -->

Y, ¿qué dos puntos se discutían?

Por una lado bla blah

Por otro foo bar

<!-- -->

Además de todo eso, también surgieron ideas curiosas, por ejemplo, paralelizar la ejecución de los tests. Quizá así podríamos acelerar su ejecución. Por lo pronto, lo que sí hicimos para mejorar el tiempo de ejecución fue minimizar al máximo en número de conexiones a la base de datos desde los tests. No recuerdo la cifra, pero redujimos por lo menos un tercio el tiempo de ejecución de los tests de integración.

Y tú, ¿qué crees? ¿qué sería mejor? ¿utilizar una base de datos nuevecita para cada ejecución de los tests?

## Referencias

- Pirámide Vs Cucurucho de tests
- Los [tests de integración son un dolor]

<!-- 

Hoy en la oficina hemos tenido una *discusión* interesante. 

Tenemos un gran número de tests de integración (algo menor que unitarios, está bien saber que no tenemos una pirámide invertida o un cucurucho de tests - buscar referencia)

Resulta que cada vez lleva más tiempo ejecutarlos, muchos de ellos acceden a bbdd. Son de integración ¿recuerdas?

Sí, ya se, J.B.Rainsberger ya lo dice en su blog desde hace mcho tiempo: integration tests are a scam, and they drags you down - buscar referncia

Qué dos puntos se defendían en la discusión?

1. Por qué cada test debe limpiar la bbdd? qué tal si al lanzar los test se crea una nueva bbdd, limpia, desde cero, y la dejamos en un estado que nos da igual, no hace falta limpiarla y los tests irán más rápidos. También, al ser una bbdd separada, no interferimos en la bbdd de desarrollo.
2. Por otro lado, si descuidamos los tests, y no hacemos que limpien todo, terminaremos por ser vagos y hacer malos tests. Podemos incluso tener errores al borrar algunos registros, total, nos da igual, el siguiente test va a empezar ocn una bbdd limpia. También, utilizando la misma bbdd de desarrollo nos aseguramos que testeamos algo real (aunque no llegue a ser la de producción). Si lo hacemos contra otra bbdd, podemos estar falseando algunas características.

Tamibén hemos llegado a la conclusión que quizá paralelizando la ejecución, consigamos acelerarlos

y tú, qué crees? qué sería mejor, utilizar una bbdd nueva, o no?

-->

