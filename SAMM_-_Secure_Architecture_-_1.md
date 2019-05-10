<div style="float:left; width:65%;">

</div>

<div style="float:right; width:30%;">

[<http://www.opensamm.org/downloads/BackButton.png>](http://www.owasp.org/index.php/SAMM_-_Construction)

</div>

<div style="width:100%; float:left;">

<div style="width:30%; float:right; padding-top:50px; padding-left:10px;">

#### Results

  - Ad hoc prevention of unexpected dependencies and one-off
    implementation choices
  - Stakeholders aware of increased project risk due to libraries and
    frameworks chosen
  - Established protocol within development for proactively applying
    security mechanisms to a design

#### Success Metrics

  - \>80% of development staff briefed on software framework
    recommendations in past 1 year
  - \>50% of projects self-reporting application of security principles
    to design

#### Costs

  - Buildout, maintenance, and awareness of software framework
    recommendations
  - Ongoing project overhead from analysis and application of security
    principles

#### Personnel

  - Architects (2-4 days/yr)
  - Developers (2-4 days/yr)
  - Security Auditors (2-4 days/yr)
  - Managers (2 days/yr)

#### Related Levels

  - Education & Guidance - 1

</div>

<div style="float:left; width:65%;">

## Activities

### A. Maintain list of recommended software frameworks

Across software projects within the organization identify commonly used
third-party software libraries and frameworks in use. Generally, this
need not be an exhaustive search for dependencies, but rather focus on
capturing the high-level components that are most often used.

From the list of components, group them into functional categories based
on the core features provided by the third-party component. Also, note
the usage prevalence of each component across project teams to weight
the reliance upon the third-party code. Using this weighted list as a
guide, create a list of components to be advertised across the
development organization as recommended components.

Several factors should contribute to decisions for inclusion on the
recommended list. Although a list can be created without conducting
research specifically, it is advisable to inspect each for incident
history, track record for responding to vulnerabilities, appropriateness
of functionality for the organization, excessive complexity in usage of
the third-party component, etc.

This list should be created by senior developers and architects, but
also include input from managers and security auditors. After creation,
this list of recommended components matched against functional
categories should be advertised to the development organization.
Ultimately, the goal is to provide well-known defaults for project
teams.

### B. Explicitly apply security principles to design

During design, technical staff on the project team should use a short
list of guiding security principles as a checklist against detailed
system designs. Typically, security principles include defense in depth,
securing the weakest link, use of secure defaults, simplicity in design
of security functionality, secure failure, balance of security and
usability, running with least privilege, avoidance of security by
obscurity, etc.

In particular for perimeter interfaces, the design team should consider
each principle in the context of the overall system and identify
features that can be added to bolster security at each such interface.
Generally, these should be limited such that they only take a small
amount of extra effort beyond the normal implementation cost of
functional requirements and anything larger should be noted and
scheduled for future releases.

While this process should be conducted by each project team after being
trained with security awareness, it is helpful to incorporate more
security-savvy staff to aide in making design decisions.

</div>

</div>

<div style="float:left; width:100%;">




\----

-----

### Additional Resources

[:Category:SAMM-SA-1](:Category:SAMM-SA-1 "wikilink")

</div>

__NOTOC__ __NOEDITSECTION__

[Category:SAMM-SA-1](Category:SAMM-SA-1 "wikilink")