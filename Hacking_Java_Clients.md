## Status

Released 14/1/2008

## Hacking Java Clients

When performing a security assessment of client-server Java
applications, it is sometimes necessary to modify the client component
in order to properly understand and assess the security mechanisms in
place. Typical examples are systems that employ a communication channel
that can't be intercepted with tools such as the personal proxies
(WebScarab, Paros, etc.). A convenient means of accessing the internals
of a Java program is to have an interactive scripting environment
(BeanShell, Jython, JRuby, Groovy, etc.) that exposes the internal
objects and allows you to perform arbitrary operations on these objects.
The following [white
paper](http://research.corsaire.com/whitepapers/060816-assessing-java-clients-with-the-beanshell.pdf)
outlines this technique.

There are a number of techniques that can be used to insert such an
interpreter, these include:

1.  Recompile the source code and include the interpreter into the app.
    (Of course, you'll need access to the source and a build
    environment)
2.  Insert the interpreter using inheritance (as described in the
    white-paper mentioned above).
3.  Insert the interpreter by directly manipulating the byte-code
4.  Use [this tool](http://www.adaptj.com/root/main/stacktrace)
5.  Use [a new feature implemented by
    Java 6](http://www.fasterj.com/articles/hotpatch1.shtml)

[Category:Java](Category:Java "wikilink")