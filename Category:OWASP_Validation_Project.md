#### Main

# Overview

Most web application platforms do not include features to validate user
input. This leaves many organizations to craft their own validation
mechanisms, often incomplete, flawed, and inefficient.

The OWASP Validation Project was created to provide guidance and tools
related to validation. Our philosophy is that validation is required for
every part of the HTTP request, including headers, query string,
cookies, form fields, and hidden fields.

Currently, there are several projects underway to create validation
technologies for various platforms. The long term goal is to provide a
detailed guide for implementing proper input validation as well as
provide validation engines for popular web application environments.

The OWASP Validation Project is need of a leader\! Contact owasp 'at'
owasp.org if you are interested\!

# Feedback and Participation:

We hope you find the OWASP Validation Project useful. Please contribute
to the Project by volunteering for one of the Tasks, sending your
comments, questions, and suggestions to owasp@owasp.org. To join the
OWASP Validation Project mailing list or view the archives, please visit
the [subscription
page.](http://lists.owasp.org/mailman/listinfo/owasp-validation)

# News

**`Rough``   ``Draft``   ``of``   ``the``   ``Validation``
 ``Questionnaire``   ``Released!``   ``-``   ``14:05,``   ``23``
 ``January``   ``2007``   ``(EST)`**

The OWASP Validation Project is pleased to announce the rough draft
release of the "Validation Questionnaire." The purpose of this document
is to aide developers in performing a basic level of input validation
threat modeling. If we can clearly define our application's sources of
input and the potential risk associated with each source, then we can
better implement an appropriate input validation scheme. Please feel
free to offer suggestions for improvement\!

[Click
here](http://www.owasp.org/index.php/Image:ValidationQuestionnaire.doc)
to download the validation questionnaire.

**`New``   ``OWASP``   ``J2EE``   ``Filters``   ``Released!``   ``-``
 ``10:07,``   ``5``   ``January``   ``2007``   ``(EST)`**

The OWASP Community has released two brand new J2EE Filters\! Both of
the new filters attempt to address current hot topics is the web
application security community.

:\***[OWASP CSRF Guard](http://www.owasp.org/index.php/CSRF_Guard)** -
protects a web application from Cross-Site Request Forgery attacks
through the use of a unique random request token

:\***[PDF Attack
Filter](http://www.owasp.org/index.php/PDF_Attack_Filter_for_Java_EE)**
- protects a web application from the recently discovered [XSS-PDF
Flaw](http://www.gnucitizen.org/blog/danger-danger-danger/) through the
use of a redirect trick

If you have any suggestions or comments for either filter, please email
your comments to <owasp@owasp.org>

**[Click here for old
news...](http://www.owasp.org/index.php/Validation_News)**

# Project Roadmap

The three major goals of the OWASP Validation Project are the following:

:\# build an input validation guide

:\# provide and implement input validation mechanisms for various
platforms

:\# rewrite Stinger to incorporate the design principles in the guide

The [OWASP Validation
Roadmap](http://www.owasp.org/index.php/OWASP_Validation_Project_Roadmap)
contains the latest information as to project goals and targeted release
dates.

# Guide to Building Input Validation

One of the major goals of the OWASP Validation Project is to provide
clear and detailed documentation on building input validation mechanisms
for your web application needs. In the near future, this section will
contain such documentation. Check back soon\!

# Implementation

The second major goal of the OWASP Validation Project is to provide
input validation mechanisms which adhere to one or more of the design
principles outlined in the 'Input Validation Guide'. If you have a
project which fits this requirement, please submit it via email to the
project lead.

## OWASP Validation Documentation

The primary purpose of the OWASP Validation Documentation project is to
provide the design principles necessary to build an effective input
validation engine. More can be found
[here](http://www.owasp.org/index.php/OWASP_Validation_Documentation_Project).

## Java

The Stinger library is a full J2EE Validation Engine which strongly
adheres to the principle's outline in the [Validation
Documentation](http://www.owasp.org/index.php/OWASP_Validation_Documentation_Project).
More information can be found on the Stinger Project page at
<http://www.owasp.org/index.php/OWASP_Stinger_Project>

Most modern Java web frameworks include their own data validation
features. All of these can validate user data in GET and POST requests,
but usually do not validate cookie data. Web frameworks that provide
their own validation features include:

  - [Apache Struts](http://struts.apache.org)
  - [WebWork](http://www.opensymphony.com/webwork/wikidocs/Validation.html)
  - [Spring
    MVC](http://www.springframework.org/docs/reference/validation.html)
  - [Java Server Faces](http://java.sun.com/javaee/javaserverfaces/)
  - [JBoss Seam](http://labs.jboss.com/portal/jbossseam/?prjlist=false)

## .NET

One of the goals of the OWASP Validation Project is to implement Stinger
2.0 on the .NET platform.

If you are interested in leading this project, please contact [Eric
Sheridan](mailto:eric.sheridan@owasp.org).

Please refer to the project road map for an estimated time of arrival.

## PHP

The PHP Filters Project provides an API framework for validating input
for various purposes. The project can be found
[here](http://www.owasp.org/index.php/PHP_Filters).

OWASP Recently released the [OWASP
Top 5](http://www.owasp.org/index.php/PHP_Top_5), an article
illustrating several attack vectors against PHP applications.

The majority of the PHP Top 5 can be alleviated with a solid and well
defined validation mechanism.

## Classic ASP

Stinger 1.0 was migrated to pure classic ASP VBScript code, See
[OWASP_Stinger_Version_1](OWASP_Stinger_Version_1 "wikilink") for
more information on this version. Notice that ASP version loads only one
rules file per page for easy of use for developers. If you need diferent
rulesets for a sigle page use programatic rules. You can download this
project [here](http://www.owasp.org/images/b/b2/StingerASP1.0.zip).

## RegEx Repository

The [OWASP RegEx
Repository](http://www.owasp.org/index.php/OWASP_Validation_Regex_Repository)
contains a multitude of regular expressions for common data types.
Developers implementing input validation engines should review these
regular expressions. Save the time of developing a complicated regular
expression that currently exists\!

# Project Sponsor

The OWASP Validation project is sponsored by
[<http://www.owasp.org/images/d/d1/Aspect_logo.gif>](http://www.aspectsecurity.com)

#### Project Details

__NOTOC__ <headertabs />

__NOTOC__

[Validation Project](Category:OWASP_Project "wikilink") [Category:OWASP
Tool](Category:OWASP_Tool "wikilink") [Category:OWASP
Download](Category:OWASP_Download "wikilink")