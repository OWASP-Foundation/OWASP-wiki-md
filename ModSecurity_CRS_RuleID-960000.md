## Rule ID: 960000

<table style="border-style:double;border-width:3px;" >

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Rule ID

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

960000

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Rule Message

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Attempted multipart/form-data bypass

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Rule Summary

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Identify multipart/form-data name evasion attempts

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Impact

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

2 - Critical

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Rule

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

`SecRule FILES_NAMES|FILES "['\";=]"
"phase:2,t:none,id:'960000',rev:'2.2.5',block,capture,msg:'Attempted
multipart/form-data
bypass',logdata:'%{matched_var}',severity:'2',setvar:'tx.msg=%{rule.msg}',setvar:'tx.id=%{rule.id}',tag:'RULE_MATURITY/7',tag:'RULE_ACCURACY/7',tag:'`[`https://www.owasp.org/index.php/ModSecurity_CRS_RuleID-%{tx.id`](https://www.owasp.org/index.php/ModSecurity_CRS_RuleID-%%7Btx.id)`}',setvar:tx.anomaly_score=+%{tx.critical_anomaly_score},setvar:tx.protocol_violation_score=+%{tx.notice_anomaly_score},setvar:tx.%{rule.id}-PROTOCOL_VIOLATION/INVALID_REQ-%{matched_var_name}=%{tx.0}"`

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Detailed Rule Information

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

  - There are possible impedance mismatches between how ModSecurity
    interprets multipart file names and how a destination app server
    such as PHP might parse the Content-Disposition data.
  - These rules check for the existence of the ' " ; = meta-characters
    in either the file or file name variables in order to detect evasion
    attempts.

<!-- end list -->

    ///  A description of the regular expression:
    ///
    ///  Match any (single) character contained within the brackets

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Example Payload

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Content-Disposition: form-data; name="fileRap"; filename="file=.txt"

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Example Audit Log Entry

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

Include an example ModSecurity Audit Log Entry for when this rule
matchs.

    --50b28e4c-A--
    [27/Jun/2012:16:07:22 +0300] T@sFin8AAQEAADwGDRIAAAAA 127.0.0.1 56803 127.0.0.1 80
    --50b28e4c-B--
    POST /fileupload.asp HTTP/1.1
    Host: localhost
    Accept: */*
    Accept-Language: en
    User-Agent: Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 6.0)
    Connection: close
    Referer: http://localhost/
    Content-Type: multipart/form-data; boundary=--------397236876
    Content-Length: 930

    --50b28e4c-C--
    ----------397236876
    Content-Disposition: form-data; name="fileRap"; filename="file=.txt"
    Content-Type: text/plain

    555-555-0199@example.com
    ----------397236876

    --50b28e4c-F--
    HTTP/1.1 403 Forbidden
    Vary: Accept-Encoding
    Content-Length: 307
    Connection: close
    Content-Type: text/html; charset=iso-8859-1

    --50b28e4c-E--

    --50b28e4c-H--
    Message: Access denied with code 403 (phase 2). Pattern match "['\";=]" at FILES:fileRap. [file "/opt/modsecurity/etc/crs/base_rules/modsecurity_crs_20_protocol_violations.conf"] [line "73"] [id "960000"] [rev "2.2.5"] [msg "Attempted multipart/form-data bypass"] [data "file=.txt"] [severity "CRITICAL"] [tag "RULE_MATURITY/7"] [tag "RULE_ACCURACY/7"] [tag "https://www.owasp.org/index.php/ModSecurity_CRS_RuleID-960000"]
    Action: Intercepted (phase 2)
    Stopwatch: 1340802442388746 3425 (- - -)
    Stopwatch2: 1340802442388746 3425; combined=2114, p1=1798, p2=300, p3=0, p4=0, p5=15, sr=91, sw=1, l=0, gc=0
    Response-Body-Transformed: Dechunked
    Producer: ModSecurity for Apache/2.7.0-dev1 (http://www.modsecurity.org/); core ruleset/2.2.5.
    Server: Apache/2.2.22 (Debian)
    Engine-Mode: "ENABLED"

    --50b28e4c-K--
    SecRule "FILES_NAMES|FILES" "@rx ['\";=]" "phase:2,log,t:none,id:960000,rev:2.2.5,block,capture,msg:'Attempted multipart/form-data bypass',logdata:%{matched_var},severity:2,setvar:tx.msg=%{rule.msg},setvar:tx.id=%{rule.id},tag:RULE_MATURITY/7,tag:RULE_ACCURACY/7,tag:https://www.owasp.org/index.php/ModSecurity_CRS_RuleID-%{tx.id},setvar:tx.anomaly_score=+%{tx.critical_anomaly_score},setvar:tx.protocol_violation_score=+%{tx.notice_anomaly_score},setvar:tx.%{rule.id}-PROTOCOL_VIOLATION/INVALID_REQ-%{matched_var_name}=%{tx.0}"


    --50b28e4c-Z--

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Attack Scenarios

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

An attacker manipulated the file name which is mistakenly treated as
code by the backend server.

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

Easy with regular expressions

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

**7**
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

**7**
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

Josh Amishav-Zlatin - jamuse![Justat.gif](Justat.gif
"Justat.gif")gmail.com.com

</td>

</tr>

<tr>

<td style="border-style:solid;border-width:1px;background-color:#CCCCCC;text-transform:uppercase " >

Additional References

</td>

<td style="background-color:#F2F2F2;table-layout:fixed;width:700px;" >

<http://www.ietf.org/rfc/rfc2183.txt>

</td>

</tr>

</table>

[Category:OWASP ModSecurity Core Rule Set
Project](Category:OWASP_ModSecurity_Core_Rule_Set_Project "wikilink")