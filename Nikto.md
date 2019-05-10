## Description

Nikto is an Open Source (GPL) web server scanner which performs
comprehensive tests against web servers for multiple items, including
over 3500 potentially dangerous files/CGIs, versions on over 900
servers, and version specific problems on over 250 servers. Scan items
and plugins are frequently updated and can be automatically updated (if
desired).

Nikto is not designed as an overly stealthy tool. It will test a web
server in the shortest timespan possible, and it's fairly obvious in log
files. However, there is support for LibWhisker's anti-IDS methods in
case you want to give it a try (or test your IDS system).

Not every check is a security problem, though most are. There are some
items that are "info only" type checks that look for items that may not
have a security flaw, but the webmaster or security engineer may not
know are present on the server. These items are usually marked
appropriately in the information printed. There are also some checks for
unknown items which have been seen scanned for in log files.

## Features

`   * Uses rfp's LibWhisker as a base for all network funtionality`
`   * Main scan database in CSV format for easy updates`
`   * Fingerprint servers via favicon.ico files`
`   * Determines "OK" vs "NOT FOUND" responses for file type, if possible`
`   * Determines CGI directories for each server, if possible`
`   * Switch HTTP versions as needed so that the server understands requests properly`
`   * SSL Support (Unix with OpenSSL or maybe Windows with ActiveState's Perl/NetSSL)`
`   * Output to file in plain text, HTML or CSV`
`   * Plugin support (standard PERL)`
`   * Checks for outdated server software`
`   * Proxy support (with authentication)`
`   * Host authentication (Basic)`
`   * Watches for "bogus" OK responses`
`   * Attempts to perform educated guesses for Authentication realms`
`   * Captures/prints any Cookies received`
`   * Mutate mode to "go fishing" on web servers for odd items`
`   * Builds Mutate checks based on robots.txt entries (if present)`
`   * Scan multiple ports on a target to find web servers (can integrate nmap for speed, if available)`
`   * Multiple IDS evasion techniques`
`   * Users can add a custom scan database`
`   * Supports automatic code/check updates (with web access)`
`   * Multiple host/port scanning (scan list files)`
`   * Username guessing plugin via the cgiwrap program and Apache ~user methods `

## Version 2

Nikto version 2 contains many enhancements over the first version. Some
of the major new features include:

`   * Fingerprinting web servers via favicon.ico files`
`   * 404 checking for each file type`
`   * Enhanced false positive reduction via multiple methods: headers, page content, and content hashing`
`   * Scan tuning to include or exclude entire classes of vulnerability checks`
`   * Expanded scan database can have multiple positive or negative triggers, to allow AND/OR/NOT for flexible checks`
`   * Uses LibWhisker 2, which has its own long list of enhancements`
`   * A "single" scan mode that allows you to craft an HTTP request by hand`
`   * Updated and greatly enhanced documentation`
`   * Authorization guessing handles any directory, not just the root directory`
`   * New HTML report`
`   * Basic template engine so that HTML reports can be easily customized`
`   * An experimental knowledge base for scans, which will allow regenerated reports and retests (future)`
`   * ... and countless tweaks/bugfixes/optimizations ... `

## Download

<http://cirt.net/nikto/nikto-current.tar.gz>

## NiktoFE

Nikto was ported to GUI version by Aung Khant (http://yehg.net). You can
get it from <http://yehg.net/lab/pr0js/files.php/NiktoFEv01.zip>

## References

<http://cirt.net/nikto2>

[Category:Non-OWASP Open Tool](Category:Non-OWASP_Open_Tool "wikilink")