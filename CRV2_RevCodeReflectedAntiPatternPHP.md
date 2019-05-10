To mitigate reflected XSS attacks fully, a PHP code should never output
variables using echo, print and other output generating functions. If
the output needs to be complex (for example a HTML list of variables)
the HTML part should be outside PHP tags, and the rest should be inside
and using safe output functions (available in OWASP PHP Security Project
Core Library). For example:

`  `
`   foreach ($list as $item)`
`   {`
`   ?>`
`   <li><?php phpsec\exho($item);?></li>`
`   <?php`
`   }`

Or

`  `
`   foreach ($list as $item)`
`   {`
`      phpsec\printf("<li>%s</li>\n",$item);`
`   }`