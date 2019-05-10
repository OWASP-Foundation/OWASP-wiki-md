Here we evaluate and compare various LDAP Client APIs to understand how
well they satisfy the [Secure LDAP Client API
Standard](Projects/OWASP_Framework_Security_Project/Secure_LDAP_API_Standard "wikilink").

**NOTE: Both the standard and evaluations below are in a draft state and
are likely to change before formal publication.**

## Overview

<table class="wikitable">

<tr>

<th>

API

</th>

<th>

Grade

</th>

<th>

Documents the Security Risks of LDAP Filter Injection

</th>

<th>

Documents LDAP Bind Authentication Without Filter Queries

</th>

<th>

Provides an LDAP Filter Escape Function

</th>

<th>

Provides LDAP Filter Syntax Templates

</th>

<th>

Provides an Abstract API for LDAP Filter Queries

</th>

<th>

Supports LDAP with StartTLS

</th>

<th>

Supports LDAPS

</th>

<th>

Enables SSL/TLS Certificate Validation by Default

</th>

<th>

Documents the Customization of Trusted Certificate Authorities

</th>

<th>

Documents the Risk of Disabling Certificate Validation

</th>

<th>

Score

</th>

</tr>

<tr>

<td>

[Apache Directory LDAP API
(java)](http://directory.apache.org/api/user-guide/2-basic-ldap-api-usage.html)

</td>

<td>

?

</td>

<td>

NO

</td>

<td>

?

</td>

<td>

NO

</td>

<td>

NO

</td>

<td>

NO

</td>

<td>

?

</td>

<td>

?

</td>

<td>

?

</td>

<td>

?

</td>

<td>

?

</td>

<td>

?

</td>

</tr>

<tr>

<td>

[ColdFusion 10
cfldap](https://helpx.adobe.com/coldfusion/cfml-reference/coldfusion-tags/tags-j-l/cfldap.html)

</td>

<td>

?

</td>

<td>

NO (-2)

</td>

<td>

?

</td>

<td>

NO

</td>

<td>

NO

</td>

<td>

NO

</td>

<td>

?

</td>

<td>

?

</td>

<td>

?

</td>

<td>

?

</td>

<td>

?

</td>

<td>

?

</td>

</tr>

<tr>

<td>

\[<https://msdn.microsoft.com/en-us/library/System.DirectoryServices(v=vs.110>).aspx
.NET 4.5\]

</td>

<td>

?

</td>

<td>

NO

</td>

<td>

?

</td>

<td>

NO

</td>

<td>

NO

</td>

<td>

NO

</td>

<td>

?

</td>

<td>

?

</td>

<td>

?

</td>

<td>

?

</td>

<td>

?

</td>

<td>

?

</td>

</tr>

<tr>

<td>

[Perl
Net::LDAP](http://search.cpan.org/~marschap/perl-ldap/lib/Net/LDAP.pod)

</td>

<td>

?

</td>

<td>

YES

</td>

<td>

?

</td>

<td>

NO

</td>

<td>

NO

</td>

<td>

NO

</td>

<td>

?

</td>

<td>

?

</td>

<td>

?

</td>

<td>

?

</td>

<td>

?

</td>

<td>

?

</td>

</tr>

<tr>

<td>

[PHP 5](http://php.net/manual/en/ref.ldap.php)

</td>

<td>

?

</td>

<td>

NO (-1)

</td>

<td>

?

</td>

<td>

YES

</td>

<td>

NO

</td>

<td>

NO

</td>

<td>

?

</td>

<td>

?

</td>

<td>

?

</td>

<td>

?

</td>

<td>

?

</td>

<td>

?

</td>

</tr>

<tr>

<td>

[python-ldap](http://www.python-ldap.org/)

</td>

<td>

?

</td>

<td>

YES

</td>

<td>

?

</td>

<td>

YES

</td>

<td>

YES

</td>

<td>

NO

</td>

<td>

?

</td>

<td>

?

</td>

<td>

?

</td>

<td>

?

</td>

<td>

?

</td>

<td>

?

</td>

</tr>

</table>

## Notes

  - ColdFusion 10: Besides not warning developers about the risk of LDAP
    Filter injection, [this
    page](http://help.adobe.com/en_US/ColdFusion/10.0/Developing/WSc3ff6d0ea77859461172e0811cbec0eb56-7fe5.html)
    contains an example which is blatantly vulnerable to injection.
    Minus 2 points.

<!-- end list -->

  - PHP 5: Besides not warning developers about the risk of LDAP Filter
    injection, [this
    page](http://php.net/manual/en/function.ldap-search.php) contains an
    example which leads developers a likely injection. Minus 1 point.

## Tickets

TODO: here we keep track of links to bug submissions/feature requests
sent to each API maintainer

### Apache Directory LDAP API (java)

### ColdFusion 10 cfldap

### .NET 4.5

### Perl Net::LDAP

### PHP 5

### python-ldap