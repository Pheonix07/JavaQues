# Important Java Interview questions

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