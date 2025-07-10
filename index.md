---
title: Design Patterns
layout: default
nav_order: 1
permalink: /
toc: true
toc_sticky: true
---

# 📘 JavaScript Design Patterns

"Design patterns" are reusable solutions to common problems in software design. They are not finished code but templates that can be adapted to solve problems in various situations. They help make your code more flexible, reusable, and maintainable.

Design patterns are generally divided into three main categories:


## 1. Creational Patterns

These deal with object creation mechanisms.

| Pattern              | Purpose                                                                                             |
| -------------------- | --------------------------------------------------------------------------------------------------- |
| **Singleton**        | Ensures a class has only one instance and provides a global access point to it.                     |
| **Factory Method**   | Defines an interface for creating an object, but lets subclasses decide which class to instantiate. |
| **Abstract Factory** | Produces families of related objects without specifying their concrete classes.                     |
| **Builder**          | Separates the construction of a complex object from its representation.                             |
| **Prototype**        | Creates new objects by copying an existing object, known as the prototype.                          |



## 2. Structural Patterns

These deal with object composition.

| Pattern       | Purpose                                                                    |
| ------------- | -------------------------------------------------------------------------- |
| **Adapter**   | Allows incompatible interfaces to work together.                           |
| **Bridge**    | Separates abstraction from implementation so they can vary independently.  |
| **Composite** | Composes objects into tree structures to represent part-whole hierarchies. |
| **Decorator** | Adds behavior to objects dynamically without altering their structure.     |
| **Facade**    | Provides a simplified interface to a larger system.                        |
| **Flyweight** | Reduces memory usage by sharing common parts of objects.                   |
| **Proxy**     | Provides a surrogate or placeholder for another object.                    |


## 3. Behavioral Patterns

These focus on communication between objects.

| Pattern                     | Purpose                                                                  |
| --------------------------- | ------------------------------------------------------------------------ |
| **Observer**                | Allows an object to notify other objects when its state changes.         |
| **Strategy**                | Enables selecting an algorithm's behavior at runtime.                    |
| **Command**                 | Encapsulates a request as an object.                                     |
| **Chain of Responsibility** | Passes a request along a chain of handlers.                              |
| **State**                   | Allows an object to change its behavior when its internal state changes. |
| **Template Method**         | Defines the skeleton of an algorithm, allowing steps to be overridden.   |
| **Mediator**                | Centralizes complex communication between related objects.               |
| **Memento**                 | Captures and restores an object’s internal state.                        |
| **Visitor**                 | Adds operations to existing object structures without modifying them.    |
| **Iterator**                | Provides a way to access elements of a collection sequentially.          |
| **Interpreter**             | Implements a language's grammar and interpreter.                         |



##  🛠️ When to Use Design Patterns?

1. When your code feels repetitive or rigid

2. When you're working in a team and want a shared vocabulary

3. When solving recurring design problems

[Click to view in more detail with example and UML daigram](details.md)
