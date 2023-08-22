## Constructor

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

**Example for Constructor**

```java
public class Customer {

    private String name;
    private double creditLimit;
    private String email;

    public Customer() // Default Constructor {
        this("Nobody", "nobody@nowhere.com");
    }

    public Customer(String name, String email) // Parameterized Constructor
    {
        this(name, 1000, email);
    }

    public Customer(String name, double creditLimit, String email)  //Constructor Overloading
    {
        this.name = name;
        this.creditLimit = creditLimit;
        this.email = email;
    }
}

```

### STATIC AND INSTANCE METHOD

**Static Methods**

Static methods are declared using a static modifier. Static methods can't access instance methods and instant variables directly. They're usually used for operations that don't require any data from an instance of the class (from 'this'). If you remember, the this keyword is the current instance of a class.

So inside a static method, we can't use the this keyword. Whenever you see a method that doesn't use instance variables, that method should probably be declared as a static method. For example, main is a static method, and it's called by the Java virtual machine when it starts the Java application.

<details>
<summary><strong> Example for Static Methods</strong></summary>
<p align="center">
<img height="280" src="https://github.com/tutungduong/oop_java_pInsights/blob/main/Images/Static_methods.png">
</p>

</details>
<br>

**Instance Methods**

Instance methods belong to an instance, of a class. To use an instance method, we have to instantiate the class first, usually by using the new keyword.

Instance methods can access instance methods and instance variables directly.

Instance methods can also access static methods and static variables directly.

**Example for Instance Methods**

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

<br>

**When to use static or instance method in java**

<p align="center">
<img height="270" src="https://github.com/tutungduong/oop_java_pInsights/blob/main/Images/static_and_instance.png">
</p>

### Different POJO and The Record

**Plain Old Java Object**
A plain old Java object (whose acronym is POJO) is a class that generally only has instance fields.

It's used to house data, and pass data, between functional classes.

It usually has few, if any methods other than getters and setters. Many database frameworks use POJO's to read data from, or to write data to, databases, files or streams

<details>
<summary><strong> Example for POJO</strong></summary>

```java
public class PersonPOJO {
    private String name;
    private int age;

    public PersonPOJO(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }

    @Override
    public String toString() {
        return "PersonPOJO{" +
                "name='" + name + '\'' +
                ", age=" + age +
                '}';
    }

    public static void main(String[] args) {
        PersonPOJO person = new PersonPOJO("John", 30);
        System.out.println(person);
    }
}
```

</details>
<br>

**The Record**
The record is a special class that contains data, that's not meant to be altered.

In other words, it seeks to achieve immutability, for the data in its members.

It contains only the most fundamental methods, such as constructors and accessors.

Best of all, you the developer, don't have to write or generate any of this code.

<details>
<summary><strong> Example for The Record</strong></summary>

```java
public record PersonRecord(String name, int age) {
    public static void main(String[] args) {
        PersonRecord person = new PersonRecord("Jane", 25);
        System.out.println(person);
    }
}
```

</details>

## Inheritance

Inheritance is the mechanism by which an object acquires the some/all properties of another object.

The idea behind inheritance in Java is that you can create new classes that are built upon existing classes. When you inherit from an existing class, you can reuse methods and fields of the parent class. Moreover, you can add new methods and fields in your current class also.

In Oriented Object Programming, the computer programs are designed in such a way where everything is an object that interacts with one another object. It basically, helps in reusing the code and establish a relationship between different classes.

**Why use inheritance in java**

- For Method Overriding (so runtime polymorphism can be achieved).
- For Code Reusability.

## Type of Inheritance

<p align="center">
<img height="270" src="https://github.com/tutungduong/oop_java_pInsights/blob/main/Images/type_inheritance.png">
</p>

### Single Inheritance

In single inheritance, one class inherits the properties of another. It enables a derived class to inherit the properties and behavior from a single parent class. This will, in turn, enable code reusability as well as add new features to the existing code.

When a class inherits another class, it is known as a single inheritance. In the example given below, Dog class inherits the Animal class, so there is the single inheritance.

<p align="center">
<img src="https://github.com/tutungduong/oop_java_pInsights/blob/main/Images/single_Inheritance.png">
</p>

