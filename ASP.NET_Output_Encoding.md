# Description

Cross-site scripting attacks exploit vulnerabilities in web page
validation by injecting client-side script code. The script code embeds
itself in response data, which is sent back to an unsuspecting user. In
addition to validating input, any data retrieved from untrusted or
shared sources should be encoded on output. For example: data retrieved
from a database that may have had malicious input persisted to it.

# Encoding Output Values in Code

Use `Server.HtmlEncode` to encode untrusted data for use in HTML output:

    var encodedHtml = Server.HtmlEncode(untrustedData);

Use `Server.UrlEncode` to encode untrusted data for use in the key/value
pairs of a URL query string.

    var url = "https://www.bing.com/search?q=" + HttpUtility.UrlEncode(untrustedData);

# Encoding Output Values in HTML markup

Starting with ASP.NET 4.0 you can HTML encode values in markup with the
`<%: %>` syntax, as shown below.

    <span><%: untrustedData %></span>

Or, in Razor syntax, you can HTML encode with `@`, as shown below.

    <span>@untrustedData</span>

Starting with ASP.NET 4.5 you can also HTML encode the result of
data-binding expressions. Just add a colon (:) to the end of the \<%\#
prefix that marks the data-binding expression:

    <asp:TemplateField HeaderText="Name">
        <ItemTemplate><%#: Item.Products.Name %></ItemTemplate>
    </asp:TemplateField>

# IHtmlString

If you have model properties that are used to display raw HTML you
should consider using the `HtmlString` and `MvcHtmlString` classes
starting with .NET 4.0. These both implement the `IHtmlString` interface
and will instruct ASP.NET to skip output encoding when using `<%:
model.Property %>` or `@model.Property` in HTML markup. Converting a
property on your view model from `String` to `MvcHtmlString` will
instruct ASP.NET that HTML encoding has already been accounted for.

    public class User
    {
        public int Id { get; set; }
        public string Name { get; set; }
        public MvcHtmlString Description { get; set; } // Output encoding is handled manually
    }

# AntiXssEncoder

By default the ASP.NET encoding methods use a black-listing technique
that evaluates the string for a set of character combinations that may
indicate presence of malicious script. A superior approach is to use a
[white-listing
technique](Input_Validation_Cheat_Sheet#White_List_Input_Validation "wikilink")
for validation, which can be achieved using the Anti-Cross Site
Scripting Library from Microsoft. Starting with ASP.NET 4.5 you can
specify that the `AntiXssEncoder` from this library be used as the
default encoder for you entire application using the `encoderType`
setting in web.config as shown below.

    <httpRuntime encoderType="System.Web.Security.AntiXss.AntiXssEncoder" />

If you are using a version of .NET earlier than 4.5, you will need to
download and include the library as a reference to your project, and
then use the earlier library name for the encodeType setting as shown
below.

    <httpRuntime encoderType="Microsoft.Security.Application.AntiXssEncoder, AntiXssLibrary" />

In addition to the common `HtmlEncode` and `UrlEncode` methods, the
Anti-Cross Site Scripting Library provides the following
`AntiXssEncoder` methods for more specialized output encoding needs:

## CssEncode

Encodes the specified string for use in cascading style sheets (CSS).
This method encodes all characters except those that are in the safe
list, by using the CSS escape character (/) followed by up to six
hexadecimal digits.

|                         |                                                                   |
| ----------------------- | ----------------------------------------------------------------- |
| `alert('XSS Attack!');` | `alert\000028\000027XSS\000020Attack\000021\000027\000029\00003B` |
| `user@contoso.com`      | `user\000040contoso\00002Ecom`                                    |

## HtmlFormUrlEncode

Encodes the specified string for use in form submissions whose MIME type
is "application/x-www-form-urlencoded". This method encodes all
characters except those that are in the safe list. Characters are
encoded by using %SINGLE_BYTE_HEX notation.

|                         |                                     |
| ----------------------- | ----------------------------------- |
| `alert('XSS Attack!');` | `alert%28%27XSS+Attack%21%27%29%3B` |
| `user@contoso.com`      | `user%40contoso.com`                |

## XmlAttributeEncode

Encodes the specified string for use in XML attributes, and is slightly
more restrictive than XmlEncode below. This method encodes all
characters except those that are in the safe list. Characters are
encoded by using &\#DECIMAL; notation.

<table>
<tbody>
<tr class="odd">
<td><p><code>alert('XSS Attack!');</code></p></td>
<td><p><code>alert('XSS Attack!');</code></p></td>
</tr>
<tr class="even">
<td><p><code></p>
<script>
<p>alert('XSSあAttack!');</p>
</script>
<p></code></p></td>
<td><p><code>&lt;script&gt;alert('XSSあAttack!');&lt;/script&gt;</code></p></td>
</tr>
</tbody>
</table>

## XmlEncode

Encodes the specified string for use in XML. This method encodes all
characters except those that are in the safe list. Characters are
encoded by using &\#DECIMAL; notation.

<table>
<tbody>
<tr class="odd">
<td><p><code>alert('XSS Attack!');</code></p></td>
<td><p><code>alert('XSS Attack!');;</code></p></td>
</tr>
<tr class="even">
<td><p><code></p>
<script>
<p>alert('XSSあAttack!');</p>
</script>
<p></code></p></td>
<td><p><code>&lt;script&gt;alert('XSSあAttack!');&lt;/script&gt;</code></p></td>
</tr>
</tbody>
</table>

# References

  - [Output
    Encoding](http://blogs.msdn.com/b/cisg/archive/2008/08/28/output-encoding.aspx)
  - \[<http://msdn.microsoft.com/en-us/library/System.Web.HttpUtility_methods(v=vs.110>).aspx
    HttpUtility Methods\]
  - [Which ASP.NET Controls Automatically
    Encode?](http://blogs.msdn.com/b/sfaust/archive/2008/09/02/which-asp-net-controls-automatically-encodes.aspx)
  - [New \<%: %\> Syntax for HTML Encoding Output in ASP.NET 4 (and
    ASP.NET
    MVC 2)](http://weblogs.asp.net/scottgu/new-lt-gt-syntax-for-html-encoding-output-in-asp-net-4-and-asp-net-mvc-2)
  - [HTML Encoded Data-Binding
    Expressions](http://www.asp.net/aspnet/overview/aspnet-and-visual-studio-2012/whats-new#_Toc318097391)
  - \[<http://msdn.microsoft.com/en-us/library/system.web.ihtmlstring(v=vs.110>).aspx
    IHtmlString Interface\]
  - [What is an MvcHtmlString and when should I use
    it?](http://stackoverflow.com/questions/2293357/what-is-an-mvchtmlstring-and-when-should-i-use-it)
  - [Microsoft Anti-Cross Site Scripting Library
    V4.3](http://www.microsoft.com/en-sg/download/details.aspx?id=43126)
  - \[<http://msdn.microsoft.com/en-us/library/system.web.security.antixss.antixssencoder_methods(v=vs.110>).aspx
    AntiXssEncoder Methods\]
  - [ASP.NET Request Validation](ASP.NET_Request_Validation "wikilink")

[Category:OWASP .NET Project](Category:OWASP_.NET_Project "wikilink")