## The Presentation: "Automated vs. Manual Security: You can't filter The Stupid"

Automated application security tools have been available for quite a
while, but their manual counterparts are still doing quite well. This
presentation will cover the relative strengths and weaknesses of both
automated solutions, such as Web Application Firewalls (WAFs), source
code review tools, and automated application scanners, and manual
approaches, namely application penetration tests and manual code
reviews. The presentation will conclude that automated tools are well
suited for lower-priority applications, but manual analysis is important
for critical applications.

Automated tools certainly have some strengths (namely low incremental
cost, detecting simple vulnerabilities, and performing highly repetitive
tasks). In addition to preventing some attacks, WAFs also have
advantages for some compliance frameworks. However, automated solutions
are far from perfect. To begin with, there are entire classes of very
important vulnerabilities that are theoretically impossible for
automated software to detect (at least until HAL comes online). Examples
include complex information leakage, race conditions, logic flaws,
design flaws, subjective vulnerabilities such as CSRF, and multistage
process attacks.

Beyond that, there are many vulnerabilities that are too complicated or
obscure to practically detect with an automated tool. Automated tools
are designed to cover common application designs and platforms.
Applications using an unusual layout or components will not be
thoroughly protected by automated tools. Realistically, only the most
vanilla of web applications written on common, simple platforms will
receive solid code coverage from an automated tool.

On the other hand, manual testing is far more versatile. An experienced
penetration tester can identify complicated vulnerabilities in the same
way that an attacker does. Specific, real-world examples of
vulnerabilities only recognizable by humans will be provided. The
diversity of vulnerabilities shown will clearly demonstrate that all
applications have the potential for significant vulnerabilities not
detectible by automated tools.

Manual source code reviews present even more benefits by identifying
vulnerabilities that require access to source code. Examples include
“hidden” or unused application components, SQL injection with no
evidence in the response, exotic injection attacks (e.g. mainframe
session attacks), vulnerabilities in back-end systems, and intentional
backdoors. Many organizations assume that this type of vulnerability is
not a large threat, but source code can be obtained by disgruntled
developers, by internal attackers when the repository isn’t properly
secured, by exploiting platform bugs or path directory traversal
attacks, and by external attackers using a Trojan horse or similar
technique.

## The Speakers: Charles Henderson & David Byrne

Charles Henderson has been in the security industry for over 15 years
and manages the Application Penetration Testing and Code Review Practice
at Trustwave. He has specialized in application security testing and
application security assessment throughout his career but has also
worked in physical security testing and network security testing.

David Byrne has almost a decade of experience in information security,
specializing in web application penetration testing. Currently, he is a
Senior Security Consultant in Trustwave’s SpideLabs division. Before
joining Trustwave, David was the Security Architect at Dish Network. In
addition to penetration testing, David has extensive experience working
with developers and implementers to design security controls into
applications from the ground up. He also has worked with governance and
compliance groups to create security policies and standards documents.

In 2006, David started the Denver chapter of OWASP. In 2008, he released
Grendel (grendel-scan.com), an open source web application security
scanner. David has spoken at many industry events, including Black Hat,
DEFCON, Toorcon, and the Computer Security Institute’s annual
conference.

[Back to Presentation
Agenda](Front_Range_OWASP_Conference_2009#Agenda_and_Presentations:_5_March_2009 "wikilink")