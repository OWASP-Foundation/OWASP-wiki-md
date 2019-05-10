[\< Back to the Application Security Guide For
CISOs](Application_Security_Guide_For_CISOs "wikilink") __NOTOC__

# Part III: Application Security Program

## III-1 Executive Summary

From the risk management strategic point of view, the mitigation of
application security risks is not a one time exercise; rather it is an
ongoing activity that requires paying close attention to emerging
threats and planning ahead for the deployment of new security measures
to mitigate these new threats.

This includes the planning for the adoption of new application security
activities, processes, controls and training. When planning for new
application security processes and controls, it is important for CISOs
to know on which application security domains to invest in order for the
business to deliver on its missions.

**To build and grow an application security program, CISOs must:**

  - Map business priorities to security priorities
  - Assess the current state using a security program maturity model
  - Establish the target state using a security program maturity model

**Map business priorities to security priorities**

All security priorities must be able to be mapped to business
priorities. This is the first step towards establishing the relevance of
every security initiative and shows business management how security
supports the mission. It also demonstrates to security staff how the
staff supports the mission.

**Assess the current state using a security program maturity model**

Accessing process maturity is a prerequisite for adoption of application
security and software security processes. One criteria that is often
adopted by organizations is to consider the organization's capabilities
in application security domains and the maturity of the organization in
operating in these domains. Examples of these application security
domains include application security governance, vulnerability risk
management, regulatory compliance and application security engineering
such as to design and implement secure applications. Specifically in the
case of application security engineering, adopting software security
assurance is often necessary when there is not direct control on
implementing the security of such software since it is produced by a
third party vendor. A factor to consider in this case is to measure the
software security assurance using a maturity model. A pre-requisite for
measuring software security assurance is the adoption of a Secure
Software Development Lifecycle (S-SDLC). At high level, S-SDLC consists
of embedding "build security in" security activities, training and tools
within the SDLC. Examples of these activities might include software
security processes/tools such as architectural risk analysis/threat
modeling, secure code reviews/static source code analysis, application
security testing/application vulnerability scanning and secure coding
for software developers. A reference to OWASP software assurance
maturity model as well as to the several OWASP projects dedicated to
software security and S-SDLC are provided in this guide as well.

**Establish the target state using a security program maturity model**

Not all organizations need to be at the highest maturity. The maturity
should be at a level that it can manage the security risk that affects
the business. Obviously, this varies among organizations and is driven
by the business and what it accepts as risk as part of continuous
collaboration and transparency from the security organization.

Once a target state is identified, CISOs should build a roadmap that
identifies its strategy for addressing known issues as well as detecting
and mitigating new risks.

