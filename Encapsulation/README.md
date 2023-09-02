## Data hiding

Data hiding is an essential concept in object-oriented programming. In simple terms, it can be defined as masking a class's internal operations and only providing an interface through which other entities can interact with the class without being aware of what is happening within.

The goal is to implement classes in a way that prevents unauthorized access to or modification of the original contents of a class by its instances (or objects). The underlying algorithms of one class need not be known to another class. The two classes can still communicate, though.

## Encapsulation

<p align="center">
<img height="270" src="https://github.com/tutungduong/oop_java_pInsights/blob/main/Images/encapsulation.png">
</p>

Encapsulation is a fundamental programming technique used to achieve data hiding in OOP. Encapsulation in OOP refers to binding data and the methods to manipulate that data together in a single unit—class.

Encapsulation is usually done to hide the state and representation of an object from the outside. A class can be thought of as a capsule with methods and attributes inside it.

When encapsulating classes, a good convention is to declare all variables of a class private. This will restrict direct access by the code outside that class.

At this point, a question can be raised. If the methods and variables are encapsulated in a class, how can they be used outside that class? The answer to this is simple. One has to implement public methods to let the outside world communicate with this class. These methods are called getters and setters. We can also implement other custom methods.

## Encapsulation in java

We can achieve encapsulation in Java in the following ways.

- 1 Declaring the instance variable of the class as private. so that it cannot be accessed directly by anyone from outside the class.

- 2 Provide the public setter and getter methods in the class to set/modify the values of the variable/fields.

### Advantages

**1**. The encapsulated code is more flexible and easy to change with new requirements.<br>
**2**. It prevents the other classes to access the private fields.<br>
**3**. Encapsulation allows modifying implemented code without breaking others code who have implemented the code.<br>
**4**. It keeps the data and codes safe from external inheritance. Thus, Encapsulation helps to achieve security.<br>
**5**. It improves the maintainability of the application.<br>
**6**. If you don't define the setter method in the class then the fields can be made read-only.<br>
**7**. If you don't define the getter method in the class then the fields can be made write-only<br>

### Disavantages

The main disadvantage of the encapsulation in Java is it increases the length of the code and slow shutdown execution.

### Tightly Encapsulated Class

If each variable is declared as private in the class, it is called tightly encapsulated class in Java. For tightly encapsulated class, we are not required to check whether class contains getter and setter method or not and whether these methods are declared as public or not.

:bulb: **Key points:** <br>
**1**. It is highly recommended to declare data members as private in the class.<br>
**2**. A combination of data hiding and abstraction is nothing but encapsulation.
Encapsulation = Data Hiding + Abstraction <br>
If any component follows data hiding and abstraction, it is called an encapsulated component.
