## Summary

Browsers will sometimes ask a user if they wish to remember the password
that they just entered. The browser will then store the password, and
automatically enter it whenever the same authentication form is visited.
This is a convenience for the user. Additionally some websites will
offer custom "remember me" functionality to allow users to persist log
ins on a specific client system.

Having the browser store passwords is not only a convenience for
end-users, but also for an attacker. If an attacker can gain access to
the victim's browser (e.g. through a Cross Site Scripting attack, or
through a shared computer), then they can retrieve the stored passwords.
It is not uncommon for browsers to store these passwords in an easily
retrievable manner, but even if the browser were to store the passwords
encrypted and only retrievable through the use of a master password, an
attacker could retrieve the password by visiting the target web
application's authentication form, entering the victim's username, and
letting the browser to enter the password.

Additionally where custom "remember me" functions are put in place
weaknesses in how the token is stored on the client PC (for example
using base64 encoded credentials as the token) could expose the users
passwords. Since early 2014 most major browsers will override any use of
autocomplete="off" with regards to password forms and as a result
previous checks for this are not required and recommendations should not
commonly be given for disabling this feature. However this can still
apply to things like secondary secrets which may be stored in the
browser inadvertently.

## How to Test

  - Look for passwords being stored in a cookie. Examine the cookies
    stored by the application. Verify that the credentials are not
    stored in clear text, but are hashed.
  - Examine the hashing mechanism: if it is a common, well-known
    algorithm, check for its strength; in homegrown hash functions,
    attempt several usernames to check whether the hash function is
    easily guessable.
  - Verify that the credentials are only sent during the log in phase,
    and not sent together with every request to the application.
  - Consider other sensitive form fields (e.g. an answer to a secret
    question that must be entered in a password recovery or account
    unlock form).

## Remediation

Ensure that no credentials are stored in clear text or are easily
retrievable in encoded or encrypted forms in cookies.