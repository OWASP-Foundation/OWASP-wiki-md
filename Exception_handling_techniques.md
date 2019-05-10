## Status

To be reviewed

## Exceptions Overview

Exceptions are occurrences that alter the normal program flow. They can
have various causes, such as hardware failures, resource exhaustion,
programming bugs etc. When an exceptional event occurs, an exception is
said to be "thrown." The code responsible for treating the exception is
called an "exception handler," and it "catches" the thrown exception.
Exception handling refers to passing the execution of a program to an
appropriate exception handler when an exception occurs. For example, if
a method that opens a file is called, and the file cannot be opened, the
execution of that method will stop, and the code from the appropriate
exception handler will be run.

In Java, exception-handling code is cleanly separated from the
exception-generating code. The try block (also called "guarded region")
is the code in which exceptions may occur, and it must be immediately
followed by either a finally block or at least one catch block. In Java
7, there is a new syntactic construction, called "try-with-resources",
which is the only exception to this rule, as it is not forced to be
followed by a finally or catch block.

A finally block contains code that is always executed at some point
after the try block, whether an exception was thrown or not. Even if
there is a return statement in the try block, the finally block executes
right after the return statement is encountered, and before the return
executes. If the try block executes without exception, the finally block
is executed immediately after the try block completes. If an exception
was thrown, the finally block executes immediately after the
corresponding catch block completes. However, if the JVM exits while the
try or catch code is being executed, then the finally block may not
execute. Likewise, if the thread executing the try or catch code is
interrupted or killed, the finally block may not execute even though the
application keeps running.

## Swallowing Exceptions

Swallowing exceptions means to continue processing as if nothing had
gone wrong even though an exception has been thrown. You catch the
exception, but do nothing meaningful with it. The classical example is
an empty catch block:

`   catch(Exception e) {`
`   }`

Swallowing exceptions is considered bad practice, because the ignored
exception may lead the application to an unexpected failure, at a point
in the code that bears no apparent relation to the source of the
problem. Finding the cause of the failure in such cases can be very
challenging and time-consuming. Merely letting an exception propagate
outward can at least cause the program to fail swiftly, preserving
information to aid in debugging the failure.

In addition, in case an exception is caught, it is strongly recommended
to log information about it, as it is very useful for debugging
purposes.

## Resource cleanup and finally block

One of the situations when exceptions may occur is when we work with
resources, such as files, databases, network sockets etc.

Opening/closing, connecting/disconnecting, read/write statements are
examples of operations that may throw exceptions in particular cases. If
our code needs to work with resources, it is important to release them
as soon as we are finished using them.

The following example is about writing a text in a file. The
constructor, the write, the flush of the file operation can throw
IOException, hence they are being placed inside the try block. We are
aware that we must close the file after writing in it. A naive (and
wrong) approach would be the following:

`   File file = new File("file.txt");`
`   Writer writer = null;`
`   try {`
`       writer = new PrintWriter(file);`
`       writer.write("Hello world!");`
`       writer.flush();`
`       writer.close();`
`   }`
`   catch(FileNotFoundException e) {`
`       System.err.println("Caught FileNotFoundException: " + e.getMessage());   `
`   }`
`   catch (IOException e) {`
`       System.err.println("Caught IOException: " + e.getMessage());`
`   }`

As you can see in the example, we close a resource inside the try block.
However this is not a good practice, because if an exception is thrown
before our close statement is reached, then it will not be executed and
resources might thus leak. We could add the close statement in the catch
block, which leads to code duplication. If we have several catch blocks,
this means we have to add the close statement there. Whenever we need to
add a new catch block, we must also remember to put the close statement
there. This way of handling exceptions is error-prone and unnecessarily
complicated.

So where should we place the close statement? We would need a block that
always gets executed, no matter if we have exceptions or not, like...
finally.

Indeed, the ideal place to release resources is the finally block. As we
have seen before, finally always gets executed. This means the closing
of resources will get executed even if exceptions occur, and in addition
we do not have code duplication, which is mainly what we want. This
approach is the best way to correctly handle the resources our code
used.

To fix the above example, a finally block was added and the file was
closed there, as shown in the code below.

`   File file = new File("file.txt");`
`   Writer writer = null;`
`   try {`
`       writer = new PrintWriter(file);`
`       writer.write("Hello world!");`
`       writer.flush();`
`   }`
`   catch(FileNotFoundException e) {`
`       System.err.println("Caught FileNotFoundException: " + e.getMessage());   `
`   }`
`   catch (IOException e) {`
`       System.err.println("Caught IOException: " + e.getMessage());`
`   } finally {`
`       if (writer != null)`
`           try {`
`               writer.close();`
`           } catch (IOException e) {`
`               System.err.println("Caught IOException: " + e.getMessage());`
`           }`
`   }`

## Try-with-resources

In Java 7, resource cleanup was automated by means of the
try-with-resources block. In practice, this new syntax allows you to
declare resources that are part of the try block. You define the
resources ahead of time and the runtime automatically closes those
resources (if they are not already closed) after the execution of the
try block.

A resource can be any object that implements the interface
java.lang.AutoCloseable.

Although the try-with-resources block can have a finally or catch block,
it is not mandatory.

In our example, since Writer implements AutoCloseable, we can place it
in a try-with-resources block as follows:

`   File file = new File("file.txt");`
`   try(Writer writer = new PrintWriter(file)) {`
`       writer.write("Hello world!");`
`       writer.flush();`
`   }`

The code looks far more readable this way, and the developer is no
longer supposed to close the resources, it is automatically done as long
as the classes implement the AutoCloseable interface. Also note that the
function that contains this code must throw IOException in order to
compile, since there are no catch blocks.

[Category:Java](Category:Java "wikilink") [Category:Error
Handling](Category:Error_Handling "wikilink")