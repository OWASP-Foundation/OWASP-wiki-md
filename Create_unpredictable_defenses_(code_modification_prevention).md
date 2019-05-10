__NOTOC__
\= Context = Mobile app developers must take into account a whole host
of new risks that relate to hosting code in an uncontrolled environment.
If you are hosting code in an untrustworthy environment, you are
susceptible to the risk that an adversary will reverse engineer and
modify your code via binary attacks
<sup>[1]([#ReferenceItem1 "wikilink")\]</sup>
<sup>[2]([#ReferenceItem2 "wikilink")\]</sup>
<sup>[3]([#ReferenceItem3 "wikilink")\]</sup>
<sup>[4]([#ReferenceItem4 "wikilink")\]</sup>.

![MainProjectIcon.png](MainProjectIcon.png "MainProjectIcon.png") This
content is part of a much bigger set of principles defined within the
[Architectural Principles That Prevent Code Modification or Reverse
Engineering](https://www.owasp.org/index.php/Architectural_Principles_That_Prevent_Code_Modification_or_Reverse_Engineering)
project.

# Description

When invoking a particular integrity control at runtime, it is critical
to assign a probability of execution to each control invocation. By
assigning probabilities of execution to a particular control instance,
you are creating integrity defenses that are unpredictable to the
adversary. Furthermore, you avoid the "break-once-run-anywhere" scenario
outlined below.

# Examples

For example, an organization implements Checksum control "A" that is
verifying the code integrity of another Checksum control "B". Checksum
control "B" is verifying the integrity of a particularly sensitive
method within the app. In order to modify this method, the attacker must
modify the method, Checksum control "B", and Checksum control "A" in
order to allow for a successful crack. If you reduce the probability of
execution of "A", "A" may not always check the integrity of "B". In
implementing this behavior, the adversary may think they have
successfully cracked the mobile app by modifying the protected method
along with Checksum control "B". Due to the reduced
probability-of-execution feature, the attacker has overlooked that "B"
will occasionally check "A". The adversary has created a crack that is
unreliable and will not work across all instances of the mobile app in
the wild.

# External References

<span id="ReferenceItem1">\[1\] Arxan Research: [State of Security in
the App Economy,
Volume 2](https://www.arxan.com/assets/1/7/State_of_Security_in_the_App_Economy_Report_Vol._2.pdf),
November 2013:

  -
    *“Adversaries have hacked 78 percent of the top 100 paid Android and
    iOS apps in 2013.”*</span>

<span id="ReferenceItem2">\[2\] HP Research: [HP Research Reveals Nine
out of 10 Mobile Applications Vulnerable to
Attack](http://www8.hp.com/us/en/hp-news/press-release.html?id=1528865#.UuwZFPZvDi5),
18 November 2013:

  -
    *"86 percent of applications tested lacked binary hardening, leaving
    applications vulnerable to information disclosure, buffer overflows
    and poor performance. To ensure security throughout the life cycle
    of the application, it is essential to build in the best security
    practices from conception."*</span>

<span id="ReferenceItem3">\[3\] North Carolina State University:
[Dissecting Android Malware: Characterization and
Evolution](http://www.csc.ncsu.edu/faculty/jiang/pubs/OAKLAND12.pdf), 7
September 2011:

  -
    *“Our results show that 86.0% of them (Android Malware) repackage
    legitimate apps to include malicious payloads; 36.7% contain
    platform-level exploits to escalate privilege; 93.0% exhibit the
    bot-like capability.”*</span>

<span id="ReferenceItem4">\[4\] InfoSecurity Magazine: [Two Thirds of
Personal Banking Apps Found Full of
Vulnerabilities](http://www.infosecurity-magazine.com/view/36376/two-thirds-of-personal-banking-apps-found-full-of-vulnerabilities/),
January 3 2014:

  -
    *“But one of his more worrying findings came from disassembling the
    apps themselves ... what he found was hardcoded development
    credentials within the code. An attacker could gain access to the
    development infrastructure of the bank and infest the application
    with malware causing a massive infection for all of the
    application’s users.”*</span>

[Category:OWASP Reverse Engineering and Code Modification Prevention
Project](Category:OWASP_Reverse_Engineering_and_Code_Modification_Prevention_Project "wikilink")
[Category:Principle](Category:Principle "wikilink")