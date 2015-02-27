# [Extreme Programming explained, by Kent Beck](http://rchavarria.github.io/blog/2015/01/02/extreme-programming-explained/)

- Extreme Programming (XP, o Programación Extrema) es una metodología ligera 
para equipos de tamaño pequeño o mediano que desarrollan software 
enfrentándose a requisitos vagos o en contínuo cambio.
- XP es un experimento para responder a la pregunta: ¿Cómo programarías si
tuvieras suficiente tiempo? Donde se explica la diferencia entre la *Mentalidad
de la suficiencia* frente a la *Mentalidad de la escasez* (parábola de la
tribu del bosque y de la montaña)
- La mayoría de las prácticas en XP son tan viejas como la programación en
sí misma.

## Parte I: el problema

- El problema básico es el riesgo, así que, ¿cómo gestiona XP el riesgo?

1. Desviaciones de la planificación: ciclos de releases cortos
2. Cancelación del proyecto: pregunta al cliente que elija la release más pequeña
que tiene sentido para el negocio
3. El sistema se vuelve rancio: no se permite que se acumule lo que ha dejado de
ser útil
4. Tasa de defectos: teste funciones y funcionalidades
5. Malentendido en el negocio: el cliente es una parte integral del equipo
6. Cambios en el negocio: ciclos de releases cortos
7. Falsa riqueza de funcionalidades: se realizan las tareas con la máxima prioridad
8. Rotación del personal: los programadores aceptan responsabilidades

- XP puede ayudar en varios aspectos para una estrategia para maximizar el 
valor económico del proyecto:

1. Gastando menos dinero y generando ingresos antes
2. Incrementando la probabilidad de que el proyecto siga con vida durante más tiempo

- Hay cuatro variables fundamentales en el desarrollo software: **Coste**, **Tiempo**,
**Calidad** y **Alcance**.
- Clientes y Managers escogen los valores de tres de ellas, el equipo de desarrollo
elige el valor resultante de la cuarta.
- Si no les gusta el resultado, pueden cambiar los valores de entrada o pueden 
elegir otras tres variables de control distintas.
- En la mayoría de los casos, el Coste es la variable más restrictiva. La inversión
comenzar poco a poco y crecer a lo largo del tiempo.
- La Calidad es una variable extraña. A menudo, insistir en una mejor Calidad
puede hacer que los proyectos estén hechos antes. Los sacrificios internos de
Calidad de forma temporal para reducir el tiempo de entrega puede ser una
forma tentativa de jugar. Pero hay que tener cuidado o la falta de calidad
te pillará y puede que llegues a un punto de código inmantenible.
- En cuanto al desarrollo del software, el **Alcance** es la variable más importante
a tener en cuenta.
- ¿Qué tal si vemos la flexibilidad de los requisitos como una oportunidad y no
como un problema? Así podemos ver el Ámbito como la más fácil de las cuatro variables
de control, porque es tan flexible que podemos darle la forma que queramos.
- ¿Cómo conseguir que no suba el coste del cambio con el paso del tiempo?

1. Diseño sencillo
2. Tests automáticos
3. Refinamiento constante del diseño

- Necesitamos controlar el desarrollo del software mediante muchos pequeños ajustes,
no con unos pocos ajustes muy grandes.
- Haz muchos cambios pequeños (mejor que unos pocos grandes) pero nunca apartar
los ojos de la carretera (porque desarrollar es como conducir, es mejor ir haciendo
pequeñas correcciones que un volantazo para corregir el rumbo).

## Los cuatro valores

**Comunicación**

- Cualquier problema en un proyecto puede, invariantemente, ser
rastreado hasta encontrar a alguien que no habló con otro alguien acerca de algo
importante. 
- El efecto de los tests, programación en parejas y las estimaciones es que
Programadores, Clientes y Managers están obligados a comunicarse.

**Simplicidad**

- La Simplicidad no es fácil.
- Lo más difícil en el mundo es evitar mirar hacia adelante al pensar en funcionalidades
que vas a necesitar implementar mañana, la próxima semana o el próximo mes.

