[\< Back to the Application Security Guide For
CISOs](Application_Security_Guide_For_CISOsVs2 "wikilink")

## Executive Summary

One of the main responsibilities of CISOs is to make sure information
security policies and standards are in place for protecting the
company's assets. The main goals of these policies and standards is to
protect confidential data from un-authorized access, ensure integrity
and availability. Besides data, applications and software can also be
considered among the company assets. that need to be protected. These
applications and software might also be in scope for security
assessments such as ethical hacking-pentesting, secure code reviews and
threat modelling. The goal of these assessments is to identify and
remediate vulnerabilities during the various phases of the SDLC that
include requirements, design, implementation, deployment and operations.
These application security assessments are often part of CISOs and
SecDevOps managers responsibility to manage by make sure processes are
followed to ensure compliance with standards and policies.

Although compliance might be a critical aspect of application security,
it is not the only one. Application security spans other security
domains that can be summarised as (GRC) Governance, Risk and Compliance.
Putting application security in perspective of GRC helps to align this
guide to CISOs roles and responsibilities when initiating, creating,
managing and improving application security programs as summarised
herein:

  - From the governance perspective, CISOs might be responsible for
    institute application security processes, the roles and
    responsibilities to manage them including security training and
    awareness. Training might also include secure coding for software
    developers, threat modelling for application architects and
    vulnerability testing for pen testers.
  - From the risk management perspective, the risks managed by the CISOs
    might also include managing application security risks, such as the
    risks of exploit of gaps in security controls and application
    vulnerabilities. SecDevOps managers might be responsible for
    application vulnerability management as well as managing application
    security throughout the software development life-cycle (SDLC).
  - From compliance perspective, compliance with application and
    software security standards might be among both CISO and SecDevOps
    managers role and responsibility to manage. Compliance with industry
    standards (e.g. PCI-DSS) might be one of the reasons for starting an
    application security programs for the organisation including hiring
    staff for managing and executing the various application security
    activities that the program/initiative entails.

### Part I: How To Initiate Application Security Program(s)

-----

[Go to Part I:](CISO_AppSec_Guide_v2:_How_To_Start "wikilink")

In part I we guide CISOs and SecDevOps managers in the initial steps
that lead to the creation of an application security program. Initially
is is important to creating awareness within the organisation in
regarding the need to institute an application security program and then
create business cases and gain commitments from the business/sponsors of
the program. An example of creating awareness is to explain the
difference between application and software security and between the
approach of security built in vs. the security bolt on. An example of
creating a business case is save money spent on fixing vulnerabilities
late in the SDLC by focus on proactive security (i.e. manage issue early
in the SDLC) vs reactive security (i.e. catch issues late in SDLC and
apply costly patches to applications that are already deployed).

When creating the business cases for investing in application security,
CISOs need to be real about cyber-threat risks and present to the
business the overall picture of information security risks, not just
compliance and vulnerabilities, but also security incidents and threat
intelligence of threat agents targeting the organization information
assets including for applications. The ability to communicate risks to
the business empowers CISOs to articulate the business case for
application security and justify additional spending in application
security measures. This justification needs to consider the economical
impact of security incidents compared with the costs of unlawful non
compliance. Today's costs to the business due to the economical impacts
of security incidents are much higher than the costs of non-compliance
and failing audits. Often the severity of the impact of security
incidents might costs CISOs their jobs and the company losing reputation
and revenues. In part I of this guide we provide CISOs guidance on how
to build a business cases from cyber-threat risk perspective with useful
examples for estimating the business impact caused by exploitation of
web application vulnerabilities.

Managing risk is about prioritising the mitigation effort based upon the
level of risk but also to align security priorities to the business
priorities (i.e. referred to the appetite for risk of the organisation
). This alignment is the first step towards establishing the relevance
of every security initiative and shows business management how security
supports their mission. Besides alignment between application security
and business priorities it is important to align to the capabilities of
the organisation and specifically to the maturity of software security
processes executed within the organisation. The main challenge that
CISOs and SecDevOps managers might face is on where to put the
focus/effort for the biggest gain by the "buck" being invested into the
application security program. After a measurement of the software
security maturity of processes (e.g. SAMM, BSIMM) being executed CISOs
might find that the organisation is not ready yet to start an
application security program without investment in tools, training and
processes (i.e. ad-hoc process execution, no documented standards and
sporadic use of tools). These measurements allow the CISO to gain
visibility and assess company culture by asking the right questions.

