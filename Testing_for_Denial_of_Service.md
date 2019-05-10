''' 4.9 Denial of Service Testing '''

-----

A denial of service (DoS) attack is an attempt to make a resource
unavailable to its legitimate users. Traditionally, denial of service
(DoS) attacks have been network based: a malicious user floods a target
machine with enough traffic to make it incapable of servicing its
intended users. When the attack is launched by leveraging a large number
of machines, the attack is typically called a distributed denial of
service (DDoS) attack. In general, network DoS attacks are beyond the
scope of what application developers can prevent within their own code.
This type of “battle of the network pipes” is best mitigated via network
architecture solutions.

There are, however, types of vulnerabilities at the application level
that can allow a malicious user to make certain functionality or,
sometimes, the entire website unavailable. These problems are caused by
bugs in the application and often are triggered by malicious or
unexpected user input. This section will focus on application layer
attacks against availability that can be launched by just one malicious
user on a single machine.

Here are the DoS tests we will talk about:

1.  [Testing for SQL Wildcard Attacks
    (OWASP-DS-001)](Testing_for_SQL_Wildcard_Attacks_\(OWASP-DS-001\) "wikilink")
2.  [Testing for DoS Locking Customer Accounts
    (OWASP-DS-002)](Testing_for_DoS_Locking_Customer_Accounts_\(OWASP-DS-002\) "wikilink")
3.  [Testing for DoS Buffer Overflows
    (OWASP-DS-003)](Testing_for_DoS_Buffer_Overflows_\(OWASP-DS-003\) "wikilink")
4.  [Testing for DoS User Specified Object Allocation
    (OWASP-DS-004)](Testing_for_DoS_User_Specified_Object_Allocation_\(OWASP-DS-004\) "wikilink")
5.  [Testing for User Input as a Loop Counter
    (OWASP-DS-005)](Testing_for_User_Input_as_a_Loop_Counter_\(OWASP-DS-005\) "wikilink")
6.  [Testing for Writing User Provided Data to Disk
    (OWASP-DS-006)](Testing_for_Writing_User_Provided_Data_to_Disk_\(OWASP-DS-006\) "wikilink")
7.  [Testing for DoS Failure to Release Resources
    (OWASP-DS-007)](Testing_for_DoS_Failure_to_Release_Resources_\(OWASP-DS-007\) "wikilink")
8.  [Testing for Storing too Much Data in Session
    (OWASP-DS-008)](Testing_for_Storing_too_Much_Data_in_Session_\(OWASP-DS-008\) "wikilink")

## References

Stephen de Vries, Application denial of service (DoS) attacks:
<http://www.infosecwriters.com/text_resources/pdf/application_level_DoS_attacks.pdf>
HTTP Get and HTTP Post attacks:
<http://www.owasp.org/index.php/OWASP_HTTP_Post_Tool>



[Category:Denial of Service
Attack](Category:Denial_of_Service_Attack "wikilink")