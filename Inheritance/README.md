# Table of Contents

1. [Class and Object](#Class-And-Object)

   - [Constructor](#Constructor)
   - [Static and Instance Method](#Static-and-Method)

1. [Type of inheritance](#type-inheritance)
   - [Single Inheritance](#single-inheritance)
   - [Multiple Inheritance](#multiple-inheritance)
   - [Multilevel Inheritance](#multilevel-inheritance)
   - [Hierarchical Inheritance](#hierarchical-inheritance)
   - [Hybrid Inheritance](#hybrid-inheritance)
1. [Aggregation](#aggregation)

## Class And Object

#### CLASS:

A class is a user defined blueprint or prototype from which objects are created. It represents the set of properties or methods that are common to all objects of one type. In general, class declarations can include these components, in order:

    Modifiers : A class can be public or has default access.

    Class name: The name should begin with a initial letter (capitalized by convention).

    Superclass(if any): The name of the class’s parent (superclass), if any, preceded by the keyword extends. A class can only extend (subclass) one parent.

    Interfaces(if any): A comma-separated list of interfaces implemented by the class, if any, preceded by the keyword implements. A class can implement more than one interface.

    Body: The class body surrounded by braces, { }.

#### OBJECT:

An object is an instance of a class.Technically, Class is a template which describes what state and behavior of an instance this class can have. Object implements the state and behavior in the form of variables and methods and requires some memory allocated. An object consists of:

    State : It is represented by attributes of an object. It also reflects the properties of an object.

    Behavior : It is represented by methods of an object. It also reflects the response of an object with other objects.

    Identity : It gives a unique name to an object and enables one object to interact with other objects.

### CONSTRUCTOR:

A constructor is used in the creation of an object, that's an instance of a class.

It is a special type of code block that has a specific name and parameters, much like a method.

It has the same name as the class itself, and it doesn't return any values.

You never include a return type from a constructor, not even void.

You can, and should, specify an appropriate access modifier, to control who should be able to create new instances of the class.

```java
public class Account { // This is the class declaration
    public Account(){ // This is the constructor declaration
        // Constructor code is code to be executed as the object is created.
    }
}
```

**THE DEFAULT CONSTRUCTOR**

If a class contains no constructor declarations, then a default constructor is implicitly declared.

This constructor has no parameters, and is often called the no-args (no arguments) constructor.

If a class contains any other constructor declarations, then a default constructor is NOT implicitly declared.

<details>
<summary><strong>Example for Constructor</strong></summary>

```java
public class Customer {

    private String name;
    private double creditLimit;
    private String email;

    public Customer() {
        this("Nobody", "nobody@nowhere.com");
    }

    public Customer(String name, String email) {
        this(name, 1000, email);
    }

    public Customer(String name, double creditLimit, String email) {
        this.name = name;
        this.creditLimit = creditLimit;
        this.email = email;
    }

    public class Main {

    public static void main(String[] args) {

        Customer customer = new Customer("Tim", 1000,
                "tim@email.com");
        System.out.println(customer.getName());
        System.out.println(customer.getCreditLimit());
        System.out.println(customer.getEmail());

        Customer secondCustomer = new Customer();
        System.out.println(secondCustomer.getName());
        System.out.println(secondCustomer.getCreditLimit());
        System.out.println(secondCustomer.getEmail());

        Customer thirdCustomer = new Customer("Joe", "joe@email.com");
        System.out.println(thirdCustomer.getName());
        System.out.println(thirdCustomer.getCreditLimit());
        System.out.println(thirdCustomer.getEmail());
    }
}

```

</details>

#### STATIC AND INSTANCE METHOD

**Static Methods**

Static methods are declared using a static modifier. Static methods can't access instance methods and instant variables directly. They're usually used for operations that don't require any data from an instance of the class (from 'this'). If you remember, the this keyword is the current instance of a class.

So inside a static method, we can't use the this keyword. Whenever you see a method that doesn't use instance variables, that method should probably be declared as a static method. For example, main is a static method, and it's called by the Java virtual machine when it starts the Java application.

<details>
<summary><strong> Example for Static Methods</strong></summary>
<p align="center">
<img height="280" src="../Images/Static_methods.png">
</p>

</details>
<br>

**Instance Methods**

Instance methods belong to an instance, of a class. To use an instance method, we have to instantiate the class first, usually by using the new keyword.

Instance methods can access instance methods and instance variables directly.

Instance methods can also access static methods and static variables directly.

<details>
<summary><strong> Example for Instance Methods</strong></summary>

```java
class Dog{
    public void bark(){
        System.out.println("woof");
    }
}

public class Main{
    public static void main(String[] args) {
        Dog rex = new Dog();        // create instance
        rex.bark();                 // call instance method
    }
}
```

</details>
<br>

**Why use Static or Instance Method in java**

<p align="center">
<img height="270" src="../Images/static_and_instance.png">
</p>
