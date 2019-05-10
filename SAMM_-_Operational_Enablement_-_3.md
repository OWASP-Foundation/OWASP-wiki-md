<div style="float:left; width:65%;">

</div>

<div style="float:right; width:30%;">

[<http://www.opensamm.org/downloads/BackButton.png>](http://www.owasp.org/index.php/SAMM_-_Deployment)

</div>

<div style="width:100%; float:left;">

<div style="width:30%; float:right; padding-top:50px; padding-left:10px;">

#### Results

  - Organization-wide understanding of expectations for
    security-relevant documentation
  - Stakeholders better able to make tradeoff decisions based on
    feedback from deployment and operations
  - Operators and/or users able to independently verify integrity of
    software releases

#### Add’l Success Metrics

  - \>80% of projects with updated operational security guide in last 6
    months
  - \>80% of stakeholders briefed on code signing options and status in
    past 6 months

#### Add’l Costs

  - Ongoing project overhead from audit of operational guides
  - Ongoing organization overhead from management of code signing
    credentials
  - Ongoing project overhead from identification and signing of code
    modules.

#### Add’l Personnel

  - Developers (1 days/yr)
  - Architects (1 days/yr)
  - Managers (1 days/yr)
  - Security Auditors (1-2 days/yr)

#### Related Levels

</div>

<div style="float:left; width:65%;">

## Activities

### A. Expand audit program for operational information

When conducting routine project-level audits, expand the review to
include inspection of artifacts related to operational enablement for
security. Projects should be checked to ensure they have an updated and
complete operational security guides as relevant to the specifics of the
software.

These audits should begin toward the end of the development cycle close
to release, but must be completed and passed before a release can be
made. For legacy systems or inactive projects, this type of audit should
be conducted and a one-time effort should be made to address findings
and verify audit compliance, after which additional audits for
operational enablement are no longer required.

Audit results must be reviewed with business stakeholders prior to
release. An exception process should be created to allow projects
failing an audit to continue with a release, but these projects should
have a concrete timeline for mitigation of findings. Exceptions should
be limited to no more that 20% of all active projects.

### B. Perform code signing for application components

Though often used with special-purpose software, code signing allows
users and operators to perform integrity checks on software such that
they can cryptographically verify the authenticity of a module or
release. By signing software modules, the project team enables
deployments to operate with a greater degree of assurance against any
corruption or modification of the deployed software in its operating
environment.

Signing code incurs overhead for management of signing credentials for
the organization. An organization must follow safe key management
processes to ensure the ongoing confidentiality of the signing keys.
When dealing with any cryptographic keys, project stakeholders must also
consider plans for dealing with common operational problems related to
cryptography such as key rotation, key compromise, or key loss.

Since code signing is not appropriate for everything, architects and
developers should work with security auditors and business stakeholders
to determine which parts of the software should be signed. As projects
evolve, this list should be reviewed with each release, especially when
adding new modules or making changes to previously signed components.

</div>

</div>

<div style="float:left; width:100%;">




\----

-----

### Additional Resources

[:Category:SAMM-OE-3](:Category:SAMM-OE-3 "wikilink")

</div>

__NOTOC__ __NOEDITSECTION__

[Category:SAMM-OE-3](Category:SAMM-OE-3 "wikilink")