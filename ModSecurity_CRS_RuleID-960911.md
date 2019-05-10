## Rule ID: 906911

<table style="border-style:double;border-width:3px;" >

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Rule ID

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

906911

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Rule Message

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Invalid HTTP Request Line

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Rule Summary

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Validate request line against the format specified in the HTTP RFC

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Impact

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

4 - Warning

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Rule

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

<code>

`SecRule REQUEST_LINE "!^(?:(?:[a-z]{3,10}\s+(?:\w{3,7}?://[\w\-\./]*(?::\d+)?)?/[^?#]*(?:\?[^#\s]*)?(?:#[\S]*)?|connect (?:\d{1,3}\.){3}\d{1,3}\.?(?::\d+)?|options \*)\s+[\w\./]+|get /[^?#]*(?:\?[^#\s]*)?(?:#[\S]*)?)$" \`
`   "phase:1,t:none,t:lowercase,block,msg:'Invalid HTTP Request Line',id:'960911',severity:'4',rev:'2.2.0',logdata:'%{request_line}',tag:'`[`https://www.owasp.org/index.php/ModSecurity_CRS_RuleID-%{tx.id`](https://www.owasp.org/index.php/ModSecurity_CRS_RuleID-%%7Btx.id)`}',tag:'`<http://www.w3.org/Protocols/rfc2616/rfc2616-sec3.html#sec3.2.1>`',tag:'RULE_ACCURACY_LEVEL/5',setvar:'tx.msg=%{rule.msg}',setvar:'tx.id=%{rule.id}',setvar:tx.anomaly_score=+%{tx.notice_anomaly_score},setvar:tx.protocol_violation_score=+%{tx.notice_anomaly_score},setvar:'tx.%{rule.id}-PROTOCOL_VIOLATION/INVALID_REQ-%{matched_var_name}=%{matched_var}'"`</code>

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Detailed Rule Information

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

  - Uses rule negation against the regex for positive security. The
    regex specifies the proper construction of URI request lines such
    as:

`"http:" "//" host [ ":" port ] [ abs_path [ "?" query ]] `

  - It also outlines proper construction for CONNECT, OPTIONS and GET
    requests.

<!-- end list -->

    ///  A description of the regular expression:
    ///
    ///  Beginning of line or string
    ///  Match expression but don't capture it. [(?:[a-z]{3,10}\s+(?:\w{3,7}?://[\w\-\./]*(?::\d+)?)?/[^?#]*(?:\?[^#\s]*)?(?:#[\S]*)?|connect (?:\d{1,3}\.){3}\d{1,3}\.?(?::\d+)?|options \*)\s+[\w\./]+|get /[^?#]*(?:\?[^#\s]*)?(?:#[\S]*)?]
    ///      Select from 2 alternatives
    ///          (?:[a-z]{3,10}\s+(?:\w{3,7}?://[\w\-\./]*(?::\d+)?)?/[^?#]*(?:\?[^#\s]*)?(?:#[\S]*)?|connect (?:\d{1,3}\.){3}\d{1,3}\.?(?::\d+)?|options \*)\s+[\w\./]+
    ///              Match expression but don't capture it. [[a-z]{3,10}\s+(?:\w{3,7}?://[\w\-\./]*(?::\d+)?)?/[^?#]*(?:\?[^#\s]*)?(?:#[\S]*)?|connect (?:\d{1,3}\.){3}\d{1,3}\.?(?::\d+)?|options \*]
    ///                  Select from 3 alternatives
    ///                      [a-z]{3,10}\s+(?:\w{3,7}?://[\w\-\./]*(?::\d+)?)?/[^?#]*(?:\?[^#\s]*)?(?:#[\S]*)?
    ///                          Any character in this class: [a-z], between 3 and 10 repetitions
    ///                          Whitespace, one or more repetitions
    ///                          Match expression but don't capture it. [\w{3,7}?://[\w\-\./]*(?::\d+)?], zero or one repetitions
    ///                              \w{3,7}?://[\w\-\./]*(?::\d+)?
    ///                                  Alphanumeric, between 3 and 7 repetitions, as few as possible
    ///                                  ://
    ///                                  Any character in this class: [\w\-\./], any number of repetitions
    ///                                  Match expression but don't capture it. [:\d+], zero or one repetitions
    ///                                      :\d+
    ///                                          :
    ///                                          Any digit, one or more repetitions
    ///                          /
    ///                          Any character that is NOT in this class: [?#], any number of repetitions
    ///                          Match expression but don't capture it. [\?[^#\s]*], zero or one repetitions
    ///                              \?[^#\s]*
    ///                                  Literal ?
    ///                                  Any character that is NOT in this class: [#\s], any number of repetitions
    ///                          Match expression but don't capture it. [#[\S]*], zero or one repetitions
    ///                              #[\S]*
    ///                                  #
    ///                                  Any character in this class: [\S], any number of repetitions
    ///                      connect (?:\d{1,3}\.){3}\d{1,3}\.?(?::\d+)?
    ///                          connect
    ///                          Space
    ///                          Match expression but don't capture it. [\d{1,3}\.], exactly 3 repetitions
    ///                              \d{1,3}\.
    ///                                  Any digit, between 1 and 3 repetitions
    ///                                  Literal .
    ///                          Any digit, between 1 and 3 repetitions
    ///                          Literal ., zero or one repetitions
    ///                          Match expression but don't capture it. [:\d+], zero or one repetitions
    ///                              :\d+
    ///                                  :
    ///                                  Any digit, one or more repetitions
    ///                      options \*
    ///                          options
    ///                          Space
    ///                          Literal *
    ///              Whitespace, one or more repetitions
    ///              Any character in this class: [\w\./], one or more repetitions
    ///          get /[^?#]*(?:\?[^#\s]*)?(?:#[\S]*)?
    ///              get
    ///              Space
    ///              /
    ///              Any character that is NOT in this class: [?#], any number of repetitions
    ///              Match expression but don't capture it. [\?[^#\s]*], zero or one repetitions
    ///                  \?[^#\s]*
    ///                      Literal ?
    ///                      Any character that is NOT in this class: [#\s], any number of repetitions
    ///              Match expression but don't capture it. [#[\S]*], zero or one repetitions
    ///                  #[\S]*
    ///                      #
    ///                      Any character in this class: [\S], any number of repetitions
    ///  End of line or string

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Example Payload

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Here is an example payloads taken from HTTPrint
(http://net-square.com/httprint/) that will trigger this rule.

`127.0.0.1 - - [14/Sep/2010:11:51:43 -0400] "\x16\x03" 501 214 TI@aD8CoAWYAAAOFHNMAAACA`

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Example Audit Log Entry

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Include an example ModSecurity Audit Log Entry for when this rule
matchs.

    --1167a167-A--
    [14/Sep/2010:11:51:43 --0400] TI@aD8CoAWYAAAOFHNMAAACA 127.0.0.1 51285 127.0.0.1 80
    --1167a167-B--
    ^V^C

    --1167a167-F--

    --1167a167-H--
    Message: Match of "rx ^(?:(?:[a-z]{3,10}\\s+(?:\\w{3,7}?://[\\w\\-\\./]*(?::\\d+)?)?/[^?#]*(?:\\?[^#\\s]*)?(?:#[\\S]*)?|connect (?:\\d{1,3}\\.){3}\\d{1,3}\\.?(?::\\d+)?|options \\*)\\s+[\\w\\./]+|get /[^?#]*(?:\\?[^#\\s]*)?(?:#[\\S]*)?)$"
    against "REQUEST_LINE" required. [file "/usr/local/apache/conf/modsec_current/base_rules/modsecurity_crs_20_protocol_violations.conf"] [line "34"] [id "960911"] [rev "2.0.8"] [msg "Invalid HTTP Request Line"] [severity "WARNING"]
    [tag "http://www.w3.org/Protocols/rfc2616/rfc2616-sec3.html#sec3.2.1"]
    Apache-Error: [file "core.c"] [line 3773] [level 3] Invalid method in request \\x16\\x03
    Stopwatch: 1284479503453580 43606 (4888 42377 -)
    Producer: ModSecurity for Apache/2.5.12 (http://www.modsecurity.org/); core ruleset/2.0.8.
    Server: Apache/2.2.12 (Unix) mod_ssl/2.2.12 OpenSSL/0.9.8l DAV/2

    --1167a167-Z--

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Attack Scenarios

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Some malformed URIs are created on purpose as part of HTTP
fingerprinting scans -

<http://projects.webappsec.org/Fingerprinting>

Other times, these are caused by poorly written web clients.

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Ease of Attack

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Easy

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Ease of Detection

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Easy with either regular expressions or by monitoring Apache error
logging in phase:5

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

False Positives

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

**None known**
If there are any known false positives - specify them here Also sign-up
for the Reporting False Positives mail-list here:
<https://lists.sourceforge.net/lists/listinfo/mod-security-report-false-positives>
Send FP Report emails here:
mod-security-report-false-positives![10x](Justat.gif
"10x")lists.sourceforge.net

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

False Negatives

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

**None known**

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Rule Maturity

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

**8**
10 point scale (0-9) where:
0 = Beta/Experimental
9 = Heavily Tested

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Rule Accuracy

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

**8**
10 point scale (0-9) where:
0 = High % of FP
5 = No false positives reported

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Rule Documentation Contributor(s)

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Ryan Barnett - ryan.barnett![Justat.gif](Justat.gif
"Justat.gif")owasp.org

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Additional References

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

<http://www.w3.org/Protocols/rfc2616/rfc2616-sec3.html#sec3.2.1>

</td>

</tr>

</table>

[Category:OWASP ModSecurity Core Rule Set
Project](Category:OWASP_ModSecurity_Core_Rule_Set_Project "wikilink")