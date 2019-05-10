[OWASP Code Review Guide Table of
Contents](OWASP_Code_Review_Guide_Table_of_Contents "wikilink")__TOC__

## Error, Exception handling & Logging.

Contact author: [Eoin Keary](mailto:eoinkeary@owasp.org)

An important aspect of secure application development is to prevent
information leakage. Error messages give an attacker great insight into
the inner workings of an application.

The purpose of reviewing the Error Handling code is to assure the
application fails safely under all possible error conditions, expected
and unexpected. No sensitive information is presented to the user when
an error occurs.

For example SQL injection is much tougher to successfully pull off
without some healthy error messages. It lessens the attack footprint and
our attacker would have to resort to use “blind SQL injection” which is
more difficult and time consuming.

A well-planned error/exception handling strategy is important for three
reasons:

1.  Good error handling does not give an attacker any information which
    is a means to an end, attacking the application
2.  A proper centralised error strategy is easier to maintain and
    reduces the chance of any uncaught errors “Bubbling up” to the front
    end of an application.
3.  Information leakage can lead to social engineering exploits.

Some development languages provide checked exceptions which mean that
the compiler shall complain if an exception for a particular API call is
not caught Java and C\# are good examples of this. Languages like C++
and C do not provide this safety net. Languages with checked exception
handling still are prone to information leakage as not all types of
error are checked for.

When an exception or error is thrown we also need to log this
occurrence. Sometimes this is due to bad development, but it can be the
result of an attack or some other service your application relies on
failing.

All code paths that can cause an exception to be thrown should check for
success in order for the exception not to be thrown.

To avoid a NullPointerException we should check is the object being
accessed is not null.

## Generic error messages

We should use a localized description string in every exception, a
friendly error reason such as “System Error – Please try again later”.
When the user sees an error message, it will be derived from this
description string of the exception that was thrown, and never from the
exception class which may contain a stack trace, line number where the
error occurred, class name or method name.

Do not expose sensitive information in exception messages. Information
such as paths on the local file system is considered privileged
information; any system internal information should be hidden from the
user. As mentioned before an attacker could use this information to
gather private user information from the application or components that
make up the app.

Don’t put people’s names or any internal contact information in error
messages. Don’t put any “human” information, which would lead to a level
of familiarity and a social engineering exploit.

## How to locate the potentially vulnerable code

### JAVA

In java we have the concept of an error object, the Exception object.
This lives in the java package java.lang and is derived from the
Throwable object Exceptions are thrown when an abnormal occurrence has
occurred. Another object derived from Throwable is the Error object,
which is thrown when something more serious occurs.

Information leakage can occur when developers use some exception
methods, which ‘bubble’ to the user UI due to a poor error handling
strategy. The methods are as follows: printStackTrace() getStackTrace()

Also another object to look at is the java.lang.system package:

setErr() and the System.err field.

### .NET

In .NET a System.Exception object exists. Commonly used child objects
such as ApplicationException and SystemException are used. It is not
recommended that you throw or catch a SystemException this is thrown by
runtime.

When an error occurs, either the system or the currently executing
application reports it by throwing an exception containing information
about the error, similar to java. Once thrown, an exception is handled
by the application or by the default exception handler. This Exception
object contains similar methods to the java implementation such as:

StackTrace Source Message HelpLink

In .NET we need to look at the error handling strategy from the point of
view of global error handling and the handling of unexpected errors.
This can be done in many ways and this article is not an exhaustive
list. Firstly an Error Event is thrown when an unhandled exception is
thrown. This is part of the TemplateControl class.

<http://msdn.microsoft.com/library/default.asp?url=/library/en-us/cpref/html/frlrfSystemWebUITemplateControlClassErrorTopic.asp>

## Error handling can be done in three ways in .NET

  - In the web.config file's customErrors section.
  - In the global.asax file's Application_Error sub.
  - On the aspx or associated codebehind page in the Page_Error sub

The order of error handling events in .NET is as follows:

1.  On the Page in the Page_Error sub.
2.  The global.asax Application_Error sub
3.  The web.config file

