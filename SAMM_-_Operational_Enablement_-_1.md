<div style="float:left; width:65%;">

</div>

<div style="float:right; width:30%;">

[<http://www.opensamm.org/downloads/BackButton.png>](http://www.owasp.org/index.php/SAMM_-_Deployment)

</div>

<div style="width:100%; float:left;">

<div style="width:30%; float:right; padding-top:50px; padding-left:10px;">

#### Results

  - Ad hoc improvements to software security posture through better
    understanding of correct operations
  - Operators and users aware of their role in ensuring secure
    deployment
  - Improved communications between software developers and users for
    security-critical information

#### Success Metrics

  - \>50% of projects with updated deployment security information in
    past 6 months
  - \>50% of projects with operational procedures for events updated in
    past 6 months

#### Costs

  - Ongoing project overhead from maintenance of deployment security
    information
  - Ongoing project overhead from maintenance of critical operating
    procedures

#### Personnel

  - Developers (1-2 days/yr)
  - Architects (1-2 days/yr)
  - Managers (1 days/yr)
  - Support/Operators (1 days/yr)

#### Related Levels

</div>

<div style="float:left; width:65%;">

## Activities

### A. Capture critical security information for deployment

With software-specific knowledge, project teams should identify any
security-relevant configuration and operations information and
communicate it to users and operators. This enables the actual security
posture of software at deployment sites to function in the same way that
designers in the project team intended.

This analysis should begin with architects and developers building a
list of security features built-in to the software. From that list,
information about configuration options and their security impact should
be captured as well. For projects that offer several different
deployment models, information about the security ramifications of each
should be noted to better inform users and operators about the impact of
their choices.

Overall, the list should be lightweight and aim to capture the most
critical information. Once initially created, it should be reviewed by
the project team and business stakeholders for agreement. Additionally,
it is effective to review this list with select operators or users in
order to ensure the information is understandable and actionable.
Project teams should review and update this information with every
release, but must do so at least every 6 months.

### B. Document procedures for typical application alerts

With specific knowledge of ways in which software behaves, project teams
should identify the most important error and alert messages which
require user/operator attention. From each identified event, information
related to appropriate user/operator actions in response to the event
should be captured.

From the potentially large set of events that the software might
generate, select the highest priority set based on relevance in terms of
the business purpose of the software. This should include any
security-related events, but also may include critical errors and alerts
related to software health and configuration status.

For each event, actionable advice should be captured to inform users and
operators of required next steps and potential root causes of the event.
These procedures must be reviewed by the project team and updated at
every major product release, every 6 months, but can be done more
frequently, e.g. with each release.

</div>

</div>

<div style="float:left; width:100%;">




\----

-----

### Additional Resources

[:Category:SAMM-OE-1](:Category:SAMM-OE-1 "wikilink")

</div>

__NOTOC__ __NOEDITSECTION__

[Category:SAMM-OE-1](Category:SAMM-OE-1 "wikilink")