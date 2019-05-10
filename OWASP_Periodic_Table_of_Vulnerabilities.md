# Main

<div style="width:100%;height:100px;border:0,margin:0;overflow: hidden;">

![OWASP_Inactive_Banner.jpg](OWASP_Inactive_Banner.jpg
"OWASP_Inactive_Banner.jpg")

</div>

## Introduction

After 25 years of software engineering since the first Internet worm was
written to exploit a buffer overflow vulnerability, web developers are
still building insecure software. It is time for a new approach. The
vast majority of software bug classes can be eliminated by making
changes to protocols and standards and building protections into
perimeter technologies, platform infrastructures, and application
frameworks before a developer even writes a single line of custom code.
By allowing developers to focus on just a small subset of bug classes,
training and standards programs can be more targeted and effective,
enabling developers to write secure code much more efficiently.

Vulnerabilities and weaknesses from industry-recognized indexes
including OWASP Top 10, WASC TCv2, and CWE-25 are analyzed to determine
which of the remediation strategies are ideal for solving the software
security problem. Where changes to internet standards and protocols are
required, alternatives in perimeter, framework, or custom code solutions
are also provided until the internet-scale solutions are in place. If a
solution can be completely implemented in perimeter or infrastructure
technologies, only that solution is provided. Similarly, if any part of
the solution can be provided in standard or custom frameworks, that
solution is not recommended to be implemented in custom code. The
guiding principle is essentially: "implement security controls as far
from custom code as possible." Only if there is no other way to solve a
particular security problem is a custom code solution recommended.

## Browsers, Standards, and Protocols

The most scalable and effective approach to addressing vulnerability
classes is to fix the browsers, standards, and protocols that enable web
applications. This approach can sometimes increase security for every
application on the internet without changing a single line of
application code. The amount of industry collaboration required to
implement a protocol/standard change can be enormous, but some classes
of vulnerabilities simply cannot be addressed without this kind of
change (e.g. Clickjacking). A solution at this level is incredibly
powerful: a Content Security Policy (CSP) solution to Cross-Site
Scripting (XSS) might allow most application owners to write a simple
policy file instead of implementing a costly framework or custom code
solution to protect their existing application assets.

## Perimeter / Platform Technologies

Less scalable, but almost as effective, is to address vulnerabilities in
perimeter technologies such as application firewalls, load balancers,
geocaching services (e.g. Akamai), and proxies. These technologies can
shield vulnerable applications without requiring changes to the
applications themselves. While most classes of vulnerability depend
heavily on the application code and aren't easily solved by a generic
perimeter solution, some are generalizable to the point where a
perimeter solution could protect any application behind it before an
attack even has a chance to do damage. Anti-automation and protocol
validation are especially good solutions for perimeter technologies to
address.

Similarly, some vulnerability classes should be addressed in platform
technologies such as web servers, application servers, and operating
systems. Often these technologies are responsible for exposing the
vulnerability in the first place, and must be responsible for providing
the solution.

## Generic Application Frameworks

The next most scalable approach requires upgrading popular application
frameworks so they are robust against common attack classes. Platforms
such as Java Struts/J2EE, Ruby on Rails, and PHP can theoretically
prevent developers from introducing most classes of vulnerability in the
first place. However, the current state of the framework industry is a
result of being more driven by features than by security; any conflict
between the two is usually decided in favor of adding features and ease
of use, as opposed to difficult-to-use security enhancements. Some
frameworks even have built-in vulnerabilities out of the box\!

Improvements to application frameworks won't immediately help protect
existing applications (though they would make any new applications built
on the platform much safer). Many applications currently rely on
insecure features of their frameworks that would be eliminated or
refactored when the framework is secured. Existing applications would
need to follow an upgrade path provided by a "secure" branch of existing
frameworks before these solutions could take effect. Many applications
don't even use popular frameworks at all, and so could never be helped
by improvements to common development platforms.

