## JBroFuzz 0.1 - 1.1: Building a Java Fuzzer for the Web

![JBroFuzz-SplashScreen.jpg](JBroFuzz-SplashScreen.jpg
"JBroFuzz-SplashScreen.jpg")

The process of creating a stable and functional fuzzing tool for web
applications, when examined in greater detail holds a number of caveats.
With the ever-growing need for reliable penetration testing tools,
[JBroFuzz](http://www.owasp.org/index.php/Category:OWASP_JBroFuzz) in
its short history, has been designed with the key objective of being
able to fuzz the web.

This talk aims to cover the evolution of development of this
application, starting from the architectural design criteria, to the
definition of fuzzers and generators, encompassing also the graphical
user interface. Key areas covered will include:

## Overview

  - Designing fuzz categories (OWASP Testing Guide v2)
      - Recursive fuzzing
      - Replasive fuzzing
  - How to build a core java fuzzing framework
      - The need for BigInteger
      - Fuzzers are iterators
  - Limitations in implementing default HTTP/S connections
      - Why not use a HTTP Commons implementation
      - Calculating POST length re-writes
  - GUI Design
      - Sticking to Swing and AWT
      - Building a standalone application
  - Expanding JBroFuzz
      - What is inside the jar file
      - Implement your own fuzzer by extending JBroFuzz

This presentation will be interactive, with a number of demonstrations,
relating to JBroFuzz's functionality and operation.