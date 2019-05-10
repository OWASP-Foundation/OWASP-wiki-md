**OWASP Testing Guide v3 Roadmap**

-----

  - **26th April 2008: start the new project**

OWASP Leaders brainstorming.
Call for participation.
[Index
brainstorming](http://www.owasp.org/index.php/OWASP_Testing_Guide_v3_Startup)
[Index
draft](http://www.owasp.org/index.php/OWASP_Testing_Guide_v3_Table_of_Contents)
Discuss th article content.
Deadline: Sun 18th May 2008.

  - **20th May 2008**

New draft Index

  - **25th May 2008**

**Updated index:** Added or to improve:

(toimp)1. Frontispiece

(toimp)1.1 About the OWASP Testing Guide Project

(new) 2.4 Security requirements test derivation, functional and non
functional test requirements, and test cases through use and misuse
cases

(new) 2.4.1 Security tests integrated in developers and testers
workflows

(new) 2.4.2 Developers' security tests: Unit Tests, component level
tests, etc

(new) 2.4.3 Functional testers' security tests: integrated system tests,
tests in UAT, and production environment

(new) 2.5 Security test data analysis and reporting: root cause
identification and business/role case test data reporting

4\. (toimp) Web Application Penetration Testing

4.1 Introduction and Objectives

(new) 4.1.1 Testing Checklist

(toimp) 4.2 Information Gathering

(new)4.2.1 Spiders, Robots and Crawlers

(new) 4.2.2 Search Engine Discovery/Reconnaissance

(new) 4.2.3 Identify application entry points

4.2.3 (toimp) Testing for Web Application Fingerprint

(toimp)4.2.5 Analysis of Error Codes

(new) 4.3 Configuration Management Testing

(toimp) 4.3.1 SSL/TLS Testing (SSL Version, Alghoritms, Key lenght,
Digital Cert. Validity

(toimp) 4.3.3 Application Configuration Management Testing

(new) 4.3.4 Testing for misconfiguration

(new) 4.3.7 Infrastructure and Application Admin Interfaces

(toimp)4.4 Business Logic Testing

(toimp)4.5 Authentication Testing

(new)4.5.1 Credentials transport over an encrypted channel

(new) 4.5.2 Testing for user enumeration

(to imp) 4.5.2 Testing for Guessable (Dictionary) User Account

(new) 4.6 Authorization testing

(new) 4.6.1 Testing for Path Traversal

(new)4.6.2 Testing for bypassing authorization schema

(new)4.6.3 Testing for Privilege Escalation

(new)4.7.2 Test the token strength (old 4.5.2 Testing for Cookie and
Session Token Manipulation)

(new) 4.7.3 Testing for Cookies attributes

(new)4.8.1 Testing for Reflected Cross Site Scripting

(new)4.8.2 Testing for Stored Cross Site Scripting

(new) 4.8.3 Testing for DOM based Cross Site Scripting

(new)4.8.4 Testing for Cross Site Flashing

(toimp) 4.8.1.1 Testing for XST

(toimp) 4.8.2 Testing for SQL Injection

(toimp) 4.10 Web Services Testing

(new)4.11 Client site testing

(new) 4.11.1 AJAX Testing

(new)4.11.2 Flash Testing

(new)4.11.3 RIA Testing

(toimp: Mat)5. Writing Reports: value the real risk

  - **26th May 2008**

Added:
4.3.8 Testing for HTTP Methods and XST in Infrastucture and Application
Testing section
Sent Paragraph Template to the list
Sent new index to the list

  - **28th May 2008**

Added: New Testing Guide checklist.

  - **30th May 2008**

Added:
Session Fixation
Discuss abouut new Aspect paper about HTTP verb manipulation

-----

  - **1st June 2008**

Les's start writing\!

  - **15th June 2008**

Added: 4.1.1 Testing Checklist
4.2 Information Gathering
4.2.1 Spiders, Robots and Crawlers
4.2.3 Identify application entry points
2.4 Security requirements test derivation,functional and non functional
test requirements, and test cases through use and misuse cases
4.4 Business Logic Testing
4.6 Authorization testing
4.5.3 Testing for Guessable (Dictionary) User Account
4.6 Authorization testing
4.6.2 Testing for Bypassing Authorization Schema
4.6.3 Testing for Privilege Escalation

  - **29th June 2008**

Written (M.Meucci): Testing_for_user_enumeration

-----

  - **7th July 2008**

Written: Testing_for_Default_or_Guessable_User_Account
(K.Horvath)
Testing_for_business_logic (K.Horvath)

  - **9th July 2008**

Testing_for_cookies_attributes (K.Horvath)

  - **12th August 2008**

Articles reviewed/written (M.Meucci):
Testing:_Introduction_and_objectives
Testing_Checklist
4.3 Configuration Management Testing
4.2 Information Gathering

  - **13 August 2008**

Reviewed (M.Meucci):
Testing_for_business_logic Testing_for_SQL_Wildcard_Attacks
(Rick.mitchell)
Added:
(new: G.Fedon) 4.5.9 Testing Multiple Factors Authentication
Written (M.Meucci):
Testing_for_authentication

  - **14 August 2008**

Reviewed (M.Meucci): Testing_for_credentials_transport
Written (M.Meucci):
Testing_for_user_enumeration (M.Mella)
Testing_for_authorization
Testing_for_Session_Management
merged the 2 articles:
Testing for Session_Management_Schema
Testing for Cookie and Session Token Manipulation
Now we have a new one: Testing for Session_Management_Schema

  - **15 August 2008**

Testing_for_Session_Fixation

  - **16th August 2008**

Reviewed (M.Cova):
4.2 Information Gathering
4.3 Configuration Management Testing
4.5 Authentication Testing

  - **18th August 2008**

Reviewed (M.Cova):
4.6 Authorization testing
Written (A.van der Stock):
Testing_for_HTTP_Methods_and_XST (HTTP Verb)

  - **20th August 2008**

Reviewed (M.Cova):
Web Services
Written (A.Parata):
4.8.5.4 MS Access Testing

  - **21st August 2008**

Updated (M.Meucci):
Testing_for_Session_Fixation
Testing_for_Bypassing_Authorization_Schema
Testing_for_Privilege_escalation

  - **22nd August 2008**

Writing (Adam): Testing_for_Admin_Interfaces
Update/Write:
(imp: M.Meucci -100%) 4.10 Web Services Testing
(new: M.Meucci -100%) 4.10.1 WS Information Gathering
(new: M.Meucci -100%) 4.10.2 Testing WSDL
(imp: M.Meucci -100%)4.10.3 XML Structural Testing
Improved:
Testing_for_Data_Validation

  - **23rd August 2008**

Deleted:
Client Side Testing (we have not time to finish this section: we can
focus on DOM XSS and Cross Site Flashing articles)
Added:
AJAX Testing
Updated:
(new: M.Meucci) 4.1.1 Testing Checklist

  - **24th August 2008**

Added:
Testing_for_Race_Conditions (A.Goodman) - Mat: to understand if this
article is suitable in Authentication Testing section.
Review (M.Cova):
Data Validation Section
Review: MS Access Testing

  - **25th August 2008**

Reviewed (C.Heinrich):
4.2.1 Spiders, Robots and Crawlers
4.2.2 Search Engine Discovery/Reconnaissance
Written (G.Fedon):
Testing_Multiple_Factors_Authentication

  - **26th August 2008**

Completed (G.Fedon):
Testing_Multiple_Factors_Authentication

-----

  - **27th August 2008**

Started the reviewing phase:
<http://www.owasp.org/index.php/OWASP_Testing_Project_v3_Review_Roadmap>
Updated (Harish):
OWASP_Testing_Guide_Appendix_D:_Encoded_Injection

-----

  - **7th September 2008**

Written:
(S.Di Paola)4.8.4 Testing for Cross Site Flashing

Reviewed:
MS Access Testing
Testing PostgreSQL
Testing for Race Conditions
Infrastructure and Application Admin Interfaces

-----

  - *' October 2008*'

Review all the Guide

-----

  - *' 6h November 2008*'

Published the Guide\!

-----

**Project deadlines:**

1.  21st May: Project status presentation at the OWASP AppSec Euro 08
    Conference in Belgium.
2.  15th June - Participants to report on project status.
3.  24th August - Finish the writing phase.
4.  6th November 2008 - Project completion. Participants should deliver
    final project report.