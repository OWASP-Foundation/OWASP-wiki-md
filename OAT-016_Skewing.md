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

OAT-016

### Threat Event Name

Skewing

### Summary Defining Characteristics

Repeated link clicks, page requests or form submissions intended to
alter some metric.

### Indicative Diagram

![OAT-016_Skewing.png](OAT-016_Skewing.png "OAT-016_Skewing.png")

### Description

Automated repeated clicking or requesting or submitting content, a
ecting application-based metrics such as counts and measures of
frequency and/or rate. The metric or measurement may be visible to users
(e.g. betting odds, likes, market/ dynamic pricing, visitor count, poll
results, reviews) or hidden (e.g. application usage statistics, business
performance indicators). Metrics may affect individuals as well as the
application owner, e.g. user reputation, influence others, gain fame, or
undermine someone else's reputation.

For malicious alteration of digital advertisement metrics, see [OAT-003
Ad Fraud](OAT-003_Ad_Fraud "wikilink") instead.

### Other Names and Examples

Biasing KPIs; Boosting friends, visitors, and likes; Click fraud;
Dynamic pricing hacking; Election fraud; Hit count fraud; Market
distortion; Metric and statistic skewing; Page impression fraud; Poll
fraud; Poll skewing; Poll/voting subversion; Rating/review skewing; SEO;
Stock manipulation; Survey skewing

### See Also

  - [OAT-003 Ad Fraud](OAT-003_Ad_Fraud "wikilink")
  - [OAT-017 Spamming](OAT-017_Spamming "wikilink")
  - [OAT-019 Account Creation](OAT-019_Account_Creation "wikilink")

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