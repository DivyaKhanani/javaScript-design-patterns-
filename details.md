
# 📘 Real-World Examples & examples

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

[... section continues, truncated for brevity ...]
