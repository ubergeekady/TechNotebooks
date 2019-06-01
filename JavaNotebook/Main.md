## Types, Variables & Conversions

```java
// Java program to demonstrate primitive data types in Java 
class Aditya 
{ 
	public static void main(String args[]) 
	{ 
		char a = 'G'; 
		int i=89; 
		byte b = 4; 
		short s = 56; 
		long lo = 112234454L;
		double d = 4.355453532; 
		float f = 4.7333434f; 
		boolean bool = true;
    String str = "Aditya";
		
		System.out.println("char: " + a); 
		System.out.println("integer: " + i); 
		System.out.println("byte: " + b); 
		System.out.println("short: " + s); 
		System.out.println("long: " + lo); 
		System.out.println("float: " + f); 
		System.out.println("double: " + d); 
		System.out.println("boolean: " + bool); 
	}	 
}
```

It is fairly common to assign a value of one type to a variable of another type. If the two types are compatible, then Java will perform the conversion automatically. For example, it is always possible to assign an **int** value to a **long** variable. However, not all types are compatible, and thus, not all type conversions are implicitly allowed. For instance, there is no automatic conversion defined from **double** to **byte**. Fortunately, it is still possible to obtain a conversion between incompatible types. To do so, you must use a *cast*, which performs an explicit conversion between incompatible types. Let’s look at both automatic type conversions and casting. 

**Automatic Conversions** : When one type of data is assigned to another type of variable, an *automatic type conversion* will take place if the following two conditions are met: 

- The two types are compatible. 
- The destination type is larger than the source type. 

When these two conditions are met, a *widening conversion* takes place. For example, the **int** type is always large enough to hold all valid **byte** values, so no explicit cast statement is required. 

For widening conversions, the numeric types, including integer and floating-point types, are compatible with each other. However, there are no automatic conversions from the numeric types to **char** or **boolean**. Also, **char** and **boolean** are not compatible with each other. Java also performs an automatic type conversion when storing a literal integer constant into variables of type **byte**, **short**, **long**, or **char**. 

**Casting Incompatible Types**

Although the automatic type conversions are helpful, they will not fulfill all needs. For example, what if you want to assign an **int** value to a **byte** variable? This conversion will not be performed automatically, because a **byte** is smaller than an **int**. This kind of conversion is sometimes called a *narrowing conversion*, since you are explicitly making the value narrower so that it will fit into the target type. 

To create a conversion between two incompatible types, you must use a cast. A *cast* is simply an explicit type conversion. It has this general form: 

(*target*-*type*) *value* 

Here, *target-type* specifies the desired type to convert the specified value to. For example, the following fragment casts an **int** to a **byte**. If the integer’s value is larger than the range of a byte**, it will be reduced modulo (the remainder of an integer division by the) byte’s range.

```java
int a;
byte b;
// ...
b = (byte) a;
```

A different type of conversion will occur when a floating-point value is assigned to an integer type: *truncation*. As you know, integers do not have fractional components. Thus, when a floating-point value is assigned to an integer type, the fractional component is lost. For example, if the value 1.23 is assigned to an integer, the resulting value will simply be 1. The 0.23 will have been truncated. Of course, if the size of the whole number component is too large to fit into the target integer type, then that value will be reduced modulo the target type’s range.

**Automatic Type Promotion** In addition to assignments, there is another place where certain type conversions may occur: in expressions. To see why, consider the following. In an expression, the precision required of an intermediate value will sometimes exceed the range of either operand. For example, examine the following expression:

```java
 byte a = 40;
 byte b = 50;
 byte c = 100;
 int d = a * b / c;
```

The result of the intermediate term **a \* b** easily exceeds the range of either of its **byte** operands. To handle this kind of problem, Java automatically promotes each **byte**, **short**, or **char** operand to **int** when evaluating an expression. This means that the subexpression **a\*b** is performed using integers—not bytes. Thus, 2,000, the result of the intermediate expression, **50 \* 40**, is legal even though **a** and **b** are both specified as type **byte**.

As useful as the automatic promotions are, they can cause confusing compile-time errors. For example, this seemingly correct code causes a problem:  					 				 			 		

```java
byte b = 50;
b = b * 2; // Error! Cannot assign an int to a byte!
```

