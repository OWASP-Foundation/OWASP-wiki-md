[Development Guide Table of
Contents](Guide_Table_of_Contents "wikilink")

__TOC__

*This section of the Development Guide details the common issues facing
Web services developers, and methods to address common issues. Due to
the space limitations, it cannot look at all of the surrounding issues
in great detail, since each of them deserves a separate book of its own.
Instead, an attempt is made to steer the reader to the appropriate usage
patterns, and warn about potential roadblocks on the way.*

Web Services have received a lot of press, and with that comes a great
deal of confusion over what they really are. Some are heralding Web
Services as the biggest technology breakthrough since the web itself;
others are more skeptical that they are nothing more than evolved web
applications. In either case, the issues of web application security
apply to web services just as they do to web applications.

## What are Web Services?

Suppose you were making an application that you wanted other
applications to be able to communicate with. For example, your Java
application has stock information updated every 5 minutes and you would
like other applications, ones that may not even exist yet, to be able to
use the data.

One way you can do this is to serialize your Java objects and send them
over the wire to the application that requests them. The problem with
this approach is that a C\# application would not be able to use these
objects because it serializes and deserializes objects differently than
Java.

Another approach you could take is to send a text file filled with data
to the application that requests it. This is better because a C\#
application could read the data. But this has another flaw: Lets assume
your stock application is not the only one the C\# application needs to
interact with. Maybe it needs weather data, local restaurant data, movie
data, etc. If every one of these applications uses its own unique file
format, it would take considerable research to get the C\# application
to a working state.

The solution to both of these problems is to send a standard file
format. A format that any application can use, regardless of the data
being transported. Web Services are this solution. They let any
application communicate with any other application without having to
consider the language it was developed in or the format of the data.

At the simplest level, web services can be seen as a specialized web
application that differs mainly at the presentation tier level. While
web applications typically are HTML-based, web services are XML-based.
Interactive users for B2C (business to consumer) transactions normally
access web applications, while web services are employed as building
blocks by other web applications for forming B2B (business to business)
chains using the so-called SOA model. Web services typically present a
public functional interface, callable in a programmatic fashion, while
web applications tend to deal with a richer set of features and are
content-driven in most cases.

## Securing Web Services

Web services, like other distributed applications, require protection at
multiple levels:

  - SOAP messages that are sent on the wire should be delivered
    confidentially and without tampering

<!-- end list -->

  - The server needs to be confident who it is talking to and what the
    clients are entitled to

<!-- end list -->

  - The clients need to know that they are talking to the right server,
    and not a phishing site (see the Phishing chapter for more
    information)

<!-- end list -->

  - System message logs should contain sufficient information to
    reliably reconstruct the chain of events and track those back to the
    authenticated callers

Correspondingly, the high-level approaches to solutions, discussed in
the following sections, are valid for pretty much any distributed
application, with some variations in the implementation details.

The good news for Web Services developers is that these are
infrastructure-level tasks, so, theoretically, it is only the system
administrators who should be worrying about these issues. However, for a
number of reasons discussed later in this chapter, WS developers usually
have to be at least aware of all these risks, and oftentimes they still
have to resort to manually coding or tweaking the protection components.

## Communication security

There is a commonly cited statement, and even more often implemented
approach "We are using SSL to protect all communication, we are secure".
At the same time, there have been so many articles published on the
topic of "channel security vs. token security" that it hardly makes
sense to repeat those arguments here. Therefore, listed below is just a
brief rundown of most common pitfalls when using channel security alone:

  - It provides only "point-to-point" security

Any communication with multiple "hops" requires establishing separate
channels (and trusts) between each communicating node along the way.
There is also a subtle issue of trust transitivity, as trusts between
node pairs {A,B} and {B,C} do not automatically imply {A,C} trust
relationship.

  - Storage issue

After messages are received on the server (even if it is not the
intended recipient), they exist in the clear-text form, at least
temporarily. Storing the transmitted information at the intermediate
aggravates the problem or destination servers in log files (where it can
be browsed by anybody) and local caches.

  - Lack of interoperability

While SSL provides a standard mechanism for transport protection,
applications then have to utilize highly proprietary mechanisms for
transmitting credentials, ensuring freshness, integrity, and
confidentiality of data sent over the secure channel. Using a different
server, which is semantically equivalent, but accepts a different format
of the same credentials, would require altering the client and prevent
forming automatic B2B service chains.

Standards-based token protection in many cases provides a superior
alternative for message-oriented Web Service SOAP communication model.

That said the reality is that the most Web Services today are still
protected by some form of channel security mechanism, which alone might
suffice for a simple internal application. However, one should clearly
realize the limitations of such approach, and make conscious trade-offs
at the design time, whether channel, token, or combined protection would
work better for each specific case.

## Passing credentials

In order to enable credentials exchange and authentication for Web
Services, their developers must address the following issues.

First, since SOAP messages are XML-based, all passed credentials have to
be converted to text format. This is not a problem for username/password
types of credentials, but binary ones (like X.509 certificates or
Kerberos tokens) require converting them into text prior to sending and
unambiguously restoring them upon receiving, which is usually done via a
procedure called Base64 encoding and decoding.

Second, passing credentials carries an inherited risk of their
disclosure, either by sniffing them during the wire transmission, or by
analyzing the server logs. Therefore, things like passwords and private
keys need to be either encrypted, or just never sent "in the clear".
Usual ways to avoid sending sensitive credentials are using
cryptographic hashing and/or signatures.

## Ensuring message freshness

Even a valid message may present a danger if it is utilized in a "replay
attack". i.e. it is sent multiple times to the server to make it repeat
the requested operation. This may be achieved by capturing an entire
message, even if it is sufficiently protected against tampering, since
it is the message itself that is used for attack now (see the XML
Injection section of the Interpreter Injection chapter).

Usual means to protect against replayed messages is either using unique
identifiers (nonces) on messages and keeping track of processed ones, or
using a relatively short validity time window. In the Web Services
world, information about the message creation time is usually
communicated by inserting timestamps, which may just tell the instant
the message was created, or have additional information, like its
expiration time, or certain conditions.

The latter solution, although easier to implement, requires clock
synchronization and is sensitive to server time skew, whereas server or
clients' clocks drift too much, preventing timely message delivery,
although this usually does not present significant problems with
modern-day computers. A greater issue lies with message queuing at the
servers, where messages may be expiring while waiting to be processed in
the queue of an especially busy or non-responsive server.

