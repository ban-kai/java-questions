# Java Interview Questions Compilation

1. [Explain JVM, JRE and JDK? ](#1-explain-jvm-jre-and-jdk)
2. [Is Java a Compiled or an Interpreted programming language ?](#2-is-java-a-compiled-or-an-interpreted-programming-language-)
3. [Why java is not 100% Object-oriented?](#3-why-java-is-not-100-object-oriented)
4. [What are wrapper classes?](#4-what-are-wrapper-classes)
5. [What is singleton class and how can we make a class singleton?](#5-what-is-singleton-class-and-how-can-we-make-a-class-singleton)
6. [What is the difference between Array list and vector?](#6-what-is-the-difference-between-array-list-and-vector)
7. [What is the difference between equals() and == ?](#7--what-is-the-difference-between-equals-and--)
8. [What are the differences between Heap and Stack Memory?](#8-what-are-the-differences-between-heap-and-stack-memory)
9. [What is Polymorphism?](#9-what-is-polymorphism)
10. [What are the OOP Concepts in Java?](#10-what-are-the-oop-concepts-in-java)
11. [What is the difference between abstract classes and interfaces?](#11-what-is-the-difference-between-abstract-classes-and-interfaces)
12. [What is method overloading and method overriding?](#12-what-is-method-overloading-and-method-overriding)
13. [Can you override a private or static method in Java?](#13-can-you-override-a-private-or-static-method-in-java)
14. [What is multiple inheritance? Is it supported by Java?](#14-what-is-multiple-inheritance-is-it-supported-by-java)
15. [What is association?](#15-what-is-association)
16. [Is Java platform independent?](#16-is-java-platform-independent)
17. [What are the various access specifiers for Java classes?]()


## 0. Up
## 1. Explain JVM, JRE and JDK? 

__JVM (Java Virtual Machine)__: It is an abstract machine. It is a specification that provides run-time environment in which java bytecode can be executed. It follows three notations:

* Specification: It is a document that describes the implementation of the Java virtual machine. It is provided by Sun and other companies.
* Implementation: It is a program that meets the requirements of JVM specification.
* Runtime Instance: An instance of JVM is created whenever you write a java command on the command prompt and run the class.

__JRE (Java Runtime Environment)__ : JRE refers to a runtime environment in which java bytecode can be executed. It implements the JVM (Java Virtual Machine) and provides all the class libraries and other support files that JVM uses at runtime. So JRE is a software package that contains what is required to run a Java program. Basically, it’s an implementation of the JVM which physically exists. 

__JDK(Java Development Kit)__ : It is the tool necessary to compile, document and package Java programs. The JDK completely includes JRE which contains tools for Java programmers. The Java Development Kit is provided free of charge. Along with JRE, it includes an interpreter/loader, a compiler (javac), an archiver (jar), a documentation generator (javadoc) and other tools needed in Java development. In short, it contains JRE + development tools.

Refer to this below image and understand how exactly these components reside: ![java](https://cdn-images-1.medium.com/max/1600/0*MsGzRuN1Q09dOkwi.png)

## 2. Is Java a Compiled or an Interpreted programming language ?


Java implementations typically use a two-step compilation process. Java source code is compiled down to bytecode by the Java compiler. The bytecode is executed by a Java Virtual Machine (JVM). Modern JVMs use a technique called Just-in-Time (JIT) compilation to compile the bytecode to native instructions understood by hardware CPU on the fly at runtime.

Some implementations of JVM may choose to interpret the bytecode instead of JIT compiling it to machine code, and running it directly. While this is still considered an "interpreter," It's quite different from interpreters that read and execute the high level source code (i.e. in this case, Java source code is not interpreted directly, the bytecode, output of Java compiler, is.)

It is technically possible to compile Java down to native code ahead-of-time and run the resulting binary. It is also possible to interpret the Java code directly.

At run time, JVM interprets the byte code and executes them. However, a full interpreter based execution potentially hurts the performance of application since pretty much everything that a compiler could have done upfront at compile time will now be done repeatedly by the interpreter and this adds to the overall execution time of the program.

To summarize, depending on the execution environment, bytecode can be:

* compiled ahead of time and executed as native code (similar to most C++ compilers)
* compiled just-in-time and executed
* interpreted
* directly executed by a supported processor (bytecode is the native instruction set of some CPUs)

![java](http://novtopro.qiniudn.com/blog/2017/01/21/kotlin-kickstart/jit.png)

## 3. Why java is not 100% Object-oriented?

Java is not 100% Object-oriented because it makes use of eight primitive datatypes such as boolean, byte, char, int, float, double, long, short which are not objects.

## 4. What are wrapper classes?

Wrapper classes converts the java primitives into the reference types (objects). Every primitive data type has a class dedicated to it. These are known as wrapper classes because they “wrap” the primitive data type into an object of that class. Refer to the below image which displays different primitive type, wrapper class and constructor argument. 

## 5. What is singleton class and how can we make a class singleton?

Singleton class is a class whose only one instance can be created at any given time, in one JVM. A class can be made singleton by making its constructor private.

```java
// Java program implementing Singleton class
// with getInstance() method
class Singleton
{
    // static variable single_instance of type Singleton
    private static Singleton single_instance = null;
 
    // variable of type String
    public String s;
 
    // private constructor restricted to this class itself
    private Singleton()
    {
        s = "Hello I am a string part of Singleton class";
    }
 
    // static method to create instance of Singleton class
    public static Singleton getInstance()
    {
        if (single_instance == null)
            single_instance = new Singleton();
 
        return single_instance;
    }
}
```
The best example of singleton usage scenario is when there is a limit of having only one connection to a database due to some driver limitations or because of any licensing issues.

## 6. What is the difference between Array list and vector?

|Array List	| Vector |
| ---------- | -------|
|Array List is not synchronized. | Vector is synchronized. |
|Array List is fast as it’s non-synchronized. | Vector is slow as it is thread safe. |
|If an element is inserted into the Array List, it increases its Array size by 50%.	|Vector defaults to doubling size of its array. |
|Array List does not define the increment size.	| Vector defines the increment size. |
|Array List can only use Iterator for traversing an Array List.	| Except Hashtable, Vector is the only other class which uses both Enumeration and Iterator. |

## 7.  What is the difference between equals() and == ?

Equals() method is defined in Object class in Java and used for checking equality of two objects defined by business logic.
“==” or equality operator in Java is a binary operator provided by Java programming language and used to compare primitives and objects. public boolean equals(Object o) is the method provided by the Object class. The default implementation uses == operator to compare two objects. For example: method can be overridden like String class. equals() method is used to compare the values of two objects.

* .equals(...) will only compare what it is written to compare, no more, no less.
* If a class does not override the equals method, then it defaults to the equals(Object o) method of the closest parent class that has overridden this method.
* If no parent classes have provided an override, then it defaults to the method from the ultimate parent class, Object, and so you're left with the Object#equals(Object o) method. Per the Object API this is the same as ==; that is, it returns true if and only if both variables refer to the same object, if their references are one and the same. Thus you will be testing for object equality and not functional equality.
* Always remember to override hashCode if you override equals so as not to "break the contract". As per the API, the result returned from the hashCode() method for two objects must be the same if their equals methods show that they are equivalent. The converse is not necessarily true.

## 8. What are the differences between Heap and Stack Memory?
The major difference between Heap and Stack memory are:

|Features	| Stack |	Heap |
|-----------| -------| ------|
|Memory	| Stack memory is used only by one thread of execution.	| Heap memory is used by all the parts of the application.|
| Access |	Stack memory can’t be accessed by other threads. |	Objects stored in the heap are globally accessible. |
| Memory Management	| Follows LIFO manner to free memory. |	Memory management is based on generation associated to each object. |
| Lifetime	| Exists until the end of execution of the thread.	| Heap memory lives from the start till the end of application execution. |
| Usage |	Stack memory only contains local primitive and reference variables to objects in heap space. |	Whenever an object is created, it’s always stored in the Heap space. |

## 9. What is Polymorphism?

If you think about the Greek roots of the term, it should become obvious.

* Poly = many: polygon = many-sided, polystyrene = many styrenes (a), polyglot = many languages, and so on.
* Morph = change or form: morphology = study of biological form, Morpheus = the Greek god of dreams able to take any form.
So polymorphism is the ability (in programming) to present the same interface for differing underlying forms (data types).

For example, in many languages, integers and floats are implicitly polymorphic since you can add, subtract, multiply and so on, irrespective of the fact that the types are different. They're rarely considered as objects in the usual term.

But, in that same way, a class like BigDecimal or Rational or Imaginary can also provide those operations, even though they operate on different data types.

The classic example is the Shape class and all the classes that can inherit from it (square, circle, dodecahedron, irregular polygon, splat and so on).

With polymorphism, each of these classes will have different underlying data. A point shape needs only two co-ordinates (assuming it's in a two-dimensional space of course). A circle needs a center and radius. A square or rectangle needs two co-ordinates for the top left and bottom right corners and (possibly) a rotation. An irregular polygon needs a series of lines.

By making the class responsible for its code as well as its data, you can achieve polymorphism. In this example, every class would have its own Draw() function and the client code could simply do:

shape.Draw()
to get the correct behavior for any shape.

This is in contrast to the old way of doing things in which the code was separate from the data, and you would have had functions such as drawSquare() and drawCircle().

__Another definition__

The word polymorphism is used in various contexts and describes situations in which something occurs in several different forms. In computer science, it describes the concept that objects of different types can be accessed through the same interface. Each type can provide its own, independent implementation of this interface. It is one of the core concepts of object-oriented programming (OOP).

If you’re wondering if an object is polymorphic, you can perform a simple test. If the object successfully passes multiple is-a or instanceof tests, it’s polymorphic. As I’ve described in my post about inheritance, all Java classes extend the class Object. Due to this, all objects in Java are polymorphic because they pass at least two instanceof checks.

Different Types of Polymorphism
Java supports 2 types of polymorphism:

* static or compile-time
* dynamic

### Static Polymorphism
Java, like many other object-oriented programming languages, allows you to implement multiple methods within the same class that use the same name but a different set of parameters. That is called method overloading and represents a static form of polymorphism.

The parameter sets have to differ in at least one of the following three criteria:

* They need to have a different number of parameters, e.g. one method accepts 2 and another one 3 parameters.
* The types of the parameters need to be different, e.g. one method accepts a String and another one a Long.
* They need to expect the parameters in a different order, e.g. one method accepts a String and a Long and another one accepts a Long and a String. This kind of overloading is not recommended because it makes the API difficult to understand.

In most cases, each of these overloaded methods provides a different but very similar functionality.

Due to the different sets of parameters, each method has a different signature. That allows the compiler to identify which method has to be called and to bind it to the method call. This approach is called static binding or static polymorphism.

Let’s take a look at an example.

__A Simple Example for Static Polymorphism__

I use the same CoffeeMachine project as I used in the previous posts of this series. You can clone it at https://github.com/thjanssen/Stackify-OopInheritance.

The BasicCoffeeMachine class implements two methods with the name brewCoffee. The first one accepts one parameter of type CoffeeSelection. The other method accepts two parameters, a CoffeeSelection, and an int.

```
public class BasicCoffeeMachine {
    // ...
    public Coffee brewCoffee(CoffeeSelection selection) throws CoffeeException {
        switch (selection) {
        case FILTER_COFFEE:
            return brewFilterCoffee();
        default:
            throw new CoffeeException(
                "CoffeeSelection ["+selection+"] not supported!");
        }   
    }
    public List brewCoffee(CoffeeSelection selection, int number) throws CoffeeException {
        List coffees = new ArrayList(number);
        for (int i=0; i<number; i++) {
            coffees.add(brewCoffee(selection));
        }
        return coffees;
    }
    // ...
}
```

Now when you call one of these methods, the provided set of parameters identifies the method which has to be called.

In the following code snippet, I call the method only with a CoffeeSelection object. At compile time, the Java compiler binds this method call to the brewCoffee(CoffeeSelection selection) method.

```
BasicCoffeeMachine coffeeMachine = createCoffeeMachine();
coffeeMachine.brewCoffee(CoffeeSelection.FILTER_COFFEE);
```

If I change this code and call the brewCoffee method with a CoffeeSelection object and an int, the compiler binds the method call to the other brewCoffee(CoffeeSelection selection, int number) method.

```
BasicCoffeeMachine coffeeMachine = createCoffeeMachine();
List coffees = coffeeMachine.brewCoffee(CoffeeSelection.ESPRESSO, 2);
```
### Dynamic Polymorphism

This form of polymorphism doesn’t allow the compiler to determine the executed method. The JVM needs to do that at runtime.

Within an inheritance hierarchy, a subclass can override a method of its superclass. That enables the developer of the subclass to customize or completely replace the behavior of that method.

It also creates a form of polymorphism. Both methods, implemented by the super- and subclass, share the same name and parameters but provide different functionality.

Let’s take a look at another example from the CoffeeMachine project.

__Method Overriding in an Inheritance Hierarchy__
The BasicCoffeeMachine class is the superclass of the PremiumCoffeeMachine class.

![java](https://stackify.com/wp-content/uploads/2017/12/word-image-13.png)

Both classes provide an implementation of the brewCoffee(CoffeeSelection selection) method.

```
import java.util.ArrayList;
import java.util.List;
import java.util.Map;
public class BasicCoffeeMachine extends AbstractCoffeeMachine {
    protected Map beans;
    protected Grinder grinder;
    protected BrewingUnit brewingUnit;
    public BasicCoffeeMachine(Map beans) {
        super();
        this.beans = beans;
        this.grinder = new Grinder();
        this.brewingUnit = new BrewingUnit();
        this.configMap.put(CoffeeSelection.FILTER_COFFEE, new Configuration(30, 480));
    }
    public List brewCoffee(CoffeeSelection selection, int number) throws CoffeeException {
        List coffees = new ArrayList(number);
        for (int i=0; i<number; i++) {
            coffees.add(brewCoffee(selection));
        }
        return coffees;
    }
    public Coffee brewCoffee(CoffeeSelection selection) throws CoffeeException {
        switch (selection) {
        case FILTER_COFFEE:
            return brewFilterCoffee();
        default:
            throw new CoffeeException("CoffeeSelection ["+selection+"] not supported!");
        }
    }
    private Coffee brewFilterCoffee() {
        Configuration config = configMap.get(CoffeeSelection.FILTER_COFFEE);
        // grind the coffee beans
        GroundCoffee groundCoffee = this.grinder.grind(this.beans.get(CoffeeSelection.FILTER_COFFEE), config.getQuantityCoffee());
        // brew a filter coffee
        return this.brewingUnit.brew(CoffeeSelection.FILTER_COFFEE, groundCoffee, config.getQuantityWater());
    }
    public void addBeans(CoffeeSelection selection, CoffeeBean newBeans) throws CoffeeException {
        CoffeeBean existingBeans = this.beans.get(selection);
        if (existingBeans != null) {
            if (existingBeans.getName().equals(newBeans.getName())) {
                existingBeans.setQuantity(existingBeans.getQuantity() + newBeans.getQuantity());
            } else {
                throw new CoffeeException("Only one kind of beans supported for each CoffeeSelection.");
            }
        } else {
            this.beans.put(selection, newBeans);
        }
    }
}
```

```
import java.util.Map;
public class PremiumCoffeeMachine extends BasicCoffeeMachine {
    public PremiumCoffeeMachine(Map beans) {
        // call constructor in superclass
        super(beans);
        // add configuration to brew espresso
        this.configMap.put(CoffeeSelection.ESPRESSO, new Configuration(8, 28));
    }
    private Coffee brewEspresso() {
        Configuration config = configMap.get(CoffeeSelection.ESPRESSO);
        // grind the coffee beans
        GroundCoffee groundCoffee = this.grinder.grind(this.beans.get(CoffeeSelection.ESPRESSO), config.getQuantityCoffee());
        // brew an espresso
        return this.brewingUnit.brew(
            CoffeeSelection.ESPRESSO, groundCoffee, config.getQuantityWater());
    }
    public Coffee brewCoffee(CoffeeSelection selection) throws CoffeeException {
        if (selection == CoffeeSelection.ESPRESSO)
            return brewEspresso();
        else
            return super.brewCoffee(selection);
    }
}
```

If you read the post about the OOP concept inheritance, you already know the two implementations of the brewCoffee method. The BasicCoffeeMachine only supports the CoffeeSelection.FILTER_COFFEE. The brewCoffee method of the PremiumCoffeeMachine class adds support for CoffeeSelection.ESPRESSO. If it gets called with any other CoffeeSelection, it uses the keyword super to delegate the call to the superclass.

__Late Binding__

When you want to use such an inheritance hierarchy in your project, you need to be able to answer the following question: which method will the JVM call?

That can only be answered at runtime because it depends on the object on which the method gets called. The type of the reference, which you can see in your code, is irrelevant. You need to distinguish three general scenarios:

* Your object is of the type of the superclass and gets referenced as the superclass. So, in the example of this post, a BasicCoffeeMachine object gets referenced as a BasicCoffeeMachine.
* Your object is of the type of the subclass and gets referenced as the subclass. In the example of this post, a PremiumCoffeeMachine object gets referenced as a PremiumCoffeeMachine.
* Your object is of the type of the subclass and gets referenced as the superclass. In the CoffeeMachine example, a PremiumCoffeeMachine object gets referenced as a BasicCoffeeMachine.


__Superclass Referenced as the Superclass__

The first scenario is pretty simple. When you instantiate a BasicCoffeeMachine object and store it in a variable of type BasicCoffeeMachine, the JVM will call the brewCoffee method on the BasicCoffeeMachine class. So, you can only brew a CoffeeSelection.FILTER_COFFEE.

```
// create a Map of available coffee beans
Map beans = new HashMap();
beans.put(CoffeeSelection.FILTER_COFFEE,
new CoffeeBean("My favorite filter coffee bean", 1000));
// instantiate a new CoffeeMachine object
BasicCoffeeMachine coffeeMachine = new BasicCoffeeMachine(beans);
Coffee coffee = coffeeMachine.brewCoffee(CoffeeSelection.FILTER_COFFEE);
```

__Subclass Referenced as the Subclass__

The second scenario is similar. But this time, I instantiate a PremiumCoffeeMachine and reference it as a PremiumCoffeeMachine. In this case, the JVM calls the brewCoffee method of the PremiumCoffeeMachineclass, which adds support for CoffeeSelection.ESPRESSO.

```
// create a Map of available coffee beans
Map beans = new HashMap();
beans.put(CoffeeSelection.FILTER_COFFEE,
new CoffeeBean("My favorite filter coffee bean", 1000));
beans.put(CoffeeSelection.ESPRESSO,
new CoffeeBean("My favorite espresso bean", 1000));
// instantiate a new CoffeeMachine object
PremiumCoffeeMachine coffeeMachine = new PremiumCoffeeMachine(beans);
Coffee coffee = coffeeMachine.brewCoffee(CoffeeSelection.ESPRESSO);
```

__Subclass Referenced as the Superclass__

This is the most interesting scenario and the main reason why I explain dynamic polymorphism in such details.

When you instantiate a PremiumCoffeeMachine object and assign it to the BasicCoffeeMachine coffeeMachine variable, it still is a PremiumCoffeeMachine object. It just looks like a BasicCoffeeMachine.

The compiler doesn’t see that in the code, and you can only use the methods provided by the BasicCoffeeMachine class. But if you call the brewCoffee method on the coffeeMachine variable, the JVM knows that it is an object of type PremiumCoffeeMachine and executes the overridden method. This is called late binding.

```
// create a Map of available coffee beans
Map beans = new HashMap();
beans.put(CoffeeSelection.FILTER_COFFEE,
new CoffeeBean("My favorite filter coffee bean", 1000));
// instantiate a new CoffeeMachine object
BasicCoffeeMachine coffeeMachine = new PremiumCoffeeMachine(beans);
Coffee coffee = coffeeMachine.brewCoffee(CoffeeSelection.ESPRESSO);
```

__Summary__

Polymorphism is one of the core concepts in OOP languages. It describes the concept that different classes can be used with the same interface. Each of these classes can provide its own implementation of the interface.

Java supports two kinds of polymorphism. You can overload a method with different sets of parameters. This is called static polymorphism because the compiler statically binds the method call to a specific method.

Within an inheritance hierarchy, a subclass can override a method of its superclass. If you instantiate the subclass, the JVM will always call the overridden method, even if you cast the subclass to its superclass. That is called dynamic polymorphism.
```
class Person {
    void walk() {
        System.out.println("Can Run….");
    }
}
class Employee extends Person {
    void walk() {
        System.out.println("Running Fast…");
    }
}

Person p = new Employee(); //upcasting
p.walk(); // Running Fast…
```

## 10. What are the OOP Concepts in Java?

There are four main OOP concepts in Java. These are:

* __Abstraction.__ Abstraction means using simple things to represent complexity. We all know how to turn the TV on, but we don’t need to know how it works in order to enjoy it. In Java, abstraction means simple things like objects, classes, and variables represent more complex underlying code and data. This is important because it lets avoid repeating the same work multiple times.
* __Encapsulation.__ This is the practice of keeping fields within a class private, then providing access to them via public methods. It’s a protective barrier that keeps the data and code safe within the class itself. This way, we can re-use objects like code components or variables without allowing open access to the data system-wide.
* __Inheritance.__ This is a special feature of Object Oriented Programming in Java. It lets programmers create new classes that share some of the attributes of existing classes. This lets us build on previous work without reinventing the wheel.
* __Polymorphism.__ This Java OOP concept lets programmers use the same word to mean different things in different contexts. One form of polymorphism in Java is method overloading. That’s when different meanings are implied by the code itself. The other form is method overriding. That’s when the different meanings are implied by the values of the supplied variables. 

__How Abstraction Works__
Abstraction as an OOP concept in Java works by letting programmers create useful, reusable tools. For example, a programmer can create several different types of objects. These can be variables, functions, or data structures. Programmers can also create different classes of objects. These are ways to define the objects.

For instance, a class of variable might be an address. The class might specify that each address object shall have a name, street, city, and zip code. The objects, in this case, might be employee addresses, customer addresses, or supplier addresses.

__How Encapsulation Works__
Encapsulation lets us re-use functionality without jeopardizing security. It’s a powerful OOP concept in Java because it helps us save a lot of time. For example, we may create a piece of code that calls specific data from a database. It may be useful to reuse that code with other databases or processes. Encapsulation lets us do that while keeping our original data private. It also lets us alter our original code without breaking it for others who have adopted it in the meantime.

__How Inheritance Works__
Inheritance is another labor-saving Java OOP concept. It works by letting a new class adopt the properties of another. We call the inheriting class a subclass or a child class. The original class is often called the parent. We use the keyword extends to define a new class that inherits properties from an old class.

__How Polymorphism Works__
Polymorphism in Java works by using a reference to a parent class to affect an object in the child class. We might create a class called “horse” by extending the “animal” class. That class might also implement the “professional racing” class. The “horse” class is “polymorphic,” since it inherits attributes of both the “animal” and “professional racing” class.

Two more examples of polymorphism in Java are method overriding and method overloading.

In __method overriding__, the child class can use the OOP polymorphism concept to override a method of its parent class. That allows a programmer to use one method in different ways depending on whether it’s invoked by an object of the parent class or an object of the child class.

In __method overloading__, a single method may perform different functions depending on the context in which it’s called. That is, a single method name might work in different ways depending on what arguments are passed to it.

## 11. What is the difference between abstract classes and interfaces?

|Abstract Class	|Interfaces|
|---------------|----------|
|An abstract class can provide complete, default code and/or just the details that have to be overridden.| An interface cannot provide any code at all,just the signature.|
|In case of abstract class, a class may extend only one abstract class.	| A Class may implement several interfaces. |
| An abstract class can have non-abstract methods.	| All methods of an Interface are abstract. |
| An abstract class can have instance variables. | An Interface cannot have instance variables |
| An abstract class can have any visibility: public, private, protected. |	An Interface visibility must be public (or) none.|
|If we add a new method to an abstract class then we have the option of providing default implementation and therefore all the existing code might work properly |	If we add a new method to an Interface then we have to track down all the implementations of the interface and define implementation for the new method (this is before Java 8) |
|An abstract class can contain constructors	| An Interface cannot contain constructors |
| Abstract classes are fast	| Interfaces are slow as it requires extra indirection to find corresponding method in the actual class |

## 12. What is method overloading and method overriding?

__Method Overloading :__
* In Method Overloading, Methods of the same class shares the same name but each method must have different number of parameters or parameters having different types and order.
* Method Overloading is to “add” or “extend” more to method’s behavior.
* It is a compile time polymorphism.
* The methods must have different signature.
* It may or may not need inheritance in Method Overloading.

Let’s take a look at the example below to understand it better.

```java
class Adder {
Static int add(int a, int b)
{
return a+b;
}
Static double add( double a, double b)
{
return a+b;
}
public static void main(String args[])
{
System.out.println(Adder.add(11,11));
System.out.println(Adder.add(12.3,12.6));
}}
```

__Method Overriding :__
* In Method Overriding, sub class have the same method with same name and exactly the same number and type of parameters and same return type as a super class.
* Method Overriding is to “Change” existing behavior of method.
* It is a run time polymorphism.
* The methods must have same signature.
* It always requires inheritance in Method Overriding.

Let’s take a look at the example below to understand it better.

```java
class Car {
void run(){
System.out.println(“car is running”); 
}
Class Audi extends Car{
void run()
{
System.out.prinltn(“Audi is running safely with 100km”);
}
public static void main( String args[])
{
Car b=new Audi();
b.run();
}
}
```
## 13. Can you override a private or static method in Java?

You cannot override a private or static method in Java. If you create a similar method with same return type and same method arguments in child class then it will hide the super class method; this is known as method hiding. Similarly, you cannot override a private method in sub class because it’s not accessible there. What you can do is create another private method with the same name in the child class. Let’s take a look at the example below to understand it better.

## 14. What is multiple inheritance? Is it supported by Java?

If a child class inherits the property from multiple classes is known as multiple inheritance. Java does not allow to extend multiple classes.

The problem with multiple inheritance is that if multiple parent classes have a same method name, then at runtime it becomes difficult for the compiler to decide which method to execute from the child class.

Therefore, Java doesn’t support multiple inheritance. The problem is commonly referred as Diamond Problem.

![java](https://d1jnx9ba8s6j9r.cloudfront.net/blog/wp-content/uploads/2017/04/MultipleInheritance-Java-240x300.png)

## 15. What is association?

Association is a relationship where all object have their own lifecycle and there is no owner. Let’s take an example of Teacher and Student. Multiple students can associate with a single teacher and a single student can associate with multiple teachers but there is no ownership between the objects and both have their own lifecycle. These relationship can be one to one, One to many, many to one and many to many.

## 16. Is Java platform independent?

Yes. Java is a platform independent language. We can write java code on one platform and run it on another platform. For e.g. we can write and compile the code on windows and can run it on Linux or any other supported platform. This is one of the main features of java.

## 17. What are the various access specifiers for Java classes?

The types of access specifiers for classes are:

* Public: Class,Method,Field is accessible from anywhere.
* Protected: Method,Field can be accessed from the same class to which they belong or from the sub-classes,and from the class of same package,but not from outside.
* Default: Method,Field,class can be accessed only from the same package and not from outside of it’s native package.
* Private: Method,Field can be accessed from the same class to which they belong.

## 18. What all memory areas are allocated by JVM?

Heap, Stack, Program Counter Register and Native Method Stack.

## 19. What’s the purpose of Static methods and static variables?

When there is a requirement to share a method or a variable between multiple objects of a class instead of creating separate copies for each object, we use static keyword to make a method or variable shared for all objects. A static method or variable is shared across all object instances of that class.

## 20. What is class?

Class is nothing but a template that describes the data and behavior associated with instances of that class. Another definition is that a class represents a blueprint.

## 21. What is data encapsulation and what’s its significance?

Encapsulation is a concept in Object Oriented Programming for combining properties and methods in a single unit.

Encapsulation helps programmers to follow a modular approach for software development as each object has its own set of methods and variables and serves its functions independent of other objects. Encapsulation also serves data hiding purpose.

## 22. Different Data types in Java and their size

byte — 8 bit (are esp. useful when working with a stream of data from a network or a file).
short — 16 bit
char — 16 bit Unicode
int — 32 bit (whole number)
float — 32 bit (real number)
long — 64 bit (Single precision)
double — 64 bit (double precision)
boolean - virtual machine dependent.

## 23. What is Unicode?

Java uses Unicode to represent the characters. Unicode defines a fully international character set that can represent all of the characters found in human languages.

## 24. What are Literals?

A literal is a value that may be assigned to a primitive or string variable or passed as an argument to a method.

## 25. What is Type casting in Java?

To create a conversion between two incompatible types, we must use a cast. There are two types of casting in java: automatic casting (done automatically) and explicit casting (done by programmer).

Java object typecasting one object reference can be type cast into another object reference. The cast can be to its own class type or to one of its subclass or superclass types or interfaces. There are compile-time rules and runtime rules for casting in java.

Typecast Objects with a dynamically loaded Class ? – The casting of object references depends on the relationship of the classes involved in the same hierarchy. Any object reference can be assigned to a reference variable of the type Object, because the Object class is a superclass of every Java class.
There can be 2 casting java scenarios

* Upcasting
* Downcasting

When we cast a reference along the class hierarchy in a direction from the root class towards the children or subclasses, it is a downcast. When we cast a reference along the class hierarchy in a direction from the sub classes towards the root, it is an upcast. We need not use a cast operator in this case.

The compile-time rules are there to catch attempted casts in cases that are simply not possible. This happens when we try to attempt casts on objects that are totally unrelated (that is not subclass super class relationship or a class-interface relationship) At runtime a ClassCastException is thrown if the object being cast is not compatible with the new type it is being cast to.

Below is an example showing when a ClassCastException can occur during object casting

```java
//X is a supper class of Y and Z which are sibblings.

public class X {}
public class Y extends X {}
public class Z extends X {}
public class RunTimeCastDemo {

	public static void main(String args[]) {
		X x = new X();
		Y y = new Y();
		Z z = new Z();
		X xy = new Y(); // compiles ok (up the hierarchy)
		X xz = new Z(); // compiles ok (up the hierarchy)
		//		Y yz = new Z();   incompatible type (siblings)
		//		Y y1 = new X();   X is not a Y
		//		Z z1 = new X();   X is not a Z
		X x1 = y; // compiles ok (y is subclass of X)
		X x2 = z; // compiles ok (z is subclass of X)
		Y y1 = (Y) x; // compiles ok but produces runtime error
		Z z1 = (Z) x; // compiles ok but produces runtime error
		Y y2 = (Y) x1; // compiles and runs ok (x1 is type Y)
		Z z2 = (Z) x2; // compiles and runs ok (x2 is type Z)
		//		Y y3 = (Y) z;     inconvertible types (siblings)
		//		Z z3 = (Z) y;     inconvertible types (siblings)
		Object o = z;
		Object o1 = (Y) o; // compiles ok but produces runtime error
	}
}
```

__CASTING OBJECT REFERENCES: IMPLICIT CASTING USING A COMPILER__

In general an implicit cast is done when an Object reference is assigned (cast) to:

* A reference variable whose type is the same as the class from which the object was instantiated.
An Object as Object is a super class of every Class.
* A reference variable whose type is a super class of the class from which the object was instantiated.
* A reference variable whose type is an interface that is implemented by the class from which the object was instantiated.
* A reference variable whose type is an interface that is implemented by a super class of the class from which the object was instantiated.

Consider an interface Vehicle, a super class Car and its subclass Ford. The following example shows the automatic conversion of object references handled by the compiler

```java
interface Vehicle {}
class Car implements Vehicle {}
class Ford extends Car {}
```

Let c be a variable of type Car class and f be of class Ford and v be an vehicle interface reference. We can assign the Ford reference to the Car variable:
I.e. we can do the following

Example 1
`c = f; //Ok Compiles fine`

Where c = new Car();
And, f = new Ford();
The compiler automatically handles the conversion (assignment) since the types are compatible (sub class – super class relationship), i.e., the type Car can hold the type Ford since a Ford is a Car.

Example 2
`v = c; //Ok Compiles fine`
`c = v; // illegal conversion from interface type to class type results in compilation error`

Where c = new Car();
And v is a Vehicle interface reference (Vehicle v)

The compiler automatically handles the conversion (assignment) since the types are compatible (class – interface relationship), i.e., the type Car can be cast to Vehicle interface type since Car implements Vehicle Interface. (Car is a Vehicle).

CASTING OBJECT REFERENCES: EXPLICIT CASTING 

Sometimes we do an explicit cast in java when implicit casts don’t work or are not helpful for a particular scenario. The explicit cast is nothing but the name of the new “type” inside a pair of matched parentheses. As before, we consider the same Car and Ford Class.

```java 
class Car {
  void carMethod(){}
}
class Ford extends Car {
 void fordMethod () {}
}
```

We also have a breakingSystem() function which takes Car reference (Superclass reference) as an input parameter.
The method will invoke carMethod() regardless of the type of object (Car or Ford Reference) and if it is a Ford object, it will also invoke fordMethod(). We use the instanceof operator to determine the type of object at run time.

```java
public void breakingSystem (Car obj) {
    obj.carMethod();
   if (obj instanceof Ford)((Ford)obj).fordMethod ();
}
```

To invoke the fordMethod(), the operation (Ford)obj tells the compiler to treat the Car object referenced by obj as if it is a Ford object. Without the cast, the compiler will give an error message indicating that fordMethod() cannot be found in the Car definition.

The following program shown illustrates the use of the cast operator with references.

Honda and Ford are Siblings in the class Hierarchy. Both these classes are subclasses of Class Car. Both Car and HeavyVehicle Class extend Object Class. Any class that does not explicitly extend some other class will automatically extends the Object by default. This code instantiates an object of the class Ford and assigns the object’s reference to a reference variable of type Car. This assignment is allowed as Car is a superclass of Ford. In order to use a reference of a class type to invoke a method, the method must be defined at or above that class in the class hierarchy. Hence an object of Class Car cannot invoke a method present in Class Ford, since the method fordMethod is not present in Class Car or any of its superclasses. Hence this problem can be colved by a simple downcast by casting the Car object reference to the Ford Class Object reference as done in the program. Also an attempt to cast an object reference to its Sibling Object reference produces a ClassCastException at runtime, although compilation happens without any error.

```java
class Car extends Object {

	void carMethod() {
	}
}

class HeavyVehicle extends Object {
}

class Ford extends Car {

	void fordMethod() {
		System.out.println("I am fordMethod defined in Class Ford");
	}
}

class Honda extends Car {

	void fordMethod() {
		System.out.println("I am fordMethod defined in Class Ford");
	}
}

public class ObjectCastingEx {

	public static void main(String[] args) {
		Car obj = new Ford();
		//    Following will result in compilation error
		//    obj.fordMethod();	//As the method fordMethod is undefined for the Car Type
		//  Following will result in compilation error
		// ((HeavyVehicle)obj).fordMethod();
					//fordMethod is undefined in the HeavyVehicle Type
		//  Following will result in compilation error
		((Ford) obj).fordMethod();
		//Following will compile and run
		//	Honda hondaObj = (Ford)obj;	Cannot convert as they are sibblings
	}
}
```

## 26 Why should I have super type reference & sub class object?

Just now I've got an email from one of my student with the following question: "Why should we create `Animal obj = new Dog();` instead of `Dog obj = new Dog();`" Of course the example given here is made by myself but the question in detail is why all use super interface or super class reference instead of using the same class reference. You got the question right? This article answers the question.

The answer is: "It is a best practice being followed by our ancestors. Stop asking questions and code that way :-)" 

Ok, more seriously, consider the following example:

There is a SuperFancyClass created by developer A for some super fancy purposes. Note that all the references are HashMap.

```java
import java.util.HashMap;

public class SuperFancyClass {
    
    private HashMap<String, Object> mapOne;
    private HashMap<Integer, Object> mapTwo;

    public SuperFancyClass() {
        this.mapOne = new HashMap<>();
        this.mapTwo = new HashMap<>();
    }

    public HashMap<String, Object> doStuff1() {
        // Do something
        return this.mapOne;
    }

    public HashMap<String, Object> doStuff2() {
        // Do something
        return this.mapOne;
    }

    public HashMap<Integer, Object> doStuff3() {
        // Do something
        return this.mapTwo;
    }

    // Some other highly complex code here
}
```

That class is being used by developer B as given below.

```java
import java.util.HashMap;

public class SensitiveAgent {

    public static void main(String[] args) {
        
        SuperFancyClass superFancy = new SuperFancyClass();
        HashMap<String, Object> map1 = superFancy.doStuff1();
        HashMap<String, Object> map2 = superFancy.doStuff2();
        HashMap<Integer, Object> map3 = superFancy.doStuff3();
    }
    // Some other highly complex code here
}
```

Assuming both classes are highly complex but both developers A and B are happy with what they have, there is nothing else to worry.

As time progress, now developer A wants to make his Maps to maintain the insertion order. The Java API says, `HashMap` does not respect the insertion order so if you need insertion order, you need to switch to `LinkedHashMap`.

So now developer A wants to find and replace all of his/her HashMaps by LinkedHashMap. But this will not be such a short happy ending story in a highly complex code base where there can be several other local HashMaps which cannot be replaced by LinkedHashMap. So in reality, developer A has to go and change everywhere it requires to LinkedHashMap as provided below.

```java
import java.util.LinkedHashMap;

public class SuperFancyClass {
    
    private LinkedHashMap<String, Object> mapOne;
    private LinkedHashMap<Integer, Object> mapTwo;

    public SuperFancyClass() {
        this.mapOne = new LinkedHashMap<>();
        this.mapTwo = new LinkedHashMap<>();
    }

    public LinkedHashMap<String, Object> doStuff1() {
        // Do something
        return this.mapOne;
    }

    public LinkedHashMap<String, Object> doStuff2() {
        // Do something
        return this.mapOne;
    }

    public LinkedHashMap<Integer, Object> doStuff3() {
        // Do something
        return this.mapTwo;
    }

    // Some other highly complex code here
}
```

But now the code of developer B collapses because of the changes done in SuperFancyClass. Then developer B has to go and change the references from HashMap to LinkedHashMap as shown below.

```java
import java.util.LinkedHashMap;

public class SensitiveAgent {

    public static void main(String[] args) {
        
        SuperFancyClass superFancy = new SuperFancyClass();
        LinkedHashMap<String, Object> map1 = superFancy.doStuff1();
        LinkedHashMap<String, Object> map2 = superFancy.doStuff2();
        LinkedHashMap<Integer, Object> map3 = superFancy.doStuff3();
    }

    // Some other highly complex code here
}
```

Rule of debugging:
Now, this is the time to introduce an important rule of debugging: 

__Fixing a bug is equivalent to making several other bugs.__

In other words, if you modify an existing code, the number of changes you have made will be proportional to the number of newly expected bugs because we are all human and we do mistakes. Without our intention, we might delete a local variable that hides an instance variable. Or else we might modify that single line which causes to bring the entire world to end. So always keep your changes as less as possible.
Coming back to the previous scenario, developer A modifies the SuperFancyClass in 7 places and developer B has to modify the SensitiveAgent in 3 places. Even in a code-base which contains two dummy classes, there are 10 places altogether to modify. Just imagine a project with hundreds/thousands of classes and millions of lines. Yep they do exists and it will be a catastrophic.

Time to travel back...
Suppose if the developer A designed his/her class as given below using super interface references (However the objects must be created using subclass. See the constructor):

```java
import java.util.Map;
import java.util.HashMap;

public class SuperFancyClass {
    
    private Map<String, Object> mapOne;
    private Map<Integer, Object> mapTwo;

    public SuperFancyClass() {
        this.mapOne = new HashMap<>();
        this.mapTwo = new HashMap<>();
    }

    public Map<String, Object> doStuff1() {
        // Do something
        return this.mapOne;
    }

    public Map<String, Object> doStuff2() {
        // Do something
        return this.mapOne;
    }

    public Map<Integer, Object> doStuff3() {
        // Do something
        return this.mapTwo;
    }

    // Some other highly complex code here
}
```

The developer B would developed his/her code like this because the return types of those methods are Map; the super interface:

```java
import java.util.Map;

public class SensitiveAgent {

    public static void main(String[] args) {
        
        SuperFancyClass superFancy = new SuperFancyClass();
        Map<String, Object> map1 = superFancy.doStuff1();
        Map<String, Object> map2 = superFancy.doStuff2();
        Map<Integer, Object> map3 = superFancy.doStuff3();
    }

    // Some other highly complex code here
}
```

Now if the same situation comes where the developer A wants to preserve insertion order in his/her maps, only lines he/she has to change are just those two lines inside the constructor as shown below:

```java
import java.util.Map;
import java.util.LinkedHashMap;

public class SuperFancyClass {
    
    private Map<String, Object> mapOne;
    private Map<Integer, Object> mapTwo;

    public SuperFancyClass() {
        this.mapOne = new LinkedHashMap<>();
        this.mapTwo = new LinkedHashMap<>();
    }

    public Map<String, Object> doStuff1() {
        // Do something
        return this.mapOne;
    }

    public Map<String, Object> doStuff2() {
        // Do something
        return this.mapOne;
    }

    public Map<Integer, Object> doStuff3() {
        // Do something
        return this.mapTwo;
    }

    // Some other highly complex code here
}
```

Developer B does not need to change anything because there is nothing changed int the API level (return types are not changed by developer A). So now the same behavior is achieved with less number of modifications (This time only 2). This is what we call extensible, modifiable, (all those blah-blah-blah-able) code.

Then why not Object instead of Map?

Now you may have a question: Should we always use the super most interface/class as the reference? Not always. It depends on the requirements. Climbing towards super types means, we are limiting the features because 99% of the time, sub classes have more features than super types. For example, compare java.lang.Number with its sub classes or compare java.util.Collection with its sub interfaces/classes. So use the super type reference which has all the functionalities you are expected to have.

Does the rule applied to local variables?
Then what is the advantage of using super reference in local variables which have no impact on others? I guess this is because we developers are used to that and there is nothing wrong in following the same practice in local variables. For example, consider this case:

```java
import java.util.List;
import java.util.ArrayList;

public class HelloWorld {
    public static void main(String[] args) {
        List<String> list = new ArrayList<>();
        list.add("Java");
        list.add("Python");
        list.add("C++");
        System.out.println(list);
    }
}
```

In this code there is no advantage of using super interface reference but I do write this way because I am used to it. If there is no disadvantages, why do you bother about it? Keep calm and code your references in super type :-)

### __Easy ones but worth mentioning:__ 

* Explain public static void main(String args[])
* Why Java is platform independent?
* What are constructors in Java?

[up](#0-up)
