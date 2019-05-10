## Status

Released on (mm/dd/yyyy) : 02/07/2012

## Description

JEE Java Server Page (JSP) provides mechanism to specify, in a JSP, the
error page to redirect if a Java exception occur.

## Configuration

The configuration have 2 steps:

  - The definition of the page in charge of managing error.
  - The specification of the redirection into the page where the Java
    exception can occur.

### Step 1 : Definition of the page in charge of managing error

This page is a normal JSP but we specify the page attribute
"isErrorPage" to "true" value ("false" is the default value). This flag
indicate to server that the page is in charge of managing exception,
thus, the server made available the source exception through the
"exception" implicit object.

    <?xml version="1.0" encoding="ISO-8859-1" ?>
    <%@ page language="java"
        contentType="text/html; charset=ISO-8859-1"
        pageEncoding="ISO-8859-1"

        isErrorPage="true"
    %>

    <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">

    <html ns="http://www.w3.org/1999/xhtml">
    <body>
        <%-- Log error on server side --%>
        <%
            //When the page attribute "isErrorPage" is set to "true" the exception object is available
            System.err.println("Error : " + exception.getMessage());
        %>

        <%-- Display generic error to client --%>
        <b>An error occur !</b>
    </body>
    </html>

### Step 2 : Specification of the redirection into the page where the Java exception can occur

Into the risky JSP, we specify the page attribute "errorPage" to the
page in charge of managing error.

    <?xml version="1.0" encoding="ISO-8859-1" ?>
    <%@ page language="java"
        contentType="text/html; charset=ISO-8859-1"
        pageEncoding="ISO-8859-1"

        errorPage="errorManagement.jsp"
    %>

    <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">

    <html ns="http://www.w3.org/1999/xhtml">
    <body>
        <%
            //Sample code to generate an exception...
            if(request.getParameter("e") != null) {
                throw new ServletException("Explicit error !!!");
            }
        %>
    </body>
    </html>

## Best practice

In order to don't miss any server error, it's preferable to configure
error handling at [web deployment
descriptor](Servlet_spec_-_web.xml "wikilink") level. Configuration into
JSP must be reserved to specific case.

[Category:Java](Category:Java "wikilink")