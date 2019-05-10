This section describes the OWASP web application security testing
methodology and explains how to test for evidence of vulnerabilities
within the application due to deficiencies with identified security
controls.

**What is Web Application Security Testing?**
A security test is a method of evaluating the security of a computer
system or network by methodically validating and verifying the
effectiveness of application security controls. A web application
security test focuses only on evaluating the security of a web
application. The process involves an active analysis of the application
for any weaknesses, technical flaws, or vulnerabilities. Any security
issues that are found will be presented to the system owner, together
with an assessment of the impact, a proposal for mitigation or a
technical solution.

**What is a Vulnerability?**
A vulnerability is a flaw or weakness in a system's design,
implementation, operation or management that could be exploited to
compromise the system's security objectives.

**What is a Threat?**
A threat is anything (a malicious external attacker, an internal user, a
system instability, etc) that may harm the assets owned by an
application (resources of value, such as the data in a database or in
the file system) by exploiting a vulnerability.

**What is a Test?**
A test is an action to demonstrate that an application meets the
security requirements of its stakeholders.

**The Approach in Writing this Guide**

The OWASP approach is open and collaborative:

  - Open: every security expert can participate with his or her
    experience in the project. Everything is free.
  - Collaborative: brainstorming is performed before the articles are
    written so the team can share ideas and develop a collective vision
    of the project. That means rough consensus, a wider audience and
    increased participation.

This approach tends to create a defined Testing Methodology that will
be:

  - Consistent
  - Reproducible
  - Rigorous
  - Under quality control

The problems to be addressed are fully documented and tested. It is
important to use a method to test all known vulnerabilities and document
all the security test activities.

**What is the OWASP testing methodology?**
Security testing will never be an exact science where a complete list of
all possible issues that should be tested can be defined. Indeed,
security testing is only an appropriate technique for testing the
security of web applications under certain circumstances. The goal of
this project is to collect all the possible testing techniques, explain
these techniques, and keep the guide updated. The OWASP Web Application
Security Testing method is based on the black box approach. The tester
knows nothing or has very little information about the application to be
tested.

The testing model consists of:

  - Tester: Who performs the testing activities
  - Tools and methodology: The core of this Testing Guide project
  - Application: The black box to test

The test is divided into 2 phases:

  - Phase 1 Passive mode:

In the passive mode the tester tries to understand the application's
logic and plays with the application. Tools can be used for information
gathering. For example, an HTTP proxy can be used to observe all the
HTTP requests and responses. At the end of this phase, the tester should
understand all the access points (*gates*) of the application (e.g.,
HTTP headers, parameters, and cookies). The Information Gathering
section explains how to perform a passive mode test.

For example the tester could find the following:

    https://www.example.com/login/Authentic_Form.html

This may indicate an authentication form where the application requests
a username and a password.

The following parameters represent two access points (gates) to the
application:

    http://www.example.com/Appx.jsp?a=1&b=1

In this case, the application shows two gates (parameters a and b). All
the gates found in this phase represent a point of testing. A
spreadsheet with the directory tree of the application and all the
access points would be useful for the second phase.

  - Phase 2 Active mode:

In this phase the tester begins to test using the methodology described
in the follow sections.

The set of active tests have been split into 11 sub-categories for a
total of 91 controls:

  - Information Gathering
  - Configuration and Deployment Management Testing
  - Identity Management Testing
  - Authentication Testing
  - Authorization Testing
  - Session Management Testing
  - Input Validation Testing
  - Error Handling
  - Cryptography
  - Business Logic Testing
  - Client Side Testing