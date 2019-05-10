__FORCETOC__ We would like to thank our speakers for donating their
time and effort to help make this conference successful.

Introducing a new paradigm for integrating developers with offensive and
defensive teams to enhance SDLC. Learn how to integrate Offensive,
Defensive, and Development Teams in a structured way to provide
knowledge sharing, strengthening of defenses, coverage, and response,
and ultimately the development of a high level of security maturity over
time. This new concept of "Red + Yellow == Orange && Blue + Yellow ==
Green" focuses on the role of Developers as a critical piece of security
assurance activities when combined with Security Teams. Orange Teams add
value when they have been integrated into SDLC by creating a cycle of
perpetual offensive testing and threat modeling to make software more
secure over time through a high level of dedicated interaction. Green
teams add value when they help ensure software is capable of providing
powerful logging and DFIR information. This talk will evaluate the
current gap in skills and knowledge, and explore how different Team
combinations can lead to more secure software.

No one builds software completely from scratch anymore. The use of open
source software is at an all-time high. The benefits in terms of time to
market are too great to ignore. Once incorporated, they are orphaned and
left to fend for themselves. That’s a huge problem when a CVE is
announced and we are left with a hugely expensive upgrade or
uncontrolled exposure to risk. Let's talk strategy.

This presentation is based on my experience in different products with
which I was involved. It includes considerations that every developer
should take to secure the applications. As developers, our task to
figure out and remediate OWASP Top 10 vulnerabilities is the top
priority, but there is no one automated tool that can detect all
security flaws listed in the OWASP Top 10. It is necessary to use a
combination of different tools to make sure our application is free from
any vulnerabilities. I am going to go through the OWASP Top 10
vulnerabilities list and recommend/demonstrate different tools to use to
help reproduce and remediate each vulnerability.

By far the best known “list” in the arena of application security is the
OWASP Top 10. There’s no question it has helped greatly over the years
to raise awareness of common vulnerabilities in web applications like
SQL injection, XSS, and CSRF. But in the end that’s all it is – an
awareness document. This session will introduce and examine a different
top ten list that is aimed at developers who are actually writing the
code and building the software. It is known as the OWASP Top 10
Proactive Controls and it’s chock-full of practical, application
security goodness. The audience will learn how secure development
techniques and prescriptive guidance provided in the Top 10 Proactive
Controls can move the needle toward having highly secure applications
throughout an organization.

Continuous Integration\!\! DevSecOps\!\! SecDevOps\!\! Application
security automation gets lots of buzz and products are evolving to
accommodate it, says Gartner. I'll explain the simple setup and process
we have using Qualys, Jenkins, java and Excel to automate the creation,
rescan and reporting of web app vulnerability scans. I'll also compare
the APIs of some commercial products. I'll describe the tasks you need
to do before automation can happen and how we architected security and
access control into our process.

Many web applications have fairly complicated policies for determining
who can access what data. A messy, but not uncommon, case is
multi-tenant applications — say, a webapp with multiple client firms,
different levels of access for particular users at each firm (perhaps in
terms of which users have access to which projects or records within the
app). Implementing all this access control with ad hoc logic can be
tricky and error-prone. It can be hard to verify that different features
are all applying the same rules. And once that’s done, augmenting it
(say, to add a notion of “group” privileges within a tenant firm) can be
fraught with peril.

An alternative is to explicitly represent the rules that the software
ought to follow, in terms of who can access which elements of data, and
what operations they can perform on them. Making this tangible,
centralized data makes it possible to inspect, and easy to change, with
assurance that new rules will be consistently followed.

This talk will describe the evolution of a system with a very
complicated permissioning model over several years, describing benefits
and pitfalls. It will also describe how much the application logic has
to be driven by introspection on the rules — using them, for example, to
build queries on which objects of particular types a user has permission
to access or modify. In the end, the performance costs were modest, and
the tradeoff with maintenance has made the exercise well worthwhile.

Keeping your applications safe can be a Sisyphean task. When an issue is
found and fixed, how can you ensure the problem never resurfaces? This
talk will walk through a real-world example of finding a major
vulnerability, fixing it with an elegantly simple security control, and
preventing it from coming back via a custom checkin-time code scan. How
do we take care of a vulnerability? We Only Handle It Once.

