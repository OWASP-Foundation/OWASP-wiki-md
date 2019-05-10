Legend:
Review: M.Meucci
TD: Paragraph to be assigned

</ul>

## [Frontispiece](Testing_Guide_Frontispiece "wikilink")

1.  Copyright and License (100%, Review)
2.  Endorsements (100%, Review)
3.  Trademarks (100%, Review)

## [Introduction](Testing_Guide_Introduction "wikilink")

1.  Performing An Application Security Review 0% TD
2.  Principles of Testing 0% TD
3.  Testing Techniques Explained 0% TD

## [The OWASP Testing Framework](The_OWASP_Testing_Framework "wikilink")

3\. The OWASP Testing Framework 20% (Review)
**3.1. Overview**
**3.2. Phase 1 — Before Development Begins
**

  - Phase 1A: Policies and Standards Review
  - Phase 1B: Develop Measurement and Metrics Criteria (Ensure
    Traceability)

**3.3. Phase 2: During Definition and Design
**

  - Phase 2A: Security Requirements Review
  - Phase 2B: Design an Architecture Review
  - Phase 2C: Create and Review UML Models
  - Phase 2D: Create and Review Threat Models

**3.4. Phase 3: During Development
**

  - Phase 3A: Code Walkthroughs
  - Phase 3B: Code Reviews

**3.5. Phase 4: During Deployment
**

  - Phase 4A: Application Penetration Testing
  - Phase 4B: Configuration Management Testing

**3.6. Phase 5: Maintenance and Operations
**

  - Phase 5A: Conduct Operational Management Reviews
  - Phase 5B: Conduct Periodic Health Checks
  - Phase 5C: Ensure Change Verification

**3.7. A Typical SDLC Testing Workflow
**

  - Figure 3: Typical SDLC Testing Workflow

**3.8 Methodologies Used (Review)
** 3.8.1 The goal 50% TD
3.8.2 Overview of Approaches 50% TD
3.8.3 Security Requirements Review 0% TD
3.8.4 Security Architecture Review 0% TD
3.8.5 Code Review 50% TD
3.8.6 Automated Code Scanning 0% TD
3.8.7 Penetration Testing 50% TD
3.8.8 Automated Vulnerability Scanning 0% TD

## [Manual testing techniques](Manual_testing_techniques "wikilink")

**4.1 Introduction and objectives** 0% TD
**4.2 Information Gathering (spider, google)** 0% TD
**4.3 Business logic testing** 50% TD
**4.4 Authentication Testing** 50% TD
4.4.1 Default or guessable (dictionary) user account 90% TD
4.4.2 Brute Force 0% TD
4.4.3 Bypassing authentication schema 0% TD
4.4.4 Vulnerable remember password and pwd reset 90% TD
4.4.5 Logout and account expiry 0% TD
**4.5 Session Management Testing** 0% TD
4.5.1 Cookie and Session token Manipulation(reg, forg/brute force) 100%
Review
4.5.2 Weak session tokens 70% TD
4.5.3 Session Riding 100% Review
4.5.4 Exposed session variables 0% TD
4.5.5 HTTP Exploit 0% TD
**4.6 Data Validation Testing** 0% TD
4.6.1 Cross site scripting 0% TD
4.6.1.1 Incubated attacks 0% TD
4.6.1.2 Phishing (using javascript) 0% TD
4.6.1.3 HTTP Methods + XSS (TRACE) 0% TD
4.6.2 SQL Injection 0% TD
4.6.2.1 Oracle, mySQL, SQL Server, TeraData 0% TD
4.6.2.2 Extended stored procedures 0% TD
4.6.2.3 Stored procedure injection 0% TD
4.6.2.4 Oracle +SQLServer ports and attacks 0% TD
4.6.2.5 Listener attacks etc. 1521 1433 1527 0% TD
4.6.3 Orm injection 0% TD
4.6.4 Ldap injection 0% TD
4.6.5 Xml injection 0% TD
4.6.6 Code injection 0% TD
4.6.7 Buffer overflow Testing 100% Review
4.6.7.1 Heap overflow 100% Review
4.6.7.2 Stack overflow 100% Review
4.6.7.3 Format string 100% Review
**4.7 Denial of Service Testing** 95% Review
4.7.1 Locking Customer Accounts 100% Review
4.7.2 Buffer Overflows 100% Review
4.7.3 User Specified Object Allocation 100% Review
4.7.4 User Input as a Loop Counter 100% Review
4.7.5 Writing User Provided Data to Disk 100% Review
4.7.6 Failure to Release Resources 100% Review
4.7.7 Storing too Much Data in Session 90% Review
**4.8 Infrastructure and configuration Testing** 0% TD
4.8.1 Intro and objective 0% TD
4.8.2 Infrastructure configuration management testing 100% TD
4.8.3 Application configuration management testing 100% TD
4.8.4 Old, backup and unreferenced files 100% TD
4.8.5 File extensions handling 90% TD
4.8.6 Analisys of error code 50% TD
4.8.7 SSL/TLS Testing: support of weak ciphers and cert validity 100%
TD
4.8.8 Testing defense from Automatic attacks (maybe a duplicate) 10%
TD
**4.9 Web Services Testing** 0% TD
4.9.1 XML Structural Attacks 0% TD
4.9.2 XML content-level attacks 0% TD
4.9.3 HTTP GET parameters/REST attacks 0% TD
4.9.4 Naughty SOAP attachments 0% TD
4.9.5 Brute force attacks 0% TD
**4.10 AJAX Testing** 0% TD
4.10.1 Vulnerabilities 0% TD
4.10.2 How to test 0% TD

