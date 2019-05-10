**XML Security Gateway Evaluation Criteria**

`  Version 0.2 (June 14, 2007)`

`  OWASP (http://www.owasp.org)`
`  Content is available under a Creative Commons 2.5 License `

`  Table of Contents`

`  Introduction`

`       Contributors`
`       Contact`

*' Categories*'

`       Section 1 - Authentication`
`       Section 2 - Authorization`
`       Section 3 - Audit Logging`
`       Section 4 - Deployment Architecture`
`       Section 5 - Content Validation`
`       Section 6 - Management & Metrics`
`       Section 7 - Transformation`
`       Section 8 - Tools`

`  A. License`

**Introduction**

The OWASP XML Security Gateway Evaluation Criteria Project (XSGEC)
defines an open standard for evaluating XML Security Gateways, such as
those used to protect and provide security services for Web services
applications. This criteria provides the OWASP community a set of
standard evaluation guidance to assess the functionality and quality of
XML Security Gateways. The main drivers for this project is to add
clarity to the process of assessing the XML Security Gateway strengths
and weaknesses, and enlightening the community as to the utility of XML
Security Gateways to deliver a number of valuable security services for
distributed systems.

The XML Security Gateway Evaluation Criteria (XSGEC) Project's Guiding
Principles were created in order to express the intentions of its
contributors when designing the criteria.

  - Create evaluation criteria supporting a transparent, level playing
    field for XML Security Gateway solutions to define their solution's
    key value proposition

<!-- end list -->

  - Where practical, attempt to standardize nomenclature and metrics

<!-- end list -->

  - Educate the community on the design considerations for XML security

XML Security Gateways (XSG) may serve as both service providers and
service requesters, so the evaluation criteria seeks to assess the
tool's capabilities in delivering security and assurance services to
inbound and outbound service requests.

**Contributors**

The following people have contributed their time and expertise to the
project:

  - Sebastien Deleersnyder, Ascure
  - Muthu Meyyappan, United Healthcare
  - James McGovern, The Hartford
  - Mark O'Neill, Vordel
  - Gunnar Peterson, Arctec Group
  - Ivan Ristic, Breach Security
  - Brian Roddy, Cisco
  - Philippe Bogaerts, NetAppSec
  - Paul Lesov, Wells Fargo

**Contact**

`  Participation in the XML Security Gateway Evaluation Criteria`
`  project is open to all. If you wish to comment on the evaluation`
`  criteria or join the team mailing list please contact Gunnar Peterson via`
`  email gunnar@arctecgroup.net.`

**Categories**

**Section 1 - Authentication** This section describes the authentication
support at the service level and message level for inbound and outbound
communication to the XSG.

1.1 Inbound authentication How does the XSG perform authentication for
inbound services requests?

  - Mutual SSL
  - HTTP Basic Authentication
  - HTTP Digest Authentication
  - WS-Security Username Token Authentication
  - WS-Security X.509 Certificate Based Authentication
  - WS-Security: Kerberos Token
  - SAML Authentication assertion
  - Validation against Active Directory
  - Dereference Active Directory Federation Services

1.2 Outbound authentication What capabilities does the XSG have to
perform outbound assertion for authenticating the XSG's request to the
service? What token types are supported for insertion?

  - Mutual SSL
  - HTTP Basic Authentication
  - HTTP Digest Authentication
  - WS-Security Username Token
  - WS-Security X.509 Certificate
  - WS-Security: Kerberos Token
  - SAML Authentication assertion
  - WS-Federation assertion

1.3 Proxy Functionality What capabilities does the XSG have mapping
attributes on behalf of service requesters and service providers?

Consider the following scenario

Service Requester --\> Guard 1 --\> Guard 2 --\> Resources/Service
Provider

