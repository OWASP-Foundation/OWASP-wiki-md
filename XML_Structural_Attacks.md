XML Structural Attacks:

Attacking the strucytre of the SOAP message in an attempt to circumvent
the schema or XML parser.

Attackers can create XML documents which are structured in such a way as
to create a DoS attacks on the receiving server by tying up memory and
CPU resources.

XML messages which contain large amounts of parameters can cause
problems with parsers. Parsers are CPU intensive, a problem that has not
been addressed as of yet (via XML acceleration).

This category of attack also includes XML documents which are not
"*well-formed*": With overlapping XML attributes. The end tag
\</element\> is placed in the middle of another element in the SOAP
document. This attack can also occur with open tags that have no
matching end tags.

Perticularly but not exclusivley With DOM based parsing oversized
attachments can cause an issue. DOM parsers load the complete
document.message into memory prior to parsing. This is memory intensive
and may cause DOS )or performance degradeation with a large message
being processed by DOM.

**Paradox:** You have to parse before you validate. Prior to validation,
a document must be parsed against a schema, but in parsing the document
a violation may occur via a structural attack.