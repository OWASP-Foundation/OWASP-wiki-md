<table>
<thead>
<tr class="header">
<th><p>width="700" align="center"</p></th>
<th><p><br />
</p></th>
<th><p>width="500" align="center"</p></th>
<th><p><br />
</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>align="right"</p></td>
<td><figure>
<img src="OWASP_Inactive_Banner.jpg" title="OWASP_Inactive_Banner.jpg" alt="OWASP_Inactive_Banner.jpg" width="800" /><figcaption>OWASP_Inactive_Banner.jpg</figcaption>
</figure></td>
<td><p>align="right"</p></td>
<td></td>
</tr>
</tbody>
</table>

[Click here to return to OWASP Projects
page.](:Category:OWASP_Project "wikilink")
[Click here to see (& edit, if wanted) the
template.](:Project_Information:Webekci "wikilink")

## What is WeBekci?

WeBekci is a web based ModSecurity 2.x management tool. WeBekci is
written in PHP, Its backend is powered by MySQL and the frontend by
XAJAX framework. It is an OWASP Project.

## What is ModSecurity for Apache?

With over 70% of all attacks now carried out over the web application
level, organisations need every help they can get in making their
systems secure. Web application firewalls are deployed to establish an
external security layer that increases security, detects, and prevents
attacks before they reach web applications
[(ModSecurity).](http://www.modsecurity.org)

## Goals

It will remove management overhead of ModSecurity 2.x. You can configure
modsecurity.conf, add special rules and watch system, apache and
modsecurity logs (only guardianlog has been implemented in this
version).

## Features

It covers 90 percent of the ModSecurity 2.x configuration features.
Manual- and GUI-based rule managements are supported. It permits to add
single-argument rules and it covers 70 percent of the action parameters.
It can be used in monitoring system, apache and ModSecurity guardian
logs. As of this version the monitoring utility is rather basic and it
gives some information about the system.

## Future Development

  - **Configuration** : Most of the configuration parameters will be
    managed through the web interface
  - **Rule Generator** : Basic rules will be generated using the web
    interface
  - **Core Rule Integration**: Core rules will be added to the database
    for use
  - **Logging and Reporting**: Apache error log and modsec_audit log
    will be parsed and presented to the user thru the web interface
  - **DB Support** : MySQL

![webekci.gif](webekci.gif "webekci.gif")

## Requirement

  - Platform Linux/Unix,
  - Apache + ModSecurty 2.x
  - Php
  - Mysql

## News

`'''OWASP WeBekci Project Release! - 31 March 2007 '''`

## Installation

Download adress: <http://sourceforge.net/projects/webekci/>

` # tar –zxvf webekci-1.0.tar.gz`
` # mv webekci /usr/local/www/`
` # cd /usr/local/www/webekci`

Primarily, create .htaccess and .htpasswd files. These are required for
WeBekci\`s own. Edit .htaccess file:

` # vi .htaccess `

In the .htaccess file, enter the correct path for the .htpasswd file in
the AuthUserFile line in accordance with your own configuration:

` AuthUserFile /usr/home/bunyamin/.htpasswd`
` AuthType Basic`
` AuthName "Owasp-WeBekci Screet Area"`
` `<LIMIT GET POST>
` require valid-user`
` `</LIMIT>

Now edit .htpasswd file:

` # vi .htpasswd`

If the user name is going to be “webekci” and password “1234”, then
enter:

` webekci:cwc9eWGIM9r5M`

You may enter your own UID and password.

Now, you need define “directory” in the httpd.conf file.

` Alias /webekci/ "/usr/local/www/webekci/"`
` <Directory "/usr/local/www/webekci/">`
`    Options None`
`    AllowOverride All`
`    Order Allow,Deny`
`    Allow from all`
` `</Directory>

Note: If you are using mod_rewrite, then enter “AllowOverride All” so
that .htaccess file can be read. Otherwise enter “AllowOverride None”.

` # apachectl restart`

Make necessary modifications in config.php file. Add the following line:

$config\['modsecurity_conf'\]='/usr/local/etc/apache22/extra/mod_security.conf';

It’s important to create the mod_security.conf file and include its
path to the httpd.conf. Let’s add the following line into your
httpd.conf. Change the path according to your distribution if necessary.

` Include etc/apache22/extra/mod_security.conf`

To give the www user read and write permissions:

` # chown www /usr/local/etc/apache22/extra/mod_security.conf`

Note: www user is the user where apache runs. Please check the the
following entries in httpd.conf:

User www

Group www

Some distributions may have different user and/or group names.

After configuring WeBekci you need to restart apache. Do this with these
sudo configurations: $config\['apache_config_test'\] =
'/usr/local/bin/sudo /usr/local/sbin/httpd -t';

$config\['apache_restart'\]='/usr/local/bin/sudo /usr/local/sbin/httpd
-k restart';

Also alter your config.php according to your distro. Edit sudoers file:

` # vi /usr/local/etc/sudoers`

Enter these lines:

` www ALL=NOPASSWD:/usr/local/sbin/httpd -k restart`
` www ALL=NOPASSWD:/usr/local/sbin/httpd -t`

Now www user can do “config test” and “restart” operations restart
apache without having to enter password.

Please make sure you entered MySQL related changes in your config.php
file; and browse your site and run the install.php file:

<http://www.site.com/webekci/install.php>

Do not forget to delete install.php later..

` # rm install.php`

A reminder: www user must have read-write rights to audit, debug and
guardian log files. For instance, if the Guardian log file has the path
as “/var/log/modsec_guardian.log” , then we need to enter this command:

` # chown www /var/log/modsec_guardian.log`

Now the guardian log can be seen in the program. You have to do chown
for other log files, too.

I express my gratitude to those who helped me with this write-up.

## Project Contributor

The project is lead by \* [Bunyamin Demir](User:Bunyamin "wikilink")
(bunyamin\~owasp.org)

Mail list: owasp-webekci\~lists.owasp.org

## Documents

ModSecurity 2.1.0 Reference documentation
[(English)](http://www.modsecurity.org/documentation/modsecurity-apache/2.1.0/modsecurity2-apache-reference.pdf)
[(Turkish)](http://www.modsecurity.org/documentation/contributed/ModSecurity_2.1.0_Turkish.pdf)

WeBekci documentation
[(English)](Media:Owasp-webekci-1.0_en.doc "wikilink")
[(Turkish)](Media:Owasp-webekci-1.0_tr.doc "wikilink")

## Project Sponsor

If you would like to help WeBekci project development, feel free to
contact the project leader.

[WeBekci Project](Category:OWASP_Project "wikilink") [WeBekci
Project](Category:OWASP_Project "wikilink")