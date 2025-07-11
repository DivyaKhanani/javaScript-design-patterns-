---
layout: default
title: Real-World Examples & UML
toc: true
nav_order: 2
toc_sticky: true
---

# 📘 Real-World Examples & UML
---

## 🏗️ Creational Patterns  
> Deal with object creation mechanisms.

### 1. Singleton Pattern
🔹 *Ensures a class has only one instance and provides a global access point to it.*
```js
class AppConfig {
  constructor() {
    if (AppConfig.instance) return AppConfig.instance;
    this.settings = {};
    AppConfig.instance = this;
  }
}
```
**UML:**
```
+-------------+
|  AppConfig  |
+-------------+
| -settings   |
| -instance   |
| +set()      |
| +get()      |
+-------------+
```

### 2. Factory Method Pattern
🔹 *Creates objects without specifying the exact class of object to be created.*
```js
class ButtonFactory {
  static createButton(type) {
    return type === "icon" ? new IconButton() : new Button();
  }
}
```
**UML:**
```
+----------------+
| ButtonFactory  |
+----------------+
| +createButton()|
+----------------+
```

### 3. Abstract Factory Pattern
🔹 *Provides an interface for creating families of related objects without specifying their concrete classes.*
```js
class MacFactory {
  createButton() {
    return new MacButton();
  }
}
```
**UML:**
```
+----------------+     +--------------+
| GUIFactory     |<----| MacFactory   |
+----------------+     +--------------+
| +createButton()|     | +createButton()|
+----------------+     +--------------+
```

### 4. Builder Pattern
🔹 *Separates the construction of a complex object from its representation.*
```js
const burger = new BurgerBuilder().addBun("sesame").addPatty("beef").build();
```
**UML:**
```
+------------------+
|  BurgerBuilder   |
+------------------+
| -burger          |
| +addBun()        |
| +build()         |
+------------------+
```

### 5. Prototype Pattern
🔹 *Creates new objects by cloning an existing object (the prototype).*
```js
const clone = Object.assign(Object.create(Object.getPrototypeOf(original)), original);
```
**UML:**
```
+------------+
| Prototype  |
+------------+
| +clone()   |
+------------+
```

## 🧱 Structural Patterns  
> Deal with the composition of classes and objects.

### 6. Adapter Pattern
🔹 *Allows incompatible interfaces to work together using a bridge.*
```js
class PrinterAdapter {
  print(text) {
    this.oldPrinter.printOld(text);
  }
}
```
**UML:**
```
+----------------+     +----------------+
|  PrinterAdapter| --> |   OldPrinter   |
+----------------+     +----------------+
```

### 7. Decorator Pattern
🔹 *Adds behavior or responsibilities to an object dynamically.*
```js
class MilkDecorator {
  cost() {
    return this.coffee.cost() + 2;
  }
}
```
**UML:**
```
+-------------+
|   Coffee    |
+-------------+
      ^
      |
+------------------+
| MilkDecorator    |
+------------------+
```

### 8. Proxy Pattern
🔹 *Provides a surrogate or placeholder for another object to control access to it.*
```js
class ProxyImage {
  display() {
    if (!this.realImage) {
      this.realImage = new RealImage(this.filename);
    }
    this.realImage.display();
  }
}
```
**UML:**
```
+------------+
| ProxyImage |
+------------+
      |
      v
+-----------+
| RealImage |
+-----------+
```

### 9. Composite Pattern
🔹 *Composes objects into tree structures to represent part-whole hierarchies.*
```js
class Folder {
  display(indent = 0) {
    this.children.forEach(child => child.display(indent + 2));
  }
}
```
**UML:**
```
+-------------+
|   Component |
+-------------+
      ^
   ---------
   |       |
+--------+ +---------+
|  File  | | Folder  |
+--------+ +---------+
```

### 10. Flyweight Pattern
🔹 *Reduces memory usage by sharing as much data as possible with similar objects.*
```js
const car = factory.getCar("Toyota", "Corolla");
```
**UML:**
```
+-------------+
|  CarFactory |
+-------------+
      |
      v
   +--------+
   |  Car   |
   +--------+
```

### 11. Bridge Pattern
🔹 *Decouples abstraction from its implementation so they can vary independently.*
```js
class Circle {
  draw() {
    this.drawingAPI.drawCircle(this.x, this.y, this.radius);
  }
}
```
**UML:**
```
+----------+       +-----------------+
|  Circle  | ----> |   DrawingAPI    |
+----------+       +-----------------+
```



