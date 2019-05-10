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

#### Main

# Overview

The project was initially inspired by the input validation framework
Heimdall [1](http://portal.acm.org/citation.cfm?id=1250584), where the
main goal is to provide a clear separation between validation and
application logic. This separation was achieved by using an XML
configuration file defining which tests were to be run on which object
properties.

The first step of our project consisted in checking whether the need for
an XML external file could be eliminated by using annotations to
associate tests and object properties, instead.

After a new input validation framework based on annotations was
succesfully implemented, the focus of the project shifted to investigate
how far annotations can be pushed for validation purpouses, while
keeping their use as intuitive and simple as possible.

At the moment we defined and implemented:

  - *composed* annotations: which allow the user to compose existing
    annotations in a boolean fashion to create new tests without the
    need of writing new code.
  - *cross* annotations: which allow the user to define tests on
    multiple object properties, rather than just single ones, which have
    inter-dependent validation constraints.

Other main features that characterize the framework are:

  - Easy integration in any esisting Java projects
  - High reusability of existing validation tests
  - Possibility of creating new custom annotations with little effort

A slide presentation is available here
[PDF](http://www.ii.uib.no/~dagh/validatorflyer.pdf) while a full
technical report can be downloaded here
[PDF](http://www.ii.uib.no/publikasjoner/texrap/pdf/2009-389.pdf)

# Project Goals

The final goal of the project is to create a framework for input
validation based on annotations, which is easy to use and will help
integrate this aspect of security into both new and existing
applications.

Th current goals are:

  - Continuously improving the framework with frequent releases
  - Extend the library of predefined annotations
  - Create an Eclipse plug-in to simplify the creation of custom
    annotations and help their insertion in the application code
  - Investigate further uses of annotations for input validation
  - Improve both the documentation
  - Implement a better summary for the validation results, that can
    contain custom error messages and that is easy to query by the user

# Main Links

Full technical report [TECHNICAL
DOCUMENTATION](http://www.ii.uib.no/publikasjoner/texrap/pdf/2009-389.pdf)

Project [DOWNLOAD SITE](http://sourceforge.net/projects/shipvalidator/)

Email list
[owasp_cvuja_project](https://lists.owasp.org/mailman/listinfo/owasp_cvuja_project)

Bug Tracker : [Sourceforge bug
tracker](https://sourceforge.net/tracker/?group_id=263528&atid=1160394)
-- ==== Project Identification ====  --\>

#### Project Details

__NOTOC__ <headertabs/>

[Content Validation using Java Annotations
Project](Category:OWASP_Project "wikilink") [Category:OWASP
Tool](Category:OWASP_Tool "wikilink") [Category:OWASP
Download](Category:OWASP_Download "wikilink") [Category:OWASP Alpha
Quality Tool](Category:OWASP_Alpha_Quality_Tool "wikilink")
[Category:OWASP Content Validation using Java Annotations
Project](Category:OWASP_Content_Validation_using_Java_Annotations_Project "wikilink")