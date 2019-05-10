## Introduction

In this elaborately and complexly connected world of the Internet,
designers and programmers are forever expected to exercise vigil against
attacks that threaten to bring down one of the greatest business
enablers; Software Applications. Applications are constantly probed for
vulnerability and when found to be vulnerable, are attacked with
sustained belligerence. This hurts the business, the designer’s
reputation and the programmer’s self-esteem. The mention of cross site
scripting (XSS) threats raises this specter, which has most programmers
ducking for cover. From programming school up, we are exhorted to
validate all inputs. Trust no one, we are told. But then, as always,
practice strays away from learning. Programmer resilience in the face of
such threats has always brought about solutions that neutralize the
threats and for XSS too there are validation frameworks and validation
controls. But then, with increased proliferation of SOA, a html based
form is not necessarily the only source of input to an application.
Trust no one. And then, there are applications that are already deployed
and vulnerable. Re-factoring such applications can be cumbersome and
expensive. This article endeavors to bring forth a definition system
which works in collaboration with a validation system to protect an
application from attacks. The idea is much like building a moat around a
fort. The application is not concerned with the validation system, other
than lowering the draw bridge to accept valid inputs\!

## The Concept

### The Validation System

All applications receive inputs; that is what they are intended for -
receive input, process the content and produce results. There are a
variety of ways through which an application will receive inputs:

  - Web forms
  - Custom client applications
  - Applications and Services
  - File based records

And it is best for an application's wellbeing that all of these inputs
are validated against defined rules. The approach the validation system
should take is, to have a pre-processor which will convert each of the
inputs to a defined XML document instance and validate this XML document
instance against a defined Schema document. With the schema document
defining the structure of the input that the application will receive,
the data type for each input field and the boundary conditions for each
input field, this validation process will cover most input scenarios for
almost all applications. There is no need to write any specific code;
just the appropriate configuration. There are however, cases where the
content or data might have a defined boundary and yet lead to the
application collecting and persisting malicious input. This is
particularly the case with free-form text or the string data type. In
such situations, the content or value of the input must be examined for
unauthorized inputs - like script tags or SQL. To say it with a picture,
the system would look thus:

<center>

[500px,400px](Image:Conceptual_-_control_flow.jpg "wikilink")

</center>

The pre-processors are kept outside the scope of this application for
each input situation will require specific handling. For instance, files
with voluminous data might want to incorporate threading logic and work
by splitting the files into record batches. Similarly, the exception
handling system is kept out of the system, for each site or application
would demand specific handling of exceptions. However, a reference
implementation for each input type should be built so that the
effectiveness of the validation system can be demonstrated.

### The Utility

The tedium of creating and maintaining XML Schema documents for each
input set that an application receives is certainly a retardant for
developers to design and use such a validation system. Yes, there are
lots of tools, but… Be that as it may, one thought process is to build a
utility which, at design/development time will capture the input field
definitions, the data types and the permissible value ranges and
generate the appropriate schema document, with appropriate restrictions.
A forms based applciation is best suited for this, which would help a
programmer create a XML schema document based on specified input
parameters and constraints. This generated schema can then be used, at
run time,to validate the contents of the input / message. An appropriate
pre-processor will be requried (unless the reference implementation is
being used) which would create the XML instance document, to be
validated with the defined schema.

The input parameters of the message that ought to captured through a
windows form are suggested to be:

  - Input Name - the name of the instance document element (eg.
    Username)
  - Has Content? - Indicate if the specified input (element in target
    Xml document instance) has content
  - Sample Input Value - sample value for the above named input (eg.
    Jairamr)
  - Data Type - the data type of the input parameter (eg. String). \*:
    Currently, ‘string’, ‘integer’, ‘decimal’ data types are supported.
  - Min, max values - the value range for the input parameter (eg.
    -100,100)
      -
        This is a polymorphic grid cell. For an input data type of
        ‘string’ the min and max values \*:translate as minimum and
        maximum lengths of the string. The header of the column changes
        \*:appropriately after you select the data type.
  - Input Format - any specific format restrictions for the input value
    (eg.
      -
        SSN, Credit Card number etc). Please provide a regular
        expression pattern to which the input \*:values are to be
        matched. Please exercise care to use RegEx that is compliant
        with the W3C XSD \*:specification.
  - Special Characters - Please provide the special characters that you
    would like to allow as \*:valid input. If you are providing a format
    pattern, include the special characters in that \*:RegEx.
  - Markup Allowed - This is a Boolean value which you set as true by
    checking the check-box. If \*:the input values must contain any kind
    of marked up text, please mark the check box. The \*:default value
    is false.
  - Mandatory - This is a Boolean value which you set as true by
    checking the check-box. A \*:mandatory input must occur in the input
    message for the message to successfully validate.
  - Has Attributes? - Indicate whether the input (element in target Xml
    document instance) has \*:attributes
  - Has Elements? - Indicate whether the input (element in target Xml
    document instance) has \*:elements

