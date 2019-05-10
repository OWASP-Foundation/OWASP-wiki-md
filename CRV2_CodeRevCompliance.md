# Code review and compliance

Many organizations with responsibilities such as safeguarding the
integrity, confidentiality and availability of their software and data
need to meet compliance.Compliance is most of the time a mandatory
subject instead of a free-will decision taken by the organization. It
comes in many forms and flavors such as PCI (Payment Card Industry),
Central Bank regulations, Auditing objectives and HIPPA among others.

Compliance is an integral part of software security development
life-cycle and Code review is an important piece in this constellation.
Many compliance rules involves an execution of Code reviews in order to
comply with certain regulations.

To execute proper code reviews that meet compliance rules it is
imperative to use an approved methodology . This guide, for example, is
mentioned in many compliance requirements such as PCI, specifically on
Requirement 6: "Develop and maintain secure systems" . PCI-DSS 3.0 which
is available since November 2013, exposes a series of requirements which
apply to development of software and identifying vulnerabilities in
code. The Payment Card Industry Data Security Standard (referred to as
PCI-DSS from now on) became a mandatory compliance step for companies
processing credit card payments in June 2005.

Performing code reviews on custom code has been a requirement since the
first version of the standard. This section will discuss what needs to
be done with regards to code reviews to be compliant with the relevant
PCI requirements.

## PCI-DSS Code Review Requirements

The PCI standard contains several points relating to secure application
development, but we will focus solely on the points which mandate code
reviews here. All of the points relating to code reviews can be found in
requirement 6: Develop and maintain secure systems and applications.
Specifically requirement 6.3.2 mandates a code review of custom code:

Review custom code prior to release to production or customers in order
to identify any potential coding vulnerability (using either manual or
automated processes) to include at least the following:

  - Code changes are reviewed by individuals other than the originating
    code author, and by individuals knowledgeable about code-review
    techniques and secure coding practices.
  - Code reviews ensure code is developed according to secure coding
    guidelines
  - Appropriate corrections are implemented prior to release.
  - Code-review results are reviewed and approved by management prior to
    release.

6.5 Address common coding vulnerabilities in software-development
processes as follows:

  - Train developers in secure coding techniques, including how to avoid
    common coding vulnerabilities, and understanding how sensitive data
    is handled in memory.
  - Develop applications based on secure coding guidelines.

OWASP guidelines are mentioned in the PCI requirements as one of the
advised best practices to be followed."Note: The vulnerabilities listed
at 6.5.1 through 6.5.10 were current with industry best practices when
this version of PCI DSS was published. However, as industry best
practices for vulnerability management are updated (for example, the
OWASP Guide, SANS CWE Top 25, CERT Secure Coding, etc.), the current
best practices must be used for these requirements". (PCI-DSS, pg 55)

The current version of the standard (version 3.0 at the time of writing)
contains requirement 6.6. This requirement gave companies options:

  - Reviewing public-facing web applications via manual or automated
    application vulnerability security assessment tools or methods, at
    least annually and after any changes
  - Installing an automated technical solution that detects and prevents
    web-based attacks (for example, a web-application firewall) in front
    of public-facing web applications, to continually check all traffic.

The PCI Council expanded option one to include internal resources
performing code reviews. This added weight to an internal code review
and should provide an additional reason to ensure this process is
performed correctly.

## PA-DSS Code Review requirements

The Payment Application Data Security Standard (PA-DSS) is a set of
rules and requirements similar to PCI-DSS however, this applies
especifically to software vendors and others who develop payment
applications that store, process, or transmit cardholder data as part of
authorization or settlement, where these payment applications are sold,
distributed, or licensed to third parties. Requirements regarding Code
review are also applied since these are derived from PCI-DSS. In PA-DSS
is treated in requirement 5. Develop secure payment applications

"5.2 Develop all payment applications (internal and external, and
including web administrative access to product) based on secure coding
guidelines.

5.1.4 Review of payment application code prior to release to customers
after any significant change, to identify any potential coding
vulnerability.

Note: This requirement for code reviews applies to all payment
application components (both internal and public-facing web
applications), as part of the system development life cycle. Code
reviews can be conducted by knowledgeable internal personnel or third
parties.

Aligns with PCI DSS Requirement 6.3.2" (PCI, 2010)

## CISSP best practices and compliance

This Code Review guideline offers an approved methodology for these
requirements.As mentioned in the Official Guide to the CISSP CBK
"“Several organizations have developed frameworks for secure web
development. One of the most common is the Open Web Application Security
Project (OWASP)14 OWASP has several guides available for web application
development including:

  - Development Guide
  - Code Review Guide
  - Testing Guide
  - Top Ten web application security vulnerabilities

” (Excerpt From: Hernandez. “Official (ISC)2 Guide to the CISSP CBK.”
iBooks. <https://itun.es/us/mFXoL.l>)

This guide is definitely part of any security practitioner library and
it supports an approved methodology to review code.

## References

PCI-DSS Version 3, Security Council" Payment Card Industry Data Security
Standard,Requirements and Security Assessment Procedures" available at
<https://www.pcisecuritystandards.org/documents/PCI_DSS_v3.pdf>
(Accessed on December 9, 2013) PA-DSS Version 2, Security Council
"Payment Application Data Security Standard, Requirements and Security
Assessment Procedures" available at
<https://www.pcisecuritystandards.org/documents/pa-dss_v2.pdf>( Accessed
on December 20, 2013)