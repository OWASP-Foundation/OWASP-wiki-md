Does anyone know the current state of this code? I have an application
which I would like to test for CSRF vulnerability. I downloaded
CSRFTester and am trying to get it to load. The error I get is
"Exception in thread "main" java.lang.UnsupportedClassVersionError: Bad
version number in .class file"

` Yes it works. You're running with an old version of Java, and it's telling you that it doesn't understand`
` the format of the class file.  Try upgrading to Java 1.6 and running it. `[`Jeff``
 ``Williams`](User:Jeff_Williams "wikilink")` 08:25, 24 February 2009 (EST)`