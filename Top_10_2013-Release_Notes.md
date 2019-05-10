The threat landscape for applications security constantly changes. Key
factors in this evolution are advances made by attackers, the release of
new technologies with new weaknesses as well as more built in defenses,
and the deployment of increasingly complex systems. To keep pace, we
periodically update the OWASP Top 10. In this 2013 release, we made the
following changes:

1.  Broken Authentication and Session Management moved up in prevalence
    based on our data set. Probably because this area is being looked at
    harder, not because issues are actually more prevalent. This caused
    Risks A2 and A3 to switch places.
2.  Cross-Site Request Forgery (CSRF) moved down in prevalence based on
    our data set from 2010-A5 to 2013-A8. We believe this is because
    CSRF has been in the OWASP Top 10 for 6 years, and organizations and
    framework developers have focused on it enough to significantly
    reduce the number of CSRF vulnerabilities in real world
    applications.
3.  We broadened Failure to Restrict URL Access from the 2010 OWASP Top
    10 to be more inclusive:
    \+     2010-A8: Failure to Restrict URL Access is now <u>2013-A7:
    Missing Function Level Access Control</u> – to cover all of function
    level access control. There are many ways to specify which function
    is being accessed, not just the URL.
4.  We merged and broadened 2010-A7 & 2010-A9 to CREATE: <u>2013-A6:
    Sensitive Data Exposure</u>:
    \-     This new category was created by merging 2010-A7 – Insecure
    Cryptographic Storage & 2010-A9 - Insufficient Transport Layer
    Protection, plus adding browser side sensitive data risks as well.
    This new category covers sensitive data protection (other than
    access control which is covered by 2013-A4 and 2013-A7) from the
    moment sensitive data is provided by the user, sent to and stored
    within the application, and then sent back to the browser again.
5.  We added: <u>2013-A9: Using Components with Known
    Vulnerabilities</u>:
    \+     This issue was mentioned as part of 2010-A6 – Security
    Misconfiguration, but now has a category of its own as the growth
    and depth of component based development has significantly increased
    the risk of using components with known vulnerabilities.

<center>

| OWASP Top 10 - 2010 (Previous Version)                                               | OWASP Top 10 - 2013 (Current Version)                                                                            |
| ------------------------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------------------------- |
| [A1-Injection](Top_10_2010-A1 "wikilink")                                            | [text=documentRootTop10]({{Top_10:LanguageFile "wikilink")                                                       |
| [A3-Broken Authentication and Session Management](Top_10_2010-A3 "wikilink")         | [text=documentRootTop10]({{Top_10:LanguageFile "wikilink")                                                       |
| [A2-Cross Site Scripting (XSS)](Top_10_2010-A2 "wikilink")                           | [text=documentRootTop10]({{Top_10:LanguageFile "wikilink")                                                       |
| [A4-Insecure Direct Object Reference](Top_10_2010-A4 "wikilink")                     | [text=documentRootTop10]({{Top_10:LanguageFile "wikilink")                                                       |
| [A6-Security Misconfiguration](Top_10_2010-A6 "wikilink")                            | [text=documentRootTop10]({{Top_10:LanguageFile "wikilink")                                                       |
| [A7-Insecure Cryptographic Storage - Merged with A9 --\>](Top_10_2010-A7 "wikilink") | [text=documentRootTop10]({{Top_10:LanguageFile "wikilink")                                                       |
| [A8-Failure to Restrict URL Access - Broadened into --\>](Top_10_2010-A8 "wikilink") | [text=documentRootTop10]({{Top_10:LanguageFile "wikilink")                                                       |
| [A5-Cross Site Request Forgery (CSRF)](Top_10_2007-A5 "wikilink")                    | [text=documentRootTop10]({{Top_10:LanguageFile "wikilink")                                                       |
| [<buried in A6: Security Misconfiguration>](Top_10_2010-A6 "wikilink")               | [text=documentRootTop10]({{Top_10:LanguageFile "wikilink")                                                       |
| [A10-Unvalidated Redirects and Forwards](Top_10_2010-A10 "wikilink")                 | [text=documentRootTop10]({{Top_10:LanguageFile "wikilink")                                                       |
| [A9-Insufficient Transport Layer Protection](Top_10_2010-A9 "wikilink")              | Merged with [2010-A7](Top_10_2010-A7 "wikilink") into [text=documentRootTop10]({{Top_10:LanguageFile "wikilink") |

</center>