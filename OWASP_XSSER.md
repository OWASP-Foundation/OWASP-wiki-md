

-----

<table>
<thead>
<tr class="header">
<th><p>colspan="8" align="center" style="background:#4058A0; color:white"</p></th>
<th><p><font color="white"><strong>OWASP XSSer Project</strong><br />
Web application vulnerability scanner / Security auditor</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>style="width:15%; background:#7B8ABD" align="center"</p></td>
<td><p><strong>Project Name</strong></p></td>
</tr>
<tr class="even">
<td><p>style="width:15%; background:#7B8ABD" align="center"</p></td>
<td><p><strong>Short Project Description</strong></p></td>
</tr>
<tr class="odd">
<td><p>style="width:15%; background:#7B8ABD" align="center"</p></td>
<td><p><strong>Key Project Information</strong></p></td>
</tr>
</tbody>
</table>

<table>
<thead>
<tr class="header">
<th><p>align="center" style="background:#7B8ABD; color:white"</p></th>
<th><p><font color="black"><strong>Last Package</strong></p></th>
<th><p>align="center" style="background:#7B8ABD; color:white"</p></th>
<th><p><font color="black"><strong>Main Links</strong></p></th>
<th><p>align="center" style="background:#7B8ABD; color:white"</p></th>
<th><p><font color="black"><strong>Related Documentation</strong></p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>style="width:29%; background:#cccccc" align="center"</p></td>
<td><p><a href="https://xsser.03c8.net/xsser/xsser_1.7-2.tar.gz"><strong>XSSer "ZiKA-47 Swarm!" (v1.7-2b)</strong></a></p></td>
<td><p>style="width:42%; background:#cccccc" align="center"</p></td>
<td><p><a href="https://xsser.03c8.net"><strong>Official site</strong></a><br />
<a href="https://github.com/epsylon/xsser"><strong>Code Repository</strong></a></p></td>
<td><p>style="width:29%; background:#cccccc" align="center"</p></td>
<td><p>Paper(2009): 'XSS for fun and profit':<br />
<a href="https://xsser.03c8.net/xsser/XSS_for_fun_and_profit_SCG09_(english).pdf"><strong>English</strong></a> - <a href="https://xsser.03c8.net/xsser/XSS_for_fun_and_profit_SCG09_(spanish).pdf"><strong>Spanish</strong></a></p></td>
</tr>
</tbody>
</table>

# Current Version

<table>

<tr>

<td>

