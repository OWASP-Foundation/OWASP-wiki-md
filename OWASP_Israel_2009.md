## Location and Time

The 2009 annual OWASP Israel conference was held at the
Interdisciplinary Center Herzliya (IDC) on September 6th between in the
Chais auditorium at the Efi Arazi school of computer science. You can
find information on how to get to the IDC and a map of the campus
[here](http://portal.idc.ac.il/He/Main/about_idc/campus_tour/Pages/MapsDirections1.aspx).

All presentations are in Hebrew.

The conference was sponsored by:

[![Image:OWASP IL Sponsors IDC New.JPG](OWASP_IL_Sponsors_IDC_New.JPG
"Image:OWASP IL Sponsors IDC New.JPG")](http://www.idc.ac.il)    [<https://www.owasp.org/images/6/6c/OWASP_IL_Sponsors_IBM.jpg>](http://www-01.ibm.com/software/awdtools/appscan/)    
[<https://www.owasp.org/images/8/89/OWASP_IL_Sponsors_Imperva.png>](http://www.imperva.com)

## Contact

For further details contact Ofer Shezaf at shezaf at owasp.org.il

## Agenda

**13:30-14:00 Gathering**

**14:00-14:10 Opening words, Ofer Shezaf, OWASP Israel chapter lead**

### 14:10-14:40 Identity Theft, Computers and Behavioral Biometrics

'''Robert Moskovitch, Deutsche Telekom Laboratories at Ben-Gurion
University '''

Identity Theft is a fraud, in which someone pretends to be someone else
is order to steal money or get other benefits. To overcome the problem
of Identity Theft an additional security layer relying on the
verification of users, based on their keystroke dynamics is proposed.
Additionally we suggest to continuously verify users based on their
keystrokes and mouse dynamics. The motivation for such technology, its
challenges and potential, will be discussed.

Robert Moskovitch is a Project Manager at the Deutsche Telekom
Laboratories at Ben Gurion University.

### 14:40-15:30 The Bank Job: A hacker’s day of work - Exploiting a vulnerable web site

**Adi Sharabani , IBM**

In this presentation we will show how severe a Cross-Site Scripting
vulnerabilities are. We will build a step-by-step working exploit code
for an XSS vulnerability found in an online banking site to hijack user
sessions, transfer money and cover the traces. The money will be shared
among the audience.

The presentation does not require any prior knowledge, but it is also
aimed for technical people.

Adi is a security research group manager for IBM labs

([Download
presentation](Media:OWASP_IL_2009_The_Bank_Job.ppt‎ "wikilink"))

### 15:30-16:00 IdM: the missing security link

**Avi Douglen**

Identity management is often driven by operational requirements rather
than security requirements. The presentation will explore the security
aspects of IdM as part of authentication and authorization. Among the
issues discussed are: What security benefits can an IdM provide? What
IdM types, techniques and methods best suit security requirements? And
lastly what are the security pitfalls and disadvantages of IdM.

Avi is an independent security architect

([Download Presentation](Media:OWASP_IL_2009_IdM.ppt‎ "wikilink"))


**16:00-16:20 Break**

### 16:20 - 17:00 ReDoS (Regular Expression Denial of Service) Revisited

**Alex Roichman, Checkmarx**

The presentation will explore the Regular Expression Denial of Service
(ReDoS) attack and how it be used in order to implement new and old
attacks. ReDoS is commonly known as a “bug” in systems, but the
presentation will show how serious it is and how using this technique,
various applications can be “ReDoSed”. These include, among others, Web
Application, WAFs, IDS, AV, Web Servers, Client-side browsers (including
cellular devices), and Database.

Alex is chief security architect at Checkmarx

([Download presentation](Media:OWASP_IL_2009_ReDoS.ppt‎ "wikilink"))

### 17:00 - 17:40 SSSL: Server Side Secure Login to Phish-Protect your website

**Ronen Margulis, Bar Ilan University (Joint work with Prof. Amir
Herzberg)**

SSSL combines two highly efficient mechanisms to defend against phishing
attacks. The first mechanism is a specially crafted bookmark which
provides two-factor authentication. The second mechanism is an
interactive custom image which is presented to the user on each login,
and which the user has to click on in order to submit his credentials.
SSSL's main advantages are its enhanced security and simple deployment.
These two defense mechanisms were proven to be the most efficient
mechanisms among different defense mechanisms tested in real life
experiments. Furthermore, the two mechanisms complement each other: each
protects a different secret, creating a safer login method. SSSL may be
most useful in preventing a number of phishing attacks at high-value
sites such as banking sites and single sign-on sites such as OpenID
providers

([Download presentation](Media:OWASP_IL_2009_SSSL.ppt "wikilink"))

### 17:40 - 18:20 A New Approach to XSS Detection using JavaScript modeling

**Ofer Rotberg, IDC**

Cross-site Scripting (XSS) has emerged as one of the most prevalent
types of security vulnerabilities in web applications. Current defense
mechanisms are mainly based on detecting malicious content on
HTTP-requests using a negative security logic approach. This approach
has known limitations, derived from the difficulty to define all the
HTTP-request payload characteristics that may lead to XSS attacks. In
this work we present a positive security logic approach to detect and
prevent XSS attacks by verifying that every web-page sent back to the
user's browser contains only "legal and original" code scripts inserted
into the HTTP-response by the web application without being influenced
by malicious input. Our results show that after a short learning period
the XSS detector has zero false-positive and zero false-negative given
our prototype limitations.

([Download
Presentation](Media:OWASP_IL_2009_XSS_detection.ppt‎ "wikilink"))

[Category:Israel](Category:Israel "wikilink")