**Feedback**

- Trabaja en diferentes escalas de tiempos. Por ejemplo, los tests unitarios dan
feedback en minutos o días, mientras que los tests funcionales proporcionan feedback
en semanas o meses.
- El sistemas se pone en producción tan pronto como tiene sentido hacerlo. De esta
forma el Negocio puede comenzar a ver cómo va a ser el sistema.
- El feedback funciona con la Comunicación y la Simplicidad. Cuanto más feedback
tienes, más fácil es comunicar. Si estás comunicando claramente, sabrás qué debes
medir y testear. Los sistemas simples son más fáciles de testear.

**Coraje**

- En ocasiones, hay que saltarse las normas, romper el flujo, romper la mitad
de los tests. Después de unos días de duro trabajo (y coraje), los tests
deberían volver a estar bien.
- Otro movimiento de coraje es el de desechar código.
- Si no tienes los tres primeros valores en su lugar, el Coraje por sí mismo
no es más que hackear y crackear el sistema.

## Principios básicos

Un valor puede ser vago, un principio es más concreto.

1. **Feedback rápido**: el tiempo entre una acción y su feedback es crítico
para aprender (semanas mejor que meses, minutos mejor que dias).
2. **Asumir simplicidad**: tratar cualquier problema como si pudiera ser resuelto
con una simplicidad ridícula. Confía en tu habilidad para añadir complejidad en
el futuro, cuando realmente la necesites.
3. **Cambio incremental**: cualquier problemas se resuelve con una serie de
cambios pequeños que poco a poco van marcando la diferencia.
4. **Acepta el cambio**
5. **Trabajo de calidad**: a nadie le gusta un trabajo descuidado, a todo el
mundo le gusta hacer un buen trabajo.

Existen otros principios, que no son tan céntricos como los anteriores, pero
que tamibén se tienen en cuenta:

6. **Enseña a aprender**: en lugar de adoctinar, o mandar, se pueden suerir
estrategias, lecturas, para que cada uno aprenda sus lecciones.
7. **Inversión inicial pequeña**: el foco que un presupuesto ajustado genera
te incentiva a hacer un excelente trabajo en todo lo que haces, pero no recortes
mucho o no podrás hacer nada interesante.
8. **Juega para ganar**: en lugar de trabajar *según el manual* (para que cuando
todo acabe no te puedan echar la culpa del fracaso), en XP cada miembro del
equipo hace lo que está en su mano para ayudar al equipo a ganar.
9. **Experimentos concretos**: cada vez aque tomas una decisión y no la
compruebas (con un experimento) puedes haber tomado la decisión incorrecta.
10. **Comunicación honesta y abierta**: los programadores deben de ser libres
de reportar malas noticias a clientes y managers, de entregarlas pronto y
de no ser castigados por ello.
11. **Trabaja con los instintos de la gente, no contra ellos**: puedes hacer
incapié todo lo que quieras sobre una buena práctica (quizá la mejor que conozcas),
pero cuando la presión hace efecto, si la práctica no arregla un problema
inmediato será descartada por la gente.
12. **Aceptar responsabilidad**: si el equipo llega a la conclusión de que cierta
tarea debe ser hecha, alguien elegirá hacerla, aunque sea la peor tarea del
mundo.
13. **Adaptación local**: no hay que seguir todas las normas a rajatabla, tú debes
decidir cómo hacer software. Cambia, mide y adapta lo que mejor trabaje para ti.
14. **Viaja ligero**: el equipo solo arrastra lo que deban arrastar para producir
valor al cliente, normalmente, solo código y tests.
15. **Mediciones honestas**: especialemente las horas trabajadas.

## Vuelta a lo básico

**Codificar**

