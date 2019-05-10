## Overview

The J2EE platform does not include any validation features. This leaves
many organizations to craft their own validation mechanisms, often
incomplete, flawed, and inefficient.

OWASP Stinger 2.x is an implementation of the design principals detailed
in the [OWASP Validation
Documentation](http://www.owasp.org/index.php/OWASP_Validation_Documentation_Project).
The basic idea is to define validation rules for the cookies and
parameters of an HTTP request. These rules are specified in simple XML
files using the 'Security Validation Definition Language.' Furthermore,
Stinger 2 is implemented as a J2EE filter such that all HTTP traffic is
validated *before* it is ever processed by the web application.

## Project Lead

The OWASP Stinger Project leader is [Wesley
West](mailto:Wesley.M.West@ge.com).

## License

Stinger is offered under the
[LGPL](http://www.gnu.org/copyleft/lesser.html). For further information
on OWASP licenses, please consult the [OWASP
Licenses](OWASP_Licenses "wikilink") page.

## Downloads

:\*[Click here](http://www.owasp.org/index.php/OWASP_Stinger_2_Releases)
to view all OWASP Stinger 2.x releases

:\*[Click here](http://www.owasp.org/index.php/OWASP_Stinger_Manual) to
view the OWASP Stinger 2.x Manual

## Feedback and Participation

We hope you find Stinger useful. Please contribute back to the project
by sending your comments, questions, and suggestions to the Stinger
mailing list. Thanks\!

To join the OWASP Stinger mailing list or view the archives, please
visit the [subscription
page](http://lists.owasp.org/mailman/listinfo/owasp-stinger).

## Donations

The Open Web Application Security Project is purely an open-source
community driven effort. As such, all projects and research efforts are
contributed and maintained with an individual's *spare time.* If you
have found this or any other project useful, please support OWASP with a
[donation](https://www.owasp.org/index.php/Contributions).

## Project Sponsors

None at this time.

[Category:OWASP Stinger
Project](Category:OWASP_Stinger_Project "wikilink")