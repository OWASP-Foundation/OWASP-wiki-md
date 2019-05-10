__FORCETOC__ We would like to thank our speakers for donating their
time and effort to help make this conference successful.

Data center security teams are being challenged to rapidly deploy and
secure new applications while controlling costs and improving
efficiency. In this presentation, we will provide an inside look at some
of the problems with traditional access management implementations and
how enterprises can sucessfully overcome these challenges by integrating
web application firewall technologies with Identity and Access
Management. Learn about best practices, specific use cases and how this
new integration translates into operational simplicity for the
enterprise.

Attendees will be able to play Capture the Flag during the conference.
No sign-up necessary. Information about the game will be available at
the registration desk. If you are interested in playing, please bring
your own laptop. It is recommended that your laptop have either Chrome
or Firefox web browsers installed. Please note that you will not be
attacking other attendees; the CTF game will be on a remote server. You
will use a NERD wireless connection to the internet, then to the server
to be attacked. There are 10 flags on the server.

The results will be discussed at the end of the conference during the
panel session time. There are no physical or digital prizes, but
bragging rights and peer recognition is of inestimable value.

Fuzzing is easy, but getting useful information from fuzzing isn’t.
‘Spray and pray’ might get some results, but a set of well-designed
tests will get much better results faster. Unfortunately, the job
doesn’t end there. Fuzzing doesn’t find vulnerabilities; fuzzing finds
unexpected behavior. Interpreting that unexpected behavior relies on
understanding the application you’re fuzzing and the tests you’ve
designed. This presentation will discuss techniques for creating tests
targeted towards uncovering specific behavior, including authorization
bypasses, directory traversals, and buffer overflows.

Increasingly "real-time" web applications require new hacks on-top of
HTTP that requires server support (e.g. WebSockets, SPDY); this
presentation will demonstrate how this new functionality permits
attackers to more effectively, and more stealthily establish
bidirectional communication with compromised hosts; thus bypassing any
outbound connection restrictions. We will cover the theory, historical
techniques, defensive methodologies and new techniques throughout the
presentation.

At the heart of these techniques is the ability to establish arbitrary
bidirectional TCP connections given vulnerabilities in web applications,
even in the presence of restrictive DMZ firewalls; this is a
"well-known" attacker methodology. Attackers have for many years known
to abuse the trusted relationship between web servers (or any exposed
service\!) and perimeter firewalls (inbound ports). Generally these
tricks come at a price and are something that can be detected by a
vigilant security team.

We will discuss how attackers can easily bypass outbound firewall rules,
the history of these methodologies, and common defensive techniques
combating this threat. Furthermore, new techniques will be described
that utilize "real-time" protocols; specifically, how can these new
techniques create back-channels and simultaneously hide from those
vigilant security teams, increase the throughput and reliability of an
attacker’s "VPN", and arbitrarily direct traffic from the internet into
a DMZ environment.

Audience: This class is open to all

This 50-minute class will give students a basic understanding of what is
Metasploit, some of the features it allows and examples of how it can be
used. This includes Meterpreter basics, the MSF command line interface,
MSF console, using exploits and payloads. One example exploit that may
be shown is the MS08-067 vulnerability and maybe another one per the
class's choosing, time-permitting. This class is in no way the full
class and is designed to get you using Metasploit in the class's
timeframe.

