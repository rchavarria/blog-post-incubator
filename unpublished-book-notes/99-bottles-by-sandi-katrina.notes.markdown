# [99 bottles of OOP](https://www.sandimetz.com/99bottles)
##### by [Sandi Metz](https://www.sandimetz.com/) and [Katrina Owen](http://www.kytrinyx.com/)

## Introduction

Una refactorizacion no es el resultado final sino el camino. Writing code is the process of working your way to the next stable end point, not the end point itself.

## 1. Rediscovering simplicity

This is the basic promise of Object-Oriented Design (OOD): that if you’re willing to accept increases in the complexity of your code along some dimensions, you’ll be rewarded with decreases in complexity along others. OOD doesn’t claim to be free; it merely asserts that its benefits outweigh its costs. Design decisions inevitably involve trade-offs.

### 1.1. Simplifying code

Imagine a continuum with "most concrete" at one end and "most abstract" at the other. Code at the concrete end might be expressed as a single long procedure full of if statements. Code at the abstract end might consist of many classes, each with one method containing a single line of code.

#### 1.1.1. Incomprehensibly concise

Inconsistent styling makes code harder for humans to parse; it raises costs without providing benefits. Por ejemplo con los if.s o todo if.s o todo ternarios pero no mezcla. al meno en la misma funcion o clase

Duplication of logic suggests that there are concepts hidden in the code that are not yet visible because they haven’t been isolated and named

Terminology: Method versus Message: methods are defined, and messages are sent.

Combining many ideas into a small section of code makes it difficult to isolate and name any single concept. Codigo demasiado conciso suele ser dificil de leer

Code clarity is built upon names.

While it’s difficult to get exact figures for value and cost, asking the following questions will give you insight into the potential expense of a bit of code: How difficult was it to write? How hard is it to understand? How expensive will it be to change? Preguntatelas cada vez que quieras saber si tu codigo es bueno o costoso

#### 1.1.2. Speculatively General

It does many things well but can’t resist indulging in unnecessary complexity.

Programmers love clever code.

Writing it, or suddenly understanding it, supplies a little burst of appreciative pleasure

You must resist being clever for its own sake

#### 1.1.3. Concretely Abstract

The code is DRY, and DRYing out code should reduce costs.

DRY makes sense when it reduces the cost of change more than it increases the cost of understanding the code.

When you choose beer as the name of a method that returns the string "beer," you’ve named the method after what it does right now. En el ejemplo anterior, en lugar de `beer`, el nombre del método podría haber sido `drink`

You should name methods not after what they do, but after what they mean, what they represent in the context of your domain

#### 1.1.4. Shameless Green

Shamelesss green parece demasiado sencilla, demasiado facil, no queremeos parar ahi, pero debemos saber cuando hacerlo. One of the biggest challenges of design is knowing when to stop,

#### 1.2. Judging Code

While having standards of any sort is a virtue, the chance of achieving your standards is improved if they are explicit and quantifiable.

#### 1.2.1. Evaluating Code Based on Opinion

good code not only works, but is also simple, understandable, expressive and changeable.

Our sense of elegance, expressiveness and simplicity is an outgrowth of our experiences when reading and modifying code.

Code that is easy to understand and a pleasure to extend naturally feels simple and elegant.

#### 1.2.2. Evaluating Code Based on Facts

numbers produced by metrics are facts.

Source Lines of Code

SLOC numbers reflect code volume, and while it’s useful for some purposes, knowing SLOC alone is not enough to predict code quality.

Cyclomatic Complexity

counts the number of unique execution paths through a body of source code.

can be used in several ways.

two variants of the same method, you can choose between them based on their cyclomatic complexity.

use it to limit overall complexity.

determine if you’ve written enough tests.

Assignments, Branches and Conditions (ABC) Metric

Fitzpatrick describes the ABC metric as a measure of size, as if ABC is a more sophisticated version of SLOC.

