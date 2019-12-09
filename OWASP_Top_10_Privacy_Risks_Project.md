# Main

<div style="width:100%;height:90px;border:0,margin:0;overflow: hidden;">

![_lab_big.jpg](_lab_big.jpg "_lab_big.jpg")

</div>

<table>
<tbody>
<tr class="odd">
<td><h2 id="the_project_in_a_nutshell">The project in a nutshell</h2>
<p>The OWASP Top 10 Privacy Risks Project provides a top 10 list for privacy risks in web applications and related countermeasures. It covers technological and organizational aspects that focus on real-life risks, not just legal issues. The Project provides tips on how to implement privacy by design in web applications with the aim of helping developers and web application providers to better understand and improve privacy. The list uses the OECD Privacy Guidelines as a framework and can also be used to assess privacy risks associated with specific web applications.</p>
<h2 id="top_10_privacy_risks">Top 10 Privacy Risks</h2>
<dl>
<dt></dt>
<dd>P1    Web Application Vulnerabilities
</dd>
<dd>P2    Operator-sided Data Leakage
</dd>
<dd>P3    Insufficient Data Breach Response
</dd>
<dd>P4    Insufficient Deletion of personal data
</dd>
<dd>P5    Non-transparent Policies, Terms and Conditions
</dd>
<dd>P6    Collection of data not required for the primary purpose
</dd>
<dd>P7    Sharing of data with third party
</dd>
<dd>P8    Outdated personal data
</dd>
<dd>P9    Missing or Insufficient Session Expiration
</dd>
<dd>P10  Insecure Data Transfer
</dd>
</dl>
<p>Further information is provided in the Top 10 Privacy Risks tab.</p>
<h2 id="contact_us">Contact us</h2>
<p>{{Template:Contact</p></td>
<td><p>name = Florian Stahl</p></td>
<td><p>email = florian.stahl@owasp.org</p></td>
<td><p>username = Florian_Stahl }}<br />
Stefan Burgmair <a href="mailto:Stefan.Burgmair@owasp.org">@</a></p>
<h2 id="quick_download">Quick Download</h2>
<ul>
<li><a href="https://www.owasp.org/images/0/0a/OWASP_Top_10_Privacy_Countermeasures_v1.0.pdf">Top 10 Privacy Risks Countermeasures v1.0 (PDF)</a></li>
<li><a href="https://www.owasp.org/images/d/df/OWASP_Top10PrivacyRisks_20150529.pptx">Top 10 Privacy Risks Presentation (PPTX)</a></li>
<li><a href="https://www.owasp.org/images/6/6f/OWASPTop10PrivacyRisks_20141209.pdf">Results presentation at German OWASP Day 2014</a></li>
<li><a href="https://www.owasp.org/images/c/c3/Top10PrivacyRisks_IAPP_Summit_2015.pdf">Presentation from IAPP Global Privacy Summit 2015</a></li>
<li><a href="https://www.owasp.org/images/2/27/Presentation_HowToBoostPrivacy_IAPP_Intensive_2016.pdf">Presentation of countermeasures from IAPP Data Protection Intensive 2016</a></li>
</ul>
<h2 id="licensing">Licensing</h2>
<p>OWASP Top 10 Privacy Risks Project is free to use. It is licensed under the Creative Commons CC-BY-SA v3.0 License.</p></td>
<td><h2 id="download_infographic_version">Download Infographic version</h2>
<figure>
<img src="Top_10_Risks.png" title="Top_10_Risks.png" alt="Top_10_Risks.png" width="200" /><figcaption>Top_10_Risks.png</figcaption>
</figure></td>
<td><h2 id="news_events">News &amp; Events</h2>
<ul>
<li>[20 Feb 2014] Project Start</li>
<li>[21 Sep 2014] Top 10 Privacy Risks v1.0 published</li>
<li>[1 July 2015] German Translation available</li>
<li>[8 April 2016] Countermeasures v1.0 published</li>
<li>[19 December 2018] Call for Participation for the OWASP Top 10 Privacy Risks 2019</li>
</ul>
<h2 id="external_links">External Links</h2>
<p><a href="http://www.oecd.org/sti/ieconomy/2013-oecd-privacy-guidelines.pdf">OECD Privacy Guidelines</a> <a href="https://secure.edps.europa.eu/EDPSWEB/edps/EDPS/IPEN">Internet Privacy Engineering Network - IPEN</a><br />
<a href="https://www.youtube.com/watch?v=mO7bjmUAq-Q">Video from IPEN workshop at Berlin state parliament</a><br />
<a href="https://www.youtube.com/watch?v=6SEdnWlSZyk">Video from panel discussion at CPDP 2015 in Brussels</a><br />
<a href="https://www.youtube.com/watch?v=WXSZiWNyPZA">Video from presentation at AppSec EU 2015</a><br />
<a href="https://privacyscore.org/">Check your website with PRIVACYSCORE</a></p></td>
</tr>
</tbody>
</table>

