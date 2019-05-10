At the OWASP Project Summit, active participants and community members
decided on a vulnerability view, with up to two (2) forward looking
vulnerability classes, with ordering defined partially by quantitative
data, and partially by qualitative surveys.

For the survey, we collected the vulnerability categories that had been
previously identified as being “on the cusp” or were mentioned in
feedback to 2017 RC1 on the Top 10 mailing list. We put them into a
ranked survey and asked respondents to rank the top four vulnerabilities
that they felt should be included in the OWASP Top 10 - 2017. The survey
was open from Aug 2 – Sep 18, 2017. 516 responses were collected and the
vulnerabilities were ranked.

<center>

<table style="align:center; border-collapse: collapse; text-align:center; margin: 0px 5px 0px 5px; border: 3px solid #444444; background-color: {{Top 10:BackgroundColor|year=2017 }}; padding=2;">

<tr style="background-color: {{Top 10:BorderColor|year=2017}}; height: 2em; font-size: 130%; color: #FFFFFF;  text-shadow: 2px 2px 8px #444444; ">

<th style="border: 3px solid #444444;">

</th>

<th style="border: 3px solid #444444; text-align:left;">

</th>

<th style="border: 3px solid #444444;">

</th>

</tr>

<tr>

<td style="border: 3px solid #444444;">

1

</td>

<td style="border: 3px solid #444444; text-align:left;">

Exposure of Private Information ('Privacy Violation') \[CWE-359\]

</td>

<td style="border: 3px solid #444444;">

748

</td>

</tr>

<tr>

<td style="border: 3px solid #444444;">

2

</td>

<td style="border: 3px solid #444444; text-align:left;">

Cryptographic Failures \[CWE-310/311/312/326/327\]

</td>

<td style="border: 3px solid #444444;">

584

</td>

</tr>

<tr>

<td style="border: 3px solid #444444;">

3

</td>

<td style="border: 3px solid #444444; text-align:left;">

Deserialization of Untrusted Data \[CWE-502\]

</td>

<td style="border: 3px solid #444444;">

514

</td>

</tr>

<tr>

<td style="border: 3px solid #444444;">

4

</td>

<td style="border: 3px solid #444444; text-align:left;">

Authorization Bypass Through User-Controlled Key (IDOR & Path Traversal)
\[CWE-639\] 

</td>

<td style="border: 3px solid #444444;">

493

</td>

</tr>

<tr>

<td style="border: 3px solid #444444;">

5

</td>

<td style="border: 3px solid #444444; text-align:left;">

Insufficient Logging and Monitoring \[CWE-223 / CWE-778\]

</td>

<td style="border: 3px solid #444444;">

440

</td>

</tr>

</table>

</center>

Exposure of Private Information is clearly the highest-ranking
vulnerability, but fits very easily as an additional emphasis into the
existing
<b><u>[text=documentRootTop10New]({{Top_10:LanguageFile "wikilink")</u></b>.
Cryptographic Failures can fit within Sensitive Data Exposure. Insecure
deserialization was ranked at number three, so it was added to the Top
10 as
<b><u>[text=documentRootTop10New]({{Top_10:LanguageFile "wikilink")</u></b>
after risk rating. The fourth ranked User-Controlled Key is included in
<b><u>[text=documentRootTop10New]({{Top_10:LanguageFile "wikilink")</u></b>;
it is good to see it rank highly on the survey, as there is not much
data relating to authorization vulnerabilities. The number five ranked
category in the survey is Insufficient Logging and Monitoring, which we
believe is a good fit for the Top 10 list, which is why it has become
<b><u>[text=documentRootTop10New]({{Top_10:LanguageFile "wikilink")</u></b>.
We have moved to a point where applications need to be able to define
what may be an attack and generate appropriate logging, alerting,
escalation and response. 

Traditionally, the data collected and analyzed was more along the lines
of frequency data: how many vulnerabilities were found in tested
applications. As is well known, tools traditionally report all instances
found of a vulnerability and humans traditionally report a single
finding with a number of examples. This makes it very difficult to
aggregate the two styles of reporting in a comparable manner.

For 2017, the incidence rate was calculated by how many applications in
a given data set had one or more of a specific vulnerability type. The
data from many larger contributors was provided in two views. The first
was the traditional frequency style of counting every instance found of
a vulnerability, while the second was the count of applications in which
each vulnerability was found in (one or more times). While not perfect,
this reasonably allows us to compare the data from Human Assisted Tools
and Tool Assisted Humans. The raw data and analysis work is
<u>[available in
GitHub](https://github.com/OWASP/Top10/tree/master/2017/datacall)</u>.
We intend to expand on this with additional structure for future
versions of the Top 10.

We received 40+ submissions in the call for data, and because many were
from the original data call that was focused on frequency, we were able
to use data from 23 contributors covering \~114,000 applications. We
used a one-year block of time where possible and identified by the
contributor. The majority of applications are unique, though we
acknowledge the likelihood of some repeat applications between the
yearly data from Veracode. The 23 data sets used were either identified
as tool assisted human testing or specifically provided incidence rate
from human assisted tools. Anomalies in the selected data of 100%+
incidence were adjusted down to 100% max. To calculate the incidence
rate, we calculated the percentage of the total applications there were
found to contain each vulnerability type. The ranking of incidence was
used for the prevalence calculation in the overall risk for ranking the
Top 10.