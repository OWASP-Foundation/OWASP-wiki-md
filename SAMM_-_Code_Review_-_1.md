<div style="float:left; width:65%;">

</div>

<div style="float:right; width:30%;">

[<http://www.opensamm.org/downloads/BackButton.png>](http://www.owasp.org/index.php/SAMM_-_Verification)

</div>

<div style="width:100%; float:left;">

<div style="width:30%; float:right; padding-top:50px; padding-left:10px;">

#### Results

  - Inspection for common code vulnerabilities that lead to likely
    discovery or attack
  - Lightweight review for coding errors that lead to severe security
    impact
  - Basic code-level due diligence for security assurance

#### Success Metrics

  - \>80% of project teams briefed on relevant code review checklists in
    past 6 months
  - \>50% of project teams performing code review on high-risk code in
    past 6 months
  - \>3.0 Likert on usefulness of code review checklists reported by
    developers

#### Costs

  - Buildout or license of code review checklists
  - Ongoing project overhead from code review activities of high-risk
    code

#### Personnel

  - Developers (2-4 days/yr)
  - Architects (1-2 days/yr)
  - Managers (1-2 days/yr)
  - Business Owners (1 day/yr)

#### Related Levels

  - Security Requirements - 1

</div>

<div style="float:left; width:65%;">

## Activities

### A. Create review checklists from known security requirements

From the known security requirements for a project, derive a lightweight
code review checklist for security. These can be checks specific to the
security concerns surrounding the functional requirements or checks for
secure coding best practices based on the implementation language,
platform, typical technology stack, etc. Due to these variations, often
a set of checklist are needed to cover the different types of software
development within an organization.

Regardless, of whether created from publicly available resources or
purchased, technical stakeholders such as development managers,
architects, developers, and security auditors should review the
checklists for efficacy and feasibility. It is important to keep the
lists short and simple, aiming to catch high-priority issues that are
straightforward to find in code either manually or with simple search
tools. Code analysis automation tools may also be used to achieve this
same end, but should also be customized to reduce the overall set of
security checks to a small, valuable set in order to make the scan and
review process efficient.

Developers should be briefed on the goals of checklists appropriate to
their job function.

### B. Perform point-review of high-risk code

Since code-level vulnerabilities can have dramatically increased impacts
if they occur in security-critical parts of software, project teams
should review high-risk modules for common vulnerabilities. Common
examples of high-risk functionality include authentication modules,
access control enforcement points, session management schemes, external
interfaces, input validators and data parsers, etc.

Utilizing the code review checklists, the analysis can be performed as a
normal part of the development process where members of the project team
are assigned modules to review when changes are made. Security auditors
and automated review tools can also be utilized for the review.

During development cycles where high-risk code is being changed and
reviewed, development managers should triage the findings and prioritize
remediation appropriately with input from other project stakeholders.

</div>

</div>

<div style="float:left; width:100%;">




\----

-----

### Additional Resources

[:Category:SAMM-CR-1](:Category:SAMM-CR-1 "wikilink")

</div>

__NOTOC__ __NOEDITSECTION__

[Category:SAMM-CR-1](Category:SAMM-CR-1 "wikilink")