# Practical Object-Oriented Design in Ruby
## de Sandi Metz

[![Practical Object-Oriented Design in Ruby](https://raw.githubusercontent.com/rchavarria/blog-post-incubator/master/published-book-notes/img/poodr.jpg)](enlace a la reseña en el blog)

### Por qué lo he leído

¿Quién lo ha recomendado? ¿Dónde lo he visto?

<!-- more -->

### De qué trata el libro

Si le tuviera que contar a alguien de qué va el libro, ¿qué le diría?
¿Qué esperaba encontrar yo en él? ¿Ha sido lo que esperaba?

### Conclusiones y valoración

La *review* en sí del libro. ¿Qué me ha parecido? ¿Lo recomendaría? ¿Me ha gustado el estilo?

### Qué he aprendido

### Frases que me gustaría recordar

### Recursos relacionados

[titulo sobre el enlace a las notas]: foo-bar-foo-bar

### Notas tomadas

#### Capítulo 1

#### Capítulo 2: Diseñando clases con una única responsabilidad

- Es fácil crear un software que funcione una vez, pero muy difícil hacer que sea sencillo aplicarle cambios durante mucho tiempo
- Diseño es más el arte de preservar la *cambialidad* que el acto de alcanzar la perfección
- Código que es fácil de cambiar, es código T.R.U.E.: transparente, razonable, usable y ejemplar (si encuentro alguna referencia más sobre ello, mejor)
- Las aplicaciones que son fáciles de cambiar consisten en clases fáciles de reutilizar
- Describe lo que hace la clase en una frase, si tienes que usar *y* u *o*, probablemente tenga más de una responsabilidad
- Nunca vas a saber menos de lo que sabes ahora, y eso puede ser una razón para posponer una decisión de diseo
- siempre existe una tension entre mejorarlo ahora o mejorarlo después. Un buen diseñador sabe minimizar los costes tomando decisiones valorando lo que sabe ahora y lo que sabrá en el futuro
- Aplica SRP también a los métodos, no solo a las clases. Beneficios: fácil de cambiar, fácil de reutilizar
- No tomes decisiones, pero mantén tus opciones de tomar decisiones más adelante

#### Capítulo 3: Gestionando dependencias

- El reto al diseñar es hacer que cada clase tenga las menos dependencias posibles
- las dependencias acoplan clases, hacen que funcionen como una única cosa, se mueven a la vez, **cambian** a la vez y dificulta la reutilización de uno de ellos
- técnicas para reducir dependencias desacoplando el código:

1. inyectar dependencias: las clases son más reutilizables cuanto menos saben de otras clases
2. aislar dependencias: crear nuevos objetos en métodos a parte, encapsular llamadas a métodos de dependencias
3. eliminar dependencias del orden de los argumentos. Usar un hash (o mapa) como única argumento. Aísla la llamada al método si no puedes modificarlo.

- Gestiona la dirección de las dependencias: depende de cosas que cambien menos frecuentemente que tú. La dirección elegida va a depender de qué cambio va a sufrir cada parte. Si no hay cambios, da igual qué dirección elijamos. Depender de abstracciones es más seguro, porque por definición son más estables que las concrecciones
- Para conocer las dependencias más interesantes nos fijamos en 3 aspectos: probabilidad del cambio, nivel de abstacción y número de dependencias (sobretodo de la 1ª y 3ª)
- las dependencias más peligrosas son aquellas que cambian con frecuencia y muchas otras clases dependen de ellas
- En resumen, gestionar dependencias es: inyectarlas, aislarlas y depender de abstracciones

#### Capítulo 4: Creando interfaces flexibles


