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

OAT-015

### Threat Event Name

Denial of Service

### Summary Defining Characteristics

Target resources of the application and database servers, or individual
user accounts, to achieve denial of service (DoS).

### Indicative Diagram

![OAT-015_Denial_of_Service.png](OAT-015_Denial_of_Service.png
"OAT-015_Denial_of_Service.png")

### Description

Usage may resemble legitimate application usage, but leads to exhaustion
of resources such as file system, memory, processes, threads, CPU, and
human or financial resources. The resources might be related to web,
application or databases servers or other services supporting the
application, such as third party APIs, included third-party hosted
content, or content delivery networks (CDNs). The application may be
affected as a whole, or the attack may be against individual users such
as account lockout.

This ontology’s scope excludes other forms of denial of service that a
ect web applications, namely HTTP Flood DoS (GET, POST, Header
with/without TLS), HTTP Slow DoS, IP layer 3 DoS, and TCP layer 4 DoS.
Those protocol and lower layer aspects are covered adequately in other
taxonomies and lists.

### Other Names and Examples

Account lockout; App layer DDoS; Asymmetric resource consumption
(amplification); Business logic DDoS; Cash overflow; Forced deadlock;
Hash DoS; Inefficient code; Indexer DoS; Large files DoS; Resource
depletion, locking or exhaustion; Sustained client engagement

### See Also

  - [OAT-005 Scalping](OAT-005_Scalping "wikilink")
  - [OAT-013 Sniping](OAT-013_Sniping "wikilink")
  - [OAT-017 Spamming](OAT-017_Spamming "wikilink")
  - [OAT-019 Account Creation](OAT-019_Account_Creation "wikilink")
  - [OAT-021 Denial of
    Inventory](OAT-021_Denial_of_Inventory "wikilink")

## Cross-References

### CAPEC Category / Attack Pattern IDs

  - 2 Inducing Account Lockout
  - 25 Forced Deadlock
  - 119 Deplete Resources

### CWE Base / Class / Variant IDs

  - 399 Resource Management Errors
  - 645 Overly Restrictive Account Lockout Mechanism

### WASC Threat IDs

  - 10 Denial of Service

### OWASP Attack Category / Attack IDs

  - Account Lockout Attack
  - [Cash Overflow](Cash_Overflow "wikilink")
  - [Denial of Service](Denial_of_Service "wikilink")
  - [Resource Depletion](:Category:Resource_Depletion "wikilink")

[Category: Automated Threat](Category:_Automated_Threat "wikilink")