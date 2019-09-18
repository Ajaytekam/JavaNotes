## Java Class Inheritence

In Java, it is possible to inherit attributes and methods from one class to another, and this concept is known as inheritence. It is an important part of OOPs. 

The idea behind inheritance in Java is that we can create new classes that are built upon existing classes. When we inherit from an existing class, we can reuse methods and fields of the parent class. Moreover, we can add new methods and fields in the current class also. 

### Inheritance in java provides :
* Method Overriding (so runtime polymorphism can be achieved).
* Code Reusability.

**Syntax:**
```java
class <sub_class_name> extends <super_class_name> {
	// methods and fields
	//
}
```
Where:   
* `Sub Class` : Subclass is a class which inherits the other class. It is also called a derived class, extended class, or child class.
* `Super Class` : Superclass is the class from where a subclass inherits the features. It is also called a base class or a parent class.
* `extends` : It indicates that you are making a new class that derives from an existing class. The meaning of "extends" is to increase the functionality.   

In the terminology of Java, a class which is inherited is called a superclass, and the new class is called subclass.

**Example of Java Inheritence :**  

Example1:
```java
class profile {
	String name;
	int age;
}

class student extends profile {
	String stndrd;

	student(String n, int a, String s) {
		name = n;
		age = a;
		stndrd = s;	
	}

	void show() {
		System.out.println("Name: "+name);
		System.out.println("Age: "+age);
		System.out.println("Standard: "+stndrd);
	}
}

class Single {
	public static void main(String args[]) {
		student s1 = new student("Ajay kumar", 25, "MCA-III");
		s1.show();
	}
}
```
Output:
```console
Name: Ajay kumar
Age: 25
Standard: MCA-III
```
At above there is a super-class named `profile` and a sub-class named `student`.

## Types of inheritance in java :

**1. Single Inheritence :** Single inheritance refers to a child and parent class relationship where a class extends the another class. The previous java code is an exmaple of single inhritence. 
```console
		ClassA
		  ^
		  |
	      |
	      |
		ClassB


Fig: Single Inheritence
```
**2. Multilevel Inheritence :** Multileve inheritence refers to a child and parent class relationship where a class extends the child class. For example class C extends class B and class B extends class A.
```console
		ClassA
		  ^
		  |
	      |
	      |
		ClassB
		  ^
		  |
		  | 
		  |
		ClassC

Fig: Multilevel Inheritence
```
Example :
```java
class profile {
	String name;
	int age;
}

class student extends profile {
	String stndrd;

	student(String n, int a, String s) {
		name = n;
		age = a;
		stndrd = s;	
	}

	void show() {
		System.out.println("Name: "+name);
		System.out.println("Age: "+age);
		System.out.println("Standard: "+stndrd);
	}
}

class result extends student {
	int marks;
	static final int total_marks = 700;
	result(String n, int a, String s, int mr) {
		super(n, a, s);
		marks = mr;
	}

	void show() {
		System.out.println("Name: "+name);
		System.out.println("Age: "+age);
		System.out.println("Standard: "+stndrd);
		System.out.println("marks: "+marks+"/"+total_marks);
	}
}

class Single {
	public static void main(String args[]) {
		result r1 = new result("Ajay kumar", 25, "MCA-III", 555);
		r1.show();
	}
}
```
Output:
```console
Name: Ajay kumar
Age: 25
Standard: MCA-III
marks: 555/700
```
**3. Hierarchical Inheritence :** Hierarchical inheritence refers to a child and parent class relationship where more than one classes extends the same class. For example, classes B, C extends the same class A.

```console
        ClassA
		   ^
		  / \
	     /   \
	    /     \
       /       \
      /         \
  ClassB      ClassC

Fig: Hierarchical Inheritence
```
Example:

```java
class whicle {
	int price;
	String model;
	int miledge;
}

class bikes extends whicle {
 	String type = "MotorBike";
	bikes(int p, String ml, int m) {
		price = p;
		model = ml;
		miledge = m;
	}

	public void show() {
		System.out.println("Type: "+type);
		System.out.println("Price: "+price);
		System.out.println("Model: "+model);
		System.out.println("Miledge: "+miledge);
	}
}


class cars extends whicle {
 	String type = "Cars";
	cars(int p, String ml, int m) {
		price = p;
		model = ml;
		miledge = m;
	}

	public void show() {
		System.out.println("Type: "+type);
		System.out.println("Price: "+price);
		System.out.println("Model: "+model);
		System.out.println("Miledge: "+miledge);
	}
}

class MyClass {
	public static void main(String args[]) {
		bikes b1 = new bikes(60000, "Pulser 135", 55);
		cars c1 = new cars(350000, "Maruti Alto", 22);
		b1.show();
		c1.show();
	}
}
```
Output:
```console
Type: MotorBike
Price: 60000
Model: Pulser 135
Miledge: 55

Type: Cars
Price: 350000
Model: Maruti Alto
Miledge: 22
```