OWASP provides several projects and guidance for CISOs to help develop
and implement an application security program. Besides reading this
section of the guide, see the [Appendix B: Quick Reference to OWASP
Guides &
Projects](https://www.owasp.org/index.php/CISO_AppSec_Guide:_Quick_Reference_to_OWASP_Guides_%26_Projects)
for more information on the type of security engineering domain
activities that can be incorporated within an application security
program.

## III-2 Introduction

Mitigating the risk of attacks that seek to exploit application
vulnerabilities as well as potential gaps in protective and detective
controls is one of the CISOs main concerns. In the case when
vulnerabilities are only found after a security incident, the next step
is to fix the identified vulnerabilities and limit further impact.
Typically, this involves reproducing the vulnerabilities and re-testing
the vulnerabilities after fixes are implemented to ensure
vulnerabilities can no longer be exploited. If the incident is due to a
gap of a security control such as a failure to filter malicious input or
to detect the attack event, the next step is to implement
countermeasures to mitigate the risk. Countermeasures may be a
combination of deterrent, preventative, detective, corrective, and
compensating security controls. To make such decisions, the CISO needs
to consider both the risks of vulnerabilities as well as the weaknesses
of security control measures to make a decision on how to mitigate the
risks. Typically fixing a vulnerability involves a vulnerability
management cycle that includes identifying the vulnerability, fixing it
and then re-testing it to determine that it is no longer present.

For countermeasures, the test that the countermeasure is effective in
preventing and detecting an attack vector can also be tested with a
functional security test after a countermeasure is deployed. The
decision as to which countermeasure to deploy might depend on different
factors such as the cost of the countermeasure vs. the business impact
of the incident as well as on how risk mitigation effective is the
countermeasure by comparing with others. The next step for the CISO
after the security incident is under control is to make sure any
vulnerabilities are fixed and countermeasures are deployed to mitigate
the risk. In this section of the guide we focus on application security
measures that are most cost effective to target the issues identified in
Part 2. For example how to divide budgets across software security
activities such as secure code training, secure code reviews, security
verification and testing and issue and risk management.

In the 2013 CISO Survey, CISOs identified their top priorities and also
the risks facing their programs. In this guide, you will find guidance
for tools and processes to not only execute on these priorities, but
also to manage the risks that may impact your priorities.

<center>

<table>
<caption>2013 CISO Survey: Top 5 CISO Priorities</caption>
<tbody>
<tr class="odd">
<td><ol>
<li>Security awareness and training for developers</li>
<li>Secure development lifecycle processes (e.g., secure coding, QA process)</li>
<li>Security testing of applications (dynamic analysis, runtime observation)</li>
<li>Application layer vulnerability management technologies and processes</li>
<li>Code review (static analysis of source code to find security defects)</li>
</ol></td>
</tr>
</tbody>
</table>

</center>

These priorities can be inhibited by the top program risks identified by
CISOs in the same 2013 CISO Survey.

<center>

<table>
<caption>2013 CISO Survey: Top 5 CISO Risks</caption>
<tbody>
<tr class="odd">
<td><ol>
<li>Lack of awareness of application security issues within the organization</li>
<li>Insecure source code development</li>
<li>Poor/inadequate testing methodologies</li>
<li>Lack of budget to support application security initiatives</li>
<li>Staffing (e.g., lack of security skills within team)</li>
</ol></td>
</tr>
</tbody>
</table>

</center>

## III-3 Addressing CISO's Application Security Functions

### Application security governance, risk and compliance

Governance is the process that introduces policies, standards, processes
and sets the strategy, goals and organizational structure to support
them. At an operational level, governance, compliance and risk
management are interrelated. As part of governance responsibilities,
CISOs influence the application security goals and work with executive
management to set the application security standards, processes and
organizational structure to support these goals. As part of compliance
responsibilities, CISOs work with auditors and the legal counsel to
derive information security policies and establish requirements to
comply, measure and monitor these requirements including application
security requirements. As part of risk management responsibilities,
CISOs identify, quantify and make risk evaluations to determine how to
mitigate application security risks that include introducing new
application security standards and processes (governance), new
application security requirements (compliance) and new application
security measures (risks and controls). From a governance perspective,
the adoption of application and software security processes, the
establishment of application security teams and application security
standards within any given organization varies greatly depending on the
type of organization’s industry, the size of the organization and the
different roles and responsibility that the CISO has in that
organization. OWASP provides several projects and guidance for CISOs to
help develop, implement and manage application security governance. See
the [Appendix B: Quick Reference to OWASP Guides &
Projects](https://www.owasp.org/index.php/CISO_AppSec_Guide:_Quick_Reference_to_OWASP_Guides_%26_Projects)
for more information on OWASP projects and guides in the governance
domain.

Typically the source of application security investments also varies
depending on the size and the type of the organization. For CISOs
reporting to the organization's head of operational information security
and risk management, typically the budget for application security is
part of the overall budget allocated by information security and
operational risk departments. For these CISOs, one the main reasons for
the adoption of new application security activities, guides and tools
such as the ones that OWASP provides, is first and foremost to satisfy
compliance and to reduce risks to the organization’s assets such as
applications and software. Compliance varies greatly depending on the
type of industry and clients served by the organization. For example,
organizations that produce software that implements cryptography for use
by governments such as the department and agencies of the United States
Federal government need to comply with Federal Information Processing
Standards (FIPS) 140. Organizations that produce software and
applications that handle cardholder data such credit and debit card data
for payments need to comply with the Payment Card Industry Data Security
Standard (PCI DSS). CISOs that report to the organization's head of
information technology, typically have responsibility on both security
and information technology functions that might also include the
compliance of applications and software with technology security
standards such as FIPS 140 and PCI-DSS. Compliance with security
technology standards represent an opportunity for promoting secure
development and testing within the organization such as by using OWASP
security testing guides for achieving security certifications for
applications and software products. Compliance with PCI-DSS
requirements, for example, might already require the organization to
test applications for a minimum set of common vulnerabilities such as
the OWASP Top 10. The budget allocated by the IT department for
achieving certifications with technology security standards such as
FIPS-140 and PCI-DSS can also be used for promoting secure coding guides
such as the OWASP secure coding guide and invest in static code analysis
tools. For example, in the case of compliance with PCI-DSS, CISOs might
opt for static code analysis to satisfy the requirement 6.6 of PCI-DSS.
OWASP provides several projects and guidance for CISOs to help develop
and implement policies, standards and guidelines for application
security as well as to help define application security requirements
that can be verified and audited. See the [Appendix B: Quick Reference
to OWASP Guides &
Projects](https://www.owasp.org/index.php/CISO_AppSec_Guide:_Quick_Reference_to_OWASP_Guides_%26_Projects)
for information on OWASP projects in the standards and policies and
audit & compliance domains.

CISOs of small organizations can also use vulnerability management
metrics to make the business case in which phases of the SDLC to invest
in security and improve both software quality as well as security. For
example, since most of the quality and security bugs are due to coding
errors, it is important for CISOs to emphasize to the IT department the
need for secure coding processes, standards and training for developers
since focusing on these software security activities also leads to cost
savings for the organization. A study from NIST about the cost of fixing
security issues for example has shown that the cost of fixing a coding
issue in production is six times more expensive than fixing it during
coding. To achieve these money saving and efficiency goals, CISOs can
work together with the engineering department managers to promote
application and secure software initiatives. [Part
IV](https://www.owasp.org/index.php/CISO_AppSec_Guide:_Metrics_For_Managing_Risks_%26_Application_Security_Investments)
of the CISO guide provides guidance regarding setting metrics for
managing application security risks and for deciding on application
security investments.

Among CISO responsibilities the Continuity of Business (CoB) is of
primary importance specifically for web applications that provide
critical business functions to customers. CISOs are responsible to roll
out CoB plans to ensure that the business could continue to operate
despite adverse circumstances or events. A CoB plan includes procedures
to restore services that are lost because of a negative event such as a
power outage of the data center where a web application is hosted. A
critical item of CoB planning is the identification of web applications
that are deemed business critical and assign a level of criticality and
specific requirements for CoB testing such as the maximum time to
recover from a loss of service. Similarly to CoB, having a disaster
recovery plan is also one of the CISO responsibilities: this includes
process, policies and procedures for recovery or continuation of
technology infrastructure in the case of natural or human provoked
disaster.

One of the main CISOs responsibilities is to increase application
security awareness among the application security stakeholders. A 2012
Survey by the Ponemon Institute and Security Innovation that included
more than 800 IT executives found that "gaps in perceptions between
security practitioners and developers about application security
maturity, readiness and accountability indicate why many organizations'
critical applications are at risk." Almost 80% of developers and 64% of
security managers that participated to this survey, responded that their
organization has no process for building security controls into their
applications, and more than 50% of both developers and security officers
reported that they did not receive software and application security
training, only 15% of developers and 12% of security officers reported
that applications met security regulations and 68% of developers versus
47% of officers reported to be aware of any security breaches affecting
applications occurring in the past 2 years. It is clear that there is
opportunity for efficiency gain by building security into the SDLC
through security training. OWASP has several training and awareness
resources that can be used for the training on application and software
security for development, operational and information security teams.
Please consult the Appendix B: Quick Reference to OWASP Guides &
Projects for more information on OWASP guides and projects in the
security training domain.

For CISOs whose main focus is information security and risk management,
one of the main requirements besides compliance is to introduce
efficiencies and save the money spent for existing security processes,
including application security. Since the information security
department allocates budgeting, any request for budget of application
security needs to be justified by improving security and by reducing
risks. Security and risk reduction goals are aligned by improving
security test processes with use of better tools and training for
developers. For CISOs of large organizations, promoting a software
security initiative is also justified by cost-avoidance revenue from the
decreased cost fixing vulnerabilities as a result of secure coding
standards, secure code reviews and security testing in earlier phases of
the SDLC when bug fixes are less costly. See [Appendix B: Quick
Reference to OWASP Guides &
Projects](https://www.owasp.org/index.php/CISO_AppSec_Guide:_Quick_Reference_to_OWASP_Guides_%26_Projects)
for information on OWASP guides and projects that help CISOs in
implementing an application security program including software security
development and security testing processes.

Often CISOs need to justify the budget for application security by
taking into consideration the different needs of security and business
departments. For CISOs that serve in financial organizations for
example, security is often a compromise with security and business
goals. In this case, it is important for CISOs to be able to align
application security programs with the business goals and when these
goals not align, to focus on the ones that do. For example, by focusing
on improving both software quality and security and by reaching a
compromise in the case security impacts negatively the customer
experience so different security options need to be considered. In the
case the business is sponsoring a new application development project,
CISOs can use this as an opportunity to promote new application security
features for the application and work together with project managers by
achieving compliance with security standards, improving security by
design and by coding and yet achieving overall cost savings for the
overall project.

### The importance of security metrics

For CISOs whose responsibility is manage application vulnerability
risks, security metrics such as application vulnerability metrics
constitutes an important factor in making business cases for investing
in application security measures to control and reduce risks. Security
metrics such as measurements of vulnerabilities found on the same
applications during the roll out of application security activities
aimed to reduce the number and the risk of vulnerabilities for example,
can demonstrate to senior managers and company executives that the
adoption of application security processes, training and tools
ultimately helps the organization to deliver applications and software
products that have a fewer number of vulnerabilities and pose less risk
to the organization and the customers.

## III-4 Targeting Software Security Activities and S-SDLC Processes

OWASP provides several projects and guidance for CISOs to help in the
development and implementation of software security activities and
Security in the Software Life Cycle (S-SDLC). To know more, besides
reading this section of the guide, please consult the [Appendix B: Quick
Reference to OWASP Guides & Projects for more
information](https://www.owasp.org/index.php/CISO_AppSec_Guide:_Quick_Reference_to_OWASP_Guides_%26_Projects)

### Recognizing the importance and criticality of secure software

Since insecure coding causes a large number of vulnerabilities in
applications, it is important that the CISO recognizes the importance
that secure software has in improving the security of the application.
The causes of insecure software might depends by different factors such
as coding errors, not following secure coding standards and security
requirements, integration with vulnerable software libraries, missing
secure code review processes and security testing and formal secure code
training and awareness for software developers. From CISO perspective,
it is important to understand that software security is a complex
discipline and requires a special focus in security processes, tools as
well as people skills. It is also important to recognize that investing
in software security helps the organization to save money spent in
application vulnerability remediation costs in the future. By investing
in software security initiatives, organizations can focus on fixing
vulnerabilities as early as during coding phase of the Software
Development Life-Cycle (SDLC) where is cheaper to identify, test and fix
them than during the validation phase.

Today, also thanks to OWASP, software security has matured and evolved
as a discipline. For example, several organizations already adopt
software security best practices within their software development
processes such as the documentation of security requirements, following
of secure coding standards and use of software security testing tools
such as static source code analysis tools to identify vulnerabilities in
source code before releasing source code to be build and integrated for
final integrated and user acceptance tests. By integrating software
security activities in the SDLC, organizations can produce software and
applications with a fewer number of vulnerabilities and lower risks than
software and applications that don’t.

### Integrating risk management as part of the SDLC

CISOs determine how software security activities can be integrated as
part of the SDLC. According to the National Institute of Standards and
Technology’s Special Publication 800-30, “Effective risk management must
be totally integrated into the SDLC ... \[which\] has five phases:
initiation, development or acquisition, implementation, operation or
maintenance and disposal.” The integration of security in the SDLC
process begins by identifying the information assets that the software
will be processing and by specifying requirements for confidentiality,
integrity and availability. The next steps consist of information assets
value determination, identification of the potential threats and
identification of the necessary application security countermeasures
such as authentication, authorization and encryption.

A comprehensive set of security requirements need to also include
requirements to implement secure software by following certain security
and technology standards, security approved technologies and platforms
as well as security checks prior of software integration with other
vendors software components/libraries.

### Assess risks before procurement of third party components/services

When software is acquired as either part of the commercial off-the-shelf
(COTS) or as free open source (FOSS) for example, it is important for
CISO to have a process in place to validate this type of software
libraries against specific security requirements prior to acquiring
them. This could provide the CISO of the organization a certain level of
assurance that the acquired software is secure and can be integrated
with the application. In that regard, OWASP had developed a legal
project and a contract annex of a sample contract that included security
requirements for the life cycle so that COTS products would be more
secure. Please refer to the [Appendix B Quick Reference to OWASP Guides
&
Projects](https://www.owasp.org/index.php/CISO_AppSec_Guide:_Quick_Reference_to_OWASP_Guides_%26_Projects)
for more information on OWASP projects that can help CISOs to assess
procurement of new application processes, services, technologies and
security tools.

### Security in the SDLC (S-SDLC) methodologies

In cases when the CISO of the organization has also responsibility over
promoting a software security process within the organization, it is
important not to take this goal lightly since usually requires careful
planning of resources and development of new processes and activities.
Fortunately today, several “Security in the SDLC” (S-SDLC) methodologies
can be adopted by CISOs to incorporate security in the SDLC. The most
popular S-SDLC methodologies used today are Cigital’s Touch Points,
Microsoft SDL, OWASP CLASP and the BITS Software Assurance Framework. At
high level, these S-SDLC methodologies are very similar and consist on
integrating security activities such as security requirements, secure
architecture review, architecture risk analysis/threat modeling, static
analysis/review of source code, security/penetration testing activities
within the existing SDLCs used by the organization. The challenge for
the integration of security in the SDLC from CISO perspective is to make
sure that these software security activities are aligned with the
software engineering processes used by the organization. This means for
example to integrate with different types of S-SDLC s such as Agile,
RUP, Waterfall as these might be already followed by different software
development teams within the organization. An example on how these can
be integrated within a waterfall SDLC as well as iterated within
different iterations of a SDLC process is shown below.

![Security_in_the_SDLC_Process.png](Security_in_the_SDLC_Process.png
"Security_in_the_SDLC_Process.png")

Adopting a holistic approach toward application and software security
leads to better results since can align with information security and
risk management already adopted by the organization. From information
security perspective, the holistic approach toward application security
should include for example security training for software developers as
well as security officers and managers, integration with information
security and risk management, alignment with information security
policies and technology standards and leveraging of information security
tools and technologies used by the organization.

### Software assurance maturity models

Besides of following a holistic approach toward application security
that considers other domains it is also important for the CISO to
consider what the organization capabilities are from day one in building
software security and plan on how to integrate new activities in the
future. Measuring the organizations capabilities in software security is
possible today with software security maturity models such as the Build
Security In Maturity Model (BSIMM) and the Open Software Assurance
Maturity Model (SAMM). These models can also help the CISO in the
assessment, planning and implementation of a software security
initiative for the organization. These maturity models are explicitly
designed for software security assurance. These models, even if are
based upon empirical measurements, are feed from real data (e.g.
software security surveys) hence allow to measure organizations against
peers that already had implemented software security initiatives. By
allowing their organization’s secure software development software
practices to be measured using these models, CISOs can compare their
organization secure software development capabilities against other
software development organizations to determine in which software
security activities the organization either leads or lags.

For the software security activities for which the organization is
lagging, BSIMM and SAMM measurements allow the CISO to construct a plan
for software security activities to close these gaps in the future. It
is important to notice that these models are not prescriptive that is,
are not telling organizations what to do but rather to measure security
activities in comparison with similar organizations in the field. The
models are organized along similar domains, governance, intelligence,
SSDL touch points, deployment for BSIMM and governance, construction,
verification, deployment for SAMM. SAMM measurements are done in three
best practices and three levels of maturity for each business function.

<center>

Figure: Business functions and security practices for each business
function ![<File:SAMM.jpg>](SAMM.jpg "File:SAMM.jpg")

</center>

BSIMM measurements cover 12 best practices and 110 software security
activities. The maturity levels help the CISO to plan for the
organizational improvements in software security processes. Software
security improvements can be measured by assigning goals and objectives
to reach for each activity. For CISOs that either have already started
to deploy a software security initiative such as S-SDLC within their
organization or that just plan it in the future, the measurements that a
model such as BSIMM and SAMM provide are important measurement yard
sticks to determine in which application security activities to focus
spending. If not already familiar with BSIMM and SAMM, CISOs can also
refer to the Capability Maturity Model (CMM) and the various maturity
levels to plan for the organization secure software development process
capabilities.

Like BSIMM and SAMM, CMM is also an empirical model whose goal is
improve the predictability, effectiveness, and control of an
organization's software processes. In CMM for example, these are five
levels that can be used to measure how the organization moves up to
different levels of maturity of software engineering process: initial,
repeatable, defined, managed, optimizing. In the first level (initial),
the software engineering process is ad-hoc and used by the organization
in uncontrolled and reactive manner. As the software development
organization reaches level 2, the software development processes are
repeatable and is possible to provide consistent results. When an
organization reaches level 3, it means that it has adopted a set of
defined and documented standard software development processes and these
are followed consistently across the organization. At a level 4, that is
managed, a software development organization has adopted metrics and
measurements so that software development can be managed and controlled.
When a software development organization is at level 5, optimized, the
focus is on continually improving process performance through both
incremental and innovative technological change and improvements in
software development.

In reference to software security processes, at CMM Level 1 (Initial)
CISOs have an ad-hoc process to “catch” and "patch" application
vulnerabilities. At this level, the organization maturity in software
security practice consists on running web application vulnerability
scanning tool in reaction of events such as to validate the applications
for compliance with PCI-DSS and OWASP Top 10. At CMM Level 2, the
organization has already adopted standard processes for security testing
applications for vulnerabilities including secure code reviews of the
existing software libraries and components. At this level, the secure
testing process can be repeated to produce consistent results (e.g. get
same security issues if executed by different testers) but is not
adopted across all software development groups within the same
organization. At CMM Level 2, the application security processes are
also reactive, that is, are not executed as required by the security
testing standards. At CMM Level 3, application security processes are
executed by following defined process standards and these are followed
by all security teams within the same organization. At this level,
application security processes are also proactive that means are
executed to security test applications as part of governance, risk and
compliance requirements prior to release into production. At level CMM 4
(managed) application security risks are identified and managed at
different phases of the SDLC. At this level, the focus of security is
the reduction of risks for all applications before these are released in
production. At level CMM 5 (optimized), the application security
processes are optimized for increased application coverage and for the
highest return of investments in application security activities.

### Security strategy

#### Strategy

*“Strategy (Greek "στρατηγία"—stratēgia, "art of general, command,
generalship") is a high level plan to achieve one or more goals under
conditions of uncertainty. The art and science of planning and
marshalling resources for their most efficient and effective use.
Strategy is important because the resources available to achieve these
goals are usually limited. Strategy is also about attaining and
maintaining a position of advantage over adversaries through the
successive exploitation of known or emergent possibilities rather than
committing to any specific fixed plan designed at the outset.”*

Like with a general IT strategy most organizations should have a
security strategy. It enables an organization to look beyond short-term
tactical choices and develop strategic and long term planning. Because
of the evolving cyber threat landscape it is important for CISOs to
protect the information security assets for the threat of tomorrow. This
strategy can guide operational decisions, plans and set priorities for
the appropriate level of investment of resources to achieve your
organization’s goals.

#### Have a plan and be ready to change it

A security strategy will not cover all eventualities, but rather provide
you with a good strategic framework. Furthermore, with time your
environment or underlying assumptions will change and your strategy will
need to constantly evolve and be adapted accordingly. It is better to
define a strategy and revise it frequently, adapting it to new
circumstances, than to hold back developing your security strategy
indefinitely, waiting for all information to become available.

To define the fundamentals of you security strategy, you should consider
the following three general questions:

1.  **Stakeholders:** Who are your key stakeholders and potential threat
    agents?
2.  **Assets:** What are your information assets and how do they (and
    their protection) generate value for your clients inside and outside
    the organization?
3.  **Capabilities:** What are the essential security and protection
    capabilities that the organization and its stakeholders need to
    deliver that value proposition?

![Strategy_3_key_questions.png](Strategy_3_key_questions.png
"Strategy_3_key_questions.png")

#### How to define your organization's security strategy

As with all strategy documents you will analyze the impact of underlying
assumptions and goals and derive your security strategy on how to
achieve these goals.

#### Collecting input for developing your security strategy

In general the following inputs are useful in the process of defining
your security strategy. Often organizations may not have all of them, or
these inputs maybe in informal less accessible form (e.g. in the mind of
some of your key employees in the organization). Or they might be
outdated or not exactly matching what you are expecting. Devising a
security strategy based on limited clarity of the overall strategy of an
organization or missing pieces of information may be challenging.
However, it is still better to develop some strategy and evolve it over
time as more and more related information becomes available.
![Security_strategy_inputs.png](Security_strategy_inputs.png
"Security_strategy_inputs.png")
**1. Business strategy**
CISOs should look first at the organization's business strategy such as
the mission statement, the business goals as well as the other strategy
components (see the following points) in support of these goals. For
example, which parts of your operation are critically reliant on the
confidentiality, availability and integrity of the information provided
by the IT functions? What would be the impact on your Sales and
Marketing in case of system failures or loss of prizing information, how
dependent is the supply chain on the functioning IT backbone, can
deliveries be made in case of failure, would fraud be spotted in case of
security problems? Which parts of the value chain are susceptible to
potential attacks? Which opportunities can certain security postures
offer as a competitive advantage for the business (e.g. can a more
robust security environment enable more e-commerce, higher dependency on
IT processes and more efficiency)? Can procurement processes be
dramatically changed, e.g. when allowing a BYOD (bring your own device)
strategy? Are there new and potentially disruptive business cases
possible due to secure and reliable application? How far can you allow
some of your data to leave the immediate control of your organization
(e.g. in case of cloud based applications)? How can you minimize the
risks, by legal and technical controls? Are the resulting risk levels
acceptable for the business?
**2. Corporate strategy**
How does your corporate strategy align with your IT and security
strategy? Does your corporation aim for a decentralized or centralized
organizational structure? How does this affect your ability to enforce
central and local security policies? Are frequent corporate acquisitions
and their integration an important part of your corporate strategy and
how do you integrate new entities effectively and manage the security of
these newly acquired corporate entities across the whole organization?
**3. IT strategy & Review of the IT architecture**
One important aspect of the security strategy is the alignment with the
IT strategy for example depending on whether systems are decentralized
or centralized, it will determine how and to which extend the
organization can enforce central and local security policies. Further
aspects are system architecture overview, trust boundaries, data flows,
data in motion, and data at rest. How did your business strategy drive
your IT strategy. What kind of IT assets and capabilities does your
organization have and plan to develop going forward?
**4. Compliance and legal requirements**
**5. Analyze your threats and risks**
You need to understand how these risks affect your business operation
and could possibly affect your business and business strategy. (See also
part II of this guide)
**6. Review of your current security status**
Another important factor to consider before setting the security
strategy is the maturity of the organization and the capabilities in the
various security domains and specifically the application security
domain. A maturity model such as OWASP openSAMM and the various
activities in the Strategy and Metrics (SM) can also be used by CISOs to
review the current security status and set goals. Specifically, by
following the openSAMM model CISOs can start with level 1 (basic) SAMM
activities such as "estimate the overall business risk profile" and
"build and maintain assurance program roadmap"'. As the maturity of the
organization grows, CISO can incorporate level 2 openSAMM activities
such as "classify data and applications based on business risk", and
"establish and measure per-classification security goals". Understanding
the current security status of your organization will allow to develop a
clear roadmap as one of the key components of a good security strategy
going forward.

#### Components of your security strategy

A security strategy should contain or enable the following components:
**1. General guiding principles & priorities**
What security investments will the organization make over the next x
months. In general most companies use a time period of 12 – 24 months
for their strategy definitions. It would be advisable to have a main
security strategy defined for 12 months, with a second longer term
planning component for between 2 and 5 years, depending on the type of
organization, that outlines security investment plans for the longer
term. Of course in today’s fast changing security arena, threats and
risks can change very quickly and the plan should be adapted whenever
underlying assumption change and be reviewed at least on a yearly
basis.
**2. Risk Management, risk acceptance levels**
(see Part II)
**3. Security Roadmap**
To define your security roadmap, a good way is to look at the general
company and IT roadmaps and combine this with a security roadmap derived
from risk based assessments using maturity models like for example
openSAMM.
**4. Security architecture & Processes**
What security properties does the overall system architecture present?
What and where are the trust boundaries and underlying trust assumptions
for your organization? Which are core security systems like
authentication and authorization? How deep is the reliance on individual
central and legacy systems, e.g. if you deploy single-sign-on or
equivalents, how reliable is the central system managing all
authorization controls?
Furthermore the security architecture needs to consider the attack
surface and the exposure to cyber threats, specifically which parts of
the application architecture and the functionality are susceptible to
potential cyber attacks. And building on that is resiliency, hence the
question is which security architecture is the most resilient in case of
attacks, like for example DdoS, etc.
The procurement of security technology and services is a critical
component of the security strategy, too. Questions to ask here are
whether the procurement process addresses security risks introduced by
the adoption of third part technology and what the organization can do
to improve the security of third party processes and applications.
And in today's cloud based systems, data can often leave the security
perimeter and flow through other networks (e.g. in the cloud) and
systems. And the organization may have no or only very limited control
on how this data is protected in such cloud applications.
**5. Continuity of Business & Incidence Response**
It is important that CISOs also develop a Continuity of Business (CoB)
plan as part of the security strategy that takes into account possible
system failures and the dependencies of the supply chain on the
functioning IT infrastructure.
A security strategy should consider worst case scenarios and plan for
security measures in advance. A proactive risk strategy is to answer
questions about managing business impact before an incident actually
occurs. For a service delivery business for example the question might
be whether the application can still operate to guarantee delivery and
fail securely.

![Security_strategy_outputs.png](Security_strategy_outputs.png
"Security_strategy_outputs.png")

#### Conclusion

The overall goal for the security strategy is to minimize the risks and
maximize the business benefits for the organization. The key question
that the strategy must answer is whether security controls are
sufficient and efficient enough to reduce the risk for the organization
and the residual risks after security measures are applied are
acceptable for the business.

Generally, most roadmaps have a duration of 1-2 years. The 2013 OWASP
CISO Survey found that 64% of roadmaps projected for 1-2 years.

<center>

![Roadmapduration.png](Roadmapduration.png "Roadmapduration.png")

</center>

## III-5 How to Choose the Right OWASP Projects For Your Organization

Depending on the overall security level and risk profile of the
organization unit different tools and standards can be particularly
useful for the CISO in advancing his or her security strategy.

Note, following the risk discussions in the previous chapter, depending
on the risk profile of different business units, the security strategy
can actually be different based on their different individual risk
scenarios and different regulatory requirements. For example a financial
department may require a substantially stronger security posture, while
an internal web page announcing the lunch menus of the cantine may be
sufficiently protected with basic security measures (though to the
authors knowledge in military settings, even the lunch menu can be
considered as confidential information as further information about
supply logistics etc. could be derived from that).

Based on these different risk profiles different tools and standards may
be more relevant for the project and organizational unit in question.

Also note that OWASP provides several projects and guidance for CISOs to
help in the development and implementation of software security
development and security testing processes. Please refer to [Appendix
B](https://www.owasp.org/index.php/CISO_AppSec_Guide:_Quick_Reference_to_OWASP_Guides_%26_Projects)
for a quick reference to OWASP guides & projects.

In general tools can be classified in various categories (and so are
also the OWASP projects).

![<File:Owasp_projects.png>](Owasp_projects.png
"File:Owasp_projects.png")

### Project's maturity

  - Stable (a project or tool that is mature and constantly maintained
    to a good quality)
  - Beta (relatively proven, though not to optimal quality)
  - Alpha (this usually reflects a good first prototype, but still a lot
    of functionality may be missing or not up to standard)
  - Inactive (former projects that have been retired or deprecated or
    that at some point have been abandoned).

Obviously for a CISO, the most interesting projects and tools would be
stable and reliable ones. He can rely on a certain proven quality, and
on them being available and maintained to a certain degree in the future
days to come. Beta projects can also be very valuable, as they may
represent projects that have not finished their full review cycle yet
but are already available for early adopters and can help to build good
foundations for your security programs and tools going forward.

### Project's categories

Usually OWASP projects are divided in either Tools or Documentation. And
by the category of use: Builders, Breakers and Defenders. These
categories can help the manager to quickly navigate the large portfolio
of OWASP tools available and more easily find the right project for his
current needs.

### People, processes and technology

The CISO can also choose to achieve his security goals through three
main ways. **People**, **Processes** and **Technology**. Managing the
organization it is usually important to shape all three pillars to
achieve the best impact throughout your organization. Focusing on only
one or two of them can leave the organization vulnerable.

![People_Process_Technology.png](People_Process_Technology.png
"People_Process_Technology.png")

#### People

This will address the training and motivation of staff, suppliers,
clients and partners. If they are well educated and motivated, the
chances of malicious behavior or accidental mistakes can dramatically be
reduced and many basic security threats can be avoided.

#### Processes

If an organization becomes more mature, the processes will be well
defined and in fact channel and enable the work force to do things the
"right way". Processes can ensure that the actions of the organization
became reliable and repeatable. For example with well-defined standard
operating procedures, the incident response process will be reliable and
not rely on ad hoc decisions that would before have varied with the
individual decision maker. In highly mature organizations, the business
and IT processes will be constantly evaluated and improved. If a failure
happens, improved processes can allow an organization as a whole to
learn from past mistakes and improve its operation to more efficient and
secure ways.

#### Technology

Technology can guide and support people by providing good training and
knowledge, by being engaging and motivating to work with. Technology can
facilitate an organization to follow sound security practices by
providing good tools, while making difficult to deviate from the right
path without detection. For example, good technology would automate
access controls and authentication and make them very simple for the
authorized user, while denying access or privileges to an unauthorized
attacker. Finally, a number of automated tools can in the background
help and support the people and organization in their work to defend
against risks more effectively and more efficiently. Many of the
security standards and tools (in OWASP and other bodies) can also be
seen as focusing on parts of this framework. For example, staff training
will enable the people to build their security understanding and do the
right thing, while the various SDLC models can help an organization
establish the right level of processes for its development and incident
response mechanisms.