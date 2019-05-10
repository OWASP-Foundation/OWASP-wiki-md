__NOTOC__

This is the table of content of the New Testing Guide v3.
You can download the stable version
[here](http://www.owasp.org/images/5/56/OWASP_Testing_Guide_v3.pdf)
Back to the OWASP Testing Guide Project:
<http://www.owasp.org/index.php/OWASP_Testing_Project>

Updated: 2nd November 2008

**T A B L E o f C O N T E N T S**

-----

## [Foreword by Eoin Keary - Global Board](Testing_Guide_Foreword "wikilink")

## [1. Frontispiece](Testing_Guide_Frontispiece "wikilink")

**[1.1 About the OWASP Testing Guide
Project](Testing_Guide_Frontispiece "wikilink")**

**[1.2 About The Open Web Application Security
Project](About_The_Open_Web_Application_Security_Project "wikilink")**

## [2. Introduction](Testing_Guide_Introduction "wikilink")

**2.1 The OWASP Testing Project**

**2.2 Principles of Testing**

**2.3 Testing Techniques Explained**

2.4 [Security requirements test
derivation](https://www.owasp.org/index.php/Testing_Guide_Introduction#Security_Requirements_Test_Derivation),[functional
and non functional test
requirements](https://www.owasp.org/index.php/Testing_Guide_Introduction#Functional_and_Non_Functional_Test_Requirements),
and [test cases through use and misuse
cases](https://www.owasp.org/index.php/Testing_Guide_Introduction#Test_Cases_Through_Use_and_Misuse_Cases)

2.4.1 [Security tests integrated in developers and testers
workflows](https://www.owasp.org/index.php/Testing_Guide_Introduction#Security_Tests_Integrated_in_Developers_and_Testers_Workflow)

2.4.2 [Developers' security tests: unit tests and component level
tests](https://www.owasp.org/index.php/Testing_Guide_Introduction#Developers.27_Security_Tests)

2.4.3 [Functional testers' security tests: integrated system tests,
tests in UAT, and production
environment](https://www.owasp.org/index.php/Testing_Guide_Introduction#Functional_Testers.27_Security_Tests)

2.5 [Security test data analysis and reporting: root cause
identification and business/role case test data
reporting](https://www.owasp.org/index.php/Testing_Guide_Introduction#Security_Test_Data_Analysis_and_Reporting)

## [3. The OWASP Testing Framework](The_OWASP_Testing_Framework "wikilink")

**3.1. Overview**

'''3.2. Phase 1: Before Development Begins '''

**3.3. Phase 2: During Definition and Design**

**3.4. Phase 3: During Development**

**3.5. Phase 4: During Deployment**

**3.6. Phase 5: Maintenance and Operations**

'''3.7. A Typical SDLC Testing Workflow '''

## [4. Web Application Penetration Testing](Web_Application_Penetration_Testing "wikilink")

[**4.1 Introduction and
Objectives**](Testing:_Introduction_and_objectives "wikilink")

[4.1.1 Testing Checklist](Testing_Checklist "wikilink")

[**4.2 Information
Gathering**](Testing:_Information_Gathering "wikilink")

[4.2.1 Spiders, Robots and Crawlers
(OWASP-IG-001)](Testing:_Spiders,_Robots,_and_Crawlers_\(OWASP-IG-001\) "wikilink")

[4.2.2 Search Engine Discovery/Reconnaissance
(OWASP-IG-002)](Testing:_Search_engine_discovery/reconnaissance_\(OWASP-IG-002\) "wikilink")

[4.2.3 Identify application entry points
(OWASP-IG-003)](Testing:_Identify_application_entry_points_\(OWASP-IG-003\) "wikilink")

[4.2.4 Testing for Web Application Fingerprint
(OWASP-IG-004)](Testing_for_Web_Application_Fingerprint_\(OWASP-IG-004\) "wikilink")

[4.2.5 Application Discovery
(OWASP-IG-005)](Testing_for_Application_Discovery_\(OWASP-IG-005\) "wikilink")

[4.2.6 Analysis of Error Codes
(OWASP-IG-006)](Testing_for_Error_Code_\(OWASP-IG-006\) "wikilink")

[**4.3 Configuration Management
Testing**](Testing_for_configuration_management "wikilink")

[4.3.1 SSL/TLS Testing (SSL Version, Algorithms, Key length, Digital
Cert. Validity)
(OWASP-CM-001)](Testing_for_SSL-TLS_\(OWASP-CM-001\) "wikilink")
[4.3.2 DB Listener Testing
(OWASP-CM-002)](Testing_for_DB_Listener_\(OWASP-CM-002\) "wikilink")

[4.3.3 Infrastructure Configuration Management Testing
(OWASP-CM-003)](Testing_for_infrastructure_configuration_management_\(OWASP-CM-003\) "wikilink")

[4.3.4 Application Configuration Management Testing
(OWASP-CM-004)](Testing_for_application_configuration_management_\(OWASP-CM-004\) "wikilink")

[4.3.5 Testing for File Extensions Handling
(OWASP-CM-005)](Testing_for_file_extensions_handling_\(OWASP-CM-005\) "wikilink")

[4.3.6 Old, Backup and Unreferenced Files
(OWASP-CM-006)](Testing_for_Old,_Backup_and_Unreferenced_Files_\(OWASP-CM-006\) "wikilink")

[4.3.7 Infrastructure and Application Admin Interfaces
(OWASP-CM-007)](Testing_for_Admin_Interfaces_\(OWASP-CM-007\) "wikilink")

[4.3.8 Testing for HTTP Methods and Cross Site Tracing (XST)
(OWASP-CM-008)](Testing_for_HTTP_Methods_and_XST_\(OWASP-CM-008\) "wikilink")

[**4.4 Authentication Testing**](Testing_for_authentication "wikilink")

[4.4.1 Credentials transport over an encrypted channel
(OWASP-AT-001)](Testing_for_credentials_transport_\(OWASP-AT-001\) "wikilink")

[4.4.2 Testing for user enumeration
(OWASP-AT-002)](Testing_for_user_enumeration_\(OWASP-AT-002\) "wikilink")

[4.4.3 Testing for Guessable (Dictionary) User Account
(OWASP-AT-003)](Testing_for_Default_or_Guessable_User_Account_\(OWASP-AT-003\) "wikilink")

[4.4.4 Brute Force Testing
(OWASP-AT-004)](Testing_for_Brute_Force_\(OWASP-AT-004\) "wikilink")

[4.4.5 Testing for bypassing authentication schema
(OWASP-AT-005)](Testing_for_Bypassing_Authentication_Schema_\(OWASP-AT-005\) "wikilink")

[4.4.6 Testing for vulnerable remember password and pwd reset
(OWASP-AT-006)](Testing_for_Vulnerable_Remember_Password_and_Pwd_Reset_\(OWASP-AT-006\) "wikilink")

[4.4.7 Testing for Logout and Browser Cache Management
(OWASP-AT-007)](Testing_for_Logout_and_Browser_Cache_Management_\(OWASP-AT-007\) "wikilink")

[4.4.8 Testing for CAPTCHA
(OWASP-AT-008)](Testing_for_Captcha_\(OWASP-AT-008\) "wikilink")

[4.4.9 Testing Multiple Factors Authentication
(OWASP-AT-009)](Testing_Multiple_Factors_Authentication_\(OWASP-AT-009\) "wikilink")

[4.4.10 Testing for Race Conditions
(OWASP-AT-010)](Testing_for_Race_Conditions_\(OWASP-AT-010\) "wikilink")

[**4.5 Session Management
Testing**](Testing_for_Session_Management "wikilink")

[4.5.1 Testing for Session Management Schema
(OWASP-SM-001)](Testing_for_Session_Management_Schema_\(OWASP-SM-001\) "wikilink")

[4.5.2 Testing for Cookies attributes
(OWASP-SM-002)](Testing_for_cookies_attributes_\(OWASP-SM-002\) "wikilink")

[4.5.3 Testing for Session Fixation
(OWASP-SM-003)](Testing_for_Session_Fixation_\(OWASP-SM-003\) "wikilink")

[4.5.4 Testing for Exposed Session Variables
(OWASP-SM-004)](Testing_for_Exposed_Session_Variables_\(OWASP-SM-004\) "wikilink")

[4.5.5 Testing for Cross Site Request Forgery (CSRF)
(OWASP-SM-005)](Testing_for_CSRF_\(OWASP-SM-005\) "wikilink")

[**4.6 Authorization Testing**](Testing_for_Authorization "wikilink")

[4.6.1 Testing for path traversal
(OWASP-AZ-001)](Testing_for_Path_Traversal_\(OWASP-AZ-001\) "wikilink")

[4.6.2 Testing for bypassing authorization schema
(OWASP-AZ-002)](Testing_for_Bypassing_Authorization_Schema_\(OWASP-AZ-002\) "wikilink")

[4.6.3 Testing for Privilege Escalation
(OWASP-AZ-003)](Testing_for_Privilege_escalation_\(OWASP-AZ-003\) "wikilink")

[**4.7 Business Logic Testing
(OWASP-BL-001)**](Testing_for_business_logic_\(OWASP-BL-001\) "wikilink")

[**4.8 Data Validation
Testing**](Testing_for_Data_Validation "wikilink")

[4.8.1 Testing for Reflected Cross Site Scripting
(OWASP-DV-001)](Testing_for_Reflected_Cross_site_scripting_\(OWASP-DV-001\) "wikilink")

[4.8.2 Testing for Stored Cross Site Scripting
(OWASP-DV-002)](Testing_for_Stored_Cross_site_scripting_\(OWASP-DV-002\) "wikilink")

[4.8.3 Testing for DOM based Cross Site Scripting
(OWASP-DV-003)](Testing_for_DOM-based_Cross_site_scripting_\(OWASP-DV-003\) "wikilink")

[4.8.4 Testing for Cross Site Flashing
(OWASP-DV-004)](Testing_for_Cross_site_flashing_\(OWASP-DV-004\) "wikilink")

[4.8.5 Testing for SQL Injection
(OWASP-DV-005)](Testing_for_SQL_Injection_\(OWASP-DV-005\) "wikilink")

[4.8.5.1 Oracle Testing](Testing_for_Oracle "wikilink")

[4.8.5.2 MySQL Testing](Testing_for_MySQL "wikilink")

[4.8.5.3 SQL Server Testing](Testing_for_SQL_Server "wikilink")

[4.8.5.4 MS Access Testing](Testing_for_MS_Access "wikilink")

[4.8.5.5 Testing PostgreSQL (from OWASP
BSP)](OWASP_Backend_Security_Project_Testing_PostgreSQL "wikilink")

[4.8.6 Testing for LDAP Injection
(OWASP-DV-006)](Testing_for_LDAP_Injection_\(OWASP-DV-006\) "wikilink")

[4.8.7 Testing for ORM Injection
(OWASP-DV-007)](Testing_for_ORM_Injection_\(OWASP-DV-007\) "wikilink")

[4.8.8 Testing for XML Injection
(OWASP-DV-008)](Testing_for_XML_Injection_\(OWASP-DV-008\) "wikilink")

[4.8.9 Testing for SSI Injection
(OWASP-DV-009)](Testing_for_SSI_Injection_\(OWASP-DV-009\) "wikilink")

[4.8.10 Testing for XPath Injection
(OWASP-DV-010)](Testing_for_XPath_Injection_\(OWASP-DV-010\) "wikilink")

[4.8.11 IMAP/SMTP Injection
(OWASP-DV-011)](Testing_for_IMAP/SMTP_Injection_\(OWASP-DV-011\) "wikilink")

[4.8.12 Testing for Code Injection
(OWASP-DV-012)](Testing_for_Code_Injection_\(OWASP-DV-012\) "wikilink")

[4.8.13 Testing for Command Injection
(OWASP-DV-013)](Testing_for_Command_Injection_\(OWASP-DV-013\) "wikilink")

[4.8.14 Testing for Buffer overflow
(OWASP-DV-014)](Testing_for_Buffer_Overflow_\(OWASP-DV-014\) "wikilink")

[4.8.14.1 Testing for Heap
overflow](Testing_for_Heap_Overflow "wikilink")

[4.8.14.2 Testing for Stack
overflow](Testing_for_Stack_Overflow "wikilink")

[4.8.14.3 Testing for Format
string](Testing_for_Format_String "wikilink")

[4.8.15 Testing for incubated vulnerabilities
(OWASP-DV-015)](Testing_for_Incubated_Vulnerability_\(OWASP-DV-015\) "wikilink")

[4.8.16 Testing for HTTP Splitting/Smuggling
(OWASP-DV-016)](Testing_for_HTTP_Splitting/Smuggling_\(OWASP-DV-016\) "wikilink")

[**4.9 Testing for Denial of
Service**](Testing_for_Denial_of_Service "wikilink")

[4.9.1 Testing for SQL Wildcard Attacks
(OWASP-DS-001)](Testing_for_SQL_Wildcard_Attacks_\(OWASP-DS-001\) "wikilink")

[4.9.2 Testing for DoS Locking Customer Accounts
(OWASP-DS-002)](Testing_for_DoS_Locking_Customer_Accounts_\(OWASP-DS-002\) "wikilink")

[4.9.3 Testing for DoS Buffer Overflows
(OWASP-DS-003)](Testing_for_DoS_Buffer_Overflows_\(OWASP-DS-003\) "wikilink")

[4.9.4 Testing for DoS User Specified Object Allocation
(OWASP-DS-004)](Testing_for_DoS_User_Specified_Object_Allocation_\(OWASP-DS-004\) "wikilink")

[4.9.5 Testing for User Input as a Loop Counter
(OWASP-DS-005)](Testing_for_User_Input_as_a_Loop_Counter_\(OWASP-DS-005\) "wikilink")

[4.9.6 Testing for Writing User Provided Data to Disk
(OWASP-DS-006)](Testing_for_Writing_User_Provided_Data_to_Disk_\(OWASP-DS-006\) "wikilink")

[4.9.7 Testing for DoS Failure to Release Resources
(OWASP-DS-007)](Testing_for_DoS_Failure_to_Release_Resources_\(OWASP-DS-007\) "wikilink")

[4.9.8 Testing for Storing too Much Data in Session
(OWASP-DS-008)](Testing_for_Storing_too_Much_Data_in_Session_\(OWASP-DS-008\) "wikilink")

[**4.10 Web Services Testing**](Testing_for_Web_Services "wikilink")

[4.10.1 WS Information Gathering
(OWASP-WS-001)](Testing:_WS_Information_Gathering_\(OWASP-WS-001\) "wikilink")

[4.10.2 Testing WSDL
(OWASP-WS-002)](Testing_WSDL_\(OWASP-WS-002\) "wikilink")

[4.10.3 XML Structural Testing
(OWASP-WS-003)](Testing_for_XML_Structural_\(OWASP-WS-003\) "wikilink")

[4.10.4 XML Content-level Testing
(OWASP-WS-004)](Testing_for_XML_Content-Level_\(OWASP-WS-004\) "wikilink")

[4.10.5 HTTP GET parameters/REST Testing
(OWASP-WS-005)](Testing_for_WS_HTTP_GET_parameters/REST_attacks_\(OWASP-WS-005\) "wikilink")

[4.10.6 Naughty SOAP attachments
(OWASP-WS-006)](Testing_for_Naughty_SOAP_Attachments_\(OWASP-WS-006\) "wikilink")

[4.10.7 Replay Testing
(OWASP-WS-007)](Testing_for_WS_Replay_\(OWASP-WS-007\) "wikilink")

[**4.11 AJAX Testing**](Testing_for_AJAX:_introduction "wikilink")

[4.11.1 AJAX Vulnerabilities
(OWASP-AJ-001)](Testing_for_AJAX_Vulnerabilities_\(OWASP-AJ-001\) "wikilink")

[4.11.2 How to test AJAX
(OWASP-AJ-002)](Testing_for_AJAX_\(OWASP-AJ-002\) "wikilink")

## [5. Writing Reports: value the real risk](Writing_Reports:_value_the_real_risk "wikilink")

[5.1 How to value the real risk](How_to_value_the_real_risk "wikilink")

[5.2 How to write the report of the
testing](How_to_write_the_report_of_the_testing "wikilink")

## [Appendix A: Testing Tools](Appendix_A:_Testing_Tools "wikilink")

  - Black Box Testing Tools
  - Source Code Analyzers
  - Other Tools

## [Appendix B: Suggested Reading](OWASP_Testing_Guide_Appendix_B:_Suggested_Reading "wikilink")

  - Whitepapers
  - Books
  - Useful Websites

## [Appendix C: Fuzz Vectors](OWASP_Testing_Guide_Appendix_C:_Fuzz_Vectors "wikilink")

  - Fuzz Categories
      - Recursive fuzzing
      - Replasive fuzzing
  - Cross Site Scripting (XSS)
  - Buffer Overflows and Format String Errors
      - Buffer Overflows (BFO)
      - Format String Errors (FSE)
      - Integer Overflows (INT)
  - SQL Injection
      - Passive SQL Injection (SQP)
      - Active SQL Injection (SQI)
  - LDAP Injection
  - XPATH Injection

## [Appendix D: Encoded Injection](OWASP_Testing_Guide_Appendix_D:_Encoded_Injection "wikilink")

-----

[Category:OWASP Testing
Project](Category:OWASP_Testing_Project "wikilink")