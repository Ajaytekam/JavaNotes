## Lambda Expressions

Lambda expression is a new and important feature of Java which was included in Java SE 8. It provides a clear and concise way to represent one method interface using an expression. It is very useful in collection library. It helps to iterate, filter and extract data from collection.

## Functional Interface

Lambda expression provides implementation of functional interface, a function that doesn’t have a name and doesn’t belong to any class. The fuctional interface needs lees coding to create a function. The main difference between Lambda expression and Functional interface is that a normal method/function in java hase four parts : Name, parameter list, body and return type but in lambda expression only two part needed body and parameter list. 

Syntax for Java Lambda Expression :
```java
(argument-list) -> { body }
```
Where :   
* **argument-list** can be empty or non-empty.
* **arrow-token** is used to link arguments-list and body of expression.
* **body** contains expressions and statements for lambda expression.

### Example of Lambda Expressions :

* Lambda expressions with no parameter.
```java
// ShowMsg() is implemented using lambda expressions
interface TestL {
	public void ShowMsg();
}

class LambdaTest {
	public static void main(String args[]) {

		// lambda expression
		TestL m = ()-> System.out.println("This is Test Message.");
	   	m.ShowMsg();
	}	
}
```
Output:
```console
This is Test Message.
```
Another implementation. It basically return string :
```java
interface TestL {
	public String ShowMsg();
}

class LambdaTest1 {
	public static void main(String args[]) {
		TestL m = ()-> {
			return "This is Another Test.";
		};

	   	System.out.println(m.ShowMsg());
	}	
}
```
Output:
```console
This is another Test.
```
We can also put interface definition inside class.
```java
class LambdaTest1 {

	interface TestL {
	 	String ShowMsg();
    }

	public static void main(String args[]) {
		TestL m = ()-> {
			return "This is Another Test.";
		};

	   	System.out.println(m.ShowMsg());
	}	
}
```
* Lambda expressions with single parameter.
```java
interface TestL1 {
	int square(int num);
}

interface TestL2 {
	void Message(String str);
}

class LambdaTest {
	public static void main(String args[]) {
		TestL1 n1 = (a)->(a*a);
		System.out.println(n1.square(10));
		System.out.println(n1.square(5));
		System.out.println(n1.square(20));

		TestL2 m1 = (s)->{System.out.println("Hello "+s);};

		m1.Message("Ajay");
		m1.Message("John");

	}	
}
```
Output:
```console
100
25
400

Hello Ajay
Hello John
```
* Lambda expressions with Multiple parameter.
```java
class LambdaTest {

	// defining lembda expression implementation
	interface TestL1 {
	 	int operate(int a, int b);
    }

	interface TestL2 {
		void print(String name, int age);
	}

	public static void main(String args[]) {

		// definig lembda expression
		TestL1 add = (a, b)->(a+b);
		TestL1 sub = (a, b)->(a-b);
		TestL1 div = (a, b)->(a/b);
		
	   	System.out.println(add.operate(10,20));
	   	System.out.println(sub.operate(10,20));
	   	System.out.println(div.operate(40,10));

		TestL2 pt = (name, age)->{
				System.out.println("Name: "+name);
				System.out.println("Age: "+age);
		};

		pt.print("Ajay kumar", 25);
		pt.print("John Doe", 50);
	}	
}
```
Output:
```console
30
-10
4

Name: Ajay kumar
Age: 25
Name: John Doe
Age: 50
```

### Lambda Expression : Foreach Loop
Example 1:
```java
import java.util.*;

class forEachDemo {
	public static void main(String args[]) {
		List<String> list = new ArrayList<String>();
		list.add("Ajay Kumar");
		list.add("Bruce Wayne");
		list.add("Ramesh Kumar");
		list.add("John Snow");
		list.add("Sumesh Kumar");

		list.forEach((name)-> System.out.println(name));
	}
}
```
Output:
```console
Ajay Kumar
Bruce Wayne
Ramesh Kumar
John Snow
Sumesh Kumar
```
Example 2:
```java
mport java.util.*;

class forEachDemo {
	public static void main(String args[]) {
		List<Integer> num = new ArrayList<Integer>();
	  	// add 1 to 20 into Arraylist
		for(int i=1;i<=20;i++) {
			num.add(i);
		}

		// print only even numbers
		num.forEach(
			(n)->{if(n%2==0) System.out.println(n);}
		);
	}
}
```
Output:
```console
2
4
6
8
10
12
14
16
18
20
```
