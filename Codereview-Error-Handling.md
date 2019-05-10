__TOC__

## Error Handling

Error Handling is important in a number of ways. It may affect the state
of the application, or leak system information to a user. The initial
failure to prevent the error may cause the application to traverse into
an insecure state. Weak error handling also aids the attacker, as the
errors returned may assist them in constructing correct attack vectors.
A generic error page for most errors is recommended. This approach makes
it more difficult for attackers to identify signatures of potentially
successful attacks. There are methods which can circumvent systems with
leading error handling practices which should be kept in mind; Attacks
such as blind SQL injection using booleanization or response time
characteristics can be used to address such generic responses.

The other key area relating to error handling is the premise of "fail
securely". Errors induced should not leave the application in an
insecure state. Resources should be locked down and released, sessions
terminated (if required), and calculations or business logic should be
halted (depending on the type of error, of course).

An important aspect of secure application development is to prevent
information leakage. Error messages give an attacker great insight into
the inner workings of an application.

''The purpose of reviewing the Error Handling code is to assure that the
application fails safely under all possible error conditions, expected
and unexpected. No sensitive information is presented to the user when
an error occurs. ''

For example, SQL injection is much tougher to successfully execute
without some healthy error messages. It lessens the attack footprint,
and an attacker would have to resort to using “blind SQL injection”
which is more difficult and time consuming.

A well-planned error/exception handling strategy is important for three
reasons:

1.  Good error handling does not give an attacker any information which
    is a means to an end, attacking the application
2.  A proper centralised error strategy is easier to maintain and
    reduces the chance of any uncaught errors “Bubbling up” to the front
    end of an application.
3.  Information leakage can lead to social engineering exploits.

Some development languages provide checked exceptions, which means that
the compiler shall complain if an exception for a particular API call is
not caught. Java and C\# are good examples of this. Languages like C++
and C do not provide this safety net. Languages with checked exception
handling still are prone to information leakage, as not all types of
errors are checked for.

When an exception or error is thrown, we also need to log this
occurrence. Sometimes this is due to bad development, but it can be the
result of an attack or some other service your application relies on
failing.

All code paths that can cause an exception to be thrown should check for
success in order for the exception not to be thrown.

• To avoid a NullPointerException we should check if the object being
accessed is not null.

### Error Handling Should Be Centralized if Possible

When reviewing code it is recommended that you assess the commonality
within the application from a error/exception handling perspective.
Frameworks have error handling resources which can be exploited to
assist in secure programming, and such resources within the framework
should be reviewed to assess if the error handling is "wired-up"
correctly.

  - A generic error page should be used for all exceptions if possible.

This prevents the attacker from identifying internal responses to error
states. This also makes it more difficult for automated tools to
identify successful attacks.

**Declarative Exception Handling**

<exception   key=”bank.error.nowonga”
                    path=”/NoWonga.jsp”
                    type=”mybank.account.NoCashException”/>

This could be found in the struts-config.xml file, a key file when
reviewing the wired-up struts environment

### Java Servlets and JSP

Specification can be done in web.xml in order to handle unhandled
exceptions. When Unhandled exceptions occur, but are not caught in code,
the user is forwarded to a generic error page:

<error-page>
`      `<exception-type>`UnhandledException`</exception-type>
`      `<location>`GenericError.jsp`</location>
</error-page>

Also in the case of HTTP 404 or HTTP 500 errors during the review you
may find:

<error-page>
` `<error-code>`500`</error-code>
` `<location>`GenericError.jsp`</location>
</error-page>

### Failing Securely

Types of errors:

  - The result of business logic conditions not being met.
  - The result of the environment wherein the business logic resides
    fails.
  - The result of upstream or downstream systems upon which the
    application depends fail.
  - Technical hardware / physical failure.

