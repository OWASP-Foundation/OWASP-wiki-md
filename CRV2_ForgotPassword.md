## Overview

If your web site needs to have user authentication then most likely it
will require user name and password to authenticate user accesses.
However as computer system have increased in complexity, so has
authenticating users has also increased. As a result the code reviewer
needs to be aware of the benefits and drawbacks of user authentication
referred to as “Direct Authentication” pattern in this section. This
section is going to emphasis design patterns for when users forget user
id and or password and what the code reviewer needs to consider when
reviewing how user id and passwords can be retrieved when forgotten by
the user and how to do this in a secure manner.

## General considerations

Notified user by (phone sms, email) an email where the user has to click
a link in the email that takes them to your site and ask the user to
enter a new password.

Ask user to enter login credentials they already have (Facebook,
Twitter, Google, Microsoft Live, OpenID etc) to validate user before
allowing user to change password.

Send notification to user to confirm register and or forgot password.

Send notifications that account information has been changed for
registered email. Set appropriate time out value. I.e. If user does not
respond to email within 48 hours then user will be frozen out of system
until user re-affirms password change.

### General Considerations

1.  The identity and shared secret/password must be transferred using
    encryption to provide data confidentiality. HTTPS should also be
    used but in itself should not be the only mechanism used for data
    confidentiality.
2.  A shared secret can never be stored in clear text format, even if
    only for a short time in a message queue.
3.  A shared secret must always be stored in hashed or encrypted format
    in a database.
4.  The organization storing the encrypted shared secret does not need
    the ability to view or decrypt users passwords. User password must
    never be sent back to a user.
5.  If the client must cache the username and password for presentation
    for subsequent calls to a Web service then a secure cache mechanism
    needs to be in place to protect user name and password.
6.  When reporting an invalid entry back to a user, the username and or
    password should no be identified as being invalid. User feed
    back/error message must consider both user name and password as one
    item “user credential”. I.e. “The username or password you entered
    is incorrect.”

### AntiPatterns: Forget password.

1.  Validate all fields have been completed correctly
    1.  Avoid password fields being wiped out.
    2.  Retain user’s email address between log-in and “Forgotten
        password” page.
2.  CAPTCHA should be used aa last resort or not all. CAPTCHA can be
    hacked.
3.  OpenID does have security implications (e.i. if a hacker gains
    access to your OpenID, the hacker now potentially have access to all
    the sites you use with that OpenID.
4.  Make sure security questions don’t ask for information that can
    easily be found on social sites like Facebook. E.I. “Mother’s maiden
    name”.
5.  Do not mask user input of password. Show character until next
    character is typed in. Masking every character only provides
    security if someone is standing directly over you.
6.  Do not send a onetime password to allow user to reset his/her
    password. This password would be stored even if for a short time in
    clear text and email storage is not the place to store passwords.
7.  Do not have an error message saying account does not exists for this
    email address. This could be used to find out if user has an account
    for a porn or another site if hacker knows users email address.
8.  **Important**: Do not allow listing of users. The password reset
    tokens should be uniquely generated, and be cryptographically secure
    random. Otherwise a listing of users can be generated from forget
    password feature.