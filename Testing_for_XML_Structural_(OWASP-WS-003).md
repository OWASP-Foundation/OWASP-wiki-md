## Brief Summary

XML needs to be well-formed to function properly. XML which is not
well-formed shall fail when parsed by the XML parser on the server side.
A parser needs to run thorough the entire XML message in a serial manner
in order to assess the XML well-formedness.

An XML parser is also very CPU labour intensive. Some attack vectors
exploit this weakness by sending very large or malformed XML messages.

Testers can create XML documents which are structured in such a way as
to create a denial of service attack on the receiving server by tying up
memory and CPU resources. This occurs via overloading the XML parser
which, as we mentioned, is very CPU-intensive.

## Description of the Issue

This section discusses the types of attack vectors one could send to a
web service in an attempt to assess its reaction to malformed or
maliciously-crafted messages.

For example, elements which contain large numbers of attributes can
cause problems with parsers. This category of attack also includes XML
documents which are not well-formed XML (e.g., with overlapping
elements, or with open tags that have no matching close tags). DOM-based
parsing can be vulnerable to DoS due to the fact that the complete
message is loaded into memory (as opposed to SAX parsing). For example,
oversized attachments can cause an issue with DOM architectures.

**Web Services weakness:** You have to parse XML via SAX or DOM before
validating the structure and content of the message.

## Black Box Testing and example

**Examples:**

Malformed structure: The XML message must be well-formed in order to be
successfully parsed. Malformed SOAP messages may cause unhandled
exceptions to occur;

<?xml version="1.0" encoding="ISO-8859-1"?>

<note id="666">

**<to>**`OWASP`
<from>`EOIN`</from>
<heading>`I am Malformed `**</to>**
</heading>

<body>

Don’t forget me this weekend\!

</body>

</note>

**Example 2:**

Back to the following WS example:

<http://www.example.com/ws/FindIP.asmx?WSDL>

we have obtained the following WS Profile:
\[Method\] GetURLIP

`[Input] string EnterURL`
`[Output] string`

A standard SOAP Request is like the following:

`POST /ws/email/FindIP.asmx HTTP/1.0`
`User-Agent: Mozilla/4.0 (compatible; MSIE 6.0; MS Web Services Client Protocol 1.1.4322.2032)`
`Content-Type: text/xml; charset=utf-8`
`SOAPAction: "`<http://example.com/webservices/GetURLIP>`"`
`Content-Length: 329`
`Expect: 100-continue`
`Connection: Keep-Alive`
`Host: www.example.com`

<?xml version="1.0" encoding="utf-8"?>

<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"  xmlns:xsd="http://www.w3.org/2001/XMLSchema">
<soap:Body>
<GetURLIP ns="http://example.com/webservices/">
<EnterURL>**`www.owasp.org`**</EnterURL>
</GetURLIP>
</soap:Body>
</soap:Envelope>

The SOAP Response is:

`HTTP/1.1 200 OK`
`Server: Microsoft-IIS/5.0`
`Date: Mon, 26 Mar 2007 11:29:25 GMT`
`MicrosoftOfficeWebServer: 5.0_Pub`
`X-Powered-By: ASP.NET`
`X-AspNet-Version: 1.1.4322`
`Cache-Control: private, max-age=0`
`Content-Type: text/xml; charset=utf-8`
`Content-Length: 396`

<?xml version="1.0" encoding="utf-8"?>

<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"  xmlns:xsd="http://www.w3.org/2001/XMLSchema">
<soap:Body>
<GetURLIPResponse ns="http://example.com/webservices/">
<GetURLIPResult>**`www.owasp.com``   ``IP``   ``Address``   ``is:``
 ``216.48.3.18`**
</GetURLIPResult>
</GetURLIPResponse>
</soap:Body>
</soap:Envelope>

An example of XML Structural testing is the following:

`POST /ws/email/FindIP.asmx HTTP/1.0`
`User-Agent: Mozilla/4.0 (compatible; MSIE 6.0; MS Web Services Client Protocol 1.1.4322.2032)`
`Content-Type: text/xml; charset=utf-8`
`SOAPAction: "`<http://example.com/webservices/GetURLIP>`"`
`Content-Length: 329`
`Expect: 100-continue`
`Connection: Keep-Alive`
`Host: www.example.com`

<?xml version="1.0" encoding="utf-8"?>