![Image:Xsser-zika-banner.png](Xsser-zika-banner.png
"Image:Xsser-zika-banner.png")
XSSer v1.7-2b ("The Mosquito: <u>ZiKA-47 Swarm</u>")

  - Download (.tar.gz) source code:
    [**XSSer_v1.7-2.tar.gz**](https://xsser.03c8.net/xsser/xsser_1.7-2.tar.gz)
  - Download (.zip) source code:
    [**XSSer_v1.7-2.zip**](https://xsser.03c8.net/xsser/xsser_1.7-2.zip)
  - Or update your copy directly from the XSSer -Github- repository:

$ git clone <https://github.com/epsylon/xsser>

</ul>

This version include more features on the GTK+ interface: <b>xsser
--gtk</b>

</td>

</tr>

<tr>

<td>

<table>

<tr>

<td>

![Image:Xsser-zika-gui.png](Xsser-zika-gui.png
"Image:Xsser-zika-gui.png")
[**+ Click for
Zoom**](https://www.owasp.org/images/f/f7/Xsser-zika-gui.png)

</td>

<td>

![Image:Xsser-zika-tor.png](Xsser-zika-tor.png
"Image:Xsser-zika-tor.png")
[**+ Click for
Zoom**](https://www.owasp.org/images/b/b1/Xsser-zika-tor.png)

</td>

</tr>

<tr>

<td>

![Image:Xsser-zika-map.png](Xsser-zika-map.png
"Image:Xsser-zika-map.png")
[**+ Click for
Zoom**](https://www.owasp.org/images/7/74/Xsser-zika-map.png)

</td>

<td>

![Image:Xsser-zika-spidering.png](Xsser-zika-spidering.png
"Image:Xsser-zika-spidering.png")
[**+ Click for
Zoom**](https://www.owasp.org/images/3/38/Xsser-zika-spidering.png)

</td>

</tr>

</table>

</td>

</tr>

</table>

# How it works


![Image:Xsser-url-schema.png](Xsser-url-schema.png
"Image:Xsser-url-schema.png")
[**+ Click for
Zoom**](https://www.owasp.org/images/f/f9/Xsser-url-schema.png)

\=Installation=

XSSer runs on many platforms. It requires Python and the following
libraries:


`   - python-pycurl - Python bindings to libcurl`
`    - python-xmlbuilder - create xml/(x)html files - Python 2.x`
`    - python-beautifulsoup - error-tolerant HTML parser for Python`
`    - python-geoip - Python bindings for the GeoIP IP-to-country resolver library`


On Debian-based systems (ex: Ubuntu), run:


`   $ sudo apt-get install python-pycurl python-xmlbuilder python-beautifulsoup python-geoip`

# Options

xsser \[OPTIONS\] \[--all <url> |-u <url> |-i <file> |-d <dork>
(options)|-l \] \[-g <get> |-p <post> |-c <crawl> (options)\]
\[Request(s)\] \[Checker(s)\] \[Vector(s)\] \[Anti-antiXSS/IDS\]
\[Bypasser(s)\] \[Technique(s)\] \[Final Injection(s)\] \[Reporting\]
{Miscellaneous}

` --version             show program's version number and exit`
` -h, --help            show this help message and exit`
` -s, --statistics      show advanced statistics output results`
` -v, --verbose         active verbose mode output results`
` --gtk                 launch XSSer GTK Interface`
` --wizard              start Wizard Helper!`

` *Special Features*:`
`   You can set Vector(s) and Bypasser(s) to build complex scripts for XSS`
`   code embedded. XST allows you to discover if target is vulnerable to`
`   'Cross Site Tracing' [CAPEC-107]:`

`   --imx=IMX           IMX - Create an image with XSS (--imx image.png)`
`   --fla=FLASH         FLA - Create a flash movie with XSS (--fla movie.swf)`
`   --xst=XST           XST - Cross Site Tracing (--xst http(s)://host.com)`

` *Select Target(s)*:`
`   At least one of these options must to be specified to set the source`
`   to get target(s) urls from:`

`   --all=TARGET        Automatically audit an entire target`
`   -u URL, --url=URL   Enter target to audit`
`   -i READFILE         Read target(s) urls from file`
`   -d DORK             Search target(s) using a query (ex: 'news.php?id=')`
`   -l                  Search from a list of 'dorks'`
`   --De=DORK_ENGINE    Use this search engine (default: yahoo)`
`   --Da                Search massively using all search engines`

` *Select type of HTTP/HTTPS Connection(s)*:`
`   These options can be used to specify which parameter(s) we want to use`
`   as payload(s) to inject:`

`   -g GETDATA          Send payload using GET (ex: '/menu.php?q=')`
`   -p POSTDATA         Send payload using POST (ex: 'foo=1&bar=')`
`   -c CRAWLING         Number of urls to crawl on target(s): 1-99999`
`   --Cw=CRAWLER_WIDTH  Deeping level of crawler: 1-5 (default 3)`
`   --Cl                Crawl only local target(s) urls (default TRUE)`

` *Configure Request(s)*:`
`   These options can be used to specify how to connect to the target(s)`
`   payload(s). You can choose multiple:`

`   --cookie=COOKIE     Change your HTTP Cookie header`
`   --drop-cookie       Ignore Set-Cookie header from response`
`   --user-agent=AGENT  Change your HTTP User-Agent header (default SPOOFED)`
`   --referer=REFERER   Use another HTTP Referer header (default NONE)`
`   --xforw             Set your HTTP X-Forwarded-For with random IP values`
`   --xclient           Set your HTTP X-Client-IP with random IP values`
`   --headers=HEADERS   Extra HTTP headers newline separated`
`   --auth-type=ATYPE   HTTP Authentication type (Basic, Digest, GSS or NTLM)`
`   --auth-cred=ACRED   HTTP Authentication credentials (name:password)`
`   --proxy=PROXY       Use proxy server (tor: `<http://localhost:8118>`)`
`   --ignore-proxy      Ignore system default HTTP proxy`
`   --timeout=TIMEOUT   Select your timeout (default 30)`
`   --retries=RETRIES   Retries when the connection timeouts (default 1)`
`   --threads=THREADS   Maximum number of concurrent HTTP requests (default 5)`
`   --delay=DELAY       Delay in seconds between each HTTP request (default 0)`
`   --tcp-nodelay       Use the TCP_NODELAY option`
`   --follow-redirects  Follow server redirection responses (302)`
`   --follow-limit=FLI  Set limit for redirection requests (default 50)`

` *Checker Systems*:`
`   These options are useful to know if your target is using filters`
`   against XSS attacks:`

`   --hash              send a hash to check if target is repeating content`
`   --heuristic         discover parameters filtered by using heuristics`
`   --discode=DISCODE   set code on reply to discard an injection`
`   --checkaturl=ALT    check reply using: alternative url -> Blind XSS`
`   --checkmethod=ALTM  check reply using: GET or POST (default: GET)`
`   --checkatdata=ALD   check reply using: alternative payload`
`   --reverse-check     establish a reverse connection from target to XSSer to`
`                       certify that is 100% vulnerable (recommended!)`

` *Select Vector(s)*:`
`   These options can be used to specify injection(s) code. Important if`
`   you don't want to inject a common XSS vector used by default. Choose`
`   only one option:`

`   --payload=SCRIPT    OWN  - Inject your own code`
`   --auto              AUTO - Inject a list of vectors provided by XSSer`

` *Anti-antiXSS Firewall rules*:`
`   These options can be used to try to bypass specific WAF/IDS products.`
`   Choose only if required:`

`   --Phpids0.6.5       PHPIDS (0.6.5) [ALL]`
`   --Phpids0.7         PHPIDS (0.7) [ALL]`
`   --Imperva           Imperva Incapsula [ALL]`
`   --Webknight         WebKnight (4.1) [Chrome]`
`   --F5bigip           F5 Big IP [Chrome + FF + Opera]`
`   --Barracuda         Barracuda WAF [ALL]`
`   --Modsec            Mod-Security [ALL]`
`   --Quickdefense      QuickDefense [Chrome]`

` *Select Bypasser(s)*:`
`   These options can be used to encode vector(s) and try to bypass`
`   possible anti-XSS filters. They can be combined with other techniques:`

`   --Str               Use method String.FromCharCode()`
`   --Une               Use Unescape() function`
`   --Mix               Mix String.FromCharCode() and Unescape()`
`   --Dec               Use Decimal encoding`
`   --Hex               Use Hexadecimal encoding`
`   --Hes               Use Hexadecimal encoding with semicolons`
`   --Dwo               Encode IP addresses with DWORD`
`   --Doo               Encode IP addresses with Octal`
`   --Cem=CEM           Set different 'Character Encoding Mutations'`
`                       (reversing obfuscators) (ex: 'Mix,Une,Str,Hex')`

` *Special Technique(s)*:`
`   These options can be used to inject code using different XSS`
`   techniques. You can choose multiple:`

`   --Coo               COO - Cross Site Scripting Cookie injection`
`   --Xsa               XSA - Cross Site Agent Scripting`
`   --Xsr               XSR - Cross Site Referer Scripting`
`   --Dcp               DCP - Data Control Protocol injections`
`   --Dom               DOM - Document Object Model injections`
`   --Ind               IND - HTTP Response Splitting Induced code`
`   --Anchor            ANC - Use Anchor Stealth payloader (DOM shadows!)`

` *Select Final injection(s)*:`
`   These options can be used to specify the final code to inject on`
`   vulnerable target(s). Important if you want to exploit 'on-the-wild'`
`   the vulnerabilities found. Choose only one option:`

`   --Fp=FINALPAYLOAD   OWN    - Exploit your own code`
`   --Fr=FINALREMOTE    REMOTE - Exploit a script -remotely-`
`   --Doss              DOSs   - XSS (server) Denial of Service`
`   --Dos               DOS    - XSS (client) Denial of Service`
`   --B64               B64    - Base64 code encoding in META tag (rfc2397)`

` *Special Final injection(s)*:`
`   These options can be used to execute some 'special' injection(s) on`
`   vulnerable target(s). You can select multiple and combine them with`
`   your final code (except with DCP code):`

`   --Onm               ONM - Use onMouseMove() event`
`   --Ifr               IFR - Use `<iframe>` source tag`

` *Reporting*:`
`   --save              export to file (XSSreport.raw)`
`   --xml=FILEXML       export to XML (--xml file.xml)`

` *Miscellaneous*:`
`   --silent            inhibit console output results`
`   --no-head           NOT send a HEAD request before start a test`
`   --alive=ISALIVE     set limit of errors before check if target is alive`
`   --update            check for latest stable version`

# Contact

**Irc:**

`   * irc.freenode.net - channel: `*`#xsser`*

**Project Leader:**

`   * `[**`psy`**](User:Psy "wikilink")` - `[**`03c8.net`**](https://03c8.net)

[Category:OWASP Project](Category:OWASP_Project "wikilink")