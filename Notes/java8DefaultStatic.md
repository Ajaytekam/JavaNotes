## Default and Static methods in Java 8 Interfaces

Prior to java 8, interface in java can only have abstract methods. All the methods of interfaces are public & abstract by default. Java 8 allows the interfaces to have default and static methods. The reason we have default methods in interfaces is to allow the developers to add new methods to the interfaces without affecting the classes that implements these interfaces.

Designing interfaces have always been a tough job because if we want to add additional methods in the interfaces, it will require change in all the implementing classes. As interface grows old, the number of classes implementing it might grow to an extent that it’s not possible to extend interfaces. That’s why when designing an application, most of the frameworks provide a base implementation class and then we extend it and override methods that are applicable for our application.

We can say that concept of default method is introduced in java 8 to add the new methods in the existing interfaces in such a way so that they are backward compatible. Backward compatibility is adding new features without breaking the old code.


### Default method :

For creating a default method in java interface, we need to use “default” keyword with the method signature.
```java
interface Test1 {
	
	void display(String str);

    default void method() {
        System.out.println("This is default method.");
    }
}

class DefaultM implements Test1 {

	public void display(String str) {
		System.out.println(str);
	}

    public static void main(String args[]) {
        DefaultM ob = new DefaultM();
        ob.method();
		ob.display("redefined interface method");
    }
}
```
Output:
```console
This is default method.
redefined interface method
```
#### Overriiding default method :
```java
interface Test1 {
	
	void display(String str);

    default void method() {
        System.out.println("This is default method.");
    }
}

class DefaultM implements Test1 {

	public void display(String str) {
		System.out.println(str);
	}


    public void method() {
        System.out.println("Override default method.");
    }

    public static void main(String args[]) {
        DefaultM ob = new DefaultM();
        ob.method();
		ob.display("redefined interface method");
    }
}
```
Output:
```console
Override default method.
redefined interface method
```

### Static method :

Static methods in interfaces are similar to the default methods except that we cannot override these methods in the classes that implements these interfaces. The static methods contain the complete definition of the function. To use a static method, Interface name should be instantiated with it.
```java
interface Test1 {
    static void method() {
        System.out.println("This is static method.");
    }
}

class StaticM implements Test1 {

    public static void main(String args[]) {
        Test1.method();
    }
}
```
Output:
```console
This is static method.
```
The static method defines in Interface hello(), cannot be overridden in implementing the class. However, if the method with same name is implemented in the implementation class then that method becomes a static member of that respective class. Example :
```java
iinterface Test1 {
    static void method() {
        System.out.println("This is static method from interface.");
    }
}

class StaticM implements Test1 {

	static void method() {	
        System.out.println("This is static method from Main Class.");
	}

    public static void main(String args[]) {
		// calling interface static method
        Test1.method();

		// calling class static method
		method();
    }
}
```
Output:
```console
This is static method from interface.
This is static method from Main Class.
```

 
