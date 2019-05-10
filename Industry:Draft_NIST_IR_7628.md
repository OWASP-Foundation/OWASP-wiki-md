__NOTOC__

Return to [Global Industry
Committee](Global_Industry_Committee "wikilink")

| colspan="4" align="center" style="background:\#4058A0; color:white" | <font color="white">**ACTIVITY IDENTIFICATION** |
| ------------------------------------------------------------------- | ----------------------------------------------- |
| style="width:15%; background:\#7B8ABD" align="center"               | **Activity Name**                               |
| style="width:25%; background:\#7B8ABD" align="center"               | **Short Description**                           |
| style="width:25%; background:\#7B8ABD" align="center"               | '''Related Projects '''                         |
| style="width:25%; background:\#7B8ABD" align="center"               | **Email Contacts & Roles**                      |

| colspan="4" align="center" style="background:\#4058A0; color:white" | <font color="white">**ACTIVITY SPECIFICS** |
| ------------------------------------------------------------------- | ------------------------------------------ |
| style="width:25%; background:\#7B8ABD" align="center"               | **Objectives**                             |
| style="width:25%; background:\#7B8ABD" align="center"               | **Deadlines**                              |
| style="width:25%; background:\#7B8ABD" align="center"               | **Status**                                 |
| style="width:25%; background:\#7B8ABD" align="center"               | **Resources**                              |
|                                                                     |                                            |

## Submission Response

*Latest first*

### Final version

This response is submitted on behalf of the Open Web Application
Security Project (OWASP) <http://www.owasp.org/> by the OWASP Global
Industry Committee
<http://www.owasp.org/index.php/Global_Industry_Committee>.

#### DHS-2.15.3.2 Supplemental Guidance

"The organization specifically authorizes and monitors the use of
guest/anonymous accounts and removes, disables, or otherwise secures
unnecessary accounts."

We recommend: This text is amended to mention that anonymous/guest
accounts are not recommended whenever reasonably avoidable.

#### DHS-2.15.20/ NIST SP 800-53 AC-7 Unsuccessful Login Attempts

Comments: In possibly publicly accessible systems, it may be difficult
to identify a particular user and multiple invalid authentication
attempts should be restricted by total errors, and by errors from host
address ranges, as well as by user account.

We recommend: In Supplemental Guidance add "Automatic lockouts by remote
address range may also need to be considered where multiple accounts are
targeted in a brute force attack on authentication mechanisms."

#### DHS-2.15.19/ NIST SP 800-53 AC-9 Previous Logon Notification

It is useful to see not only the previous successful logon, but all
recent significant activity.

We recommend: Add "The system notifies the user of all successful and
unsuccessful logon attempts in the last week/month/quarter" and add "The
system notifies the user of all critical changes (CRUD) undertaken, on
the system or by other methods (e.g., automatic patching), in the last
week/month/quarter"

#### DHS-2.16.2/ NIST SP 800-53 AU-2, AU-13 Auditable Events

The OWASP Enterprise Security API (ESAPI) Toolkits help software
developers guard against security-related design and implementation
flaws. The exception classes (e.g., in the Java EE version) define the
types of security-related errors that should be identified and logged
for web applications.

<http://www.owasp.org/index.php/Category:OWASP_Enterprise_Security_API>

For web applications, the exception classes defined in the current
version of the OWASP ESAPI project should be used as a guide.

#### DHS-2.16.3/ NIST SP 800-53 AU-3 Content of Audit Records

For web applications, additional information is available which assist
with the creation of a full audit trail. In Supplemental Guidance add
"The user agent, remote host and any x-forwarded-for values should also
be recorded for web enabled systems. In higher risk systems or more
critical functions (identified by type, location or subject) the request
headers, response headers and response body could also be included.".

OWASP Enterprise Security API, The Open Web Application Security
Project, <http://www.owasp.org/index.php/ESAPI>

