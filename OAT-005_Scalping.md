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

OAT-005

### Threat Event Name

Scalping

### Summary Defining Characteristics

Obtain limited-availability and/or preferred goods/services by unfair
methods.

### Indicative Diagram

![OAT-005_Scalping.png](OAT-005_Scalping.png "OAT-005_Scalping.png")

### Description

Acquisition of goods or services using the application in a manner that
a normal user would be unable to undertake manually.

Although Scalping may include monitoring awaiting availability of the
goods or services, and then rapid action to beat normal users to obtain
these, Scalping is not a "last minute" action like [OAT-013
Sniping](OAT-013_Sniping "wikilink"), nor just related to automation on
behalf of the user such as in [OAT-006
Expediting](OAT-006_Expediting "wikilink"). This is because Scalping
includes the additional concept of limited availability of sought-after
goods or services, and is most well known in the ticketing business
where the tickets acquired are then resold later at a profit by the
scalpers/touts. This can also lead to a type of user denial of service,
since the goods or services become unavailable rapidly.

### Other Names and Examples

Bulk purchase; Purchase automaton; Purchase bot; Restaurant table/hotel
room reservation speed-booking; Queue jumping; Sale stampede; Secondary
ticketing; Ticket resale; Ticket scalping; Ticket touting

### See Also

  - [OAT-006 Expediting](OAT-006_Expediting "wikilink")
  - [OAT-013 Sniping](OAT-013_Sniping "wikilink")
  - [OAT-015 Denial of Service](OAT-015_Denial_of_Service "wikilink")
  - [OAT-021 Denial of
    Inventory](OAT-021_Denial_of_Inventory "wikilink")

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