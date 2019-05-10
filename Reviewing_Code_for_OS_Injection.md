__TOC__

## Introduction

Injection flaws allow attackers to pass malicious code through a web
application to another subsystem. Depending on the subsystem, different
types of injection attacks can be performed:

RDBMS: SQL Injection
WebBrowser/Appserver: SQL Injection
OS-shell: Operating system commands Calling external applications from
your application.

OS Commanding is one of the attack classes that fall into [Injection
Flaws](http://www.webappsec.org/projects/threat/classes/os_commanding.shtml).
In other classifications, it is placed in [Input Validation and
Representation](https://www.fortify.com/vulncat/en/vulncat/index.html)
category, [OS Commanding](Top_10_2007-A2 "wikilink") threat class or
defined as [Failure to Sanitize Data into Control
Plane](http://cwe.mitre.org/data/definitions/77.html) weakness and
[Argument Injection](http://capec.mitre.org/data/definitions/6.html)
attack pattern enumeration. OS Commanding happens when an application
accepts untrusted/insecure input and passes it to external applications
(either as the application name itself or arguments) without validation
or a proper escaping.

## How to Locate the Potentially Vulnerable code

Many developers believe text fields are the only areas for data
validation. This is an incorrect assumption. Any external input must be
data validated:

Text fields, List boxes, radio buttons, check boxes, cookies, HTTP
header data, HTTP post data, hidden fields, parameter names and
parameter values. … This is not an exhaustive list.

“Process to process” or “entity-to-entity” communication must be
investigated also. Any code that communicates with an upstream or
downstream process and accepts input from it must be reviewed.

All injection flaws are input-validation errors. The presence of an
injection flaw is an indication of incorrect data validation on the
input received from an external source outside the boundary of trust,
which gets more blurred every year.

Basically for this type of vulnerability we need to find all input
streams into the application. This can be from a user’s browser, CLI or
fat client but also from upstream processes that “feed” our application.

An example would be to search the code base for the use of APIs or
packages that are normally used for communication purposes.

The **java.io**, **java.sql**, **java.net**, **java.rmi**, **java.xml**
packages are all used for application communication. Searching for
methods from those packages in the code base can yield results. A less
“scientific” method is to search for common keywords such as “UserID”,
“LoginID” or “Password”.

## Vulnerable Patterns for OS Injection

What we should be looking for are relationships between the application
and the operating system; the application-utilising functions of the
underlying operating system.

In Java using the Runtime object, **java.lang.Runtime** does this. In
.NET calls such as '''System.Diagnostics.Process.Start '''are used to
call underlying OS functions. In PHP we may look for calls such as
**exec()** or **passthru()**.

**Example**:

We have a class that eventually gets input from the user via a HTTP
request. This class is used to execute some native exe on the
application server and return a result.

`public class DoStuff {`
`public string executeCommand(String userName)`
`{  try {`
`       String myUid = userName;`
`       Runtime rt = Runtime.getRuntime();`
`       rt.exec("`***`cmd.exe``
 ``/C`***` doStuff.exe " +”-“ +myUid); // Call exe with userID`
`   }catch(Exception e)`
`       {`
`e.printStackTrace();`
`       }`
`   }`
`}`

The method executeCommand calls ***doStuff.exe*** (utilizing cmd.exe)
via the ***java.lang.runtime*** static method ***getRuntime()***. The
parameter passed is not validated in any way in this class. We are
assuming that the data has not been data validated prior to calling this
method. *Transactional analysis should have encountered any data
validation prior to this point.* Inputting “Joe69” would result in the
following MS DOS command:

***doStuff.exe –Joe69***

Lets say we input ***Joe69 & netstat –a*** we would get the following
response:

The exe doStuff would execute passing in the User Id Joe69, but then the
DOS command ***netstat*** would be called. How this works is the passing
of the parameter “&” into the application, which in turn is used as a
command appender in MS DOS and hence the command after the & character
is executed.

This wouldn't be true, if the code above was written as (here we assume
that ***doStuff.exe*** doesn't act as an command interpreter, such as
cmd.exe or /bin/sh);

`public class DoStuff {`
`public string executeCommand(String userName)`
`{  try {`
`       String myUid = userName;`
`       Runtime rt = Runtime.getRuntime();`
`       rt.exec("doStuff.exe " +”-“ +myUid); // Call exe with userID`
`   }catch(Exception e)`
`       {`
`e.printStackTrace();`
`       }`
`   }`
`}`

Why? From [Java 2
documentation](http://java.sun.com/j2se/1.5.0/docs/api/java/lang/Runtime.html);

'' ... More precisely, the given command string is broken into tokens
using a StringTokenizer created by the call new StringTokenizer(command)
with no further modification of the character categories. The tokens
produced by the tokenizer are then placed in the new string array
cmdarray, in the same order ... ''

The produced array contains the executable (the first item) to call and
its arguments (the rest of the arguments). So, unless the first item to
be called is an application which parses the arguments and interprets
them, and further calls other external applications according to them,
it wouldn't be possible to execute ***netstat*** in the above code
snippet. Such a first item to be called would be ***cmd.exe*** in
Windows boxes or ***sh*** in Unix-like boxes.

Most of the out-of-box source code/assembly analyzers would (and some
wouldn't\!) flag a *Command Execution* issue when they encounter the
dangerous APIs; ***System.Diagnostics.Process.Start***,
***java.lang.Runtime.exec***. However, obviously, the calculated risk
should differ. In the first example, the "command injection" is there,
whereas, in the second one without any validation nor escaping what can
be called as "argument injection" vulnerability exists. The risk is
still there, but the severity depends on the command being called. So,
the issue needs analysis.

### UNIX

An attacker might insert the string **“; cat /etc/hosts”** and the
contents of the UNIX hosts file might be exposed to the attacker if the
command is executed through a shell such as /bin/bash or /bin/sh.

### .NET Example

`namespace ExternalExecution`
`{`
`class CallExternal`
`{`
`static void Main(string[] args)`
`{`
`String arg1=args[0];`
`System.Diagnostics.Process.Start("doStuff.exe", arg1);`
`}`
`}`
`}`

Yet again there is no data validation to speak of here, assuming that
there is no upstream validation occurring in another class.

### Classic ASP Example

```
 <%
   option explicit
   dim wshell
   set wshell = CreateObject("WScript.Shell")
   wshell.run "c:\file.bat " & Request.Form("Args")
   set wshell = nothing
 %>

```

These attacks include calls to the operating system via system calls,
the use of external programs via shell commands, as well as calls to
backend databases via SQL (i.e. SQL injection). Complete scripts written
in Perl, Python, shell, bat, and other languages can be injected into
poorly designed web applications and executed.

## Good Patterns & procedures to prevent OS injection

See the Data Validation section.

## Related Articles

[Command Injection](Command_Injection "wikilink")

[Interpreter Injection](Interpreter_Injection "wikilink")

[Category:OWASP Code Review
Project](Category:OWASP_Code_Review_Project "wikilink") [Category:Input
Validation](Category:Input_Validation "wikilink")