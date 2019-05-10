#### Main

## Introduction

AntiXSS is a class for use with PHP 5+ that helps to reduce XSS
(cross-site scripting) vulnerabilities by automatically encoding output
to behave only as intended.

<table>
<tbody>
<tr class="odd">
<td><p>style="width:56%;color:#000"</p></td>
<td><table>
<tbody>
<tr class="odd">
<td><p>style="width:280px;text-align:center;color:#000"</p></td>
<td><div style="font-size:162%;border:none;margin: 0;color:#000">
<p>'''NOTE</p></td>
<td><p>!'''</p>
</div>
<div style="top:+0.2em;font-size: 95%">
</div></td>
</tr>
</tbody>
</table></td>
<td><p>style="width:14%;font-size:95%;color:#000"</p></td>
<td><p>NOTE: This library will eventually replaced by the ESAPI for PHP port. That effort is not complete as yet. The actual API will not change dramatically between AntiXSS library and ESAPI for PHP.</p></td>
<td><p>style="width:14%;font-size:95%"</p></td>
<td></td>
</tr>
</tbody>
</table>

## Requirements

  - PHP5 and above
  - mb_string PHP extension

## Usage

1.  Make sure the **mb_string** extension is available with your PHP
    installation. If you are using Apache on Windows, this can most
    likely be done by adding (or un-commenting) a line in your php.ini
    file. On other platforms, you may need to recompile PHP. See
    [1](http://us2.php.net/mb_string) for more information.
2.  To make the code available to your program, **include the
    owasp.antixss.php file**, using a line like this: require_once
    "/path/to/owasp.antixss.php";
3.  It is not necessary to instantiate the class, though you may if you
    wish. Instead, **make calls using the Scope Resolution Operator
    (::)**, like this: echo AntiXSS::HTMLEncode($myOutput);

## Examples

### HTML

<tt>

Hello, <strong>\<php echo AntiXSS:HTMLEncode($nameOfMyUser);
?\></strong>\!

</tt>

### JavaScript

<tt> ... alert(myFunction('

<?php echo AntiXSS:JavaScriptEncode($myVariable); ?>

'); ... </tt>

### URL

`...` `http://example.com/myscript.php?<?php echo
AntiXSS::URLEncode($myQueryStringValue); ?>` `...`

### XML

<tt>
<myelement myattribute="<?php echo AntiXSS::XMLAttributeEncode($myAttributeValue); ?>">

<?php echo AntiXSS::XMLEncode($myElementValue); ?>

</myelement > </tt>

## Downloads

Downloads are not yet available.

  - owasp.antixss.php
  - demo.owasp.antixss.php

## Troubleshooting

### Encoding

The AntiXSS class will use any character encoding supported by libmbfl,
the library upon which the mbstring functions are based, with the
exception of 7bit and BASE64.

A list of supported character sets is available at PHP.net:
[2](http://us2.php.net/mb_string)

The Owasp AntiXSS class utilizes the following encodings: UTF-32,
HTML-ENTITIES

Typically, your doctype definition will match the encoding of your
source files and your database source. If you run into issues where some
characters don't display or display wrong, check the encoding of every
data source and file involved.

And particularly if you wish to output extended or multibyte characters
from within your source files, make sure the encoding of all files
involved matches the output format, unless you will be handling your
conversions manually using mb_convert_encoding.

#### Project Identification

__NOTOC__ <headertabs />

[PHP AntiXSS Library Project](Category:OWASP_Project "wikilink")