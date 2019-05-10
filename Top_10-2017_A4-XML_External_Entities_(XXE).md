`   <td colspan=2 ``>`

Attackers can exploit vulnerable XML processors if they can upload XML
or include hostile content in an XML document, exploiting vulnerable
code, dependencies or integrations.

</td>

`   <td colspan=2  ``>`

`By default, many older XML processors allow specification of an external entity, a URI that is dereferenced and evaluated during XML processing.`
<u>[`SAST`](Source_Code_Analysis_Tools "wikilink")</u>` tools can discover this issue by inspecting dependencies and configuration. `<u>[`DAST`](:Category:Vulnerability_Scanning_Tools "wikilink")</u>` tools require additional manual steps to detect and exploit this issue. Manual testers need to be trained in how to test for XXE, as it not commonly tested as of 2017. `

</td>

`   <td colspan=2  ``>`

`These flaws can be used to extract data, execute a remote request from the server, scan internal systems, perform a denial-of-service attack, as well as execute other attacks.`
`The business impact depends on the protection needs of all affected application and data.`

</td>

Applications and in particular XML-based web services or downstream
integrations might be vulnerable to attack if:

  - The application accepts XML directly or XML uploads, especially from
    untrusted sources, or inserts untrusted data into XML documents,
    which is then parsed by an XML processor.
  - Any of the XML processors in the application or SOAP based web
    services has <u>[document type definitions
    (DTDs)](https://en.wikipedia.org/wiki/Document_type_definition)</u>
    enabled. As the exact mechanism for disabling DTD processing varies
    by processor, it is good practice to consult a reference such as the
    <u>[OWASP Cheat Sheet 'XXE
    Prevention'](XML_External_Entity_\(XXE\)_Prevention_Cheat_Sheet "wikilink")</u>.
  - If the application uses SAML for identity processing within
    federated security or single sign on (SSO) purposes. SAML uses XML
    for identity assertions, and may be vulnerable.
  - If the application uses SOAP prior to version 1.2, it is likely
    susceptible to XXE attacks if XML entities are being passed to the
    SOAP framework.
  - Being vulnerable to XXE attacks likely means that the application is
    vulnerable to denial of service attacks including the Billion Laughs
    attack

Developer training is essential to identify and mitigate XXE. Besides
that, preventing XXE requires:

  - Whenever possible, use less complex data formats such as JSON, and
    avoiding serialization of sensitive data.
  - Patch or upgrade all XML processors and libraries in use by the
    application or on the underlying operating system. Use dependency
    checkers. Update SOAP to SOAP 1.2 or higher.
  - Disable XML external entity and DTD processing in all XML parsers in
    the application, as per the <u>[OWASP Cheat Sheet 'XXE
    Prevention'](XML_External_Entity_\(XXE\)_Prevention_Cheat_Sheet "wikilink")</u>.
  - Implement positive ("whitelisting") server-side input validation,
    filtering, or sanitization to prevent hostile data within XML
    documents, headers, or nodes.
  - Verify that XML or XSL file upload functionality validates incoming
    XML using XSD validation or similar.
  - <u>[SAST](Source_Code_Analysis_Tools "wikilink")</u> tools can help
    detect XXE in source code, although manual code review is the best
    alternative in large, complex applications with many integrations.

If these controls are not possible, consider using virtual patching, API
security gateways, or Web Application Firewalls (WAFs) to detect,
monitor, and block XXE attacks.

Numerous public XXE issues have been discovered, including attacking
embedded devices. XXE occurs in a lot of unexpected places, including
deeply nested dependencies. The easiest way is to upload a malicious XML
file, if accepted:

<b>Scenario \#1</b>: The attacker attempts to extract data from the
server: <b><span style="color:red;"> \<?xml version="1.0"
encoding="ISO-8859-1"?\>

  -
    \<\!DOCTYPE foo \[
    \<\!ELEMENT foo ANY \>
    \<\!ENTITY xxe SYSTEM "file:///etc/passwd" \>\]\>
    \<foo\>\&xxe;\</foo\>

</span></b>

<b>Scenario \#2</b>: An attacker probes the server's private network by
changing the above ENTITY line to: <b><span style="color:red;">

  -
    \<\!ENTITY xxe SYSTEM "https://192.168.1.1/private" \>\]\>

</span></b>

<b>Scenario \#3</b>: An attacker attempts a denial-of-service attack by
including a potentially endless file: <b><span style="color:red;">

  -
    \<\!ENTITY xxe SYSTEM "file:///dev/random" \>\]\>

</span></b>

  - <u>[OWASP Application Security Verification
    Standard](:Category:OWASP_Application_Security_Verification_Standard_Project#tab=Home "wikilink")</u>
  - <u>[OWASP Testing Guide: Testing for XML
    Injection](Testing_for_XML_Injection_\(OTG-INPVAL-008\) "wikilink")</u>
  - <u>[OWASP XXE
    Vulnerability](XML_External_Entity_\(XXE\)_Processing "wikilink")</u>
  - <u>[OWASP Cheat Sheet: XXE
    Prevention](XML_External_Entity_\(XXE\)_Prevention_Cheat_Sheet "wikilink")</u>
  - <u>[OWASP Cheat Sheet: XML
    Security](XML_Security_Cheat_Sheet "wikilink")</u>

<!-- end list -->

  - <u>[CWE-611: Improper Restriction of
    XXE](https://cwe.mitre.org/data/definitions/611.html)</u>
  - <u>[Billion Laughs
    Attack](https://en.wikipedia.org/wiki/Billion_laughs_attack)</u>
  - <u>[SAML Security XML External Entity
    Attack](https://secretsofappsecurity.blogspot.tw/2017/01/saml-security-xml-external-entity-attack.html)</u>
  - <u>[Detecting and exploiting XXE in SAML
    Interfaces](https://web-in-security.blogspot.tw/2014/11/detecting-and-exploiting-xxe-in-saml.html)</u>