## **Object Oriented Concepts**
**Class** is a template of an Object, a logical construct. **Objects** are instance of a class & exists in physical reality in heap memory. Dot operator links with reference variable with instance variables `instance_variable . reference_variable`. ***New keyword*** is used to create an instance of class, dynamically allocates memory & returns a reference to it. If class is not initialised, by default, all the values within it becomes null. In primitives there is pass by value, unlike objects, where we follow passed by referenced. **final** keyword make any variable as constant. Write constant in capital letter. *When a non-primitive is final, you cannot reassign it*.

Code on the left side of equal to happens in **compile time**, rest runs in **runtime**. Constructor defines what will have when any object is instantiated. ***this*** keyword is used to access any custom reference variable. **Constructor overloading** refers to defining  constructor with different type of variables to provide ease at instantiation. Constructor **chaining** refers to internally calling a constructor from another constructor.** Wrapper classes** are used to create primitives in the format of objects `Integer id = new Integer(12115007)`.**Singleton** is the type of class which only allows programmer to create one instance object of the class. We make the constructor private which denies creating multiple instances.

Before **garbage collection**, we cannot destory objects manually, but, can specify actions that need to be performed when this object gets collected using *finalise* method within the class. **Static** is used for the attributes which are common to all the attributes, but, are independent of object. Like population is common to human class, but, it is independent of the object of human class. Also, use class name to access the static variable, as it is common to every object. Static method in short belongs to the class not object. To initialise static variable use a static block. It will only run for the first time, when the class in loaded once. In case of inner classes, outside class cannot be static as it is not dependent on any other class. Static methods are resolved in compile time not run time.

```java
public class StaticBlock {
    static long population = 10;
    static long incomeTax;

    static { // this is the static block snippet
        System.out.println("I am initializing my static variables !");
        incomeTax = population * 125;
    }
}
```
### **Four Pillars of OOPS**
---
1. **Inheritance :** Over here, we have a derived class *(child)* which has inherited all the members or properties of base class. Using extends keyword, we can derive a new child class out of parent class `class Child extends Base {}`. But, we have to reinitialise the attributes of the parent in the constructor of the child. Super keyword is used to call immediate parent constructor. `super(length, breadth)` will call `public Rect(l, b) { this.length = l; this.breadth = b }`. Type of the reference variable determines which members can be accessed, not, the type of object. Super keyword should be used at the top of the child class constructor.
   - **Single level** inheritance refers to when there is a single child class & a single parent class.
   - **Multi level** inheritance refers to when parent of child class can also be child of another parent class & vice-versa.
   - **Multiple** inheritance refers to when child class is extending more than one classes. *`Not supported in java`*.
   - **Hierarchial** inheritance refers to multiple child class condition extending single parent class.
  
2. **Polymorphism :** refers to many ways to represent a single entity/member. It means that the defination of the method is same like paramters allowed etc., but, the action of the methods remains different for different cases. Like Shape also has area method, circle & square also has area method, difference is in the action of area method with instance of circle & square.
   - **Compile Time or Static** polymorphism achieved using method overloading. Which means same name, but, return type, arguments can be different.
   - **Runtime or Dynamic** polymorphism achieved with method overriding. Which means differnt body, but, everything same. In ` Parent obj = new Child() ` which method will be called, depends on the children, but, which attributes could be used depends on Parent. Known as *Upcasting*. Dynamic method dispatching service decide if a method needs to be executed in runtime or compile time.**Final** method is used to avoid overriding known as early binding. Static methods runs on first class call & cannot be overridden, can be inherited.
  
3. **Abstraction :** refers to hiding unneccessary information & provide only the valuable information. Like if we use arraylist, we don't really care about how it is implemented, we just use it. ` It is a design issue.`

4. **Encapsulation :** refers to wrapping the implementation of the data members & methods in a class. ` It is a programmer issue ` where they achieve abstraction through encapsulating code. **Data hiding** refers to hiding data using private keyword, ensuring data security & encapsulation is a sub-process of it where we are concerned with reducing the complexity of the system by providing ready-mate functions.
---

