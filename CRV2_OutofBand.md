# This is a draft version

## Overview

The term 'out-of-band' is commonly used when an web application
communicates with an end user over a channel separate to the HTTP
request/responses conducted through the users' web browser. Common
examples include text/SMS, phone calls, e-mail and regular mail.

## Description

The main reason an application would wish to communicate with the end
user via these separate channels is for security. A username and
password combination could be sufficient authentication to allow a user
to browse and use non-sensitive parts of a website, however more
sensitive (or risky) functions could require a stronger form of
authentication. A username and password could have been stolen through
an infected computer, through social engineering, database leak or other
attacks, meaning the web application cannot put too much in trust a web
session providing the valid username and password combination is
actually the intended user.

Examples of sensitive operations could include:

  - Changing password
  - Changing account details, such as e-mail address, home address, etc
  - Transferring funds in a banking application
  - Submitting, modifying or cancelling orders

In these cases many applications will communicate with you via a channel
other than a browsing session. Many large on-line stores will send you
confirmation e-mails when you change account details, or purchase items.
This protects in the case that an attacker has the username and
password, if they buy something, the legitimate user will get an e-mail
and have a chance to cancel the order or alert the website that they did
not modify the account.

When out-of-band techniques are performed for authentication it is
termed two-factor authentication. There are three ways to authenticate:

1.  Something you know (e.g. password, passphrase, memorized PIN)
2.  Something you have (e.g. mobile phone, cash card, RSA token)
3.  Something you are (e.g. iris scan, fingerprint)

If a banking website allows users to initiate transactions online, it
could use two-factor authentication by taking 1) the password used to
log in and 2) sending an PIN number over SMS to the users registered
phone, and then requiring the user enter the PIN before completing the
transaction. This requires something the user knows (password) and has
(phone to receive the PIN).

A 'chip-and-pin' banking card will user two-factor authentication, by
requiring users to have the card with them (something they have) and
also enter a PIN when performing a purchase (something they know). A
'chip-and-pin' card is no use within the PIN number, likewise knowing
the PIN number is useless if you do not have the card.

## What to Review

When reviewing code modules which perform out-of-band functions, some
common issues to look out for include:

  - Recognize the risk of the system being abused. Attackers would like
    to flood someone with SMS messages from your site, or e-mails to
    random people. Ensure:
      - When possible, only authenticated users can access links that
        cause an out-of-band feature to be invoked (forgot password
        being an exception).
      - Rate limit the interface, thus users with infected machines, or
        hacked accounts, can't use it to flood out-of-band messages to a
        user.
      - Do not allow the feature to accept the destination from the
        user, only use registered phone numbers, e-mails, addresses.
  - For high risk sites (e.g. banking) the users phone number can be
    registered in person rather than via the web site.
  - Do not send any personal or authentication information in the
    out-of-band communication.
  - Ensure any PINs or passwords send over out-of-band channels have a
    short life-span and are random.
  - A consideration can be to prevent SMS messages being sent to the
    device currently conducting the browsing session (i.e. user browsing
    on their iPhone, were the SMS is sent to). However this can be hard
    to enforce.
  - If possible give users the choice of band they wish to use. For
    banking sites Zitmo malware on mobile devices (see references) can
    intercept the SMS messages, however iOS devices have not been
    affected by this malware yet, so users could choose to have SMS PINs
    sent to their Apple devices, and when on Android they could use
    recorded voice messages to receive the PIN.
  - In a typical deployments specialized hardware/software separate from
    the web application will handle the out-of-band communication,
    including the creation of temporary PINs and possibly passwords. In
    this scenario there is no need to expose the PIN/password to your
    web application (increasing risk of exposure), instead the web
    application should query the specialized hardware/software with the
    PIN/password supplied by the end user, and receive a positive or
    negative response.

Many sectors including the banking sector have regulations requiring the
use of two-factor authentication for certain types of transactions. In
other cases two-factor authentication can reduce costs due to fraud and
re-assure customers of the security of a website.

## Languages

## References

  - <https://www.owasp.org/index.php/Forgot_Password_Cheat_Sheet>
  - <http://securelist.com/blog/virus-watch/57860/new-zitmo-for-android-and-blackberry/>