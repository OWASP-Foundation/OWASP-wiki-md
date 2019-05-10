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

OAT-010

### Threat Event Name

Card Cracking

### Summary Defining Characteristics

Identify missing start/expiry dates and security codes for stolen
payment card data by trying different values.

### Indicative Diagram

![OAT-010_Card_Cracking.png](OAT-010_Card_Cracking.png
"OAT-010_Card_Cracking.png")

### Description

Brute force attack against application payment card processes to
identify the missing values for start date, expiry date and/or card
security code (CSC), also referred to in many ways, including card
validation number 2 (CVN2), card validation code (CVC), card
verification value (CV2) and card identification number (CID).

When these values are known as well as the Primary Account Number (PAN),
[OAT-001 Carding](OAT-001_Carding "wikilink") is used to validate the
details, and [OAT-012 Cashing Out](OAT-012_Cashing_Out "wikilink") to
obtain goods or cash.

### Other Names and Examples

Brute forcing credit card information; Card brute forcing; Credit card
cracking; Distributed guessing attack

### See Also

  - [OAT-001 Carding](OAT-001_Carding "wikilink")
  - [OAT-012 Cashing Out](OAT-012_Cashing_Out "wikilink")

## Cross-References

### CAPEC Category / Attack Pattern IDs

  - 112 Brute Force
  - 210 Abuse of Functionality

### CWE Base / Class / Variant IDs

  - 799 Improper Control of Interaction Frequency
  - 837 Improper Enforcement of a Single, Unique Action

### WASC Threat IDs

  - 11 Brute Force
  - 21 Insufficient Anti-Automation
  - 42 Abuse of Functionality

### OWASP Attack Category / Attack IDs

  - [Abuse of
    Functionality](:Category:Abuse_of_Functionality "wikilink")
  - [Brute Force Attack](Brute_force_attack "wikilink")

[Category: Automated Threat](Category:_Automated_Threat "wikilink")