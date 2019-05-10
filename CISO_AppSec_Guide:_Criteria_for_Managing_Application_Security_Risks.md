[\< Back to the Application Security Guide For
CISOs](Application_Security_Guide_For_CISOs "wikilink") __NOTOC__

# Part II: Criteria for Managing Application Security Risks

## II-1 Executive Summary

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

To systematically prioritize technical risks for remediation, CISOs
should consider a risk scoring methodology known as the Common
Vulnerability Scoring System Version 2.0 (CVSSv2). To help regularly
communicate application risk to the business executives, CISOs may
consider providing “emerging cyber-threat awareness” reports to
executive management.

**Communicating to business executives**

CISOs need to be real about cyber-threat risks and present to the
business the overall picture of information security risks, not just
compliance and vulnerabilities but also security incidents and threat
intelligence of threat agents targeting the organization information
assets including for applications. The ability to communicate risks to
the business empowers CISOs to articulate the business case for
application security and justify additional spending in application
security measures. This justification needs to consider the economical
impact of security incidents compared with the costs of unlawful non
compliance. Today's costs to the business due to the economical impacts
of security incidents are much higher than the costs of non-compliance
and failing audits. Often the severity of the impact of security
incidents might cost CISOs their jobs and the company losing reputation
and revenues.

**Threat modeling**

A top-down approach to identifying threats and countermeasures, CISOs
should consider a threat modeling technique also described in Part III.
The threat modeling technique allows the target application to be
decomposed to reveal its attack surface and subsequently its relevant
threats, associated countermeasures, and finally, its security control
gaps and design flaws.

**Handling new technology risks**

New application technologies and platforms such as mobile applications,
Web 2.0, and cloud computing services offer different threats and
countermeasure techniques. Changes to applications are also a source of
potential risks especially when new or different technologies are
integrated within applications. As applications evolve by offering new
services to citizens, clients, customers and employees, it is also
necessary to plan for mitigation of new vulnerabilities introduced by
the adoption and implementation of new technologies such as mobile
devices, web 2.0 and new services such as cloud computing. Adopting a
risk framework to evaluate the risks introduced by new technologies is
essential to determine which countermeasures to adopt to mitigate these
new risks. This guide will provide guidance for CISOs on how to mitigate
risks of new threats against applications as well as of vulnerabilities
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

## II-2 Introduction

Once an application has been targeted by an attack and the organization
has suffered either a data breach incident or fraud as result of it, it
is important to understand the root causes (e.g. vulnerabilities,
control gaps) of the incident and to invest in security measures that
will prevent such incident from occurring again. In this section of the
guide, we address how to target spending to mitigate the risk posed by
specific attacks and vulnerability exploits that caused data breach
incidents. As best practice, we are not advocating to fix only
vulnerabilities that might have been the cause of the incident even if
these are the ones that need to be prioritized first for remediation to
limit further damage. Vulnerabilities that might have been already
exploited to attack the application certainly represent the highest
probability to be also exploited in future targeted attacks.

The main question for the CISO is also to whether the same
vulnerabilities can be used in attacks in the future against
applications that have a similar functionality and type of data.
Nevertheless, the application might have other types of vulnerabilities
that might be opportunistically exploited by an attacker. These are
vulnerabilities that either enable or facilitate an attacker to conduct
the attacks against applications. The main point is that since the risk
of data breaches and online fraud are a factor of likelihood and impact
of vulnerabilities, it is important to consider likelihood and impact as
factors to determine which issues to target for spending. In general,
vulnerabilities are prioritized based upon technical risks not business
impact, for example, vulnerabilities that yield high technical risks are
prioritized for remediation over low risk ones. A vulnerability of high
technical risk can be SQL injection, for example, independently from the
data asset and the value that such asset has for the organization.
Clearly if that SQL injection vulnerability is affecting either
authentication or confidential data it might represent a very different
risk to the organization than a SQL injection vulnerability that might
affect data that is considered of low risk for the organization such as
marketing research data, for example. The impact might be more of
reputation risk in this case rather than data breach risk.

In part I of this guide we provide business cases that CISOs can use to
request budget for application security. Application security budget
typically need to cover several information security and risk governance
needs. Besides the usual need to spend for compliance with information
security standards, policies and regulations, CISOs might advocate
additional budget to address mitigation of increased risks of data
breach incidents. One critical factor is to quantify the impact of the
data breach incident that already occurred. This implies that the CISOs
are authorized to access data in relation to data breach incidents such
as incident reports filed by the Security Incident Response Teams
(SIRT), data from legal in relation to law suits and regulatory fines
and fraud data that includes amount of money losses incurred because of
online fraud. All this type of information is essential to determine the
overall impact. In absence of this data, the best the CISO can do is to
use data breach incident data from public sources and data breach
incident reports. In part I of this guide, we provided some examples of
how this data can be used to estimate impact. We documented what are the
critical factors to estimate impacts of data breaches: these as the
value of the data assets (e.g. citizen, client, employee or customer
confidential and personal identifiable information, credit cards and
bank account data) and the liability for the organization in case these
assets are lost. Once the potential business impact of a data breach is
estimated, the next step is to determine how much should be spent to
mitigate the risk. At high level, this is a risk strategy decision that
depends on the organization risk culture and the organization priorities
for mitigating risks.

Depending on the type of organization, the number one priority can be
"to not to be caught in unlawful non-compliance" such as in case of
suffering a data breach and additionally failing to comply with
compliance with PCI-DSS standards. This can be the case of a small
company that provides online payment processing services and who could
lose business from credit card issuers and additional fines, law suits
and audit and legal costs. For an organization such as an engineering or
research organization whose patents and trading secrets are critical
assets, the protection from internal threats of commercial or country
sponsored spying might represent number one priority. In general, it is
important to address application security as a business enabler for
protecting digital assets whose value is represented in terms of costs
of security measures vs. benefits in protecting the digital assets. In
part I of the guide we present one criteria that can be used as the one
that optimizes spending by maximizing risk mitigation value while
minimizing the security costs. Another criteria, is to consider security
not as a tax but as an investment, this criteria is the Return of
Investment in Security (ROSI). The ROSI can be used for making both
tactical and strategic risk mitigation decisions. Tactically, ROSI can
be used to decide which security measures should be targeted for
spending by considering the cost vs the effective of the measure in
mitigating the impact of the data loss. Strategically, ROSI can be used
to decide which application security activities to invest in the SDLC
such as the ones that will bring money savings in the long term.

## II-3 Defining Risk

Before we discuss how to manage application security risks, we need to
use a consistent terminology. According to the OWASP Top Ten Risks to
Web Applications, the characterization of risk of vulnerability is as
such “Attackers can potentially use many different paths through your
application to do harm to your business or organization. Each of these
paths represents a risk that may, or may not, be serious enough to
warrant attention.”

![<File:2010-T10-ArchitectureDiagram.png>](2010-T10-ArchitectureDiagram.png
"File:2010-T10-ArchitectureDiagram.png")

This section will discuss:

  - Prioritizing Overall Risk
  - Understanding Risk Drivers
      - Threat Agents
      - Attacks, Weaknesses (Vulnerabilities), and Controls
        (Countermeasures)

## II-4 Prioritizing Overall Risk

Prioritizing risks from known vulnerabilities is a reactive but tangible
approach to managing clear business risk. These risk characteristics are
useful to CISOs for determining the risks to the business of a threat
agent exploiting either vulnerabilities or control weaknesses and gaps
to compromise an asset and cause a negative impact to the business. To
note that the value of the asset has nothing to do with the asset’s cost
of financial value is the relative value that the organization places
into the asset in the case this asset is either lost or compromised.

<center>

|                                                                                                                                  |
| -------------------------------------------------------------------------------------------------------------------------------- |
| Business risk occurs when there is a likelihood (probability) of a threat to the system, a vulnerability, and an asset of value. |

</center>

Business risk from security issues is driven by:

  - Threat Likelihood (TL) - probability of the occurrence of the threat
  - Vulnerability Exposure (VE) - probability of the exposure of the
    vulnerability to the threat
  - Asset Value (AV) - business impact

![<File:Risk_definition_medium.png>](Risk_definition_medium.png
"File:Risk_definition_medium.png")

CISOs should use a consistent approach to characterizing technical risks
to known vulnerabilities. This can be accomplished using a risk scoring
methodology such as the Common Vulnerability Scoring System Version 2.0
(CVSSv2). There are many in use today, CVSSv2 is one such methodology.
When using a risk scoring methodology, it is critical to not only score
a vulnerability based on likelihood and business impact, but also its
context within your organization. This allows CISOs to prioritize risks
to drive application security investment. OWASP is the primary source to
provide organizations with the top ten web application risks that need
to be mitigated. The testing of OWASP Top 10 might require organizations
to routinely perform security testing of these vulnerabilities in web
applications. Once the vulnerabilities are identified and the severity
assigned to these, it is important to have a vulnerability management
process that allows managers to prioritise the fixes of these
vulnerabilities by risk severity but also by the business impacts they
might cause in the case these will be exploited by an attacker. However,
vulnerabilities are just one aspect of risk mitigation for application
security risks.

