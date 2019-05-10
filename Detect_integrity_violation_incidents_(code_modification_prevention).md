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

Whether a hacker is trying to pirate your app, steal your data, or alter
the behavior of a critical piece of infrastructure software as part of a
larger crime – inspecting and/or modifying an application can play an
essential role. As part of a layered protection strategy, companies
should have mechanisms in place that add anti-decompile, anti-debug,
anti-tamper and anti-root controls directly into an application to
protect, detect, and respond to attacks on the application's integrity.
Consider how reverse engineering and debugging application attacks can
cross data, operational, and IP risk boundaries:

<table style="width:100%">

<tr>

<th>

Attack

</th>

<th>

Resulting Risk

</th>

</tr>

<tr>

<td>

Circumventing encryption used during data transmission or storage
exposes otherwise secured data

</td>

<td>

Unauthorized data access leads to data loss, loss of revenue, privacy
breaches, regulatory non-compliance, and trade secret theft

</td>

</tr>

<tr>

<td>

Insert and modify data within your application

</td>

<td>

Altering application to circumvent controls and voiding authorization
and access controls to gain access to restricted information or gain
additional access for free

</td>

</tr>

<tr>

<td>

View critical function code, the values of dynamic keys and how
sensitive information is saved to your file systems and databases

</td>

<td>

Loss of highly sensitive data such as: digital keys, certificates,
credentials, and proprietary algorithms

</td>

</tr>

<tr>

<td>

Modify and release a copycat or malware infected version of your
application

</td>

<td>

A redistributed version of your application performs illicit actions
that cause reputational damage and exposure

</td>

</tr>

</table>



![MainProjectIcon.png](MainProjectIcon.png "MainProjectIcon.png") This
content is part of a much bigger set of principles. See the
[Architectural Principles That Prevent Code Modification or Reverse
Engineering](https://www.owasp.org/index.php/Architectural_Principles_That_Prevent_Code_Modification_or_Reverse_Engineering)
project for more information.

# Description

Detecting integrity violation is important because otherwise the
attacker has unlimited time to perfect an integrity attack. An integrity
violation is defined as an insertion of code into the application. As
part of a layered protection strategy, companies should have mechanisms
in place that add vulnerability masking, anti-debug and anti-tamper
functionality directly into an application to protect, detect, and
respond to attacks on the application's integrity.

# Examples

For example, a Checksum control is responsible for detecting code
changes between compile-time and runtime of the application.
As another example, an anti-debug control is important not only because
it is a hacker's tool of choice, but because it can be used to insert
and modify data within your
application.<sup>[5]([#ReferenceItem5 "wikilink")\]</sup>

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

<span id="ReferenceItem5">\[5\] PreEmptive and Deloitte Review:
[Application Integrity
Protection](https://www.preemptive.com/solutions/application-integrity-protection),

  -
    *“Whether a hacker is trying to pirate your app, steal your data, or
    alter the behavior of a critical piece of infrastructure software as
    part of a larger crime – inspecting and/or modifying an application
    can play an essential role...”*</span>

[Category:OWASP Reverse Engineering and Code Modification Prevention
Project](Category:OWASP_Reverse_Engineering_and_Code_Modification_Prevention_Project "wikilink")
[Category:Principle](Category:Principle "wikilink")