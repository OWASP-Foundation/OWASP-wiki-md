## Introduction

## Java EE Authentication Technologies

The Java EE framework contains a number of options from an
authentication standpoint, such as,

  - Java Authentication and Authorization Service (JAAS)
  - Java Secure Socket Extensions (JSSE.)
      - Authentication and key exchange (RSA & DSA), SSL Authentication
  - Java 2 Security Model

### Servlet Authentication

The Java API javax.servlet.HttpServlet contains a number of methods to
receive HTTP requests. One fundamental practice in application security
is not to hue HTTP GET during the authentication sequence (This is
because sensitive credentials may be logged inadvertently on the web
server). HttpServlet harbours methods such as doPost(), doPut(),
doDelete(), doGet() to name a few. These methods can be used to process
incomming HTTP requests.

During the course of Servlet processing, the HttpServlet.service()
method is called before the "do" methods (doGet(), doPost(), etc.)
therefore no significant processing should be placed in
HttpServlet.service() prior to validating that the correct HTTP method
was used to submit the transaction. Therefore it is prudent to examine
that the correct http method (doPost(), doGet() has been over-ridden as
opposed to service() method.

In the case of an authentication servlet it would be recommended to
assure that the doGet() method has been overridden.

One solution to prevent HTTP GET requests is to use the
HTTPServletRequest.getMethod() to examine if the method is POST.

{ if( (request.getMethod()).compareTo(“POST”)) { // POST submission
processing . . . } else { // not POST throw new Exception(“HTTP method
error”); }

## J2EE Authorization Technologies

## J2EE Session Management

## J2EE Data Validation

## J2EE Error Handling

## Crypto in J2EE/Java