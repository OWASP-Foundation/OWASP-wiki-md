## Summary

WordPress started in 2003 with a single bit of code to enhance the
typography of everyday writing and with fewer users than you can count
on your fingers and toes. Since then it has grown to be the largest
self-hosted blogging tool in the world, used on millions of sites and
seen by tens of millions of people every day. WordPress is web software
you can use to create a beautiful website or blog. We like to say that
WordPress is both free and priceless at the same time.

## Common Misconfigurations

### PHP Errors On : Server misconfiguration

#### Description

Wordpress CMS assumes that the server would have PHP Errors turned off
and developers will rely on internal WP_DEBUG feature for Debugging the
issues.

#### How to test

In order to test for PHP Errors setting, one can make a call to known
Full path disclosing files. one such file is
wp-includes/rss-functions.php (a list of such files was created for
specific versions of wordpress example
[2.9.2](https://code.google.com/p/inspathx/source/browse/trunk/paths_vuln/wordpress_2.9.2)
and
[3.0.4](https://code.google.com/p/inspathx/source/browse/trunk/paths_vuln/wordpress-3.0.4)
) if a call is made to <http://%site%/wp-includes/rss-functions.php> and
a error message is obtained in the lines of

Fatal error: Call to undefined function _deprecated_file() in
/home/ABCD_XYZ/public_html/wp-includes/rss-functions.php on line 8

#### Remediation

1\. Using .htaccess file in webroot place \`php_flag display_errors
off\`

2\. Using php.ini for the server \`display_errors off\`

## Additional Hardening

Install PHP- Suhosin Patch:

  - [Suhosin Patch PHP](http://suhosin.org/stories/index.html)

### Misconfiguration 1

#### Description

%ProductName% allows unauthorized attacker to list all users of the
system ...

// Detailed description of the impact. Is it enabled by default?
Vulnerable versions.

#### How to test

In order to test for %Misconfiguration_1%, one should ...

// Proof-of-concept here. Please include the screenshots and widely
known tools/scanners\!

#### Remediation

Initial/common value of parameter "listUsers" from config.xml is set to
"true".

To assess the vulnerability it is enough to change the value to false:

    <security>
        <listUsers>false</listUsers>
    </security>

## Checklist

define( 'WP_DEBUG_LOG', true ); // log to wp-content/debug.log

''' To be filled in in accordance to the template, some useful links:
'''

<http://codex.wordpress.org/Hardening_WordPress> (consider writing only
real security risks with good examples)

<https://github.com/anantshri/wp-security> (extract samples from here.
keep them as code sections either for a plugin or for a theme
functions.php, .htaccess or nginx config file)

## Testing Wordpress Security and Misconfiguration

  - [Scan Your Site with WPScan](http://wpscan.org)
  - [Scan site with Nikto](http://hackertarget.com/nikto-tutorial/)