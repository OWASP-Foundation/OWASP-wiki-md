## Description

A collection of Greasemonkey scripts written by Aung Khant from
<http://yehg.net> that aim to provide security for you and your site. We
love to write Greasemonkey scripts than Browser Addons because
Greasemonkey is more flexible. Any one can view and edit source codes
with ease. They will forever be compatible with any versions of Gecko
browsers while most security addons are no longer compatible with new
versions unless their authors take pains to modify codes for
compatibility. Send suggestions and bugs via our contact form at our
home page. Feel free to modify codes to adapt your need.

## Requirements

Gecko Browser Family (Firefox/Flock/..etc)

Greasemoney Addon <http://www.greasespot.net/>

## Current Scripts

  - **phpinfo() Security Checker**

Description: Whenver the script detects a phpinfo() page, it
fingerprints it for how much secure that phpinfo page. It's a
combination of my security thoughts and phpinfosec.com's project. Use it
for security and performance issues. Ideal for web masters and web
server admins who are a bit confused with phpinfo() page's numberous
configuration items. Date: July 2008

  - **WebPageFingerPrint (aka. Hacking Script)**

Description: Although the initial release v.01 was for fingerprinting
web page, this v0.2 version is integrated with JS-file fingerprinting,
fuzzing, bruteforcing \[version 0.1\] WebPageFingerPrinting script
without having to view html source. Sometimes, clicking each in
WebDeveloper Toolbar is tedious.I'd like to read a summerized view of
current web page first. Here this script comes in.

Resource: [Be sure to see its
movies](http://sourceforge.net/project/showfiles.php?group_id=233075&package_id=284105&release_id=613469)

Warning: Use it only for lawful purposes as the script has vulnerability
scanning which invokes IDS detection. Date: July, 2008

  - **Malware Script Detector v2**

Description: The version 2 is similar to XSS warning addon. Look for URL
string for XSS payloads. Detect and stop XSS attacks from evil bad guys
to you in addition to detection of Malicious JavaScript embedded in
malicious sites. This script has been tested for false positives
thoroughly. False positives may occur at those sites which use crypto
strings like order.php?token={a:xC2;id:ac3f52233;\[\]} and Squirrel mail
sites which use URL strings like compose.php?to=John\<joh@abc.net\>. We
can't fix it for the sake of security. If you know this one, you can
feel assured this is safe to accept and go on. Available also: Standlone
version for webmasters. Resource: [Introducing
MSD](http://yehg.net/lab/pr0js/presentation/IntroducingMSD.pps)

Date: March 2008

  - **Malware Script Detector v1**

Description: Detect & Alert Malicious JavaScript : XSSProxy, XSS-Shell,
AttackAPI, Beef. But No guarantee for full prevention of XSS-Injection
threats. Many ways to bypass it such as obfuscation but I'm sure it
protects you from casual attackers. Date: Feb 2008

## Download

<http://yehg.net/lab/#tools.greasemonkey>

[Category:Non-OWASP_Open_Tool](Category:Non-OWASP_Open_Tool "wikilink")