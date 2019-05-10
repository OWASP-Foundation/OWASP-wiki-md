__TOC__

### Overview

There are several issues inherent to classic ASP pages that may lead to
security issues. We are talking about beginner mistakes or code misuse.
The following examples will give you a good idea of what is being
discussed. All of these examples are based on common findings through
experience of ASP testing.

### ASP Pages Execution Order Issues

ASP pages are executed in the following way:

1.  **Server Side Includes**. First, the interpreter adds to the current
    file the text of all the files in include sentences and process it
    as if it was a single file.
2.  **Server Side VBSCript Code**. Second, the VBScript in \<% and %\>
    code is executed.
3.  **Client Side JAvascript/VBScript Code**. Finally, once the page is
    completely loaded in the browser, JavaScript code is executed.

This might be obvious, however, ignoring this order might lead to severe
security issues. Here are some examples.

### Wrong dynamic inclusion of files.

```
 <%
 If User = "Admin" Then
 %>
 <!--#include file="AdminMenu.inc"-->
 <%
 Else
 %>
 <!--#include file="UserMenu.inc"-->
 <%
 End If
 %>
```

The previous code will add the content of both files to the ASP page;
execution as SSI are executed first, then ASP code. It is possible that
the page is displayed correctly due to the "If" sentence, however, all
the code will be processed; this might lead to race conditions or
undesired execution of functions.

### HTML and JavaScript comments do not skip execution of ASP code

```
 <!-- <%= "Debug: This is the DB user: " & DBUserName %> -->
 <script type="Text/JavaScript">
 var x = 'Hello, ';
 //<%= "Debug: This is the DB password: " & DBUserPassword %>
 alert (x + "Juan");
 </script>
```

If you are proficient in ASP technology, the result of the example above
would be clear, however, many developers cannot tell the final output.

```
 <!-- Debug: This is the DB user: SA -->
 <script type="Text/JavaScript">
 var x = 'Hello, ';
 //Debug: This is the DB password: Password
 alert (x + "Juan");
 </script>
```

Above shows that sensitive information in the commented-out code is
disclosed in HTML or JavaScript comments.

### Using JavaScript to drive ASP functionality

Yes, this is not possible, but that is another reason to look for it.

```
 <script>
   var name;
   name = prompt ("Enter your UserName:");
   <%
     If name != "user" Then
       'The user is an admin
       Role = "Admin"
      Else
        Role = "User"
      End IF
   %>
 <script>
```

The code above shall grant Admin privileges every time to the logged
user as, as we saw before, ASP code is executed first. Besides, there is
no sharing of variables between JavaScript and ASP code.

Another example:

```
 <%@ Language=VBScript %>
 <script type="text/javascript">
   if (confirm('go to yahoo?')){
     <% response.redirect "http://www.yahoo.com/" %>
   }else {
     <% response.redirect "http://www.altavista.com/" %>
   }
 </script>
```

You will always go to Yahoo and will never be displayed with a prompt;
code within \<% %\> is executed first.

### Stopping execution with Response.End

Lack of this sentence might end up in execution of undesired code.

```
 <%
   If Not ValidInfo Then
 %>
 <script>
   alert("Information is invalid");
   location.href="default.asp";
 </script>
 <%
   End if
   Call UpdateInformationFunction()
 %>
```

In example above, the "UpdateInformationFunction" is called all the time
regardless of the "ValidInfo" variable value, as ASP code is executed
first, then JavaScript. ASP code is executed in server and the output is
sent to Browser, then JavaScript is executed. That means that is
required a **Response.End** to stop execution server side.

## Other Issues

#### Java classes hosted in MS Java Virtual Machine

These classes can be called from ASP pages, so you should look also for
insecure functionality within such classes. This is an example:

```
 <html><body>
 <% Dim date
   Set date = GetObject("java:java.util.Date")
 %>
 <p> The date is <%= date.toString() %>
 </body></html>
```

#### Not Using Option Explicit

Mistyped variables might lead to race conditions on business logic. This
option will force the user to declare all the used variables, and it
will add a bit of performance as well.

#### IsClientConnected property

This property determines if the client has disconnected from the server
since the last **Response.Write**. This property is particularly useful
to prevent the server from continuing execution of long pages after an
unexpected disconnect. As you might figured out, this is very useful
property to avoid DoS attacks to the Server and DB in long execution
pages.

[Category:OWASP Code Review
Project](Category:OWASP_Code_Review_Project "wikilink")