OWASP ESAPI Java EE error exception classes, The Open web Application
Security Project,
<http://owasp-esapi-java.googlecode.com/svn/trunk_doc/org/owasp/esapi/errors/package-summary.html>

For web applications, the record content defined in the current version
of the OWASP ESAPI project should be used as a guide i.e.

  - provide a mechanism for setting the logging level threshold that is
    currently enabled. This usually works by logging all events at and
    above that severity level, and discarding all events below that
    level. This is usually done via configuration, but can also be made
    accessible programmatically.
  - ensure that dangerous HTML characters are encoded before they are
    logged to defend against malicious injection into logs that might be
    viewed in an HTML based log viewer.
  - encode any CRLF characters included in log data in order to prevent
    log injection attacks.
  - avoid logging the user's session ID. Rather, they should log
    something equivalent like a generated logging session ID, or a
    hashed value of the session ID so they can track session specific
    events without risking the exposure of a live session's ID.
  - record the following information with each event:
      - identity of the user that caused the event,
      - a description of the event (supplied by the caller),
      - whether the event succeeded or failed (indicated by the caller),
      - severity level of the event (indicated by the caller),
      - that this is a security relevant event (indicated by the
        caller),
      - hostname or IP where the event occurred (and ideally the user's
        source IP as well),
      - a time stamp
  - filter out any sensitive data specific to the current application or
    organization.

#### DHS-2.10.3/ NIST SP 800-53 CA-2 System Monitoring and Evaluation

Penetration testing is an essential component of a comprehensive
security program and is a key way in which compliance efforts related to
FIPS 200 and NIST 800-53 can make a material impact on system security.

Also in the supplemental guidance, "Changing security requirements and
discovery of vulnerabilities necessitate a review.", changes to the
environment such as new threats should also necessitate a review.

#### DHS-2.8.7/ NIST SP 800-53 SC-2, SC-7, SC-32 Boundary Protection

Administrative functions should be appropriately segregated from user
activity, so the latter cannot access or utilize administrator
functionality.

We recommend adding to the Supplemental Guidance, "Web administrative
interfaces should use separate authentication methods for users of any
other resources. This may include isolating the administrative interface
on a different domain and with additional access controls. In a web
application environment, if a higher value system does not use strong
authentication and encrypted channels to log on to the interface, the
system may be vulnerable from privilege escalation, eavesdropping, man
in the middle and replay attacks."

Administrative Interfaces, pp220-222, A Guide to Building Secure Web
Applications and Web Services, v2.0, The Open Web Application Security
Project, <http://www.owasp.org/index.php/Category:OWASP_Guide_Project>

#### DHS-2.8.16/ NIST SP 800-53 SC-18 Mobile Code

We recommend providing a greater level of detail and references to
specific vulnerabilities - including XSS, CSRF and others. We also
recommend referencing external best practices like the OWASP Top 10:
<http://www.owasp.org/index.php/Category:OWASP_Top_Ten_Project>

#### DHS-2.8.17/ NIST SP 800-53 SC-19 Voice-Over Internet Protocol

If used, any administrative access points should be included in
vulnerability assessment and penetration testing efforts.

#### DHS-2.14.3/ NIST SP 800-53 SI-3 Malicious Code Protection

Malicious code may be present in custom-built software. This could
include time bombs, back doors, Easter eggs, salami attacks and other
types of attack that could affect business processes. Traditional
anti-malware products are not built to detect such code, and instead
secure development, procurement, configuration and monitoring practices
are required to ensure software does not perform functions other than
those intended.

We recommend that enhancements item 12 "12. The authenticity of all
firmware/software shall be verified prior to loading on any component of
the AMI system or device connected to the AMI network." should also
mention that verification needs to "examine and test all software for
malicious code". Also add an enhancement "Verify software quality
(including security) before configuration and monitors for, and performs
audits to identify, unauthorized changes to production software code."

