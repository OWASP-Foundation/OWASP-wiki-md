<div style="float:left; width:65%;">

</div>

<div style="float:right; width:30%;">

[<http://www.opensamm.org/downloads/BackButton.png>](http://www.owasp.org/index.php/SAMM_-_Construction)

</div>

<div style="width:100%; float:left;">

<div style="width:30%; float:right; padding-top:50px; padding-left:10px;">

#### Results

  - High-level understanding of factors that may lead to negative
    outcomes
  - Increased awareness of threats amongst project teams
  - Inventory of threats for your organization

#### Success Metrics

  - \>50% of project stakeholders briefed on the threat models of
    relevant projects within past 12 months
  - \>75% of project stakeholders briefed on attacker profiles for
    relevant architectures

#### Costs

  - Buildout and maintenance of project artifacts for threat models

#### Personnel

  - Business Owners (1 day/yr)
  - Developers (1 day/yr)
  - Architects (1 day/yr)
  - Security Auditors (2 day/yr)
  - Managers (1 day/yr)

#### Related Levels

  - Strategy & Metrics - 1
  - Security Requirements - 2

</div>

<div style="float:left; width:65%;">

## Activities

### A. Build and maintain application-specific threat models

Based purely on the business purpose of each software project and the
business risk profile (if available) identify likely worst-case
scenarios for the software under development in each project team. This
can be conducted using simple attack trees or through a more formal
threat modeling process such as Microsoft’s STRIDE, Trike, etc.

To build attack trees, identify each worst-case scenario in one sentence
and label these as the high-level goals of an attacker. From each
attacker goal identified, identify preconditions that must hold in order
for each goal to be realized. This information should be captured in
branches underneath each goal where each branch is either a logical AND
or a logical OR of the statements contained underneath. An AND branch
indicates that each directly attached child nodes must be true in order
to realize the parent node. An OR branch indicates that any one of the
directly attached child nodes must be true in order to achieve the
parent node.

Regardless of the threat modeling approach, review each current and
historic functional requirement to augment the attack tree to indicate
security failures relevant to each. Brainstorm by iteratively dissecting
each failure scenario into all the possible ways in which an attacker
might be able to reach one of the goals. After initial creation, the
threat model for an application should be updated when significant
changes to the software are made. This assessment should be conducted
with senior developers and architects as well as one or more security
auditors.

### B. Develop attacker profile from software architecture

Initially, conduct an assessment to identify all likely threats to the
organization based on software projects. For this assessment, consider
threats to be limited to agents of malicious intent and omit other risks
such as known vulnerabilities, potential weaknesses, etc.

Begin by generally considering external agents and their corresponding
motivations for attack. To this list, add internal roles that could
cause damage and their motivations for insider attack. Based on the
architecture of the software project(s) under consideration, it can be
more efficient to conduct this analysis once per architecture type
instead of for each project individually since applications of
architecture and business purpose will generally be susceptible to
similar threats.

This assessment should be conducted with business owners and other
stakeholders but also include one or more security auditors for
additional perspective on threats. In the end, the goal is to have a
concise list of threat agents and their corresponding motivations for
attack.

</div>

</div>

<div style="float:left; width:100%;">




\----

-----

### Additional Resources

[:Category:SAMM-TA-1](:Category:SAMM-TA-1 "wikilink")

</div>

__NOTOC__ __NOEDITSECTION__

[Category:SAMM-TA-1](Category:SAMM-TA-1 "wikilink")