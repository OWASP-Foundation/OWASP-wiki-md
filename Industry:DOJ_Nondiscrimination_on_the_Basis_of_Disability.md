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

### Submission Response

This response is submitted on behalf of the Open Web Application
Security Project (OWASP) by the OWASP Global Industry Committee. OWASP
is a worldwide free and open community focused on improving the security
of application software. Our mission is to make application security
"visible," so that people and organizations can make informed decisions
about application security risks. Everyone is free to participate in
OWASP and all of our materials are available under a free and open
software license. The OWASP Foundation is a U.S. recognized 501(c)(3)
not-for-profit charitable organization that ensures the ongoing
availability and support for our work at OWASP. OWASP has previously
submitted responses to related standards and guidance:

:\*BS 8878:2009 Web accessibility. Building accessible experiences for
disabled people DPC

:\*W3C Mobile Web Application Best Practices Working Draft and NIST
documents such as NIST SP 800-37 (Rev 1), SP 800-53 (Rev 3), SP 800-122
and IR 7628.

OWASP produces guidance documents, standards and tools such as the Top
Ten, Development Guide, Code Review Guide, Testing Guide, Application
Security Verification Standard and the Software assurance Maturity
Model. These are already referenced by organizations such as DISA, NIST,
NSA and the FFIEC. Reference: OWASP Citations
<http://www.owasp.org/index.php/Industry:Citations>

1\) Should the Department adopt the WCAG 2.0s "Level AA Success
Criteria" as it's standard for Web site accessibility for entities
covered by Titles II and III of the ADA? Is there any reason why the
Department should consider adopting another success criteria level of
the WCAG 2.0? From a website security point of view, WCAG 2.0s "Level AA
Success Criteria" is not inconsistent with having a secure website.
Conformance levels A, AA and AAA all require additional considerations
for security due to the use of:

:\*input, storage and output of additional text

:\*alternative forms of CATCHA

:\*input, storage and output of additional files

:\*third-party services

:\*additional client-side scripting

:\*flexible session timeouts

:\*enforcing code validity These can all be achieved using secure
development practices, but the additional requirements increase
complexity. There is one aspect in the more stringent "Level AAA Success
Criteria" which would be difficult to achieve in a secure manner:

:\*re-authentication recovery Reference: "Can an accessible web
application be secure? Assessment issues for security testers,
developers and auditors", Colin Watson, OWASP AppSec Europe 2009,
<http://www.owasp.org/images/2/22/AppSecEU09_owasp_appsec_eu09_colin_watson_2.ppt>

6\) What Resources and services are available to public accommodations
and public entities to make their Web sites accessible? What is the
ability of covered entities to make their Web sites accessible with
in-house staff? What technical assistance should the Department make
available to public entities and public accommodations to assist them
with complying with this rule? The W3C WAI pages on WCAG 2.0 provide
ample information. In particular the "Techniques and Failures for Web
Content Accessibility Guidelines 2.0" provide excellent guidance and
duplication of this effort elsewhere would appear to be un-necessary. In
terms of ensuring the security is maintained, we recommend OWASP's own
guidance documents, standards and tools such as the Top Ten, Development
Guide, Code Review Guide, Testing Guide, Application Security
Verification Standard and the Software assurance Maturity Model. These
are already referenced by organizations such as DISA, NIST, NSA and the
FFIEC. Reference: OWASP Citations
<http://www.owasp.org/index.php/Industry:Citations>

7\) Are there distinct or specialized features used on Web sites that
render compliance with accessibility requirements difficult or
impossible?

When applying website accessibility standards to transactional websites.
(E-commerce, financial, healthcare, educational, eGovernment,
hospitality, recreational, services, transportation, legal, et alia) It
is important for users to understand that these websites must comply
with security standards set forth to protect customer, patient and
student information. These same security standards could make it more
difficult for users with disabilities to utilize transactional websites.

The following features may render compliance with accessibility
requirements difficult or impossible, however they are very important
tools in protecting sensitive information in a transactional website.

Session Timeout

  -
    One such standard is enforcing a session timeout. Session tokens
    that do not expire on the HTTP server can allow an attacker
    unlimited time to guess or brute-force a valid authenticated session
    token. If a user’s cookie file is captured or brute-forced, then an
    attacker can use these static session tokens to gain access to that
    user’s web account for that site. OWASP recommends that idle session
    time out for highly protected web applications are set at 5 minutes
    and no more than 20 minutes for low risk applications.