Generic Framework solution guidelines would, however, help application
owners prioritize refactoring efforts for their existing applications in
order to make their application code more robust against future
development mistakes. This is true whether their applications use
popular frameworks or not. Implementing a robust solution to a
vulnerability class is much more cost-effective in the long run than
training every developer to understand every vulnerability and
continuously patching new instances of the vulnerability each time they
appear. Cross-Site Scripting is a classic example of the "whac-a-mole
vulnerability" that recurrently wastes developer time and attention and
could be solved more holistically with a framework wrapper. Application
owners can pattern their security refactoring efforts against the
recommended solutions for Generic Frameworks in order to completely
eliminate the same classes of vulnerabilities from their existing
applications, even if they can't easily port their applications to a
framework which has already addressed those vulnerabilities.

## Custom Application Frameworks

Some vulnerabilities are unique to a specific application and can't be
solved by a generic framework solution. For example, a generic framework
might ship with a Social Security Number (SSN) validator, but a custom
framework solution would be needed for a CustomWidgetItem validator. The
SSN data type is well-defined and not unique to a specific application
or business, but the CustomWidgetItem is unique to that application and
has its own validation rules.

Organizations should still customize application frameworks to support
their own application-specific APIs and security controls. Developers
can leverage these controls during development instead of having to
build the controls in during their daily coding efforts. If developers
use a CustomWidgetItem object that has already been validated by
framework code, it is much more likely that they will use it safely than
if they have to remember to do their own validation each time they use
the object. By addressing the vulnerability once with a single framework
customization, the application owner can protect all future development
from introducing the vulnerability into new code.

## Custom Code

If none of the other solution options are possible for a given
vulnerability class (or the solution still requires the developer to do
something in order to leverage a framework feature), developers will be
required to think about how to protect against that class in every line
of code that they write. This is the least scalable of all of the
solution models, which explains why current efforts to educate
developers about all vulnerability classes hasn't resulted in secure
software. Some classes of attacks, such as Abuse of Functionality,
depend completely on the custom code and business logic of the
application and cannot be abstracted at all into other solution models.

The set of vulnerabilities which must be eliminated in custom code is
only a small fraction of the total vulnerability space. By focusing
training and testing efforts on just this set of issues, after
addressing all other problems in a more scalable manner, developers have
a much better chance of building secure applications in the future.

# Periodic Table of Vulnerabilities

