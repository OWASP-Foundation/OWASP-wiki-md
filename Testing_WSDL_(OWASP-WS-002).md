## Brief Summary

Once the WSDL is identified, we can test that entry point.

## Description of the Issue

Check the WSDL of the web service to find the entry points and try to
invoke an operation that is not used in a standard SOAP Request. Ensure
that the WS doesn’t give you some confidential information.

## Black Box testing and example

Given the Standard SOAP message that the Web services supplier waits for
the Web services consumer, you can craft a particular message that
invoke some hidden operations.

**Example:**

A good example is WebGoat 5.0 WSDL Scanning lesson. The following is a
screenshot from that lesson:

<center>

![Image:WSDLWebGoat.png](WSDLWebGoat.png "Image:WSDLWebGoat.png")

</center>


Here we have an interface that invokes a Web Service using only
FirstName, LastName, and Login Count as parameters.
If you look at the relative WSDL you will find:

`...`
<wsdl:portType name="WSDLScanning">
<wsdl:operation name="'''getFirstName'''" parameterOrder="id">
<wsdl:input message="impl:getFirstNameRequest" name="getFirstNameRequest"/>
<wsdl:output message="impl:getFirstNameResponse" name="getFirstNameResponse"/>

</wsdl:operation>
<wsdl:operation name="'''getLastName'''" parameterOrder="id">
<wsdl:input message="impl:getLastNameRequest" name="getLastNameRequest"/>
<wsdl:output message="impl:getLastNameResponse" name="getLastNameResponse"/>
</wsdl:operation>

<wsdl:operation name="'''getCreditCard'''" parameterOrder="id">
<wsdl:input message="impl:getCreditCardRequest" name="getCreditCardRequest"/>
<wsdl:output message="impl:getCreditCardResponse" name="getCreditCardResponse"/>
</wsdl:operation>

<wsdl:operation name="'''getLoginCount'''" parameterOrder="id">
<wsdl:input message="impl:getLoginCountRequest" name="getLoginCountRequest"/>
<wsdl:output message="impl:getLoginCountResponse" name="getLoginCountResponse"/>
</wsdl:operation>
</wsdl:portType>
`...`

We find four operations and not only three. Using the WebScarab Web
Service plugin, we can craft a SOAP Request to get the Credit Card given
a specific ID.

<center>

![Image:WSDLWebScarab.png](WSDLWebScarab.png "Image:WSDLWebScarab.png")

</center>

The SOAP Request resulting from this request is:

`POST `<http://localhost:80/WebGoat/services/SoapRequest>` HTTP/1.0`
`Accept: application/soap+xml, application/dime, multipart/related, text/*`
`Host: localhost:80`
`Content-Type: text/xml; charset=utf-8`
`SOAPAction: ""`
`Content-length: 576`
`Authorization: Basic Z3Vlc3Q6Z3Vlc3Q=`

<?xml version='1.0' encoding='UTF-8'?>

<wsns0:Envelope
   xmlns:wsns1='http://www.w3.org/2001/XMLSchema-instance'
   xmlns:xsd='http://www.w3.org/2001/XMLSchema'
   xmlns:wsns0='http://schemas.xmlsoap.org/soap/envelope/'>
`  `<wsns0:Body
     wsns0:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
`    <wsns2:`**`getCreditCard`**
`          xmlns:wsns2='`<http://lessons.webgoat.owasp.org>`'>`
`      `<id xsi:type='xsd:int'
           xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance'
       >**`101`**</id>
`    `</wsns2:getCreditCard>
`  `</wsns0:Body>
</wsns0:Envelope>

And the SOAP Response with the credit card number (987654321) is:

`HTTP/1.1 200 OK`
`Server: Apache-Coyote/1.1`
`Content-Type: text/xml;charset=utf-8`
`Date: Wed, 28 Mar 2007 10:18:12 GMT`
`Connection: close`

<?xml version="1.0" encoding="utf-8"?>

<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/"  xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">

<soapenv:Body>
<ns1:getCreditCardResponse soapenv:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/"  xmlns:ns1="http://lessons.webgoat.owasp.org">
<getCreditCardReturn xsi:type="xsd:string">**`987654321`**</getCreditCardReturn></ns1:getCreditCardResponse>
</soapenv:Body>
</soapenv:Envelope>



**WSDigger**
WSDigger is a free open source tool to automate web services security
testing.

With this tool we can test our web services, interacting with them
through a simple interface, to enter search queries and invoke web
services dynamically, without writing code.
When we interact with the web service, malicious data has been entered
into WSDigger, and the web service method must be invoked by clicking on
the invoke button.

<center>

![Image:wsdigger_part.jpg](wsdigger_part.jpg
"Image:wsdigger_part.jpg")

</center>



**Result expected:**
The tester should include full details of where the web service
application permits access to an operation that is not used during
normal SOAP messages and that provides access to confidential data.

## References

**Whitepapers**
\* W3Schools schema introduction -
<http://www.w3schools.com/schema/schema_intro.asp>
**Tools**
\*[OWASP WebScarab](OWASP_WebScarab_Project "wikilink"): Web Services
plugin

  - Foundstone WSDigger:
    <http://www.foundstone.com/us/resources/proddesc/wsdigger.htm>