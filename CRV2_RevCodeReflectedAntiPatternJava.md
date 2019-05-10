# Reflection Security Issues

Java reflection is a mechanism used by Java programs given them the
ability to change the runtime actions of the application running within
the Java Virtual Machine (JVM). It makes it easier for developers to
write programs because it helps gather information to implement proper
analysis by the software itself (Schildt, 2011), however it compromises
the systems because malware can easily bypass the security around the
JVM.

Two security vulnerabilities found regarding the use of Java Reflection
are CVE-2012-4681 and CVE-2012-5076. Both of them are related to Java
Applets and another common factor is the use of Java reflection.

## What to look in the code

In order to avoid this security issues, make sure that

  - Java Runtime Environment (JRE) is higher that Java SE 7 Update 6
    version
  - Correct implementtion of classes such as
    com.sun.beans.finder.ClassFinder.findClass
  - Avoid Private structure using AccessibleObject.setAccessible because
    it breaks the encapsulation
  - Avoid Use of sun.misc.Unsafe because it provides direct access to
    memory
  - Verify correct Implementation of java.lang.reflect.ReflectPermission
    following best practices as described in Oracle Documents, September
    2011

## References

Schildt Hebert, 2011 ‘Java: The complete Reference, 8th Edition ‘
McGraw-Hill

Common Vulnerabilities and Exposure, 2012 ‘CVE-2012-4681’, available at
(http://cve.mitre.org/cgi-bin/cvename.cgi?name=2012-4681) last viewed on
October 3rd, 2013

Oracle Documents, 2011 “Permissions in the Java 2 SDK’ available at
<http://docs.oracle.com/javase/1.4.2/docs/guide/security/permissions.html#ReflectPermission>,
last viewed on October 3rd, 2013