## Overview

This column is about securing systems that are implemented in the Web
services paradigm. The scope of this topic is huge and the issues are
complex. Further complicating the problem is the fact that we are still
very, very early in the life of the paradigm and most of the detail has
yet to be worked out. However, since this is an evolutionary paradigm,
even if we don't yet have all the specifics, we do know what the general
classes of problems are . . . and where to look for them. So for now, in
this column, we will be looking at the kinds of controls that will need
to be implemented in order to secure systems that are built around Web
services. We will focus on issues at the macro level here; there are
some problems that exist independently of the choice of Web server,
application server, authentication mechanism, etc. These issues, if not
addressed, will result in exposed systems, no matter how well the WS\*
standards are implemented, whether secure programming techniques were
employed or how well the rest of the system is done.

## What is a Web service?

Whenever one encounters an article or paper on Web services, somewhere
early in the document, the author defines the term. Most begin with a
disclaimer to the effect that there are as many descriptions as there
are describers. I certainly do not want to be the one to break with
tradition. However, before we get to that, it is important to have a
small sample of what others have to say.

**BEA Systems** – Characteristics of Web services will be:

:\* "Loose coupling between the public contract and the underlying
implementation

:\* Asynchronous interaction

:\* Business-level documents as the unit of communication." \[1\]

**CIO Magazine** – "Web services is an amorphous blob of business apps,
and different players define it differently. Ultimately, it can be
described as any application delivered over the Internet and accessed by
any device, from Pcs to mobile phones. What Web services can offer is a
set of shared protocols and standards that permit systems to share data
and services without requiring humans to broker the conversation. The
result promises to be 'on-the-fly' links between the online processes of
different companies." \[2\]

**HP** – "Web Services proposes a service-oriented paradigm for
computing in which distributed, loosely coupled services collaboratively
provide business services and can be accessed by the Internet and by end
customers (possibly consumers)." \[3\]

**IBM** – "Web services are software components that are developed using
specific technologies from three primary technology categories:

:\* An XML-based description format (for example, WSDL)

:\* An application messaging proctocol (for example, SOAP)

:\* A collection or transport protocol (for example, HTTP)" \[4\]

**Microsoft** – "XML Web services are built on XML, SOAP, WSDL and UDDI
specifications. These constitute a set of baseline specifications that
provide the foundation for application integration and aggregation."
\[5\]

**Sun Microsystems** – "The foundation of Web services is XML messaging
over standard Web protocols such as HTTP." \[6\]

**World Wide Web Consortium** – "A Web service is a software system
designed to support interoperable machine-to-machine interaction over a
network. It has an interface described in a machine-processable format
(specifically WSDL). Other systems interact with the Web service in a
manner prescribed by its description using SOAP-messages, typically
conveyed using HTTP with an XML serialization in conjunction with other
Web-related standards." \[7\]

## Web Services from the Information Security Perspective

Of course, the way one talks about Web services depends upon one's
focus. So lets take a look at some of the characteristics of Web
services that have implications for Information Security practitioners.

:\# Web services is a set of services that provide a means by which
disparate systems can work with each other.

:\# Web services provide for a loose coupling of systems – i.e. the
endpoint systems have no direct knowledge of each other nor any
relationship (formal or informal) with each other.

:\# The endpoint systems were not originally designed as pieces of an
integrated system nor were they originally designed to participate in
the provision of a service to "strangers." (More on what this means
later).

:\# Web services use a stateless, asynchronous messaging mechanism.

:\# Web services transactions can span significant amounts of space and
time and multiple machines.

:\# The system architecture is one which:

::\* is multi-layer

::\* is distributed

::\* is implemented using a services-based software architecture

::\* allows remote procedure calls (RPCs) using Web Services Definition
Language (WSDL) as the Interface Definition Language (IDL) (to systems
that were not originally designed to provide that service).

Basically, Web services allows us to create new systems by connecting
existing systems from (potentially multiple) different security and
trust domains into one system . . . over the Internet. Gives me a
headache just to think about it . . .

## Some Security Implications of This Perspective

Web services systems offer all of the security problems inherent in the
distributed computing environment, EAI and Web applications all rolled
up in one package. There is not enough time in this column to examine
all of them. We will introduce a few here with the intention of
exploring them more fully in subsequent columns.

### Emergent Risks

