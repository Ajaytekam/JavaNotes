## Java Constructor :


A constructor in Java is a special method that is used to initialize objects. The constructor is called when an object of a class is created. It can be used to set initial values for object attributes:

**Rules for Creating Java Constructor** :
* Constructor name must be the same as its class name.
* A Constructor must have no explicit return type.
* A Java constructor cannot be abstract, static, final, and synchronized.

All classes have constructors by default: if you do not create a class constructor yourself, Java creates one for you, which do nothing but sets all the member valriabls values to default.

### There are three types of Java Constructors :
* Default Constructor (no-arg constructor)
* Parameterized Constructor

### Default Constructor (no-arg constructor) 

Default constructor does not have any argument in it. Syntax :
```java
<class_name>() {
	// Statement to execute 
}
```
Example :
```java
iclass DefConst {

	DefConst() {
		System.out.println("Default constructor is called");
	}

	public static void main(String args[]) {
		DefConst obj1 = new DefConst();
		DefConst obj2 = new DefConst();
	}
}
```
Output :
```console
Default constructor is called
Default constructor is called
```
The default constructor is called twice because two objects are created.

### Parameterized Constructor :

A constructor which has a specific number of parameters is called a parameterized constructor. Syantax :
```java
<class_name>(parameter_list...) {
	// Statement to execute 
}
```
Example :
```java
class ParConst {
	private int x;
	private int y;

	ParConst(int x, int y) {
		System.out.println("Parameterized constructor is called");
		this.x = x;
		this.y = y;
	}

	void showValues() {
		System.out.println("X:"+x);
		System.out.println("Y:"+y);
	}

	public static void main(String args[]) {
		ParConst obj1 = new ParConst(5, 6);
		obj1.showValues();
		ParConst obj2 = new ParConst(10, 20);
		obj2.showValues();
	}
}
```
Output :
```console
Parameterized constructor is called
X:5
Y:6
Parameterized constructor is called
X:10
Y:20
```

## Constructor overloading :

In java constructors can be overloaded like methods. onstructor overloading in Java is a technique of having more than one constructor with different parameter lists. They are arranged in a way that each constructor performs a different task. They are differentiated by the compiler by the number of parameters in the list and their types. Examle :
```java
class ConstOver {
	public int x=1;
	public int y=1;

	// default constructor
	ConstOver() {
		System.out.println("This is default constructor");
		System.out.println(add());
	}

	// parameterized constructor with 
	// one argument
	ConstOver(int x) {
		this.x = x;
		System.out.println("Parameterized constructor with one args");
		System.out.println(add());
	}

	// parameterized constructor with 
	// two argument
	ConstOver(int x, int y) {
		this.x = x;
		this.y = y;
		System.out.println("Parameterized constructor with two args");
		System.out.println(add());
	}

	private int add() {
		return x+y;
	}

	public static void main(String args[]) {
		ConstOver obj1 = new ConstOver();	
		ConstOver obj2 = new ConstOver(10);	
		ConstOver obj3 = new ConstOver(10, 20);	
	}
}
```
Output:
```console
This is default constructor
2
Parameterized constructor with one args
11
Parameterized constructor with two args
30
```