Screen-shots of a sample implementation of such an utility is shown
below:

<center>

[800px,600px](Image:SchemaGenerator-screenshot.JPG "wikilink")

</center>

With a robust definition system, the characteristics or meta-data of the
inputs that an application would receive can be translated in to an XML
Schema document, which would it turn facilitate the validation of
content, at run-time.

## Content Types

Essentially, the inputs provided with the data definition utility would
result in the creation of the appropriate XmlSchemaElement definitions.
The table below describes the input combinations and the corresponding
XMLSchemaElement definitions. The data types, value ranges, length and
patterns would be incorporated as XmlSchemaRestriction Facets for
elements that of the types XmlSchemaSimpleType and
XmlSchemaComplexType-XmlSchemaSimpleContent.

1.  Element - Simple Type (restrictions / extensions)
2.  Element + Attributes - Complex Type - simple content
3.  Element + Content - Simple Type
4.  Element + Content + Attributes - Complex Type - simple content
5.  Element + Element(s) - Complex Type – sequence
6.  Element + Element(s) + Attributes - Complex Type - simple content,
    sequence
7.  Element + Element(s) + Attributes + Content - Complex Type - complex
    content, sequence

Thus, for the validation system, all possible forms of inputs must be
canonically represented in UTF-8 encoded form. All encoded / encrypted
formats of inputs must be processed appropriately, before it is
presented to the validation system. This task is left to the
pre-processors. For example, in the pre-processor for httpRequests,
there would be one component that processes http headers, one that
handles cookies, one that handles query strings and one that handles
request parameters. Once the inputs are reduced to their string
representations, these pre-processor components will then create the XML
document instance which will be validated against the configured schema
document for that request.

The content type definition along with the value, length and format
restrictions defined in the generated schema will allow little space of
mal-content. The schema validation system will throw validation
exceptions, and will not require the validation system to process input
content (data). Two situations when content must be examined are when
the programmer specifies the length of a input to be large enough to
allow for mal-content (for example input string of max length of 80
characters) or when the user input can contain (undefined in the schema)
markup information, like HTML. For such situations, each know
vulnerability would use specific RegEx expressions to parse the content
and raise exceptions when pattern matches are found. This approach is
based on the idea that 'we know what we don't want\!'. The pre-processor
would that handle the exception depending on how it is programmed -
leaving the application in a safe state.

## Technical Details

A brief description of the generated XML schema document would be thus:

A <xs:complexType> element node should be created for the root element
and added to a fresh xml schema document instance. After this is done,
each defined input element, along with the specified meta-data, in the
definition utility should passed to a SchemeGenerator class instance.
The SchemaGenerator would then create an appropriate xml schema element.
The xml schema definitions for the input elements could be created as

1\. <xs:simpleType> with an appropriate 'base' type definition. The
other input paramteres would help in specifying <xs:restriction> facets.

2\. <xs:complexType> elements, with either <xs:simpleContent> or
<xs:complexContent> depending on whether the input element is defined as
'not containing' or 'containing' markup information.

For the string data type, the base derivation (restriction) would be
such that the value space must be devoid of any markup text. By
implication,

<script>

tags are trapped. If the programmer chooses to allow markup text, only

<script>

tags, SQL construct patterns, should be trapped, while other markup text
is passed as valid. This will neutralize most of the trivial attacks. In
many cases though, the input value minimum and maximum length, if
appropriately chosen, the secondary restrictions of <xs:minLength> and
<xs:maxLength> will trap the expanded text.

The schema validation system for data types for numeric values
<xs:integer>, <xs:decimal> <xs:float> etc will trap

<script>

tags. This is further supported by the <xs:minInclusive> and
<xs:maxinclusive> facets.

## Developer actions

The end objective of this validation system is that no coding should be
needed for validating inputs to applications - just specification and
configuration\! When the pre-processors are developed, that would indeed
be the case. During the development of the input forms or input messages
for applications, the programmer or designer should generate the per
input schema document (specification) with an appropriate target
namespace. These documents must then be saved in a appropriate folders
and the pre-processors configured to use them. The pre-processor module
must then be configured into the applications’ processing chain, for
instance in a http module in the ASP.NET engine. And a configuration
system should map the input to a corresponding document, which the
validation system will use.

## Further possibilities

I, for one, do not believe that an application should passively protect
itself from attacks and fill up log files with incidents. I believe that
the protection net must extend to preventing access. For example, if a
input message fails validation, it could be a XSS attack or quite simple
a denial of service attack. Since we have trapped an exception, we can
also capture and pass on, the offending user’s or application’s context
to an network management application. The management application can
then, either through rules or through human decision, block the
offending user or application from accessing the target application or
system.

[Category:OWASP Columns](Category:OWASP_Columns "wikilink")
[Category:OWASP Validation](Category:OWASP_Validation "wikilink")
[Category:OWASP How To](Category:OWASP_How_To "wikilink")