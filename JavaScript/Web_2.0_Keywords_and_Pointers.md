__TOC__

Ajax and JavaScript have brought functionality back to the client side,
which has brought a number of old security issues back to the forefront.
The following keywords relate to API calls used to manipulate user state
or the control the browser. The event of AJAX and other Web 2.0
paradigms has pushed security concerns back to the client side, but not
excluding traditional server side security concerns.

Look for Ajax usage, and possible JavaScript issues:

eval(
document.cookie
document.referrer
document.attachEvent
document.body
document.body.innerHtml
document.body.innerText
document.close
document.create
document.createElement
document.execCommand
document.forms\[0\].action
document.location
document.open
document.URL
document.URLUnencoded
document.write
document.writeln
location.hash
location.href
location.search
window.alert
window.attachEvent
window.createRequest
window.execScript
window.location
window.open
window.navigate
window.setInterval
window.setTimeout
XMLHTTP

[Category:OWASP Code Review
Project](Category:OWASP_Code_Review_Project "wikilink")