<table>
<caption>About CVSSv2: A Methodology to Prioritize Risk</caption>
<tbody>
<tr class="odd">
<td><ul>
<li>Online Calculator - <a href="http://nvd.nist.gov/cvss.cfm?calculator&amp;adv&amp;version=2">http://nvd.nist.gov/cvss.cfm?calculator&amp;adv&amp;version=2</a></li>
<li>CVSSv2 guide - <a href="http://www.first.org/cvss/cvss-guide.html">http://www.first.org/cvss/cvss-guide.html</a></li>
</ul>
<p>This risk scoring system utilizes multiple data points to assess risk:</p>
<ul>
<li>Base Metrics
<ul>
<li>Access Vector (AV)</li>
<li>Access Complexity (AC)</li>
<li>Authentication (Au)</li>
<li>Confidentiality Impact (C)</li>
<li>Integrity Impact (I)</li>
<li>Availability Impact (A)</li>
</ul></li>
<li>Temporal Metrics
<ul>
<li>Exploitability (E)</li>
<li>Remediation Level (RL)</li>
<li>Report Confidence (RC)</li>
</ul></li>
<li>Environmental Metrics
<ul>
<li>Collateral Damage Potential (CDP)</li>
<li>Target Distribution (TD)</li>
<li>Security Requirements (CR, IR, AR)</li>
</ul></li>
</ul></td>
</tr>
</tbody>
</table>

-----

## II-5 Understanding Risk Drivers: Threats and Countermeasures

