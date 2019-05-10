# Main

<div style="width:100%;height:160px;border:0,margin:0;overflow: hidden;">

![OWASP_Project_Header.jpg](OWASP_Project_Header.jpg
"OWASP_Project_Header.jpg")

</div>

<table>
<tbody>
<tr class="odd">
<td><p>valign="top" style="border-right: 1px dotted gray;padding-right:25px;"</p></td>
<td><h2 id="owasp_json_sanitizer_project">OWASP JSON Sanitizer Project</h2>
<p>Our Mission: Given JSON-like content, convert it to valid JSON! The OWASP JSON Sanitizer Project is a simple to use Java library that can be attached at either end of a data-pipeline to help satisfy Postel's principle: <i>be conservative in what you do, be liberal in what you accept from others.</i> When applied to JSON-like content from others, this project will produce well-formed JSON that should satisfy any parser you use. When applied to your output before you send, it will coerce minor mistakes in encoding and make it easier to embed your JSON in HTML and XML.</p>
<p>This library is very easy to use. For more information, visit the <a href="https://code.google.com/p/json-sanitizer/wiki/GettingStarted">getting started guide</a>.</p>
<h2 id="licensing">Licensing</h2>
<p>The OWASP JSON Sanitizer is free to use under the <a href="http://www.apache.org/licenses/LICENSE-2.0">Apache 2 License</a>.</p></td>
<td><p>valign="top" style="padding-left:25px;width:200px;border-right: 1px dotted gray;padding-right:25px;"</p></td>
<td><h2 id="what_is_this">What is this?</h2>
<p>The OWASP JSON Sanitizer Projects provides:</p>
<ul>
<li>Java based JSON outbound or inbound sanitization library</li>
</ul>
<h2 id="code_repo">Code Repo</h2>
<p><a href="https://github.com/owasp/json-sanitizer">OWASP JSON Sanitizer at GitHub</a></p>
<h2 id="email_list">Email List</h2>
<p><a href="https://groups.google.com/forum/#!forum/json-sanitizer-support">Project Support List</a></p>
<h2 id="project_leaders">Project Leaders</h2>
<p>Author/Project Leader<br />
<a href="https://www.owasp.org/index.php/User:Mike_Samuel">Mike Samuel</a> <a href="mailto:jim.manico@owasp.org">@</a><br />
<br />
Project Manager<br />
<a href="https://www.owasp.org/index.php/User:Jmanico">Jim Manico</a> <a href="mailto:jim.manico@owasp.org">@</a></p>
<h2 id="related_projects">Related Projects</h2>
<ul>
<li><a href="XSS_(Cross_Site_Scripting)_Prevention_Cheat_Sheet" title="wikilink">XSS (Cross Site Scripting) Prevention Cheat Sheet</a></li>
<li><a href="OWASP_Java_HTML_Sanitizer_Project" title="wikilink">OWASP Java HTML Sanitizer Project</a></li>
<li><a href="OWASP_Java_Encoder_Project" title="wikilink">OWASP Java Encoder Project</a></li>
<li><a href="OWASP_Dependency_Check" title="wikilink">OWASP Dependency Check</a></li>
<li><a href="https://github.com/sourceclear/headlines">Sourceclear Headlines</a></li>
<li><a href="https://code.google.com/p/keyczar/">Google KeyCzar</a></li>
<li><a href="http://shiro.apache.org/">Apache SHIRO</a></li>
</ul></td>
<td><p>valign="top" style="padding-left:25px;width:200px;"</p></td>
<td><h2 id="quick_download">Quick Download</h2>
<ul>
<li><a href="https://search.maven.org/#artifactdetails%7Ccom.mikesamuel%7Cjson-sanitizer%7C1.1%7Cjar">v1.1 home at Maven Central</a></li>
<li><a href="https://search.maven.org/remotecontent?filepath=com/mikesamuel/json-sanitizer/1.1/json-sanitizer-1.1.jar">v1.1 jar at Maven Central</a></li>
</ul>
<h2 id="news_and_events">News and Events</h2>
<ul>
<li>[October 15, 2015] v1.1 Released at Maven Central!</li>
<li>[July 5, 2014] v1 Released at Maven Central!</li>
<li>[March 29, 2014] Template and Doc cleanup!</li>
<li>[Oct 17, 2012] .9 Released!</li>
</ul>
<h2 id="classifications">Classifications</h2>
<table>
<tbody>
<tr class="odd">
<td><p>align="center" valign="top" width="50%" rowspan="2"</p></td>
<td><figure>
<img src="Owasp-incubator-trans-85.png" title="Owasp-incubator-trans-85.png" alt="Owasp-incubator-trans-85.png" /><figcaption>Owasp-incubator-trans-85.png</figcaption>
</figure></td>
<td><p>align="center" valign="top" width="50%"</p></td>
<td><figure>
<img src="Owasp-builders-small.png" title="Owasp-builders-small.png" alt="Owasp-builders-small.png" /><figcaption>Owasp-builders-small.png</figcaption>
</figure></td>
</tr>
<tr class="even">
<td><p>align="center" valign="top" width="50%"</p></td>
<td><figure>
<img src="Owasp-defenders-small.png" title="Owasp-defenders-small.png" alt="Owasp-defenders-small.png" /><figcaption>Owasp-defenders-small.png</figcaption>
</figure></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>colspan="2" align="center"</p></td>
<td><p><a href="http://www.apache.org/licenses/LICENSE-2.0">Apache 2 License</a></p></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>colspan="2" align="center"</p></td>
<td><figure>
<img src="Project_Type_Files_CODE.jpg" title="Project_Type_Files_CODE.jpg" alt="Project_Type_Files_CODE.jpg" /><figcaption>Project_Type_Files_CODE.jpg</figcaption>
</figure></td>
<td></td>
<td></td>
</tr>
</tbody>
</table></td>
</tr>
</tbody>
</table>

