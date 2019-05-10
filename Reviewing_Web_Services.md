__TOC__

## Reviewing Webservices and XML Payloads

When reviewing webservices, one should focus firstly on the generic
security controls related to any application. Webservices also have some
unique controls should be looked at.

### XML Schema : Input validation

Schemas are used to ensure that the XML payload received is within
defined and expected limits. They can be specific to a list of known
good values or simply define length and type. Some XML applications do
not have a schema implemented, which may mean input validation is
performed downstream or even not at all\!\!

*Keywords*

**`Namespace`**`: : An XML namespace is a collection of XML elements and attributes identified by an Internationalised Resource Identifier (RI). `

In a single document, elements may exist with the same name that were
created by different entities.

To distinguish between such different definitions with the same name, an
XML Schema allows the concept of namespaces - think Java packages :)

The schema can specify a finite amount of parameters, the expected
parameters in the XML payload alongside the expected types and values of
the payload data.

The ProcessContents attribute indicates how XML from other namespaces
should be validated. When the processContents attribute is set to
**lax** or **skip**, input validation is not performed for wildcard
attributes and parameters.

The value for this attribute may be

  - **strict**: There must be a declaration associated with the
    namespace and validate the XML.
  - **lax** There should be an attempt to validate the XML against its
    schema.
  - **skip** There is no attempt to validate the XML.

`processContents=strict\lax\skip`

### Infinite Occurrences of an Element or Attribute

The unbounded value can be used on an XML schema to specify the there is
no maximum occurrence expected for a specific element.

`maxOccurs= positive-Integer`

|unbounded

Given that any number of elements can be supplied for an unbounded
element, it is subject to attack via supplying the web service with vast
amounts of elements, and hence a resource exhaustion issue.

### Weak namespace, Global elements, the <any> element & SAX XML processors

The <any> element can be used to make extensible documents, allowing
documents to contain additional elements which are not declared in the
main schema. The idea that an application can accept any number of
parameters may be cause for alarm. This may lead to denial of
availability or even in the case of a SAX XML parser legitimate values
may be overwritten.

<xs:element name="cloud">
` `<xs:complexType>
`   `<xs:sequence>
`     `<xs:element name="process" type="xs:string"/>
`     `<xs:element name="lastcall" type="xs:string"/>
`     `**<xs:any minOccurs="0"/>**
`   `</xs:sequence>
` `</xs:complexType>
</xs:element>

The <any> element here permits additional parameters to be added in an
arbitary manner.

A namespace of \#\#any in the <any> element means the schema allows
elements beyond what is explicitly defined in the schema, thereby
reducing control on expected elements for a given request.

<xs:any namespace='##any' />

A schema that does not define restrictive element namespaces permits
arbitrary elements to be included in a valid document, which may not be
expected by the application. This may give rise to attacks, such as XML
Injection, which consist of including tags which are not expected by the
application.

[Category:OWASP Code Review
Project](Category:OWASP_Code_Review_Project "wikilink")