Here, Class A is your parent class and Class B is your child class which inherits the properties and behavior of the parent class

**Example for Single Inheritance**

```java
class Animal{
    void eat(){
        System.out.println("eating...");
    }
}

class Dog extends Animal{
    void bark(){
        System.out.println("barking...");
    }
}

class Main{
    public static void main(String args[]){
        Dog d=new Dog();
        d.bark();
        d.eat();
    }
}

// RESULT
barking...
eating..
```

### Multiple Inheritance

To reduce the complexity and simplify the language, multiple inheritance is not supported in java.

<p align="center">
<img src="https://github.com/tutungduong/oop_java_pInsights/blob/main/Images/multiple-inheritance.png">
</p>

**Example for Multiple Inheritance**

```java
class A{
    oid msg(){
        System.out.println("Hello");
    }
}
class B{
    void msg(){
        System.out.println("Welcome");
    }
}
class C extends A,B{

 public static void main(String args[]){
   C obj=new C();
   obj.msg();//Now which msg() method would be invoked?
}
}

// RESULT
compile time error
```

### Multilevel Inheritance

When a class is derived from a class which is also derived from another class, i.e. a class having more than one parent class but at different levels, such type of inheritance is called Multilevel Inheritance.

When there is a chain of inheritance, it is known as multilevel inheritance. As you can see in the example given below, BabyDog class inherits the Dog class which again inherits the Animal class, so there is a multilevel inheritance.

<p align="center">
<img src="https://github.com/tutungduong/oop_java_pInsights/blob/main/Images/multilevel-Inheritance.png">
</p>

If we talk about the flowchart, class B inherits the properties and behavior of class A and class C inherits the properties of class B. Here A is the parent class for B and class B is the parent class for C. So in this case class C implicitly inherits the properties and methods of class A along with Class B. That’s what is multilevel inheritance.

**Example for Multilevel Inheritance**

```java
class Animal{
    void eat(){
        System.out.println("eating...");
    }
}

class Dog extends Animal{
    void bark(){System.out.println("barking...");}
}

class BabyDog extends Dog{
    void weep(){System.out.println("weeping...");}
}

public class Main{
    public static void main(String args[]){
        BabyDog d=new BabyDog();
        d.weep();
        d.bark();
        d.eat();
    }
}

//RESULT
weeping...
barking...
eating...
```

### Hierarchical Inheritance

When a class has more than one child classes (subclasses) or in other words, more than one child classes have the same parent class

When two or more classes inherits a single class, it is known as hierarchical inheritance. In the example given below, Dog and Cat classes inherits the Animal class, so there is hierarchical inheritance.

<p align="center">
<img height="200" src="https://github.com/tutungduong/oop_java_pInsights/blob/main/Images/hierarchical_inheritance.png">
</p>

**Example for Hierarchical Inheritance**

```java
class Animal{
    void eat(){
        System.out.println("eating...");
    }
}
class Dog extends Animal{
    void bark(){
        System.out.println("barking...");
    }
}
class Cat extends Animal{
    void meow(){
        System.out.println("meowing...");
    }
}
public class Main{
    public static void main(String args[]){
    Cat c=new Cat();
    c.meow();
    c.eat();
    //c.bark();//Compile Time Error
    }
}

//RESULT
meowing...
eating...
```

### Hybrid Inheritance

Hybrid inheritance is a combination of two or more types of inheritance.

<p align="center">
<img src="https://github.com/tutungduong/oop_java_pInsights/blob/main/Images/hybrid_inheritance.png">
</p>

**Example for Hybrid Inheritance**

