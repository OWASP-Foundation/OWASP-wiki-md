__TOC__

## Laying the Groundwork

In order to effectively review a code baseline, it is critical that the
review team understands the business purpose of the application and the
most critical business impacts. This will guide them in their search for
serious vulnerabilities. The team should also identify the different
threat agents, their motivation, and how they could potentially attack
the application.

All this information can be assembled into a high-level threat model of
the application that represents all of information that is relevant to
application security. The goal for the reviewer is to verify that the
key risks have been properly addressed by security controls that work
properly and are used in all the right places. In some cases the threat
model will already be created, in other cases the reviewers might need
to draft one up themselves.

Ideally the reviewer should be involved in the design phase of the
application, but this is almost never the case. However regardless of
the size of the code change, the engineer initiating the code review
should direct reviewers to any relevant architecture or design
documents. The easiest way to do this is to include a link to the
documents (assuming they're stored in an online document repository) in
the initial e-mail, or in the code review tool if that is supported.

Performing code review can feel like an audit, and most developers hate
being audited. The way to approach this is to create an atmosphere of
collaboration between the reviewer, the development team, the business
representatives, and any other vested interests. Portraying the image of
an advisor and not a policeman is very important if you wish to get full
co-operation from the development team.

## Before We Start

The reviewer(s) need to be familiar with:

1.  **Code**: The language(s) used, the features and issues of that
    language from a security perspective. The issues one needs to look
    out for and best practices from a security and performance
    perspective.
2.  **Context**: The working of the application being reviewed. All
    security is in context of what we are trying to secure. Recommending
    military standard security mechanisms on an application that vends
    apples would be over-kill, and out of context. What type of data is
    being manipulated or processed, and what would the damage to the
    company be if this data was compromised? Context is the '' "Holy
    Grail" '' of secure code inspection and risk assessment… we’ll see
    more later.
3.  **Audience**: The intended users of the application. Is it
    externally facing or internal to “trusted” users? Does this
    application talk to other entities (machines/services)? Do humans
    use this application?
4.  **Importance**: The size of the consequences of failure. Shall the
    enterprise be affected in any great way if the application can not
    perform its functions as intended?

## Discovery: Gathering the Information

The reviewers will need certain information about the application in
order to be effective. The information should be assembled into a threat
model that can be used to prioritize the review. Frequently, this
information can be obtained by studying design documents, business
requirements, functional specifications, test results, and the like.
However, in most real-world projects, the documentation is significantly
out of date and almost never has appropriate security information. If
the development organization has procedures and templates for
architecture and design documents, the reviewer can suggest updates to
ensure security is considered at these phases.

One of the most effective ways to get started, is to talk with the
developers and the lead architect for the application. This does not
have to be a long meeting, it could be a whiteboard session for the
development team to share some basic information about the key security
considerations and controls. A walkthrough of the actual running
application is very helpful to give the reviewers a good idea about how
the application is intended to work. Also, a brief overview of the
structure of the codebase and any libraries used can help the reviewers
get started.

If the information about the application cannot be gained in any other
way, then the reviewers will have to spend some time doing
reconnaissance and sharing information about how the application appears
to work by examining the code.

## Context, Context, Context

Security code review is not simply about reviewing code. It’s important
to remember that the reason that we review code is to ensure that the
code adequately protects the information and assets it has been
entrusted with, such as money, intellectual property, trade secrets,
lives, or data.

The context in which the application is intended to operate is a very
important issue in establishing potential risk. If reviewers do not
understand the business context, they will not be able to find the most
important risks and may focus on issues that are inconsequential to the
business.

As preparation for a security code review, a high level threat model
should be prepared which includes the relevant information. This process
is described more fully in a later section, but the major areas are
listed here:

  - Threat Agents
  - Attack Surface (including any public and backend interfaces)
  - Possible Attacks
  - Required Security Controls (both to stop likely attacks and to meet
    corporate policy)
  - Potential Technical Impacts
  - Important Business Impacts

Defining context should provide us with the following information:

  - Establish the importance of the application to the enterprise.
  - Establish the boundaries of the application context.
  - Establish the trust relationships between entities.
  - Establish potential threats and possible controls.

The reviewers can use simple questions like the following to gather this
information from the development team:

“***What type/how sensitive is the data/asset contained in the
application?***”:

This is a keystone to security and assessing possible risk to the
application. How desirable is the information? What effect would it have
on the enterprise if the information were compromised in any way?

“***Is the application internal or external facing?***”, “***Who uses
the application, and are they trusted users?**”*

This is a bit of a false sense of security, as attacks take place by
internal/trusted users more often than is acknowledged. It does give us
context that the application *should* be limited to a finite number of
identified users, but it’s not a guarantee that these users shall all
behave properly. Even if a application is sitting behind a firewall,
defense in depth can be considered when the data is sensitive.

*“**Where does the application host sit**?”*

Users should not be allowed past the DMZ into the LAN without being
authenticated. Internal users also need to be authenticated. No
authentication = no accountability and a weak audit trail.

If there are internal and external users, what are the differences from
a security standpoint? How do we identify one from another? How does
authorization work?

“***How important is this application to the enterprise?***”.

Is the application of minor significance or a Tier A / Mission critical
application, without which the enterprise would fail? Any good web
application development policy would have additional requirements for
different applications of differing importance to the enterprise. It
would be the analyst’s job to ensure the policy was followed from a code
perspective also.

A useful approach is to present the developers with a checklist, which
asks the relevant questions pertaining to any web application.

## The Checklist

Defining a generic checklist which can be filled out by the development
team is of high value, if the checklist asks the correct questions in
order to give us context. The checklist is a good barometer for the
level of security the developers have attempted or thought of. If
security code review becomes a common requirement, then this checklist
can be incorporated into a development procedure so that the information
is always available to code reviewers. The checklist should cover the
most critical security controls and vulnerability areas such as:

  - Data Validation
  - Authentication
  - Session Management
  - Authorization
  - Cryptography
  - Error Handling
  - Logging
  - Security Configuration
  - Network Architecture

[Category:OWASP Code Review
Project](Category:OWASP_Code_Review_Project "wikilink")