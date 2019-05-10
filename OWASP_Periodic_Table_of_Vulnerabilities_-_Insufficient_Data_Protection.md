[Return to Periodic Table Working
View](OWASP_Periodic_Table_of_Vulnerabilities#Periodic_Table_of_Vulnerabilities "wikilink")

## Insufficient Data Protection

### Root Cause Summary

Sensitive data is not sufficiently protected against disclosure,
modification or non-repudiation.

### Browser / Standards Solution

None

### Perimeter Solution

None

### Generic Framework Solution

Provide a configuration-based suite of encryption utilities for all data
security needs. This includes safeguards to prevent tampering (with
Hash-based Message Authentication Code or HMAC) and eavesdropping (with
symmetric or public key encryption).

The framework solution must be designed for ease of key rotation and
transparent, simple substitution of more secure algorithms as
cryptographic techniques improve.

### Custom Framework Solution

None

### Custom Code Solution

Identify which kinds of data need to be protected (e.g. Personally
Identifiable Information (PII) or authentication and identification
data). Examples of PII are names, passport numbers, address information
and personal characteristics.
Never store more information than is needed. Minimize the use,
collection and retention of data.
Use a risk-based approach, order the data by impact level (for example
low, moderate and high) if it is to be inappropriately accessed, used or
disclosed.
Make sure that all applicable (eg. local, federal) laws are obeyed.

### Discussion / Controversy

Data protection laws vary from country to country. Ensure that the
correct mitigations and protections have been taken.

### References

[Top 10 2013-A6-Sensitive Data
Exposure](Top_10_2013-A6-Sensitive_Data_Exposure "wikilink")
[Directive 95/46/EC (European
Union)](http://eur-lex.europa.eu/LexUriServ/LexUriServ.do?uri=CELEX:31995L0046:en:NOT)
[Guide to Protecting the Confidentiality of Personally Identifiable
Information
(NIST)](http://csrc.nist.gov/publications/nistpubs/800-122/sp800-122.pdf)
[Insufficient Data Protection
(WASC)](http://projects.webappsec.org/w/page/13246941/Insufficient%20Data%20Protection)