<div style="float:left; width:65%;">

</div>

<div style="float:right; width:30%;">

[<http://www.opensamm.org/downloads/BackButton.png>](http://www.owasp.org/index.php/SAMM_-_Verification)

</div>

<div style="width:100%; float:left;">

<div style="width:30%; float:right; padding-top:50px; padding-left:10px;">

#### Results

  - Formally offered assessment service to consistently review
    architecture for security
  - Pinpoint security flaws in maintenance-mode and legacy systems
  - Deeper understanding amongst project stakeholders on how the
    software provides assurance protections

#### Add’l Success Metrics

  - \>80% of stakeholders briefed on status of review requests in past 6
    months
  - \>75% of projects undergoing design review in past 12 months

#### Add’l Costs

  - Buildout, training, and maintenance of design review team
  - Ongoing project overhead from review activities

#### Add’l Personnel

  - Architects (1-2 days/yr)
  - Developers (1 day/yr)
  - Managers (1 day/yr)
  - Security Auditors (2-3 days/yr)

#### Related Levels

  - Education & Guidance - 2
  - Strategy & Metrics - 2

</div>

<div style="float:left; width:65%;">

## Activities

### A. Inspect for complete provision of security mechanisms

For each interface on a module in the high-level architecture diagram,
formally iterate through the list of security mechanisms and analyze the
system for their provision. This type of analysis should be performed on
both internal interfaces, e.g. between tiers, as well as external ones,
e.g. those comprising the attack surface.

The six main security mechanisms to consider are authentication,
authorization, input validation, output encoding, error handling and
logging. Where relevant, also consider the mechanisms of cryptography
and session management. For each interface, determine where in the
system design each mechanism is provided and note any missing or unclear
features as findings.

This analysis should be conducted by security-savvy staff with
assistance from the project team for application-specific knowledge.
This analysis should be performed once per release, usually toward the
end of the design phase. After initial analysis, subsequent releases are
required to update the findings based on changes being made during the
development cycle.

### B. Deploy design review service for project teams

Institute a process whereby project stakeholders can request a design
review. This service may be provided centrally within the organization
or distributed across existing staff, but all reviewers must be trained
on performing the reviews completely and consistently.

The review service should be centrally managed in that the review
request queue should be triaged by senior managers, architects, and
stakeholders that are familiar with the overall business risk profile
for the organization. This allows prioritization of project reviews in
alignment with overall business risk.

During a design review, the review team should work with project teams
to collect information sufficient to formulate an understanding of the
attack surface, match project-specific security requirements to design
elements, and verify security mechanisms at module interfaces.

</div>

</div>

<div style="float:left; width:100%;">




\----

-----

### Additional Resources

[:Category:SAMM-DR-2](:Category:SAMM-DR-2 "wikilink")

</div>

__NOTOC__ __NOEDITSECTION__

[Category:SAMM-DR-2](Category:SAMM-DR-2 "wikilink")