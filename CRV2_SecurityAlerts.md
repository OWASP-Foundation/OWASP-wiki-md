# This is a draft version

## Overview

How will your code and applications react when something has gone wrong?
Many companies that follow secure design and coding principals do so to
prevent attackers from getting into their network, however many
companies do not consider designing and coding for the scenario where an
attacker may have found a vulnerability, or has already exploited it to
run code within a companies firewalls (i.e. within the Intranet).

Many companies employ SIEM logging technologies to monitor network and
OS logs for patterns that detect suspicions activity, this section aims
to further encourage application layers and interfaces to do the same.

## Description

This section concentrates on:

1.  design and code that allows the user to react when a system is being
    attacked
2.  concepts allowing applications to flag when they have been breached

When a company implements secure design and coding, it will have the aim
of preventing attackers from misusing the software and accessing
information they should not have access to. Input validation checks for
SQL injections, XSS, CSRF, etc should prevent attackers from being able
to exploit these types of vulnerabilities against the software. However
how should software react when an attacker is attempting to breach the
defenses, or the protections have been breached?

For an application to alert to security issues, it needs context on what
is 'normal' and what constitutes a security issue. This will differ
based on the application and the context within which it is running. In
general applications should not attempt to log every item that occurs as
the excessive logging will slow down the system, fill up disk or DB
space, and make it very hard to filter through all the information to
find the security issue.

At the same time, if not enough information is monitored or logged, then
security alerting will be very hard to do based on the available
information. To achieve this balance an application could use it's own
risk scoring system, monitoring at a system level what risk triggers
have been spotted (i.e. invalid inputs, failed passwords, etc.) and use
different modes of logging. Take an example of normal usage, in this
scenario only critical items are logged. However if the security risk is
perceived to have increased, then major or security level items can be
logged and acted upon. This higher security risk could also invoke
further security functionality as described later in this section.

Take an example where an online form (post authentication) allows a user
to enter a month of the year. Here the UI is designed to give the user a
drop down list of the months (January through to December). In this case
the logged in user should only ever enter one of 12 values, since they
typically should not be entering any text, instead they are simply
selecting one of the pre-defined drop down values.

If the server receiving this form has followed secure coding practices,
it will typically check that the form field matches one of the 12
allowed values, and then considers it valid. If the form field does not
match, it returns an error, and may log a message in the server. This
prevents the attacker from exploiting this particular field, however
this is unlikely to deter an attacker and they would move onto other
form fields.

In this scenario we have more information available to us than we have
recorded. We have returned an error back to the user, and maybe logged
an error on the server. In fact we know a lot more; an authenticated
user has entered an invalid value which they should never have been able
to do (as it's a drop down list) in normal usage. This could be due to a
few reasons:

1.  There's a bug in the software and the user is not malicious
2.  An attacker has stolen the users login credentials and is attempting
    to attack the system
3.  A user has logged in but has a virus/trojan which is attempting to
    attack the system
4.  A user has logged in but is experiencing a man-in-the-middle attack
5.  A user is not intending to be malicious but has somehow changed the
    value with some browser plugin, etc.

If it's the first case above, then the company should know about it to
fix their system. If it's case 2, 3 or 3 then the application should
take some action to protect itself and the user, such as reducing the
functionality available to the user (i.e. no PII viewable, can't change
passwords, can't perform financial transactions) or forcing further
authentication such as security questions or out-of-band authentication.
The system could also alert the user to the fact that the unexpected
input was spotted and advise them to run antivirus, etc, thus stopping
an attack when it is underway.

Obviously care must be taken in limiting user functionality or alerting
users encase it's an honest mistake, so using a risk score or noting
session alerts should be used. For example, if everything has been
normal in the browsing session and 1 character is out of place, then
showing a red pop-up box stating the user has been hacked is not
reasonable, however if this is not the usual IP address for the user,
they have logged in at an unusual time, and this is the 5th malformed
entry with what looks like an SQL injection string, then it would be
reasonable for the application to react. This possible reaction would
need to be stated in legal documentation.

In another scenario, if an attacker has got through the application
defenses extracted part of the applications customer database, would the
company know? Splitting information in the database into separate tables
makes sense from an efficiency point of view, but also from a security
view, even putting confidential information into a separate partition
can make it harder for the attacker. However if the attacker has the
information it can be hard to detect and applications should make steps
to aid alerting software (e.g. SIEM systems). Many financial
institutions use risk scoring systems to look at elements of the users
session to give a risk score, if Johnny always logs in at 6pm on a
Thursday from the same IP, then we have a trusted pattern. If suddenly
Johnny logs in at 2:15am from an IP address on the other side of the
world, after getting the password wrong 7 times, then maybe he's
jetlagged after a long trip, or perhaps his account has been hacked.
Either way, asking him for out-of-band authentication would be
reasonable to allow Johnny to log in, or to block an attacker from using
Johnnys account.

If the application takes this to a larger view, it can determine that on
a normal day 3% of the users log on in what would be considered a
riskier way, i.e. different IP address, different time, etc. If on
Thursday it sees this number rise to 23% then has something strange
happened to the user base, or has the database been hacked? This type of
information can be used to enforce a blanket out-of-band authentication
(and internal investigation of the logs) for the 23% of 'riskier' users,
thereby combining the risk score for the user with the overall risk
score for the application.

Another good option is 'honey accounts' which are usernames and
passwords that are never given out to users. These accounts are added
just like any other user, and stored in the DB, however they are also
recorded in a special cache and checked on login. Since they are never
given to any user, no user should ever logon with them, however if one
of those accounts are used, then the only way that username password
combination could be known is if an attacker got the database, and this
information allows the application to move to a more secure state and
alert the company that the DB has been hacked.

## What to Review

When reviewing code modules from an security alerting point of view,
some common issues to look out for include:

  - Will the application know if it's being attacked? Does it ignore
    invalid inputs, logins, etc or does it log them and monitor this
    state to capture a cumulative perception of the current risk to the
    system?
  - Can the application automatically change it's logging level to react
    to security threats? Is changing security levels dynamic or does it
    require a restart?
  - Does the SDLC requirements or design documentation capture what
    would constitute a security alert? Has this determination been peer
    reviewed? Does the testing cycle run through these scenarios?
  - Does the system employ 'honey accounts' such that the application
    will know if the DB has been compromised?
  - Is there a risk based scoring system that records the normal usage
    of users and allows for determination or reaction if the risk
    increases?
  - If a SIEM system is being used, have appropriate triggers been
    identified? Has automated tests been created to ensure those trigger
    log messages are not accidentally modified by future enhancements or
    bug fixes?
  - Does the system track how many failed login attempts a user has
    experienced? Does the system react to this?
  - Does certain functionality (i.e. transaction initiation, changing
    password, etc) have different modes of operation based on the
    current risk score the application is currently operating within?
  - Can the application revert back to 'normal' operation when the
    security risk score drops to normal levels?
  - How are administrators alerted when security risk score rises? Or
    when a breach has been assumed? At an operational level, is this
    tested regularly? How are changes of personnel handled?

## References