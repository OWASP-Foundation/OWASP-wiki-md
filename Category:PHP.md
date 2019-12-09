# Main

<table>
<tbody>
<tr class="odd">
<td><h2 id="about">About</h2>
<p>There are 1.8 billion websites on the internet today. Nearly 80% are powered by the PHP programming language. Freedom, privacy, security, and protection from totalitarianism are not possible if PHP is insecure. This project seeks to be the clearing house for the best ways of protecting PHP websites, apps, and the data they have. Thank you for reading. ​</p>
<h2 id="what_does_php_security_mean">What Does PHP Security Mean?</h2>
<ul>
<li>CONFIG: Is my configuration secure? E.g. am I using the latest version of PHP? How does my PHP.ini file look?</li>
<li>CODEBASE: Is my codebase secure? Am I protecting against SQL injection? Am I protecting against stored XSS attacks?</li>
<li>ARCHITECTURE: is the app designed with security in-mind? Do I have good documentation on securing the app? Do I have brute force protection or MFA as available options?</li>
<li>INFRASTRUCTURE: is my deployment environment secure? E.g. Have I hardened the web server the application runs on?</li>
<li>DEVELOPMENT: Is my development infrastructure secure? E.g. Do I have 2FA on my Github account along with all other developers?</li>
</ul>
<h2 id="what_can_you_learn_here">What Can You Learn Here?</h2>
<ul>
<li>What is the fastest way to secure my legacy PHP application?</li>
<li>What options do I need in my php.ini file for security?</li>
<li>What is the proper way to sanitize data in 2019 with PHP?</li>
<li>How can I check my dependencies for vulnerabilities?</li>
<li>How do you secure the web server running the PHP code?</li>
<li>How does one secure phpmyadmin, MySQL, and Postgres databases?</li>
<li>How can you harden your WordPress or Drupal site?</li>
</ul>
<p>​</p></td>
<td><h2 id="team">Team</h2>
<p>Lead: Dan Ehrlich</p>
<p>Please email dan.ehrlich@owasp.org if you would like to help out.</p>
<p><br />
</p>
<h2 id="meta">Meta</h2>
<p>Last Updated: 01/2019</p>
<p><br />
</p>
<h2 id="other_resources">Other Resources</h2>
<p><a href="https://paragonie.com/blog/2017/12/2018-guide-building-secure-php-software">Ultimate 2018 PHP Security Guide</a><br />
<a href="https://lists.owasp.org/mailman/listinfo/php-project">Mailing List</a><br />
</p>
<h2 id="related_projects">Related Projects</h2>
<ul>
<li><a href="OWASP_Project" title="wikilink">OWASP Project Repository</a></li>
<li><a href="Language" title="wikilink">Languages Repository</a></li>
<li><a href="PHP" title="wikilink">PHP</a></li>
<li><a href="Perl" title="wikilink">Perl</a></li>
<li><a href="Python" title="wikilink">Python</a></li>
<li><a href="JavaScript" title="wikilink">JavaScript</a></li>
<li><a href="C/C++" title="wikilink">C/C++</a></li>
<li><a href="SQL" title="wikilink">SQL, PL/SQL, DB Scripting</a></li>
</ul></td>
</tr>
</tbody>
</table>

# PHP Security Overview

It is not easy to produce a PHP application without security
vulnerabilities. Most application security
[vulnerabilities](:Category:Vulnerability "wikilink") apply to PHP
applications just like other environments.

The goals of this project are to provide information about building,
configuring, deploying, operating, and maintaining secure PHP
applications

  - [PHP Security for
    Developers](PHP_Security_for_Developers "wikilink")
    \* This section covers dangerous calls and common vulnerabilities
    associated with them, such as system() exec(), eval() and so on.
    This section will also cover standard security mechanisms available
    in the standard language, such as cryptography, logging, encryption,
    and error handling. Securing elements of an application, such as
    controllers, business logic, and persistence layers will be covered.
    We'll discuss handling request parameters, encoding, injection, and
    more.
    \* CONFIG
    \* CODEBASE

<!-- end list -->

  - [PHP Security for
    DevSecOps](PHP_Security_for_DevSecOps "wikilink")
    \* How to secure a PHP application when running on the major cloud
    providers. How to secure a PHP application if all you've got is an
    unmanaged Linux server. Harden web server, harden database, and
    various network defenses such as WAFs, GeoIP, and DNSBL.
    \* How to secure the development environment. Do you have control
    over the Source code repository? Are commits signed? How do you know
    which Docker Images to trust? Do you scan containers for
    vulnerabilities?
    \* INFRASTRUCTURE
    \* DEVELOPMENT

