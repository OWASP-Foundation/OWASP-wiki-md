# Main

# Download

| width="35%"                                                                                                                                                             | Document (wiki)                                                                                                                  | width="40%" | Document (PDF) | width="10%" | Language | width="10%" | Date |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------- | ----------- | -------------- | ----------- | -------- | ----------- | ---- |
| [OWASP Best Practices: Einsatz von Web Application Firewalls - **VERSION 1.0.2**](Best_Practices:_Einsatz_von_Web_Application_Firewalls "wikilink")                     | [OWASP Best Practices: Einsatz von Web Application Firewalls -*' VERSION 1.0.2*'](Media:Best_Practices_Guide_WAF.pdf "wikilink") | Deutsch     | 2008-03-18     |             |          |             |      |
| [OWASP Best Practices: Use of Web Application Firewalls - **VERSION 1.0.5**](:Category:OWASP_Best_Practices:_Use_of_Web_Application_Firewalls/Version_1.0.5 "wikilink") | [OWASP Best Practices: Use of Web Application Firewalls - **VERSION 1.0.5**](Media:Best_Practices_WAF_v105.en.pdf "wikilink")    | English     | 2008-07-17     |             |          |             |      |
|                                                                                                                                                                         |                                                                                                                                  |             |                |             |          |             |      |

Best Practices: Web Application Firewalls

# Terminology

The specialist terms used in this document are not explained in detail
and knowledge of their meaning is assumed. No glossary has been included
in order to keep the volume manageable and to keep to the actual subject
of this paper as closely as possible - the use of Web Application
Firewalls.

Detailed definitions and more in-depth descriptions concerning WAS - Web
Application Security - can be found at:

  - <http://www.owasp.org/index.php/Category:AttackOWASP>
    Category:Attack
  - <http://www.owasp.org/index.php/Category:ThreatOWASP>
    Category:Threat
  - <http://www.owasp.org/index.php/Category:VulnerabilityOWASP>
    Category:Vulnerability
  - <http://www.webappsec.org/projects/threat/v1/WASC-TC-v1_0.de.docWASTC>
    Web Application Security Consortium: Web Security Threat
    Classification
  - <http://www.webappsec.org/projects/wafec/WAFEC> Web Application
    Security Consortium: Web Application Firewall Evaluation Criteria
  - <http://www.owasp.org/images/9/9c/OWASPAppSecEU2006_WAFs_WhenAreTheyUseful.ppt>
    OWASP WAFs When Are They Useful

# Licence

This document is licensed under a *Creative Commons attribution under
equivalent conditions as the 2.0 Germany license.* To view the licence,
please go to <http://creativecommons.org/licenses/bysa/2.0/de/> or send
a letter to Creative Commons, 171 Second Street, Suite 300, San
Francisco, California 94105, USA.

![Image:CC-15.png](CC-15.png "Image:CC-15.png")

# Authors

\-- original Daten aus .odf Dokument: unlesbares Layout und veraltet:
Maximilian Dermann maximilian.dermann(at)lht.dlh.deLufthansa Technik AG

Miro Dziadzkamirko.dziadzka(at)artofdefence.com art of defence GmbH

Boris Hemkemeierboris(at)owasp.orgOWASP German Chapter

Achim Hoffmannachim.hoffmann(at)securenet.deSecureNet GmbH

Alexander Meiselalexander.meisel(at)artofdefence.comart of defence GmbH

Matthias Rohr matthias.rohr(at)securenet.deSecureNet GmbH

Thomas Schreiberthomas.schreiber(at)securenet.deSecureNet GmbH --\>

|                                                             |                    |                                                   |                      |                                                                |  |                                       |                                             |
| ----------------------------------------------------------- | ------------------ | ------------------------------------------------- | -------------------- | -------------------------------------------------------------- |  | ------------------------------------- | ------------------------------------------- |
| style="border-bottom:1px solid black" width="24%"           |                    | style="border-bottom:1px solid black" width="24%" |                      | style="border-bottom:1px solid black" width="24%"              |  | style="border-bottom:1px solid black" | <small>updated email address (2012)</small> |
| style="vertical-align:top;float:right;padding-right:0.5em;" | Maximilian Dermann | maximilian.dermann(at)lht.dlh.de                  | Lufthansa Technik AG |                                                                |  |                                       |                                             |
| style="vertical-align:top;float:right;padding-right:0.5em;" | Mirko Dziadzka     | mirko.dziadzka(at)artofdefence.com                | art of defence GmbH  | <small>mirko.dziadzka(at)riverbed.com</small>                  |  |                                       |                                             |
| style="vertical-align:top;float:right;padding-right:0.5em;" | Boris Hemkemeier   | boris(at)owasp.org                                | OWASP German Chapter |                                                                |  |                                       |                                             |
| style="vertical-align:top;float:right;padding-right:0.5em;" | Achim Hoffmann     | achim.hoffmann(at)securenet.de                    | SecureNet GmbH       | <small>achim.hoffmann(at)sicsec.de, achim(at)owasp.org</small> |  |                                       |                                             |
| style="vertical-align:top;float:right;padding-right:0.5em;" | Alexander Meisel   | alexander.meisel(at)artofdefence.com              | art of defence GmbH  | <small>alex.meisel(at)riverbed.com</small>                     |  |                                       |                                             |
| style="vertical-align:top;float:right;padding-right:0.5em;" | Matthias Rohr      | matthias.rohr(at)securenet.de                     | SecureNet GmbH       | <small>matthias.rohr(at)owasp.org</small>                      |  |                                       |                                             |
| style="vertical-align:top;float:right;padding-right:0.5em;" | Thomas Schreiber   | thomas.schreiber(at)securenet.de                  | SecureNet GmbH       |                                                                |  |                                       |                                             |

# Project About

This document has been developed by the *OWASP German Chapter*. The
authors are employees of companies, who are consulting on the use and
operation of WAFs, are producing WAFs and/or are setting up WAFs.

__NOTOC__ <headertabs />

[Category:Germany](Category:Germany "wikilink") [Category:OWASP
Project](Category:OWASP_Project "wikilink") [Category:OWASP Best
Practices](Category:OWASP_Best_Practices "wikilink") [Category:OWASP
Document](Category:OWASP_Document "wikilink") [Category:OWASP
Download](Category:OWASP_Download "wikilink")
[Category:OWASP_Alpha_Quality_Document](Category:OWASP_Alpha_Quality_Document "wikilink")
[Category:OWASP_Builders](Category:OWASP_Builders "wikilink")
[Category:OWASP_Defenders](Category:OWASP_Defenders "wikilink")
[Category:How To](Category:How_To "wikilink")
[Category:SAMM-EH-3](Category:SAMM-EH-3 "wikilink")