__NOTOC__

Return to [Global Industry
Committee](Global_Industry_Committee "wikilink")

| colspan="4" align="center" style="background:\#4058A0; color:white" | <font color="white">**ACTIVITY IDENTIFICATION** |
| ------------------------------------------------------------------- | ----------------------------------------------- |
| style="width:15%; background:\#7B8ABD" align="center"               | **Activity Name**                               |
| style="width:25%; background:\#7B8ABD" align="center"               | **Short Description**                           |
| style="width:25%; background:\#7B8ABD" align="center"               | '''Related Projects '''                         |
| style="width:25%; background:\#7B8ABD" align="center"               | **Email Contacts & Roles**                      |

| colspan="4" align="center" style="background:\#4058A0; color:white" | <font color="white">**ACTIVITY SPECIFICS** |
| ------------------------------------------------------------------- | ------------------------------------------ |
| style="width:25%; background:\#7B8ABD" align="center"               | **Objectives**                             |
| style="width:25%; background:\#7B8ABD" align="center"               | **Deadlines**                              |
| style="width:25%; background:\#7B8ABD" align="center"               | **Status**                                 |
| style="width:25%; background:\#7B8ABD" align="center"               | **Resources**                              |
|                                                                     |                                            |

## Submission Response

*Latest first*

### Final version

![<File:Owasp-ico-data-sharing-cop-consultation-response-1.pdf>](Owasp-ico-data-sharing-cop-consultation-response-1.pdf
"File:Owasp-ico-data-sharing-cop-consultation-response-1.pdf")

### Draft Text version 1

#### Introduction

This official response has been submitted on behalf of the Open Web
Application Security Project (OWASP) by the OWASP Global Industry
Committee, following our own consultation process.

#### Response

The OWASP response only replies to two questions.

**6. Is the code relevant to the types of data sharing your organisation
is involved in? If not, which additional areas should we cover?**

In "Technical Security" on page 15, there is no mention of websites, yet
these are one of the common channels that lead to personal data
breaches. Our suggestion is to add an item: "If personal data is
collected or processed using a web site or mobile application, have the
most common security risks been identified, removed or mitigated?"

This could reference as footnotes, or in other supporting materials, the
following free guidance documents:

  - [OWASP Top Ten - The Ten Most Critical Web Application Security
    Risks](http://www.owasp.org/index.php/Category:OWASP_Top_Ten_Project#tab=Main)
    and further guidance contained therein
  - [WASC Threat
    Classification](http://projects.webappsec.org/Threat-Classification)
  - [CWE/SANS TOP 25 Most Dangerous Software
    Errors](http://www.sans.org/top25-software-errors/)

**10. Is there anything else you think the code should cover or are
there any other ways in which you think the code could be improved?**

In "technical security" on page 15, we believe "is your information
encrypted" is too simplistic. Many difficulties exist in implementing
encryption properly and problems can be introduced in unexpected ways.
Whilst we understand this document cannot provide all the detail
required, a better question would be "How is encryption implemented and
managed?"

On page 17 in the discussion of data standards, non-Latin characters are
mentioned, but the more generic issues of encoding (e.g. UTF-8) and
escaping are not. These are significant factors in successful data
sharing and for ensuring the integrity of the data once it has been
exported from one system and imported into another. If not properly
defined and implemented, data that is safe in one system might actively
exploit a weakness in another leading to data loss, destruction, etc
(e.g. by SQL injection). Our suggestion is to add after "capabilities of
its system.", a new sentence "Ensure the data are correctly encoded and
escaped when output so they can safely be used by the receiving
system.".

#### About OWASP

*to be added in final draft*

Return to [Global Industry
Committee](Global_Industry_Committee "wikilink")