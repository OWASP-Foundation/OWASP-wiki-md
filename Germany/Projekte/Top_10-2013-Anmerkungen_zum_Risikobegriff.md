Although the [|2007](https://www.owasp.org/index.php/Top_10_2007) and
earlier versions of the [OWASP
Top 10](https://www.owasp.org/index.php/Top10) focused on identifying
the most common “vulnerabilities,” the OWASP Top 10 has always been
organized around risks. This has caused some understandable confusion on
the part of people searching for an airtight weakness taxonomy. The
[OWASP Top 10 for 2010](https://www.owasp.org/index.php/Top_10_2010)
clarified the risk-focus in the Top 10 by being very explicit about how
threat agents, attack vectors, weaknesses, technical impacts, and
business impacts combine to produce risks. This version of the OWASP Top
10 follows the same methodology.Although the
[2007](https://www.owasp.org/index.php/Top_10_2007) and earlier versions
of the [OWASP Top 10](https://www.owasp.org/index.php/Top10) focused on
identifying the most common “vulnerabilities,” the OWASP Top 10 has
always been organized around risks. This has caused some understandable
confusion on the part of people searching for an airtight weakness
taxonomy. The [OWASP Top 10
for 2010](https://www.owasp.org/index.php/Top_10_2010) clarified the
risk-focus in the Top 10 by being very explicit about how threat agents,
attack vectors, weaknesses, technical impacts, and business impacts
combine to produce risks. This version of the OWASP Top 10 follows the
same methodology.

The Risk Rating methodology for the Top 10 is based on the [OWASP Risk
Rating
Methodology](https://www.owasp.org/index.php/OWASP_Risk_Rating_Methodology).
For each Top 10 item, we estimated the typical risk that each weakness
introduces to a typical web application by looking at common likelihood
factors and impact factors for each common weakness. We then rank
ordered the Top 10 according to those weaknesses that typically
introduce the most significant risk to an application.

The [OWASP Risk Rating
Methodology](https://www.owasp.org/index.php/OWASP_Risk_Rating_Methodology)
defines numerous factors to help calculate the risk of an identified
vulnerability. However, the Top 10 must talk about generalities, rather
than specific vulnerabilities in real applications. Consequently, we can
never be as precise as system owners can be when calculating risks for
their application(s). You are best equipped to judge the importance of
your applications and data, what your threat agents are, and how your
system has been built and is being operated.

Our methodology includes three likelihood factors for each weakness
(prevalence, detectability, and ease of exploit) and one impact factor
(technical impact). The prevalence of a weakness is a factor that you
typically don’t have to calculate. For prevalence data, we have been
supplied prevalence statistics from a number of different organizations
(as referenced in the Acknowledgements section on page 3) and we have
averaged their data together to come up with a Top 10 likelihood of
existence list by prevalence. This data was then combined with the other
two likelihood factors (detectability and ease of exploit) to calculate
a likelihood rating for each weakness. This was then multiplied by our
estimated average technical impact for each item to come up with an
overall risk ranking for each item in the Top 10.

Note that this approach does not take the likelihood of the threat agent
into account. Nor does it account for any of the various technical
details associated with your particular application. Any of these
factors could significantly affect the overall likelihood of an attacker
finding and exploiting a particular vulnerability. This rating also does
not take into account the actual impact on your business. Your
organization will have to decide how much security risk from
applications the organization is willing to accept given your culture,
industry, and regulatory environment. The purpose of the OWASP Top 10 is
not to do this risk analysis for you.

<td>

 

</td>

<td style="text-align: center; padding: 4px; font-size: 200%; font-weight: bold; border: 3px solid #444444;">

2

</td>

<td style="text-align: center; padding: 4px; font-size: 200%; font-weight: bold; border: 3px solid #444444;">

0

</td>

<td style="text-align: center; padding: 4px; font-size: 200%; font-weight: bold; border: 3px solid #444444;">

1

</td>

<td style="text-align: center; padding: 4px; font-size: 200%; font-weight: bold; border: 3px solid #444444;">

2

</td>

<td>

 

</td>

</tr>

<tr>

<td>

 

</td>

<td colspan="3"  style="border: #4d953d 1px solid; background-color: #D9D9D9; text-align: center; padding: 4px;">

<span style="font-weight: bold; font-size: 150%; color: red;">Likelihood
Rating: 1</span>
     (Average of Exploitability, Prevalence and Detectability)

</td>

<td style="text-align: center; padding: 4px; font-size: 200%; font-weight: bold; solid #444444;">

\* 2  

</td>

<td>

 

</td>

</tr>

<tr>

<td>

 

</td>

<td>

 

</td>

<td colspan="3"  style="border: #4d953d 1px solid; background-color: #D9D9D9; text-align: center; padding: 4px;">

<span style="font-weight: bold; font-size: 150%; color: red;">Risk
Ranking: 2</span>
     (Likelihood \* Impact)

<td>

 

</td>