## 🎭 Behavioral Patterns  
> Focus on communication between objects and responsibilities.

### 12. Observer Pattern
🔹 *Defines a one-to-many dependency so that when one object changes state, all its dependents are notified.*
```js
class Subject {
  constructor() {
    this.observers = [];
  }
  subscribe(observer) {
    this.observers.push(observer);
  }
  notify(data) {
    this.observers.forEach(observer => observer.update(data));
  }
}
```
**UML:**
```
+-----------+
|  Subject  |
+-----------+
| -observers|
| +subscribe() |
| +notify()    |
+-----------+
       |
     ------
     |    |
+---------+  +------+
| Logger  |  | ...  |
+---------+  +------+
```

### 13. Strategy Pattern
🔹 *Enables selecting an algorithm at runtime by encapsulating them into interchangeable strategy objects.*
```js
class DiscountContext {
  setStrategy(strategy) {
    this.strategy = strategy;
  }
  getDiscount(price) {
    return this.strategy.calculate(price);
  }
}
```
**UML:**
```
+--------------------+
|  DiscountContext   |
+--------------------+
| -strategy          |
| +setStrategy()     |
| +getDiscount()     |
+--------------------+
     |
     +-------------+
     |             |
+----------------+ +-----------------+
| RegularDiscount| | PremiumDiscount |
+----------------+ +-----------------+
```

### 14. Chain of Responsibility
🔹 *Passes a request along a chain of handlers where each one can handle it or pass it along.*
```js
class Handler {
  setNext(handler) {
    this.next = handler;
  }
  handle(request) {
    if (this.next) return this.next.handle(request);
  }
}
```
**UML:**
```
+-----------+
|  Handler  |
+-----------+
| -next     |
| +setNext()|
| +handle() |
+-----------+
     ^
    -----
   |     |
+-------------+ +----------------+
| AuthHandler | | LoggingHandler |
+-------------+ +----------------+
```

### 15. Command Pattern
🔹 *Encapsulates a request as an object, allowing undo, logging, or queuing.*
```js
class LightOnCommand {
  execute() {
    this.light.on();
  }
}
```
**UML:**
```
+----------------+
| RemoteControl  |
+----------------+
| -command       |
| +setCommand()  |
| +pressButton() |
+----------------+
       |
       v
+----------------+
| LightOnCommand |
+----------------+
       |
       v
   +--------+
   | Light  |
   +--------+
```

### 16. Template Method Pattern
🔹 *Defines the skeleton of an algorithm, letting subclasses fill in specific steps.*
```js
class CSVParser extends DataParser {
  processData() {
    console.log("Processing CSV data");
  }
}
```
**UML:**
```
+-------------+
| DataParser  |
+-------------+
| +parse()    |
| +readData() |
| +saveData() |
| +processData() (abstract) |
+-------------+
     |
     v
+---------------+
|  CSVParser    |
+---------------+
```

### 17. Memento Pattern
🔹 *Captures and externalizes an object’s internal state to restore it later.*
```js
const saved = editor.save();
editor.restore(saved);
```
**UML:**
```
+---------+        +----------+
| Editor  |<----->| Memento  |
+---------+        +----------+
| +save() |        | +getContent() |
| +restore()|      +----------+
+---------+
```

### 18. Mediator Pattern
🔹 *Reduces chaotic communication between multiple objects by centralizing it in a mediator.*
```js
class ChatRoom {
  showMessage(user, message) {
    console.log(`[${user.getName()}]: ${message}`);
  }
}
```
**UML:**
```
+-----------+     +-----------+
|  ChatRoom |<--->|   User    |
+-----------+     +-----------+
```

### 19. Interpreter Pattern
🔹 *Implements a grammar for interpreting expressions.*
```js
const expr = new AddExpression(new NumberExpression(5), new NumberExpression(3));
console.log(expr.interpret()); // 8
```
**UML:**
```
+----------------+         +----------------+
| Expression     |<--------| NumberExpression |
+----------------+         +----------------+
       ^
       |
+----------------+
| AddExpression  |
+----------------+
```

### 20. Visitor Pattern
🔹 *Allows adding new operations to existing class structures without modifying them.*
```js
book.accept(visitor);
magazine.accept(visitor);
```
**UML:**
```
+-----------+     +------------+
|  Visitor  |<----|  Elements  |
+-----------+     +------------+
| +visitBook()    | +accept()  |
+-----------+     +------------+
```