The code is attempting to store 50 * 2, a perfectly valid **byte** value, back into a **byte** variable. However, because the operands were automatically promoted to **int** when the expression was evaluated, the result has also been promoted to **int**. Thus, the result of the expression is now of type **int**, which cannot be assigned to a **byte** without the use of a cast. This is true even if, as in this particular case, the value being assigned would still fit in the target type.  					 				 			 		

```java
byte b = 50;
b = (byte)(b * 2);
```

Java defines several *type promotion* rules that apply to expressions. They are as follows: First, all **byte**, **short**, and **char** values are promoted to **int**, as just described. Then, if one operand is a **long**, the whole expression is promoted to **long**. If one operand is a **float**, the entire expression is promoted to **float**. If any of the operands are **double**, the result is **double**.

**Byte -> Short -> Int -> Long -> Float -> Double**



## Arrays

```java
int month_days[];
month_days = new int[12];
month_days[6] = 31;

//Other way
int month_days[] = { 31, 28, 31, 30, 31, 30, 31, 31, 30, 31,30, 31 };

//Two dimensional
int twoD[][] = new int[4][5];
```

When you allocate memory for a multidimensional array, you need only specify the memory for the first (leftmost) dimension. You can allocate the remaining dimensions separately. For example, this following code allocates memory for the first dimension of  two when it is declared. It allocates the second dimension manually. 

```java
int twoD[][] = new int[4][];
twoD[0] = new int[5];
twoD[1] = new int[5];
twoD[2] = new int[5];
twoD[3] = new int[5];
```

```java
int al[] = new int[3];
int[] a2 = new int[3];

char twod1[][] = new char[3][4];
char[][] twod2 = new char[3][4];
```

## Operators & Control Statements

[To be written later]

## Classes & Objects

A class is a blue print from which individual objects are created.

```java
/* A program that uses the Box class.
   Call this file BoxDemo.java
*/
class Box {
  double width;
  double height;
  double depth;
}
// This class declares an object of type Box.
class BoxDemo {
  public static void main(String args[]) {
    Box mybox = new Box();
    double vol;
    // assign values to mybox's instance variables
    mybox.width = 10;
    mybox.height = 20;
    mybox.depth = 15;
    // compute volume of box
    vol = mybox.width * mybox.height * mybox.depth;
    System.out.println("Volume is " + vol);
  }
}
```

```java
// This program uses a parameterized method.
class Box {
  double width;
  double height;
  double depth;
  // compute and return volume
  double volume() {
    return width * height * depth;
  }
  // sets dimensions of box
  void setDim(double w, double h, double d) {
    width = w;
    height = h;
    depth = d;
  } 
}
```

**Constructors**

```java
/* Here, Box uses a parameterized constructor to
   initialize the dimensions of a box.
*/
class Box {
  double width;
  double height;
  double depth;
  // This is the constructor for Box.
  Box(double w, double h, double d) {
    width = w;
    height = h;
    depth = d;
  }
  // compute and return volume
  double volume() {
    return width * height * depth;
  }
}
```

```
Box mybox1 = new Box(10, 20, 15);
```

In Java, it is possible to define two or more methods within the same class that share the same name, as long as their parameter declarations are different. When this is the case, the methods are said to be overloaded, and the process is referred to as *method overloading*.

```java
// Demonstrate method overloading.
class OverloadDemo {
  void test() {
    System.out.println("No parameters");
  }
  // Overload test for one integer parameter.
  void test(int a) {
    System.out.println("a: " + a);
  }
  // Overload test for two integer parameters.
  void test(int a, int b) {
    System.out.println("a and b: " + a + " " + b);
  }
  // Overload test for a double parameter
  double test(double a) {
    System.out.println("double a: " + a);
    return a*a; }
}
```

When you pass a primitive type to a method, it is passed by value. Thus, a copy of the argument is made, and what occurs to the parameter that receives the argument has no effect outside the method. When you pass an object to a method, the situation changes dramatically, because objects are passed by what is effectively call-by-reference. Keep in mind that when you create a variable of a class type, you are only creating a reference to an object. Thus, when you pass this reference to a method, the parameter that receives it will refer to the same object as that referred to by the argument. This effectively means that objects act as if they are passed to methods by use of call-by-reference. Changes to the object inside the method do affect the object used as an argument. 

**Access Control**