**Access modifier**  play an important role in data security & maintaining data integrity. There are four types of the same - public, private, default & protected. **Packages** are of two types: User-defined & In-built. Some of the in-built packages include *lang* ` contains basic & important java language essentials `, *io* ` contains input-output functions `, *util* ` contains utility class such as data structures & collection framework `.
   - *Public* modifier can be accessed any where, in same class, package, sub class, different package, but, sub class, even in the different package & different class.
   - *Protected* modifier have the similar rules as public, but, cannot be accessed from different package & not sub class.
   - *Default* modifier can only be accessed from same package, inheritance within package is allowed.
   - *Private* modifier can only be accesssed within the class.

**Abstract class** does not have body, they only provide function prototype. Later, sub class have to inherit & implement that method. Any class with one or more abstract method, must be declared as abstract by convention. We cannot create objects of the abstract class, but, you can make a constructor for the abstract class. To implement multiple inheritance we use interfaces. Here, we contain abstract function similar to abstract class & implementing multiple interfaces is also allowed over here. They are by default, final & variables are static. Implementing a class which extends an interface, reuqires to implement all the methods from all the connected interfaces. **Annotations** are also a sort of interfaces.

```java 
public @interface Override { }
```

**Generics** allows the code to be type safe & reuse the code written for multiple data types. Also, here only classes can be added, no type declaration as primitives. We can use a raw parameter ` <T> ` for creating generic classes. Thus, we can now use this code for String, Integer, Float etc. **Comparables** are used by implementig the imterface, and we can implement ` compareTo() ` method return a integer value. This is very useful in implementing custom Sort over any object & if, there are many fields to check for, the condition we give in the compare to method, then, will sort on that basis. Below is the snippet using wildcards.

```java
    public void display(List<? extends Number> list) {
        for (Number num : list) {
            System.out.print(num + " ");
        }
        System.out.println();
    }
```

**Exception Handling** is very crucial process to avoid unneccesary termination of the program without producing the workflow it was decided to follow. ` Throwable class ` extends Object class which has two categories as *Exceptions & Errors*. Exceptions are of two types as *Checked/Compile time* & *Unchecked/Runtime*. We can provide custom message by using ` throw new Exception("Hi! exception") `, but don't forget to mention ` throws Exception ` in front of the method. We can create custom Exception, by extending the Exception class & create a constructor, take ` String message ` & pass as ` super(message); `. Then, you can use getMessage() message of Exception class to throw custom message in custom exception.

```java
public class Exceptions {
    public static void main(String[] args) {
        int a = 100;
        int b = 0;
        try {
           int c = a / b;
        } catch (ArithmeticException e) {
            System.out.println(e.getMessage());
        } finally {
            System.out.println("We finally catched the exception");
        }
    } 
}
```

```java
/* 
 * Implementing clonable interface in class file, creates a shallow copy.
 * Shallow copy will not create object, it will copy the object references, but, it will create new primitives.
*/
public class Human implements Clonable {
    public Object clone() throws CloneNotSupportedException {
        return super.clone();
    }

    public static void main(String[] args) throws CloneNotSupportedException {
        Human satyam = new Human("Satyam");
        Human sattu = (Human)satyam.clone();
    }
}
```

![Collection Framework](Collection_Framework.png)

**Collection Framework** is one of the most important library in Java. It has a collection of data structures and stores methods related to each of the data structures. Vector is similar to array list, but, only difference is in arraylist multiple threads can access it unlike, vectors, in which threads needs to be in waiting area if any one thread is already operating. Thus, arraylist is more faster than vectors. **Enums** or Enumerations are the constant group of variables. They are by default static, public & final. Methods on it are as follows ` MONDAY.ordinal() ` will print the position of the constant in enum. Constructor is either private or default. It does not follows inheritance, but, implements interface.

```java
public class Basic {
    enum Week {
        MONDAY, TUESDAY, WEDNESDAY, THURSDAY, FRIDAY, SATURDAY, SUNDAY
    }

    public static void main(String[] args) {
        Week week = Week.MONDAY;
        for (Week day: Week.values()) 
            System.out.println(day);
    }
}
```



