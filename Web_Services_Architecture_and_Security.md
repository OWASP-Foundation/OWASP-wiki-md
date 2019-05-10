## Overview

Defense in depth is an information security best practice. When it comes
to Web services, defense in depth implies a layered defense and securing
the structure and function of the system wherever it is possible to do
so. In this article, we will take a look at the emerging Web services
architecture and take a first pass at identifying some of the major soft
spots. When I began writing this column, I had intended to cover both
the architecture and the defenses, but after working on it for a while,
I realized that it was way more than too much for one column. So first,
we'll try to understand what has to be defended. In subsequent articles,
we will figure out what defenses to deploy. This article will highlight
the components of the architecture that can be vulnerable to attack and
around which controls should be placed.

As with everything else in the Web services universe, the architecture
is still being refined. Currently, work on the Web Services Architecture
is being done by the Web Services Architecture Working Group of the
World Wide Web Consortium (http://www.w3.org/2002/ws/arch). We will use
the Working Draft of 8 August 2003 as the basis for discussion. This is
the most recent public release of the document and it can be found at
<http://www.w3.org/TR/ws-arch>. Though it is still a working draft, it
is complete enough to give a feel for "the big picture" and provide us
with enough information to begin planning. To be sure, as we iterate
through the process, the spec will evolve. That is to be expected. I do
believe, though, that the core concepts and functionality are pretty
well laid out by now, and that we have enough to begin to understand the
major security challenges. These are some of the things about which we
need to be aware as we begin to think about Web services security
architectures.

## The Web Services Architecture

There is going to be enough to cover in this article without it being a
primer on the WSA spec. Therefore, it would be very helpful to be
familiar with the spec or to have it handy when reading this article. I
will, however, try to provide adequate background on the topics that we
discuss. I would also like to note here that, unless otherwise
specified, all of the quotations and figures//images that appear here
are taken directly from the WSA document. I saw no sense in trying to
reinvent the wheel and have a product that was worse than the original .
. . :-) The editors of the Web Services Architecture have put in a
tremendous amount of work and done a great job to this point.

*"The WSA provides a model and a context for understanding Web services
and the technologies that comprise the WSA. The WSA promotes
interoperability through the definition of compatible protocols. The
architecture does not attempt to specify how Web services are
implemented, and imposes no restriction on how services might be
combined. The WSA describes both the minimal characteristics that are
common to all Web services, and a number of characteristics that are
needed by many, but not all, Web services."* This fits our need
perfectly for now. What we want right now is an idea of the kinds of
things we need to look out for and where to look for them. The specifics
will vary depending upon the implementation.

## Service Oriented Architectures and Distributed Systems

Early in the document, the editors note that the WSA is a Service
Oriented Architecture (SOA) and that an SOA is a type of distributed
system. They go on to say: *"A distributed system consists of discrete
software agents that must work together to implement some intended
functionality. Furthermore, the agents in a distributed system do not
operate in the same processing environment, so they must communicate by
hardware/software protocol stacks that are intrinsically less reliable
than direct code invocation and shared memory. This has important
architectural implications because distributed systems require that
developers (of infrastructure and applications) consider the
unpredictable latency of remote access, and take into account issues of
concurrency and the possibility of partial failure."* More importantly,
from our perspective, this also has critically important security
implications. We, as an industry, have been doing distributed computing
for a long time and have learned many (sometimes painful) lessons about
securing distributed systems. See, for instance, \[DCE\], \[CORBA1\],
\[CORBA2\], \[KeyNote\], and \[SESAME\]. These are brief descriptions of
a ***very*** small amount of the work that has been done in the
distributed systems security space. Web services have all of the
security problems that those systems were designed to solve, but in
spades. If Web services system designers do not understand those
services and protocols and what they do, they cannot possibly design
secure Web services systems. We will see why Web services systems are so
much more vulnerable to these problems later on. I cannot emphasize
enough, though, the importance of understanding the work that has been
done in securing distributed systems. Not understanding that equals not
understanding what is necessary to secure Web services.

## Complexity Is the Enemy of Security . . .

