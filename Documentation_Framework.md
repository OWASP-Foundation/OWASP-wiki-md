## A Tailored Web Application Security Documentation Framework

### Introduction

In the last column I wrote, I set the scene to expect some big picture
stuff. Here goes.

I strongly believe that if you are going to build an effective,
scaleable and manageable application security program you have to start
to build on great foundations. Great foundations mean great
documentation: great policy, great standards and great process to then
back it up. You have to get the basics right especially given the
immaturity of commercial technology to support dealing with the problem
today.

There are many reasons why documentation is important. For a start how
can you hold anyone accountable or expect them to do the right thing
unless you tell them clearly what the right thing is? If you work for a
company that has more than a few hundred developers, it is just not
feasible to spend time with all of them and educate about the issues and
the policy. You have to build a ***publish and subscribe*** model where
you the security evangelist publishers and the developers take
responsibility for their own code by subscribing mentally.

And here in lies a conundrum. Technical evangelists (which for the most
part is a category I think application security leaders today fall into)
are usually not good at writing documentation or developing business
process and business orientated folks are rarely technical enough to
write credible documentation or develop process that will work Six Sigma
initiatives, balance scorecards and such like are alien concepts to
technicians, and source code trees and the RUP are equally as alien to
business managers. Of course there are those with both skills but they
are few and far between.

My advice is to do what Arnie will do when he takes over as governor of
California. Accept that selecting the right tool for the job is half of
the battle; surround yourself with good people that can do it all (or
the bits that you are not as strong at) and build strong foundations. I
think Arnie will be successful by leaning on the like of Warren Buffet
for economic advice and others who together will get the job done.

### Presenting a Web Application Security Documentation Framework

Before I describe the scope of what I think is needed in a typical large
enterprise its worth discussing why one size won't fit all and why I
mandate taking a tailored approach. Over the years I have rarely seen
documentation frameworks that work. I have seen good documentation that
was not applicable to the culture or technical environment; I have seen
bad documentation (lots of it) and most often have found none at all.
Security policy has a stigma attached to it. It is usually written by
the security department for the security department itself and not for
the audience. It is largely irrelevant and rarely maintained. In
application security that general security policy problem is exaggerated
as security departments (at least until recently) rarely had competent
application security folks who could connect with the intended audience.
Application security is all about unique things. That means people will
legitimately do things in a particular way. Companies will have specific
reusable components that should be used or tried and trusted ways of
doing things. Therefore any generic documentation is likely to fail as
it is not relevant to the environment and would unreasonably demand the
audience to change ways that work today. On the other end of the
spectrum my experience is that customized documentation frameworks that
have been developed rarely contain the content about application
security that is needed. The content they do contain is usually
applicable and relevant but the scope falls far short of what is needed.

What I believe is needed is a tailored approach. A good framework from
which people / consultants can tailor the content to the organizations
culture, technology and existing process. With a tailored framework you
can quickly highlight policy, standards or processes that is missing or
weak. Tailoring allows you to not hit the ground running, provide a
solid foundation, reuse good content (leveraging experience) and still
ensure all content is applicable and therefore effective. Tailoring
allows additional documentation to be developed or existing
documentation to be eliminated based on need.

### An Example Documentation Framework

To demonstrate what I mean by a tailored framework I have created an
outline that I have used in the past and am currently developing to help
me with consulting engagements.

Many people use the words policy, standards and procedure
interchangeably. For the purpose of this framework;

:\*A policy is a collection of high level statement of intent

:\*A standard is a set of requirements about specific topics or
technologies

:\*A procedure describes a process of implementing a standard or a part
of a standard

The hierarchy of how this fits together could be explained in the simple
pyramid diagram below.

I advocate a specific web application security policy that should be
referenced (as simple as one line) in the main corporate information
security policy and mandated by the CIO (not the CSO). Each standard
should typically have an associated procedure that explains exactly how
to implement the standard. The policy should very rarely change, the
standards will be updated periodically and the procedures are likely to
be updated frequently as business process is refined.

### Compartments

One of the most important things about the framework are the
compartments. The compartments define and show the scope and extent of
documentation that is needed as well as help the audience navigate the
documentation framework to visually find what they need to know.

:\*Languages and Development Frameworks

:\*Infrastructure Configuration Management

