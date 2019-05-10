<div style="float:left; width:65%;">

</div>

<div style="float:right; width:30%;">

[<http://www.opensamm.org/downloads/BackButton.png>](http://www.owasp.org/index.php/SAMM_-_Deployment)

</div>

<div style="width:100%; float:left;">

<div style="width:30%; float:right; padding-top:50px; padding-left:10px;">

#### Results

  - Detailed guidance for security-relevant changes delivered with
    software releases
  - Updated information repository on secure operating procedures per
    application
  - Alignment of operations expectations among developers, operators,
    and users.

#### Add’l Success Metrics

  - \>50% of projects with updated change management procedures in past
    6 months
  - \>80% of stakeholders briefed on status of operational security
    guides in past 6 months

#### Add’l Costs

  - Ongoing project overhead from maintenance of change management
    procedures
  - Ongoing project overhead from maintenance of operational security
    guides

#### Add’l Personnel

  - Developers (1-2 days/yr)
  - Architects (1-2 days/yr)
  - Managers (1 days/yr)
  - Support/Operators (1 days/yr)

#### Related Levels

  - Environment Hardening - 1

</div>

<div style="float:left; width:65%;">

## Activities

### A. Create per-release change management procedures

To more formally update users and operators on relevant changes in the
software, each release must include change management procedures
relevant to upgrade and first-time installation. Overall, the goal is to
capture the expected accompanying steps that ensure the deployment will
be successful and not incur excessive downtime or degradation of
security posture.

To build these procedures during development, the project teams should
setup a lightweight internal process for capturing relevant items that
would impact deployments. It is effective to have this process in place
early in the development cycle so that this information can be retained
as soon as it is identified while in the requirements, design, and
implementation phases.

Before each release, the project team should review the list as a whole
for completeness and feasibility. For some projects, extensive change
procedures accompanying a given release may warrant special handling,
such as building automated upgrade scripts to prevent errors during
deployment.

### B. Maintain formal operational security guides

Starting from the information captured on critical software events and
the procedures for handling each, project teams should build and
maintain formal guides that capture all the security-relevant
information that users and operators need to know.

Initially, this guide should be built from the known information about
the system, such as security-related configuration options, event
handling procedures, installation and upgrade guides, operational
environment specifications, security-related assumptions about the
deployment environment, etc. Extending this, the formal operational
security guide should elaborate on each of these to cover more details
such that the majority of the users and operators will be informed for
all the questions they might have had. For large or complex systems,
this can be challenging, so project teams should work with business
stakeholders to determine the appropriate level of documentation.
Additionally, project teams should document any recommendations for
deployments that would enhance security.

The operational security guide, after initial creation, should be
reviewed by project teams and updated with each release.

</div>

</div>

<div style="float:left; width:100%;">




\----

-----

### Additional Resources

[:Category:SAMM-OE-2](:Category:SAMM-OE-2 "wikilink")

</div>

__NOTOC__ __NOEDITSECTION__

[Category:SAMM-OE-2](Category:SAMM-OE-2 "wikilink")