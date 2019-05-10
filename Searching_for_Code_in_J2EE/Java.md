__TOC__

## Input and Output Streams

These are used to read data into one’s application. They may be
potential entry points into an application. The entry points may be from
an external source and must be investigated. These may also be used in
path traversal attacks or DoS attacks.

Java.io
java.util.zip
java.util.jar
FileInputStream
ObjectInputStream
FilterInputStream
PipedInputStream
SequenceInputStream
StringBufferInputStream
BufferedReader
ByteArrayInputStream
CharArrayReader
File
ObjectInputStream
PipedInputStream
StreamTokenizer
getResourceAsStream
java.io.FileReader
java.io.FileWriter
java.io.RandomAccessFile
java.io.File
java.io.FileOutputStream
mkdir
renameTo
java.io.File.delete
java.io.File.listFiles
java.io.File.list

## Servlets

These API calls may be avenues for parameter, header, URL, and cookie
tampering, HTTP Response Splitting and information leakage. They should
be examined closely as many of such APIs obtain the parameters directly
from HTTP requests.

javax.servlet.\*
getParameterNames
getParameterValues
getParameter
getParameterMap
getScheme
getProtocol
getContentType
getServerName
getRemoteAddr
getRemoteHost
getRealPath
getLocalName
getAttribute
getAttributeNames
getLocalAddr
getAuthType
getRemoteUser
getCookies
isSecure
HttpServletRequest
getQueryString
getHeaderNames
getHeaders
getPrincipal
getUserPrincipal
isUserInRole
getInputStream
getOutputStream
getWriter
addCookie
addHeader
setHeader
setAttribute
putValue
javax.servlet.http.Cookie
getName
getPath
getDomain
getComment
getMethod
getPath
getReader
getRealPath
getRequestURI
getRequestURL
getServerName
getValue
getValueNames
getRequestedSessionId

## Cross Site Scripting

javax.servlet.ServletOutputStream.print
javax.servlet.jsp.JspWriter.print
java.io.PrintWriter.print

## Response Splitting

javax.servlet.http.HttpServletResponse.sendRedirect
addHeader, setHeader

## Redirection

sendRedirect
setStatus
addHeader, setHeader

## SQL & Database

Searching for Java Database related code this list should help you
pinpoint classes/methods which are involved in the persistence layer of
the application being reviewed.

jdbc
executeQuery
select
insert
update
delete
execute
executestatement
createStatement
java.sql.ResultSet.getString
java.sql.ResultSet.getObject
java.sql.Statement.executeUpdate
java.sql.Statement.executeQuery
java.sql.Statement.execute
java.sql.Statement.addBatch
java.sql.Connection.prepareStatement
java.sql.Connection.prepareCall

## SSL

Looking for code which utilises SSL as a medium for point to point
encryption. The following fragments should indicate where SSL
functionality has been developed.

com.sun.net.ssl
SSLContext
SSLSocketFactory
TrustManagerFactory
HttpsURLConnection
KeyManagerFactory

## Session Management

getSession
invalidate
getId

## Legacy Interaction

Here we may be vulnerable to command injection attacks or OS injection
attacks. Java linking to the native OS can cause serious issues and
potentially give rise to total server compromise.

java.lang.Runtime.exec
java.lang.Runtime.getRuntime

## Logging

We may come across some information leakage by examining code below
contained in one’s application.

java.io.PrintStream.write
log4j
jLo
Lumberjack
MonoLog
qflog
just4log
log4Ant
JDLabAgent

## Architectural Analysis

If we can identify major architectural components within that
application (right away) it can help narrow our search, and we can then
look for known vulnerabilities in those components and frameworks:

\#\#\# Ajax
XMLHTTP
\#\#\# Struts
org.apache.struts
\#\#\# Spring
org.springframework
\#\#\# Java Server Faces (JSF)
import javax.faces
\#\#\# Hibernate
import org.hibernate
\#\#\# Castor
org.exolab.castor
\#\#\# JAXB
javax.xml
\#\#\# JMS
JMS

## Generic Keywords

Developers say the darnedest things in their source code. Look for the
following keywords as pointers to possible software vulnerabilities:

Hack
Kludge
Bypass
Steal
Stolen
Divert
Broke
Trick
FIXME
ToDo
Password
Backdoor

## WEB 2.0

**Ajax and JavaScript**

Look for Ajax usage, and possible JavaScript issues:

document.write
eval
document.cookie
window.location
document.URL

## Code Execution

The following may lead to arbitrary java code execution if source of
input data is entrusted or not validated.
java.lang.ClassLoader.defineClass
java.net.URLClassLoader
java.beans.Instrospector.getBeanInfo
System.load
System.loadLibrary
Runtime.exec
ProcessBuilder (constructor)
javax.script.ScriptEngine.eval

## XMLHTTP

window.createRequest

[Category:OWASP Code Review
Project](Category:OWASP_Code_Review_Project "wikilink")