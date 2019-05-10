![Fix-now.gif](Fix-now.gif "Fix-now.gif") Performing code reviews and
other types of verification activities such as security testing is
USELESS unless findings from these activities are acted upon IMMEDIATELY
by the development team. Failure to act in a timely manner makes
attempting fixes much more difficult than they otherwise would have been
if action had been taken immediately, or simply not possible.

How can fixing what development teams may at first glance see as mere
"bugs" become so much harder or not possible? As time goes on and as
development actively continues, code where findings were originally
found becomes unrecognizable as it is branched and refactored, and as
new (unexamined) code (with potential new findings) is added to branches
and the baseline. Security-related bugs propagate and multiply as
development techniques that caused the bug continue to be practiced.

In these cases, a new code review or verification becomes necessary. As
one might expect however, performing a new code review or verification
activity out of necessity in these cases further sets back budgets and
timelines. Worse, in the meanwhile, your application AND the data AND
systems that it relies on and that it talks to REMAIN VULNERABLE TO
ATTACK.

How can one guard against reports from security teams going stale? There
are two specific actions that management and development teams can take
up front, before a single line of code is reviewed, before a single form
field is injected with an attack:

  - Figure out how to ADD code reviews and other types of verification
    activities as a REGULAR activity during YOUR development life cycle,
    and
  - Plan on TRACKING and TRIAGING findings from these activities with
    the SAME URGENCY as failed baseline builds and user-reported bugs.

Doing the above will have meant that the management team will have
provided the necessary funding AND MANDATE for the security team by
allowing the SDLC to be opened up to the addition of a new activity.
Doing the above will also have meant that the development team will have
figured out the mechanics of same and have taken MEASURABLE actions
towards the end of securing their application.

For an example of how to add code reviews and other types of
verification activities to an SDLC, see: [Agile Software Development:
Don't Forget Evil User
Stories](Agile_Software_Development:_Don%27t_Forget_EVIL_User_Stories "wikilink")

For more information about code reviews and other types of verification
activities, see: [The ASVS Project](ASVS "wikilink")

[Category:OWASP Application Security Verification Standard
Project](Category:OWASP_Application_Security_Verification_Standard_Project "wikilink")
[Category:OWASP Enterprise Security
API](Category:OWASP_Enterprise_Security_API "wikilink") [Category:How
To](Category:How_To "wikilink")