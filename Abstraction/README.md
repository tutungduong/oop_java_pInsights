<!-- ## Abstract Class

- Abstract classes are very similar to interfaces. You can't instantiate either of them. Both types may contain a mix of methods declared with, or without a method block.
- With abstract classes, you can declare fields that aren't static and final, instance fields in other words.
- Also with abstract classes, you can use any of the four access modifiers for its concrete methods.
- You can also use all but the private access modifier, for its abstract methods.
- An abstract class can extend only one parent class, but it can implement multiple interfaces.
- When an abstract class is subclassed, the subclass usually provides implementations for all of the abstract methods in its parent class.
- However, if it doesn't, then the subclass must also be declared abstract. -->

# Abstraction

<p align="center">
<img height="250px" src="https://github.com/tutungduong/oop_java_pInsights/blob/main/Images/abstraction.png">
</p>

It is the process of hiding internal implementation details from the user and providing only necessary functionality to the users. It removes all non-essential things and shows only important things to users.

Data Abstraction may also be defined as the process of identifying only the required characteristics of an object ignoring the irrelevant details.The properties and behaviors of an object differentiate it from other objects of similar type and also help in classifying/grouping the objects.

In other words, Abstraction in Java is a technique by which we can hide the data that is not required to a user

Abstraction forces to use Inheritance

**Example**

We all use an ATM machine for cash withdrawal, money transfer, retrieve min-statement, etc in our daily life. But we don't know internally what things are happening inside ATM machine when you insert ATM card for performing any kind of operations.

**Use an Abstract class when...**

- You want to share code, among several closely related classes (Animal for example, with fields, name, age...).
- You expect classes that extend your abstract class, to have many common methods or fields, or require access modifiers other than public.
- You want to declare non-static or non-final fields (for example, name, age), so this enables you to define methods, that can access and modify the state of an object (getName, setName).
- You have a requirement for your base class, to provide a default implementation of certain methods, but other methods should be open to being overridden by child classes.
  `Summary: An abstract class provides a common definition, as a base class, that multiple, derived classes can share.`

## Abstraction in java

There are two ways to achieve abstraction in java. They are as follows:<br>
**1**. Abstract class (0 to 100%)<br>
**2**. Interface (100%)

### Advantages

**1**. It reduces the complexity of viewing the things.<br>
**2**. Avoids code duplication and increases reusability.<br>
**3**. Helps to increase security of an application or program as only important details are provided to the user.<br>
**4**. Programmer can implement abstract method to perform different tasks depending on the need.

### Abstract Class in Java

An abstract class is a class, which is declared with `abstract` keyword. It is just like a normal class but has two differences.<br>
**1**. We cannot create an object of this class. Only objects of its non-abstract (or concrete) sub-classes can be created.

**2**. It can have zero or more abstract methods which are not allowed in a non-abstract class (concrete class).

:bulb: Key points: <br>
**1**. Abstract is a non-access modifier in java which is applicable for classes, interfaces, methods, and inner classes. It represents an incomplete class which depends on subclasses for its implementation. Creating subclass is compulsory for abstract class.<br>
**2**. A non-abstract class is sometimes called a concrete class.<br>
**3**. An abstract concept is not applicable to variables.

`An abstract class can have a data member, abstract method, method body (non-abstract method), constructor, and even main() method.`

### Abstract Method in Java

A method which is declared with abstract modifier and has no implementation (means no body) is called an abstract method in java. It does not contain any body. It has simply a signature declaration followed by a semicolon. It has the following general form as given below.

**Syntax:** <br>

```java
abstract type MethodName(arguments); // No body
```

**For example:** <br>

```java
abstract ListItem setNext(ListItem item); //No body
```

Since the abstract method does not contain any body. Therefore, it is also known as an incomplete method in java. <br>
A non-abstract class cannot have an abstract method whether it is inherited or declared. In Java.

:bulb: Key points: <br>
**1**. Abstract method cannot be static.<br>
**2**. It cannot be private because the abstract method must be implemented in the subclass. If we declare it as private, we cannot implement it from outside the class.<br>
**3**. A concrete method is a method which has always the body. It is also called a complete method in java.

- Declares the existence of methods but not the implementation of those.
- An abstract class defines behaviors that can vary due to polyomorphism and that each explicit class that inherits from it must implement depending on its specific need.
- You cannot have an instance of an abstract class
- For a class to be abstract at least one of its methods must be abstract (this is the difference between a conventional class and an abstract class)
- An abstract class cannot be instantiated but it can be inherited (Objects cannot be created directly with new)
- Its use depends on the application of the concept of Inheritance
- The first concrete subclass that inherits from an abstract class must implement all the superclass's methods
- An abstract method does not define how it will behave since this logic is put in the classes that will implement the method
  An abstract class forces you to use inheritance

