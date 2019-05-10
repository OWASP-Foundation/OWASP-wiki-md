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

OAT-012

### Threat Event Name

Cashing Out

### Summary Defining Characteristics

Buy goods or obtain cash utilising validated stolen payment card or
other user account data.

### Indicative Diagram

![OAT-012_Cashing_Out.png](OAT-012_Cashing_Out.png
"OAT-012_Cashing_Out.png")

### Description

Obtaining currency or higher-value merchandise via the application using
stolen, previously validated payment cards or other account login
credentials. Cashing Out sometimes may be undertaken in conjunction with
product return fraud. For financial transactions, this is usually a
transfer of funds to a mule’s account. For payment cards, this activity
may occur following [OAT-001 Carding](OAT-001_Carding "wikilink") of
bulk stolen data, or [OAT-010 Card
Cracking](OAT-010_Card_Cracking "wikilink"), and the goods are dropped
at a reshipper's address. The refunding of payments via non-financial
applications (e.g. tax refunds, claims payment) is also included in
Cashing Out.

Obtaining other information of value from the application is instead
[OAT-011 Scraping](OAT-011_Scraping "wikilink").

### Other Names and Examples

Deetsing; Money laundering; Online credit card fraud; Online payment
card fraud; Refund fraud; Stolen identity refund fraud (SIRF)

### See Also

  - [OAT-001 Carding](OAT-001_Carding "wikilink")
  - [OAT-011 Scraping](OAT-011_Scraping "wikilink")
  - [OAT-010 Card Cracking](OAT-010_Card_Cracking "wikilink")

## Cross-References

### CAPEC Category / Attack Pattern IDs

  - 210 Abuse of Functionality

### CWE Base / Class / Variant IDs

  - 799 Improper Control of Interaction Frequency
  - 837 Improper Enforcement of a Single, Unique Action

### WASC Threat IDs

  - 21 Insufficient Anti-Automation
  - 42 Abuse of Functionality

### OWASP Attack Category / Attack IDs

  - [Abuse of
    Functionality](:Category:Abuse_of_Functionality "wikilink")

[Category: Automated Threat](Category:_Automated_Threat "wikilink")