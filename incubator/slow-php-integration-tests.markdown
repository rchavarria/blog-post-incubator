Hoy en la oficina hemos tenido una *discusión* interesante. 

Tenemos un gran número de tests de integración (algo menor que unitarios, está bien saber que no tenemos una pirámide invertida o un cucurucho de tests - buscar referencia)

Resulta que cada vez lleva más tiempo ejecutarlos, muchos de ellos acceden a bbdd. Son de integración ¿recuerdas?

Sí, ya se, J.B.Rainsberger ya lo dice en su blog desde hace mcho tiempo: integration tests are a scam, and they drags you down - buscar referncia

Qué dos puntos se defendían en la discusión?

1. Por qué cada test debe limpiar la bbdd? qué tal si al lanzar los test se crea una nueva bbdd, limpia, desde cero, y la dejamos en un estado que nos da igual, no hace falta limpiarla y los tests irán más rápidos. También, al ser una bbdd separada, no interferimos en la bbdd de desarrollo.
2. Por otro lado, si descuidamos los tests, y no hacemos que limpien todo, terminaremos por ser vagos y hacer malos tests. Podemos incluso tener errores al borrar algunos registros, total, nos da igual, el siguiente test va a empezar ocn una bbdd limpia. También, utilizando la misma bbdd de desarrollo nos aseguramos que testeamos algo real (aunque no llegue a ser la de producción). Si lo hacemos contra otra bbdd, podemos estar falseando algunas características.

Tamibén hemos llegado a la conclusión que quizá paralelizando la ejecución, consigamos acelerarlos

y tú, qué crees? qué sería mejor, utilizar una bbdd nueva, o no?