**Example Abstract class**

```java
public abstract class Animal {

    protected String type;
    private String size;
    private double weight;

    public Animal(String type, String size, double weight) {
        this.type = type;
        this.size = size;
        this.weight = weight;
    }

    public abstract void move(String speed);
    public abstract void makeNoise();
}

public class Dog extends Mammal {

    public Dog(String type, String size, double weight) {
        super(type, size, weight);
    }

    @Override
    public void move(String speed) {

        if (speed.equals("slow")) {
            System.out.println(getExplicitType() + " walking");
        } else {
            System.out.println(getExplicitType() + " running");
        }

    }
    @Override
    public void makeNoise() {

        if (type == "Wolf") {
            System.out.print("Howling! ");
        } else {
            System.out.print("Woof! ");
        }

    }
}

```

## Interface

<!-- - An interface is just the declaration of methods, which you want some classes to have, it's not the implementation.

- In an interface, we define what kind of operation an object can perform. These operations are defined by the classes that implement the interface.

- Interfaces form a contract between the class, and the outside world, and this contract is enforced at build time, by the Java compiler.
- You can't instantiate interfaces, but they may contain a mix of methods declared with, or without an implementation.

- All methods on interfaces, declared without a method body, are automatically public and abstract.

- An interface can extend another interface.

- Interfaces are more flexible, and can deal with a lot more stress on the design of your program, because they aren't part of the class hierarchy.

- A best practice way of coding, is commonly called Coding to an Interface.

- By introducing interfaces into your program, you're really introducing points of variation, at which you can plug in different implementations for that interface. -->

<!-- Another way to achieve abstraction in Java, is with interfaces.

The interface in Java is a mechanism to achieve abstraction. There can be only abstract methods in the Java interface, not method body. It is used to achieve abstraction and multiple inheritance in Java.

- It is an abstract class, that is, it cannot be instantiated
- It has a list of methods that have no definition. So the methods are abstract (they have no functionality)
- Java interface is a collection of abstract methods

- Since Java 8, interfaces can now contain default methods, so in other words methods with implementation. The keyword `default` is used mostly for backwards compatibility. Public static methods were also introduced in Java 8.

- Since Java 9, an interface can also contain private methods, commonly used when default methods share common code. -->

<!-- `Summary: The interface decouples the "what", from the "how", and is used to make different types, behave in similar ways.` -->

An interface is just like a class and specifies the behavior that a class must implement.

An interface can be used to achieve 100% abstraction as it contains the method signatures/abstract methods(what to be done) and no implementation details (how to be done) of these methods. In this way, interfaces satisfy the definition of abstraction. The implementation techniques of the methods declared in an interface are totally up to to the classes implementing that interface.

An interface can be thought of as a `contract` that a class has to fulfill while implementing an interface. According to this contract, the class that `implements` an interface has to `@Override` all the abstract methods declared in that very interface.

**Rules to be followed**

- An interface can have:

  - `abstract` method(s)
  - `default` method(s)
  - `static` method(s)
  - `private` method(s)
  - `private static` method(s)
  - `public static final` variable(s)

- All the methods declared or implemented in an interface are by default `public` and all the variables are by default `public static final.`

- Just like an `abstract` class, an `interface` cannot be instantiated.

- To use an interface, a class must `implement` all of the `abstract` method(s) declared in it.

- An interface cannot have constructor(s) in it.

- A class cannot extend from more than one class, but it can implement any number of interfaces.

- An interface can `extend` from another interface.

- An interface cannot be declared `private` or `protected.`

**Note:** `A class uses the keyword implements to use an interface but an interface uses the keyword extends to use another interface.`

<p align="center">
<img height="250px" src="https://github.com/tutungduong/oop_java_pInsights/blob/main/Images/implements.png">
</p>

**Use an Interface when...**

- You expect that unrelated classes will implement your interface. For example, two of Java's own interfaces, Comparable and Cloneable, can be implemented by many unrelated classes.
- You want to specify the behavior of a particular data type, but you're not concerned about who implements its behavior.
- You want to separate different behavior.

**About Information:**

