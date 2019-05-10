# Main

<div style="position:absolute;top:-5555px">

O-Saft - check for SSL connection, certificate and ciphers(this text to
make crawlers happy;-)

</div>

<div style="width:100%;height:90px;border:0,margin:0;overflow: hidden;">

![_lab_big.jpg](_lab_big.jpg "_lab_big.jpg")

</div>

<table>
<tbody>
<tr class="odd">
<td><p>valign="top" style="border-right: 1px dotted gray;padding-right:25px;"</p></td>
<td><h2 id="o_saft">O-Saft</h2>
<dl>
<dt>OWASP SSL advanced forensic tool / OWASP SSL audit for testers</dt>

</dl>
<p>O-Saft is an easy to use tool to show informations about SSL certificate and tests the SSL connection according given list of ciphers and various SSL configurations.</p>
<p>It's designed to be used by penetration testers, security auditors or server administrators. The idea is to show the important informations or the special checks with a simple call of the tool. However, it provides a wide range of options so that it can be used for comprehensive and special checks by experienced people.</p>
<p>O-Saft is a command-line tool, so it can be used offline and in closed environments. There is also a GUI based on Tcl/Tk. However, it can simply be turned into an online CGI-tool (please read documentation first).</p>
<h4 id="introduction">Introduction</h4>
<dl>
<dt>Quick Installation:</dt>

</dl>
<ul>
<li>Download and unpack <em>o-saft.tgz</em> (Stable Release)</li>
<li>to run <em>o-saft</em>: Ensure that following perl modules (and their dependencies) are installed</li>
</ul>
<dl>
<dt></dt>
<dd>      <em>IO::Socket::INET</em>, <em>IO::Socket::SSL</em>, <em>Net::SSLeay</em>
</dd>
<dd>      <em>Net::SSLinfo</em>, <em>Net::SSLhello</em> (which are part of the tarball)
</dd>
</dl>
<ul>
<li>read and (re-)move <em>o-saft-README</em></li>
<li>Show help</li>
</ul>
<dl>
<dt></dt>
<dd><em>o-saft --help=commands</em>
</dd>
<dd><em>o-saft --help</em>
</dd>
</dl>
<ul>
<li>Start</li>
</ul>
<dl>
<dt></dt>
<dd><em>o-saft +info your.tld</em>
</dd>
<dd><em>o-saft +check your.tld</em>
</dd>
<dd><em>o-saft +quick your.tld</em>
</dd>
<dd><em>o-saft +cipherall your.tld</em>
</dd>
<dd><em>o-saft +cipherall --starttls=pop3 pop3.your.tld:110</em>
</dd>
<dd><em>o-saft +info mail.tld:25 --starttls</em>
</dd>
</dl>
<ul>
<li>to run the optional <em>checkAllCiphers</em> (tiny program to check solely ciphers, like command '+cipherall'): It usually does not need any perl module to be additionally installed</li>
</ul>
<dl>
<dt></dt>
<dd>      <em>Socket</em> (should be part of your perl installation)
</dd>
<dd>      <em>Net::SSLhello</em> (which is part of the tarball)
</dd>
<dd>      <em>NET::DNS</em> (only needed, if option '--mx' is used)
</dd>
</dl>
<ul>
<li>Start</li>
</ul>
<dl>
<dt></dt>
<dd><em>checkAllCiphers your.tld</em>
</dd>
<dd><em>checkAllCiphers --starttls=pop3 pop3.your.tld:110</em>
</dd>
<dd><em>checkAllCiphers --mx your.tld:25 --starttls=smtp</em>
</dd>
</dl>
<ul>
<li>Simple GUI</li>
</ul>
<dl>
<dt></dt>
<dd><em>o-saft.tcl</em>
</dd>
<dd><em>o-saft.tcl your.tld</em>
</dd>
</dl>
<h4 id="description">Description</h4>
<p>The main idea is to have a tool which works on common platforms and can simply be automated.</p>
<dl>
<dt>In a Nutshell:</dt>