<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"  xmlns:xsd="http://www.w3.org/2001/XMLSchema">
<soap:Body>
<GetURLIP ns="http://example.com/webservices/">
<EnterURL>`www.example.com`
</GetURLIP>
</EnterURL>
</soap:Body>
</soap:Envelope>

A web service utilizing DOM based parsing can be "upset" by including a
very large payload in the XML message which the parser would be obliged
to parse:

**VERY LARGE & UNEXPECTED PAYLOAD:**

<Envelope>

<Header>

`   `<wsse:Security>
`     `<Hehehe>`I am a Large String (1MB)`</Hehehe>
`     `<Hehehe>`I am a Large String (1MB)`</Hehehe>
`     `<Hehehe>`I am a Large String (1MB)`</Hehehe>
`     `<Hehehe>`I am a Large String (1MB)`</Hehehe>
`     `<Hehehe>`I am a Large String (1MB)`</Hehehe>
`     `<Hehehe>`I am a Large String (1MB)`</Hehehe>
`     `<Hehehe>`I am a Large String (1MB)`</Hehehe>`…`
`    `<Signature>`…`</Signature>
`   `</wsse:Security>
` `

</Header>

<Body>

`   `<BuyCopy><ISBN>`0098666891726`</ISBN></BuyCopy>
` `

</Body>

</Envelope>

**Binary attachments:**

Web Services can also have a binary attachment such as a Blob or exe.
Web service attachments are encoded in base64 format, since the trend is
that DIME (Direct Internet Message Encapsulation) seems to be a dead-end
solution.

By attaching a very large base64 string to the message, a tester may
consume parser resources to the point of affecting availability.
Additional attacks may include the injection of an infected binary file
into the base64 binary stream. Inadequate parsing of such an attachment
may exhaust resources:

**UNEXPECTED LARGE BLOB:**

<Envelope>
` `

<Header>

`   `<wsse:Security>
`     `<file>`jgiGldkooJSSKFM%()LFM$MFKF)$KRFWF$FRFkflfkfkkorepoLPKOMkjiujhy:llki-123-01ke123-`
`      04QWS03994k£R$Trfe£elfdk4r-45kgk3lg"£!04040lf;lfFCVr$V$BB^^N&*<M&NNB%...........10MB`</file>
`    `<Signature>`…`</Signature>
`   `</wsse:Security>
` `

</Header>

<Body>

`   `<BuyCopy><ISBN>`0098666891726`</ISBN></BuyCopy>
` `

</Body>

</Envelope>


**WSDigger**
Using this tool we can insert a malicious data into web service method
and see the results in the output of WSDigger interface.
WSDigger contains sample attack plug-ins for:

  - SQL injection
  - cross site scripting
  - XPATH injection attacks



<center>

![Image:wsdigger_attack.jpg](wsdigger_attack.jpg
"Image:wsdigger_attack.jpg")

</center>



## Grey Box Testing and example

If one has access to the schema of the web service, it should be
examined. One should assess that all the parameters are being data
validated. Restrictions on appropriate values should be implemented in
accordance to data validation best practice.

**enumeration**: Defines a list of acceptable values.

**fractionDigits**: Specifies the maximum number of decimal places
allowed. Must be greater than or equal to zero.

**length**: Specifies the exact number of characters or list items
allowed. Must be greater than or equal to zero.

**maxExclusive**: Specifies the upper bounds for numeric values (the
value must be less than this value).

**maxInclusive**: Specifies the upper bounds for numeric values (the
value must be less than or equal to this value).

**maxLength**: Specifies the maximum number of characters or list items
allowed. Must be greater than or equal to zero.

**minExclusive**: Specifies the lower bounds for numeric values (the
value must be greater than this value) .

**minInclusive**: Specifies the lower bounds for numeric values (the
value must be greater than or equal to this value).

**minLength**: Specifies the minimum number of characters or list items
allowed. Must be greater than or equal to zero.

**pattern**: Defines the exact sequence of characters that are
acceptable.

**totalDigits**: Specifies the exact number of digits allowed. Must be
greater than zero.

**whiteSpace**: Specifies how white space (line feeds, tabs, spaces, and
carriage returns) is handled.

## References

**Whitepapers**
\* W3Schools schema introduction -
<http://www.w3schools.com/schema/schema_intro.asp>
**Tools**
\* [OWASP WebScarab](OWASP_WebScarab_Project "wikilink"): Web Services
plugin