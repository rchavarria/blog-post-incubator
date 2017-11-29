# Charlas

## [Seamos hipsters, pensemos en Serverless](https://2017.codemotion.es/agenda.html#5649626120060928/5768955947909120)

**Feedback**

El ponente tenía mucha labia, era dicharachero y simpático, lo que hizo la charla divertida.

La presentación contenía mucho texto, podria haber sido más visual. La historia estaba bien hilada. Sentí un poco de publicidad de Azure pero fue muy práctica. +1 a la practicidad y a la demo en vivo (aunque fue super rápida)

**Aprendizaje**

Serverless = despreocuparse de la infraestructura (¿eso no es un IaaS o o PaaS o SaaS?). Infraestructura administrada, gestionada, orienta a eventos.

Servicios serverless (ofrecidos por Azure): cognitivos, almacenamiento, base datos, event bus, Functions

Las Azure Functions constan de:

•	Triggers: cómo y cuándo se llama a la Function. Vamos, que reaccionan a eventos: llamada http, modificación de una tabla de la BD, nuevo item en una cola,...
•	Binding: de dónde entran y salen los datos (parámetros y valores devueltos). Puede ser desde/hacia casi cualquier servicio: storage, db, colas,...

# [Clean architecture](https://2017.codemotion.es/agenda.html#5649626120060928/5098174129635328)

**Feedback**

Buena presentación, muy visual y cuidada. En algún momento podría haber sido algo interactiva. El título no cuadra con el contenido de la charla. Dejando de lado las espectativas, el contenido ha sido muy interesante, con un repaso a muchas arquitecturas, con ejemplos de algunas de ellas.

**Aprendizaje**

Evolución de las arquitecturas: monolito, 3 capas, N capas, MVC, CQRS, Clean. Aunque mezcló algunos conceptos en el „timeline“, que no serían exactamente arquitecturas.

Clean arquitecture es prácticamente lo mismo que Hexagonal architecture, donde lo más importante es el concepto de Inversión de Dependencias

Arquitectua que no conocía, y tampoco entendí muy bien: space based architecture. ¿Es distribuida?

# [Progressive wep apps orientadas a componentes con Vue.js](https://2017.codemotion.es/agenda.html#5649626120060928/5699320770723840)

**Feedback**

El ponente hablaba muy rápido, pero eso sí, tenía muy claro qué quería contar y cómo contarlo. La presentación tenía muchísmo contenido, por lo que el ritmo fue rapidísimo. Se quedó corto de tiempo, pero hay que contar que hubo problemas técnicos para comenzar.

**Aprendizaje**

Qué son las PWAs

Concepto de App Shell: mínimo código/contenido para que la app funcione offline. Sería el esqueleto de la app. Se cachea. Luego, el contenido dinámico se carga del servidor.

Concepto de Web Push Notifications

Existe una plantilla para crear PWA con Vue.js de forma rápida. Ya trae Service Worker con cacheo y tal.

EZV: ¿podría utilizarse WPushN para monitorización? Probablemente necesitemos un Service Worker. Existe una traspa con código.

# [El despertar de la zona de confort](https://2017.codemotion.es/agenda.html#5649626120060928/6007471319547904)

**Feedback**

Comenzó nerviosa (los problemas técnicos del principio no ayudaron), pero logró sobreponerse con esfuerzo. Fue una ponente divertida, sencilla, cercana y natural. La presentación fue muy, muy visual, con pocos textos y contaba con unos chistacos preparados que hicieron la charla muy divertida.

**Aprendizaje**

Podríamos decir que existen diferentes fases a la hora de salir de la zona de confort:

•	Curiosidad: tengo una idea
•	Ganas: hacer
•	Consumir conocimiento: aprender, comunidades
•	Difundir conocimiento: compartir, blog, stack overflow, charlas, organizar eventos (creo que al final se puede resumir en socializar con la gente)
•	Hablar en público
•	Motivar la curiosidad: hacer que otros comiencen este camino

¿Por qué „salir de la z.d.c.“ tiene que significar hablar en conferencias?

# [Taller: testing fácil con docker: gestiona dependencias y unifica entornos](https://2017.codemotion.es/agenda.html#5693168230072320/6560049195384832)

