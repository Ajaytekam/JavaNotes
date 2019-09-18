## Java Methods

 In Java, every method must be part of some class which is different from languages like C, C++, and Python. The syntax of method declaration in java is as follows :
```java
<modifier> <return-type> method-name(parameter list, ...) {
	// method body
	...
	...
}
```
Example:
```java
public int add(int x, int y) {
	return(x+y);
}
```
**As we can see the method declaration has six components :**

**1. Modifier:** Defines access type of the method i.e. from where it can be accessed in application. In Java, there 4 type of the access specifiers:
* `public` : accessible in all class in your application.
* `protected` : accessible within the class in which it is defined and in its subclasses(inherited).
* `private` : accessible only within the class in which it is defined.
* `default` (declared/defined without using any modifier) : accessible within same class and package within which its class is defined. 

                   
**2. The return type :** The data type of the value returned by the method or void if does not return a value.  
**3. Method Name :** Name of defined method.  
**4. Parameter list :** Comma separated list of the input parameters are defined, preceded with their data type, within the enclosed parenthesis. If there are no parameters, you must use empty parentheses ().    
**5. Method body :** it is enclosed between braces. The code you need to be executed to perform your intended operations.    
**6. Method signature :** It consists of the method name and a parameter list (number of parameters, type of the parameters and order of the parameters). The return type and exceptions are not considered as part of it.Method Signature of above function: 
```java
add(int a, int b);
```
Example code :
```java
import java.util.*;

class MyClass {

	public int add(int x, int y) {
		return(x+y);
	}

	public int multi(int x, int y) {
		return(x*y);
	}

	public static void main(String args[]) {
		MyClass ob = new MyClass();
		System.out.println(ob.add(10, 20));
		System.out.println(ob.multi(10, 20));

	}
}
```
Output:
```console
30
200
```
## Method Overloading

If two or more method in a class have same name but different parameters, it is known as method overloading. Overloading always occur in the same class(unlike method overriding).

Method overloading is one of the ways through which java supports polymorphism. Method overloading can be done by changing number of arguments or by changing the data type of arguments. If two or more method have same name and same parameter list but differs in return type are not said to be overloaded method

Note: Overloaded method can have different access modifiers.

**Different ways of Method overloading :**

There are two different ways of method overloading:
    
* Method overloading by changing data type of Arguments.
```java
import java.util.*;

class Calculate {
	public void add(int x, int y) {
		System.out.println(x+y);
	}

	public void add(float x,float y,float z) {
		System.out.println(x+y+z);
	}
}

class MyClass {
	public static void main(String args[]) {
		Calculate obj = new Calculate();
	  	obj.add(5, 10);
		obj.add(5.2f, 4.3f, 15.3f);
	}
}
```
Output:
```console
15
24.8
```
* Method overloading by changing no. of argument.
```java
import java.util.*;

class Calculate {
	public void add(int x, int y) {
		System.out.println(x+y);
	}

	public void add(int x, int y, int z) {
		System.out.println(x+y+z);
	}
}

class MyClass {
	public static void main(String args[]) {
		Calculate obj = new Calculate();
	  	obj.add(5, 10);
		obj.add(5, 10, 15);
	}
}
```
Output:
```console
15
30
```
