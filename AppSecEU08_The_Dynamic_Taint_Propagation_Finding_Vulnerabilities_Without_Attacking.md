The purpose of this talk is to demonstrate a new technique for finding
security vulnerabilities. This technique analyzes the flow of data
throughout an application and identifies vulnerable paths. This type of
approach has great potential to be used in conjunction with standard
regression tests because regression tests generally exercise the
application much more rigorously than typical security tests.

Until recently, dynamic testing was left to security teams and ethical
hackers who used advanced tools, such as Web application scanners, to
analyze running Web applications. However, many organizations are
attempting to move security testing earlier in the development cycle.
The QA group is a natural candidate, since it generally has the
infrastructure in place to test applications for quality issues. Yet,
the security testing tools currently available to QA were designed for
penetration testers (since they require an in-depth knowledge of
application security theory) and are not generally usable by QA
professionals. As a result, very few QA groups have successfully
deployed security testing solutions. That’s where Dynamic Taint
Propagation comes into play. By modifying the program executable to
carry more information about the origin of the data being processed,
dynamic taint propagation allows testers to find vulnerabilities without
disturbing the normal functionality of the program.