cognitive as opposed to physical size. High ABC numbers indicate code that takes up a lot of mental space. In this sense, ABC is a measure of complexity

#### 1.2.3. Comparing Solutions

## 2. Test Driving Shameless Green

### 2.1. Understanding Testing

The Shameless Green solution strives for maximum understandability but is generally unconcerned with changeability.

### 2.2. Writing the First Test

aunque parezca muy importante. el primer test no lo es tano

Despite its apparent import, the choice you make here hardly matters

while it is important to consider the problem and to sketch out an overall plan before writing the first test, don’t overthink it. Find a starting place and get going, in faith that as you proceed, the fog will clear.

When doing TDD, you toggle between wearing two hats. While in the "writing tests" hat, you keep your eye on the big picture and work your way forward with the overall plan in mind. When in the "writing code" hat, you pretend to know nothing other than the requirements specified by the tests at hand. Thus, although each individual test is correct, until all are written, the code is incomplete.

### 2.3. Removing Duplication

Verses 99 through 3 are nearly identical—they differ only in that the number changes within each verse.

the true and false branches contain many things that don’t vary based on number

de eta form queda un if mucjo mas pequeño

alter the if statement to return only the things that change

The difference between the solution that adds a conditional and the solution that interpolates a variable into a string is that in the first, as the tests get more specific, the code stays equally specific.

as the tests get more specific, the code gets more generic.

### 2.4. Understanding Transformations

the "Transformation Priority Premise" (a blog post that you are urged to scan), Martin defines transformations as "simple operations that change the behavior of code."

se podrian ver las transformaviones como lo contrario a refatorizar?

### 2.5. Tolerating Duplication

as tests get more specific, code should become more generic. Code becomes more generic by becoming more abstract.

One way to make code more abstract is to DRY it out,

herring es un pescado. red herring es algo qye oculta algo mas importsnte

