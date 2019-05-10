<div style="float:left; width:65%;">

</div>

<div style="float:right; width:30%;">

[<http://www.opensamm.org/downloads/BackButton.png>](http://www.owasp.org/index.php/SAMM_-_Construction)

</div>

<div style="width:100%; float:left;">

<div style="width:30%; float:right; padding-top:50px; padding-left:10px;">

#### Results

  - Detailed understanding of attack scenarios against business logic
  - Prioritized development effort for security features based on likely
    attacks
  - More educated decision-making for tradeoffs between features and
    security efforts
  - Stakeholders that can better avoid functional requirements that
    inherently have security flaws

#### Add’l Success Metrics

  - \>75% of all projects with updated abuse-case models within past 6
    months

#### Add’l Costs

  - Project overhead from buildout and maintenance of abuse-case models

#### Add’l Personnel

  - Security Auditor (2 days/yr)
  - Managers (1 day/yr)
  - Architects (2 days/yr)
  - Business Owners (1 day/yr)

#### Related Levels

  - Threat Assessment - 1 & 3
  - Strategy & Metrics - 1

</div>

<div style="float:left; width:65%;">

## Activities

### A. Build an access control matrix for resources and capabilities

Based upon the business purpose of the application, identify user and
operator roles. Additionally, build a list of resources and capabilities
by gathering all relevant data assets and application-specific features
that are guarded by any form of access control.

In a simple matrix with roles on one axis and resources on the other,
consider the relationships between each role and each resource and note
in each intersection the correct behavior of the system in terms of
access control according to stakeholders.

For data resources, it is important to note access rights in terms of
creation, read access, update, and deletion. For resources that are
features, gradation of access rights will likely be
application-specific, but at a minimum note if the role should be
permitted access to the feature.

This permission matrix will serve as an artifact to document the correct
access control rights for the business logic of the overall system. As
such, it should be created by the project teams with input from business
stakeholders. After initial creation, it should be updated by business
stakeholders before every release, but usually toward the beginning of
the design phase.

### B. Specify security requirements based on known risks

Explicitly review existing artifacts that indicate organization or
project-specific security risk in order to better understand the overall
risk profile for the software. When available, draw on resources such as
the high-level business risk profile, individual application threat
models, findings from design review, code review, security testing, etc.

In addition to review of existing artifacts, use abuse-case models for
an application to serve as fuel for identification of concrete security
requirements that directly or indirectly mitigate the abuse scenarios.

This process should be conducted by business owners and security
auditors as needed. Ultimately, the notion of risks leading to new
security requirements should become a built-in step in the planning
phase whereby newly discovered risks are specifically assessed by
project teams.

</div>

</div>

<div style="float:left; width:100%;">




\----

-----

### Additional Resources

[:Category:SAMM-SR-2](:Category:SAMM-SR-2 "wikilink")

</div>

__NOTOC__ __NOEDITSECTION__

[Category:SAMM-SR-2](Category:SAMM-SR-2 "wikilink")