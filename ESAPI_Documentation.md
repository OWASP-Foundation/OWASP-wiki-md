## Overview

This page documents our current thoughts on the various documents we
need to produce for the ESAPI project, and the audience, purpose, and
high level outline of each document.

## Documentation Plan

Proposed Documents

The following is the set of documentation that is proposed for ESAPI.
This is still a work in progress.

### Smaller Documents

#### ESAPI Executive Overview

`Audience: Executives`
` Purpose: To provide executives with an understanding of:`

  - What ESAPI is? Goals.
  - Why an ESAPI is necessary. (App Sec is
    important/why/standardization)
  - The benefits of using an ESAPI? (Cost, ROI)
  - The current status of ESAPI? (Maturity, Stability, Licensing,
    Support)
  - Who created it, where it came from, credibility, who is using it?
  - How to adopt an ESAPI?

Outline: (See Purpose)

\==== FAQ (For non-users) ====

`Audience: Potential users of ESAPI`
` Purpose: To provide 'quick' hit, information about ESAPI`
`Topics: Summary of main points in the Executive Overview`

#### FAQ (For people using ESAPI)

`Audience (Technical people using ESAPI)`
` Purpose: To provide 'quick' hit information about how to use ESAPI, and add to or integrate ESAPI with existing security controls.`

Outline:

  - How to use it the first time
  - Common usage issues
  - Common extension questions
  - Performance



### Larger Documents

#### Getting Started Guide

`Audience: Developers new to ESAPI`
` Purpose: Explain to these developers how to start immediately using ESAPI`

Outline: (20 pages or less)
\* Overview of ESAPI

  - How to download, install, get dependencies
  - Where is all the documentation/javadoc
  - Where/what is Swingset - where are the coding examples
  - List of the top 5 quick hits you can achieve with ESAPI
  - Concrete examples of how to accomplish each of these 5 things, with
    problem descriptions, example problem code, and example code that
    addresses the problem


\==== How to Secure an Existing Application with ESAPI ====

`Audience: Developers`
` Purpose: Explain to developers how to address most of the common security problems in an existing application using ESAPI`

Outline:
\* Similar to previous, except it goes through all major areas where
ESAPI provides controls, not just the top 5.
\==== How to Use ESAPI in a New Application ====

`Audience: Developers`
`Purpose: Provide application architecture guidance on how to build your applications in a manner that facilitates the use of ESAPI.  `
`Benefit: This should help make it easier to use ESAPI, make your application more secure, easier to analyze, and easier to maintain.`
`Assumption: This assumes that an ESAPI that works in the developers' environment is already available.`

Outline/Topics:

  - Architectural guidance for each control, if any, on how to take most
    facilitate the use of ESAPI in your application
  - e.g., use of DAOs, application organizational considerations wrt
    Access Control, etc.


\==== How to Create a Custom ESAPI for Your Organization ====

`Audience: Organizations and developers that want to use ESAPI`
` Purpose: How to extend or customize ESAPI for your organization or project`

Outline:

  - Overview of related controls, how dependent/independent they are on
    the rest of the API
  - For each control:
      - Expectations for 'as is' use, extension, replacement of this
        control
      - How to extend this control
      - How to replace this control

Goals: All of this content would be on the wiki, and PDFs of each of
these 'may' be produced as well.

### Non-Documents

#### Javadoc

  - Review/Update all Javadoc to make sure its complete, accurate, and
    properly extends javadoc from other classes
  - Make sure all parameters are documented as well as return values

Status: This was done in the Spring of 2009 but probably deserves a
refresh at this point.

### Web Pages

  - Revamp the ESAPI Website (lots of details needed on this)
  - How will ESAPI be updated and released.
  - Features Roadmap
  - Where to get ESAPI source and libraries - a list of language
    specific libraries is here:
    <http://www.owasp.org/index.php/Category:OWASP_Enterprise_Security_API#tab=Downloads>
  - How to build ESAPI from source - See:
    <http://www.owasp.org/index.php/ESAPI-Building> and:
    <http://www.owasp.org/index.php/ESAPI-BuildingWithEclipse>
  - How to integrate ESAPI into your project
  - How to contribute to ESAPI



### Other Documents

  - ESAPI Architecture/Design Guideline
  - Assurance Argument [ESAPI_Assurance](ESAPI_Assurance "wikilink")