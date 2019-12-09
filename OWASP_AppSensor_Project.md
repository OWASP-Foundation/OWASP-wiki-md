# Main

<div style="width:100%;height:120px;border:0,margin:0;overflow: hidden;">

![Appsensor-header.jpg](Appsensor-header.jpg "Appsensor-header.jpg")

</div>

<div style="width:100%;height:90px;border:0,margin:0;overflow: hidden;">

![_flagship_big.jpg](_flagship_big.jpg "_flagship_big.jpg")

</div>

<table>
<tbody>
<tr class="odd">
<td><h2 id="owasp_appsensor">OWASP AppSensor</h2>
<p>The AppSensor project defines a conceptual framework and methodology that offers prescriptive guidance to implement <a href="https://www.owasp.org/index.php/ApplicationLayerIntrustionDetection">intrusion detection and automated response</a> into applications.</p>
<p>The project offers a comprehensive guide and a reference implementation. These resources can be used by architects, developers, security analyst and system administrators to plan, implement and monitor an AppSensor system.</p>
<h2 id="introduction">Introduction</h2>
<p>If you walk into a bank and try opening random doors, you will be identified, led out of the building and possibly arrested. However, if you log into an online banking application and start looking for vulnerabilities no one will say anything. This needs to change! As critical applications continue to become more accessible and inter-connected, it is paramount that critical information is sufficiently protected. We must also realize that our defenses may not be perfect. Given enough time, attackers can identify security flaws in the design or implementation of an application.</p>
<p>In addition to implementing layers of defense within an application, we must identify malicious individuals before they are able to identify any gaps in our defenses. The best place to identify malicious activity against the application is within the application itself. Network based intrusion detection systems are not appropriate to handle the custom and intricate workings of an enterprise application and are ill-suited to detect attacks focusing on application logic such as authentication, access control, etc. This project delivers a framework which can be used to build a robust system of attack detection, analysis, and response within an enterprise application.</p>
<h2 id="detect_and_respond_to_attacks_from_within_the_application">Detect and Respond to Attacks from Within the Application</h2>
<h3 id="detection">Detection</h3>
<p>AppSensor defines over 50 different detection points which can be used to identify a malicious attacker.</p>
<h3 id="response">Response</h3>
<p>AppSensor provides guidance on how to respond once a malicious attacker has been identified. Possible actions include: logging out the user, locking the account or notifying an administrator. More than a dozen response actions are described.</p>
<h3 id="defending_the_application">Defending the Application</h3>
<p>An attacker often requires numerous probes and attack attempts in order to locate an exploitable vulnerability within the application. By using AppSensor it is possible to identify and eliminate the threat of an attacker before they are able to successfully identify an exploitable flaw.</p>
<h2 id="citations">Citations</h2>
<ul>
<li><a href="http://www.crosstalkonline.org/">CrossTalk</a>, The Journal of Defense Software Engineering
<ul>
<li>Creating Attack-Aware Software Applications with Real Time Defenses, Vol. 24, No. 5, Sep/Oct 2011</li>
</ul></li>
</ul>
<ul>
<li>Norwegian University of Science and Technology in Tronheim
<ul>
<li><a href="https://brage.bibsys.no/xmlui/handle/11250/252956">AppSensor: Attack-Aware Applications Compared Against a Web Application Firewall and an Intrusion Detection System</a>, Thomassen P, 2012</li>
</ul></li>
</ul>
<ul>
<li>US Department of Homeland Security
<ul>
<li><a href="https://buildsecurityin.us-cert.gov/swa/topics/resilient-software/">Resilient Software</a></li>
<li><a href="https://buildsecurityin.us-cert.gov/swa/resources">Software Assurance Resources</a></li>
</ul></li>
</ul>
<h2 id="licensing">Licensing</h2>
<p>OWASP AppSensor is free to use.</p>
<h3 id="guide">Guide</h3>
<p>The guide is licensed under the <a href="http://creativecommons.org/licenses/by-sa/3.0/">Creative Commons Attribution-ShareAlike 3.0 license</a>, so you can copy, distribute and transmit the work, and you can adapt it, and use it commercially, but all provided that you attribute the work and if you alter, transform, or build upon this work, you may distribute the resulting work only under the same or similar license to this one.</p>
<h3 id="reference_implementation">Reference Implementation</h3>
<p>The reference implementation is licensed under the <a href="http://opensource.org/licenses/MIT">MIT License</a>, which is a permissive (commercial-friendly) license only requiring you to include a copy of the license upon distribution or copying.</p>
<p>© OWASP Foundation</p></td>
<td><h2 id="what_is_appsensor">What is AppSensor?</h2>
<p>Detect and respond to attacks from within the application. This project includes both a well documented idea (the Guide) and a reference implementation (the Code).</p>
<h2 id="intro_for_developers">Intro for Developers</h2>
<figure>
<img src="Appsensor-developer-small.jpg" title="Appsensor-developer-small.jpg" alt="Appsensor-developer-small.jpg" /><figcaption>Appsensor-developer-small.jpg</figcaption>
</figure>
<p><a href="https://www.owasp.org/index.php/File:Appsensor_intro_for_developers.pdf">Two-sided US Letter or A4</a></p>
<h2 id="appsensor_website">AppSensor Website</h2>
<figure>
<img src="Appsensor-website-small.jpg" title="Appsensor-website-small.jpg" alt="Appsensor-website-small.jpg" /><figcaption>Appsensor-website-small.jpg</figcaption>
</figure>
<p>See the <a href="http://appsensor.org/">AppSensor website</a> for an introduction and quick start instructions.</p>
<h2 id="overview">Overview</h2>
<figure>
<img src="Appsensor-cisobriefing-small.jpg" title="Appsensor-cisobriefing-small.jpg" alt="Appsensor-cisobriefing-small.jpg" /><figcaption>Appsensor-cisobriefing-small.jpg</figcaption>
</figure>
<p><a href="https://www.owasp.org/index.php/File:Appsensor-ciso-briefing.pdf">12-page US Letter booklet</a></p>
<h2 id="project_founder">Project Founder</h2>
<ul>
<li><a href="https://www.owasp.org/index.php/User:MichaelCoates">Michael Coates</a> <a href="mailto:michael.coates@owasp.org">@</a></li>
</ul>
<h2 id="project_leaders">Project Leaders</h2>
<ul>
<li><a href="https://www.owasp.org/index.php/User:John_Melton">John Melton</a> <a href="mailto:john.melton@owasp.org">@</a></li>
</ul>
<h2 id="related_projects">Related Projects</h2>
<ul>
<li><a href=":Category:OWASP_ModSecurity_Core_Rule_Set_Project" title="wikilink">OWASP ModSecurity Core Rule Set</a></li>
</ul></td>
<td><h2 id="quick_download">Quick Download</h2>
<ul>
<li>OWASP AppSensor Guide v2 EN
<ul>
<li><a href="https://www.owasp.org/index.php/File:Owasp-appsensor-guide-v2.pdf">PDF</a></li>
<li><a href="https://www.owasp.org/index.php/File:Owasp-appensor-guide-v2.doc">DOC</a></li>
<li><a href="http://www.lulu.com/shop/owasp-foundation/appsensor-guide/paperback/product-21608107.html">Hard copy</a></li>
</ul></li>
<li>OWASP AppSensor Reference Implementation
<ul>
<li><a href="https://github.com/jtmelton/appsensor">v2 Code</a></li>
</ul></li>
</ul>
<h2 id="news_and_events">News and Events</h2>
<ul>
<li>[25 Sep 2015] <a href="http://appsecusa2015.sched.org/event/09495faf5cced352cb4a2acc16ce9158#.VaOSoHhfk2w">Presentation</a> at AppSec USA 2015</li>
<li>[27 Jul 2015] <a href="https://www.owasp.org/index.php/File:Owasp-appensor-guide-v2.doc">AppSensor Guide v2.0.2</a> published</li>
<li>[09 Jun 2015] AppSensor Code v2.1.0 <a href="https://github.com/jtmelton/appsensor/releases/tag/v2.1.0">released</a></li>
<li>[20 May 2015] Working session at <a href="http://2015.appsec.eu/project-summit/">OWASP Project Summit</a> - Code</li>
<li>[19 May 2015] Working session at <a href="http://2015.appsec.eu/project-summit/">OWASP Project Summit</a> - Documentation</li>
<li>[09 Apr 2015] <a href="https://www.owasp.org/index.php/File:Appsensor-ciso-briefing.pdf">CISO Briefing</a> booklet published</li>
<li>[22 Feb 2015] Proposal for <a href="https://www.owasp.org/index.php/GSoC2015_Ideas#OWASP_AppSensor">Google Summer of Code 2015</a></li>
<li>[13 Feb 2015] <a href="https://www.owasp.org/index.php/File:Appsensor_intro_for_developers.pdf">Introduction for Developers</a> flyer published</li>
<li>[13 Feb 2015] AppSensor project awarded OWASP flagship status</li>
<li>[28 Jan 2015] AppSensor Code v2.0.0 final <a href="https://github.com/jtmelton/appsensor/releases/tag/v2.0.0">released</a></li>
</ul>
<h2 id="code_repository">Code Repository</h2>
<ul>
<li>AppSensor v2 <a href="https://github.com/jtmelton/appsensor">https://github.com/jtmelton/appsensor</a> (Current)</li>
<li>Note: LEGACY AppSensor v1 <a href="https://code.google.com/p/appsensor/">https://code.google.com/p/appsensor/</a></li>
</ul>
<h2 id="in_print">In Print</h2>
<figure>
<img src="AppSensor2_small.jpg" title="AppSensor2_small.jpg" alt="AppSensor2_small.jpg" /><figcaption>AppSensor2_small.jpg</figcaption>
</figure>
<p>The <a href="http://www.lulu.com/shop/owasp-foundation/appsensor-guide/paperback/product-22290600.html">AppSensor Guide</a> and <a href="http://www.lulu.com/shop/owasp-foundation/appsensor-ciso-briefing/paperback/product-22121723.html">CISO Briefing</a> can be purchased at cost as print on demand books.</p></td>
</tr>
</tbody>
</table>

