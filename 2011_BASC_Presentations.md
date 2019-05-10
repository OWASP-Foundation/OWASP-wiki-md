__FORCETOC__ We would like to thank our speakers for donating their
time and effort to help make this conference successful.

Don’t you hate it when you are minding your own business, in a familiar
place, in the right time…and you end up in a strange place, in the wrong
time, maybe even the wrong century? In this talk I will provide tips and
tricks for dealing with this all-too-common tragedy. Don’t be a victim,
be prepared.

(This is actually an informative, yet lighthearted introduction to the
topic of pragmatic, risk-based security, but without using terms like
“risk-based security”. There are two target audiences for this talk,
those who need a non-technical introduction to thinking about risk,
threat modeling, and security, and those interested in using “subversive
education” to get their message out to an audience).

Last year’s Lord of the Bing presentation stabbed Google Hacking in the
heart with a syringe full of adrenaline and injected life back into a
dying art form. New attack tools and modern defensive techniques
redefined the way people thought about Google Hacking. Among these were
the first ever Bing Hacking tool and the Google/Bing Hacking Alert RSS
feeds, which have grown to become the world’s single largest repository
of live vulnerabilities on the web. And it was only the beginning…

This year, we once again tear down the basic assumptions about what
Google/Bing Hacking is and the extent to which it can be exploited to
target organizations and even governments. In our secret underground
laboratory, we’ve been busy creating an entirely new arsenal of Diggity
Hacking tools. Just a few highlights of the new tools are:

  - BaiduDiggity – first ever Baidu hacking tool, which targets
    vulnerabilities disclosed by China’s dominant search engine. DEMO:
    Live targeting of vulnerabilities in Chinese government websites
    exposed via Baidu.

<!-- end list -->

  - DroidDiggity – fully functional GoogleDiggity and BingDiggity
    application for Android phones.

<!-- end list -->

  - GoogleCodeSearchDiggity – identifying vulnerabilities in open source
    code projects hosted by Google Code, MS CodePlex, SourceForge, and
    more. The tool comes with over 40 default searches that identify SQL
    injection, cross-site scripting (XSS), insecure remote and local
    file includes, hard-coded passwords, and much more.

<!-- end list -->

  - FlashDiggity – automated Google
    searching/downloading/decompiling/analysis of SWF files to identify
    Flash vulnerabilities and info disclosures.

<!-- end list -->

  - SHODAN Hacking Alerts – new live vulnerability RSS feeds based on
    results from the popular SHODAN hacking search engine.

<!-- end list -->

  - MalwareDiggity and MalwareDiggity Alerts – leveraging Bing API and
    the Google SafeBrowsing API together to provide an answer to a
    simple question, “Am I being used as a platform to distribute
    malware to people who visit my website?”

<!-- end list -->

  - AlertDiggity – Windows systray application that filters the results
    of the various Google/Bing/Shodan Hacking Alerts RSS feeds and
    notifies the user if any new alerts match a domain belong to them.

<!-- end list -->

  - DiggityDLP – Data loss prevention tool that leverages Google/Bing to
    identify exposures of sensitive info (e.g. SSNs, credit card
    numbers, etc.) via common document formats such as .doc, .xls, and
    .pdf. Also utilizes Google APIs for searching across Google
    Docs/Spreadsheets for data leaks.

That is just a taste of the new tools that will be explored in this DEMO
rich presentation. So come ready to engage us as we re-define Google
Hacking once again. WARNING: For safety, you should be in good health
and free from high blood pressure, heart, back or neck problems, motion
sickness, or other conditions that could be aggravated by this
adventure.

Binary instrumentation is a tool for understanding the dynamic behavior
of a program by observing its execution with injected code. Security and
Privacy researchers use binary instrumentation tools to analyze program
and malware behavior. Binary instrumentation makes it possible to detect
programs that decrypt them self at runtime and malware that exploits
buffer overflow. It can be used to perform taint analysis to track the
flow of data through a program. Instrumentation can also help find
exploitable bugs like memory use after deallocation and references to
uninitialized data. The talk will describe a popular instrumentation
tool called Pin and connect it to security/privacy related ideas. The
talk would be interesting to people interested in analyzing behavior of
native applications and developing their own tools.

MozSecWorld is a web security reference site. It can teach you simple
ways that you can make your own websites more secure. You'll learn
through diagrams, explanations, and best of all, live demos\! :) If you
are a web developer, you might find the open-source code for each demo
helpful too.

This presentation will feature the recently unveiled, official OWASP
Mobile Top 10 Risks. As many agree that mobile application security is
in its infancy, this list is intended to help developers and
organizations prioritize their security efforts throughout the
development life cycle. Many of the same mistakes made over the past
decade in other areas of application security have managed to resurface
in the mobile world. There have also been many new security challenges
introduced by mobile applications and platforms. Through the OWASP
Mobile Security Project, the primary goal is to enhance the visibility
of mobile security risks just as OWASP has successfully done for the
web.

