<div style="float:left; width:65%;">

</div>

<div style="float:right; width:30%;">

[<http://www.opensamm.org/downloads/BackButton.png>](http://www.owasp.org/index.php/SAMM_-_Verification)

</div>

<div style="width:100%; float:left;">

<div style="width:30%; float:right; padding-top:50px; padding-left:10px;">

#### Results

  - High-level understanding of security implications from perimeter
    architecture
  - Enable development teams to self-check designs for security
    best-practices
  - Lightweight process for conducting project-level design reviews

#### Success Metrics

  - \>50% of projects with updated attack surface analysis in past 12
    months
  - \>50% of projects with updated security requirements design-level
    analysis in past 12 months

#### Costs

  - Buildout and maintenance of architecture diagrams for each project
  - Ongoing project overhead from attack surface and security
    requirement design inspection

#### Personnel

  - Architects (2-3 days/yr)
  - Developers (1-2 days/yr)
  - Managers (1 day/yr)
  - Security Auditor (1 day/yr)

#### Related Levels

  - Security Requirements - 1

</div>

<div style="float:left; width:65%;">

## Activities

### A. Identify software attack surface

For each software project, create a simplified view of the overall
architecture. Typically, this should be created based on project
artifacts such as high-level requirements and design documents,
interviews with technical staff, or module-level review of the code
base. It is important to capture the high-level modules in the system,
but a good rule of thumb for granularity is to ensure that the diagram
of the whole system under review fits onto one page.

From the single page architecture view, analyze each component in terms
of accessibility of the interfaces from authorized users, anonymous
users, operators, application-specific roles, etc. The components
providing the interfaces should also be considered in the context of the
one-page view to find points of functional delegation or data
pass-through to other components on the diagram. Group interfaces and
components with similar accessibility profiles and capture this as the
software attack surface.

For each interface, further elaborate the one-page diagram to note any
security-related functionality. Based on the identified interface groups
comprising the attack surface, check the model for design-level
consistency for how interfaces with similar access are secured. Any
breaks in consistency can be noted as assessment findings

This analysis should be conducted by security-savvy technical staff,
either within the project team or external. Typically, after initial
creation, the diagram and attack surface analysis only needs to be
updated during the design phase when additions or changes are made to
the edge system interfaces.

### B. Analyze design against known security requirements

Security requirements, either formally identified or informally known,
should be identified and collected. Additionally, identify and include
any security assumptions upon which safe operation of the system relies.

Review each item on the list of known security requirements against the
one-page diagram of the system architecture. Elaborate the diagram to
show the design-level features that address each security requirement.
Separate, granular diagrams can be created to simplify capturing this
information if the system is large and/or complex. The overall goal is
to verify that each known security requirement has been addressed by the
system design. Any security requirements that are not clearly provided
at the design level should be noted as assessment findings.

This analysis should be conducted by security-savvy technical staff with
input from architects, developers, managers, and business owners as
needed. It should be updated during the design phase when there are
changes in security requirements or high-level system design.

</div>

</div>

<div style="float:left; width:100%;">




\----

-----

### Additional Resources

[:Category:SAMM-DR-1](:Category:SAMM-DR-1 "wikilink")

</div>

__NOTOC__ __NOEDITSECTION__

[Category:SAMM-DR-1](Category:SAMM-DR-1 "wikilink")