| rowspan="2" colspan="2" align="center" style="background:\#D8D8D8; border-width:3px 1px 3px 3px;" | **VULNERABILITY**                                                                                                                                                                     | colspan="5" align="center" style="background:\#D8D8D8; border-width:3px 3px 1px 1px;" | **LOCATION OF SECURITY CONTROL**                                                     |
| ------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------ |
| align="center" style="background:\#D8D8D8; border-width:1px 1px 3px 1px;"                         | **Standards**                                                                                                                                                                         | align="center" style="background:\#D8D8D8; border-width:1px 1px 3px 1px;"             | **Infrastructure/Perimeter**                                                         |
| width="11%" style="background:\#f0f0f0; border-width:2px 1px 2px 3px;"                            | **[Abuse of Functionality](OWASP_Periodic_Table_of_Vulnerabilities_-_Abuse_of_Functionality "wikilink")**                                                                             |                                                                                       | width="4%" align="center" style="background:\#f0f0f0; border-width:3px 1px 2px 1px;" |
| style="background:\#f0f0f0; border-width:2px 1px 2px 3px;"                                        | **[Application Misconfiguration](OWASP_Periodic_Table_of_Vulnerabilities_-_Application_Misconfiguration "wikilink")**                                                                 |                                                                                       | align="center" style="background:\#f0f0f0; border-width:2px 1px 2px 1px;"            |
| style="background:\#f0f0f0; border-width:2px 1px 2px 3px;"                                        | **[Brute Force (Generic) / Insufficient Anti-automation](OWASP_Periodic_Table_of_Vulnerabilities_-_Brute_Force_\(Generic\)_/_Insufficient_Anti-automation "wikilink")**               |                                                                                       | align="center" style="background:\#f0f0f0; border-width:2px 1px 2px 1px;"            |
| style="background:\#f0f0f0; border-width:2px 1px 2px 3px;"                                        | **[Brute Force Login](OWASP_Periodic_Table_of_Vulnerabilities_-_Brute_Force_Login "wikilink")**                                                                                       |                                                                                       | align="center" style="background:\#f0f0f0; border-width:2px 1px 2px 1px;"            |
| style="background:\#f0f0f0; border-width:2px 1px 2px 3px;"                                        | **[Brute Force Session Identifier](OWASP_Periodic_Table_of_Vulnerabilities_-_Brute_Force_Session_Identifier "wikilink")**                                                             |                                                                                       | align="center" style="background:\#f0f0f0; border-width:2px 1px 2px 1px;"            |
| style="background:\#f0f0f0; border-width:2px 1px 2px 3px;"                                        | **[Brute Force Predictable Resource Location/Insecure Indexing](OWASP_Periodic_Table_of_Vulnerabilities_-_Brute_Force_Predictable_Resource_Location/Insecure_Indexing "wikilink")**   |                                                                                       | align="center" style="background:\#f0f0f0; border-width:2px 1px 2px 1px;"            |
| style="background:\#f0f0f0; border-width:2px 1px 2px 3px;"                                        | **[Buffer Overflow](OWASP_Periodic_Table_of_Vulnerabilities_-_Buffer_Overflow "wikilink")**                                                                                           |                                                                                       | align="center" style="background:\#f0f0f0; border-width:2px 1px 2px 1px;"            |
| style="background:\#f0f0f0; border-width:2px 1px 2px 3px;"                                        | **[Clickjacking](OWASP_Periodic_Table_of_Vulnerabilities_-_Clickjacking "wikilink")**                                                                                                 |                                                                                       | align="center" style="background:\#f0f0f0; border-width:2px 1px 2px 1px;"            |
| style="background:\#f0f0f0; border-width:2px 1px 2px 3px;"                                        | **[Content Spoofing](OWASP_Periodic_Table_of_Vulnerabilities_-_Content_Spoofing "wikilink")**                                                                                         |                                                                                       | align="center" style="background:\#f0f0f0; border-width:2px 1px 2px 1px;"            |
| style="background:\#f0f0f0; border-width:2px 1px 2px 3px;"                                        | **[Cookie Theft/Session Hijacking](OWASP_Periodic_Table_of_Vulnerabilities_-_Cookie_Theft/Session_Hijacking "wikilink")**                                                             |                                                                                       | align="center" style="background:\#f0f0f0; border-width:2px 1px 2px 1px;"            |
| style="background:\#f0f0f0; border-width:2px 1px 2px 3px;"                                        | **[Cross-Site Request Forgery](OWASP_Periodic_Table_of_Vulnerabilities_-_Cross-Site_Request_Forgery "wikilink")**                                                                     |                                                                                       | align="center" style="background:\#f0f0f0; border-width:2px 1px 2px 1px;"            |
| style="background:\#f0f0f0; border-width:2px 1px 2px 3px;"                                        | **[Cross-Site Scripting (XSS)](OWASP_Periodic_Table_of_Vulnerabilities_-_Cross-Site_Scripting_\(XSS\) "wikilink")**                                                                   |                                                                                       | align="center" style="background:\#f0f0f0; border-width:2px 1px 2px 1px;"            |
| style="background:\#f0f0f0; border-width:2px 1px 2px 3px;"                                        | **[Cross-Site Scripting (XSS) - DOM-Based](OWASP_Periodic_Table_of_Vulnerabilities_-_Cross-Site_Scripting_\(XSS\)_-_DOM-Based "wikilink")**                                           |                                                                                       | align="center" style="background:\#f0f0f0; border-width:2px 1px 2px 1px;"            |
| style="background:\#f0f0f0; border-width:2px 1px 2px 3px;"                                        | **[Denial of Service (Application Based)](OWASP_Periodic_Table_of_Vulnerabilities_-_Denial_of_Service_\(Application_Based\) "wikilink")**                                             |                                                                                       | align="center" style="background:\#f0f0f0; border-width:2px 1px 2px 1px;"            |
| style="background:\#f0f0f0; border-width:2px 1px 2px 3px;"                                        | **[Denial of Service (Connection Based)](OWASP_Periodic_Table_of_Vulnerabilities_-_Denial_of_Service_\(Connection_Based\) "wikilink")**                                               |                                                                                       | align="center" style="background:\#f0f0f0; border-width:2px 1px 2px 1px;"            |
| style="background:\#f0f0f0; border-width:2px 1px 2px 3px;"                                        | **[Directory Indexing](OWASP_Periodic_Table_of_Vulnerabilities_-_Directory_Indexing "wikilink")**                                                                                     |                                                                                       | align="center" style="background:\#f0f0f0; border-width:2px 1px 2px 1px;"            |
| style="background:\#f0f0f0; border-width:2px 1px 2px 3px;"                                        | **[Fingerprinting](OWASP_Periodic_Table_of_Vulnerabilities_-_Fingerprinting "wikilink")**                                                                                             |                                                                                       | align="center" style="background:\#f0f0f0; border-width:2px 1px 2px 1px;"            |
| style="background:\#f0f0f0; border-width:2px 1px 2px 3px;"                                        | **[Format String](OWASP_Periodic_Table_of_Vulnerabilities_-_Format_String "wikilink")**                                                                                               |                                                                                       | align="center" style="background:\#f0f0f0; border-width:2px 1px 2px 1px;"            |
| style="background:\#f0f0f0; border-width:2px 1px 2px 3px;"                                        | **[HTTP Request/Response Smuggling](OWASP_Periodic_Table_of_Vulnerabilities_-_HTTP_Request/Response_Smuggling "wikilink")**                                                           |                                                                                       | align="center" style="background:\#f0f0f0; border-width:2px 1px 2px 1px;"            |
| style="background:\#f0f0f0; border-width:2px 1px 2px 3px;"                                        | **[HTTP Response Splitting](OWASP_Periodic_Table_of_Vulnerabilities_-_HTTP_Response_Splitting "wikilink")**                                                                           |                                                                                       | align="center" style="background:\#f0f0f0; border-width:2px 1px 2px 1px;"            |
| style="background:\#f0f0f0; border-width:2px 1px 2px 3px;"                                        | **[Implicit Logout](OWASP_Periodic_Table_of_Vulnerabilities_-_Implicit_Logout "wikilink")**                                                                                           |                                                                                       | align="center" style="background:\#f0f0f0; border-width:2px 1px 2px 1px;"            |
| style="background:\#f0f0f0; border-width:2px 1px 2px 3px;"                                        | **[Improper Filesystem Permissions](OWASP_Periodic_Table_of_Vulnerabilities_-_Improper_Filesystem_Permissions "wikilink")**                                                           |                                                                                       | align="center" style="background:\#f0f0f0; border-width:2px 1px 2px 1px;"            |
| style="background:\#f0f0f0; border-width:2px 1px 2px 3px;"                                        | **[Improper Input Handling](OWASP_Periodic_Table_of_Vulnerabilities_-_Improper_Input_Handling "wikilink")**                                                                           |                                                                                       | align="center" style="background:\#f0f0f0; border-width:2px 1px 2px 1px;"            |
| style="background:\#f0f0f0; border-width:2px 1px 2px 3px;"                                        | **[Improper Output Handling](OWASP_Periodic_Table_of_Vulnerabilities_-_Improper_Output_Handling "wikilink")**                                                                         |                                                                                       | align="center" style="background:\#f0f0f0; border-width:2px 1px 2px 1px;"            |
| style="background:\#f0f0f0; border-width:2px 1px 2px 3px;"                                        | **[Information Leakage](OWASP_Periodic_Table_of_Vulnerabilities_-_Information_Leakage "wikilink")**                                                                                   |                                                                                       | align="center" style="background:\#f0f0f0; border-width:2px 1px 2px 1px;"            |
| style="background:\#f0f0f0; border-width:2px 1px 2px 3px;"                                        | **[Insufficient Authentication/Authorization](OWASP_Periodic_Table_of_Vulnerabilities_-_Insufficient_Authentication/Authorization "wikilink")**                                       |                                                                                       | align="center" style="background:\#f0f0f0; border-width:2px 1px 2px 1px;"            |
| style="background:\#f0f0f0; border-width:2px 1px 2px 3px;"                                        | **[Insufficient Data Protection](OWASP_Periodic_Table_of_Vulnerabilities_-_Insufficient_Data_Protection "wikilink")**                                                                 |                                                                                       | align="center" style="background:\#f0f0f0; border-width:2px 1px 2px 1px;"            |
| style="background:\#f0f0f0; border-width:2px 1px 2px 3px;"                                        | **[Insufficient Password Recovery](OWASP_Periodic_Table_of_Vulnerabilities_-_Insufficient_Password_Recovery "wikilink")**                                                             |                                                                                       | align="center" style="background:\#f0f0f0; border-width:2px 1px 2px 1px;"            |
| style="background:\#f0f0f0; border-width:2px 1px 2px 3px;"                                        | **[Insufficient Process Validation](OWASP_Periodic_Table_of_Vulnerabilities_-_Insufficient_Process_Validation "wikilink")**                                                           |                                                                                       | align="center" style="background:\#f0f0f0; border-width:2px 1px 2px 1px;"            |
| style="background:\#f0f0f0; border-width:2px 1px 2px 3px;"                                        | **[Insufficient Session Expiration](OWASP_Periodic_Table_of_Vulnerabilities_-_Insufficient_Session_Expiration "wikilink")**                                                           |                                                                                       | align="center" style="background:\#f0f0f0; border-width:2px 1px 2px 1px;"            |
| style="background:\#f0f0f0; border-width:2px 1px 2px 3px;"                                        | **[Insufficient Transport Layer Protection](OWASP_Periodic_Table_of_Vulnerabilities_-_Insufficient_Transport_Layer_Protection "wikilink")**                                           |                                                                                       | align="center" style="background:\#f0f0f0; border-width:2px 1px 2px 1px;"            |
| style="background:\#f0f0f0; border-width:2px 1px 2px 3px;"                                        | **[Integer Overflow/Underflow](OWASP_Periodic_Table_of_Vulnerabilities_-_Integer_Overflow/Underflow "wikilink")**                                                                     |                                                                                       | align="center" style="background:\#f0f0f0; border-width:2px 1px 2px 1px;"            |
| style="background:\#f0f0f0; border-width:2px 1px 2px 3px;"                                        | **[LDAP Injection](OWASP_Periodic_Table_of_Vulnerabilities_-_LDAP_Injection "wikilink")**                                                                                             |                                                                                       | align="center" style="background:\#f0f0f0; border-width:2px 1px 2px 1px;"            |
| style="background:\#f0f0f0; border-width:2px 1px 2px 3px;"                                        | **[Mail Command Injection](OWASP_Periodic_Table_of_Vulnerabilities_-_Mail_Command_Injection "wikilink")**                                                                             |                                                                                       | align="center" style="background:\#f0f0f0; border-width:2px 1px 2px 1px;"            |
| style="background:\#f0f0f0; border-width:2px 1px 2px 3px;"                                        | **[Null Byte Injection](OWASP_Periodic_Table_of_Vulnerabilities_-_Null_Byte_Injection "wikilink")**                                                                                   |                                                                                       | align="center" style="background:\#f0f0f0; border-width:2px 1px 2px 1px;"            |
| style="background:\#f0f0f0; border-width:2px 1px 2px 3px;"                                        | **[OS Commanding](OWASP_Periodic_Table_of_Vulnerabilities_-_OS_Commanding "wikilink")**                                                                                               |                                                                                       | align="center" style="background:\#f0f0f0; border-width:2px 1px 2px 1px;"            |
| style="background:\#f0f0f0; border-width:2px 1px 2px 3px;"                                        | **[Path Traversal](OWASP_Periodic_Table_of_Vulnerabilities_-_Path_Traversal "wikilink")**                                                                                             |                                                                                       | align="center" style="background:\#f0f0f0; border-width:2px 1px 2px 1px;"            |
| style="background:\#f0f0f0; border-width:2px 1px 2px 3px;"                                        | **[Race Conditions](OWASP_Periodic_Table_of_Vulnerabilities_-_Race_Conditions "wikilink")**                                                                                           |                                                                                       | align="center" style="background:\#f0f0f0; border-width:2px 1px 2px 1px;"            |
| style="background:\#f0f0f0; border-width:2px 1px 2px 3px;"                                        | **[Remote File Inclusion](OWASP_Periodic_Table_of_Vulnerabilities_-_Remote_File_Inclusion "wikilink")**                                                                               |                                                                                       | align="center" style="background:\#f0f0f0; border-width:2px 1px 2px 1px;"            |
| style="background:\#f0f0f0; border-width:2px 1px 2px 3px;"                                        | **[Routing Detour](OWASP_Periodic_Table_of_Vulnerabilities_-_Routing_Detour "wikilink")**                                                                                             |                                                                                       | align="center" style="background:\#f0f0f0; border-width:2px 1px 2px 1px;"            |
| style="background:\#f0f0f0; border-width:2px 1px 2px 3px;"                                        | **[Server Misconfiguration](OWASP_Periodic_Table_of_Vulnerabilities_-_Server_Misconfiguration "wikilink")**                                                                           |                                                                                       | align="center" style="background:\#f0f0f0; border-width:2px 1px 2px 1px;"            |
| style="background:\#f0f0f0; border-width:2px 1px 2px 3px;"                                        | **[Session Fixation](OWASP_Periodic_Table_of_Vulnerabilities_-_Session_Fixation "wikilink")**                                                                                         |                                                                                       | align="center" style="background:\#f0f0f0; border-width:2px 1px 2px 1px;"            |
| style="background:\#f0f0f0; border-width:2px 1px 2px 3px;"                                        | **[SOAP Array Abuse, XML Attribute Blowup, XML Entity Expansion](OWASP_Periodic_Table_of_Vulnerabilities_-_SOAP_Array_Abuse,_XML_Attribute_Blowup,_XML_Entity_Expansion "wikilink")** |                                                                                       | align="center" style="background:\#f0f0f0; border-width:2px 1px 2px 1px;"            |
| style="background:\#f0f0f0; border-width:2px 1px 2px 3px;"                                        | **[SQL Injection](OWASP_Periodic_Table_of_Vulnerabilities_-_SQL_Injection "wikilink")**                                                                                               |                                                                                       | align="center" style="background:\#f0f0f0; border-width:2px 1px 2px 1px;"            |
| style="background:\#f0f0f0; border-width:2px 1px 2px 3px;"                                        | **[SSI Injection](OWASP_Periodic_Table_of_Vulnerabilities_-_SSI_Injection "wikilink")**                                                                                               |                                                                                       | align="center" style="background:\#f0f0f0; border-width:2px 1px 2px 1px;"            |
| style="background:\#f0f0f0; border-width:2px 1px 2px 3px;"                                        | **[URL Redirector Abuse](OWASP_Periodic_Table_of_Vulnerabilities_-_URL_Redirector_Abuse "wikilink")**                                                                                 |                                                                                       | align="center" style="background:\#f0f0f0; border-width:2px 1px 2px 1px;"            |
| style="background:\#f0f0f0; border-width:2px 1px 2px 3px;"                                        | **[Weak HTTP Authentication Methods](OWASP_Periodic_Table_of_Vulnerabilities_-_Weak_Authentication_Methods "wikilink")**                                                              |                                                                                       | align="center" style="background:\#f0f0f0; border-width:2px 1px 2px 1px;"            |
| style="background:\#f0f0f0; border-width:2px 1px 2px 3px;"                                        | **[XML External Entities](OWASP_Periodic_Table_of_Vulnerabilities_-_XML_External_Entities "wikilink")**                                                                               |                                                                                       | align="center" style="background:\#f0f0f0; border-width:2px 1px 2px 1px;"            |
| style="background:\#f0f0f0; border-width:2px 1px 2px 3px;"                                        | **[XML Injection](OWASP_Periodic_Table_of_Vulnerabilities_-_XML_Injection "wikilink")**                                                                                               |                                                                                       | align="center" style="background:\#f0f0f0; border-width:2px 1px 2px 1px;"            |
| style="background:\#f0f0f0; border-width:2px 1px 3px 3px;"                                        | **[XPath/XQuery Injection](OWASP_Periodic_Table_of_Vulnerabilities_-_XPath/XQuery_Injection "wikilink")**                                                                             |                                                                                       | align="center" style="background:\#f0f0f0; border-width:2px 1px 3px 1px;"            |