- Like abstract classes, interfaces cannot be used to create objects (in the example above, it is not possible to create an "Animal" object in the MyMainClass)
- Interface methods do not have a body - the body is provided by the "implement" class
- On implementation of an interface, you must override all of its methods
- Interface methods are by default `abstract` and `public`
- Interface attributes are by default `public`, `static` and `final`
- An interface cannot contain a constructor (as it cannot be used to create objects)

**Example Interface class**

```java
// Interface definition for eating behavior
interface Eatable {
    void eat();
}

// The class represents a bird
class Bird implements Eatable {
    @Override
    public void eat() {
        System.out.println("Bird is eating seeds.");
    }

    public void fly() {
        System.out.println("Bird is flying.");
    }
}

// The class represents a fish
class Fish implements Eatable {
    @Override
    public void eat() {
        System.out.println("Fish is eating plankton.");
    }

    public void swim() {
        System.out.println("Fish is swimming.");
    }
}
```

### Multiple Inheritance

When a class is derived from more than a single base class, i.e. when a class has more than one immediate parent classes, it is an instance of `Multiple Inheritance. Example:`

- A `Hyundai` Elantra IS A `Car`
- A `Hyundai` Elantra IS A `Sedan` as well

<p align="center">
<img height="250px" src="https://github.com/tutungduong/oop_java_pInsights/blob/main/Images/multiple_implements.png">
</p>

**Implementation**

In Java, a class can’t extend from more than one class. So the question arises, “how can we implement multiple inheritance?”

The answer to the above question is `Interfaces`. In Java, multiple inheritance can be implemented using interfaces.

`Note: A class can implement more than one interfaces and an interface can extend from more than one interfaces.`

**Example Multiple Interface class**

```java
// Definition of interfaces
interface Swimmable {
    void swim();
}

interface Flyable {
    void fly();
}

// The class shows a bird that can fly and swim
class FlyingFish implements Swimmable, Flyable {
    @Override
    public void swim() {
        System.out.println("FlyingFish is swimming.");
    }

    @Override
    public void fly() {
        System.out.println("FlyingFish is flying.");
    }
}
```

**Java 8 Interface**

Since Java 8, interface can have default and static methods which is discussed later.

The Java compiler adds public and abstract keywords before the interface method. Moreover, it adds public, static and final keywords before data members.

In other words, Interface fields are public, static and final by default, and the methods are public and abstract.

```java
interface MyInterface {
    // Default method
    default void sayHello() {
        System.out.println("Hello from MyInterface");
    }

    // Static method
    static void greet() {
        System.out.println("Greetings from MyInterface");
    }
}

class MyClass implements MyInterface {
    // Overriding default method
    @Override
    public void sayHello() {
        System.out.println("Hello from MyClass");
    }
}

```

**Java 9 Interface**

Starting from JDK 9, interfaces can also contain private methods. These methods are useful for breaking down complex implementations into smaller reusable components without exposing them to implementing classes. Private methods can only be accessed within the interface itself and are not inherited by implementing classes.

```java
interface MyInterface {
    // Public abstract method
    void doSomething();

    // Private helper method
    private void internalHelper() {
        System.out.println("Doing internal work");
    }

    // Default method using the private helper
    default void doSomethingWithHelper() {
        internalHelper();
        System.out.println("Doing something with helper");
    }
}

class MyClass implements MyInterface {
    @Override
    public void doSomething() {
        System.out.println("Doing something");
    }
}

```

<!-- ## The relationship between classes and interfaces

As shown in the figure given below, a class extends another class, an interface extends another interface, but a class implements an interface.

<p align="center">
<img height="350" src="https://user-images.githubusercontent.com/13514156/120521854-a4ab4600-c39a-11eb-93e1-1bdf9fee8769.jpeg">
</p>

Example

```java
interface Bank{
float rateOfInterest();
}
class SBI implements Bank{
public float rateOfInterest(){return 9.15f;}
}
class PNB implements Bank{
public float rateOfInterest(){return 9.7f;}
}
class TestInterface2{
public static void main(String[] args){
Bank b=new SBI();
System.out.println("ROI: "+b.rateOfInterest());
}}
```

## Multiple inheritance in Java by interface

If a class implements multiple interfaces, or an interface extends multiple interfaces, it is known as multiple inheritance.

<p align="center">
<img height="350" src="https://user-images.githubusercontent.com/13514156/120522069-b4c32580-c39a-11eb-9c48-6331fe379440.png">
</p>

`Multiple inheritance is not supported through class in java, but it is possible by an interface, why?`

As we have explained in the inheritance chapter, multiple inheritance is not supported in the case of class because of ambiguity. However, it is supported in case of an interface because there is no ambiguity. It is because its implementation is provided by the implementation class. For example:

