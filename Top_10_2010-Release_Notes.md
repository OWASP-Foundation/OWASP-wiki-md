The threat landscape for Internet applications constantly changes. Key
factors in this evolution are advances made by attackers, the release of
new technology, as well as the deployment of increasingly complex
systems. To keep pace, we periodically update the OWASP Top 10. In this
2010 release, we have made three significant changes:

1.  We clarified that the Top 10 is about the Top 10 Risks, not the Top
    10 most common weaknesses. See the details on the “Application
    Security Risks” page below.
2.  We changed our ranking methodology to estimate risk, instead of
    relying solely on the frequency of the associated weakness. This has
    affected the ordering of the Top 10, as you can see in the table
    below.
3.  We replaced two items on the list with two new items:

<div style="margin-left: 50px;">

  - ADDED: A6 – Security Misconfiguration. This issue was A10 in the Top
    10 from 2004: Insecure Configuration Management, but was dropped in
    2007 because it wasn’t considered to be a software issue. However,
    from an organizational risk and prevalence perspective, it clearly
    merits re-inclusion in the Top 10; so now it’s back.
  - ADDED: A10 – Unvalidated Redirects and Forwards. This issue is
    making its debut in the Top 10. The evidence shows that this
    relatively unknown issue is widespread and can cause significant
    damage.
  - REMOVED: A3 – Malicious File Execution. This is still a significant
    problem in many different environments. However, its prevalence in
    2007 was inflated by large numbers of PHP applications having this
    problem. PHP now ships with a more secure configuration by default,
    lowering the prevalence of this problem.
  - REMOVED: A6 – Information Leakage and Improper Error Handling. This
    issue is extremely prevalent, but the impact of disclosing stack
    trace and error message information is typically minimal. With the
    addition of Security Misconfiguration this year, proper
    configuration of error handling is a big part of securely
    configuring your application and servers.
    </div>

<center>

| OWASP Top 10 - 2007 (Previous Version)                                                                          | OWASP Top 10 - 2010 (Current Version)                                        |
| --------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| [A2-Injection Flaws](Top_10_2007-A2 "wikilink")                                                                 | [A1-Injection](Top_10_2010-A1 "wikilink")                                    |
| [A1-Cross Site Scripting (XSS)](Top_10_2007-A1 "wikilink")                                                      | [A2-Cross Site Scripting (XSS)](Top_10_2010-A2 "wikilink")                   |
| [A7-Broken Authentication and Session Management](Top_10_2007-A7 "wikilink")                                    | [A3-Broken Authentication and Session Management](Top_10_2010-A3 "wikilink") |
| [A4-Insecure Direct Object Reference](Top_10_2007-A4 "wikilink")                                                | [A4-Insecure Direct Object References](Top_10_2010-A4 "wikilink")            |
| [A5-Cross Site Request Forgery (CSRF)](Top_10_2007-A5 "wikilink")                                               | [A5-Cross Site Request Forgery (CSRF)](Top_10_2010-A5 "wikilink")            |
| [(was T10 2004 A10 - Insecure Configuration Management)](A10_2004_Insecure_Configuration_Management "wikilink") | [A6 Security Misconfiguration (NEW)](Top_10_2010-A6 "wikilink")              |
| [A8-Insecure Cryptographic Storage](Top_10_2007-A8 "wikilink")                                                  | [A7-Insecure Cryptographic Storage](Top_10_2010-A7 "wikilink")               |
| [A10-Failure to Restrict URL Access](Top_10_2007-A10 "wikilink")                                                | [A8-Failure to Restrict URL Access](Top_10_2010-A8 "wikilink")               |
| [A9-Insecure Communications](Top_10_2007-A9 "wikilink")                                                         | [A9-Insufficient Transport Layer Protection](Top_10_2010-A9 "wikilink")      |
| (not in 2007 Top 10)                                                                                            | [A10-Unvalidated Redirects and Forwards (NEW)](Top_10_2010-A10 "wikilink")   |
| [A3-Malicious File Execution](Top_10_2007-A3 "wikilink")                                                        | \<dropped from 2010 Top 10\>                                                 |
| [A6-Information Leakage and Improper Error Handling](Top_10_2007-A6 "wikilink")                                 | \<dropped from 2010 Top 10\>                                                 |

</center>

[Category:OWASP Top Ten
Project](Category:OWASP_Top_Ten_Project "wikilink")