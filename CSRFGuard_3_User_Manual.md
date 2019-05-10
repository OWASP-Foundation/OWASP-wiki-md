# Overview

Welcome to the OWASP CSRFGuard 3 User Manual\! The purpose of this
article is to provide the user with guidance on obtaining, installing,
deploying, and developing with the OWASP CSRFGuard library. The author's
goal was to keep the User Manual informative, use to understand, and
concise. If you find that one or more aspects of this document does not
adhere to these goals, please me know at eric dot sheridan at owasp dot
org.

# Download

Users can download the latest release of OWASP CSRFGuard using one of
the following links:

Download and build the source at -
<https://github.com/aramrami/OWASP-CSRFGuard>

# Installation

Installation of OWASP CSRFGuard 3 is very straight forward requiring
three simple steps:

:\# Copy the Owasp.CsrfGuard.jar file to your application's classpath

:\# Declare CsrfGuard in your application's deployment descriptor
(web.xml)

:\# Configure the Owasp.CsrfGuard.properties file as you see fit

[Click here](CSRFGuard_3_Installation "wikilink") for more detailed
information regarding the installation of OWASP CSRFGuard.

# Configuration

The minimum configuration settings that users should review include:

:\* Default new token landing page
(org.owasp.csrfguard.NewTokenLandingPage)

:\* Support for Ajax and XMLHttpRequest (org.owasp.csrfguard.Ajax)

:\* URI resources that should not be protected
(org.owasp.csrfguard.unprotected.\*)

:\* Actions executed when an attack is detected
(org.owasp.csrfguard.action.\*)

[Click here](CSRFGuard_3_Configuration "wikilink") for more information
regarding the configuration of OWASP CSRFGuard.

# Token Injection

Users of OWASP CSRFGuard can inject prevention tokens into HTML using
two strategies:

:\* JavaScript DOM Manipulation - largely automated process requiring
minimal effort and is ideal for most web applications

:\* JSP Tag Library - provides fine grained strategy ideal for
situations where automated DOM manipulation is insufficient.

[Click here](CSRFGuard_3_Token_Injection "wikilink") for more
information regarding the injection of CSRF prevention tokens within
your application.

# Known Issues

The following is a quick bulleted list of known issues within the
current release:

:\* No known way to inject CSRF prevention tokens into setters of
document.location (ex: document.location="<http://www.owasp.org>";)

[Category:OWASP_CSRFGuard_Project](Category:OWASP_CSRFGuard_Project "wikilink")