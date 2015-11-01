En el [post anterior] contaba que me gusta aprender, y que una de las mejoras
formas era practicando. Y que actualmente estaba usando la plataforma
[exercism.io] para ello, concretamente el [track de ECMAScript] para practicar
escribiendo código en ES2015. Es muy fácil decir que te gusta aprender, y que
te gusta practicar. En esta ocasión lo demuestro. 

He grabado un breve screencast, de menos de 10 minutos, donde muestro cómo de
fácil es usar exercism.io. En el screencast resuelvo un ejercicio llamado
*Robot name*, donde se trata de generar nombres aleatorios para cada uno de los
robots que crea el cliente de la clase `Robot`.

<!-- more -->

## Screencast

<!--   Y AQUI INSERTAR EL SCREENCAST -->

El proceso a seguir es muy sencillo. El primer paso es descargar el problema
mediante el comando:

``` bash
exercism fetch ecmascript robot-name
```

el cual indica a exercism.io obtener un ejercicio del track de ECMAScript
llamado robot-name.

Una vez descargado, podemos leer el fichero `README` para saber de qué trata el
problema. Lo siguiente que deberíamos leer son los tests, obtenidos
directamente de la plataforma. Los tests nos indicaran qué fichero debemos
crear, y nos darán pistas sobre el código que deberemos escribir. Al final, de
lo que se trata, es de resolver los problemas uno a uno, hasta completarlos
todos.

En ese punto el problema estaría resuelto. Podemos subir nuestra solución a la
plataforma con el comando:

``` bash
exercism submit robot-name.js
```

donde `robot-name.js` es el nombre del fichero donde está implementada nuestra
solución.

Por fin, el último paso, es usar exercism.io para comentar soluciones de otros
usuarios, aprender de las soluciones de otros, e ir iterando sobre nuestra
propia solución para ir perfeccionándola. O al menos para aprender nuevas
técnicas de nuestro lenguaje de programación resolviendo de distintas formas el
mismo problema, a modo de kata.

## Otros screencasts

- [El juego del disparejo]

[post anterior]: /blog/2015/10/25/youve-got-commit/
[exercism.io]: http://exercism.io/
[track de ECMAScript]: http://exercism.io/languages/ecmascript
[El juego del disparejo]: /blog/2014/10/23/screencast-programacion-juego-disparejo/