</dl>
<p>:* show SSL connection details</p>
<p>:* show certificate details</p>
<p>:* check for supported ciphers</p>
<p>:* check for ciphers provided in your own libssl.so and libcrypt.so</p>
<p>:* check for ciphers without any dependency to a library (+cipherall)</p>
<p>:* checks the server's priority for ciphers (+cipherall)</p>
<p>:* check for special HTTP(S) support (like SNI, HSTS, certificate pinning)</p>
<p>:* check for protections against attacks (BEAST, CRIME, DROWN, FREAK, Heartbleed, Lucky 13, POODLE, RC4 Bias, Sweet32 ...)</p>
<p>:* check the length of Diffie Hellman Parameters by the cipher (+cipherall needs option '--experimental')</p>
<p>:* may check for a single attribute</p>
<p>:* may check multiple targets at once</p>
<p>:* can be scripted (headless or as CGI)</p>
<p>:* should work on any platform (just needs perl, openssl optional)</p>
<p>:* can be used in CI / CD environments</p>
<p>:* output format can be customized</p>
<p>:* various trace and debug options to hunt unusual connection problems</p>
<p>:* supports STARTTLS for various protocols like (SMTP, POP3, IMAP, LDAP, RDP, XMPP, IRC (experimental) ...),[without options using openssl]<br />
  slows down to prevent blockades of requests due to too much connections (supported for some protocols like SMTP)</p>
<p>:* Proxy is supported (besides commands using openssl)</p>
<p>:* check of STARTTLS/SMTP for all servers of a MX Resource Record (e.g. <em>checkAllCiphers --mx your.tld:25 --starttls=smtp</em>)</p>
<p>:* checkAllCiphers.pl and '+cipherall' support DTLS for '--experimental' use (if records are *not* fragmented)</p>
<h2 id="new_features_of_test_version">New Features of Test Version</h2>
<dl>
<dt>Quick Installation (test version):</dt>

