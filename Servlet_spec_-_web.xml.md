## Status

Released on (mm/dd/yyyy) : 02/06/2012

## Description

JEE web specification provides a way to configure, declaratively in the
web deployment descriptor ("web.xml" file), the web app. behavior when
an exception occur in a web component.

Behavior can be configured to react on elements below to display a
resource:

  - Java exception
  - HTTP response code

## Possible configurations

Configuration below redirect user to page "/errorManagement.jsp" when an
error occur.

**Configuration to react on Java exception**

    <?xml version="1.0" encoding="UTF-8"?>
    <web-app xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
        ns="http://java.sun.com/xml/ns/javaee" xmlns:web="http://java.sun.com/xml/ns/javaee/web-app_2_5.xsd"
        xsi:schemaLocation="http://java.sun.com/xml/ns/javaee http://java.sun.com/xml/ns/javaee/web-app_3_0.xsd"
        id="WebApp_ID" version="3.0">

        ...

        <!-- Define error page to react on Java exception -->
        <error-page>
            <exception-type>java.lang.Throwable</exception-type>
            <location>/errorManagement.jsp</location>
        </error-page>

        ...

    </web-app>

**Configuration to react on HTTP response code**

    <?xml version="1.0" encoding="UTF-8"?>
    <web-app xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
        ns="http://java.sun.com/xml/ns/javaee" xmlns:web="http://java.sun.com/xml/ns/javaee/web-app_2_5.xsd"
        xsi:schemaLocation="http://java.sun.com/xml/ns/javaee http://java.sun.com/xml/ns/javaee/web-app_3_0.xsd"
        id="WebApp_ID" version="3.0">

        ...

        <!-- Define error page to react on HTTP response code -->
        <error-page>
            <error-code>500</error-code>
            <location>/errorManagement.jsp</location>
        </error-page>

        ...

    </web-app>

**Content of the error management page**

    <?xml version="1.0" encoding="ISO-8859-1" ?>

    <%@ page language="java"
        contentType="text/html; charset=ISO-8859-1"
        pageEncoding="ISO-8859-1"
        isErrorPage="true"%>

    <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">

    <html ns="http://www.w3.org/1999/xhtml">
    <head>
    <meta http-equiv="Content-Type" content="text/html; charset=ISO-8859-1" />
    <title>Page to manage error</title>
    </head>

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

## Best practice

In order to don't miss any server error, it's a best practice to define
a java exception based error page and set exception type to
"java.lang.Exception".

[Category:Java](Category:Java "wikilink")