Let’s begin by defining **public** and **private**. When a member of a class is modified by **public**, then that member can be accessed by any other code. When a member of a class is specified as **private**, then that member can only be accessed by other members of its class. Now you can understand why **main( )** has always been preceded by the **public** modifier. It is called by code that is outside the program—that is, by the Java run-time system. When no access modifier is used, then by default the member of a class is public within its own package, but cannot be accessed outside of its package.

An access modifier precedes the rest of a member’s type specification. That is, it must begin a member’s declaration statement.

```java
public int i;
private double j;
private int myMethod(int a, char b) { //...
```

**Static**

There will be times when you will want to define a class member that will be used independently of any object of that class. Normally, a class member must be accessed only  in conjunction with an object of its class. However, it is possible to create a member that can be used by itself, without reference to a specific instance. To create such a member, precede its declaration with the keyword **static**. When a member is declared **static**, it can be accessed before any objects of its class are created, and without reference to any object. You can declare both methods and variables to be **static**. The most common example of a **static** member is **main( )**. **main( )** is declared as **static** because it must be called before any objects exist.

Instance variables declared as **static** are, essentially, global variables. When objects of its class are declared, no copy of a **static** variable is made. Instead, all instances of the class share the same **static** variable. Methods declared as **static** have several restrictions:

- They can only directly call other **static** methods.
- They can only directly access **static** data.
- They cannot refer to **this** or **super** in any way.

If you need to do computation in order to initialize your **static** variables, you can declare a **static** block that gets executed exactly once, when the class is first loaded. The following example shows a class that has a **static** method, some **static** variables, and a **static** initialization block:

```java
// Demonstrate static variables, methods, and blocks.
class UseStatic {
  static int a = 3;
  static int b;
  static void meth(int x) {
    System.out.println("x = " + x);
    System.out.println("a = " + a);
    System.out.println("b = " + b);
  }
  static {
    System.out.println("Static block initialized.");
    b = a * 4;
  }
  public static void main(String args[]) {
    meth(42);
  }
}
```

```
Static block initialized. x = 42
a= 3
b = 12
```

As soon as the **UseStatic** class is loaded, all of the **static** statements are run. First, **a** is set to **3**, then the **static** block executes, which prints a message and then initializes **b** to **a\*4** or **12**. Then **main( )** is called, which calls **meth( )**, passing **42** to **x**. The three **println( )** statements refer to the two **static** variables **a** and **b**, as well as to the local variable **x**.

Outside of the class in which they are defined, **static** methods and variables can be used independently of any object. To do so, you need only specify the name of their class followed by the dot operator. For example, if you wish to call a **static** method from outside its class, you can do so using the following general form:

*classname.method*( )

Here, *classname* is the name of the class in which the **static** method is declared. As you can see, this format is similar to that used to call non-**static** methods through object- reference variables. A **static** variable can be accessed in the same way—by use of the dot operator on the name of the class. This is how Java implements a controlled version of global methods and global variables. Here is an example. Inside **main( )**, the **static** method **callme( )** and the **static** variable **b** are accessed through their class name **StaticDemo**.  

```java
class StaticDemo {
  static int a = 42;
  static int b = 99;
  static void callme() {
    System.out.println("a = " + a);
  } 
}
class StaticByName {
  public static void main(String args[]) {
    StaticDemo.callme();
    System.out.println("b = " + StaticDemo.b);
  }
}
```

**Final**

A field can be declared as **final**. Doing so prevents its contents from being modified, making it, essentially, a constant. This means that you must initialize a **final** field when it is declared. You can do this in one of two ways: First, you can give it a value when it is declared. Second, you can assign it a value within a constructor. The first approach is the most common. Here is an example:

```java
final int FILE_NEW = 1;
final int FILE_OPEN = 2;
final int FILE_SAVE = 3;
final int FILE_SAVEAS = 4;
final int FILE_QUIT = 5;
```

**Nested Classes**

It is possible to define a class within another class; such classes are known as *nested classes*. The scope of a nested class is bounded by the scope of its enclosing class. Thus, if class B is defined within class A, then B does not exist independently of A. A nested class has access to the members, including private members, of the class in which it is nested. However, the enclosing class does not have access to the members of the nested class. A nested class that is declared directly within its enclosing class scope is a member of its enclosing class. It is also possible to declare a nested class that is local to a block. 

