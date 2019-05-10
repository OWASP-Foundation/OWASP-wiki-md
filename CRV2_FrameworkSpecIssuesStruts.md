Apache Structs 2 is an open-source web application framework for Java EE
web applications. Today most development that uses Structs is using the
newest version Sructs 2. Structs web framework has reached its end of
life and is no longer officially supported. The Struts framework acts as
a façade for Java applications, providing a framework to divide the code
of an application into the Model, View and Controller components defined
in the MVC pattern.

Apache Struts 2 doesn't provide any security mechanism - it is just a
pure web framework.

• Keep Up to date on Releases. Code Reviewer needs to understand what
version of Structs is being used. Lastest version of Structs at the time
of writing this book was Apache Struts 2.3.16.3 GA.

• Restrict access to the Config Browser Config Browser Plugin exposes
internal configuration and should be used only during development phase.

• Don't mix different access levels in the same namespace You cannot mix
actions with different security levels in the same namespace. Always
group actions in one namespace by security level.

<security-constraint>
`   `<web-resource-collection>
`       `<web-resource-name>`admin`</web-resource-name>
`       `<url-pattern>`/secure/*`</url-pattern>
`   `</web-resource-collection>
`   `<auth-constraint>
`       `<role-name>`admin`</role-name>
`   `</auth-constraint>
</security-constraint>

• Code reviewer to be aware and keep up to date on for all third party
software. Apache open source code is very good at being open and
transparent on all security issues. Current security bulletins can be
found at.
<http://struts.apache.org/release/2.3.x/docs/security-bulletins.html>

A list of Current security.

S2-001 Critical – Remote exploit on form validation error.

S2-002 Important – Cross site scripting (XSS) vulnerability on and tags.

S2-003 Critical - XWork ParameterInerceptors bypass allows OGNL
statement execution.

S2-004 Important - Directory traversal vulnerability while serving
static content.

S2-005 Critical - XWork ParameterInterceptors bypass allows remote
command execution.

S2-006 Important - Multiple Cross-Site Scripting (XSS) in XWork
generated error pages.

S2-007 Important - User input is evaluated as an OGNL expression when
there's a conversion error.

S2-008 Critical - Multiple critical vulnerabilities in Struts2.

S2-009 Critical - ParameterInterceptor vulnerability allows remote
command execution.

S2-010 Moderate- When using Struts 2 token mechanism for CSRF
protection, token check may be bypassed by misusing known session
attributes.

S2-011 Important - Long request parameter names might significantly
promote the effectiveness of DOS attacks.

S2-012 Moderately Critical - Showcase app vulnerability allows remote
command execution.

S2-013 High Critical - A vulnerability, present in the includeParams
attribute of the URL and Anchor Tag, allows remote command execution.

S2-014 Highly Critical - A vulnerability introduced by forcing parameter
inclusion in the URL and Anchor Tag allows remote command execution,
session access and manipulation and XSS attacks.

S2-015 Highly Critical - A vulnerability introduced by wildcard matching
mechanism or double evaluation of OGNL Expression allows remote command
execution.

S2-016 Highly Critical - A vulnerability introduced by manipulating
parameters prefixed with "action:"/"redirect:"/"redirectAction:" allows
remote command execution.

S2-017 Important - A vulnerability introduced by manipulating parameters
prefixed with "redirect:"/"redirectAction:" allows for open redirects.

S2-018 Important - Broken Access Control Vulnerability in Apache
Struts2.

S2-019 Important - Dynamic Method Invocation disabled by default.

S2-020 Important - Upgrade Commons FileUpload to version 1.3.1 (avoids
DoS attacks) and adds 'class' to exclude params in ParametersInterceptor
(avoid ClassLoader manipulation).

S2-021 High - Improves excluded params in ParametersInterceptor and
CookieInterceptor to avoid ClassLoader manipulation.

S2-022 Medium - Extends excluded params in CookieInterceptor to avoid
manipulation of Struts' internals.