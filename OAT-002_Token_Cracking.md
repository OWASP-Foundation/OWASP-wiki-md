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

OAT-002

### Threat Event Name

Token Cracking

### Summary Defining Characteristics

Mass enumeration of coupon numbers, voucher codes, discount tokens, etc.

### Indicative Diagram

![OAT-002_Token_Cracking.png](OAT-002_Token_Cracking.png
"OAT-002_Token_Cracking.png")

### Description

Identification of valid token codes providing some form of user benefit
within the application. The benefit may be a cash alternative, a
non-cash credit, a discount, or an opportunity such as access to a
limited offer.

For cracking of usernames, see [OAT-007 Credential
Cracking](OAT-007_Credential_Cracking "wikilink") instead.

### Other Names and Examples

Coupon guessing; Voucher, gift card and discount enumeration

### See Also

  - [OAT-007 Credential
    Cracking](OAT-007_Credential_Cracking "wikilink")
  - [OAT-011 Scraping](OAT-011_Scraping "wikilink")
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
  - 21 Insfficient Anti-Automation
  - 42 Abuse of Functionality

### OWASP Attack Category / Attack IDs

  - [Abuse of
    Functionality](:Category:Abuse_of_Functionality "wikilink")
  - [Brute Force Attack](Brute_force_attack "wikilink")

[Category: Automated Threat](Category:_Automated_Threat "wikilink")