- Es la única actividad con la que sabemos que sin ella no podemos tener software.
Escribir código simplemente está bien para pequeños programas, pero para
appliaciones más complejas necesitamos algo más allá de la programación.
- El código te da la oportunidad de comunicarte clara y concisamente. Si tienes una
idea y me la explicas, probablemente yo te malinterprete. Si la codificamos juntos,
puedo ver tus ideas en la lógica que escribes. Esta comunciación se transforma
fácilmente en aprendizaje. Veo tus ideas y tengo las mias propias. Así que ahora
es mi turno de codificar y enseñarte mis ideas.
- Ya que no podemos prescindir del código (ya que si no no existiría el programa),
deberíamos usarlo para tantos propósitos sobre ingenieria del software como fuera
posible: comunicar, describir algoritmos, tests, especificaciones, ...

**Testear**

- Cualquier cosa que no puede ser testeada, no existe. PUedes creer que has
implementado tu diea,pero si no puedes probarla, ¿cómo puedes estar seguro?
- También se pueden escribir tests para requerimientos no-funcionales:
rendimiento, cumplimentación de estándares de codificación, ...
- Los tests te dicen cuando has terminado. Cuando ya no puedes pensar en
ningún test erróneo más, es cuando has terminado completamente (ya no tienes
ningún código de producción más que escribir).
- Lamentablemente, la mayoría del software se entrega sin haber escrito tests,
luego los tests automáticos no son esenciales, entonces ¿porqué considerarlo
como una actividad básica?
- Una respuesta para el largo plazo es que los tests mantienen viva la
aplicación por más tiempo, y permiten a los programadores a realizar cambios
durante más tiempo también.
- La razón a corto plazo es que programar con tests es más divertido, ya que
uno programa con mucha más confianza, puede tomar mayores riesgos programando
y programará más rápido.

**Escuchar**

- Como programador, no sabes nada del negocio, así que debes preguntar. Y si
vas a hacer preguntas, mejor que estés preparado para escuchar las respuestas.
- Los programadores ayudan al Cliente a entender lo que es difícil y lo que es
fácil de implementar.
- Los temas que tienen que ser comunicados son comunicados cuando necesitan ser
comunicados y con el nivel de detalle que necesitan ser comunicados.

**Diseñar**

- Diseñar es crear una estrucutra que organice la lógica del sistema.
- Buen diseño: un cambio en una parte del sistema no siempre requiere un cambio
en otra parte del mismo. También asegura que cada pieza de la lógica del sistema
tiene un solo lugar. Mueve la lógica cerca de los datos con los que opera. 
Permite la extensión del sistema con cambios en un solo lugar.

**Conclusión**

Codificas porque quieres algún tipo de software. Testeas para saber cuando has
terminado de codificar. Escuchas para saber qué codificar o qué testear.
Diseñas para poder codificar, testear y escuchar de forma indefinida.

## Parte II: la solución

Prácticas

- **Juego de planificación**: lo que se va a entregar es una mezcla entre las prioridades
del negocio y las estimaciones técnicas.
- **Releases pequeñas**: cada release debería ser tan pequeña como fuera posible,
conteniendo los requisitos más valiosos para el negocio.
- **Metáfora**: la metáfora simplemente ayuda a todo el mundo en el proyecto a
entender los elementos básicos y sus relaciones. Buscando una metáfora es probable
que lleguemos a una arquitectura que sea fácil de comunicar e implementar.
- **Diseño simple**: ejecuta todos los tests, no tiene lógica duplicada, comunica
cada intención importante a los programadores y tiene el mínimo número de clases
y métodos (elementos) posibles.
- **Testear**: cualquier funcionalidad del programa sin un test automático
simplemente no existe. Existen tests unitarios y funcionales. El resultado es un
programa que es cada vez más confiado con el tiempo y que es capaz de aceptar
cambios.
- **Refactorizar**: cuando se añade una funcionalidad, los programadores se preguntan
si pueden hacer el programa más simple, sin que ello cause el fallo en algún test.
No se refactoriza bajo especulación. Uno refactoriza cuando el sistema lo pide.
Cuando el sistema requiere que se duplique código, está pidiendo una refactorización.
- **Programación en parejas**: hay dos roles: uno piensa acerca de la mejor forma de
implementar el método en el que se está trabajando mientras que el otro piensa de
una forma más estratégica.
- **Propiedad colectiva del código**: cualquiera que vea una oportunidad para añadir valor
a cualquier porción del código está obligado a hacerlo en cualquier momento.
- **Integración contínua**: el código es integrado y testeado muchas veces a lo
largo de un día de trabajo.
- **Semana laboral de 40 horas**: uno quiere estar fresco y con energía cada mañana, y cansado y
satisfecho cada noche. Trabajar muchas horas extras durante mucho tiempo es un
síntoma de un serio problema en el proyecto.
- **Cliente conel equipo**: un cliente real se sienta con el equipo, disponible para
responder a cualquier pregunta, resolver disputas y establecer prioridades a pequeña
escala.
- **Estándar de codificación**: un estándar de codificación es adoptado voluntariamente
por el equipo al completo.

