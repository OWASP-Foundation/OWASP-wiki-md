[\< Back to The
Application_Security_Program_Quick_Start_Guide](Application_Security_Program_Quick_Start_Guide "wikilink")

## Key Activities

### Evaluation

  - Dedicate time to understanding the “lay of the land” and the key
    players, along with their objectives and motivations.
  - Spend time with the parts of the organization that you are least
    familiar with.
  - Identify the security mandate as defined by the business/management.
  - Identify how IT Operations align with the security mandate.
  - Be alert to your existing biases.

## Key Questions

<span id="Management"></span>

### Management

***Has the business defined an internal security mandate?*** Business
drivers may originate from legal or industry compliance obligations,
internal policy, or customer or partner requirements. All actions and
activities in the Application Security program should tie back to
specific business obligations. If there is no business mandate, a case
must be made to the business that an application security program is
necessary. There are a number of industry statistical reports and
benchmarks available that address what other, similar organizations have
implemented and why.

***What are the current and planned human and financial resources
dedicated to Application Security?*** If resources are currently
dedicated to ensuring the integrity of applications, examine the current
allocation of those resources against their outcomes. The goal is to
ensure that in a world of limited resources, each activity is measured
for actual efficacy.

If there are few or no resources allocated to ensuring the integrity of
applications, the case must be made by leveraging data relevant to the
organization that can be quantified in financial terms. Building a
formal business case is the most effective way to approach the problem.
The case must address the needs as they apply to existing business
objectives. This is not the time for expounding on the virtues of
security. You must translate the business benefit of reallocating
financial resources. Simply asking for X number of dollars to reduce Y
number of vulnerabilities is typically ineffective.

***What are the IT & Business priorities?*** IT is both an enabler and
supporter of the business. Security is no different in this respect;
however, it has the added challenge of needing to be transparent where
it can be, and be a part of the ordinary workflow, or be perceived as a
roadblock. Once the business priorities have been identified, the
application security goals must be aligned with those priorities. If the
business priorities are to release new functionality at a rapid pace,
then application testing must keep pace; if the priorities are to
maintain the user experience over a long period of time, a pplication
testing must be rigorous before the user is ever exposed to the
application.

### Security

<span id="Security"></span> ***What is the overall security budget and
the priorities of that budget?*** ***What percentage of that budget is
allocated to Application Security?*** Most departments will feel under
budget to some degree. Examine the overall security budget (including
cyberinsurance budget if possible, as it likely falls outside of the
security budget) to understand what receives financial priority and how
the Application Security program could benefit from those activities. If
there is significant spend on security infrastructure, ensure that they
are leveraging controls to protect applications -- for example, alerting
on the lack or improper use of security headers.

***Which of your assets are most frequently attacked?*** Not all attacks
are equal, and not all attacks are opportunistic. Careful examination of
attack frequency and velocity can identify the assets requiring
additional testing to ensure resiliency. Often, low(er) priority assets
will be targeted for exploitation as they tend not be as resilient to
attacks.

***What security tools and/or services do you as a company currently
own/use?*** Query other parts of the security organization to understand
what tools and services they already have access to. Software and
services are often bundled in contracts but not used as they were not
the primary purpose for purchase. If the QA team already has access to
security tools that were bundled as part of their QA software
acquisition there are opportunities to leverage that existing financial
commitment and even allow for native integration.

### IT Operations

<span id="IT Operations"></span> ***What are your assets?*** Include
assets you own and assets hosted or owned by third parties. Unknown or
unmanaged assets cannot be protected. It is also difficult to fix issues
if the person or team responsible for those assets is unknown.
Developing an accurate and update-to-date asset inventory can be
challenging, however, for the purpose of this exercise we will be
focusing on web-based assets. The narrowed scope can be aggressively
targeted and maintained.

***How are web assets isolated and distributed throughout the
infrastructure?*** If an attacker were able to compromise a machine (say
a webserver, or a database server) what would prevent them from pivoting
and hacking into other nearby machines? Are they physically isolated,
logically isolated, or do they share similar credentials, etc?

***How frequently do you perform network and server vulnerability
scans?*** Addressing web application vulnerabilities on a server that
never patches its operating system is a waste of resources. Understand
how often infrastructure is assessed and patched – this should match or
exceed the pac e of attack frequency.

