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

- Una aplicación software está hecha de clases pero **definida** por mensajes. Los mensajes reflejan la *vida* (lo que está vivo) de la aplicación
- La interfaz pública es un contrato que describe las responsabilidades de una clase
- No hay que centrarse en los objetos de dominio, si no en los mensajes que se pasan entre ellos
- Diseñar basado en mensajes crea aplicaciones más flexibles que diseñar pensando en objetos. En lugar de preguntarte: tengo un objeto ¿qué debería hacer?, deberías preguntarte tengo un mensaje, ¿a quién se lo envío?
- No envías mensajes porque tienes objetos, tienes objetos porque necesitas enviar un mensaje a alguien
- Pregunta *Qué* en lugar de decir *Cómo*. Una consecuencia de esto es que las interfaces públicas (dependencias al fin y al cabo) se reducen
- Las cosas que una clase conoce conforman su **contexto**, lo cual tiene un efecto directo en lo fácil o difícil que es reusar (y por tanto testear) esa clase
- Un objeto será muy fácil de reutilizar si:

1. no sabe de quien depende (inyección de dependencias)
2. no sabe qué hacen (tell, don't ask)

- Al eliminar parte del contexto, unos objetos confían en los objetos recibidores de los mensajes enviados en que éstos realizarán las tareas correctas
- **qué y cómo, contexto y confianza**
- Llevar tu atención de clases a mensajes te permite diseñar tu aplicación construyéndola sobre interfaces públicas
- La claridad de tus interfaces revelan tus habilidades como diseñador y reflejan tu autodisciplina, porque las interfaces evolucionan y nunca estarán perfectas porque los requisitos cambian
- Los métoos públicos no lo son para que los demás puedan usarlos, si no porque son **estables**, y los privados son así porque son **inestables**
- Si tu diseño te pide usar interfaces privadas de otros, re-piensa tu diseño. Si aún así debes seguir usándolas, aísla dependencias
- Construye tus interfaces públicas intentando minimizar el contexto de los clientes de esas interfaces
- Muchas de las violaciones de la *ley* de Demeter, fallan evaluando contra T.R.U.E.
- No todas las violaciones de Demeter son iguales. Si sólo están implicadas clases muy estables, a lo mejor no es tan malo (por ejemplo, con clases como `String`, `Object`,...). Depende mucho de la estabilidad de la interfaz
- El camino más rápido para evitar violaciones es la delegación. Pero la deleación no evita el acoplamiento que supone la violación. En su lugar, debemos tomar las violaciones como pistas de que hay objetos a cuyas interfaces públicas les faltan métodos. **Esto es diseñar pensando en mensajes y no en objetos**

#### Capítulo 5: Reduciendo costes con tipado débil (duck typing)

- El objetivo de la POO es el de reducir el coste del cambio. A esto ayuda que los mensajes sean el centro de tu aplicación y saber que hay que diseñar con interfaces públicas muy pensadas.
- El código concreto (cada clase con métodos diferentes) es fácil de entender, pero costoso de cambiar. El código abstracto puede parecer oscuro al principio, pero una vez entendido es mucho más fácil de cambiar.
- Los *duck types* hacen tu código más abstracto

#### Capítulo 6: Adquiriendo comportamiento a través de la herencia

- Los objectos autocontenidos, pequeños, con mínimo contexto, interfaces claras y dependencias inyectadas son **reutilizables** por naturaleza.
- La herencia basada en clases es fundamentalmente una forma de delegar automáticamente los mensajes entre clases cuando una de ellas no los entiende
- Cuando una clase pregunta por su tipo para saber qué mensaje debe enviarse a sí misma, es posible que algún subtipo (subclase) esté deseando aparecer, como en el caso del *duck typing*, que nuevos tipos o abstracciones gritaban por ser creados
- ¿Qué problema resuelve la herencia? Tipos altamente relacionados pero que difieren en alguna dimensión
- Cuando una lcase hereda de otra, hereda todo su comportamiento: público y privado, general y específico, abstracto y concreto
- Para que una herencia funcione, debe de haber una relación de generalización-especialización, donde la especialización sea todo lo general y algo más
- Crear una herencia tiene costes, y la mejor forma de minimizarlos es esperar todo lo posible para tener el máximo de conocimiento y dar con las abstracciones más adecuadas
- La regla general de refactorizar a una herencia es colocar el código de tal forma que haya que promocionar abstracciones a las superclases, en lugar de *rebajar* concrecciones a las subclases
- Toda decisión de diseño tiene dos costes: el de implementar el cambio y el de corregit la decisión si ésta fue equivocada, por lo que hay que preguntarse ¿qué pasará cuando esté equivocado?
- El código para tareas parecidas debe seguir patrones parecidos
- Crear código que falla con mensajes de error claros y útiles requiere poco esfuerzo en el presente pero proporciona valor para siempre
- Forzar a una subclase a saber cómo y cuándo interactuar con su superclase siempre causa muchos problemas porque conocen el algoritmo de la superclase, están acoplados a ella, y si el algoritmo cambia, deben cambiar o pueden fallar
- Para desacoplarlas se pueden usar *hook messages*, similares a los *factory methods*. Lo que hacen es devolver el control del algoritmo a la superclase, la superclase controla y sabe cuándo se deben hacer las cosas

El libro está lleno de refactorizaciones muy conocidas, pero razonadas, hechas en el momento oportuno y explicadas con muchísima claridad. Es como si supiera tus razones para cambiar el código y las plasmara en palabras.

#### Capítulo 7: Compartiendo comportamiento con módulos

El capítulo habla de *roles*, de *papeles* jugados por las clases. Creo que voy a utilizar el término en inglés, para no perder significado en la traducción. Así que en este capítulo se habla de *role behaviour*.

- Cada problema resuelto por la herencia puede ser resuelto de otra manera, debemos pensar en la manera más efectiva en cuanto a costes.
- Los módulos en Ruby serían como los `trait`s en PHP, otra forma de compartir código, muy parecido a la herencia (de hecho las técnias de refactorización son las mismas), pero más desacoplado que la herencia.
- Si una clase tiene una propiedad llamada `type` o `category` está pidiendo a gritos una herencia
- Si hay código que pregunta por el tipo de un objeto para enviar un mensaje u otro, estamos necesitando *duck typing*, una abstracción
- Cuando además del interfaz (*duck type*) necesitamos compartir comportamiento, necesitamos un *role* (módulo, trait, mixing,...)
- El código de una clase abstracta o en un módulo debería ser usado en su totalidad por las sublcases, si no, estamos equivocados con la abstracción
- Para que una herencia sea correcta, las subclases deben poder sustituir a sus superclases (Bárbara Liskov, SOLID)
- La técnica fundamental para escribir código *heredable* es [*template method*](https://en.wikipedia.org/wiki/Template_method_pattern)
- Evita escribir código que obliga a sus subclases a enviar el mensaje `super` (llamar al método `super()`)
- No crees jerarquías profundas

#### Capítulo 8: Combinando objetos con Composición

Impresionante ver cómo refactoriza una herencia a una composición de objetos: engloba una colección de objetos en una nueva clase, crea una factoría que crea cada una de las partes, simplifica las partes como dadas de configuación. De esta forma, añadir un uevo tipo no requiere una nueva clase, solamente nueva configuración

- La herencia sólo es una forma de organizar el código, que a cambio de cierto acoplamiento, tenemos delegación automática de mensajes
- La composición es otra forma de organizar el código donde cada parte e smás independiente, pero no tenemos delegacion automática de mensajes, se no que hay que hacerlo de forma explícita
- Beneficios de la herencia (recordando las siglas T.R.U.E.): *reasonable* pequeños cambios en el top de la jerarquía pueden tener efectos muy potentes; *usable* las jerarquías cumplen con la **O** de *S.O.L.I.D.*, son open-closed; *exemplary* por naturaleza, la jerarquía indica cómo ir extendiendo el código
- Costes de la herencia: los peores costes se producen cuando se usa la herencia para resolver el problema equivocado. En este caso tenemos los mismos beneficios, pero en negativo: un pequeño cambio tiene consecuencias muy graves, me fuerza a implementar una solución de una manera específica,...
- Código creado con composición es *transparente* (T de *true*), suelen ser clases pequeñas con una única responsabilidad y suele ser fácil entenderlas. Son *usables* (U de *true*) porque son pequeños y enfocados. Son *razonables* (R de true) porque se pueden extender sin modificar
- La composición es ideal para describir objetos que están hechos de varias partes pero no ayuda mucho a organizar el código para una serie de partes que son casi idénticas, porque no tiene delegación automática de mensajes
- Eligiendo relaciones (herencia, roles/*duck typing*, composición)

1. Herencia para relaciones *es-un* (is-a). Especialmente si la jerarquía es estrecha y tiene pocos niveles
2. Role/duck type para relaciones *se-comporta-como* (behaves-like-a). Donde varios objetos no relacionados se quieren comportar del mismo modo
3. Composición para relaciones *tiene-un* (has-a). Un objeto tiene varias partes pero es más que la suma de ellas, si no sería una colección y ya está

- Las claves para que mejoren tus diseños son

1. Acepta tus errores con alegría
2. Mantente separado emocionalmente de decisiones de diseño pasadas
3. Refactoriza sin piedad

#### Capítulo 9: Diseñando tests efectivos en costes

- Desde un punto de vista práctico, la posibilidad de hacer cambios en el código es la única métrica de diseño que importa
- 3 aspectos fundamentales para tener código modificable

1. Código bien diseñado: de forma que es fácil modificarlo
2. Buenas habilidades de refactorización: refactorizando es como se cambia de un diseño a otro
3. Capacidad de escribir buenos tests: que te permitan refactorizar con impunidad

- El verdadero objetivo del testing (como el del diseño) es el de reducir costes
- Beneficios

1. Encontrar bugs pronto (reduce costes) y ayuda a saber si algo va a ser posible hacerlo
2. Reemplaza a la documentación: escribe tests como si tu futuro yo fuera a tener amnesia
3. Posponer decisiones de diseño
4. Ayudan a las abstracciones: porque son el único punto que ayudan a entenderlas. Tienes muchas abstracciones pequeñas y separadas, con los tests puedes comprender cómo interactúan
5. Exponen fallos en el diseño: si el test es difícil de escribir, el objeto será difícil de reusar

- Para obtener el máximo valor de los tests, hay que tener el mínimo de ellos. Para ello, hay que testear cada cosa una sola vez, y en el lugar apropiado.

1. Mensajes entrantes tipo *query* hay que testear el **estado** que devuelven
2. Mensajes salientes tipo *command*, hay que testear que son llamados, cuantas veces y con qué parámetros
3. Mensajes salientes tipo *query*, no se testean (ya los testearán los tests de otro objeto)

- ¿Cuándo escribir tests? Antes que el código siempre que se pueda. Para los junior es difícil, porque escriben código muy acoplado, **los tests son formas de reusar código, y es difícil reusar código acoplado**.
- Escribir los tests primero no es sustituto y no garantiza un buen diseño, pero la reusabilidad que dan es una muy buena mejora
- Las applicaciones bien diseñadas son fáciles de cambiar, y los tests bien diseñados evitan ser cambiados siguiendo los cambios en el código, y todo esto reduce mucho los costes
- Tus tests deberían conocer acerca del S.U.T., pero nada más, nada de objetos fuera del S.U.T. Es mala idea probar el S.U.T. desde el interior, se deben conocer sus límites, y se deben probar los mensajes salientes y entrantes.
- Tu aplicación mejorará si borras código no usado. Ese código es dinero en negativo en efectivo, y cuesta mantenerlo y testearlo.
- Los mensajes entrantes son el interfaz público de tus objetos
- Los mensajes entrantes se prueban con tests de estado
- Cuando solo hay una implementación de un role o duck type, es bueno inyectar la dependencia real al escribir los tests. Si hay muchas, ninguna (estamos haciendo BDD) o son muy lentas, tenemos que inventarnos una implementación *ideal* (tests doubles)
- Los mensajes salientes tipo query (no tienen efectos colaterales) no hay que testearlos, serán tratados como mensajes entrantes en otros objetos
- Los mensajes salientes tipo command: se debe comprobar que son llamados, pero no se debe comprobar el valor devuelto. Esos tests pertenecen al otro objeto como mensaje entrante. Si lo hacemos, estaremos duplicando tests y aumentando costes.

