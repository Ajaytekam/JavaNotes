## Classes in Java

A class is a template or blueprint from which objects are created and an object is the instance(result) of a class. It is a logical entity. A class in Java can contains Fields, Methods, Constructors, Blocks, Nested class and interface. 

**Object** : An entity that has state and behavior is known as an object, where state represnets the value/data of an object and behavior represent functionality/methods of an object. An object is a physical entity. Some important points of class objects are :
* An object is a real-world entity.
* An object is a runtime entity.
* The object is an entity which has state and behavior.
* The object is an instance of a class.

### Declaring class

Class Structure:
```java
class <class_name> {
	// class variables 
	// class methods
}
```
Example :
```java
import java.util.*;

class TestClass {
    // class variables
    int x;
    String s = "Hello world";

    // class methods
    public void printValue() {
    	System.out.println("Number: "+x);
    	System.out.println("String: "+s);
	}   

	public static void main(String args[]) {

		// creating object from a class
		TestClass t1 = new TestClass();

		// calling class method by object
		t1.printValue();
	}
}
```
**Output:**
```console
Number: 0
String: Hello world
```
The variable `x` value is 0 because we would not assign any value to it, so by default its value is zero. We can also change the values of class variables by using reference varible, for example :
```java
t1.x = 12;
t1.s = "Hello world Ajay";
```
Because these variables are withn default access mode.

### Object Creation :

The objects are created by using `new` keyword. The syntax is :
```java
<classname> <object_name> = new <classname>();
```
Example :
```java
TestClass obj1 = new TestClass();
```
Also note that in the bracket `( )`, the parameters are provided to initialize the values of class variables if constructors are declared in the class.

### this keyword :

The this keyword can be used to refer current class instance variable. If there is ambiguity between the instance variables and parameters, this keyword resolves the problem of ambiguity.
    
  
**Some example :**

Example 1:
```java
import java.util.*;

class Profile { 
	String name;
    String city;
	int age;

	public void setValue(String name, String city, int age) {
		this.name = name;
		this.city = city;
		this.age = age;
	}

    public void printValue() {
    	System.out.println("Name: "+name);
    	System.out.println("Age: "+age);
    	System.out.println("City: "+city);
	} 
}

class MyClass {
	public static void main(String args[]) {
		Profile p1 = new Profile();
		Profile p2 = new Profile();

		p1.setValue("Ajay kumar", "Bilaspur", 25);
		p2.setValue("Bruce Wayne", "Gothom", 49);
		
		p1.printValue();
		p2.printValue();
	}
}
```
Output:
```console
Name: Ajay kumar
Age: 25
City: Bilaspur

Name: Bruce Wayne
Age: 49
City: Gothom
```