Failures are never expected, but they do occur. In the event of a
failure, it is important not to leave the "doors" of the application
open and the keys to other "rooms" within the application sitting on the
table. In the course of a logical workflow, which is designed based upon
requirements, errors may occur which can be programmatically handled,
such as a connection pool not being available, or a downstream server
not being contactable.

Such areas of failure should be examined during the course of the code
review. It should be examined if all resources should be released in the
case of a failure and during the thread of execution if there is any
potential for resource leakage, resources being memory, connection
pools, file handles etc.

The review of code should also include pinpointing areas where the user
session should be terminated or invalidated. Sometimes errors may occur
which do not make any logical sense from a business logic perspective or
a technical standpoint;

e.g: "A logged in user looking to access an account which is not
registered to that user and such data could not be inputted in the
normal fashion."

Such conditions reflect possible malicious activity. Here we should
review if the code is in any way defensive and kills the user’s session
object and forwards the user to the login page. (Keep in mind that the
session object should be examined upon every HTTP request).

### Information Burial

Swallowing exceptions into an empty catch() block is not advised as an
audit trail of the cause of the exception would be incomplete.

## Generic Error Messages

We should use a localized description string in every exception, a
friendly error reason such as “System Error – Please try again later”.
When the user sees an error message, it will be derived from this
description string of the exception that was thrown, and never from the
exception class which may contain a stack trace, line number where the
error occurred, class name, or method name.

Do not expose sensitive information in exception messages. Information
such as paths on the local file system is considered privileged
information; any internal system information should be hidden from the
user. As mentioned before, an attacker could use this information to
gather private user information from the application or components that
make up the app.

Don’t put people’s names or any internal contact information in error
messages. Don’t put any “human” information, which would lead to a level
of familiarity and a social engineering exploit.

## How to Locate the Potentially Vulnerable Code

### JAVA

IIn Java we have the concept of an error object; the Exception object.
This lives in the Java package java.lang and is derived from the
Throwable object. Exceptions are thrown when an abnormal occurrence has
occurred. Another object derived from Throwable is the Error object,
which is thrown when something more serious occurs.

Information leakage can occur when developers use some exception
methods, which ‘bubble’ to the user UI due to a poor error handling
strategy. The methods are as follows:

printStackTrace()
getStackTrace()

Also important to know is that the output of these methods is printed in
System console, the same as System.out.println(e) where there is an
Exception. Be sure to not redirect the outputStream to PrintWriter
object of JSP, by convention called "out". Ex. printStackTrace(out);

Also another object to look at is the java.lang.system package:

setErr() and the System.err field.

### .NET

In .NET a System.Exception object exists. Commonly used child objects
such as ApplicationException and SystemException are used. It is not
recommended that you throw or catch a SystemException this is thrown by
runtime.

When an error occurs, either the system or the currently executing
application reports it by throwing an exception containing information
about the error, similar to Java. Once thrown, an exception is handled
by the application or by the default exception handler. This Exception
object contains similar methods to the Java implementation such as:

StackTrace
Source
Message
HelpLink
In .NET we need to look at the error handling strategy from the point of
view of global error handling and the handling of unexpected errors.
This can be done in many ways and this article is not an exhaustive
list. Firstly, an Error Event is thrown when an unhandled exception is
thrown.

This is part of the TemplateControl class.

<http://msdn.microsoft.com/library/default.asp?url=/library/en-us/cpref/html/frlrfSystemWebUITemplateControlClassErrorTopic.asp>

Error handling can be done in three ways in .NET

  - In the web.config file's customErrors section.
  - In the global.asax file's Application_Error sub.
  - On the aspx or associated codebehind page in the Page_Error sub

The order of error handling events in .NET is as follows:

1.  On the Page in the Page_Error sub.
2.  The global.asax Application_Error sub
3.  The web.config file

It is recommended to look in these areas to understand the error
strategy of the application.

### Classic ASP

