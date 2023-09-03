## Polymorphism

<!-- - Polymorphism lets us write code to call a method, but at runtime, this method's behavior can be different, for different objects.
- This means the behavior that occurs, while the program is executing, depends on the runtime type of the object.
- And the runtime type, might be different from the declared type in the code.
- The declared type has to have some kind of relationship to the runtime type, and inheritance is one way to establish this relationship.
- There are other ways, but in this here, we'll talk about how to use inheritance, to support polymorphism. -->

The word **polymorphism** is a combination of two Greek words, “poly” meaning many, and “morph” meaning forms. In programming, polymorphism is a phenomenon that allows an object to have several different forms and behaviors.

For example, take the `Animal` class. There are many different animals, e.g., lion, deer, dog, and crocodile, etc. So, they are all animals, but their properties are different. The animal class can have a method, `makeNoise`. Its implementation should be different for a lion, deer, or any other animal as they all have different noises. This is called polymorphism.

<p align="center">
<img height="250px" src="https://github.com/tutungduong/oop_java_pInsights/blob/main/Images/polymorphism.png">
</p>

**Polymorphism in action**

That was polymorphism in action.

- It's the ability to execute different behavior, for different types, which are determined at runtime. And yet we did it with just two statements, in the main method, as shown here.

```java
    Movie movie = Movie.getMovie(type,title);
    movie.watchMovie();
```

- Polymorphism enables you to write generic code, based on the base class, or a parent class. And this code, in the main method, is extendable, meaning it doesn't have to change, as new subclasses become available.
- This code can handle any instances that are a Movie, or a subclass of movie, that are returned from the factory method.

**Example for Polymorphism**

```java
public class Car {

    private String description;

    public Car(String description) {
        this.description = description;
    }

    public void startEngine() {
        System.out.println("Car -> startEngine");
    }

    protected void runEngine() {
        System.out.println("Car -> runEngine");
    }

    public void drive() {
        System.out.println("Car -> driving, type is " + getClass().getSimpleName());
        runEngine();
    }
}

class GasPoweredCar extends Car {

    private double avgKmPerLiter;
    private int cylinders = 6;

    public GasPoweredCar(String description) {
        super(description);
    }

    public GasPoweredCar(String description, double avgKmPerLiter, int cylinders) {
        super(description);
        this.avgKmPerLiter = avgKmPerLiter;
        this.cylinders = cylinders;
    }

    @Override
    public void startEngine() {
        System.out.printf("Gas -> All %d cylinders are fired up, Ready!%n", cylinders);
    }

    @Override
    protected void runEngine() {
        System.out.printf("Gas -> usage exceeds the average: %.2f %n", avgKmPerLiter);
    }
}

```

### Types of polymorphism

There are two types of polymorphism: dynamic polymorphism and static polymorphism, as shown in the figure below.

<p align="center">
<img src="https://github.com/tutungduong/oop_java_pInsights/blob/main/Images/type_polymorphism.svg">
</p>

#### Dynamic polymorphism

**Dynamic polymorphism** is the mechanism that defines the methods with the same name, return type, and parameters in the base class and derived classes. Hence, the call to an overridden method is decided at runtime. That is why dynamic polymorphism is also known as **runtime polymorphism**. It is achieved by method overriding.

#### Method overriding

In object-oriented programming, if a subclass provides a specific implementation of a method that had already been defined in one of its parent classes, it is known as method overriding.

Suppose we have a parent class, Animal, with its subclass, Lion. Below is the implementation of two functions with the same name in each class to check method overriding behavior.

```java
class Animal {
	public void printAnimal() {
		System.out.print("I am from the Animal class\n");
	}
	void printAnimalTwo() {
		System.out.print("I am from the Animal class\n");
	}
}

class Lion extends Animal {
	// method overriding
	public void printAnimal() {
		System.out.print("I am from the Lion class\n");
	}
}

public class main {
	public static void main(String[] args) {
		Animal animal;
		Lion lion = new Lion();
		animal = lion;

		animal.printAnimal();
		animal.printAnimalTwo();
	}
}

```

#### Static polymorphism

Static polymorphism is also known as compile-time polymorphism, and it is achieved by method overloading or operator overloading.

#### Method overloading

Methods are said to be **overloaded** if a class has more than one method with the same name, but either the number of arguments is different, or the type of arguments is different. We have implemented method overloading using two functions with the same name but with different numbers of arguments. You can see this in the implementation below.

```java
class Calculator {

  int add(int num1, int num2) {
    return num1 + num2;
  }

  int add(int num1, int num2, int num3) {
    return num1 + num2 + num3;
  }

  public static void main(String args[]) {

    Calculator obj = new Calculator();
    System.out.println("10 + 20 = " + obj.add(10, 20));
    System.out.println("10 + 20 + 30 = " + obj.add(10, 20, 30));
  }

}
```

#### Operator overloading (Only Java language is not used)

**Operators** can be overloaded to operate in a certain user-defined way. Its corresponding method is invoked to perform its predefined function whenever an operator is used. For example, when the `+` operator is called, it invokes the special function, `add`, but this operator acts differently for different data types. The `+` operator adds the numbers when it is used between two `int` data types and merges two strings when used between `string` data types.

Let’s look at the implementation below, where we’ve overloaded the + operator to add complex numbers instead of simply adding two real numbers.

