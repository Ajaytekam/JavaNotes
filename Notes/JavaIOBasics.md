## Java Iinput/Output

Java I/O (Input and Output) is used to process the input and produce the output. Java uses the concept of a stream to make I/O operation fast. 

**Stream :** A stream is a sequence of data. In Java, a stream is composed of bytes. It's called a stream because it is like a stream of water that continues to flow. In Java, 3 streams are created for us automatically. All these streams are attached with the console.

* **System.out** : standard output stream.
* **System.in** : standard input stream.
* **System.err** : standard error stream.

Java encapsulates Stream under java.io package. Java defines two types of streams. They are :

**1. Byte Stream :** It provides a convenient means for handling input and output of byte.  
**2. Character Stream :** It provides a convenient means for handling input and output of characters. Character stream uses Unicode and therefore can be internationalized.

Byte stream is defined by using two abstract class at the top of hierarchy, they are InputStream and OutputStream.
```console
		ByteStream
		    /\
           /  \
          /    \
         /      \
        /        \
  InputStream  OutputStream
```
**InputStream :** Abstract class that describe stream input.  
**OutputStream :** Abstract class that describe stream output.   

These two abstract classes have several concrete classes that handle various devices such as disk files, network connection etc.
|Stream Class|Description|
|-----|------|
|FileInputStream|Input stream that reads from a file|
|FileOutputStream|Output stream that write to a file.|
|BufferedInputStream|Used for Buffered Input Stream.|
|BufferedOutputStream|Used for Buffered Output Stream.|
|FileReader|Used for reading filtered character streams.|
|FileWriter|USed for writing filtered character streams.|
|BufferedReader|Used for reading from Buffered Input Stream.|
|BufferedWriter|used for writing into Buffed Output Stream|


## InputStream :

Java application uses an input stream to read data from a source; it may be a file, an array, peripheral device or socket. To implement this, input stream class is used. InputStream class is an abstract class. It is the superclass of all classes representing an input stream of bytes. Some of useful methods used on InputStream class :
|Method|Description|
|-----|----------|
|int read()|reads the next byte of data from the input stream. It returns -1 at the end of the file.|
|int read(byte[] b)|It is used to read up to b.length bytes of data from the input stream.|
|int read(byte[] b, int off, int len)|It is used to read up to len bytes of data from the input stream.|
|long skip(long x)|It is used to skip over and discards x bytes of data from the input stream.|
|FileChannel getChannel()getChannel|It is used to return the unique FileChannel object associated with the file input stream.|
|FileDescriptor getFD()|It is used to return the FileDescriptor object.|
|protected void finalize()finalize|It is used to ensure that the close method is call when there is no more reference to the file input stream.|
|int available()|returns an estimate of the number of bytes that can be read from the current input stream.|
|void close()|used to close the current input stream.|


All above methods throws `IOException`. 

#### Constructor used within FileInputStream Class :
* FileInputStream(File file): Creates an input file stream to read from the specified File object.
* FileInputStream(FileDescriptor fdobj): Creates an input file stream to read from the specified file descriptor.
* FileInputStream(String name): Creates an input file stream to read from a file with the specified name.

Now first we need to create an object of FileInputStream.
```java
FileInputStream finObj =new FileInputStream("file.txt");
```
Also the `read()` method returns `int` type value, so we have to typecast it in order to print it as character.  
A simple example of `read()` Method :
```java
import java.io.FileInputStream;

class ReadFile {
	public static void main(String args[]) {
		try {
			FileInputStream fin = new FileInputStream("file.txt");
			int ch;
			while((ch=fin.read())!=-1) {
				System.out.print((char)ch);
			}
			fin.close();
		} catch(Exception e) {System.out.println(e);} 
		
	}
}
```
Output:
```console
Hello world
This is Text
This is another text
```

## OutputStream :

Java FileOutputStream is an output stream used for writing data to a file. If you have to write primitive values into a file, use FileOutputStream class. You can write byte-oriented as well as character-oriented data through FileOutputStream class. But, for character-oriented data, it is preferred to use FileWriter than FileOutputStream.

Method of OutputStream :
|Method|Description|
|------|-----------|
|void finalize()|used to clean up the connection with the file output stream.|
|void write(byte[] ary)|used to write ary.length bytes from the byte array to the file output stream.|
|write(byte[] ary, int off, int len)|used to write len bytes from the byte array starting at offset off to the file output stream.|
|void write(int b)|used to write the specified byte to the file output stream.|
|FileChannel getChannel()|It is used to return the file channel object associated with the file output stream.|
|FileDescriptor getFD()|It is used to return the file descriptor associated with the stream.|
|void close()close|It is used to closes the file output stream.|

Creating Object:
```java
FileOutPutStream fout = new FileOutPutStream("file.txt");
```
Example : Writing a single character on the file:
```java

```

Link:
https://www.geeksforgeeks.org/java-io-packag/
https://www.javatpoint.com/java-fileinputstream-class
http://tutorials.jenkov.com/java-io/index.html
https://www.tutorialspoint.com/java/java_files_io.htm (Try This)