Web browsers have become the predominant means for developing and
deploying applications, and thus they often handle sensitive data such
as social interactions or financial credentials and information. As a
consequence, defensive measures such as TLS, the Same-Origin Policy
(SOP), and Content Security Policy (CSP) are critical for ensuring that
sensitive data remains in trusted hands. Browser extensions, while a
useful mechanism for allowing third-party extensions of core browser
functionality, pose a security risk in this regard since they have
access to privileged browser APIs that are not necessarily restricted by
the SOP or CSP. Because of this, they have become a major vector for
introducing malicious code into the browser. Prior work has led to
improved security models for isolating and sandboxing extensions, as
well as techniques for identifying potentially malicious extensions. The
area of privacy violating browser extensions has so far been covered by
manual analysis and systems performing search on specific text on
network traffic. However, comprehensive content-agnostic systems for
identifying tracking behavior at the network level are an area that has
not yet received significant attention.

In this talk, I will present a dynamic technique for identifying
privacy-violating extensions in Web browsers that relies solely on
observations of the network traffic patterns generated by browser
extensions. Next I will present Ex-Ray, a prototype implementation of
this technique for the Chrome Web browser, and use it to evaluate all
extensions from the Chrome store with more than 1,000 installations
(10,691 in total). Our evaluation finds new types of tracking behavior
not covered by state of the art systems. Finally, I discuss potential
browser improvements to prevent abuse by future user-tracking
extensions.

This talk is about a paper accepted to ACSAC 2017.

Great talk for beginners or people learning about web application
vulnerabilities\! At this point, most people are aware of SQL injection
and Cross Site Scripting. We've seen how they work and seen how to
mitigate them. Great. That's about all I have to say about those. Let's
look at the additional web application vulnerabilities that may be
getting overlooked. Let's look at other common vulnerabilities like
Cross Site Request Forgery, Session Management, Clickjacking. We'll
learn how to find them, exploit them and mitigate them.

Over the past year we have seen an increased use of open source
intelligence for attacking institutions. The recent ransomware attacks
have proven that healthcare institutions need more security and
monitoring more than ever.

In my talk I will explain how to use deep web tools - shodan and censys
effectively to track hospitals and healthcare institutions. I will share
some of the interesting scenarios that I have seen and finally how to
create scripts to automate this process. This includes optimizing the
payloads and understanding how to narrow down to targets.

CSRF remains an elusive problem due to legacy code, legacy frameworks,
and developers not understanding the problem or how to protect against
it. Wiping out CSRF introduces primitives and strategies for building
solutions to CSRF that can be bolted on to any http application where
http requests and responses can be intercepted, inspected, and modified.
Modern frameworks have done a great job at providing solutions to the
CSRF problem that automatically integrate into the application and solve
most of the conditions. However, many existing apps and new apps that
don't take advantage of these frameworks or use them incorrectly are
still plagued with this problem. Wiping out CSRF will provide an in
depth overview of the various reasons that CSRF occurs and provide
payload examples to target those specific issues and variations. We'll
see live demos of these attacks and the protections against them. Next
we'll look at how to compose these primitives into a complete solution
capable of solving most cases of CSRF explaining the limits and how to
layer them to address potential short comings. Finally we'll finish by
looking at Same Site Cookies, a new extension to cookies that could be
the final nail in the coffin, and see how to use the prior solution as a
graceful degradation for user agents that don't support it yet.

Reconnaissance is the first stage of a hacking process. During this
stage, the attacker collects as much information as possible about the
target from publicly available sources. Most common sources used are
search engines, social networks & technical forums. It’s during this
stage the attacker identifies low hanging fruits and the weak spots of
the target. The information collected in the reconnaissance stage is
used in further stages to tailor attacks against a particular weak spot
of the organization.

In passive reconnaissance, the attacker tries to be as non-intrusive as
possible to stay out of the target’s radar. Public domain data is the
main source of information in this stage of an attack. The key motto of
a passive reconnaissance is to identify the attack surface without
triggering any alert. In this talk, I will be covering how a systematic
approach in performing non-intrusive recon can help us find gems.