# Release Formats

  - [Compressed view](Media:Periodic_Table_Infographic.pdf "wikilink") -
    One-pager that highlights the vulnerability classes that developers
    will still have to worry about at the top, with "solved"
    vulnerabilities ordered toward the bottom.
  - Infographic - Cartoony, visually-appealing storyboard introduction
    of the project, its goals, and high-level approach.
  - [Working
    View/Summary](OWASP_Periodic_Table_of_Vulnerabilities#tab=Periodic_Table_of_Vulnerabilities "wikilink")
    - Working view summarizes solutions in respective columns for quick
    reference but doesn't provide details. Links directly to detailed
    sections.
  - Solution Detail (see linked issues on summary view) - Detailed view
    combines references, detailed solution designs,
    discussion/controversy detail, and other relevant information for
    each solution recommendation. The detail view does NOT explain what
    each vulnerability/weakness is - it only references existing
    vulnerability descriptions from other projects (e.g. OWASP Top 10,
    WASC TCv2, CWE, etc.). A short summary of root cause(s) is included,
    but only to the level of depth required to suggest all of the
    solution design elements that need to be addressed.
  - Solution Checklist - Summary of solutions grouped by target (e.g.
    perimeter or framework) so that maintainers of standards,
    frameworks, and perimeter technologies can view the solutions
    required for their areas ONLY. May require templating to generate
    list automatically, or short summaries in place of detailed
    descriptions.
  - [Periodic Table Interactive View](http://periodictable.github.io/) -
    Minimal representation of the Periodic Table View combined with a
    legend mapping each symbol to the vulnerability name, related
    taxonomies, and solution targets. Rolling over each element gives
    solution highlights. Clicking an element opens the corresponding
    Solution Detail view.
  - Periodic Table Poster-Size View - Vulns/Weaknesses laid out like the
    table of chemical elements, with solution target along the top and
    some measure of severity progressing down through the "periods". Top
    10 could be highlighted in some way. Issues may show up in multiple
    periods. Poster-size so we can get all the relevant information in
    each "element".
  - [Periodic Table Compact
    View](Media:OWASP_Periodic_Table_-_Letter_Size.pdf "wikilink") -
    Minimal representation of the Periodic Table View combined with a
    legend mapping each symbol to the vulnerability name, related
    taxonomies, and solution targets. View is designed to fit on a
    single US Letter size piece of paper, printed in grayscale.

# Project About

__NOTOC__ <headertabs />

[Category:OWASP Project](Category:OWASP_Project "wikilink")