Usually, some of the requirements that determine the design,
construction, implementation and operation of systems are intended to
prevent, detect or mitigate the (information security) threats and risks
that the system is expected to encounter during its lifetime. These
known and anticipated threats comprise the design threat model and drive
the design control assumptions and the design trust assumptions of the
system. The system design and selection of controls, then, are based on
the threats and risks that were known or anticipated at the time the
system was designed and implemented. (For this discussion, the notion of
controls includes business and technical processes and procedures as
well as "the usual" physical access controls, firewalls, encryption,
etc.). When one inserts Web services between endpoint systems that were
not designed with Web services in mind, one violates the design threat
models, design control assumptions and the design trust assumptions made
by the endpoint systems. This has the effect of introducing threats for
which there are no controls in the design control set. One has just
introduced a new set of threats and risks. These emergent risks and
threats imply:

:\* New risk models

:\* New trust models

:\* New business processes

:\* New technical processes

:\* New operations processes

This implies the need for a thorough reassessment of the threats and
vulnerabilities to which existing systems will be exposed when they are
incorporated into a system that is mediated by Web services.

### End-to-end Controls

If done "by the book," an organization's selection of InfoSec controls
is based on risk assessments and is a compromise between the cost of
protecting its assets and their value. Introducing Web services into a
system's environment introduces a set of risks for which there must be
controls implemented. Some of these controls should allow organizations
to manage end-to-end:

Privacy

::\* On the communication channel

::\* Of confidential information

Audit trails to determine

::\* Who initiated the transaction

::\* When did it originate

::\* From where did it originate

::\* When did it pass through what process

::\* What transformations if any were done on the data while it was in
transit

Integrity

::\* Of the communication channel

::\* Of the data in flight

::\* Of the semantic and referential integrity of the data

::\* Of the transaction (some of which can be very long-running)

::\* Of the session

::\* Of the network and the systems

Non-repudiation

::\* Of origin – the sender cannot falsely deny having been the
originator of the message

::\* Of receipt – the recipient cannot falsely deny having received the
message

The Four Dimensions of Trust

::\* Identification – establish the identity of the principals
participating in the transaction

::\* Authentication – establish that the principals truly are who they
represent themselves to be

::\* Authorization – determine what functions the authenticated
principal has the rights to peform on what objects

::\* Trust Management – ". . . formulating security policies and
security credentials, determining whether particular sets of credentials
satisfy the relevant policies, and deferring trust to third parties."
\[8\]

## Interconnection of Systems from Different Trust Domains

A major challenge for the design of systems that incorporate Web
services is that the system must securely transport data and mediate
between systems that exist in completely different trust domains. A
major challenge for any given client (endpoint) of Web services is that
it has to do business with other endpoints that are outside its own
trust domain and, in the absence of certain controls, can make no
assumptions about the provenance, integrity or validity of data that it
receives from the Web service. Because of this, trust management will
become a major source of risk and have a greater impact on business and
technical processes than all other aspects of designing, implementing
and managing Web services and their clients. It is hard to overemphasize
the importance of understanding the nature of this "impedance mismatch"
and allowing for it in the design of Web services systems.

### Some Implications for the Organization's Risk Management Process and System Development Life Cycle

With the introduction of Web services comes a change in the way legacy
systems interact with their environment. This change has implications
for the organization's risk profile and risk management process. It also
impacts the system development process and the SDLC. A few of the areas
affected are described below. A subsequent column will cover the topic
in much more detail.

:\# System security engineering is especially important when building
systems that use Web services because "both sides of the interface" are
affected.

:\# A thorough risk assessment at the beginning of Web services projects
is important in order to understand how the introduction of Web services
will affect the risk, trust and control assumptions of the systems with
which the Web services will interface.

:\# Having a formal assurance (Certification and Accreditation) process
in place is very important. It is imperative that the business owners
who are accountable for the performance of the system understand the
risks and exposures that Web services create and have a means by which
they can be confident that the controls that have been chosen will do
the job they are intended to do.

:\# Clearly defining system ownership and the accountable party is
particularly important in this case. It is difficult because of the
nature of this kind of system, but that is why it is so important. With
so many players involved, it is crucial to successfully managing the
risks associated with these systems that clear ownership and
accountability be established on a system-by-system basis.

