## The presentation

![Owasp_logo_normal.jpg](Owasp_logo_normal.jpg
"Owasp_logo_normal.jpg")An introduction to the OWASP mission.

This presentation is given as part of [OWASP Software Assurance
Day](OWASP_Software_Assurance_Day_DC_2010 "wikilink") at the [| 13th
Annual Software Assurance
Forum](https://buildsecurityin.us-cert.gov/bsi/events/1133-BSI.html).

[Download the
presentation](Media:Jeff_Williams_2010-09_OWASP_DHS_SWA_Day_-_OWASP.pptx "wikilink")

## The speaker

Jeff Williams is the founder and CEO of Aspect Security, specializing
exclusively in application security professional services. Jeff also
serves as the volunteer Chair of the Open Web Application Security
Project (OWASP). He has made extensive contributions to the application
security community through OWASP, including writing the Top Ten,
WebGoat, Secure Software Contract Annex, Enterprise Security API, OWASP
Risk Rating Methodology, and starting the worldwide local chapters
program. If nothing else, Jeff is probably the tallest application
security expert in the world and likes nothing better than discussing
new ideas for changing the way we build software.

## Notes

Introduction to OWASP – Jeff Williams takes a different view of
assurance. He is promoting the assurance view into high speed software
development. Also he will explain how OWASP works and the methods used
to change the world. These are ideas that can actually change the game.

“Security is a process, not a product.” If security is a process we
could just follow it. Security is more like an artifact of a process; an
emergent characteristic of following a procedss. We in OWASP like to
look at security as an eco-system.

Background – There are roughly 10 million developers writing code and
about a trillion lines of code. If there were just 100 developers
looking at 100 apps for 100 organizations.

  - 83 apps would have a serious vulnerability
  - 72 apps would have XSS
  - 40 would have SQL injection
  - 1 company would have responsible appsec program (rounded up)
  - 1 developer would have any security training
  - All applications would have code from unknown origin
  - 90 apps use libraries with known unpatched holes
  - 5 apps have has some sort of scan or test
  - 1 app has had a manual code review (rounded up)
  - There is no amount of automation that can find the problems
  - 0 apps provide any visibility into security

Every website has a privacy page, but none have a security page.

How do you want the world to be? Is this acceptable? We trust this
software. Software is becoming more and more complicated every day. We
are connecting our architectures at an amazing rate. We trust it to do
more sensitive things.

Three forces: complexity, connectivity, criticality – create a perfect
storm of insecurity

What is stopping us from having assurance? 1. Trust – we trust the
internet, we naturally trust software, we assume no vulnerabilities
instead of the other way around of having to be proven 2. Blame – we
instantly blame the developers. 3. Hide – we hide security. When
developers are blamed, they hide their security measures.

These three aspects create a toxic eco-system. We have no other option
than to trust due to this system. This is a self-enforcing cycle that
keeps security down.

OWASP’s mission is focused on visibility to break the cycle. OWASP is
working toward a security facts label (like a food nutrition label)

There is an underlying economic principle at work. At markets where
there is asymmetric information, it is very difficult for consumers to
get a fair price. When you buy software you have no idea if it is a
lemon so you cannot get a fair price for security. Until we fix the
software market, nothing else matters. We will not get secure code out
of it. See the 1970 paper by the economist George Akerlof [The Market
for Lemons](http://en.wikipedia.org/wiki/The_Market_for_Lemons). Ross
Anderson’s paper [Why Information Security Is So
Hard](http://www.acsac.org/2001/papers/110.pdf) also discusses the
ecomonic challenges facing security practitioners.

OWASP is an eco-system. An OWASP intern started the
[Pythonsecurity.org](http://www.Pythonsecurity.org) project due to a
void of information. These ecosystems pull together information, a
community, etc. There are builders and breakers working together for
security. Security is co-evolutionary. The bad guys break in, the good
guys add more defenses, repeatedly. This is the process that generates
security.

Evolution of an ecosystem – individual, website, contributors,
self-sustaining, etc.

OWASP is trying to bootstrap lots of ecosystems like this Python
Security ecosystem. OWASP operates on a shoestring budget. It has only
two full time employees. It is a 501c3 organization. OWASP just began
the college chapters program. This program seeks to embed security
knowledge into all colleges with computer science degrees.

OWASP offers many conferences around the world. OWASP works with
industry. OWASP has a connections committee to bring together people who
need to speak to each other to improve security. OWASP receives
approximately 15000 page views on its website. Last week when twitter
was infected with the XSS worm, there was a large spike in traffic.

The reasoning behind the agenda: start narrow with things you can use
now, then expose you to ways to improve security, show you the OWASP
live compact disc (CD), then move toward success stories from
implementing the DISA STIG.

While consumers may not be risking a significant amount, there are
companies that are losing millions of dollars per day, and this does not
need to be happening.

Q. How do you get a developer passionate about security? What made the
community shift toward focusing on security?

A. Developers want to do the right thing and build secure code. There is
a lot for developers to learn. I don’t think we can expect developers to
become security experts. We need to focus on making security easier for
developers. We should take security out of their hands and put it into
standards and tools. Visibility is at the core of the solution to get
people focused on it and to improve.

Q. You mentioned critical infrastructure and legacy. What is OWAPS’s
position on legacy systems? There must be an interim solution.

A. There has to be an interim because of the vast amount of lines of
code. We need to take the same approach with new systems. Identify the
risk, prioritize the risks, and then put controls in place to counter
them. We become hypnotized by little problems that are revealed by
tools, but we miss the larger more important risks that may not be as
easy to detect.

Q. Is there a roadmap for APIs? A. We will cover that in the ESAPI
presentation.

Q. So many people think of other types of security other than
application security. How can we bridge these two communities?

A. We have had challenges turning network security folks into software
security folks. We have had luck with making developers more aware of
software security. There is more work to be done.

Q. There is a large knowledge gap between the developers and the
security folks that have never written a line of code. Could OWASP do
anything to point out the knowledge gap?

A. There is no silver bullet. The solution is complex. If a new cycle of
visibility and collaboration can be created, then this would make a big
difference. We have an issue of many compliance and security people that
are not engineers. They are analyzing artifacts without understanding
the fundamental pathways of how the code works. There are no people in
between the developers and the assessors. We need people who understand
both to serve this intermediate position. We either need to teach
security people engineering or vice versa.

When you think of software assurance, please don’t confuse all of this
with verification. Verification is not application security. We should
spend 80% building it right, then 10% checking, then 10% for other
things.

\--[Walter Houser](User:Walter_Houser "wikilink") 22:13, 4 October 2010
(UTC)

[Category:OWASP_Conference_Presentations](Category:OWASP_Conference_Presentations "wikilink")