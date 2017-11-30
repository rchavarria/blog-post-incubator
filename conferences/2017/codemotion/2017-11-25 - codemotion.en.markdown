# Talks

## [Let’s be hipsters, let’s think Serverless](https://2017.codemotion.es/agenda.html#5649626120060928/5768955947909120)

Serverless = do not think about the infraestructure (isn’t it a IaaS, PaaS or a SaaS?). Infraestructure is managed and admin by a third party, usually event oriented.

Azure serverless services: cognitive (machine learning,...), storage, databases, event bus, functions

Azure functions are made of:
-	Triggers: how and when a Function is invoked. Event driven: http call, a change in a database table, new item in a queue,...
-	Bindings: where data is retrieved, where data is returned. It can be almost any service: storage, db, queue, social connector (twitter,...) (third party integrations?)

## [Clean architecture](https://2017.codemotion.es/agenda.html#5649626120060928/5098174129635328)

He explained evolution is server architecture: monolith, 3 layers, N layers, MVC, CQRS, Clean,...

Clean architecture is basically the Hexagonal architecture. The most important concept is Dependency Inversion and Inversion of Control.

He showed a new architecture: space-based architecture. It looked like a distributed one. I didn’t understand the concept really well.

## [Component oriented Progressive Wep Apps with Vue.js](https://2017.codemotion.es/agenda.html#5649626120060928/5699320770723840)

He explained what PWAs are, and what they’re made of: https, responsive design, service workers, web push notifications, web app manifest, offline first, caching,...

App Shell concept: the minimum resources for your app to work offline. Dynamic content might be loaded from server or browser cache.

Web Push Notifications: use the browser API to show push notifications to users as if they were native in mobile devices.

There is a template using Vue.js that includes the code to create a basic PWA (service workers, some data caching, webpack config,...) (https://github.com/vuejs-templates/pwa)

## [Comfort zone awakes](https://2017.codemotion.es/agenda.html#5649626120060928/6007471319547904)

She talked about several phases to go out of the comfort zone:

-	Curiosity: I have an idea
-	Have the will to do things, to start implementing the idea
-	Consume knowledge: learnings, community, talks
-	Spread knowledge: share, blogs, stack overflow, give talks, organize events (I would summarize it as „socialize with people“)
-	Public talking (why every time someone talks about comfort zone she ends up talking about how to talk in public spaces?)
-	Motivate curiosity: make other people to start this journey

## [Workshop: easy testing with docker, manage dependencies and unify environments](https://2017.codemotion.es/agenda.html#5693168230072320/6560049195384832)

I learn a little bit about how to use docker: commands (docker run, docker images, docker ps, docker rm) and parameters:

-	-it to run a command inside a container
-	-d to run the container in background
-	-e to send environment varialbes
-	-p to expose ports
-	-v to mount volumes
-	--rm to remove the container after it does its job. It seems to be a best practice to create/discard containers for each execution
-	-w to set the working directory for the container

With docker you do NOT pollute your environment (you can have different versions of your tools: php, apache,...)

Some issues with docker: user rights (it’s executed as root), docker-in-docker Vs docker-siblings, share files, share results

We should start using Pipelines in Jenkins

Jenkins plugin: Docker pipelines plugin: makes really easy use docker from Jenkins: it manages user rights, create/delete containers, share files,...

## [What rules should be broken to make your dev team the fastest](https://2017.codemotion.es/agenda.html#5693168230072320/5105557983723520)

He talked about three (kind of) velocities:

1.	Hackathon: go as fast as possible (where qualilty is the least important issue)
2.	Banks: slow, with lots of resources, known direction (overengineering, overcomplicating problems, enterprise,...)
3.	Startup: where people is opening the road in the jungle, with a more or less clear objective, but without a known path

All products should have a Product Manager, who decides what to do and where to go (road-map). The target should be clear for all the people in the team.

Do the bare minimum to go to the target. No meta-work. Be practical, be aware of abstractions, don’t make up them.

I would like to highlight some quotes:

-	If you enforce a rule, you must put a system that checks the rule. Talking about code style, guidelines,...
-	Technical debt is the mortgage of the code. It’s not fair when someone in the team take shorcuts and other clean up the technical debt.

The user is more important than: optimize, abstract, reuse, automate.

Time-suckers: we should solve the root cause of the problems, not (only) their consecuences

Coordination requires transparency. Everybody in the team must know about what others are doing

Ship, ship, ship: release as soon as possible to production, get feedback as soon as possible

Everybody should have the user in mind

He finally talked about motivation, slack time, research, small projects to experiment

## [What’s  a senior developer?](https://2017.codemotion.es/agenda.html#5693168230072320/4878640902832128)

First, he started with what’s NOT a senior dev? It’s not if a title says so, or if the developer is expensive, or if she writes code nobody understand, or if she works for the company for a long time.

A senior dev doubts about processes, practices and dogmas, she speaks outloud, she provides data that prove her theories.

Senior means maturity

Personal principles:

-	Confidence, reliability: don’t promise anything you’re not going to deliver
-	Responsability: maturity is how do you face your errors (because you’re gonna fail)
-	Flexibility: do not know just one tool, language or technology
-	Pragmatism: write code is not everything, one should know where she wants to go and she knows about resources that will lead to that place (tools, languages, technics, ...)

Useful rules to work withing a team: listen to and learn from everybody, lead by example (be proactive), teach others, offer for help, doubt about processes, provide solutions, not just problems, help improving the company culture.

Senior plan their carrer, the chose the next step in their carrer paths.

## [The IT worker](https://2017.codemotion.es/agenda.html#5693168230072320/5145563993473024)

With IT worker he means not only developers, but anybody that works with information.

There was nothing to learn specifically in this talk, because it wasn’t a technical one. It could be seen as the closing talk of the event. It was that kind of talks, with more questions than answers:

-	What’s an IT worker?
-	Do we know how much power do we have?
-	What do we think about information manipulation?
-	Is it ethical to let companies lie to/manipulate/influence people in the wrong direction?
-	Do you work for the company you want?
-	Is your work alineated with your values?
-	Are we doing as much as possible to build a better world?
-	Are we doing our best to include all the people in the information era?
-	Should we educate/teach the rest of the people about how dangerous the technology can be? Or how technology can be used to manipulate our decisions?

New ideas to (think about) “implement”

-	Could we use Web Push Notifications for monitoring? We probably need some Service Worker. But, the speaker didn’t mention technologies such Web Sockets when talking about push notifications. Maybe, something to research. Not all browsers will support them yet I think.
-	We should start using Jenkins Pipelines: it’s the new way of working in Jenkins, and it’ll be the future way of doing it.
-	We should use docker for each tool. Currently, we have two docker images: Jenkins and MySQL. We should have an image for PHP/PHPUnit, other for Node and JS tests, other for the browser that runs the tests (not sure about this), …
-	Can we agree in something to know what is doing everyone? A message in Teams, …
-	Could we release versions more frequently? Not for CMC, but for internal use. To get feedback from EZV employees at least.
