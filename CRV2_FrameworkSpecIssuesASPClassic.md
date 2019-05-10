# CLASSIC ASP

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

![<File:Classic-asp.png>](Classic-asp.png "File:Classic-asp.png")

The text in the example above has a number of issues: Firstly, it
redisplay the HTTP request to the user in the form of
Request.Url.ToString() Assuming there has been no data validation prior
to this point, we are vulnerable to cross site mscripting attacks\!\!
Secondly the error message and stack trace is displayed to the user
using Server.GetLastError().ToString() which divulges internal
information regarding the application.