# Acknowledgements

## Volunteers

All OWASP projects rely on the voluntary efforts of people in the
software development and information security sectors. They have
contributed their time and energy to make suggestions, provide feedback,
write, review and edit documentation, give encouragement, make
introductions, produce demonstration code, promote the concept, and
provide OWASP support. They participated via the project’s mailing
lists, by developing code, by updating the wiki, by undertaking research
studies, and through contributions during the AppSensor working session
at the OWASP Summit 2011 in Portugal and the AppSensor Summit at AppSec
USA 2011. Without all their efforts, the project would not have
progressed to this point, and this guide would not have been completed.

  - Josh Amishav-Zlatin
  - Ryan Barnett
  - Simon Bennetts
  - Joe Bernik
  - Rex Booth
  - Luke Briner
  - Rauf Butt
  - Juan C Calderon
  - Fabio Cerullo
  - Marc Chisinevski
  - Robert Chojnacki
  - Michael Coates
  - Dinis Cruz
  - Sumanth Damaria
  - August Detlefsen
  - Ryan Dewhurst
  - Sean Fay

<!-- end list -->

  - Timo Goosen
  - Dennis Groves
  - Randy Janida
  - Chetan Karande
  - Eoin Keary
  - Alex Lauerman
  - Junior Lazuardi
  - Benjamin-Hugo LeBlanc
  - Jason Li
  - Manuel López Arredondo
  - Bob Maier
  - Jim Manico
  - Sherif Mansour Farag
  - John Melton
  - Mark Miller
  - Rich Mogull
  - Craig Munson