</dl>
<ul>
<li>Download and unpack: <em>master.zip</em></li>
<li>Start <em>INSTALL.sh</em> (if you want:)</li>
<li>Enjoy new functionality:</li>
</ul>
<p>:* --starttls='CUSTOM' to customize your own STARTTLS sequence including error handling, see help for '--starttls_phase1..5' and '--starttls_error1..3'</p>
<p>:* '+cipherraw' and 'checkAllCiphers.pl' changed bahavior to check sni (now the default is to use solely sni &gt;=tls1,<br />
new option --togglesni tests without and with sni in one call</p>
<p>:* checkAllCiphers.pl/+cipherall: shows the length of dh_parameter for ciphers with DHE and DH_anon, shows the elliptic curve that the server prefers for ECDHE (independant from openssl)</p>
<p>:* checkAllCiphers.pl/+cipherall: support of fagmented messages reassembling SSL/TLS-records</p>
<ul>
<li>please give us feedback via the <a href="https://lists.owasp.org/mailman/listinfo/o-saft">mailinglist</a></li>
</ul></td>
<td><p>valign="top" style="padding-left:25px;width:200px;border-right: 1px dotted gray;padding-right:25px;"</p></td>
<td><h2 id="what_is_o_saft">What is O-Saft?</h2>
<p>O-Saft provides:</p>
<ul>
<li>SSL connection details</li>
<li>certificate details</li>
<li>full cipher check</li>
<li>special HTTP(s) checks</li>
<li>check for SSL vulnerabilities</li>
<li>can be scripted</li>
<li>platfrom independent</li>
<li>customizable output</li>
<li>supports STARTTLS and Proxy (for most commands)</li>
</ul>
<h2 id="screen_shots">Screen Shots</h2>
<p>-- code stolen from generated page and improved 9/2016</p>
<div class="thumbcaption">
<div class="magnify">
<p><a href="/index.php/File:O-Saft_cipherCLI.png" class="internal" title="Enlarge"><img src="/File:O-Saft_cipherCLI.png" width="15" height="11" alt="O-Saft +cipher ..." /></a></p>
</div>
<p>O-Saft +cipher ...</p>
</div>
<p>--&gt;</p>
<p>-- original wiki code 9/2016 <img src="O-Saft_cipherCLI.png" title="fig:O-Saft_cipherCLI.png" alt="O-Saft_cipherCLI.png" /> --&gt;</p>
<h2 id="documentation">Documentation</h2>
<ul>
<li><a href="O-Saft/Documentation" title="wikilink">help/man page</a></li>
</ul>
<h2 id="presentations">Presentations</h2>
<ul>
<li>03.04.2015 O-Saft Workshop at <u><a href="https://sites.google.com/view/bsidesmunich2017">BSides Munich 2017</a></u></li>
</ul>
<ul>
<li>Workshop <u>[<a href="http://www.it-security-konferenz.de/programm.html#workshop3%7C3">http://www.it-security-konferenz.de/programm.html#workshop3|3</a>. Kölner IT-Security-Konferenz]</u></li>
<li>17.03.2016 <u><a href="BeNeLux_OWASP_Day_2016" title="wikilink">OWASP BeNeLux Day 2016</a></u>, Luxembourg</li>
</ul>
<dl>
<dt></dt>
<dd>There will be a training <u><a href="BeNeLux_OWASP_Day_2016#Trainingday" title="wikilink">O-Saft - TLS/SSL in Practice</a></u>.
</dd>
</dl>
<ul>
<li>20.05.2015 <u><a href="https://2015.appsec.eu/">AppSecEU 2015</a></u>, Amsterdam</li>
</ul>
<dl>
<dt></dt>
<dd>There will be a training <u><a href="http://2015.appsec.eu/trainings/#train4">TLS/SSL in Practice</a></u> which in particular covers O-Saft.
</dd>
</dl>
<p>-- wenn wir eine bessere Beschreibung brauchen:</p>
<p><code>    </code><a href="http://appseceurope2014.sched.org/event/0e316b9ea5c28375dcc8fd41baedd481"><code>http://appseceurope2014.sched.org/event/0e316b9ea5c28375dcc8fd41baedd481</code></a></p>
<p>--&gt;</p>
<ul>
<li>09.12.2014 Presentation '' Richtig verschlüsseln mit SSL/TLS'' at <u><a href="German_OWASP_Day_2014" title="wikilink">German OWASP Day 2014</a></u>, program see <u><a href="German_OWASP_Day_2014/Programm" title="wikilink">here</a></u></li>
<li><u><a href="https://2014.appsec.eu/">AppSecEU 2014</a></u>, Cambridge</li>
</ul>
<dl>
<dt></dt>
<dd>There will be a training <u><a href="http://appseceurope2014.sched.org/event/0e316b9ea5c28375dcc8fd41baedd481">TLS/SSL in Practice</a></u> which in particular covers O-Saft. For <u><a href="http://appseceurope2014.sched.org/">schedule see here</a></u>.
</dd>
</dl>
<ul>
<li>Vortrag beim German OWASP Day 2014: <u><a href="Media:Richtig_verschluesseln_mit_SSL+TLS_-_Achim_Hoffmann+Torsten_Gigler.pdf" title="wikilink">Richtig verschlüsseln mit SSL/TLS</a></u></li>
<li>Vortrag beim Münchner OWASP-Stammtisch: <u><a href="Media:SSL-in-der-Praxis_OWASP-Stammtisch-Muenchen.pdf‎" title="wikilink">Überblick über aktuelle Angriffsmöglichkeiten auf HTTPS / SSL</a></u> (enthält auch ein paar Beispiele mit o-saft)</li>
</ul>
<p><small>(These presentations are in German)</small></p>
<h2 id="project_leader">Project Leader</h2>
<p><a href="User:Achim" title="wikilink">Achim</a> Hoffmann</p>
<h2 id="licensing">Licensing</h2>
<p>OWASP O-Saft is free to use. It is licensed under the GPL v2 license.</p>
<h2 id="related_projects">Related Projects</h2>
<h2 id="github">Github</h2>
<ul>
<li><u><a href="https://github.com/OWASP/O-Saft">https://github.com/OWASP/O-Saft</a></u></li>
</ul>
<h2 id="ohloh">Ohloh</h2>
<ul>
<li><u><a href="https://www.ohloh.net/p/O-Saft">https://www.ohloh.net/p/O-Saft</a></u></li>
</ul></td>
<td><p>valign="top" style="padding-left:25px;width:200px;"</p></td>
<td><h2 id="quick_download">Quick Download</h2>
<ul>
<li><strong>Stable Release (19.01.19)</strong>: <u><a href="https://github.com/OWASP/O-Saft/archive/19.01.19.tar.gz">o-saft.tgz</a></u></li>
<li>more see <a href="#Change_Log" title="wikilink">#Change Log</a></li>
</ul>
<h2 id="docker">Docker</h2>
<p>A Docker Container can be found at <u><a href="https://hub.docker.com/r/owasp/o-saft/">https://hub.docker.com/r/owasp/o-saft/</a></u></p>
<h2 id="news_and_events">News and Events</h2>
<ul>
<li>[12. - 16.06.17] <u><a href="https://owaspsummit.org/Working-Sessions/Owasp-Projects/O-Saft.html">O-Saft Track</a></u> (at OWASP Summit, London)</li>
<li><strong>2013 Top Security Tools</strong></li>
</ul>
<dl>
<dt></dt>
<dd>thanks for voting <u><a href="http://www.toolswatch.org/2013/12/2013-top-security-tools-as-voted-by-toolswatch-org-readers/">O-Saft as #10 best security tools 2013</a></u>
</dd>
</dl>
<h2 id="in_print_media">In Print / Media</h2>
<p>Find a OWASP 24/7 podcast about the tool <a href="http://trustedsoftwarealliance.com/2014/07/01/achim-hoffman-and-the-o-saft-project-for-scanning-ssl-connections/">here</a>.</p>
<h2 id="classifications">Classifications</h2>
<table>
<tbody>
<tr class="odd">
<td><p>align="center" valign="top" width="50%" rowspan="2"</p></td>
<td><figure>
<img src="Owasp-labs-trans-85.png" title="Owasp-labs-trans-85.png" alt="Owasp-labs-trans-85.png" /><figcaption>Owasp-labs-trans-85.png</figcaption>
</figure></td>
<td><p>align="center" valign="top" width="50%"</p></td>
<td><figure>
<img src="Owasp-builders-small.png" title="Owasp-builders-small.png" alt="Owasp-builders-small.png" /><figcaption>Owasp-builders-small.png</figcaption>
</figure></td>
</tr>
<tr class="even">
<td><p>align="center" valign="top" width="50%"</p></td>
<td><figure>
<img src="Owasp-defenders-small.png" title="Owasp-defenders-small.png" alt="Owasp-defenders-small.png" /><figcaption>Owasp-defenders-small.png</figcaption>
</figure></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>colspan="2" align="center"</p></td>
<td><figure>
<img src="Cc-button-y-sa-small.png" title="Cc-button-y-sa-small.png" alt="Cc-button-y-sa-small.png" /><figcaption>Cc-button-y-sa-small.png</figcaption>
</figure></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>colspan="2" align="center"</p></td>
<td><figure>
<img src="Project_Type_Files_TOOL.jpg" title="Project_Type_Files_TOOL.jpg" alt="Project_Type_Files_TOOL.jpg" /><figcaption>Project_Type_Files_TOOL.jpg</figcaption>
</figure></td>
<td></td>
<td></td>
</tr>
</tbody>
</table></td>
</tr>
</tbody>
</table>

# FAQs

  - FAQs

<!-- end list -->

  - Where can I get missing Perl-Modules?
    This depends on your OS and Perl installation, but just try *cpan
    <Module-Name>*, e.g. *cpan Net:DNS*

:\* I am connected to the internet via a Proxy
open the cpan-shell using 'cpan' and configure your proxy settings: 'o
conf init /proxy/'

:\* I can not download the requested files (the proxy needs
authentication)
run 'cpan <Module-Name>' several times, read the error messages and copy
the requested files manually to the paths (without any additional
temporary extension of the name),
e.g. http://www.cpan.org/authors/01mailrc.txt.gz =\>
<Your Program Path>/cpan/sources/authors/01mailrc.txt.gz

  - I get the Error "invalid SSL_version specified at
    .../perl/vendor/lib/IO/Socket/SSL.pm line ..."

:\* add options *--notlsv13 --nodtlsv1*, e.g. *perl o-saft.pl +info
your.tld --notlsv13 --nodtlsv1*

:\* use *+cipherall* to check the ciphers for all protocols

  - My local SSL libraries do \*not\* support legacy Protocols like
    SSLv2, SSLv3 or legacy Ciphers

:\* use *o-saft.pl* for all protocols that are supported by your local
computer

:\* use *o-saft.pl +cipherall* (or 'checkAllCiphers.pl') to get the
ciphers for the missing protocols, or recompile 'Net::SSLeay' and/or
*openssl* to support more protocols and ciphers, see [Documentation
INSTALLATION](O-Saft/Documentation#INSTALLATION "wikilink") for details

  - I can not use the latest features of the test (experimental) version

:\* Please verify that you downloaded and unpacked the
['master.zip'-Archive](https://github.com/OWASP/O-Saft/archive/master.zip)

:\* some new functions are protected by the option *--experimental*,
please add it to your command (and take care what happens)

  - o-saft.pl seems to hang

<!-- end list -->

  -
    try one or all of following options (see [Documentation Performance
    Problems](O-Saft/Documentation#Performance_Problems "wikilink"));
      - *--no-dns* *-no-http* *--no-cert* *--no-sni* *--no-openssl*

# Acknowledgements

  - Acknowledgements

## Volunteers

O-Saft is developed by from the contributions of OWASP members. The
primary contributors to date have been:

  -
## Repository

O-Saft's source code can be found at <https://github.com/OWASP/O-Saft> .

The latest stable tarball is
<https://github.com/OWASP/O-Saft/raw/master/o-saft.tgz>

# Road Map and Getting Involved

  - Road Map

<https://www.owasp.org/index.php/Projects/O-Saft/Roadmap>

  - Involvement in the development and promotion of O-Saft is actively
    encouraged\!

You do not have to be a security expert in order to contribute.
Contacts:

  - mailto: Achim at owasp dot org
  - [Mailinglist](https://lists.owasp.org/mailman/listinfo/o-saft)

Some of the ways you can help:

  - Quality assurance: simply test O-Saft and report defects and strange
    responses of servers
  - Give some ideas how to implement scoring
  - Need help in implementing

\--

:\* SSL for other protocols using STARTTLS, ...
(currently, February 2015, we have STARTTLS functionality for LDAP,
IMAP, POP3, SMTP, RDP, FTP, XMPP,...) --\>

:\* authentication for proxies (BASIC, NTLM) -- done 12/2015

:\* to check the size of Diffie Hellmann Parameters --\>

:\* check for more SSL/TLS-Extensions (including obsolete ones)

:\* check for more vulnerabilities

:\* check the full certificate chain -- don't include legacy project
template, just for information here

# Project About

} --\>

# Change Log

## Change Log

  - 19.01.2019 Stable Release **19.01.19**;
  - 18.11.2018 Stable Release **18.11.18**;
  - 18.07.2018 Stable Release **18.07.18**; bugfixes, GUI improved,
    docker improved, OCSP Stapling, Makefile\*,
    contrib/build_openssl.sh
  - 16.04.2018 Link Docker Container (pinkstar removed) as docker is
    supported directly

<!-- end list -->

  - 18.01.2018 Docker improved; +sni checks improved; wrapper script
    o-saft; +robot
  - 17.11.2017 Dockerfile improved; +cipherall improved; bugfix: no
    prefered cipher for SSLv2; bit-length for serial number corrected
  - 17.09.2017 docker build openssl with GOST and KRB5 ciphers; bugfix
    for BEAST and sub-domain checks
  - 17.07.2017 docker image supported; performance improved; support
    unresponsive targets
  - 17.04.2017 ALPN and NPN support improved
  - 17.01.2017 checking OCSP improved; certificate verification
    corrected; performance improved
  - 09.09.2016 GUI improved
  - 30.08.2016 Check for new vulnerabilities **DROWN**
  - 30.08.2016 Check for new vulnerabilities **Sweet32**
  - 16.07.2016 new commands (checks) for STS preload, HSTS preload HSTS
    http-equiv
  - 16.05.2016 code quality improved using perlcritic

\-- not yet ready to announce

  - 07.01.2016 simple **check for SLOTH** added (experimental)

\--\>

  - 15.12.2015 Stable Release **15.12.15**
  - 15.11.2015 Stable Release **15.11.15**
  - 08.01.2015, stable release **15.01.07**
  - 05.04.2015, **simple GUI** available
    <u>[o-saft.tcl](https://github.com/OWASP/O-Saft/blob/master/o-saft.tcl)</u>
  - 07.12.2014, stable release **14.12.07**
  - 16.11.2014, stable release **14.11.14**
  - 15.10.2014, check for **Poodle** vulnerability, see test version:
    <u>[master.zip](https://github.com/OWASP/O-Saft/archive/master.zip)</u>
  - 10.04.2014 Heartbleed check, see
    <u><https://github.com/OWASP/O-Saft></u>

## Download

  - Stable Release (18.07.18):
    <u>[o-saft.tgz](https://github.com/OWASP/O-Saft/archive/18.07.18.tar.gz)</u>
  - Stable Release (18.01.18):
    <u>[o-saft.tgz](https://github.com/OWASP/O-Saft/archive/18.01.18.tar.gz)</u>
  - Stable Release (17.11.17):
    <u>[o-saft.tgz](https://github.com/OWASP/O-Saft/archive/17.11.17.tar.gz)</u>
  - Stable Release (17.06.17):
    <u>[o-saft.tgz](https://github.com/OWASP/O-Saft/archive/17.06.17.tar.gz)</u>
  - Stable Release (17.05.17):
    <u>[o-saft.tgz](https://github.com/OWASP/O-Saft/archive/17.05.17.tar.gz)</u>
  - Stable Release (17.04.17):
    <u>[o-saft.tgz](https://github.com/OWASP/O-Saft/archive/17.04.17.tar.gz)</u>
  - Stable Release (17.03.17):
    <u>[o-saft.tgz](https://github.com/OWASP/O-Saft/archive/17.03.17.tar.gz)</u>
  - Stable Release (16.12.16):
    <u>[o-saft.tgz](https://github.com/OWASP/O-Saft/archive/16.12.16.tar.gz)</u>
  - Stable Release (16.11.16):
    <u>[o-saft.tgz](https://github.com/OWASP/O-Saft/archive/16.11.16.tar.gz)</u>
  - Stable Release (16.09.16):
    <u>[o-saft.tgz](https://github.com/OWASP/O-Saft/archive/16.09.16.tar.gz)</u>
  - Stable Release (15.12.15):
    <u>[o-saft.tgz](https://github.com/OWASP/O-Saft/archive/15.12.15.tar.gz)</u>

__NOTOC__ <headertabs />

[Category:OWASP Project](Category:OWASP_Project "wikilink")
[Category:OWASP_Builders](Category:OWASP_Builders "wikilink")
[Category:OWASP_Defenders](Category:OWASP_Defenders "wikilink")
[Category:OWASP_Tool](Category:OWASP_Tool "wikilink")
[Category:SSL](Category:SSL "wikilink")
[Category:Test](Category:Test "wikilink")