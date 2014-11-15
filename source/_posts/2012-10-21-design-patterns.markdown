---
author: mariostallone
comments: true
date: 2012-10-21 04:25:27+00:00
layout: post
slug: design-patterns
title: Design Patterns
wordpress_id: 99
categories:
- Design Patterns
- General
- Technology
- Tips
tags:
- design
- design patterns
- good code
- patterns
---

Most of you in the Software Development Industry must have at some time or the other heard the term **Design Patterns . **Well, I heard this a while back from a few friends. Design Patterns was originally conceived by [Gamma, Erich](http://en.wikipedia.org/wiki/Erich_Gamma); [Richard Helm](http://en.wikipedia.org/w/index.php?title=Richard_Helm&action=edit&redlink=1), [Ralph Johnson](http://en.wikipedia.org/wiki/Ralph_Johnson_(computer_scientist)), and [John Vlissides](http://en.wikipedia.org/wiki/John_Vlissides)  in their book _[Design Patterns: Elements of Reusable Object-Oriented Software](http://en.wikipedia.org/wiki/Design_Patterns_(book))._

To be brief, Design Patterns are a collection of approaches to Designing software applications that enable reuse and extensibility. It's a more Object Oriented way of writing code, that is structured, well written, well understood and most importantly highly extendable and reusable.

Now, many of you might wonder, why must your code be extendable?
We work in an industry thats driven by Clients'requirements. And mind you, these requirements hardly freeze that easily. Well you might say, if you were to follow the waterfall methodology of Software Design, where does change in Software requirements occur. Truth is, in all practicality, the waterfall model cannot be followed all the time, and even if it were to be followed, an iteration over the code to add a new feature, must be made with minimal change to the existing code base.

Most articles I've found these days about good programming spring from the Agile, TDD and XP Community. They've inspired me to write better code, and well, I must say I've grown to like their style of development too.

Here are some of the ideals I try to follow, they're not in any order, just random stuff I do while writing code.

  * Do not use **else** 
	* I try real hard to avoid the else statement. When I first heard this from Object Calisthenics, I found it weird  but slowly grew to realize that I realize that I didnt need it. A simple **return **or **continue** could easily replace an **else.**
  * Only one level of **Indentation**	
  * Good method names
  * Let a method perform one task and only one task
  * Break down taks into Classes, give each class a **Single ****Responsibility**
  * Use helper methods to perform tasks such as formatting text, etc.

When I started writing code, I use to have this notion that my code must not be understood by others, that made my code complex and better!

Now, Ive grown to realize that, the easier my code is to be understood, the better it is.

Coming back to my initial topic of discussion, I find that Design Patterns help me write better code. We might have some point of time used many of these patterns, but without giving them a proper name.

Well, the Gang of Four, have taken the trouble to pen these down and have given a name for each of them. Now, the Gang of Four are not the only ones who documented them, they are the most acknowledged and one of the first to do so. SInce I acknowledge them, I will be using them as a reference and I shall also add a few more that I find or come across.

**Creational Design Patterns**
	
  * Abstract Factory	
  * Builder
  * Factory Method
  * Object Pool
  * Prototype
  * Singleton

**Structural Patterns**
	
  * Adapter	
  * Bridge
  * Composite
  * Decorator
  * Facade
  * Flyweight
  * Proxy

**Behavioral Patterns**
	
  * Chain of Responsibility	
  * Command Interpreter
  * Iterator
  * Mediator
  * Memento
  * Observer
  * State
  * Strategy
  * Template Method
  * Visitor


Now why am I telling you all of this. Well, I intend on going through all these 22 patterns via code examples over a span of (hopefully) 22days :-)

So, I'm going to document my understanding via Code Examples, etc. Each Pattern will have its own post.

Code examples will be posted to github and can be browsed through via my github handle -> [Github](https://github.com/mariostallone)

So ciao for now, see you in the next post.

PS : I'm not going in any order
