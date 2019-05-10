It is pretty easy to remove all persistent XSS attacks from PHP, just
remove all instances of output functions (such as echo and print) with
their safe counterparts from OWASP PHP Security Core Library, and then
whenever you need HTML elements to be outputted, used the appropriate
functions or PHP tags. There's a scanner in PHP Security Project that
scans for this and can replace it effectively as well.

## Scanner PHP

As mentioned earlier, you can download the Scanner PHP using the PHPSEC
framework at
<https://www.owasp.org/index.php/OWASP_PHP_Security_Project>

` /**`
` * Array to hold all the words that are considered unsafe.`
` * @var Array`
` */`
` public static $blacklist = array("T_ECHO"=>"echo", "T_PRINT"=>"print","printf","vprintf");`