Unlike Java and .NET, classic ASP pages do not have structured error
handling in try-catch blocks. Instead they have a specific object called
"err". This make error handling in a classic ASP pages hard to do and
prone to design errors on error handlers, causing race conditions and
information leakage. Also, as ASP uses VBScript (a subtract of Visual
Basic), sentences like "On Error GoTo label" are not available.

## Vulnerable Patterns for Error Handling

### Page_Error

Page_Error is page level handling which is run on the server side.
Below is an example but the error information is a little too
informative and hence bad practice.

<script language="C#" runat="server">

`Sub Page_Error(Source As Object, E As EventArgs)`
`Dim message As String = `<Font Color="red">`Request.Url.ToString()& Server.GetLastError().ToString()`</font>
`Response.Write(message) // display message `
`End Sub`
` `

</script>

The text in the example above has a number of issues: Firstly, it
redisplays the HTTP request to the user in the form of
Request.Url.ToString() Assuming there has been no data validation prior
to this point, we are vulnerable to cross site scripting attacks\!\!
Secondly, the error message and stack trace is displayed to the user
using Server.GetLastError().ToString() which divulges internal
information regarding the application.

After the Page_Error is called, the Application_Error sub is called.

### Global.asax

When an error occurs, the Application_Error sub is called. In this
method we can log the error and redirect to another page.

`<%@ Import Namespace="System.Diagnostics" %>`
`  `

<script language="C#" runat="server">

`    void Application_Error(Object sender, EventArgs e) {`
`         String Message = "\n\nURL: `<http://localhost/>`" + Request.Path`
`                          + "\n\nMESSAGE:\n " + Server.GetLastError().Message`
`                          + "\n\nSTACK TRACE:\n" + Server.GetLastError().StackTrace;`
`         // Insert into Event Log`
`         EventLog Log = new EventLog();`
`         Log.Source = LogName;`
`         Log.WriteEntry(Message, EventLogEntryType.Error);`
`       Server.Redirect(Error.htm) // this shall also clear the error`
`    }`

</script>

Above is an example of code in Global.asax and the Application_Error
method. The error is logged and then the user is redirected. Unvalidated
parameters are being logged here in the form of Request.Path. Care must
be taken not to log or redisplay unvalidated input from any external
source.

### Web.config

Web.config has custom error tags which can be used to handle errors.
This is called last and if Page_error or Application_error is called
and has functionality, that functionality shall be executed first. As
long as the previous two handling mechanisms do not redirect or clear
(Response.Redirect or a Server.ClearError), this will be called and you
shall be forwarded to the page defined in web.config.

<customErrors defaultRedirect="error.html" mode="On
|Off
|RemoteOnly">
`   `<error statusCode="statuscode" redirect="url"/>
</customErrors>

The “On" directive means that custom errors are enabled. If no
defaultRedirect is specified, users see a generic error. The "Off"
directive means that custom errors are disabled. This allows the
displaying of detailed errors. "RemoteOnly" specifies that custom errors
are shown only to remote clients, and ASP.NET errors are shown to the
local host. This is the default.

<customErrors mode="On" defaultRedirect="error.html">
`    `<error statusCode="500" redirect="err500.aspx"/>
`    `<error statusCode="404" redirect="notHere.aspx"/>
`    `<error statusCode="403" redirect="notAuthz.aspx"/>
</customErrors>

## Leading Practice for Error Handling

### Try & Catch (Java/ .NET)

Code that might throw exceptions should be in a try block and code that
handles exceptions in a catch block. The catch block is a series of
statements beginning with the keyword catch, followed by an exception
type and an action to be taken. These are very similar in Java and .NET

**Example:**

**Java Try-Catch:**

`public class DoStuff {`
`    public static void Main() {`
`        try {`
`            StreamReader sr = File.OpenText("stuff.txt");`
`            Console.WriteLine("Reading line {0}", sr.ReadLine());    `
`        }`
`        catch(Exception e) {`
`            Console.WriteLine("An error occurred. Please leave to room”);`
`    logerror(“Error: “, e);`
`        }`
`    }`
`}`

