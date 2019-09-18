# Java Interfaces 

The interface in Java is a mechanism to achieve abstraction. Like a class, an interface can have methods and variables, but the methods declared in interface are by default abstract (only method signature, no body). It is used to achieve abstraction and multiple inheritance in Java.

### Some important points about interfaces :

* A Java class can implement multiple Java Interfaces. It is necessary that the class must implement all the methods declared in the interfaces.
* If a class implements an interface and does not provide method bodies for all functions specified in the interface, then class must be declared abstract.
* All methods in an interface are implicitly public and abstract.An interface cannot be instantiated.
* An interface reference can point to objects of its implementing classes.
* An interface can extend from one or many interfaces. Class can extend only one class but implement any number of interfaces.
* An interface cannot implement another Interface. It has to extend another interface if needed.
* An interface which is declared inside another interface is referred as nested interface. 
* At the time of declaration, interface variable must be initialized. Otherwise, the compiler will throw an error.
* The class cannot implement two interfaces in java that have methods with same name but different return type.

### Declaring Interfaces

An interface is declared by using the interface keyword.
```java
interface <interface_name> {
	// declare constant variables
	// and
	// declare abstract method (body only)
}
```
Example :
```java
interface Calculate {
	float PI = 3.14;
	public float Area();
	public float perimeter();
}
```
Using interfaces in class with the `implements` keyword.
```java
import java.util.*;

interface Calculate {
    double PI = 3.14;
    public double Area();
    public double perimeter();
}

class Circle implements Calculate {
	double radious;
	Circle(double r) {
		this.radious = r;
	}

  	public double Area() {
		return(PI*this.radious*this.radious);
	}

	public double perimeter() {
		return(2*PI*this.radious);
	}
}


class Ractangle implements Calculate {
	double height, width;
	Ractangle(double w, double h) {
		this.width = w;
		this.height = h;
	}

  	public double Area() {
		return(this.width*this.height);
	}

	public double perimeter() {
		return(2*(this.width*this.height));
	}
}

class MyClass {

	public static void main(String args[]) {
		Ractangle rtl = new Ractangle(2.5, 3.5);
		Circle crl = new Circle(2.5);
		System.out.println("Area of Circle: "+rtl.Area());
		System.out.println("Perimeter of Cirle: "+crl.perimeter());
		System.out.println("Area if Ractangle: "+crl.Area());
		System.out.println("Perimeter if Ractangle: "+crl.perimeter());
	}
}
```
Output :
```console
Area of Circle: 8.75
Perimeter of Cirle: 15.700000000000001
Area if Ractangle: 19.625
Perimeter if Ractangle: 15.700000000000001
```

Another simple example :
```java
import java.util.*;

interface test1 {
	public void method1();
	public void method2();
}

class MyClass implements test1 {

	public void method1() {
		System.out.println("This is method1");
	}


	public void method2() {
		System.out.println("This is method2");
	}

	public static void main(String args[]) {
		MyClass m1 = new MyClass();
		m1.method1();	
		m1.method2();	
	}
}
```
**Output :**
```java
This is method1
This is method2
```

### Extending interfaces :

an interface can extends to another enterface. Example :
```java
iimport java.util.*;

interface Test1 {
	public void method1();	
}

interface Test2 extends Test1 {
	public void method2();	
}


class MyClass implements Test2 {

	public void method1() {
		System.out.println("This is method1");
	}
	
	public void method2() {
		System.out.println("This is method2");
	}

	public static void main(String args[]) {
		MyClass obj = new MyClass();
		obj.method1();
		obj.method2();
	}
}
```
    
### Multiple Interfaces

Implementing multiple interface in single class. Example :
```java
import java.util.*;

interface Test1 {
	public void method1();	
}

interface Test2 {
	public void method2();	
}

class MyClass implements Test1, Test2 {

	public void method1() {
		System.out.println("This is method1");
	}
	
	public void method2() {
		System.out.println("This is method2");
	}

	public static void main(String args[]) {
		MyClass obj = new MyClass();
		obj.method1();
		obj.method2();
	}
}
```

## Difference Between Java Classes and Interfaces

* A class can be instantiated by creating its objects. An interface is never instantiated as the methods declared inside an interface are abstract and does not perform any action, so there is no use of instantiating any interface.
* A class is declared using a keyword ‘class’. In the same way, an interface is created using a keyword ‘interface’.
* The members of a class can have the access specifier like public, private, protected. But the members of an interface are always public as they have to be accessed by the classes implementing them.
* The methods inside a class are defined to perform an action on the fields declared in the class. As interface lacks in the declaration of fields, the methods inside an interface are purely abstract.
* A class can implement any number of interfaces but can extend only one super class. An interface can extend any number of interfaces but can not implement any interface.
* A class has constructors defined inside it to get the variable initialized. But, an interface does not have any constructors as there are no fields to be initialized. The fields of an interface are initialized at the time of their declaration only.

## Note: After java 8, the default and static methods can be added onto the interfaces.

**Example : Interface with default method :**
```java
interface Test1 {
	default void method() {
		System.out.println("This is default method.");
	}
}

class DefaultM implements Test1 {

	public static void main(String args[]) {
		DefaultM ob = new DefaultM();
		ob.method();
	}
}
```
Output:
```console
This is default method.
```
**Example : Interface with default method :**

To call a static method of an interface, we just need to put interface name with static method name. 
```java
Interface.static_method();
```
Example :
```java
interface Test1 {
	static void method() {
		System.out.println("This is static ethod.");
	}
}

class DefaultM implements Test1 {

	public static void main(String args[]) {
		Test1.method();
	}
}
```
Output:
```console
This is static method.
```