Students are expected to already have Metasploit installed on their
laptops (Download at <http://www.metasploit.com/download/>) with VMWare
Workstation (trial version or the full version) with Windows XP (trial
version or full that is not patched) OS installed as well. There will be
no technical support because of the limited class time and we will be on
an internal class wired network. All notes will be made available.

Hardware and Software Requirements:
A. The recommended is at least 50GB+ of hardrive space
B. 4GB or more of RAM
C. The more horsepower (CPU) you have, the better for virtual machines
D. Metasploit installed
E. VMWare Workstation
F. Windows XP (unpatched) virtual machine

Audience: Students that have taken the fundamental elements class or
students that have an understanding of Metasploit or have already used
it

This 1-hour course will continue where the fundamental elements class
left off. This will be a quick overview of some of the mostly used
features of Metasploit including information gathering and vulnerability
scanning. We may have time to go over some exploit development,
defeating antivirus and/or meterpreter scripting. This class will not
cover MSF post exploitation.

Students are expected to already have Metasploit installed on their
laptops (Download at <http://www.metasploit.com/download/>) with VMWare
Workstation (trial version or the full version) with Windows XP (trial
version or full that is not patched) OS installed as well. There will be
no technical support because of the limited class time and we will be on
an internal class wired network. All notes will be made available.

Hardware and Software Requirements:
A. The recommended is at least 50GB+ of hardrive space
B. 4GB or more of RAM
C. The more horsepower (CPU) you have, the better for virtual machines
D. Metasploit installed
E. VMWare Workstation
F. Windows XP (unpatched) virtual machine

The number one threat to mobile devices and applications is loss or
theft of the device. The old security mantra of, "if an attacker has
physical access, it is game over" is more relevant to mobile devices
than virtually any other technology security practitioners have been
tasked with securing. For this reason it is imperative for organizations
to clearly understand their risk when deploying or supporting these
devices.

Learning Objectives

Discover and explore physical locations on Apple iOS devices where
sensitive information is commonly stored. Discover and explore physical
locations on Google Android devices where sensitive information is
commonly stored. Learn to mitigate risks through effective use of Mobile
Device Management ("MDM") technology, device configuration, policy, and
secure development.

Why choose this talk?

According to my research, I coined the term "offensive mobile
forensics". By definition, this activity is the preemptive analysis of
mobile devices and applications to quantitatively measure your
organization's level of risk caused by the proliferation and use of
today's mobile technology. Anyone that has performed research in this
area knows mobile devices are potential trojan horses for virtually
every organization. This talk arms attendees with the information and
tools required to conductoffensive mobile forensics in their own
environments.

People have been talking about secure Software Development Life Cycles
(SDLCs) for years, but there has been little traction in scaling secure
SDLC activities outside of a few very security-conscious companies. We
assert that a key reason for this is that to scale, these processes
require automation. Static analysis, web application firewalls, and
dynamic testing are the primary methods many organizations use to secure
their applications because these tools can scale effectively. However,
there is widespread acknowledgement that relying solely on verification
activities for security is neither cost effective nor holistic. In fact,
a 2012 study by SD Elements (to be published) indicates that on average
42% of security requirements are NOT covered by automated static and/or
dynamic testing tools. To efficiently scale secure SDLC, we emphasize on
process automation via criteria-based requirement generation, contextual
on-the-job training for developers, and smart checklists. Our data
indicates a significant savings for the organization on remediation
costs. This talk discusses the process automation in detail and
demonstrates how it effectively scales to large development teams.

In the event that your password table gets into the wild, how long will
it take an attacker to expose the plaintext passwords? The recent set of
well publicized disclosures of user passwords raised the question of
whether current best practices adequately protect passwords from brute
force attacks by many of our clients. In addition, with the advent of
GPU-based (or FPGA) computing where GPUs are used for general purpose
computing, are the current defenses and practices built for brute-force
attacks sufficient? Cigital reviewed the current hardware innovations,
analyzed the current methods for protecting passwords at rest and
whether the methods sufficiently protected the passwords from being
revealed using today’s hardware.

This talk discusses the pros and cons of the current practices such as
salted-hashes, adaptive hashes and proposes an alternative solution for
strengthening these existing practices. The talk will discuss the
cryptographic properties of the current practices, but does not require
a PhD in mathematics to understand the details.

Securing mobile applications is a multi-dimensional problem space,
carrying with it elements of desktop security, web application security,
and network security. Coupled with a large attack space is the
additional security issue of technological infancy. Since the mobile
application space is still an emerging technology, the threat space is
still being defined. This continuously growing, rapidly changing, and
large threat space represents a significant risk to the enterprise.
Developers can minimize this threat by introducing a number of secure
development practices into the SDLC.

Because the technologies behind mobile application development are
changing rapidly, secure development tools are not yet comprehensive.
However, good processes that combine these tools with design,
development, and testing methodologies can bridge the security gap as
the tools grow and become more effective. An effective security program
will engage available tools across the SDLC. At a minimum, secure mobile
application development should include threat modeling, static
analysis/whitebox testing, and blackbox testing. This testing should
focus on attacks against the network component, the server component,
and the client component.

The presentation will focus on implementing secure development
methodologies with an emphasis on:

1.  Threat Modeling
    1.  Threat modeling methodologies for Mobile Application development
    2.  Threat modeling 3rd party applications
    3.  Protecting PII on the device
2.  Whitebox Testing
    1.  Static analysis availability, strengths, and limitations
    2.  Whitebox testing tools
    3.  Whitebox client side testing
    4.  PII Storage issues
    5.  Client side attack vectors
3.  Blackbox Testing
    1.  Blackbox testing tools
    2.  Blackbox proxy issues
    3.  Blackbox server issues

Identifying application-level vulnerabilities via scanning, penetration
tests and code reviews is only the first step in actually addressing the
underlying risk. Managing vulnerabilities for applications is more
challenging than dealing with traditional infrastructure-level
vulnerabilities because they typically require the coordination of
security teams with application development teams. The process also
means that security managers need to get time from developers during
already-cramped development and release schedules. In addition, fixes
require changes to custom application code and application-specific
business logic rather than the patches and configuration changes that
are often sufficient to address infrastructure-level vulnerabilities.
This presentation will illustrate the communication difficulties between
security and development teams, and how this usually results in
unactionable reports and fewer vulnerabilities remediated. In addition,
the presentation will walk through an example workflow of addressing
application vulnerabilities as software defects. This will be based on
freely-available tools and show specific examples of how vulnerabilities
can be grouped together, false positives can be culled out, and
vulnerabilities transitioned to software defects, as well as how
security managers can monitor and verify progress.

We cannot “firewall” or “patch” our way to secure websites. In the past,
security professionals thought firewalls, Secure Sockets Layer (SSL),
patching, and privacy policies were enough. Today, however, these
methods are outdated and ineffective, as attacks on prominent,
well-protected websites are occurring every day. Organizations around
the world rely on highly accurate, scalable and continuous Web security
services to maintain the safety of their websites in today’s hostile
online environment. Website developers must also learn to code in a
secure fashion to have any chance of providing organizations with proper
defenses in the current threat-scape. The session will provide specific
tips and guidelines to make website code both low risk and less
vulnerable.

Despite over a decade of taking information security "seriously", we
have yet to eradicate even one of the OWASP Top 10. The way we approach
application security today often wastes a lot of time and money and
doesn't yield very good results.

This talk shines a light on some of the things we do that we think are
helping, but actually contribute more to the problem than the solution.
Along the way, it covers a number of common practices that are getting
us nowhere fast and offers suggestions for improvement for each one.