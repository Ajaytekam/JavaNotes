## Iterators

In java, iterators are used in collection framework to retrive/traverse a collection object one by one. It is a universal iterator as we can apply it to any Collection object. By using Iterator, we can perform both read and remove operations. It is improved version of Enumeration with additional functionality of remove-ability of a element. Also note that the iterator only moves/fatches forword, means it will not retrive elements again from backword, for that we have to create another object to fatch/retrieve from the beginning.

**Class Library `java.util.Iterator`**

## Iterator Methods :

**1. hasNext() :** Returns a true(boolean) value if the more number of elements are encountered during iteration.  
```java
public boolean hasNext();
```
**2. next() :** Returns the next specified element during the iteration.  
```java
public Object next();
```
**3. remove() :** Removes from the underlying collection the last element returned by this iterator.
```java
public void remove();
```

The iterator object is created by calling `Iterator()` method.
```java
Iterator itr = cln.iterator();
```
where `cln` is any collection object.

Example1 :
```java
import java.util.*;

class MyClass {
	public static void main(String args[]) {
		ArrayList<String> list = new ArrayList<String>();
		list.add("Java");
		list.add("C");
		list.add("C++");
		list.add("JavaScript");
		list.add("HTML");
		list.add("CSS");

		// creating iterator object
		Iterator itr = list.iterator();
			
		while(itr.hasNext()) {
			System.out.println(itr.next());
		}
	}
}
```
**Output :**
```console
Java
C
C++
JavaScript
HTML
CSS
```

Storing `itr.next()` object into string.
```java
// creating iterator object
Iterator itr = list.iterator();
String str;		
while(itr.hasNext()) {
	str = (String)itr.next();
	System.out.println(str);
}
```

Example2:

Using remove() method :
```java
import java.util.*;

class MyClass {
	public static void main(String args[]) {
		ArrayList<String> list = new ArrayList<String>();
		list.add("Java");
		list.add("C");
		list.add("C++");
		list.add("JavaScript");
		list.add("HTML");
		list.add("CSS");

		// creating iterator object
		Iterator itr1 = list.iterator();
		while(itr1.hasNext()) {
			System.out.print(itr1.next()+", ");
		}
		System.out.println("");

		// remove the last element
		itr1.remove();

		Iterator itr2 = list.iterator();
		while(itr2.hasNext()) {
			System.out.print(itr2.next()+", ");
		}
	}
}
```
Another example of using remove() method.
```java
import java.util.*;

class MyClass {
	public static void main(String args[]) {
		ArrayList<Integer> list = new ArrayList<Integer>();
		
		// adding elements from 1 to 20 in listarray
		for(int x=1;x<=20;x++) {
			list.add(x);
		}


		// removing all the odd numbers from
		// the list
		Iterator itr = list.iterator();
		int num;        
		while(itr.hasNext()) {
    		num = (int)itr.next();
			if(num%2!=0) {
				itr.remove();
			}
		}

		// printing elements	
		Iterator itr1 = list.iterator();   
		while(itr1.hasNext()) {
			System.out.println(itr1.next());
		}
	}
}
```
### Limitations of Iterator :

* Only forward direction iterating is possible.
* Replacement and addition of new element is not supported by Iterator.