Using the Secure Proxy patterns defined by Blakley and Heath
(http://www.opengroup.org/bookstore/catalog/g031.htm) define which proxy
functions (trusted proxy, delegate, authz proxy, and so on) the XSG
supports and how they are implemented.

<table cellspacing="2" cellpadding="2" class="t1" border="1">

<tr>

<td valign="middle" class="td1">



</td>

<td valign="middle" class="td1">

passwd to guard1

</td>

<td valign="middle" class="td1">

userid to guard2

</td>

<td valign="middle" class="td1">

guard2 authn

</td>

<td valign="middle" class="td1">

guard2 authz

</td>

<td valign="middle" class="td1">

sso

</td>

<td valign="middle" class="td1">

delegation protocol

</td>

</tr>

<tr>

<td valign="middle" class="td1">

ideal

</td>

<td valign="middle" class="td1">

no

</td>

<td valign="middle" class="td1">

yes

</td>

<td valign="middle" class="td1">

user

</td>

<td valign="middle" class="td1">

user

</td>

<td valign="middle" class="td1">

yes

</td>

<td valign="middle" class="td1">

no

</td>

</tr>

<tr>

<td valign="middle" class="td1">

trusted proxy

</td>

<td valign="middle" class="td1">

no

</td>

<td valign="middle" class="td1">

no

</td>

<td valign="middle" class="td1">

guard1

</td>

<td valign="middle" class="td1">

guard1

</td>

<td valign="middle" class="td1">

yes

</td>

<td valign="middle" class="td1">

no

</td>

</tr>

<tr>

<td valign="middle" class="td1">

authn impersonation

</td>

<td valign="middle" class="td1">

yes

</td>

<td valign="middle" class="td1">

yes

</td>

<td valign="middle" class="td1">

user

</td>

<td valign="middle" class="td1">

user

</td>

<td valign="middle" class="td1">

yes

</td>

<td valign="middle" class="td1">

no

</td>

</tr>

<tr>

<td valign="middle" class="td1">

id-assert impersonation

</td>

<td valign="middle" class="td1">

no

</td>

<td valign="middle" class="td1">

yes

</td>

<td valign="middle" class="td1">

no

</td>

<td valign="middle" class="td1">

user

</td>

<td valign="middle" class="td1">

yes

</td>

<td valign="middle" class="td1">

no

</td>

</tr>

<tr>

<td valign="middle" class="td1">

delegate

</td>

<td valign="middle" class="td1">

no

</td>

<td valign="middle" class="td1">

yes

</td>

<td valign="middle" class="td1">

user

</td>

<td valign="middle" class="td1">

user

</td>

<td valign="middle" class="td1">

yes

</td>

<td valign="middle" class="td1">

yes

</td>

</tr>

<tr>

<td valign="middle" class="td1">

authz proxy

</td>

<td valign="middle" class="td1">

no

</td>

<td valign="middle" class="td1">

no

</td>

<td valign="middle" class="td1">

no

</td>

<td valign="middle" class="td1">

no

</td>

<td valign="middle" class="td1">

yes

</td>

<td valign="middle" class="td1">

no

</td>

</tr>

<tr>

<td valign="middle" class="td1">

login tunnel

</td>

<td valign="middle" class="td1">

no

</td>

<td valign="middle" class="td1">

yes

</td>

<td valign="middle" class="td1">

user

</td>

<td valign="middle" class="td1">

user

</td>

<td valign="middle" class="td1">

no

</td>

<td valign="middle" class="td1">

no

</td>

</tr>

</table>

What tokens and protocols are supported for these scenarios? How is
identity and attribute mapping handled?

**Section 2 - Authorization**

2.1 Describe XSG support for standards-based authorization:

  - XACML
  - SAML
  - LDAP

2.2 Describe how Policy Enforcement Point (PEP) and Policy Decision
Point (PDP) implement authorization workflow rules.

2.3 Describe how out bound messages are marked as authorized so that
service providers and service consumers can verify that policy has been
applied to the message

**Section 3 - Audit Logging**

3.1 Describe the audit logging input and output options

3.2 Describe log analysis tools

3.3 Describe security event notification options

3.4 Where and how is logging integrated into XSG?

3.4.1 How are the logs secured? Describe support for

  - Access control model for logs
  - Log sanitization
  - Log Signing (XML Signature)
  - Remoting of log information to log management platform such as
    LogLogic

3.5 Does the XSG support correlation for end to end transaction logging?
How is this implemented?

**Section 4 - Deployment Architecture**

4.1 Describe the physical deployment for the XSG:

  - Standalone hardware device
  - Software only
  - Both

4.2 Describe the options for fail over, scalability and high
availability

4.3 Describe integration with messaging systems, such as JMS and MQ
Series

**Section 5 - Content Validation**

5.1 Describe security model support for positive (whitelist) and
negative (blacklist) security models

5.1.1 Positive security model (default deny) define whitelist for all
allowed requests. Does the XSG support learning mode? How is the
whitelist configured?

5.1.2 Negative security model (default allow) define blacklist for
unallowed requests. Is the blacklist signature based or rules based?

5.2 Describe schema validation support

5.3 Describe content validation, including injection attack, external
entity attack, buffer overflow prevention

5.4 Describe message and request security analysis

5.5 Describe SOAP attachment analysis

**Section 6 - Management & Metrics**

6.1 Describe the available management tools for the XSG

6.2 Describe the available system metrics and reporting available
including diagnostics, alerts, and warnings, e.g. SNMP, email, Syslog

6.3 How are upgrades accomplished for hardware, OS, and software?

6.4 Describe how policy is managed, versioned, and stored.

**Section 7 - Transformation**

7.1 Describe how the XSG supports XML transformation, e.g. XPath, XQuery

**Section 8 - Tools**

8.1 Describe any security testing tools that work with the XSG

8.2 Describe any development tools that work with the XSG

**Section 9 - Performance**

9.1 Define parameters for performance metrics

**A. Licence**

This work is licensed under the Creative Commons Attribution License. To
view a copy of this license, visit
<http://creativecommons.org/licenses/by/2.5/> or send a letter to:
Creative Commons, 559 Nathan Abbott Way, Stanford, California 94305,
USA.