:\*Architecture and Design

:\*Development, Deployment and Maintenance

:\*Operational Security Management

As you can see from the framework diagram there are quite a few
standards and procedures that I recommend. These diagrams are by no
means complete. Organizations may need and choose far less than this to
fit into their culture, security maturity or posture. Others may need
far more. Remember these are not all encompassing and others may be
needed or some may be eliminated based on your tailoring process. But at
least this level of detail is typical in a large enterprise if you are
going to scale and be effective. The OWASP Guide (which many people use
as their web application security standards today) covers a limited
sub-set of this (mainly design and architecture). Lets review the
concept of each Compartment in more detail.

### Languages, Development Frameworks and Protocols

The compartment deals with the languages and technology platforms upon
which code is written;

:\*Frameworks

:\*\*J2EE

:\*\*.NET

:\*\*STRUTS

:\*Languages

:\*\*Java

:\*\*C\#

:\*\*HTML (yes, HTML)

:\*\*C

:\*\*XML

:\*HTTP

:\*SSL

:\*SOAP

A .NET standard may deal with versions, removing the samples,
namespaces, removing tools etc. A J2EE standard covering things like
class scope maybe supported by procedures for obfuscating code that is
deployed to presentation tiers or how to call reusable security
components (one of the most powerful procedures you can develop by the
way).

### Infrastructure Configuration Management

The infrastructure configuration management compartment deals with
secure configurations for the components on which the application relies
on for services. These include;

:\*Web servers

:\*Application servers

:\*Databases

:\*Firewalls

:\*Directory Services

:\*LAN/WAN Devices

At a minimum these are standards around which web and application
servers can be used and security requirements for their configuration.
Supporting procedures are then needed to spell out to administrators how
to achieve those requirements such as applying security patches, setting
file permissions or configuring access control.

### Architecture and Design

:\*Application Architecture

:\*Network Security

:\*\*Firewalls

:\*\*Remote Access

:\*Application Design

:\*\*Authentication

:\*\*Input Filtering

:\*\*Authorization

:\*\*User Management

:\*\*Transport Security

:\*\*Cryptography

:\*\*Error Handling

:\*\*Session Management

:\*\*Data Handling

At a minimum these are standards around which web and application
servers can be used and security requirements for their configuration.
Supporting procedures are then needed to spell out to administrators how
to achieve those requirements such as applying security patches, setting
file permissions or configuring access control.

### Development and Deployment

:\*Application and Content Deployment

:\*Assessment

:\*\*Threat Modeling

:\*\*Architecture Reviews

:\*\*Code Review

:\*\*Documentation Review

:\*\*Process Reviews

:\*\*Manual Inspection

:\*\*Black Box Testing (implementation)

:\*Source Code Management

:\*Source Code Escrow

We all know there is a lot more to conducting an assessment that running
a scanner over a web site (a topic we intend to cover in detail soon).
Assessment standards should define the types of testing that is needed
and be supported by detailed procedures for how to conduct it.
Deployment standards would prescribe appropriate means to deploy code
(no, FTP is not generally a suitable\!)

Finally to underpin all this scalable framework is robust Operational
Security Management

:\*Change Control standards/procedures

:\*Patch Management standards/procedures

:\*Incident response standards/procedures/ event logging may have it
covered

Once we have developed and deployed a secure application, we need to
ensure that the day to day management of the applications maintains the
high level of security and best practices implemented.

### Conclusion / Advice

If you want to develop an effective application security program you
need to build from solid foundations and make sure you have the basics
covered. That means a good documentation framework. A good documentation
framework covers policy, standards and procedures. The best way to
create a framework is to use a tailored approach starting with base
documents developed by experienced application security professionals
and tailor them to your environment, culture and business. Do not
reinvent the wheel.

Develop the core standards and procedures that you need based on your
priorities. Never aim to have a static set of documents. Assume it will
always be a work in progress.

There are a lot of topics to define requirements for and develop
procedures and process to help people meet those requirements. Do not
underestimate the amount of work or skill needed but do not be afraid to
start and maintain what you psychologically think is incomplete work. It
will never be complete. You do not need it all from day one.

[Category:OWASP Columns](Category:OWASP_Columns "wikilink")
[Category:OWASP_WASS_Project](Category:OWASP_WASS_Project "wikilink")