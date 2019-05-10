**The idea is to make sure a cookie can only be used by the user who it
was intended for.** In other words, if a hacker gained access to the
cookie he/she would not be able to use it.

The following code samples are for ColdFusion MX, but the principle can
easily be used in other languages.

1\. when the user starts a session, set a cookie named "hash" with a
hash value of the remote IP address and a secret string, for example
"s3cr375tr1ng"

2\. upon each following request made, the application checks whether the
cookie still exists, and whether the value still matches the remote IP

If the values do not match, then you'd delete the rest of the cookie
values and require them to be reset.

**Now for the ColdFusion code**

We're assuming you're using jsessionid because they expire when the
browser closes, and ColdFusion MX

In onSessionStart we set the following cookie

\<cfcookie

`   name="hash" `
`   value="#hash( cgi.remote_addr & "s3cr375tr1ng" )#" `
`   domain=".clickfind.com.au">`

In onRequestStart we have the following code

\<cfif compareNoCase( cookie.hash, hash( cgi.remote_addr &
"s3cr375tr1ng" ) ) neq 0 \>

</cfif>

The above idea was created to secure
[www.clickfind.com.au](http://www.clickfind.com.au), but we like sharing
;-) If you have any improvements or suggestions, please do let us know
[contact us](http://www.clickfind.com.au/contact-us.cfm)