Passwords

  -
    OWASP Recommends that website security policy for passwords include
    the following:
      - Password change frequency
      - Enforcement of a minimum password length
      - No maximum password length limits
      - Previous passwords should not be allowed to be chosen
      - Password lock out policy
      - Password complexity requirements
      - Password lock out

Strong Authentication

  -
    Strong authentication (such as tokens, certificates, etc) provides a
    higher level of security than username and passwords. The
    generalized form of strong authentication is “something you know,
    something you hold”. Therefore, anything that requires a secret (the
    “something you know”) and authenticator like a token, USB fob, or
    certificate (the “something you hold”) is a stronger control than
    username and passwords (which is just “something you know”) or
    biometrics (“something you are”).

OWASP recommends strong authentication for certain applications:

:\*for high value transactions

:\*where privacy is a strong or legally compelled consideration (such as
health records, government records, etc)

:\*where audit trails are legally mandated and require a strong
association between a person and the audit trail, such as banking
applications

:\*administrative access for high value or high risk systems

CAPTCHA

  -
    OWASP does not recommend the use of CAPTCHA. Instead OWASP
    recommends that Website owner provide another method to sign up or
    register for a website offline or via another method. Site should
    use a “no follow” tag. Another option is to limit privileges of a
    newly signed up account or similar until a positive validation has
    occurred.

8\) Given that most websites today provide significant amounts of
services and information in a dynamic, evolving setting that would be
difficult, if not impossible, to replicate through alternative,
accessible means, to what extent can accessible alternatives still be
provided? Might viable accessible alternatives still exist for simple,
non-dynamic Web sites? It is important that alternative means provide
the same level of protection to the users, their data and the business
systems, so that for example weaker authentication requirements in an
alternative telephone service make it easier to steal a person's
identity than through an online website service, or the telephone
service can be used to assist exploitation of the website (e.g.
enumerate usernames).

19\) The Department is interested in gathering other information or data
relating to the Department’s objective to provide requirements for Web
accessibility under titles II and III of the ADA. Are there additional
issues or information not addressed by the Department’s questions that
are important for the Department to Consider? In the OWASP response to
Question 1, we stated that an accessible website can be secure. It is
also worth mentioning that an insecure website possibly may not be
accessible because it would be possible to create web pages (responses)
which do not meet the conformance requirements. A simple example would
be injecting code which includes inaccessible content from a third party
website, or which breaks the code validity because an extra H1 tag has
been inserted.

### Draft Text version 2

This response is submitted on behalf of the Open Web Application
Security Project (OWASP) by the OWASP Global Industry Committee. OWASP
is a worldwide free and open community focused on improving the security
of application software. Our mission is to make application security
"visible," so that people and organizations can make informed decisions
about application security risks. Everyone is free to participate in
OWASP and all of our materials are available under a free and open
software license. The OWASP Foundation is a U.S. recognized 501(c)(3)
not-for-profit charitable organization that ensures the ongoing
availability and support for our work at OWASP. OWASP has previously
submitted responses to related standards and guidance:

:\*BS 8878:2009 Web accessibility. Building accessible experiences for
disabled people DPC

:\*W3C Mobile Web Application Best Practices Working Draft and NIST
documents such as NIST SP 800-37 (Rev 1), SP 800-53 (Rev 3), SP 800-122
and IR 7628.

1\) Should the Department adopt the WCAG 2.0s "Level AA Success
Criteria" as it's standard for Web site accessibility for entities
covered by Titles II and III of the ADA? Is there any reason why the
Department should consider adopting another success criteria level of
the WCAG 2.0? From a website security point of view, WCAG 2.0s "Level AA
Success Criteria" is not inconsistent with having a secure website.
Conformance levels A, AA and AAA all require additional considerations
for security due to the use of:

:\*input, storage and output of additional text

:\*alternative forms of CATCHA

:\*input, storage and output of additional files

:\*third-party services

:\*additional client-side scripting

:\*flexible session timeouts

:\*enforcing code validity These can all be achieved using secure
development practices, but the additional requirements increase
complexity. There is one aspect in the more stringent "Level AAA Success
Criteria" which would be difficult to achieve in a secure manner:

:\*re-authentication recovery Reference: "Can an accessible web
application be secure? Assessment issues for security testers,
developers and auditors", Colin Watson, OWASP AppSec Europe 2009,
<http://www.owasp.org/images/2/22/AppSecEU09_owasp_appsec_eu09_colin_watson_2.ppt>

