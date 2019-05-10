<div style="float:left; width:65%;">

</div>

<div style="float:right; width:30%;">

[<http://www.opensamm.org/downloads/BackButton.png>](http://www.owasp.org/index.php/SAMM_-_Construction)

</div>

<div style="width:100%; float:left;">

<div style="width:30%; float:right; padding-top:50px; padding-left:10px;">

#### Results

  - Detailed mapping of assets to user roles to encourage better
    compartmentalization in design
  - Reusable design building blocks for provision of security
    protections and functionality
  - Increased confidence for software projects from use of established
    design techniques for security

#### Add’l Success Metrics

  - \>80% of projects with updated permission matrix in past 6 months
  - \>80% of project teams briefed on applicable security patterns in
    past 6 months

#### Add’l Costs

  - Buildout or license of applicable security patterns
  - Ongoing project overhead from maintenance of permission matrix

#### Add’l Personnel

  - Architects (2-4 days/yr)
  - Developers (1-2 days/yr)
  - Managers (1-2 days/yr)
  - Business Owners (1 day/yr)
  - Security Auditors (1-2 days/yr)

#### Related Levels

  - Education & Guidance - 1

</div>

<div style="float:left; width:65%;">

## Activities

### A. Identify and promote security services and infrastructure

Organizations should identify shared infrastructure or services with
security functionality. These will typically include single-sign-on
services, corporate directory systems, access control or entitlements
services, and authentication systems. By collecting and evaluating
reusable systems, assemble a list of such resources and categorize them
by the security mechanism they fulfill. It is also helpful to consider
each resource in terms of why a development team would want to integrate
with it, i.e. the benefits of using the shared resource.

If multiple resources exist in each category, an organization should
select and standardize on one or more shared service per category.
Because future software development will rely on these selected
services, each should be thoroughly audited to ensure the baseline
security posture is understood. For each selected service, design
guidance should be created for development teams to understand how to
integrate with the system. After such guidance is assembled, it should
be made available to development teams through training, mentorship,
guidelines, and standards.

The benefits of doing this include promotion of known-secure systems,
simplified security guidance for project design teams, and clearer paths
to building assurance around the applications utilizing the shared
security services.

### B. Identify security design patterns from architecture

Across software projects at an organization, each should be categorized
in terms of the generic architecture type. Common categories include
client-server applications, embedded systems, desktop applications,
web-facing applications, web services platforms, transactional
middleware systems, mainframe applications, etc. Depending on your
organizations specialty, more detailed categories may need to be
developed based upon language, or processor architecture, or even era of
deployment.

For the generic software architecture type, a set of general design
patterns representing sound methods of implementing security
functionality can be derived and applied to the individual designs of an
organization’s software projects. These security design patterns
represent general definitions of generic design elements they can be
researched or purchased, and it is often even more effective if these
patterns are customized to be made more specific to your organization.
Example patterns include a single-sign-on subsystem, a cross-tier
delegation model, a hardened interface design, separation-of-duties
authorization model, a centralized logging pattern, etc.

The process of identification of applicable and appropriate patterns
should be carried out by architects, senior developers, and other
technical stakeholders during the design phase.

</div>

</div>

<div style="float:left; width:100%;">




\----

-----

### Additional Resources

[:Category:SAMM-SA-2](:Category:SAMM-SA-2 "wikilink")

</div>

__NOTOC__ __NOEDITSECTION__

[Category:SAMM-SA-2](Category:SAMM-SA-2 "wikilink")