- Cómo unas prácticas son apoyadas por otras para reforzar sus debilidades:

1. Juego de planificación: cliente con el equipo, releases cortas.
2. Releases cortas: juego de planificación, integración contínua, tests y 
diseño simple.
3. Metáfora: tests, cliente con el equipo, refactorizar.
4. Diseño simple: refactorizar, metáfora y programación en parejas.
5. Tests: diseño simple, programación en parejas.
6. Refactorizar: propiedad colectiva del código, estándar de codificación, 
programación en pareja, diseño simple, tests, integración contínua,
semana laboral de 40 horas.
7. Programación en pareja: estándar de codificación, semana laboral de 40 horas,
metáfora, tests y diseño simple.
8. Propiedad colectiva del código: integración contínua, tests, programación en 
pareja, estándar de codificación
9. Integración contínua: tests, programación en pareja, refactorizar.
10. Semana laboral de 40 horas: en general, todas las prácticas llevan a trabajar
jornadas razonables.
11. Cliente con el equipo: escriben tests funcionales, priorizan a pequeña escala
y toman decisiones.
12. Estándar de codificación: programación en pareja y refactorizar.

### Estrategia de gestión

- El trabajo del manager es indicar lo que necesita ser echo, pero sin asignar el
trabajo a nadie en concreto.
- Un manager está para guiar al equipo cuando éste lo necesita
- Es el manager quien tiene que tomar las riendas de adaptar XP a las condiciones
locales del equipo.
- Un manager no impone mucha sobrecarga, es decir, burocracia.

**Métricas**

- La herramienta básica de gestión en XP son las métricas.
- El medio de las métricas es un gran gráfico bien visible, el manager lo actualiza
periódicamente.
- No tiene que haber demasiadas métricas, y se debe estar preparado para retirar
aquellas que ya no sirven para su propósito.
- Cualquier métrica que se aproxime a su 100% tiene muchas probabilidades de ser
inútil.

**Coaching**

La gestión está dividida en dos roles: el coach y el que realiza el seguimiento.
El coaching se encarga principalmente de la ejecución técnica y de la evolución
de los procesos.

**Seguimiento**

- Si no mides lo que pasa en la realidad contra una predicción que hiciste en el
pasado, nunca aprenderás.
- Planificar es siempre emocional.

**Intervenciones**

- Cuando hay problemas que el equipo no puede solucionar, es el manager quien
tiene que intervernir, pero con cuidado, si abasallar, o perderá toda la
confianza del equipo.
- Ejemplos: cambios de personal, se necesitan cambios en los procesos del
equipo, matar el proyecto

## Estrategia del entorno

- Tomar control del entorno físico envía un mensaje bastante poderoso al
equipo
- Tomar el control de su entorno físico es el primer paso hacia la toma de
control de cómo ellos trabajarán en conjunto
- La división de poderes entre Negocio y Desarrollo no quiere decir que
haya que evitar hacer los trabajos difíciles
- La mayoría de las veces el trabajo será más sencillo de lo que en un
principio te imaginaste. Si no es así, hazlo igual, es por eso por lo
que te pagan

