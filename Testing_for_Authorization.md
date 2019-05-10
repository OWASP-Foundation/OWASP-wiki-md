''' 4.6 Authorization Testing '''

-----

Authorization is the concept of allowing access to resources only to
those permitted to use them. Testing for Authorization means
understanding how the authorization process works, and using that
information to circumvent the authorization mechanism.

Authorization is a process that comes after a successful authentication,
so the tester will verify this point after he holds valid credentials,
associated with a well-defined set of roles and privileges. During this
kind of assessment, it should be verified if it is possible to bypass
the authorization schema, find a path traversal vulnerability, or find
ways to escalate the privileges assigned to the tester.

[4.6.1 Testing Directory traversal/file include
(OTG-AUTHZ-001)](Testing_for_Path_Traversal_\(OTG-AUTHZ-001\) "wikilink")

[4.6.2 Testing for bypassing authorization schema
(OTG-AUTHZ-002)](Testing_for_Bypassing_Authorization_Schema_\(OTG-AUTHZ-002\) "wikilink")

[4.6.3 Testing for Privilege Escalation
(OTG-AUTHZ-003)](Testing_for_Privilege_escalation_\(OTG-AUTHZ-003\) "wikilink")

[4.6.4 Testing for Insecure Direct Object References
(OTG-AUTHZ-004)](Testing_for_Insecure_Direct_Object_References_\(OTG-AUTHZ-004\) "wikilink")