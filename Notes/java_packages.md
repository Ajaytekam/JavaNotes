## Java Packages :

A package is nothing but a pack/group of classes, interfaces and other packages. In java the packages are used to organize our classes and interfaces. Therer are two types of packages in java :  

**1. Built-in Package**
**2. User-Defined Package**

**1. Built-in Package** : The already defined package like java.io.*, java.lang.* etc are known as built-in packages. In java we have several built-in packages, for example, to take user input we have to import `Scanner` class from `java.util` package,
```java
import java.util.Scanner;
```
Where:
* `java` is a top level package
* `util` is a sub package
* `Scanner` is a class which is present in the sub package util


**2. User-Defined Package** : The packages created by the user or defined by the user is known as user-defined package.

### Creating Java packages :

* To create a java packge first create a directory/folder on the name of package. For eaxmple we are going to create a package named `calculate`. 

* Now inside the directory we need to create java class files which are nothing but the class library contained by package 'calulate'. 

* Inside 'calculate' we created two class 'Ractangle.java' and 'Circle.java'.   

Filename: Ractangle.java
```java
package calculate;

public class Ractangle {
	double height;
	double width;

	public Ractangle(double h, double w) {
		height = h;
		width = w;
	}

	public void Area() {
		System.out.println(width*height);
	}

	public void Perimeter() {
		System.out.println(2*(width*height));
	}
}
```

Filename: Circle.java
```java
package calculate;

public class Circle {
	double radious;
	double pi = 3.14;

	public Circle(double r) {
		radious = r;
	}

	public void Area() {
		System.out.println(pi*(radious*radious));
	}

	public void Perimeter() {
		System.out.println(2*(pi*radious));
	}
}
```

At above code the 1st line `package caculate;` simply declares the package, or from which packge the class will belongs to. Now the structure of our package `calculate wil look like`   
```console
calclate
  |
  |----- Ractangle.java
  |----- Circle.java
```

**Using the packages within the programs:** 

**Example1:**
```java
import calculate.Circle;

class MyClass {
	public static void main(String args[]) {
		Circle c1 = new Circle(2.5);
		c1.Area();
		c1.Perimeter();
	}
}
``` 
Output:
```console
19.625
15.70001
``` 
The above example include only `Circle` class from the package.   

**Example2:**
```java
import calculate.Ractangle;

class MyClass {
	public static void main(String args[]) {
		Ractangle r1 = new Ractangle(2.5, 3.5);
		r1.Area();
		r1.Perimeter();
	}
}
```
output:
```console
8.75
17.5
```
The above example imports only `Ractangle` class from package.    

**Eaxmple3:** Importing Both packages at the same time.   
```java
import calculate.*;

class MyClass {
	public static void main(String args[]) {
		Circle c1 = new Circle(2.5);
 	    c1.Area();
        c1.Perimeter();

		Ractangle r1 = new Ractangle(2.5, 3.5);
		r1.Area();
		r1.Perimeter();
	}
}
```
Output:
```console
19.625
15.70001
8.75
17.5
```

**Example4:** Importing package classes with fully qualified name. 
```java
class MyClass {
	public static void main(String args[]) {
	
		// importing fully qualified domain name
		calculate.Circle c1 = new calculate.Circle(2.5);
 	    c1.Area();
        c1.Perimeter();

		// importing fully qualified domain name (same as above)
		calculate.Ractangle r1 = new calculate.Ractangle(2.5, 3.5);
		r1.Area();
		r1.Perimeter();
	}
}
```

### Creating a class inside package while importing another package 

package class file : `Ractangle.java`
```java
i// Declaring package
package calculate;

// importing built-in Scanner libraray
import java.util.Scanner;

public class Ractangle {
	double height;
	double width;

	public Ractangle(double h, double w) {
		height = h;
		width = w;
	}

	public Ractangle() {
		Scanner ob = new Scanner(System.in);
		System.out.println("Enter Height: ");
		height = ob.nextDouble();
		System.out.println("Enter Width: ");
		width = ob.nextDouble();
	}

	public void Area() {
		System.out.println(width*height);
	}

	public void Perimeter() {
		System.out.println(2*(width*height));
	}
}
```

Implementing above package into a program

```java
import calculate.Ractangle;

class MyClass {
	public static void main(String args[]) {

		// calling defferent constructor at both
		// initializaions of objects
		Ractangle r1 = new Ractangle(2.5, 3.5);
		r1.Area();
		r1.Perimeter();

		Ractangle r2 = new Ractangle();
		r2.Area();
		r2.Perimeter();
	}
}
```
Output:
```console
8.75
17.5
Enter Height: 
3.5
Enter Width: 
1.5
5.25
10.5
```

### Sub packages in Java :

A package inside another package is known as sub package. For example we can create another package `simpleMath` inside the packagei Calculate. The package `simpleMath` has three classes `Addition`, `Subtraction` and `Multiplication`. 
```console
calclate
  |
  |----- Ractangle.java
  |----- Circle.java
  |----- simpleMath (sub-package/directory)
			|
			|----- Addition.java
			|----- Multiplication.java
			|----- Subtraction.java
```
The codes for new classes from sub-package `simpleMath` are :  

**File: Addition.java**
```java
package calculate.simpleMath;

public class Addition {
	
	public void Add(int x, int y) {
		System.out.println(x+y);
	}

	public void Add(float x, float y) {
		System.out.println(x+y);
	}
}
```

**File: Subtraction.java**
```java
package calculate.simpleMath;

public class Subtraction {
	
	public void Sub(int x, int y) {
		System.out.println(x-y);
	}

	public void Sub(float x, float y) {
		System.out.println(x-y);
	}
}
```

**File: Multiplication.java**
```java
ipackage calculate.simpleMath;

public class Multiplication {
	
	public void Multi(int x, int y) {
		System.out.println(x*y);
	}

	public void Multi(float x, float y) {
		System.out.println(x*y);
	}
}
```

### Implementing the above classes in a program :

Example1 : Importing a single class `Addition`
```java
import calculate.simpleMath.Addition;

class MyClass {
	public static void main(String args[]) {
		Addition a1 = new Addition();
		a1.Add(10, 20);
		a1.Add(2.3f, 5.6f);
	}
}
```
Output:
```console
30
7.8999996
```

Example2 : Importing all sub-classes
```java
import calculate.simpleMath.*;

class MyClass {
	public static void main(String args[]) {
		// addition class
		Addition a1 = new Addition();
		a1.Add(10, 20);
		a1.Add(2.3f, 5.6f);

		// Multiplication class
		Multiplication m1 = new Multiplication();
		m1.Multi(2, 5);
		m1.Multi(2.5f, 5.2f);

		// Subtraction class
		Subtraction s1 = new Subtraction();
		s1.Sub(10, 5);
		s1.Sub(10.5f, 5.10f);
	}
}
```
Output
```console
30
7.8999996
10
13.0
5
5.4
```
