[Return to Periodic Table Working
View](OWASP_Periodic_Table_of_Vulnerabilities#Periodic_Table_of_Vulnerabilities "wikilink")

## Abuse of Functionality

### Root Cause Summary

Abuse of functionality, sometimes referred to as a "business logic
attack", depends on the design and implementation for application
functions and features. As functionality is added to applications,
thought must be given to how the function or feature can be manipulated
to circumvent the business process, or abused to perform a function not
intended by the developer.

Some examples include:

  - Using a send-mail form to generate spam
  - Using a password reset flow to enumerate accounts
  - Using a checkout form to issue a credit to a bank account, instead
    of debiting that account

### Browser / Standards Solution

None

### Perimeter Solution

None

### Generic Framework Solution

None

### Custom Framework Solution

None

### Custom Code Solution

Robust threat modeling exercises should be performed for each
application feature to enumerate ways that attackers can abuse the
feature. All functions and features of the application should be tested
against a comprehensive set of use and abuse cases to ensure that the
application enables only the intended functionality and no more.

### Discussion / Controversy

Although there are some common abuse cases, vulnerabilities are
generally application-specific and highly dependent on the features
implemented by each application. If a generic solution can be
implemented for a class of abuse, a separate vulnerability topic will
exist to cover the solution.

### References

[WASC Abuse of
Functionality](http://projects.webappsec.org/w/page/13246913/Abuse%20of%20Functionality)
[CAPEC – 210: Abuse of
Functionality\>](http://capec.mitre.org/data/definitions/210.html)
[OWASP Category: Abuse of
Functionality](https://www.owasp.org/index.php/Category:Abuse_of_Functionality)
[OWASP Business Logic Cheat
Sheet](https://www.owasp.org/index.php/Business_Logic_Security_Cheat_Sheet)
[OWASP Testing Guide – Testing for business Logic
(OWASP-BL-001)](https://www.owasp.org/index.php/Testing_for_business_logic_\(OWASP-BL-001\))