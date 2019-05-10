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

## Result

[BS 10012:2009 Data Protection - Specification for a Personal
Information Management
System](http://www.bsigroup.com/en/Shop/Publication-Detail/?pid=000000000030175849)
was published in May 2009.

The suggestions in our response are not directly included, although many
of the sections OWASP commented on have been reworded.

## Submission Response

*Latest first*

### Final version

\[This response is submitted on behalf of the Open Web Application
Security Project (OWASP)\]

4.3 Training and awareness

-----

Comment: Information security organizations have a wide body of
knowledge that can help in the protection of personal information and
have well-established channels for the dissemination of new threats.

Proposed change: Add reference to "information security organizations"
in the sentence "The organization shall also ensure that this member of
staff works with relevant external trade organizations and data
protection organizations in order to remain informed about issues
related to the management of personal information." so that it reads
"The organization shall also ensure that this member of staff works with
relevant external trade organizations, INFORMATION SECURITY
ORGANIZATIONS and data protection organizations in order to remain
informed about issues related to the management of personal
information.".

4.4 Risk assessment

-----

Comment: The risk assessment should not be limited to the
planned/existing processing. Threat risk modelling looks at mis-use too
and should be used to identify threats and vulnerabilities in the
systems used to collect, store, use, transmit personal information. See
<http://www.owasp.org/index.php/Threat_Risk_Modeling> for a further
explanation in the context of a web application.

Proposed change: In the first paragraph, add a new sentence "The
organization shall use threat risk modelling to expose additional
threats and vulnerabilities.".

4.7.2 On-line privacy statements

-----

Comment: Privacy statements on the Internet should not be limited solely
to websites.

Proposed change: Change the text "where personal information is
collected over the Internet via a website, an on-line privacy statement
is included on the website." to "where personal information is collected
over the Internet (E.G. WEBSITE, INSTANT MESSAGING, WIDGET, MOBILE
APPLICATION, EMAIL, ETC) OR OTHER DIGITAL CHANNEL, an on-line privacy
statement is included."

4.7.3 Record of FPNs and statements

-----

Comment: The retention of fair processing notices (FPNs) and online
privacy notices for as long as personal information to which they relate
is retained will require knowing exactly where the data are at all
times, so that it can be destroyed securely when it is no longer
required.

Proposed change: Add a sentence at the end of this paragraph "The PIMS
must address how personal information will be monitored throughout its
lifecycle, from collection to secure destruction, including all
processes, systems, applications, media (electronic or otherwise) and
other organisations where the information may reside, pass through or be
processed by."

4.10 Accuracy

-----

Comment: The procedures suggested are somewhat reactive. Organisations
can also review their own data to identify inaccuracies and make
corrections e.g. de-duplication, removal of redundant data, address
validation, re-checking with the subject, etc.

Proposed change: In the fifth paragraph ("The PIMS shall incorporate
procedures for:...") add another item "c) periodic checking of data
integrity and correction of identifiable inaccuracies".

4.11 Retention and disposal

-----

Comment: If personal information is transmitted between systems or
stored in multiple locations, all instances of the data must be removed
securely at the disposal point. For example, data may initially have
been collected via a web application and could exist on web servers, on
database servers, on proxies, and in paper reports and file exports
generated from the web application as well as any internal or
third-party systems where the data is transferred to.

Proposed change: In the fourth paragraph("The PIMS shall incorporate or
reference disposal procedures which are managed:...") add another item
"4. cover all systems, applications, media and other locations where the
personal information may have existed".

4.13.1 Security controls

-----

Comment: Compliance with BS ISO 27001 is one consideration. But many
business processes rely on software, and much of this software is not
secure enough to protect personal information.

Proposed change: Add another note "Organizations developing or using
software (e.g. websites, CRM systems, web applications, widgets) to
process personal information may wish to consider using a maturity model
to assess their software development processes against industry "best
practice", and create a plan to improve. A well-developed example is the
SAMM (Software Assurance Maturity Model)- see <http://www.opensamm.org/>
Organisations might also consider choosing software development
frameworks and methods that have been heavily analysed and carefully
designed to improve security such as the OWASP Enterprise Security API –
<http://www.owasp.org/index.php/ESAPI> available for a range of common
web programming languages.".

4.13.2 Storage and handling

-----

Comment: Online storage and handling are also particularly at risk from
external threats.

Proposed change: Add another note "Any online systems that store or
handle personal information must also be examined carefully. The Open
Web Application Security Project (OWASP) provides open access to many
guides and tools to help with the development, testing, deployment and
verification of application security - <http://www.owasp.org/>".

4.13.5 Security assessments

-----

Comment: Web applications are often built insecurely; many of today's
business processes are being enabled over the web and this is exposing
personal information to additional threats. There are many problems
common to other software systems, but web applications also have
particular issues. There is currently only one standard available to
specifically establish a level of confidence in the security of web
applications.

Proposed change: Add a note "The OWASP Application Security Verification
Standard (ASVS) is an open standard that defines ranges in coverage and
levels of rigor that can be used to perform application security
verifications - <http://www.owasp.org/index.php/ASVS>".

4.13.6 Notification of security incidents

-----

Comment: Organizations should be pro-actively looking for security
incidents, not just reacting when an incident is brought to their
attention.

Proposed change: Add a new item to the first paragraph ("The PIMS shall
incorporate procedures:..."), "e) to identify actual, unusual and
potentially malicious behaviour".

Bibliography

-----

Comment: OWASP builds documents, tools, teaching environments,
guidelines, checklists, and other materials to help organisations
improve their capability to produce secure code. All of the OWASP tools,
documents, forums, and chapters are free and open to anyone interested
in improving application security. The ICO currently has a draft Privacy
Notices Code of Practice consultation open until 3 April at
<http://www.ico.gov.uk/about_us/consultations/our_consultations.aspx>

Proposed change: Add to bibliography "The Open Web Application Security
Project (OWASP) at <http://www.owasp.org>".

Add to bibliography "Privacy Notices Code of Practice, ICO at \[tbc\]"

### Draft Text version 2

*No changes*

### Draft Text version 1

*The format for providing feedback requires a comment and proposed
change. As feedback is provided PER SECTION, we cannot assume anyone
will read the feedback to other sections first i.e. each comment/change
must stand on its own merit.*

4.3 Training and awareness

-----

Comment: Information security organizations have a wide body of
knowledge that can help in the protection of personal information and
have well-established channels for the dissemination of new threats.

Proposed change: Add reference to "information security organizations"
in the sentence "The organization shall also ensure that this member of
staff works with relevant external trade organizations and data
protection organizations in order to remain informed about issues
related to the management of personal information." so that it reads
"The organization shall also ensure that this member of staff works with
relevant external trade organizations, INFORMATION SECURITY
ORGANIZATIONS and data protection organizations in order to remain
informed about issues related to the management of personal
information.".

4.3 Risk assessment

-----

Comment: The risk assessment should not be limited to the
planned/existing processing. Threat risk modelling looks at mis-use too
and should be used to identify threats and vulnerabilities in the
systems used to collect, store, use, transmit personal information. See
<http://www.owasp.org/index.php/Threat_Risk_Modeling> for a further
explanation in the context of a web application.

Proposed change: In the first paragraph, add a new sentence "The
organization shall use threat risk modelling to expose additional
threats and vulnerabilities.".

4.7.2 On-line privacy statements

-----

Comment: Privacy statements on the Internet should not be limited solely
to websites.

Proposed change: Change the text "where personal information is
collected over the Internet via a website, an on-line privacy statement
is included on the website." to "where personal information is collected
over the Internet (E.G. WEBSITE, MOBILE APPLICATION, EMAIL, ETC) OR
OTHER DIGITAL CHANNEL, an on-line privacy statement is included."

4.7.3 Record of FPNs and statements

-----

Comment: The retention of fair processing notices (FPNs) and online
privacy notices for as long as personal information to which they relate
is retained will require knowing exactly where the data is at all times,
so that it can be destroyed securely when it is no longer required.

Proposed change: Add a sentence at the end of this paragraph "The PIMS
must address how personal information will be monitored throughout its
lifecycle, from collection to secure destruction, including all
processes, systems, applications, media (electronic or otherwise) and
other organisations where the information may reside or pass through."

4.10 Accuracy

-----

Comment: The procedures suggested are somewhat reactive. Organisations
can also review their own data to identify inaccuracies and make
corrections e.g. de-duplication, removal of redundant data, address
validation, etc.

Proposed change: In the fifth paragraph ("The PIMS shall incorporate
procedures for:...") add another item "c) periodic checking of data
integrity and correction of identifiable inaccuracies".

4.11 Retention and disposal

-----

Comment: If personal information is transmitted between systems or
stored in multiple locations, all instances of the data must be removed
securely at the disposal point. For example, data may initially have
been collected via a web application and could exist on web servers, on
database servers, on proxies, and in paper reports and file exports
generated from the web application as well as any internal or
third-party systems where the data is transferred to.

Proposed change: In the fourth paragraph("The PIMS shall incorporate or
reference disposal procedures which are managed:...") add another item
"4. cover all systems, applications, media and other locations where the
personal information may have existed".

4.13.1 Security controls

-----

Comment: Compliance with BS ISO 27001 is an important consideration. But
many business processes are underpinned by software, and much of this
software is not secure enough to protect personal information.

Proposed change: Add another note "Organizations developing or using
software (e.g. CRM systems, web applications) to process personal
information may wish to consider using a maturity model to assess their
software development processes against industry "best practice", and
create a plan to improve. A well-developed example is the OpenSAMM
(Software Assurance Maturity Model)- see <http://www.opensamm.org/>
Organisations might also consider choosing development frameworks and
methods that have been heavily analysed and carefully designed to
improve security such as the OWASP Enterprise Security API –
<http://www.owasp.org/index.php/ESAPI> available for a range of common
web programming languages.".

4.13.2 Storage and handling

-----

Comment: Online storage and handling are also particularly at risk from
external threats.

Proposed change: Add another note "Any online systems that store or
handle personal information must also be examined carefully. The Open
Web Application Security Project (OWASP) provides open access to many
guides and tools to help with the development, testing, deployment and
verification of application security - <http://www.owasp.org/>".

4.13.5 Security assessments

-----

Comment: Web applications are often built insecurely; many of today's
business processes are being enabled over the web and this is exposing
personal information to additional threats. There are many problems
common to other software systems, but web applications also have
particular issues. There is currently only one standard available to
specifically establish a level of confidence in the security of web
applications.

Proposed change: Add a note "The OWASP Application Security Verification
Standard (ASVS) is an open standard that defines ranges in coverage and
levels of rigor that can be used to perform application security
verifications - <http://www.owasp.org/index.php/ASVS>".

4.13.6 Notification of security incidents

-----

Comment: Organizations should be pro-actively looking for security
incidents, not just reacting when an incident is brought to their
attention.

Proposed change: Add a new item to the first paragraph ("The PIMS shall
incorporate procedures:..."), "e) to identify actual, unusual and
potentially malicious behaviour".

Bibliography

-----

Comment: OWASP builds documents, tools, teaching environments,
guidelines, checklists, and other materials to help organisations
improve their capability to produce secure code. All of the OWASP tools,
documents, forums, and chapters are free and open to anyone interested
in improving application security.

Proposed change: Add to bibliography "The Open Web Application Security
Project (OWASP) at <http://www.owasp.org>".

Return to [Global Industry
Committee](Global_Industry_Committee "wikilink")