Malicious Code Verification Requirements, V13, OWASP Application
Security Verification Standards (ASVS), The Open Web Application
Security Project <http://www.owasp.org/index.php/ASVS>

#### DHS-2.14.10/ NIST SP 800-53 SI-10 Information Input Accuracy, Completeness, Validity, and Authenticity

Software developers often expect a single value for each data input, but
bad design or a malicious user might lead to more than one value being
submitted. The format and content of structured data should be tested
against what is defined. Information could be accurate, complete, valid
and authentic but still be contrary to valid business logic. These
concerns need to be built into the checking processes.

Validity checks should include "character set, length, numerical range,
acceptable values, integrity, character set and cardinality". Also where
a specification exists for data (e.g., an XML schema, data interchange
standard), both compliance with the permissible structure and the values
contained should be undertaken. The validity of information may depend
on other factors such as business logic, timing and related
transactions.

Reference: Data Validation, pp161-172, A Guide to Building Secure Web
Applications and Web Services, v2.0, The Open Web Application Security
Project, <http://www.owasp.org/index.php/Category:OWASP_Guide_Project>

#### DHS-2.14.12/ NIST SP 800-53 SI-12 Information Output Handling and Retention

There should be appropriate encoding/encryption of information generated
by the system or supplied to other systems. The proper validation,
formatting and encoding of such information is just as important as
making sure the inputs are correct. Incorrect output checking could leak
sensitive information. For web applications, incorrect output encoding
can lead to issues such as cross-site scripting (XSS) attacks on web
browser users.

#### Appendix C NIST CSCTG Vulnerability Classes

In C.3.1.3. Authorization Vulnerability, add "Insecure direct object
references" and "Failure to restrict URL access" to examples.

In C.3.1.7. General Logic Errors, add "Business logic flaw" to examples.

In C.3.1.8. Input Validation, change title to "Input and Output
Validation", and add "Unvalidated redirects and forwards" to examples.

In C.3.1.12. Protocol Errors, add "Insufficient transport layer
protection", "Use of weak SSL/TLS protocols", "SSL/TLS key exchange
without authentication", "SSL/TLS weak key exchange" and "Low SSL/TLS
cipher strength" to examples.

SSL Server Rating Guide <https://www.ssllabs.com/projects/rating-guide/>

In C.3.1.13. Range and Type Error Vulnerability, add "Cardinality
incorrect", "Value integrity modification" and "Sequencing or timing
error" to examples.

In C.3.1.15. Session Management Vulnerability, add "Cross site request
forgery", "Cookie attributes not set securely (e.g. domain, secure and
HTTPonly)" and "Overly long session timeout" to examples.

### Draft Text version 1

This response is submitted on behalf of the Open Web Application
Security Project (OWASP) <http://www.owasp.org/> by the OWASP Global
Industry Committee
<http://www.owasp.org/index.php/Global_Industry_Committee>.

#### DHS-2.15.3.2 Supplemental Guidance

"The organization specifically authorizes and monitors the use of
guest/anonymous accounts and removes, disables, or otherwise secures
unnecessary accounts."

We recommend: This text is amended to mention that anonymous/guest
accounts are not recommended whenever reasonably avoidable.

#### DHS-2.15.20/ NIST SP 800-53 AC-7 Unsuccessful Login Attempts

Comments: In possibly publicly accessible systems, it may be difficult
to identify a particular user and multiple invalid authentication
attempts should be restricted by total errors, and by errors from host
address ranges, as well as by user account.

We recommend: In Supplemental Guidance add "Automatic lockouts by remote
address range may also need to be considered where multiple accounts are
targeted in a brute force attack on authentication mechanisms."

#### DHS-2.15.19/ NIST SP 800-53 AC-9 Previous Logon Notification

It is useful to see not only the previous successful logon, but all
recent significant activity.

