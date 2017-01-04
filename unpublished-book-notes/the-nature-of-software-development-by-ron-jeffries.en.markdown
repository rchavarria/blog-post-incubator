# The nature of software development
### by Ron Jeffries

[![The nature of software development](/img/nature-software-development.jpg)](https://www.amazon.es/Nature-Software-Development-Simple-Valuable/dp/1941222374/)

[Spanish version](the-nature-of-software-development-by-ron-jeffries.markdown)

# Notas tomadas

This book is an attempt at finding some essential simplicity inside the complex activity of building software products.

## Introduction

It’s not a book of recipes. There are many ways to accomplish what you need. I trust you to find ways, think of ways, and select among them.

## Chapter 1 The Search for Value

Value, we’ll see, is *what you want*

## Chapter 2 Value Is What We Want

A project delivers value only when we ship the software and put it to use.

Very likely, there’s a subset of capability that can start providing value sooner than the whole package. Let’s find those features and ship them first.

Sometimes the most important information we can get is that we’re doing the wrong thing. One very good way to find out if we’re going in the right direction is to ship a small version of the product early. If it flops, we can change direction at low cost.

It’s not enough for our teams to work on mysterious technical bits that make sense only to them. We need to guide our teams to build pieces that make sense to us, and to our users. These are often called minimal marketable features (MMFs).

(*remember that picture with rectangles where value grow and what types of boxes should be built first*)

Suppose the height of the features is their value, and the width is their cost.

Best value comes from small, value-focused features, delivered frequently.

## Chapter 3 Guiding Goes Better “Feature by Feature”

When we build our software projects feature by feature, we can see how much is done and how rapidly the project is progressing. We get a good sense of how much will be done by any given date.

(*contrary to the traditional way, where we start seeing value much much later*)

When our projects grow feature by feature, we can respond to what’s really happening.

## Chapter 4 Organizing by Feature

Responsibility and authority are aligned.

Organize into small teams. Make sure that each team has all the people and all the skills necessary to build the entire feature, not just part of it.

As you're building teams by feature, you'll find you're lacking of experts in one aspect. Soon, you might find yourself creating a team whose database person, or UX person, really isn’t quite good enough. Super. You’ve identified a training opportunity. A learning opportunity. An opportunity to form a guild, a Community of Practice!

A highly paid expert shouldn’t be highly paid just because she’s an expert. She should be highly paid because she is helping other people become experts.

(*IDEA: why not I propose to create a Community of Practice, a Community to learn how to write tests*)

## Chapter 5 Planning Feature by Feature

> Plans are useless, but planning is indispensable ~ *General Eisenhower*

It’s important to identify key features that we’ll need to have early, as well as features we can’t live without.

Let’s do plan but at the same time stay loose and ready for change.

(*Do this instead of plan deeply in details*): Set a time and money budget; produce the most valuable features first; keep the product ready to ship at any time—and stop when the clock runs out.

Continuous planning: feature splitting

Because we’re focused on value, we need to plan all the time.

Things go best if each feature, often called a story, takes only **two or three** days to do. (*I've already realized that. If something is going to take more than 3 days, it's not splitted small enough*)

I don’t recommend working with larger stories and breaking them down into technical items, often called tasks. If we use tasks, the business-side people do not have a clear look at how things are going. It’s better to break down stories into smaller stories, each making sense to the business-side people.

Planning with “stretch goals” is destructive. The reason is that the team will in fact try. Eager to please, they’ll unconsciously hurry. Since defects take longer to fix than they do to prevent, hurrying will slow you down.

Once we become proficient at breaking all features down to approximately the same size. (*this is how it is to work with no-estimates*)

Our job is to select the work to do versus the work to defer.

## Chapter 6 Building the Product, Feature by Feature

We plan and manage our project in short one- or two-week cycles. In each cycle, we define the next few features to build and we say how they’ll be tested. The team then builds the features and we all verify whether they pass the tests. In each of these one- or two-week iterations, we go through a complete product development cycle.

The feature-by-feature style includes a complete development cycle in every iteration: requirements, design, coding, and testing.

Eliminate the test-and-fix finish.

This can even happen when we work feature by feature—if the features aren’t really done.

For feature-by-feature development to work, it needs to be nearly free of defects all the time.

## Chapter 7 Build Features and Foundation in Parallel

(*Foundation as in base or arquitecture in the application*)

Features do need to be supported by a foundation, and the foundation needs to be well designed.

Build features and foundation

Let’s consider some options: We could build out the whole design first, or we could build each full feature one at a time, each with its foundation. We can’t build all the foundation first, and we can’t build all the features first. It’s safer by far to build a simple yet functional version of each feature first!

(*It makes no sense to build features in their completeness in one shot, it's better to build them incrementally*)

## Chapter 8 Bug-Free and Well Designed

Any defects in our features amount to negative features. They reduce our line of apparent progress. Defect repair adds unknown delay. Repair as you go to provide clarity on what’s done. (*The more bugs, the bigger will be the uncertainty about where we are*)

Remember, we’re working incrementally. We need a good design early on, but we only need a small good design.

The design can easily deteriorate. Skill and care are required to keep our project alive. As the project grows, as the features grow, we must grow the design to support those features.

To keep the design good, we need to improve it as we go. What doesn’t work is to let the design go.

Testing and refactoring work together to make feature-by-feature development possible. For the best quality, smoothest progress, and greatest predictability, this is the best known way to work.

## Chapter 9 Full Circle

## Chapter 10 Value—What Is It?

## Chapter 11 Value—How Can We Measure It?

Sit with your developers and stakeholders. Select a combination of next things to do that the group agrees is most valuable. Build it, ship it promptly, and listen to your users. Repeat.

## Chapter 12 Of Course It’s Hard!

Take every idea as, maybe, a good way to start doing things for a while. Then make the process your own, and build your own ideas. But keep it simple! (*Understand this as a way to get a hard work done: do it bit by bit, incrementally, learn in the way, and make it your own*)

## Chapter 13 Not That Simple

And yet, it’s all about deciding what we want, guiding ourselves toward what we really want, by building things and seeing how they work out. (*what we want -> prioritize -> build -> see -> decide next step*)

## Chapter 14 Creating Teams That Thrive

Purpose, Autonomy, and Mastery

proporciona direccion

The Product Champion provides purpose, direction.

Bring concerns or problems to the team, and let the whole team create solutions in concert. (*It's important for the team to create solutions by its own, to feel as if they own the work*)

With true autonomy, no one double-checks the team: they decide, they build, we all see the results.

Mastery comes from the iterative process. In each iteration, we meet and look back on how things went and determine how to do better. We move toward mastery.

## Chapter 15 The “Five-Card Method”for Initial Forecasting

## Chapter 16 Managing Natural Software Development

My experience has been that managing is mostly about trying to keep projects on track. How do we ensure that we are keeping to the plan? Honestly, our job isn’t to stick to the plan—it’s to steer our course for the best result, not some fixed target.

## Chapter 17 Whip the Ponies Harder

Under pressure, teams will consciously or unconsciously begin to be more conservative in what they take on. They will begin rating things as a bit larger or a bit harder than they used to. This will give the impression that they’re going faster, but they are not.

Are there any ways to go faster? How can we do it?

Work on team productivity before individual productivity.

Increase individual productivity by increasing capability, not by urging people to work harder.

Can we at least use our velocity to predict when we’ll be done? In a word, no!

We do best not when we predict when we’ll be done, but when we choose when to be done. The best way to do this, as we’ve discussed, is always to be “done.”

If your organization has some fixed content in mind. You are likely not managing by value but by cost.

## Chapter 18 To Speed Up, Build with Skill

Build skill in the development team. That investment will pay off rapidly in less time lost to fixing defects, and in smoother development.

The fastest teams move smoothly and gracefully.

## Chapter 19 Refactoring

We need steady progress. To keep progress steady, we need a clear, clean design all the time. To accomplish this, we must refactor.

The time needed to build a feature comes from two main components: its inherent difficulty, and the accidental difficulty of putting it into whatever code already exists. Teams are good at estimating the inherent difficulty. What makes us erratic, what makes us slow down, is the accidental difficulty. We call this difficulty “bad code.”

The word refactoring refers to a simple, regular process of keeping the code clean. We try not to create the twisty little passages that slow us down. When twists do crop up, we straighten them out. (*When the road becomes twisty, we straighten it by refactoring the code*)

Campground Rule: Leave the campground a little better than you found it.

This process does just what we need: areas where we do little work aren’t slowing us down, and they are left mostly alone. Areas where we do lots of work get more attention; they clean up quickly.

## Chapter 20 Agile Methods

Some advice about frameworks (or agile methods):

- Have too little framework, not too much.
- Keep it light. 
- Control the framework; don’t let the framework control you. 
- Keep process changes close to the team.
- Make learning a priority.
- Think.

## Chapter 21 Scaling Agile

## Chapter 22 Conclusion