There are two types of nested classes: *static* and *non-static*. A static nested class is one that has the **static** modifier applied. Because it is static, it must access the non-static members of its enclosing class through an object. That is, it cannot refer to non-static members of its enclosing class directly. Because of this restriction, static nested classes are seldom used. 

The most important type of nested class is the *inner* class. An inner class is a non-static nested class. It has access to all of the variables and methods of its outer class and may refer to them directly in the same way that other non-static members of the outer class do. 

The following program illustrates how to define and use an inner class. The class named **Outer** has one instance variable named **outer_x**, one instance method named **test( )**, and defines one inner class called **Inner**.

```java
// Demonstrate an inner class.
class Outer {
  int outer_x = 100;
  void test() {
    Inner inner = new Inner();
    inner.display();
  }
  // this is an inner class
  class Inner {
    void display() {
      System.out.println("display: outer_x = " + outer_x);
    }
  }
}
class InnerClassDemo {
  public static void main(String args[]) {
    Outer outer = new Outer();
    outer.test();
  }
}
```

In the program, an inner class named **Inner** is defined within the scope of class **Outer**. Therefore, any code in class **Inner** can directly access the variable **outer_x**. An instance method named **display( )** is defined inside **Inner**. This method displays **outer_x** on the standard output stream. The **main( )** method of **InnerClassDemo** creates an instance of class **Outer** and invokes its **test( )** method. That method creates an instance of class **Inner** and the **display( )** method is called. 

It is important to realize that an instance of **Inner** can be created only in the context of class **Outer**. The Java compiler generates an error message otherwise. In general, an inner class instance is often created by code within its enclosing scope, as the example does. 

As explained, an inner class has access to all of the members of its enclosing class, but the reverse is not true. Members of the inner class are known only within the scope of the inner class and may not be used by the outer class. For example, 

**Inheritance**

Inheritance is an important pillar of OOP(Object Oriented Programming). It is the mechanism in java by which one class is allow to inherit the features(fields and methods) of another class.

- **Super Class:** The class whose features are inherited is known as super class(or a base class or a parent class).
- **Sub Class:** The class that inherits the other class is known as sub class(or a derived class, extended class, or child class). The subclass can add its own fields and methods in addition to the superclass fields and methods.
- **Reusability:** Inheritance supports the concept of “reusability”, i.e. when we want to create a new class and there is already a class that includes some of the code that we want, we can derive our new class from the existing class. By doing this, we are reusing the fields and methods of the existing class.

```
class derived-class extends base-class  
{  
   //methods and fields  
}  
```

```java
//Java program to illustrate the 
// concept of inheritance 

// base class 
class Bicycle 
{ 
	// the Bicycle class has two fields 
	public int gear; 
	public int speed; 
		
	// the Bicycle class has one constructor 
	public Bicycle(int gear, int speed) 
	{ 
		this.gear = gear; 
		this.speed = speed; 
	} 
		
	// the Bicycle class has three methods 
	public void applyBrake(int decrement) 
	{ 
		speed -= decrement; 
	} 
		
	public void speedUp(int increment) 
	{ 
		speed += increment; 
	} 
	
	// toString() method to print info of Bicycle 
	public String toString() 
	{ 
		return("No of gears are "+gear 
				+"\n"
				+ "speed of bicycle is "+speed); 
	} 
} 

// derived class 
class MountainBike extends Bicycle 
{ 
	
	// the MountainBike subclass adds one more field 
	public int seatHeight; 

	// the MountainBike subclass has one constructor 
	public MountainBike(int gear,int speed, 
						int startHeight) 
	{ 
		// invoking base-class(Bicycle) constructor 
		super(gear, speed); 
		seatHeight = startHeight; 
	} 
		
	// the MountainBike subclass adds one more method 
	public void setHeight(int newValue) 
	{ 
		seatHeight = newValue; 
	} 
	
	// overriding toString() method 
	// of Bicycle to print more info 
	@Override
	public String toString() 
	{ 
		return (super.toString()+ 
				"\nseat height is "+seatHeight); 
	} 
	
} 

// driver class 
public class Test 
{ 
	public static void main(String args[]) 
	{ 
		
		MountainBike mb = new MountainBike(3, 100, 25); 
		System.out.println(mb.toString()); 
			
	} 
} 

```

