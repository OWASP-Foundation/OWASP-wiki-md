Untrusted data, if being placed inside a Javascript function/code
requires validation. Unvalidated data may break out of the data context
and wind up being executed in the code context on a users browser.

**Examples of exploitation points (sinks) which are worth reviewing
for:**

<script>

var currentValue=**'UNTRUSTED DATA**';

</script>

<script>

someFunction(**'UNTRUSTED DATA**');

</script>

`    attack: ');`**`/*``   ``BAD``   ``STUFF``   ``*/`**
`    `

**Potential solutions:**

[OWASP HTML sanatiser
Project](https://www.owasp.org/index.php/OWASP_Java_HTML_Sanitizer_Project)
[OWASP JSON Sanitizer
Project](https://www.owasp.org/index.php/OWASP_JSON_Sanitizer)

ESAPI javascript escaping can be call in this manner:

`    String safe = ESAPI.encoder().encodeForJavaScript( request.getParameter( "input" ) );`

**Please note there are some JavaScript functions that can never safely
use untrusted data as input - EVEN IF JAVASCRIPT ESCAPED\!**

For example:

<script>

`    window.setInterval('...EVEN IF YOU ESCAPE UNTRUSTED DATA YOU ARE XSSED HERE...');`
`    `

</script>

**eval()**

`    var txtField = "A1";`
`    var txtUserInput = "'test@google.ie';`**`alert(1);`**`";`
`    `**`eval`**`(   "document.forms[0]." + txtField + ".value =" + A1);`

**jquery**

`    var txtAlertMsg = "Hello World: ";`
`    var txtUserInput = "test`

<script>

alert(1)\<\\/script\>";

`    $("#message").`**`html`**`(   txtAlertMsg +"`<b>`" + txtUserInput + "`</b>`");`

`    Safe usage (use text, not html)`
`    $("#userInput").`**`text`**`(   "test`

<script>

alert(1)\<\\/script\>");\<-- treat user input as text

**Nested Contexts** Best to avoid such nested contexts: an element
attribute calling a Javascript function etc These contexts can really
mess with your mind.

`    <div onclick="showError('<%=request.getParameter("errorxyz")%>')" >An error occurred ....`

</div>

`    `**`Here``   ``we``   ``have``   ``a``   ``HTML``
 ``attribute(onClick)``   ``and``   ``within``   ``a``   ``nested``
 ``Javascript``   ``function``   ``call``   ``(showError).`**

When the browser processes this it will first HTML decode the contents
of the onclick attribute. It will pass the results to the JavaScript
Interpreter. So we have 2 contextx here...HTML and Javascript (2 browser
parsers). We need to apply “layered” encoding in the RIGHT order:
**1) JavaScript encode**
**2) HTML Attribute Encode so it "unwinds" properly and is not
vulnerable**.

`   <div onclick="showError`
`   ('<%= Encoder.encodeForHtml(Encoder.encodeForJavaScript( request.getParameter("error")%>')))" `
`   >An error occurred ....`

</div>