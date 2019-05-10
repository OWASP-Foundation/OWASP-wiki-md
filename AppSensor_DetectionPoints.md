# About This Document

These detection points are part of the [OWASP
AppSensor](http://www.owasp.org/index.php/Category:OWASP_AppSensor_Project)
project which advocates bringing intelligent intrusion detection inside
the application. These detection points can be used to identify a
malicious user that is probing for vulnerabilities or weaknesses within
your application.

[Read
more](http://www.owasp.org/index.php/ApplicationLayerIntrustionDetection)
about why application logging is the way to go.

__TOC__

# Detection Points

<div id="re">

</div>

## RequestException

<div id="RE1">

</div>

### RE1: Unexpected HTTP Command

<table style="border-style:double;border-width:3px;" >

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

ID

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

RE1

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Title

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Unexpected HTTP Command

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Category

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

RequestException

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Description

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

An HTTP request is received which contains unexpected/disallowed
commands.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Considerations

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

A list of accepted commands should be generated (i.e. GET and POST) and
all other HTTP commands should generate an event. See [HTTP/1.1: Method
Definitions](http://www.w3.org/Protocols/rfc2616/rfc2616-sec9.html).

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Tuning

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Browsers and proxies using the HEAD method to check whether the content
of a file has changed.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Examples

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Instead of a GET or POST request, the user sends a TRACE request to the
application.

Cross references:

  - [OWASP ModSecurity Core Rule Set
    Project](:Category:OWASP_ModSecurity_Core_Rule_Set_Project "wikilink")
    v2.2.7
      - (30b) HTTP Policy Enforcement: Method Is Not Allowed by Policy
        (960032)
      - (40e) AppSensor Detection Points: Invalid Request Method for
        Resource (981088)

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Code

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

[Java](http://www.owasp.org/index.php/AppSensor_DetectionPoint_RE1#java)
[.Net](http://www.owasp.org/index.php/AppSensor_DetectionPoint_RE1#net)
[PHP](http://www.owasp.org/index.php/AppSensor_DetectionPoint_RE1#php)

</td>

</tr>

</table>

<div id="RE2">

</div>

### RE2: Attempt to Invoke Unsupported HTTP Method

<table style="border-style:double;border-width:3px;" >

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

ID

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

RE2

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Title

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Attempt to Invoke Unsupported HTTP Method

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Category

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

RequestException

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Description

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

An HTTP request is received which contains a non-existent HTTP command
(does not match anything in this list: HEAD, GET, POST, PUT, DELETE,
TRACE, OPTIONS, CONNECT).

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Considerations

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

\-

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Tuning

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

\-

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Examples

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Instead of a GET or POST request, the user sends a TEST request to the
application (TEST is not a valid HTTP request method).

Cross references:

  - [OWASP ModSecurity Core Rule Set
    Project](:Category:OWASP_ModSecurity_Core_Rule_Set_Project "wikilink")
    v2.2.7
      - (40e) AppSensor Detection Points: Attempt to Invoke Unsupported
        HTTP Method (981087)

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Code

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

[Java](http://www.owasp.org/index.php/AppSensor_DetectionPoint_RE2#java)
[.Net](http://www.owasp.org/index.php/AppSensor_DetectionPoint_RE2#net)
[PHP](http://www.owasp.org/index.php/AppSensor_DetectionPoint_RE2#php)

</td>

</tr>

</table>

<div id="RE3">

</div>

### RE3: GET When Expecting POST

<table style="border-style:double;border-width:3px;" >

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

ID

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

RE3

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Title

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

GET When Expecting POST

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Category

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

RequestException

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Description

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

A page which is expecting only POST requests, is requested by HTTP
method GET.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Considerations

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Some pages may be designed to receive both GET and POST requests.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Tuning

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Some resources may allow both GET and POST methods e.g. an edit form may
be hyperlinked using a parameter value defining the record to be edited,
but the form is submitted by POST to itself. Users may bookmark a page
that is the result of a POST and return to it at a later date.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Examples

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

The user sends a GET request to a page which has only been used for
POSTs.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Code

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

[Java](http://www.owasp.org/index.php/AppSensor_DetectionPoint_RE3#java)
[.Net](http://www.owasp.org/index.php/AppSensor_DetectionPoint_RE3#net)
[PHP](http://www.owasp.org/index.php/AppSensor_DetectionPoint_RE3#php)

</td>

</tr>

</table>

<div id="RE4">

</div>

### RE4: POST When Expecting GET

<table style="border-style:double;border-width:3px;" >

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

ID

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

RE4

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Title

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

POST When Expecting GET

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Category

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

RequestException

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Description

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

A page which is expecting only GET requests, receives a POST.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Considerations

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

\-

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Tuning

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

(same as RE3)

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Examples

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

The user utilizes a proxy tool to build a custom POST request and sends
it to a page which has been accessed by GET requests.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Code

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

[Java](http://www.owasp.org/index.php/AppSensor_DetectionPoint_RE4#java)
[.Net](http://www.owasp.org/index.php/AppSensor_DetectionPoint_RE4#net)
[PHP](http://www.owasp.org/index.php/AppSensor_DetectionPoint_RE4#php)

</td>

</tr>

</table>

<div id="RE5">

</div>

### RE5: Additional/Duplicated Data in Request

<table style="border-style:double;border-width:3px;" >

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

ID

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

RE5

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Title

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Additional/Duplicated Data in Request

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Category

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

RequestException

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Description

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Additional unexpected parameters or HTTP headers, or duplicates, are
received with the request.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Considerations

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Additional parameters may be an attempt to override values or to exploit
unexposed functionality. Duplicated parameters may be an indication of
attempted HTTP parameter pollution.

Beware of firing this detector when additional cookies, not used by the
application, are found (as opposed to duplicated cookies) since these
may relate to third-party code (e.g. advertisements, analytics) or some
other application.

Note that extra HTTP headers may be added by intermediate proxies, and
unless the network configuration is fixed (an internal network perhaps),
additional headers cannot be controlled and thus cannot be used to infer
existence of a potential attacker.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Tuning

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Links from third party sites/services may included additional parameters
(e.g. from search engines, from advertisements). Additional cookies
headers may be added by other applications or by third parties such as
advertisers, and there may be very little control over these. Additional
HTTP headers may be added by intermediate network devices (e.g. for
traffic management).

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Examples

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Example 1: Additional form or URL parameters submitted with request
(e.g. debug=1, servervariable=2000).

Example 2: A parameter is defined more than once in the URL Query
String.

Example 3: An HTTP header is duplicated.

Example 4: An additional HTTP header is found.

Example 5: A URL path parameter with the same name as a form parameter
is sent with the request.

Cross references:

  - [OWASP ModSecurity Core Rule Set
    Project](:Category:OWASP_ModSecurity_Core_Rule_Set_Project "wikilink")
    v2.2.7
      - (40e) AppSensor Detection Points: Invalid Number of Parameters -
        Missing Parameter(s) (981089)
      - (40e) AppSensor Detection Points: Invalid Number of Parameters -
        Additional Parameter(s) (981090)
      - (40e) AppSensor Detection Points: Invalid Parameter Name(s)
        (981091)

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Code

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

[Java](http://www.owasp.org/index.php/AppSensor_DetectionPoint_RE5#java)
[.Net](http://www.owasp.org/index.php/AppSensor_DetectionPoint_RE5#net)
[PHP](http://www.owasp.org/index.php/AppSensor_DetectionPoint_RE5#php)

</td>

</tr>

</table>

<div id="RE6">

</div>

### RE6: Data Missing from Request

<table style="border-style:double;border-width:3px;" >

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

ID

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

RE6

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Title

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Data Missing from Request

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Category

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

RequestException

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Description

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Expected parameters or HTTP headers are missing from the request.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Considerations

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Bookmarking and use of a browser's "back button" can lead to requests
without the expected parameters.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Tuning

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

A bookmarked page may be missing the required POST parameters (see also
RE3). Users may choose to send a blank or different User Agent header
value.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Examples

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Example 1: A page is requested without any of the required form
parameters.

Example 2: The HTTP-Accept header is not present in a request.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Code

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

[Java](http://www.owasp.org/index.php/AppSensor_DetectionPoint_RE6#java)
[.Net](http://www.owasp.org/index.php/AppSensor_DetectionPoint_RE6#net)
[PHP](http://www.owasp.org/index.php/AppSensor_DetectionPoint_RE6#php)

</td>

</tr>

</table>

<div id="RE7">

</div>

### RE7: Unexpected Quantity of Characters in Parameter

<table style="border-style:double;border-width:3px;" >

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

ID

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

RE7

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Title

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Unexpected Quantity of Characters in Parameter

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Category

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

RequestException

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Description

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

The user provides a parameter value with a large number of characters.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Considerations

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

\-

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Tuning

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

If the input field does not have client-side validation and/or MAXLENGTH
attributes, a user might inadvertently copy in some text that is longer
than expected.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Examples

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Example 1: The user submits a form field with more characters than the
form's maxlength attribute and client-side validation would allow.

Example 2: The user submits data in a form's hidden field which is
longer than expected.

Cross references:

  - [OWASP ModSecurity Core Rule Set
    Project](:Category:OWASP_ModSecurity_Core_Rule_Set_Project "wikilink")
    v2.2.7
      - (40e) AppSensor Detection Points: Invalid Parameter Length -
        Value Is Below Normal Range (981092)
      - (40e) AppSensor Detection Points: Invalid Parameter Length -
        Value Is Above Normal Range (981093)

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Code

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

[Java](http://www.owasp.org/index.php/AppSensor_DetectionPoint_RE7#java)
[.Net](http://www.owasp.org/index.php/AppSensor_DetectionPoint_RE7#net)
[PHP](http://www.owasp.org/index.php/AppSensor_DetectionPoint_RE7#php)

</td>

</tr>

</table>

<div id="RE8">

</div>

### RE8: Unexpected Type of Characters in Parameter

<table style="border-style:double;border-width:3px;" >

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

ID

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

RE8

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Title

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Unexpected Type of Characters in Parameter

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Category

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

RequestException

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Description

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

The user provides a parameter value containing characters outwith the
expected range.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Considerations

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

\-

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Tuning

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Text fields may include text from copy and paste operations that contain
illegal characters.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Examples

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Example 1: The user sends an HTTP header containing a line break
character.

Example 2: The user sends a URL parameter value that contains ASCII
characters below 20 or above 7E.

Cross references:

  - [OWASP ModSecurity Core Rule Set
    Project](:Category:OWASP_ModSecurity_Core_Rule_Set_Project "wikilink")
    v2.2.7
      - (40e) AppSensor Detection Points: Invalid Character(s) in
        Payload - Expecting Digits (981094)
      - (40e) AppSensor Detection Points: Invalid Character(s) in
        Payload - Expecting Letters (981095)
      - (40e) AppSensor Detection Points: Invalid Character(s) in
        Payload - Expecting AlphNumeric (981096)
      - (40e) AppSensor Detection Points: Invalid Character(s) in
        Payload - Expecting Email (981097)
      - (40e) AppSensor Detection Points: Invalid Character(s) in
        Payload - Expecting Path (981103)
      - (40e) AppSensor Detection Points: Invalid Character(s) in
        Payload - Expecting Url (981104)
      - (40e) AppSensor Detection Points: Invalid Character(s) in
        Payload - Expecting Flag (981110)
      - (40e) AppSensor Detection Points: Invalid Character(s) in
        Payload - Expecting SafeText (981105)

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Code

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

[Java](http://www.owasp.org/index.php/AppSensor_DetectionPoint_RE8#java)
[.Net](http://www.owasp.org/index.php/AppSensor_DetectionPoint_RE8#net)
[PHP](http://www.owasp.org/index.php/AppSensor_DetectionPoint_RE8#php)

</td>

</tr>

</table>

<div id="AE">

</div>

## AuthenticationException

<div id="AE1">

</div>

### AE1: Use of Multiple Usernames

<table style="border-style:double;border-width:3px;" >

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

ID

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

AE1

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Title

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Use of Multiple Usernames

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Category

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

AuthenticationException

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Description

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Multiple usernames are attempted when logging into the application.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Considerations

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

The assignment of login attempts to a user can be based on a sessionID
given to the user when they first visit the website. Correlating based
on IP address is difficult since multiple users could be using the site
from the same IP address (e.g. corporate NAT).

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Tuning

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

\-

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Examples

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

User first tries username 'bob', then username 'sue', then 'steve', etc.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Code

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

[Java](http://www.owasp.org/index.php/AppSensor_DetectionPoint_AE1#java)
[.Net](http://www.owasp.org/index.php/AppSensor_DetectionPoint_AE1#net)
[PHP](http://www.owasp.org/index.php/AppSensor_DetectionPoint_AE1#php)

</td>

</tr>

</table>

<div id="AE2">

</div>

### AE2: Multiple Failed Passwords

<table style="border-style:double;border-width:3px;" >

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

ID

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

AE2

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Title

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Multiple Failed Passwords

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Category

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

AuthenticationException

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Description

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

For a single username, multiple bad passwords, or other authentication
credentials, are entered.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Considerations

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

See [Popularity is
Everything](http://www.eecs.harvard.edu/~michaelm/postscripts/hotsec2010.pdf)
section 4 - Attack-Detection Scenarios for ideas about tracking use of
unsuccessful passwords and looking whether these are used against
multiple accounts.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Tuning

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

A users providing the same wrong password more than once may be
different to different wrong passwords. See [Account Lockout, Bill
Cheswick, Episode 76, OWASP Podcast,
September 22, 2010](http://www.owasp.org/index.php/OWASP_Podcast#tab=Latest_Shows).

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Examples

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Example 1: User tries username:password combination of 'user:pass1',
'user:pass2', 'user:pass3', etc.

Example 2: Multiple failed PINs are attempted for the same customer
account.

Example 3: In an online banking application, several invalid mobile
authentication codes, transaction verification codes or transaction
authentication numbers are submitted.

Example 4: A user provides the correct password, but repeatedly fails to
provide the required second password correctly.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Code

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

[Java](http://www.owasp.org/index.php/AppSensor_DetectionPoint_AE2#java)
[.Net](http://www.owasp.org/index.php/AppSensor_DetectionPoint_AE2#net)
[PHP](http://www.owasp.org/index.php/AppSensor_DetectionPoint_AE2#php)

</td>

</tr>

</table>

<div id="AE3">

</div>

### AE3: High Rate of Login Attempts

<table style="border-style:double;border-width:3px;" >

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

ID

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

AE3

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Title

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

High Rate of Login Attempts

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Category

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

AuthenticationException

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Description

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

The rate of login attempts becomes too high (possibly indicating an
automated login attack).

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Considerations

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

The threshold should relate to a limit and period appropriate to the
application (e.g. total number in a second or minute or hour).

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Tuning

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

\-

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Examples

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

User sends the following login attempts within 1 second - 'user1:pass1',
'user1:pass2', 'user2:pass3', 'user2:pass4'.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Code

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

[Java](http://www.owasp.org/index.php/AppSensor_DetectionPoint_AE3#java)
[.Net](http://www.owasp.org/index.php/AppSensor_DetectionPoint_AE3#net)
[PHP](http://www.owasp.org/index.php/AppSensor_DetectionPoint_AE3#php)

</td>

</tr>

</table>

<div id="AE4">

</div>

### AE4: Unexpected Quantity of Characters in Username

<table style="border-style:double;border-width:3px;" >

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

ID

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

AE4

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Title

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Unexpected Quantity of Characters in Username

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Category

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

AuthenticationException

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Description

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

The user provides a username with a large number of characters.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Considerations

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

\-

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Tuning

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

(same as RE7)

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Examples

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

The user sends a username that is 200 characters long when 6-8 are
expected.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Code

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

[Java](http://www.owasp.org/index.php/AppSensor_DetectionPoint_AE4#java)
[.Net](http://www.owasp.org/index.php/AppSensor_DetectionPoint_AE4#net)
[PHP](http://www.owasp.org/index.php/AppSensor_DetectionPoint_AE4#php)

</td>

</tr>

</table>

<div id="AE5">

</div>

### AE5: Unexpected Quantity of Characters in Password

<table style="border-style:double;border-width:3px;" >

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

ID

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

AE5

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Title

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Unexpected Quantity of Characters in Password

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Category

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

AuthenticationException

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Description

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

The user provides a password with a large number of characters.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Considerations

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Higher limits may be required for sites which allow users to have pass
phrases.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Tuning

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

(same as RE7)

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Examples

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Example 1: The user sends a password that is 200 characters long, when
5-20 are expected.

Example 2: The user sends a PIN of 30 characters.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Code

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

[Java](http://www.owasp.org/index.php/AppSensor_DetectionPoint_AE5#java)
[.Net](http://www.owasp.org/index.php/AppSensor_DetectionPoint_AE5#net)
[PHP](http://www.owasp.org/index.php/AppSensor_DetectionPoint_AE5#php)

</td>

</tr>

</table>

<div id="AE6">

</div>

### AE6: Unexpected Type of Character in Username

<table style="border-style:double;border-width:3px;" >

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

ID

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

AE6

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Title

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Unexpected Type of Character in Username

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Category

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

AuthenticationException

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Description

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

The user provides a username which contains characters outwith the
expected range.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Considerations

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Any characters below hex value 20 or above 7E are often considered
illegal (decimal values of below 32 or above 126).

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Tuning

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Users may be confused between a username, customer identification code
and their account number, or even between offline and online
identifiers. Mis-typing might add a character like "\]" or "\#" if these
are adjacent to the ENTER/CR key. Whitespace may be appended to values
when copied from a spreadsheet cell (e.g. a line feed character when
cell values are copied and pasted from Excel). A password may be put in
the username field by accident.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Examples

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

The user sends a username that contains ASCII non-printable characters
such as the NULL byte.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Code

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

[Java](http://www.owasp.org/index.php/AppSensor_DetectionPoint_AE6#java)
[.Net](http://www.owasp.org/index.php/AppSensor_DetectionPoint_AE6#net)
[PHP](http://www.owasp.org/index.php/AppSensor_DetectionPoint_AE6#php)

</td>

</tr>

</table>

<div id="AE7">

</div>

### AE7: Unexpected Type of Character in Password

<table style="border-style:double;border-width:3px;" >

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

ID

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

AE7

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Title

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Unexpected Type of Character in Password

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Category

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

AuthenticationException

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Description

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

The user provides a password containing characters outwith the expected
range.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Considerations

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Examples include null byte, and characters which need the ALT key to be
used.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Tuning

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

(same as AE6)

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Examples

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

The user sends a password that contains ASCII characters below 20 or
above 7E.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Code

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

[Java](http://www.owasp.org/index.php/AppSensor_DetectionPoint_AE7#java)
[.Net](http://www.owasp.org/index.php/AppSensor_DetectionPoint_AE7#net)
[PHP](http://www.owasp.org/index.php/AppSensor_DetectionPoint_AE7#php)

</td>

</tr>

</table>

<div id="AE8">

</div>

### AE8: Providing Only the Username

<table style="border-style:double;border-width:3px;" >

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

ID

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

AE8

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Title

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Providing Only the Username

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Category

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

AuthenticationException

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Description

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

The user submits a POST request which only contains the username
variable. The password variable has been removed.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Considerations

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

This is different from only providing the username in the login form
since in that case the password variable would be present and empty.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Tuning

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

\-

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Examples

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

The user utilizes a proxy tool to remove the password variable from the
submitted POST request.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Code

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

[Java](http://www.owasp.org/index.php/AppSensor_DetectionPoint_AE8#java)
[.Net](http://www.owasp.org/index.php/AppSensor_DetectionPoint_AE8#net)
[PHP](http://www.owasp.org/index.php/AppSensor_DetectionPoint_AE8#php)

</td>

</tr>

</table>

<div id="AE9">

</div>

### AE9: Providing Only the Password

<table style="border-style:double;border-width:3px;" >

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

ID

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

AE9

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Title

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Providing Only the Password

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Category

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

AuthenticationException

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Description

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

The user submits a POST request which only contains the password
variable. The username variable has been removed.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Considerations

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

This is different from only providing the password in the login form
since in that case the username variable would be present and empty.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Tuning

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

\-

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Examples

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

The user utilizes a proxy tool to remove the username variable from the
submitted POST request.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Code

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

[Java](http://www.owasp.org/index.php/AppSensor_DetectionPoint_AE9#java)
[.Net](http://www.owasp.org/index.php/AppSensor_DetectionPoint_AE9#net)
[PHP](http://www.owasp.org/index.php/AppSensor_DetectionPoint_AE9#php)

</td>

</tr>

</table>

<div id="AE10">

</div>

### AE10: Additional POST Variable

<table style="border-style:double;border-width:3px;" >

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

ID

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

AE10

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Title

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Additional POST Variable

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Category

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

AuthenticationException

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Description

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Additional, unexpected POST variables are received during an
authentication request.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Considerations

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

\-

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Tuning

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

(same as RE5)

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Examples

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

The user utilizes a proxy tool to add the POST variable of 'admin=true'
to the request.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Code

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

[Java](http://www.owasp.org/index.php/AppSensor_DetectionPoint_AE10#java)
[.Net](http://www.owasp.org/index.php/AppSensor_DetectionPoint_AE10#net)
[PHP](http://www.owasp.org/index.php/AppSensor_DetectionPoint_AE10#php)

</td>

</tr>

</table>

<div id="AE11">

</div>

### AE11: Missing POST Variable

<table style="border-style:double;border-width:3px;" >

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

ID

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

AE11

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Title

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Missing POST Variables

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Category

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

AuthenticationException

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Description

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Expected POST variables are not present within the submitted
authentication request.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Considerations

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

\-

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Tuning

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

(same as RE6)

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Examples

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

The user utilizes a proxy tool to remove an additional POST variable,
such as 'guest=true', from the POST request.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Code

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

[Java](http://www.owasp.org/index.php/AppSensor_DetectionPoint_AE11#java)
[.Net](http://www.owasp.org/index.php/AppSensor_DetectionPoint_AE11#net)
[PHP](http://www.owasp.org/index.php/AppSensor_DetectionPoint_AE11#php)

</td>

</tr>

</table>

<div id="AE12">

</div>

### AE12: Utilization of Common Usernames

<table style="border-style:double;border-width:3px;" >

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

ID

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

AE12

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Title

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Utilization of Common Usernames

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Category

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

AuthenticationException

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Description

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Common dictionary usernames are used to attempt to log into the
application.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Considerations

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

\-

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Tuning

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Common usernames might be allowed during self-registration or when
editing account details.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Examples

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Log in attempted with usernames "administrator", then "admin", then
"test"

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Code

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

[Java](http://www.owasp.org/index.php/AppSensor_DetectionPoint_AE12#java)
[.Net](http://www.owasp.org/index.php/AppSensor_DetectionPoint_AE12#net)
[PHP](http://www.owasp.org/index.php/AppSensor_DetectionPoint_AE12#php)

</td>

</tr>

</table>

<div id="AE13">

</div>

### AE13: Deviation from Normal GEO Location

<table style="border-style:double;border-width:3px;" >

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

ID

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

AE13

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Title

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Deviation from Normal GEO Location

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Category

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

AuthenticationException

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Description

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

In some applications, most users log in from one or a just a few
geographic locations. If the application learns these GeoIP locations,
it can then detect when a user is logging into the application from a
different location. This would help to identify possible account
hijacking attacks (from phishing, banking trojans).

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Considerations

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Use of applications while mobile.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Tuning

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

\-

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Examples

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Example 1: A banking customer's IP address has never been seen before
when they log in.

Example 2: A system attempts to authenticate to web services from a
different country.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Code

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

[Java](http://www.owasp.org/index.php/AppSensor_DetectionPoint_AE13#java)
[.Net](http://www.owasp.org/index.php/AppSensor_DetectionPoint_AE13#net)
[PHP](http://www.owasp.org/index.php/AppSensor_DetectionPoint_AE13#php)

</td>

</tr>

</table>

<div id="SE">

</div>

## SessionException

<div id="SE1">

</div>

### SE1: Modifying Existing Cookie

<table style="border-style:double;border-width:3px;" >

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

ID

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

SE1

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Title

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Modifying Existing Cookie

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Category

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

SessionException

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Description

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

A request is received containing a cookie with a modified value.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Considerations

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

This could be determined if the cookie is modified to an illegal value.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Tuning

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

In a poorly designed application, the length of the cookie value, or the
combined size of all the cookies, might possibly exceed that which is
supported.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Examples

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Example 1: The user utilizes a proxy tool to change the encrypted cookie
to an alternative value which does not properly decode within the
application.

Example 2: The user modifies an unencrypted cookie and sets an illegal
value for a particular variable.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Code

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

[Java](http://www.owasp.org/index.php/AppSensor_DetectionPoint_SE1#java)
[.Net](http://www.owasp.org/index.php/AppSensor_DetectionPoint_SE1#net)
[PHP](http://www.owasp.org/index.php/AppSensor_DetectionPoint_SE1#php)

</td>

</tr>

</table>

<div id="SE2">

</div>

### SE2: Adding New Cookie

<table style="border-style:double;border-width:3px;" >

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

ID

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

SE2

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Title

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Adding New Cookie

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Category

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

SessionException

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Description

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

A request is received which contains additional cookies that are not
expected by the application.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Considerations

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

A session cookie existing when it should not (e.g. prior to
authentication) is probably indicative of an attack. But cookies may
also be set by third party sites which get send with the request - these
may be harmless. Also consider what other applications exist on
sub-domains (e.g. www.example.com, extranet.example.com and
sales.example.com) which may also be setting cookies.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Tuning

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

\-

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Examples

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

The user utilizes a proxy tool to add cookies to the request.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Code

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

[Java](http://www.owasp.org/index.php/AppSensor_DetectionPoint_SE2#java)
[.Net](http://www.owasp.org/index.php/AppSensor_DetectionPoint_SE2#net)
[PHP](http://www.owasp.org/index.php/AppSensor_DetectionPoint_SE2#php)

</td>

</tr>

</table>

<div id="SE3">

</div>

### SE3: Deleting Existing Cookie

<table style="border-style:double;border-width:3px;" >

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

ID

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

SE3

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Title

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Deleting Existing Cookie

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Category

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

SessionException

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Description

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

A request is received which does not contain the expected cookies.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Considerations

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

The user may have bookmarked a page they had visited during a previous
authenticated session.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Tuning

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

In a poorly designed application, the number of cookies might exceed the
allowed number supported by the user's browser.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Examples

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

The user utilizes a proxy tool to remove cookies or portions of cookies
from a request.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Code

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

[Java](http://www.owasp.org/index.php/AppSensor_DetectionPoint_SE3#java)
[.Net](http://www.owasp.org/index.php/AppSensor_DetectionPoint_SE3#net)
[PHP](http://www.owasp.org/index.php/AppSensor_DetectionPoint_SE3#php)

</td>

</tr>

</table>

<div id="SE4">

</div>

### SE4: Substituting Another User's Valid Session ID or Cookie

<table style="border-style:double;border-width:3px;" >

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

ID

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

SE4

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Title

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Substituting Another User's Valid Session ID or Cookie

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Category

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

SessionException

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Description

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

A request is received which contains cookie data that is clearly from
another user or another session.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Considerations

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

\-

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Tuning

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

A mis-configured proxy might send the same session ID or cookie for all
users.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Examples

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

The user utilizes a proxy tool to substitute valid data from another
user or session into the cookie. An example would be changing some sort
of identification number within the cookie.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Code

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

[Java](http://www.owasp.org/index.php/AppSensor_DetectionPoint_SE4#java)
[.Net](http://www.owasp.org/index.php/AppSensor_DetectionPoint_SE4#net)
[PHP](http://www.owasp.org/index.php/AppSensor_DetectionPoint_SE4#php)

</td>

</tr>

</table>

<div id="SE5">

</div>

### SE5: Source Location Changes During Session

<table style="border-style:double;border-width:3px;" >

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

ID

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

SE5

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Title

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Source Location Changes During Session

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Category

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

SessionException

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Description

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Valid requests, containing valid session credentials, are received from
multiple source locations indicating a possible session hijacking
attack.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Considerations

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

A full IP address may not be constant for some users during normal use
due to clustered proxies or while mobile. Enforcing single fixed IP
addresses for each session in an intranet application may be valid.
However, if the application is accessible over public networks, changing
IP address cannot be excluded and it may be more useful to consider
fixing just part of the IP address, or looking for more significant
changes such as when the user's IP address geo-location region or
country changes (see [Autonomous System
Number](http://www.apnic.net/services/services-apnic-provides/helpdesk/faqs/asn-faqs)
(ASN) and [Detecting Malice with ModSecurity: GeoLocation
Data](http://blog.modsecurity.org/2010/10/detecting-malice-with-modsecurity-geolocation-data.html)).
Note: source port number should not be used in checks since this usually
changes very frequently.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Tuning

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

If the full IP address is used for this, it may change slightly from
request to request by the same user.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Examples

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Example 1: User A's session is compromised and User B begins using the
account. The requests originating from User B will possibly contain a
different source IP address the User A. The source IP addresses could be
the same if both users where behind the same NAT.

Example 2: An application at a fixed server location, which calls web
services, changes IP address unexpectedly.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Code

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

[Java](http://www.owasp.org/index.php/AppSensor_DetectionPoint_SE5#java)
[.Net](http://www.owasp.org/index.php/AppSensor_DetectionPoint_SE5#net)
[PHP](http://www.owasp.org/index.php/AppSensor_DetectionPoint_SE5#php)

</td>

</tr>

</table>

<div id="SE6">

</div>

### SE6: Change of User Agent Mid Session

<table style="border-style:double;border-width:3px;" >

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

ID

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

SE6

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Title

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Change of User Agent Mid Session

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Category

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

SessionException

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Description

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

The User-Agent value of the header changes during a session. This may
indicate a different browser is now being used. Although this value is
under the control of the sender, a change in this may indicates that the
session has been compromised and is being used another individual. This
will likely not be the case that the user has simply copied and pasted
the URL from one browser to another on the same system because this
action would not copy over the appropriate session identifiers.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Considerations

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

The User Agent string may change in some browsers when the content type
changes (e.g. from HTML to PDF). This detection point may only be useful
in environments where a single browser is deployed. Optionally also
include other HTTP headers in this check. For example, the
Accept-Encoding and Accept-Language headers do not normally change and
could be concatenated with the User-Agent and hashed to created an
identifier.

The [ideas](http://panopticlick.eff.org/about.php) described in
[Panopticlick](http://panopticlick.eff.org/), [client identification
mechanisms](https://sites.google.com/a/chromium.org/dev/Home/chromium-security/client-identification-mechanisms),
[canvas
fingerprinting](http://www.darknet.org.uk/2014/07/clear-cookies-cant-escape-canvas-fingerprinting/)
and [JavaScript browser
fingerprinting](http://www.businessinfo.co.uk/labs/probe/probe.php) can
also be used to fingerprint a particular client system but require the
use of client-side code. Application owners should check the legality of
collecting data, and whether it is considered "personal data" which may
have additional constraints in some jurisdictions.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Tuning

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

\-

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Examples

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Mid session, the User Agent changes from Firefox to Internet Explorer.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Code

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

[Java](http://www.owasp.org/index.php/AppSensor_DetectionPoint_SE6#java)
[.Net](http://www.owasp.org/index.php/AppSensor_DetectionPoint_SE6#net)
[PHP](http://www.owasp.org/index.php/AppSensor_DetectionPoint_SE6#php)

</td>

</tr>

</table>

<div id="ACE">

</div>

## AccessControlException

<div id="ACE1">

</div>

### ACE1: Modifying URL Argument Within a GET for Direct Object Access Attempt

<table style="border-style:double;border-width:3px;" >

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

ID

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

ACE1

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Title

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Modifying URL Argument Within a GET for Direct Object Access Attempt

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Category

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

AccessControlException

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Description

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

The application is designed to use an identifier for a particular
object, such as using categoryID=4 or user=guest within the URL. A user
modifies this value in an attempt to access unauthorized information.
This exception should be thrown anytime the identifier received from the
user is not authorized due to the identifier being non-existent or the
identifier not authorized for that user.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Considerations

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

\-

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Tuning

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Bookmarking , truncation, and mistyping issues could lead to some access
control exceptions.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Examples

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

The user modifies the following URL from

example.com/viewpage?page=1\&user=guest

to

example.com/viewpage?page=22\&user=admin

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Code

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

[Java](http://www.owasp.org/index.php/AppSensor_DetectionPoint_ACE1#java)
[.Net](http://www.owasp.org/index.php/AppSensor_DetectionPoint_ACE1#net)
[PHP](http://www.owasp.org/index.php/AppSensor_DetectionPoint_ACE1#php)

</td>

</tr>

</table>

<div id="ACE2">

</div>

### ACE2: Modifying Parameter Within A POST for Direct Object Access Attempt

<table style="border-style:double;border-width:3px;" >

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

ID

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

ACE2

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Title

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Modifying Parameter Within A POST for Direct Object Access Attempt

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Category

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

AccessControlException

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Description

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

The value of a non-free text html form element (i.e. drop down box,
radio button) is modified to an illegal value. The value either does not
exist or is not authorized for the user.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Considerations

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

\-

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Tuning

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

(same as ACE1 for bookmarking)

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Examples

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

The user utilizes a proxy tool to intercept a POST request and changes
the submitted value to a value that was not available through the normal
display. For example, the user encounters a dropdown box containing the
numbers 1 through 10. The user selects 5 and then intercepts the request
to change the submitted value to 100.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Code

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

[Java](http://www.owasp.org/index.php/AppSensor_DetectionPoint_ACE2#java)
[.Net](http://www.owasp.org/index.php/AppSensor_DetectionPoint_ACE2#net)
[PHP](http://www.owasp.org/index.php/AppSensor_DetectionPoint_ACE2#php)

</td>

</tr>

</table>

<div id="ACE3">

</div>

### ACE3: Force Browsing Attempt

<table style="border-style:double;border-width:3px;" >

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

ID

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

ACE3

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Title

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Force Browsing Attempt

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Category

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

AccessControlException

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Description

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

An authenticated or unauthenticated user sends a request for a
non-existent resource (e.g. page, directory listing, image, file, etc),
or a resource that is not authorized for that user.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Considerations

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

\-

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Tuning

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Requests for non-existent resources may occur for many reasons such as
[Benign Unexpected URLs - Part 1 - Missing (404 Not Found Error)
Files](http://www.clerkendweller.com/2010/10/26/Benign-Unexpected-URLs-Part-1-Missing-Files)

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Examples

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Example 1: The user is authenticated and requests
site.com/PageThatDoesNotExist.

Example 2: The user is authenticated and requests a video they are not
authorized to download/view.

Example 3: An unauthenticated user (perhaps with a session ID) requests
a listing of a directory detailed in the site's robots.txt file.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Code

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

[Java](http://www.owasp.org/index.php/AppSensor_DetectionPoint_ACE3#java)
[.Net](http://www.owasp.org/index.php/AppSensor_DetectionPoint_ACE3#net)
[PHP](http://www.owasp.org/index.php/AppSensor_DetectionPoint_ACE3#php)

</td>

</tr>

</table>

<div id="ACE4">

</div>

### ACE4: Evading Presentation Access Control Through Custom POST

<table style="border-style:double;border-width:3px;" >

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

ID

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

ACE4

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Title

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Evading Presentation Access Control Through Custom POST

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Category

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

AccessControlException

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Description

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

A POST request is received which is not authorized for the current user
and the user could not have performed this action without crafting a
custom POST request.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Considerations

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

This situation is most likely to occur when presentation layer access
controls are in place and have removed the user's ability to initiate
the action through the presentation of the application. An attacker may
be aware of the functionality and attempt to bypass this presentation
layer access control by crafting their own custom message and sending
this in an attempt to execute the functionality.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Tuning

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

\-

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Examples

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

The application contains the ability for an administrator to delete a
user. This method is normally invoked by entering the username and
submitting to <https://oursite/deleteuser> Presentation layer access
controls ensure the delete user form is not displayed to
non-administrator users. A malicious user has access to a
non-administrator account and is aware of the delete user functionality.
The malicious user sends a custom crafted POST message to
<https://oursite/deleteuser> in an attempt to execute the delete user
method.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Code

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

[Java](http://www.owasp.org/index.php/AppSensor_DetectionPoint_ACE4#java)
[.Net](http://www.owasp.org/index.php/AppSensor_DetectionPoint_ACE4#net)
[PHP](http://www.owasp.org/index.php/AppSensor_DetectionPoint_ACE4#php)

</td>

</tr>

</table>

<div id="IE">

</div>

## InputException

<div id="IE1">

</div>

### IE1: Cross Site Scripting Attempt

<table style="border-style:double;border-width:3px;" >

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

ID

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

IE1

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Title

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Cross Site Scripting Attempt

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Category

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

InputException

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Description

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

The HTTP request contains common XSS attacks which are often used by
attackers probing for XSS vulnerabilities.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Considerations

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Detection should be configured to test all GET and POST values as well
as all header names and values for the following values.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Tuning

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

There are many patterns which could be XSS but may also be normal user
input to a free text field e.g. "Press the 'drop' button" if a pattern
were looking for a single quotation mark followed by SQL commands like
DROP, INSERT, UPDATE and DELETE. Applications that are used to discuss
or share information about programming, software development and
security may want to allow such free text input, provided it is
encoded/escaped correctly.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Examples

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

The user utilizes a proxy tool to add an XSS attack to the header value
and the 'displayname' POST variable. The header value could be displayed
to an admin viewing log files and the 'displayname' POST variable may be
stored in the application and displayed to other users. Note, the
following XSS attacks would only be used by an attacker to probe for
vulnerability. An actual XSS attack would be customized by the attacker.

<script>

alert(document.cookie);

</script>

<script>

alert();

</script>

alert(String.fromCharCode(88,83,83))
<IMG SRC="javascript:alert('XSS');"> <IMG SRC=javascript:alert('XSS')>
<IMG SRC=javascript:alert(&quot;XSS&quot;)>

<BODY ONLOAD=alert('XSS')>

Cross references:

  - [OWASP ModSecurity Core Rule Set
    Project](:Category:OWASP_ModSecurity_Core_Rule_Set_Project "wikilink")
    v2.2.7
      - (41c) XSS Attacks: Cross-site Scripting (XSS) Attack (106 Rules)

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Code

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

[Java](http://www.owasp.org/index.php/AppSensor_DetectionPoint_IE1#java)
[.Net](http://www.owasp.org/index.php/AppSensor_DetectionPoint_IE1#net)
[PHP](http://www.owasp.org/index.php/AppSensor_DetectionPoint_IE1#php)

</td>

</tr>

</table>

<div id="IE2">

</div>

### IE2: Violation Of Implemented White Lists

<table style="border-style:double;border-width:3px;" >

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

ID

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

IE2

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Title

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Violation Of Implemented White Lists

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Category

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

InputException

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Description

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

The application receives user-supplied data that violates an established
white list validation.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Considerations

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

See AC3 (Force Browsing Attempts) about requests for
non-existent/unauthorised (i.e. not white listed) URLs.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Tuning

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

(same as IE1)

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Examples

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

The user submits data that is not correct for the particular field. This
may not be attack data necessarily, but repeated violations could be an
attempt by the attacker to determine how an application works or to
discover a flaw.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Code

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

[Java](http://www.owasp.org/index.php/AppSensor_DetectionPoint_IE2#java)
[.Net](http://www.owasp.org/index.php/AppSensor_DetectionPoint_IE2#net)
[PHP](http://www.owasp.org/index.php/AppSensor_DetectionPoint_IE2#php)

</td>

</tr>

</table>

<div id="IE3">

</div>

### IE3: Violation Of Implemented Black Lists

<table style="border-style:double;border-width:3px;" >

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

ID

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

IE3

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Title

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Violation Of Implemented Black Lists

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Category

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

InputException

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Description

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

The application receives user-supplied data that violates an established
black list validation.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Considerations

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

This may not be attack data necessarily, but repeated violations could
be an attempt by the attacker to determine how an application works or
to discover a flaw or to exploit a flaw. This black list approach
suffers from the potential for greater false positives than IE2 above,
and cannot be used to identify all potential malicious data.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Tuning

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

(same as IE1)

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Examples

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Example 1: URL in comment field identified as suspected phishing and
malware pages using [Google Safe Browsing
API](http://code.google.com/apis/safebrowsing/)).

Example 2: Parameter value matches a known SQL injection pattern.

Example 3: Parameter value matches a known XSS pattern.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Code

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

[Java](http://www.owasp.org/index.php/AppSensor_DetectionPoint_IE3#java)
[.Net](http://www.owasp.org/index.php/AppSensor_DetectionPoint_IE3#net)
[PHP](http://www.owasp.org/index.php/AppSensor_DetectionPoint_IE3#php)

</td>

</tr>

</table>

<div id="IE4">

</div>

### IE4: Violation of Input Data Integrity

<table style="border-style:double;border-width:3px;" >

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

ID

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

IE4

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Title

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Violation of Input Data Integrity

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Category

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

InputException

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Description

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

The application receives HTTP header or body parameter values which have
been tampered with when no change should have occurred.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Considerations

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

\-

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Tuning

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

This detection point should only be used with parameters that cannot be
altered by accident. Input types text and textarea would not normally be
suitable, even if the elements are disabled in the browser. Be wary of
assuming JavaScript will prevent modification of form elements in all
conditions.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Examples

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Example 1: Hidden form field modified by client.

Example 2: Select list value submitted in response, not sent by server
as an available option value.

Example 3: Cookie set by server has been manipulated by the client.

Example 4: Cookie created by client instead of by the server.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Code

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

[Java](http://www.owasp.org/index.php/AppSensor_DetectionPoint_IE4#java)
[.Net](http://www.owasp.org/index.php/AppSensor_DetectionPoint_IE4#net)
[PHP](http://www.owasp.org/index.php/AppSensor_DetectionPoint_IE4#php)

</td>

</tr>

</table>

<div id="IE5">

</div>

### IE5: Violation of Stored Business Data Integrity

<table style="border-style:double;border-width:3px;" >

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

ID

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

IE5

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Title

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Violation of Stored Business Data Integrity

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Category

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

InputException

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Description

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

User's input leads to violation of data integrity.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Considerations

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

\-

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Tuning

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

\-

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Examples

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Example 1: A user's action leads to a system integrity error when
writing to, or updating, a database.

Example 2: Business rule checks detect that a user's action is not
compatible.

Example 3: Data accuracy checking detects duplicate records for a user.

Example 4: User input leads to an unexpected file change (e.g. .htaccess
file overwritten, page template changed).

Example 5: User's request leads to a new, unexpected, outbound network
connection being made (e.g. mail sent to an SMTP server, files
downloaded from a FTP server).

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Code

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

[Java](http://www.owasp.org/index.php/AppSensor_DetectionPoint_IE5#java)
[.Net](http://www.owasp.org/index.php/AppSensor_DetectionPoint_IE5#net)
[PHP](http://www.owasp.org/index.php/AppSensor_DetectionPoint_IE5#php)

</td>

</tr>

</table>

<div id="IE6">

</div>

### IE6: Violation of Security Log Integrity

<table style="border-style:double;border-width:3px;" >

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

ID

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

IE6

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Title

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Violation of Security Log Integrity

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Category

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

InputException

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Description

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Security or audit log tampering detected.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Considerations

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

AppSensor may rely on the accuracy of "log" data to make decisions when
thresholds are reached. This detector aims to detect the insertion of
forged entries, corruption of logs, unauthorised deletion of and changes
to records.

See also:

  - [NIST SP 800-92 Guide to Security Log
    Management](http://csrc.nist.gov/publications/nistpubs/800-92/SP800-92.pdf)
  - [Tamper Detection in Audit
    Logs](http://www.cs.toronto.edu/vldb04/protected/eProceedings/contents/pdf/RS13P1.PDF)
  - [Forensic Tamper Detection in SQL
    Server](http://www.sqlsecurity.com/images/tamper/tamperdetection.htm)

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Tuning

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

\-

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Examples

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Example 1: Special characters embedded in logged data about a user's
activity cause the data to overwrite a previous log entry.

Example 2: Log file integrity is broken by modification to an existing
log entry.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Code

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

[Java](http://www.owasp.org/index.php/AppSensor_DetectionPoint_IE6#java)
[.Net](http://www.owasp.org/index.php/AppSensor_DetectionPoint_IE6#net)
[PHP](http://www.owasp.org/index.php/AppSensor_DetectionPoint_IE6#php)

</td>

</tr>

</table>

<div id="IE7">

</div>

### IE7: Detect Abnormal Content Output Structure

<table style="border-style:double;border-width:3px;" >

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

ID

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

IE7

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Title

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Detect Abnormal Content Output Structure

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Category

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

InputException

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Description

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Output data is of an unexpected format, structure or contains unexpected
components.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Considerations

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

\-

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Tuning

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

\-

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Examples

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Example 1: An abnormal number of inline scripts or iframes are returned
in an HTML page indicating a successful XSS injection.

Example 2: An XML file generated utilizing user input no longer matches
the expected structure/schema/document declaration.

Example 3: Generated JSON data contains does not match expected format.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Code

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

[Java](http://www.owasp.org/index.php/AppSensor_DetectionPoint_CIE2#java)
[.Net](http://www.owasp.org/index.php/AppSensor_DetectionPoint_CIE2#net)
[PHP](http://www.owasp.org/index.php/AppSensor_DetectionPoint_CIE2#php)

</td>

</tr>

</table>

<div id="EE">

</div>

## EncodingException

<div id="EE1">

</div>

### EE1: Double Encoded Character

<table style="border-style:double;border-width:3px;" >

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

ID

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

EE1

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Title

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Double Encoded Characters

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Category

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

EncodingException

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Description

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

An HTTP request is received which contains one or more double encoded
values.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Considerations

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

\-

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Tuning

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Data supplied by other party systems may have encoding issues.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Examples

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

The user sends encodes the % symbol to %25 and appends 3C. The user is
sending %253C which may be interpreted by the application as %3C which
is actually \<.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Code

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

[Java](http://www.owasp.org/index.php/AppSensor_DetectionPoint_EE1#java)
[.Net](http://www.owasp.org/index.php/AppSensor_DetectionPoint_EE1#net)
[PHP](http://www.owasp.org/index.php/AppSensor_DetectionPoint_EE1#php)

</td>

</tr>

</table>

<div id="EE2">

</div>

### EE2: Unexpected Encoding Used

<table style="border-style:double;border-width:3px;" >

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

ID

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

EE2

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Title

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Unexpected Encoding Used

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Category

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

EncodingException

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Description

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

An HTTP request is received which contains values that have encoded in
an unexpected format.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Considerations

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

\-

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Tuning

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

(same as EE1)

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Examples

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

The user encodes an attack such as alert(document.cookie) into the UTF-7
format and sends this data the application. This could bypass validation
filters and be rendered to a user in certain situations.

Cross references:

  - [OWASP ModSecurity Core Rule Set
    Project](:Category:OWASP_ModSecurity_Core_Rule_Set_Project "wikilink")
    v2.2.7
      - (30c) HTTP Policy Enforcement: Request Content Type Is Not
        Allowed by Policy (960010)

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Code

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

[Java](http://www.owasp.org/index.php/AppSensor_DetectionPoint_EE2#java)
[.Net](http://www.owasp.org/index.php/AppSensor_DetectionPoint_EE2#net)
[PHP](http://www.owasp.org/index.php/AppSensor_DetectionPoint_EE2#php)

</td>

</tr>

</table>

<div id="CIE">

</div>

## CommandInjectionException

<div id="CIE1">

</div>

### CIE1: Blacklist Inspection for Common SQL Injection Values

<table style="border-style:double;border-width:3px;" >

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

ID

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

CIE1

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Title

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Blacklist Inspection for Common SQL Injection Values

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Category

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

CommandInjectionException

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Description

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

A request is received which contains common SQL injection attack
attempts.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Considerations

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

The point of this detection is not to detect all variations of a SQL
injection attack, but to detect the common probes which an attacker or
tool might use to determine if a SQL injection vulnerability is present.
Unless the site contains some sort of message board for discussing SQL
injection, there is little reason that the SQL injection examples should
ever be received from a user request.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Tuning

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

(same as IE1)

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Examples

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

The user sends a request and modifies a URL parameter from category = 5
to category = 5' OR '1' = '1 in an attempt to perform an SQL injection
attack. The user could perform similar attacks by modifying POST
variables or even the request headers to contain SQL injection attacks.
' OR '1'='1 ' OR 'a'='a ' OR 1=1-- xp_cmdshell UNION JOIN

Cross references:

  - [OWASP ModSecurity Core Rule Set
    Project](:Category:OWASP_ModSecurity_Core_Rule_Set_Project "wikilink")
    v2.2.7
      - (41c) SQL Injection Attacks (13 Rules)
      - (48e) Bayesian Analysis Detects Probable Attack: SQL Injection
        Attack (-)

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Code

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

[Java](http://www.owasp.org/index.php/AppSensor_DetectionPoint_CIE1#java)
[.Net](http://www.owasp.org/index.php/AppSensor_DetectionPoint_CIE1#net)
[PHP](http://www.owasp.org/index.php/AppSensor_DetectionPoint_CIE1#php)

</td>

</tr>

</table>

<div id="CIE2">

</div>

### CIE2: Detect Abnormal Quantity of Returned Records

<table style="border-style:double;border-width:3px;" >

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

ID

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

CIE2

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Title

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Detect Abnormal Quantity of Returned Records

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Category

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

CommandInjectionException

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Description

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

A database query is executed which returns more records than expected.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Considerations

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

\-

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Tuning

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

\-

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Examples

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Example 1: A query of a non-SQL dataset should only return 1 record but
100 records are returned.

Example 2: The application is designed to allow a user to maintain 5
profiles. A user makes a request to view all of their profiles. The
database SQL query, which is expected to always return 5 or less
results, returns 10,000 records. Something in the application, or user's
actions, has caused unauthorized data to be returned.

Example 3: Extraction of data from an XML file should only return one
matching node, but more than one is returned.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Code

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

[Java](http://www.owasp.org/index.php/AppSensor_DetectionPoint_CIE2#java)
[.Net](http://www.owasp.org/index.php/AppSensor_DetectionPoint_CIE2#net)
[PHP](http://www.owasp.org/index.php/AppSensor_DetectionPoint_CIE2#php)

</td>

</tr>

</table>

<div id="CIE3">

</div>

### CIE3: Null Byte Character in File Request

<table style="border-style:double;border-width:3px;" >

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

ID

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

CIE3

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Title

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Null Byte Character in File Request

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Category

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

CommandInjectionException

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Description

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

A request is received to download a file from the server. The filename
requested contains the null byte the file name. This is an attempted OS
injection attack.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Considerations

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

\-

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Tuning

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

\-

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Examples

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

The user modifies the filename of the requested file to download to
contain the null byte. The null byte can be added by inserting the hex
value %00.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Code

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

[Java](http://www.owasp.org/index.php/AppSensor_DetectionPoint_CIE3#java)
[.Net](http://www.owasp.org/index.php/AppSensor_DetectionPoint_CIE3#net)
[PHP](http://www.owasp.org/index.php/AppSensor_DetectionPoint_CIE3#php)

</td>

</tr>

</table>

<div id="CIE4">

</div>

### CIE4: Carriage Return or Line Feed Character in File Request

<table style="border-style:double;border-width:3px;" >

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

ID

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

CIE4

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Title

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Carriage Return or Line Feed Character in File Request

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Category

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

CommandInjectionException

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Description

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

A request is received which contains the carriage return or line feed
characters within the POST data or the URL parameters. This is an
attempted HTTP split response attack.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Considerations

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

\-

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Tuning

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

\-

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Examples

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

The user includes the hex value %0D or %0A in the HTTP request POST data
or URL parameters.

Cross references:

  - [OWASP ModSecurity Core Rule Set
    Project](:Category:OWASP_ModSecurity_Core_Rule_Set_Project "wikilink")
    v2.2.7
      - (40b) Generic Attacks: PHP Injection (959151,958976)

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Code

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

[Java](http://www.owasp.org/index.php/AppSensor_DetectionPoint_CIE4#java)
[.Net](http://www.owasp.org/index.php/AppSensor_DetectionPoint_CIE4#net)
[PHP](http://www.owasp.org/index.php/AppSensor_DetectionPoint_CIE4#php)

</td>

</tr>

</table>

<div id="FIO">

</div>

## FileIOException

<div id="FIO1">

</div>

### FIO1: Detect Large Individual File

<table style="border-style:double;border-width:3px;" >

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

ID

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

FIO1

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Title

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Detect Large Individual File

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Category

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

FileIOException

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Description

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

A file upload feature detects that a large file has been submitted for
upload which exceeds the maximum upload size.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Considerations

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

\-

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Tuning

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

\-

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Examples

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

The user attempts to upload a large file to occupy resources or fill up
disk space.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Code

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

[Java](http://www.owasp.org/index.php/AppSensor_DetectionPoint_FIO1#java)
[.Net](http://www.owasp.org/index.php/AppSensor_DetectionPoint_FIO1#net)
[PHP](http://www.owasp.org/index.php/AppSensor_DetectionPoint_FIO1#php)

</td>

</tr>

</table>

<div id="FIO2">

</div>

### FIO2: Detect Large Number of File Uploads

<table style="border-style:double;border-width:3px;" >

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

ID

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

FIO2

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Title

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Detect Large Number of File Uploads

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Category

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

FileIOException

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Description

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

A user uploads an excessively large number of files.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Considerations

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

The limit and period used to determine the threshold rate is application
dependent, and may also depend on the user's role.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Tuning

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

\-

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Examples

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

A single user attempts to upload multiple small files to occupy
resources or fill up disk space.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Code

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

[Java](http://www.owasp.org/index.php/AppSensor_DetectionPoint_FIO2#java)
[.Net](http://www.owasp.org/index.php/AppSensor_DetectionPoint_FIO2#net)
[PHP](http://www.owasp.org/index.php/AppSensor_DetectionPoint_FIO2#php)

</td>

</tr>

</table>

<div id="HT">

</div>

## Honey Trap

<div id="HT1">

</div>

### HT1: Alteration to Honey Trap Data

<table style="border-style:double;border-width:3px;" >

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

ID

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

HT1

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Title

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Alteration to Honey Trap Data

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Category

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

HoneyTrap

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Description

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Fake (not otherwise needed by the application) data sent to the user and
returned (e.g. as form, URL, cookie values or in the path or HTTP
header) is modified. This is usually combined with making the name or
value a tempting item for an attacker to try modifying.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Considerations

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Similar techniques can also be used for the creation of accessible
CAPTCHA.

See also ideas at
<http://blogs.sans.org/appsecstreetfighter/2009/06/04/my-top-6-honeytokens/>

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Tuning

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

\-

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Examples

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Example 1: Otherwise useless hidden fields, which look like potential
vulnerabilities, added to some forms are sent back to the server
modified (e.g. <input type="hidden" name="admin" value="false" />).

Example 2: An additional URL parameter, which is not used by the
application, is modified by the user (e.g.
www.example.com/account.jsp?debug=0).

Example 3: An additional fake cookie is added and is modified by the
user.

Example 4: URL rewriting is used and a fake directory name is added;
this is modified by the user (e.g.
www.example.com/orders/normaluser/display.php).

Cross references:

  - [OWASP ModSecurity Core Rule Set
    Project](:Category:OWASP_ModSecurity_Core_Rule_Set_Project "wikilink")
    v2.2.7
      - (40e) AppSensor Detection Points: Tampering of Hidden Parameter
        Honeytrap Data (981131)

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Code

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

[Java](http://www.owasp.org/index.php/AppSensor_DetectionPoint_HT1#java)
[.Net](http://www.owasp.org/index.php/AppSensor_DetectionPoint_HT1#net)
[PHP](http://www.owasp.org/index.php/AppSensor_DetectionPoint_HT1#php)

</td>

</tr>

</table>

<div id="HT2">

</div>

### HT2: Honey Trap Resource Requested

<table style="border-style:double;border-width:3px;" >

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

ID

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

HT2

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Title

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Honey Trap Resource Requested

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Category

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

HoneyTrap

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Description

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

A purposely leaked resource that has no use in normal application use is
requested by a user.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Considerations

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Ensure the resource is not linked from normal application content such
that a spider or robot might find the resource in any case.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Tuning

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

\-

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Examples

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Example 1: Page, directory or other resource listed in the application's
robots.txt robots exclusion file is requested by the user.

Example 2: URL identified only in HTML comments is requested by the
user.

Example 3: Unexposed server function call included in Flash file source
code is requested by the user.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Code

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

[Java](http://www.owasp.org/index.php/AppSensor_DetectionPoint_HT2#java)
[.Net](http://www.owasp.org/index.php/AppSensor_DetectionPoint_HT2#net)
[PHP](http://www.owasp.org/index.php/AppSensor_DetectionPoint_HT2#php)

</td>

</tr>

</table>

<div id="HT3">

</div>

### HT3: Honey Trap Data Used

<table style="border-style:double;border-width:3px;" >

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

ID

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

HT3

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Title

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Honey Trap Data Used

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Category

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

HoneyTrap

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Description

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Special data sent or accessed by a user.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Considerations

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

For honey trap data that is detected on egress only, use of outbound
content monitoring (e.g. a web application firewall or similar
technique) may be helpful.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Tuning

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

\-

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Examples

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Example 1: Fake user name and password only visible in source HTML code
used to attempt to log in to the application (e.g. in HTML comments, in
server-side code 'accidentally' delivered to the user).

Example 2: A special code number or account name is left in a discussion
forum site; this is then used in the application.

Example 3: An attempt is made to authenticate with the user name listed
in the first row (e.g. ID=1) of the application's database table of
Users.

Example 4: Data from a fake account record is sent by the server and
detected; this record should not normally be accessible by anyone using
the application.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Code

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

[Java](http://www.owasp.org/index.php/AppSensor_DetectionPoint_HT3#java)
[.Net](http://www.owasp.org/index.php/AppSensor_DetectionPoint_HT3#net)
[PHP](http://www.owasp.org/index.php/AppSensor_DetectionPoint_HT3#php)

</td>

</tr>

</table>

<div id="UT">

</div>

## UserTrendException

<div id="UT1">

</div>

### UT1: Irregular Use of Application

<table style="border-style:double;border-width:3px;" >

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

ID

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

UT1

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Title

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Irregular Use of Application

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Category

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

UserTrendException

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Description

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

The application receives an unusual pattern of requests for the same
page or feature from a user. The user may be sending different data
combinations or trying to detect errors in the page.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Considerations

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

\-

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Tuning

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Use of bookmarked URLs and the "back" button might generate
out-of-sequence requests. See also related frequency of feature use in
UT4.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Examples

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Example 1: The user requests a particular page, such as the address
update page, numerous times.

Example 2: The user requests a page out-of-sequence, such as an
intermediate step in a multi-stage form, or a series of actions that do
not map to a valid business process.

Example 3: The user only requests dynamic content, and not the
associated static files (e.g. images, styles heets).

Example 4: The user sends a slow request/read in an attempt at
application denial of service.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Code

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

[Java](http://www.owasp.org/index.php/AppSensor_DetectionPoint_UT1#java)
[.Net](http://www.owasp.org/index.php/AppSensor_DetectionPoint_UT1#net)
[PHP](http://www.owasp.org/index.php/AppSensor_DetectionPoint_UT1#php)

</td>

</tr>

</table>

<div id="UT2">

</div>

### UT2: Speed of Application Use

<table style="border-style:double;border-width:3px;" >

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

ID

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

UT2

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Title

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Speed of Application Use

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Category

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

UserTrendException

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Description

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

The speed of requests from a user indicates that an automated tool is
being used to access the site. The use of a tool undertaking a high
number of requests quickly may indicate unapproved content scraping or
data gathering, reconnaissance for an attack, or attempts to identify
vulnerabilities in the site. Slow usage (e.g. between account creation
and use) might indicate automated account creation that are then used
subsequently for attacks.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Considerations

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

If enforced inappropriately or too rigorously, this detection point
could lead to false positives.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Tuning

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Time periods need to be set broadly enough to cater for the normal
spread in user behavior. Some users may use automated tools that store
passwords securely to populate and submit authentication forms.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Examples

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Example 1: The user utilizes an automated tool to request hundreds of
pages per minute.

Example 2: The user does not log in to the site until a long time after
their account is created.

Example 3: New (uncached) static content such as images and style sheets
associated with each page are not requested in a similar time period as
the page.

Example 4: A CAPTCHA challenge is responded to more quickly than a human
could possibly do.

Example 5: The user's clickstream data velocity is too high.

Example 6: The time interval between the applications displaying a
page/form and the time for the user to complete the page/form and submit
it is too fast.

Example 7: A web scraping tool is used to obtain content from a website.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Code

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

[Java](http://www.owasp.org/index.php/AppSensor_DetectionPoint_UT2#java)
[.Net](http://www.owasp.org/index.php/AppSensor_DetectionPoint_UT2#net)
[PHP](http://www.owasp.org/index.php/AppSensor_DetectionPoint_UT2#php)

</td>

</tr>

</table>

<div id="UT3">

</div>

### UT3: Frequency of Site Use

<table style="border-style:double;border-width:3px;" >

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

ID

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

UT3

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Title

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Frequency of Site Use

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Category

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

UserTrendException

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Description

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Change in how often the site is used by a user

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Considerations

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

\-

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Tuning

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Some users may correctly change their behavior in the frequency of
accessing the application.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Examples

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

The user normally accesses the site once per week, but this changes to
many times per day.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Code

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

[Java](http://www.owasp.org/index.php/AppSensor_DetectionPoint_UT3#java)
[.Net](http://www.owasp.org/index.php/AppSensor_DetectionPoint_UT3#net)
[PHP](http://www.owasp.org/index.php/AppSensor_DetectionPoint_UT3#php)

</td>

</tr>

</table>

<div id="UT4">

</div>

### UT4: Frequency of Feature Use

<table style="border-style:double;border-width:3px;" >

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

ID

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

UT4

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Title

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Frequency of Feature Use

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Category

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

UserTrendException

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Description

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

The rate of a user utilizing a particular application feature changes
dramatically.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Considerations

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

\-

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Tuning

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

It may be valid for some functionality may be requested repeatedly. For
example a real customer placing many orders, a press officer publishing
a backlog of press releases, or an administrator populating a staff
directory.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Examples

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Example 1: The user submits many forum messages in a short period of
time.

Example 2: The user adds many new friends rapidly.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Code

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

[Java](http://www.owasp.org/index.php/AppSensor_DetectionPoint_UT4#java)
[.Net](http://www.owasp.org/index.php/AppSensor_DetectionPoint_UT4#net)
[PHP](http://www.owasp.org/index.php/AppSensor_DetectionPoint_UT4#php)

</td>

</tr>

</table>

<div id="STE">

</div>

## SystemTrendException

<div id="STE1">

</div>

### STE1: High Number of Logouts Across The Site

<table style="border-style:double;border-width:3px;" >

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

ID

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

STE1

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Title

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

High Number of Logouts Across The Site

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Category

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

SystemTrendException

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Description

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

A sudden spike in logouts across the application could indicate a XSS
and CSRF attack placed within the application which is automatically
logging off users.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Considerations

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

\-

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Tuning

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

\-

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Examples

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

The hourly usage of the log-off feature of the application suddenly
spikes by 500%.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Code

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

[Java](http://www.owasp.org/index.php/AppSensor_DetectionPoint_STE1#java)
[.Net](http://www.owasp.org/index.php/AppSensor_DetectionPoint_STE1#net)
[PHP](http://www.owasp.org/index.php/AppSensor_DetectionPoint_STE1#php)

</td>

</tr>

</table>

<div id="STE2">

</div>

### STE2: High Number of Logins Across The Site

<table style="border-style:double;border-width:3px;" >

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

ID

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

STE2

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Title

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

High Number of Logins Across The Site

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Category

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

SystemTrendException

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Description

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

A sudden spike in logins across the application could indicate users
being redirected to the site from a phishing email looking to exploit a
XSS vulnerability in the site.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Considerations

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

\-

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Tuning

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

\-

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Examples

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

The hourly usage of the logon feature of the application suddenly spikes
by 1,000%.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Code

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

[Java](http://www.owasp.org/index.php/AppSensor_DetectionPoint_STE2#java)
[.Net](http://www.owasp.org/index.php/AppSensor_DetectionPoint_STE2#net)
[PHP](http://www.owasp.org/index.php/AppSensor_DetectionPoint_STE2#php)

</td>

</tr>

</table>

<div id="STE3">

</div>

### STE3: Significant Change in Usage of Same Transaction Across The Site

<table style="border-style:double;border-width:3px;" >

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

ID

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

STE3

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Title

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Significant Change in Usage of Same Transaction Across The Site

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Category

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

SystemTrendException

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Description

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

A sudden spike in similar activity across numerous users of the
application may indicate a phishing attack or CSRF attack against the
users; a rapid reduction in activity may indicate users are being
redirected elsewhere; a significant change in average transaction value
or other quantitative measure may indicate suspicious activity.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Considerations

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

External events (e.g. a news item) may lead to additional unexpected
traffic which is not an attack.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Tuning

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

A special requirement, situation or event may dramatically change the
rate of use of certain transactions. (See also UT4)

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Examples

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Example 1: The hourly usage of the update email address feature of the
application suddenly spikes by 2,000%.

Example 2: A website is compromised and users are redirected to a
malicious site part-way through a process; the number of successful
fully completed transactions drops to nil.

Example 3: A number of slow requests/reads are received in an attempt at
application denial of service.

Example 4: The find contacts functionality is used excessively to
identify related friends.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Code

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

[Java](http://www.owasp.org/index.php/AppSensor_DetectionPoint_STE3#java)
[.Net](http://www.owasp.org/index.php/AppSensor_DetectionPoint_STE3#net)
[PHP](http://www.owasp.org/index.php/AppSensor_DetectionPoint_STE3#php)

</td>

</tr>

</table>

<div id="RP">

</div>

## Reputation

These reputation detection points could be treated either as:

  - like any other detection point contributing to the count of
    suspicious events, or
  - used to alter security logging, or the threshold levels, or
    associated response actions

The former could lead to a much higher false positive rate.

<div id="RP1">

</div>

### RP1: Suspicious or Disallowed User Source Location

<table style="border-style:double;border-width:3px;" >

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

ID

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

RP1

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Title

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Suspicious or Disallowed User Source Location

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Category

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Reputation

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Description

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

The user is identified as using an IP address associated with a
blacklist

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Considerations

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Suspicious or invalid geo-location, IP addresses or IP address ranges
may be identified using a whitelist, internal blacklist, list of Tor
nodes (e.g. <https://torstat.xenobite.eu/>), HTTP blacklist (e.g.
<http://www.projecthoneypot.org/httpbl.php> and Dshield
<http://www.dshield.org>) list of spammers (e.g. Spamhaus
<http://www.spamhaus.org/>) or known botnets (e.g.
<http://www.shadowserver.org/wiki/>).

"Suspicious" may also depend upon the type of user e.g. users in the
"CMS manager" role should be using an internal network IP address,
public users could be from anywhere, customers should only be accessing
the application from a particular geographical region, search engine
robots should be from a limited range of IP addresses.

Take care that "suspicious" does not contribute to greater false
positives.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Tuning

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

The currency and accuracy of needs to be considered when the information
is used in AppSensor. The method of challenge and removal of
inaccuracies, and the speed of this process, should also be considered.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Examples

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Example 1: A user with an external IP address is accessing an internal
application, which should not be occurring.

Example 2: An authenticated user is accessing the application using a
known Tor node, and attack detection thresholds are made stricter.

Example 3: An authenticated user is accessing the application from a
known trustworthy IP address, and thresholds for certain activity (e.g.
input data validation errors) are relaxed slightly.

Example 4: The IP address of the payment authentication server, used by
the application for credit card authorisation, changes.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Code

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

[Java](http://www.owasp.org/index.php/AppSensor_DetectionPoint_RP1#java)
[.Net](http://www.owasp.org/index.php/AppSensor_DetectionPoint_RP1#net)
[PHP](http://www.owasp.org/index.php/AppSensor_DetectionPoint_RP1#php)

</td>

</tr>

</table>

<div id="RP2">

</div>

### RP2: Suspicious External User Behavior

<table style="border-style:double;border-width:3px;" >

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

ID

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

RP2

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Title

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Suspicious External User Behavior

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Category

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Reputation

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Description

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

External (to the application) devices and systems (e.g. host and network
IDS, file integrity monitoring, disk usage monitoring, anti-malware
service, IPS, network firewall, web application firewall, web server
logging, XML gateway, database firewall, SIEM) detect anomalous behavior
by the user (e.g. session and/or IP address) or suspicious user
properties (e.g. fraud score, previously compromised, unusual
current/previous behavior).

This information can be used by the application to contribute to its
knowledge about a potential attacker. In some cases, the information
could be detected by the application itself (e.g. XSS pattern black
listing), but may be more effectively identified by the external device,
or is not known to the application normally (e.g. requests for missing
resources that the web server sees, but does not pass onto the
application).

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Considerations

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

The greater the knowledge a device or system has about the application,
the greater confidence can be given to evidence of suspicious behaviour.
Therefore, for example, attempted SQL injection detected by a web
application firewall (WAF) might be given greater weight than
information from a network firewall about the IP address.

The power of AppSensor is its accuracy and low false positive rate, and
the usage of external data should be carefully assessed to ensure it
does not contribute to a higher false positive rate.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Tuning

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

The level of trust in information from the external
device/system/organization needs to be considered.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Examples

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Example 1: A network IDS has detected suspicious activity by a
particular IP address, and this is used to temporarily tighten the
attack detection thresholds for requests from all users in the same IP
address range.

Example 2: An application is using the ModSecurity web application
firewall with the [Core Rule
Set](:Category:OWASP_ModSecurity_Core_Rule_Set_Project "wikilink"), and
utilises the anomaly score data passed forward in the X-WAF-Events and
X-WAF-Score HTTP headers (optional rules in
modsecurity_crs_49_header_tagging.conf) to adjust the level of
application logging for each user.

Example 3: Information from an instance of PHPIDS suggests request data
may be malicious.

Example 4: An adverse score is indicated for the user or IP address by a
fraud detection engine, or by an external reputation or fraud rating
service (e.g. [Open Fraud Detection
Project](http://wafsec.com/index.php/api/))

Example 5: The username (email address) is related to an account
compromised by a data breach (e.g. [';--have i been
pwned?](http://www.haveibeenpwned.com/))

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Code

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

[Java](http://www.owasp.org/index.php/AppSensor_DetectionPoint_RP2#java)
[.Net](http://www.owasp.org/index.php/AppSensor_DetectionPoint_RP2#net)
[PHP](http://www.owasp.org/index.php/AppSensor_DetectionPoint_RP2#php)

</td>

</tr>

</table>

<div id="RP3">

</div>

### RP3: Suspicious Client-Side Behavior

<table style="border-style:double;border-width:3px;" >

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

ID

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

RP3

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Title

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Suspicious Client-Side Behavior

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Category

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Reputation

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Description

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

The application receives a report of client-side security policy
exceptions.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Considerations

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Take care this information does not contribute to greater false
positives.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Tuning

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

\-

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Examples

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Example 1: An internal corporate intranet application detects use of a
non-standard workstation configuration (e.g. using JavaScript font or
plugin detection see
[SE6](http://www.owasp.org/index.php/AppSensor_DetectionPoints#SE6:_Change_Of_User_Agent_Mid_Session)).
An alert is raised for further investigation.

Example 2: An online banking application receives details of suspicious
client-side behaviour that would not be expected in normal application
use, via a [Content Security
Policy](http://www.w3.org/Security/wiki/Content_Security_Policy)
violation report. The application increases logging for the user, and
decreases the monetary limit at which the user's payments require manual
authorisation by bank staff.

Example 3: The HTTP user agent header value does not agree with other
indicators (e.g. using JavaScript detection as in example 1 above).
[Reference](http://ha.ckers.org/blog/20100904/browser-detection-autopwn-etc/).

Example 4: A honey client system monitoring the web application reports
unexpected behavior in the generated web pages output.

Example 5: A third-party monitoring system detects page content that is
unauthorised and/or contrary to policy (e.g. structure, included links,
HTML validation, inclusion of certain data such as payment card data).

Example 6: Client-side code is injected that creates a hash of the page
content in the receiving client web browser to monitor for manipulated
HTML code.
[Reference](http://blog.spiderlabs.com/2013/07/modsecurity-advanced-topic-of-the-week-detecting-banking-trojan-page-modifications.html)

Cross references:

  - [OWASP ModSecurity Core Rule Set
    Project](:Category:OWASP_ModSecurity_Core_Rule_Set_Project "wikilink")
    v2.2.7
      - (42e) Content Security Policy Enforcement: Content Security
        Policy (CSP) Violation (960001)

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Code

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

[Java](http://www.owasp.org/index.php/AppSensor_DetectionPoint_RP3#java)
[.Net](http://www.owasp.org/index.php/AppSensor_DetectionPoint_RP3#net)
[PHP](http://www.owasp.org/index.php/AppSensor_DetectionPoint_RP3#php)

</td>

</tr>

</table>

<div id="RP4">

</div>

### RP4: Change to Environment Threat Level

<table style="border-style:double;border-width:3px;" >

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

ID

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

RP4

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Title

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Change to Environment Threat Level

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Category

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Reputation

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Description

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

The general threat level (e.g. general risk of attack from the Internet,
or specific targetted attacks against an organisation) is elevated. This
could also be used to change response sensitivity due to short-term
effects such as application upgrades/patching.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Considerations

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

This input could be used to alter thresholds for AppSensor responses.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Tuning

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

The detection point could receive specially crafted input from an
attacker, and therefore the information should be considered as
untrusted.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Examples

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Example 1: A machine-readable threat index is read from a third-party
and is used to control security logging levels.

Example 2: Business circumstances (e.g. increased attention by
activists) raises the suspicion the application may be at increased risk
of mis-use, and response thresholds for attack detection are tightened
for non-authenticated users.

Example 3: The Defense Condition Level
([DEFCON](http://www.fas.org/nuke/guide/usa/c3i/defcon.htm)) is raised
and response thresholds are changed.

Example 4: Sensor signal missing.

Example 5: External power source disconnected.

Example 6: Firmware or software patch signing check failure.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Code

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

[Java](http://www.owasp.org/index.php/AppSensor_DetectionPoint_RP4#java)
[.Net](http://www.owasp.org/index.php/AppSensor_DetectionPoint_RP4#net)
[PHP](http://www.owasp.org/index.php/AppSensor_DetectionPoint_RP4#php)

</td>

</tr>

</table>

[Category:OWASP AppSensor
Project](Category:OWASP_AppSensor_Project "wikilink")