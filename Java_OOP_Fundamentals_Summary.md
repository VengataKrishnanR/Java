
# Java OOP Fundamentals — Structured Summary

## 1. Overview
**OOP** stands for **Object-Oriented Programming** — a programming paradigm where everything revolves around **objects**.  
Objects represent **real-world entities** with:
- **Properties** (state/data)
- **Behaviors** (functions/methods)

### Key Differences from Procedural Programming
| Procedural Programming | OOP |
|------------------------|-----|
| Focuses on **functions** | Focuses on **data** |
| Data moves freely between functions | Data is controlled via objects |
| No strict data hiding | Strong data hiding through encapsulation |
| Tight coupling between code parts | Loose coupling via encapsulation and abstraction |

---

## 2. Objects & Classes

### **Object**
- Real-world entity with:
  - **Properties** (state) → e.g., Car color, breed of dog
  - **Behaviors** (methods) → e.g., drive, bark, sleep
- Example:  
  **Dog**  
  - Properties: breed, color, age  
  - Behaviors: bark(), eat(), sleep()

### **Class**
- Blueprint/template for creating objects.
- Defines **properties** and **behaviors** once, objects can be created from it.
- Multiple objects can be created from the same class with their own unique property values.

**Analogy:** Class = Recipe, Object = Cake

---

## 3. Four Pillars of OOP

### **1. Abstraction**
- **Definition:** Hiding internal implementation and showing only essential features.
- **Example:** Car brake pedal — you know pressing it slows the car, but not *how* it works internally.
- **Achieved via:** Interfaces & Abstract Classes
- **Advantages:**
  - Hides complexity
  - Increases security/confidentiality
  - Simplifies client code

---

### **2. Encapsulation**
- **Definition:** Bundling data (variables) and methods that operate on that data into a single unit (class).
- **Also known as:** Data Hiding
- **Control via:** Access Modifiers (`private`, `public`, `protected`, `default`)
- **Example:**  
  Dog class has:
  - Property: `color` (private)
  - Methods: `getColor()` and `setColor()` (public)
  - Other classes must use these methods to access/change `color`.

**Analogy:** Capsule medicine — data inside is protected.

---

### **3. Inheritance**
- **Definition:** Ability of one class (child/subclass) to acquire properties and behaviors from another class (parent/superclass).
- **Keyword:** `extends`
- **Types:**
  1. Single Inheritance
  2. Multilevel Inheritance
  3. Hierarchical Inheritance
  4. Multiple Inheritance (Not allowed in Java — leads to **Diamond Problem**, solved via Interfaces)
- **Advantages:**
  - Code reusability
  - Enables polymorphism

**Example:**  
`Car` inherits from `Vehicle` → `Car` gets `Vehicle`'s properties/methods and can have its own.

---

### **4. Polymorphism**
- **Definition:** Same method behaving differently in different contexts.
- **Types:**
  1. **Compile-time (Static) Polymorphism / Method Overloading**  
     - Same method name, different parameter lists (type/number).
     - Decided at compile time.
  2. **Runtime (Dynamic) Polymorphism / Method Overriding**  
     - Child class redefines parent's method with same name, return type, and parameters.
     - Decided at runtime based on object type.

**Analogy:** A person can be a father, husband, and employee — different roles in different contexts.

---

## 4. Relationships in OOP

### **"Is-a" Relationship**
- Based on Inheritance.
- Example: `Dog` is an `Animal`.

### **"Has-a" Relationship**
- Based on Composition/Aggregation.
- One class contains an object of another class.
- **Aggregation (Weak)**: Objects can exist independently. Example: School and Students.
- **Composition (Strong)**: Objects are strongly dependent. Example: School and Classrooms.

---


---

## 5. Quick Revision Table

| Concept        | Definition | Achieved via | Example |
|----------------|------------|--------------|---------|
| Abstraction    | Show only essential details | Interfaces, Abstract classes | Car brake |
| Encapsulation  | Bundle data + methods, hide details | Classes + Access Modifiers | Dog's color with getter/setter |
| Inheritance    | Acquire parent's properties/methods | `extends` keyword | Car from Vehicle |
| Polymorphism   | Same method, different behavior | Overloading, Overriding | Person roles |

---

## 6. ASCII Diagram — OOP Structure

```
          [Class: Vehicle]
         /                 [Class: Car]           [Class: Bike]
   |                        |
[Car Object]           [Bike Object]
```



