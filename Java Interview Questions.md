# Important Java Interview questions

|Table of content |
|:-----------------------|
| [ 01. What do you know about JVM, JRE, and JDK](#01-what-do-you-know-about-jvm-jre-and-jdk) |
| [ 02. 02. Is JRE Platform Dependent or Independent?](#02-is-jre-platform-dependent-or-independent) |
| [ 03. What is the Ultimate Base Class in Java Class Hierarchy? List the name of methods of it. ](#03-what-is-the-ultimate-base-class-in-java-class-hierarchy-list-the-name-of-methods-of-it) |
| [ 19. Explain upcasting ](#19-explain-up-casting) |
| [ 20. Explain Dynamic Method Dispatch](#20-explain-dynamic-method-dispatch) |
|[ 21. What do you know about final keyword? ](#21-what-do-you-know-about-final-keyword) |

---
### 01. What do you know about JVM, JRE, and JDK

**Definition:**
- **JVM (Java Virtual Machine):** JVM is an integral part of the Java Runtime Environment (JRE) responsible for executing Java bytecode. It abstracts the underlying hardware and provides a platform-independent environment for Java applications.

- **JRE (Java Runtime Environment):** JRE includes the JVM and essential runtime libraries required for running Java applications. It does not contain development tools such as compilers and debuggers.

- **JDK (Java Development Kit):** JDK is a complete development package for Java applications. It includes the JRE, development tools (compiler, debugger), and additional utilities to develop, compile, and run Java code.

**Concept:**
- JVM allows Java programs to be executed on various platforms without modification.
- JRE provides the runtime environment for Java applications, ensuring they can run on a target system.
- JDK is used by developers to write, compile, and run Java applications. It includes JRE for testing purposes.

**Example:**
- Imagine you want to run a Java program on your computer. You need JRE installed to execute the program. To develop Java programs, you would use JDK, which includes JRE along with development tools.

**Real-Life Relatable Example:**
- Think of JRE as a car engine that makes your car (Java program) run smoothly. JDK is like an auto shop with tools and parts (development tools) to build and maintain the car.

**Advantages:**
- JVM ensures Java's platform independence.
- JRE simplifies the deployment of Java applications.
- JDK provides a comprehensive development environment.

**Limitations:**
- JVM performance can vary based on the implementation.
- JRE may not include certain tools needed for advanced development tasks.
- JDK requires more disk space due to the inclusion of development tools.

---
### 02. Is JRE Platform Dependent or Independent?

**Definition:**
JRE (Java Runtime Environment) is platform-independent. It is designed to provide a consistent runtime environment for Java applications across different platforms. This means that Java applications compiled on one platform can run on any platform with a compatible JRE without modification.

**Concept:**
JRE's platform independence is achieved through the use of the Java Virtual Machine (JVM), which abstracts the underlying hardware and operating system details. When you run a Java application with JRE, it is executed by the JVM, ensuring that the application behaves consistently regardless of the platform it runs on.

**Example:**
Suppose you have a Java application developed on a Windows computer. You can package the application with JRE and then run it on a macOS or Linux system with the appropriate JRE installed, and it will work without any platform-specific adjustments.

**Real-Life Relatable Example:**
Think of JRE as a universal translator for Java applications. It ensures that the same Java program can "speak" and run correctly on different "languages" (platforms).

**Advantages:**
1. Simplifies cross-platform Java application development.
2. Reduces the need for platform-specific coding.
3. Enhances the portability of Java applications.

**Limitations:**
While JRE itself is platform-independent, you may encounter platform-specific issues in your Java code if it relies on platform-specific features or dependencies. Careful coding practices are necessary to ensure complete platform independence.

---
### 03. What is the Ultimate Base Class in Java Class Hierarchy? List the name of methods of it.

 The ultimate base class in the Java class hierarchy is the `Object` class.

**Additional Information:**

- The `Object` class is a fundamental class in Java and serves as the root class for all other classes.
- It is located at the top of the class hierarchy, meaning that every class in Java is either directly or indirectly derived from the `Object` class.
- The `Object` class provides a set of common methods and behaviors that are inherited by all Java objects.

### Methods of the `Object` Class

1. **`equals(Object obj)`**
   - **Definition:** Compares the content of two objects for equality.
   - **Usage:** Often overridden in custom classes to provide meaningful equality checks.

2. **`hashCode()`**
   - **Definition:** Returns a hash code value for the object.
   - **Usage:** Used in hash-based data structures like `HashMap` for efficient storage and retrieval.

3. **`toString()`**
   - **Definition:** Returns a string representation of the object.
   - **Usage:** Often overridden to provide a human-readable description of the object.

4. **`getClass()`**
   - **Definition:** Returns the runtime class of an object.
   - **Usage:** Useful for determining the class of an object at runtime.
---
### 19. Explain Up Casting
**Defination:** Upcasting in Java is the process of converting a reference of a subclass to a reference of its superclass. In simpler terms, it's when you treat an object of a derived class as an object of its base class.


**Concept:**
When you upcast, you're essentially widening the scope of what the object can do, as it gains access only to the methods and fields of the superclass. This is done implicitly in Java, meaning you don't need to explicitly cast it.

**Example:**
Let's say we have a class hierarchy like this:
```java
class Animal {
    void makeSound() {
        System.out.println("Animal makes a sound");
    }
}

class Dog extends Animal {
    void makeSound() {
        System.out.println("Dog barks");
    }
}
```
Now, you can upcast a Dog object to an Animal reference:
```java
Animal myAnimal = new Dog();
myAnimal.makeSound(); // This will call the overridden method in Dog: "Dog barks"
```
### Real-Life Example:
Think of upcasting like a universal remote control. Imagine you have a universal remote that can control various electronic devices. The remote has basic functions that are common to all devices, like power on/off and volume control. When you use the remote to control a specific device, you're essentially "upcasting" it to behave like that device, even though it's a universal remote with limited functions.

### Advantages

**Polymorphism:** Upcasting allows you to write more flexible and reusable code by treating objects of different classes in a common way.

**Simplified Code:** It can make your code simpler and more concise by reducing the need for conditional checks on object types.

**Maintenance:** When you add new subclasses, your existing code doesn't need modification as long as they inherit from the same superclass.


### Limitations:
**Limited Access:**
After upcasting, you can only access the methods and fields of the superclass. Any specific behavior of the subclass is hidden.

**Runtime Errors:** 
If you upcast to a superclass and then try to access a method or field unique to the subclass, it will result in a **runtime error**.

**Loss of Type-Specific Functionality:** Upcasting may lead to a loss of type-specific functionality, which might be needed in some situations.

---
### 20. Explain Dynamic Method Dispatch

**Definition:**
Dynamic Method Dispatch in Java is a mechanism that allows a subclass to provide a specific implementation of a method that is already defined in its superclass. It enables the selection of the method to be executed at runtime based on the actual object type, rather than the reference type.

**Concept:**
With Dynamic Method Dispatch, you can call a method on an object using a reference to its superclass. The actual method executed depends on the type of object the reference is pointing to, making it a runtime decision.

#### Example:
Consider a class hierarchy:
```java
class Animal {
    void makeSound() {
        System.out.println("Animal makes a sound");
    }
}

class Dog extends Animal {
    void makeSound() {
        System.out.println("Dog barks");
    }
}

class Cat extends Animal {
    void makeSound() {
        System.out.println("Cat meows");
    }
}
```
Now, using Dynamic Method Dispatch:

```java
Animal myAnimal1 = new Dog();
Animal myAnimal2 = new Cat();

myAnimal1.makeSound(); // Output: "Dog barks"
myAnimal2.makeSound(); // Output: "Cat meows"
```

### Real-Life Analogy:
Think of Dynamic Method Dispatch like a music player with interchangeable speakers. You have a music player with a "play" button. Depending on the type of speakers you connect (e.g., rock speakers, jazz speakers), the sound output varies, but you still use the same "play" button.

### Advantages:

**Polymorphism:** Promotes code flexibility and reusability by allowing different implementations of methods in subclasses.

**Method Overriding:** Facilitates method overriding, enabling subclasses to provide their own implementation of inherited methods.

**Run-time Flexibility:** Decides the method to execute at runtime, adapting to the actual object type.

### Limitations:

**Performance Overhead:** Dynamic Method Dispatch introduces a slight performance overhead compared to static method calls.

**Complexity:** In complex class hierarchies, it may become challenging to track method execution paths.

---

### 21. What do you know about final keyword?

**Definition:**
In Java, the final keyword is used to indicate that a variable, method, or class cannot be modified, overridden, or extended, respectively, once it's declared with final.

**Concept:**
The final keyword in Java signifies something as unchangeable or constant. It enforces the idea of "one-time setup and no modification" for variables, methods, and classes. It ensures that once something is marked as final, it cannot be altered or overridden, providing consistency and preventing unintended changes in your codebase.

**Usage:**

**Final Variable:** A **final** variable cannot be reassigned after its initial value is set.

**Final Method:** A **final** method in a class cannot be overridden by any subclass.

**Final Class:** A **final** class cannot be extended by other classes.

```java
final int x = 10; // Final variable
class Parent {
    final void display() { // Final method
        System.out.println("This method cannot be overridden.");
    }
}

final class FinalClass { // Final class
    // Class definition
}
```
### Real-Life Analogy:
The final keyword is like sealing an envelope. Once sealed, you can't change what's inside. Similarly, in Java, marking something as final means it can't be modified or overridden, ensuring its integrity and consistency.

### Advantages:

**Immutable Values:** 
Final variables ensure that their values remain constant, which can be useful for constants or thread safety.

**Method Security:** Final methods prevent unintended method overriding, ensuring consistency in behavior.

**Class Integrity:** Final classes protect their integrity, preventing inheritance and unintended modifications.

### Limitations:

**Immutability:** Final variables cannot be changed, which may not be suitable for every situation.

**Extensibility:** Final classes cannot be extended, limiting the ability to build on existing code.

---