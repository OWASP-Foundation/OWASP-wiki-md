<div style="float:left; width:65%;">

</div>

<div style="float:right; width:30%;">

[<http://www.opensamm.org/downloads/BackButton.png>](http://www.owasp.org/index.php/SAMM_-_Construction)

</div>

<div style="width:100%; float:left;">

<div style="width:30%; float:right; padding-top:50px; padding-left:10px;">

#### Results

  - Customized application development platforms that provide built-in
    security protections
  - Organization-wide expectations for proactive security effort in
    development
  - Stakeholders better able to make tradeoff decisions based on
    business need for secure design

#### Add’l Success Metrics

  - \>50% of active projects using reference platforms
  - \>80% of projects reporting framework, pattern, and platform usage
    feedback in past 6 months
  - \>3.0 Likert on usefulness of guidance/platforms reported by project
    teams

#### Add’l Costs

  - Buildout or license of reference platform(s)
  - Ongoing maintenance and support of reference platforms
  - Ongoing project overhead from usage validation during audit

#### Add’l Personnel

  - Managers (1 day/yr)
  - Business Owners (1 day/yr)
  - Architects (3-4 days/yr)
  - Developers (2-3 days/yr)
  - Security Auditors (2 days/yr)

#### Related Levels

  - Policy & Compliance - 2
  - Design Review - 3
  - Code Review - 3
  - Security Testing - 3

</div>

<div style="float:left; width:65%;">

## Activities

### A. Establish formal reference architectures and platforms

After promoting integration with shared security services and working
with security patterns specific to each type of architecture, a
collection of code implementing these pieces of functionality should be
selected from project teams and used as the basis for a shared
code-base. This shared code-base can initially start as a collection of
commonly recommended libraries that each project needs to use and it can
grow over time into one or more software frameworks representing
reference platforms upon which project teams build their software.
Examples of reference platforms include frameworks for
model-view-controller web applications, libraries supporting
transactional back-end systems, frameworks for web services platforms,
scaffolding for client-server applications, frameworks for middle-ware
with pluggable business logic, etc.

Another method of building initial reference platforms is to select a
particular project early in the life-cycle and have security-savvy staff
work with them to build the security functionality in a generic way so
that it could be extracted from the project and utilized elsewhere in
the organization.

Regardless of approach to creation, reference platforms have advantages
in terms of speeding audit and security-related reviews, increasing
efficiency in development, and lowering maintenance overhead.

Architects, senior developers and other technical stakeholders should
participate in design and creation of reference platforms. After
creation, a team must maintain ongoing support and updates.

### B. Validate usage of frameworks, patterns, and platforms

During routine audits of projects conduct additional analysis of project
artifacts to measure usage of recommended frameworks, design patterns,
shared security services, and reference platforms. Though conducted
during routine audits, the goal of this activity is to collect feedback
from project teams as much as to measure their individual proactive
security effort.

Overall, it is important to verify several factors with project teams.
Identify use of non-recommended frameworks to determine if there may be
a gap in recommendations versus the organization’s functionality needs.
Examine unused or incorrectly used design patterns and reference
platform modules to determine if updates are needed. Additionally, there
may be more or different functionality that project teams would like to
see implemented in the reference platforms as the organization evolves.

This analysis can be conducted by any security-savvy technical staff.
Metrics collected from each project should be collated for analysis by
managers and stakeholders.

</div>

</div>

<div style="float:left; width:100%;">




\----

-----

### Additional Resources

[:Category:SAMM-SA-3](:Category:SAMM-SA-3 "wikilink")

</div>

__NOTOC__ __NOEDITSECTION__

[Category:SAMM-SA-3](Category:SAMM-SA-3 "wikilink")