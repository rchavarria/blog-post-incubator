# Lista de reglas de PHP_CodeSniffer

- ¿has conducido alguna vez en el extranjero? o si has ido de acompañante, ¿has prestado atención a la carretera?
- es todo tan distinto. pero a la vez es prácticamente igual a conducir en tu propio país (quitando alguna excepción como Inglaterra o Japón, que conducen por la izquierda).
- seguro que encuentras los mismos elementos: semáforos, cruces, rotondas, carreteras de doble sentido, autovías, y **normas**.
- las normas de circulación no son las mismas en todos los lugares, pero podríamos encontrar algunas normas básicas que sí lo son
- esas normas básicas son las que nos permiten conducir en otros países con una cierta confianza

- escribiendo código dentro de nuestro equipo de trabajo ocurre algo similar
- cada uno tenemos nuestro estilo a la hora de escribir código: nombrar las variables, espaciado, paréntesis, indentación,...
- si tuviéramos total libertad para desarrollar como nos apeteciera, el trabajo en equipo sería mucho más duro
- por eso conviene tener unas ciertas normas, unas **reglas** básicas de cómo escribir código, para que todos los miembros del equipo escriban código acorde a un cierto *estándar*.

- Aquí es donde aparece [PHP_CodeSniffer], una herramienta de análisis estático de código PHP que genera informes sobre qué partes del código de nuestro equipo violan las reglas o el estándar que previamente definió el equipo

<!-- more -->

## Reglas

- cada una de esas reglas puede hacer referencia a aspectos muy distintos de nuestro código: indentación con espacios o tabuladores, apertua de llaves (`{`) en la misma línea o en la siguiente, sintaxis a la hora de manipular arrays (`array()` o `[]`),... 
- 

