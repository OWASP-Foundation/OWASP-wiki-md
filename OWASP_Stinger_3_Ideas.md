## Overview

The OWASP Stinger 3.x series will be heavily driven by the community.
Everyone is encouraged to contribute ideas and suggestions to make
Stinger 3.x the most powerful and flexible web application firewall as
possible. One major goal of the OWASP Stinger 3.x series is to develop a
solid and flexible validation engine capable of implementing common web
application security features.. With the help of the community, I
believe this goal can be achieved\!

## Development Complete

The following is a list of ideas that have been fully implemented in the
Stinger 3.x baseline:

:\* Validation of the entire HTTP request: including URI, headers,
cookies, and parameters

:\* A robust "learning" mode to make rule generation simplistic and
efficient.

:\* A more flexible "Action" framework. Actions will be able to execute
logic before and/or after the request is processed by the web
application

## Under Development

The following is a list of ideas currently under development in the
Stinger 3.x baseline:

:\* The ability to enforce web application firewall logic

::\* Defining and enforcing URI level access control

::\* Cross Site Request Forgery Guard

::\* HTTP Cookie Guard

::\* No-Cache Guard

::\* 200 Response Codes (fooling web application scanners)

::\* Request Rate Throttler

::\* Enforce [HTTPOnly](HTTPOnly "wikilink") on all cookies

## Planning to Develop

The following is a list of ideas that will be integrated into the
Stinger 3.x baseline:

:\* A full web application dedicated to editing the OWASP Stinger
configuration files

## Ideas Under Consideration

The following is a list of ideas that are under consideration for the
Stinger 3.x baseline:

:\* The ability to validate the Java properties files used by the web
application

:\* The ability to to build rules for and validate rules against
serialized objects

If you have an idea that you would like seen in Stinger 3.x, please
email me at [eric dot sheridan at
owasp.org](mailto:eric.sheridan@owasp.org)