## The presentation

![Owasp_logo_normal.jpg](Owasp_logo_normal.jpg
"Owasp_logo_normal.jpg")An overview of the OWASP Top Ten, the OWASP
ASVS, and the OWASP Guides.

This presentation is given as part of [OWASP Software Assurance
Day](OWASP_Software_Assurance_Day_DC_2010 "wikilink") at the [| 13th
Annual Software Assurance
Forum](https://buildsecurityin.us-cert.gov/bsi/events/1133-BSI.html).

[Download the
presentation](Media:Dave_Wichers_2010-09_OWASP_DHS_SWA_Day_-_OWASP_Projects.pptx "wikilink")

## The speaker

Dave Wichers is a cofounder and the Chief Operating Officer (COO) of
[Aspect Security](http://www.aspectsecurity.com), a company that
specializes in application security services.

As a volunteer to OWASP, Dave is:

  - A member of the [OWASP
    Board](About_OWASP#Global_Board_Members "wikilink"),
  - The [OWASP
    Conferences](:Category:OWASP_AppSec_Conference "wikilink") Chair,
  - Project lead and coauthor of the [OWASP Top
    10](OWASP_Top_Ten_Project "wikilink"),
  - Coauthor of the [OWASP Application Security Verification
    Standard](ASVS "wikilink"), and
  - Contributor to the [OWASP Enterprise Security API
    (ESAPI)](ESAPI "wikilink") project.

Dave has over 20 years of experience in the information security field,
and has focused exclusively on application security since 1998. At
Aspect, in addition to his COO duties, he is Aspect's application
security courseware lead, one of their chief instructors, and provides a
wide variety of application security consulting services to Aspect's
clients. Prior to starting Aspect, he ran the Application Security
Services Group at Exodus Communications. Dave has a Bachelors and
Masters degree in Computer Science, is a CISSP, and a CISM.

Dave can be reached at: dave.wichers (at) aspectsecurity.com or
dave.wichers (at) owasp.org

## Notes

**Getting Started with the Top Ten and OWASP Guides** – Dave Wichers We
are still not asking for secure software. Is your customer really asking
you to create secure software? There is a fundamental supply and demand
problem. No one will produce something that no one wants to buy. If
software firms spend the effort to build secure software, then it
increases the cost. If it has the same functionality but has the
invisible feature of security, then no one will buy it yet. We as
consumers must demand security from these companies we patronize.
Microsoft has worked very hard to produce secure software. Some vendors
are starting to win contracts because their software is more secure.

Microsoft was seeing roughly 8 – 15% of up front costs, but then saw
costs drop dramatically due to efficiencies and cost avoidance.
Investing in software quality can also provide a means for cost
reduction which is a huge culture problem.

Startups only care about marketshare, not security. Small companies
should have security as a priority as they gain a certain portion of
marketshare.

Open Source is not necessarily more or less secure. It varies. DHS’ HOST
program and another site setup in partnership with Coverity provide
feedback to open source developers.

When Wichers works with the DISA STIGs he look at the code to see if it
is secure. If he finds something, they fix it. If not, then they don’t
fix it. They are focusing on verification. If there is enough flaws
found, then they might ask if there is a better way to build security
in. But if we don’t demand security then we won’t get it.

Wichers discussed half a dozen projects, but OWASP has many more in
various levels of maturity. There is a bar at the top of the OWASP
website that lists some of the most mature projects. The OWASP
meritocracy allows members to start new projects and then gain traction.
There are slide decks on each OWASP project available online.

Many are listing OWASP references in either strong or weak ways. PCI
point directly to the OWASP Top 10 despite having no formal
relationship. The DISA STIG makes many references to the Top 10 for more
information.

  - [OWASP Top Ten Project](:Category:OWASP_Top_Ten_Project "wikilink")

**Top 10 Web Application Security Risks**

The first step to helping developers is to make them aware of the
issues. The Top 10 is a broad brush awareness document for any
community. But it won’t provide all the details. If you don’t understand
the technical foundation of the problems then you can’t build code to be
secure against them.

The Top 10 helps developers to understand risk. Businesses must
understand the risks and how significant they are. The business must
understand the gravity of the ramifications if this risk is exploited.
Until the business understands the risk, they won’t do anything about
it.

The managers must care for the developers to care. The Top 10 includes a
section stating that it is related to risk instead of just technical
specifications. Businesses understand and are concerned with risk.
Everything is a cost-benefit balance.

The attacks are becoming extremely professional and advanced. Economic
pressures may not come as strongly from the consumers who are
“path-of-least-resistance driven” but business-to-business pressure
will be much stronger. This has been seen in the credit card processing
industry. Google removed all of its internal Microsoft operating system
installations after the Chinese hack.

The OWASP material ranges from understanding risk, to avoiding risk, to
measuring risk, to managing risk.

Microsoft has statistics about the cost of the appsec program being zero
or negative because the cost of rework outweighs their investment. This
information is publicly available. Over time the up front cost is
reduced.

The Top 10 was created in 2003. Each year it has been condensed so it is
easily consumable. The Top 10 was always about risk, but making this
distinction has been made clearer. Although some flaws may be less
prevalent, they are just as devastating when exploited. The Top 10 is
prioritized based upon the OWASP Risk Rating Methodology.

**The OWASP Prevention Cheat Sheet** provides article on how to avoid
the most common web security problems. They are all interlinked. They
include very concise guidance for developers.

  - [OWASP Application Security Verification Standard
    Project](:Category:OWASP_Application_Security_Verification_Standard_Project "wikilink")

**The OWASP Application Security Verification Standard (ASVS)** provides
a standard for how to verify security services. This helps organizations
to compare application security service vendors. The ASVS is a positive
model stating what should be found. The byproduct is a comprehensive
roadmap of requirements which other OWASP ecosystems could leverage. The
standard is our opinion of what should be included. The ASVS is a
verification standard and is organized in terms of level of difficulty.
This is why automated verification is at level 1 and design verification
is at level 3.

  - [OWASP Legal Project](:Category:OWASP_Legal_Project "wikilink")

The government needs to ask for secure software in any form. **The OWASP
Legal Guide** facilitates the requiring of secure software in contracts.
Its use would require a smart purchaser of security to require it of
their vendor and having it as a factor of competitive bidding.

Q. Have any vendors adopted the legal language? A. A few companies have
experimented with the legal language.

  - [OWASP Development Guide](:Category:OWASP_Guide_Project "wikilink")

**The OWASP Developer Guide** was the original flagship document. The
document has languished but there is a team that is working to update
it.

  - [OWASP Enterprise Security API (ESAPI)
    Project](:Category:OWASP_Enterprise_Security_API "wikilink")

Developers need secure controls to build secure software. This document
explains the intent of this statement. It outlines the standard set of
controls needed and provides an explanation of the implementation. It
outlines standard control implementation in many popular languages. The
ESAPI source code is a great example of secure code. There are plenty of
other free OWASP tools online as well.

  - [OWASP Code Review
    Guide](:Category:OWASP_Code_Review_Project "wikilink")

**The OWASP Code Review Guide** outlines approaches to code review,
reporting, metrics, etc. by example within various languages. It will
soon be aligned with the ASVS.

  - [OWASP Testing Guide](:Category:OWASP_Testing_Project "wikilink")

**The OWASP Testing Guide** may be the largest OWASP project in terms of
the number of contributors. This may be the most popular guide due to
the number of people trying to perform testing.

  - [OWASP Common
    Numbering](http://www.owasp.org/index.php/Common_OWASP_Numbering)
    project organizes the guides in the same standardized order.

<!-- end list -->

  - [OWASP Secure Coding Practices - Quick Reference
    Guide](OWASP_Secure_Coding_Practices_-_Quick_Reference_Guide "wikilink")

\--[Walter Houser](User:Walter_Houser "wikilink") 22:13, 4 October 2010
(UTC)

[Category:OWASP_Conference_Presentations](Category:OWASP_Conference_Presentations "wikilink")