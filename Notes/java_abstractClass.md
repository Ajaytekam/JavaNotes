## Java Abastract Classes

A class which is declared with the abstract keyword is known as an abstract class in Java. It can have abstract (only method, not implementation body) and non-abstract methods (method with the body).

Abstraction is a process of hiding the implementation details and showing only functionality to the user. Abstraction lets you focus on what the object does instead of how it does it. There are two ways to achieve abstraction in java :
* Abstract class (0 to 100%)
* Interface (100%)   

`abstract` keyword is used to create a abstract class and method. 
```java
abstract class TestClass {
	
	// an abstract method
	abstrat void method();
}
```
Abstract class in java can’t be instantiated. An abstract class is mostly used to provide a base for subclasses to extend and implement the abstract methods and override or use the implemented methods in abstract class. Some of the important points to note about Abstract class is :
* An abstract class must be declared with an abstract keyword.
* It can have abstract and non-abstract methods.
* It cannot be instantiated.
* It can have constructors and static methods also.
* It can have final methods which will force the subclass not to change the body of the method.

Example of Abstract class:
```java
abstract class TestClass {
	abstract void method1();
	abstract void method2();
}

class MyClass extends TestClass {

	void method1() {
		System.out.println("This is method1.");
	}

	void method2() {
		System.out.println("This is method2.");
	}

	public static void main(String args[]) {
		MyClass obj = new MyClass();
		obj.method1();
		obj.method2();
	}
}
```
Output:
```console
This is method1.
This is method2.
```
Another exmaple with concrete method.
```java
abstract class TestClass {

	// an abstract method
	abstract void method1();

	// method with body
	void method2() {
		System.out.println("This is method2.");
	}
}

class MyClass extends TestClass {
	// definig abstract method body
	void method1() {
		System.out.println("This is method1.");
	}

	public static void main(String args[]) {
		MyClass obj = new MyClass();
		obj.method1();
		obj.method2();
	}
}
```
Output:
```console
This is method1.
This is method2.
```

## Abstract class with Constructor data members and methods:

An abstract class can have a data member, abstract method, method body (non-abstract method), constructor, and even main() method. Example :
```java
abstract class TestClass {

	public float PI=3.14f;

	// abstract class constructor
	TestClass() {
		System.out.println("Construtor from abstractClass");
	}
	
	abstract float Area();
	abstract float Perimeter();
}

class Circle extends TestClass {
	private float radious;
	
	Circle(float r) {
		radious = r;
	}	

	float Area() {
		return(PI*(radious*radious));
	}

	float Perimeter() {
		return(2f*PI*radious);
	}		
}


class Ractangle extends TestClass {
	private float width;
	private float height;

	Ractangle(float w, float h) {
		width = w;
		height =  h;
	}

	float Area() {
		return(width*height);
	}

	float Perimeter() {
		return((width+height)*2);
	}
}

class MyClass {

	public static void main(String args[]) {
		Ractangle rt = new Ractangle(5.3f, 2.5f);
		Circle cr = new Circle(2.5f);

		System.out.println("Circle Area: "+cr.Area());
		System.out.println("Circle Perimeter: "+cr.Perimeter());
		System.out.println("Ractangle Area: "+rt.Area());
		System.out.println("Ractangle Perimeter: "+rt.Perimeter());
	}
}
```
Output:
```console
Construtor from abstractClass
Construtor from abstractClass

Circle Area: 19.625
Circle Perimeter: 15.700001
Ractangle Area: 13.25
Ractangle Perimeter: 15.6
```
