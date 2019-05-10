[Return to Periodic Table Working
View](OWASP_Periodic_Table_of_Vulnerabilities#Periodic_Table_of_Vulnerabilities "wikilink")

## Insufficient Process Validation

### Root Cause Summary

The application fails to enforce business process rules, such as
ordering of multi-step form submission or conditions on asynchronous
transactions.

### Browser / Standards Solution

N/A

### Perimeter Solution

N/A

### Generic Framework Solution

The generic framework should provide built-in support for multi-step
forms which automatically checks for correct client state, including
unexpected use of the "back" button, multiple submissions of the same
form, and out-of-order access of form steps. The framework should expose
configuration-based rules about how to handle each error condition.

### Custom Framework Solution

N/A

### Custom Code Solution

Developers must remember to explicitly enforce all business and process
rules for every transaction, including every individual step of a
multi-step transaction.

### Discussion / Controversy

### References

[Insufficent Process Validation
(WASC)](http://projects.webappsec.org/w/page/13246943/Insufficient%20Process%20Validation)