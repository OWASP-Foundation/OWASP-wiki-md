''' 4.10 Web Services Testing '''

-----

SOA (Service Orientated Architecture)/Web services applications are
up-and-coming systems which are enabling businesses to interoperate and
are growing at an unprecedented rate. Webservice "clients" are generally
not user web front-ends but other backend servers. Webservices are
exposed to the net like any other service but can be used on HTTP, FTP,
SMTP, MQ among other transport protocols. The Web Services Framework
utilizes the HTTP protocol (as standard Web Application) in conjunction
with XML, SOAP, WSDL and UDDI technologies:

  - The "Web Services Description Language" (WSDL) is used to describe
    the interfaces of a service.
  - The "Simple Object Access Protocol" (SOAP) provides the means for
    communication between Web Services and Client Applications with XML
    and HTTP.
  - "Universal Description, Discovery and Integration" (UDDI) is used to
    register and publish Web Services and their characteristics so that
    they can be found from potential clients.

The vulnerabilities in web services are similar to other
vulnerabilities, such as SQL injection, information disclosure, and
leakage, but web services also have unique XML/parser related
vulnerabilities, which are discussed here as well.

The following articles describe the web services testing:

[4.10.1 WS Information Gathering
(OWASP-WS-001)](Testing:_WS_Information_Gathering_\(OWASP-WS-001\) "wikilink")
[4.10.2 Testing WSDL
(OWASP-WS-002)](Testing_WSDL_\(OWASP-WS-002\) "wikilink")
[4.10.3 XML Structural Testing
(OWASP-WS-003)](Testing_for_XML_Structural_\(OWASP-WS-003\) "wikilink")
[4.10.4 XML Content-level Testing
(OWASP-WS-004)](Testing_for_XML_Content-Level_\(OWASP-WS-004\) "wikilink")
[4.10.5 HTTP GET parameters/REST Testing
(OWASP-WS-005)](Testing_for_WS_HTTP_GET_parameters/REST_attacks_\(OWASP-WS-005\) "wikilink")
[4.10.6 Naughty SOAP attachments
(OWASP-WS-006)](Testing_for_Naughty_SOAP_Attachments_\(OWASP-WS-006\) "wikilink")
[4.10.7 Replay Testing
(OWASP-WS-007)](Testing_for_WS_Replay_\(OWASP-WS-007\) "wikilink")