```Java
//parent class
class GrandFather
{
    public void showG()
    {
        System.out.println("He is grandfather.");
    }
}
//inherits GrandFather properties
class Father extends GrandFather
{
    public void showF()
    {
        System.out.println("He is father.");
    }
}
//inherits Father properties
class Son extends Father
{
    public void showS()
    {
        System.out.println("He is son.");
    }
}
//inherits Father properties
public class Daughter extends Father
{
    public void showD()
    {
        System.out.println("She is daughter.");
    }
    public static void main(String args[])
    {
//Daughter obj = new Daughter();
//obj.show();
        Son obj = new Son();
        obj.showS();  // Accessing Son class method
        obj.showF();  // Accessing Father class method
        obj.showG();  // Accessing GrandFather class method
        Daughter obj2 = new Daughter();
        obj2.showD();  // Accessing Daughter class method
        obj2.showF();    // Accessing Father class method
        obj2.showG();   // Accessing GrandFather class method
    }
}

// RESULT

    He is son.
    He is father.
    He is grandfather.
    She is daughter.
    He is father.
    He is grandfather.
```

<!-- ## Aggregation

If a class have an entity reference, it is known as Aggregation

<p align="center">
<img height="400" src="../Images/inheritance-challenge.png">
</p>

Create a main method that will create either a SalariedEmployee or HourlyEmployee, and call the methods, getAge, collectPay, and the method shown for the specific type of class you decide to implement.

**Example for Aggregation**

```java
public class Worker {

    private String name;
    private String birthDate;
    protected String endDate;

    public Worker() {

    }

    public Worker(String name, String birthDate) {
        this.name = name;
        this.birthDate = birthDate;
    }

    public int getAge() {

        int currentYear = 2025;
        int birthYear = Integer.parseInt(birthDate.substring(6));

        return (currentYear - birthYear);
    }

    public double collectPay() {
        return 0.0;
    }

    public void terminate(String endDate) {
        this.endDate = endDate;
    }

    @Override
    public String toString() {
        return "Worker{" +
                "name='" + name + '\'' +
                ", birthDate='" + birthDate + '\'' +
                ", endDate='" + endDate + '\'' +
                '}';
    }
}

```

```java
public class Employee extends Worker {

    private long employeeId;
    private String hireDate;

    private static int employeeNo = 1;

    public Employee(String name, String birthDate, String hireDate) {
        super(name, birthDate);
        this.employeeId = Employee.employeeNo++;
        this.hireDate = hireDate;
    }

    @Override
    public String toString() {
        return "Employee{" +
                "employeeId=" + employeeId +
                ", hireDate='" + hireDate + '\'' +
                "} " + super.toString();
    }
}

```

```java
public class SalariedEmployee extends Employee {

    double annualSalary;
    boolean isRetired;

    public SalariedEmployee(String name, String birthDate, String hireDate,
                            double annualSalary) {
        super(name, birthDate, hireDate);
        this.annualSalary = annualSalary;
    }

    @Override
    public double collectPay() {

        double paycheck = annualSalary / 26;
        double adjustedPay = (isRetired) ? 0.9 * paycheck : paycheck;

        return (int) adjustedPay;
    }

    public void retire() {

        terminate("12/12/2025");
        isRetired = true;
    }
}

```

```java
public class HourlyEmployee extends Employee {

    private double hourlyPayRate;

    public HourlyEmployee(String name, String birthDate, String hireDate,
                          double hourlyPayRate) {
        super(name, birthDate, hireDate);
        this.hourlyPayRate = hourlyPayRate;
    }

    @Override
    public double collectPay() {
        return 40 * hourlyPayRate;
    }

    public double getDoublePay() {
        return 2 * collectPay();
    }
}

```

```java
public class Main {

    public static void main(String[] args) {

        Employee tim = new Employee("Tim", "11/11/1985",
                "01/01/2020");
        System.out.println(tim);
        System.out.println("Age = " + tim.getAge());
        System.out.println("Pay = " + tim.collectPay());

        SalariedEmployee joe = new SalariedEmployee("Joe", "11/11/1990",
                "03/03/2020", 35000);
        System.out.println(joe);
        System.out.println("Joe's Paycheck = $" + joe.collectPay());

        joe.retire();
        System.out.println("Joe's Pension check = $" + joe.collectPay());

        HourlyEmployee mary = new HourlyEmployee("Mary", "05/05/1970",
                "03/03/2021", 15);
        System.out.println(mary);
        System.out.println("Mary's Paycheck = $" + mary.collectPay());
        System.out.println("Mary's Holiday Pay = $" + mary.getDoublePay());
    }
}

``` -->
