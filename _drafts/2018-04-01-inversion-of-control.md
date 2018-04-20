---
layout:   post
title:    "Inversion of Control (IoC) Design Pattern"
date:     2018-04-01 17:00:00 +0100
category: patterns
tags:     [ "design pattern", "pattern", "ioc", "inversion of control", "dependency injection", "template method", "strategy pattern", "service locator", "dependency inversion principle" ]
---

# Inversion of Control

The Inversion of Control (or IoC) is commonly used in frameworks. IoC is a more generic design pattern or a design principle. Other design patterns implement the IoC principle; such as the Dependency Injection, Template Method, Strategy and Service Locator patterns.

Inversion of Control patterns provide a generic outline to fulfil tasks done in a common manner. It provides an outline of a process, which calls customised code to satisfy specific requirements. 

The pattern controls the flow of execution and calls custom code to fulfil various tasks - e.g. a framework calls custom code. This is inverted from regular flow control, where the custom code calls libraries. It is often referred to as the "Hollywood Principle" and the "don't call us, we'll call you" design pattern.

Whilst Inversion of Control is a hallmark of frameworks it is not used exclusively in them, see *Template Method Pattern* below.


**Affects:** Flow control

**Goals:**
 - Decouple tasks from their implementations
 - Focus the domain of a module to a task
 - Remove assumptions regarding other systems
 - Prevent side effects

 In the book "[Head First Design Patterns](http://shop.oreilly.com/product/9780596007126.do)" (Freeman & Freeman) Inversion of Control is referred to as the "Dependency Inversion Principle" (p. 141 in the 2009 edition, p. 139 in the 2004 first edition). I think the book prefers the term "principle" to pattern, as Inversion of Control really describes many patterns and is more a general principle than a specific pattern.


# IoC pattern: Dependency Injection

Dependency Injection is where dependencies to an object are passed to it. This may be done in a few ways, including via:
 - the object's contructor
 - setter method(s)
 - interface injection

 Instead of the dependencies being stated explicitly upfront, they are decoupled by being passed to (or injected into) the object that requires them.

 The object's requirements are passed to it, and it's requirements are fulfilled via **composition**, rather than a direct dependency.

 This allows custom code to be determined and called at runtime. So long as the dependency being injected adheres to the required contract, we can be unconcerned with which customised implementation we are using.



# IoC pattern: Template Method Pattern

When two components operate in an overall significantly similar fashion, but the work to be performed differs, the template method is a good choice of pattern to use.

When you notice two or more classes which follow the same processes, but in some steps they use algorithms which differ, you have found candidates for using the template method pattern.

A good description can be found here: [Template Method Design Pattern](https://sourcemaking.com/design_patterns/template_method)

So, you have a base or abstract class, which implements the outer steps to be taken. The derived classes then fill in their differences by implementing certain methods methods differently.


# Other IOC patterns

Other Inversion of Control patterns include:

- Strategy Pattern
- Service Locator Pattern


# References

 - [Inversion of Control Containers and the Dependency Injection pattern](https://martinfowler.com/articles/injection.html) by Martin Fowler
 - [Inversion of Control](https://en.wikipedia.org/wiki/Inversion_of_control) on Wikipedia
 - [What is dependency injection?](https://stackoverflow.com/questions/130794/what-is-dependency-injection) on Stack Overflow
 - [Developer's Guide to Dependency Injection Using Unity](https://msdn.microsoft.com/en-us/library/dn223671(v=pandp.30).aspx)
 - [Inversion of Control – An Introduction with Examples in .NET ](http://joelabrahamsson.com/inversion-of-control-an-introduction-with-examples-in-net/) by Joel Abrahamsson
 - [Inversion of Control: Overview with Examples](https://www.codeproject.com/Articles/380748/Inversion-of-Control-Overview-with-Examples)
 - [What is Inversion of Control?](https://stackoverflow.com/questions/3058/what-is-inversion-of-control) on Stack Overflow
 - [Dependency Injection](https://en.wikipedia.org/wiki/Dependency_injection) on Wikipedia
 - [Template Method Design Pattern](https://sourcemaking.com/design_patterns/template_method)
 - [Head First Design Patterns](http://shop.oreilly.com/product/9780596007126.do)
 - Erich Gamma, Richard Helm, Ralph Johnson, John Vlissides (1994) _Design Patterns: Elements of Reusable Object-Oriented Software_. Published by Addison-Wesley.
 