# **Source and sink code reviews.**

  - **Source:** End-point or output point. A source is an input used in
    a program, such as a file, servet request, console input, or a
    socket. When input is not validated, it is considered untrusted.

<!-- end list -->

  - **Sink:** A sink can be any external format to which data can be
    written out. Sink examples include databases, files, console output,
    and sockets. Writing data to a sink without checking it may indicate
    a serious security vulnerability.

The word sink has been used for both input and output in the IT
industry. sink or event sink is a class or function designed to receive
incoming events from another object or function. The .NET Framework
provides a delegate-based event system to connect an event sender
(source) to an event receiver (sink).

Another way of thinking about it could be like a kitchen sink—the source
is where everything goes in (Drain opening) and the sink is where it all
goes at the other end (into the pipe, and out the house).

  - **Lost Sink:** A lost sink is an API method that can no longer be
    traced.

<!-- end list -->

  - **Taint tracking:** Finding a route from a source to a sink. If the
    input that is provided at the source is not evaluated, or sanitized
    before it reaches the sink a tainted route has been found.

In the following code sample, the main method calls a method,
getVulnerableSource, that returns a string. Note that, although the
method reads data from a completely unknown file, it never checks the
validity of the returned data. The main method then passes this tainted
data into writeToVulnerableSink. The writeToVulnerableSink method writes
the data out to the file, never checking its validity.

## Source to Sink example of unvalidated data.

`import java.io.*;`
`public class TestCase_IOT_Static {`
`public static void main(String[] args) {`
`try {`
`  String file = args[0];`
`  writeToVulnerableSink(file, getVulnerableSource(file));`
`} catch (Exception e) {`
`}`
`}`
`public static String getVulnerableSource(String file)`
`throws java.io.IOException, java.io.FileNotFoundException {`
`FileInputStream fis = new FileInputStream(file);`
`byte[] buf = new byte[100];`
`fis.read(buf);`
`String ret = new String(buf);`
`fis.close();`
`return ret;`
`}`
`public static void writeToVulnerableSink(String file, String str)`
`throws java.io.FileNotFoundException {`
`FileOutputStream fos = new FileOutputStream(file);`
`PrintWriter writer = new PrintWriter(fos);`
`writer.write(str);`
`}`
`}`