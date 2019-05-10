Stating from
[wikipedia](http://en.wikipedia.org/wiki/Java_%28programming_language%29),
Java is an object oriented programming language developed by Sun in the
early 1990s with the aim to be portable and cross compatible.

Looking at the security point of view, Java is a big step ahead from C
programming language:

  - automatic garbage collector: Java virtual machine use an automatic
    garbage collector to free unused or unreferenced previously
    allocated memory regions. This approach solves the annoying problem
    that afflict many C source codes and their poor memory management,
    not enforced however by the programming language itself
  - hardening against buffer overflow, thanks to language design you
    can't stuff in a String object more items than it is able to contain
  - hardening against off-by-one buffer overflow, thanks to a better
    language expressiveness (an array length is a public attribute of
    the array itself and Vector objects give public method size() to
    check for

Big step ahead but security is a real concern also in the Java world.

Let's see some best practices about writing, or trying to write a more
secured java code.

First of all a big truth: 100% safe code doesn't exists. Our goal is to
provide as much as possible ways to harden it and make it stronger.