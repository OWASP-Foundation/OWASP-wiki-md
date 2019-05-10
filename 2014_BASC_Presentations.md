__FORCETOC__ We would like to thank our speakers for donating their
time and effort to help make this conference successful.

Securing code is important. But history has shown us that we can never
be certain that our code is 100% perfect. This becomes particularly true
in rapidly evolving environments. As an industry we need to take a
broader look. What security features are provided by the hardware, OS,
language, compiler, and even application type? Join us bright and early
as Dr. DeMott kicks off the 2014 Boston Application Security Conference
with a Keynote you won’t forget.

The presentation focuses on problems of following bad Mobile development
practice. During this session, you will learn how to perform a Code
Assisted PenTest on Mobile applications and uncover some well-known and
some other not so well known security issues. It is far easy to gain a
practical knowledge of security vulnerabilities than it is to read about
them. Watch as Dinesh walks you through custom created demo applications
and source code review tools, to catch security flaws noted in the
various hand-held devices. Expect to see a lot of demos, tools, hacking
and a lot of fun.

Graphical user interfaces (GUIs) contain a number of common visual
elements or widgets such as labels, text fields, buttons, and lists.
GUIs typically provide the ability to set attributes on these widgets to
control their visibility, enabled status, and whether they are writable.
While these attributes are extremely useful to provide visual cues to
users to guide them through an application's GUI, they can also be
misused for purposes they were not intended. In particular, in the
context of GUI-based applications that include multiple privilege levels
within the application, GUI element attributes are often misused as a
mechanism for enforcing access control policies.

In this session, we introduce GEMs, or instances of GUI element misuse,
as a novel class of access control vulnerabilities in GUI-based
applications. We present a classification of different GEMs that can
arise through misuse of widget attributes, and describe a general
algorithm for identifying and confirming the presence of GEMs in
vulnerable applications. We then present GEM Miner, an implementation of
our GEM analysis for the Windows platform. We evaluate GEM Miner using
real-world GUI-based applications that target the small business and
enterprise markets, and demonstrate the efficacy of our analysis by
finding numerous previously unknown access control vulnerabilities in
these applications.

As defenders, we have to be right 100% of the time where an attacker
only needs to be right once. The attack surface of a modern web site is
incredibly large and we need to be aware of all of it. Additionally,
individual attacks may not always be effective but sometimes using them
together can gain the desired effect. In this talk, we’ll take a look at
the whole attack surface for a typical web site and the various ways
that an attacker will use to compromise a site.

This presentation will look at the relationship between security
architecture and application architecture, specifically on the impact on
application security from recent proposed changes to the Clark-Wilson
integrity model. I'll explore those changes in depth, discuss the
implications for application design. I'll also discuss the implications
of these changes to distributed application architectures such as
service oriented architectures and other distributed models.

This presentation will be based upon my recent book: Security for
Service Oriented Architectures, CRC press, and 10 years of experience
working with application security architecture in various corporations.

For a small or medium sized business (SMB) the fallout from a security
or privacy incident can be at best a PR nightmare. At their worst it can
cause irrecoverable damage and end your business by impacting sales or
ad revenue. Your user base may take a hit. You may need to draft a blog
post or email your customers describing the incident and asking them to
change passwords. A key culprit is budget constraints – as a SMB you are
allocating resources to innovating, creating, and improving your
product. Security, while important, isn't always the primary objective.

Our talk will introduce a simple framework for SMBs to focus their
security efforts. We will then discuss a common scenario applicable to
most SMBs that employs our framework; and leverages it to introduce
cheap and effective security mechanisms that provide prevention,
limitation, detection, and response capabilities. The key take away will
be the thought process and sample techniques that can enable a SMB to
take their rag-tag security outfit and turn it into a business enabler.

Development teams are embracing Mobile First Development. They are
building native iOS and Android mobile apps, some are using PhoneGap,
and others are using Appcelerator. Evolving AppSec from web applications
to include mobile is where Mobile First AppSec comes in. Mobile First
AppSec describes what application security teams must consider for
successfully testing mobile applications. The heart of Mobile First
AppSec is driving the security testing based on the mobile application’s
architecture. This talk discusses the popular mobile application
architectures and how the architecture drives risk. The talk then
relates the different application architectures and development
frameworks to differences in their threat model and the consequences on
security tests and testing techniques.

