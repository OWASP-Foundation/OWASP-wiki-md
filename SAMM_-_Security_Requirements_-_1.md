<div style="float:left; width:65%;">

</div>

<div style="float:right; width:30%;">

[<http://www.opensamm.org/downloads/BackButton.png>](http://www.owasp.org/index.php/SAMM_-_Construction)

</div>

<div style="width:100%; float:left;">

<div style="width:30%; float:right; padding-top:50px; padding-left:10px;">

#### Results

  - High-level alignment of development effort with business risks
  - Ad hoc capturing of industry best-practices for security as explicit
    requirements
  - Awareness amongst stakeholders of measures being taken to mitigate
    risk from software

#### Success Metrics

  - \>50% of project teams with explicitly defined security requirements

#### Costs

  - Project overhead from addition of security requirements to each
    development cycle

#### Personnel

  - Security Auditor (2 days/yr)
  - Business Owner (1 days/yr)
  - Managers (1 day/yr)
  - Architects (1 day/yr)

#### Related Levels

  - Education & Guidance - 1
  - Policy & Compliance - 2
  - Design Review - 1
  - Code Review - 1
  - Security Testing - 1

</div>

<div style="float:left; width:65%;">

## Activities

### A. Derive security requirements from business functionality

Conduct a review of functional requirements that specify the business
logic and overall behavior for each software project. After gathering
requirements for a project, conduct an assessment to derive relevant
security requirements. Even if software is being built by a third-party,
these requirements, once identified, should be included with functional
requirements delivered to vendors.

For each functional requirement, a security auditor should lead
stakeholders through the process of explicitly noting any expectations
with regard to security. Typically, questions to clarify for each
requirement include expectations for data security, access control,
transaction integrity, criticality of business function, separation of
duties, uptime, etc.

It is important to ensure that all security requirements follow the same
principles for writing good requirements in general. Specifically, they
should be specific, measurable, and reasonable.

Conduct this process for all new requirements on active projects. For
existing features, it is recommended to conduct the same process as a
gap analysis to fuel future refactoring for security.

### B. Evaluate security and compliance guidance for requirements

Determine industry best-practices that project teams should treat as
requirements. These can be chosen from publicly available guidelines,
internal or external guidelines/standards/policies, or established
compliance requirements.

It is important to not attempt to bring in too many best-practice
requirements into each development iteration since there is a time
trade-off with design and implementation. The recommended approach is to
slowly add best-practices over successive development cycles to bolster
the software’s overall assurance profile over time.

For existing systems, refactoring for security best practices can be a
complex undertaking. Where possible, add security requirements
opportunistically when adding new features. At a minimum, conducting the
analysis to identify applicable best practices should be done to help
fuel future planning efforts.

This review should be performed by a security auditor with input from
business stakeholders. Senior developers, architects, and other
technical stakeholders should also be involved to bring design and
implementation-specific knowledge into the decision process.

</div>

</div>

<div style="float:left; width:100%;">




\----

-----

### Additional Resources

[:Category:SAMM-SR-1](:Category:SAMM-SR-1 "wikilink")

</div>

__NOTOC__ __NOEDITSECTION__

[Category:SAMM-SR-1](Category:SAMM-SR-1 "wikilink")