```
No of gears are 3
speed of bicycle is 100
seat height is 25
```

In above program, when an object of MountainBike class is created, a copy of the all methods and fields of the superclass acquire memory in this object. That is why, by using the object of the subclass we can also access the members of a superclass. Please note that during inheritance only object of subclass is created, not the superclass. In practice, inheritance and polymorphism are used together in java to achieve fast performance and readability of code. In inheritance, subclass acquires super class properties. An important point to note is, when subclass object is created, a separate object of super class object will not be created. Only a subclass object object is created that has super class variables. This situation is different from a normal assumption that a constructor call means an object of the class is created, so we can’t blindly say that whenever a class constructor is executed, object of that class is created or not.

```java
// A Java program to demonstrate that both super class 
// and subclass constructors refer to same object 

// super class 
class Fruit 
{ 
	public Fruit() 
	{ 
		System.out.println("Super class constructor"); 
		System.out.println("Super class object hashcode :" + 
						this.hashCode()); 
		System.out.println(this.getClass().getName()); 
	} 
} 

// sub class 
class Apple extends Fruit 
{ 
	public Apple() 
	{ 
		System.out.println("Subclass constructor invoked"); 
		System.out.println("Sub class object hashcode :" + 
						this.hashCode()); 
		System.out.println(this.hashCode() + " " + 
						super.hashCode()); 

		System.out.println(this.getClass().getName() + " " + 
						super.getClass().getName()); 
	} 
} 

// driver class 
public class Test 
{ 
	public static void main(String[] args) 
	{ 
		Apple myApple = new Apple(); 
	} 
} 

```

```
super class constructor 
super class object hashcode :366712642
Apple
sub class constructor 
sub class object hashcode :366712642
366712642   366712642
Apple  Apple
```

As we can see that both super class(Fruit) object hashcode and subclass(Apple) object hashcode are same, so only one object is created. This object is of class Apple(subclass) as when we try to print name of class which object is created, it is printing Apple which is subclass.

**Single Inheritance :** In single inheritance, subclasses inherit the features of one superclass. In image below, the class A serves as a base class for the derived class B.

```java
//Java program to illustrate the 
// concept of single inheritance 
import java.util.*; 
import java.lang.*; 
import java.io.*; 

class one 
{ 
	public void print_geek() 
	{ 
		System.out.println("Geeks"); 
	} 
} 

class two extends one 
{ 
	public void print_for() 
	{ 
		System.out.println("for"); 
	} 
} 
// Driver class 
public class Main 
{ 
	public static void main(String[] args) 
	{ 
		two g = new two(); 
		g.print_geek(); 
		g.print_for(); 
		g.print_geek(); 
	} 
} 

```

**Multilevel Inheritance :** In Multilevel Inheritance, a derived class will be inheriting a base class and as well as the derived class also act as the base class to other class. In below image, the class A serves as a base class for the derived class B, which in turn serves as a base class for the derived class C. In Java, a class cannot directly access the grandparent's members.

```java
// Java program to illustrate the 
// concept of Multilevel inheritance 
import java.util.*; 
import java.lang.*; 
import java.io.*; 

class one 
{ 
	public void print_geek() 
	{ 
		System.out.println("Geeks"); 
	} 
} 

class two extends one 
{ 
	public void print_for() 
	{ 
		System.out.println("for"); 
	} 
} 

class three extends two 
{ 
	public void print_geek() 
	{ 
		System.out.println("Geeks"); 
	} 
} 

// Drived class 
public class Main 
{ 
	public static void main(String[] args) 
	{ 
		three g = new three(); 
		g.print_geek(); 
		g.print_for(); 
		g.print_geek(); 
	} 
} 

```

**Hierarchical Inheritance** : In Hierarchical Inheritance, one class serves as a superclass (base class) for more than one sub class.In below image, the class A serves as a base class for the derived class B,C and D.

```java
// Java program to illustrate the 
// concept of Hierarchical inheritance 
import java.util.*; 
import java.lang.*; 
import java.io.*; 

class one 
{ 
	public void print_geek() 
	{ 
		System.out.println("Geeks"); 
	} 
} 

class two extends one 
{ 
	public void print_for() 
	{ 
		System.out.println("for"); 
	} 
} 

class three extends one 
{ 
	/*............*/
} 

// Drived class 
public class Main 
{ 
	public static void main(String[] args) 
	{ 
		three g = new three(); 
		g.print_geek(); 
		two t = new two(); 
		t.print_for(); 
		g.print_geek(); 
	} 
} 

```