Like all software vendors, EMC faces challenges when it comes to
managing the response to security vulnerabilities reported on open
source embedded components. We will share our experiences by taking
OpenSSL Heartbleed and the Bash Bug ‘ShellShock’ as examples and walk
through the various challenges we encountered while dealing with it and
the processes we built to overcome some of those problems.

Android Wear and Google Glass introduce new ways of interacting with our
apps and receiving timely, contextual information from the world around
us. Smartphones and tablets are becoming the central point for sending
and receiving data from wearables and sensors. Building apps for a
wearable world introduces new risks as well as shifts the
responsibilities for implementing security controls to other layers.

Many of the same issues we’re familiar with from past Android
experiences are still relevant, while some issues are less impactful or
not (currently) possible within existing wearables. At the same time,
extending the app’s trust boundaries introduces new points of exposure
for developers to be aware of in order to proactively defend against
attacks. We want to highlight these areas, which developers may not be
aware of when adding a wearable component to an existing app.

In this presentation, we will explore how Android Wear and Glass work
underneath the hood. We will examine their methods of communication,
data replication, and persistence options. We will examine how they fit
into the Android development ecosystem and the new risks to privacy and
security that need to be considered. Our goal isn’t to deter developers
from building wearable apps, but to enable them to make strong security
decisions throughout development.

This session will provide thought leadership and use cases on securing
Big Data technologies through stateless tokenization. We will cover: an
overview of what native Big Data consists of, Big Data architectures,
stateless tokenization use, and finally how to implement and secure Big
Data architectures through stateless tokenization deployments.

Specific focal points include:

  - What Big Data is and how it is used
  - An overview of Big Data architectures in the enterprise
  - What stateless tokenization is and how it is used
  - Secure Big Data deployments through stateless tokenization

Effective Risk Assessment is an incredible tool available to the
Information Security professional. A defensible risk assessment ensures
that you’ll analyze the most risky aspects of your most risky
applications. It lets you develop countermeasures that have the biggest
impact. In a real world scenario a properly conducted risk assessment
can help you work in the most efficient way. This talk is about how
MathWorks uses the OCTAVE Allegro Framework to model application risks
and develop countermeasures.

Content Security Policy (CSP) has been proposed as a principled and
robust browser security mechanism against content injection attacks such
as XSS. When configured correctly, CSP renders malicious code injection
and data exfiltration exceedingly difficult for attackers. However,
despite the promise of these security benefits and being implemented in
almost all major browsers, CSP adoption is minuscule-our measurements
show that CSP is deployed in enforcement mode on only 1% of the Alexa
Top 100.

In this paper, we present the results of a long-term study to determine
challenges in CSP deployments that can prevent wide adoption. We
performed weekly crawls of the Alexa Top 1M to measure adoption of web
security headers, and find that CSP both significantly lags other
security headers, and that the policies in use are often ineffective at
actually preventing content injection. In addition, we evaluate the
feasibility of deploying CSP from the perspective of a
security-conscious website operator. We used an incremental deployment
approach through CSP's report-only mode on four websites, collecting
over 10M reports. Furthermore, we used semi-automated policy generation
through web application crawling on a set of popular websites. We found
both that automated methods do not suffice and that significant barriers
exist to producing accurate results.

Finally, based on our observations, we suggest several improvements to
CSP that could help to ease its adoption by the web community.

Software development has been transformed by practices like Continuous
Integration and Continuous Delivery, while application security has
remained trapped in expert-based waterfall mode. In this talk, Jeff will
show you how you can evolve into a “Continuous Application Security”
organization that generates assurance automatically across an entire
application security portfolio. Jeff will show you how to bootstrap the
“sensor-model-dashboard” feedback loop that makes real time,
continuous application security possible. He will demonstrate the
approach with a new \*free\* tool called ["Contrast for
Eclipse"](http://marketplace.eclipse.org/node/1876552) that brings the
power of instrumentation-based application security testing directly
into the popular IDE. Check out [“Application Security at DevOps Speed
and Portfolio Scale”](https://www.youtube.com/watch?v=4B-HgsT_J_M) for
some background.