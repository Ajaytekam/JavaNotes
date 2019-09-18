## Basics of Java Programs

**Filename:** MyProgram.java
```java
class MyProgram {
	public static void main(String args[]) {
		System.out.println("Hello world");
	}
}
```
**Compilation steps**
```console
$ javac MyProgram.java
$ java MyProgram
```

### Keyword Details :
* class keyword is used to declare a class in java.
* public keyword is an access modifier which represents visibility. It means it is visible to all.
* static is a keyword. If we declare any method as static, it is known as the static method. The core advantage of the static method is that there is no need to create an object to invoke the static method. The main method is executed by the JVM, so it doesn't require to create an object to invoke the main method. So it saves memory.
* void is the return type of the method. It means it doesn't return any value.
* main represents the starting point of the program.
* `String args[]` is used for command line argument. We will learn it later.
* `System.out.println()` is used to print statement. Here, System is a class, out is the object of PrintStream class, `println()` is the method of PrintStream class. We will learn about the internal working of `System.out.println` statement later.

### Some Important points in Java :
* The Javac compiler will create `.class` file for every class. 
* To execute the code we have to run the class file which have main() function in it.
* A java program can have multiple main class file, but we can execute one at a time. 