**Multiple Inheritance (Through Interfaces)** : In Multiple inheritance ,one class can have more than one superclass and inherit features from all parent classes. Please note that Java does not support multiple inheritance with classes. In java, we can achieve multiple inheritance only through Interfaces. In image below, Class C is derived from interface A and B.

```java
// Java program to illustrate the 
// concept of Multiple inheritance 
import java.util.*; 
import java.lang.*; 
import java.io.*; 

interface one 
{ 
	public void print_geek(); 
} 

interface two 
{ 
	public void print_for(); 
} 

interface three extends one,two 
{ 
	public void print_geek(); 
} 
class child implements three 
{ 
	@Override
	public void print_geek() { 
		System.out.println("Geeks"); 
	} 

	public void print_for() 
	{ 
		System.out.println("for"); 
	} 
} 

// Drived class 
public class Main 
{ 
	public static void main(String[] args) 
	{ 
		child c = new child(); 
		c.print_geek(); 
		c.print_for(); 
		c.print_geek(); 
	} 
} 

```

**Hybrid Inheritance(Through Interfaces) :** It is a mix of two or more of the above types of inheritance. Since java doesn’t support multiple inheritance with classes, the hybrid inheritance is also not possible with classes. In java, we can achieve hybrid inheritance only through interfaces:

**Important facts about inheritance in Java**

- **Default superclass**: Except Object, which has no superclass, every class has one and only one direct superclass (single inheritance). In the absence of any other explicit superclass, every class is implicitly a subclass of Object
- **Superclass can only be one:** A superclass can have any number of subclasses. But a subclass can have only **one** superclass. This is because Java does not support multiple inheritance with classes. Although with interfaces, multiple inheritance is supported by java.
- **Inheriting Constructors:** A subclass inherits all the members (fields, methods, and nested classes) from its superclass. Constructors are not members, so they are not inherited by subclasses, but the constructor of the superclass can be invoked from the subclass.
- **Private member inheritance:** A subclass does not inherit the private members of its parent class. However, if the superclass has public or protected methods(like getters and setters) for accessing its private fields, these can also be used by the subclass.

**What all can be done in a Subclass?**

In sub-classes we can inherit members as is, replace them, hide them, or supplement them with new members:

- The inherited fields can be used directly, just like any other fields.
- We can declare new fields in the subclass that are not in the superclass.
- The inherited methods can be used directly as they are.
- We can write a new *instance* method in the subclass that has the same signature as the one in the superclass, thus overriding it (as in example above, *toString()* method is overridden).
- We can write a new *static* method in the subclass that has the same signature as the one in the superclass, thus hiding it.
- We can declare new methods in the subclass that are not in the superclass.
- We can write a subclass constructor that invokes the constructor of the superclass, either implicitly or by using the keyword super.

**Why Constructors are not inherited in Java?**

Constructor is a block of code that allows you to create an object of class and has same name as class with no explicit return type. Whenever a class (child class) extends another class (parent class), the sub class inherits state and behavior in the form of variables and methods from its super class but it does not inherit constructor of super class because of following reasons:

Constructors are special and have same name as class name. So if constructors were inherited in child class then child class would contain a parent class constructor which is against the constraint that constructor should have same name as class name. For example see the below code:

```java
class Parent { 
	public Parent() 
	{ 
	} 

	public void print() 
	{ 
	} 
} 

public class Child extends Parent { 
	public Parent() 
	{ 
	} 
	public void print() 
	{ 
	} 

	public static void main(String[] args) 
	{ 
		Child c1 = new Child(); // allowed 
		Child c2 = new Parent(); // not allowed 
	} 
} 

```

If we define Parent class constructor inside Child class it will give compile time error for return type and consider it a method. But for print method it does not give any compile time error and consider it a overriding method.

Now suppose if constructors can be inherited then it will be impossible to achieving encapsulation. Because by using a super class’s constructor we can access/initialize private members of a class.

A constructor cannot be called as a method. It is called when object of the class is created so it does not make sense of creating child class object using parent class constructor notation. i.e. Child c = new Parent();

