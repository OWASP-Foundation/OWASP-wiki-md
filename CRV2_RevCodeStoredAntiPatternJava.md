# XSS Stored vulnerabilities in Java

Once understood how the vulnerability works, inspect a correct
implementation of input sanitizers in the Java application. For example
The OWASP HTML Sanitizer is a fast and easy to configure HTML Sanitizer
written in Java which lets you include HTML authored by third-parties in
your web application while protecting against XSS. The existing
dependencies are on guava and JSR 305. The other jars are only needed by
the test suite. The JSR 305 dependency is a compile-only dependency,
only needed for annotations. This code was written with security best
practices in mind, has an extensive test suite, and has undergone
adversarial security review. A great place to get started using the
OWASP Java HTML Sanitizer is here:
<https://code.google.com/p/owasp-java-html-sanitizer/wiki/GettingStarted>.

# Bad Session Stores

As described in the research paper written by V.Benjamin Livshits(2005),
Bad session stores occurs when objects stored in attributes of
javax.servlet.http.HttpSession are not subclasses of
java.io.Serializable.

As further described by Livshits, it causes issues because HttpSessions
objects could be written out to disk especially when all objects stored
are handled as attributes that must be serialized, if not done properly
this will cause exceptions or data corruption.

## What to look for in the code

  - Parameters of HttpSession.set Attribute
  - Control if javax.servlet.httpSession is a subclass of
    java.io.Serializable

# References

OWASP Java HTML Sanitizer available at
<https://www.owasp.org/index.php/OWASP_Java_HTML_Sanitizer_Project>

V. Benjamin Livshits, "Findings Security Errors in Java Applications
Using Lightweight Static Analysis" 2005 available at
(http://research.microsoft.com/en-us/um/people/livshits/papers/pdf/acsac04v.pdf)
Last Viewed October 3rd 2013