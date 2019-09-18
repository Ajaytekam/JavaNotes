## Java Collections

A Collection is a group of individual objects represented as a single unit. Java provides Collection Framework which defines several classes and interfaces to represent a group of objects as a single unit.

It basicaly helps in working with different types of collections such as lists, sets, maps, stacks and queues etc. By using java collections, we perform all operations on data such as searching, sorting, insertion, manipulation, deletion, etc.

The main component of java collection framework is as follows :

* **Interfaces**
* **Classes**
* **Algorithm**

![Java Collection](jc.png)

**Interfaces :** Interface in Java refers to the abstract data types. They allow Java collections to be manipulated independently from the details of their representation. Also, they form a hierarchy in object-oriented programming languages.

**Classes :** Classes in Java are the implementation of the collection interface. It basically refers to the data structures that are used again and again.

**Algorithm :** Algorithm refers to the methods which are used to perform operations such as searching and sorting, on objects that implement collection interfaces.

 
### Java Collections : List

A List is an ordered Collection of elements which may also contain duplicates. It is an interface that extends the Collection interface.i Lists are further classified into the following:

1. **ArrayList**
2. **LinkedList**
3. **Vectors**
  
  
### 1. ArrayList :

ArrayList is the implementation of List Interface where the elements can be dynamically added or removed from the list. Also, the size of the list is increased dynamically if the elements are added more than the initial size. 

Class Library : `java.util.ArrayList`

Creating an ArrayList of type `string`:
```java
ArrayList<String> listname = new ArrayList<String>();
```
Example :
Creating another list by copying values from another list:
```java
ArrayList<String> listB = new ArrayList<String>(listA);
```
Example :
```java
import java.util.*;

class MyClass {
	public static void main(String args[]) {
		ArrayList<String> listA = new ArrayList<String>();
	   	listA.add("Ajay");
	   	listA.add("ajax98");
	   	listA.add("dk0d");
	   	listA.add("h4x34r");
	   	listA.add("mdma12");
		listA.forEach(System.out::println);
	}
}
```
## Methods of ArrayList :

**1. add()** : Add an element to an Arraylist. 
```java
public boolean add(Element);
```
Syntax :
```java
list.add("String");
```
This method has also another variation where we can specify on which index position the element is inserted.
```java
list.add(postion, "String")
```
Example :
```java
import java.util.*;

class test1 {
	public static void main(String args[]) {
		ArrayList<String> list = new ArrayList<String>();
		list.add("Hello");
		list.add("world");
		list.add("This");
		list.add("is");
		list.add("Test.");
		System.out.println(list);

		// inserting another element at the third position.
		list.add(2, "Ajay");
		System.out.println(list);
	}
}
```
**Output:**
```console
[Hello, world, This, is, Test.]
[Hello, world, Ajay, This, is, Test.]
```
Note: we can also create an arraylist with an initial capacity, which is specified by the last bracket.
```java
ArrayList<String> list = new ArrayList<String>(5);
```

**2. addAll()** : Used to add all the elements of the specified collection/list into the new listwithin the specified index position.
```java
public boolean addAll(int index, Collection<? extends E> c)
```
Syntax :
```java
list2.addAll(list1);
```
Add all the element of list1 into list2.  
```java
list2.addAll(3, list1);
```
Add elements of list1 into list2 from fourth index position (3).  

Example :
```java
import java.util.*;

class test1 {
    public static void main(String args[]) {
        ArrayList<String> list1 = new ArrayList<String>();
        list1.add("Hello");
        list1.add("world");
        list1.add("This");
        list1.add("is");
        list1.add("Test.");
    	
		// creating a new list and copy the old one
		ArrayList<String> list2 = new ArrayList<String>();
		list2.addAll(list1);
		System.out.println(list2);

        ArrayList<String> list3 = new ArrayList<String>();
		list3.add("ajay");
		// use within index 
		list2.addAll(2, list3);
		System.out.println(list2);
	}
}
```
**Output:**
```console
[Hello, world, This, is, Test.]
[Hello, world, ajay, This, is, Test.]
```
**3. remove()** : Removes the first occurrence of the specified element from this list.
```java
public boolean remove(Object o);
```
**There are two methods available-**
```java
list.remove(element);
```
* Removes the first occurance of the specified element from the list.
```java
list.remove(indexOf);
```
* Removes the element at the specified position in this list. Shifts any subsequent elements to the left.

Example :
```java
import java.util.*;

class test1 {
	public static void main(String args[]) {
		ArrayList<String> list1 = new ArrayList<String>();
		list1.add("Hello");
		list1.add("world");
		list1.add("This");
		list1.add("is");
		list1.add("Test.");

		// remove element "world" from list
		list1.remove("world");
		System.out.println(list1);

		// remove first element "hello" by using index
		list1.remove(0);
		System.out.println(list1);
	}
}
```

**4. removeAll() :** It removes all occurrences of matching elements, not only first occurrence. If element is found in argument collection, it re-arranges the index.
```java
public boolean removeAll(Collection c)
```
This method returns true if this list changed as a result of the call.

