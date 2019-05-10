The OWASP Foundation is deeply concerned about the risk associated with
increasingly useful and powerful browsers. We are seeking to support the
browser vendors with research, resources, and ideas. At our recent
Summit in Portugal, OWASP's Intrinsic Security Working Group (ISWG) met
to discuss the key security challenges in browsers. The ISWG is a group
of web application security specialists that contribute their time to
OWASP to try to make the Internet a safer place.

We'd like to identify practical solutions to some of the security issues
that could affect security of both browser users and organizations with
web applications. The following recommendations are some initial ideas
we'd like to help get implemented. We selected these ideas as good
starting points because they are either relatively simple to implement
or they offer a great deal of protection.

The first protection the ISWG recommends browsers implement is the
HTTPOnly flag. The majority of major browsers currently offer some level
of protection when applications use the HTTPOnly flag. Unfortunately,
because the implementations are not complete, it is still possible under
certain circumstances to bypass the mechanism. When this flag is turned
on, JavaScript should not be able to read or write to the cookie object
in the page's DOM. Also, it is possible to read cookie data from
XmlHttpRequest response data even with HTTPOnly on. Ideally, no
JavaScript could access or modify any cookie data from a cookie with the
HTTPOnly flag.

The second protection the ISWG is recommending is to disable
"autocomplete" features within cross-domain iframes. Browser users
utilize this feature so they don't have to remember passwords for
multiple sites or save themselves the effort of repeatedly typing in the
same credentials. If a browser automatically populates a login form for
a site the user trusts, an attacker can trick the user into clicking the
"login" button and execute fully authenticated functionality on the
attacker's behalf with the victim's credentials.

The final protection the ISWG is recommending is to implement of "jail"
tags. Jail tags could allow applications to reliably mark pieces of the
page where untrusted user input appears without introducing any risk of
cross-site scripting. The future of the web is more inter-connectivity
and more user content, so the need for this type of protection is
critical.

Thanks for your time,
OWASP Intrinsic Security Working Group
<http://www.owasp.org/>