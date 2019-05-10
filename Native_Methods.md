The moment you see native methods (which leave the Java security manager
and memory protection), you know you found an area that might contain
potential Buffer Overflows, or other C++ type vulnerabilities. Native
methods also have the potential to cause code portability problems on
the server, and strips your ability to deploy Java applets to clients on
multiple OS's.

Marc Schoenefeld, a leading Java researcher, has suggested using CORBA
to broker objects between a Java server application and a C program as a
reasonable alternative to using native methods.

(why are you mentioning .NET here, we are talking about Java?) In the
.Net Framework this is even more problematic due to the high usage of
unmanaged COM objects (Note to Dinis: Put here details about his 'Buffer
Overflows on the .Net Framework' Research)