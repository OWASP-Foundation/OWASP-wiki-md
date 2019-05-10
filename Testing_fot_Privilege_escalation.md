**This is a draft of a section of the new Testing Guide v3**

## Brief Summary


This section describes the issue of escalating privileges from one stage
to another...
\== Description of the Issue ==
Privilege escalation occurs when a user gets to access more resources
than is normally allowed when it should have been protected from the
application. This is usually conducted from a flaw in the application.
The result is that the application performs actions with more privileges
than intended by the application developer or system administrator.

The degree of the escalation depends on which privileges the attacker is
authorized to possess and which privileges can be obtained in a
successful attack. For example, a programming error that permits a user
to gain extra privilege after successful authentication limits the
degree of escalation because the user is already authorized to hold some
privilege. Likewise, a remote attacker gaining superuser privilege
without any authentication presents a greater degree of escalation.


\== Black Box testing and example == **Testing for Topic X
vulnerabilities:**
...
**Result Expected:**
...

\== Gray Box testing and example == **Testing for Topic X
vulnerabilities:**
...
**Result Expected:**
...

\== References == **Whitepapers**
...
**Tools**
...