A parent class constructor is not inherited in child class and this is why super() is added automatically in child class constructor if there is no explicit call to super or this.

**Overriding**

In any object-oriented programming language, Overriding is a feature that allows a subclass or child class to provide a specific implementation of a method that is already provided by one of its super-classes or parent classes. When a method in a subclass has the same name, same parameters or signature and same return type(or sub-type) as a method in its super-class, then the method in the subclass is said to override the method in the super-class.

Method overriding is one of the way by which java achieve Run Time Polymorphism.The version of a method that is executed will be determined by the object that is used to invoke it. If an object of a parent class is used to invoke the method, then the version in the parent class will be executed, but if an object of the subclass is used to invoke the method, then the version in the child class will be executed.In other words, it is the type of the object being referred to (not the type of the reference variable) that determines which version of an overridden method will be executed.

```java
// A Simple Java program to demonstrate 
// method overriding in java 

// Base Class 
class Parent 
{ 
	void show() { System.out.println("Parent's show()"); } 
} 

// Inherited class 
class Child extends Parent 
{ 
	// This method overrides show() of Parent 
	@Override
	void show() { System.out.println("Child's show()"); } 
} 

// Driver class 
class Main 
{ 
	public static void main(String[] args) 
	{ 
		// If a Parent type reference refers 
		// to a Parent object, then Parent's 
		// show is called 
		Parent obj1 = new Parent(); 
		obj1.show(); 

		// If a Parent type reference refers 
		// to a Child object Child's show() 
		// is called. This is called RUN TIME 
		// POLYMORPHISM. 
		Parent obj2 = new Child(); 
		obj2.show(); 
	} 
} 

```

Overriding and Access-Modifiers : The access modifier for an overriding method can allow more, but not less, access than the overridden method. For example, a protected instance method in the super-class can be made public, but not private, in the subclass. Doing so, will generate compile-time error.

```java
// A Simple Java program to demonstrate 
// Overriding and Access-Modifiers 

class Parent 
{ 
	// private methods are not overridden 
	private void m1() { System.out.println("From parent m1()");} 
	
	protected void m2() { System.out.println("From parent m2()"); } 
} 

class Child extends Parent 
{ 
	// new m1() method 
	// unique to Child class 
	private void m1() { System.out.println("From child m1()");} 
	
	// overriding method 
	// with more accessibility 
	@Override
	public void m2() { System.out.println("From child m2()");} 
	
} 

// Driver class 
class Main 
{ 
	public static void main(String[] args) 
	{ 
		Parent obj1 = new Parent(); 
		obj1.m2(); 
		Parent obj2 = new Child(); 
		obj2.m2(); 
	} 
} 


//From parent m2()
//From child m2()
```

Final methods can not be overridden : If we don’t want a method to be overridden, we declare it as final. Please see Using final with Inheritance .

```java
// A Java program to demonstrate that 
// final methods cannot be overridden 

class Parent 
{ 
	// Can't be overridden 
	final void show() { } 
} 

class Child extends Parent 
{ 
	// This would produce error 
	void show() { } 
} 

```

```
13: error: show() in Child cannot override show() in Parent
    void show() {  }
         ^
  overridden method is final
```

Private methods can not be overridden : Private methods cannot be overridden as they are bonded during compile time. Therefore we can’t even override private methods in a subclass.(See this for details).

The overriding method must have same return type (or subtype) : From Java 5.0 onwards it is possible to have different return type for a overriding method in child class, but child’s return type should be sub-type of parent’s return type. This phenomena is known as covariant return type.

Invoking overridden method from sub-class : We can call parent class method in overriding method using super keyword.

```java
// A Java program to demonstrate that overridden 
// method can be called from sub-class 

// Base Class 
class Parent 
{ 
	void show() 
	{ 
		System.out.println("Parent's show()"); 
	} 
} 

// Inherited class 
class Child extends Parent 
{ 
	// This method overrides show() of Parent 
	@Override
	void show() 
	{ 
		super.show(); 
		System.out.println("Child's show()"); 
	} 
} 

// Driver class 
class Main 
{ 
	public static void main(String[] args) 
	{ 
		Parent obj = new Child(); 
		obj.show(); 
	} 
} 

```

Overriding and constructor : We can not override constructor as parent and child class can never have constructor with same name(Constructor name must always be same as Class name).