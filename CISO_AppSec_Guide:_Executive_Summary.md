[\< Back to the Application Security Guide For
CISOs](Application_Security_Guide_For_CISOs "wikilink")

__NOTOC__

## Executive Summary

The fact that applications ought to be considered company's assets is
"per se" a good reason to put applications in scope for compliance with
information security policies and standards. The impact of compliance
with information security policies and standards for applications
typically depends on the classification of the asset-data stored by the
application, the type of exposure of the application to the users (e.g.
internet, intranet, extranet) and the risk of the functionality that the
application supports with the data (e.g. access to confidential data,
transfer of money, payments, users administration etc). From an
information security perspective, applications should be in scope for
organizations specific vulnerability assessments and application
security requirements. The security validations and certifications of
applications follow specific security requirements such as the secure
design, secure coding and secure operations. These are often part of the
goals of application security standards. Therefore, compliance is a
critical aspect of application security, and of CISOs responsibilities,
but not the only one. Application security spans other security domains
that CISOs are responsible for. These can be summarized as (GRC)
Governance, Risk and Compliance.

  - From the governance perspective, CISOs are responsible for institute
    application security processes, roles and responsibilities to manage
    them, and software security training and awareness for software
    developers such as defensive coding and vulnerability risk
    management for information security officers/managers.
  - From the risk management perspective, the risks managed by the CISOs
    also include application security risks, such as the risks of
    specific threats targeting applications that process confidential
    user data by seeking to exploit gaps in security controls as well as
    vulnerabilities in applications.
  - Among CISOs security domains, compliance with regulations and
    security standards is often the one that gets the most attention
    from the organization's executive management. The aim of this guide,
    is to help CISOs fulfill compliance requirements as well as to use
    compliance requirements as one of the reasons for justifying
    investments in application security. For some organizations,
    managing risks of security incidents such as credit card fraud,
    theft of personal identifiable information, theft of intellectual
    property and confidential data is what gets most of the executive
    management attention, especially when the organization has been
    impacted by data breach security incidents.

### Part I: Reasons for Investing in Application Security

-----

[Go to Part I: Reasons for Investing in Application
Security](CISO_AppSec_Guide:_Reasons_for_Investing_in_Application_Security "wikilink")

In this digital era, public and private organizations serve an
increasing number of citizens, clients, customers and employees through
web applications. Often these web applications provide “highly trusted
services” over the internet, including functions that bear high risk for
the business. These web applications are the target of an
ever-increasing number of fraudsters and cyber-criminals. Many incidents
result in a denial of online access, breach of customer data and online
fraud.

Chief Information Security Officers (CISOs) are tasked to enforce
application security measures in order to avoid, mitigate and reduce
security risks affecting the organization's ability to deliver on its
mission. This evolving threat landscape further drives audit, legal and
compliance requirements. CISOs must create a business case for investing
in an application security program. The business case should be mapped
to the security threats on the business and the program services
necessary to serve as a countermeasure. Industry security spending
benchmarks and quantitative risk calculations provide support to
security investment budget requests.

### Part II: Criteria for Managing Application Security Risks

-----

[Go to Part II: Criteria for Managing Application Security
Risks](CISO_AppSec_Guide:_Criteria_for_Managing_Application_Security_Risks "wikilink")

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
cyber-threat awareness” reports to executive management.

**Communicating to business executives**

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
and revenues.

**Threat modeling**

A top-down approach to identifying threats and countermeasures, CISOs
should consider a threat modeling technique also described in Part III.
The threat modeling technique allows the target application to be
decomposed to reveal its attack surface and subsequently its relevant
threats, associated countermeasures, and finally, its gaps and
weaknesses.

**Handling new technology**

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

### Part III: Application Security Program

-----

[Go to Part III: Application Security
Program](CISO_AppSec_Guide:_Application_Security_Program "wikilink")

From the risk management strategic point of view, the mitigation of
application security risks is not a one time exercise; rather it is an
ongoing activity that requires paying close attention to emerging
threats and planning ahead for the deployment of new security measures
to mitigate these new threats. This includes the planning for the
adoption of new application security activities, processes, controls and
training. When planning for new application security processes and
controls, it is important for CISOs to know on which application
security domains to invest, in order for the business to deliver on its
missions.

'To build and grow an application security program, CISOs must:

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

### Part IV: Metrics For Managing Risks & Application Security Investments

-----

[Go to Part IV: Metrics For Managing Risks & Application Security
Investments](CISO_AppSec_Guide:_Metrics_For_Managing_Risks_&_Application_Security_Investments "wikilink")

Once application security and software security investments are made, it
is important for CISOs to measure and report the status of governance,
risk and compliance of the application security program to Executive
Management. Furthermore, CISOs need to show the effectiveness of the
application security program investment and its impact on business risk.

CISOs also need metrics to manage and monitor the people, processes, and
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

**Application security risk metrics**

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

[Category:OWASP Application Security Guide For CISO
Project](Category:OWASP_Application_Security_Guide_For_CISO_Project "wikilink")