6\) What Resources and services are available to public accommodations
and public entities to make their Web sites accessible? What is the
ability of covered entities to make their Web sites accessible with
in-house staff? What technical assistance should the Department make
available to public entities and public accommodations to assist them
with complying with this rule? The W3C WAI pages on WCAG 2.0 provide
ample information. In particular the "Techniques and Failures for Web
Content Accessibility Guidelines 2.0" provide excellent guidance and
duplication of this effort elsewhere would appear to be un-necessary. In
terms of ensuring the security is maintained, we recommend OWASP's own
guidance documents, standards and tools such as the Top Ten, Development
Guide, Code Review Guide, Testing Guide, Application Security
Verification Standard and the Software assurance Maturity Model. These
are already referenced by organizations such as DISA, NIST, NSA and the
FFIEC. Reference: OWASP Citations
<http://www.owasp.org/index.php/Industry:Citations>

7\) Are there distinct or specialized features used on Web sites that
render compliance with accessibility requirements difficult or
impossible? At Conformance Level AA, no.

When applying website accessibility standards to transactional websites.
(E-commerce, financial, healthcare, educational) It is important for
users to understand that these websites must comply with security
standards set forth to protect customer, patient and student
information. These same security standards could make it more difficult
for users with disabilities to utilize transactional websites.

The following features may render compliance with accessibility
requirements difficult or impossible, however they are very important
tools in protecting sensitive information in a transactional website.

Session Timeout

  -
    One such standard is enforcing a session timeout. Session tokens
    that do not expire on the HTTP server can allow an attacker
    unlimited time to guess or brute-force a valid authenticated session
    token. If a user’s cookie file is captured or brute-forced, then an
    attacker can use these static session tokens to gain access to that
    user’s web account for that site. OWASP recommends that idle session
    time out for highly protected web applications are set at 5 minutes
    and no more than 20 minutes for low risk applications.

Passwords

  -
    OWASP Recommends that website security policy for passwords include
    the following:
      - Password change frequency
      - Enforcement of a minimum password length
      - No maximum password length limits
      - Previous passwords should not be allowed to be chosen
      - Password lock out policy
      - Password complexity requirements
      - Password lock out

Strong Authentication

  -
    Strong authentication (such as tokens, certificates, etc) provides a
    higher level of security than username and passwords. The
    generalized form of strong authentication is “something you know,
    something you hold”. Therefore, anything that requires a secret (the
    “something you know”) and authenticator like a token, USB fob, or
    certificate (the “something you hold”) is a stronger control than
    username and passwords (which is just “something you know”) or
    biometrics (“something you are”).

OWASP recommends strong authentication for certain applications:

:\*for high value transactions

:\*where privacy is a strong or legally compelled consideration (such as
health records, government records, etc)

:\*where audit trails are legally mandated and require a strong
association between a person and the audit trail, such as banking
applications

:\*administrative access for high value or high risk systems

CAPTCHA

  -
    OWASP does not recommend the use of CAPTCHA. Instead OWASP
    recommends that Website owner provide another method to sign up or
    register for a website offline or via another method. Site should
    use a “no follow” tag. Another option is to limit privileges of a
    newly signed up account or similar until a positive validation has
    occurred.

8\) Given that most websites today provide significant amounts of
services and information in a dynamic, evolving setting that would be
difficult, if not impossible, to replicate through alternative,
accessible means, to what extent can accessible alternatives still be
provided? Might viable accessible alternatives still exist for simple,
non-dynamic Web sites? It is important that alternative means provide
the same level of protection to the users, their data and the business
systems, so that for example weaker authentication requirements in an
alternative telephone service make it easier to steal a person's
identity than through an online website service, or the telephone
service can be used to assist exploitation of the website (e.g.
enumerate usernames).

19\) The Department is interested in gathering other information or data
relating to the Department’s objective to provide requirements for Web
accessibility under titles II and III of the ADA. Are there additional
issues or information not addressed by the Department’s questions that
are important for the Department to Consider? In the OWASP response to
Question 1, we stated that an accessible website can be secure. It is
also worth mentioning that an insecure website possibly may not be
accessible because it would be possible to create web pages (responses)
which do not meet the conformance requirements. A simple example would
be injecting code which includes inaccessible content from a third party
website, or which breaks the code validity because an extra H1 tag has
been inserted.

### Draft Text version 1

### CW's notes

*CW: I think the following questions posed by the DoJ are the most
relevant for response by OWASP. My comments on each of those are
included below.*

