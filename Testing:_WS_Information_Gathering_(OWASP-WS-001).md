## Brief Summary

The first step to perform a Web Service Test is to determine the WS
entry points and the communication schema: this is described in the WSDL
associated with the Web Service.

## Black Box Testing and example

**Zero Knowledge**
Normally you will have a WSDL path to access the Web Service, but if you
have zero knowledge about it, you will have to use UDDI to find a
specific service. Web Services have three critical building blocks –
UDDI, WSDL and SOAP. There is a third intermediate player facilitating
communication between the consumer and supplier, referred to as
Universal Business Registry (UBR). There are several ways to find our
WSDL: the easiest one is to make a search Query in public search engine.
For example, if you have to assess an example.com public WS, on
google.com you can type:

`inurl:wsdl site:example.com`

and you will find all the public Example WSDL. Net Square wsPawn is a
useful tool that acts as Web Services Consumer and makes a query to the
UBR and looks for services as per requirements. Then UBR supplies the
list of available services. The Web Services Consumer chooses one or
more available services. Next, Web Services Consumer requests an access
point or end point for these services. UBR supplies this information.
From this moment, Web Services Consumer approaches the Web Services
Supplier’s Host/IP address (WSDL) and starts accessing service.
**WSDL endpoints**
When a tester accesses the WSDL, he can determine an access point and
available interfaces for web services. These interfaces or methods take
inputs using SOAP over HTTP/HTTPS. If these inputs are not defined well
at the source code level, they can be compromised and exploited. For
example given this WSDL Endpoint:

<http://www.example.com/ws/FindIP.asmx?WSDL>

you can obtain the following description of the Web Services:

    <?xml version="1.0" encoding="utf-8"?>
    <wsdl:definitions xmlns:http="http://schemas.xmlsoap.org/wsdl/http/" xmlns:soap="http://schemas.xmlsoap.org/wsdl/soap/" xmlns:s="http://www.w3.org/2001/XMLSchema" xmlns:soapenc="http://schemas.xmlsoap.org/soap/encoding/" xmlns:tns="http://example.com/webservices/" xmlns:tm="http://microsoft.com/wsdl/mime/textMatching/" xmlns:mime="http://schemas.xmlsoap.org/wsdl/mime/" targetNamespace="http://example.com/webservices/" xmlns:wsdl="http://schemas.xmlsoap.org/wsdl/">
      <wsdl:types>
        <s:schema elementFormDefault="qualified" targetNamespace="http://example.com/webservices/">
          <s:element name="GetURLIP">
            <s:complexType>
              <s:sequence>
                <s:element minOccurs="0" maxOccurs="1" name="EnterURL" type="s:string" />
              </s:sequence>
            </s:complexType>
          </s:element>
          <s:element name="GetURLIPResponse">
            <s:complexType>
              <s:sequence>
                <s:element minOccurs="0" maxOccurs="1" name="GetURLIPResult" type="s:string" />
              </s:sequence>
            </s:complexType>
          </s:element>
          <s:element name="string" nillable="true" type="s:string" />
        </s:schema>
      </wsdl:types>
      <wsdl:message name="GetURLIPSoapIn">
        <wsdl:part name="parameters" element="tns:GetURLIP" />
      </wsdl:message>
      <wsdl:message name="GetURLIPSoapOut">
        <wsdl:part name="parameters" element="tns:GetURLIPResponse" />
      </wsdl:message>
      <wsdl:message name="GetURLIPHttpGetIn">
        <wsdl:part name="EnterURL" type="s:string" />
    ……
      </wsdl:service>
    </wsdl:definitions>

This WS simply receives in input a logical name (EnterURL) and gives in
output the relative IP Address. So we have GetURLIP as method for the WS
and EnterURL (string) as input. In that manner we have identified the WS
entry point and we are ready to test it.

**Web Services Discovery**
Web Services consumer needs a simple and standardized way to find Web
Services available from remote servers. There are two ways to discover a
Web Service, DISCO and UDDI.
The Web Service Discovery (DISCO) is one way that we can discover the
URL's WSDL descriptor and other XML documents, like Schema Definition
Document (.xsd).
For instance, with an HTTP query to a Web server:
<http://myexample.com/myexampleService.asmx?DISCO>

we obtain the following DISCO descriptor:

    <?xml version="1.0" encoding="utf-8"?>
    <discovery xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" ns="http://schemas.xmlsoap.org/disco/">
      <contractRef ref="http://myexample.com/MyexampleService.asmx?wsdl" docRef="http://myexample.com/myexample.asmx" ns="http://schemas.xmlsoap.org/disco/scl/" />
      <soap address="http://myexample.com/MyexampleService.asmx" xmlns:q1="http://myexample.com/terraserver/" binding="q1:myexampleServiceSoap" ns="http://schemas.xmlsoap.org/disco/soap/" />
    </discovery>


We can see in the above XML document we have a reference for a WSDL
document, where we can obtain a description of Web Services available
from remote Web Server.

DISCO is a Microsoft technology, UDDI (Universal Description, Discovery
and Integration) is an OASIS standard .

