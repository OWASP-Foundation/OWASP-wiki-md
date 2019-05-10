*This article is for the OWASP Top 10 2004*

### Description

Web applications use input from HTTP requests (and occasionally files)
to determine how to respond. Attackers can tamper with any part of an
HTTP request, including the url, querystring, headers, cookies, form
fields, and hidden fields, to try to bypass the site’s security
mechanisms. Common names for common input tampering attacks include:
forced browsing, command insertion, cross site scripting, buffer
overflows, format string attacks, SQL injection, cookie poisoning, and
hidden field manipulation. Each of these attack types is described in
more detail later in this paper.

  - A4 – Cross Site Scripting Flaws discusses input that contains
    scripts to be executed on other user’s browsers
  - A5 – Buffer Overflows discusses input that has been designed to
    overwrite program execution space
  - A6 – Injection Flaws discusses input that is modified to contain
    executable commands

Some sites attempt to protect themselves by filtering out malicious
input. The problem is that there are so many different ways of encoding
information. These encoding formats are not like encryption, since they
are trivial to decode. Still, developers often forget to decode all
parameters to their simplest form before using them. Parameters must be
converted to the simplest form before they are validated, otherwise,
malicious input can be masked and it can slip past filters. The process
of simplifying these encodings is called “canonicalization.” Since
almost all HTTP input can be represented in multiple formats, this
technique can be used to obfuscate any attack targeting the
vulnerabilities described in this document. This makes filtering very
difficult.

A surprising number of web applications use only client-side mechanisms
to validate input. Client side validation mechanisms are easily
bypassed, leaving the web application without any protection against
malicious parameters. Attackers can generate their own HTTP requests
using tools as simple as telnet. They do not have to pay attention to
anything that the developer intended to happen on the client side. Note
that client side validation is a fine idea for performance and
usability, but it has no security benefit whatsoever. Server side checks
are required to defend against parameter manipulation attacks. Once
these are in place, client side checking can also be included to enhance
the user experience for legitimate users and/or reduce the amount of
invalid traffic to the server.

These attacks are becoming increasingly likely as the number of tools
that support parameter “fuzzing”, corruption, and brute forcing grows.
The impact of using unvalidated input should not be underestimated. A
huge number of attacks would become difficult or impossible if
developers would simply validate input before using it. Unless a web
application has a strong, centralized mechanism for validating all input
from HTTP requests (and any other sources), vulnerabilities based on
malicious input are very likely to exist.

### Environments Affected

All web servers, application servers, and web application environments
are susceptible to parameter tampering.

### Examples and References

  - OWASP Guide to Building Secure Web Applications and Web Services,
    [Chapter 8: Data Validation](Data_Validation "wikilink")
  - modsecurity project (Apache module for HTTP validation)
    <http://www.modsecurity.org>
  - [How to Build an HTTP Request Validation Engine (J2EE validation
    with
    Stinger)](How_to_Build_an_HTTP_Request_Validation_Engine_for_Your_J2EE_Application "wikilink")
  - [Have Your Cake and Eat it
    Too](Have_Your_Cake_and_Eat_It_Too "wikilink") (.NET validation)

### How to Determine If You Are Vulnerable

Any part of an HTTP request that is used by a web application without
being carefully validated is known as a “tainted” parameter. The
simplest way to find tainted parameter use is to have a detailed code
review, searching for all the calls where information is extracted from
an HTTP request. For example, in a J2EE application, these are the
methods in the HttpServletRequest class. Then you can follow the code to
see where that variable gets used. If the variable is not checked before
it is used, there is very likely a problem. In Perl, you should consider
using the “taint” (-T) option. It is also possible to find tainted
parameter use by using tools like OWASP’s WebScarab. By submitting
unexpected values in HTTP requests and viewing the web application’s
responses, you can identify places where tainted parameters are used.

### How to Protect Yourself

The best way to prevent parameter tampering is to ensure that all
parameters are validated before they are used. A centralized component
or library is likely to be the most effective, as the code performing
the checking should all be in one place. Each parameter should be
checked against a strict format that specifies exactly what input will
be allowed. “Negative” approaches that involve filtering out certain bad
input or approaches that rely on signatures are not likely to be
effective and may be difficult to maintain.

Parameters should be validated against a “positive” specification that
defines:

  - Data type (string, integer, real, etc…)
  - Allowed character set
  - Minimum and maximum length
  - Whether null is allowed
  - Whether the parameter is required or not
  - Whether duplicates are allowed
  - Numeric range
  - Specific legal values (enumeration)
  - Specific patterns (regular expressions)

A new class of security devices known as web application firewalls can
provide some parameter validation services. However, in order for them
to be effective, the device must be configured with a strict definition
of what is valid for each parameter for your site. This includes
properly protecting all types of input from the HTTP request, including
URLs, forms, cookies, querystrings, hidden fields, and parameters. The
OWASP Filters project is producing reusable components in several
languages to help prevent many forms of parameter tampering. The Stinger
HTTP request validation engine (stinger.sourceforge.net) was also
developed by OWASP for J2EE environments.

[Category:OWASP Top Ten
Project](Category:OWASP_Top_Ten_Project "wikilink")