**Feedback**

El ritmo fue muy rápido, pero para ser un taller en vivo podríamos decir que „no falló nada“ a la hora de presentar. Se nota que el ponente venía muy preparado. La presentación contiene muchísimo contenido, lo que permite seguir el taller luego desde casa. Fue difícil hacer en taller en vivo, debido a limitaciones de conexión para tanta gente, pero es algo entendible

**Aprendizaje**

Unos cuantos comandos para docker: docker run, docker images, docker ps, docker rm

Parámetros interesantes: -it para ejecutar un comando dentro del contenedor, -d para ejecutarlo en background (perfecto para servidores), -e para pasar variables de entorno, -p para exponer puertos, -v para montar volúmenes (poderoso con -v „$PWD“), --rm para borrar el contenedor una vez terminado, -w para definir el directorio de trabajo

Con docker NO contaminas tu entorno, y puedes tener varias versiones de tu entorno (varios javas, pythons, ...)

Problemas de docker: permisos de usuarios, docker in docker (vs docker siblings), compartir ficheros

Puedes usar docker para tener diferentes versiones de tus herramientas „a la vez“

Plugin de docker para Jenkins si usas pipelines

**Notas en crudo del taller:**

- cada "docker run" crea un contenedor
- "docker run -it <image> /bin/sh" para ejecutar bash dentro del contenedor
- "-d" opción ejecuta el contenedor en background
- docker stop: para contenedor
- docker rm: borra definitivamente el contendor
- "-e" pasa vbles entorno
- "-p" expone puertos (traspa 52)
- Con docker NO contaminas tu entorno, y puedes tener varias versiones de tu entorno (varios javas, pythons, ...)
- "-v "$PWD":/data" mapea el directorio de trabajo del host al /data del contenedor
- se puede publicar cualquier carpeta en un servidor web nginx haciendo
    cd <la carpeta que me da la gana>
    docker run -p 9000:80 -v "$PWD":/usr/share/nginx/html:ro -d nginx
- ":ro" read-only?
- eso también sirve para mapear mi espacio de trabajo en local con el directorio que publica la imagen de apache. modifico mis ficheros en local (mapeados al apache), guardo, refresco el browser y... tachán
- (traspa 76) casos de uso de docker. uno de ellos es utilzarlo para comandos, es decir, en lugar de instalar java, tengo el contenedor con java y "ya tengo" el comando java disponible
- mega comando:
    docker run
    --rm (borra el contenedor cuando termines)
    -v "$PWD":/data (mapeo de directorios)
    -w /data (workind directory del comando ejecutado en el contenedor)
    maven (imagen)
    mvn package (finalemente, el comando a ejecutar en el contenedor)
- la salida del anterior comando, por ejemplo "/data/target/xxxx.jar" resulta que lo tengo disponible en el host, en $PWD/target/xxx.jar  (maaaagic)
- ¿qué habría que hacer para ejecutar los tests en node?
  1. git clone
  2. cd <directorio raiz del proyecto>
  3. docker run --rm -v "$PWD":/data -w /data <imagen node> npm install;npm test (o el comando karma que haga falta)
  4. el resultado de los tests los tienes en el $PWD del host