```java
interface Printable{
void print();
}
interface Showable{
void print();
}

class TestInterface3 implements Printable, Showable{
public void print(){System.out.println("Hello");}
public static void main(String args[]){
TestInterface3 obj = new TestInterface3();
obj.print();
 }
}

// RESULT
Hello
```

## Interface inheritance

A class implements an interface, but one interface extends another interface.

```java
interface Printable{
void print();
}
interface Showable extends Printable{
void show();
}
class TestInterface4 implements Showable{
public void print(){System.out.println("Hello");}
public void show(){System.out.println("Welcome");}

public static void main(String args[]){
TestInterface4 obj = new TestInterface4();
obj.print();
obj.show();
 }
}
```

## Default Method in Interface

```java
interface Drawable{
void draw();
default void msg(){System.out.println("default method");}
}
class Rectangle implements Drawable{
public void draw(){System.out.println("drawing rectangle");}
}
class TestInterfaceDefault{
public static void main(String args[]){
Drawable d=new Rectangle();
d.draw();
d.msg();
}}

// RESULT
drawing rectangle
default method
```

## Static Method in Interface

Since Java 8, we can have static method in interface

```java
interface Drawable{
void draw();
static int cube(int x){return x*x*x;}
}
class Rectangle implements Drawable{
public void draw(){System.out.println("drawing rectangle");}
}

class TestInterfaceStatic{
public static void main(String args[]){
Drawable d=new Rectangle();
d.draw();
System.out.println(Drawable.cube(3));
}}
``` -->

## Difference between abstract class and interface

- The main difference between interface and abstract class is that an interface provides an encapsulation mechanism for method protocols without forcing the user to use inheritance.
- But there are many differences between abstract class and interface that are given below.
<!-- 
|                                                              | Abstract class            | Interface                                                |
| ------------------------------------------------------------ | ------------------------- | -------------------------------------------------------- |
| An instance can be created from it                           | No                        | No                                                       |
| Has a constructor                                            | Yes                       | No                                                       |
| Implemented as part of the Class Hierarchy. Uses inheritance | Yes ( in extends clause ) | No ( in implements clause )                              |
| records and enums can extend or implement?                   | No                        | yes                                                      |
| Inherits from java.lang.Object                               | Yes                       | No                                                       |
| Can have both abstract methods and concrete methods          | Yes                       | Yes ( as of jDK8 )                                       |
| Abstract methods must include abstract modifier              | Yes                       | No ( implicit )                                          |
| Supports default modifier for it's methods                   | No                        | Yes ( as of jDK8 )                                       |
| Can have instance fields (non-static instance fields )       | Yes                       | No                                                       |
| Can have static fields (class fields)                        | Yes                       | Yes - ( implicity <strong>public static final</strong> ) |

| Abstract class                                                                                                                               | Interface                                                                                                                                                                                                               |
| -------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Abstract class can have abstract and non-abstract methods.                                                                                   | Interface can have only abstract methods. Since Java 8, it can have default and static methods also.                                                                                                                    |
| Abstract class doesn't support multiple inheritance.                                                                                         | Interface supports multiple inheritance.                                                                                                                                                                                |
| Abstract class can have final, non-final, static and non-static variables.                                                                   | Interface has only static and final variables.                                                                                                                                                                          |
| Abstract class can provide the implementation of interface.                                                                                  | Interface can't provide the implementation of abstract class.                                                                                                                                                           |
| The abstract keyword is used to declare abstract class.                                                                                      | The interface keyword is used to declare interface.                                                                                                                                                                     |
| An abstract class can extend another Java class and implement multiple Java interfaces.                                                      | An interface can extend another Java interface only.                                                                                                                                                                    |
| An abstract class can be extended using keyword "extends".                                                                                   | An interface can be implemented using keyword "implements".                                                                                                                                                             |
| A Java abstract class can have class members like private, protected, etc.                                                                   | Members of a Java interface are public by default.                                                                                                                                                                      |
| An abstract class can inherit from a single class (abstract or not)                                                                          | interface can extend several interfaces at the same time.                                                                                                                                                               |
| An abstract class can have methods that are or are not abstract                                                                              | interfaces can only and exclusively define abstract methods or a default method                                                                                                                                         |
| In abstract classes the word abstract is mandatory to define an abstract method (as well as the class)                                       | When you define an interface, this word is optional since it is inferred in the concept of interface.                                                                                                                   |
| Abstract classes, unlike interfaces, can have constructors, default method implementations and can only be inherited once from these.        | Although in java 8, default implementations are allowed, they cannot contain constructors. In the case of interfaces, if you can implement multiple of these                                                            |
| abstract classes are more used for base type objects. It is like the parent in the hierarchy in a set of objects that share the same parent. | The interfaces are known as a contract. This is because they force you to implement their methods, which ensures all business logic that every object that implements it will have access to the methods defined in it. |
| Abstract think more about objects                                                                                                            | Interface think more about implementation                                                                                                                                                                               |