Starting an application security program might also be triggered by
compliance events such as the need to comply to specific industry
standards (e.g. testing web applications for OWASP T10 to comply with
PCI-DSS) or by a security event such as data compromise cause by an
exploit of vulnerabilities in a web application.

Independently from the "triggers" is is important that the CISOs set
realistic expectations of the risk reduction that can be achieved based
upon the resources out in place. and created a roadmap for creating the
application security program including training of the software
development team, on boarding of application security tools and
technologies following proof of concepts and pilots.

The most important aspect that CISOs and SecDevOps mangers need to focus
upon during the initial phases of the application security program is to
gain commitments from the sponsors of the application and software
security initiative as well as from the application security
stakeholders that, besides the business managers, include program
managers, software developers/engineers and testers. This level of
commitment depends also on the approach taken by the organisation to
push the application security initiative within the organisation.
Possible approaches are either a top down approach where in the driving
seat is the CEO/business. Example of top down approach might include a
two months freeze on development, every developer on security training,
S-SDLC to be created and executed by all teams and for all projects. A
bottom up approach is where in the driving seat are CISO and SecDevIps
Managers and there is need to partner and working together with DevOp
managers that might agree to commit developers to secure training and
demand secure code reviews and testing to be executed in compliance with
application security standards.

### Part II: How To Create Application Security Program(s)

-----

[Go to Part II:](CISO_AppSec_Guide_v2:_How_To_Create "wikilink")

Creating an an application security program involves planning for the
adoption of new application security activities, processes, controls and
training. When planning for new application security processes and
controls, it is important for CISOs to know on which application
security domains to invest, in order for the business to deliver on its
missions.

'To build and grow an application security program, CISOs must:

""Create a Roadmap""

  - Map business priorities to security priorities
  - Assess the current state using a security program maturity model
  - Establish the target state using a security program maturity model

<!-- end list -->

  - Assess software maturity for processes, training and tools
  - Document the software security standards and process (S-SDLC and
    SecDevOps)
  - Document security testing standards
  - Plan for adoption of application security tools (SAST, DAST)
  - Plan train developers on secure coding and use of tools
  - Set goals-objectives and time to reach them as milestones to track

Flesh out:

*Assess the current state using a security program maturity model*'

Accessing process maturity is a prerequisite for adoption of application
security and software security processes. One criteria that is often
adopted by organizations is to consider the organization's capabilities
in application security domains and the maturity of the organization in
operating in these domains. Examples of these application security
domains include application security governance, vulnerability risk
management, regulatory compliance and application security engineering;
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
security processes/tools such as architectural risk analysis/ threat
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

""Create the software security process (S-SDLC and SecDevOps)"" How to
Build Security In the SDLC Articulate SecDevOps and DevSecOps and what
entitles to. Building security During Agile and integration of security
during CI and CD

**Security Requirement Engineering** How can be done and when and how
and when can be validated

**Secure Code Reviews** Manual and automated, role of peer reviewers and
SAST and DAST

**Secure Build Testing** Breaking the builds for security

**Threat Modelling & Architecture Risk Analysis**

A top-down approach to identifying threats and countermeasures, CISOs
should consider a threat modeling technique also described in Part III.
The threat modeling technique allows the target application to be
decomposed to reveal its attack surface and subsequently its relevant
threats, associated countermeasures, and finally, its gaps and
weaknesses.

**Security-Vulnerability Testing** From ad-hoc to consistent execution
of quality and timing. Lite testing vs Deep Dive Testing Framing
threats, attacks and vulnerabilities in test scenarios Test Driven
Security

**Adoption of Application Security Tools** Articulate when and where in
the SDLC to use them (which phase) who need to use and how are deployed
including the value that they provide

**Emerging Application Security Technologies""** RASP document how can
be piloted before deployment

**Software Security Training** Articulate for who and what and document
in official document

""Create A Strategy With Goals For Activities""

  - teams trained on software security and threat modelling
  - apps/products in scope for vulnerability testing, secure code
    reviews and static build testing and consistently executed during
    changes
  - secure coding standards documented and adopted
  - security requirements are documented and validated with testing
    during the validation phase
  - quality of reports is consistent for level of false positives
  - issues are identified and remediated according to compliance time
    frames