- (traspa 98) Pipeline de docker que ejecuta los tests en mvn
- (traspa 106) enter the Docker pipeline plugin, para manejar contenedores con comandos en el pipeline, en lugar de utilizar el paso "sh" del pipeline
- el plugin: mapea directorios, gestiona permisos (docker se ejecuta como root), borra el contendor,...
- la librería "test containers" (parece que solo para java) permite que tus tests digan que dependen de ciertos contenedores para ejecutarse. el Docker pipeline plugin permite lanzar varios contenedores también
- (traspa 121) docker siblings, monantdo un volumen el "comando" docker, para tener varios contenedores hermanos, nada de un docker dentro de un docker ("-v ...docker.sock:....docker.sock)
- (t. 124) habilitar docker en la imagen de docker, porque por defecto, jenkins no tiene un cliente docker. trion/jenkins-docker-client es una imagen que tiene un cliente docker

# [Las reglas que hay que romper para que tu equipo de desarrollo sea el más rápido](https://2017.codemotion.es/agenda.html#5693168230072320/5105557983723520)

**Feedback**

El ponente comenzó muy bien, divertido. Siguió con un discurso pulido y con muy buen ritmo. La presentación estaba muy trabajada, a veces minimalista, lo que daba valor y centraba el foco en el mensaje. Muy buena. Saqué unas cuantas ideas a implementar/proponer en el equipo.

**Aprendizaje**

Distintas velocidades de desarrollo: hackathon (cualquier cosa vale para ir rápido), startup, banca (tienes recursos, dinero y objetivo a largo plazo, matas moscas a cañonazos). Startup sería la „correcta“, abriendo camino iregular por la selva, sin un rumbo fijo pero un objetivo más o menos conocido.

Todo producto debería contar con un Product Manager, que decida qué hay que hacer y qué no. Debe tener muy claro hacia dónde ir (road-map)

Hacer sólo lo necesario, nada de meta-trabajo. Practicidad, cuidado con las abstracciones, no te las inventes.

„Cuando pones una ley, tienes que poner un policía“, reglas de estilo,...

„La deuda técnica es la hipoteca del código“, quien la hace la paga, no vale que unos limpien y otros ensucien dentro del equipo.

El usuario es más importante que: optimizar, abstraer, reutilizar, automatizar,...

Time-suckers: hay que resolver la causa raiz de los problemas, no solo las consecuencias

Coordinazión: requiere transparencia. Que todos sepan qué están haciendo los demás

EZV: Que todos sepan qué están haciendo los demás

Ship, ship, ship: soltar laster, cuanto antes a producción

EZV: se podrían liberar versiones internas?

El equipo: todos deben pensar en el usuario, cómo mantener la motivación

EZV: tiempo de slack, los viernes?

# [¿Qué es un senior developer?](https://2017.codemotion.es/agenda.html#5693168230072320/4878640902832128)

**Feedback**

Pese a problemas técnicos, el ponente se mantuvo tranquilo. Estaba bien preparado y el ritmo fue el correcto. La presentación fue agradable y visual. Se agradeció que en ciertos momentos se apoyara en historias para transmitir el mensaje.

**Aprendizaje**

Qué no es un senior? Que lo diga el título, que sea caro, que escriba código complejo, que lleve mucho tiempo en la empresa

Qué es un senior? Cuestiona procesos, prácticas y dogmas, alza la voz. Aporta datos para respaldar sus teorías. Senior es madurez

4 principios personales:

1.	Confianza, fiabilidad: no prometas algo que no vas a cumplir
2.	Responsabilidad, madurez es cómo afrontas los errores (porque seguro que los vas a cometer)
3.	Flexibilidad: no te ligas a una única herramienta, lenguaje, tecnología
4.	Pragmatismo: no todo es escribir código, sabe dónde quiere llegar y conoce los recursos que le llevarán allí (herramientas, lenguajes, técnicas,...)

5 reglas para el trabajo en una empresa

1.	Escucha y aprende de los demás
2.	Lidera dando ejemplo, proactividad
3.	Enseña a los demás, ofrece ayuda
4.	Cuestiona los procesos, aporta soluciones (no te quedes en la queja fácil)
5.	Ayuda a mejorar la cultura de la empresa

Los seniors „planifican“ su carrera, deciden su próximo paso

# [El informático](https://2017.codemotion.es/agenda.html#5693168230072320/5145563993473024)

**Feedback**

Otra charla con problemas técnicos. No importó mucho, no había mucha presentación que mostrar. Solo mensaje. Me encantó, muchas pregunas, muchas reflexiones. Removiendo la conciencia. Podría haber servido como keynote para cerrar el evento.

**Aprendizaje**

Nada que aprender en sí, pero mucho para reflexionar. ¿qué es un informático? ¿somos conscientes del poder que tenemos? ¿qué pensamos de la manipulación de la información? ¿estás realmente en el trabajo que deseas? ¿tu trabajo está alineado con tus valores? ¿estamos haciendo lo posible para dejar un mundo mejor? Tenemos el deber de educar a los no-informaticos de los peligros de ciertos algoritmos.