We recommend: Add "The system notifies the user of all successful and
unsuccessful logon attempts in the last week/month/quarter" and add "The
system notifies the user of all critical changes (CRUD) undertaken, on
the system or by other methods (e.g., automatic patching), in the last
week/month/quarter"

#### DHS-2.16.2/ NIST SP 800-53 AU-2, AU-13 Auditable Events

The OWASP Enterprise Security API (ESAPI) Toolkits help software
developers guard against security-related design and implementation
flaws. The exception classes (e.g., in the Java EE version) define the
types of security-related errors that should be identified and logged
for web applications.

<http://www.owasp.org/index.php/Category:OWASP_Enterprise_Security_API>

For web applications, the exception classes defined in the current
version of the OWASP ESAPI project should be used as a guide.

#### DHS-2.16.3/ NIST SP 800-53 AU-3 Content of Audit Records

For web applications, additional information is available which assist
with the creation of a full audit trail. In Supplemental Guidance add
"The user agent, remote host and any x-forwarded-for values should also
be recorded for web enabled systems. In higher risk systems or more
critical functions (identified by type, location or subject) the request
headers, response headers and response body could also be included.".

OWASP Enterprise Security API, The Open Web Application Security
Project, <http://www.owasp.org/index.php/ESAPI>

OWASP ESAPI Java EE error exception classes, The Open web Application
Security Project,
<http://owasp-esapi-java.googlecode.com/svn/trunk_doc/org/owasp/esapi/errors/package-summary.html>

For web applications, the record content defined in the current version
of the OWASP ESAPI project should be used as a guide i.e.

  - provide a mechanism for setting the logging level threshold that is
    currently enabled. This usually works by logging all events at and
    above that severity level, and discarding all events below that
    level. This is usually done via configuration, but can also be made
    accessible programmatically.
  - ensure that dangerous HTML characters are encoded before they are
    logged to defend against malicious injection into logs that might be
    viewed in an HTML based log viewer.
  - encode any CRLF characters included in log data in order to prevent
    log injection attacks.
  - avoid logging the user's session ID. Rather, they should log
    something equivalent like a generated logging session ID, or a
    hashed value of the session ID so they can track session specific
    events without risking the exposure of a live session's ID.
  - record the following information with each event:
      - identity of the user that caused the event,
      - a description of the event (supplied by the caller),
      - whether the event succeeded or failed (indicated by the caller),
      - severity level of the event (indicated by the caller),
      - that this is a security relevant event (indicated by the
        caller),
      - hostname or IP where the event occurred (and ideally the user's
        source IP as well),
      - a time stamp
  - filter out any sensitive data specific to the current application or
    organization.

#### DHS-2.10.3/ NIST SP 800-53 CA-2 System Monitoring and Evaluation

Penetration testing is an essential component of a comprehensive
security program and is a key way in which compliance efforts related to
FIPS 200 and NIST 800-53 can make a material impact on system security.

Also in the supplemental guidance, "Changing security requirements and
discovery of vulnerabilities necessitate a review.", changes to the
environment such as new threats should also necessitate a review.

#### DHS-2.8.7/ NIST SP 800-53 SC-2, SC-7, SC-32 Boundary Protection

Administrative functions should be appropriately segregated from user
activity, so the latter cannot access or utilize administrator
functionality.

We recommend adding to the Supplemental Guidance, "Web administrative
interfaces should use separate authentication methods for users of any
other resources. This may include isolating the administrative interface
on a different domain and with additional access controls. In a web
application environment, if a higher value system does not use strong
authentication and encrypted channels to log on to the interface, the
system may be vulnerable from privilege escalation, eavesdropping, man
in the middle and replay attacks."

Administrative Interfaces, pp220-222, A Guide to Building Secure Web
Applications and Web Services, v2.0, The Open Web Application Security
Project, <http://www.owasp.org/index.php/Category:OWASP_Guide_Project>

#### DHS-2.8.16/ NIST SP 800-53 SC-18 Mobile Code

