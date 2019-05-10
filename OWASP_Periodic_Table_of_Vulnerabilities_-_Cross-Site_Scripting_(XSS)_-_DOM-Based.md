[Return to Periodic Table Working
View](OWASP_Periodic_Table_of_Vulnerabilities#Periodic_Table_of_Vulnerabilities "wikilink")

### Cross-Site Scripting (XSS) - DOM-Based

## Root Cause Summary

Client-side code (e.g. JavaScript) inserts attacker-controlled data into
the DOM in a way that allows the data to be executed as functional code.
Examples include using document.write, which can introduce SCRIPT nodes
directly, and modifying innerHTML or other element attributes that can
cause SCRIPT nodes to be generated or function definitions to be
overwritten. DOM-Based XSS differs from other forms of cross-site
scripting which are the result of vulnerable server-side code.

## Browser / Standards Solution

None

## Perimeter Solution

None

## Generic Framework Solution

"Web 2.0" frameworks must expose an API for page creation/modification
that does not use document.write/ln or allow dynamic data to be injected
into innerHTML or similar DOM element attributes. Dynamic data must be
written to the DOM by using createTextNode, which does not introduce the
danger of interpreting user data as functional code.

## Custom Framework Solution

None

## Custom Code Solution

None

## Discussion / Controversy

DOM-Based Cross-Site Scripting is Sometimes referred to as “Type-0 XSS”.

## References

[OWASP - DOM Based XSS](https://www.owasp.org/index.php/DOM_Based_XSS)

[DOM-based XSS](http://www.mediawiki.org/wiki/DOM-based_XSS)

[WASC - DOM Based Cross Site Scripting or XSS of the Third
Kind](http://www.webappsec.org/projects/articles/071105.shtml)

[DOM based Cross-site Scripting
vulnerabilities](http://www.acunetix.com/blog/web-security-zone/dom-xss/)