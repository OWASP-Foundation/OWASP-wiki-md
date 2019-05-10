HTML elements which contain user controlled data or data from untrusted
sourced should be reviewed for contextual output encoding. In the case
of HTML entities we need to help ensure HTML Entity Encoding is
perfromed:

**Example HTML Entity containing untrusted data:**

`   HTML Body Context`
`   `
`   <span>UNTRUSTED DATA</span>`
`   OR`
`   `

<body>

...UNTRUSTED DATA

</body>

`   OR`
`   <div>UNTRUSTED DATA </div>`
`   `

HTML Entity Encoding is required

`   & --> &`
`   < --> <`
`   > --> >`
`   " --> "`
`   ' --> '`

It is recommended to review where/if untrusted data is placed within
entity objects. searching the source code fro teh followign encoders may
help establish if HTML entity encoding is being done in the application
and in a consistant manner.
**OWASP Java Encoder Project**
<https://www.owasp.org/index.php/OWASP_Java_Encoder_Project>

`   `<input type="text" name="data" value="<%= Encode.forHtmlAttribute(dataValue) %>`" />`
`   `

**OWASP ESAPI**
<http://code.google.com/p/owasp-esapi-java/source/browse/trunk/src/main/java/org/owasp/esapi/codecs/HTMLEntityCodec.java>

`   String safe = ESAPI.encoder().encodeForHTML( request.getParameter( "input" ) );`

**PHP**
<http://php.net/manual/en/function.htmlentities.php>

**.NET**
<http://msdn.microsoft.com/en-us/library/w3te6wfz.aspx>