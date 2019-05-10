## Brief Summary

Most web applications allow users to reset their password if they have
forgotten it, usually by sending them a password reset email and/or by
asking them to answer one or more "security questions." In this test, we
check that this function is properly implemented and that it does not
introduce any flaw in the authentication scheme. We also check whether
the application allows the user to store the password in the browser
("remember password" function).

## Description of the Issue

A great majority of web applications provide a way for users to recover
(or reset) their password in case they have forgotten it. The exact
procedure varies heavily among different applications, also depending on
the required level of security, but the approach is always to use an
alternate way of verifying the identity of the user. One of the simplest
(and most common) approaches is to have on file the user's email address
(e.g., this is obtained when the user first registers), and send the old
password (or a new one) to that address. This scheme is based on the
assumption that the user's email has not been compromised and that is
secure enough for this goal.
Alternatively (or in addition to that), the application could ask the
user to answer one or more "secret questions", which are usually chosen
by the user among a set of possible ones. The security of this scheme
lies in the ability to provide a way for someone to identify themselves
to the system with answers to questions that are not easily answerable
via personal information lookups. As an example, a very insecure
question would be “your mother’s maiden name” since that is a piece of
information that an attacker could find out without much effort. An
example of a better question would be “favorite grade-school teacher”
since this would be a much more difficult topic to research about a
person whose identity may otherwise already be stolen.
Another common feature that applications use to provide users a
convenience is to cache the password locally in the browser (on the
client machine) and having it 'pre-typed' in all subsequent accesses.
While this feature can be perceived as extremely friendly for the
average user, at the same time, it introduces a flaw, as the user
account becomes easily accessible to anyone that uses the same account
on the client machine.

## Black Box Testing and Examples

**Password Reset**
The first step is to check whether secret questions are used. Sending
the password (or a password reset link) to the user email address
without first asking for a secret question means relying 100% on the
security of that email address, which is not suitable if the application
needs a high level of security.
On the other hand, if secret questions are used, the next step is to
assess their strength.
As a first point, how many questions need to be answered before the
password can be reset? The majority of applications only need the user
to answer to one question, but some critical applications require the
user to answer correctly to two or even more questions.
As a second step, we need to analyze the questions themselves. Often a
self-reset system offers the choice of multiple questions; this is a
good sign for the would-be attacker as this presents him/her with
options. Ask yourself whether you could obtain answers to any or all of
these questions via a simple Google search on the Internet or with a
social engineering attack. As a penetration tester, here is a
step-by-step walk-through of assessing a password self-reset tool:

  - Are there multiple questions offered?
      - If so, try to pick a question which would have a “public”
        answer; for example, something Google would find with a simple
        query
      - Always pick questions which have a factual answer such as a
        “first school” or other facts which can be looked up
      - Look for questions which have few possible options, such as
        “what make was your first car”. These questions would present
        the attacker with a short-list of answers to guess at and based
        on statistics the attacker could rank answers from most to least
        likely
  - Determine how many guesses you have (if possible)
      - Does the password reset allow unlimited attempts?
      - Is there a lockout period after X incorrect answers? Keep in
        mind that a lockout system can be a security problem in itself,
        as it can be exploited by an attacker to launch a Denial of
        Service against legitimate users
  - Pick the appropriate question based on analysis from above point,
    and do research to determine the most likely answers
  - How does the password-reset tool (once a successful answer to a
    question is found) behave?
      - Does it allow immediate change of the password?
      - Does it display the old password?
      - Does it email the password to some pre-defined email address?
      - The most insecure scenario here is if the password reset tool
        shows you the password; this gives the attacker the ability to
        log into the account, and unless the application provides
        information about the last login the victim would not know that
        his/her account has been compromised.
      - A less insecure scenario is if the password reset tool forces
        the user to immediately change his/her password. While not as
        stealthy as the first case, it allows the attacker to gain
        access and locks the real user out.
      - The best security is achieved if the password reset is done via
        an email to the address the user initially registered with, or
        some other email address; this forces the attacker to not only
        guess at which email account the password reset was sent to
        (unless the application tells that) but also to compromise that
        account in order to take control of the victim's access to the
        application.


The key to successfully exploiting and bypassing a password self-reset
is to find a question or set of questions which give the possibility of
easily acquiring the answers. Always look for questions which can give
you the greatest statistical chance of guessing the correct answer, if
you are completely unsure of any of the answers. In the end, a password
self-reset tool is only as strong as the weakest question. As a side
note, if the application sends/visualizes the old password in cleartext
it means that passwords are not stored in a hashed form, which is a
security issue in itself.

**Password Remember**
The "remember my password" mechanism can be implemented with one of the
following methods:

1.  Allowing the "cache password" feature in web browsers. As of 2014
    this is the preferred method as all major browsers have disabled the
    setting of autocomplete="off" by default for password fields.
2.  Storing the password in a permanent cookie. The password must be
    hashed/encrypted and not sent in the clear.

To check the second implementation type, examine the cookies stored by
the application. Verify that the credentials are not stored in
cleartext, but are hashed. Examine the hashing mechanism: if it is a
common, well-known algorithm, check for its strength; in homegrown hash
functions, attempt several usernames to check whether the hash function
is easily guessable. Additionally, verify that the credentials are only
sent during the login phase, and not sent together with every request to
the application.

## Gray Box Testing and Examples

This test uses only functional features of the application and HTML code
that is always available to the client, the graybox testing follows the
same guidelines of the previous section. The only exception is for the
password encoded in the cookie, where the same gray box analysis
described in the [Testing for Session Management
Schema](Testing_for_Session_Management_Schema_\(OWASP-SM-001\) "wikilink")
chapter can be applied.