To this point, we have not talked much about Web services, per se. From
a high-level software architecture perspective, Web services systems are
not any different from any other distributed, multi-tier, services-based
architecture. In the simplest case of a services-based architecture,
there are three "layers." There is a presentation layer, a layer that
provides business processing and data access services to the
presentation layer, and a data management/storage layer. So far, the
discussion has been around issues that arise because of the nature of
the architecture . . . that it is distributed, multi-tier and
services-based. There are, though, a set of security issues that are
specific to the services layer. Anyone who has built software systems
using the DCE (or DCOM/MSDCE), CORBA or SESAME understands them.
Naturally, the specific details differ because of the diferences in the
environments, but the general problems are the same. For instance, the
basic security requirements of authentication, integrity and
confidentiality and the need for registration services and naming
services exist for each of the environments; and each environment
provides a set of security services. Such is the case of Web services.
However, there are some aspects of the Web services environment that
make meeting these requirements quite challenging . . . Following is a
current snapshot of the "State of the Web Services Security Union."

### Emerging Standards for Securing Web Services

WS-Security – Web Services Security – An extension of SOAP that provides
privacy and integrity mechanisms for parts of SOAP messages. (September,
2002)

SAML – Security Assertion Markup Language – An XML-based framework for
exchanging security information. (May, 2002)

XACML – eXtensible Access Control Markup Language – A language for
expressing information security policy. (February, 2003)

XKMS – (XML-KISS and XML-KRSS) – Provide access to PKI key management
functions. (March 2001)

XMLEnc – Defines a mechanism for encrypting part(s) of an XML document
(with potentially different keys). (December, 2002)

WS-Policy – Describes the capabilities and constraints of the security
(and other business) policies on intermediaries and endpoints. (May,
2003)

### WS Security Specifications in Process

WS-Trust – Will describe a framework for trust models that enables Web
services to securly interoperate.

WS-Privacy – Will describe a model for how Web services and requesters
state privacy preferences and organizational privacy practice
statements.

WS-SecureConversation – Will describe how to manage and authenticate
message exchanges between parties including security context exchange
and establishing and deriving session keys.

WS-Federation – Will describe how to manage and broker the trust
relationships in a heterogeneous federated environment including support
for federated identities.

WS-Authorization – Will describe how to manage authorization data and
authorization policies.

Much work has been done, but the hard part is yet to come.

### Trust Management Revisited

The general problems for trust management are not new. There is a
healthy literature on the topic and there exist several subsystems that
provide various trust management mechanisms. The problem is that the Web
services paradigm is enough of a shift that it serves to broaden the
scope of "The Trust Management Problem" significantly. It is the
decoupling of the endpoints that creates the problems. The challenge for
designers, implementers and risk managers of systems that are built
around Web services is that this introduces a whole universe of issues
and problems that do not exist in tightly-coupled systems, and most have
no experience with trust management issues that arise out of
loosely-coupled systems. Complicating the problem is that most of the
standards work that addresses trust management issues is still in
committee.

In the next few columns, we will go into more detail on the implications
described here. None of what we will cover will be rocket science, and I
do not expect that it will be earthshaking news to anyone. After all,
this is a self-selecting audience, and I expect that the anyone who
would be interested in this topic would already be thinking about this.
You may already have tried to get the message across to
$unwilling_to_hear_anything_manager. For some reason, it is easier
to get those folks' attention if the message comes from someone else. My
goal in writing this column is to provide those who need it with a
message that they can take to $unwilling_to_hear_anything_manager
and say: "Look, here is someone else who is saying what I've been saying
all along."

## References

\[1\] BEA Weblogic Workshop: The Future of Web Services – Here, Today,
(note: the following URL is broken)
<http://www.bea.com/products/weblogic/wl_workshop_tech_wp.pdf>

\[2\] Emerging Technology – Investing in Web Services,
<http://www.cio.com/archive/091502/et_pundit.html>

\[3\] Web services concepts – a technical overview,
<http://www.hpmiddleware.com/downloads/pdf/web_services_tech_overview.pdf>

\[4\] Best practices for Web services: Back to the basics, Part 1,
<http://www-106.ibm.com/developerworks/library/ws-best1>

\[5\] Web Services Specifications,
<http://msdn.microsoft.com/library/default.asp?url=/library/en-us/dnglobspec/html/wsspecsover.asp>

\[6\] Sun ONE and Web Services,
<http://www.sun.com/executives/sunjournal/v5n2/feature6.html>

\[7\] Web Services Architecture, <http://www.w3.org/TR/ws-arch/wsa.pdf>

\[8\] Decentralized Trust Management,
<http://www.crypto.com/papers/policymaker.pdf>

[Category:OWASP Columns](Category:OWASP_Columns "wikilink")
[Category:Web Services](Category:Web_Services "wikilink")