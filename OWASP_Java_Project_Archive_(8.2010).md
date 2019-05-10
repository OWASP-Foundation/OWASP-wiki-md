'''This is an archived page. Will be cleaned up later. '''

Current project page:
<https://owasp.org/index.php/Category:OWASP_Java_Project>

<table>
<thead>
<tr class="header">
<th><p>width="700" align="center"</p></th>
<th><p><br />
</p></th>
<th><p>width="500" align="center"</p></th>
<th><p><br />
</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>align="right"</p></td>
<td><figure>
<img src="OWASP_Inactive_Banner.jpg" title="OWASP_Inactive_Banner.jpg" alt="OWASP_Inactive_Banner.jpg" width="800" /><figcaption>OWASP_Inactive_Banner.jpg</figcaption>
</figure></td>
<td><p>align="right"</p></td>
<td></td>
</tr>
</tbody>
</table>

#### Main

The OWASP Java Project's goal is to enable Java and J2EE developers to
build secure applications efficiently. See the [OWASP Java Project
Roadmap](http://www.owasp.org/index.php/OWASP_Java_Project#tab=Roadmap)
for more information on our plans.

## Java Security Overview

While Java and J2EE contain many security technologies, it is not easy
to produce an application without security vulnerabilities. Most
application security
[vulnerabilities](:Category:Vulnerability "wikilink") apply to Java
applications just like other environments. The notable exception is
[buffer overflow](Buffer_Overflow "wikilink") and related issues that do
not apply to Java applications.

There is a wealth of information about vulnerabilities that apply to
Java and JavaEE application in the
[Vulnerability](:Category:Vulnerability "wikilink") articles here at
OWASP. The articles that have specific Java examples are tagged with the
[Java category](:Category:Java "wikilink").

The goals of this project are to provide information about building,
configuring, deploying, operating, and maintaining secure Java
applications. We cover the following topics:

  - [J2EE Security for
    Architects](OWASP_Java_Table_of_Contents#J2EE_Security_for_Architects "wikilink")
    Provides information about the design and architectural
    considerations for a Java web application. Common architectures such
    as EJB, Web Services and Spring Middle tiers are discussed.

<!-- end list -->

  - [J2EE Security for
    Developers](OWASP_Java_Table_of_Contents#J2EE_Security_for_Developers "wikilink")
    These articles cover dangerous Java calls and common vulnerabilities
    associated with them, such as Runtime.exec(), Statement.execute(),
    readline(), etc... The dangers of native code, dynamic code, and
    reflection will be discussed. We'll also talk about using tools like
    PMD, jlint, FindBugs, Eclipse, jad, and more. This section will also
    cover standard security mechanisms in the JDK, such as cryptography,
    logging, encryption, error handling. Securing elements of an
    application, such as servlets, JSPs, controllers, business logic,
    and persistence layers will be covered. We'll discuss handling
    request parameters, encoding, injection, and more. We'll also
    discuss the use of security mechanisms such as log4j, BouncyCastle,
    XML encryption, XML signature, and other technologies.

<!-- end list -->

  - [J2EE Security for
    Deployers](OWASP_Java_Table_of_Contents#J2EE_Security_For_Deployers "wikilink")
    These articles cover topics specifically related to the J2EE
    environment. We discuss minimizing the attack surface in web.xml,
    configuring error handlers, and performing hardening of popular J2EE
    application servers.

<!-- end list -->

  - [J2EE Security for Security Analysts and
    Testers](OWASP_Java_Table_of_Contents#J2EE_Security_for_Security_Analysts_and_Testers "wikilink")
    These articles cover the verification, analysis, and testing of the
    security of J2EE applications. This section will cover using tools
    to find vulnerabilities, both in source code and in running
    applications. These articles will focus on J2EE-specific aspects of
    testing applications that use various common J2EE frameworks and
    coding patterns.

#### Related OWASP Projects

  - [OWASP Enterprise Security API (ESAPI)
    Project](:Category:OWASP_Enterprise_Security_API "wikilink")
    a free and open collection of all the security methods that a
    developer needs to build a secure web application.

<!-- end list -->

  - [OWASP Development
    Guide](:Category:OWASP_Guide_Project "wikilink")
    a massive document covering all aspects of web application and web
    service security

<!-- end list -->

  - [OWASP Java Encoder
    Project](OWASP_Java_Encoder_Project "wikilink")
    a Java 1.5+ simple-to-use drop-in high-performance encoder class
    with no dependencies to help Java web developers defend against
    Cross Site Scripting

<!-- end list -->

  - [OWASP AntiSamy Java
    Project](:Category:OWASP_AntiSamy_Project "wikilink")
    an API for validating rich HTML/CSS input from users without
    exposure to cross-site scripting and phishing attacks

<!-- end list -->

  - [OWASP Java HTML Sanitizer
    Project](OWASP_Java_HTML_Sanitizer_Project "wikilink")
    a fast and easy to configure HTML Sanitizer written in Java which
    lets you include HTML authored by third-parties in your web
    application while protecting against XSS.

<!-- end list -->

  - [OWASP Java JSON Sanitizer](OWASP_JSON_Sanitizer "wikilink")
    a tool to convert JSON-like content to valid JSON\! The OWASP JSON
    Sanitizer Project is a simple to use Java library that can be
    attached at either end of a data-pipeline

<!-- end list -->

  - [OWASP Dependency Check](OWASP_Dependency_Check "wikilink")
    a Java utility that identifies project dependencies and checks if
    there are any known, publicly disclosed, vulnerabilities

<!-- end list -->

  - [OWASP Secure Headers
    Project](OWASP_Secure_Headers_Project "wikilink")
    a collection of HTTP response headers to elevate the security of
    your web app\!

<!-- end list -->

  - [OWASP Secure Coding Practices - Quick Reference
    Guide](OWASP_Secure_Coding_Practices_-_Quick_Reference_Guide "wikilink")
    this document provides a quick high level reference for secure
    coding practices. It is technology agnostic and defines a set of
    general software security coding practices, in a checklist format,
    that can be integrated into the development lifecycle.

<!-- end list -->

  - [OWASP Code Review
    Guide](:Category:OWASP_Code_Review_Project "wikilink")
    a project to capture best practices for reviewing code.

<!-- end list -->

  - [OWASP CSRFGuard
    Project](:Category:OWASP_CSRFGuard_Project "wikilink")
    a J2EE filter that implements a unique request token to mitigate
    CSRF attacks

<!-- end list -->

  - [OWASP Code Pulse](OWASP_Code_Pulse_Project "wikilink")
    a real-time code coverage tool of penetration testing activities

#### Resources

<tbd>

#### Roadmap

The OWASP Java Project's overall goal is to...

`build and maintain a central landing page on the Web for all Java users (developers, architects & co.) interested in Web security`

and to

`produce materials that show J2EE architects, developers, and`
`deployers how to deal with most common application security`
`problems throughout the lifecycle.`

In the near term, we are focused on the following tactical goals:

1.  Restructure the existing content
2.  Align the page with other Java-related OWASP projects like ESAPI,
    Webgoat, ASVS (including a new chapter: "OWASP J2EE Related
    Projects")
3.  Priorize work on missing content
4.  Implement a J2EE/Java EE Secure Coding Guideline based on ESAPI,
    ASVS and/or the Quick Reference Guide.
5.  Set-up a comparision of security aspects of web frameworks such like
    struts2, spring mvc, jsf, gwt, etc.
6.  Set-up a comparision of security aspects of templating technologies
    such as jsp, velocity, tiles, etc.
7.  Provide examples of how to prevent comman attacks like XSS in
    popular web frameworks
8.  A practical guide to implementing a security policy for a Java web
    application
9.  Provide secure configuration guides for popular application servers
10. Provide an OWASP Java Top 10

## Current Tasks

  - Call for volunteers - Join the [mailing
    list](http://lists.owasp.org/mailman/listinfo/java-project), read
    the [Tutorial](Tutorial "wikilink"), check the [OWASP Java Table of
    Contents](OWASP_Java_Table_of_Contents "wikilink") and get started\!
  - Review of current articles

See the [OWASP Java Table of
Contents](OWASP_Java_Table_of_Contents "wikilink") for details of
individual article status

## Ideas

Please submit your high level ideas about the direction of the OWASP
Java Project here (you can sign your ideas by adding four tilde
characters like this \~\~\~\~)

  - To add specific articles, visit the [OWASP Java Table of
    Contents](OWASP_Java_Table_of_Contents "wikilink")

#### Project About

__NOTOC__ <headertabs/>z

## Joining the Project

Mirko Richter is the project lead. The project's high level roadmap can
be found at the Roadmap tab.

  - Please submit your ideas for individual articles to the [Java
    Project Article Wishlist](Java_Project_Article_Wishlist "wikilink").
  - If you'd like to contribute:

<!-- end list -->

1.  visit the [Tutorial](Tutorial "wikilink"),
2.  join the [mailing
    list](http://lists.owasp.org/mailman/listinfo/java-project)
3.  and pick a topic from the [OWASP Java Table of
    Contents](OWASP_Java_Table_of_Contents "wikilink"), or suggest a new
    topic.

Remember to add the tag:
\[\[Category:OWASP_Java_Project|Category:OWASP Java Project\]\] to the
end of new articles so that they're properly categorised.