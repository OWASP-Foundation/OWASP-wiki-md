## This is a draft

__TOC__

## Error Handling

Proper error handling is important in two ways:

1.  It may affect the state of the application
    1.  The initial failure to prevent the error may cause the
        application to traverse into an insecure state. This covers the
        key premise of **failing securely**
        *<include reference to antipatterns>*, errors induced should not
        leave the application in an insecure state. Resources should be
        locked down and released, sessions terminated (if required), and
        calculations or business logic should be halted (depending on
        the type of error, of course).
2.  It may leak system information to a user
    1.  An important aspect of secure application development is to
        prevent information leakage. Error messages give an attacker
        great insight into the inner workings of an application. Weak
        error handling also aids the attacker, as the errors returned
        may assist them in constructing correct attack vectors.

A generic error page for most errors is recommended, this approach makes
it more difficult for attackers to identify signatures of potentially
successful attacks such as blind SQL injection using booleanization
*<should include reference>* or analysis of response time
characteristics.

### Reviewing Error Handling

The purpose of reviewing the Error Handling code is to assure that the
application fails safely under all possible error conditions, expected
and unexpected. No sensitive information is presented to the user when
an error occurs. A company coding guidelines should include sections on
Error Handling and how it should be controlled by an application suite,
this will allow developers to code against this guidelines as well as
review against them.

For example, SQL injection is much tougher to successfully execute
without some healthy error messages. It lessens the attack footprint,
and an attacker would have to resort to using “blind SQL injection”
which is more difficult and time consuming.

A well-planned error/exception handling guideline is important in a
company for three reasons:

1.  Good error handling does not give an attacker any information which
    is a means to an end, attacking the application
2.  A proper centralised error strategy is easier to maintain and
    reduces the chance of any uncaught errors “bubbling up” to the front
    end of an application.
3.  Information leakage could lead to social engineering exploits, for
    example if the hosting companies name is returned, or some employees
    name can be seen.

Regardless of whether the development language provide checked
exceptions or not, reviewers should remember:

1.  Not all errors are exceptions
    1.  Don't rely on exception handling to be your only way of handling
        errors, handle all case statement 'default' sections, ensure all
        'if' statements have their 'else' clauses covered, ensure that
        all exits from a function (e.g. return statements, exceptions,
        etc) are covered. RAII concepts (e.g. auto pointers and the
        like) are an advantage here. In languages like Java and C\#,
        remember that errors are different from exceptions (different
        hierarchy) and should be handled.
2.  Catching an exception is not automatically handling it
    1.  You've caught your exception, so how do you handle it? For many
        cases this should be obvious enough, based on your business
        logic, but for some (e.g. out of memory, array index out of
        bounds, etc) the handling many not be so simple.
