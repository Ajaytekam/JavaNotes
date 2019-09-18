## Nested Class in Java

In java, it is possible to define a class within another class, such classes are known as nested classes. They enable you to logically group classes that are only used in one place, thus this increases the use of encapsulation, and create more readable and maintainable code.   

Example :
```java
class OuterClass {
....
	class InnerClass {
		....
	}
}
```

### Types of Nested/Inner Classes :

**1. Static inner class**    
**2. Non-Static inner class**   

The main difference between static and non-static inner class is that the static class will only access static members of outer class and non-static class will access all the members of outer class. There is also differences in object creation. 


**1. Static inner class**

The object is created in static inner class is like this :  
```java
OuterClass.StaticInnerClass object = new OuterClass.StaticInnerClass();
``` 
Example :   
```java
class OuterClass {
    public static void SMessage() {
        System.out.println("This is Static Message from OuterClass");
    }
        
    public void Message() {
        System.out.println("This is Message from OuterClass");
    }

    static class InnerClass {
        void Show() {
            SMessage(); 
        }
    }
}
class MyClass {
    public static void main(String args[]) {
        OuterClass.InnerClass obj = new OuterClass.InnerClass();
        obj.Show();
    }
}
```
Output:
```console
This is Static Message from OuterClass
``` 

**2. Non-Static inner class**  

To create an object for non-static inner class, first we have to create an object for outerClass then by using that we can create object for inner class. 
```java
OuterClass OuterObject = new OuterClass();
OuterClass.InnerClass InnerObject = OuterObjet.new InnerClass();
```
Example :
```java
class OuterClass {
	public void Message() {
		System.out.println("This is Message from OutClass");
	}

	class InnerClass {	
		public void Message() {
			System.out.println("This is Message from InnerClass");
		}
	}
}

class MyClass {
	public static void main(String args[]) {
		OuterClass  OuterObj = new OuterClass();
		OuterObj.Message();
		OuterClass.InnerClass InnerObj = OuterObj.new InnerClass();
	   	InnerObj.Message();	   
	}
}
```
Output :
```console
This is Message from OutClass
This is Message from InnerClass
```
