<div style="float:left; width:65%;">

</div>

<div style="float:right; width:30%;">

[<http://www.opensamm.org/downloads/BackButton.png>](http://www.owasp.org/index.php/SAMM_-_Deployment)

</div>

<div style="width:100%; float:left;">

<div style="width:30%; float:right; padding-top:50px; padding-left:10px;">

#### Results

  - Granular verification of security characteristics of systems in
    operations
  - Formal expectations on timelines for infrastructure risk mitigation
  - Stakeholders consistently aware of current operations status of
    software projects

#### Add’l Success Metrics

  - \>80% of project teams briefed on patch management process in past
    12 months
  - \>80% of stakeholders aware of current patch status in past 6 months

#### Add’l Costs

  - Ongoing organization overhead from patch management and monitoring
  - Buildout or license of infrastructure monitoring tools

#### Add’l Personnel

  - Architects (1-2 days/yr)
  - Developers (1-2 days/yr)
  - Business Owners (1-2 days/yr)
  - Managers (1-2 days/yr)
  - Support/Operators (3-4 days/yr)

#### Related Levels

</div>

<div style="float:left; width:65%;">

## Activities

### A. Establish routine patch management process

Moving to a more formal process than ad hoc application of critical
upgrades and patches, an ongoing process should be created in the
organization to consistently apply updates to software dependencies in
the operating environment.

In the most basic form, the process should aim to make guarantees for
time lapse between release and application of security upgrades and
patches. To make this process efficient, organizations typically accept
high latency on lower priority updates, e.g. maximum of 2 days for
critical patches spanning to a maximum of 30 days for low priority
patches.

This activity should be primarily conducted by support and operations
staff, but routine meetings with development should also be conducted to
keep the whole project abreast of past changes and scheduled upgrades.

Additionally, development staff should share a list of third-party
components upon which the software project internally depends so that
support and operations staff can monitor those as well to cue
development teams on when an upgrade is required.

### B. Monitor baseline environment configuration status

Given the complexity of monitoring and managing patches alone across the
variety of components composing the infrastructure for a software
project, automation tools should be utilized to automatically monitor
systems for soundness of configuration.

There are both commercial and open-source tools available to provide
this type of functionality, so project teams should select a solution
based on appropriateness to the organization’s needs. Typical selection
criteria includes ease of deployment and customization, applicability to
the organization’s platforms and technology stacks, built-in features
for change management and alerting, metrics collection and trend
tracking etc.

In addition to host and platform checks, monitoring automation should be
customized to perform application-specific health checks and
configuration verifications. Support and operations personnel should
work with architects and developers to determine the optimal amount of
monitoring for a given software project.

Ultimately, after a solution is deployed for monitoring the
environment’s configuration status, unexpected alerts or configuration
changes should be collected and regularly reviewed by project
stakeholders as often as weekly but at least once per quarter.

</div>

</div>

<div style="float:left; width:100%;">




\----

-----

### Additional Resources

[:Category:SAMM-EH-2](:Category:SAMM-EH-2 "wikilink")

</div>

__NOTOC__ __NOEDITSECTION__

[Category:SAMM-EH-2](Category:SAMM-EH-2 "wikilink")