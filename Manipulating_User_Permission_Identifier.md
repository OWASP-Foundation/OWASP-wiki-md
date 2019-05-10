## Description

This attack focus on manipulation of user permission identifier in order
to elevate his privileges on the application, resulting in unauthorized
access, fraudulent transactions and application disrupt. The user
permission identifier is normally tied or associated with a session ID,
local cookies, hidden fields, among others.

To execute this attack, it is necessary to determine how the application
manages user permission identifier, where/how/which information is
stored and managed (client-side, server-side or both) and what data is
used as part of identifier. Based on this, the attacker can forge his
request using new values for session identifier and raise his permission
on the application.

## Examples

Assume that an application stores the authentication decision (auth=0/1)
in an unencrypted cookie on client machine. An attacker can violate this
information of user session and set “auth=1” in order to get
illegitimate access and elevated his privilege in the application.

## External References

  - <http://capec.mitre.org/data/definitions/74.html>

## Related Threats

[:Category: Authorization](:Category:_Authorization "wikilink")

[:Category: Information
Disclosure](:Category:_Information_Disclosure "wikilink")

## Related Attacks

  - [Session Hijacking](Session_Hijacking "wikilink")

## Related Vulnerabilities

[:Category: Environmental
Vulnerability](:Category:_Environmental_Vulnerability "wikilink")

## Related Countermeasures

[:Category:Access Control](:Category:Access_Control "wikilink")

## Categories

[:Category: Resource
Manipulation](:Category:_Resource_Manipulation "wikilink")