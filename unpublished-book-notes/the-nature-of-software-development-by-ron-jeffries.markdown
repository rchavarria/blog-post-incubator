# Frases que quiero recordar

> Valor es lo que uno quiere

> Un experto excelentemente remunerado no debería ser remunerado solamente porque es un experto. Debería ser excelentemente remunerado por ayudar a otras personas a que se conviertan en expertos.

> Las cosas van mejor si cada funcionalidad, también llamada *historia*, sólo tardamos **dos o tres** días en implementarla.

> El estilo de *funcionalidad a funcionalidad* incluye un ciclo completo de desarrollo en cada iteración: requisitos, diseño, codificación y testeo.

> Podemos construir todo el diseño primero, o podemos construir cada funcionalidad completamente de una en una, cada una con su base. Lo que no podemos hacer es construir toda la base al principio, así como tampoco podemos construir todas las funcionalidades al principio. Es de lejos mucho más seguro construir una versión simple pero funcional de cada funcionalidad primero.

> Trabajamos incrementalmente. Necesitamos un buen diseño relativamente pronto, pero solo necesitamos un **pequeño** buen diseño.

> Para obtener la mejor calidad, un progreso continuado y una gran predictabilidad, los tests y las refactorizaciones son la mejor forma conocida de trabajar.

> Toma cada posible idea como una posible forma de comenzar a hacer cosas durante un tiempo. Luego, haz tuyo el proceso, y construye tus propias ideas. ¡Pero mantenlo simple!

> Nuestro trabajo no es ceñirnos al plan, es ir corrigiendo el curso para obtener el mejor resultado, no llegar a algún punto fijo.

> Lo hacemos mejor no cuando predecimos cuándo habremos terminado, si no cuando elegimos cuándo está terminado (pero es que debemos mantenernos siempre en un estado de *terminado* de forma constante)

> Necesitamos un progreso constante, regular e ininterrumpido. Para mantener un progreso ininterrumpido, necesitamos un diseño claro y limpio todo el tiempo. Y para conseguirlo, necesitamos refactorizar nuestro código.

> La palabra refactorizar se refiere al proceso simple y regular de mantener el código limpio. Cuando la carretera se convierte en un camino intrincado, lo enderezamos refactorizando el código.

# Referencias

- [The fundamental theorem of Agile Software Development], de J.B.Rainsberger
- [Notas sobre The nature of Software development]

# The nature of software development
### by Ron Jeffries

