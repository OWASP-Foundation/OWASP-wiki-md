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

\[*This response is submitted on behalf of the Open Web Application
Security Project (OWASP) <http://www.owasp.org/>. OWASP is a worldwide
free and open community focused on improving the security of application
software. Our mission is to make application security "visible," so that
people and organizations can make informed decisions about application
security risks. Everyone is free to participate in OWASP and all of our
materials are available under a free and open software license. The
OWASP Foundation is a not-for-profit charitable organization, registered
in the United States, that ensures the ongoing availability and support
for our work.*\]

0.2 Understanding accessible experiences

-----

Comment: Web sites are fast becoming something we cannot live without,
but it is insecure. User confidence is vital, and it does not matter
what the skill, knowledge, experience or ability level a user has, we
must develop web sites that are safe to use and do not create additional
risks to the user.

Proposed change: In the sentence "The goal of any web project should be
to create web experiences that are accessible, usable and enjoyable for
everyone." add the word "safe" so that it reads "The goal of any web
project should be to create web experiences that are accessible, usable,
safe and enjoyable for everyone." This would necessitate an additional
column in Table 1

Safe

-----

The user's privacy, data and computer systems are not compromised while
they accomplish their goals.

Examples

-----

No malicious code was downloaded while downloading the web content

-----

The user has confidence in the integrity of the information in the video

-----

The audio description and video are available when the user requires

-----

By changing browser settings or the type of user agent, the user should
not be at greater risk than other users

-----

5.1 Web technologies

-----

Comment: In the choice of technology, how it is implemented and
maintained, and how it interacts with the user, the servers and
third-parties should be understood so that the security risks, and hence
accessibility issues, are considered during the selection stage.

Proposed change: Add another bullet point "whether the technology could
introduce additional security vulnerabilities and how these would be
mitigated;"

6.3.2 User Agent Accessibility Guidelines (UAAG)

-----

Comment: While the website should be usable in popular browsers, this is
not sufficient for testing purposes. Developers/programmers needs to
realise that people will try and access the content using "non-browser"
tools to look for vulnerabilities and the website should be secure
enough to protect users and itself from such threats. This requires
testing beyond "popular browsers".

Proposed change: Add "Note 6 - The website must secure enough to protect
itself and its users from security vulnerabilities which may not be
apparent by limiting testing to 'a reasonable range of web browsers'.

8.2.3.3 Validation

-----

Comment: Security testing should also be undertaken at the same time.

Proposed change: Add "The Security of the website should be validated by
ensuring that vulnerabilities identified in the OWASP Top 10 are
mitigated. A comprehensive testing methodology is published by OWASP as
'OWASP Testing Guide'
<http://www.owasp.org/index.php/Category:OWASP_Testing_Project>"

8.2.3.4 Conformance inspection

-----

Comment: Undocumented or unwanted functionality can often lead to
security vulnerabilities. For a webpage to conform, every aspect must be
validated; this requires a full understanding of the webpage and how it
interacts with the user, data, servers, etc.

Proposed change: Add to the end of the first paragraph "All elements
within the webpage must be inspected. Thus any undocumented features,
functions or security vulnerabilities must also undergo validation
testing. The web site code should be reviewed to ensure no security
vulnerabilities exist that may hamper the usage and accessibility. OWASP
provides a very methodical approach to security code review that is
available under 'OWASP Code Review Guide'
<http://www.owasp.org/index.php/Category:OWASP_Code_Review_Project>"

8.2.3.6 Expert review

-----

Comment: Security is an aspect of quality (see ISO 9126)

Proposed change: Add "Quality can not be achieved without ensuring
proper security. Security is a quality vector and should be taken into
consideration while conducting expert reviews."

Annex F - F.1.2 Web developer

-----

Comment: Security is an aspect of quality (see ISO 9126). Content may
not be fully accessible, or fully comply with a particular conformance
level (e.g. WCAG 2.0) if there are security vulnerabilities.

Proposed change: Add "It is also important for a web developer to learn
secure coding. This will help reduce the risk of security
vulnerabilities in the website and provide users with a better usability
and accessibility of the content. OWASP has defined best practices for
secure coding aided with code snippets and examples that can help
developers to learn the art of secure coding."

Annex G - G.2 Criteria for measuring success

-----

Comment: Without validated security, there is no way to ensure that
webpages conform to accessibility requirements.

Proposed change: Add as a new bullet point under a) "How well the risk
of getting compromised through a security vulnerability is mitigated?
(degree of risk vs. usability)" and as a new bullet point under b) "How
low is the threat of user’s computer becoming infected through malicious
code from the website? (Degree of confidence in the website for
efficient utilization)" and as a new bullet point under c) "Perceived
security (Peace of mind / trust / reliable and secure user experience)"

Annex H (informative) Contracting web design and auditing services

-----

Comment: User confidence is vital, and it does not matter what the
skill, knowledge, experience or ability level a user has, we must
develop web sites that are safe to use and do not create additional
risks to the user. Webpages and websites with security vulnerabilities
are not accessible unless the vulnerabilities are also validated for
conformance.

