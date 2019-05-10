## Introduction

The Open Web Application Security Project (OWASP) is dedicated to
helping organizations understand and improve the security of their web
applications and web services. This list was created to focus
corporations and government agencies on the most serious of these
vulnerabilities. Web application security has become a hot topic as
companies race to make content and services accessible though the web.
At the same time, hackers are turning their attention to the common
weaknesses created by application developers.

When an organization puts up a web application, they invite the world to
send them HTTP requests. Attacks buried in these requests sail past
firewalls, filters, platform hardening, and intrusion detection systems
without notice because they are inside legal HTTP requests. Even
“secure” websites that use SSL just accept the requests that arrive
through the encrypted tunnel without scrutiny. **This means that your
web application code is part of your security perimeter.** As the
number, size and complexity of your web applications increases, so does
your perimeter exposure.

The security issues raised here are not new. In fact, some have been
well understood for decades. Yet for a variety of reasons, major
software development projects are still making these mistakes and
jeopardizing not only their customers’ security, but also the security
of the entire Internet. There is no “silver bullet” to cure these
problems. Today’s assessment and protection technology is improving, but
can currently only deal with a limited sub-set of the issues at best. To
address the issues described in this document, organizations will need
to change their development culture, train developers, update their
software development processes, and use technology where appropriate.

**The OWASP Top Ten is a list of vulnerabilities that require immediate
remediation.** Existing code should be checked for these vulnerabilities
immediately, as these flaws are being actively targeted by attackers.
Development projects should address these vulnerabilities in their
requirements documents and design, build, and test their applications to
ensure that they have not been introduced. Project managers should
include time and budget for application security activities including
developer training, application security policy development, security
mechanism design and development, penetration testing, and security code
review.

We encourage organizations to join the growing list of companies that
have **adopted the OWASP Top Ten** as a minimum **standard** and are
committed to producing web applications that do not contain these
vulnerabilities.

We have chosen to present this list in a format similar to the highly
successful SANS/FBI Top Twenty List in order to facilitate its use and
understanding. The SANS list is focused on flaws in particular widely
used network and infrastructure products. Because each website is
unique, the OWASP Top Ten is organized around particular types or
categories of vulnerabilities that frequently occur in web applications.
These categories are being standardized in the OASIS Web Application
Security (WAS) XML Project.

This list represents the combined wisdom of OWASP experts, whose
experience includes many years of application security work for
governments, financial services, pharmaceuticals and manufacturing, as
well as developing tools and technology. This document is designed to
introduce the most serious web application vulnerabilities. There are
many books and guidelines that describe these vulnerabilities in more
detail and provide detailed guidance on how to eliminate them. One such
guideline is the OWASP Guide available at <http://www.owasp.org>.

The OWASP Top Ten is a living document. It includes instructions and
pointers to additional information useful for correcting these types of
security flaws. We update the list and the instructions as more critical
threats and more current or convenient methods are identified, and we
welcome your input along the way. This is a community consensus document
– your experience in fighting attackers and in eliminating these
vulnerabilities can help others who come after you. Please send
suggestions via e-mail to topten@owasp.org with the subject "OWASP Top
Ten Comments.”

__NOEDITSECTION__

[Category:OWASP Top Ten
Project](Category:OWASP_Top_Ten_Project "wikilink")