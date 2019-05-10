## Description

Encoding, closely related to [Escaping](Escaping "wikilink") is a
powerful mechanism to help protect against many types of attack,
especially [injection attacks](:Category:Injection_Attack "wikilink")
and [Cross-site Scripting
(XSS)](Cross-site_Scripting_\(XSS\) "wikilink"). Essentially, encoding
involves translating special characters into some equivalent that is no
longer significant in the target interpreter. So, for example, using
HTML entity encoding before sending untrusted data into a browser will
protect against many forms of [Cross-site Scripting
(XSS)](Cross-site_Scripting_\(XSS\) "wikilink").

Considerations:

  - What interpreter?
    To encode properly, you need to know what interpreters the data
    might end up in. For example, if the data is going into a SQL
    interpreter, you should consider encoding based on syntax of the SQL
    engine you are using.

<!-- end list -->

  - What characters? Complete?
    You want to make sure that you encode all the characters that might
    cause a problem, so the best approach is to use a positive encoding
    scheme, where all characters except a minimal **known good** set are
    encoded.

<!-- end list -->

  - What encoding scheme?
    There are dozens of ways to encode characters and many interpreters
    allow multiple forms of a single significant character. For a
    browser, HTML entity encoding is a good way to prevent script
    injection, but URL encoding or Unicode encoding (%xx) will not
    prevent scripts from running. Be sure to use the appropriate
    encoding scheme for the target interpreter.

<!-- end list -->

  - Double encoding and decoding?
    Be careful not to double encode your data. In some cases, doubly
    encoding data can inadvertently introduce special characters in the
    final output. Also, be aware that some processors may automatically
    undo your encoding. There is some evidence that XML processors are
    decoding HTML entity encoding, thus reintroducing potential
    [XSS](Cross-site_Scripting_\(XSS\) "wikilink") problems.

See the [:Category:OWASP Encoding
Project](:Category:OWASP_Encoding_Project "wikilink") for more
information.

## Examples

<u>ASP.NET Example</u>

ASP.NET pages have a "ValidateRequest" property which is set to true by
default. This prevents XSS-type attacks in submitted form fields -
ASP.NET will throw an exception if it detects script-type "unsafe"
content in a request. Unfortunately this mechanism will be triggered in
response to certain characters you may actually want to receive in a
request, such as \> and \<.

<code title="Page declaration attribute">

\<%@ Page Language="C\#" CodeFile="Default.aspx.cs" Inherits="_Default"
ValidateRequest="false" %\>

</code>

To get around this, disable page validation for the page and use
Server.HTMLEncode (and its URL equivalent URLEncode for GET operations)
to encode user input: -

<code title="c# server-side code">

`   protected override void OnLoad(EventArgs e) `
`   {    `
`       lblMessage.Text = Server.HtmlEncode(txtName.Text);`
`   }`

</code>

<u>PHP Example</u>

PHP offers two identical built in functions to perform entity encoding:
[htmlentities](http://www.php.net/manual/en/function.htmlentities.php)
and
[htmlspecialchars](http://www.php.net/manual/en/function.htmlspecialchars.php).
By default both functions require only the string to encode as a
parameter, however optionally additional parameters can be used to
govern how apostrophes and double quotes are encoded (if the parameter
is not provided the function will convert double quotes and leave
apostrophes alone), which character set to output the results as (ISO
ISO-8859-1 is the default if not provided), and whether or not to double
encode the results. If the double encode parameter is not provided, or
set to true, existing html entities will be encoded a second time.

<u>Java Example</u>

Unlike ASP.Net and PHP, Java does not have built in entity encoding
functionality. There is, however, an example function to perform entity
encoding provided by OWASP: [How to perform HTML entity encoding in
Java](How_to_perform_HTML_entity_encoding_in_Java "wikilink"). As a word
of warning for those writing internationalized websites, the
implementation is very "basic ASCII" centric in terms of encoding
characters, and will encode every character not in the a-z,A-Z,0-9 range
even if the page character set would normally support the characters
un-encoded without issue. This can dramatically increase the size of
page being served. An alternative to avoid this issue is to use the
encoding function provided by the widely distributed Apache Commons Lang
library. To use this library first import
org.apache.commons.lang.StringEscapeUtils. Additionally the input must
be unescaped prior to encoding, hence the nested function call in the
sample code below.

<code title="StringEscapeUtils example">

`   String Output = StringEscapeUtils.escapeHtml(StringEscapeUtils.unescapeHtml(input));`

</code>

## Related Threats

## Related Attacks

## Related Vulnerabilities

## Related Countermeasures

  - [Input Validation](Input_Validation "wikilink")