---
title: Coupling and Cohesion
tags: [architecture, framework]
summary: Defines coupling and cohesion as the two fundamental measures of software design quality, and maps SOLID, DRY, Law of Demeter, and KISS back to these two properties. Reach for it when evaluating a design decision or explaining why a design principle matters.
related: []
---

# What are Coupling and Cohesion?

*Coupling* is a measure of how strongly components are interconnected, such that a change to one component can require changes to others.

*Cohesion* is a measure of how closely all the parts of a component align with a single purpose.

For example, suppose my function sorts an array of integers. If I have to modify the function to make it sort an array of strings, the function is coupled to the integer type. If, instead, the function works with an abstract Comparable type, I can use it with any type that satisfies that contract without modifying the function itself. In other words, it is not coupled to any specific element type, although it is still coupled to the Comparable contract. At the same time, if the function is responsible only for sorting the array it receives - with no unrelated transformations, business-rule validation, and so on - it has high cohesion.

# How to Measure Coupling and Cohesion?

For coupling: the number of components touched while working on a single task and how the effort is distributed between them.

For cohesion: the number of distinct concerns to keep in mind while working on a single component and how the effort is distributed between them.

# Reducing Design Principles to Coupling and Cohesion

## SOLID principle

### Single Responsibility Principle

- A class should never have more than one reason to change.
- This is essentially a direct expression of the High Cohesion principle.

### Open/Closed Principle

- Software entities should be open for extension, but closed for modification.
- If adding new functionality requires modifying an existing entity, that functionality becomes coupled to the entity itself and potentially to its existing extensions. If, instead, we add the functionality by extending the entity without modifying it, we preserve its original cohesion and keep the new functionality isolated from the existing code. So this principle helps keep coupling low and cohesion high as the system evolves.

### Liskov Substitution Principle

- Functions that use pointers or references to base classes must be able to use pointers or references of derived classes without knowing it.
- If code using a base class has to handle specific subclasses as special cases, it becomes coupled to their implementations. Then changing one subclass may require changes in the code using the base class or even coordinated changes in other subclasses. The principle therefore helps avoid such unnecessary coupling.

### Interface Segregation Principle

- No code should be forced to depend on methods it does not use
- This principle prevents us from creating "super-interfaces" that cover many unrelated responsibilities at once. Smaller, more focused interfaces increase cohesion and reduce unnecessary dependencies between clients and functionality they do not use. So this principle is intended to increase cohesion and reduce coupling.

### Dependency Inversion Principle

- One should depend upon abstractions, not concrete implementations.
- When depending on concrete implementations, the code depends not only on the abstraction they provide but also on implementation details that may change. When depending on an abstraction, the code is isolated from many of these implementation changes. So by reducing dependencies on implementation details, this principle reduces coupling.

## DRY principle

### Don't Repeat Yourself

- Every piece of knowledge must have a single, unambiguous, authoritative representation within a system.
- When the same logic is duplicated in several places, changing it in one place will often require changing it in all the others, introducing logical coupling between them. So this principle is intended to reduce coupling.

## Law of Demeter

- Interact only with your immediate dependencies.
- Interacting with dependencies of dependencies makes the code depend on their structure and additional interfaces, increasing coupling. It can also reduce cohesion by making the code responsible for navigating relationships outside its own concern. So this principle is intended primarily to reduce coupling while also supporting cohesion.

## KISS principle

### Keep It Simple, Stupid

- Systems should be as simple as possible.
- This principle does not provide strict definitions of complexity or simplicity, so everyone may interpret them somewhat differently. But if we consider complexity to be the amount of information that has to be kept in mind simultaneously, the "Low Coupling, High Cohesion" principle, as described above, directly helps reduce that amount, i.e. reduce complexity and make the system simpler.