<!-- end list -->

  - [PHP Security for Software
    Architects](PHP_Security_for_Software_Architects "wikilink")
    \* Provides information about the design and architectural
    considerations for a PHP web application. Which frameworks to use,
    which frameworks are dead, and using the various FIGs.
    \* ARCHITECTURE

# Pages

## Resources

[Awesome PHP
Security](https://github.com/guardrailsio/awesome-php-security)

[Awesome AppSec](https://github.com/paragonie/awesome-appsec)

[Best 3rd Party PHP Security
Guide](https://paragonie.com/blog/2017/12/2018-guide-building-secure-php-software)

[Secure php.ini
Configuration](https://github.com/danehrlich1/very-secure-php-ini)




## Libraries

[Google PHP recaptcha](https://github.com/google/recaptcha)
[Paragonie Anti-CSRF Library](https://github.com/paragonie/anti-csrf)
[Enhanced BCrypt
Encryption](https://github.com/paragonie/password_lock)
[PHP GnuPG Emailer](https://github.com/paragonie/gpg-mailer)
[PHP CSP Builder](https://github.com/paragonie/csp-builder)




## Documents

[OWASP PHP Top 5](OWASP_PHP_Top_5 "wikilink")




## Legacy Pages

The pages below are from 2005-2014 when this project was maintained by a
different team. These pages have been kept so that no links are broken,
and because there might be certain situations, particularly with
extremely legacy apps, where their use might be appropriate. THere is
great advice below, but be careful, there is also outdated advice as
well.

[PHP Security for
Architects](https://www.owasp.org/index.php/PHP_Security_for_Architects)
[PHP Security for
Developers](https://www.owasp.org/index.php/PHP_Security_for_Developers)
[PHP Security for
Deployers](https://www.owasp.org/index.php/PHP_Security_for_Deployers)

[PHP Configuration Cheat
Sheet](https://www.owasp.org/index.php/PHP_Configuration_Cheat_Sheet)
[PHP CSRF Guard](https://www.owasp.org/index.php/PHP_CSRF_Guard)
[Log Injection](https://www.owasp.org/index.php/Log_Injection)

[OWASP PHP Security
Project](https://www.owasp.org/index.php/Projects/OWASP_PHP_Security_Project)
[OWASP PHP Security Project
Roadmap](https://www.owasp.org/index.php/Projects/OWASP_PHP_Security_Project/Roadmap)

[OWASP RBAC
Project](https://www.owasp.org/index.php/Projects/OWASP_RBAC_Project)
[OWASP VaultDB
Project](https://www.owasp.org/index.php/Projects/OWASP_VaultDB_Project)
[OWASP PHPRBAC
Project](https://www.owasp.org/index.php/OWASP_PHPRBAC_Project)
[OWASP WebGoatPHP](https://www.owasp.org/index.php/WebGoatPHP)


# Related Resources

<table>
<tbody>
<tr class="odd">
<td><h1 id="get_involved">Get involved</h1>
<p>To get involved join the mailing list: <a href="https://lists.owasp.org/mailman/listinfo/owasp-php">OWASP PHP Mailing List</a></p>
<h2 id="mailing_list">Mailing List</h2>
<p><a href="http://lists.owasp.org/mailman/listinfo/php-project">OWASP PHP Project Mailing List</a></p></td>
<td><h2 id="twitter_feed">Twitter Feed</h2>
<p>(none)</p></td>
<td><h2 id="code_repository">Code Repository</h2>
<p>(none)</p></td>
</tr>
</tbody>
</table>



## PHP Projects Mailing Lists

<https://lists.owasp.org/pipermail/owasp_php_security_project/>

<https://lists.owasp.org/pipermail/owasp_phprbac/>



## Related OWASP Resources

[OWASP Project Repository](OWASP_Project "wikilink")

[Languages Repository](Language "wikilink")

[.NET Project](OWASP_.NET_Project "wikilink")

[Ruby Technology Knowledge Base](Ruby "wikilink")

[PHP Technology Knowledge Base](PHP "wikilink")

[Perl Technology Knowledge Base](Perl "wikilink")

[Python Technology Knowledge Base](Python "wikilink")

[JavaScript Technology Knowledge Base](JavaScript "wikilink")

[C/C++ Technology Knowledge Base](C/C++ "wikilink")

[SQL, PL/SQL and DB Scripting Technology Knowledge Base](SQL "wikilink")

# Project Archives

The previous version of this PHP Project home page is archived here:
[OWASP_PHP_Project_Archive_(03.2015)](OWASP_PHP_Project_Archive_\(03.2015\) "wikilink")



__NOTOC__ <headertabs />



[Category:Technology](Category:Technology "wikilink")
[Category:Language](Category:Language "wikilink")