So goes the mantra. *"We will all be busier than ever . . ."* So goes
the
[lament](http://www.mail-archive.com/full-disclosure@lists.netsys.com/msg11122.html).
A couple of years ago, the [following
observation](https://honor.trusecure.com/pipermail/firewall-wizards/2001-February/010238.html)
was made on the Firewall Wizards mailing list: "Recent evolution has
excerbated complexity, opening backdoor opportunities." The message here
is really simple. Every new dimension that is added to a system also
adds an "attack surface" to the system. Lets take a look at the Web
Service Technologies stack diagram from the "attack surface"
perspective. This diagram is Figure 3 in the WSA document.

<center>

![Image:WSA_STACK.jpg](WSA_STACK.jpg "Image:WSA_STACK.jpg")

</center>

Complex, huh? I will not spend much time on this diagram right now. Each
of the blocks/layers in the diagram presents an attack surface. We will
spend more time on them later in this and subsequent articles. For now,
though, to appreciate the scope of the challenge faced by security
practitioners and designers and builders of Web services, I offer this
challenge: Pick one of the functions named in the diagram, say the
Discovery process, and think about how many ways that can be attacked.
Then look at the diagram again. That was just the tip of the iceberg.
Complexity ***is*** the enemy of security.

## The Architectural Models

The editors have partitioned the architecture into five dimensions or
models. Each model addresses a global aspect of the overall
architecture. These models go a long way in breaking the overall
architecture into managable chunks. To me, this is what gives the WSA
document its value. The diagram below shows the models and their
relationships with each other, along with the key concept of that model.

<center>

![Image:Meta.jpg](Meta.jpg "Image:Meta.jpg")

</center>

The five models are:

:\#The Policy Model - focuses on policies associated with the
architecture. The main construct of the Policy Model is the policy.
Policies are the essentially the rules of the game.

:\#The Service Oriented Model - focuses on the functionality offered by
the system. The primary construct of the Services Model is the
Action/Function/Service.

:\#The Resource Oriented Model - focuses on the resources necessary for
and avaliable to the system. The primary construct associated with this
model is the Resource.

:\#The Message Oriented Model - focuses on messages, message structure,
message format, etc. The primary construct of the Message Oriented Model
is the message.

:\#The Management Model - focuses on the management of Web services. The
primary construct of the Management Model is the managed resource.

Each of the models will be addressed in more detail below.

## The Policy Model

The following comments are taken from the introduction of the policy
model:

''"The Policy Model focuses on those aspects of the architecture that
relate to policies and, by extension, security and quality of service.

"Security is fundamentally about constraints; about constraints on the
behavior on action and on accessing resources. Similarly, quality of
service is also about constraints on service. In the PM, these
constraints are modeled around the core concept of policy; and the
relationships with other elements of the architecture. Thus the PM is a
framework in which security can be realized." (In this case, I think the
authors were referring primarily to application-level security).

"However, there are many other kinds of constraints, and policies, that
are relevant to Web services; including various application-level
constraints."''

The figure below illustrates the concepts and relationships in the
Policy Model. In this article, we will only focus on the parts of the
model that have implications for security architects and planners . . .

<center>

![Image:Policy.jpg](Policy.jpg "Image:Policy.jpg")

</center>

There is much of the Policy Model that is of interest to security
practitioners from several perspectives. In the first column, I very
briefly mentioned "The Trust Management Problem." Well, ***this*** is
one of the places where we try to manage it.

From the enterprise security perspective, policy is part of the
enforcement component of the organization's risk management process. The
figure below, derived from
[GAO/AIMD-98-68](http://www.gao.gov/special.pubs/ai9868.pdf), shows the
risk management cycle and the highlighted box shows where the Policy
Model fits within it.

<center>

![Image:Risk_management_cycle.jpg](Risk_management_cycle.jpg
"Image:Risk_management_cycle.jpg")

</center>

The policy statement is a position statement. It defines the
organization's operating rules of engagement. Policy is the source of
authority for the system security engineering process and is/should be
part of the input into all phases of the system development life cycle.
It is the "requirements specification" which drives the design and
implementation of the access control mechanisms and the constraints that
the system protection mechanisms must place on users.

The Policy Model defines several concepts that should be part of the
system security architecture. They are of interest at two levels - they
are critical parts of the architecture, but they are also attack points
. . . The concepts that are of immediate interest from a security
perspective are:

:\****Policy*** - *"A policy is a constraint on the behavior of
agents."*

:\****Obligation*** - *"An obligation is a kind of policy that relates
to the required actions and states of an agent and/or resource."*

:\****Permission*** - *"A permission is a mechanism deployed on behalf
of an owner that enforces permission policies."*

:\****Permission guard*** - *"A permission guard is a mechanism deployed
on behalf of an owner that enforces permission policies."*

:\****Audit guard*** - *"An audit guard is a mechanism deployed on
behalf of an owner that monitors actions and agents to verify the
satisfaction of obligations."*

**Policy** is the central concept. It is the formal articulation of the
constraints that provide the adequate level of protection given the
outcome of the risk assessment. It is *"a machine processable
description of some constraint on the behavior of agents as they perform
actions, access resources."* **Machine processable** is a key condition
for Web services systems. This implies a considerable amount of work in
accurately translating policy statements that come out of the risk
management process into a set of machine processable constraint
definitions. It also implies a (software) subsystem that manages
identification, authentication, authorization, integrity and
non-repudiation. (This subsystem would be the realization of the policy,
permission and audit guards). There is a significant amount of research,
a large literature and several systems that do most of what needs to be
done. There is still a considerable amount of work to be done
integrating them into the Web services environment. For many system
designers and developers, this is an area that is completely new. The
next column will focus on this. There is **much** to talk about.

**Obligation** is one type of policy. It is important because it
identifies an action that an agent is required to perform or a state
that a service is required to maintain. Obligations can be
security-related. An obligation might be as simple as the requirement
that the application throw an exception when someone has unsuccessfully
tried to log in more than a defined number of times.

One of the interesting attributes of an obligation is that it cannot be
proactively enforced. This implies the necessity of an audit mechanism.
Thus the necessity for the **audit guard**.

From the security perspective, there are some things to be concerned
about when it comes to obligations. It goes without saying that the
integrity of the policy data store is of paramount importance. Another
critical aspect is the "auditability" of the obligation and the
integrity of the audit process. If the definition of the obligation is
vague, it will be very hard for the audit process to detect when (or if)
the obligation has been met or when the system has failed to meet the
obligation. Therefore it is important that the definition of the
obligation be as clear as possible and, therefore, that the conditions
for success or failure in meeting the obligation be as easy as possible
to detect.

*"**Permission** is a kind of policy that relates to the allowed actions
and states of an agent and/or resource."* Basically, these are the
access control rules. They are all about system security and determining
the constraints under which agents can be given access to system
function. There is much more to be said about permissions. That will
happen in the next column when we talk more about policy. It is hard to
talk about one in the absence of the other.

*"A **permission guard** is a mechanism deployed on behalf of an owner
that enforces permission policies."* Exactly what one would think it is.
Sounds simple. It is anything but. The concept is quite straightforward.
The implementation is not. It never has been, but with the advent of the
Web and Web services it's become devilishly hard to do "The Right Way
(TM)." We will get into this more in the next column also.

An ***audit guard*** is to obligations what the permission guard is to
permissions. The audit guard "monitors actions and agents to verify the
satisfaction of obligations." As with permissions guards, the concept is
simple and the realization anything but. They are very important,
though, from the security perspective. Not only are they an enforcement
mechanism, they are also the primary source of information for
forensics. Audit mechanisms have traditionally been one of the first
targets of invasive users or malware. Protecting the mechanisms and the
data they generate should be primary design and implementation goals.

This will do it for the Policy Model. Next we will take a look at the
Service Oriented Model.

## The Service Oriented Model

*"The Service Oriented Model focuses on those aspects of the
architecture that relate to Service and action.*

*"The primary purpose of the SOM is to explicate the relationships
between and agent and action."*

<center>

![Image:SOM.jpg](SOM.jpg "Image:SOM.jpg")

</center>

The diagram above illustrates the major concepts and relationships of
the SOM. From the information security perspective, the primary concern
is preserving the integrity of the service. This implies preserving the
integrity of the components of the service. So for us, the items of
interest in the Service Oriented Model are:

:\****Action** - "An action, for the purposes of this architecture, is
any action that may be performed by an agent as a result of receiving a
message, or results in sending a message or other observable state."*

:\****Agent** - "An agent is a program acting on behalf of another
person, entity, or process."*

:\****Choreography** - "A choreography defines the sequence and
conditions under which multiple cooperating independent Web services
exchange information in order to achieve some useful function."*

:\****Identifier** - The exact definition of identifier has not been
hammered out yet.*

:\****Service description** - "A service description is a set of
documents that describe the interface to and semantics of a service."*

:\****Service end point** - "A service end point is a network location
at which an implementation of a service interface is made available."
(The service end point is discussed in the document but does not show up
in the current diagram of the model).*

:\****Service interface** - "A service interface is the abstract
boundary that a service exposes."*

:\*'**'Service operation** - "A service operation is an abstract
grouping of messages that a service sends and receives in order to
perform a particular task. '' If we can preserve the integrity of these
items, we can preserve the integrity of the service. It is not practical
to try to go into detail about each of these and talk about how to
secure them because of the variety of ways in which they could be
implemented. The time to define the controls that need to be put in
place to secure them is during the system design process when much more
is known about exactly how they will be physically implemented. The goal
in this article was to identify them as areas of concern and urge that
they be given attention throughout the system life cycle.

## The Resource Oriented Model

Whereas the SOM was intended to model Web services from the
functionality perspective, the Resource Oriented Model *"focuses on
those aspects of the architecture that relate to resources and the
service model associated with manipulating resources. It builds on the
Service Oriented Model, primarily by developing the service model
associated with resources and common actions associated with
manipulating them."* This is an important model. A major function it
serves is to focus attention on the fact that the architecture
***assumes*** that resources are going to be manipulated and defines the
allowable maniuplations. From the security planning perspective, this
equates to shining bright lights on parts of the system that are going
to be attacked. A diagram of the ROM is below.

<center>

![Image:ROM.jpg](ROM.jpg "Image:ROM.jpg")

</center>

*"A key role of this part of the architecture is to explicate the Web
itself, and how it relates to Web services. The ROM does so by showing
how resources are an independent concept, and yet how the manipulation
of resources is an instance of a Service Model: with particular kinds of
services and identified actions on resources."* It is the services and
actions on resources that represent attack vectors. The concepts of the
ROM that are of interest here are:

:\****Description** - This is the description of the resource.*

:\****Discovery service** - "A discovery service is a service that
performs discovery; of particular interest are discovery services that
permit the discovery of Web services."*

:\****Identifier** - "An identifier is a preferably opaque string of
bits that may be used to associate with a resource.*

:\****Representation** - "A representation is a data object that denotes
a resource state, and is the vehicle for conveying the meaning of a
resource."*

:\****Resource** - "A resource is defined by RFC 2396 to be anything
that has an identifier."*

:\****URI** - RFC 2396 says a Uniform Resource Identifier "can be
further classified as a locator, a name, or both."*

A Web service will not be used if:

:\#No one knows of its existence.

:\#No one can tell what it does.

:\#No one knows how to locate it.

:\#No one knows how to identify it.

:\#No one can determine its state.

The ROM describes the aspects of the Web Services Architecture that
addresses those problems. This is a weak analogy, but sufficient for the
point: The concepts of the Resource Oriented Model are to Web services
as DNS is to the Internet. The components that comprise the ROM are
vulnerable to the same general kinds of attacks that DNS is. The two
most basic classes of attack are Denial of Service (DoS) and data
manipulation that usually results in redirecting the victim to a
malicious destination. With respect to the ROM:

:\*If I can successfully attack the ***discovery service***, I can take
it down completely or I can manipulate the contents of the conversation
the service will have with the requesting agents.

:\*This will allow me to manipulate the ***description*** of the
resource which includes the ***representation*** of the current state of
the resource.

:\*I can also manipulate the ***URI*** of with the resource (service).
This means that I can hijack services.

The list could go on. The point is, maintaining the integrity of the
discovery service is critical. There is no limit to the nastiness that
can be accomplished by compromising it.

This is not to say that maintaining the integrity of the other concepts
listed above is not important. They are all important. It's just that
the scope of the damage that might be done by corrupting, say the
representation of a resource state, is not quite as great as if the
discovery service is corrupted.

## The Message Oriented Model

The Message Oriented Model also provides some juicy targets. After all,
the message is the means by which agents pass information among
themselves.

<center>

![Image:MOM.jpg](MOM.jpg "Image:MOM.jpg")

</center>

There are lots of moving parts in the MOM. Most of them are of at least
passing interest to security types. Some are particularly juicy. I am
only going focus on "the juicy ones" because the general set of security
concerns of sending messages over hostile networks is well known. The
concepts that exacerbate risks associated with the Message Oriented
Model are:

:\****Intermediary** - "An intermediary is an agent that is both a
message recipient and a message sender. An intermediary may process some
aspect of the message, and acts to forward the message to the next
message recipient towards an ultimate message receiver along the message
path."*

:\****Message Exchange Pattern** - "A Message Exchange Pattern (MEP) is
a template, devoid of application semantics, that describes a generic
pattern for the exchange of messages between agents."*

:\****Message Path** - "A message path is the sequence of agents that
process a message. . . . However, messages may also be processed by a
number of intermediaries that manage and constrain the message along the
path."*

The Service Oriented Model introduced the notion of a **choreography**.
The instance of a choreography that comes to mind is a workflow
application in which a complete unit of work involves several steps
which need to be performed in a certain order, and which may involve the
coordination of several services over the lifetime of the unit of work.
A choreography would rely on the above aspects of the MOM in order to
complete the unit of work. In a different set of circumstances, a
distributed transaction may route a message differently depending upon
the state of participants in the transaction or outcomes of certain
steps in the transaction. There are many valid reasons for having an
architecture in which there are intermediaries, message exchange
patterns and message paths. Problem is, from an information security
perspective, this is an architecture designed for man-in-the-middle
(MITM) attacks. Just thinking about the trust relationships and
assumptions that must exist to support this architecture gives me a
massive headache. This should raise a giant red flag to all the
stakeholders in Web services. If there has ever been a situation in
which a formal certifcation and accreditation process is justified, this
is it.

## The Management Model

Web services implies the existence of agents "somewhere out there on the
Web" that do things. It goes without saying that it must be possible to
manage these agents. Now, think SNMP. If you have never had the
opportunity to deal with SNMP, it would be worth talking with someone
who has had to manage a network and the devices on it. Then think about
managing Web services. The Managment Model addresses this problem.

<center>

Management Model Diagram

</center>

There is more to the management model than is captured in the diagram
above and interested readers are strongly encouraged to read the
document. For purposes of this article, though, there is one aspect of
the model that needs particular attention. If history indeed repeats
itself, (and it certainly does in the IT universe), the ***management
interface*** will be one of the most vulnerable points in the whole Web
services architecture. I leave it as an exercise to the reader to do a
literature review of the security problems created by mangement
interfaces. Security mailing list and newsgroup archives are a good
starting place. All I will say is that all of our experience has shown
us that especial care should be given to the design, implementation and
operation of the management interfaces.

## The Rest

So far, we have briefly looked at the architectural models. There is
much more in the Web Services Architecture document than the models.
There is a good discussion of stakeholders' perspectives which includes
a section on threats to security and privacy. To do justice to this
section would take as long or longer as it has taken to get to this
point. I will defer covering this until later. Much of what is covered
in that section will be covered in the next article anyway . . .

In this article we have covered a lot and not much at all. We have seen
a very small tip of a very large iceberg. There is a lot to Web
services. The architecture is complex. The trust relationships that will
have to exist in order for Web services to work are complex. The
realization of the discovery process is going to be complex. This is a
huge beast. And "complexity is the enemy of security . . ."

## References

:\*The DCE Security Service:
<http://www.hpl.hp.com/hpjournal/95dec/dec95a6.pdf>

:\*Overview: CORBA security:
<http://student.cosy.sbg.ac.at/~amayer/projects/corbasec/sec_overview.html>

:\*Interoperable Secure CORBA:
<http://choices.cs.uiuc.edu/Security/malakim/present1/sld001.htm>

:\*Using the KeyNote Trust Management System:
<http://www.crypto.com/trustmgt/kn.html>

:\*SESAME: <https://www.cosic.esat.kuleuven.ac.be/sesame/>

[Category:OWASP Columns](Category:OWASP_Columns "wikilink")
[Category:Web Services](Category:Web_Services "wikilink")