***What is your tolerance around production safety?*** Some environments
are more sensitive to production testing, as there is always some
likelihood of impact; the goal is to get the likelihood of impact as
close to zero as possible. As the likelihood of impact approaches zero,
the frequency of testing should be increased. Ultimately, production
systems are the primary targets of our adversaries – they should be
tested as often as possible; at a minimum, at least as frequently as the
application itself is changed or updated.

<span id="Engineering Groups"></span>

### Engineering Groups (including QA and Software Development)

***According to the software development group’s understanding of the
current processes, whose responsibility is application security?***
Security lives in our corporate cultures and psyche. Developers are
ultimately responsible for their code; understand whether they also
believe they are responsible for the integrity of that code. Security is
not the sole responsibility of either the developer community or the
security department. Foster a healthy environment of mutual
responsibility and accountability from all stakeholders. Begin by
sharing information in a non-aggressive manner.

***Where does Security fit into the software development lifecycle?***
If a development lifecycle does not exist, the first priority is to
demonstrate the business value of having a defined process. Most
organizations will have some process in place, even if it is an immature
one. The absence of a development process could also prove to be an
opportunity to ensure security is built into a process from the start.

Roughly, the steps to building or updating software can be generalized
as:

1.  Planning / Analysis
2.  Design
3.  Implementation
4.  Testing
5.  Maintain
6.  Decommission

Let’s break down each step and discuss basic security activities that
are often considered to reduce risk.

**Planning / Analysis:** Ensure business analysts and stakeholders have
considered and can detail the security needs and risk tolerance of an
application. This may reference internal data classification policies to
describe the data sensitivity. Threat modeling may also help clarify the
potential threat agents who may be motivated to attack the proposed
application.

**Design:** A security architecture review may reveal security design
flaws in key areas such as authentication, access control, or separation
of concerns, and of course may identify missing categorical security
controls.

**Implementation:** The implementation process normally consists of the
coding and development of the overall architecture design formulated in
the previous phase. Developers should be receiving continuous security
feedback to ensure all security issues are being identified and
mitigated in conformance with the organization’s risk tolerance.

**Testing:** Testing should include security tests as well as functional
tests. Areas of concentration should be on vulnerabilities that would
not have been uncovered during the implementation phase, such as
business logic vulnerabilities.

**Maintenance:** Once the application is promoted to production,
continuous testing of security issues should be ongoing throughout the
life of the application. As vulnerability vectors and attacks evolve,
the application should be tested to ensure defensibility against these
new attacks.

***How are software defects documented, trended, and prioritized?*** The
key to adoption of an Application Security program is alignment with and
transparency to current workflows. Identify how application defects are
documented, trended and prioritized, and plan to insert the application
security defects into these existing documents and processes.

***Are developers encouraged to develop secure code?*** Positive
incentive programs foster ownership and accountability for output.
Corporate culture varies from each organization; tapping into that
culture to offer incentives for producing rugged code will create a
natural momentum for finding and fixing security issues. Some cultures
will value access to otherwise less accessible personnel, such as lunch
with the CTO; others will be motivated by gifts that they might not have
purchased for themselves, such as a robotics kit. Take the time to
understand the culture of your organization and tap into the inherent
desire most people have to be rewarded. Remember that money does not
motivate everyone, and can even be demotivating in some cases.

***Are abuse and misuse cases part of test scripts?*** Test scripts are
often developed for the sole purpose of ensuring the application
performs the intended functionality. Introduce test scripts that could
identify the misuse of intended functionality, such as the ability to
execute similar functionality a user should not be able to access.

'**'Is everyone in the organization expected to have general software
security knowledge or is there a team/individual tasked with being the
"Security Deputy"?**' Security deputy programs are a good approach to
disseminating application security information to non-security focused
departments; they also have the added bonus of fostering a two-way
relationship.

Implement a deputy program that:

  - is focused on the goals of the application developers and
    application security testers
  - is aimed at achieving results beyond simple security awareness
  - can address the points throughout the development cycle where
    vulnerabilities are introduced – at the time the code is written

[\< Back to The
Application_Security_Program_Quick_Start_Guide](Application_Security_Program_Quick_Start_Guide "wikilink")