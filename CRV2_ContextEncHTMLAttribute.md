**HTML Attribute Encoding:** HTML attributes may contain untrusted data.
It is important to determine if any ot the HTML attribites on a given
page contains data from outside the trust boundary.

Some HTML attributes are considered safeer than others such as
align, alink, alt, bgcolor, border, cellpadding, cellspacing, class,
color, cols, colspan, coords, dir, face, height, hspace, ismap, lang,
marginheight, marginwidth, multiple, nohref, noresize, noshade, nowrap,
ref, rel, rev, rows, rowspan, scrolling, shape, span, summary, tabindex,
title, usemap, valign, value, vlink, vspace, width

when reviewing code for XSS we need to look for HTML attributes such as
the folloiwng

`   `<input type="text" name="fname" value="'''UNTRUSTED DATA'''">

Attacks may take the following format:

`   ">`

<script>

/\* bad stuff \*/

</script>

**What is Attribute encoding?**
HTML attribute encoding replaces a subset of characters that are
important to prevent a string of characters from breaking the attribute
of an HTML element.
We replace ", &, and \< with ", &, and \>.
This is because the nature of attributes, the data they contain, and how
they are parsed and interpreted by a browser or HTML parser is different
than how an HTML document and its elements are read.
[XSS Prevention
CheatSheet](https://www.owasp.org/index.php/XSS_%28Cross_Site_Scripting%29_Prevention_Cheat_Sheet#RULE_.232_-_Attribute_Escape_Before_Inserting_Untrusted_Data_into_HTML_Common_Attributes):
Except for alphanumeric characters, escape all characters with ASCII
values less than 256 with the &\#xHH; format (or a named entity if
available) to prevent switching out of the attribute. The reason this
rule is so broad is that developers frequently leave attributes
unquoted. Properly quoted attributes can only be escaped with the
corresponding quote. Unquoted attributes can be broken out of with many
characters, including \[space\] % \* + , - / ; \< = \> ^ and |.

Attribute encoding may be perfromed in a number of ways.
**HttpUtility.HtmlAttributeEncode**
<http://msdn.microsoft.com/en-us/library/wdek0zbf.aspx>

**OWASP Java Encoder Project**
[OWASP Java Encoder Project
<https://www.owasp.org/index.php/OWASP_Java_Encoder_Project>](https://www.owasp.org/index.php/OWASP_Java_Encoder_Project)