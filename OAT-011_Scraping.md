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

OAT-011

### Threat Event Name

Scraping

### Summary Defining Characteristics

Collect application content and/or other data for use elsewhere.

### Indicative Diagram

![OAT-011_Scraping.png](OAT-011_Scraping.png "OAT-011_Scraping.png")

### Description

Collecting accessible data and/or processed output from the application.
Some scraping may use fake or compromised accounts, or the information
may be accessible without authentication. The scraper may attempt to
read all accessible paths and parameter values for web pages and APIs,
collecting the responses and extracting data from them. Scraping may
occur in real time, or be more periodic in nature. Some Scraping may be
used to gain insight into how it is constructed and operates - perhaps
for cryptanalysis, reverse engineering, or session analysis.

When another application is being used as an intermediary between the
user(s) and the real application, see [OAT-020 Account
Aggregation](OAT-020_Account_Aggregation "wikilink"). If the intent is
to obtain cash or goods, see [OAT-012 Cashing
Out](OAT-012_Cashing_Out "wikilink") instead.

### Other Names and Examples

API provisioning; Bargain hunting; Comparative shopping; Content
scraping; Data aggregation; Database scraping; Farming; Harvesting; Meta
search scraper; Mining; Mirroring; Pagejacking; Powering APIs; Ripping;
Scraper bot; Screen scraping; Search / social media bot

### See Also

  - [OAT-012 Cashing Out](OAT-012_Cashing_Out "wikilink")
  - [OAT-018 Footprinting](OAT-018_Footprinting "wikilink")
  - [OAT-020 Account
    Aggregation](OAT-020_Account_Aggregation "wikilink")

## Cross-References

### CAPEC Category / Attack Pattern IDs

  - 167 Lifting Sensitive Data from the Client
  - 210 Abuse of Functionality
  - 281 Analyze Target

### CWE Base / Class / Variant IDs

  - 799 Improper Control of Interaction Frequency

### WASC Threat IDs

  - 21 Insufficient Anti-Automation
  - 42 Abuse of Functionality

### OWASP Attack Category / Attack IDs

  - [Abuse of
    Functionality](:Category:Abuse_of_Functionality "wikilink")

[Category: Automated Threat](Category:_Automated_Threat "wikilink")