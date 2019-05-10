Last revision (mm/dd/yy): **//**

[Vulnerabilities Table of Contents](ASDR_TOC_Vulnerabilities "wikilink")

## Description

Functions with inconsistent implementations across operating systems and
operating system versions cause portability problems.

The behavior of functions in this category varies by operating system,
and at times, even by operating system version. Implementation
differences can include:

  - Slight differences in the way parameters are interpreted, leading to
    inconsistent results.
  - Some implementations of the function carry significant security
    risks.
  - The function might not be defined on all platforms.

## Risk Factors

TBD

## Examples

TBD

## Related [Attacks](Attacks "wikilink")

  - [Attack 1](Attack_1 "wikilink")
  - [Attack 2](Attack_2 "wikilink")

## Related [Vulnerabilities](Vulnerabilities "wikilink")

  - [Vulnerability 1](Vulnerability_1 "wikilink")
  - [Vulnerabiltiy 2](Vulnerabiltiy_2 "wikilink")

## Related [Controls](Controls "wikilink")

  - [Control 1](Control_1 "wikilink")
  - [Control 2](Control_2 "wikilink")

## Related [Technical Impacts](Technical_Impacts "wikilink")

  - [Technical Impact 1](Technical_Impact_1 "wikilink")
  - [Technical Impact 2](Technical_Impact_2 "wikilink")

## References

TBD \[\[Category:FIXME|add links

In addition, one should classify vulnerability based on the following
subcategories:
Ex:\[\[Category:Error_Handling_Vulnerability|Category:Error Handling
Vulnerability\]\]

Availability Vulnerability

Authorization Vulnerability

Authentication Vulnerability

Concurrency Vulnerability

Configuration Vulnerability

Cryptographic Vulnerability

Encoding Vulnerability

Error Handling Vulnerability

Input Validation Vulnerability

Logging and Auditing Vulnerability

Session Management Vulnerability\]\]

__NOTOC__

[Category:OWASP ASDR Project](Category:OWASP_ASDR_Project "wikilink")
[Category:Code Quality
Vulnerability](Category:Code_Quality_Vulnerability "wikilink")
[Category:Implementation](Category:Implementation "wikilink")
[Category:Vulnerability](Category:Vulnerability "wikilink")