The concept of pluralization is a red herring.[

The fact that "bottle" is duplicated many times signals that there’s an underlying concept that has not yet been unearthed.

Within the domain of the song, "bottle/bottles" represents something important, and that thing is not pluralization.

Code like this pluralize method gets written when programmers take the DRY principle to extremes,

When faced with a situation like this, ask these questions:

Does the change I’m contemplating make the code harder to understand?

When abstractions are correct, code is easy to understand.

What is the future cost of doing nothing now?

If it doesn’t increase your costs, delay making changes.

When will the future arrive, or how soon will I get more information?

patiently tolerating duplication if doing so will help reveal the underlying abstraction.

### 2.6. Hewing to the Plan

hay veces que es mejr esperar a tener mas informacion  . ma ejemplos. para poder decidir mejor la abstraccion a sar

The goal is to use green to maximize your understanding of the problem and to unearth all available information before committing to abstractions.

switched from if to case. These keywords tell a different story.

What does it mean to write if rather than case?

Use of if / elsif implies that each subsequent condition varies in a meaningful way

future readers will feel obliged to closely examine each one.

Readers of case statements expect conditions to be fundamentally the same.

cambiar un if por un case para indicar que las condiciones son muy similares es un agto deluberado de gratitud

is an act of kindness towards your reader. Intention-revealing code is built from the accumulation of such thoughtful acts.

### 2.7. Exposing Responsibilities

Duplication is useful when it supplies independent, specific examples of a general concept that you don’t yet understand.

y eso es un dipliccion qu no vamos a tolerar

code duplicates an example that already exists and so supplies no new information about the problem

Fake It style TDD may initially seem awkward and tedious, but with practice it becomes both natural and speedy. Developing the habit of writing just enough code to pass the tests forces you to write better tests

Kent Beck describes different ways to make tests pass. Three of his "Green Bar Patterns" are: Fake It ("Til You Make It") Obvious Implementation Triangulate

cuidado con ir directamenye a la solucion obvia t pued llecar por el camino equivocado

Fake It style TDD may initially seem awkward and tedious, but with practice it becomes both natural and speedy. Developing the habit of writing just enough code to pass the tests forces you to write better tests

The next Green Bar Pattern is Triangulate, which Beck describes as a way to "conservatively drive abstraction with tests." Triangulation requires writing several tests at once, which means you’ll have multiple simultaneous broken tests. The idea is to write one bit of code which makes all of the tests pass.

consigue varias .copias. del mismo conxpto antes de extraer lo duplucado

expands it from tests to code.

### 2.8. Choosing Names

### 2.9. Revealing Intentions

asi justifica un metodo publico muy pequeño u muy sencillo.

The distinction between intention and implementation […] allows you to understand a computation first in essence and later, if necessary, in detail. — Kent Beck Implementation Patterns (p. 69) Here song is the intention, and verses(99, 0) is the implementation.

### 2.10. Writing Cost-Effective Tests

the first step in learning the art of testing is to understand how to write tests that confirm what your code does without any knowledge of how your code does it.

### 2.11. Avoiding the Echo-Chamber

tests are too tightly coupled to code. Such tests impede change and increase costs.

### 2.12. Considering Options

duplicacion en testear el metoo song escribino toooooda la cancion a mano

you find the duplication distressing, consider the alternatives.

pero eso acopla el test a la implementacion

Assert that the expected output matches that of some other method.

Assert that the expected output matches a dynamically generated string.

This logic already exists in the Bottles class,

Assert that the expected output matches a hard-coded string.

only the third is independent of the current implementation and so guaranteed to survive changes to Bottles

Tests are not the place for abstractions—they are the place for concretions. Abstractions belong in code.

DRY is a very good idea in code, but much less useful in tests. When testing, the best choice is very often just to write it down.

### 2.13. Summary

## 3. Unearthing Concepts

### 3.1. Listening to Change

The arrival of a new requirement tells you two things, one very specific, the other more general.

Specifically, a new requirement tells you exactly how the code should change.

More generally, the need for change imposes higher standards on the affected code.

new requirement arrives, the bar is raised. Code that needs to be changed must be changeable

si el codij no esta abierto a modiicaviones y no sabes po dond emoezar... empieza eliminndo olores del odio

Open Closed Flowchart

### 3.3. Recognizing Code Smells

### 3.4. Identifying the Best Point of Attack

it must be admitted that there is no direct connection between removing the duplication, and succeeding in making the code open to the six-pack

ng sabes como hace que el codigo este abiero. asi que empiezas a eliminar olores. con la esperanza de ncontrar lo en l camino

You don’t have to know how to solve the whole problem in advance. The plan is to nibble away, one code smell at a time, in faith that the path to openness will be revealed.

### 3.5. Refactoring Systematically

Recall that new requirements should be implemented in two steps. First, you rearrange existing code so that it becomes open to the new requirement. Next, you write new code to meet that requirement. The first of these steps is refactoring.

you should never change tests during a refactoring. If your tests are flawed such that they interfere with refactoring, improve them first, and then refactor.

### 3.6. Following the Flocking Rules

la abstraccion de la qu habla es la abstraccion detra de codio duplicado

The good news is that you don’t have to be able to see the abstraction in advance. You can find it by iteratively applying a small set of simple rules. These rules are known as "Flocking Rules",

Flocking Rules Select the things that are most alike. Find the smallest difference between them. Make the simplest change that will remove that difference.

### 3.7. Converging on Abstractions

#### 3.7.1. Focusing on Difference

sameness is easier to identify, difference is more useful because it has more meaning. DRYing out sameness has some value, but DRYing out difference has more.

#### 3.7.2. Simplifying Hard Problems

Programmers love hard problems.

It’s no wonder that many programmers gravitate towards starting a problem at its most confusing part.

It is common to find that hard problems are hard only because the easy ones have not yet been solved.

#### 3.7.3. Naming Concepts

The general rule is that the name of a thing should be one level of abstraction higher than the thing itself.

el titulo de las columnas sera el titulo de las abstraccion

One way to identify the category is to imagine the concrete examples as rows and columns in a spreadsheet.[

#### 3.7.4. Making Methodical Transformations

Naming things after domain concepts improves communication between you and the folks who pay the bills. Only good can come of this.

When you’re struggling to find a good name but have only a few concrete instances to guide you, it can be illuminating to imagine other things that would also be in the same category.[

Flocking Rules Select the things that are most alike. Find the smallest difference between them. Make the simplest change to remove that difference: parse the new code parse and execute it parse, execute and use its result

#### 3.7.5. Refactoring Gradually

la idea del punto 3 es hacer cambios linea a linea. no mas alla de cambiar un sola lknea

Flocking Rules Select the things that are most alike. Find the smallest difference between them. Make the simplest change to remove that difference: parse the new code parse and execute it parse, execute and use its result delete unused code

como añadir un parametro a una funcion y llamar a esa funcoon pasandole el parametro haciendo cambio de una sola linea? meiante parametros opcionales y refactorizacion gradual

añadir libro a l lista

In his book Refactoring to Patterns, Joshua Kerievsky talks about "Gradual Cutover Refactoring,"

pequeños cambios. en una sola linea. ejecutando lo tests en cada cambio

The small amount of time lost to making incremental changes is more than recouped by avoiding lengthy and frustrating debugging sessions. This style of coding is not only fast, it’s also stress-free.

### 3.8. Summary

Sometimes the first step, refactoring to openness, requires such a large leap that it is not obvious how to achieve it. In that case, be guided by code smells.

Making existing code open to a new requirement often requires identifying and naming abstractions. The Flocking Rules concentrate on turning difference into sameness, and thus are useful tools for unearthing abstractions.

## 4. Practicing Horizontal Refactoring

### 4.1. Replacing Difference With Sameness

The refactoring rules say to start by choosing the cases that are most alike.

habla de la sustitucion de un 1 hardcodeado por una variable

This substitution is important, not because it changes the resulting value, but because it increases the level of abstraction. It is this increase in abstraction that makes things the same. Without it, you are doomed to the conditional.

### 4.2. Equivocating About Names

When the perfect name for a concept is elusive, there are three strategies for moving forward.

Some folks allot themselves five to ten minutes to ponder (usually with thesaurus in hand), and then use the best name they can come up with during that interval.

Other folks find it more cost effective to instantly choose a meaningless name like foo or namethis. This strategy allows them to move forward quickly, and (one hopes) insures that the name will get improved later.

you can simply ask someone else for help

### 4.3. Deriving Names From Responsibilities

To help you name the new concept, remember the "what would the column header be?" technique

### 4.4. Choosing Meaningful Defaults

### 4.5. Seeking Stable Landing Points

esta hablando de los metodos. container. quantity y pronoun

These methods are incredibly consistent, and this did not happen by accident—it’s a direct result of the refactoring rules. The rules lead to consistent code, and consistency matters deeply.

it makes code easy to understand.

lowers costs.

consistent code enables future refactorings.

### 4.6. Obeying the Liskov Substitution Principle

el metood devuelv valores de distinto tipo segun el if

The true branch returns a string, but the false branch returns the argument that was passed, which is indeed an instance of Integer

lo anterior violaba liskov. porque requiere que el sender sepa que tipo de datos retorna quantity

The idea of reducing the number of dependencies imposed upon message senders by requiring that receivers return trustworthy objects is a generalization of the Liskov Substitution Principle

The Liskov Substitution Principle also applies to duck types

Liskov prohibits you from doing anything that would force the sender of a message to test the returned result in order to know how to behave.

Liskov violations force message senders to have knowledge of the various return types, and to either treat them differently, or convert them into something consistent

### 4.7. Taking Bigger Steps

it may seem as if you are now being given permission to act in a way that was previously prohibited.

Now that you recognize the pattern, and know how to make this change using small steps, it makes sense to start writing larger chunks of code.

if you take bigger steps and the tests begin to fail, there’s something about the problem that you don’t understand. If this happens, don’t push forward and refactor under red. Undo, return to green, and make incremental changes until you regain clarity.

### 4.8. Discovering Deeper Abstractions

hay algo en el ultimo cambio que no cuadra. si number es -1 devuelve 99? alo huele mal

The proposed change alters quantity such that: its conditional has 3 branches instead of 2 it sometimes checks -1, which is an invalid number of beers These inconsistencies don’t guarantee that something is wrong, but they should certainly motivate you to think more deeply about the underlying abstraction.

When you’re confused, don’t try to solve the entire problem straightaway. The more confused you are, the more important it is to nibble

asi. para el verso cero. en lugar de pasar number - 1. pasa directamente 99. de forma que la diferencia cambia . ahora es number - 1 contra 99

Instead of trying to understand everything at once, simply search for a way to make line 5 above look more like line 8 (even if not identical), using existing code.

### 4.9. Depending on Abstractions

Abstractions are beneficial in many ways. They consolidate code into a single place so that it can be changed with ease.

They name this consolidated code, allowing the name to be used as a shortcut for an idea, independent of its current implementation.

abstractions tell you where your code relies upon an idea. But to get this last benefit, you must refer to an abstraction in every place where it applies.

### 4.10. Summary

## 5. Separating Responsibilities

### 5.1. Selecting the Target Code Smell

The truth about refactoring is that it sometimes makes things worse

The refactoring recipes don’t promise to result in code that better expresses the problem—they merely make it easy to create that new expression,

#### 5.1.1. Identifying Patterns in Code

The current code, although not open to the new requirement, is improved.

have faith, and iterate.

recuerda el flujo diagrama de un poco anres de aqui

This means you must continue to be guided by code smells

One way to get better at identifying smells is to practice describing the characteristics of code.

make note of the things that catch your eye. Include any patterns that you see, and things you like, hate, or don’t understand.

#### 5.1.2. Spotting Common Qualities

Question 1: Do any methods have the same shape?

los 5 metodos extraidos tienen la misma estructura

Yes. The flocked five all have the same shape.

los 5 metood parecen muy iguales. pero podrian teer ligeras diferencias qu les hicieran parecer muy diferentes. lo que le hau difiil de refactorizar

Superfluous difference raises the cost of reading code, and increases the difficulty of future refactorings.

Squint Test

Look for: changes in shape, and changes in color.

Changes in indentation reveal the presence of conditionals.

Changes in color indicate differences in the level of abstraction

Question 2: Do any methods take an argument of the same name?

Six methods take number as an argument—

Question 3: Do arguments of the same name always mean the same thing?

the parameter that verse then passes on to container stands for something else—a bottle number.

the verse method and the flocked five methods use the same argument name to represent different concepts. This is rarely a good idea.

Having multiple methods that take the same argument is a code smell. It’s important, however, to recognize that here the term "same" means same concept, not identical name.

Question 4: If you were to add the private keyword, where would it go?

Question 5: If you were going to break this class into two pieces, where’s the dividing line?

Same as above, after verse and before the flocked five methods.

#### 5.1.3. Enumerating Flocked Method Commonalities

Question 6: Do the tests in the conditionals have anything in common?

all of the conditionals test the value of number

they test for number to be exactly equal to another value.

These conditionals could logically have used the less than, greater than or not equal operators, and still pass the tests.

Programmers tend to blithely interchange these different comparison operators, confident that if the tests pass, the code is correct. However, having tests that pass doesn’t guarantee the best expression of code, and this is a case where your choice of operator affects future costs.

Question 7: How many branches do the conditionals have?

two branches.

Question 8: Do the methods contain any code other than the conditional?

No.

Question 9: Do methods that take number as an argument depend more on number, or more on the class as a whole?

only on the number

#### 5.1.4. Insisting Upon Messages

deeply non-object-oriented pattern: the flocked five methods take an argument, examine it, and then supply behavior for it.

You should feel entitled to send messages to objects, and look for a way to write code that allows you to do so.

y es siio es el lugar dond se decide que objetos crear

There is a place for conditionals in OO.

Some object, somewhere, must choose which objects to create, and this often involves a conditional.

### 5.2. Extracting Classes

The questions above identify characteristics that group methods together,

Each item above acts like a vote, and these votes combine to point to Primitive Obsession as the dominant code smell

Obsessing on a primitive results in code that passes built-in types around, and supplies behavior for them.

The cure for Primitive Obsession is Extract Class.

#### 5.2.1. Modeling Abstractions

The primitive that you’re replacing represents a bottle number. Notice

This new class does not represent a kind of bottle: it represents a kind of number

A bottle is a thing, while a number is an idea.

the power of OO is that it lets you model ideas.

Experienced OO programmers deftly create virtual worlds in which ideas are as real as physical things.

#### 5.2.2. Naming Classes

#### 5.2.3. Extracting BottleNumber

As you might recall, safe refactoring relies upon tests running green

the existing Bottles tests become the safety net for this new class

while extracting the class, code that is known to work is copied from Bottles into BottleNumber

It’s important to put this new class fully into use before editing any of the copied code.

the process of changing code was subdivided into four steps. parse the new code parse and execute it parse, execute and use its result delete unused code

creating an empty BottleNumber class,

The methods weren’t moved—they were duplicated

It must now be admitted that the added line of code is, by any standard, ugly. BottleNumber.new(number).container(number) In the above code, both new and container require the number argument, so it must be passed twice.

you should refrain from altering the code in these copied methods until the new class is fully wired into the old.

#### 5.2.4. Removing Arguments

Now that the old Bottles class fully uses BottleNumber, the existing tests serve as a safety net for changes to the new class

Notice that if you’re willing to simultaneously alter both the senders and the receivers every message, it’s easy to make this change.

Keep in mind that is a multi-line change

Whether arguments are being added or removed, the trick is the same: you must change the method definition to temporarily set the argument to a default.

steps for removing an argument using one-line changes.

Alter the method definition to change the argument name, and provide a default.

def container(number) became: def container(delete_me=nil)

Change every sender of the message to remove the parameter. In the example: BottleNumber.new(number).container(number) became: BottleNumber.new(number).container

Finally, delete the argument from the method definition. So, finally: def container(delete_me=nil) became: def container

#### 5.2.5. Trusting the Process

but that when you change pronoun, the tests begin to fail.

it doesn’t point out a flaw in the process. Instead, it exposes a slightly more complex bit of code.

A great benefit of these refactoring techniques is that you can accomplish quite a bit while thinking very little. Sometimes, however, thought just can’t be avoided.

The blessing of these techniques is that altering code in such small increments severely constrains the number of errors any change can introduce.

### 5.3. Appreciating Immutability

One of the best things about immutable objects is that they are easy to understand and reason about.

Because they are easy to reason about, immutable objects are also easy to test

they are thread safe.

If you lean towards mutating the existing BottleNumber rather than making another, it’s possible that you are biased against creating new objects.

### 5.4. Assuming Fast Enough

The benefits of immutability are so great that, if it were free, you’d choose it every time

The first solution to any problem should avoid caching, use immutable objects, and treat object creation as free.

### 5.5. Creating BottleNumbers

In the code above, a new instance of BottleNumber is created each time container, quantity, action, or successor are invoked.

Line 4 above creates a new instance of BottleNumber and caches it in a temporary variable (this is the Temporary Variable code smell) within the verse method.

This cache reduces object creation without adding much additional complexity, so here it’s justified because the benefits outweigh the costs.

### 5.6. Recognizing Liskov Violations

Your object-oriented intuition is bang on [13] if you expect the successor of a BottleNumber to be another BottleNumber. If this were true, you could replace: quantity(successor(number)) with: bottle_number.successor.quantity

The problem is that successor still returns a number,

The type of the object has changed, but the successor method still returns the old type. You

This inconsistency is another violation of the generalized Liskov Substitution Principle

this successor method lies.

expect any method named successor to return an object that implements the same API as the receiver,

forces the sender to know that the return is untrustworthy

This current refactoring is almost complete, and it is often better to finish horizontal refactorings before undertaking vertical tangents.

The current problem can be solved by declaring another variable to hold bottle number 98 and writing some shameless code.

### 5.7. Summary

## 6. Achieving Openness

this chapter removes a Data Clump, deals with the conditionals in BottleNumber, introduces a Factory, fixes a Liskov violation, and ultimately, fulfills the six-pack requirement.

### 6.1. Consolidating Data Clumps

quantity and container appear together in three different places

Having a clump of data usually means you are missing a concept.

When a clump gets sent as a set of parameters, the method that receives the clump can easily become polluted with clump management logic.

If more than one method takes the same clump as input, some or all of this management logic will inevitably get duplicated in several places

the logic might accidentally diverge,

two things always appear together, it’s a signal that this pairing represents a deeper concept, and that concept should be named.

Programmers add blank lines to signify changes of topic. The presence of multiple topics suggest the existence of multiple responsibilities, which makes code harder to understand when reading, and easier to harm when changing.

### 6.2. Making Sense of Conditionals

pueden casi adiinar el futuro

Skilled programmers are good at picking what best to do next.

they have a secret understanding of the underlying patterns of code,

They know what’s right before they do it.

They also know that they don’t know everything.

Skilled programmers do what’s right when they intuit the truth

otherwise they engage in careful, precise, reproducible, and reversible coding experiments.

You are encouraged to do the same.

### 6.3. Replacing Conditionals with Polymorphism

#### 6.3.1. Dismembering Conditionals

Polymorphism, by definition, involves more than one kind of object,

This, in turn, will force you to add new code that is aware of the existence of these new classes

as conditionals disappear from BottleNumber, new dependencies will arise

BottleNumber represents a smart, bottle-ish kind of number

qu son las raas true de los condicionales

A few specific numbers are not yet smart enough.

The above makes it clear that 0 and 1 are special,

Each conditional supplies specific behavior in its true branch and generalized behavior in its false

y para ello va seguir la receta Reemplazar cond con polimorfismo de Foler

Removing the conditionals without breaking the tests requires a process that carefully and systematically moves the code from each true branch into a new object, rather than willy-nilly deleting it.

#### 6.3.2. Manufacturing Objects

#### 6.3.3. Prevailing with Polymorphism

Each refactoring followed a recipe, which led to a stable landing point, which in turn enabled the next refactoring.

habla denunas preguntas quebhizo al principio

If you examine the code in light of the above, you’ll notice that the questions revolve around verse variation, while the current code is more concerned with bottle number variation

all verses are alike in some abstract way, and that within verses, bottle numbers vary.

#### 6.3.4. Making Peace With Conditionals

The current factory contains a conditional which bears a strong resemblance to the original from Shameless Green.

Shameless Green has a special case for 2, but the factory does not. Recall

conditional in Shameless Green produces verses, but the one in the factory produces bottle numbers.

Factories don’t know what to do: instead, they know how to choose who does

Shameless Green was a procedure because it combined these two things. The current code is object-oriented because it breaks them apart.

### 6.4. Transitioning Between Types

successor methods violate the generalized Liskov Substitution Principle.

The following technique can be used to solve type change problems of any size.

Alterations are needed in several places. Ultimately: The factory should be located such that it is reachable by the successor methods, the successor methods should invoke the factory, and the verse method should expect successor to return a bottle number.

Step 1 is to put the factory within successor's reach

the best choice is to make the factory a class method on an existing class. The most reasonable choice among existing classes is BottleNumber

e una ayuda al polimorfismo porque no contiene el nlmbre dl tipo en la sigatura del etoo

for supports polymorphism.

To illustrate how, consider to_s.

Imagine the consequences of including the receiver’s type in the message name, as in hash_to_s, float_to_s, and, inevitably, string_to_s

Now that the for factory method exists, you can alter verse to invoke

Step 2 requires that you change the two successor methods to invoke the factory, but unfortunately, changing either one without simultaneously making all remaining changes will cause the tests to fail

The root of the problem is that the verse method expects successor to return something that will work in the factory, and the factory, in turn, expects to receive a number

The trick to moving forward using one-line changes is to temporarily alter the factory to tolerate both kinds of input

you must change the factory to check the type of its input argument.

return number if number.kind_of?(BottleNumber)

guard clause on line 3 above bounces the input argument right back out if it is already a bottle number.

the guard clause is temporary, and will be removed at the completion of this refactoring.

you can continue with step 2 by altering the successor methods to return a bottle number.

Step 3 requires changing the verse method to expect successor to return a bottle number.

Correcting the Liskov violation is important because object-oriented programming, especially in dynamically-typed languages like Ruby, relies on explicit trust in the implicit contracts between objects.

Trustworthy objects are a joy to work with because they always behave as you expect.

Objects that sometimes fail to respond to a message you plan to send, or occasionally return something you don’t expect,

untrustworthy objects require senders of messages to know too much.

### 6.5. Making the Easy Change

make the change easy (warning: this may be hard), then make the easy change — Kent Beck via Twitter Most of this book has been concerned with making the change easy. That hard work paid off here, where you made the easy change.

### 6.6. Defending the Domain

Bottle numbers are now independent objects, and ought to be freely useable in contexts other than those from which they were extracted.

se podria haber sobrescrito el metodo to-s de bottlenumber6. lo tests asaian. peo esria mintndo porqu quntity srria 6 y container bottle. cundo la quantity debe ser 1 y conti er six-pack

Clever shortcuts are a false economy. Invest in code that tells the truth. Just write it down.

### 6.7. Prying Open the Factory

una de ellas es geera el nlmbr d la cas poruu siun un paton

There are many of kinds of factories, and a plethora of strategies for making them open.

Even so, there are many things to dislike about this code.

is harder to understand than the original.

BottleNumber0, etc, are no longer explicitly referenced in the source code.

The code uses an exception for flow control.

The factory ignores bottle number classes whose names do not follow the convention.

deberia modiicar la fctoria entonces? psrece qu hay unos cuantos inconvenientes

Your goal is to minimize costs, and costs are determined by the situation at hand. There’s no hard and fast rule about what’s best. It just depends.

### 6.8. Summary

Having repeatedly advocated these prescriptive strategies, however, it ended with the confession that the answer to every question about object-oriented design is not necessarily to "follow recipe X." Rather, the answer is "it depends."

Afterword

este capitulo podria servir como review del libro

how to write code.

Strive for simplicity. Don’t abstract too soon. Focus on smells. Concentrate on difference. Take small steps. Follow the Flocking Rules. Refactor under green. Fix the easy problems first. Work horizontally. Seek stable landing points. Be disciplined. Don’t chase the shiny thing.

This book wants you to fall in love with polymorphism.

when you disperse behavior into polymorphic objects, you can use factories to isolate both the names of the classes and the conditionals that choose them.

your code depends upon abstract roles rather than on concrete classes.

Your objects must be trustworthy, and your code must trust your objects. Failing at either obligation dooms you to conditionals.

Hold high standards, but judge yourself gently.