<!-- end list -->

  - Louis Nadeau
  - Giri Nambari
  - Erlend Oftedal
  - Jay Reynolds
  - Chris Schmidt
  - Sahil Shah
  - Eric Sheridan
  - John Steven
  - Raphael Taban
  - Alex Thissen
  - Don Thomas
  - Christopher Tidball
  - Stephen de Vries
  - Kevin W Wall
  - Colin Watson
  - Mehmet Yilmaz

## OWASP Summer of Code 2008

The AppSensor Project was initially supported by the [OWASP Summer of
Code 2008](https://www.owasp.org/index.php/OWASP_Summer_of_Code_2008),
leading to the publication of the book AppSensor v1.1.

## Google Summer of Code 2012

Additional development work on [SOAP web
services](http://www.google-melange.com/gsoc/project/google/gsoc2012/edil/60002)
was kindly supported by the [Google Summer of
Code 2012](http://www.google-melange.com/gsoc/program/home/google/gsoc2012).

## OWASP Code Sprint 2015

Development work was also supported by the [OWASP Summer Code
Sprint 2015](https://www.owasp.org/index.php/Summer_Code_Sprint2015).

## Other Acknowledgements

The project has also benefitted greatly from the generous contribution
of time and effort by many volunteers in the OWASP community including
those listed above, and contributors to the OWASP ESAPI project, members
of the former OWASP Global Projects Committee, the OWASP Board, OWASP
staff and support from the OWASP Project Reboot initiative. The v2 code
and documentation were conceived during the AppSensor Summit held during
AppSec USA 2011 in Minneapolis.

# Road Map and Getting Involved

Please join the project's mailing lists to keep up-to-date with what's
going on, and to contribute your ideas, feedback, and experience:

  - [General
    project](https://lists.owasp.org/mailman/listinfo/owasp-appsensor-project)
  - [Code
    development](https://lists.owasp.org/mailman/listinfo/owasp-appsensor-dev)

## Current activities

### Non code

  - Update AppSensor Guide to keep in step with code changes and
    improvements to ideas ([see discussion and editable list of
    changes](http://lists.owasp.org/pipermail/owasp-appsensor-project/2015-February/000855.html))
  - Create demo
  - Develop training materials

### v2 Code

The current code being worked on is located on
[GitHub](https://github.com/jtmelton/appsensor)

The code has been fully rewritten. v2.0.0 final was released in late
January 2015. v2.1.0 final was released in June 2015. v2.2.0 final was
released in September 2015

The main reason for the rewrite was to allow a client-server style model
as opposed to requiring AppSensor be fully embedded in the application.
You can now have a central server collecting events from multiple
applications and performing analysis. These front-end applications can
be in any language as long as they speak rest/soap. There's been a host
of other changes, but this was the primary one. A number of starter
ideas for coding, user interface and documentation have been outlined
via the mailing list at [17th
March 2014](http://lists.owasp.org/pipermail/owasp-appsensor-project/2014-March/000682.html).

if you want to work on ANYTHING, please let jtmelton\[@\]gmail.com know.

## Code Roadmap

### Q4 2015 (2.0)

  - ~~Jan - v 2.0.0 final release~~ -\> DONE

### Q4 2014 (2.0)

  - ~~Oct - v 2.0.0 release candidate~~ -\> DONE
  - ~~Jan 2015 (delay due to bug) - v 2.0.0 final~~ -\> DONE
  - ~~Additional unit tests~~ -\> DONE
  - ~~Move appsensor.org site over from static html to python~~ -\> NOT
    NECESSARY
  - ~~Finish up user documentation at appsensor.org~~ -\> DONE

### June 2015 (2.1)

  - ~~Add at least 1 attack emitter for DEVOPS visualization (JMX -\>
    SNMP, syslog, SNMP, .. something)~~ ([github
    issue](https://github.com/jtmelton/appsensor/issues/19)) -\> DONE
  - ~~Sample application / demo~~ ([github
    issue](https://github.com/jtmelton/appsensor/issues/9)) -\> DONE
  - ~~Finish up developer documentation on github and appsensor.org~~
    ([github issue](https://github.com/jtmelton/appsensor/issues/12))
    -\> DONE
  - ~~Preparation for GSOC 2015 submission~~ -\> DONE - see
    [GSoC2015_Ideas](GSoC2015_Ideas "wikilink") - Update - OWASP not
    selected

### September 2015 (2.2)

  - ~~First version of administration UI for appsensor (monitoring UI)
    (github issues
    [here](https://github.com/jtmelton/appsensor/issues/10) and
    [here](https://github.com/jtmelton/appsensor/issues/11))~~ -\> DONE

### January 2016 (2.3)

  - ~~Get CI server (cloudbees?) setup ([github
    issue](https://github.com/jtmelton/appsensor/issues/15))~~ -\> DONE
  - Video demo of setting up appsensor (screen capture) (related to
    sample apps)
  - New detection point implementations ([github
    issue](https://github.com/jtmelton/appsensor/issues/8))
  - AOP examples of detection point implementations

### May 2016 (2.4)

  - Trend monitoring implementation ([github
    issue](https://github.com/jtmelton/appsensor/issues/6))
  - Additional integrations for reporting (graphite, ganglia -\> see
    list supported by codahale metrics)

## Past activities

**September 2015** Final release v2.2.0 code

**June 2015** Final release v2.1.0 code

**April 2015** CISO Briefing booklet published

**February 2015** Introduction for Developers flyer published

**January 2015** Final release v2.0.0 code

**May 2014** Finalisation and publication of the AppSensor Guide v2.0

**November, 2013** - AppSensor 2.0 hackathon, and document writing &
review at AppSecUSA 2013, New York

**2012-2013** - Active Development of next AppSensor book

**September, 2011** - AppSensor Summit at AppSec USA 2011, Minneapolis

**September, 2010** - Presented at AppSecUSA
[slides](http://www.slideshare.net/michael_coates/real-time-application-defenses-the-reality-of-appsensor-esapi-5181743)

**June, 2010** - Active ESAPI Integration Underway

**November, 2009** [OWASP DC,
November 2009](http://www.owasp.org/images/0/06/Defend_Yourself-Integrating_Real_Time_Defenses_into_Online_Applications-Michael_Coates.pdf)

**2009** v1.2 in the works, demo application in development

**May, 2009** - AppSec EU Poland - Presentation
([PPT](http://www.owasp.org/images/b/b7/AppsecEU09_MichaelCoates.pptx))
([Video](http://blip.tv/file/2198771))

**January, 2009** - v1.1 Released - Beta Status

**November, 2008** - AppSensor Talk at OWASP Portugal

**November, 2008** - v1.0 Released - Beta Status

**April 16, 2008** - Project Begins

# Detection Points

Below are the primary detection points defined within AppSensor. These
are just the titles; the document contains descriptions, examples and
considerations for implementing these detection points.

`'''`[`Detailed``   ``Detection``   ``Point``   ``Information``
 ``Here`](http://www.owasp.org/index.php/AppSensor_DetectionPoints)` '''`

**[`Response``   ``Action``   ``Information``
 ``Here`](http://www.owasp.org/index.php/AppSensor_ResponseActions)**

**Summary of Information** **Detection Categories:**

RE - Request

AE - Authentication

SE - Session

ACE - Access Control

IE - Input

EE - Encoding

CIE - Command Injection

FIO - File IO

HT - Honey Trap

UT - User Trend

STE - System Trend

RP - Reputation

**Signature Based Event Titles**

ID Event

RE1 Unexpected HTTP Command

RE2 Attempt to Invoke Unsupported HTTP Method

RE3 GET When Expecting POST

RE4 POST When Expecting GET

RE5 Additional/Duplicated Data in Request

RE6 Data Missing from Request

RE7 Unexpected Quantity of Characters in Parameter

RE8 Unexpected Type of Characters in Parameter

AE1 Use Of Multiple Usernames

AE2 Multiple Failed Passwords

AE3 High Rate of Login Attempts

AE4 Unexpected Quantity of Characters in Username

AE5 Unexpected Quantity of Characters in Password

AE6 Unexpected Type of Character in Username

AE7 Unexpected Type of Character in Password

AE8 Providing Only the Username

AE9 Providing Only the Password

AE10 Adding POST Variable

AE11 Missing POST Variable

AE12 Utilization of Common Usernames

SE1 Modifying Existing Cookie

SE2 Adding New Cookie

SE3 Deleting Existing Cookie

SE4 Substituting Another User's Valid Session ID or Cookie

SE5 Source IP Address Changes During Session

SE6 Change Of User Agent Mid Session

ACE1 Modifying URL Argument Within a GET for Direct Object Access
Attempt

ACE2 Modifying Parameter Within a POST for Direct Object Access Attempt

ACE3 Force Browsing Attempt

ACE4 Evading Presentation Access Control Through Custom POST

IE1 Cross Site Scripting Attempt

IE2 Violation of Implemented White Lists

IE3 Violation Of Implemented Black Lists

IE4 Violation of Input Data Integrity

IE5 Violation of Stored Business Data Integrity

IE6 Violation of Security Log Integrity

EE1 Double Encoded Character

EE2 Unexpected Encoding Used

CIE1 Blacklist Inspection for Common SQL Injection Values

CIE2 Detect Abnormal Quantity of Returned Records

CIE3 Null Byte Character in File Request

CIE4 Carriage Return or Line Feed Character In File Request

FIO1 Detect Large Individual File

FIO2 Detect Large Number of File Uploads

HT1 Alteration to Honey Trap Data

HT2 Honey Trap Resource Requested

HT3 Honey Trap Data Used

**Behavior Based Event Titles**
UT1 Irregular Use of Application

UT2 Speed of Application Use

UT3 Frequency of Site Use

UT4 Frequency of Feature Use

STE1 High Number of Logouts Across The Site

STE2 High Number of Logins Across The Site

STE3 Significant Change in Usage of Same Transaction Across The Site

RP1 Suspicious or Disallowed User IP Address

RP2 Suspicious External User Behavior

RP3 Suspicious Client-Side Behavior

RP4 Change to Environment Threat Level

# Media

## Introductory Briefings

|                                                                                                 |  |                                                                                                   |  |                                                                                                          |
| :---------------------------------------------------------------------------------------------: |  | :-----------------------------------------------------------------------------------------------: |  | :------------------------------------------------------------------------------------------------------: |
|                                           Developers                                            |  |                                            Architects                                             |  |                                                  CISOs                                                   |
| ![Appsensor-developer-small.jpg](Appsensor-developer-small.jpg "Appsensor-developer-small.jpg") |  | ![Appsensor_crosstalk_small.jpg](Appsensor_crosstalk_small.jpg "Appsensor_crosstalk_small.jpg") |  | ![Appsensor-cisobriefing-small.jpg](Appsensor-cisobriefing-small.jpg "Appsensor-cisobriefing-small.jpg") |

The CISO briefing is also available to [buy at cost in
print](http://www.lulu.com/shop/owasp-foundation/appsensor-ciso-briefing/paperback/product-22121723.html).

## AppSensor Website

![Appsensor-website-large.jpg](Appsensor-website-large.jpg
"Appsensor-website-large.jpg")

<http://appsensor.org/>

## Code

  - v2 [Github Code](https://github.com/jtmelton/appsensor)
  - (LEGACY) v1 [Google Code](http://code.google.com/p/appsensor/)

## AppSensor Guide

  - OWASP AppSensor Guide
      - v2.0 EN
          - [PDF](https://www.owasp.org/index.php/File:Owasp-appsensor-guide-v2.pdf)
          - [DOC](https://www.owasp.org/index.php/File:Owasp-appensor-guide-v2.doc)
          - [Print on demand at cost hard
            copy](http://www.lulu.com/shop/owasp-foundation/appsensor-guide/paperback/product-21608107.html)
      - v1.1 EN
          - [PDF](https://www.owasp.org/images/2/2f/OWASP_AppSensor_Beta_1.1.pdf)
          - [DOC](https://www.owasp.org/images/b/b0/OWASP_AppSensor_Beta_1.1.doc)

## Presentations

[Automated Application Defenses to Thwart Advanced Attackers (Slides &
Audio)](http://www.brighttalk.com/webcast/20680)

July, 2010 - OWASP London (UK) - [Real Time Application Attack Detection
and Response with OWASP
AppSensor](http://www.owasp.org/index.php/File:Owasp-london-20100715-appsensor-3.pdf)

June, 2010 - OWASP Leeds/North (UK) - OWASP AppSensor - The Self-Aware
Web Application

June, 2010 - Video presentation - [Automated Application Defenses to
Thwart Advanced
Attackers](http://michael-coates.blogspot.com/2010/06/online-presentation-thursday-automated.html)

November, 2009 - AppSec DC - [Defend Yourself: Integrating Real Time
Defenses into Online
Applications](http://www.owasp.org/images/0/06/Defend_Yourself-Integrating_Real_Time_Defenses_into_Online_Applications-Michael_Coates.pdf)

May, 2009 - [OWASP Podcast
\#51](http://www.owasp.org/download/jmanico/owasp_podcast_51.mp3)

May, 2009 - AppSec EU Poland - [Real Time Defenses against Application
Worms and Malicious
Attackers](https://www.owasp.org/images/b/b7/AppsecEU09_MichaelCoates.pptx)

November, 2008 - [OWASP Summit Portugal 2008
PPT](https://www.owasp.org/images/7/77/Presentation_AppSensor.ppt)

## Video Demos of AppSensor

[Detecting Multiple Attacks & Logging Out
Attacker](http://www.youtube.com/watch?v=8ItfuwvLxRk)

[Detecting XSS Probes](http://www.youtube.com/watch?v=CekUMk_VRV8)

[Detecting URL Tampering](http://www.youtube.com/watch?v=LfD4y67qdWE)

[Detecting Verb Tampering](http://www.youtube.com/watch?v=1D6nTlmYjhY)

## Source Documents / Artwork

  - Guide
      - [Word (content
        only)](https://www.owasp.org/index.php/File:Owasp-appensor-guide-v2.doc),
        DOC 11Mb
      - [Word, images, Lulu covers,
        diagrams](https://4ed64fe7f7e3f627b8d0-bc104063a9fe564c2d8a75b1e218477a.ssl.cf2.rackcdn.com/appsensor-guide-2v0-owasp.zip),
        ZIP 96Mb
  - Introduction for Developers
      - [A4 Illustrator and PDF
        exports](https://www.owasp.org/index.php/File:Appsensor-intro-for-developers-a4.zip),
        ZIP 19Mb
      - [US letter Illustrator and PDF
        exports](https://www.owasp.org/index.php/File:Appsensor-intro-for-developers-usletter.zip),
        ZIP 19Mb
  - Poster
      - [A1 Illustrator and PDF
        export](https://www.owasp.org/index.php/File:Owasp-appsensor-poster-a1.zip)
        ZIP, 18Mb

# Project About

}}

__NOTOC__ <headertabs></headertabs>

[AppSensor Project](Category:OWASP_Project "wikilink") [Category:OWASP
Project](Category:OWASP_Project "wikilink")
[Category:OWASP_Builders](Category:OWASP_Builders "wikilink")
[Category:OWASP_Defenders](Category:OWASP_Defenders "wikilink")
[Category:OWASP_Document](Category:OWASP_Document "wikilink")
[Category:OWASP_Download](Category:OWASP_Download "wikilink")
[Category:SAMM-EH-3](Category:SAMM-EH-3 "wikilink")
[Category:SAMM-SA-2](Category:SAMM-SA-2 "wikilink")
[Category:SAMM-VM-3](Category:SAMM-VM-3 "wikilink")