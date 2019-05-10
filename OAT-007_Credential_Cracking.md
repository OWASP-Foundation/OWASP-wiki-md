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

OAT-007

### Threat Event Name

Credential Cracking

### Summary Defining Characteristics

Identify valid login credentials by trying different values for
usernames and/or passwords.

### Indicative Diagram

![OAT-007_Credential_Cracking.png](OAT-007_Credential_Cracking.png
"OAT-007_Credential_Cracking.png")

### Description

Brute force, dictionary (word list) and guessing attacks used against
authentication processes of the application to identify valid account
credentials. This may utilise common usernames or passwords, or involve
initial username evaluation.

The use of stolen credential sets (paired username and passwords) to
authenticate at one or more services is [OAT-008 Credential
Stuffing](OAT-008_Credential_Stuffing "wikilink").

### Other Names and Examples

Brute-force attacks against sign-in; Brute forcing log-in credentials;
Brute-force password cracking; Cracking login credentials; Password
brute-forcing; Password cracking; Reverse brute force attack; Username
cracking; Username enumeration

### See Also

  - [OAT-002 Token Cracking](OAT-002_Token_Cracking "wikilink")
  - [OAT-008 Credential
    Stuffing](OAT-008_Credential_Stuffing "wikilink")
  - [OAT-019 Account Creation](OAT-019_Account_Creation "wikilink")

## Cross-References

### CAPEC Category / Attack Pattern IDs

  - 16 Dictionary-based Password Attack
  - 49 Password Brute Forcing
  - 70 Try Common(default) Usernames and Passwords
  - 112 Brute Force

### CWE Base / Class / Variant IDs

  - 307 Improper Restriction of Excessive Authentication Attempts
  - 799 Improper Control of Interaction Frequency
  - 837 Improper Enforcement of a Single, Unique Action

### WASC Threat IDs

  - 11 Brute Force
  - 21 Insufficient Anti-Automation
  - Abuse of Functionality

### OWASP Attack Category / Attack IDs

  - [Abuse of
    Functionality](:Category:Abuse_of_Functionality "wikilink")
  - [Brute Force Attack](Brute_force_attack "wikilink")

[Category: Automated Threat](Category:_Automated_Threat "wikilink")