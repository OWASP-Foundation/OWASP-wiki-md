## Summary

Workflow vulnerabilities involve any type of vulnerability that allows
the attacker to misuse an application/system in a way that will allow
them to circumvent (not follow) the designed/intended workflow.

“A workflow consists of a sequence of connected steps where each step
follows without delay or gap and ends just before the subsequent step
may begin. It is a depiction of a sequence of operations, declared as
work of a person or group, an organization of staff, or one or more
simple or complex mechanisms. Workflow may be seen as any abstraction of
real work.” (https://en.wikipedia.org/wiki/Workflow)

The application’s business logic must require that the user complete
specific steps in the correct/specific order and if the workflow is
terminated without correctly completing, all actions and spawned actions
are “rolled back” or canceled. Vulnerabilities related to the
circumvention of workflows or bypassing the correct business logic
workflow are unique in that they are very application/system specific
and careful manual misuse cases must be developed using requirements and
use cases.

The applications business process must have checks to ensure that the
user's transactions/actions are proceeding in the correct/acceptable
order and if a transaction triggers some sort of action, that action
will be “rolled back” and removed if the transaction is not successfully
completed.

## Examples

Example 1

Many of us receive so type of “club/loyalty points” for purchases from
grocery stores and gas stations. Suppose a user was able to start a
transaction linked to their account and then after points have been
added to their club/loyalty account cancel out of the transaction or
remove items from their “basket” and tender. In this case the system
either should not apply points/credits to the account until it is
tendered or points/credits should be “rolled back” if the point/credit
increment does not match the final tender. With this in mind, an
attacker may start transactions and cancel them to build their point
levels without actually buy anything.

Example 2

An electronic bulletin board system may be designed to ensure that
initial posts do not contain profanity based on a list that the post is
compared against. If a word on a "black" the list is found in the user
entered text the submission is not posted. But, once a submission is
posted the submitter can access, edit, and change the submission
contents to include words included on the profanity/black list since on
edit the posting is never compared again. Keeping this in mind,
attackers may open an initial blank or minimal discussion then add in
whatever they like as an update.

## How to Test

Generic Testing Method

• Review the project documentation and use exploratory testing looking
for methods to skip or go to steps in the application process in a
different order from the designed/intended business logic flow.

• For each method develop a misuse case and try to circumvent or perform
an action that is "not acceptable" per the the business logic workflow.

Testing Method 1

• Start a transaction going through the application past the points that
triggers credits/points to the users account.

• Cancel out of the transaction or reduce the final tender so that the
point values should be decreased and check the points/ credit system to
ensure that the proper points/credits were recorded.

Testing Method 2

• On a content management or bulletin board system enter and save valid
initial text or values.

• Then try to append, edit and remove data that would leave the existing
data in an invalid state or with invalid values to ensure that the user
is not allowed to save the incorrect information. Some "invalid" data or
information may be specific words (profanity) or specific topics (such
as political issues).

## Related Test Cases

[Testing Directory traversal/file include
(OTG-AUTHZ-001)](Testing_Directory_traversal/file_include_\(OTG-AUTHZ-001\) "wikilink")

[Testing for bypassing authorization schema
(OTG-AUTHZ-002)](Testing_for_Bypassing_Authorization_Schema_\(OTG-AUTHZ-002\) "wikilink")

[Testing for Bypassing Session Management Schema
(OTG-SESS-001)](Testing_for_Session_Management_Schema_\(OTG-SESS-001\) "wikilink")

[Test Business Logic Data Validation
(OTG-BUSLOGIC-001)](Test_business_logic_data_validation_\(OTG-BUSLOGIC-001\) "wikilink")

[Test Ability to Forge Requests
(OTG-BUSLOGIC-002)](Test_Ability_to_forge_requests_\(OTG-BUSLOGIC-002\) "wikilink")

[Test Integrity Checks
(OTG-BUSLOGIC-003)](Test_integrity_checks_\(OTG-BUSLOGIC-003\) "wikilink")

[Test for Process Timing
(OTG-BUSLOGIC-004)](Test_for_Process_Timing_\(OTG-BUSLOGIC-004\) "wikilink")

[Test Number of Times a Function Can be Used Limits
(OTG-BUSLOGIC-005)](Test_number_of_times_a_function_can_be_used_limits_\(OTG-BUSLOGIC-005\) "wikilink")

[Test Defenses Against Application Mis-use
(OTG-BUSLOGIC-007)](Test_defenses_against_application_mis-use_\(OTG-BUSLOGIC-007\) "wikilink")

[Test Upload of Unexpected File Types
(OTG-BUSLOGIC-008)](Test_Upload_of_Unexpected_File_Types_\(OTG-BUSLOGIC-008\) "wikilink")

[Test Upload of Malicious Files
(OTG-BUSLOGIC-009)](Test_Upload_of_Malicious_Files_\(OTG-BUSLOGIC-009\) "wikilink")

## References

OWASP Detail Misuse Cases -
<https://www.owasp.org/index.php/Detail_misuse_cases>

Real-Life Example of a 'Business Logic Defect -
<http://h30501.www3.hp.com/t5/Following-the-White-Rabbit-A/Real-Life-Example-of-a-Business-Logic-Defect-Screen-Shots/ba-p/22581>

Top 10 Business Logic Attack Vectors Attacking and Exploiting Business
Application Assets and Flaws – Vulnerability Detection to Fix -
<http://www.ntobjectives.com/go/business-logic-attack-vectors-white-paper/>
and <http://www.ntobjectives.com/files/Business_Logic_White_Paper.pdf>

CWE-840: Business Logic Errors -
<http://cwe.mitre.org/data/definitions/840.html>

## Remediation

The application must be self-aware and have checks in place ensuring
that the users complete each step in the work flow process in the
correct order and prevent attackers from circumventing/skipping/or
repeating any steps/processes in the workflow. Test for workflow
vulnerabilities involves developing business logic abuse/misuse cases
with the goal of successfully completing the business process while not
completing the correct steps in the correct order.