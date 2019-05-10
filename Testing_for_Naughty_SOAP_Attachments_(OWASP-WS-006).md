## Brief Summary

This section describes attack vectors for Web Services that accept
attachments. The danger exists in the processing of the attachment on
the server and redistribution of the file to clients.

## Description of the Issue

Binary files, including executables and document types that can contain
malware, can be posted using a web service in several ways. These files
can be sent as a parameter of a web service method; they can be sent as
an attachment using SOAP with Attachments, and they can be sent using
DIME (Direct Internet Message Encapsulation) and WS-Attachments.

An attacker can craft an XML document (SOAP message) to send to a web
service that contains malware as an attachment. Testing to ensure the
Web Service host inspects SOAP attachments should be included in the web
application testing plan.

## Black Box testing and example

**Testing for file as parameter vulnerabilities:**

1\. Find WSDL that accepts attachments:

For example:

`... <s:element name="UploadFile">`
`  <s:complexType>`
`  <s:sequence>`
`  <s:element minOccurs="0" maxOccurs="1" name="filename" type="s:string" /> `
`  <s:element minOccurs="0" maxOccurs="1" name="type" type="s:string" /> `
`  <s:element minOccurs="0" maxOccurs="1" name="chunk" type="s:base64Binary" /> `
`  <s:element minOccurs="1" maxOccurs="1" name="first" type="s:boolean" /> `
` </s:sequence>`
` </s:complexType>`
` </s:element>`
` <s:element name="UploadFileResponse">`
` <s:complexType>`
` <s:sequence>`
` <s:element minOccurs="1" maxOccurs="1" name="UploadFileResult" type="s:boolean" /> `
` </s:sequence>`
` </s:complexType>`
` </s:element> ... `

2\. Attach a test virus attachment using a non-destructive virus like
EICAR, to a SOAP message and post to the target Web Service. In this
example, EICAR is used.

SOAP message with EICAR attachment (as Base64 data):

`POST /Service/Service.asmx HTTP/1.1`
`Host: somehost`
`Content-Type: text/xml; charset=utf-8`
`Content-Length: length`
`SOAPAction: `<http://somehost/service/UploadFile>


<?xml version="1.0" encoding="utf-8"?>

<soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xmlns:xsd="http://www.w3.org/2001/XMLSchema"
  xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
<soap:Body>
<UploadFile ns="http://somehost/service">
<filename>`eicar.pdf`</filename>
<type>`pdf`</type>
<chunk>`X5O!P%@AP[4\PZX54(P^)7CC)7}$EICAR-STANDARD-ANTIVIRUS-TEST-FILE!$H+H*`</chunk>
<first>`true`</first>
</UploadFile>
</soap:Body>
</soap:Envelope>

**Result Expected:**

A SOAP response with the UploadFileResult parameter set to true (this
will vary per service). The EICAR test virus file is allowed to be
stored on the host server and can be redistributed as a PDF.

''' Testing for SOAP with Attachment vulnerabilities

The testing is similar, however, the request would be similar to the
following (note the EICAR base64 info):

`  `
`POST /insuranceClaims HTTP/1.1`
`Host: www.risky-stuff.com`
`Content-Type: Multipart/Related; boundary=MIME_boundary; type=text/xml;`
`        start="<claim061400a.xml@claiming-it.com>"`
`Content-Length: XXXX`
`SOAPAction: http://schemas.risky-stuff.com/Auto-Claim`
`Content-Description: This is the optional message description.`
`  `
`--MIME_boundary`
`Content-Type: text/xml; charset=UTF-8`
`Content-Transfer-Encoding: 8bit`
`Content-ID: <claim061400a.xml@claiming-it.com>`
`  `
`<?xml version='1.0' ?>`
`<SOAP-ENV:Envelope`
`xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/">`
`<SOAP-ENV:Body>`
`<claim:insurance_claim_auto id="insurance_claim_document_id"`
`xmlns:claim="http://schemas.risky-stuff.com/Auto-Claim">`
`<theSignedForm href="cid:claim061400a.tiff@claiming-it.com"/>`
`<theCrashPhoto href="cid:claim061400a.jpeg@claiming-it.com"/>`
`  `
`</claim:insurance_claim_auto>`
`</SOAP-ENV:Body>`
`</SOAP-ENV:Envelope>`
`  `
`--MIME_boundary`
`Content-Type: image/tiff`
`Content-Transfer-Encoding: base64`
`Content-ID: <claim061400a.tiff@claiming-it.com>`
`  `
`X5O!P%@AP[4\PZX54(P^)7CC)7}$EICAR-STANDARD-ANTIVIRUS-TEST-FILE!$H+H*`
`--MIME_boundary`
`Content-Type: image/jpeg`
`Content-Transfer-Encoding: binary`
`Content-ID: <claim061400a.jpeg@claiming-it.com>`
`  `
`...Raw JPEG image..`
`--MIME_boundary-- `

**Result Expected:**

The EICAR test virus file is allowed to be stored on the host server and
can be redistributed as a TIFF file.

## References

  - Xml.com - <http://www.xml.com/pub/a/2003/02/26/binaryxml.html>
  - W3C: "Soap with Attachments" -
    <http://www.w3.org/TR/SOAP-attachments>

**Tools**

  - EICAR (http://www.eicar.org/anti_virus_test_file.htm)
  - [OWASP WebScarab](OWASP_WebScarab_Project "wikilink")