**.NET Try–Catch**

`public void run() {`
`            while (!stop) {`
`                try {`

`                    // Perform work here`

`                } catch (Throwable t) {`
`                    // Log the exception and continue`
`       WriteToUser(“An Error has occurred, put the kettle on”);`
`                    logger.log(Level.SEVERE, "Unexception exception", t);`
`                }`
`            }`
`        }`

In general, it is best practice to catch a specific type of exception
rather than use the basic catch(Exception) or catch(Throwable) statement
in the case of Java.

In classic ASP there are two ways to do error handling, the first is
using the err object with an On Error Resume Next.

`Public Function IsInteger (ByVal Number)    `
`  Dim Res, tNumber`
`  Number = Trim(Number)`
`  tNumber=Number       `
`  On Error Resume Next                      'If an error occurs continue execution`
`  Number = CInt(Number)                 'if Number is a alphanumeric string a Type Mismatch error will occur`
`  Res = (err.number = 0)                'If there are no errors then return true`
`  On Error GoTo 0               'If an error occurs stop execution and display error`
`  re.Pattern = "^[\+\-]? *\d+$"         'only one +/- and digits are allowed`
`  IsInteger = re.Test(tNumber) And Res`
`End Function`

The second is using an error handler on an error page
(http://support.microsoft.com/kb/299981).

`Dim ErrObj`
`set ErrObj = Server.GetLastError()`
`'Now use ErrObj as the regular err object`

### Releasing resources and good housekeeping

If the language in question has a finally method, use it. The finally
method is guaranteed to always be called. The finally method can be used
to release resources referenced by the method that threw the exception.
This is very important. An example would be if a method gained a
database connection from a pool of connections, and an exception
occurred without finally, the connection object shall not be returned to
the pool for some time (until the timeout). This can lead to pool
exhaustion. finally() is called even if no exception is thrown.

`try {`
`       System.out.println("Entering try statement");`
`       out = new PrintWriter(new FileWriter("OutFile.txt"));`
`     //Do Stuff….`

`   } catch (Exception e) {`
`       System.err.println("Error occurred!”);`

`   } catch (IOException e) {`
`       System.err.println("Input exception ");`

`   } finally {`

`       if (out != null) { `
`           out.close(); // RELEASE RESOURCES`
`       } `
`   }`

A Java example showing finally() being used to release system resources.

### Classic ASP

For Classic ASP pages it is recommended to enclose all cleaning in a
function and call it into an error handling statement after an "On Error
Resume Next".

### Centralised exception handling (Struts Example)

Building an infrastructure for consistent error reporting proves more
difficult than error handling. Struts provides the ActionMessages and
ActionErrors classes for maintaining a stack of error messages to be
reported, which can be used with JSP tags like \<html: error\> to
display these error messages to the user.

To report a different severity of a message in a different manner (like
error, warning, or information) the following tasks are required:

1.  Register, instantiate the errors under the appropriate severity
2.  Identify these messages and show them in a consistent manner.

Struts ActionErrors class makes error handling quite easy:

`ActionErrors errors = new ActionErrors()`
`errors.add("fatal", new ActionError("....")); `
`errors.add("error", new ActionError("....")); `
`errors.add("warning", new ActionError("...."));`
`errors.add("information", new ActionError("....")); `
`saveErrors(request,errors); // Important to do this`

Now that we have added the errors, we display them by using tags in the
HTML page.

<logic:messagePresent property="error">` `
<html:messages property="error" id="errMsg" >
`    `<bean:write name="errMsg"/>
</html:messages>
</logic:messagePresent >

### Classic ASP

For classic ASP pages you need to do some IIS configuration, follow the
same link for more information <http://support.microsoft.com/kb/299981>

[Category:OWASP Code Review
Project](Category:OWASP_Code_Review_Project "wikilink")