# Top 10 Privacy Risks

## Top 10 Privacy Risks 2014

Version 1.0 of the OWASP Top 10 Privacy Risks list. Further information
and related countermeasures are provided in [this PDF
document](https://www.owasp.org/images/0/0a/OWASP_Top_10_Privacy_Countermeasures_v1.0.pdf).

<table style="background-color:#FFFFFF;border-collapse:collapse;border:1px solid #000000;color:#000000;width:100%" cellspacing="3" cellpadding="3" border="1">

<tr>

<td bgcolor="#D8D8D8">

<b>No.</b>

</td>

<td bgcolor="#D8D8D8">

<b>Title</b>

</td>

<td bgcolor="#D8D8D8">

<b>Frequency</b>

</td>

<td bgcolor="#D8D8D8">

<b>Impact    </b>

</td>

<td bgcolor="#D8D8D8">

<b>Description</b>

</td>

</tr>

<tr>

<td>

P1

</td>

<td>

Web Application Vulnerabilities

</td>

<td bgcolor="orange">

High

</td>

<td bgcolor="red">

Very high

</td>

<td>

Vulnerability is a key problem in any system that guards or operates on
sensitive user data. Failure to suitably design and implement an
application, detect a problem or promptly apply a fix (patch) is likely
to result in a privacy breach. This risk also encompasses the OWASP Top
10 List of web application vulnerabilities and the risks resulting from
them.

</td>

</tr>

<tr>

<td>

P2

</td>

<td>

Operator-sided Data Leakage

</td>

<td bgcolor="orange">

High

</td>

<td bgcolor="red">

Very high

</td>

<td>

Failure to prevent the leakage of any information containing or related
to user data, or the data itself, to any unauthorized party resulting in
loss of data confidentiality. Introduced either due to intentional
malicious breach or unintentional mistake e.g. caused by insufficient
access management controls, insecure storage, duplication of data or a
lack of awareness.

</td>

</tr>

<tr>

<td>

P3

</td>

<td>

Insufficient Data Breach Response

</td>

<td bgcolor="orange">

High

</td>

<td bgcolor="red">

Very high

</td>

<td>

Not informing the affected persons (data subjects) about a possible
breach or data leak, resulting either from intentional or unintentional
events; failure to remedy the situation by fixing the cause; not
attempting to limit the leaks.

</td>

</tr>

<tr>

<td>

P4

</td>

<td>

Insufficient Deletion of Personal Data

</td>

<td bgcolor="red">

Very high

</td>

<td bgcolor="orange">

High

</td>

<td>

Failure to effectively and/or timely delete personal data after
termination of the specified purpose or upon request.

</td>

</tr>

<tr>

<td>

P5

</td>

<td>

Non-transparent Policies, Terms and Conditions

</td>

<td bgcolor="red">

Very high

</td>

<td bgcolor="orange">

High

</td>

<td>

Not providing sufficient information to describing how data is
processed, such as its collection, storage, and processing. Failure to
make this information easily-accessible and understandable for
non-lawyers.

</td>

</tr>

<tr>

<td>

P6

</td>

<td>

Collection of data not required for the primary purpose

</td>

<td bgcolor="red">

Very high

</td>

<td bgcolor="orange">

High

</td>

<td>

Collecting descriptive, demographic or any other user-related data that
are not needed for the purposes of the system. Applies also to data for
which the user did not provide consent.

</td>

</tr>

<tr>

<td>

P7

</td>

<td>

Sharing of Data with Third Party

</td>

<td bgcolor="orange">

High

</td>

<td bgcolor="orange">

High

</td>

<td>

Providing user data to any third-party, without obtaining the user’s
consent. Sharing results either due to transfer or exchanging for a
monetary compensation or otherwise due to inappropriate use of
third-party resources included in the web site like widgets (e.g. maps,
social networks buttons), analytics or web bugs (e.g. beacons).

</td>

</tr>

<tr>

<td>

P8

</td>

<td>

Outdated personal data

</td>

<td bgcolor="orange">

High

</td>

<td bgcolor="red">

Very high

</td>

<td>

The use of outdated, incorrect or bogus user data. Failure to update or
correct the data.

</td>

</tr>

<tr>

<td>

P9

</td>

<td>

Missing or insufficient Session Expiration

</td>

<td bgcolor="yellow">

Medium

</td>

<td bgcolor="red">

Very high

</td>

<td>

Failure to effectively enforce session termination. May result in
collection of additional user-data without the user’s consent or
awareness.

</td>

</tr>

<tr>

<td>

P10

</td>

<td>

Insecure Data Transfer

</td>

<td bgcolor="yellow">

Medium

</td>

<td bgcolor="red">

Very high

</td>

<td>

Failure to provide data transfers over encrypted and secured channels,
excluding the possibility of data leakage. Failure of enforcing
mechanisms limiting the leak surface, e.g. allowing to infer any user
data out of the mechanics of Web application operation.

</td>

</tr>

</table>

Note: The values between 0 to 3 used for frequency and impact rating
were replaced by a textual description: 0-1: Low, 1-1.5: Medium, 1.5-2:
High, \> 2: Very high

# Participation and Discussion

## Participate

Some ways you can help:

  - Discuss with us in the mailing list or Google docs
  - Tell your colleagues and friends about the project
  - Provide feedback (feel free to contact us)
  - Apply the results in practice to improve web application privacy

Sign up to our [mailing
list](https://groups.google.com/a/owasp.org/forum/#!forum/top-10-privacy-risks-project/join)
to stay informed.

## Discussions and Documentation

To avoid overwriting issues we use Google Docs for our discussions.

### Current discussions

Privacy Risk Candidate List 2019:
<https://docs.google.com/document/d/1eEU7TsoaPG56-zhJi4bi1SD53Jto84GQ8dDGTajL8TY/edit>
Method Update 2019:
<https://docs.google.com/document/d/1AlAg2cybvo5VX-frzF5uHeAcib3X2rTAA2p97XH8fHw/edit>

### Closed discussions and documents

Countermeasures document:
<https://docs.google.com/document/d/1GaoJDPtyXMv09wIw9xXTVPYTR_6fQROlptszPhxVc1s/edit?usp=sharing>
Method:
<https://docs.google.com/document/d/1nHM9LH2rP6ac3DvJ7lehDNb9qVP5YADOQGNEuiy5okg/edit>
Privacy Risk list 2014:
<https://docs.google.com/document/d/1ufAuGtW42gUHtJF-9_VOzNZEegZJnMyqDcyfzmsjJeQ/edit>
Draft list:
<https://docs.google.com/document/d/1WMljvy09nulPnzv5XkFc2uxn1bSR-ftKqx5VoayTzW8/edit>
Impact rating:
<https://docs.google.com/a/owasp.org/document/d/1Gjd5XVJyGWHryUA2WyPSRQ0gQuaD5zWUCHU76_FHMKU/edit>
Calculation of the complete Privacy Risks list v1.0:
<https://docs.google.com/spreadsheets/d/1q7Xh4gclSieXNpVbdvyFwsZMENo2r3BoN2S3ww_W5-M/edit>
Brainstorming for countermeasures:
<https://docs.google.com/a/owasp.org/document/d/1g4Q_XDVGEAbVR_7DLNIbDN2men57BQ0pNn8CyRc2od8/edit>

## Survey Results

A survey was performed to determine the frequency of occurrence of
privacy violations in web applications.

63 people participated in total. The survey was online for 3 weeks from
4 to 25 August 2014.

Here is a summary of the results or you can [download the full
report](https://www.owasp.org/images/c/c8/PrivacyTop10Survey.pdf).

Part 1:

Q1 Do or did you work as a:

Software Developer 26.98%

Software Designer 12.70%

Legal Practitioner 4.76%

Software Project Manager 11.11%

Data Privacy Expert 33.33%

Security Expert 66.67%

Public Servant 12.70%

Other 11.11%

Q2 In total, how many years of professional experience do you have
related to privacy?

Average: 6.2 years

Q3 In total, how many years of professional experience do you have
related to web applications?

Average: 8.1 years

Part 2:

The following ratings are between 1 and 4.

The possible choices for answers where:

\[1\] Up to one out of four web applications. (0-25%)

\[2\] Up to ev ery second web application. (26-50%)

\[3\] Up to three out of four web applications. (51-75%)

\[4\] More than three out of four web applications. (76-100%)

\[excluded\] N/A

01\. Collection of data not required for main purpose

Average Rating: 3.1

02\. Collection of Incorrect Data

Average Rating: 2.0

03\. Collection without consent

Average Rating: 3.0

04\. Problems with getting Consent

Average Rating: 2.6

05\. Outdated Personal Data

Average Rating: 2.6

06\. Inability of users to modify stored data

Average Rating: 2.3

07\. Insufficient deletion of personal data

Average Rating: 3.3

08\. Unrelated use

Average Rating: 2.7

09\. Data Aggregation and Profiling

Average Rating: 2.4

10\. Sharing of data with third party

Average Rating: 2.8

11\. Operator-sided Data Leakage

Average Rating: 2.7

12\. Insecure data transfer

Average Rating: 2.3

13\. Web Application Vulnerabilities

Average Rating: 2.9

14\. Insufficient Data Breach Response

Average Rating: 2.6

15\. Form field design issues

Average Rating: 2.2

16\. Missing or Insufficient Session Expiration

Average Rating: 2.4

17\. Misleading Content

Average Rating: 2.3

18\. Non-transparent Policies, Terms and Conditions

Average Rating: 3.2

19\. Inappropriate Policies, Terms and Conditions

Average Rating: 2.7

20\. Transfer or processing through third party

Average Rating: 2.6

# FAQs

## Frequently Asked Questions

### Why is this project only about web applications and not about any kind of software?

Web applications can easily collect data from users without their
permission or without adequately informing them how their data is used.
Cookies, and other trackers, enable the monitoring of user's behaviour,
and this information may be used for a variety of commercial purposes,
including targeted advertising, profiling, and the sale of aggregated
data. This is why the subject is so important, especially for web
applications.

### Are the Top 10 Privacy Risks applicable for mobile apps as well?

Privacy risks for mobile apps are very similar. The rating might be
slightly different and there might be some additional risks related to
the loss of devices and the use of location data, but in general the Top
10 Privacy Risks are applicable for mobile apps as well.

### What is the difference between this project and the OWASP Top 10?

There are two main differences. First, the OWASP Top 10 describes
technical risks, that are not primarily affecting privacy. Second, the
OWASP Top 10 do not address software such as cookies or trackers, or
organisational issues like privacy notices, profiling, or the sharing of
data with third parties.

### Why should companies and other organisations be concerned about privacy risks?

Privacy risks may have serious consequences for an organisation, such
as:

  - perceived harm to privacy;
  - a failure to meet public expectations on both the use and protection
    of personal information;
  - retrospective imposition of regulatory conditions;
  - low adoption rates or poor participation in the scheme from both the
    public and partner organisations;
  - the costs of redesigning the system or retro-fitting solutions;
  - failure of a project or completed system;
  - withdrawal of support from key supporting organisations due to
    perceived privacy harms; and/ or
  - failure to comply with the law, leading to enforcement action from
    the regulator or compensation claims from individuals.

(Source: <http://ico.org.uk/pia_handbook_html_v2/html/1-Chap2-2.html>)

# Translation

Currently project documentation is available in English and German. If
you are interested in helping to translate to another language, please
contact the project leaders.

## German

### Top 10 Datenschutzrisiken

<table style="background-color:#FFFFFF;border-collapse:collapse;border:1px solid #000000;color:#000000;width:100%" cellspacing="3" cellpadding="3" border="1">

<tr>

<td bgcolor="#D8D8D8">

<b>Nr.</b>

</td>

<td bgcolor="#D8D8D8">

<b>Titel</b>

</td>

<td bgcolor="#D8D8D8">

<b>Häufigkeit</b>

</td>

<td bgcolor="#D8D8D8">

<b>Schaden    </b>

</td>

<td bgcolor="#D8D8D8">

<b>Beschreibung</b>

</td>

</tr>

<tr>

<td>

P1

</td>

<td>

Schwachstellen in Webanwendungen

</td>

<td bgcolor="orange">

Hoch

</td>

<td bgcolor="red">

Sehr hoch

</td>

<td>

Schwachstellen sind ein zentrales Problem in jedem System, mit dem
sensible Nutzerdaten erhoben, verarbeitet und genutzt werden. Bestehen
Fehler im Design oder in der Implementierung der Applikation, werden
Probleme nicht entdeckt oder Sicherheitspatches nicht unverzüglich
eingespielt, führt dies mit hoher Wahrscheinlichkeit zu einer Verletzung
des Persönlichkeitsrechts. Dieses Risiko wird bereits in anderen
Projekten behandelt, wie der OWASP Top 10 Liste der häufigsten
Sicherheitsrisiken für Webanwendungen.

</td>

</tr>

<tr>

<td>

P2

</td>

<td>

Datenabfluss beim Betreiber

</td>

<td bgcolor="orange">

Hoch

</td>

<td bgcolor="red">

Sehr hoch

</td>

<td>

Wird die unerwünschte Preisgabe personenbezogener oder
personenbeziehbarer Daten an nicht autorisierte Personen nicht wirksam
verhindert, ist dies ein Verlust der Vertraulichkeit. Ursachen sind
entweder ein vorsätzlich durchgeführter Datenabzug oder unbeabsichtigte
Fehler wie beispielsweise unzureichendes Zugriffsmanagement, unsichere
Datenablage, Datendopplung oder fehlendes Problembewusstsein
(Awareness).

</td>

</tr>

<tr>

<td>

P3

</td>

<td>

Unzureichende Reaktion bei einer Datenpanne

</td>

<td bgcolor="orange">

Hoch

</td>

<td bgcolor="red">

Sehr hoch

</td>

<td>

Betroffene werden nicht über mögliche Pannen oder Datenlecks
benachrichtigt, die durch Angriffe oder unbeabsichtigte Ereignisse
entstehen. Angemessene Abhilfemaßnahmen zum Schließen der Lücken und
Beseitigung der Ursache fehlen.

</td>

</tr>

<tr>

<td>

P4

</td>

<td>

Unzureichende Löschung personenbezogener Daten

</td>

<td bgcolor="red">

Sehr hoch

</td>

<td bgcolor="orange">

Hoch

</td>

<td>

Personenbezogene Daten werden nicht termingerecht oder nicht effektiv
nach Zweckablauf bzw. aufgrund einer Löschanfrage gelöscht.

</td>

</tr>

<tr>

<td>

P5

</td>

<td>

Intransparente Nutzungsbedingungen

</td>

<td bgcolor="red">

Very high

</td>

<td bgcolor="orange">

High

</td>

<td>

Informationen zur Datenverarbeitung wie Erhebung, Speicherung und
Nutzung personenbezogener Daten sind unzureichend. Diese Informationen
sind nicht leicht zugänglich oder für juristische Laien nicht
verständlich aufbereitet.

</td>

</tr>

<tr>

<td>

P6

</td>

<td>

Sammeln von Daten, die über den eigentlichen Zweck hinaus gehen

</td>

<td bgcolor="red">

Sehr hoch

</td>

<td bgcolor="orange">

Hoch

</td>

<td>

Es werden Beschreibungsdaten, demographische Daten oder sonstige
personenbezogene Daten gesammelt, die nicht für den vereinbarten Zweck
der Anwendung benötigt werden. Ebenso werden Daten gesammelt, für deren
Erhebung der Nutzer keine Einverständniserklärung abgegeben hat.

</td>

</tr>

<tr>

<td>

P7

</td>

<td>

Weitergabe von Daten an Dritte

</td>

<td bgcolor="orange">

Hoch

</td>

<td bgcolor="orange">

Hoch

</td>

<td>

Personenbezogene Daten werden ohne Einverständnis des Nutzers an Dritte
weiter gegeben bzw. diesen zur Verfügung gestellt. Die Weitergabe von
Daten und Erkenntnissen erfolgt entweder direkt oder auf Anfrage, gegen
Zahlung oder auch durch unsachgemäßen Einsatz von Diensten Dritter wie
beispielsweise Widgets für Webseiten (z.B. Landkarten, Buttons von
sozialen Netzwerken), Analysetools oder Web Bugs (z.B. Beacons).

</td>

</tr>

<tr>

<td>

P8

</td>

<td>

Veraltete personenbezogene Daten

</td>

<td bgcolor="orange">

Hoch

</td>

<td bgcolor="red">

Sehr hoch

</td>

<td>

Es werden veraltete, inkorrekte oder gefälschte personenbezogene Daten
genutzt. Datenaktualisierungen oder -korrekturen finden nicht in
ausreichendem Maße statt.

</td>

</tr>

<tr>

<td>

P9

</td>

<td>

Fehlendes oder unzureichendes Session-Ende

</td>

<td bgcolor="yellow">

Mittel

</td>

<td bgcolor="red">

Sehr hoch

</td>

<td>

Unzureichendes Beenden von Sessions. Dies kann dazu führen, dass
zusätzliche Nutzerdaten ohne Einverständnis oder Wissen des Nutzers
gesammelt werden.

</td>

</tr>

<tr>

<td>

P10

</td>

<td>

Unsichere Datenübertragung

</td>

<td bgcolor="yellow">

Mittel

</td>

<td bgcolor="red">

Sehr hoch

</td>

<td>

Die Datenübermittlung erfolgt nicht auf verschlüsselten und sicheren
Kanälen, so dass ein unautorisierter Zugriff nicht verhindert wird.
Mechanismen zum Verringern der Angriffsfläche, werden nicht umgesetzt.
Hierzu gehört es zu verhindern, dass durch das Verhalten der
Webanwendung Rückschlüsse auf Nutzerdaten möglich sind.

</td>

</tr>

</table>

### Presentation

[Video and
presentation](https://www.it-sa.de/de/events/2/2015-10-06/forum-rot-management/11939/#12089)
from it-sa Security Expo and Congress 2015

### Flyer

![Top_10_Privacy_Risks_German.png](Top_10_Privacy_Risks_German.png
"Top_10_Privacy_Risks_German.png")

## Japanese

[Link to
slidedeck](https://speakerdeck.com/owaspjapan/introducing-owasp-top10-privacy-risks-number-owasp-night-21th)

# Acknowledgements

## Volunteers

The Top 10 Privacy Risk list is developed by a team of volunteers. The
primary contributors to date have been:

  - Stefan Burgmair
  - R. Jason Cronk
  - Edward Delaporte
  - Tim Gough
  - Prof. Hans-Joachim Hof
  - Lukasz Olejnik
  - Florian Stahl

## Partners

  - [University of Applied Sciences
    Munich](http://www.cs.hm.edu/en/home/index.en.html)
  - [European Data Protection Supervisory's Internet Privacy Engineering
    Network
    (IPEN)](https://secure.edps.europa.eu/EDPSWEB/edps/EDPS/IPEN)
  - [International Association of Privacy Professionals
    (IAPP)](http://privacyassociation.org/)

## Sponsors

  - [msg systems](http://www.msg-systems.com/)

Feel free to contact us in case you are also interested to support the
OWASP Top 10 Privacy Risks project.

# Project About

__NOTOC__ <headertabs />

[Category:OWASP Project](Category:OWASP_Project "wikilink")
[Category:OWASP_Builders](Category:OWASP_Builders "wikilink")
[Category:OWASP_Defenders](Category:OWASP_Defenders "wikilink")
[Category:OWASP_Document](Category:OWASP_Document "wikilink")