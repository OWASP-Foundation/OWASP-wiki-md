If you are performing an application security verification according to
the [OWASP Application Security Verification Standard
(ASVS)](::Category:OWASP_Application_Security_Verification_Standard_Project "wikilink")
verification requirements, then you will need to perform an analysis of
the application’s security architecture. The ASVS Level 1 security
architecture requirements read in part:

*“... the web application can be defined by simply listing its
components. Components may be defined in terms of either individual or
groups of source files, libraries, and/or executables... the list need
not be sorted or otherwise organized; the web application can be treated
as groups of components within a single monolithic entity...”*

The level of detail, and corresponding depth and breadth of analysis, is
the same for ASVS Levels 1, 1A, and 1B.

A recommended first step is to draw a network-level picture that
identifies which physical servers your application components are
located on, and servers where none of your application components are
located, as depicted in the figure below

![Image:Asvs_network.gif](Asvs_network.gif "Image:Asvs_network.gif")

The above requirements can then be met by simply listing web application
and IT environment components, as described in the ASVS article [How to
meet verification reporting
requirements](How_to_meet_verification_reporting_requirements "wikilink"):

`   The Target of Verification (TOV) can be described in`
`   terms of the following components:`
`     `
`       *`<application component name>` – <1-2 sentence `
`       description>`
`   `
`       *`<application component name>` – <1-2 sentence `
`       description>`
`   `
`       *`<application component name>` – <1-2 sentence `
`       description>`
`   `
`   The intended environment of the TOV can be described in `
`   terms of the following components:`
`         `
`       *`<environment component name>` – <1-2 sentence `
`       description>`
`   `
`       *`<environment component name>` – <1-2 sentence `
`       description>`
`   `
`       *`<environment component name>` – <1-2 sentence `
`       description>`

Helpful hints:

  - Examples of IT environment components are application servers and
    operating systems.
  - In most instances, also identifying subcomponents for each TOV
    component will be helpful and/or necessary if for example counting
    LOC to determine (more to the point: to reduce) code review tool
    license fees.
      - E.g. "authentication module subcomponent" - this would likely be
        included in a review
      - E.g. "management subcomponent" - this would likely be included
        in a review
      - E.g. "<open source server> <user function>-related subcomponents
        that were not modified" - this MAY NOT be included in a review
      - E.g. "<open source server> <user function>-related subcomponents
        that were modified" - this would likely be included in a review

[Category:OWASP Application Security Verification Standard
Project](Category:OWASP_Application_Security_Verification_Standard_Project "wikilink")
[Category:How To](Category:How_To "wikilink")