| parameters                            | Abstract class                                 | Interface                   |
| ------------------------------------- | ---------------------------------------------- | --------------------------- | --- |
| keyword used                          | abstract                                       | interface                   |
| Type of variable                      | static and non-static                          | static                      |
| Access modifiers                      | All access modifiers                           | Only public acces modifiers |
| speed                                 | Fast                                           | Slow                        |
| When to used                          | To avoid independence                          | For future Enhancement      | --> |
| Interfaces                            | Abstract Classes                               |
| ------------------------------------- | ---------------------------------------------- |
| Support multiple inheritance          | Don’t support multiple inheritance             |
| All members are public                | Can have private, protected and public members |
| All access modifiers                  | Only public acces modifiers                    |
| All data members are static and final | Can have non-static and non-final members too  |
| Can’t have constructors               | Constructors can be defined                    |

<!-- <p align="center">
<img src="../Images/interface_and_abstract.png">
</p> -->

<!-- Example:

```java
public abstract class Shape{
public abstract void draw();
}
```

Example:

```java
public interface Drawable{
void d
aw();
}
``` -->

Simply, abstract class achieves partial abstraction (0 to 100%) whereas interface achieves fully abstraction (100%).

**Example of abstract class and interface**

Let’s implement the example of Elantra given at the start of the lesson. This example can be implemented using:

- A base class named `Car`
- An interface named `IsSedan`
- An `Elantra` class derived from `Car` and implementing `IsSedan`

The above illustration then becomes:

<p align="center">
<img height="250px" src="https://github.com/tutungduong/oop_java_pInsights/blob/main/Images/interface.png">
</p>

```java
class Car {  // Base class

  private int model;  // Common features of all cars
  private String manufacturer;

  public Car(int model, String manufacturer) {  // Constructor
    this.model = model;
    this.manufacturer = manufacturer;
  }

  public void printDetails() {

    System.out.println("The model of " + getClass().getSimpleName() + " is: " + model);
    System.out.println("The manufacturer of " + getClass().getSimpleName() + " is: " + manufacturer);
  }

}  // End of Car class

interface IsSedan {  // Interface for sedans

  int bootSpace = 420;  // Sedans have boot space

  void bootSpace();    // Every sedan must implement this

}  // End of IsSedan interface

class Elantra extends Car implements IsSedan {  // Elantra is a Car and is a Sedan also

  private String variant;    // Elantra's data member

  public Elantra(int model, String variant) {  // Constructor
    super(model, "Hyundai");  // Calling the parent constructor with alredy known manufacturer
    this.variant = variant;
  }

  @Override
  public void bootSpace() { // Implementation of the interface method
    System.out.println("The bootspace of Elantra is: " + IsSedan.bootSpace +" litres");
  }

  @Override
  public void printDetails() {  // Overriding the parent class's inherited method
    super.printDetails();    // Calling the method from parent class
    System.out.println("The variant of Elantra is: " + variant); // printing the data member of this class
  }

}  // End of Elantra class


class Main {

  public static void main(String[] args) {

    Elantra sport = new Elantra(2019, "Sport");  //creating Sports variant Elantra
    Elantra eco = new Elantra(2018, "Eco");      //creating Eco variant Elantra

    sport.printDetails();
    sport.bootSpace();

    System.out.println();

    eco.printDetails();
    eco.bootSpace();
  }

}
```

<!-- ```java
// Abstract class
abstract class Animal {
    String name;

    Animal(String name) {
        this.name = name;
    }

    // Abstract method
    abstract void makeSound();

    // Concrete method
    void sleep() {
        System.out.println(name + " is sleeping.");
    }
}

// Interface
interface Swimmable {
    void swim();
}

// Concrete class that extends the abstract class and implements the interface
class Dolphin extends Animal implements Swimmable {
    Dolphin(String name) {
        super(name);
    }

    @Override
    void makeSound() {
        System.out.println(name + " makes a clicking sound.");
    }

    @Override
    public void swim() {
        System.out.println(name + " is swimming gracefully.");
    }
}
``` -->