## Protecting message integrity

When a message is received by a web service, it must always ask two
questions: ¿whether I trust the caller?, ¿whether it created this
message ?. Assuming that the caller trust has been established one way
or another, the server has to be assured that the message it is looking
at was indeed issued by the caller, and not altered along the way
(intentionally or not). This may affect technical qualities of a SOAP
message, such as the message's timestamp, or business content, such as
the amount to be withdrawn from the bank account. Obviously, neither
change should go undetected by the server.

In communication protocols, there are usually some mechanisms like
checksum applied to ensure packet's integrity. This would not be
sufficient, however, in the realm of publicly exposed Web Services,
since checksums (or digests, their cryptographic equivalents) are easily
replaceable and cannot be reliably tracked back to the issuer. The
required association may be established by utilizing HMAC, or by
combining message digests with either cryptographic signatures or with
secret key-encryption (assuming the keys are only known to the two
communicating parties) to ensure that any change will immediately result
in a cryptographic error.

## Protecting message confidentiality

Oftentimes, it is not sufficient to ensure the integrity; in many cases
it is also desirable that nobody can see the data that is passed around
and/or stored locally. It may apply to the entire message being
processed, or only to certain parts of it; In either case, some type of
encryption is required to conceal the content. Normally, symmetric
encryption algorithms are used to encrypt bulk data, since it is
significantly faster than the asymmetric ones. Asymmetric encryption is
then applied to protect the symmetric session keys, which, in many
implementations, are valid for one communication only and are
subsequently discarded.

Applying encryption requires conducting an extensive setup work, since
the communicating parties now have to be aware of which keys they can
trust, deal with certificate and key validation, and know which keys
should be used for communication.

In many cases, encryption is combined with signatures to provide both
integrity and confidentiality. Normally, signing keys are different from
the encrypting ones, primarily because of their different lifecycles,
signing keys are permanently associated with their owners, while
encryption keys may be invalidated after the message exchange. Another
reason may be separation of business responsibilities - the signing
authority (and the corresponding key) may belong to one department or
person, while encryption keys are generated by the server controlled by
members of IT department.

## Access control

After the message has been received and successfully validated, the
server must decide:

  - Does it know who is requesting the operation (Identification)

<!-- end list -->

  - Does it trust the caller's identity claim (Authentication)

<!-- end list -->

  - Does it allow the caller to perform this operation (Authorization)

There is not much WS-specific activity that takes place at this stage,
just several new ways of passing the credentials for authentication.
Most often, authorization (or entitlement) tasks occur completely
outside of the Web Service implementation, at the Policy Server that
protects the whole domain.

There is another significant problem here, the traditional HTTP
firewalls do not help at stopping attacks at the Web Services. An
organization would need an XML/SOAP firewall, which is capable of
conducting application-level analysis of the web server's traffic and
make intelligent decision about passing SOAP messages to their
destination. The reader would need to refer to other books and
publications on this very important topic, as it is impossible to cover
it within just one chapter.

## Audit

A common task, typically required from the audits, is reconstructing the
chain of events that led to a certain problem. Normally, this would be
achieved by saving server logs in a secure location, available only to
the IT administrators and system auditors, in order to create what is
commonly referred to as "audit trail". Web Services are no exception to
this practice, and follow the general approach of other types of Web
Applications.

Another auditing goal is non-repudiation, meaning that a message can be
verifiably traced back to the caller. Following the standard legal
practice, electronic documents now require some form of an "electronic
signature", but its definition is extremely broad and can mean
practically anything, in many cases, entering your name and birthday
qualifies as an e-signature.

As far as the WS are concerned, such level of protection would be
insufficient and easily forgeable. The standard practice is to require
cryptographic digital signatures over any content that has to be legally
binding, if a document with such a signature is saved in the audit log,
it can be reliably traced to the owner of the signing key

## Web Services Security Hierarchy