3.  Don't catch more that you can handle
    1.  Catch all clauses (e.g. 'catch(Exception e)' in Java & C\# or
        'catch(...) in C++) should be avoided as you will not know what
        type of expcetion you are handling, and if you don't know the
        exception type, how do you accurately handle it? It could be
        that the downstream server is not responding, or a user may have
        exceeded their quota, or you may be out of memory, these issues
        should be handled in different ways and thus should be caught in
        exception clauses that are specific.

When an exception or error is thrown, we also need to log this
occurrence. Sometimes this is due to bad development, but it can be the
result of an attack or some other service your application relies on
failing. This has to be imagined in the production scenario, if your
application handles 'failing securely' by returning an error response to
the client, and since we don't want to leak informaiton that error will
be generic, we need to have some way of identifying why the failure
occured. If your customer reports 1000's of errors occured last night,
you know that customer is going to want to know why. If you don't have
proper logging and tracability coded into your application then you will
not be able to establish if those errors were due to some attempted
hack, or an error in your business logic when handling a particular type
of error.

All code paths that can cause an exception to be thrown should check for
success in order for the exception not to be thrown. This could be hard
to impossible for a manual code review to cover, especially for large
bodies of code. However if there is a debug version of the code, then
modules/functions could throw relevant exceptions/errors and an
automated tool can ensure the state and error responses from the module
is as expected. This then means the code reviewer has the job of
ensuring all relevant exceptions/errors are tested in the debug code.

### Centralized Error Handling

When reviewing code it is recommended that you assess the commonality
within the application from a error/exception handling perspective.
Frameworks have error handling resources which can be exploited to
assist in secure programming, and such resources within the framework
should be reviewed to assess if the error handling is "wired-up"
correctly. A generic error page should be used for all exceptions if
possible as this prevents the attacker from identifying internal
responses to error states. This also makes it more difficult for
automated tools to identify successful attacks.

For JSP structs this could be controlled in the struts-config.xml file,
a key file when reviewing the wired-up struts environment:

<exception key=”bank.error.nowonga”
                    path=”/NoWonga.jsp”
                    type=”mybank.account.NoCashException”/>

Specification can be done for JSP in web.xml in order to handle
unhandled exceptions. When unhandled exceptions occur, but are not
caught in code, the user is forwarded to a generic error page:

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

For IIS development the 'Application_Error()' handler will allow the
application to catch all uncaught exceptions and handle them in a
consistent way. Note this is important or else there is a chance your
exception informaiton could be sent back to the client in the response.

For Apache development, returning failures from handlers or modules can
prevent an further processing by the Apache engine and result in an
error response from the server. Response headers, body, etc can be set
by by the handler/module or can be configured using the "ErrorDocument"
configuration.

We should use a localized description string in every exception, a
friendly error reason such as “System Error – Please try again later”.
When the user sees an error message, it will be derived from this
description string of the exception that was thrown, and never from the
exception class which may contain a stack trace, line number where the
error occurred, class name, or method name.

Do not expose sensitive information like exception messages. Information
such as paths on the local file system is considered privileged
information; any internal system information should be hidden from the
user. As mentioned before, an attacker could use this information to
gather private user information from the application or components that
make up the app.

Don’t put people’s names or any internal contact information in error
messages. Don’t put any “human” information, which would lead to a level
of familiarity and a social engineering exploit.

### Failing Securely

There can be many different reasons why an application may fail, for
example:

  - The result of business logic conditions not being met.
  - The result of the environment wherein the business logic resides
    fails.
  - The result of upstream or downstream systems upon which the
    application depends fail.
  - Technical hardware / physical failure.

Failures are like the Spanish Inquisition; popularly nobody expected the
Spanish Inquisition (see Monty Python) but in real life the Spanish knew
when an inquisition was going to occur and were prepared for it,
similarly in an application, though you don't expect errors to occur
your code should be prepared for them to happen. In the event of a
failure, it is important not to leave the "doors" of the application
open and the keys to other "rooms" within the application sitting on the
table. In the course of a logical workflow, which is designed based upon
requirements, errors may occur which can be programmatically handled,
such as a connection pool not being available, or a downstream server
returning a failure.

Such areas of failure should be examined during the course of the code
review. It should be examined if resources should be released such as
memory, connection pools, file handles etc.

The review of code should also include pinpointing areas where the user
session should be terminated or invalidated. Sometimes errors may occur
which do not make any logical sense from a business logic perspective or
a technical standpoint, for example a logged in user looking to access
an account which is not registered to that user. Such conditions reflect
possible malicious activity. Here we should review if the code is in any
way defensive and kills the user’s session object and forwards the user
to the login page. (Keep in mind that the session object should be
examined upon every HTTP request).

## How to Locate the Potentially Vulnerable Code

### Java

In Java we have the concept of an error object; the Exception object.
This lives in the Java package java.lang and is derived from the
Throwable object. Exceptions are thrown when an abnormal occurrence has
occurred. Another object derived from Throwable is the Error object,
which is thrown when something more serious occurs. The Error object can
be caught in a catch clause, but cannot be handled, the best you can do
is log some information about the Error and then re-throw it.

Information leakage can occur when developers use some exception
methods, which ‘bubble’ to the user UI due to a poor error handling
strategy. The methods are as follows:

`printStackTrace()`
`getStackTrace()`

Also important to know is that the output of these methods is printed in
System console, the same as System.out.println(e) where there is an
Exception. Be sure to not redirect the outputStream to PrintWriter
object of JSP, by convention called "out", for example:

`printStackTrace(out); `

Note it is possible to change where system.err and system.out write to
(like modifing fd 1 & 2 in bash or C/C++), using the java.lang.system
package:

setErr() for the System.err field and setOut() for the System.out field.

This could be used on a process wide basis to ensure no output gets
written to standard error or standard out (which can be reflected back
to the client) but instead write to a configured log file.

### .NET

In .NET a System.Exception object exists and has commonly used child
objects such as ApplicationException and SystemException are used. It is
not recommended that you throw or catch a SystemException this is thrown
by runtime.

When an error occurs, either the system or the currently executing
application reports it by throwing an exception containing information
about the error, similar to Java. Once thrown, an exception is handled
by the application or by the default exception handler. This Exception
object contains similar methods to the Java implementation such as:

`StackTrace`
`Source`
`Message`
`HelpLink`

In .NET we need to look at the error handling strategy from the point of
view of global error handling and the handling of unexpected errors.
This can be done in many ways and this article is not an exhaustive
list. Firstly, an Error Event is thrown when an unhandled exception is
thrown.

This is part of the TemplateControl class, see
<http://msdn.microsoft.com/library/default.asp?url=/library/en-us/cpref/html/frlrfSystemWebUITemplateControlClassErrorTopic.asp>

Error handling can be done in three ways in .NET, executed in the
following order:

  - On the aspx or associated codebehind page in the Page_Error.
  - In the global.asax file's Application_Error (as mentioned before).
  - In the web.config file's customErrors section.

It is recommended to look in these areas to understand the error
strategy of the application.

### Classic ASP

Unlike Java and .NET, classic ASP pages do not have structured error
handling in try-catch blocks. Instead they have a specific object called
"err". This makes error handling in a classic ASP pages hard to do and
prone to design errors on error handlers, causing race conditions and
information leakage. Also, as ASP uses VBScript (a subtract of Visual
Basic), sentences like "On Error GoTo label" are not available.

### C++

In the C++ language, any object or built in type can be thrown. However
there is a STL type std::exception which is supposed to be used as the
parent of any user defined exception, indeed this type is used in the
STL and many libraries as the parent type of all exceptions. Having
std::exception encourages developers to create a hierarchy of exceptions
which match the exception usage and means all exceptions can be caught
by catching a std::exception object (instead of a 'catch (...)' block).
Unlike Java, even errors that you can't recover from (e.g.
std::bad_alloc which means your out of memory) derive from
std::exception, so a 'catch( std::exception& e)' is similar to 'catch
(...)' except that it allows you access to the exception so you can know
what occurred and possibly print some error information using e.what().