```c++
#include<iostream>
using namespace std;

class ComplexNumber {
private:
	int real, imaginary;
public:
	// Constructor
	ComplexNumber(int r = 0, int i = 0) {real = r; imaginary = i;}

	// Overloading function for + operator
	ComplexNumber operator + (ComplexNumber const &c) {
		ComplexNumber result;
		result.real = real + c.real;
		result.imaginary = imaginary + c.imaginary;
		return result;
	}

	// display results
	void display() {
		cout << "( " << real << " + " << imaginary << " i )" << '\n';
	}
};

int main() {
	ComplexNumber c1(11, 5), c2(2, 6);
	ComplexNumber c3 = c1 + c2;
	c3.display();
}
```

<!-- ## Method Overloading and Overriding

### Method Overloading (Compile time Polymorphism)

`Method overloading` means providing two or more separate methods, in a class, with the `same name`, but `different parameters`. Method return type may or may not be different, and that allows us to reuse the same method name. To the code calling an overloaded method, it looks like a single method can be called, with different sets of arguments.

In actuality, each call that's made with a different set of arguments, is calling a separate method.

Java developers often refer to method overloading, as compile-time polymorphism. This means the compiler is determining the right method to call, based on the method name and argument list. Usually `overloading` happens within a `single class`. But methods can also be overloaded by subclasses.

That's because, a subclass inherits one version of the method from the parent class, and then the subclass can have another overloaded version of that method.

Let’s see this in action by overloading the product method in the Calculator class:

```java
class Calculator {

  public double product(double x, double y) {
    return x * y;
  }

  // Overloading the function to handle three arguments
  public double product(double x, double y, double z) {
    return x * y * z;
  }

  // Overloading the function to handle int
  public int product(int x, int y){
    return x * y;
  }

}

class Demo {

  public static void  main(String args[]) {
    Calculator cal = new Calculator();

    double x = 10;
    double y = 20;
    double z = 5;

    int a = 12;
    int b = 4;

    System.out.println(cal.product(x, y));
    System.out.println(cal.product(x, y, z));
    System.out.println(cal.product(a, b));
  }

}
```

`Note: Methods that have no arguments and differ only in the return types cannot be overloaded since the compiler won’t be able to differentiate between their calls.`
**Advantages of method overloading**
One might wonder if we could simply create new methods to perform different jobs rather than overloading the same method. However, an obvious benefit is that the code becomes simple and clean. We don’t have to keep track of different methods.

Polymorphism is a very important concept in object-oriented programming, and method overloading plays a vital role in its implementation.
**Method Overloading Rules**

Methods will be considered overloaded if both methods follow the following rules:

- Methods must have the same method name.
- Methods must have different parameters.

If methods follow the rules above:

- They may or may not have different return types.
- They may or may not have different access modifiers.
- They may or may not throw different checked or unchecked exceptions.

### Method Overriding (Runtime Polymorphism)

Method overriding, means defining a method in a child class, that already exists in the parent class, with the same signature (the `same name, same arguments`).

By extending the parent class, the child class gets all the methods defined in the parent class (those methods are also known as derived methods).

`Method overriding` is also known as `Runtime Polymorphism`, or `Dynamic Method Dispatch`, because the method that is going to be called, is decided at runtime, by the Java virtual machine.

When we `override` a method, it's recommended to put `@Override`, immediately above the method definition.

The @Override statement is not required, but it's a way to get the compiler to flag an error, if you don't actually properly override this method.

We'll get an error, if we don't follow the overriding rules correctly.
We can't override static methods, `only instance methods` can be overridden.

**Method Overriding Rules**

A method will be considered overridden, if we follow these rules.

- It must have the same name and same arguments.
- The return type can be a subclass of the return type in the parent class.
- It can't have a lower access modifier. In other words, it can't have more restrictive access privileges.
- For example, if the parent's method is protected, then using private in the child's overridden method is not allowed. However, using public for the child's method would be allowed, in this example.

There's also some important points about method overriding to keep in mind.

- Only `inherited methods` can be overridden, in other words, methods can be overridden only in child classes.
- Constructors and private methods cannot be overridden.
  Methods that are final cannot be overridden.
- A subclass can use super.methodName() to call the superclass version of an overridden method. -->

### Method Overloading & Method Overriding

<p align="center">
<img src="https://github.com/tutungduong/oop_java_pInsights/blob/main/Images/overriding_vs_overloading.png">
</p>

<!-- | Method Overloading                                                       | Method Overriding                                                                |
| ------------------------------------------------------------------------ | -------------------------------------------------------------------------------- |
| Provides functionality to reuse a method name with different parameters. | Used to override a behavior which the class has inherited from the parent class. |
| Usually in a single class but may also be used in a child class.         | `Always in two classes` that have a child-parent or IS-A relationship.           |
| `Must have` different parameters                                         | `Must have` the same parameters and same name.                                   |
| May have different return types.                                         | `Must have` the same return type or covariant return type(child class).          |
| May have different access modifiers(private, protected, public).         | `Must NOT` have a lower modifier but may have a higher modifier                  |
| May throw different exceptions.                                          | `Must NOT` throw a new or broader checked exception.                             | -->

| Method Overloading                                                          | Method Overriding                                                                                   |
| --------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- |
| Overloading happens at compile time.                                        | Overriding happens at runtime.                                                                      |
| Gives better performance because the binding is being done at compile time. | Gives less performance because the binding is being done at run time.                               |
| Private and final methods can be overloaded.                                | Private and final methods can not be overridden.                                                    |
| Return type of method does not matter in case of method overloading.        | Return type of method must be the same in the case of overriding.                                   |
| Arguments must be different in the case of overloading.                     | Arguments must be the same in the case of overriding.                                               |
| It is being done in the same class.                                         | Base and derived classes are required here.                                                         |
| Mostly used to increase the readability of the code.                        | Mostly used to provide the implementation of the method that is already provided by its base class. |