## Estrategia de planificación

- En XP se hace un plan de forma rápida y barata, por lo que hay poca inercia
cuando tenemos que cambiarlo
- Primero, aprende las reglas y síguelas (como estas para planificar). Cuando
estés cómodo con ellas, podrás saltártelas para mejorar
- El objetivo del juego de planificación es maximizar el valor del software
producido por el equipo
- Estrategia: invertir lo mínimo posible para poner la funcionalidad más valiosa
en producción tan rápido como sea posible
- Jugadores: Desarrollo y Negocio
- Movimientos: exploración, compromiso y pequeñas correcciones (pequeños cambios
frente a grandes cambios, como pequeñas correcciones conduciendo un coche).
- Fase de exploración: qué es lo que el sistema debería hacer finalmente. Escribir
una historia. Estimar una historia. Dividir una historia.
- Fase de compromiso: Negocio elige el alcance y una fecha, Desarrollo se
compromete a entregar todo o parte del alcance en esa fecha. Negocio elige si hace
el alcance menor o alarga la fecha de entrega. Ordenar por valor. Ordenar por
riesgo. Establecer la velocidad. Elegir alcance.
- Fase de pequeñas correciones: actualizar el plan en base a lo que se va aprendiendo.
Iteraciones. Recuperación. Nuevas historias. Reestimaciones.

## Planificación de la iteración

- Las piezas son *tarjetas de tareas* en lugar de *tarjetas de historias*, pero los
movimientos de cada fase son bastante similares
- Fase de exploración: escribir una tarea. Dividir / Combinar tareas
- Fase de compromiso: aceptar una tarea. Estimar una tarea. Establecer factores de
carga (cuánto trabajo tiene cada persona en el equipo). Balancear carga de trabajo.
- Fase de pequeñas correcciones: implementar una tarea. Guardar progreso.
Recuperación. Verificar historia

## Estrategia de desarrollo

- Mientras una pareja está desarrollando, puede actuar como si fuera la única pareja
en el proyecto, como si fueran los únicos que tocan el código. Luego, cambian de
sombrero, como integradores, y están muy atentos a posibles colisiones, conflictos
en el código.
- Propiedad colectiva del código: uno de los efectos de la propiedad colectiva del
código es que el código complejo no vive mucho tiempo. Ademas, tiende a expandir el
conocimiento del sistema alrededor de todos los integrantes del equipo.
- Programación en parejas: no es una persona programando mientras la otra persona
mira. Es un diálogo tratando simultáneamente de programar, analizar, diseñar y
testear. Funciona para XP porque incentiva la comunicación.

## Estrategia de diseño

- Hay dos problemas con lo de diseñar para un futuro: 

1. Las especificaciones pueden cambiar (por lo que el diseño ya no vale para nada)
2. Puedes aprender una mejor manera de hacer las cosas. 

- Si no pasa una de las dos, es mejor diseñar para el futuro pero **yo no me
arriesgo** a que no haya cambios y mucho menos a no aprender nada.

- Cuando tienes delante una gran refactorización, tienes que afrontarla en mucho
pasos pequeños. Mientras estás desarrollando, ves la oporutnidad de hacer un
pequeño cambio. Hazlo. La gran refactoización se irá reduciendo.
- Cuatro reglase del diseño simple:

1. El sistema (código y tests) debe comunicar todo lo que quiere comunicar
2. El sistema no debe contener código duplicado
3. El sistema debería tener el menor número de clases posible
4. El sistema debería tener el menor número de métodos posible

### El papel de los gráficos/dibujos en el diseño

- Pros: si te resulta imposible reducir el número de elementos, si hay una
asimetría obvia, si hay más líneas que cajas; entonces, todo eso son pistas
de un mal diseño. Otra fortaleza es la velocidad de comunicación
- Contras: los gráficos no te pueden dar un feedback concreto (no se pueden
ejecutar)
- Los gráficos no se guardan. Desear que se pudiera guardar un gráfico en una
pizarra es una señal de que el diseño no ha sido comunicado, ni al equipo ni
al sistema