""Application Security Program Deployment Plan""

  - Plan with milestones for reaching goals for activities and metrics
    to track goals
  - Plan should include governance model with roles and duties with RACI
    reflected in the previously created application security standards
    documents
  - Plan should include on boarding with tool and technologies including
    PoVs and PoCs before production deployment

### Part III: How to Manage Application Security Program(s)

-----

[Go to Part III:](CISO_AppSec_Guide_v2:_How_To_Manage "wikilink")

After the program has been created that is process and standards are
documented, application security testing activities, use of tools and
training need a plan for execution before these can be managed.

Activities can executed according to process requirements and
application and products are required to follow security requirements
during design, development and before deployment it is important to that
SecDevOps managers have resources such as project managers to be able to
track and manage execution for the process as well as measure and report
on the benefit of the program in term of increased security of the
application/product that is being developed and highlight this to the
business sponsors.

**Articulate process and program execution management vs
risk-vulnerability management**

Articulate process management CISOs and SecDevOps need to create a plan
and metrics to manage and monitor the people, processes, and
technologies that make up the application security program. Example
metrics for measuring governance, risk and compliance of application
security processes are also included.

Security metrics consist of three categories:

  - Application security process metrics
  - Application security risk metrics
  - Security in the SDLC metrics

**Application security process metrics**

These support informed decisions to decide where to focus the risk
mitigation effort and to manage application security risks more
effectively. These risk management goals are usually very organization
specific and depend on the type of organization and the industry sector
that the organization does business with, to decide which application
security risks should be prioritized for action.

  - How well is the organization meeting security policies, technical
    standards, and industry practices?
  - How consistently are we executing security SLAs? By application? By
    division? By channel?

**Application security risk metrics** From the risk management strategic
point of view, the mitigation of application security risks is not a one
time exercise; rather it is an ongoing activity that requires paying
close attention to emerging threats and planning ahead for the
deployment of new security measures to mitigate these new threats.

CISOs must prioritize security issues in order to identify areas needing
attention first. To make informed decisions on how to manage application
security risks, CISOs often need to assess the costs of fixing known
vulnerabilities and adoption of new countermeasures and to consider the
risk mitigation benefits of doing so. Costs vs. benefits trade offs are
critical to decide on which application security measures and security
controls to invest in to reduce the level of risk. Often CISOs need to
explain to executive management the risks to applications and to
articulate the potential business impacts for the organization in case
applications are attacked and confidential data is breached. Security
risks are business risks only when all three risk characteristics exist:

  - Viable threat
  - Vulnerability that may be exposed
  - Asset of value

To systematically prioritize risks for investment, CISOs should consider
a risk scoring methodology known as the Common Vulnerability Scoring
System Version 2.0 (CVSSv2). To help regularly communicate application
risk to the business executives, CISOs may consider providing “emerging
cyber-threat awareness” reports to executive management. Once
application security and software security investments are made, it is
important for CISOs to measure and report the status of governance, risk
and compliance of the application security program to Executive
Management. Furthermore, CISOs need to show the effectiveness of the
application security program investment and its impact on business risk.

  - Vulnerability risk management metrics - What is the Mean Time to
    Repair on an annual basis? On a monthly basis? By application? By
    division? What are the known security issues in production?
  - Security incident metrics - What security issues have been
    exploited? Were they known issues that were released in production?
    What was the cost to the business?
  - Threat intelligence reporting and attack monitoring metrics - Which
    applications are receiving more attacks than others? Which
    applications have upcoming expected peak usage?

**Security in the SDLC metrics**

One often neglected aspect when spending on software security is the
economics of dealing with insecure software applications. The investment
in software security to identify and fix security issues prior to
release of software in production actually pays for itself because it
saves the organization money. Patching vulnerabilities after
applications are released into production is very expensive; it is much
cheaper than to invest in secure architecture reviews to identify design
flaws and remediate them prior to coding, as well as to invest in secure
code reviews to identify and fix security bugs in software during
coding, and to ensure that releases are configured correctly.

  - Metrics for risk mitigation decisions - What is the Mean Time to
    Repair by an application's risk category? Does it meet expectations?
    What is the risk heat map by application? By division? By channel?
  - Metrics for vulnerability root causes identification - What are the
    root causes of vulnerabilities for each application? Is there a
    systemic issue? Which security practices have been best adopted by
    each development team? Which development teams need more attention?
  - Metrics for software security investments - Which SDLC phase have
    identified the most security issues? What is the maturity of the
    corresponding security practices in each SDLC phase? What is the
    urgency for more security people, process, and technologies in each
    SDLC phase? What are the cost-savings between security testing
    versus downstream vulnerability penetration testing? What are the
    cost-savings between issues identified in each phase?

