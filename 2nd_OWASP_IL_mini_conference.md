The 2nd OWASP IL mini conference was held at the Interdisciplinary
Center (IDC) Herzliya on May 21th 2007. The event was a huge success
with over a 150 people attending and 8 companies and organizations
sponsoring the event. The feedback for the carefully selected
presentations presentations, all of them relevant, informative and most
importantly none commercial was great.

The meeting was sponsored by Breach Security, Checkpoint, Hacktics,
Microsoft, Zend, 2Bsecure, F5 Networks and the Efi Arazi school of
Computer Science at the Interdisciplinary Center (IDC) Herzliya.

<center>

![Image:Breach_logo.gif](Breach_logo.gif
"Image:Breach_logo.gif")    ![OWASP_IL_Sponsor_Hacktics.jpg](OWASP_IL_Sponsor_Hacktics.jpg
"OWASP_IL_Sponsor_Hacktics.jpg")![OWASP_IL_Sponsor_Zend.jpg](OWASP_IL_Sponsor_Zend.jpg
"OWASP_IL_Sponsor_Zend.jpg")    ![Image:OWASP_IL_Sponsor_2B.jpg](OWASP_IL_Sponsor_2B.jpg
"Image:OWASP_IL_Sponsor_2B.jpg")    ![Image:OWASP_IL_Sponsor_F5.jpg](OWASP_IL_Sponsor_F5.jpg
"Image:OWASP_IL_Sponsor_F5.jpg")

</center>

<center>

![Image:OWASP_IL_Sponsor_Checkpoint.gif](OWASP_IL_Sponsor_Checkpoint.gif
"Image:OWASP_IL_Sponsor_Checkpoint.gif")    ![Image:OWASP_IL_Sponsor_Microsoft.gif](OWASP_IL_Sponsor_Microsoft.gif
"Image:OWASP_IL_Sponsor_Microsoft.gif")    ![Image:OWASP_IL_Sponsor_IDC.jpg](OWASP_IL_Sponsor_IDC.jpg
"Image:OWASP_IL_Sponsor_IDC.jpg")

</center>

The agenda of the meeting was:

<big>**[Updates from OWASP Europe,
Milan](media:OWASP_IL_7_OWASP_Introduction.pdf‎ "wikilink")**</big>
**Ofer Shezaf, OWASP IL chapter leader, CTO, [Breach
Security](http://www.breach.com/)**
Since the conference is just a few days after OWASP Europe 2007 in
Milan, and since most of you would not have a chance to be there, I will
try to convey the content and spirit of this unique conference to you.

In addition you will hear Yair Amit, who will repeat the presentation he
is going to make in OWASP Europe, and Erez Metula will build his lecture
on OWASP chief evangelist's presentation about .NET. For my presentation
in OWASP Europe, you had to come to the previous OWASP IL Mini
Conference.

<small>[download
presentation](media:OWASP_IL_7_OWASP_Introduction.pdf "wikilink")</small>

<big>**[Pen-Testing at Microsoft: FuzzGuru fuzzing
framework](media:OWASP_IL_7_FuzzGuru.pdf "wikilink")**</big>
**John Neystadt, Lead Program Manager, Microsoft Forefront Edge,
Microsoft**
Fuzzing is the main systematic methodology used these days by hackers to
find vulnerabilities in web and other applications. Fuzzing can find
buffer overrun, denial-of-service and information disclosure
vulnerabilities. It should be done for C++, C\#/Java, ASP/JP code.

FuzzGuru is a generic network fuzzing development framework developed in
Microsoft Israel Development Center and is formally recommended best
practice for all products developed in Microsoft.

In this talk John will present some fuzzing testing theory, demonstrate
the tools and discuss Microsoft fuzzing practices.

<small>[download
presentation](media:OWASP_IL_7_FuzzGuru.pdf "wikilink")</small>

<big>**[Unregister Attacks in
SIP](media:OWASP_IL_7_UnregisterAttackInSip.pdf "wikilink")**</big>
**Ronit Halachmi-Bekel, Efi Arazi school of Computer Science at
Interdisciplinary Center (IDC) Herzliya**
The presentation discusses a research work done at the Efi Arazi school
of Computer Science at Interdisciplinary Center (IDC) Herzliya about the
"unregister attack", a new kind of a denial of service attack on SIP
servers. In this attack, the attacker sends a spoofed "unregister"
message to a SIP server and cancels the registration of the victim at
that server. This prevents the victim user from receiving any calls.

The research also offers a solution: the SIP One-Way Hash Function
Algorithm (SOHA), motivated by the one-time password mechanism. SOHA
prevents the unregister attack in all situations. The algorithm is easy
to deploy since it requires only a minor modification and is fully
backwards compatible and requires no additional configuration from the
user or the server.

The paper is a joint work with Dr. Anat Bremler-Barr and Jussi
Kangasharju. The paper was presented at the 14th IEEE International
Conference on Network Protocols (ICNP).

<small>[download
presentation](media:OWASP_IL_7_UnregisterAttackInSip.pdf "wikilink")</small>

<big>**[Application Denial of Service; is it Really That
Easy?](media:OWASP_IL_7_Application_DOS.pdf "wikilink")**</big>
**Shay Chen, Hacktics**
Denial of service attacks, which are quite a nuisance on the network
layer, are a nightmare when done on the application layer, but are
equally underrated.

On our last conference, Dr. Anat Bremler-Bar discussed some of the
theoretical aspects of application layer denial of service attacks. Shay
Chen will expand and explore the practicalities of application layer
denial of service. He will show real world techniques, real life stories
and personal experiences conducting DOS attacks during penetration
testing on major Israeli sites.

<small>[download
presentation](media:OWASP_IL_7_Application_DOS.pdf "wikilink")</small>

<big>**[Behavioral Analysis for Generating A Positive Security Model For
Applications](media:OWASP_IL_7_WAF_Positive_Security.pdf "wikilink")**</big>
**Ofer Shezaf, OWASP IL chapter leader, CTO, Breach Security**
In the last OWASP IL conference, as well as in OWASP Europe in Milan, I
explored the potential of a negative security model for securing
applications. While a negative security model can provide some level of
security, most agree that a positive security model is preferable for
protection application.

However, building a rule set to provide positive security is a difficult
and never ending project. Modern tools employ behavioral analysis to
build automatically those rules. The presentation will discuss the
algorithms and methods used to build automatically an application layer
positive security rule set as well as the problems and limitation of
such as approach.

<small>[download
presntation](media:OWASP_IL_7_WAF_Positive_Security.pdf "wikilink")</small>

<big>**[Overtaking Google Desktop - Leveraging XSS to Raise
Havoc](media:OWASP_IL_7_Overtaking_Google_Desktop.pdf "wikilink")**</big>
**Yair Amit, Senior Security Researcher, Watchfire**
Yair will present a ground breaking research paper by Watchfire
application security team. The paper describes an innovative attack
methodology against Google Desktop which enables a malicious individual
to achieve a remote, persistent access to sensitive data, and
potentially a full system control.

This represents a significant real world example of a new generation of
computer attacks which take advantage of Web application vulnerabilities
utilizing the increasing power of the Web browser. Their purpose is to
remotely access private information.

This presentation was presented by Yair the week before at OWASP Europe
in Milan.

<small>[download
presentation](media:OWASP_IL_7_Overtaking_Google_Desktop.pdf‎ "wikilink")</small>

<big>**[Application Security is Not Just About
Development](media:OWASP_IL_7_AppSec_and_Beyond.pdf‎ "wikilink")**</big>
**David Lewis, CISM, CISA, CISSP, Rosenblum Holtzman**
What many developers forget about is that the application even though it
is a very important part of securing the "Gold", data, there are other
risks that require their attention. These risks require their
understanding and preventative measures need to be implemented, managed
and validated to limit the exposure to themselves and their
organizations. E.g. Developers do not see the need for securing their
code.

One of the things I will provide you during my presentation is why you
should secure your code. It is one of the ways you will keep your job.

<small>[download
presentation](media:OWASP_IL_7_AppSec_and_Beyond.pdf‎ "wikilink")</small>

<big>**[.NET reverse
engineering](media:OWASP_IL_7_DOT_NET_Reverse_Engineering.pdf‎ "wikilink")**</big>
**Erez Metula, Application Security Department Manager, 2Bsecure**
The presentation will introduce MSIL (Microsoft Intermediate Language)
and debugging MSIL. Based on this foundation the presentation will
explore and demonstrate tools and techniques for changing the behavior
of .NET assemblies and the CLR using reversing engineering techniques.

<small>[download
presentation](media:OWASP_IL_7_DOT_NET_Reverse_Engineering.pdf‎ "wikilink")</small>

[Category:Israel](Category:Israel "wikilink")