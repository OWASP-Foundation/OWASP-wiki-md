## Rule ID: 981227

<table style="border-style:double;border-width:3px;" >

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Rule ID

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

981227

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Rule Message

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Apache Error: Invalid URI in Request

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Rule Summary

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Identify Invalid URIs Blocked by Apache

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

`SecRule WEBSERVER_ERROR_LOG "@contains Invalid URI in request" "phase:5,t:none,log,pass,msg:'Apache Error: Invalid URI in Request',id:'981227',rev:'2.2.0',`
`logdata:'%{matched_var}',severity:'4',tag:'`[`https://www.owasp.org/index.php/ModSecurity_CRS_RuleID-%{tx.id`](https://www.owasp.org/index.php/ModSecurity_CRS_RuleID-%%7Btx.id)`}',tag:'`<http://www.w3.org/Protocols/rfc2616/rfc2616->
`sec3.html#sec3.2.1',tag:'RULE_ACCURACY_LEVEL/5',setvar:'tx.msg=%{rule.msg}',setvar:'tx.id=%{rule.id}',setvar:tx.anomaly_score=+%{tx.notice_anomaly_score},`
`setvar:tx.protocol_violation_score=+%{tx.notice_anomaly_score},setvar:'tx.%{rule.id}-PROTOCOL_VIOLATION/INVALID_REQ-%{matched_var_name}=%{matched_var}'"`</code>

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Detailed Rule Information

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

`There are some request violations that Apache will handle internally, prior to the`
`ModSecurity phase:1 POST-READ-REQUEST hook.  For these requests, we can still get`
`visibility by running a check in phase:5 logging to look for the Apache error msg.`

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Example Payload

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Here is an example payloads taken from the access_log:

`127.0.0.1 - - [06/May/2011:11:22:24 -0400] "\tGET / HTTP/1.1" 400 226`

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Example Audit Log Entry

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Include an example ModSecurity Audit Log Entry for when this rule
matchs.

    --57ae6b4f-A--
    [06/May/2011:11:22:24 --0400] TcQSMMCoAWQAAKNEEHMAAAAA 127.0.0.1 62905 127.0.0.1 80
    --57ae6b4f-B--
            GET / HTTP/1.1
    Host: local
    User-Agent: Mozilla/5.0 (Windows; U; Windows NT 5.1; en-US; rv:1.8.0.7) Gecko/20060909 Firefox/1.5.0.7
    Accept: text/xml,application/xml,application/xhtml+xml,text/html;q=0.9,text/plain;q=0.8,image/png,*/*;q=0.5

    --57ae6b4f-F--
    HTTP/1.1 400 Bad Request
    Content-Length: 226
    Connection: close
    Content-Type: text/html; charset=iso-8859-1

    --57ae6b4f-E--
    <!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML 2.0//EN">
    <html><head>
    <title>400 Bad Request</title>
    </head><body>
    <h1>Bad Request</h1>
    <p>Your browser sent a request that this server could not understand.<br />
    </p>
    </body></html>

    --57ae6b4f-H--
    Message: Warning. String match "Invalid URI in request" at WEBSERVER_ERROR_LOG. [file "/usr/local/apache/conf/crs/base_rules/modsecurity_crs_20_protocol_violations.conf"]
    [line "51"] [id "981227"] [rev "2.2.0"] [msg "Apache Error: Invalid URI in Request"] [data "[file \x22core.c\x22] [line 3504] [level 3] Invalid URI in request \x5c\x5ctGET / HTTP/1.1"]
    [severity "WARNING"] [tag "https://www.owasp.org/index.php/ModSecurity_CRS_RuleID-981227"] [tag "http://www.w3.org/Protocols/rfc2616/rfc2616-sec3.html#sec3.2.1"]
    [tag "RULE_CONFIDENCE_LEVEL/5"]
    Apache-Error: [file "core.c"] [line 3504] [level 3] Invalid URI in request \\tGET / HTTP/1.1
    Stopwatch: 1304695344229544 6998 (- - -)
    Stopwatch2: 1304695344229544 6998; combined=5474, p1=0, p2=0, p3=140, p4=4392, p5=942, sr=0, sw=0, l=0, gc=0
    Response-Body-Transformed: Dechunked
    Producer: ModSecurity for Apache/2.6.0-rc2 (http://www.modsecurity.org/); core ruleset/2.2.0.
    Server: Apache/2.2.17 (Unix) mod_ssl/2.2.12 OpenSSL/0.9.8l DAV/2

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

**0**
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

**9**
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