There are many logging libraries for C++, so if your codebase uses a
particular logging class look for usages of that logger for anywhere
sensitive information can be written to the logs.

## Vulnerable Patterns for Error Handling in IIS

### Page_Error

Page_Error is page level handling which is run on the server side in
.NET. Below is an example but the error information is a little too
informative and hence bad practice.

<script language="C#" runat="server">

`Sub Page_Error(Source As Object, E As EventArgs)`
`Dim message As String = Request.Url.ToString()& Server.GetLastError().ToString()`
`Response.Write(message) // display message `
`End Sub`

</script>

The text in the example above has a number of issues:

  - Firstly, it displays the HTTP request to the user in the form of
    Request.Url.ToString(). Assuming there has been no data validation
    prior to this point, we are vulnerable to cross site scripting
    attacks\!
  - Secondly, the error message and stack trace is displayed to the user
    using Server.GetLastError().ToString() which divulges internal
    information regarding the application.

After the Page_Error is called, the Application_Error sub is called.

### Global.asax

When an error occurs, the Application_Error function is called. In this
method we can log the error and redirect to another page. In fact
catching errors in Application_Error instead of Page_Error would be an
example of centralizing errors as described earlier,

`<%@ Import Namespace="System.Diagnostics" %>`

<script language="C#" runat="server">

