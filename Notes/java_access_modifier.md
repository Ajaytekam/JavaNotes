## Java Access Modifiers

The access modifiers in Java specifies the accessibility or scope of a field, method, constructor, or class. We can change the access level of fields, constructors, methods, and class by applying the access modifier on it. There are four types of access modifiers available in java:

**1. Default (No keyword required)**   
**2. Private**    
**3. Protected**   
**4. Public**   


**The scope of access modifiers:**
|Access specifier | Class | Package | Subclass(same package) | Subclass (diff package) | Outside |
------------|-------|---------|--------------|--------------|-------|
**private**     | Yes   |  No     |    No        |    No        |   No  |
**default**     | Yes   |  Yes    |    Yes       |    No        |   No  |
**public**      | Yes   |  Yes    |    Yes       |    Yes       |   Yes |    
**protected**   | Yes   |  Yes    |    Yes       |    Yes       |   No  |    

**Note:** At above table subclass means child-class.  
 
**1. Private :** The private access modifier is specified using the keyword private. The methods or data members declared as private are accessible only within the class in which they are declared. Any other class of same package will not be able to access these members. Top level Classes or interface can not be declared as private because private means “only visible within the enclosing class” and protected means “only visible within the enclosing class and any subclasses”. However, inner-classes in the case of a nested class can be declared private.  

Example of private method :
```java
class Test1 {
	// private members
	private String str = "This is Private Sting.";
	private int x;
	private int y;

	Test1(int a, int b) {
		x = a;
		b = b;
	}	

	// private method
	private int add() {
		return (x+y);
	}

	public void ShowData() {
		System.out.println(str);
		System.out.println(add());
	}
}

public class MyClass {
	public static void main(String args[]) {
		Test1 obj = new Test1(10, 20);
		obj.ShowData();
	}
}
```
Output:
```console
This is Private Sting.
10
```

Note : Top level Classes or interface can not be declared as private, only inner-classes of a nested class can be declared as private.  

Example of Java-Inner class with private access modifier. Creating an inner class is quite simple. We just need to write a class within a class. Unlike a class, an inner class can be private and once we declare an inner class private, it cannot be accessed from an object outside the class.

```java
class Test1 {
	// inner class
	private class InnerClass {
		public void show() {
			System.out.println("Hello world");
			System.out.println("This is Private InnerClass");
		}
	}

	// accessing the innerClass from within 
	// the outerclass method
	public void displayMsg() {
		InnerClass obj = new InnerClass();
		obj.show();
	}
}

class PClass {
	public static void main(String args[]) {
		Test1 ob = new Test1();	
		ob.displayMsg();
	}
}
```
Output:
```console
Hello world
This is Private InnerClass
```

**2. default :**  When no access specified for a class, variable, method or constructor, then by default, it is assumed to be a default access modifier. The scope of this modifier is limited to the package only. This means that if we have a class with the default access modifier in a package, only those classes that are in this package can access this class. No other class outside this package can access this class. Similarly, if we have a default method or data member in a class, it would not be visible in the class of another package. 

Example :
```java
// declaring package 
package defaultPackage;

class Logger {
    void message(){
        System.out.println(“This is a message”);
    }
}
```
Here, `Logger` class has the default access modifier. And this `logger` class is visible to the classes that belong to the `defaultPackage` package. If you import `Logger` class in different package and try to instantiate it, you’ll get compilation error.   
   
**3. public :** The public access modifier is accessible everywhere. It has the widest scope among all other modifiers. Public access modifier has no any scope restriction. The public access modifier can be applied to classes and interfaces along with methods, data members and variables. Example :
```java
// Test1.java
public class Test1 {
	public void displayMsg() {
		System.out.println("Hello world");
	}
}

// PClass.java
public class PClass {
	public static void main(String args[]) {
		Test1 ob = new Test1();	
		ob.displayMsg();
	}
}
// note : compile both file saparately
```
Output :
```console
Hello world
```

**4. protected :** Protected data member and method are only accessible by the classes of the same package and the subclasses present in any package. You can also say that the protected access modifier is similar to default access modifier with one exception that it has visibility in sub classes from different package. Classes cannot be declared protected. Example :   
**File: /tesp/Test1.java**
```java
package testp;

public class Test1 {
	protected void message() {
		System.out.println("This is protected function from anoter package.");
	}
}
``` 
The above file is belong to package `testp`  
**File: MyClass.java**
```java
import testp.Test1;

public class MyClass extends Test1 {
	public static void main(String args[]) {
		MyClass ob = new MyClass();
		ob.message();
	}
}
```
The above class inherits the Test1 class from a package, thus the function message() from class Test1 is protected mode, so we can access it from here. (because protected elements can be accessed by subclass from different package or outside from package.)