## [Writing Reports: value the real risk](Writing_Reports:_value_the_real_risk "wikilink")

**5.1 How to value the real risk** 0% TD
**5.2 How to write the report of the testing** 0% TD

## [Appendix A: Testing Tools](Appendix_A:_Testing_Tools "wikilink")

`  1. Source Code Analyzers`
`         * Open Source / Freeware`
`         * Commercial `
`  2. Black Box Scanners`
`         * Open Source`
`         * Commercial `
`  3. Other Tools`
`         * Runtime Analysis`
`         * Binary Analysis`
`         * Requirements Management `

## [Appendix B: Suggested Reading](OWASP_Testing_Guide_Appendix_B:_Suggested_Reading "wikilink")

`  1. Whitepapers`
`  2. Books`
`  3. Articles`
`  4. Useful Websites`
`  5. OWASP — `<http://www.owasp.org>` `

## [Appendix C: Fuzz Vectors](OWASP_Testing_Guide_Appendix_C:_Fuzz_Vectors "wikilink")




### Version 0.1 (October 4th)

**Paragraph___________________________________________________
|__State___ |___Action___ |___Author___**

1 Frontispiece

`  2.1 Copyright and License                                        100%      Review    `
`  2.2 Endorsements                                             100%      Review`
`  2.3 Trademarks                                               100%      Review    `

2\. Introduction

`  1. Performing An Application Security Review                       0%        TD`
`  2. Principles of Testing                                           0%        TD`
`  3. Testing Techniques Explained                                    0%        TD`

3\. Methodologies Used (Review)

`  3.1 The goal                                                      50%    TD`
`  3.2 Overview of Approaches                                        50%    TD`
`  3.3 Security Requirements Review                               0%    TD`
`  3.4 Security Architecture Review                               0%    TD`
`  3.5 Code Review                                               50%    TD`
`  3.6 Automated Code Scanning                                        0%    TD`
`  3.7 Penetration Testing                                       50%    TD`
`  3.8 Automated Vulnerability Scanning                               0%    TD`

4\. Finding Specific Issues In a Non-Technical Manner (Review)

`  4.1. Threat Modeling Introduction                                  0%    TD`
`  4.2. Design Reviews                                                0%    TD`
`  4.3. Threat Modeling the Application                               0%    TD`
`  4.4. Policy Reviews                                                0%    TD`
`  4.5. Requirements Analysis                                         0%    TD`
`  4.6. Developer Interviews and Interaction                          0%    TD`

5\. Finding Specific Vulnerabilities Using Source Code Review

`  5.1 For code review please see the OWASP Code Review Project`

6\. Manual testing techniques (Review)

