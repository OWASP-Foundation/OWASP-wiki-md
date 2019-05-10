# Description

An exception is any error condition or unexpected behavior that is
encountered by your application. There are several key security concerns
to be aware of when handling exceptions in .NET web applications:

  - Preventing system information leakage that could aid a malicious
    user.
  - Ensuring the application fails securely under all circumstances,
    both expected and not expected.
  - Using a centralized error strategy to reduce points of failure and
    promote consistency.
  - Log when exceptions are thrown and include sufficient detail for
    security auditing.

# Displaying Errors

When your application displays error messages, it should not give away
information that a malicious user might find helpful in attacking your
system. For example, if your application fails while attempting to
connect to a database, it should not display an error message that
includes the connection string being used.

The default display mechanism for unhandled exceptions in ASP.NET is
controlled via the *<customErrors>* element in the web.config file. This
element includes a *mode* attribute that can be set to: *Off*, *On*, or
*RemoteOnly*. This mode setting should never be set to *Off* in a
production environment because it will cause exception details to be
displayed to the end user which may include sensitive information about
the system.

    <customErrors mode="RemoteOnly" defaultRedirect="/Error">
      <error statusCode="404" redirect="/Error?id=404" />
      <error statusCode="403" redirect="/Error?id=403" />
    </customErrors>

## HTTP Status Codes

When reviewing error responses be careful that a malicious user is not
able to glean any potentially sensitive information about the system
from the status code returned. For example: an API search that takes a
tenant ID parameter and returns an HTTP 404 response for no results, and
an HTTP 500 response if the tenant ID does not exist. An attacker could
potentially leverage this information to determine if a tenant ID is
valid or not. One solution would be to catch the exception thrown when a
supplied tenant ID does not exist, and return an HTTP 404 status code
with the error response.

# Where to Catch Exceptions

There are a variety of places within a typical web application where
exceptions can be caught and logged. First and foremost you want to
catch exceptions at an application level and ensure they are handled
properly. Often this may be the only location necessary to catch
exceptions. In addition to this, handling exceptions at lower levels in
the application will give you more control and may provide you with more
detailed contextual information.

If you use try/catch blocks to handle exceptions be aware of two
concerns:

1.  Avoid using the *Exception* class but instead use a descendant class
    that is the most applicable to the condition you are expecting.
2.  Be careful not to just catch an exception and continue processing.
    Always use the *throw* statement to re-throw the exception unless
    you are certain that this will not leave the application in an
    unexpected and potentially vulnerable state.

<!-- end list -->

    try
    {
      Emailer.SendNewUserActivation(this)
    }
    catch (SmtpException ex)
    {
      this.Delete();
      throw;
    }

# Logging Exception Details

Logging exception details is important when you need to properly
diagnose error conditions with the system. You don't want this detail to
be displayed on an error page because it may inadvertently aid a
malicious user in an attack. Logging allows your error pages to display
a simple generic message alerting end users that an error has occurred,
with possibly some options for contacting support. The detail you need
for assisting with these issues will be kept securely in the log store.

You can use several methods to log exception events, including popular
third party libraries: log4net, nlog, Common.Logging, etc. An
out-of-the-box solution included with .NET is System.Diagnostics Tracing
as shown in the code examples in this article. These trace messages can
then be written out using trace listeners such as the
*TextWriterTraceListener* configured here.

    <system.diagnostics>
      <trace autoflush="true">
        <listeners>
          <add name="EventTracer"
            type="System.Diagnostics.TextWriterTraceListener, System, Version=2.0.3600.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            initializeData="<app root directory>\eventtrace.log" />
        </listeners>
      </trace>
    </system.diagnostics>

One benefit to using System.Diagnostics Tracing in your code is that
most logging frameworks already support including these events and
writing them to a variety of output types.

For detailed security guidance specific to logging see [Reviewing Code
for Logging Issues](Reviewing_Code_for_Logging_Issues "wikilink").

## Application Level

The following code example shows how to create an error handler in the
Global.asax.cs file that will catch and log all unhandled ASP.NET errors
at the application level. Unhandled exceptions must be logged within
*Application_Error* rather than in a subsequent page defined by
*<customErrors>*, because the exception details are only available at
this point.

    void Application_Error(object sender, EventArgs e)
    {
      // Get the exception object.
      var exception = Server.GetLastError();

      // Log exception details. Be sure to include items like client IP
      // address and current authenticated user if applicable.
      System.Diagnostics.Trace.TraceError(exception.ToString());
    }

## Server.ClearError

Use the *Server.ClearError()* method with caution when handling
exceptions. This method will clear the exception state and allow
execution to continue rather than displaying an error message to the end
user. There are valid scenarios where this is needed, but in general you
should avoid this as it could allow a malicious user to bypass security
controls if they are somehow able to force an error condition.

## ASP.NET Web Forms

ASP.NET web form pages provide the ability to capture exceptions at the
page level in a similar fashion to the application level. This may be
useful if you need to perform failure handling logic or log additional
detail unique to the page.

    void Page_Error(object sender, EventArgs e)
    {
      // Get the exception object.
      var exception = Server.GetLastError();

      // Log exception details. Be sure to include items like client IP
      // address and current authenticated user if applicable.
      System.Diagnostics.Trace.TraceError(exception.ToString());
    }

## ASP.NET MVC

