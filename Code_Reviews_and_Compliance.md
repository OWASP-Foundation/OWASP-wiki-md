__TOC__

## Introduction

The Payment Card Industry Data Security Standard (referred to as PCI
from now on) became a mandatory compliance step for companies processing
credit card payments in June 2005.

Performing code reviews on custom code has been a requirement since the
first version of the standard. This section will discuss what needs to
be done with regards to code reviews to be compliant with the relevant
PCI requirements.

## Code Review Requirements

The PCI standard contains several points relating to secure application
development, but we will focus solely on the points which mandate code
reviews here. All of the points relating to code reviews can be found in
requirement 6: Develop and maintain secure systems and applications.
Specifically requirement 6.3.7 mandates a code review of custom code:

**6.3.7 - Review of custom code prior to release to production or
customers in order to identify any potential coding vulnerability.**
This requirement could be interpreted to mean that the code review must
consider other PCI requirements, namely:

**6.3.5 - Removal of custom application accounts, usernames, and
passwords before applications become active or are released to
customers**
**6.5 - Develop all web applications based on secure coding guidelines
such as the Open Web Application Security Project guidelines. Review
custom application code to identify coding vulnerabilities. Cover
prevention of common coding vulnerabilities in software development
processes, to include the following:**
6.5.1 Unvalidated input
6.5.2 Broken access control (for example, malicious use of user IDs)
6.5.3 Broken authentication and session management (use of account
credentials and session cookies)
6.5.4 Cross-site scripting (XSS) attacks
6.5.5 Buffer overflows
6.5.6 Injection flaws (for example, structured query language (SQL)
injection)
6.5.7 Improper error handling
6.5.8 Insecure storage
6.5.9 Denial of service
6.5.10 Insecure configuration management
The standard does not discuss specific methodologies that need to be
followed, so any of the approaches outlined in this guide could be used.
The current version of the standard (version 1.1 at the time of writing)
introduced requirement 6.6. This requirement gave companies two
options:
**1) Having all custom application code reviewed for common
vulnerabilities by an organisation that specialises in application
security**

**2) Installing an application layer firewall in front of web-facing
applications**

The PCI Council expanded option one to include internal resources
performing code reviews. This added weight to an internal code review
and should provide an additional reason to ensure this process is
performed correctly.

[Category:OWASP Code Review
Project](Category:OWASP_Code_Review_Project "wikilink")