`  6.1 Introduction and objectives                                0%    TD`
`  6.2 Information Gathering (spider, google)                         0%    TD`
`  6.3 Business logic testing                                        50%    TD`
`       `
`  6.4 Authentication Testing                                        50%        TD`
`  6.4.1 Default or guessable (dictionary) user account              90%        TD`
`  6.4.2 Brute Force                                                  0%        TD`
`  6.4.3 Bypassing authentication schema                              0%        TD`
`  6.4.4 Vulnerable remember password and pwd reset                  90%        TD`
`  6.4.5 Logout and account expiry                                0%        TD`
`       `
`  6.5 Session Management Testing                                     0%        TD`
`  6.5.1 Cookie and Session token Manipulation `
`           (regeneration, forging/brute force)                     100%       Review    `
`  6.5.2 Weak session tokens                                         70%        TD`
`  6.5.3 Session Riding                                             100%       Review`
`  6.5.4 Exposed session variables                                0%        TD`
`  6.5.5 HTTP Exploit                                                 0%        TD`
`       `
`  6.6 Data Validation Testing                                        0%        TD      `
`  6.6.1 Cross site scripting                                         0%        TD`
`  6.6.1.1 Incubated attacks                                          0%        TD`
`  6.6.1.2 Phishing (using javascript)                                0%        TD`
`  6.6.1.3  HTTP Methods + XSS (TRACE)                                0%        TD`
`  6.6.2 SQL Injection                                                0%        TD`
`  6.6.2.1 Oracle, mySQL, SQL Server, TeraData                        0%        TD  `
`  6.6.2.2 Extended stored procedures                                 0%        TD`
`  6.6.2.3 Stored procedure injection                                 0%        TD`
`  6.6.2.4 Oracle +SQLServer ports and attacks                        0%        TD`
`  6.6.2.5 Listener attacks etc. 1521 1433 1527                       0%        TD`
`  6.6.3 Orm injection                                                0%        TD`
`  6.6.4 Ldap injection                                               0%        TD`
`  6.6.5 Xml injection                                                0%        TD`
`  6.6.6 Code injection                                               0%        TD`
`       `
`  6.7 Denial of Service Testing                                     95%        Review`
`  6.7.1 Locking Customer Accounts                                  100%        Review`
`  6.7.2 Buffer Overflows                                           100%        Review      `
`  6.7.3 User Specified Object Allocation                           100%        Review      `
`  6.7.4 User Input as a Loop Counter                               100%        Review`
`  6.7.5 Writing User Provided Data to Disk                         100%        Review`
`  6.7.6 Failure to Release Resources                               100%        Review`
`  6.7.7 Storing too Much Data in Session                            90%        Review`

`  6.8 Buffer overflow Testing                                      100%        Review      `
`  6.8.1 Heap overflow                                              100%        Review`
`  6.8.2 Stack overflow                                             100%        Review`
`  6.8.3 Format string                                              100%        Review`

`  6.9 Infrastructure and configuration Testing                       0%         TD`
`   6.9.1 Intro and objective                                         0%         TD`
`   6.9.2 Infrastructure configuration management testing           100%         TD`
`   6.9.3 Application configuration management testing              100%         TD`

`   6.9.4 Old, backup and unreferenced files                        100%         TD `
`   6.9.5 File extensions handling                           90%         TD`
`   6.9.6 Analisys of error code                                     50%         TD     `
`   6.9.7 SSL/TLS Testing: support of weak                          100%         TD`
`             ciphers and certificate validity      `
`   6.9.8 Testing defense from Automatic                             10%         TD`
`             Attacks (maybe a duplicate)       `

`  6.10 Web Services Testing                                          0%         TD`
`  6.10.1 XML Structural Attacks                                      0%    TD`
`  6.10.2 XML content-level attacks                               0%    TD`
`  6.10.3 HTTP GET parameters/REST attacks                        0%    TD`
`  6.10.4 Naughty SOAP attachments                                0%    TD`
`  6.10.5 Brute force attacks                                         0%    TD`

`  6.11 AJAX Testing                                                  0%    TD`
`  6.11.1 Vulnerabilities                                         0%    TD`
`  6.11.2  How to test                                                0%    TD`

7\. The OWASP Testing Framework 95% (Review)

`  7.1. Overview`
`  7.2. Phase 1 — Before Development Begins`
`         * Phase 1A: Policies and Standards Review`
`         * Phase 1B: Develop Measurement and Metrics Criteria `
`           (Ensure Traceability) `
`  7.3. Phase 2: During Definition and Design`
`         * Phase 2A: Security Requirements Review`
`         * Phase 2B: Design an Architecture Review`
`         * Phase 2C: Create and Review UML Models`
`         * Phase 2D: Create and Review Threat Models `
`  7.4. Phase 3: During Development`
`         * Phase 3A: Code Walkthroughs`
`         * Phase 3B: Code Reviews `
`  7.5. Phase 4: During Deployment`
`         * Phase 4A: Application Penetration Testing`
`         * Phase 4B: Configuration Management Testing `
`  7.6. Phase 5: Maintenance and Operations`
`         * Phase 5A: Conduct Operational Management Reviews`
`         * Phase 5B: Conduct Periodic Health Checks`
`         * Phase 5C: Ensure Change Verification `
`  7.7. A Typical SDLC Testing Workflow`
`         * Figure 3: Typical SDLC Testing Workflow. `

Appendix A: Testing Tools 95% (Review)

`  1. Source Code Analyzers`
`         * Open Source / Freeware`
`         * Commercial `
`  2. Black Box Scanners`
`         * Open Source`
`         * Commercial `
`  3. Other Tools`
`         * Runtime Analysis`
`         * Binary Analysis`
`         * Requirements Management `

Appendix B: Suggested Reading 95% (Review)

`  1. Whitepapers`
`  2. Books`
`  3. Articles`
`  4. Useful Websites`
`  5. OWASP — `<http://www.owasp.org>` `

Appendix C: Fuzz Vectors 95% (Review)