[![The nature of software development](/img/nature-software-development.jpg)](https://www.amazon.es/Nature-Software-Development-Simple-Valuable/dp/1941222374/)

[English version](the-nature-of-software-development-by-ron-jeffries.en.markdown)

# Notas tomadas

Este libro es un intento de encontrar alguna simplicidad esencial dentro de la compleja actividad de construir productos software.

## Introducción

Éste no es un libro de recetas. Hay muchas maneras de conseguir lo que necesitas. Confío en tí para que encuentres caminos, pienses en caminos y elijas entre todos ellos.

## Capítulo 1: La búsqueda del valor

Como veremos más adelante, **valor es lo que uno quiere**

## Capítulo 2: Valor es lo que queremos

Un proyecto entrega valor solo cuando entregamos el software y entra en uso, nunca antes.

Es muy probable que haya un subconjunto de funcionalidades que puedan proporcionar valor antes que el paquete completo. Encontremos esas funcionalidades y entreguémoslas primero.

A veces, la información más importante que podemos obtener es saber que estamos haciendo algo mal. Una forma muy buena de saber si vamos en la buena dirección es entregar una versión pequeña del producto de una forma temprana. Si no funciona, podemos cambiar de dirección a un coste menor.

No es bueno que nuestros equipos trabajen en partes específicamente técnicas, que solo tienen sentido para ellos. Necesitamos guiar a nuestros equipos para que construyan piezas que tengan sentido para nosotros, y para nuestros usuarios. Estas piezas se suelen llamar *minimal marketable features (MMFs)*.

(*Haciendo referencia a una gráfica de rectángulos donde el valor crece hacia arriba, que nos sirve para averiguar qué tipo de cajas deberíamos de construir primero*)

XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
Incluir enlace a la imagen
XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX

Imagina que la altura de una funcionalidad es su valor y la anchura es su coste. El mejor valor viene de funcionalidades pequeñas, enfocadas en el valor, construidas y entregadas frecuentemente.

## Capítulo 3: Nos guiamos mejor "funcionalidad a funcionalidad"

Cuando construimos nuestro proyecto software funcionalidad a funcionalidad, podemos ver cuánto hay hecho y cómo de rápido está progresando el proyecto. Tenemos una buena sensación de cuánto tendremos hecho dada una determinada fecha en el futuro. (*no como en la forma tradicional de hacer software, que sólo podemos ver el valor aportado mucho más tarde en la vida del proyecto*)

Cuando nuestros proyectos crecen funcionalidad a funcionalidad, podemos responder/reaccionar a lo que realmente está pasando. 

## Capítulo 4: Organizando por funcionalidad

Organizando el trabajo por funcionalidad, Responsabilidad y Autoridad están alineados.

Organiza el trabajo en pequeños equipos. Asegúrate que cada equipo tiene toda la gente y todos los conocimientos necesarios para construir la funcionalidad completa, no sólo una parte de ella.

Como estás construyendo equipos por funcionalidad, encontrarás que tienes escasez de expertos en algún aspecto. Pronto, encontrarás creando un equipo donde la persona de la base de datos, o de UX, no es lo suficientemente buena. Fenomenal! Has identificado una oportunidad de formación. Una oportunidad de aprendizaje. Una oportunidad para formar un gremio, una **Comunidad de práctica**.

Un experto excelentemente remunerado no debería ser remunerado solamente porque es un experto. Debería ser excelentemente remunerado por ayudar a otras personas a que se conviertan en expertos.

(*IDEA: ¿por qué no propongo crear una Comunidad de Práctica, una comunidad para aprender a escribir tests?*)

## Capítulo 5: Planificando funcionalidad a funcionalidad

> Los planes no sirven para nada, pero la planificación es indispensable ~ *General Eisenhower*

Es importante identificar funcionalidades clave que necesitemos tener de forma temprana, así como funcionalidades de las que no podemos prescindir.

Planifiquemos, pero al mismo tiempo, debemos estar preparados para el cambio. (*abraza el cambio*)

(*Haz esto en lugar de crear un plan detallado*): establece un período de tiempo y un presupuesto; implementa las funcionalidades con más valor al principio; mantén el producto listo para entregar en cualquier momento; para cuando el período de tiempo se acabe.

Planificación contínua: división de funcionalidades en funcionalidades más pequeñas

Necesitamos estar planificando todo el tiempo, porque estamos enfocados en el valor. Si planificáramos solamente una vez al inicio, estaríamos enfocados en costes.

Las cosas van mejor si cada funcionalidad, también llamada *historia*, sólo tardamos **dos o tres** días en implementarla. (*Me pasa algo parecido. Si algo me va a llevar más de 3 días, es que no he dividido lo suficiente la historia/tarea*)

No recomiendo trabajar con historias más grandes, y partirlas en ítems técnicos, también llamadas *tareas*. si usamos tareas, la gente de negocio no tiene una visión clara de cómo las cosas están yendo. Es mejor dividir las historias en historias más pequeñas, de forma que cada parte tenga sentido para la gente de negocio.

Planificar con objetivos muy ambiciosos es destructivo. La razón es que el equipo intentará cumplirlos. Deseosos de cumplir, se apresurarán inconscientemente al realizar el trabajo. Como los defectos (bugs) llevan más tiempo solucionarlos que prevenirlos, las prisas harán que tu ritmo sea cada vez más lento (e impredecible).

Con la práctica, llegaremos a convertirnos en muy buenas a la hora de dividir las funcionalidades en funcionalidades de más o menos el mismo tamaño (*así es la forma de trabajo que consigue hacerlo sin estimaciones*)

Nuestro trabajo es seleccionar el trabajo a hacer y desechar el trabajo a posponer.

## Capítulo 6: Construyendo el producto, funcionalidad a funcionalidad

Planificamos y gestionamos nuestro proyecto en ciclos cortos de una o dos semanas. En cada ciclo, definimos cuáles van a ser las siguientes funcionalidades a construir y decidimos cómo van a ser probadas. Luego, el equipo implementa las funcionalidades y todos verificamos si pasan los tests o no. En cada una de estas iteraciones, realizamos un ciclo de desarrollo completo.

El estilo de "funcionalidad a funcionalidad" incluye un ciclo completo de desarrollo en cada iteración: requisitos, diseño, codificación y testeo.

Hay que eliminar la fase de testeo y corrección, testeo y corrección.

Esta fase puede incluso ocurrir cuando estamos trabajando de la forma funcionalidad a funcionalidad, si las funcionalidades no están realmente completadas al final del ciclo.

Para que este método funcione, el producto debe de estar libre de defectos prácticamente todo el tiempo.

## Capítulo 7: Construir funcionalidades y fundación en paralelo

(*Fundación como base o arquittectura de la aplicación*)

Las funcionalidades necesitan del soporte de una fundación, y la fundación necesita estar bien diseñada.

Consideremos varias opciones: podemos construir todo el diseño primero, o podemos construir cada funcionalidad completamente de una en una, cada una con su fundación. Lo que no podemos hacer es construir toda la fundación al principio, así como tampoco podemos construir todas las funcionalidades al principio. Es de lejos mucho más seguro construir una versión simple pero funcional de cada funcionalidad primero. (*no tiene sentido construir las funcionalidades de una tacada, es mejor construirlas de forma incremental*)

## Capítulo 8: Libre de bugs y bien diseñado

Cualquier defecto en nuestras funcionalidades se acumulan como funcionalidades en negativo. Reducen nuestra línea de progreso aparente. La reparación de defectos añaden retrasos desconocidos. Repara sobre la marcha para proporcionar claridad a lo que está hecho. (*cuantos más defectos, más grande será la incertidumbre sobre dónde nos encontramos*)

Recuerda, estamos trabajando incrementalmente. Necesitamos un buen diseño relativamente pronto, pero solo necesitamos un **pequeño** buen diseño.

El diseño puede deteriorarse fácilmente. Se requiere habilidad y cariño para mantener nuestro proyecto con vida. Conforme el proyecto va creciendo, las funcionalidades crecen con él, y debemos de hacer crecer el diseño que soporta esas funcionalidades.

Para mantener el diseño en buen estado, necesitamos mejorarlo sobre la marcha. Lo que no funciona, es dejar el diseño a su antojo.

Los tests y las refactorizaciones trabajan juntos para hacer posible el desarrollo funcionalidad a funcionalidad. Para obtener la mejor calidad, un progreso continuado, una gran predictabilidad, los tests y las refactorizaciones son la mejor forma conocida de trabajar.

## Capítulo 9: Se cierra el círculo

## Capítulo 10: Valor, ¿qué es?

## Capítulo 11: Valor, ¿cómo podemos medirlo?

Siéntate con tus desarrolladores y cliente. Seleccionad una combinación de las siguientes cosas a hacer y que el grupo esté de acuerdo en que son las cosas con más valor. Construidlo y entregadlo, y luego escuchad a vuestros usuarios. Repetid.

## Capítulo 12: ¡Por supuesto que es difícil!

Toma cada posible idea como una posible forma de comenzar a hacer cosas durante un tiempo. Luego, haz tuyo el proceso, y construye tus propias ideas. ¡Pero mantenlo simple! (*Se puede entender esto como una forma de conseguir hacer un trabajo, por muy difícil que sea: hacerlo poco a poco, de forma incremental, aprendiendo en el camino, y haciéndolo nuestro, no simplemente siguiendo una receta*)

## Capítulo 13: No es tan sencillo

Aún así, todo se reduce a decidir qué es lo que queremos, guiarnos a nosotros mismos hacia qué es lo que realmente queremos, construyendo cosas y viendo cómo se comportan. (*qué queremos -> priorizar -> construir -> observar -> decidir el siguiente paso*)

## Capítulo 14: Creando los mejore equipos

Propósito, autonomía y maestría

El dueño del producto proporciona propósito, dirección, hacia dónde debemos ir. Acerca problemas al equipo, y deja que el equipo al completo cree soluciones por sí mismos. (*Es importante que el equipo cree soluciones por ellos mismos, para que sientan el trabajo como suyo*)

Con la autonomía real, nadie supervisa al equipo: ellos deciden, ellos construyen, y todos vemos los resultados.

La maestría viene con el proceso iterativo. En cada iteración, nos reunimos y echamos la vista atrás para ver cómo fueron las cosas y determinar cómo lo podemos hacer mejor. De esta forma nos movemos hacia la maestría.

## Capítulo 15: El método de las 5 cartas para una predicción inicial

## Capítulo 16: Gestionando el desarrollo natural del software

Mi experiencia (la del autor) ha sido que gestionar trata sobre todo de intentar mantener los proyectos a raya, evitar desviaciones. Cómo nos aseguramos de que estamos siguiendo el plan? Sinceramente, nuestro trabajo no es ceñirnos al plan, es ir corrigiendo el curso para obtener el mejor resultado, no llegar a algún punto fijo.

## Capítulo 17: Arrear a los caballos más fuerte

Bajo presión, los equipos (consciente o inconscientemente) empiezan a ser más conservativos con las tareas a las que se comprometen. Empiezan a valorar las cosas un poco más largas o un poco más duras de lo que solían hacerlo. Esto puede dar la impresión de que se mueven más rápido, pero no lo están haciendo en absoluto.

Trabaja en mejorar la productividad del equipo antes que la productividad individual.

Incrementa la productividad individual incrementando su capacidad de solucionar problemas, no alentando a la gente a trabajar más y más duro.

Podemos por lo menos usar nuestra velocidad para predecir cuándo habremos terminado? En una palabra, NO!

Lo hacemos mejor no cuando predecimos cuándo habremos terminado, si no cuando elegimos cuando está terminado. La mejor manera de hacer esto, como ya hemos discutido antes, es estar siempre listo, estar siempre en estado "terminado".

Si tu organización tiene en mente algún contenido fijo, hay muchas probabilidades de que no estés gestionando por valor, si no por coste.

## Capítulo 18: Para acelerar, construye con habilidad

Mejora las habilidades dentro del equipo de desarrollo. Esa inversión será rentable rápidamente en forma de pasar menos tiempo perdido arreglando bugs y en un desarrollo más contínuo, más constante.

Los equipos más constantes se mueven de forma regular y elegante.

## Capítulo 19: Refactorizando

Necesitamos un progreso constante, regular, ininterrumpido. Para mantener un progreso ininterrumpido, necesitamos un diseño claro y limpio todo el tiempo. Y para conseguirlo, necesitamos refactorizar nuestro código.

El tiempo necesario para construir una funcionalidad viene de dos factores: la dificultad inherente y la dificulatad accidental de poner la funcionalidad dentro del código existente. Los equipos son buenos estimando la dificultad inherente. Lo que nos hace erráticos, lo que nos hace ser lentos, es la dificultad accidental. Llamamos a esta dificultad *código malo*. (*totalmente relacionada con la charla de J.B.Rainsberger [The fundamental theorem of Agile Software Development]*)

La palabra refactorizar se refiere al proceso simple y regular de mantener el código limpio. Tratamos de no crear los caminos enrevesados que nos hacen ir lento. Cuando los caminos se entrelazan, los enderezamos refactorizando. (*Cuando la carretera se convierte en un camino intrincado, lo enderezamos refactorizando el código*)

XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
imagen de los caminos que se entrelazan o enderezn
XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX

> Deja el campo un poco mejor de cómo lo encontraste ~ *Regla del Boy Scout*

Este proceso hace justamente lo que necesitamos: las áreas donde trabajamos poco no nos hacen ir más lento, y las dejamos de lado. Las áreas donde hacemos la mayoría del trabajo, tiene casi toda nuestra atención, con lo que se limpia rápidamente.

## Capítulo 20: Métodos ágiles

Algunos consejos sobre los métodos ágiles o frameworks:

- Toma un poquito del framework, no demasiado
- Mantén el proceso ligero
- Controla el framework, no dejes que el framework te controle a tí
- Haz del aprendizaje una prioridad
- Piensa

## Capítulo 21: Escalando Agile

## Capítulo 22: Conclusión