CISOs should adopt a threat modeling technique to drive risk scoring.
Per OWASP's Application Threat Modeling
(https://www.owasp.org/index.php/Application_Threat_Modeling), "threat
modeling is an approach for analyzing the security of an application. It
is a structured approach that enables you to identify, quantify, and
address the security risks associated with an application."

### About threat agents

A threat agent (https://www.owasp.org/index.php/Category:Threat_Agent)
“is used to indicate an individual or group that can manifest a
threat. It is fundamental to identify who would want to exploit the
assets of a company, and how they might use them against the company.” A
threat agent can be defined as the function of his capabilities,
intentions and past activities:

`     Threat Agent = Capabilities + Intentions + Past Activities`

A threat agent can be characterized as the intersection between the
agent’s motives, the specific type of attacks used and the
vulnerabilities that are exploited.

![<File:ThreatAgentIntersection.png>](ThreatAgentIntersection.png
"File:ThreatAgentIntersection.png")

### The growing maturity of threat agents

By identifying the threat agent intentions and the capabilities such as
the types of attacks used against applications and the vulnerabilities
that are exploited, CISOs can assess likelihood and business impact. As
cyber threats evolve, it is important to understand what these threat
agents are, their intentions and the past activities (e.g. the type of
attacks used by them). By analyzing how threats evolve, CISO can adapt
application security measures to mitigate the risks of these threats.

In the past decade, threat agents have radically changed and matured.
Historically, threat agents began as an opportunistic venture --
targeting anyone with a vulnerability, regardless of asset value.
Today's threats are targeted, usually known as the Advanced Persistent
Threat.

  - Script kiddies, worms and virus authors
  - Fraudsters & cyber-criminals
  - Hacktivists
  - Cyber-spies
  - Advanced persistent threat (APT) agents

#### Script kiddies, worms and virus authors

Between the years 2000 and 2005, the main threats agents could be
characterized as the so called “script kiddies” seeking to gain
notoriety by hacking into government systems using easy-to-find
techniques and scripts to search for and exploit weaknesses in other
computers as worm and virus authors seeking to spread them for causing
notable major computer disruptions and get famous as a result.
Historically, the primary targets of these threat agents weren’t
websites but computer hosts for the sake of getting notoriety by
infecting them with viruses and worms. Notable script kiddie of the late
90s includes Jonathan James, known as "cOmrade" on the Net, that pleaded
guilty to intercepting 3,300 emails, stealing passwords, and nicking
data by using network sniffers installed by compromising servers of US
Dept of Defense with backdoors. In the year 2000, Jeanson James Ancheta
created a worm that allowed him to infect as many computers on the
Internet as he could with off-the-shelf Remote Access Trojans (RATs).
Over time, he amassed about 40,000 worm-infected remote access computers
(also known as bots). In the same year 2000, Onel Deguzman authored the
ILOVEYOU virus that spread by emails to 10 million hosts worldwide
costing companies an estimated $ 5.5 billion dollars for cleaning it. In
the year 2000, a 15 year script kiddie, Michael Calce known as “mafia
boy” takes down eBay, Amazon and CNN websites for 90 minutes by
accidental use of a file sharing tool. Notable worm author of the year
2004 is Sven Jascham author of the Sasser worm that is estimated to have
impacted 10 million hosts. The impact of the Sasser worm included
disabling hosts for satellite communications, disabling hosts for
operation of air lines trans-Atlantic flights and disabling hosts for
financial organizations and hospitals. Today CISOs need to be on the
threat alert for today’s script kiddies threat agents using readily
available tools that look for common exploits of known vulnerabilities
to expose them to the public. CISOs need to make sure that systems and
applications are not vulnerable to these easy exploits since this might
severely impact the organization operations when critical hosts are
infected and disabled as well as damage the company reputation when news
of these exploits are posted on social media (e.g Twitter).

#### Fraudsters & cyber-criminals

In the years between 2005 and 2010, the motives of the threat agents
shifted from hacking for fame and notoriety to hacking for financial
gain. During this period, the targets of the attacks also shifted from
hosts to websites and the motives for the attacks changed from causing
disruption using viruses and worms to stealing confidential and
sensitive data such as personal data for identity theft and credit and
debit card data for credit card fraud. In the year 2007 for example,
Albert Gonzales and other three conspirators succeeded in stealing 130
million credit card numbers from Heartland Payment Systems, a New Jersey
card payment processor; 7-Eleven, the Texas-based convenience store
chain; and Hannaford Brothers, a Maine-based supermarket chain. The
attackers used SQL Injection attacks that resulted in the placement of
malware to sniff the network for credit card data used at retail stores.
They later engaged in ATM fraud by encoding the data on the magnetic
stripes of blank cards and withdrawing tens of thousands of dollars at a
time from ATMs.

  - In 2010, a cyber-criminal gang of 37 Russian hackers succeeded in
    stealing $ 3 million from online bank accounts by infecting online
    bank users PCs with the ZEUS banking Trojan. The ZEUS Trojan is
    specifically designed to steal banking information by using man in
    the browser, key logging and attacking online banking applications
    by hijacking the session and by taking over the victim bank
    accounts.
  - In 2012, banking malware became more sophisticated when malware
    named “GameOver” was designed to steal user’s online banking
    credentials by defeating common methods of multi factor
    authentication employed by financial institutions as well as to
    perform wire transfers using the victims’ credentials without
    requiring any interaction from the victim during the attack. For
    CISOs at financial institutions, understanding how these threat
    agents and malware attacks seek to compromise user’s online
    credentials and bypass multi factor authentication is critical in
    determining which countermeasures can be deployed to protect the
    financial institutions from these attacks. Often CISOs at financial
    organizations subscribe to “threat intelligence services” so that
    they are notified when customer's online credentials and bank and
    credit card data have been recovered from Zeus Command and Control
    and “dropping” servers. Typically these alerts are the outcome of
    ZEUS malware hosted botnets being taken down by law enforcement.
    Based upon this information, CISO can inform the businesses to take
    actions to limit the impact, such as notifying the customers and
    suspending and replacing credit and bank accounts.

#### Hacktivists

In the years between 2010 and 2012, a new class of threat agents emerged
that seek to attack government and corporate websites for political
motives. These are computer hacker groups, such as Lulzec and Anonymous.
In 2011, Lulzec claimed responsibility for compromising user accounts
and credit card data users of the Sony’s PlayStation Network while
Anonymous claimed responsibility for defacing the site of the company
HBGary federal and publishing several thousand of client’s emails. These
threat agents are commonly referred to as “hacktivists” and seek to
attack websites not for financial gain but for exposing corporate and
government owned information to the public. It is important for CISOs to
notice, that according to the 2012's Verizon Data Breach Investigation
Report (released on March, 22nd 2012), even if hacktivists caused a
small percentage of incidents (3%) hence affecting a low probability,
overall, they account for the largest impact in terms of volume of data
records compromised (58%). According to the Verizon's report,
hacktivists are more likely to attack large organizations rather than
small ones since these provide them with the most return of investment
(i.e. from the attacker's perspective) in terms of data that can be
compromised and disclosed to public. CISOs in large private and public
(e.g. Government) organizations that have a known public brand should
consider the risk of confidential data (e.g. names, last names and
emails) and confidential personal identifiable data (e.g. names, last
names and card numbers) as high risk. CISOs responsible for the security
of both government and corporate hosted and managed websites that store
customer's confidential and personal identifiable information, might
likely become the target of hacktivists for political reasons and need
to worry about reputation damage impacts also resulting from public
disclosure of website vulnerabilities. Hacktivists often engage in
attacking the organization's employees and customers with spear phishing
and their websites with SQL injection, Cross Site Scripting and web
service vulnerability exploits for the sake to steal and post the
compromised information online. Another type of attack that CISOs
managing government and corporate websites need to worry about are
disruptions due to Distributed Denial of Service (DDoS) attacks.
Typically, Hacktivists target websites with DDoS hosted at financial and
government organizations for political reasons. For example, several
credit card sites such as Mastercard.com and Visa.com were attacked in
2011 by Anonymous with DDoS in retaliation of removing WikiLeaks
operators among the VISA's and MasterCard's clients.

#### Cyber-spies

Since the years 2011 and 2012, besides hacktivists, fraudsters and
cyber-criminals, another class of new threat agents that some of the
CISO of international organizations, governments, financial, defense and
high tech engineering type of companies need to deal with are
cyber-spies seeking to compromise websites for stealing top secrets,
financial restricted and intellectual property type of information such
as company’s trading secrets. These type of attacks often involve the
use of Remote Access Tools (RATs) as publicly revealed by McAfee in the
operation Shady RAT report. In this 2011 study, it is reported that
these type of attacks went on for several years starting in mid-2006,
impacting "at least 72 organizations, including defense contractors,
businesses worldwide, the United Nations and the International Olympic
Committee". These type of cyber espionage attacks involved the use
“spear-phishing email containing an exploits sent to an individual
with the right level of access at the company, and the exploit, when
opened, in an unpatched system, will trigger a download of the implant
malware”. Spyware malware typically execute and initiate a backdoor
communication channel to the C\&C web server and interpret the
instructions encoded in the hidden comments embedded in the webpage
code.” Besides spear-phishing, cyber espionage tools can spread also by
compromising web servers via SQL injection
(http://www.mcafee.com/uk/about/night-dragon.aspx), infected USBs, and
infected hardware or software. The analysis of some of the most recently
used cyber-spying malware seems to indicate that these are developed by
countries engaged in cyber espionage. In 2012 for example, Kaspersky
labs identified a cyber-spying malware such as “Gauss” that bear code
similarities with other cyber-espionage tools such as Flame and
cyber-war tools like Stuxnet. According to Kaspersky, Gauss is “designed
to steal sensitive data, with a specific focus on browser passwords,
online banking account credentials, cookies, and specific configurations
of infected machines.

#### Advanced persistent threat (APT) agents

Often cyber-espionage activities are associated with APTs (Advanced
Persistent Threats). APTs are characterized by advanced that is use
sophisticated methods, such as zero-day exploits and persistent that is,
the attackers return to target systems over and over again with a long
term objective of achieving his goals without detection. Historical APTs
include operation Aurora targeting Google, Juniper, Rackspace and Adobe
companies as well as operation Nitro, Lurid, Night Dragon, Stuxnet and
DuQu. CISOs of government organizations as well as corporations whose
protection of intellectual property and confidential and restricted
information constitute a primary concern, need to be aware they might
become the target of APTs seeking to target employees and customers with
spear phishing to infect PCs with spyware, as well as to exploit system
and web application vulnerabilities like SQL injection for installation
and dissemination of cyber espionage tools.

### About attacks and vulnerabilities

In this section of the guide we will describe how to proactively manage
the risks posed by specific types of attacks, such as threat agents
whose motives and attack goals have been previously analyzed. Typically,
risk mitigation consists of fixing vulnerabilities as well as applying
new countermeasures. The choice of which vulnerabilities are critical to
mitigate starts first with the understanding of the threat scenarios and
the threat agents motives, especially of hacking and malware and how
these threat agents might adversely target applications leading to
compromise of the data assets as well as of critical business functions.
One critical tool that CISOs can use to prioritize risk is the use of
risk frameworks that factor the threat agents, the technical risks posed
by application vulnerabilities that the threat agent seeks to exploit
and the business impacts. The risk profile of each application is
different depending on the inherent values of the asset whose business
impact depends upon and the likelihood as the application might be
targeted by a threat agent. After vulnerabilities are prioritized for
remediation, it is important to consider the effectiveness of existing
countermeasures and identify any gaps in risk mitigation measures that
require the CISO to consider new countermeasures. The control gap
analysis can be used to determine which countermeasures need to be
implemented based upon security principles. The principle of defense in
depth can be used to identify gaps and these gaps can be filled by
applying countermeasures. To decide on which countermeasures to invest,
CISOs should consider both the costs and the effectiveness of new
countermeasures in mitigating the risks. To decide how much should be
spent in countermeasures, the calculation of potential financial losses
as factor of likelihood and impact to determine the financial liability
can also be used as criteria.

#### Script kiddies attacks

In the case of script kiddies, the attacks that CISO need to be prepared
to defend from are the ones seeking to run scripts and off the shelf
vulnerability scanning tools for the sake of identifying application
vulnerabilities. Among the script kiddies goals are to probe websites
for common vulnerabilities and when these are identified, they often
seek to disclose them to the public for fame and notoriety.

Since script kiddies often seek to identify vulnerabilities and not
necessarily to exploit them for data compromise, the impact for the
business is often reputation damage. Assuming that this vulnerability
discovery is limited to running vulnerability scanning tools, the main
vulnerabilities that CISOs need to worry about are the ones that are
most common, more precisely, the ones that OWASP Top 10 characterizes as
‘widespread” and “easy to detect” such as cross site scripting (OWASP A2
XSS), Cross Site Request Forgery (OWASP A5-CSRF) and security
misconfigurations (OWASP A6-Config.). Other these vulnerabilities are
disclosed to the public without contacting the organization whose web
application has been identified to be vulnerable. When these are
disclosed to public, they might obviously also increase the risk to the
organization since these might be exploited to compromise the website as
well as the data. It is therefore important that CISOs pay close
attention to script kiddies threat and remediate this type of
vulnerabilities. In some cases, these vulnerabilities are published in a
public accessible database after the owners of the vulnerability have
been contacted and offered help to remediate. For example xssed.org
collects and validates information about XSS vulnerabilities and
publicly tracks them for remediation as well as offers a service to
notify organizations when these vulnerabilities are released to public.

CISOs cannot assume that reputation damage is just restricted to the
organization’s vulnerabilities being released to the public since
vulnerabilities can be occasionally exploited for defacing the website
and publishing unauthorized content. Examples of vulnerabilities that
can be exploited for defacing includes exploit of file injection
vulnerabilities such as Cross Frame Scripting (XFS), that is part of
(OWASP A1:Injection) group. For mitigating the risk of these
vulnerabilities, CISOs need to invest in vulnerability scanning tools
for testing them before the web application is released into the
production environment. Additionally, the focus should be given to
building secure software whose components and libraries such as the
OWASP ESAPI (Enterprise Security API) “a free, open source, web
application security control library that makes it easier for
programmers to write lower-risk applications.”

Besides investing in vulnerability testing and secure software to
mitigate the risk of reputation type impacts, CISOs can also invest in
attack monitoring and detection measures such as WAF (Web Application
Firewalls). Since these types of vulnerabilities are easy to identify
and widespread among web applications, they are also the ones that
websites are most probed for, therefore knowing when a web application
is a target of a script kiddie attack can be used for further monitor
the activities and issue alerts in case the attacks are not limited to
probing the website but to try to exploit the vulnerability of
compromised data.

#### Fraudsters and cyber-criminals attacks

Fraudsters and cyber-criminals attack websites that represent an
opportunity for them for financial gain. Examples are websites that
process credit card payments such as e-commerce websites, websites that
allow access to credit and debit card data as well as bank accounts and
perform financial transactions and wire transfers, such as online
banking websites and any website that stores and collects private
information, such as Personal Identifiable Information of an individual.
Besides committing fraud by attacking the financial transactions such as
payments and money transfers that the websites supports, other types of
attacks that are sought by fraudsters are the ones that are allowed
unauthorized access to sensitive data, such as credit and debit card
data that can be used for card non present financial transactions and to
counterfeit cards, as well as personal identifiable information that can
be used for impersonating the victim for identity theft.

By taking into consideration these attacker financial goals, any
vulnerability that allows the fraudster/cyber-criminal to control
payments and money transfers as well as to gain unauthorized access to
sensitive data is very likely to be the target for an exploit. First and
for most, these are vulnerabilities that can be exploited for gaining
un-authorized access to e-commerce and financial type of applications.
These include exploit of weak authentication and session management
vulnerabilities (OWASP A3- Broken Authentication and Session Management)
since the exploit might allow for compromised credentials for accessing
the web applications such as username and passwords as well as
SessionIDs for impersonating the victim. Other likely vulnerability
exploits might include the exploit of the Cross Site Request Forgery
(OWASP-A5-CSRF) vulnerability to ride the session for performing
un-authorized financial transactions such as payments and money
transfers. Among the most damaging web application vulnerabilities that
fraudsters and cyber-criminals might seek to exploit are SQL injection
(OWASP- A1-Injection), access to sensitive data by manipulating
unprotected parameters such as direct references (OWASP A4 Insecure
direct object reference), exploit of failure of the web application to
restrict URL access (OWSP A8-Failure to Restrict URL Access), poor or
non-existent cryptographic controls to protect confidential data in
storage (OWASP A7-Insecure Crypto Storage) and in transit (OWASP
A9-Insufficient Transport layer protection. In the case the CISOs are
responsible for managing risks of inherently risky websites such as
e-commerce, online banking and sites that process confidential and
personal information such as for insurance, loans, credit they need to
focus on testing and fixing these vulnerabilities since these are the
most likely to be exploited and cause the highest business impact.

Application layer intrusion detection rules (IDS) can also be embedded
within the web application as OWASP ESAPI or in the web server such as a
WAF (Web Application Firewall) can log and monitor suspicious activity
and trigger alerts for potential fraud attempts.

Application threat analysis and modeling is the key activity for
determining the exposure of applications to threats and to determine how
to protect the data from the impact of these threats. From a threat
analysis perspective, after threat agents and their motives and attacks
are identified it is important to analyze the probable attack scenarios,
identify the attack vectors used and the vulnerabilities that can be
exploited. An attack tree can help to translate the attacker goals into
the means to realize these goals. From the attacker perspective, the
main goal is to pursue attacks that are easier and cheaper to conduct
and have the highest probability to succeed rather than otherwise. For
example, consider that credit card and account data can be purchased
from cyber-criminal organizations on the black market and if it is
easier, cheaper and less risky for a fraudster than to break into an
application, this is probably what a fraudster will do. If the website
that stores credit card data has open vulnerabilities that are easily
exploitable to get credit card data, probably the fraudster will attack
this website first instead. From a CISOs perspective, fixing of
application vulnerabilities that can be exploited by a fraudster can be
justified as reduced opportunity for exploiting them. Attack trees can
also be useful to understand the realization of possible threats by
following the same attack patterns used by a fraudster. This allows for
the identification of any weaknesses and points of least resistance for
an attacker to pursuit. For example, if applications are accessible
through different data interfaces and channels, the fraudster will focus
on the ones that offer the least resistance and greatest opportunity for
compromised data, such as mobile instead of web channels. As one of the
security principles is "you are only as secure as your weakest point",
identifying where these weakest points are is critical in the assessment
of the security of any system exposed to attacks, including
applications. The identification of the data entry points for a given
application, internal and external, is critical to determine the attack
surface of the application and is usually identified as part of the
application threat modeling assessment.

Another critical analysis that is part of application threat modeling is
to analyze which threats can be realized by exploiting a certain class
of vulnerabilities so that CISOs can focus on applying countermeasures
for mitigating these vulnerabilities. An in depth analysis of threats
impacting applications and software is best conducted by using threat
trees and risk frameworks. These are formal methods that allow for
mapping threats to vulnerabilities and countermeasures. OWASP has
included guides for application threat modeling as well as reference to
"threat trees" and "threat-countermeasures" frameworks that can be used
for this threat analysis.

#### Business logic attacks

A class of vulnerabilities that are often exploited by fraudsters and
not tested in applications are design flaws and logical vulnerabilities.
One of the main reasons these are not tested is because automated
vulnerability scanning tools do not understand the business logic of the
application to be able to identify them. In absence of specific manual
security tests that test for possible use and abuse cases of the
application, for example, these type of vulnerabilities are most likely
not identified and remediated and might cause serious financial losses
and business impacts when are exploited. Examples of attacks that
exploit these vulnerabilities are the so called "business logic
attacks". Examples of business logic attacks that exploit design flaws
in applications include bypassing role base access controls to gather
unauthorized confidential data and to perform un-authorized financial
transactions, attacking the logic of shopping carts to alter the price
of an item before check out and alter the shipping address of a
purchased item before credit card validations are completed during a
check out. Typically, business logic attacks exploit input validation
vulnerabilities such as in missing validation of parameters in business
transactions (e.g. Role ID, RuleIDs, PriceIDs), weak enforcement of
controls for transaction workflows, flaws in committing financial
transactions before all checks are done and misconfigurations of Role
Based Access Controls (RBAC) and business policy rules. Most of these
vulnerabilities need to be tested manually based upon use and mis-use
cases, a technique that is considered part of application threat
modeling and also documented in OWASP Application Threat Modeling
methodology.

Often design flaws are to be found in how application security controls
are designed and require specific security testing to identify them. For
example, this is the case of flaws in the design of password resets, use
of guessable challenge questions in multi-factor authentication, session
management flaws allowing sessions to not expire or not close,
misconfiguration of authorizations and access controls. These design
flaws usually fall under the class of common vulnerabilities such as
OWASP A3 Broken Authentication and Session Management, OWASP A4 Insecure
Direct Object Reference, OWASP A6 Security Mis-Configurations and OWASP
A8 Failure To Restrict URL access and can be tested for specific manual
tests. OWASP provides specific guidelines for security testing
applications for vulnerabilities as well. A class of vulnerabilities
also exploited for business logic attacks includes the insufficient
anti-automation (WASC 21). This is a vulnerability that can be exploited
by attackers to spam online registrations, posting of information using
automation tools, but also for fraud such as to automatically enumerate
and validate credit card data such as numbers and PINs using automated
scripts that test the application error codes and success responses.

The most important criteria for CISOs to protect from business logic
attacks is not to assume that the testing of design flaws and business
logic flaws is covered under normal vulnerability scans and security
tests. Design and business logic flaws is a class of vulnerabilities
that requires to be tested by deriving specific security tests from use
and abuse cases produced by security teams specifically engaged in
threat modeling applications. CISOs should consider the investment in
application threat modeling process specifically for identifying and
testing this class of vulnerabilities when these are not identified and
tested by other security processes.

#### Phishing attacks

Since often one of the attack techniques adopted by fraudsters and
cyber-criminals is social engineering the victim to select malicious
links serving malware, exploits of web application vulnerabilities that
facilitate phishing the victim with malicious links might also be
targeted. These attacks include using Cross Site Scripting (A2: XSS)
vulnerabilities to run malicious scripts that can steal cookies and run
keyloggers. Another web application vulnerability that can be used for
tricking a victim to visit a malicious site and get infected with
malware is OWASP A10: invalidated redirects and forwards. Additional
vulnerabilities that facilitate malware installation through phishing
include XFS exploits for click jacking attacks. These attacks trick a
victim into performing undesired actions by clicking on a concealed
malicious link. These are vulnerabilities that CISOs can prioritize for
remediation since they facilitate the installation of malware on the
victim’s PC. Since the identification of these vulnerabilities often
require manual security testing such as manual ethical
hacking/penetration testing as well as manual source code review to
identify these vulnerabilities in the source code, it is critical for
the CISO to invest in hiring and train pen testers as well as software
developers with secure coding skills as well as secure code review
processes, secure coding standards and static source code analysis
tools.

#### "Man in the browser" and "man in the middle" attacks

Unfortunately, identifying and fixing these vulnerabilities is not a
guarantee of immunity from attack of fraudsters but of a minimum level
of software security assurance. Resilient software today requires the
CISO to consider investment in countermeasures to protect web
applications from another class of attacks such as Man in the Browser
(MiTB) and Man in the Middle (MiTM). Through MiTB, fraudsters can
collect confidential, authentication and credit/card data from the
victim by injecting HTML fields in the browser outside the control of
the web application. Additionally, the victim’s logging credentials are
collected through key loggers and sent to the fraudster’s for
impersonating the victim. In a money transfer session for example, the
fraudster will connect to the victim’s PC from his command and control
server and hijack the session to transfer money to an account under the
control of the attacker (e.g. money mule account). Through, MiTM,
fraudsters will redirect the victim to a malicious site whose web
traffic and data will be under the control of the attacker.

To protect e-commerce and financial web applications from MiTB and MiTM
attacks, CISOs need to adopt a defense in depth approach that includes
different layers of controls at the client-PC layer, at the web server
and web application server layer as well as at the backend databases and
services layers. At the client PC layer, investing in user’s information
and awareness on malware threats is very important. Simple measures such
as keeping browsers and PCs up to date and patched as well as hardened
with limited user’s privileges and with a limited number of applications
installed (e.g. ideally with no email and no Facebook installed on PC)
can limit the chances of malware infections. Pointed security
information embedded in the website login web pages can keep warning
users about malware risks every time they login.

Additionally, CISOs can invest in providing anti-malware client software
for free to their clients since this is more effective in detecting and
protecting the PC than traditional anti-virus. Assuming the client
PC/browser has been compromised with banking malware, additional
countermeasures that CISO might consider includes adding additional
identity validation controls for high risk transactions such as in the
case of wire transfers and payments. These include positive pay, dual
verification & authorizations, anomaly and fraud detection. Since the
online channel is assumed compromised by the attacker, using out of band
transaction validation/authentication for payments and financial
transactions with two way notification confirmation via independent
mobile/voice channels puts the citizen/client/customer/employee in
control of the transaction and allows them to reject transactions that
either cannot be confirmed or whose integrity of transaction parameters
have been modified by the attacker and cannot be validated. Detection
measures such as receiving out of band alerts for financial transactions
as well as auditing and logging and monitoring of web traffic with WAF
and SIEM and using behavioral fraud detection to detect abnormal
transaction rates/parameters might also allow CISOs to receive reports
on detected malware based transactional events and to recommend
proactive actions to limit the impact of financial losses (e.g. suspend
the accounts that are flagged as suspicious till further validation).

When deciding on which countermeasures to deploy for mitigating the risk
of MiTB and MiTM attacks, CISOs might need to conduct trade-offs between
the risk, the effectiveness of these countermeasures and the costs. The
countermeasures that cost the least and mitigate MiTB and MiTM attacks
the most can be prioritized for investment. Typically client based
anti-malware software can be effective in mitigating the malware risks
at the front door and it is rather inexpensive to acquire and deploy if
this cost does not include the total cost of maintenance of the solution
for a large user population. Security awareness campaigns for customers
can be the least expensive measure but might not be that affective since
often customers do not pay attention to security warnings. Acquiring and
deploying out of band authentication and out of band transaction
validation/authorization can be expensive, but it offers strong
mitigation against man in the middle attacks and can be a viable option
to protect high risk transactions. Implementation of fraud detection
systems for monitoring malicious traffic might be expensive to implement
and maintain and need to be justified on the case by case basis. For
example, if it is known that some web applications are constantly under
attack from malware and impacted by fraud, investing in fraud detection
systems might be justifiable due to the tested capability of fraud
detection systems to detect attacks earlier than with other methods
(e.g. looking at transaction logs that feed to SIEMs). CISOs can select
which web applications should be put in scope for remediation of
vulnerabilities sought by fraudsters and implementation of new
countermeasures against MiTB and MiTM attacks based upon the risk
profile of the application. The risk profile of the web application can
be a function of the value of the data assets and the risk of the
transactions that the web application provides to customers. A control
gap analysis can be used to identify gaps in protective and detective
controls and to determine the degree of risk mitigation that can be
obtained when these are implemented. Once the security measures are
adopted, a calculation of the residual risk highlights whether the risk
can be accepted or needs to be reduced further by implementing
additional controls.

#### Denial of service attacks

Denial of Service (DoS) attacks might severely impact the availability
of website to users. Depending on the type of services that the website
provide to customers, a loss of service might result in a considerable
revenue loss for the organization. CISOs should consider the mitigation
of the risk of denial of service attacks as top priority, especially for
web applications that generate considerable revenue and whose
availability is considered critical by the organization.

DoS attacks can be facilitated by web application vulnerabilities, OWASP
included DoS as one of OWASP Top Ten vulnerabilities in 2004 (OWASP
A9:DoS) but this was dropped in 2007 due to the MITRE ranking in 2006.
Nevertheless, even if it is no longer part of the OWASP top ten in 2010,
depending on the exposure and the value of the assets impacted, denial
of service vulnerabilities might represent a high risk for the
organization and prioritized for mitigation. At the application level, a
denial of service might be the result of exploits of OWASP A1 injection
vulnerabilities, specifically vulnerabilities allowing injections of
SQL, XPATH and LDAP commands can cause the web application to crash. At
the user level, denial of service attacks can target the usability of
the application by a registered user, for example attackers can use
scripts to lock user accounts upon guessing valid userIDs and force user
accounts to lock upon several un-successful attempts. In absence of
temporary account locks (e.g. the user account will unlock automatically
in 24 hours), this attack cause users to not be able to log on. A side
effect of this is customers calling customer support seeking to unlock
their user accounts, possibly flooding the call centers with account
unlock calls. At a source code level, DoS attacks might occur because of
attack vectors exploiting insecure code issues causing exhaustion of
computer resources. These are insecure coding issues such as failing to
release memory from allocated resources (e.g. object's memory) when
exiting programs and causing the application to crash as a result.
Examples include exploiting of insecure code with NULL pointer deference
and improper termination, exploiting uncaught exceptions and exploiting
weaknesses when processing XML files causing the XML parsing process to
exhaust memory with malicious recursive XML files. In the cases when the
application source code is written in programming languages that allow
programmers to manage memory such as C, C++, coding errors in the
handling of memory allocations and use of unsafe functions might expose
the source code and the application to possible exploit of buffer
overflow vulnerabilities to cause the application to crash or to take
control. Buffer overflow vulnerabilities can also be exploited at server
level because of attacks seeking to exploit web and application servers
that are unpatched and vulnerable to buffer overflows. CISOs need to
make sure that application and source code vulnerabilities that could be
exploited for denial of service are in the scope of security testing
since these are typically covered by static and dynamic application
security testing tools.

#### Distributed denial of service attacks

At the transport-network layer, denial of service typically seeks to
exploit network layer protocol type vulnerabilities such as by spoofing
packets for the sake of flooding network traffic. A type of denial of
service attack called Distributed Denial of Service (DDoS) typically
seeks to flood the target web server with an unusually high level of
data traffic sent from a coordinated and controlled network of bots.
Because of the unusual network traffic that the web server is asked to
handle, it might not be able to serve all the requests over the network
and deny the requests of service to the users of the application. At the
most outer layer that is the edge of the internet it is possible to
filter the malicious traffic before it attacks the internal layer that
is the data center where the application is hosted and other
countermeasures are implemented. As the DDoS attacks take place, defense
in depth allows the organization to be alerted and prepare new filtering
blocking rules for malicious traffic. But applying the principle of
defense in depth, even if it can slow down attackers, it is not enough
and other defensive security principles need to be followed when
deploying countermeasures as well. Such as to consider control of
security of the weakest point, consider the simplicity and openness of
the security mechanism so it can be managed and vetted securely, apply
security as the lowest privilege for users' access are all essential for
the security of the design of security controls of applications and
software.

Well known DDoS attacks originating from bots include “Ping of Death”
bots that create huge electronic packets and send them to victims,
“Mailbomb” bots that send a massive amount of e-mails, crashing e-mail
server, Smurf Attack” bots that send Internet Control Message Protocol
(ICMP) messages to reflectors to amplify the attack, and “Teardrop” bots
that send malformed pieces of packets that crash a system trying to
recombine them.

Today's script kiddies, hacktivists, cyber-criminals and country
sponsored attackers use open source DDoS attack tools and bots against
possible targets. The typical, likely targets for DDoS attacks are
public and private organizations with high visibility. General
objectives of these attacks are to cause disruptions, get noticed and
damage the company reputation. Specific motives for conducting DDoS
attacks varies depending on the type of threat agents and their motives.
Script kiddies might use DDoS attacks for opportunistic motives such as
to exploit denial of service vulnerabilities and gain notoriety,
hacktivists might use DDoS attacks for political reasons and to get
attention from public media. Fraudsters and cyber-criminals might use
DDoS attacks to derail attention from other attacks such as in the case
of an account take over attack seeking to defraud online bank customers.
State sponsored cyber-attackers might use DDoS attacks for economic and
military reasons such as in the case of disrupting the operation of
another country’s government operated website.

The impact of DDoS attacks in terms of reputation and revenue loss to
private and public organizations varies greatly depending on the type of
website targeted by the attack, the duration of the attack and the
number of individuals and customers affected. The business impact of
DDoS attacks can be estimated as a function of the loss of revenue
caused by the loss of services to customers and individuals when the
website is taken down. According to the "2011 Second Annual Cost of
Cyber Crime Study Benchmark Study By Ponemon Institute" that involved 50
organizations and U.S. companies, the impact of DDoS is estimated to be
an average annual cost of $187,506. This cost is weighted by the
frequency of the attack incidents for all benchmarked companies. Another
survey from CA Technologies including 200 companies in North America as
well as Europe, estimated the cost of downtime because of a denial of
service of about $150,000 annually. These cost estimates, are just order
of magnitudes since business impacts vary greatly depending on the type
of online services affected and the volume of the online business
affected by the DDoS attacks. For a very large e-business company like
Amazon for example, whose business generated $ 48 billion in revenues
for the year 2011, assuming that most of Amazon's revenues are generated
online, a denial of service of just one hour DDoS attack might cost
several millions of dollars in revenue loss. CISOs whose companies
generate a significant part of their revenues through online websites
such as in the case of e-commerce and financial websites, need to
consider the threat of denial of service from DDoS attacks as top
priority for risk mitigation and consider investing in security measures
to mitigate the risk of such attacks.

Today DDoS attacks are very widespread. The reason why such attacks are
so widespread is due to the availability of DDoS tools and of botnets
rented to conduct DDoS attacks at a relatively low cost for the
attacker. According to “Modeling the Economic Incentives of DDoS
Attacks: Femtocell Case Study, Vicente Segura and Javier Lahuer ta,
Department of Network and Services Security of Telefonica” for example,
the cost of renting a botnet for DDoS attacks is about $ 100 per day for
1 Gbps bandwidth.

CISOs also need to be aware of the escalating DDoS threat since the
severity and sophistication of DDoS attacks are also increasing.
According to “2011 Arbor Networks, Sixth Annual Worldwide Infrastructure
Security Report”, considering with DDoS of six years ago, the power of
DDoS attacks increased ten times reaching bandwidths of 100 Gbps. This
escalation of DDoS power cannot be explained by the sophistication of
the DDoS tools alone but with new DDoS attack techniques seeking to
amplify the bandwidth of the attacks. These new DDoS attack techniques
consist of Distributed Reflector Denial of Service Attacks (DRDoS).
DRDoS attacks spoof the victim’s source IP address with DNS queries sent
towards open DNS resolvers, since open DNS resolvers that receive the
DNS queries respond to the victim's system with large packets, they can
be used to amplify the bandwidth further such as when thousands of bots
are querying thousands of DNS servers.

Traditional network layer countermeasures for protecting from DDoS
attacks include setting routers to examine and drop packets, filter IP
addresses, configure rate limits and apply ingress and egress network
filtering. Unfortunately today, most of these countermeasures are not
enough to protect from DDoS and DDRoS attacks of the intensity of 100
Gbps bandwidth. In order to protect from high power DDoS and DRDoS
attacks, CISOs whose organizations high availability websites are under
the threat of high bandwidth DDoS and DDRoS attacks, need to consider
investments in network segmentation, hosting part of the website static
content on CDN (Content Delivery Networks) and use third party
cloud-based DDoS protection services with service level agreements to
increase traffic bandwidth in case it is consumed during a DDoS attack.
Refer to (Attacks FS-ISAC_Threat_Viewpoint_DDoS_June_2012.pdf).

## II-6 Mitigating the Inherent Risks of New Application Technologies

The goal of this chapter is to guide the CISO on the consideration of
the security risks posed to the organization by the adoption of new
technologies. The term “technologies” is used herein to include recent
examples of technologies that impact applications such as mobile
technologies, web 2.0 technologies, and cloud computing Software as a
Service (SaaS). As technologies evolve, it is important for the CISO to
understand the security risks introduced by the adoption of these new
technologies since these might represent new opportunities for attackers
to attack both applications and the data. The increased risk to
applications due to the adoption of new technologies includes the
increased exposure/attack surface such as in the case of extending
applications to mobile devices, the introduction of a new class of
client and server side vulnerabilities such as in the case of Web 2.0
and the increased risk of loss of data and transaction integrity due to
the use of cloud computing. In order to target the mitigation of the
risks due to the adoption of these technologies, CISO needs to have a
clear picture of the risks that are introduced and decide to invest in a
new type of application security assessments, tools and security
measures to mitigate the risks.

### Managing the risks of mobile applications

Mobile application security is a particular concern for most
organizations today: this is mostly due to the exponential growth in the
adoption of mobile smartphones and tablets by users both for personal
and business use. From the application security perspective, access of
business applications from mobile devices increases the opportunity for
threat agents to attack the mobile device and the applications and the
data that can be stored in the mobile devices. Mobile phones that are
compromised with malware for example, expose both the client application
installed on the device as well as the server application that can be
assessed through the mobile device. Different mobile communication
channels can be also attacked including web channels to access Wi-Fi
networks, MMS, SMS messaging and GSM 2G, 3G, 4G wireless networks.
Businesses whose applications can be accessed through mobile devices
should consider the exposure to attacks increased by the adoption of
mobile applications. One important security measure is to require a
specific vulnerability assessment for testing the security of mobile
applications and of the protection of sensitive data that is stored on
the mobile device. The requirement to encrypt any confidential and
authentication data that is stored on the device, for example, might be
required by compliance with internal mobile security standards and
policies. Exposure of web services that can be accessed through a mobile
application needs also to be tested for vulnerabilities. Often the
organization might decide to avoid the risk of mobile applications
accessing financial risk transactions such as money transfers and
payment when authentication on the device is considered not as strong as
the one available for the internet PC based applications. In some cases,
device security controls might be considered not secure enough, such as
when using device based encryption (e.g. iOS keychain) because this can
be brute forced when the user is no longer in possession of the mobile
device. These are important risk considerations and can be enforced by
requiring the development organization to follow security standards for
designing mobile applications.

Besides device compromise because of a device being lost or stolen
another risk to consider is the compromise of the mobile device by
malware designed to install keyloggers to collect user's credentials and
to redirect these stolen credentials to the fraudster's server. Today
mobile applications represent an opportunity to attack applications
installed on the mobile devices through different communication channels
such as emails, social media, video-audio streaming, instant messaging
and web. Examples of opportunities for an attacker to compromise mobile
devices with malware, for example, include social engineering mobile
users to click on malicious links in emails and messages that carry
malware payloads to install spyware and remote access tools. The
sophistication of the mobile malware today is such that some mobile
malware is specifically designed to attack the time tokens sent to the
user's phone to authenticate online banking web sites. This type of
mobile banking malware has the capability to perform (MiTMO) Man in the
Mobile attacks and redirect the one time authentication tokens to the
fraudster's mobile phone so they can be used to authenticate to the
online banking site along with username and passwords. Another avenue of
attacks to mobile applications is to upload malicious applications on
the mobile application provisioning stores (e.g. Market place and Apple
Store) and lure mobile users to download rogue applications from these
stores. Since applications for Android and iOS together compose nearly
90 % of the worldwide smartphone type of applications, attacking
application provisioning stores represent the best opportunity for an
attacker to spread mobile malware to a large numbers of mobile
application users. Typically the security checks that are performed by
these mobile application stores especially in the case of the Apple
Store mitigate these risks but downloading mobile type of applications
from sites whose origin cannot always be validated by the mobile users
(possible for Android mobile type of applications) should be considered
a risk.

Nevertheless, a lot of security can be gained by just having mobile
users follow basic security measures. In some cases the lack of
enforcement of basic simple default security measures such as use of
PINs to prevent unauthorized access and allowing the installation of
applications that require to “jail break” the phone represent an
increased risk both for the data and the mobile applications residing on
these devices. A good preventive measure is to keep informing users of
the threats targeting mobile devices and recommend them to follow basic
security measures. Good resource of security awareness for mobile phones
and protection from threats targeting mobile devices is [US CERT Cyber
Threats to Mobile
Phones](http://www.us-cert.gov/sites/default/files/publications/cyber_threats-to_mobile_phones.pdf).

For CISOs whose responsibility is to manage the security of mobile
applications it is important to consider the adoption of specific
security processes and standards for the security of mobile
applications. These measures might include the adoption and
documentation of mobile technology security standards, the adoption of
vulnerability assessments to specifically security test for mobile
application type of vulnerabilities and standards for secure
provisioning of these mobile applications and application data on the
personal owned consumer devices. From the perspective of adoption of
specific security testing process for vulnerabilities in mobile type of
applications, [the OWASP mobile security
project](https://www.owasp.org/index.php/OWASP_Mobile_Security_Project)
has a number of resources such as documentation on mobile security
risks, free vulnerability assessment tools, cheat-sheets and guidelines
for the secure design of mobile applications.

An important aspect that mobile security and of particular CISO concern
is to secure organization-issued mobile devices as well as user personal
devices brought into the organization (e.g., Bring Your Own Device,
BYOD). As the practice to bring personal devices into the enterprise
environment becomes prevalent, CISOs will need to access the potential
risks and determine how much access to grant to potentially unsafe
employee-owned devices. Today some organizations might allow employee
owned devices to directly access the organization's network only through
secure connectivity such as VPN, secure virtualization, terminal servers
or remote access utilities like virtual network computing (VNC). In all
these cases, it is important that CISOs have rolled out specific
policies for remote access from employee owned devices that are strictly
enforced through a secured and centrally managed controlled access
technologies and services. A good resource that can help CISOs to set
guidelines for BYOD and for centrally managed and secure mobile devices,
such as smart phones and tablets is the NIST SP 800-124, [Guidelines for
Managing and Securing Mobile Devices in the Enterprise
(Draft)](http://csrc.nist.gov/publications/drafts/800-124r1/draft_sp800-124-rev1.pdf)
and [Guidelines on Cell Phone and PDA
Security](http://csrc.nist.gov/publications/nistpubs/800-124/SP800-124.pdf).

### Managing the risks of Web 2.0 technologies

New technologies introduce new risks and new measures need to be put in
place by the organization to mitigate these risks. One possible way to
prepare for the impact of new technologies it to plan in advance the
adoption of security measures and processes to mitigate the risks by
knowing when such technologies will become “mainstream” that it will be
widely adopted by the business. According to some analysts like Gartner,
the adoption of new technologies by the market follow a cycle also
referred as “hype” that comprises five phases that are (1) “Technology
Trigger”, (2) "Peak of Inflated Expectations", (3) "Trough of
Disillusionment", (4) "Slope of Enlightenment" and (5)”Plateau of
Productivity". In the hype cycle that Gartner published in 2009 covering
emerging technologies, Web 2.0 was shown as two or less than two years
for mainstream adoption. This prediction is validated today (2012) by
considering that several applications today have adopted and integrated
Web 2.0 technologies in their web applications. Since typically senior
management and executives’ pay specific attention on the market and
security technology research of analysts (e.g. Gartner and Forrester) it
is important for CISO to look at this research as well from the
perspective of deciding whether to adopt a certain type of technology as
well as for preparing for the security impacts of such technology. First
of all it is important to understand the terminology used. Web 2.0
technologies can be defined as “Web applications that facilitate
interactive information sharing and collaboration, interoperability, and
user-centered design on the World Wide Web”. The main characteristics of
Web 2.0 technologies are:

  - Encourage user’s participation and collaboration through a virtual
    community of social networks/sites. Users can and add and update
    their own content, examples include Twitter and social networks such
    as Facebook, Myspace, LinkedIn, YouTube
  - Transcend from the technology/frameworks used. Examples include
    AJAX, Adobe AIR, Flash, Flex, Dojo, Google Gears and others
  - Combine and aggregate data and functionality from different
    applications and systems, example include “mashups” as aggregators
    of client functionality provided by different in-house developed
    and/or third party services (e.g. web services, SaaS)

One important aspect that CISOs need to be aware of regarding of Web 2.0
technologies is how these technologies affect the threat landscape.
First of all, Web 1.0 threats are amplified by the intrinsic nature of
Web 2.0 due to the expanded volume of user’s interaction: consider for
example the hundredths of millions of users of social networks and the
increased attack surface to the web application offering links to
corporate Facebook and twitter accounts now provided to a threat agent
for attacking the user with phishing, malware as well as for exploit of
traditional Web 1.0 vulnerabilities such as injection flaws, XSS and
CSRF. Social networks specifically facilitate customer’s sharing of
confidential and private information since boundaries between private
and personal information are often crossed by voluntarily sharing of
such information with the company even if is not being explicitly
requested.

Another element of increased risks is represented by the increased
complexity of the functionality due to the integration of different Web
2.0 technologies and services both as front-end-client as well as
back-end-server. Business rich client interfaces such as widgets for
example increase the likelihood of business logic attacks while exposure
of new web services increases the exposure of attacks to back end
servers.

#### Web 2.0 vulnerabilities exploited by attackers

Because of the increased risks to web applications due the introduction
of Web 2.0 technologies, it is important that CISOs make sure that web
applications are specifically designed, implemented and tested to
mitigate the risks. From a vulnerability and threat analysis
perspective, Web 2.0 application vulnerabilities can be analyzed using
the OWASP Top 10 and the WASC Top 50 threats. OWASP Top 10
vulnerabilities that Web 2.0 applications need to be tested for include
A1-Injection, A2-XSS, A3-Broken Authentication and Session Management
and A5-CSRF. Examples of Web 2.0 injection vulnerabilities include XML
injections such as when an attacker will provide user-supplied input
that is inserted into XML without sufficient validation affecting the
structure of the XML record and the tags (and not just content). A
particular type of XML injection vulnerability is XPATH injection. This
is an attack aimed to alter an XML query to achieve the attacker’s goals
such as to perform un-authorized queries to retrieve confidential data.
Another Web 2.0 specific injection vulnerabilities includes JSON
injections to run un-authorized code, potentially malicious by injecting
malicious JavaScript code into the JSON (JavaScript Object Notation
structure) on the client.

Among Web 2.0 injection vulnerabilities, RSS feed injections can be used
to consume un-trusted sources from RSS feeds such as malicious links to
download malware on the victim’s computer. Web 2.0 exploits of XSS are
facilitated by the fact that a lot of Web 2.0 based sites that allow
adding HTML to normal text content such as when posting blogs and
feedbacks to the company products-services. When HTML data is unfiltered
from malicious input it might allow the attacker to enter unsafe HTML
tags that can be abused for XSS to attack victims reading the blog
postings or comments to select malicious links. An additional attack
vector for Web 2.0 XSS is also represented by XSS DOM since WEB 2.0 APIs
use DOM in Rich Internet Applications (RIA) written in FLASH,
Silverlight such as Mashups and Widgets. The use of AJAX (Asynchronous
JavaScript) on the client also increases the possible entry points for
attacking several HTTP requests to the web site with XSS attacks. An
example of a Web 2.0 attack exploiting injection vulnerabilities is
included in the Web Hacking Incident Database WHID 2008-32: Yahoo
HotJobs XSS that allowed the threat agents to exploit an XSS
vulnerability on Yahoo HotJobs to steal session cookies of the victims
and gain control of every service accessible to the victim within Yahoo,
including Yahoo\! Mail.

Example of exploits of Web 2.0 OWASP-A3: Broken Authentication and
Session Management vulnerabilities include use of weak passwords,
passwords stored in AJAX Widgets/Mashup that are sent and stored in
clear outside the control of the host, passwords that are stored on the
client as “autologon feature” or in the cloud to SSO from the desktop
and password recovery controls that are not protected from brute force
attacks since do not lock the accounts when several failed tries to
guess the passwords are attempted. An example of this vulnerability type
exploit is also part of the WHID catalogue as 2008-47: The Federal
Suppliers Guide validates login credential in JavaScript.

A type of vulnerability that is facilitated by Web 2.0 is CSRF such as
when clients use AJAX to make XHR calls that enable invisible queries of
a web application and the user cannot visually validate for forgery.
CSRF is also facilitated by insufficient browser enforcement of the
Single Origin Policy for desktop widgets and weak session management
when session expiration times are set to be quite high, increasing the
risk of session base attacks such as CSRF. Persistent session cookies
that are shared by widgets also increase the opportunities for CSRF
attacks. A known Web 2.0 security incident that is in the WHID catalogue
as 2009-4:”Twitter Personal info CSRF” allowed an attacker to exploit a
CSRF bug in Twitter to get twitter profiles of the visitors.

A type of vulnerability that is also exploited and used against Web 2.0
applications but also more in general against web sites is due to the
lack of anti-automation defenses. This vulnerability is not tracked by
OWASP Top 10 but by the Web Application Secure Consortium (WASC) as Top
21 within the TOP 50 issues tracked by WASC. Automation attacks against
Web 2.0 applications that are allowed to post information such as
feedback forms, blogs and wiki pages for example seek to spam these
pages with commercial information and potentially by attackers to post
links to malicious sites to spread malware via drive by download or by
phishing.

|                                                                                                                                                |
| ---------------------------------------------------------------------------------------------------------------------------------------------- |
| In 2007, Facebook was accessed through automation in an attempt to harvest user information. See WHID 2007-65:” Botnet to manipulate Facebook” |

Example: Insufficient Anti-automation for Facebook

#### Security measures to mitigate risks

Critical to the vulnerability analysis of Web 2.0 applications is the
determination of the root causes of the vulnerabilities. Only through
the identification of the vulnerabilities root causes, can
vulnerabilities be eradicated. For example if these vulnerabilities
originate from lack of security requirements for Web 2.0 that software
developers need to follow, these need to be documented. In case the
issues are caused by errors in design, these needs to be prevented by
making sure the design of web 2.0 applications is reviewed by a security
architect that has subject matter expertise in Web 2.0 technology. For
Web 2.0 vulnerabilities that are introduced by software developers as
coding errors or because of integration with software and third party
libraries that are exposed to Web 2.0 vulnerabilities it is important
that software developers are trained in defensive coding Web 2.0
applications and that security testers know how to identify and test Web
2.0 vulnerabilities.

A prescriptive set of Web 2.0 security measures that CISOs can undertake
to mitigate the risks include:

  - Documentation of security standards for Web 2.0 technologies such as
    security requirements for design, coding and testing specific Web
    2.0 technologies such as AJAX, FLASH and enforcement of them at the
    beginning of the SDLC
  - Institute a security activity during design to review threats
    against Web 2.0 applications and identify countermeasures such as
    application threat modeling. Part of this activity also includes the
    security review of the application architecture and the security
    controls that are exploited by attacks against Web 2.0 applications
    such as input validation, authentication, session management and
    anti-automation controls such as CAPTCHA.
  - Require Web 2.0 based applications to undergo a secure code review
    to assure source code adherence to security coding standards and
    static source code analysis to identify Web 2.0 coding issues in
    both client source code used by Widgets, RIA, AJAX components as
    well as server side code that is used in web services and Service
    Oriented Architectures (SOA). Specific secure code requirements can
    be documented for AJAX, these can be socialized with architects and
    software developers and validated during design and source code
    reviews.
  - Require security tests to include specific test cases for testing
    Web 2.0 component vulnerabilities and for Web Services. Refer to
    OWASP test guide test cases for testing AJAX and Web Services as
    example.
  - Make sure Web 2.0 technical risks are managed such as the business
    risks that Web 2.0 design flaws and bugs might pose to the business.
    The OWASP risk methodology can be used to manage Web 2.0 security
    risks. An example of OWASP risk framework applied to Web 2.0
    technologies is included in the table below.

| Threat Agents            | Misuses and Attack Vectors                                                         | Security Weaknesses | Security Controls / Countermeasures                                                        | Technical Impacts | Business Impacts                                                                                          |
| ------------------------ | ---------------------------------------------------------------------------------- | ------------------- | ------------------------------------------------------------------------------------------ | ----------------- | --------------------------------------------------------------------------------------------------------- |
| valign="top"             | Web 2.0, Users                                                                     | valign="top"        | User shares private/confidential information, agents post confidential information         | valign="top"      | Inherent weaknesses in controlling user contributed content in social network, blogs, IMs, private emails |
| valign="top" rowspan="3" | Malicious users, fraudsters                                                        | valign="top"        | Victim is targeted by phishing, download of malicious widgets, clicking on malicious posts | valign="top"      | Social engineering, web 2.0 vulnerabilities: XSS                                                          |
| valign="top"             | Attacker sends malicious data to the application's interfaces                      | valign="top"        | Web 2.0 vulnerabilities: XPATH injection, XML injection, JSON injection                    | valign="top"      | Filtering, parameterized APIs, ESAPI filtering methods, white list validation                             |
| valign="top"             | Attackers use leaks or flaws in the authentication or session management functions | valign="top"        | Web 2.0 broken authentication and session management vulnerabilities                       | valign="top"      | Security requirements for secure password policies, account lockout, disable auto-logins                  |
| valign="top"             | Fraudsters                                                                         | valign="top"        | Attackers create forged HTTP requests and tricks victims into submitting them              | valign="top"      | Web 2.0 cross site request forgery vulnerabilities                                                        |
| valign="top"             | Automated Scripts / Spam Bots                                                      | valign="top"        | Application post links, create accounts, game the application, scrape data                 | valign="top"      | Insufficient anti-automation                                                                              |

### Managing the risks of cloud computing services

The concept of cloud computing is not new. Many organizations used to
outsource their data centers to third party owned data centers, a
concept that in cloud computing is considered a deployment of
Infrastructure As A Service (IaaS) cloud service. The term cloud
computing encompasses outsourced infrastructure such as in the case of
Infrastructure as a Service (IaaS), outsourced platforms such as in the
case of Platform As A service (PaaS) and through outsourced software a
term that is also referred to as Software As A Service (SaaS).

CISOs today face the challenge to assess and assert the security of
cloud computing deployments within their network (e.g. on-premises or
private cloud) or outside the organization (e.g. outside premise or
public cloud). Information and application security is a primary concern
for organizations that outsource either their infrastructure component
and platforms or software and data to a third party vendor cloud
provider. CISOs need to consider the potential risks and assess them
prior to deciding to outsource their services to third parties. CISOs
should consider for example the potential risk of the company data that
is hosted on a third party cloud computing provider can be compromised
because of a security incident occurring at the cloud provider. CISOs
should also consider for example the risk that an organization might
face when the data service that is provided to their customers is
outsourced to a third party software and become unavailable because such
cloud service provider has been targeted by a denial of service attack.

It is therefore important that CISOs consider the whole spectrum of
information security risks before the organization decides to move
either their services or their data to the cloud computing service
providers. At high level these risks can be assessed by conducting a due
diligence third party information security assessment on the cloud
computing provider service vendor. These type of assessments seek to
assert the security posture of the cloud provider against the company’s
information security policies and standards as well as with audit of
industry relevant IT security standards such as SAS 70, SOC, FISMA, PCI
DSS, ISO, FIPS-140, ISO/IEC 27001-2005 etc. and others as these are
relevant to the organization’s regulated security business operations
such as HIPPA, FFIEC, MPAA etc. etc.

In the case of cloud computing assessment, security risks and
compliance-audit are actually some of the domains that need to be
assessed along with others such as cloud architecture, governance, legal
and law enforcement, privacy, business continuity and disaster recovery,
incident response, application security, encryption and key management,
identity, entitlements and access management, virtualization and
security as a service.

A comprehensive guidance on how to conduct oversight on all these
domains of cloud computing is the [Cloud Security
Alliance](https://cloudsecurityalliance.org/). CSA provides top level
security guidance for critical areas in cloud computing. CSA also
provides a set of tools that can be used by organizations to assess
security risks of cloud computing services in these domains including a
cloud control matrix spreadsheet to assess SaaS, PaaS and IaaS controls
for information security, legal, organizational-policies, risk
management, resilience and security architecture, against standards such
as COBIT 4.1, ISO 27001, NIST SP 800-53, PCI-DSS vs. 2.0 and others. The
CSA Consensus Assessments Initiative Questionnaire v1.1 allows CISOs to
assert the third party cloud computing service providers with respect to
information security as well as compliance, data governance, facility
security, human resource security, legal, operations management, risk
management, release management, resilience and security architecture. In
2013 CSA also published a white paper with guidance on adopting controls
in the cloud to mitigate the risk of the top threats to cloud computing.

<center>

<table>
<caption>Top Nine Threats to Cloud Computing</caption>
<tbody>
<tr class="odd">
<td><p><a href="https://cloudsecurityalliance.org/">https://cloudsecurityalliance.org/</a></p>
<ol>
<li>Data breaches</li>
<li>Data loss</li>
<li>Account hijacking</li>
<li>Insecure APIs</li>
<li>Denial of service</li>
<li>Malicious insiders</li>
<li>Abuse of cloud services</li>
<li>Insufficient due diligence</li>
<li>Shared technology issues</li>
</ol></td>
</tr>
</tbody>
</table>

</center>

OWASP recommends that CISOs leverage CSA documentation guidance;
questionnaires and threat analysis referred herein and use these to
construct an ad-hoc cloud computing security assessment process that can
be used by the organization’s information security team to conduct due
diligence information security, risk and compliance-audit assessment on
cloud computing providers. Such ad-hoc cloud computing security
assessment might consider the organization information security
policies, standards and regulations are the starting point to assert the
security of cloud providers since these are the same that are applicable
and more relevant to the organization requirements to protect
confidentiality, integrity and availability of the data. An ad-hoc cloud
computing security assessment should at minimum include a standard
process that can be followed including a set if questionnaires that can
be used to capture and assert the security, compliance and risk
management posture of the cloud computing security provider prior to
making a business decision to whether outsource services such as
infrastructure, networks, platform and software-data to a third party
cloud computing service provider.

The main goal of such an assessment is to identify control gaps and
potential areas of risk for the organization. Examples of application
security risks that can be identified with these assessments might
include the identification of the lack of end to end encryption of the
data granting full control and assurance to the business of the
confidentiality of the data either in transit or in storage to the third
party cloud provider, the lack of segregation of data from other
businesses in a virtualized cloud computing environment and the lack of
audit and logging for specific security events and incidents. Examples
of mitigating security controls for these risks might include the
requirement of use of end to end encryption for confidential data in
transit and storage at the cloud provider, the use of virtual firewall
and secure hypervisor architecture for securing tenants in SaaS cloud
virtualized environments and the adoption of specific audit and logging
facilities that can be used to alert both the cloud provider and the
organization outsourcing the service in the case of a security incident
as few examples.

Once these control gaps have been identified it is important to assign
the level of severity-risk and determine if compensating controls might
be implemented prior to the deployment of the cloud computing solution.
An important aspect for managing these risks is also to make sure a SLA
(Service Level Agreement) captures these risks and provides binding
contractual agreements with the cloud service provider and liability
clauses and indemnities for the organization in case these agreements
are breached.

[Category:OWASP_Application_Security_Guide_For_CISO_Project](Category:OWASP_Application_Security_Guide_For_CISO_Project "wikilink")