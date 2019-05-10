## Summary

It is common in modern enterprises to define system roles to manage
users and authorization to system resources. In most system
implementations it is expected that at least two roles exist,
administrators and regular users. The first representing a role that
permits access to privileged and sensitive functionality and
information, the second representing a role that permits access to
regular business functionality and information. Well developed roles
should align with business processes which are supported by the
application.

It is important to remember that cold, hard authorization isn't the only
way to manage access to system objects. In more trusted environments
where confidentiality is not critical, softer controls such as
application workflow and audit logging can support data integrity
requirements while not restricting user access to functionality or
creating complex role structures that are difficult to manage. Its
important to consider the Goldilocks principle when role engineering, in
that defining too few, broad roles (thereby exposing access to
functionality users don't require) is as bad as too many, tightly
tailored roles (thereby restricting access to functionality users do
require).

## Test objectives

Validate the system roles defined within the application sufficiently
define and separate each system and business role to manage appropriate
access to system functionality and information.

## How to test

Either with or without the help of the system developers or
administrators, develop an role versus permission matrix. The matrix
should enumerate all the roles that can be provisioned and explore the
permissions that are allowed to be applied to the objects including any
constraints. If a matrix is provided with the application it should be
validated by the tester, if it doesn't exist, the tester should generate
it and determine whether the matrix satisfies the desired access policy
for the application.

### Example 1

|               |  |                |  |                  |  |                                                            |
| ------------- |  | -------------- |  | ---------------- |  | ---------------------------------------------------------- |
| **ROLE**      |  | **PERMISSION** |  | **OBJECT**       |  | **CONSTRAINTS**                                            |
| Administrator |  | Read           |  | Customer records |  |                                                            |
| Manager       |  | Read           |  | Customer records |  | Only records related to business unit                      |
| Staff         |  | Read           |  | Customer records |  | Only records associated with customers assigned by Manager |
| Customer      |  | Read           |  | Customer record  |  | Only own record                                            |

A real world example of role definitions can be found in the WordPress
roles documentation
[1](http://codex.wordpress.org/Roles_and_Capabilities). WordPress has
six default roles ranging from Super Admin to a Subscriber.

### Example 2

Login with admin permission and access pages that only for
administrator. Then, login as normal user and try to access those
administrator pages URL directly.

1\. Login as administrator 2. Visit admin page. i.e.
<http://targetSite/Admin> 3. Logout 4. Login as normal user 5. Visit the
admin page URL directly. <http://targetSite/Admin>

## Tools

While the most thorough and accurate approach to completing this test is
to conduct it manually, spidering tools
[2](http://code.google.com/p/zaproxy/wiki/HelpStartConceptsSpider) are
also useful. Log on with each role in turn and spider the application
(don't forget to exclude the logout link from the spidering).

## References

[Role Engineering for Enterprise Security Management, E Coyne & J
Davis, 2007](https://www.bookdepository.co.uk/Role-Engineering-for-Enterprise-Security-Management-Edward-Coyne/9781596932180)

[Role engineering and RBAC
standards](http://csrc.nist.gov/groups/SNS/rbac/standards.html)

## Remediation

Remediation of the issues can take the following forms:

  - Role Engineering
  - Mapping of business roles to system roles
  - Separation of Duties