## Estragia de testeo

- Los tests escritos por unos dan confianza al resto del equipo
- Se puede aprender de los tests, en dos casos: 

1. tests debería fallar y no falla -> código mal
2. tests no debería fallar y falla -> código mal

- El trabajo del tester es el de traducir las ideas vagas de test de un Cliente
a unos tests reales, automáticos y aislados.

# Parte III: implementando XP

**Adoptando XP**

- Cómo adoptar XP: elige tu peor problem, resuélvelo como XP te dice y cuando
ya no sea tu peor problem, repite el proceso.

**Adoptando XP a proyectos existentes**

- ¿cómo comenzar a escribir tests para un código que ya existe? ¿todo de golpe?
No, poco a poco

## Distintos papeles en XP

**El papel del Programador**

- Su trabajo no se acaba cuando el ordenador entiende qué es lo que tiene que
hacer. Su trabajo más importante es la comunicación con el resto de la gente
- Una habilidad necesaria es *pair programming*
- Otra habilidad necesaria es el hábito de la simplicidad
- Tienes que estar dispuesto a aceptar la propiedad colectiva del código
- Sin coraje, XP simplemente no funciona

**El papel del Cliente**

- El Programador sabe *cómo* programar. El Cliente sabe *qué* programar
- Habilidades que el Cliente debe aprender: escribir buenas historias de usuario,
influir en el proyecto sin ser capaz de controlarlo o manipularlo
- El Cliente tiene que tomar decisiones
- Debe aprender a escribir historias de usuario
- Debe aprender a escribir tests funcionales

**El papel de Tester**

- Es el responsable de ayudar al Cliente a elegir y escribir los tests funcionales

**El papel de quien realiza el seguimiento**

- Debe hacer muchísimas estimaciones y darse cuenta de si la realidad del proyecto
coincide con ellas
- Su trabajo es cerrar el ciclo del feedback
- Debe mantener un ojo en el aspecto global del proyecto
- Es como un historiador del proyecto. Mantiene un log de los tests funcionales
que pasan y los errores/bugs reportados
- La habilidad que más necesita cultivar es la habilidad del recoger informacion que
necesita sin molestar a los demás ni interponerse en su trabajo diario

**El papel del Coach**

- Se debe de dar cuenta de cuando la gente se desvía del proceso definido por el
equipo y conseguir llevar esto a la atención del equipo
- Debe ser consciente tambien de cómo otros equipos están usando XP, qué son las
ideas detrás de XP y cómo esas ideas están relacionadas con la situación actual
del equipo
- Los Programadores confiados y agresivos son valiosos precisamente porque ellos
son confiados y agresivos

**El papel del Consultor**

- Los equipos XP son my buenos técnicamente, pero de bez en cuando necesitan a
un experto
- Lo que el equipo de XP no va a hacer va a ser dejar al experto que trabaje
solo en el problema
- Lo que harán, probablemente, será deshacerse de todos los cambios que hizo
el Consultor y volver a hacerlos por ellos mismos

## Qué hace que XP sea tan difícil

- Primordialmente las emociones (especialmente el miedo) son lo que hace que XP
sea tan duro de practicar y aplicar
- Debes aprender a no estar satisfecho con la complejidad, de no descansar hasta
que no puedes imaginar nada más sencillo funcionando
- Las emociones forma parte de las persones, por eso, XP no trata de eliminarlas
sino que acepta e incentiva que las personas expresen sus sentimientos

## Cuando no deberías intentar XP

- La mayor barrera para el éxito de XP en un proyecto software es la cultura
empresarial, la cultura de la empresa que quiere implantarlo
- Una cultura que no es compatible con XP is aquella que *obliga* a sus trabajadores
a realizar largas jornadas de trabajo por el hecho de *comprometerse con la
compañía*.

