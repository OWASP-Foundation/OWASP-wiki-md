__NOTOC__

This is an automated threat. To view all automated threats, please see
the [Automated Threat Category](:Category:Automated_Threat "wikilink")
page. The OWASP Automated Threat Handbook - Wed Applications
([pdf](https://www.owasp.org/index.php/File:Automated-threat-handbook.pdf),
print), an output of the [OWASP Automated Threats to Web Applications
Project](OWASP_Automated_Threats_to_Web_Applications "wikilink"),
provides a fuller guide to each threat, detection methods and
countermeasures. The [threat identification
chart](https://www.owasp.org/index.php/File:Oat-ontology-decision-chart.pdf)
helps to correctly identify the automated threat.

## Definition

### OWASP Automated Threat (OAT) Identity Number

OAT-018

### Threat Event Name

Footprinting

### Summary Defining Characteristics

Probe and explore application to identify its constituents and
properties.

### Indicative Diagram

![OAT-018_Footprinting.png](OAT-018_Footprinting.png
"OAT-018_Footprinting.png")

### Description

Information gathering with the objective of learning as much as possible
about the composition, configuration and security mechanisms of the
application. Unlike Scraping, Footprinting is an enumeration of the
application itself, rather than the data. It is used to identify all the
URL paths, parameters and values, and process sequences (i.e. to
determine entry points, also collectively called the attack surface). As
the application is explored, additional paths will be identified which
in turn need to be examined.

Footprinting can also include brute force, dictionary and guessing of
file and directory names. Fuzzing may also be used to identify further
application resources and capabilities. However, it does not include
attempts to exploit weaknesses.

### Other Names and Examples

Application analysis; API discovery; Application enumeration; Automated
scanning; CGI scanning; Crawler; Crawling; Excavation; Forced browsing;
Forceful browsing; Fuzzing; Micro service discovery; Scanning;
Spidering; WSDL scanning

### See Also

  - [OAT-004 Fingerprinting](OAT-004_Fingerprinting "wikilink")
  - [OAT-011 Scraping](OAT-011_Scraping "wikilink")

## Cross-References

### CAPEC Category / Attack Pattern IDs

  - 169 Footprinting

### CWE Base / Class / Variant IDs

  - 200 Information Exposure

### WASC Threat IDs

  - 45 Fingerprinting

### OWASP Attack Category / Attack IDs

  - \-

[Category: Automated Threat](Category:_Automated_Threat "wikilink")