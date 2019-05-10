## ESAPI control coverage of CWEs

This page covers the relationships between ESAPI controls and the
[CWE](http://cwe.mitre.org/) entries that are eliminated or reduced by
the application of those controls.

  - Validation
      - [CWE-20](http://cwe.mitre.org/data/definitions/20.html):
        Insufficient Input Validation
      - [CWE-116](http://cwe.mitre.org/data/definitions/116.html):
        Insufficient Output Sanitization
      - [CWE-228](http://cwe.mitre.org/data/definitions/228.html):
        Failure to Handle Syntactically Invalid Structure

<!-- end list -->

  - Canonicalization
      - [CWE-22](http://cwe.mitre.org/data/definitions/22.html): Path
        Traversal
      - [CWE-41](http://cwe.mitre.org/data/definitions/41.html): Failure
        to Resolve Path Equivalence
      - [CWE-178](http://cwe.mitre.org/data/definitions/178.html):
        Failure to Resolve Case Sensitivity

<!-- end list -->

  - Encoding
      - [CWE-113](http://cwe.mitre.org/data/definitions/113.html):
        Failure to Sanitize CRLF Sequences in HTTP Headers (aka 'HTTP
        Response Splitting')
      - [CWE-79](http://cwe.mitre.org/data/definitions/79.html): Failure
        to Sanitize Directives in a Web Page (aka 'Cross-site scripting'
        (XSS))
      - [CWE-89](http://cwe.mitre.org/data/definitions/89.html): Failure
        to Sanitize Data within SQL Queries (aka 'SQL Injection')

<!-- end list -->

  - Authentication
      - [CWE-287](http://cwe.mitre.org/data/definitions/287.html):
        Insufficient Authentication

<!-- end list -->

  - Session Management
      - [CWE-488](http://cwe.mitre.org/data/definitions/488.html): Data
        Leak Between Sessions
      - [CWE-613](http://cwe.mitre.org/data/definitions/613.html):
        Insufficient Session Expiration
      - [CWE-384](http://cwe.mitre.org/data/definitions/384.html):
        Session Fixation
      - [CWE-614](http://cwe.mitre.org/data/definitions/614.html):
        Sensitive Cookie in HTTPS Session Without "Secure" Attribute
      - [CWE-352](http://cwe.mitre.org/data/definitions/352.html):
        Cross-Site Request Forgery (CSRF)

<!-- end list -->

  - Access Control
      - [CWE-639](http://cwe.mitre.org/data/definitions/639.html):
        Access Control Bypass Through User-Controlled Key
      - [CWE-285](http://cwe.mitre.org/data/definitions/285.html):
        Missing or Inconsistent Access Control
      - [CWE-647](http://cwe.mitre.org/data/definitions/647.html): Use
        of Non-Canonical URL Paths for Authorization Decisions

<!-- end list -->

  - Encryption
      - [CWE-311](http://cwe.mitre.org/data/definitions/311.html):
        Failure to Encrypt Sensitive Data
      - [CWE-649](http://cwe.mitre.org/data/definitions/649.html):
        Reliance on Obfuscation or Encryption of Security-Relevant
        Inputs without Integrity Checking
      - [CWE-323](http://cwe.mitre.org/data/definitions/323.html):
        Reusing a Nonce, Key Pair in Encryption
      - [CWE-327](http://cwe.mitre.org/data/definitions/327.html): Use
        of a Broken or Risky Cryptographic Algorithm

<!-- end list -->

  - Randomizer
      - [CWE-330](http://cwe.mitre.org/data/definitions/330.html): Use
        of Insufficiently Random Values

<!-- end list -->

  - Error Handling
      - [CWE-209](http://cwe.mitre.org/data/definitions/209.html): Error
        Message Information Leaks
      - [CWE-392](http://cwe.mitre.org/data/definitions/392.html):
        Failure to Report Error in Status Code

<!-- end list -->

  - Logging
      - [CWE-222](http://cwe.mitre.org/data/definitions/222.html):
        Truncation of Security-relevant Information
      - [CWE-117](http://cwe.mitre.org/data/definitions/117.html):
        Incorrect Output Sanitization for Logs
      - [CWE-532](http://cwe.mitre.org/data/definitions/532.html):
        Information Leak Through Log Files

<!-- end list -->

  - Intrusion Detection

<!-- end list -->

  - HTTP Protection

<!-- end list -->

  - Utilities

<!-- end list -->

  - Filters

## Considerations for the Mapping

The mapping is notional; it is not complete.

Just because a feature is mapped to a CWE, does not mean that the
feature covers all child nodes of that CWE.

It would be useful to map individual API names, not just features.

## Gap Analysis

The CWE team has a capability for providing a "coverage graph" that
highlights the location of a subset of CWEs within the context of an
entire CWE hierarchy. This could be used to conduct a gap analysis to
see which CWEs are not addressed by ESAPI, which would be useful to
ESAPI consumers as well as identifying possible future requirements for
ESAPI itself. See the graphical depictions of the [CWE OWASP Top Ten
views](http://cwe.mitre.org/data/pdfs.html) for examples.

## Method

Only CWE identifiers associated with weaknesses were reviewed. (Some CWE
entries are arbitrary categories that organize weaknesses instead of
being weaknesses themselves). Only the most abstract CWE identifiers
were mapped, implying that lower-level variants are also covered (based
on the hierarchy imposed by CWE-1000, the research view, which has a
different hierarchical structure than CWE-699, the developer view).

As of December 2008, there are two different approaches for conducting
mappings: "literal" in which you only map to a CWE if it is specifically
mentioned or addressed, and "implied" in which you map to a CWE if it is
associated with general concepts. For example, the API functions for
output encoding can imply some protection against SQL injection, XSS,
and others. The initial CWE/ESAPI mapping was implied.