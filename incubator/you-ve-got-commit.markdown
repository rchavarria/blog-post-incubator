Una de las mejores formas de aprender es haciendo cosas (*learning by doing* dicen los gurús). Y otra forma muy buena es manteniendo conversaciones con profesionales de tu sector. Por todo lo aprendido hay que estar agradecido, y qué mejor forma de agradecer que contribuir a la comunidad, a tu profesión, realizando algún trabajo del que se puedan beneficiar otros. La siguiente historia cuenta un camino que estoy recorriendo, de cómo empezé algo por el simple hecho de aprender y terminé participando en un proyecto open source como es [exercism.io].

> IMAGEN DE EXERCISM.IO, CENTRADA, PARA SEPARAR UN POCO EL CONTENIDO QUE VIENE. MENUDO DIABLO!!!

<!-- more -->

Llevaba un tiempo utilizando [solveet.com] para practicar con pequeños ejercicios de programación. De hecho, utilicé la plataforma con distintos lenguajes que estaba interesado en aprender. Pero poco a poco fui perdiendo la motivación para usarla. No recibía feedback de mis soluciones, de lo cual se pueden deducir dos cosas: que mis soluciones eran penosas o que la mayoría de los usuarios no estaban por la labor de compartir. En realidad, creo que la causa principal era que yo aportaba mi solución tiempo después de la última aportada, así que los usuarios probablemente ya habrían perdido interés en ese problema en concreto. No le puedo echar la culpa a Solveet, es una plataforma estupenda. Si estás buscando algo para practicar, y en español, te lo recomiendo. Disfrutarás de lo lindo.

Con esa falta de motivación, llevaba rondando por la cabeza probar otras plataformas similares, y me decidí por [Project Euler]. Hablaban muy bien de ella, lleva mucho tiempo en funcionamiento y goza de fama, así que tenía que ser buena. Pero no duré mucho. Una de las *normas* de la casa pide que no hagas público tu código con el que resuelves los problemas. Pero ese es uno de los objectivos que busco, que la gente critique mi código y poco a poco vaya aprendiendo.

Por casualidad, vi ésta [entrevista a Katrina Owen], creadora de exercism.io y me pareció que sería buena idea probar la plataforma. Uno de los requesitos es instalar un programa, para poder bajarte problemas a tu ordenador, resolverlos y poder subirlos a la plataforma, lo cual no me llamaba mucho la atención. Pero [Manuel Rivero, en Garajeando], un blog que sigo, tiene varios post de sus soluciones en exercism.io, así que malo no podía ser.

Yo quería practicar resolviendo problemas con ECMAScript 2015. Ahí me llevé el primer chasco. Existía un track para JavaScript, pero no para ES2015. No se por qué, pero miré el código fuente en GitHub de exercism.io. Vi que había un repositorio para ECMAScript, pero en la página no existían esos ejercicios. Descubrí que era porque todavía no tenía el número de problemas necesarios para ser público. Hice un fork del proyecto, y me puse a juguetear.

Me encontré con unos cuantos problemas para ser capaz de montar el entorno de desarrollo y ejecutar los tests: dependencias desactualizadas, comandos que no se ejecutaban bien en Windows (parecía que solo funcionaba en Mac). Después de pelearme un poco con el código y la configuración, con unas pequeñas modificaciones solucioné los problemas que tenía. Subí el código a [mi cuenta de GitHub] e hize un *Pull Request* al proyecto. ¡Y contestaron! Después de pulir un par de detalles (es bastante común para primerizos y también la razón por la que muchos se echan para atrás a la hora de contribuir al open source) aceptaron mi solución. ¡Había contribuido a un proyecto open source!

Pero todavía había cosas que me molestaban. Detalles. *El diablo está en los detalles*, dicen. La verdad es que no recuerdo exactamente qué era, pero tenía *trabajo* por hacer. Pregunté un par de cosas a Katrina, arreglé un par de detalles más, algún Pull Request más, y sin esperarlo:

> You've got commit!

¿Qué es eso? ¿Qué significa? Tuve que leer el correo varias veces. No entendía. bla bla bla, *te han añadido a un par de grupos en GitHub*, bla bla bla, *ermisos de escritura*, bla bla bla, ... ¡Me estaban dando permisos de escritura en el proyecto! Sienta bastante bien saber que estás contribuyendo a un proyecto open source, y que lo están utilizando muchos usuarios.

¿Y ahora qué? Tenía que seguir. No podía dejarlo ahí. Asi que me puse como objetivo que exercism.io tendría su [track de ECMAScript 2015].

Un punto para lograrlo era incorporar al menos 10 ejercicios al track. Fácil. Un poco de trabajo... y conseguido. Pero otro punto requería de varias personas. La idea es que haya varias personas encargadas de gestionar el track, dando feedback a los primeros usuarios, para que no se sientan desamparados, e ir mantenindo el còdigo con nuevos cambios provenientes del proyecto global. Pequeñas tareas comunes a todos los lenguages. 

¡Me quedé flipado! Cuando contacté por email con varios usuarios de exercism.io, sin conocerlos de nada,... ¡Me respondieron todos! ¡Todos! Algunos de ellos no podían embarcarse en el proyecto, pero respondieron. Flipando. Con su ayuda, el track se hizo público y el trabajo duro acaba de comenzar. Ahora toca dar feedback a los usuarios y seguir incorporando ejercicios, para que los usuarios vean que el track está vivo y se animen a seguir practicando sus habilidades como programadores.

Así que, ya hay [track de ECMAScript 2015] en exercism.io. Os animo a probar la plataforma, a practicar, a mejorar y a comentar las soluciones de los demás. Espero veros por allí. Si decides probarlo, verás mi careto.