1.) Should the Department adopt the WCAG 2.0s "Level AA Success
Criteria" as it's standard for Web site accessibility for entities
covered by Titles II and III of the ADA? Is there any reason why the
Department should consider adopting another success criteria level of
the WCAG 2.0?

  -
    From a website security point of view, WCAG 2.0s "Level AA Success
    Criteria" is not inconsistent with having a secure website.
    Conformance levels A, AA and AAA all require additional
    considerations for security due to the use of:
      - input, storage and output of additional text
      - alternative forms of CATCHA
      - input, storage and output of additional files
      - third party services
      - additional client-side scripting
      - flexible session timeouts
      - enforcing code validity
    These can all be achieved using secure development practices, but
    the additional requirements increase complexity. There is one aspect
    in the more stringent "Level AAA Success Criteria" which would be
    difficult to achieve in a secure manner:
      - re-authentication recovery
    Reference: "Can an accessible web application be secure? Assessment
    issues for security testers, developers and auditors", Colin Watson,
    OWASP AppSec Europe 2009,
    <http://www.owasp.org/images/2/22/AppSecEU09_owasp_appsec_eu09_colin_watson_2.ppt>

6.) What Resources and services are available to public accommodations
and public entities to make their Web sites accessible? What is the
ability of covered entities to make their Web sites accessible with
in-house staff? What technical assistance should the Department make
available to public entities and public accommodations to assist them
with complying with this rule?

  -
    The W3C WAI pages on WCAG 2.0 provide ample information. In
    particular the "Techniques and Failures for Web Content
    Accessibility Guidelines 2.0" provide excellent guidance and
    duplication of this effeort elsewhere would appear to be
    un-necessary. In terms of ensuring the security is maintained, we
    recommed OWASP's own guidance documents, standards and tools such as
    the Top Ten, Development Guide, Code Review Guide, Testing Guide,
    Application Securitity Versification Standard and the Software
    assurance Maturity Model. These are already referenced by
    organisations such as DISA, NIST, NSA and the FFIEC.
    Reference: OWASP Citations
    <http://www.owasp.org/index.php/Industry:Citations>''

7.) Are there distinct or specialized features used on Web sites that
render compliance with accessibility requirements difficult or
impossible?

  -
    At Conformance Level AA, no.

8.) Given that most websites today provide significant amounts of
services and information in a dynamic, evolving setting that would be
difficult, if not impossible, to replicate through alternative,
accessible means, to what extent can accessible alternatives still be
provided? Might viable accessible alternatives still exist for simple,
non-dynamic Web sites?

  -
    It is important that alternative means provide the same level of
    protection to the users, their data and the business systems, so
    that for example weaker authentication requirements in an
    alternative telephone service make it easier to steal a person's
    identity than through an online website service, or the telephone
    service can be used to assist exploitation of the website (e.g.
    enumerate usernames).

19.) The Department is interested in gathering other information or data
relating to the Department’s objective to provide requirements for Web
accessibility under titles II and III of the ADA. Are there additional
issues or information not addressed by the Department’s questions that
are important for the Department to Consider?

  -
    In the OWASP response to Question 1, we stated that an accessible
    website can be secure. It is also worth mentioning that an insecure
    website possibly may not be accessible because it would be possible
    to create web pages (responses) which are do not met the conformance
    requirements. A simple example would be injecting code which
    includes inaccessible content from a third party website, or which
    breaks the code validity because an extra H1 tag has been inserted.

*Some customised About OWASP text*

This response is submitted on behalf of the Open Web Application
Security Project (OWASP) by the OWASP Global Industry Committee. OWASP
is a worldwide free and open community focused on improving the security
of application software. Our mission is to make application security
"visible," so that people and organizations can make informed decisions
about application security risks. Everyone is free to participate in
OWASP and all of our materials are available under a free and open
software license. The OWASP Foundation is a U.S. recognized 501(c)(3)
not-for-profit charitable organization, that ensures the ongoing
availability and support for our work at OWASP.

OWASP has previously submitted responses to related standards and
guidance:

  - BS 8878:2009 Web accessibility. Building accessible experiences for
    disabled people DPC
  - W3C Mobile Web Application Best Practices Working Draft

and NIST documents such as NIST SP 800-37 (Rev 1), SP 800-53 (Rev 3), SP
800-122 and IR 7628.

Return to [Global Industry
Committee](Global_Industry_Committee "wikilink")