`void Application_Error(Object sender, EventArgs e) {`
`  String Message = "\n\nURL: `<http://localhost/>`" + Request.Path`
`                          + "\n\nMESSAGE:\n " + Server.GetLastError().Message`
`                          + "\n\nSTACK TRACE:\n" + Server.GetLastError().StackTrace;`
`  // Insert into Event Log`
`  EventLog Log = new EventLog();`
`  Log.Source = LogName;`
`  Log.WriteEntry(Message, EventLogEntryType.Error);`
`  Server.Redirect(Error.htm) // this shall also clear the error`
`}`

</script>

Above is an example of code in Global.asax and the Application_Error
method. The error is logged and then the user is redirected.
Non-validated parameters are being logged here in the form of
Request.Path. Care must be taken not to log or display non-validated
input from any external source. *<link to XSS>*

### Web.config

Web.config has custom error tags which can be used to handle errors.
This is called last and if Page_error or Application_error is called
and has functionality, that functionality shall be executed first. If
the previous two handling mechanisms do not redirect or clear
(Response.Redirect or a Server.ClearError), this will be called and you
shall be forwarded to the page defined in web.config in the customErrors
section, which is configured as follows:

<customErrors mode="<On
|Off
|RemoteOnly>" defaultRedirect="<default redirect page>">
` `<error statusCode="<HTTP status code>`" redirect="`<specific redirect page for listed status code>`"/>`
</customErrors>

The "mode" attribute value of "On" means that custom errors are enabled
whilst the "Off" value means that custom errors are disabled. The "mode"
attribute can also be set to "RemoteOnly" which specifies that custom
errors are shown only to remote clients and ASP.NET errors are shown to
requests coming from the the local host. If the "mode" attribute is not
set then it defaults to "RemoteOnly".

When an error occurs, if the status code of the response matches one of
the error elements, then the relevent 'redirect' value is returned as
the error page. If the status code does not match then the error page
from the 'defaultRedirect' attribute will be displayed. If no value is
set for 'defaultRedirect' then a generic IIS error page is returned.

An example of the customErrors section completed for an application is
as follows:

<customErrors mode="On" defaultRedirect="error.html">
`    `<error statusCode="500" redirect="err500.aspx"/>
`    `<error statusCode="404" redirect="notHere.aspx"/>
`    `<error statusCode="403" redirect="notAuthz.aspx"/>
</customErrors>

## Vulnerable Patterns for Error Handling in Apache

In Apache you have two choices in how to return error messages to the
client:

1.  You can write the error status code into the req object and write
    the response to appear the way you want, then have you handler
    return 'DONE' (which means the Apache framework will not allow any
    further handlers/filters to process the request and will send the
    response to the client.
2.  Your handler or filter code can return pre-defined values which will
    tell the Apache framework the result of your codes processsing
    (essentially the HTTP status code). You can then configure what
    error pages should be returned for each error code.

In the interest of centralizing all error code handling, option 2 can
make more sense. To return a specific pre-defined value from your
handler, refer to the Apache documentation for the list of values to
use, and then return from the handler function as shown in the following
example:

`static int my_handler(request_rec *r)`
`{`
`    if ( problem_processing() )`
`    { `
`      return HTTP_INTERNAL_SERVER_ERROR;`
`    }`

`    ... continue processing request ...`
`}`

*\<what happens if an uncaught exception occurs in the filter/handler?
Will httpd core like any C++ thread?\>*

In the httpd.conf file you can then specify which page should be
returned for each error code using the 'ErrorDocument' directive. The
format of this directive is as follows:

`ErrorDocument <3-digit-code> `<action>

... where the 3 digit code is the HTTP response code set by the handler,
and the action is a local or external URL to be returned, or specific
text to display. The following examples are taken from the Apache
ErrorDocument documentation
(https://httpd.apache.org/docs/2.4/custom-error.html) which contains
more information and options on ErrorDocument directives:

`ErrorDocument 500 "Sorry, our script crashed. Oh dear"`
`ErrorDocument 500 /cgi-bin/crash-recover`
`ErrorDocument 500 `<http://error.example.com/server_error.html>
`ErrorDocument 404 /errors/not_found.html `
`ErrorDocument 401 /subscription/how_to_subscribe.html`

## Leading Practice for Error Handling

### Try & Catch (Java/.NET/C++)

Code that might throw exceptions should be in a try block and code that
handles exceptions in a catch block. The catch block is a series of
statements beginning with the keyword catch, followed by an exception
type and an action to be taken.

**Example:**

**Java Try-Catch:**

`public class DoStuff {`
`    public static void Main() {`
`        try {`
`            StreamReader sr = File.OpenText("stuff.txt");`
`            Console.WriteLine("Reading line {0}", sr.ReadLine());    `
`        }`
`        catch(MyClassExtendedFromException e) {`
`            Console.WriteLine("An error occurred. Please leave to room”);`
`        logerror(“Error: “, e);`
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
`            WriteToUser(“An Error has occurred, put the kettle on”);`
`                    logger.log(Level.SEVERE, "Unexception exception", t);`
`                }`
`            }`
`        }`

**C++ Try–Catch**

`void perform_fn() {`
`  try {`
`     // Perform work here`

`  } catch ( const MyClassExtendedFromStdException& e) {`
`     // Log the exception and continue`
`     WriteToUser(“An Error has occurred, put the kettle on”);`
`     logger.log(Level.SEVERE, "Unexception exception", e);`
`  }`
`}`

In general, it is best practice to catch a specific type of exception
rather than use the basic catch(Exception) or catch(Throwable) statement
in the case of Java.

### The Order Of Catching Exceptions

Keep in mind that many languages will attempt to match the thrown
exception to the catch clause even if it means matching the thrown
exception to a parent class. Also remember that catch clauses are
checked in the order they are coded on the page. This could leave you in
the situation where a certain type of exception might never be handled
correctly, take the following example where 'non_even_argument' is a
subclass of 'std::invalid_argument':

`class non_even_argument : public std::invalid_argument {`
`public:`
` explicit non_even_argument (const string& what_arg);`
`};`

`void do_fn()`
`{`
`   try`
`   {`
`      // Perform work that could throw `
`   }`
`   catch ( const std::invalid_argument& e )`
`   {`
`      // Perform generic invalid argument processing and return failure`
`   }`
`   catch ( const non_even_argument& e )`
`   {`
`      // Perform specific processing to make argument even and continue processing`
`   }`
`}`

The problem with this code is that when a 'non_even_argument is
thrown, the catch branch handling 'std::invalid_argument' will always
be executed as it is a parent of 'non_even_argument' and thus the
runtime system will consider it a match (this could also lead to
slicing). Thus you need to be aware of the hierarchy of your exception
objects and ensure that you list the catch for the more specific
exceptions first in your code.

### Finally

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

`   } catch (IOException e) {`
`       System.err.println("Input exception ");`

`   } catch (Exception e) {`
`       System.err.println("Error occurred!”);`

`   } finally {`

`       if (out != null) { `
`           out.close(); // RELEASE RESOURCES`
`       } `
`   }`

A Java example showing finally() being used to release system resources.

### Classic ASP Error Handling

In classic ASP there are two ways to do error handling, the first is
using the err object with a "On Error Resume Next" and "On Error GoTo
0".

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

#### RAII

RAII is Resource Acquisition Is Initialization, which is a way of saying
that when you first create an instance of a type, it should be fully
setup (or as much as possible) so that it's in a good state. Another
advantage of RAII is how objects are disposed of, effectively when an
object instance is no longer needed then it resources are automatically
returned when the object goes out of scope (C++) or when it's 'using'
block is finished (C\# 'using' directive which calls the Dispose method,
or Java 7's try-with-resources feature) *\<add reference to
<http://docs.oracle.com/javase/7/docs/technotes/guides/language/try-with-resources.html>
\>*.

RAII has the advantage that programmers (and users to libraries) don't
need to explicitly delete objects, the objects will be removed
themselves, and in the process of removing themselves (destructor or
Dispose)

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

For classic ASP pages you need to do some IIS configuration, follow
<http://support.microsoft.com/kb/299981> for more information.

[Category:OWASP Code Review
Project](Category:OWASP_Code_Review_Project "wikilink")