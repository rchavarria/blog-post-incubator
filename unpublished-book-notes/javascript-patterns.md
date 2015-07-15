--
layout: post
title: "JavaScript patterns"
date: 
author: Rubén Chavarría
comments: true
categories: 
- personal
- book reviews
- javascript
published: true
footer: false
sidebar: true
---

##### de Stoyan Stefanov

{% img left http://akamaicovers.oreilly.com/images/9780596806767/lrg.jpg %}

## Por qué lo he leído

Cuando leí [Learning JavaScript design patterns], de Addy Osmany, me quedé con
ganas de más, me equivoqué de libro. El que realmente quería leerme para
aprender sobre patrones en JavaScript era éste. Pero me dejé llevar por la
*fama* de Addy.

El objetivo de leer estos dos libros era el de profundizar en el uso de patrones
en JavaScript, poder trasladar conocimientos adquiridos en Java, a JavaScript.

<!-- more -->

## Qué esperaba

Esperaba que fuera un libro muy parecido al mítico [Design patterns], como si
fuera un catálogo de patrones disponibles, con sus descripciones, situaciones
donde es recomendable usarlos y también, por qué no, ejemplos de proyectos
reales.

## Qué encontré

Por supuesto, encontré muchos patrones, pero eso no es lo más llamativo.

El autor comenta varios aspectos del lenguaje que son cuanto menos, curiosos. No
sé si llegan al nivel de [JavaScript, the good parts], pero deben de andar 
cerca. 

Además, alguno de los patrones difieren de la idea que yo tenía, son muy
distintos a patrones con el mismo nombre, pero en otros lenguajes de
programación.

## Conclusiones

Junto con [JavaScript, the good parts], considero que éste es un libro imprescindible
para cualquier desarrollador que quiera dominar el lenguaje.

Explica en profundidad algunos de los patrones más usados en todo tipo de
proyectos. Quizá, con el nuevo estándard recién aprobado, algunos de ellos
(como la *herencia por prototipos*) queden algo obsoletos, creo que es
un libro imprescindible para entender el lenguaje.

## Qué he aprendido

Puedes consultar mis [notas sobre el libro] si quieres ver todo lo que me
ha llamado la atención de el mismo. Pero destacaría lo siguiente:

- Una regla que se repite en muchos patrones: **los miembros a compartir deben
ir en el prototipo, nunca en el `this`**
- Los constructors implícitamente devuelven `this`, incluso si no hay un
`return`, pero tu puedes devolver lo que quieras, incluso puedes redefinir el
constructor. Esto se hace, por ejemplo, en el patrón Singleton
- En la declaración de una función, su definición también sufre *hoisting*, no
solo la declaración
- Métodos clásicos de herencia y herencia de prototipos, aunque esto vaya a
cambiar con nuevas versiones del lenguaje, con la aparición de clases
- Unas cuantas sugerencias para desplegar grandes aplicaciones: combinar scripts,
minificarlos, utilizar compresión de archivos, uso de cabeceras HTML, uso de
CDNs, dónde situar las etiquetas `<script>`, enviar en trozos grandes ficheros
HTML.

## Recursos relacionados

- [notas sobre el libro]
- [Learning JavaScript design patterns], libro de Addy Osmany
- [Design patterns], libro de The Gang of Four
- [JavaScript, the good parts], libro de Douglas Crockford

[notas sobre el libro]: https://github.com/rchavarria/blog-post-incubator/blob/master/published-book-notes/javascript-patterns-by-stoyan-stefanov.markdown
[Learning JavaScript design patterns]: /blog/2015/05/29/learning-javascript-design-patterns/
[Design patterns]: http://www.amazon.com/Design-Patterns-Elements-Reusable-Object-Oriented-ebook/dp/B000SEIBB8
[JavaScript, the good parts]: http://www.amazon.com/JavaScript-Good-Parts-Douglas-Crockford/dp/0596517742