As the attack surface and threat landscape for mobile applications
continues to rapidly evolve, arming developers with the tools they need
to succeed is essential. Each environment presents very unique and
different risks to consider. Our research and findings will be presented
from a platform agnostic perspective.

Client-side development with JavaScript has grown significantly thanks
to Ajax, the plethora of JavaScript libraries such as jQuery, and
powerful JavaScript engines such as Google's V8. With the rapid push for
HTML5 and the emergence of Node.js, JavaScript has become paramount.
However, we are starting to move away from the same-domain policy.
Currently, the XMLHttpRequest object in the latest versions of Chrome
and Firefox now supports cross-domain communications to a degree. HTML5
has also introduced a number of features including WebWorkers,
cross-document messaging, and WebSockets that are JavaScript-heavy and
have raised a number of security issues. This presentation will also
delve into the best practices of rendering and parsing JSON, the
security woes surrounding WebGL, and the state of creating and running a
Node.js web server

Data breaches through Web application vulnerabilities have become
particularly rampant. Point solutions -- for example, a Web Application
Firewall that scans requests destined to the Web app -- can only stop a
limited number of attack patterns, and do not provide any protection
from a breach once a vulnerability is eventually exploited. We have been
researching a complementary approach to prevent breaches, based on the
idea that if sensitive data is tracked closely enough, an organization
can prevent breaches without worrying about Web application
vulnerabilities that lead to breaches.

We have designed a system, Pedigree, that associates tamper-proof tags
with database records and files, and uses an OS-level module to track
the flow of tagged data through the various components of a Web
application. Pedigree also tags network data, ensuring that a simple
firewall or switch can identify the provenance of a flow using the tag
on its packets. Thus, the firewall can choose to permit a flow that is a
response for an authorized Webapp user request to pass through it, while
denying flows that are unauthorized and likely correspond to malicious
exfiltration requests (e.g., an SQL injection).

In this talk, I will present the architecture of Pedigree and describe
how Pedigree might be integrated with existing Web application
frameworks and firewalls.

Information gathering is not only the first step, but perhaps the most
important repeated process within penetration testing. How well a tester
is capable of learning the characteristics and nuances of an application
can make all the difference in comprehensive testing and sophisticated
attacks. Information gathering is far more than merely mapping an
application.

This talk focuses on common pitfalls and misconceptions of information
gathering, and how we can approach it better. Using strategies from
reverse engineering and forensics, we will learn the skills and tools
needed to find evidence, grok what it means, so that we can ensure
ensure consistent & comprehensive understandings of how a site works.
Specific things that will be covered include: Anti-patterns, learning
behaviors of an application, reading exceptions between the lines,
finger printing a website beyond HTTP headers, creating a working API
for scripted attacking, and content discovery beyond throwing massive
wordlists at the wall.

Tools which support these tasks, and counter measures that make this
more challenging will be discussed throughout the talk.

Ever wanted to know more about how static binary analysis works? It's
complicated. Ever want to know how C++ language elements are
automatically transformed? The high-level overview of how machines
analyze code for security flaws is just the beginning. In this talk
we'll be delving into the gritty details of the modeling process.

With the ever increasing market for smart phones, application developers
and consumers are making a mad dash for the mobile application
architecture. Much like the race to the web many are ignoring the
security lessons previously learned and are creating a new avenue of
attack which puts individuals as well as organizations at risk. Focusing
on the two major players in this space, Apple iOS and Google Android,
this talk will focus on the types of issues common to mobile apps and
will provide advice for both smart phone owners as well as application
developers on how they can protect the data which is being entrusted to
these devices.

Theoretically, the security industry knows that mobile phones are an
exposed attack surface. Practically, there has been very little
attention paid to the subject. As an introduction, the resources that a
mobile phone can provide to a hacker will be explained. These include
persistent internet connections (providing an entry point to any
physically near network) and a low profile(which assists in evading both
physical security). Next, discussion will focus on the construction of
the proof of concept: using chroot jails with qemu files compiled for
the ARM processor architecture. With the proof of concept model in hand,
the presentation will include discussion of practical threat modeling
demonstrating the usage of the above benefits. Threats discussed in
depth: -a targeted cyber attack/penetration test, leveraging a mobile
phone as an entry point -using the phone as part of a less focused
campaign to compromise poorly protected personal resources such as
laptops or other mobile phones in coffeeshops. To conclude, focus will
be placed on further work. Potential opportunities for further research
include packaging the qemu files necessary to run an emulated Linux
environment as a payload.

Web application firewalls (WAFs) are an additional security layer that
can help protect against 'some' common attacks as from the OWASP top ten
security risks list. By customizing the rules to your applications, many
attacks can be identified and thwarted. However, this requires
significant effort with testing and maintaining application change
control. Participants will come away with the basics of web application
firewalls, differences, best practices and learn some common
characteristics of using them.