We recommend providing a greater level of detail and references to
specific vulnerabilities - including XSS, CSRF and others. We also
recommend referencing external best practices like the OWASP Top 10:
<http://www.owasp.org/index.php/Category:OWASP_Top_Ten_Project>

#### DHS-2.8.17/ NIST SP 800-53 SC-19 Voice-Over Internet Protocol

If used, any administrative access points should be included in
vulnerability assessment and penetration testing efforts.

#### DHS-2.14.3/ NIST SP 800-53 SI-3 Malicious Code Protection

Malicious code may be present in custom-built software. This could
include time bombs, back doors, Easter eggs, salami attacks and other
types of attack that could affect business processes. Traditional
anti-malware products are not built to detect such code, and instead
secure development, procurement, configuration and monitoring practices
are required to ensure software does not perform functions other than
those intended.

We recommend that enhancements item 12 "12. The authenticity of all
firmware/software shall be verified prior to loading on any component of
the AMI system or device connected to the AMI network." should also
mention that verification needs to "examine and test all software for
malicious code". Also add an enhancement "Verify software quality
(including security) before configuration and monitors for, and performs
audits to identify, unauthorized changes to production software code."

Malicious Code Verification Requirements, V13, OWASP Application
Security Verification Standards (ASVS), The Open Web Application
Security Project <http://www.owasp.org/index.php/ASVS>

#### DHS-2.14.10/ NIST SP 800-53 SI-10 Information Input Accuracy, Completeness, Validity, and Authenticity

Software developers often expect a single value for each data input, but
bad design or a malicious user might lead to more than one value being
submitted. The format and content of structured data should be tested
against what is defined. Information could be accurate, complete, valid
and authentic but still be contrary to valid business logic. These
concerns need to be built into the checking processes.

Validity checks should include "character set, length, numerical range,
acceptable values, integrity, character set and cardinality". Also where
a specification exists for data (e.g., an XML schema, data interchange
standard), both compliance with the permissible structure and the values
contained should be undertaken. The validity of information may depend
on other factors such as business logic, timing and related
transactions.

Reference: Data Validation, pp161-172, A Guide to Building Secure Web
Applications and Web Services, v2.0, The Open Web Application Security
Project, <http://www.owasp.org/index.php/Category:OWASP_Guide_Project>

#### DHS-2.14.12/ NIST SP 800-53 SI-12 Information Output Handling and Retention

There should be appropriate encoding/encryption of information generated
by the system or supplied to other systems. The proper validation,
formatting and encoding of such information is just as important as
making sure the inputs are correct. Incorrect output checking could leak
sensitive information. For web applications, incorrect output encoding
can lead to issues such as cross-site scripting (XSS) attacks on web
browser users.

#### Appendix C NIST CSCTG Vulnerability Classes

In C.3.1.3. Authorization Vulnerability, add "Insecure direct object
references" and "Failure to restrict URL access" to examples.

In C.3.1.7. General Logic Errors, add "Business logic flaw" to examples.

In C.3.1.8. Input Validation, change title to "Input and Output
Validation", and add "Unvalidated redirects and forwards" to examples.

In C.3.1.12. Protocol Errors, add "Insufficient transport layer
protection", "Use of weak SSL/TLS protocols", "SSL key exchange without
authentication", "SSL weak key exchange" and "Low SSL cipher strength"
to examples.

SSL Server Rating Guide <https://www.ssllabs.com/projects/rating-guide/>

In C.3.1.13. Range and Type Error Vulnerability, add "Cardinality
incorrect", "Value integrity modification" and "Sequencing or timing
error" to examples.

In C.3.1.15. Session Management Vulnerability, add "Cross site request
forgery", "Cookie attributes not set securely (e.g. domain, secure and
HTTPonly)" and "Overly long session timeout" to examples.

Return to [Global Industry
Committee](Global_Industry_Committee "wikilink")