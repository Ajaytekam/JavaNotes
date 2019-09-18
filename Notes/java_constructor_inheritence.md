## Handling Java Class Constructor with Inheritence

In Java, constructor of base class automatically gets called in derived class constructor. For example :
```java
class BaseClass {

	BaseClass() {
		System.out.println("BaseClass is called.");
	}	

}

class SubClass extends BaseClass {

	SubClass() {
		System.out.println("SubClass is called.");
	}

}

class MyClass {
	public static void main(String args[]) {
		SubClass obj = new SubClass();
	}
}
```
Output:
```console
BaseClass is called.
SubClass is called.
```
As we can see that the BaseClass() is automatically called first when object is created. But, if we want to call parameterized contructor of base class, then we can call it using `super()`. The point to note is base class constructor call must be the first line in Subclass constructor. Example :   
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
At above example, the constructor of  subclass `result` will first call the superclass `student` constructor with keyword `super`.