Technically speaking, Web Services themselves are very simple and
versatile, XML-based communication, described by an XML-based grammar,
called Web Services Description Language (WSDL, see
<u><http://www.w3.org/TR/2005/WD-wsdl20-20050510></u>), which binds
abstract service interfaces, consisting of messages, expressed as XML
Schema, and operations, to the underlying wire format. Although it is by
no means a requirement, the format of choice is currently SOAP over
HTTP. This means that Web Service interfaces are described in terms of
the incoming and outgoing SOAP messages, transmitted over HTTP protocol.

### Standards committees

Before reviewing the individual standards, it is worth taking a brief
look at the organizations which are developing and promoting them. There
are quite a few industry-wide groups and consortiums working in this
area, most important of which are listed below.

W3C (see <u><http://www.w3.org></u>) is the most well known industry
group, which owns many Web-related standards and develops them in
Working Group format. Of particular interest to this chapter are XML
Schema, SOAP, XML-dsig, XML-enc, and WSDL standards (called
recommendations in the W3C's jargon).

OASIS (see <u><http://www.oasis-open.org></u>) mostly deals with Web
Service-specific standards, not necessarily security-related. It also
operates on a committee basis, forming so-called Technical Committees
(TC) for the standards that it is going to be developing. Of interest
for this discussion, OASIS owns WS-Security and SAML standards.

Web Services Interoperability Organization (WS-I, see
<u><http://www.ws-i.org/></u>) was formed to promote a general framework
for interoperable Web Services. Mostly its work consists of taking other
broadly accepted standards, and developing so-called profiles, or sets
of requirements for conforming Web Service implementations. In
particular, its Basic Security Profile (BSP) relies on the OASIS'
WS-Security standard and specifies sets of optional and required
security features in Web Services that claim interoperability.

Liberty Alliance (LA, see <u><http://projectliberty.org></u>) consortium
was formed to develop and promote an interoperable Identity Federation
framework. Although this framework is not strictly Web Service-specific,
but rather general, it is important for this topic because of its close
relation with the SAML standard developed by OASIS.

Besides the previously listed organizations, there are other industry
associations, both permanently established and short-lived, which push
forward various Web Service security activities. They are usually made
up of software industry's leading companies, such as Microsoft, IBM,
Verisign, BEA, Sun, and others, that join them to work on a particular
issue or proposal. Results of these joint activities, once they reach
certain maturity, are often submitted to standardizations committees as
a basis for new industry standards.

## SOAP

Simple Object Access Protocol (SOAP, see
<u><http://www.w3.org/TR/2003/REC-soap12-part1-20030624/></u>) provides
an XML-based framework for exchanging structured and typed information
between peer services. This information, formatted into Header and Body,
can theoretically be transmitted over a number of transport protocols,
but only HTTP binding has been formally defined and is in active use
today. SOAP provides for Remote Procedure Call-style (RPC) interactions,
similar to remote function calls, and Document-style communication, with
message contents based exclusively on XML Schema definitions in the Web
Service's WSDL. Invocation results may be optionally returned in the
response message, or a Fault may be raised, which is roughly equivalent
to using exceptions in traditional programming languages.

SOAP protocol, while defining the communication framework, provides no
help in terms of securing message exchanges, the communications must
either happen over secure channels, or use protection mechanisms
described later in this chapter.

### XML security specifications (XML-dsig & Encryption)

XML Signature (XML-dsig, see
<u><http://www.w3.org/TR/2002/REC-xmldsig-core-20020212></u>/), and XML
Encryption (XML-enc, see
<u><http://www.w3.org/TR/2002/REC-xmlenc-core-20021210/></u>) add
cryptographic protection to plain XML documents. These specifications
add integrity, message and signer authentication, as well as support for
encryption/decryption of whole XML documents or only of some elements
inside them.

The real value of those standards comes from the highly flexible
framework developed to reference the data being processed (both internal
and external relative to the XML document), refer to the secret keys and
key pairs, and to represent results of signing/encrypting operations as
XML, which is added to/substituted in the original document.

However, by themselves, XML-dsig and XML-enc do not solve the problem of
securing SOAP-based Web Service interactions, since the client and
service first have to agree on the order of those operations, where to
look for the signature, how to retrieve cryptographic tokens, which
message elements should be signed and encrypted, how long a message is
considered to be valid, and so on. These issues are addressed by the
higher-level specifications, reviewed in the following sections.

### Security specifications

In addition to the above standards, there is a broad set of
security-related specifications being currently developed for various
aspects of Web Service operations.

One of them is SAML, which defines how identity, attribute, and
authorization assertions should be exchanged among participating
services in a secure and interoperable way.

A broad consortium, headed by Microsoft and IBM, with the input from
Verisign, RSA Security, and other participants, developed a family of
specifications, collectively known as "Web Services Roadmap". Its
foundation, WS-Security, has been submitted to OASIS and became an OASIS
standard in 2004. Other important specifications from this family are
still found in different development stages, and plans for their
submission have not yet been announced, although they cover such
important issues as security policies (WS-Policy et al), trust issues
and security token exchange (WS-Trust), establishing context for secure
conversation (WS-SecureConversation). One of the specifications in this
family, WS-Federation, directly competes with the work being done by the
LA consortium, and, although it is supposed to be incorporated into the
Longhorn release of Windows, its future is not clear at the moment,
since it has been significantly delayed and presently does not have
industry momentum behind it.

## WS-Security Standard

WS-Security specification (WSS) was originally developed by Microsoft,
IBM, and Verisign as part of a "Roadmap", which was later renamed to Web
Services Architecture, or WSA. WSS served as the foundation for all
other specifications in this domain, creating a basic infrastructure for
developing message-based security exchange. Because of its importance
for establishing interoperable Web Services, it was submitted to OASIS
and, after undergoing the required committee process, became an
officially accepted standard. Current version is 1.1, and it was
released on February 17, 2006.
The protocol is currently officially called WSS and developed via
committee in Oasis-Open.

### Organization of the standard

The WSS standard itself deals with several core security areas, leaving
many details to so-called profile documents. The core areas, broadly
defined by the standard, are:

  - Ways to add security headers (WSSE Header) to SOAP Envelopes

<!-- end list -->

  - Attachment of security tokens and credentials to the message

<!-- end list -->

  - Inserting a timestamp

<!-- end list -->

  - Signing the message

<!-- end list -->

  - Encrypting the message

<!-- end list -->

  - Extensibility

Flexibility of the WS-Security standard lies in its extensibility, so
that it remains adaptable to new types of security tokens and protocols
that are being developed. This flexibility is achieved by defining
additional profiles for inserting new types of security tokens into the
WSS framework. While the signing and encrypting parts of the standards
are not expected to require significant changes (only when the
underlying XML-dsig and XML-enc are updated), the types of tokens,
passed in WSS messages, and ways of attaching them to the message may
vary substantially. At the high level the WSS standard defines three
types of security tokens, attachable to a WSS Header: Username/password,
Binary, and XML tokens. Each of those types is further specified in one
(or more) profile document, which defines additional tokens' attributes
and elements, needed to represent a particular type of security token.

![Figure 4: WSS specification hierarchy](WSS_Specification_Hierarchy.gif
"Figure 4: WSS specification hierarchy")

### Purpose

The primary goal of the WSS standard is providing tools for
message-level communication protection, whereas each message represents
an isolated piece of information, carrying enough security data to
verify all important message properties, such as: authenticity,
integrity, freshness, and to initiate decryption of any encrypted
message parts. This concept is a stark contrast to the traditional
channel security, which methodically applies pre-negotiated security
context to the whole stream, as opposed to the selective process of
securing individual messages in WSS. In the Roadmap, that type of
service is eventually expected to be provided by implementations of
standards like WS-SecureConversation.

From the beginning, the WSS standard was conceived as a message-level
toolkit for securely delivering data for higher level protocols. Those
protocols, based on the standards like WS-Policy, WS-Trust, and Liberty
Alliance, rely on the transmitted tokens to implement access control
policies, token exchange, and other types of protection and integration.
However, taken alone, the WSS standard does not mandate any specific
security properties, and an ad-hoc application of its constructs can
lead to subtle security vulnerabilities and hard to detect problems, as
is also discussed in later sections of this chapter.

## WS-Security Building Blocks

The WSS standard actually consists of a number of documents, one core
document, which defines how security headers may be included into SOAP
envelope and describes all high-level blocks, which must be present in a
valid security header. Profile documents have the dual task of extending
definitions for the token types they are dealing with, providing
additional attributes, elements, as well as defining relationships left
out of the core specification, such as using attachments.

Core WSS 1.1 specification, located at
<u><http://www.oasis-open.org/committees/download.php/16790/wss-v1.1-spec-os-SOAPMessageSecurity.pdf></u>,
defines several types of security tokens (discussed later in this
section: see 0), ways to reference them, timestamps, and ways to apply
XML-dsig and XML-enc in the security headers, see the XML Dsig section
for more details about their general structure.

Associated specifications are:

  - Username token profile 1.1, located at
    <u><http://www.oasis-open.org/committees/download.php/16782/wss-v1.1-spec-os-UsernameTokenProfile.pdf></u>,
    which adds various password-related extensions to the basic
    UsernameToken from the core specification

<!-- end list -->

  - X.509 token profile 1.1, located at
    <u><http://www.oasis-open.org/committees/download.php/16785/wss-v1.1-spec-os-x509TokenProfile.pdf></u>
    which specifies, how X.509 certificates may be passed in the
    BinarySecurityToken, specified by the core document

<!-- end list -->

  - SAML Token profile 1.1, located at
    <u><http://www.oasis-open.org/committees/download.php/16768/wss-v1.1-spec-os-SAMLTokenProfile.pdf></u>
    that specifies how XML-based SAML tokens can be inserted into WSS
    headers.

<!-- end list -->

  - Kerberos Token Profile 1.1, located at
    <u><http://www.oasis-open.org/committees/download.php/16788/wss-v1.1-spec-os-KerberosTokenProfile.pdf></u>
    that defines how to encode Kerberos tickets and attach them to SOAP
    messages.

<!-- end list -->

  - Rights Expression Language (REL) Token Profile 1.1, located at
    <u><http://www.oasis-open.org/committees/download.php/16687/oasis-wss-rel-token-profile-1.1.pdf></u>
    that describes the use of ISO/IEC 21000-5 Rights Expressions with
    respect to the WS-Security specification.

<!-- end list -->

  - SOAP with Attachments (SWA) Profile 1.1, located at
    <u><http://www.oasis-open.org/committees/download.php/16672/wss-v1.1-spec-os-SwAProfile.pdf></u>
    that describes how to use WSS-Sec with SOAP Messages with
    Attachments.

### How data is passed

WSS security specification deals with two distinct types of data:
security information, which includes security tokens, signatures,
digests, etc; and message data, i.e. everything else that is passed in
the SOAP message. Being an XML-based standard, WSS works with textual
information grouped into XML elements. Any binary data, such as
cryptographic signatures or Kerberos tokens, has to go through a special
transform, called Base64 encoding/decoding, which provides
straightforward conversion from binary to ASCII formats and back. The
example below demonstrates how binary data looks like in the encoded
format:


*cCBDQTAeFw0wNDA1MTIxNjIzMDRaFw0wNTA1MTIxNjIzMDRaMG8xCz*


After encoding a binary element, an attribute with the algorithm's
identifier is added to the XML element carrying the data, so that the
receiver would know to apply the correct decoder to read it. These
identifiers are defined in the WSS specification documents.

### Security header's structure

A security header in a message is used as a sort of an envelope around a
letter, it seals and protects the letter, but does not care about its
content. This "indifference" works in the other direction as well, as
the letter (SOAP message) should not know, nor should it care about its
envelope (WSS Header), since the different units of information, carried
on the envelope and in the letter, are presumably targeted at different
people or applications.

A SOAP Header may actually contain multiple security headers, as long as
they are addressed to different actors (for SOAP 1.1), or roles (for
SOAP 1.2). Their contents may also be referring to each other, but such
references present a very complicated logistical problem for determining
the proper order of decryptions/signature verifications, and should
generally be avoided. WSS security header itself has a loose structure,
as the specification itself does not require any elements to be present;
so, the minimalist header with an empty message will look like:



<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
<soap:Header>
`    `<wsse:Security xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd" xmlns:wsu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd" soap:mustUnderstand="1">

`    `</wsse:Security>
</soap:Header>
<soap:Body>

</soap:Body>
</soap:Envelope>


However, to be useful, it must carry some information, which is going to
help securing the message. It means including one or more security
tokens (see 0) with references, XML Signature, and XML Encryption
elements, if the message is signed and/or encrypted. So, a typical
header will look more like the following picture:



<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
<soap:Header>
<wsse:Security ns="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd" xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd" xmlns:wsu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd" soap:mustUnderstand="1">
`  `<wsse:BinarySecurityToken EncodingType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0#Base64Binary" ValueType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0#X509v3" wsu:Id="aXhOJ5">`MIICtzCCAi... `
`  `</wsse:BinarySecurityToken>
`  `<xenc:EncryptedKey xmlns:xenc="http://www.w3.org/2001/04/xmlenc#">
`    `<xenc:EncryptionMethod Algorithm="http://www.w3.org/2001/04/xmlenc#rsa-1_5"/>
`   `<dsig:KeyInfo xmlns:dsig="http://www.w3.org/2000/09/xmldsig#">
`     `<wsse:SecurityTokenReference>
`       `<wsse:Reference URI="#aXhOJ5" ValueType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0#X509v3"/>
`     `</wsse:SecurityTokenReference>`  `
`   `</dsig:KeyInfo>
`   `<xenc:CipherData>
`     `<xenc:CipherValue>`Nb0Mf...`</xenc:CipherValue>
`   `</xenc:CipherData>
`   `<xenc:ReferenceList>
`     `<xenc:DataReference URI="#aDNa2iD"/>
`   `</xenc:ReferenceList>
`  `</xenc:EncryptedKey>
`  `<wsse:SecurityTokenReference wsu:Id="aZG0sG">
`   `<wsse:KeyIdentifier ValueType="http://docs.oasis-open.org/wss/2004/XX/oasis-2004XX-wss-saml-token-profile-1.0#SAMLAssertionID" wsu:Id="a2tv1Uz">` 1106844369755`</wsse:KeyIdentifier>
`  `</wsse:SecurityTokenReference>
`  `<saml:Assertion AssertionID="1106844369755" IssueInstant="2005-01-27T16:46:09.755Z" Issuer="www.my.com" MajorVersion="1" MinorVersion="1" xmlns:saml="urn:oasis:names:tc:SAML:1.0:assertion">
`       ...             `
`  `</saml:Assertion>
`  `<wsu:Timestamp wsu:Id="afc6fbe-a7d8-fbf3-9ac4-f884f435a9c1">
`   `<wsu:Created>`2005-01-27T16:46:10Z`</wsu:Created>
`   `<wsu:Expires>`2005-01-27T18:46:10Z`</wsu:Expires>
` `</wsu:Timestamp>
`  `<dsig:Signature xmlns:dsig="http://www.w3.org/2000/09/xmldsig#" Id="sb738c7">
`   `<dsig:SignedInfo Id="obLkHzaCOrAW4kxC9az0bLA22">
`       ...`
`     `<dsig:Reference URI="#s91397860">
`       ...                                 `
`        `<dsig:DigestValue>`5R3GSp+OOn17lSdE0knq4GXqgYM=`</dsig:DigestValue>
`     `</dsig:Reference>
`     `</dsig:SignedInfo>
`     `<dsig:SignatureValue Id="a9utKU9UZk">`LIkagbCr5bkXLs8l...`</dsig:SignatureValue>
`     `<dsig:KeyInfo>
`     `<wsse:SecurityTokenReference>
`       `<wsse:Reference URI="#aXhOJ5" ValueType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0#X509v3"/>
`     `</wsse:SecurityTokenReference>
`    `</dsig:KeyInfo>
`  `</dsig:Signature>
</wsse:Security>
</soap:Header>
<soap:Body xmlns:wsu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd" wsu:Id="s91397860">
<xenc:EncryptedData xmlns:xenc="http://www.w3.org/2001/04/xmlenc#" Id="aDNa2iD" Type="http://www.w3.org/2001/04/xmlenc#Content">
` `<xenc:EncryptionMethod Algorithm="http://www.w3.org/2001/04/xmlenc#tripledes-cbc"/>
`  `<xenc:CipherData>
`   `<xenc:CipherValue>`XFM4J6C...`</xenc:CipherValue>
`  `</xenc:CipherData>
</xenc:EncryptedData>
</soap:Body>
</soap:Envelope>

### Types of tokens

A WSS Header may have the following types of security tokens in it:

  - Username token

Defines mechanisms to pass username and, optionally, a password - the
latter is described in the username profile document. Unless the whole
token is encrypted, a message which includes a clear-text password
should always be transmitted via a secured channel. In situations where
the target Web Service has access to clear-text passwords for
verification (this might not be possible with LDAP or some other user
directories, which do not return clear-text passwords), using a hashed
version with nonce and a timestamp is generally preferable. The profile
document defines an unambiguous algorithm for producing password hash:

`Password_Digest = Base64 ( SHA-1 ( nonce + created + password ) )`

  - Binary token

They are used to convey binary data, such as X.509 certificates, in a
text-encoded format, Base64 by default. The core specification defines
BinarySecurityToken element, while profile documents specify additional
attributes and sub-elements to handle attachment of various tokens.
Presently, both the X.509 and the Kerberos profiles have been adopted.



`      `<wsse:BinarySecurityToken EncodingType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0#Base64Binary" ValueType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0#X509v3" wsu:Id="aXhOJ5">
`    MIICtzCCAi...`
`  `</wsse:BinarySecurityToken>



  - XML token

These are meant for any kind of XML-based tokens, but primarily, for
SAML assertions. The core specification merely mentions the possibility
of inserting such tokens, leaving all details to the profile documents.
At the moment, SAML 1.1 profile has been accepted by OASIS.



`   `<saml:Assertion AssertionID="1106844369755" IssueInstant="2005-01-27T16:46:09.755Z" Issuer="www.my.com" MajorVersion="1" MinorVersion="1" xmlns:saml="urn:oasis:names:tc:SAML:1.0:assertion">
`       ...             `
`   `</saml:Assertion>


Although technically it is not a security token, a Timestamp element may
be inserted into a security header to ensure message's freshness. See
the further reading section for a design pattern on this.

### Referencing message parts

In order to retrieve security tokens, passed in the message, or to
identify signed and encrypted message parts, the core specification
adopts usage of a special attribute, wsu:Id. The only requirement on
this attribute is that the values of such IDs should be unique within
the scope of XML document where they are defined. Its application has a
significant advantage for the intermediate processors, as it does not
require understanding of the message's XML Schema. Unfortunately, XML
Signature and Encryption specifications do not allow for attribute
extensibility (i.e. they have closed schema), so, when trying to locate
signature or encryption elements, local IDs of the Signature and
Encryption elements must be considered first.

WSS core specification also defines a general mechanism for referencing
security tokens via SecurityTokenReference element. An example of such
element, referring to a SAML assertion in the same header, is provided
below:



`   `<wsse:SecurityTokenReference wsu:Id="aZG0sGbRpXLySzgM1X6aSjg22">
`     `<wsse:KeyIdentifier ValueType="http://docs.oasis-open.org/wss/2004/XX/oasis-2004XX-wss-saml-token-profile-1.0#SAMLAssertionID" wsu:Id="a2tv1Uz">
`        1106844369755`
`      `</wsse:KeyIdentifier>
`   `</wsse:SecurityTokenReference>


As this element was designed to refer to pretty much any possible token
type (including encryption keys, certificates, SAML assertions, etc)
both internal and external to the WSS Header, it is enormously
complicated. The specification recommends using two of its possible four
reference types: Direct References (by URI) and Key Identifiers (some
kind of token identifier). Profile documents (SAML, X.509 for instance)
provide additional extensions to these mechanisms to take advantage of
specific qualities of different token types.

## Communication Protection Mechanisms

As was already explained earlier (see 0), channel security, while
providing important services, is not a panacea, as it does not solve
many of the issues facing Web Service developers. WSS helps addressing
some of them at the SOAP message level, using the mechanisms described
in the sections below.

### Integrity

WSS specification makes use of the XML-dsig standard to ensure message
integrity, restricting its functionality in certain cases; for instance,
only explicitly referenced elements can be signed (i.e. no Embedding or
Embedded signature modes are allowed). Prior to signing an XML document,
a transformation is required to create its canonical representation,
taking into account the fact that XML documents can be represented in a
number of semantically equivalent ways. There are two main
transformations defined by the XML Digital Signature WG at W3C,
Inclusive and Exclusive Canonicalization Transforms (C14N and EXC-C14N),
which differ in the way namespace declarations are processed. The WSS
core specification specifically recommends using EXC-C14N, as it allows
copying signed XML content into other documents without invalidating the
signature.

In order to provide a uniform way of addressing signed tokens, WSS adds
a Security Token Reference (STR) Dereference Transform option, which is
comparable with dereferencing a pointer to an object of specific data
type in programming languages. Similarly, in addition to the XML
Signature-defined ways of addressing signing keys, WSS allows for
references to signing security tokens through the STR mechanism
(explained in 0), extended by token profiles to accommodate specific
token types. A typical signature example is shown in an earlier sample
in the section 0.

Typically, an XML signature is applied to secure elements such as SOAP
Body and the timestamp, as well as any user credentials, passed in the
request. There is an interesting twist when a particular element is both
signed and encrypted, since these operations may follow (even
repeatedly) in any order, and knowledge of their ordering is required
for signature verification. To address this issue, the WSS core
specification requires that each new element is pre-pended to the
security header, thus defining the "natural" order of operations. A
particularly nasty problem arises when there are several security
headers in a single SOAP message, using overlapping signature and
encryption blocks, as there is nothing in this case that would point to
the right order of operations.

### Confidentiality

For its confidentiality protection, WSS relies on yet another standard,
XML Encryption. Similarly to XML-dsig, this standard operates on
selected elements of the SOAP message, but it then replaces the
encrypted element's data with a <xenc:EncryptedData> sub-element
carrying the encrypted bytes. For encryption efficiency, the
specification recommends using a unique key, which is then encrypted by
the recipient's public key and pre-pended to the security header in a
<xenc:EncryptedKey> element. A SOAP message with encrypted body is shown
in the section 0.

### Freshness

SOAP messages' freshness is addressed via timestamp mechanism, each
security header may contain just one such element, which states, in UTC
time and using the UTC time format, creation and expiration moments of
the security header. It is important to realize that the timestamp is
applied to the WSS Header, not to the SOAP message itself, since the
latter may contain multiple security headers, each with a different
timestamp. There is an unresolved problem with this "single timestampt"
approach, since, once the timestamp is created and signed, it is
impossible to update it without breaking existing signatures, even in
case of a legitimate change in the WSS Header.

`      `<wsu:Timestamp wsu:Id="afc6fbe-a7d8-fbf3-9ac4-f884f435a9c1">
`   `<wsu:Created>`2005-01-27T16:46:10Z`</wsu:Created>
`   `<wsu:Expires>`2005-01-27T18:46:10Z`</wsu:Expires>
`  `</wsu:Timestamp>

If a timestamp is included in a message, it is typically signed to
prevent tampering and replay attacks. There is no mechanism foreseen to
address clock synchronization issue (which, as was already point out
earlier, is generally not an issue in modern day systems), this has to
be addressed out-of-band as far as the WSS mechanics is concerned. See
the further reading section for a design pattern addressing this issue.

## Access Control Mechanisms

When it comes to access control decisions, Web Services do not offer
specific protection mechanisms by themselves, they just have the means
to carry the tokens and data payloads in a secure manner between source
and destination SOAP endpoints.

For more complete description of access control tasks, please, refer to
other sections of this Development Guide.

### Identification

Identification represents a claim to have certain identity, which is
expressed by attaching certain information to the message. This can be a
username, an SAML assertion, a Kerberos ticket, or any other piece of
information, from which the service can infer who the caller claims to
be.

WSS represents a very good way to convey this information, as it defines
an extensible mechanism for attaching various token types to a message
(see 0). It is the receiver's job to extract the attached token and
figure out which identity it carries, or to reject the message if it can
find no acceptable token in it.

### Authentication

Authentication can come in two flavors: credentials verification or
token validation. The subtle difference between the two is that tokens
are issued after some kind of authentication has already happened prior
to the current invocation, and they usually contain user's identity
along with the proof of its integrity.

WSS offers support for a number of standard authentication protocols by
defining binding mechanism for transmitting protocol-specific tokens and
reliably linking them to the sender. However, the mechanics of proof
that the caller is who he claims to be is completely at the Web
Service's discretion. Whether it takes the supplied username and
password's hash and checks it against the backend user store, or
extracts subject name from the X.509 certificate used for signing the
message, verifies the certificate chain and looks up the user in its
store, at the moment, there are no requirements or standards which would
dictate that it should be done one way or another.

### Authorization

XACML may be used for expressing authorization rules, but its usage is
not Web Service-specific, it has much broader scope. So, whatever policy
or role-based authorization mechanism the host server already has in
place will most likely be utilized to protect the deployed Web Services
deployed as well.

Depending on the implementation, there may be several layers of
authorization involved at the server. For instance, JSRs 224 (JAX-RPC
2.0) and 109 (Implementing Enterprise Web Services), which define Java
binding for Web Services, specify implementing Web Services in J2EE
containers. This means that when a Web Service is accessed, there will
be a URL authorization check executed by the J2EE container, followed by
a check at the Web Service layer for the Web Service-specific resource.
Granularity of such checks is implementation-specific and is not
dictated by any standards. In the Windows universe it happens in a
similar fashion, since IIS is going to execute its access checks on the
incoming HTTP calls before they reach the ASP.NET runtime, where SOAP
message is going to be further decomposed and analyzed.

### Policy Agreement

Normally, Web Services communication is based on the endpoint's public
interface, defined in its WSDL file. This descriptor has sufficient
details to express SOAP binding requirements, but it does not define any
security parameters, leaving Web Service developers struggling to find
out-of-band mechanisms to determine the endpoint's security
requirements.

To make up for these shortcomings, WS-Policy specification was conceived
as a mechanism for expressing complex policy requirements and qualities,
sort of WSDL on steroids. Through the published policy SOAP endpoints
can advertise their security requirements, and their clients can apply
appropriate measures of message protection to construct the requests.
The general WS-Policy specification (actually comprised of three
separate documents) also has extensions for specific policy types, one
of them,  for security, WS-SecurityPolicy.

If the requestor does not possess the required tokens, it can try
obtaining them via trust mechanism, using WS-Trust-enabled services,
which are called to securely exchange various token types for the
requested identity.

![Figure 5. Using Trust service](Using_Trust_Service.gif
"Figure 5. Using Trust service")

Unfortunately, both WS-Policy and WS-Trust specifications have not been
submitted for standardization to public bodies, and their development is
progressing via private collaboration of several companies, although it
was opened up for other participants as well. As a positive factor,
there have been several interoperability events conducted for these
specifications, so the development process of these critical links in
the Web Services' security infrastructure is not a complete black box.

## Forming Web Service Chains

Many existing or planned implementations of SOA or B2B systems rely on
dynamic chains of Web Services for accomplishing various business
specific tasks, from taking the orders through manufacturing and up to
the distribution process.

![Figure 6: Service chain](Service_Chain.gif "Figure 6: Service chain")

This is in theory. In practice, there are a lot of obstacles hidden
among the way, and one of the major ones among them, security concerns
about publicly exposing processing functions to intra- or Internet-based
clients.

Here are just a few of the issues that hamper Web Services interaction,
incompatible authentication and authorization models for users, amount
of trust between services themselves and ways of establishing such
trust, maintaining secure connections, and synchronization of user
directories or otherwise exchanging users' attributes. These issues will
be briefly tackled in the following paragraphs.

### Incompatible user access control models

As explained earlier, in section 0, Web Services themselves do not
include separate extensions for access control, relying instead on the
existing security framework. What they do provide, however, are
mechanisms for discovering and describing security requirements of a
SOAP service (via WS-Policy), and for obtaining appropriate security
credentials via WS-Trust based services.

### Service trust

In order to establish mutual trust between client and service, they have
to satisfy each other's policy requirements. A simple and popular model
is mutual certificate authentication via SSL, but it is not scalable for
open service models, and supports only one authentication type. Services
that require more flexibility have to use pretty much the same access
control mechanisms as with users to establish each other's identities
prior to engaging in a conversation.

### Secure connections

Once trust is established it would be impractical to require its
confirmation on each interaction. Instead, a secure client-server link
is formed and maintained the entire time a client's session is active.
Again, the most popular mechanism today for maintaining such link is
SSL, but it is not a Web Service-specific mechanism, and it has a number
of shortcomings when applied to SOAP communication, as explained in 0.

### Synchronization of user directories

This is a very acute problem when dealing with cross-domain
applications, as users' population tends to change frequently among
different domains. So, how does a service in domain B decide whether it
is going to trust user's claim that he has been already authenticated in
domain A? There exist different aspects of this problem. First, a common
SSO mechanism, which implies that a user is known in both domains
(through synchronization, or by some other means), and authentication
tokens from one domain are acceptable in another. In Web Services world,
this would be accomplished by passing around a SAML or Kerberos token
for a user.

### Domain federation

Another aspect of the problem is when users are not shared across
domains, but merely the fact that a user with certain ID has
successfully authenticated in another domain, as would be the case with
several large corporations, which would like to form a partnership, but
would be reluctant to share customers' details. The decision to accept
this request is then based on the inter-domain procedures, establishing
special trust relationships and allowing for exchanging such opaque
tokens, which would be an example of Federation relationships. Of those
efforts, most notable example is Liberty Alliance project, which is now
being used as a basis for SAML 2.0 specifications. The work in this area
is still far from being completed, and most of the existing deployments
are nothing more than POC or internal pilot projects than to real
cross-companies deployments, although LA's website does list some case
studies of large-scale projects.

## Available Implementations

It is important to realize from the beginning that no security standard
by itself is going to provide security to the message exchanges, it is
the installed implementations, which will be assessing conformance of
the incoming SOAP messages to the applicable standards, as well as
appropriately securing the outgoing messages.

### .NET Web Service Extensions

Since new standards are being developed at a rather quick pace, .NET
platform is not trying to catch up immediately, but uses Web Service
Extensions (WSE) instead. WSE, currently at the version 2.0, adds
development and runtime support for the latest Web Service security
standards to the platform and development tools, even while they are
still "work in progress". Once standards mature, their support is
incorporated into new releases of the .NET platform, which is what is
going to happen when .NET 2.0 finally sees the world. The next release
of WSE, 3.0, is going to coincide with VS.2005 release and will take
advantages of the latest innovations of .NET 2.0 platform in messaging
and Web Application areas.

Considering that Microsoft is one of the most active players in the Web
Service security area and recognizing its influence in the industry, its
WSE implementation is probably one of the most complete and up to date,
and it is strongly advisable to run at least a quick interoperability
check with WSE-secured .NET Web Service clients. If you have a
Java-based Web Service, and the interoperability is a requirement (which
is usually the case), in addition to the questions of security testing
one needs to keep in mind the basic interoperability between Java and
.NET Web Service data structures.

This is especially important since current versions of .NET Web Service
tools frequently do not cleanly handle WS-Security's and related XML
schemas as published by OASIS, so some creativity on the part of a Web
Service designer is needed. That said, WSE package itself contains very
rich and well-structured functionality, which can be utilized both with
ASP.NET-based and standalone Web Service clients to check incoming SOAP
messages and secure outgoing ones at the infrastructure level, relieving
Web Service programmers from knowing these details. Among other things,
WSE 2.0 supports the most recent set of WS-Policy and WS-Security
profiles, providing for basic message security and WS-Trust with
WS-SecureConversation. Those are needed for establishing secure
exchanges and sessions - similar to what SSL does at the transport
level, but applied to message-based communication.

### Java toolkits

Most of the publicly available Java toolkits work at the level of XML
security, i.e. XML-dsig and XML-enc, such as IBM's XML Security Suite
and Apache's XML Security Java project. Java's JSR 105 and JSR 106
(still not finalized) define Java bindings for signatures and
encryption, which will allow plugging the implementations as JCA
providers once work on those JSRs is completed.

Moving one level up, to address Web Services themselves, the picture
becomes muddier, at the moment, there are many implementations in
various stages of incompleteness. For instance, Apache is currently
working on the WSS4J project, which is moving rather slowly, and there
is commercial software package from Phaos (now owned by Oracle), which
suffers from a lot of implementation problems.

A popular choice among Web Service developers today is Sun's JWSDP,
which includes support for Web Service security. However, its support
for Web Service security specifications in the version 1.5 is only
limited to implementation of the core WSS standard with username and
X.509 certificate profiles. Security features are implemented as part of
the JAX-RPC framework and configuration-driven, which allows for clean
separation from the Web Service's implementation.

### Hardware, software systems

This category includes complete systems, rather than toolkits or
frameworks. On one hand, they usually provide rich functionality right
off the shelf, on the other hand, its usage model is rigidly constrained
by the solution's architecture and implementation. This is in contrast
to the toolkits, which do not provide any services by themselves, but
handing system developers necessary tools to include the desired Web
Service security features in their products' or to shoot themselves in
the foot by applying them inappropriately.

These systems can be used at the infrastructure layer to verify incoming
messages against the effective policy, check signatures, tokens, etc,
before passing them on to the target Web Service. When applied to the
outgoing SOAP messages, they act as a proxy, now altering the messages
to decorate with the required security elements, sign and/or encrypt
them.

Software systems are characterized by significant configuration
flexibility, but comparatively slow processing. On the bright side, they
often provide high level of integration with the existing enterprise
infrastructure, relying on the back-end user and policy stores to look
at the credentials, extracted from the WSS header, from the broader
perspective. An example of such service is TransactionMinder from the
former Netegrity, a Policy Enforcement Point for Web Services behind it,
layered on top of the Policy Server, which makes policy decisions by
checking the extracted credentials against the configured stores and
policies.

For hardware systems, performance is the key, they have already broken
gigabyte processing threshold, and allow for real-time processing of
huge documents, decorated according to the variety of the latest Web
Service security standards, not only WSS. The usage simplicity is
another attractive point of those systems - in the most trivial cases,
the hardware box may be literally dropped in, plugged, and be used right
away. These qualities come with a price, however, this performance and
simplicity can be achieved as long as the user stays within the
pre-configured confines of the hardware box. The moment he tries to
integrate with the back-end stores via callbacks (for those solutions
that have this capability, since not all of them do), most of the
advantages are lost. As an example of such hardware device, Layer 7
Technologies provides a scalable SecureSpan Networking Gateway, which
acts both as the inbound firewall and the outbound proxy to handle XML
traffic in real time.

## Problems

As is probably clear from the previous sections, Web Services are still
experiencing a lot of turbulence, and it will take a while before they
can really catch on. Here is a brief look at what problems surround
currently existing security standards and their implementations.

### Immaturity of the standards

Most of the standards are either very recent (couple years old at most),
or still being developed. Although standards development is done in
committees, which, presumably, reduces risks by going through an
exhaustive reviewing and commenting process, some error scenarios still
slip in periodically, as no theory can possibly match the testing
resulting from pounding by thousands of developers working in the real
field.

Additionally, it does not help that for political reasons some of these
standards are withheld from public process, which is the case with many
standards from the WSA arena (see 0), or that some of the efforts are
duplicated, as was the case with LA and WS-Federation specifications.

### Performance

XML parsing is a slow task, which is an accepted reality, and SOAP
processing slows it down even more. Now, with expensive cryptographic
and textual conversion operations thrown into the mix, these tasks
become a performance bottleneck, even with the latest crypto- and
XML-processing hardware solutions offered today. All of the products
currently on the market are facing this issue, and they are trying to
resolve it with varying degrees of success.

Hardware solutions, while substantially (by orders of magnitude)
improving the performance, cannot always be used as an optimal solution,
as they cannot be easily integrated with the already existing back-end
software infrastructure, at least, not without making performance
sacrifices. Another consideration whether hardware-based systems are the
right solution, they are usually highly specialized in what they are
doing, while modern Application Servers and security frameworks can
usually offer a much greater variety of protection mechanisms,
protecting not only Web Services, but also other deployed applications
in a uniform and consistent way.

### Complexity and interoperability

As could be deduced from the previous sections, Web Service security
standards are fairly complex, and have very steep learning curve
associated with them. Most of the current products, dealing with Web
Service security, suffer from very mediocre usability due to the
complexity of the underlying infrastructure. Configuring all different
policies, identities, keys, and protocols takes a lot of time and good
understanding of the involved technologies, as most of the times errors
that end users are seeing have very cryptic and misleading descriptions.

In order to help administrators and reduce security risks from service
misconfigurations, many companies develop policy templates, which group
together best practices for protecting incoming and outgoing SOAP
messages. Unfortunately, this work is not currently on the radar of any
of the standard's bodies, so it appears unlikely that such templates
will be released for public use any time soon. Closest to this effort
may be WS-I's Basic Security Profile (BSP), which tries to define the
rules for better interoperability among Web Services, using a subset of
common security features from various security standards like WSS.
However, this work is not aimed at supplying the administrators with
ready for deployment security templates matching the most popular
business use cases, but rather at establishing the least common
denominator.

### Key management

Key management usually lies at the foundation of any other security
activity, as most protection mechanisms rely on cryptographic keys one
way or another. While Web Services have XKMS protocol for key
distribution, local key management still presents a huge challenge in
most cases, since PKI mechanism has a lot of well-documented deployment
and usability issues. Those systems that opt to use homegrown mechanisms
for key management run significant risks in many cases, since questions
of storing, updating, and recovering secret and private keys more often
than not are not adequately addressed in such solutions.

## Further Reading

  - SearchSOA, SOA needs practical operational governance, Toufic Boubez

<u><http://searchsoa.techtarget.com/news/interview/0,289202,sid26_gci1288649,00.html?track=NL-110&ad=618937&asrc=EM_NLN_2827289&uid=4724698></u>

  - Whitepaper: Securing XML Web Services: XML Firewalls and XML VPNs

<u><http://forms.layer7tech.com/content/Download?docid=1114&docname=Securing%20XML%20Web%20Services:%20SSL,%20XML%20Firewalling,%20and%20Beyond></u>

  - eBizQ, The Challenges of SOA Security, Peter Schooff

<u><http://www.ebizq.net/blogs/news_security/2008/01/the_complexity_of_soa_security.php></u>

  - Piliptchouk, D., WS-Security in the Enterprise, O'Reilly ONJava

<u><http://www.onjava.com/pub/a/onjava/2005/02/09/wssecurity.html></u>

<u><http://www.onjava.com/pub/a/onjava/2005/03/30/wssecurity2.html></u>

  - WS-Security OASIS site

<u><http://www.oasis-open.org/committees/tc_home.php?wg_abbrev=wss></u>

  - Microsoft, *What's new with WSE 3.0*

<u><http://msdn.microsoft.com/webservices/webservices/building/wse/default.aspx?pull=/library/en-us/dnwse/html/newwse3.asp></u>

  - Eoin Keary, Preventing DOS attacks on web services

<u><https://www.threatsandcountermeasures.com/wiki/default.aspx/ThreatsAndCountermeasuresCommunityKB.PreventingDOSAttacksOnWebServices></u>

## Reference

[Development Guide Table of
Contents](Guide_Table_of_Contents "wikilink")

[broken link](Category:FIXME "wikilink")
[Category:OWASP_Guide_Project](Category:OWASP_Guide_Project "wikilink")
[Category:Web_Services](Category:Web_Services "wikilink")
[Category:OWASP .NET Project](Category:OWASP_.NET_Project "wikilink")