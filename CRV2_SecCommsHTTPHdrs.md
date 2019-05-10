# This is a draft version

## Overview

HTTP headers allow the server to dictate or advise the user agent and
intermediary servers how to handle the content being provided. Some of
these headers can aid a web site in securing itself; these include the
standard Cache-Control headers, and newer specifications like HSTS and
Content Security Policy headers.

## Description

From a security point of view controlling the HTTP headers sent with web
site content can tell the users browser how to store the content, how to
access further content, and how to trust various parts of the content
received by the browser.

Two points to note up front:

1.  Headers can only be trusted over a HTTPS session
2.  This section only covers HTTP response headers

Without HTTPS between the web server and the users browser an attacker
can modify the content or the associated headers. Thus if you were
returning headers specifying that your web site should only be access
over HTTPS, an attacker could remove these headers and the browser would
not receive the information. A web site should not trust HTTP request
headers for security decisions as there are many ways an attacker could
modify these headers (or construct the whole request themselves), so
there is nothing to cover for secure headers coming from the client, as
they are inherently insecure. Of course the cookie header is an
exception to this, but that is because our web site has set the cookie
header to a random value that should only be known during the browsing
session. This section will not cover the cookie header as this is
covered in the session management topic.

### Caching Headers

For business web sites that allow sensitive or confidential information
to be downloaded to the client device, the caching of that sensitive
data will become a security issue. A user accessing their bank account
details does not want an intermediary proxy caching their web pages. A
legal web site does not want copies of sensitive PDF documents stored on
the laptop or smartphone disk storage, only for that device to be lost
and the documents visible to an attacker.

The 'Cache-Control' header tells the users browser how to handle the
content being downloaded. Some browsers can interpret the header values
differently thus the understood header settings to return with content
that must not be cached are:

`Cache-Control: no-store, no-cache`
`Pragma: no-cache`
`Expires: 0`

This should be understood by all browsers (including mobile webviews)
that the content being returned must not be stored to disk cache. Note
that it is possible for intermediate proxies to ignore caching headers
and still cache the content, which is another reason why using
end-to-end HTTPS sessions is important, as the proxies will only have
encrypted versions of the sensitive content.

### Content Security Policy

Cross Site Scripting (XSS) is still one of the most frequent security
issues experienced on web sites, it's A3 on the OWASP Top 10 (2013), and
it covers a variety of ways attackers can bypass the browser same origin
policy to trick the browsers into executing the attackers code. Content
Security Policy headers are designed to allow a web site to inform the
browser where scripts, frames, etc can be sourced from, and are a good
way of mitigating XSS issues.

The structure of the header is as follows:

`Content-Security-Policy: `<directive>` `<sources>

Where the directive tells the browser what type of content is being
controlled, and the source lists the places where the content can
validly be obtained from, for example:

`Content-Security-Policy: script-src 'self' `<https://www.example.com>