Proposed changes: In H.1.1 add " In regards to web security, OWASP a
globally recognized community has produced tools, specifications and
guidelines focusing on best coding practices, security code review,
Testing Guide, Code Review and Top 10 vulnerabilities (referenced by
PCI-DSS). All OWASP resources are free to use.", In H.1.3 add another
item "awareness of website security issues", in H.3.1 add another item
"Will security implications be included in the testing?" and in H.3.2
add another item "Does the supplier use the OWASP Application Security
Verification Standard (ASVS) to provide a level of confidence in the
security of the project"

Bibliography - Useful web contents

-----

Comment: OWASP has the most comprehensive resources available for
specifying, designing, developing, testing and operating web
applications. For example, the Top 10 project is referenced in the PCI
Data Security Standard.
<http://www.owasp.org/index.php/Category:OWASP_Top_Ten_Project>

Proposed change: Add to "Useful web contents", "Open Web Application
Security Project (OWASP) <http://www.owasp.org>"

### Draft Text version 2

0.2 Understanding accessible experiences

-----

Comment: Web sites are fast becoming something we cannot live without,
but it is insecure. User confidence is vital, and it does not matter
what the skill, knowledge, experience or ability level a user has, we
must develop web sites that are safe to use and do not create additional
risks to the user.

Proposed change: In the sentence "The goal of any web project should be
to create web experiences that are accessible, usable and enjoyable for
everyone." add the word "safe" so that it reads "The goal of any web
project should be to create web experiences that are accessible, usable,
safe and enjoyable for everyone." This would necessitate an additional
column in Table 1

Safe

-----

The user's privacy, data and computer systems are not compromised while
they accomplish their goals.

Examples

-----

No malicious code was downloaded while downloading the web content

-----

The user has confidence in the integrity of the information in the video

-----

The audio description and video are available when the user requires

-----

By changing browser settings or the type of user agent, the user should
not be at greater risk than other users

-----

<div style="font-color:red;">

5.1 Web technologies

-----

Comment: In the choice of technology, how it is implemented and
maintained, and how it interacts with the user, the servers and
third-parties should be understood so that the security risks, and hence
accessibility issues, are considered during the selection stage.

Proposed change: Add another bullet point "whether the technology could
introduce additional security vulnerabilities and how these would be
mitigated;"

</div>

<strike style="color:red;">5.3 The technology selection process

-----

\[I feel there should be an additional bullet point here relating to
security, but can't think of a suitable one just yet\]

Comment: ?

Proposed change: Add another bullet "??????" in "Ensuring your audience
will be able to do the following with your web content:" after
"understand it;"</strike>

6.3 User Agent Accessibility Guidelines (UAAG)

-----

Comment: While the website should be usable in popular browsers, this is
not sufficient for testing purposes. Developers/programmers needs to
realise that people will try and access the content using "non-browser"
tools to look for vulnerabilities and the website should be secure
enough to protect users and itself from such threats. This requires
testing beyond "popular browsers".

Proposed change: Add "Note 6 - The website must secure enough to protect
itself and its users from security vulnerabilities which may not be
apparent by limiting testing to 'a reasonable range of web browsers'.
OWASP has produced a detailed testing guide
<http://www.owasp.org/index.php/Category:OWASP_Testing_Project>"

<div style="color:red;">

8.2.3.3 Validation

-----

Comment: Security testing should also be undertaken at the same time.

Proposed change: Add "The Security of the website should be validated by
ensuring that vulnerabilities identified in the ~~compliance to~~OWASP
Top 10 are mitigated. A comprehensive testing methodology is published
by OWASP as 'OWASP Testing Guide'
<http://www.owasp.org/index.php/Category:OWASP_Testing_Project>"

8.2.3.4 Conformance inspection

-----

Comment: Undocumented or unwanted functionality can often lead to
security vulnerabilities. For a webpage to conform, every aspect must be
validated; this requires a full understanding of the webpage and how it
interacts with the user, data, servers, etc.

Proposed change: Add to the end of the first paragraphs "All ~~aspects~~
elements within the webpage must be inspected. Thus any undocumented
features, functions or security vulnerabilities must also undergo
validation testing.~~undertake a validation test~~. The web ~~page~~
site code should be reviewed to ensure no security vulnerabilities exist
that may hamper the usage and accessibility. OWASP provides a~~s~~ very
methodical approach to security code review that is available under
'OWASP Code Review Guide'
<http://www.owasp.org/index.php/Category:OWASP_Code_Review_Project>"

8.2.3.6 Expert review

-----

Comment: Security is an aspect of quality (see ISO 9126)

Proposed change: Add "Quality can not be achieved without ensuring
proper security. Security is a quality vector and should be taken into
consideration while conducting expert reviews. OWASP experts familiar
with methodologies can help review the application from security
standpoint and help ensure high quality."

Comment (DC): Are we going out on a limb here offering up free
"consultancy" services from "OWASP experts" ?

Annex F - F.1.2 Web developer

-----

Comment: Security is an aspect of quality (see ISO 9126). Content
~~cannot~~ may not be accessible if there are security vulnerabilities.

Proposed change: Add "It is also important for a web developer to learn
secure coding. This will help reduce the risk of security
vulnerabilities in the website and provide users with a better usability
and accessibility of the content. OWASP has defined best practices for
secure coding aided with code snippets and examples that can help
developers to learn the art of secure coding."

Annex G - G.2 Criteria for measuring success

-----

Comment: Without validated security, there is no way to ensure that
webpages conform to accessibility requirements.

Proposed change: Add as a new bullet point under a) "How well the risk
of getting compromised through a security vulnerability is mitigated?
(degree of risk vs. usability)" and as a new bullet point under b) "How
low is the threat of user’s computer becoming infected through malicious
code from the website? (Degree of confidence in the website for
efficient utilization)" and as a new bullet point under c) "Perceived
security (Peace of mind / trust / reliable and secure user experience)"

