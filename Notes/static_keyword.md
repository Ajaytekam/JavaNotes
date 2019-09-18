## Use of Static keyword in Java

The Java, static keyword is used within variables, methods, blocks and nested class. Anything which is created with static keyword is belongs to class rather then the instance of class. Means the static items are created in shared memory area, which is shared within all the instance of class.

## Static Variable :

Variables created with static keyword is shared within all object instances of a class. Some of the use of static keyword are :

**1. Counting number of instances created from a class.**
```java
class TestClass {
	static int count;

		// construtor for counting the number of instances
	TestClass() {     
 		count++;
	}

	void display() {
		System.out.println("Hello world");
	}

	void ObjCount() {
		System.out.println("Total number of Object: "+count);
	}
}

class ObjCount {
	public static void main(String args[]) {
		TestClass t1 = new TestClass();
		TestClass t2 = new TestClass();
		TestClass t3 = new TestClass();
		t1.display();
		t2.display();
		t3.display();

		// shows number of objects created
		t3.ObjCount();
	}
}
```
**Output:**
```console
Hello world
Hello world
Hello world
Total number of Object: 3
```

**2. Creating a student list where they share same school name.**
```java
class Student {
	static String sn = "Government Public School";
	static String cn = "6th Standard";
	String name;
	int age;

		// construtor for counting the number of instances
	Student(String n, int a) {
		name=n;
		age=a;
	}

	void displayInfo() {
		System.out.println("Name : "+name);
		System.out.println("Age: "+age);
		System.out.println("School : "+sn);
		System.out.println("Class : "+cn + "\n");
	}

	public static void main(String str[]) {
		Student s1 = new Student("John snow", 12);
		Student s2 = new Student("Peter parker", 11);

		s1.displayInfo();
		s2.displayInfo();
	}
}
```
**Output:**
```console
Name : John snow
Age: 12
School : Government Public School
Class : 6th Standard

Name : Peter parker
Age: 11
School : Government Public School
Class : 6th Standard
```

### Static Methods :

Similar to static variable, the static method belongs to the class rather then instances (objects) of a class. The main advantage of a static method is, it can be invoked without creating an object of a class. Also note that a static method can only access static data members and it can also change the value of static data members. Example :
```java
class Sample {
	int x,y;
	static int count;

	Sample() {
		count++;
	}

	static void Message() {
		System.out.println("Hello world");
		System.out.println("Value of count: "+count+"\n");
	}

	static void Change() {
		count=0;
	}
}

class StaticTest {
	public static void main(String args[]) {

		// invoing static method Message() without any object
		Sample.Message();

		Sample s1 = new Sample();
		Sample s2 = new Sample();
		s1.Message();
	
		// Changing the value of static member count with
		// static method Change()
		Sample.Change();
		
		s1.Message();
	}
}
```
**Output**
```console
Hello world
Value of count: 0

Hello world
Value of count: 2

Hello world
Value of count: 0
```
Some of the restrictions on static method is that it can't access non-static data member and can't call non-static methods directly. And also "this" and "static" keyword can not be used in static context. 

### Static Black :

The static block is used to initialize the static data memer. The code inside static block is executed only once when the first object created or a static member/method is accessed or called. Also note the static blocks are executed before constructors. Example :
```java
class TestClass {
	static int x;

	// defining static block
	static {
		x = 20; 
		System.out.println("static block invoked");
	}

	void show() {
		System.out.println("Hello world");
		System.out.println(x);
	}

	public static void main(String args[]) {
		TestClass t1 = new TestClass();
		t1.show();	
	}
}
```
**Output**
```console
static block invoked
Hello world
20
```
**Another example :**
```java
class TestClass {
	static int x;

	// defining static block
	static {
		x = 20; 
		System.out.println("static block invoked");
	}

	void show() {
		System.out.println("Hello world");
		System.out.println(x);
	}

	public static void main(String args[]) {

		// calling function through anonymous object
		new TestClass().show();
	}
}
```
**Output**
```console
static block invoked
Hello world
20
```

