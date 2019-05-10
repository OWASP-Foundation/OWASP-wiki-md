## Brief Summary

In this phase, we check that the logout function is properly
implemented, and that it is not possible to “reuse” a session after
logout. We also check that the application automatically logs out a user
when that user has been idle for a certain amount of time, and that no
sensitive data remains stored in the browser cache.
\== Description of the Issue == The end of a web session is usually
triggered by one of the following two events:

  - The user logs out
  - The user remains idle for a certain amount of time and the
    application automatically logs him/her out

Both cases must be implemented carefully, in order to avoid introducing
weaknesses that could be exploited by an attacker to gain unauthorized
access. More specifically, the logout function must ensure that all
session tokens (e.g., cookies) are properly destroyed or made unusable,
and that proper controls are enforced at the server side to prevent the
reuse of session tokens.

Note: the most important thing is for the application to invalidate the
session on the server side. Generally this means that the code must
invoke the appropriate methods, e.g., HttpSession.invalidate() in Java
and Session.abandon() in .NET. Clearing the cookies from the browser is
a nice touch, but is not strictly necessary, since if the session is
properly invalidated on the server, having the cookie in the browser
will not help an attacker.

If such actions are not properly carried out, an attacker could replay
these session tokens in order to “resurrect” the session of a legitimate
user and impersonate him/her (this attack is usually known as 'cookie
replay'). Of course, a mitigating factor is that the attacker needs to
be able to access those tokens (which are stored on the victim's PC),
but, in a variety of cases, this may not be impossible or particularly
difficult. The most common scenario for this kind of attack is a public
computer that is used to access some private information (e.g., webmail,
online bank account): when the user has finished using the application
and logs out, if the logout process is not properly enforced, the
following user could access the same account, for instance, by simply
pressing the “back” button of the browser. Another scenario can result
from a Cross Site Scripting vulnerability or a connection that is not
100% protected by SSL: a flawed logout function would make stolen
cookies useful for a much longer time, making life for the attacker much
easier. The third test of this chapter is aimed to check that the
application prevents the browser to cache sensitive data, which again
would pose a danger to a user accessing the application from a public
computer.

## Black Box testing and examples

**Logout function:**
The first step is to test the presence of the logout function. Check
that the application provides a logout button and that this button is
present and well visible on all pages that require authentication. A
logout button that is not clearly visible, or that is present only on
certain pages, poses a security risk, as the user might forget to use it
at the end of his/her session.

The second step consists of checking what happens to the session tokens
when the logout function is invoked. For instance, when cookies are
used, a proper behavior is to erase all session cookies, by issuing a
new Set-Cookie directive that sets their value to a non-valid one (e.g.,
“NULL” or some equivalent value), and, if the cookie is persistent,
setting its expiration date in the past, which tells the browser to
discard the cookie. So, if the authentication page originally sets a
cookie in the following way:

    Set-Cookie: SessionID=sjdhqwoy938eh1q; expires=Sun, 29-Oct-2006 12:20:00 GMT; path=/; domain=victim.com

the logout function should trigger a response somewhat resembling the
following:

    Set-Cookie: SessionID=noauth; expires=Sat, 01-Jan-2000 00:00:00 GMT; path=/; domain=victim.com

The first (and simplest) test at this point consists of logging out and
then hitting the 'back' button of the browser, to check whether we are
still authenticated. If we are, it means that the logout function has
been implemented insecurely, and that the logout function does not
destroy the session IDs. This happens sometimes with applications that
use non-persistent cookies and that require the user to close his
browser in order to effectively erase such cookies from memory. Some of
these applications provide a warning to the user, suggesting her to
close her browser, but this solution completely relies on the user
behavior, and results in a lower level of security compared to
destroying the cookies. Other applications might try to close the
browser using JavaScript, but that again is a solution that relies on
the client behavior, which is intrinsically less secure, since the
client browser could be configured to limit the execution of scripts
(and, in this case, a configuration that had the goal of increasing
security would end up decreasing it). Moreover, the effectiveness of
this solution would be dependent on the browser vendor, version, and
settings (e.g., the JavaScript code might successfully close an Internet
Explorer instance, but fail to close a Firefox one).

If by pressing the 'back' button we can access previous pages but not
access new ones, then we are simply accessing the browser cache. If
these pages contain sensitive data, it means that the application did
not forbid the browser to cache it (by not setting the Cache-Control
header, a different kind of problem that we will analyze later).

After the “back button” technique has been tried, it's time for
something a little more sophisticated: we can re-set the cookie to the
original value and check whether we can still access the application in
an authenticated fashion. If we can, it means that there is not a
server-side mechanism that keeps track of active and non active cookies,
but that the correctness of the information stored in the cookie is
enough to grant access. To set a cookie to a determined value, we can
use WebScarab, and, intercepting one response of the application, insert
a Set-Cookie header with our desired values:

[image:TestingGuide-LogoutTest-fig1.png](image:TestingGuide-LogoutTest-fig1.png "wikilink")

Alternatively, we can install a cookie editor in our browser (e.g., Add
N Edit Cookies in Firefox):

[image:TestingGuide-LogoutTest-fig2.png](image:TestingGuide-LogoutTest-fig2.png "wikilink")

A notable example of a design where there is no control at the server
side about cookies that belong to logged-out users is ASP.NET
FormsAuthentication class, where the cookie is basically an encrypted
and authenticated version of the user credentials, which are decrypted
and checked by the server side. While this is very effective in
preventing cookie tampering, the fact that the server does not maintain
an internal record of the session status means that it is possible to
launch a cookie replay attack after the legitimate user has logged out,
provided that the cookie has not expired yet (see the references for
further detail).

It should be noted that this test only applies to session cookies, and
that a persistent cookie that only stores data about some minor user
preferences (e.g., site appearance) and that is not deleted when the
user logs out is not to be considered a security risk.

**Timeout logout**
The same approach that we have seen in the previous section can be
applied when measuring the timeout logout. The most appropriate logout
time should be a right balance between security (shorter logout time)
and usability (longer logout time) and heavily depends on the
criticality of the data handled by the application. A 60 minute logout
time for a public forum can be acceptable, but such a long time would be
way too much in a home banking application. In any case, any application
that does not enforce a timeout-based logout should be considered not
secure, unless such a behavior is addressing a specific functional
requirement. The testing methodology is very similar to the one outlined
in the previous section. First, we have to check whether a timeout
exists, for instance, by logging in and then killing some time reading
some other Testing Guide chapter, waiting for the timeout logout to be
triggered. As in the logout function, after the timeout has passed, all
session tokens should be destroyed or be unusable. We also need to
understand whether the timeout is enforced by the client or by the
server (or both). Getting back to our cookie example, if the session
cookie is non-persistent (or, more in general, the session token does
not store any data about the time), we can be sure that the timeout is
enforced by the server. If the session token contains some time related
data (e.g., login time, or last access time, or expiration date for a
persistent cookie), then we know that the client is involved in the
timeout enforcing. In this case, we need to modify the token (if it's
not cryptographically protected) and see what happens to our session.
For instance, we can set the cookie expiration date far in the future
and see whether our session can be prolonged. As a general rule,
everything should be checked server-side and it should not be possible,
by re-setting the session cookies to previous values, to access the
application again.

**Cached pages**
Logging out from an application obviously does not clear the browser
cache of any sensitive information that might have been stored.
Therefore, another test that is to be performed is to check that our
application does not leak any critical data into the browser cache. In
order to do that, we can use WebScarab and search through the server
responses that belong to our session, checking that for every page that
contains sensitive information the server instructed the browser not to
cache any data. Such a directive can be issued in the HTTP response
headers (POST RELEASE NOTE: Cache-Control: no-cache, no-store coupled
with Expires: 0 and Pragma: no-cache is generally robust although
additional flags may be necessary for the Cache-Control header in order
to better prevent persistently linked files on the filesystem; these
include must-revalidate, pre-check=0, post-check=0, max-age=0, and
s-maxage=0.)

    HTTP/1.1:
    Cache-Control: no-cache

    HTTP/1.0:
    Pragma: no-cache
    Expires: <past date or illegal value (e.g., 0)>


Alternatively, the same effect can be obtained directly at the HTML
level, including in each page that contains sensitive data the following
code: (POST RELEASE NOTE: META TAGS ARE COMMONLY INEFFECTIVE.)

    HTTP/1.1:
    <META HTTP-EQUIV="Cache-Control" CONTENT="no-cache">

    HTTP/1.0:
    <META HTTP-EQUIV="Pragma" CONTENT="no-cache">
    <META HTTP-EQUIV=”Expires” CONTENT=”Sat, 01-Jan-2000 00:00:00 GMT”>


For instance, if we are testing an e-commerce application, we should
look for all pages that contain a credit card number or some other
financial information, and check that all those pages enforce the
no-cache directive. On the other hand, if we find pages that contain
critical information but that fail to instruct the browser not to cache
their content, we know that sensitive information will be stored on the
disk, and we can double-check that simply by looking for it in the
browser cache. The exact location where that information is stored
depends on the client operating system and on the browser that has been
used. Here are some examples:

  - Mozilla Firefox:
      - Unix/Linux: \~/.mozilla/firefox/<profile-id>/Cache/
      - Windows: C:\\Documents and Settings\\<user_name>\\Local
        Settings\\Application
        Data\\Mozilla\\Firefox\\Profiles\\<profile-id>\\Cache\>

<!-- end list -->

  - Internet Explorer:
      - C:\\Documents and Settings\\<user_name>\\Local
        Settings\\Temporary Internet Files\>



## Gray Box testing and example

As a general rule, we need to check that:

  - The logout function effectively destroys all session token, or at
    least renders them unusable
  - The server performs proper checks on the session state, disallowing
    an attacker to replay some previous token
  - A timeout is enforced and it is properly checked by the server. If
    the server uses an expiration time that is read from a session token
    that is sent by the client, the token must be cryptographically
    protected


For the secure cache test, the methodology is equivalent to the black
box case, as in both scenarios we have full access to the server
response headers and to the HTML code.

## References

**Whitepapers**

  - ASP.NET Forms Authentication: "Best Practices for Software
    Developers" -
    <http://www.foundstone.com/resources/whitepapers/ASPNETFormsAuthentication.pdf>
  - "The FormsAuthentication.SignOut method does not prevent cookie
    reply attacks in ASP.NET applications" -
    <http://support.microsoft.com/default.aspx?scid=kb;en-us;900111>


**Tools**

  - Add N Edit Cookies (Firefox extension):
    <https://addons.mozilla.org/firefox/573/>