## Content Security Policy (CSP).

Is an W3C specification offering the possbility to instruct the client
browser from which location and/or which type of resources are allowed
to be loaded. To define a loading behavior, the CSP specification use
"directive" where a directive defines a loading behavior for a target
resource type. CSPt helps to detect and mitigate certain types of
attacks, including Cross Site Scripting (XSS) and data injection
attacks. These attacks are used for everything from data theft to site
defacement or distribution of malware

Directives can be specified using HTTP response header (a server may
send more than one CSP HTTP header field with a given resource
representation and a server may send different CSP header field values
with different representations of the same resource or with different
resources) or HTML Meta tag, the HTTP headers below are defined by the
specs:

  - Content-Security-Policy : Defined by W3C Specs as standard header,
    used by Chrome version 25 and later, Firefox version 23 and later,
    Opera version 19 and later.

<!-- end list -->

  - X-Content-Security-Policy : Used by Firefox until version 23, and
    Internet Explorer version 10 (which partially implements Content
    Security Policy).

<!-- end list -->

  - X-WebKit-CSP : Used by Chrome until version 25

## Risk

The risk with CSP can have 2 main sources:

1.  Policies misconfiguration,
2.  Too permissive policies.

## Code reviewer Action

Code reviewer needs to understand what content security policies were
required by application design and how these polices were tested to
ensure they are in use by the application.

## Useful security-related HTTP headers

In most architectures these headers can be set in web servers
configuration
([Apache](http://httpd.apache.org/docs/2.0/mod/mod_headers.html),
\[<http://technet.microsoft.com/pl-pl/library/cc753133(v=ws.10>).aspx
IIS\]), without changing actual application's code. This offers
significantly faster and cheaper method for at least partial mitigation
of existing issues, and an additional layer of defense for new
applications.

| Header name                                                                                                                                                        | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                         | Example                                                                                                          |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------- |
| [Strict-Transport-Security](http://tools.ietf.org/html/rfc6797)                                                                                                    | HTTP Strict-Transport-Security (HSTS) enforces secure (HTTP over SSL/TLS) connections to the server. This reduces impact of bugs in web applications leaking session data through cookies and external links and defends against Man-in-the-middle attacks. HSTS also disables the ability for user's to ignore SSL negotiation warnings.                                                                                                                           | `Strict-Transport-Security: max-age=16070400; includeSubDomains`                                                 |
| [X-Frame-Options](http://tools.ietf.org/html/draft-ietf-websec-x-frame-options-01), [Frame-Options](http://tools.ietf.org/html/draft-ietf-websec-frame-options-00) | Provides [Clickjacking](Clickjacking "wikilink") protection. Values: *deny* - no rendering within a frame, *sameorigin* - no rendering if origin mismatch, *allow-from: DOMAIN* - allow rendering if framed by frame loaded from *DOMAIN*                                                                                                                                                                                                                           | `X-Frame-Options: deny`                                                                                          |
| [X-XSS-Protection](http://blogs.msdn.com/b/ie/archive/2008/07/02/ie8-security-part-iv-the-xss-filter.aspx)                                                         | This header enables the [Cross-site scripting](Cross-site_scripting "wikilink") (XSS) filter built into most recent web browsers. It's usually enabled by default anyway, so the role of this header is to re-enable the filter for this particular website if it was disabled by the user. This header is supported in IE 8+, and in Chrome (not sure which versions). The anti-XSS filter was added in Chrome 4. Its unknown if that version honored this header. | `X-XSS-Protection: 1; mode=block`                                                                                |
| [X-Content-Type-Options](http://blogs.msdn.com/b/ie/archive/2008/09/02/ie8-security-part-vi-beta-2-update.aspx)                                                    | The only defined value, "nosniff", prevents Internet Explorer and Google Chrome from MIME-sniffing a response away from the declared content-type. This also applies to [Google Chrome](http://code.google.com/chrome/extensions/hosting.html), when downloading extensions. This reduces exposure to drive-by download attacks and sites serving user uploaded content that, by clever naming, could be treated by MSIE as executable or dynamic HTML files.       | `X-Content-Type-Options: nosniff`                                                                                |
| [Content-Security-Policy, X-Content-Security-Policy, X-WebKit-CSP](http://www.w3.org/TR/CSP/)                                                                      | [Content Security Policy](Content_Security_Policy "wikilink") requires careful tuning and precise definition of the policy. If enabled, CSP has significant impact on the way browser renders pages (e.g., inline JavaScript disabled by default and must be explicitly allowed in policy). CSP prevents a wide range of attacks, including [Cross-site scripting](Cross-site_scripting "wikilink") and other cross-site injections.                                | `Content-Security-Policy: default-src 'self'`                                                                    |
| [Content-Security-Policy-Report-Only](http://www.w3.org/TR/CSP/)                                                                                                   | Like Content-Security-Policy, but only reports. Useful during implementation, tuning and testing efforts.                                                                                                                                                                                                                                                                                                                                                           | ` Content-Security-Policy-Report-Only: default-src 'self'; report-uri  `<http://loghost.example.com/reports.jsp> |

References: Apache:
<http://httpd.apache.org/docs/2.0/mod/mod_headers.html> IIS :
<http://technet.microsoft.com/pl-pl/library/cc753133(v=ws.10>).aspx