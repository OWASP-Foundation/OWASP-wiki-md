# **OWASP Code Review Guide v2.0:**

## Forward

1.  Author - Eoin Keary
2.  Previous version to be
    updated:[1](https://www.owasp.org/index.php/Code_Review_Guide_History)

**[Content here](CRV2_Forward "wikilink")**

## Code Review Guide Introduction

1.  Author - Eoin Keary
2.  Previous version to be
    updated:[2](https://www.owasp.org/index.php/Code_Review_Introduction)

**[Content here](CRV2_Introduction "wikilink")**

### What is source code review and Static Analysis

### What is Code Review

1.  Author - Zyad Mghazli, Eoin Keary
2.  New Section

*' [Content here](CRV2_WhatIsCodeReview "wikilink")*'

### Manual Review - Pros and Cons

1.  Author - Zyad Mghazli, Eoin Keary,Gary David Robinson
2.  New Section
3.  Suggestion: Benchmark of different Stataic Analysis Tools Zyad
    Mghazli
4.  [Put content here](CRV2_ManualReviewProsCons "wikilink")

### Advantages of Code Review to Development Practices

1.  Author - Gary David Robinson
2.  New Section
3.  [Put content here](CRV2_AdvantagesToDevPractices "wikilink")

### Why code review

#### Scope and Objective of secure code review

1.  Author - Ashish Rao
2.  [Put content here](CRV2_WhyCodeReview "wikilink")

### We can't hack ourselves secure

1.  Author - Eoin Keary
2.  New Section
3.  [Put content here](CRV2_CantHackSecure "wikilink")

### 360 Review: Coupling source code review and Testing / Hybrid Reviews

1.  Author - eoin Keary
2.  New Section
3.  [Put content here](CRV2_360Review "wikilink")

### Can static code analyzers do it all?

1.  Author - Ashish Rao
2.  New Section
3.  [Put content here](CRV2_CanStaticAnalyzersDoAll "wikilink")

# Methodology

### The code review approach

1.  Author - Johanna Curiel
2.  [Put content here](CRV2_CodeReviewApproach "wikilink")

#### Preparation and context

1.  Author - Gary David Robinson
2.  Previous version to be updated:
    [3](https://www.owasp.org/index.php/Code_Review_Preparation)
3.  [Put content here](CRV2_PrepContext "wikilink")

#### Application Threat Modeling

1.  Author - Larry Conklin
2.  Previous version to be updated:
    [4](https://www.owasp.org/OCRG1.1:Application_Threat_Modeling)
3.  [Put content here](CRV2_AppThreatModeling "wikilink")

#### Understanding Code layout/Design/Architecture

1.  Author - Open
2.  [Put content here](CRV2_CodeLayoutDesignArch "wikilink")

#### Understanding Business Logic

1.  [Put content here](CRV2_BusinessLogic "wikilink")

### SDLC Integration

1.  Author - Larry Conklin
2.  Previous version to be updated:
    [5](https://www.owasp.org/index.php/Security_Code_Review_in_the_SDLC)
3.  [Put content here](CRV2_SDLCInt "wikilink")

#### Deployment Models

##### Secure deployment configurations

1.  Author -
2.  [Put content here](CRV2_SecDepConfig "wikilink")

<!-- end list -->

1.  New Section

##### Metrics and code review

1.  Author -Anthony.Scotka@tea.state.tx.us
2.  Previous version to be updated:
    [6](https://www.owasp.org/index.php/Code_Review_Metrics)
3.  [Put content here](CRV2_MetricsCodeRev "wikilink")

##### Source and sink reviews

1.  Author - Open
2.  New Section
3.  [Put content here](CRV2_SourceSinkRev "wikilink")

##### Code review Coverage

1.  Author - Open
2.  Previous version to be updated:
    [7](https://www.owasp.org/index.php/Code_Review_Coverage)
3.  [Put content here](CRV2_CodeRevCoverage "wikilink")

##### Design Reviews

1.  Author - Ashish Rao

<!-- end list -->

  - Why to review design?
      - Building security in design - secure by design principle
      - Design Areas to be reviewed
      - Common Design Flaws

<!-- end list -->

1.  [Put content here](CRV2_DesignRev "wikilink")

##### A Risk based approach to code review

1.  Author - Gary David Robinson
2.  New Section

<!-- end list -->

  - "Doing things right or doing the right things..."
      - "Not all bugs are equal

<!-- end list -->

1.  [Put content here](CRV2_RiskBasedApproach "wikilink")

#### Crawling code

1.  Author - Open
2.  Previous version to be updated:
    [8](https://www.owasp.org/index.php/Crawling_Code)

<!-- end list -->

  - API of Interest:
      - Java
      - .NET
      - PHP
      - RUBY
  - Frameworks:
      - Spring
      - .NET MVC
      - Struts
      - Zend

<!-- end list -->

1.  New Section

<!-- end list -->

  - Searching for code in C/C++

<!-- end list -->

1.  Author - Gary David Robinson

<!-- end list -->

1.  [Put content here](CRV2_CrawlingCode "wikilink")

#### Code reviews and Compliance

1.  Author -Open
2.  Previous version to be updated:
    [9](https://www.owasp.org/index.php/Code_Reviews_and_Compliance)
3.  [Put content here](CRV2_CodeRevCompliance "wikilink")

# Reviewing by Technical Control

### Reviewing code for Authentication controls

1.  Author - Gary Robinson
2.  [Put content here](CRV2_AuthControls "wikilink")

#### Forgot password

1.  Author Abbas Naderi, Larry Conklin
2.  [Put content here](CRV2_ForgotPassword "wikilink")

#### CAPTCHA

1.  Author Larry Conklin, Joan Renchie

**[Content here](CRV2_CAPTCHA "wikilink")**

#### Out of Band considerations

1.  Author - Gary Robinson
2.  Previous version to be updated:
    [10](https://www.owasp.org/index.php/Codereview-Authentication)
3.  [Put content here](CRV2_OutofBand "wikilink")

### Reviewing code Authorization weakness

1.  Author Eoin Keary .NET MVC added
2.  [Put content here](CRV2_AuthorizationWeaknesses "wikilink")

#### Checking authz upon every request

1.  Author - Abbas Naderi
2.  [Put content here](CRV2_CheckAuthzEachRequest "wikilink")

#### Reducing the attack surface

1.  Author Gary Robinson
2.  Previous version to be updated:
    [11](https://www.owasp.org/index.php/Codereview-Authorization)
3.  [Put content here](CRV2_ReducingAttSurf "wikilink")

#### SSL/TLS Implementations

1.  Author - Eoin Keary
2.  [Put content here](CRV2_SSL-TLS "wikilink")

#### Reviewing code for Session handling

1.  Author - Abbas Naderi
2.  Previous version to be updated:
    [12](https://www.owasp.org/index.php/Codereview-Session-Management)
3.  [Put content here](CRV2_SessionHandling "wikilink")

#### Reviewing client side code

1.  New Section
2.  [Put content here](CRV2_ClientSideCodeIntro "wikilink")

##### Javascript

1.  Author - Abbas Naderi
2.  [Put content here](CRV2_ClientSideCodeJScript "wikilink")

##### JSON

1.  Author - Open
2.  [Put content here](CRV2_ClientSideCodeJSon "wikilink")

##### Content Security Policy

1.  Author - Open
2.  [Put content here](CRV2_ClientSideCodeContSecPolicy "wikilink")

##### "Jacking"/Framing

1.  Author - Eoin Keary
2.  [Put content here](CRV2_ClientSideCodeJackingFraming "wikilink")

##### HTML 5?

1.  Author - Open
2.  [Put content here](CRV2_ClientSideCodeHTML5 "wikilink")

##### Browser Defenses

1.  Author - Open
2.  [Put content here](CRV2_ClientSideCodeBrowserDefPol "wikilink")

##### etc...

#### Review code for input validation

1.  Author - Open
2.  [Put content here](CRV2_InputValIntro "wikilink")

##### Regex Gotchas

1.  Author - Open
2.  New Section
3.  [Put content here](CRV2_InputValRegexGotchas "wikilink")

##### ESAPI

1.  Author - Open
2.  New Section
3.  Internal Link:
    [13](https://www.owasp.org/index.php/Codereview-Input_Validation)
4.  [Put content here](CRV2_InputValESAPI "wikilink")

##### Microsoft Web Protection Library

1.  Author - Michael Hidalgo
2.  New Section
3.  Internal Link:
    [14](https://www.owasp.org/index.php/Codereview-Input_Validation)
4.  [Put content
    here](CRV2_InputValMicrosoftWebProtectionLibrary "wikilink")

#### Reviewing code for contextual encoding

[Overall approach to content encoding and anti
XSS](Overall_approach_to_content_encoding_and_anti_XSS "wikilink")

##### HTML Attribute

1.  Author - Eoin Keary
2.  [Put content here](CRV2_ContextEncHTMLAttribute "wikilink")

##### HTML Entity

1.  Author - Eoin Keary
2.  [Put content here](CRV2_ContextEncHTMLEntity "wikilink")

##### Javascript Parameters

1.  Author - Eoin Keary
2.  [Put content here](CRV2_ContextEncJscriptParams "wikilink")

##### JQuery

1.  Author - Open
2.  [Put content here](CRV2_ContextEncJQuery "wikilink")

#### Reviewing file and resource handling code

1.  Author - Open
2.  [Put content here](CRV2_FileResourceHandling "wikilink")

#### Resource Exhaustion - error handling

1.  Author - Open
2.  [Put content here](CRV2_ResourceExhaustionErrHandling "wikilink")

##### native calls

1.  Author Open
2.  [Put content here](CRV2_ResourceExhaustionNativeCalls "wikilink")

#### Reviewing Logging code - Detective Security

1.  Author - Gary Robinson

<!-- end list -->

  - Where to Log
  - What to log
  - What not to log
  - How to log

<!-- end list -->

1.  Internal link:
    [15](https://www.owasp.org/index.php/Logging_Cheat_Sheet)
2.  [Put content here](CRV2_LoggingCode "wikilink")

#### Reviewing Error handling and Error messages

1.  Author - Gary David Robinson
2.  Previous version to be updated:
    [16](https://www.owasp.org/index.php/Codereview-Error-Handling)
3.  [Put content here](CRV2_ErrorHandlingMessages "wikilink")

#### Reviewing Security alerts

1.  Author - Gary Robinson
2.  [Put content here](CRV2_SecurityAlerts "wikilink")

#### Review for active defense

1.  Author - Colin Watson
2.  [Put content here](CRV2_ActiveDefense "wikilink")

#### Reviewing Secure Storage

1.  Author - Open source
2.  New Section
3.  [Put content here](CRV2_SecureStorage "wikilink")

#### Hashing & Salting - When, How and Where

##### Encryption

###### .NET

1.  Author Larry Conklin, Joan Renchie
2.  Previous version to be updated:
    [17](https://www.owasp.org/index.php/Codereview-Cryptographic_Controls)

<!-- end list -->

  - *Can we talk about key storage as well i.e. key management for
    encryption techniques used in the application? - Ashish Rao*

**[Content here](CRV2_HashingandSaltingdotNet "wikilink")**

# Reviewing by Vulnerability

### Review Code for XSS

1.  Author Examples added by Eoin Keary
2.  Previous version to be updated:
    [18](https://www.owasp.org/index.php/Reviewing_Code_for_Cross-Site_Scripting)
3.  In reviewing code for XSS - we can give more patterns on "source to
    sink" patterns for ASP.NET wrf to difference versions and mechanisms
    to display data in a page - Ashish Rao
4.  [Put content here](CRV2_RevCodeXSS "wikilink")

### Persistent - The Anti pattern

1.  Author
2.  [Put content
    here](CRV2_RevCodePersistentAntiPatternIntro "wikilink")

#### .NET

1.  Author Johanna Curiel, Eoin Keary
2.  [Put content
    here](CRV2_RevCodePersistentAntiPatterndotNet "wikilink")

#### .Java

1.  Author Johanna Curiel
2.  [Put content here](CRV2_RevCodePersistentAntiPatternJava "wikilink")

#### PHP

1.  Author Abbas Naderi
2.  [Put content here](CRV2_RevCodePersistentAntiPatternPHP "wikilink")

#### Ruby

1.  Author Open
2.  [Put content here](CRV2_RevCodePersistentAntiPatternRuby "wikilink")

### Reflected - The Anti pattern

1.  [Put content here](CRV2_RevCodeReflectedAntiPatternIntro "wikilink")

#### .NET

1.  Author Johanna Curiel
2.  [Put content
    here](CRV2_RevCodeReflectedAntiPatterndotNet "wikilink")

#### .Java

1.  Author Johanna Curiel
2.  [Put content here](CRV2_RevCodeReflectedAntiPatternJava "wikilink")

#### PHP

1.  Author Abbas Naderi
2.  [Put content here](CRV2_RevCodeReflectedAntiPatternPHP "wikilink")

#### Ruby

1.  Author - Open
2.  [Put content here](CRV2_RevCodeReflectedAntiPatternIRuby "wikilink")

### Stored - The Anti pattern

1.  Author - Johanna Curiel
2.  [Put content here](CRV2_RevCodeStoredAntiPatternIntro "wikilink")

#### .NET

1.  Author Johanna Curiel
2.  [Put content here](CRV2_RevCodeStoredAntiPatterndotNET "wikilink")

#### .Java

1.  Author Johanna Curiel
2.  [Put content here](CRV2_RevCodeStoredAntiPatternJava "wikilink")

#### PHP

1.  Author Johanna Curiel
2.  [Put content here](CRV2_RevCodeStoredAntiPatternPHP "wikilink")

#### Ruby

1.  Author - Johanna Curiel
2.  [Put content here](CRV2_RevCodeStoredAntiPatternRuby "wikilink")

### DOM XSS

1.  Author Larry Conklin
2.  [Put content here](CRV2_DOMXSS "wikilink")

### JQuery mistakes

1.  Author
2.  [Put content here](CRV2_JQueryMistakes "wikilink")

### Reviewing code for SQL Injection

1.  Author Gary Robinson
2.  Previous version to be updated:
    [19](https://www.owasp.org/index.php/Reviewing_Code_for_SQL_Injection)
3.  [Put content here](CRV2_RevCodeSQLInjection "wikilink")

#### PHP

1.  Author - Mennouchi Islam Azeddine
2.  [Put content here](CRV2_SQLInjPHP "wikilink")

#### Java

1.  Author - Johanna Curiel
2.  [Put content here](CRV2_SQLInjJava "wikilink")

#### .NET

1.  Author - Open
2.  [Put content here](CRV2_SQLInjdotNET "wikilink")

#### HQL

1.  Author - Open
2.  [Put content here](CRV2_SQLInjHQL "wikilink")

### The Anti pattern

1.  Author Larry Conklin
2.  [Content here](CRV2_AntiPattern "wikilink")

<https://www.owasp.org/index.php/CRV2_AntiPattern>

#### PHP

1.  Author -
2.  [Put content here](CRV2_AntiPatternPHP "wikilink")

#### Java

1.  Author -
2.  \=\> Searching for traditional SQL,JPA,JPSQL,Criteria,...
3.  [Put content here](CRV2_AntiPatternJava "wikilink")

#### .NET

1.  Author Open
2.  [Put content here](CRV2_AntiPatterndotNet "wikilink")

#### Ruby

1.  Author - Open
2.  [Put content here](CRV2_AntiPatternRuby "wikilink")

#### Cold Fusion

1.  Author - Open
2.  [Put content here](CRV2_AntiPatternColdFusion "wikilink")

### Reviewing code for CSRF Issues

1.  Author Abbas Naderi
2.  Previous version to be updated:
    [20](https://www.owasp.org/index.php/Reviewing_Code_for_Cross-Site_Request_Forgery)
3.  This page needs to be deleted. [Put content
    here](CRV2_CSRFIssues "wikilink")

### (This task has been deleted) Transactional logic / Non idempotent functions / State Changing Functions

1.  [Put content here](CRV2_TransLogic "wikilink")

### Reviewing code for poor logic /Business logic/Complex authorization

1.  Author - Open
2.  [Put content here](CRV2_PoorLogic "wikilink")

### Reviewing Secure Communications

#### .NET Config

1.  Author Johanna Curiel, Renchie Joan
2.  [Put content here](CRV2_SecCommsdotNet "wikilink")

#### Spring Config

1.  Author - Open
2.  [Put content here](CRV2_SecCommsSpringConfig "wikilink")

#### HTTP Headers

1.  Author Gary Robinson
2.  [Put content here](CRV2_SecCommsHTTPHdrs "wikilink")

### Tech-Stack pitfalls

1.  Author Open
2.  [Put content here](CRV2_TechStackPitfalls "wikilink")

### Framework specific Issues

#### Spring

1.  Author - Open
2.  [Put content here](CRV2_FrameworkSpecIssuesSpring "wikilink")

#### Struts

1.  Author - Open
2.  [Put content here](CRV2_FrameworkSpecIssuesStruts "wikilink")

#### Drupal

1.  Author Open
2.  [Put content here](CRV2_FrameworkSpecIssuesDrupal "wikilink")

#### Ruby on Rails

1.  Author - Open
2.  [Put content here](CRV2_FrameworkSpecIssuesROR "wikilink")

#### Django

1.  Author Open
2.  [Put content here](CRV2_FrameworkSpecIssuesDjango "wikilink")

#### .NET Security / MVC

1.  Author Johanna Curiel, Eoin Keary
2.  [Put content here](CRV2_FrameworkSpecIssuesdotNetMVC "wikilink")

#### Security in ASP.NET applications

1.  Author Johanna Curiel
2.  [Put content here](CRV2_FrameworkSpecIssuesASPNet "wikilink")

##### Strongly Named Assemblies

1.  Author Johanna Curiel, Larry Conklin
2.  [Put content
    here](CRV2_FrameworkSpecIssuesASPNetStrongAssembiles "wikilink")

###### Round Tripping

1.  Author - Open
2.  [Put content here](CRV2_FrameworkSpecIssuesASPNetRT "wikilink")

###### How to prevent Round tripping

1.  Author - Open
2.  Author Johanna Curiel
3.  [Put content
    here](CRV2_FrameworkSpecIssuesASPNetRTPrevention "wikilink")

##### Setting the right Configurations

1.  Author Johanna Curiel
2.  [Put content here](CRV2_FrameworkSpecIssuesASPNetConfigs "wikilink")

##### Authentication Options

1.  Author Johanna Curiel
2.  [Put content here](CRV2_FrameworkSpecIssuesASPNetAuth "wikilink")

##### Code Review for Managed Code - .Net 1.0 and up

1.  Author Johanna Curiel
2.  [Put content
    here](CRV2_FrameworkSpecIssuesASPNetManagedCode "wikilink")

##### Using OWASP Top 10 as your guideline

1.  Author Johanna Curiel
2.  [Put content here](CRV2_FrameworkSpecIssuesASPTop10 "wikilink")

##### Code review for Unsafe Code (C\#)

1.  Author Johanna Curiel
2.  [Put content
    here](CRV2_FrameworkSpecIssuesASPNetUnsafeCode "wikilink")

#### PHP Specific Issues

1.  Author Open
2.  [Put content here](CRV2_FrameworkSpecIssuesPHP "wikilink")

#### Classic ASP

1.  Author Johanna Curiel
2.  [Put content here](CRV2_FrameworkSpecIssuesASPClassic "wikilink")

#### C\#

1.  Author Open
2.  [Put content here](CRV2_FrameworkSpecIssuesCsharp "wikilink")

#### C/C++

1.  Author Open
2.  [Put content here](CRV2_FrameworkSpecIssuesCplusplus "wikilink")

#### Objective C

1.  Author Open
2.  [Put content here](CRV2_FrameworkSpecIssuesObectiveC "wikilink")

#### Java

1.  Author Open
2.  [Put content here](CRV2_FrameworkSpecIssuesJava "wikilink")

#### Android

1.  Author Open
2.  [Put content here](CRV2_FrameworkSpecIssuesAndroid "wikilink")

#### Coldfusion

1.  Author Open
2.  [Put content here](CRV2_FrameworkSpecIssuesColdfusion "wikilink")

#### CodeIgniter

1.  Author Open
2.  [Put content here](CRV2_FrameworkSpecIssuesCodeIgniter "wikilink")

# Security code review for Agile development

1.  Author Carlos Pantelides
2.  [Put content here](CRV2_CodeReviewAgile "wikilink")

# Code Review for Backdoors

1.  Author Yiannis Pavlosoglou

The review of a piece of source code for backdoors has one excruciating
difference to a traditional source code review: The fact that someone
with 'commit' or 'write' access to the source code repository has
malicious intentions spanning well beyond their current developer remit.
Because of this difference, a code review for backdoors is often seen as
a very specialised review and can sometimes be considered not a code
review per say.

A traditional code review has the objective of determining if a
vulnerability is present within the code, further to this if the
vulnerability is exploitable and under what conditions. A code review
for backdoors has the objective to determine if a certain portion of the
codebase is carrying code that is unnecessary for the logic and
implementation of the use cases it serves.

Further to this, the reviewer, looks for the trigger points of that
logic. Typical examples include a branch statement going off to a part
of assembly or obfuscated code. The reviewer is looking for patterns of
abnormality in terms of code segments that would not be expected to be
present under normal conditions.

An excellent introduction into how to look for rootkits in the Java
programming language can be found
[here](https://www.blackhat.com/presentations/bh-usa-09/WILLIAMS/BHUSA09-Williams-EnterpriseJavaRootkits-PAPER.pdf).
In this paper J. Williams covers a variety of backdoor examples
including file system access through a web server, as well as time based
attacks involving a key aspect of malicious functionality been made
available after a certain amount of time. Such examples form the
foundation of what any reviewer for back doors should try to automate,
regardless of the language in which the review is taking place.

# Code Review Tools

<https://www.owasp.org/index.php/CRV2_CodeReviewTools>