[OWASP Code Review Guide Table of
Contents](OWASP_Code_Review_Guide_Table_of_Contents "wikilink")__TOC__

Contact author: [Eoin Keary](mailto:eoin.keary@owasp.org)

## Introduction

Injection flaws allow attackers to pass malicious code through a web
application to another sub system. Depending on the subsystem different
types of injection attack can be performed: RDBMS: SQL Injection
WebBrowser/Appserver: SQL Injection OS-shell: Operating system commands
Calling external applications from your application.

## How to locate the potentially vulnerable code

Many developers believe text fields are the only areas for data
validation. This is an incorrect assumption. Any external input must be
data validated:

Text fields, List boxes, radio buttons, check boxes, cookies, HTTP
header data, HTTP post data, hidden fields, parameter names and
parameter values. … This is not an exhaustive list.

“Process to process” or “entity-to-entity” communication must be
investigated also. Any code that communicates with an upstream or
downstream process and accepts input from it must be reviewed.

All injection flaws are input validation errors. The presence of an
injection flaw is an indication of incorrect data validation on the
input received from an external source outside the boundary of trust,
which gets more blurred every year.

Basically for this type of vulnerability we need to find all input
streams into the application. This can be from a users browser, CLI or
fat client but also from upstream processes that “feed” our application.

An example would be to search the code base for the use of API’s or
packages that are normally used for communication purposes.

The **java.io**, **java.sql**, **java.net**, **java.rmi**, **java.xml**
packages are all used for application communication. Searching for
methods from those packages in the code base can yield results. A less
“scientific” method is to search for common keywords such as “UserID”,
“LoginID” or “Password”.

## Vulnerable Patterns for OS injection

What we should be looking for are relationships between the application
and the operating system. The application utilising functions of the
underlying operating system.

In java using the Runtime object, **java.lang.Runtime** does this. In
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
`       rt.exec("doStuff.exe " +”-“ +myUid); // Call exe with userID`
`   }catch(Exception e)`
`       {`
`e.printStackTrace();`
`       }`
`   }`
`}`

Ok, so the method executeCommand calls ***doStuff.exe*** via the
***java.lang.runtime*** static method ***getRuntime()***. The parameter
passed is not validated in any way in this class. We are assuming that
the data has not been data validated prior to calling this method.
*Transactional analysis should have encountered any data validation
prior to this point.* Inputting “Joe69” would result in the following MS
DOS command: ***doStuff.exe –Joe69*** Lets say we input ***Joe69 &
netstat –a*** we would get the following response: The exe doStuff would
execute passing in the User Id Joe69, but then the dos command
***netstat*** would be called. How this works is the passing of the
parameter “&” into the application, which in turn is used as a command
appender in MS DOS and hence the command after the & character is
executed.

UNIX: An attacker might insert the string **“; cat /etc/hosts”** the
contents of the UNIX hosts file might be exposed to the attacker.

.NET Example:

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

Yet again there is no data validation to speak of here. Assuming no
upstream validation occurring in another class.

These attacks include calls to the operating system via system calls,
the use of external programs via shell commands, as well as calls to
backend databases via SQL (i.e., SQL injection). Complete scripts
written in perl, python, shell, bat and other languages can be injected
into poorly designed web applications and executed.

## Good Patterns & procedures to prevent OS injection

See the Data Validation section.

## Related Articles

[Interpreter Injection](Interpreter_Injection "wikilink")

[Category:OWASP Code Review
Project](Category:OWASP_Code_Review_Project "wikilink") [Category:Input
Validation](Category:Input_Validation "wikilink")