The MVC Controller class provides an *OnException* method similar to the
*Page_Error* method in ASP.NET Web Forms. It allows you to process all
unhandled exceptions thrown by actions of the controller. One option for
implementing exception logging is to create a base controller class and
defining the *OnException* method in this one central location.

    protected override void OnException(ExceptionContext filterContext)
    {
      base.OnException(filterContext);
      System.Diagnostics.Trace.TraceError(filterContext.Exception.ToString());
    }

A second (and arguably better) approach is to utilize the
*System.Web.Mvc.HandleErrorAttribute* which can be used to handle
exceptions at the application, controller, or action level. To apply
this at the application level you add an instance of
*HandleErrorAttribute* to the *GlobalFilterCollection* at application
startup. This takes affect before the *Application_Error* method in
Global.asax.cs, and by default will redirect to the *Error* view in the
\~/Views/Shared folder. This will bypass any custom error pages defined
via the *<customErrors>* element in web.config.

    public static void RegisterGlobalFilters(GlobalFilterCollection filters)
    {
      filters.Add(new HandleErrorAttribute());
    }

You can log the exception details right within the *Error.cshtml* view
using properties from the view model which is of type
*System.Web.Mvc.HandleErrorInfo*.

    @model System.Web.Mvc.HandleErrorInfo

    @{
        ViewBag.Title = "Error";

        // Log exception details
        System.Diagnostics.Trace.TraceError(Model.Exception.ToString());
    }

    <h1 class="text-danger">Error.</h1>
    <h2 class="text-danger">An error occurred while processing your request.</h2>

## ASP.NET Web API

When handling exceptions for your API endpoints you generally want to
return a JSON or XML response rather than redirect to an HTML page.
ASP.NET Web API provides exception filters to customize how exceptions
are handled. A good way of adding exception logging is to derive your
own class from *System.Web.Http.Filters.ExceptionFilterAttribute* and
override the *OnException* method as shown.

    public class LogExceptionFilterAttribute : ExceptionFilterAttribute
    {
      public override void OnException(HttpActionExecutedContext context)
      {
        System.Diagnostics.Trace.TraceError(context.Exception.ToString());
        base.OnException(context);
      }
    }

You can apply the *\[LogExceptionFilter\]* attribute to any
*ApiController*, or add it at a global level using the following code at
application startup.

    System.Web.Http.GlobalConfiguration.Configuration.Filters.Add(new LogExceptionFilterAttribute());

### HttpResponseException

By default any exception thrown within Web API will return an HTTP
response status code of 500 (Internal Server Error). For more control
over the response you can use *HttpResponseException* as shown.

    public Product GetProduct(int id)
    {
        Product item = repository.Get(id);
        if (item == null)
        {
            throw new HttpResponseException(HttpStatusCode.NotFound)
          {
                Content = new StringContent(string.Format("No product with ID = {0}", id)),
                ReasonPhrase = "Product ID Not Found"
              };
        }
        return item;
    }

### Web API Global Error Handling (Added in Web API 2.1)

There are a number of cases in Web API where an exception can occur that
falls outside of what exception filters can handle. These include
exceptions in controller construction, message handlers, routing, and
response content serialization. To handle these exceptions you will need
to register a class that implements the *IExceptionLogger* interface, or
derives from the *ExceptionLogger* base class.

    public interface IExceptionLogger
    {
      Task LogAsync(ExceptionLoggerContext context, CancellationToken cancellationToken);
    }

You then register your class at application startup to ensure that all
exceptions raised during a Web API request life cycle are captured and
logged.

    System.Web.Http.GlobalConfiguration.Services.Add(typeof(IExceptionLogger), new MyExceptionLogger());

# Logging Sensitive Data

Be careful when logging exception details that you do not inadvertently
expose sensitive data to a logging system or external reports that may
have relaxed access controls compared to the primary system. For example
if a *SqlException* is thrown and the details contain a connection
string, you may want to mask the password attribute before logging the
event. Use care when logging exception details that may contain the
following types of data:

  - Passwords
  - Authentication tokens
  - Personally identifiable information (PII)
  - Personal health information (PHI)
  - Credit card data

# References

  - [Displaying a Custom Error
    Page](http://www.asp.net/web-forms/tutorials/deployment/deploying-web-site-projects/displaying-a-custom-error-page-cs)
  - \[<http://msdn.microsoft.com/en-us/library/h0hfz6fc(v=vs.100>).aspx
    customErrors Element (ASP.NET Settings Schema)\]
  - \[<http://msdn.microsoft.com/en-us/library/system.diagnostics.trace(v=vs.110>).aspx
    Trace Class\]
  - \[<http://msdn.microsoft.com/en-us/library/ed577840(v=vs.100>).aspx
    How to: Handle Page-Level Errors\]
  - \[<http://msdn.microsoft.com/en-us/library/system.web.mvc.controller.onexception(v=vs.118>).aspx
    Controller.OnException Method\]
  - \[<http://msdn.microsoft.com/en-us/library/system.web.mvc.handleerrorattribute(v=vs.118>).aspx
    HandleErrorAtttribute Class\]
  - [Exception Handling in ASP.NET Web
    API](http://www.asp.net/web-api/overview/testing-and-debugging/exception-handling)
  - [Web API 2 .1 Global Error
    Handling](http://www.asp.net/web-api/overview/testing-and-debugging/web-api-global-error-handling)

[Category:OWASP .NET Project](Category:OWASP_.NET_Project "wikilink")