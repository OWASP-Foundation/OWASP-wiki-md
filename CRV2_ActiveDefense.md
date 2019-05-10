__TOC__

## Active Defense

Attack detection undertaken at the application layer has access to the
complete context of an interaction and enhanced information about the
user. The application knows what is a high-value issue and what is
noise. Input data are already decrypted and canonicalized within the
application and therefore application-specific intrusion detection is
less susceptible to advanced evasion techniques. This leads to a very
low level of attack identification false positives, providing
appropriate detection points are selected.

The fundamental requirements are the ability to perform four tasks:

  - Detection of a selection of suspicious and malicious events
  - Use of this knowledge centrally to identify attacks
  - Selection of a predefined response
  - Execution of the response.

Applications can undertake a range of responses, that may include
changes to a user's account or other changes to the application's
defensive posture. It can be difficult to detect active defense in
dynamic analysis since the responses may be invisible to the tester.
Code review is the best method to determine the existence of this
defense.

Other application functionality like authentication failure counts and
lock-out, or limits on rate of file uploads are **localized** protection
mechanisms. This sort of standalone logic is **not** active defense
equivalents in the context of this review, unless they are rigged
together into an application-wide sensory network and centralized
analytical engine.

It is not a bolt-on tool or code library, but instead offers insight to
an approach for organizations to specify or develop their own
implementations – specific to their own business, applications,
environments and risk profile – building upon existing standard security
controls. However, some developers may have used the following
components:

  - [:Category:OWASP Enterprise Security
    API](:Category:OWASP_Enterprise_Security_API "wikilink")
  - [AppSensor demonstration code](https://code.google.com/p/appsensor/)

Purpose of Code Review

In this case, a code review is being used to detect the presence of a
defense, and it is the absence of this that is a weakness. Note that
active defense cannot defend an application that has known
vulnerabilities, and therefore the other parts of this guide are
extremely important. **The code reviewer should note the absence of
active defense as a vulnerability**.

The purpose of code review is not necessarily to determine the efficacy
of the active defense, but could simply be to determine if such
capability exists.

## How to Locate the Attack Detection and Response Code

### Detection Points

Detection points can be integrated into presentation, business and data
layers of the application. Application-specific intrusion detection does
not need to identify all invalid usage, to be able to determine an
attack. There is no need for “infinite data” or “big data” and therefore
the location of "detection points" may be very sparse within source
code.

A useful approach for identifying such code is to find the name of the
only guidance in this area by searching for the string:

`  AppSensor`

Additionally search for AppSensor's detection point type identities:

`  RE1, RE2, ... RE8`
`  AE1, AE2, ... AE12`
`  SE1, SE2, ... SE6`
`  ACE1, ACE2, ... ACE4`
`  IE1, IE2, ... IE6`
`  EE1, EE2`
`  CIE1, CIE2, ... CIE4`
`  FIO1, FIO2`
`  HT1, HT2, HT3`
`  UT1, UT2, ... UT4`
`  STE1, STE2, STE3`
`  RP1, RP2, RP3, RP4`

Additionally search for any tagging based on [Mitre's Common Attack
Pattern Enumeration and Classification](http://capec.mitre.org/) (CAPEC)
such as strings like:

`  CAPEC-212, CAPEC-213, etc`

The AppSensor detection point type identifiers and CAPEC codes will
often have been used in configuration values (e.g. [in ESAPI for
Java](https://code.google.com/p/appsensor/source/browse/trunk/AppSensor/src/test/resources/.esapi/ESAPI.properties?r=53)),
parameter names and security event classification. Also, examine error
logging and security event logging mechanisms as these may be being used
to collect data that can then be used for attack detection. Identify the
code or services called that perform this logging and examine the event
properties recorded/sent. Then identify all places where these are
called from.

An examination of error handling code relating to input and output
validation is very likely to reveal the presence of detection points.
For example, in a whitelist type of detection point, additional code may
have been added adjacent, or within error handling code flow:

` if ( var !Match this ) {`
`     Error handling`
`     Record event for attack detection`
` }`

In some situations attack detection points are looking for blacklisted
input, and the test may not exist otherwise, so brand new code is added:

` if ( var !Match that ) {`
`     Record event for attack detection`
` }`

Identification of detection points should also have found the locations
where events are recorded (the "event store").

If detection points cannot be found, continue to review the code for
execution of response, as this may provide insight into the existence of
active defense.

### Attack Identification

The event store has to be analysed in real time or very frequently, in
order to identify attacks based on predefined criteria. The criteria
should be defined in configuration settings (e.g. in configuration
files, or read from another source such as a database).

A process will examine the event store to determine if an attack is in
progress - typically this will be attempting to identify an
authenticated user, but it may also consider a single IP address, range
of IP addresses, or groups of users such as one or more roles, users
with a particular privilege or even all users.

### Selection of Response

Once an attack has been identified, the response will be selected based
on predefined criteria. Again an examination of configuration data
should reveal the thresholds related to each detection point, groups of
detection points or overall thresholds.

Additionally search for AppSensor's response type identities as they may
have been used in configuration settings, parameter names or in logical
operations:

`  ASR-A, ASR-B, ... ASR-N, ASR-P`

The most common response actions are user warning messages, log out,
account lockout and administrator notification. However, as this
approach is connected into the application, the possibilities of
response actions are limited only by the coded capabilities of the
application.

### Execution of Response

Search code for any global includes that poll attack
identification/response identified above. Response actions (agains a
user, IP address, group of users, etc) will usually be initiated by the
application, but in some cases other applications (e.g. alter a fraud
setting) or infrastructure components (e.g. block an IP address range)
may also be involved.

Examine configuration files and any external communication the
application performs. The following types of responses may have been
coded:

  - Logging increased
  - Administrator notification
  - Other notification (e.g. other system)
  - Proxy
  - User status change
  - User notification
  - Timing change
  - Process terminated (same as traditional defenses)
  - Function amended
  - Function disabled
  - Account log out
  - Account lock out
  - Application disabled
  - Collect data from user.

Other capabilities of the application and related system components can
be repurposed or extended, to provide the selected response actions.
Therefore review the code associated with any localised security
measures such as account lock out.

## Leading Practice for Active Defense

The guidance for adding active response to applications given in the
[OWASP_AppSensor_Project](OWASP_AppSensor_Project "wikilink"), and in
particular the [AppSensor Guide
v2](:File:Owasp-appensor-guide-v2.doc "wikilink").