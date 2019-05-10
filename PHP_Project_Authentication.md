# Authentication principles

## Evidence of identity

## Self registration

## Remember Me

## Account controls

Account Expiry

# Authentication methods

## Forms based authentication

## LDAP authentication

## Strong Authentication

# Programmatic patterns

## Positive Authentication

## Multiple Key Lookups

## Browser remembers passwords

## Change passwords

## Brute Force

## Idle Timeouts

## Logout

# Anti security patterns

## Default accounts

## Choice of usernames

## CAPTCHA

## Weak password controls

## Reversible password encryption

## Automated password resets

Automated password reset schemes are a weak backdoor password into your
system. If your system is worthless, then automated password resets
might be for you. However, in most cases, they are unsuitable.

Automated password resets take two forms:

  - Send e-mail to registered user's e-mail address
  - Questions and answers

Sending e-mail is suspect due to the ease of which web mail and POP3 /
IMAP mail may be compromised, particularly if the user chooses the same
password amongst many systems. Often the user's e-mail address is easily
determined using search engines, and so an attacker can try to brute
force the web mail / POP / IMAP account and thus gain control of your
system's credential.

Questions and answers are highly problematic in countries with strong
privacy laws. You MUST not collect data which you have no need to
collect. A questions and answers scenario is not a permissable use for
items such as:

  - Social security numbers or tax file numbers
  - Information about other individuals (mother's maiden name, birth
    date etc) without the other person's consent
  - Details of driver's license or Medicare cards (in fact, most
    government IDs are problematic in this regard)

These systems are also fairly weak when it comes to close friends or
family emulating that person. For example, many families are aware of
the first holiday location, what color house a person lived in, pets
names, etc.

The only class of questions which are "safe" whilst being open are
abstract questions, such as "what is your favorite shape?" and so on,
which can be just as difficult to remember as a real password.

A safe alternative to questions and answers is SMSing a random reset
code or temporary password to the user's mobile phone. This costs about
$0.10 c per reset, and is hard to obviate as it's a second factor and
does not generally involve the Internet. Therefore it is hard for an
attacker to intercept today.

## Referer Checks

Referers is a client provided, optional HTTP header field, and as such
can be completely faked. The referer field should not be used. If code
contains this string:

$_SERVER\["HTTP_REFERER"\]

the code is immediately suspect and should be inspected to ensure that
no actual security decisions are made. If in doubt, completely remove
this code.

# Further Reading

[PHP Security for Developers](PHP_Security_for_Developers "wikilink")

[Category:PHP](Category:PHP "wikilink")