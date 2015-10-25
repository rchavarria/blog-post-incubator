# (01-10-2015) Mantaining Balance while reducing duplication

https://www.youtube.com/watch?v=Is8ThG6Fetg&feature=youtu.be

Mantaining Balance while reducing duplication

comentarios sobre esta charla?

- en los tests, existen los custom matchers, ellos te ayudan a reducir duplicidad en el código. deberían seguir el principio DRY?
- everytime you reduce duplication you increase coupling by introducing new dependencies
- DRY is not about the same characters written twice, is about duplicated CONCEPTS
- una refactorzacón básica para eliminar dupliccidad es "extract method"
- less duplicaton can mean more indirection, and can make code more difficult to read (y más difícil de seguir la pista, porque, para no duplicar, los detalles están dispersos en varios sitios)
- en Ruby, la metaprogramación tamibén puede ayudar a eliminar duplicidad, pero la metaprogramaicón hace el código mucho más difícil de leer
- posible definicón de DRY: "every *piece of knowledge* must have a *single*, *unambiguous*, *authorative representation* within a system
- depend on things which are less likely to change (or abstractions, but abstractions can be everywhere, for example, in ruby)
- OOP in one sentence: "keep it *shy*, *dry* and *tell* the other guy" (shy por lo de encapsulación, y lo de *tell* por lo de *tell don't ask*)
- 