**WS Well Known Naming**
Common Web Services platforms have a naming convention for offering a
WSDL documents: This naming convention can be used to retrieve WSDL via
URIs probing or through queries to web search server.

Some URLs that we can use are, for example:

<http://><webservice-host>`:`<port>`/`<servicename>
<http://><webservice-host>`:`<port>`/`<servicename>`.wsdl`
<http://><webservice-host>`:`<port>`/`<servicename>`?wsdl`
<http://><webservice-host>`:`<port>`/`<servicename>`.aspx?wsdl `

`instead of .aspx extension we can also use .ascx, .asmx, .ashx extensions `

`Same thing with ?disco instead of ?wsdl`

<http://><webservice-host>`:`<port>`/<servicename.dll>?wsdl`
<http://><webservice-host>`:`<port>`/<servicename.exe>?wsdl `
<http://><webservice-host>`:`<port>`/<servicename.php>?wsdl`
<http://><webservice-host>`:`<port>`/<servicename.pl>?wsdl`

For Apache Axis we can try:

<http://><webservice-host>`:`<port>`/axis/services/`<servicename>`?wsdl`
<http://><webservice-host>`:`<port>`/axis/services/`<service-name>



**Search for public Web Services**
The seekda Web Services Search Engine can help to find a public Web
Services with related descriptions. To find Web Services just type the
keyword into seekda Web Services Search Engine. We can also browse by
several other criteria such as Tag Cloud, Services by Countries, Most
Used Services. <http://seekda.com>
![Image:seekda.jpg](seekda.jpg "Image:seekda.jpg")


Another Web Server with good links and Resources is WSindex
(http://www.wsindex.org).

![Image:wsindex.png](wsindex.png "Image:wsindex.png")

*' UDDI Browser*'
A web server that provides a very useful UDDI on-line tool to browse and
search public UDDI resources is offered on
<http://www.soapclient.com/uddisearch.html>.
We can see we can use two operators, Microsoft and XMethods

![Image:uddi_browser_part.jpg](uddi_browser_part.jpg
"Image:uddi_browser_part.jpg")
The server offers, for example, to search all UDDI with a specific
string in business names, service names or service types.
**Advanced UDDI browsing**
We can search private UDDI registries using the Advanced feature of UDDI
browser.

![Image:uddi_browser.jpg](uddi_browser.jpg "Image:uddi_browser.jpg")

This service allows interaction with Web services dynamically.
Soapclient offer others methods to allow you to discover web services
and useful links to other resources.



**Command line interaction**
Sometimes it is useful to interact with webservices from a command
line.

Simple SOAP Client - SOAPClient4XG
SOAPClient4XG is a SOAP Client for XML which allows you to make a SOAP
request from command line, for example:

`java -jar SOAPClient4XG `<http://api.google.com/search/beta2>`  my_sample_search.xml`


CURL
We can also use a Webservice using CURL.
For example:

`curl --request POST --header “Content-type: text/xml `
`       --data @my_request.xml `<http://api.google.com/search/beta2>

Perl - SOAPlite
With Perl and SOAP::lite modules we can create a scripts to automatize a
SOAP request.

**SOAP XML File**
To invoke web services from command line, we can create a SOAP request
file similar to the following one, and then use CURL to submit it to
server.

    <SOAP-ENV:Envelope
      xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/"
      SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">

      <SOAP-ENV:Body>

       <m:GetZip xmlns:m="http://namespaces.example.com">
         <country>Italy</country>
         <city>Roma</city>
       </m:GetZip>

      </SOAP-ENV:Body>

    </SOAP-ENV:Envelope>


Creating a malformed XML file we can test a Webservices for a typical
attack as the following:
\-oversized XML Tag
\-nested or recursive declarations
\-parameter attack
\-authentication testing
\-XSS
\-SQL Injection

## References

  - DISCO: <http://msdn.microsoft.com/en-us/magazine/cc302073.aspx>
  - UDDI OASIS Standard:
    <http://www.oasis-open.org/specs/index.php#uddiv3.0.2>
  - Understanding UDDI:
    <http://www-128.ibm.com/developerworks/webservices/library/ws-featuddi/index.html>
  - WebServices Testing: <http://www.aboutsecurity.net>


**Tools**
\* Net Square wsPawn

  - [OWASP WebScarab](OWASP_WebScarab_Project "wikilink"): Web Services
    plugin
  - Mac OSX Soap Client: <http://www.ditchnet.org/soapclient>
  - Foundstone WsDigger:
    <http://www.foundstone.com/us/resources/proddesc/wsdigger.htm>
  - Soaplite: <http://www.soaplite.com>
  - Perl: <http://www.perl.com>
  - SOAPClient4XG:
    <http://www-128.ibm.com/developerworks/xml/library/x-soapcl/>
  - CURL: <http://curl.haxx.se>


**On-line tools**
\* Web Services Directory: <http://www.wsindex.org>

  - Seekda: <http://seekda.com/>
  - UDDI Browser: <http://www.soapclient.com/>
  - Xmethods: <http://www.xmethods.net>
  - WSIndex: <http://www.wsindex.org>