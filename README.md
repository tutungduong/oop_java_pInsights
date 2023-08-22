# Table of Contents

1. [Object Oriented Programming](#OOP)
2. [Principles of OOP](#principles-OOP)
   - [Encapsulation](#encapsulation)
   - [Abstraction](#abstraction)
   - [Inheritance](#inheritance)
   - [Polymorphism](#polymorphism)
   - [Coupling](#coupling)
   - [Cohesion](#cohesion)
   - [Association](#association)
   - [Aggregation](#aggregation)
   - [Composition](#composition)
3. [Object and Clases](#objects-classes)
   - [Classes](#classes)
   - [Objects](#objects)
   - [Methods](#method)
   - [Constructor](#constructor)
   - [static](#static)
   - [this](#this)

## OOP - Object Oriented Programming <a name="OOP"></a>

Is a programming paradigm in which programs are organized around data, or based on the concept "objects", rather than functions and logic.

Basically an object can be defined as a data (attributes or properties) and behaviors (methods)

Simply put, OOP focuses on the objects that developers want to manipulate rather than the logic required to manipulate them. This approach to programming is well-suited for programs that are large, complex and actively updated or maintained. Due to the organization of an object-oriented program, this method is also conducive to collaborative development where projects can be divided into groups. Additional benefits of OOP include code reusability, scalability and efficiency.

OOP was developed to increase the reusability and maintainability of source code. Transparent representation of the control flow had no priority and was meant to be handled by a compiler. With the increasing relevance of parallel hardware and multithreaded coding, developing transparent control flow becomes more important, something hard to achieve with OOP

## Principles of OOP <a name="principles-OOP"></a>

<p align="center">
<img src="./Images/Pillar-OOP.png">
</p>

**Object Oriented Programming is based on the following principles**:

### `Encapsulation` <a name="encapsulation"></a>

The implementation and state of each object are privately held inside a defined boundary, or class.

Other objects do not have access to this class or the authority to make changes but are only able to call a list of public functions, or methods. This characteristic of data hiding provides greater program security and avoids unintended data corruption.

The meaning of **Encapsulation**, is to make sure that "sensitive" data is hidden from users. To achieve this, you must:

- declare class variables/attributes as `private`
- provide public get and set methods to access and update the value of a `private` variable

**Get and Set**

You learned from the previous chapter that `private` variables can only be accessed within the same class (an outside class has no access to it). However, it is possible to access them if we provide public **get** and **set** methods.

The `get` method returns the variable value, and the `set` method sets the value.

Syntax for both is that they start with either `get` or `set`, followed by the name of the variable, with the first letter in upper case:

**Example**

```java
public class Person {
  private String name; // private = restricted access

  // Getter
  public String getName() {
    return name; // return the value of the variable name
  }

  // Setter
  public void setName(String newName) {
    this.name = newName; // The set method takes a parameter (newName) and assigns it to the name variable
  }
}

```

**Why Encapsulation?**

- Better control of class attributes and methods
- Class attributes can be made read-only (if you only use the get method), or write-only (if you only use the set method)
- Flexible: the programmer can change one part of the code without affecting other parts
- Increased security of data

[See more about Encapsulation](https://github.com/tutungduong/OOP-PInsights/blob/main/Encapsulation)

### `Abstraction` <a name="abstraction"></a>

Abstract Classes and Methods

Objects only reveal internal mechanisms that are relevant for the use of other objects, hiding any unnecessary implementation code. This concept helps developers make changes and additions over time more easily.

Data abstraction is the process of hiding certain details and showing only essential information to the user.
Abstraction can be achieved with either abstract classes or interfaces (which you will learn more about in the next chapter).

- **Abstract class**: is a restricted class that cannot be used to create objects (to access it, it must be inherited from another class).
- **Abstract method**: can only be used in an abstract class, and it does not have a body. The body is provided by the subclass (inherited from).

An abstract class can have both abstract and regular methods:

Example:

```java
// Abstract class
abstract class Animal {
  // Abstract method (does not have a body)
  public abstract void sound();
  // Regular method
  public void sleep() {
    System.out.println("Zzz");
  }
}

// Subclass (inherit from Animal)
class Cat extends Animal {
  public void sound() {
    // The body of sound() is provided here
    System.out.println("The cat says: Miau");
  }
}

class Main {
  public static void main(String[] args) {
    Cat myCat = new Cat(); // Create a Cat object
    myCat.animalSound();
    myCat.sleep();
  }
}
```

[See more about Abstraction](https://github.com/tutungduong/OOP-PInsights/blob/main/Abstraction)

### `Inheritance` <a name="inheritance"></a>

Subclass and superclass

Relationships and subclasses between objects can be assigned, allowing developers to reuse a common logic while still maintaining a unique hierarchy. This property of OOP forces a more thorough data analysis, reduces development time and ensures a higher level of accuracy.

Is possible to inherit attributes and methods from one class to another. We group the "inheritance concept" into two categories:

- **subclass** (child) - the class that inherits from another class
- **superclass** (parent) - the class being inherited from

To inherit from a class, use the `extends` keyword.

Example

```java
class Vehicle {
  protected String brand = "Audi";        // Vehicle attribute
  public void honk() {                    // Vehicle method
    System.out.println("Tuut, tuut!");
  }
}

class Car extends Vehicle {
  private String modelName = "Mercedez";    // Car attribute
  public static void main(String[] args) {

    // Create a myCar object
    Car myCar = new Car();

    // Call the honk() method (from the Vehicle class) on the myCar object
    myCar.honk();

    // Display the value of the brand attribute (from the Vehicle class) and the value of the modelName from the Car class
    System.out.println(myCar.brand + " " + myCar.modelName);
  }
}
```

**Why And When To Use "Inheritance"?**

- It is useful for code reusability: reuse attributes and methods of an existing class when you create a new class.

  [See more about Inheritance](https://github.com/tutungduong/OOP-PInsights/blob/main/Inheritance)

### `Polymorphism` <a name="polymorphism"></a>

Objects are allowed to take on more than one form depending on the context. The program will determine which
meaning or usage is necessary for each execution of that object, cutting down on the need to duplicate code.

Refers to the ability of OOPs programming languages to differentiate between entities with the same name efficiently.

Polymorphism means "many forms", and it occurs when we have many classes that are related to each other by inheritance.

Like we specified in the previous chapter; Inheritance lets us inherit attributes and methods from another class. Polymorphism uses those methods to perform different tasks. This allows us to perform a single action in different ways

Example

```java
class Animal {
  public void animalSound() {
    System.out.println("The animal makes a sound");
  }
}

class Cat extends Animal {
  public void animalSound() {
    System.out.println("The cat says: Miau");
  }
}

class Dog extends Animal {
  public void animalSound() {
    System.out.println("The dog says: Guau");
  }
}

class Main {
  public static void main(String[] args) {
    Animal myAnimal = new Animal();  // Create a Animal object
    Animal myCat = new Cat();  // Create a Cat object
    Animal myDog = new Dog();  // Create a Dog object
    myAnimal.animalSound();
    myCat.animalSound();
    myDog.animalSound();
  }
}
```

**Why And When To Use "Inheritance" and "Polymorphism"?**

It is useful for code reusability: reuse attributes and methods of an existing class when you create a new class.

[See more about Polymorphism](https://github.com/tutungduong/OOP-PInsights/blob/main/Polymorphism)

### Coupling <a name="coupling"></a>

Coupling refers to the knowledge or information or dependency of another class. It arises when classes are aware of each other. If a class has the details information of another class, there is strong coupling. In Java, we use private, protected, and public modifiers to display the visibility level of a class, method, and field. You can use interfaces for the weaker coupling because there is no concrete implementation.

### Cohesion <a name="cohesion"></a>

Cohesion refers to the level of a component which performs a single well-defined task. A single well-defined task is done by a highly cohesive method. The weakly cohesive method will split the task into separate parts. The java.io package is a highly cohesive package because it has I/O related classes and interface. However, the java.util package is a weakly cohesive package because it has unrelated classes and interfaces.

### Association <a name="association"></a>

Association represents the relationship between the objects. Here, one object can be associated with one object or many objects. There can be four types of association between the objects:

- One to One
- One to Many
- Many to One, and
- Many to Many

Let's understand the relationship with real-time examples. For example, One country can have one prime minister (one to one), and a prime minister can have many ministers (one to many). Also, many MP's can have one prime minister (many to one), and many ministers can have many departments (many to many).

Association can be undirectional or bidirectional.

### Aggregation <a name="aggregation"></a>

Aggregation is a way to achieve Association. Aggregation represents the relationship where one object contains other objects as a part of its state. It represents the weak relationship between objects. It is also termed as a has-a relationship in Java. Like, inheritance represents the is-a relationship. It is another way to reuse objects.

### Composition <a name="composition"></a>

The composition is also a way to achieve Association. The composition represents the relationship where one object contains other objects as a part of its state. There is a strong relationship between the containing object and the dependent object. It is the state where containing objects do not have an independent existence. If you delete the parent object, all the child objects will be deleted automatically.

## Object and Classes

Exist two main concepts in OOP: Object and Classes.

#### Object:

- Instances of clases
- Object = instance

An instance is created so you can use the methods that that class defines.

It is a basic unit of Object Oriented Programming and represents the real life entities. A typical Java program creates many objects, which as you know, interact by invoking methods. An object consists of:

    State : It is represented by attributes of an object. It also reflects the properties of an object.

    Behavior : It is represented by methods of an object. It also reflects the response of an object with other objects.

    Identity : It gives a unique name to an object and enables one object to interact with other objects.

#### Class

Is a template that allow to create object, containt the definition of attributes and the procedure for the class

- They are used to represent entities or concepts
- Each object created from a class is called an instance of the class
- Has methods (Performs a task)
- It has attributes, by convention they must be private
- The name must begin with a capital letter

<strong>Static class:</strong>

- No need to create instances to call them
- Only static methods can be called

A class is a user defined blueprint or prototype from which objects are created. It represents the set of properties or methods that are common to all objects of one type. In general, class declarations can include these components, in order:

      Modifiers : A class can be public or has default access.

      Class name: The name should begin with a initial letter (capitalized by convention).

      Superclass(if any): The name of the class’s parent (superclass), if any, preceded by the keyword extends. A class can only extend (subclass) one parent.

      Interfaces(if any): A comma-separated list of interfaces implemented by the class, if any, preceded by the keyword implements. A class can implement more than one interface.

      Body: The class body surrounded by braces, { }.

## Other

### This vs Super

**This**

    The keyword this, is commonly used with constructors and setters, and optionally used in getters.

    In this example, we're using the this keyword in the constructor and setter, since there's a parameter with the same name, as the instance or field.

    In the getter we don't have any parameters, so there's no conflict, so therefore the this keyword is optional there.

<details>
<summary><strong> Keyword this </strong></summary>

<p >
<img height="350" src="../Images/keywork_this.png">
</p>

</details>

<br>

**Super**

    The keyword super, is commonly used with method overriding, when we call a method with the same name, from the parent class. .

    In this example, we have a method called printMethod, that calls super.printMethod.

<details>
<summary><strong> Keyword super </strong></summary>

<p align="center">
<img height="400" src="../Images/keywork_super.png">
</p>

</details>
<br>

**_Comparing Both Examples_**

<p align="center">
<img src="../Images/comparing_both.png">
</p>
<strong>Example for this() and super()</strong>

In this example, we have a class Shape, with x and y variables, and a class Rectangle that extends Shape, with variables width and height.
In the Rectangle class, the 1st constructor is calling the 2nd constructor.

The 2nd constructor calls the parent constructor, with parameters x and y.

The parent constructor will initialize the x and y variables, while the 2nd Rectangle constructor will initialize the width and height variables.

Here, we have both the super() and this() calls.

<p align="center">
<img height="400" src="../Images/super_this.png">
</p>