'''Handling Application Changes Due to Integration With Emerging
Technologies '''

New application technologies and platforms such as mobile applications,
Web 2.0, and cloud computing services offer different threats and
countermeasure techniques. Changes to applications are also a source of
potential risks, especially when new or different technologies are
integrated within applications. As applications evolve by offering new
services to citizens, clients, customers and employees, it is also
necessary to plan for mitigation of new vulnerabilities introduced by
the adoption and implementation of new technologies such as mobile
devices, web 2.0 and new services such as cloud computing. Adopting a
risk framework to evaluate the risks introduced by new technologies is
essential to determine which countermeasures to adopt to mitigate these
new risks. This guide will provide guidance for CISOs on how to mitigate
risks of new threats against applications, as well as of vulnerabilities
that might be introduced by the implementation of new technologies.

  - Mobile applications
      - Example concerns: lost or stolen devices, malware,
        multi-communication channel exposure, weak authentication
      - Example CISO actions: Meeting mobile security standards,
        tailoring security audits to assess mobile application
        vulnerabilities, secure provisioning, and application data on
        personal devices.
  - Web 2.0
      - Example concerns: securing social media, content management,
        security of third party technologies and services
      - Example CISO actions: security API, CAPTCHA, unique security
        tokens in form posts, and transaction approval workflows.
  - Cloud computing services
      - Example concerns: multi-tenant deployments, security of cloud
        computing deployments, third party risk, data breaches, denial
        of service malicious insiders
      - Example CISO actions: cloud computing security assessment,
        compliance-audit assessment on cloud computing providers, due
        diligence, encryption in transit and at rest, and monitoring.

Today's threat agents seek financial gain such as by attacking
applications to compromise users' sensitive data and company’s
proprietary information for financial gain, fraud as well as for
competitive advantage (e.g. through cyber espionage). To mitigate the
risks posed by these threat agents, it is necessary to determine the
risk exposure and factor the probability and the impact of these threats
as well as to identify the type of application vulnerabilities that can
be exploited by these threat agents. The exploit of some of these
application vulnerabilities might severely and negatively impact the
organization and jeopardize the business.

**Highlighting Issues and Concerns Based Upon Metrics and Measurements**

  - Focus on positive highlighting the benefits (e.g. security
    vulnerabilities are identified and prioritised for remediation
    timely)
  - Discuss possible causes for program execution stalling with
    stakeholders and try to address the concerns
  - Fight common misconceptions that software security impacts
    cost/budget, development releases and performance
  - Adress push backs from developers that are tired to rebuild software
    for fixing vulnerabilities, project managers that worry about delay
    of releases for products, CISOs that worry about releasing with
    vulnerabilities not remediated and business that worry about staying
    within budget constraints as well as that want to see value on
    investment

### Part IV: How to Improve Application Security Program(s)

-----

[Go to Part IV:](CISO_AppSec_Guide_v2:_How_To_Improve "wikilink")

  - increase or re-state commitment from business sponsors to support
    the program and to provide budget increase
  - Incorporating the lesson learned from security incidents and
    released vulnerabilities/exploits
  - Incorporating feedback from business and from software development
    units
  - Efficient use of tools and focus on optimisation available manual
    resources
  - Increase focus on automation for processes including security tools
    for vulnerability testing
  - Automated source code validation and audits of false positives in
    reports
  - Real time protection and detection with instrumentation
  - Continuous Integration & Development Security Improvements
  - Following the application security strategy goals
  - Focus on identity and remediate vulnerabilities early during the
    SDLC
  - Improve the maturity of execution of software security activities
  - Promote benchmarking measures for process improvements
  - Measure both threat risk levels and vulnerability risks
  - Institute escalation procedures for problems
  - Nurture security champions/evangelists
  - Accountability and responsibility
  - Focus on motivations to do better including awards and incentives

[Category:OWASP Application Security Guide For CISO
Project](Category:OWASP_Application_Security_Guide_For_CISO_Project "wikilink")