Example :
```java
import java.util.*;

class test1 {
	public static void main(String args[]) {
		ArrayList<Integer> list1 = new ArrayList<Integer>();
		list1.add(100);
		list1.add(200);
		list1.add(300);
		list1.add(450);
		list1.add(500);

		// creating a new list
		ArrayList<Integer> list2 = new ArrayList<Integer>();
		list2.add(100);
		list2.add(200);
		list2.add(500);

		// removes all elements from list1 which are in list2
		list1.removeAll(list2);
		System.out.println(list1);
	}
}
```

Note : It only takes argument as collection object, so if we want to remove only single element then we can use `Collections.singleton('element')` method. Example : 
```java
import java.util.*;

class test1 {
	public static void main(String args[]) {
		ArrayList<Integer> list1 = new ArrayList<Integer>();
		list1.add(100);
		list1.add(200);
		list1.add(300);
		list1.add(450);
		list1.add(500);
		list1.add(450);

		// removes all the appearance of 450	
		list1.removeAll(Collections.singleton(450));
		System.out.println(list1);
	}
}
```

**5. contains()** : used to check if the specified element exists in the given arraylist or not. If element exist then method returns true, else false.
```java
public boolean contains(Element)
```
Example :
```java
import java.util.*;

class test1 {
	public static void main(String args[]) {
		ArrayList<Integer> list1 = new ArrayList<Integer>();
		list1.add(100);
		list1.add(200);
		list1.add(300);
		list1.add(450);
		list1.add(500);
		list1.add(450);

		// removes all the appearance of 450	
		System.out.println(list1.contains(500));

		// Using another way
		// below conditional statement returns true
		if(list1.contains(100)) {
			System.out.println("It Contains 100");
		}
	}
}
```

**6. containsAll() :** used to check if this List contains all of the elements in the specified Collection. The method returns True if all elements in the collection col are present in the List otherwise it returns False.
```java
boolean containsAll(Collection)
```
Example :
```java
iimport java.util.*;

class test1 {
	public static void main(String args[]) {
		ArrayList<Integer> list1 = new ArrayList<Integer>();
		list1.add(100);
		list1.add(200);
		list1.add(300);
		list1.add(450);
		list1.add(500);
		list1.add(450);

		ArrayList<Integer> list2 = new ArrayList<Integer>();
		list2.add(100);
		list2.add(500);

		System.out.println(list1.containsAll(list2));
	}
}
```

**7. isEmpty()** : Returns true if the set contains no elements.
```java
boolean isEmpty(Collection)	
```
Example :
```java
import java.util.*;

class test1 {
	public static void main(String args[]) {
		ArrayList<Integer> list1 = new ArrayList<Integer>();
		System.out.println(list1.isEmpty());
	}
}
```

**8. clear()** : Removes all of the elements from this list.The list will be empty after this call returns.
```java
public void claer()
``` 
Exmaple :
```java
import java.util.*;

class MyClass {
	public static void main(String args[]) {
		ArrayList<Double> list = new ArrayList<Double>();
		list.add(1.5);
		list.add(1.75);
		list.add(1.78);
		list.add(3.50);
		list.add(8.45);

		list.clear();
	}
}
```

**9. size()** : Used to get the number of elements in this list. This method returns the number of elements in this list. 
```java
public int size()
```
Example :
```java
import java.util.*;

class MyClass {
	public static void main(String args[]) {
		ArrayList<Double> list = new ArrayList<Double>();
		list.add(1.5);
		list.add(1.75);
		list.add(1.78);
		list.add(3.50);
		list.add(8.45);

		// return size of arraylist as int value
		System.out.println(list.size());
	}
}
```

**10. indexOf()** : This method returns the index of the first occurrence of the specified element in this list. It will return '-1' if the list does not contain the element.
```java
public int indexOf(Element)
```
Example :
```java
iimport java.util.*;

class MyClass {
	public static void main(String args[]) {
		ArrayList<String> list = new ArrayList<String>(Arrays.asList("JavaScript", "C++", "PHP", "Python", "Node.JS", "C Language", "HTML", "CSS"));

		System.out.println(list.indexOf("HTML"));
		System.out.println(list.indexOf("C++"));
		System.out.println(list.indexOf("Golang"));
	}
}
```

**11. lastIndexOf()** : This method returns the index of the last occurrence of the specified element in this list. It will return '-1' if the list does not contain the element.
```java
public int lastIndexOf(Element)
```
Example :
```java
import java.util.*;

class MyClass {
	public static void main(String args[]) {
		ArrayList<String> list = new ArrayList<String>(Arrays.asList("HTML", "C++", "PHP", "Python", "Node.JS", "C Language", "HTML", "CSS"));

		System.out.println(list.indexOf("HTML"));
		System.out.println(list.lastIndexOf("HTML"));
	}
}
```

**12. toArray()** : toArray() method returns an array containing all of the elements in the list in proper sequence (from first to last element).
```java
import java.util.*;

class MyClass {
	public static void main(String args[]) {
		ArrayList<String> list = new ArrayList<>(2); 
        list.add("A");
        list.add("B");
        list.add("C");
        list.add("D");
         
        //Convert to object array
        Object[] array = list.toArray();
         
        System.out.println( Arrays.toString(array) );
 
        //Iterate and convert to desired type
        for(Object o : array) {
            String s = (String) o;
            System.out.println(s);
        }

	}
} 
```
