![<File:Low_activity.jpg>](Low_activity.jpg "File:Low_activity.jpg")

[:Category:Vulnerability](:Category:Vulnerability "wikilink")
[:Category:Access Control](:Category:Access_Control "wikilink")

# Introduction

Modern web application frameworks have made it easy to develop high
quality web applications, but developing a secure application still
requires programmers to possess a deep understanding of security
vulnerabilities and attacks. Sometimes it is difficult for an
experienced developer to find and eliminate all the vulnerabilities.
This demo represents the JSF-ESAPI framework based on JSF2.0 and OWASP
ESAPI. It helps developers write a secure and lower-risk JSF based on a
web application with minimal configuration and without extensive prior
knowledge of the web security. The figure below shows a complete
integration of the JSF-ESAPI framework with JSF2.0 and ESAPI. It works
as a middleware and consists of four important modules. ESAPI Validation
is the first module which verifies the user input as given in the XSS
prevention cheat sheet provided by OWASP. It consists of many
user-defined validator tags and generates appropriate error messages if
the user input is not valid. In this way it performs a strong
validation. There are also some tags available in the correspondence
validators in ESAPI, and they also filter the XSS relevant code from the
input. The file-based authorization module simplifies the user’s role,
such as admin, user, etc. and gives the permission to visualize certain
components at the presentation layer based on assigned roles. ESAPI
Filtering layer compares the valid form token with tokens stored in the
session for that user. If the token is mitigated or changed by man in
the middle during the process of a request-response exchange, it will
give the appropriate exception. The last module is a render module,
which renders the output after filtering the XSS content and encodes the
vulnerable characters such as \<,\>,”,’ etc. as given in the XSS
prevention cheat sheet provided by OWASP. This framework will help
developers to prevent a myriad of security problems including cross-site
scripting, CSRF (cross-site request forgery), automatic input
validation, and automatic output validation with escaped “true” or
without this parameter, authorization. All the features are included in
one framework. Advantages:

  - It requires minimal configuration to use the framework.

<!-- end list -->

  - It ensures retrofit security in the existing application.

<!-- end list -->

  - It provides the same performance as JSF framework.

<!-- end list -->

  - Automatic filtering of the XSS vulnerable code from output takes
    place when escape equals true” or “false”.

<!-- end list -->

  - The input validation is easy and no additional coding is required.

<!-- end list -->

  - It has a layered architecture. It uses what you need and leaves what
    you don’t need at the moment.

<!-- end list -->

  - One framework includes the most secure features."

# Objective

This project is a continuation of the Master thesis ([Master Thesis -
Applied Computer Science, Albert-Ludwigs-Universität Freiburg im
Breisgau - "Development of the Security Framework based on OWASP ESAPI
for JSF2.0" by Rakeshkumar
Kachhadiya](http://security4web.ch/downloads/doc/Master-Thesis.pdf))
created in May 2012.

The goal is to facilitate the work of computer scientists, when they
will implement a new application, it will be automatically safe without
them realizes. It is important to improve more security on the ‘File
based authorization’ module.

The 'File based authorization' module gives permission to visualize some
areas or pages at the presentation layer as per given user rights.

It’s responsible to maintain the user information in the file with their
assigned roles but also setting the rendering components false if the
accessible user tries to retrieve the page.

# Installation

  - Download esapi_final.jar file

<!-- end list -->

  - Download all external librairies in the 'Downloads' section. Not all
    librairies are required\! Check all librairies dependencies for this
    project in this
    [page](http://owasp-esapi-java.googlecode.com/svn/trunk_doc/1.4.4/site/dependencies.html)

<!-- end list -->

  - Download the config files (taglib.xml, faces-config.xml,
    validation.properties, ESAPI.properties, web.xml and users.txt)

<!-- end list -->

  - Add all librairies to your JSF project buildpath

<!-- end list -->

  - Make the same with the esapi_final.jar file, this jar archive
    contain all important classes

<!-- end list -->

  - Copy the files (taglib.xml, faces-config.xml, validation.properties,
    ESAPI.properties) to your web/WEB-INF directory of your JSF project

<!-- end list -->

  - Update your web.xml file

Go to the 'Example' section and download the guess example and the
auction example. You need to install this projects in Eclipse and then
download the pdf files corresponding to each example in the
'Documentation' section for step by step installation.

# Downloads

Master Jar file :
[esapi_final.jar](http://security4web.ch/OWASP/esapi_final.jar)

The full Master project jar from Rakeshkumar Kachhadiya updated : [Jar
file Rakeshkumar esapi
project](http://security4web.ch/OWASP/Rakeshkumar/Rakeshkumar_esapi.jar)

This zip contain all config files (taglib.xml, faces-config.xml,
validation.properties, ESAPI.properties, web.xml and users.txt) :
[Config
files](http://security4web.ch/OWASP/Config_files/Config_files.zip)

## Librairies

[AntiSamy 1.2.jar](http://code.google.com/p/owaspantisamy/downloads/detail?name=antisamy-bin.1.2.jar&can=1&q=label%3AFeatured)

[commons-digester3-3.1.jar](http://mvnrepository.com/artifact/org.apache.commons/commons-digester3/3.1)

[commons-fileupload-1.2.2.jar](http://grepcode.com/snapshot/repo1.maven.org/maven2/commons-fileupload/commons-fileupload/1.2.2)

[esapi-2.0.1.jar](http://code.google.com/p/owasp-esapi-java/downloads/detail?name=esapi-2.0.1-dist.zip&can=2&q=)

[jdom-1.0.jar](http://grepcode.com/snapshot/repo1.maven.org/maven2/jdom/jdom/1.0)

[jsf-impl.jar](http://grepcode.com/snapshot/repo1.maven.org/maven2/com.sun.faces/jsf-impl/2.0.2)

[jsp-2.1-6.1.9.jar](http://grepcode.com/snapshot/repo1.maven.org/maven2/org.mortbay.jetty/jsp-2.1/6.1.9)

[jsp-api-6.0.14.jar](http://repo1.maven.org/maven2/6.0.14/jsp-api-6.0.14.jar)

[jstl-1.2.jar](http://grepcode.com/snapshot/repo1.maven.org/maven2/javax.servlet/jstl/1.2)

[log4j-1.2.16.jar](http://code.google.com/p/jenkins-assembler/downloads/detail?name=log4j-1.2.16.jar&can=2&q=)

[servlet-2.3.jar](http://grepcode.com/snapshot/repo1.maven.org/maven2/javax.servlet/servlet-api/2.3)

## Examples

Two Eclipse projects for the demonstration (Both contains a login page,
this login needs some class available in the esapi_final.jar file):

[Zip Guess game
example](http://security4web.ch/OWASP/Exemples/guess/guess_example.zip)

[Zip Auction site
example](http://security4web.ch/OWASP/Exemples/auction/auction_example.zip)

## Documentation

PDF file containing a presentation and a demonstration of a 'file based
authorization' attack and a solution to protect it.

[Security_framework_OWASP_esapi_JSF_14.05.2013.pdf](http://security4web.ch/downloads/doc/Security_framework_OWASP_esapi_JSF_14.05.2013.pdf)

Step by step installation guide for the two examples :

[Example with File based authorization
protection](http://security4web.ch/OWASP/Exemples/guess/guess_example.pdf)
(guess_example documentation)

[Example with CSRF and validation
protection](http://security4web.ch/OWASP/Exemples/auction/auction_example.pdf)
(auction_example documentation)

# Project About

[Category:OWASP Project](Category:OWASP_Project "wikilink")