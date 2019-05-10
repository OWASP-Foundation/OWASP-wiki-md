# Browser Defense/Same Origin Policy

Same Origin Policy (SOP), also called Single Origin Policy is a part of
web application security model. Same Origin Policy has vulnerabilities
that the code reviewer needs to take into consideration. SOP covers
three main areas of web development, Trust, Authority, and Policy. Same
Origin Policy is made of the combination of three components (Scheme,
Hostname and Port).

Internet Explorer has two major exceptions when it comes to same origin
policy

1.  Trust Zones: if both domains are in highly trusted zone e.g,
    corporate domains, then the same origin limitations are not applied
2.  Port: IE doesn't include port into Same Origin components, therefore
    <http://yourcompany.com:81/index.html> and
    <http://yourcompany.com/index.html> are considered from same origin
    and no restrictions are applied. Microsoft does that port number
    into account for XMLHttpRequest.

These exceptions are non-standard and not supported in any of other
browser but would be helpful if developing an app for Windows RT (or) IE
based web application.

## URL

### URL Examples

The following figure displays two example URIs
(`foo://username:password@example.com:8042/over/there/index.dtb?type=animal&name=narwhal#nose`
and <urn:example:animal:ferret:nose>) and their component parts. (The
examples are derived from RFC 3986 — STD 66, chapter 3).

```
  foo://username:password@example.com:8042/over/there/index.dtb?type=animal&name=narwhal#nose
  _/   _______________/ _________/ __/            ___/ _/ ______________________/ __/

|
|
|
|
|
|
|
|

|       userinfo         hostname  port
|
|          query          fragment

|    ________________________________/_____________
|____
|/ __/        __/

|
|
|
|
|
|
|

|
|
|
|
|
|
|
scheme              authority                    path
|
|    interpretable as keys
 name   _______________________________________________
|____
|/       ____/     _____/

|
|
|
|
|
|

|                 hierarchical part
|
|    interpretable as values

|
|
|

|            path               interpretable as filename
|

|   ___________
|____________
|
  / \ /                        \
|
  urn:example:animal:ferret:nose               interpretable as extension

                path
         _________
|________
 scheme /                  \
  name  userinfo  hostname       query
  _
|__   ___
|__   ____
|____   _____
|_____
 /    \ /      \ /         \ /           \
 <nowiki>mailto:username@example.com?subject=Topic</nowiki>
```

1.  Scheme/protocol name
2.  Indicator of a hierarchical URL (constant)_
3.  Credentials to access the resource (optional)
4.  Server to retrieve the data from
5.  Port number to connect to (optional)
6.  Hierarchical Unix path to a resource
7.  “Query string” parameters (optional)
8.  “Fragment identifier” (optional)

If application allows user-supplied data in the URL then the code
reviewer needs to make sure the path, query or Fragment Id Code data is
validated.

Make sure user-supplied scheme name or authority section has good input
validation. This is a major code injection and phishing risk. Only
permit prefixes needed by the application. Do not use blacklisting. Code
reviewer should make sure only whitelisting is used for validation.

Make sure authority section should only contain alphanumerics, “-“, and
“.” And be followed by “/”, “?”,”\#”. The risk here an IDN homograph
attack.

Code reviewer needs to make sure the programmer is not assuming default
behavior because the programmers browser properly escapes a particular
character or browser standard says the character will be escaped
properly before allowing any URL-derived values are put inside a
database query or the URL is echoed back to the user.

## Trust

For example consider the HTML form element:

`form method="POST" action="`<https://example.com/login>`">`
`   ... `<input type="password">` ...`
`  `

</form>

When the user submits the form the document declares that it trusts the
confidentiality of information sent to that URL. Code reviewer needs to
make sure appropriate levels of trust are being used.

## Authority

Resources with a MIME type of image/png are treated as images and
resources with MIME type of text/html are treated as HTML documents. Web
applications can limit that content's authority by restricting its MIME
type. For example, serving user-generated content as image/png is less
risky than serving user-generated content as text/html.

## Policy

Privileges on document and resources should grant or withhold privileges
from origins as a whole (rather than discriminating between individual
documents within an origin). Withholding privileges is ineffective
because the document without the privilege can usually obtain the
privilege anyway because SOP does not isolate documents within an
origin.