It is recommended to look in these areas to understand the error
strategy of the application.

## Vulnerable Patterns for Error Handling

### Page_Error

Page_Error is page level handling which is run on the server side.
Below is an example but the error information is a little too
informative and hence bad practice.

**FIXME: code formatting**

\<script language="C\#" runat="server"\> Sub Page_Error(Source As
Object, E As EventArgs) Dim message As String = "\<font face=verdana
color=red\>\<h1\>" & Request.Url.ToString()& "\</h1\>" & "\<pre\>\<font
color='red'\>" & Server.GetLastError().ToString()& "\</pre\>\</font\>"
Response.Write(message) // display message End Sub \</script\>

The red text in the example above has a number of issues: Firstly it
redisplays the HTTP request to the user in the form of
Request.Url.ToString() Assuming there has been no data validation prior
to this point we are vulnerable to cross site scripting attacks\!\!
Secondly the error message and stack trace is displayed to the user
using Server.GetLastError().ToString() which divulges internal
information regarding the application.

After the Page_Error is called, the Application_Error sub is called:

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

Web.config has a custom errors tag which can be used to handle errors.
This is called last and if Page_error or Application_error called and
has functionality that functionality shall be executed first. As long as
the previous two handling mechanisms do not redirect or clear
(Response.Redirect or a Server.ClearError) this shall be called. And you
shall be forwarded to the page defined in web.config

<customErrors defaultRedirect="error.html" mode="On
|Off
|RemoteOnly">
`   `<error statusCode="statuscode" redirect="url"/>
</customErrors>

The “On" directive means that custom errors are enabled. If no
defaultRedirect is specified, users see a generic error. "Off" directive
means that custom errors are disabled. This allows display of detailed
errors. "RemoteOnly" specifies that custom errors are shown only to
remote clients, and ASP.NET errors are shown to the local host. This is
the default.

<customErrors mode="On" defaultRedirect="error.html">
`    `<error statusCode="500" redirect="err500.aspx"/>
`    `<error statusCode="404" redirect="notHere.aspx"/>
`    `<error statusCode="403" redirect="notAuthz.aspx"/>
</customErrors>

## Best Practices for Error Handling

### Try & Catch (Java/ .NET)

Code that might throw exceptions should be in a try block and code that
handles exceptions in a catch block. The catch block is a series of
statements beginning with the keyword catch, followed by an exception
type and an action to be taken. These are very similar in Java and .NET

Example:

Java Try-Catch:

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

.NET try – catch

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

### Releasing resources and good housekeeping

If the language in question has a finally method use it. The finally
method is guaranteed to always be called. The finally method can be used
to release resources referenced by the method that threw the exception.
This is very important. An example would be if a method gained a
database connection from a pool of connections and an exception occurred
without finally the connection object shall not be returned to the pool
for some time (until the timeout). This can lead to pool exhaustion.
finally() is called even if no exception is thrown.

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

### Centralised exception handling (Struts Example)

Building an infrastructure for consistent error reporting proves more
difficult than error handling. Struts provides the ActionMessages &
ActionErrors classes for maintaining a stack of error messages to be
reported, which can be used with JSP tags like \<html: error\> to
display these error messages to the user.

To report a different severity of a message in a different manner (like
error, warning, or information) the following tasks are required:

  - Register, instantiate the errors under the appropriate severity
  - Identify these messages and show them in a constant manner.

Struts ActionErrors class makes error handling quite easy:

`ActionErrors errors = new ActionErrors()`
`errors.add("fatal", new ActionError("....")); `
`errors.add("error", new ActionError("....")); `
`errors.add("warning", new ActionError("...."));`
`errors.add("information", new ActionError("....")); `
`saveErrors(request,errors); // Important to do this`

Now we have added the errors we display them by using tags in the HTML
page.

<logic:messagePresent property="error">` `
<html:messages property="error" id="errMsg" >
`    `<bean:write name="errMsg"/>
</html:messages>
</logic:messagePresent >

[Category:OWASP Code Review
Project](Category:OWASP_Code_Review_Project "wikilink")