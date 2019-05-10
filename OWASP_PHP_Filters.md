## Project Overview

A collection of easy to include PHP functions that sanitize user inputs.
Functions available are...

:\* sanitize_paranoid_string($string) -- input string, returns string
stripped of all non alphanumeric characters

:\* sanitize_system_string($string) -- input string, returns string
stripped of special characters

:\* sanitize_sql_string($string) -- input string, returns string with
slashed out quotes

:\* sanitize_html_string($string) -- input string, returns string with
html replacements for special characters

:\* sanitize_int($integer) -- input integer, returns ONLY the integer
(no extraneous characters

:\* sanitize_float($float) -- input float, returns ONLY the float (no
extraneous characters)

:\* sanitize($input, $flags) -- input any variable, performs
sanitization functions specified in flags. flags can be bitwise
combination of PARANOID, SQL, SYSTEM, HTML, INT, FLOAT, LDAP, UTF8

## Authors

Gavin Zuchlinski, Jamie Pratt \[jpratt at norwich dot edu\], Hokkaido

## Ideas

The PHP Filters are made public so that you can extend them and give
back improvements to the community. The original authors would rank
these as the highest priority suggestions, other suggestions are also
below. If you make changes, please be sure to share your improvements
and mail <owasp@owasp.org> with the code and all details of
improvements. The license requires this but your karma far outweighs
that anyway \!

## Download

You can download the code to this tool at
<http://sourceforge.net/project/showfiles.php?group_id=64424&package_id=106757>

[Category:OWASP Validation
Project](Category:OWASP_Validation_Project "wikilink")