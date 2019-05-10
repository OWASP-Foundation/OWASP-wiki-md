## Summary

Guest and Training accounts are useful ways to acquaint potential users
with system functionality prior to them completing the authorisation
process required for access. However, these accounts are often modeled
on business roles and may be provisioned with access to more
functionality than is required for the user.

## Test objectives

Evaluate consistency between access policy and guest/training account
access permissions

Build or validate access control matrix including guest/training
accounts

## How to test

Either with or without the help of the system developers/configurators,
develop an guest/training account vs. permission matrix. The matrix
should explore the permissions that assigned to guest/training accounts.
If a matrix is provided with the application it should be validated by
the tester, if it doesn't exist, the tester should generate it and
determine whether the matrix satisfies the desired access policy for the
application.

### Example

<insert some images of guest/training account instances>

## Tools

## References

## Remediation

Ensure guest/training accounts are provisioned with the minimum
permissions required for users that are not formally authorised or
trained to use the application.