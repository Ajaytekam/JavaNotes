## Java NIO(Non-Blocking IO) Basics

In java, the standard IO API works with byte streams and character streams, but in case of NIO all the operations are performed by using channels and buffers. In NIO data is always read from a channel into a buffer, or written from a buffer to a channel. 

The java NIO enables to do non-blocking IO. For example a thread can ask a channel to read data into a buffer. While the channel reads data into the buffer, the thread can do something else. Once data is read into the buffer, the thread can then continue processing it. The same is true for writing data to channels.

### Java NIO consist of the following core components:

* Channels
* Buffers
* Selectors

## Channels :

A Channel is a bit like a stream. Typically, all IO operations in NIO starts with a Channel. Data can be read from a channel into a Buffer and data can also written from a Buffer into a Channel. 

![Read from Channel to buffer and vice versa](nio.png)

Basically channels read data into Buffers, and Buffers write data into Channels. There are several Channel and Buffer types. Here is a list of the primary Channel implementations in Java NIO:
* **FileChannel**
* **DatagramChannel**
* **SocketChannel**
* **ServerSocketChannel**
 
As we can see, these channels cover UDP + TCP network IO, and file IO.

## Buffers :

Java NIO Buffers are used when interacting with NIO Channels. As we know, data is read from channels into buffers, and written from buffers into channels.

A buffer is basically a block of memory into which you can write data, which you can then later read again. This memory block is wrapped in a NIO Buffer object, which provides a set of methods that makes it easier to work with the memory block. Here is a list of the core Buffer implementations in Java NIO:
* ByteBuffer
* CharBuffer
* DoubleBuffer
* FloatBuffer
* IntBuffer
* LongBuffer
* ShortBuffer

These Buffer's cover the basic data types that you can send via IO: byte, short, int, long, float, double and characters. Java NIO also has a MappedByteBuffer which is used in conjunction with memory mapped files.

## Selectors :

A Selector allows a single thread to handle multiple Channel's. This is handy if the application has many connections (Channels) open, but only has low traffic on each connection. For instance, in a chat server. Here is an illustration of a thread using a Selector to handle 3 Channel's:

![Channles Example](niochannel.png)

To use a Selector we have to register the Channel's with it. Then we call it's `select()` method. This method will block until there is an event ready for one of the registered channels. Once the method returns, the thread can then process these events. Examples of events are incoming connection, data received etc.

http://tutorials.jenkov.com/java-nio/buffers.html
https://javapapers.com/java/java-nio-file-read-write-with-channels/
https://examples.javacodegeeks.com/core-java/nio/file-nio/java-nio-write-file-example/
https://javapapers.com/java/java-nio-tutorial/

