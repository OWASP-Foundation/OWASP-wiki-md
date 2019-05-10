<table>
<thead>
<tr class="header">
<th><p>width="700" align="center"</p></th>
<th><p><br />
</p></th>
<th><p>width="500" align="center"</p></th>
<th><p><br />
</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>align="right"</p></td>
<td><figure>
<img src="OWASP_Inactive_Banner.jpg" title="OWASP_Inactive_Banner.jpg" alt="OWASP_Inactive_Banner.jpg" width="800" /><figcaption>OWASP_Inactive_Banner.jpg</figcaption>
</figure></td>
<td><p>align="right"</p></td>
<td></td>
</tr>
</tbody>
</table>

# GCP Project Overview

This project documents a set of best practices for managing component
vulnerability within enterprise applications. Fundamentally, we are
concerned with usage throughout the entire process, from the time a
component is selected for inclusion within the application through its
deployment and maintenance within the production environment.

The underlying premise of this project is that the application itself
should be part of the assurance process. Application self assurance
needs to ensure that the "things" being placed into the system are not
introducing new risks. Automated vulnerability discovery must be part of
any continuous delivery process. If self-assurance and automated
monitoring are not integrated into the development and production
environment, it is virtually impossible to assure the security of the
system.

In this project, we will examine three gateways of component
vulnerability and establish a series of best practices for managing
component security. The output of the project will be a set of best
practices for managing and monitoring open source components as part of
the complete component life cycle.

[Mark Miller](User:Mark_Miller "wikilink") 14:59, 26 April 2013 (UTC)

# Gateways of Component Vulnerability

There are three gateways at which a vulnerable component may be included
within an application: Selection/Consumption, Integration, Deployment.
Each of these gateways must be policed and monitored to block, eliminate
or manage vulnerable components. In this section, we describe the three
gateways.

## **Consumption**: Selection of the components and where they came from (provenance)

The first gateway of entrance to monitor for risk management is
provenance - where does the componenent come from from. There are three
levels of risk to examine at first gateway:

`  -- Licensing`
`  -- Security`
`  -- Quality`

There must be a way to verify that the component downloaded is actually
the component selected.

Once the component has crossed through the first gate, it becomes part
of the development environment with other risk types

## **Integration**: Component management within the development environment

Is the component I'm using actually what I have downloaded. How do I
know that what I originally said was "ok" is actually what is being
used? A simplified scenario for a downloaded file is:

> I download a file and virus scan it on my machine.
> The virus scan says it is clean so I put it in my local file
> directory.
> At some later point in time, I use the file that I downloaded.
> How do I insure that the thing that I downloaded is still what I
> thought it was?
> How do I know the name wasn't changed, or the contents of the file
> haven't been altered?

The same is true for components. What kind of assurance can be made that
the component has not been altered once it enters into the development
environment.

## **Deployment**: Component maintenance within the production environment

When the component moves into production, how do I ensure that what is
actually running is the same thing that the developer thought it was.
How do I ensure that all along the path from selection through
deployment, that the component is actually what I think it is. How do I
verify that nothing has changed.

The gateways where risk can get introduced are the main points for
automated monitoring and enforcement of policies and procedures. If I do
all that great work up front, (this is validate, confirm integration
with my current environment, etc,) then I need to ensure that that the
component that was approved doesn't get invalidated by misconfiguration
or manual change of version numbers to work around company policies.

Validation must be done through ever step in the supply chain to confirm
that the component in use is what it says it is and hasn't been changed
during the process.

[Mark Miller](User:Mark_Miller "wikilink") 22:04, 24 April 2013 (UTC)

# Outline for Good Component Practices

(Rough outline: need details with downloadable check sheet)

## Component Selection

  - Set standards and policy for component usage
  - Identify components needed

## Integration into Development Environment

  - Verify company compliance policies

## Integration and Maintenance within Production Environment

  - Automated inventory of existing components, libraries and frameworks
  - Monitor usage of deployed components
  - Update risky components
  - Move beyond penetration testing to find vulnerable components

# Detailed Framework for Good Component Practices

## Component Selection

(Rough outline: need details with downloadable check sheet)

  - Set standards and policy for component usage
      - Components must be actively maintained
      - Component projects must have a security contact and security
        announcement list
      - Component projects must use security tools and make the results
        public
      - Component projects must have a history of responding to security
        vulnerability reports in a timely manner
      - Component binaries must be generated directly from project
        source code using trusted tools
      - Components with known vulnerabilities must be removed or updated
        within 1 month of vulnerability announcement

## Integration into Development Environment

## Integration and Maintenance within Production Environment

# Project About

[Category:OWASP Project](Category:OWASP_Project "wikilink")