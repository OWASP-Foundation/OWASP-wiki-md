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

OAT-009

### Threat Event Name

CAPTCHA Defeat

### Summary Defining Characteristics

Solve anti-automation tests.

### Indicative Diagram

![OAT-009_CAPTCHA_Defeat.png](OAT-009_CAPTCHA_Defeat.png
"OAT-009_CAPTCHA_Defeat.png")

### Description

Completely Automated Public Turing test to tell Computers and Humans
Apart (CAPTCHA) challenges are used to distinguish normal users from
bots. Automation is used in an attempt to analyse and determine the
answer to visual and/or aural CAPTCHA tests and related puzzles. Apart
from conventional visual and aural CAPTCHA, puzzle solving mini games or
arithmetical exercises are sometimes used. Some of these may include
context-specific challenges.

The process that determines the answer may utilise tools to perform
optical character recognition, or matching against a prepared database
of pre-generated images, or using other machine reading, or human farms.

### Other Names and Examples

Breaking CAPTCHA; CAPTCHA breaker; CAPTCHA breaking; CAPTCHA bypass;
CAPTCHA decoding; CAPTCHA solver; CAPTCHA solving; Puzzle solving

### See Also

  - [OAT-006 Expediting](OAT-006_Expediting "wikilink")
  - [OAT-011 Scraping](OAT-011_Scraping "wikilink")

## Cross-References

### CAPEC Category / Attack Pattern IDs

  - \-

### CWE Base / Class / Variant IDs

  - 804 Guessable CAPTCHA
  - 841 Improper Enforcement of Behavioral Workflow

### WASC Threat IDs

  - 21 Insufficient Anti-Automation
  - 42 Abuse of Functionality

### OWASP Attack Category / Attack IDs

  - \-

[Category: Automated Threat](Category:_Automated_Threat "wikilink")