# Getting Started

## Importing the JSON Sanitizer

You can fetch the jars from [Maven
Central](http://search.maven.org/#search%7Cga%7C1%7Cjson-sanitizer) or
you can let your favorite java package manager handle it for you via:

` `<dependency>
`   `<groupId>`com.mikesamuel`</groupId>
`   `<artifactId>`json-sanitizer`</artifactId>
`   `<version>`1.1`</version>
</dependency>

Once you've got the JSON sanitizer JAR on your classpath,

`   import com.google.json.JsonSanitizer;`

will let you call

`   String wellFormedJson = JsonSanitizer.sanitize(myJsonLikeString);`

That's it. Now wellFormedJson is a string of well-formed JSON that is
safe to pass to JavaScript?'s eval operator and which can be easily
embedded in XML or HTML.

If you have further questions, check our [support
list](https://github.com/OWASP/json-sanitizer/issues).

# Motivation

The OWASP JSON Sanitizer Project is a simple to use Java library that
can be attached at either end of a data-pipeline. When applied to
JSON-like content from others, this project will produce well-formed
JSON that should satisfy any parser you use. When applied to your output
before you send, it will coerce minor mistakes in encoding and make it
easier to embed your JSON in HTML and XML.

![JSON-Sanitizer-Arch.png](JSON-Sanitizer-Arch.png
"JSON-Sanitizer-Arch.png")

Many applications have large amounts of code that uses ad-hoc methods to
generate JSON outputs. Frequently these outputs all pass through a small
amount of framework code before being sent over the network. This small
amount of framework code can use this library to make sure that the
ad-hoc outputs are standards compliant and safe to pass to (overly)
powerful deserializers like Javascript's eval operator.

Applications also often have web service APIs that receive JSON from a
variety of sources. When this JSON is created using ad-hoc methods, this
library can massage it into a form that is easy to parse.

By hooking this library into the code that sends and receives requests
and responses, this library can help software architects ensure
system-wide security and well-formedness guarantees.

# Input

The sanitizer takes JSON like content, and interprets it as JS eval
would. Specifically, it deals with these non-standard constructs.

|               |                                                               |
| ------------- | ------------------------------------------------------------- |
| `'...'`       | Single quoted strings are converted to JSON strings.          |
| `\xAB`        | Hex escapes are converted to JSON unicode escapes.            |
| `\012`        | Octal escapes are converted to JSON unicode escapes.          |
| `0xAB`        | Hex integer literals are converted to JSON decimal numbers.   |
| `012`         | Octal integer literals are converted to JSON decimal numbers. |
| `+.5`         | Decimal numbers are coerced to JSON's stricter format.        |
| `[0,,2]`      | Elisions in arrays are filled with `null`.                    |
| `[1,2,3,]`    | Trailing commas are removed.                                  |
| `{foo:"bar"}` | Unquoted property names are quoted.                           |
| `//comments`  | JS style line and block comments are removed.                 |
| `(...)`       | Grouping parentheses are removed.                             |

The sanitizer fixes missing punctuation, end quotes, and mismatched or
missing close brackets. If an input contains only white-space then the
valid JSON string `null` is substituted.

# Output

The output is well-formed JSON as defined by
[RFC 4627](http://www.ietf.org/rfc/rfc4627.txt). The output satisfies
three additional properties:

1.  The output will not contain the substring (case-insensitively)
    `"</script"` so can be embedded inside an HTML script element
    without further encoding.
2.  The output will not contain the substring `"]]>"` so can be embedded
    inside an XML CDATA section without further encoding.
3.  The output is a valid Javascript expression, so can be parsed by
    Javascript's `eval` builtin (after being wrapped in parentheses) or
    by `JSON.parse`. Specifically, the output will not contain any
    string literals with embedded JS newlines (U+2028 Paragraph
    separator or U+2029 Line separator).
4.  The output contains only valid Unicode [scalar
    values](http://www.unicode.org/glossary/#unicode_scalar_value) (no
    isolated [UTF-16
    surrogates](http://www.unicode.org/glossary/#surrogate_pair)) that
    are [allowed in XML](http://www.w3.org/TR/xml/#charsets) unescaped.

# Security

Since the output is well-formed JSON, passing it to eval will have no
side-effects and no free variables, so is neither a code-injection
vector, nor a vector for exfiltration of secrets.

This library only ensures that the JSON string → Javascript object phase
has no side effects and resolves no free variables, and cannot control
how other client side code later interprets the resulting Javascript
object. So if client-side code takes a part of the parsed data that is
controlled by an attacker and passes it back through a powerful
interpreter like eval or innerHTML then that client-side code might
suffer unintended side-effects.

`  var myValue = eval(sanitizedJsonString);  // safe`
`  var myEmbeddedValue = eval(myValue.foo);  // possibly unsafe`

Additionally, sanitizing JSON cannot protect an application from
Confused Deputy attacks

`  var myValue = JSON.parse(sanitizedJsonString);`
`  addToAdminstratorsGroup(myValue.propertyFromUntrustedSource);`

# Performance

The sanitize method will return the input string without allocating a
new buffer when the input is already valid JSON that satisfies the
properties above. Thus, if used on input that is usually well formed, it
has minimal memory overhead.

The sanitize method takes O(n) time where n is the length in UTF-16
code-units.

# Analogy

The JSON Sanitizer is similar to a [decoupling
capacitor](http://en.wikipedia.org/wiki/Decoupling_capacitor).

Any module that takes noisy input in and puts out clean output helps
\*decouple\* the security properties of one piece of code (that uses
eval) from the security properties of another (that concatenates
untrusted strings to produce JSON) so that a failure in one does not
necessitate a failure in the other.

__NOTOC__ <headertabs />

[Category:OWASP_Tool](Category:OWASP_Tool "wikilink")
[Category:OWASP_Alpha_Quality_Tool](Category:OWASP_Alpha_Quality_Tool "wikilink")
[OWASP JSON Sanitizer Project](Category:OWASP_Project "wikilink")