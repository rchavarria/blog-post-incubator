# Code: the hidden language of computer hardware and software

##### de Charles Petzold

{% img center /images/2016/code-charles-petzold.png %}

### Por qué lo he leído

Porque era una *recomendación*. [Scott Hanselman] era el invitado en el podcast
[Developer on fire], y lo recomendó como un libro que cualquiera relacionado
con el software debería leer. El año pasado ya leí [The martian], recomendado
públicamente también por Scott. ¿Iba a dejar de pasar la oportunidad? Ni
hablar.

<!-- more -->

### Qué esperaba

Espera encontrar una novela, de ciencia ficción. Scott contaba que el libro
narraba la historia de dos amigos y vecinos que empiezan comunicándose por la
noche a través de la ventana de su habitación con una linterna. Luego la cosa
se complica porque uno de ellos se muda de ciudad. Y así comienza la historia
en el libro.

### Qué encontré

Pero nada de eso. No es una novela en sí. Se parece más a un libro de historia.
Sí, la historia comienza con los dos amigos, pero eso es sólo una excusa para
comenzar a guiarnos por un viaje que comienza por el código morse, código
Braille, y muchos más hasta llegar a explicar cómo funciona todas y cada una de
las computadoras de hoy en día.

### Conclusiones

Estoy absolutamente de acuerdo con Scott, es un libro que debería leer todo
aquel que se dedique al software. Es un repaso increíble de la historia de la
informática. Comienza describiendo el código morse, otra serie de códigos que
terminaron en el código (o alfabeto) Braille, para enlazarlo con el código
binario. Para terminar explicando nuestro sistema decimal.

Después sigue con métodos de transmisión, telégrafo y relés. Y cómo ellos se
relacionan con los códigos binarios. De esta relación aparece los *switches* y
las puertas lógicas. Termina construyendo una máquina capaz de sumar hecha de
relés.

Sigue hacia adelante, agrupando bits en bytes, y construyendo otros circuitos
digitales, como los *latches*, contadores y hasta llega a construir una memoria
RAM.

Sigue relacionando los códigos y el hardware para acabar describiendo el código
máquina de un microprocesador comercial. A partir de ahí, la tecnología avanza
muy deprisa y no se puede explicar en un solo libro (al menos si quieres ser
capaz de levantarlo con la mano), pero explica el código ASCII y otras
codificaciones para representar texto.

Y finalmente, los lenguajes de programación.

Por último sólo puedo decir que me hubiera gustado que nos hubieran enseñado la
historia del software y el hardware de esta forma en la universidad. Todas las
piezas encajan. De hecho, estuvieron ahí mucho tiempo (los relés y los códigos
binarios), pero se tardó 20 o 30 años en unirlos para crear máquinas capaces de
realizar cálculos automáticamente.

### Qué he aprendido

A parte de conocer el origen de toda una industria y que, por cierto, parece
que todos los avances se hicieron entre los años 1950 y 1970, después de esos
años parece que sólo se haya aumentado el número y reducido el tamaño de los
componentes que utilizamos, hay unas cuantas curiosidades que me gustaría
recordar:

- Para algunos parece bastante claro que nuestro sistema numérico se basa en 10
  porque es el número de dedos que tenemos en las manos, y es el número más
  grande que podemos contar con ellos. Me parece discutible, pero no se puede
  negar que lógica tiene, y mucha.
- ¿Por qué un byte tiene 8 bits y no otro número, diez por ejemplo? Parece ser
  que fue el número de bits que usaba IBM porque era muy fácil almacenar
  números en la [codificación BCD]. Después, simplemmente por coincidencia, un
  byte es ideal para almacenar texto, ya que una gran mayoría de lenguajes
  escritos alrededor del mundo necesitan 256 símbolos o menos. También, por
  conicidencia, un byte es ideal para almacenar escalas de grises en imágenes, ya
  que el ojo humano es capaz de diferenciar unas 256.
- Un *nibble* son 4 bits, o medio byte.

Finalmente, el autor aporta un par de ideas sobre un tema que me intersa mucho:
¿la programación es un arte o una ciencia?

Al principio, quienes programaban eran científicos e ingenieros, que eran
capaces de expresar ideas en forma de algoritmos matemáticos.

Pero a lo largo de la historia, mucha gente ha tratado de crear abstracciones,
lenguajes de programación de más alto nivel, para acercar la programación al
mayor número de personas. Es gracias a ello donde tienen cabida personas más
artistas, más creativas.

Me parece una metáfora (o razonamiento incluso) muy bueno y que permite ver dos
caras del desarrollo software que no tienen por qué estar enfrentadas.

[Scott Hanselman]: http://www.hanselman.com/
[Developer on fire]: http://developeronfire.com/episode-083-scott-hanselman-learn-balance
[The martian]: /blog/2015/09/06/the-martian/
[codificación BCD]: https://es.wikipedia.org/wiki/Decimal_codificado_en_binario