... tells the browser that javascript code files (i.e. \*.js files) can
only be sourced from 'self' (i.e. the current web site, note the single
quotes are necessary) or <https://www.example.com>. If the browser
rendering the page finds javascript from some other site, it will fail
to render and flag an error message to the end user. In this way the web
site has prevented the attacker from injecting links to their own
javascript (e.g. "

<script src='http://badguy.com/bad.js'>

</script>

").

The directives controlled by the Content Security Policy include:

|            |                                                                          |
| ---------- | ------------------------------------------------------------------------ |
| Directive  | Description                                                              |
| script-src | Lists the sources where javascript files are allowed to be sourced from. |
| object-src | Lists the sources where flash and other plugin objects are allowed from. |
| frame-src  | Lists the sources where frames are allowed from.                         |
| style-src  | Lists the sources where CSS files are allowed from.                      |

If a directive is not specified then the default is wide open, all
sources are allowed. If you do not wish to provide a directive for all
options then you can specify a default-src which will then apply to all
unspecified directives, for example:

`Content-Security-Policy: default-src 'self'`

... forces all scripts, frames, objects, etc to be sourced from the
current web site. When specifying a URL the scheme is enforced, so
stating <https://www.example.com> will prevent any items coming from
www.example.com over HTTP (i.e. without SSL). You can also provide a
wildcard on the leftmost portion of the domain, e.g.
<https://>\*.example.com. Multiple directives are separated by
semi-colons, e.g.

`Content-Security-Policy: script-src 'self' `<https://www.example.com>`; frame-src 'self' `<https://frames.example.com>

If you wished to completely disable an option, for example you don't
want any frames in your page, you can disable a directive using the
'none' keyword:

`Content-Security-Policy: frame-src 'none'`

#### Preventing Inlining

A further feature of Content Security Policy is to tell the browser not
to allow inline javascript code, or evals. As well as driving better
programming practices by separating scripting code from the display
markup, this option allows inline scripting to be disabled (a major
vector of XSS, e.g.

<script>

alert(1);

</script>

). By providing a script-src or style-src (in the case of CSS) the
Content Security Policy automatically bans inline scripts (javascript
and CSS). If you wish to allow inline scripting, or inline use of the
eval function (which can construct javascript) you have to explicitly
specify 'unsafe-inline' or 'unsafe-eval', e.g.

`Content-Security-Policy: script-src 'self' 'unsafe-inline'`

#### Applying CSP To Web Pages

When using Content Security Policy, note that the header has to be
included in every web page. This can easily be achieved through
configuration of common frameworks (e.g. mod_headers in Apache) if the
policy is the same for the entire site. If the Content Security Policy
header is being dynamically created for each web page, be aware that
directives cannot be repeated, if the header specifies the directive the
second listing will be ignored.

The header varies slightly between IE and other browsers, for IE you
must specify "X-Content-Security-Policy", whilst all other browsers use
"Content-Security-Policy".

#### Using Content Security Policy Reporting

The Content Security Policy allows the browser to report any violations
of the defined sources. The CSP header can include the "report-uri"
directive as in the following:

`Content-Security-Policy: default-src 'self'; report-uri /csp_receiver;`

With this directive, if the browser experiences any page/content that
violates the directive it will send a JSON report to the defined URL
similar to the following:

`{`
`  "csp-report": {`
`    "document-uri": "`<https://www.example.com/default.html>`",`
`    "referrer": "`<https://www.example.com/>`",`
`    "blocked-uri": "`<https://bad.guy.com/bad_guy.js>`",`
`    "violated-directive": "script-src 'self' `<https://www.example.com>`",`
`    "original-policy": "script-src 'self' `<https://www.example.com>`; report-uri `<https://www.example.com/csp_receiver>`"`
`  }`
`} `

This reporting feature can be used to determine any attacks occurring on
your content. Also note that if you specify HTTPS in the report-uri
scheme, and the receiver URI is on the current web server, the report
JSON can be authenticated as the cookie will be passed over the secure
session.

If you simply wish to trail the CSP headers, i.e. not actually have the
browser enforce the constraints encase it breaks anything, you can
instead use the "Content-Security-Policy-Report-Only" header. This will
tell the browser to understand the directives and monitor for policy
violations, but in the case of a violation the browser will still render
the page as if the header was not specified, instead it will send the
JSON report. This is a great way to trail the CSP headers on live
traffic to see what breaches are currently occurring, or to ensure you
have configured your CSP headers before deployment. An example of this
is:

`Content-Security-Policy-Report-Only: default-src 'self'; report-uri /csp_receiver;`

### HTTP Strict Transport Security

HTTP Strict Transport Security (HSTS) is an opt-in security enhancement
that is specified by a web application through the use of a special
response header. When the browser receives the HSTS header it will
prevent any subsequent requests from being sent over HTTP to the web
site, instead only using HTTPS, for the timeframe specified in the
header. It also prevents HTTPS click through prompts on browsers.

Simple example, using a long (1 year) max-age:

` Strict-Transport-Security: max-age=31536000`

If all present and future subdomains will be HTTPS:

` Strict-Transport-Security: max-age=31536000; includeSubDomains`

If the site owner would like their domain to be included in the
maintained by Chrome (and used by Firefox and Safari), then use:

` Strict-Transport-Security: max-age=31536000; includeSubDomains; preload`

The 'preload' flag indicates the site owner's consent to have their
domain preloaded. The site owner still needs to then go and submit the
domain to the list.

Use caution when setting excessively strict STS policies. Including
subdomains should only be used in environments where all sites within
your organization for the given domain name require ssl. Max-age limits
should be carefully considered as infrequent visitors may find your site
inaccessible if you relax your policy.

Before enabling includeSubDomains, also consider the impact of any
existing DNS CNAME records for CDNs, email services, or other 3rd party
services. Since includeSubDomains will force such CNAME subdomains to
<https://> it's likely the browser will throw a domain-mismatch error,
which is hard to reverse because of the browser caching nature of HSTS.

## What to Review

When reviewing code modules from an HTTP header security point of view,
some common issues to look out for include:

  - Do not perform security decisions based on client request HTTP
    headers (apart from the cookie headers specified as HTTPOnly)
  - Do not trust request headers not passed over HTTPS connections.
  - Ensure you validate the format (length, characters, etc) of the
    header value before processing it.
  - For sensitive content, remember to specify the relevant caching
    headers so standard browsers do not store the content to disk.
    Remember, however, that non-standard browsers or intermediate
    proxies can ignore the caching headers, thus delivering sensitive
    content over HTTPS provides more protection.
  - Consider providing Content Security Policy headers for your site.
  - Ensure CSP headers are provided for all web pages, typically using
    web framework configuration.
  - Test the CSP header settings using the
    "Content-Security-Policy-Report-Only" header to ensure current web
    usage is not affected.
  - Include CSP header testing in testing, adding specific test cases to
    ensure violations are caught.
  - If CSP headers are being used to prevent inline XSS, do not relax
    other protections such as input validation or output encoding.
  - Note there are two ways to ensure a web sites' pages are loaded
    using HTTPS only:
      - Setting "Strict-Transport-Security" headers, which only need to
        be specified once per 'max-age' timeframe and is remembered by
        the browser for subsequent get requests
      - Setting CSP header to specify an HTTPS domain, e.g.
        "Content-Security-Policy: default-src 'self' https:", which must
        be specified on every page, and only affects artifacts loaded
        for the current page, not subsequent get requests.

## References

  - <https://www.owasp.org/index.php/HTTP_Strict_Transport_Security>
  - <http://content-security-policy.com/>
  - <http://www.html5rocks.com/en/tutorials/security/content-security-policy/>
  - <http://www.w3.org/TR/CSP/>