</div>

Annex H (informative) Contracting web design and auditing services

-----

Comment: User confidence is vital, and it does not matter what the
skill, knowledge, experience or ability level a user has, we must
develop web sites that are safe to use and do not create additional
risks to the user. Webpages and websites with security vulnerabilities
are not accessible unless the vulnerabilities are also validated for
conformance.

Proposed changes: <span style="color:red;">In H.1.1 add " In regards to
web security, OWASP a globally recognized community has produced tools,
specifications and guidelines focusing on best coding practices,
security code review, Testing Guide, Code Review and Top 10
vulnerabilities (considered as a de-facto list for most of the
compliances such as PCI-DSS, VISA etc). All ~~of~~ OWASP resources are
free to use.",</span> In H.1.3 add another item "awareness of website
security issues", in H.3.1 add another item "Will security implications
be included in the testing?" and in H.3.2 add another item "Does the
supplier use the OWASP Application Security Verification Standard (ASVS)
to provide a level of confidence in the security of the project"

Comment (DC): VISA compliance? Also is the ASVS release quality yet?

Bibliography - Useful web contents

-----

Comment: OWASP has the most comprehensive resources available for
specifying, designing, developing, testing and operating web
applications. For example, the Top 10 project is referenced in the PCI
Data Security Standard.
<http://www.owasp.org/index.php/Category:OWASP_Top_Ten_Project>

Proposed change: Add "Open Web Application Security Project (OWASP)
<http://www.owasp.org>"

### Draft Text version 1

*The format for providing feedback requires a comment and proposed
change. As feedback is provided PER SECTION, we cannot assume anyone
will read the feedback to other sections first i.e. each comment/change
must stand on its own merits.*

*We may also need some generic WHO ARE OWASP text.*

0.2 Understanding accessible experiences

-----

Comment: Web sites are fast becoming something we cannot live without,
but it is insecure. User confidence is vital, and it does not matter
what the skill, knowledge, experience or ability level a user has, we
must develop web sites that are safe to use and do not create additional
risks to the user.

Proposed change: In the sentence "The goal of any web project should be
to create web experiences that are accessible, usable and enjoyable for
everyone." add the word "safe" so that it reads "The goal of any web
project should be to create web experiences that are accessible, usable,
safe and enjoyable for everyone." This would necessitate an additional
column in Table 1

Safe

-----

The user's privacy, data and computer systems are not compromised while
they accomplish their goals.

Examples

-----

No malicious code was downloaded while downloading the web content

-----

The user has confidence in the integrity of the information in the video

-----

The audio description and video are available when the user requires

-----

By changing browser settings or the type of user agent, the user should
not be at greater risk than other users

-----

5.3 The technology selection process

-----

\[I feel there should be an additional bullet point here relating to
security, but can't think of a suitable one just yet\]

Comment: ?

Proposed change: Add another bullet "??????" in "Ensuring your audience
will be able to do the following with your web content:" after
"understand it;"

6.3 User Agent Accessibility Guidelines (UAAG)

-----

Comment: While the website should be usable in popular browsers, this is
not sufficient for testing purposes. Developers/programmers needs to
realise that people will try and access the content using "non-browser"
tools to look for vulnerabilities and the website should be secure
enough to protect users and itself from such threats. This requires
testing beyond "popular browsers".

Proposed change: Add "Note 6 - The website must secure enough to protect
itself and its users from security vulnerabilities which may not be
apparent by limiting testing to 'a reasonable range of web browsers'.
OWASP has produced a detailed testing guide
<http://www.owasp.org/index.php/Category:OWASP_Testing_Project>"

Annex H (informative) Contracting web design and auditing services

-----

Comment: \[as 0.2?\]

Proposed changes: In H.1.3 add another item "awareness of website
security issues", in H.3.1 add another item "Will security implications
be included in the testing?" and in H.3.2 add another item "Does the
supplier use the OWASP Application Security Verification Standard to
provide a level of confidence in the security of the project"

Bibliography - Useful web contents

-----

Comment: OWASP has the most comprehensive resources available for
specifying, designing, developing, testing and operating web
applications. For example, the Top 10 project is referenced in the PCI
Data Security Standard.
<http://www.owasp.org/index.php/Category:OWASP_Top_Ten_Project>

Proposed change: Add "Open Web Application Security Project (OWASP)
<http://www.owasp.org>"

Return to [Global Industry
Committee](Global_Industry_Committee "wikilink")