<div style="float:left; width:65%;">

</div>

<div style="float:right; width:30%;">

[<http://www.opensamm.org/downloads/BackButton.png>](http://www.owasp.org/index.php/SAMM_-_Deployment)

</div>

<div style="width:100%; float:left;">

<div style="width:30%; float:right; padding-top:50px; padding-left:10px;">

#### Results

  - Clear understanding of operational expectations within the
    development team
  - High-priority risks from underlying infrastructure mitigated on a
    well-understood timeline
  - Software operators with a high-level plan for security-critical
    maintenance of infrastructure

#### Success Metrics

  - \>50% project with updated operational environment specification in
    past 6 months
  - \>50% of projects with updated list of relevant critical security
    patches in past 6 months

#### Costs

  - Ongoing project overhead from buildout and maintenance of
    operational environment specification
  - Ongoing project overhead from monitoring and installing critical
    security updates

#### Personnel

  - Developers (1-2 day/yr)
  - Architects (1-2 day/yr)
  - Managers (2-4 day/yr)
  - Support/Operators (3-4 days/yr)

#### Related Levels

  - Operational Enablement - 2

</div>

<div style="float:left; width:65%;">

## Activities

### A. Maintain operational environment specification

For each project, a concrete definition of the expected operating
platforms should be created and maintained. Depending on the
organization, this specification should be jointly created with
development staff, stakeholders, support and operations groups, etc.

Begin this specification should by capturing all details that must be
true about the operating environment based upon the business function of
the software. These can include factors such as processor architecture,
operating system versions, prerequisite software, conflicting software,
etc. Further, note any known user or operator configurable options about
the operating environment that affect the way in which the software will
behave.

Additionally, identify any relevant assumptions about the operating
environment that were made in design and implementation of the project
and capture those assumptions in the specification.

This specification should be reviewed and updated at least every 6
months for active projects or more often if changes are being made to
the software design or the expected operating environment.

### B. Identify and install critical security upgrades and patches

Most applications are software that runs on top of another large stack
of software composed of built-in programming language libraries,
third-party components and development frameworks, base operating
systems, etc. Because security flaws contained in any module in that
large software stack affect the overall security of the organization’s
software, critical security updates for elements of the technology stack
must be installed.

As such, regular research or ongoing monitoring of high-risk
dependencies should be performed to stay abreast of the latest fixes to
security flaws. Upon identification of a critical upgrade or patch that
would impact the security posture of the software project, plans should
be made to get affected users and operators to update their
installations. Depending on the type of software project, details on
doing this can vary.

</div>

</div>

<div style="float:left; width:100%;">




\----

-----

### Additional Resources

[:Category:SAMM-EH-1](:Category:SAMM-EH-1 "wikilink")

</div>

__NOTOC__ __NOEDITSECTION__

[Category:SAMM-EH-1](Category:SAMM-EH-1 "wikilink")