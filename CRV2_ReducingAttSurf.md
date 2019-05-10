# This is a draft version

## Overview

The Attack Surface of an application is a description of the entry/exit
points, the roles/entitlements of the users, and the sensitivity of the
data held within the application. For example, entry points such as
login screens, HTML forms, file upload screens, all introduce a level of
risk to the application. Note that the code structure also forms part of
the Attack Surface, in that the code checking authentication, or crypto,
etc, is exercised by critical functions on the applications Attack
Surface.

## Description

This section concentrates on:

1.  knowing the current state of an applications Attack Surface and
2.  understanding if a change is going to increase that Attack Surface.

Michael Howard at Microsoft and other researchers have developed a
method for measuring the Attack Surface of an application, and to track
changes to the Attack Surface over time, called the Relative Attack
Surface Quotient (RSQ).

It is assumed that the application Attack Surface is already known,
probably through some previous threat modeling exercise, or
Architectural Risk Analysis. Therefor the entry and exit points are
known, the sensitivity of the data within the application is understood,
and the various users of the system, and their entitlements, have been
mapped in relation to the functions and data.

From a code review point of view, the aim would be to ensure the change
being reviewed is not unnecessarily increasing the Attack Surface. For
example, is the code change suddenly using HTTP were only HTTPS was used
before? Is the coder deciding to write their own hash function instead
of using the pre-existing (and well exercised/tested) central repository
of crypto functions? In some development environments the Attack Surface
changes can be checked during the design phase if such detail is
captured, however at code review the actual implementation is reflected
in the code and such Attack Surface exposures can be identified.

You can also build up a picture of the Attack Surface by scanning the
application. For web apps you can use a tool like the
OWASP_Zed_Attack_Proxy_Project or Arachni or Skipfish or w3af or one
of the many commercial dynamic testing and vulnerability scanning tools
or services to crawl your app and map the parts of the application that
are accessible over the web. Once you have a map of the Attack Surface,
identify the high risk areas, then understand what compensating controls
you have in place, operational controls like network firewalls and
application firewalls.

Note that backups of code and data (online, and on offline media) are an
important but often ignored part of a system's Attack Surface.
Protecting your data and IP by writing secure software and hardening the
infrastructure will all be wasted if you hand everything over to bad
guys by not protecting your backups.

## What to Review

When reviewing code modules from an Attack Surface point of view, some
common issues to look out for include:

  - Does the code change modify the attack surface? Using an
    understanding of the Attack Surface of the application before the
    code change, does it open new ports or accept new inputs? If it does
    could the change be done in a way that does not increase the attack
    surface? If a better implementation exists then that should be
    recommended, however if there is no way to implement the code
    without increasing the Attack Surface, make sure the business knows
    of the increased risk.
  - Is the feature unnecessarily using HTTP instead of HTTPS?
  - Is the function going to be available to non-authenticated users? If
    no authentication is necessary for the function to be invoked, then
    the risk of attackers using the interface is increased. Does the
    function invoke a backend task that could be used to deny other
    legitimate users?
      - E.g. if the function writes to a file, or sends an SMS, or
        causes a CPU intensive calculation, could an attacker write a
        script to call the function many times per second and prevent
        legitimate users access to that task?
  - Are searches controlled? Search is a risky operation as it typically
    queries the database for some criteria and returns the results, if
    attacker can inject SQL into query then they could access more data
    than intended.
  - Is important data stored separately from trivial data (in DB, file
    storage, etc). Is the change going to allow unauthenticated users to
    search for publicly available store locations in a database table in
    the same partition as the username/password table? Should this store
    location data be put into a different database, or different
    partition, to reduce the risk to the database information?
  - If file uploads are allowed, are they be authenticated? Is there
    rate limiting? Is there a maximum file size for each upload or
    aggregate for each user? Does the application restrict the file
    uploads to certain types of file (by checking MIME data or file
    suffix). Is the application is going to run virus checking?
  - If you have administration users with high privilege, are their
    actions logged/tracked in such a way that they a) can't erase/modify
    the log and b) can't deny their actions?
      - Are there any alarms or monitoring to spot if they are accessing
        sensitive data that they shouldn't be? This could apply to all
        types of users, not only administrators.
  - Will changes be compatible with existing countermeasures, or
    security code, or will new code/countermeasures need to be
    developed?
  - Is the change attempting to introduce some non-centralized security
    code module, instead of re-using or extending an existing security
    module?
  - Is the change adding unnecessary user levels or entitlements that
    will complicate the attack surface.
  - If the change is storing PII or confidential data, is all of the new
    information absolutely necessary? There is little value in
    increasing the risk to an application by storing the social security
    numbers of millions of people, if the data is never used.
  - Does application configuration cause the attack surface to vary
    greatly, and is that configuration simple to use and alert the
    administrator when the attack surface is being expanded?
  - Could the change be done in a different way that would reduce the
    attack surface, i.e instead of making help items searchable and
    storing help item text in a database table beside the main
    username/password store, providing static help text on HTML pages
    reduces the risk through the 'help' interface.
  - Is information stored on the client that should be stored on the
    server?

## References

  - <https://www.owasp.org/index.php/Attack_Surface_Analysis_Cheat_Sheet>
  - <https://www.owasp.org/index.php/OWASP_Zed_Attack_Proxy_Project>
  - <http://www.cs.cmu.edu/~wing/publications/Howard-Wing03.pdf>