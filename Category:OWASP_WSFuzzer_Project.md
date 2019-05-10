[Click here to return to OWASP Projects
page.](:Category:OWASP_Project "wikilink")
[Click here to see (& edit, if wanted) the
template.](:Project_Information:template_WSFuzzer_Project "wikilink")

## Overview

WSFuzzer is a LGPL'd program, written in Python, that currently targets
Web Services. In the current version HTTP based SOAP services are the
main target. This tool was created based on, and to automate, some
real-world manual SOAP pen testing work. This tool is NOT meant to be a
replacement for solid manual human analysis. Please view WSFuzzer as a
tool to augment analysis performed by competent and knowledgable
professionals. Web Services are not trivial in nature so expertise in
this area is a must for proper pen testing.

## Goals

  - To automate some of the more intense SOAP fuzzing processes that
    would be quite time consuming if performed manually
  - To do attack vector generation in a dynamic and intelligent fashion
    based on the specific target
  - Providing its functionality/resulting data to other tools in a
    seamless fashion
  - To facilitate the repeatable use of known successful attack vectors,
    especially against specific targets
  - To be part of a solid web application pen testing toolkit
  - To be as easy to use within the spectrum of understanding, and
    working with, SOAP services

It is not the goal of WSFuzzer to replace human analysis. As a matter of
fact, WSFuzzer does not currently do much analysis of the results
gathered. The job of analysis is left to the analyst/engineer running a
given pen test.

This tool is ultimately meant to augment a pen tester's job with respect
to SOAP based web services.

Check out a video of WSFuzzer in action @
<http://www.neurofuzz.com/modules/software/vidz.php>

## Current Version

1.9.5

## Install

Pre-requisites:

Python 2.6/2.7
PyXML
Java 1.6.X
Tar and Gzip are used in concert to create the wsfuzzer\* "gzipped
archives". Hence they have the .tar.gz extension. The install process is
to simply:
1\. extract the files from this tarball (archive)
2\. alter the "JAVA_HOME" value in file "parseWsdl.sh" (parseWsdl.bat
for windows) - this is the full path up to the java home (currently Java
1.6 is required)
So for example that value may look like this on a Mac:
JAVA_HOME="/System/Library/Frameworks/JavaVM.framework/Versions/1.6.0/Home"
To extract the program one can obviously use the tar and gzip commands
separately. But an easier way takes into account that tar's -z option
feeds the archive gzip after unpacking, Thus:
tar -xvzf wsfuzzer\*.tar.gz
extracts all files from the gzipped archive and places them into a
directory that reflects the version number. For example:
cd /to/location/of/tarball
tar -xvzf wsfuzzer-1.9.4.tar.gz
extracts all files to a directory named:
version1.9.4
based on the location of the tarball. So if the tarball is in dir:
/opt/wsfuzzer
one would end up with:
/opt/wsfuzzer/version1.9.3/
Upon proper tarball extraction perform step 2 as listed above and the
install is complete. You can move on to running the program.
Get the tarball from sourceforge:
<http://sourceforge.net/project/showfiles.php?group_id=155697>

  -   - Code has been updated to be compatible with the 2.6/3.X families
        of Python. If you are running something older like Python2.4
        then you will have to install some libraries...

Hashlib is one of those lib's that needs to get installed, find it here:
<http://code.krypto.org/python/hashlib/>

## Features

  - Pen tests an HTTP SOAP web service based on either valid WSDL, known
    good XML payload, or a valid endpoint & namespace.
  - It can try to intelligently detect WSDL for a given target.
  - Includes a simple TCP port scanner.
  - WSFuzzer has the ability to Fuzz methods with multiple parameters.
    There are 2 modes of attack/fuzzing: "individual" and
    "simultaneous". Each parameter is either handled as a unique entity
    (individual mode), and can either be attacked or left alone, or
    multiple parameters are attacked simultaneously (hence the name -
    simultaneous mode) with a given data set.
  - The fuzz generation (attack strings) consists of a combination of a
    dictionary file, some optional dynamic large injection patterns, and
    some optional method specific attacks including automated XXE and
    WSSE attack generation.
  - It intelligently records attack vectors that can cause XDoS
    conditions and then uses them based on your response to execute a
    XDoS attack.
  - The tool also provides the option of using some IDS Evasion
    techniques which makes for a powerful security infrastructure
    (IDS/IPS) testing experience.
  - A time measurement of each round trip between request and response
    is now provided to potentially aid in results analysis.
  - For any given program run, the generated attack vectors are saved
    out to an XML file. The XML file is named XXX and is located in the
    same directory where the results HTML file is saved.
  - Output includes CSV and PDF files
  - A previously generated XML file of attack vectors can be utilized
    instead of the dictionary/automated combo. This is for the sake of
    repeatability when the same vectors need to be used over and over
    again.

One source of the WSFuzzer feature set is our user community. So if you
feel a feature would be useful, please submit it to us at:
[sourceforge](https://sourceforge.net/tracker/?func=add&group_id=155697&atid=796844)

## Dictionary file structure

As of version 1.9.4 the structure of the dictionary file has changed to
that of:

`  vector:::type`

A snippet from the included All_attack.txt file looks like this:

`  ?x=>:::Meta-Character Injection`
`  ABCD`

|%8.8x |%8.8x |%8.8x |%8.8x |%8.8x |%8.8x |%8.8x |%8.8x |%8.8x |%8.8x
|:::Meta-Character Injection

`  /,%ENV,/:::OS Commanding`
`   :::OS Commanding`
`  %3cscript%3ealert("XSS");%3c/script%3e:::XSS`
`  <IMG%20SRC='`<javascript:alert(document.cookie>`)'>:::XSS`
`  0 or 1=1:::SQL Injection (SQLi)`
`  ' or 0=0 --:::SQL Injection (SQLi)`
`  *(`

|(mail=\*)):::LDAP Injection

`  *(`

|(objectclass=\*)):::LDAP Injection

`  count(/child::node()):::XPath Injection`

## Command line usage

`  Usage: python WSFuzzer.py  [`
`                             -w wsdl_url |`
`                             -e endpoint -n namespace |`
`                             --xml |'''`
`                              -h host |`
`                             --conf |`
`                             --bauser username --bapass password |`
`                             --xsseuser username --xssepass password |`
`                             --keyfile keyfile --certfile certfile |`
`                             --proxy proxyserver --proxyport port |`
`                             --attacks`
`                             ]`

`   -w WSDL_URL --- A FQDN WSDL URL - i.e. `<http://host/service/service.asmx?wsdl>
`    -e endpoint -n namespace --- -e and -n are used together`
`       -e is the web service endpoint --- i.e. WSDL URL`
`       -n is the web service namespace --- i.e. URI`
`       ** When using -e and -n you will have to manually establish the method to be attacked`
`    --xml --- A text file of the XML payload to be used against the target`
`    -h host --- A URL of the target host.  This option will do some digging into`
`               the target URL, it will scrape for anything WSDL or DISCO related and construct"`
`               a list of verified WSDL URL's`
`    --conf file --- A file containing some config data so as to automate some of the"`
`                   normally interactive parts of WSFuzzer`
`    --bauser username --bapass password --- these 2 optional arguments are used together whenever HTTP Basic Auth needs to be used`
`       --bauser is a Basic Auth username`
`       --bapass is a Basic Auth password to be used with the "bauser" username`
`    --xsseuser username --xssepass password --- these 2 optional arguments are used together whenever WS-Security Auth needs to be used`
`       --xsseuser is a WS-Security username`
`       --xssepass is a WS-Security password to be used with the "xsseuser" username`
`    --keyfile keyfile --certfile certfile --- these 2 optional arguments are used together whenever client-side certs need to be used`
`       --keyfile is the PEM formatted file that contains the respective private key to be used`
`       --certfile is the PEM formatted file that contains the X.509 certificate to be used with the "keyfile"`
`    --proxy server_info --proxyport port --- these 2 optional arguments are used together`
`       --proxy is a Proxy server's IP address or FQDN`
`       --proxyport is the number of the TCP port for the server identified in switch --proxy`
`    --attacks is the name of a XML attack vector file previously generated by WSFuzzer`

## Configuration File Examples

The basic story with the config files is that the more info you add in
to them the less questions you will be asked by the program.

The following represents the possible values per option for proper use
of the config files:

`   wsdl - full path to the WSDL resource, including protocol`
`   xml - full path to the file holding an XML payload`
`   endpoint - full URL representing the target endpoint`
`   namespace - the namespace for the target`
`   method - name of the target method`
`   parameters - comma separated list of parameter names, for example: param1, param2, param3`
`   simultaneous - 'yes'`
`   host - full URL, if the protocol is not present "http" will be used`
`   uri - path to the resource`
`   soapaction - name of the action`
`   idsevasion - 'yes' or 'no'`
`   idsevasionopt - '0','1','2','3','4','5','6','7','8','9','10','11','12','13','14','R'`
`   directory - the name of the directory you want to use for a given program run`
`   alternatehost - either the string representing the alternate host or 'no'`
`   attacks - full path to the XML file holding the attack vectors you want to use`
`   dictionary - full path to an attack dictionary`
`   automate - 'yes' or 'no'`
`   bauser - basic auth username`
`   bapass - basic auth password`
`   xsseuser - WS-Security username`
`   xssepass - WS-Security password`
`   keyfile - full path to the key file`
`   certfile - full path to the cert file`
`   proxy - full URL of the proxy server to be used`
`   proxyport - number of port to be used`
`   `

The following represents the options that each mode will read in:

`   Mode 1 will read in:`
`   wsdl`
`   simultaneous`
`   bauser`
`   bapass`
`   xsseuser`
`   xssepass`
`   keyfile`
`   certfile`
`   proxy`
`   proxyport`
`   idsevasion`
`   idsevasionopt`
`   directory`
`   alternatehost`
`   attacks`
`   dictionary`
`   automate`
`    Mode 2 will read in:`
`   endpoint`
`   namespace`
`   method`
`   parameters`
`   simultaneous`
`   soapaction`
`   bauser`
`   bapass`
`   xsseuser`
`   xssepass`
`   keyfile`
`   certfile`
`   proxy`
`   proxyport`
`   idsevasion`
`   idsevasionopt`
`   directory`
`   alternatehost`
`   attacks`
`   dictionary`
`   automate`
`    Mode 3 will read in:`
`   xml`
`   host`
`   uri`
`   soapaction`
`   bauser`
`   bapass`
`   xsseuser`
`   xssepass`
`   keyfile`
`   certfile`
`   proxy`
`   proxyport`
`   idsevasion`
`   idsevasionopt`
`   directory`
`   alternatehost`
`   attacks`
`   dictionary`
`   automate`

The structure of the files should resemble these examples:

`   # Mode 1 automates some parts of the -w switch`
`   Mode = 1`
`   wsdl = `<http://target/resource.asmx?wsdl>
`   idsevasion = no`
`   simultaneous = yes`
`   directory = directoryName`
`   dictionary = attack2.txt`
`   automate = no`
`   alternatehost = no`

`   # Mode 2 automates some of the endpoint (-e) and namespace (-n) options`
`   Mode = 2`
`   endpoint = `<http://your.end.point>
`   namespace = the_namespace`
`   method = target_method`
`   parameters = param1, param2, param3`
`   simultaneous = yes`
`   dictionary = dict.txt`
`   automate = no`
`   idsevasion = yes`
`   idsevasionopt = 5`
`   directory = directoryName`

`   # Mode 3 automates some parts of the --xml switch`
`   Mode = 3`
`   xml = payload.xml`
`   dictionary = dict.txt`
`   host = `<http://target:port>
`   automate = no`
`   idsevasion = yes`
`   idsevasionopt = R`
`   uri = /path/to/resource.jws`
`   simultaneous = yes`
`   directory = directoryName`

## Run-Time Examples

Here are examples of different types of runs:

  - python WSFuzzer --conf confmode3.txt
  - python WSFuzzer -w <http://target/service/service.asmx?wsdl>
  - python WSFuzzer -e <http://target/service/service.asmx> -n
    <urn:service>
  - python WSFuzzer --xml file.xml
  - python WSFuzzer -h <http://target>

Upon completion of a run the current output is based on a directory the
prog will create. That dir is created within the root dir where the
program is installed and run from. By default the pattern for dir
creation is based on the string FuzzingResults-N. N is dynamically
calculated based on existing directories fitting the pattern. So if you
run the prog from "/opt/WSFuzzer" for instance you will end up with
something like:

  - /opt/WSFuzzer/FuzzingResults-0
  - /opt/WSFuzzer/FuzzingResults-1
  - ...
  - /opt/WSFuzzer/FuzzingResults-N

In each one of these directories there will be an index.html file and a
dir called HeaderData.

index.html will give you an overview of the results as such:

`   Method  Request Params          IDS evasion                     Response    Http Info   Round Trip`
`   xpath   {'parameters': '%00'}   /WSDIGGeR_WS/WSDiggER_WS.AsMX   Soap Fault  HTTP Log    276.2158 M`
`   xpath   {'parameters': 'TRUE'}  /WSDIggER_WS/WSDIgGer_WS.AsMx   Soap Fault  HTTP Log    2.88 S`

In the HeaderData dir you will find files that hold a Request / Response
pair for each of the attacks sent to the target. One file has one
Request and one Response. In some cases there will be no response if the
attack Request caused some sort of crash on the server (500 status
response, etc). Each one of the links in the Http Info column will
provide you a path into the respective file as per the rest of the data
in that row.

In reference to the "Round Trip" values:

`   M = milliseconds`
`   S = seconds `

### Using a known good XML payload (the --xml switch)

This is a snippet from a run using the Static XML option (--xml)

`  python2.4 WSFuzzer.py --xml xpath.xml`
`   Running WSFuzzer 1.9, the latest version`
`  Local "All_attack.txt" data matches that on neurofuzz.com`
`  Local "dirs.txt" data matches that on neurofuzz.com`
`  Local "filetypes.txt" data matches that on neurofuzz.com`
`  If you would like to establish the directory name for the results then type it in now (leave blank for the default): xmltest`
`   Since you are using the static XML feature we need some data from you...`
`   Host to attack (i.e. sec.neurofuzz.com): 192.168.1.207`

`   URI to attack (i.e. /axis/EchoHeaders.jws): /WSDigger_WS/WSDigger_WS.asmx`
`   Unless some serious masking/spoofing is in place, it seems you are targeting a .Net host so you will need to use`
`  a SOAPAction header ...`
`   Enter the SOAPAction value: `<http://foundstone.com/Stringproc/xpath>
`  Method: xpath`
`  Param discovered: query, of type: xsi:string`
`  Simultaneous Mode activated`
`   Input name of Fuzzing dictionary(full path): attack.txt`
`  Dictionary Chosen: attack.txt`
`   Would you like to enable automated fuzzing to augment what you have already chosen?`
`   This option generates a lot of traffic, mostly with a bad attitude &->`
`   Answer: n`
`   Parameter: query`
`  Would you like to fuzz this param: y`
`   Fuzzing this param`
`  adding parameter`
`   Would you like to enable IDS evasion(y/n)?`
`   Answer: n`
`   Not using IDS evasion`
`  Shall I begin Fuzzing(y/n)?`
`   Answer: y`
`   Commencing the fuzz ....`
`   Starting to fuzz method (xpath)`
`   Generated 4 parameter based Attack Strings ...`

`   Fuzzing completed for method (xpath)`

The following represents an example of the payload contained as the
content of the xml file passed in via the --xml switch. In reference to
the example above, the file xpath.xml has the following as its contents:

<?xml version="1.0" encoding="utf-8"?>

`  `<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/"
   xmlns:xsi=" http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">
`  `<soap:Body>
`  `<xpath ns="http://foundstone.com/Stringproc">
`  `<query>`WHATEVER`</query>
`  `</xpath>
`  `</soap:Body>
`  `</soap:Envelope>

  -   - This option (--xml) is ideal for the use of WSFuzzer when
        targeting .Net services/hosts. In order to use this option
        successfully you need to know/have the following in reference to
        your target:

<!-- end list -->

  - A valid XML payload. All you need to do is use whatever method you'd
    like to generate a valid payload based on your target. As a pen
    tester this is usually no problem since you are working closely with
    the target's developers/engineers.
  - Proper host data in the form of host.domain or an IP address, i.e.
    sec.neurofuzz.com or 192.168.1.207
  - Proper resource data (URI), i.e. /WSDigger_WS/WSDigger_WS.asmx
  - If you are targeting a .Net service you will also need to know the
    value for a valid SOAPAction HTTP header, this could be the name of
    the method or a FQDN - it totally depends on how the target services
    were built. For instance in the example above the SOAPAction value
    is: <http://foundstone.com/Stringproc/xpath>

### Individual Mode / No IDS Evasion

Here is a snippet from a run utilizing individual mode and no IDS
Evasion:

`  WSFuzzer.py -w `<http://jboss_target.example.com/ws4ee/services/LoginService?wsdl>
`   Running WSFuzzer 1.9, the latest version`
`  Local "All_attack.txt" data matches that on neurofuzz.com`
`  Local "dirs.txt" data matches that on neurofuzz.com`
`  Local "filetypes.txt" data matches that on neurofuzz.com`
`   WSDL Discovered (http://jboss_target.example.com/ws4ee/services/LoginService?wsdl)`
`   If you would like to establish the directory name for the results then type it in now (leave blank for the default): mytest`
`   Method(0): authenticateUser`
`  Params:`
`  in0(string)`
`  in1(string)`
`  in2(string)`
`   Method(1): setToken`
`  Params:`
`  in0(string)`
`   Select the methods you want to Fuzz(ex: 0,1,2,3 or A for All)`
`   Methods: 0`
`   Would you like to attack all the chosen params simultaneously? n`
`   Method: authenticateUser`
`  Parameter: in0 Type: string`
`   Choose fuzz type(ex. 1)`
`  0) Do not fuzz this parameter`
`  1) Dictionary (One entry per line)`
`  FuzzType: 1`
`   Fuzzing using dictionary`
`  Input name of dictionary(full path): attack1.txt`
`  Dictionary Chosen: attack1.txt`
`   Would you like to enable automated fuzzing to augment what you have already chosen?`
`  This option generates a lot of traffic, mostly with a bad attitude &->`
`  Answer: y`
`   adding parameter`
`  Parameter: in1 Type: string`
`   Choose fuzz type(ex. 1)`
`  0) Do not fuzz this parameter`
`  1) Dictionary (One entry per line)`
`  FuzzType: 0`
`   Not fuzzing this param`
`  adding parameter`
`  Parameter: in2 Type: string`
`   Choose fuzz type(ex. 1)`
`  0) Do not fuzz this parameter`
`  1) Dictionary (One entry per line)`
`  FuzzType: 1`
`   Fuzzing using dictionary`
`  Input name of dictionary(full path): attack2.txt`
`  Dictionary Chosen: attack2.txt`
`   Would you like to enable automated fuzzing to augment what you have already chosen?`
`  This option generates a lot of traffic, mostly with a bad attitude &->`
`  Answer: n`
`   Would you like to enable IDS evasion(y/n)?`
`  Answer: n`
`  Not using IDS evasion`
`   Shall I begin Fuzzing(y/n)?`
`   Answer: y`
`   Commencing the fuzz ....`
`   starting fuzzing method (authenticateUser)`
`   Generated 6101 Attack Strings ...`
`   <<< Baseline XML Payload with Random data val's >>>`
`   `

<?xml version="1.0" encoding="UTF-8"?>

`  `<SOAP-ENV:Envelope SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/"
   xmlns:SOAP-ENC="http://schemas.xmlsoap.org/soap/encoding/"
   xmlns:xsi="http://www.w3.org/1999/XMLSchema-instance" xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/"
   xmlns:xsd="http://www.w3.org/1999/XMLSchema">
`  `<SOAP-ENV:Body>
`  `<authenticateUser SOAP-ENC:root="1">
`  `<v1 xsi:type="xsd:string">`xdeiykUzTnXTlFPrEiyJvAszywDojsxbAQNDxVnysdjJrQKCYqGsrNeTQaHWfAZIuhcrohfygMilBDCTCJRGvplQi`</v1>
`  `<v2 xsi:type="xsd:string">`suDtTvYwFdbJxDSuvgnnUhzzXbsFrLQuTKfPPNTejarrVATMXUqD`</v2>
`  `<v3 xsi:type="xsd:string">`gGdVVAKWMmARMSBBlZhQdnBHzVVHGfgHwUoxFItflzKaTbxMNppRtWevzQxCJcXhdF`</v3>
`  `</authenticateUser>
`  `</SOAP-ENV:Body>
`  `</SOAP-ENV:Envelope>
`   <<<<<<<<<<<<<<<<<<<<<<<<>>>>>>>>>>>>>>>>>>>>>>>>>>>`
`   Fuzzing completed for method (authenticateUser)`

And here is a snippet from the results output of the run above:

`   Method          Request Params                             IDS Evasion  Response   Http Info    Round Trip`
`   authenticateUser    {'in0': '/*', 'in1': None, 'in2': None}    None     0      HTTP Log     276.2158 M`
`   authenticateUser    {'in0': '\\00', 'in1': None, 'in2': None}  None     0      HTTP Log     2.88 S`

### Simultaneous Mode / No IDS Evasion

Here is a snippet from a run utilizing simultaneous mode and no IDS
Evasion:

`  python WSFuzzer.py -w `<http://jboss_target.example.com/ws4ee/services/LoginService?wsdl>
`   Running WSFuzzer 1.9, the latest version`
`  Local "All_attack.txt" data matches that on neurofuzz.com`
`  Local "dirs.txt" data matches that on neurofuzz.com`
`  Local "filetypes.txt" data matches that on neurofuzz.com`
`   WSDL Discovered (http://jboss_target.example.com/ws4ee/services/LoginService?wsdl)`
`  If you would like to establish the directory name for the results then type it in now (leave blank for the default): mytest`
`   Method(0): authenticateUser`
`  Params:`
`  in0(string)`
`  in1(string)`
`  in2(string)`
`   Method(1): setToken`
`  Params:`
`  in0(string)`
`   Select the methods you want to Fuzz(ex: 0,1,2,3 or A for All)`
`  Methods: 0`
`   Would you like to attack all the chosen params simultaneously? y`
`  Input name of Fuzzing dictionary(full path): attack3.txt`
`  Dictionary Chosen: attack3.txt`
`   Would you like to enable automated fuzzing to augment what you have already chosen?`
`  This option generates a lot of traffic, mostly with a bad attitude &->`
`  Answer: n`
`   Method: authenticateUser`
`  Parameter: in0 Type: string`
`  Would you like to fuzz this param: y`
`  Fuzzing using dictionary`
`  adding parameter`
`   Method: authenticateUser`
`  Parameter: in1 Type: string`
`  Would you like to fuzz this param: y`
`  Fuzzing using dictionary`
`  adding parameter`
`   Method: authenticateUser`
`  Parameter: in2 Type: string`
`  Would you like to fuzz this param: y`
`  Fuzzing using dictionary`
`  adding parameter`
`   Would you like to enable IDS evasion(y/n)? Answer: n`
`  Not using IDS evasion`
`   Shall I begin Fuzzing(y/n)?`
`   Answer: y`
`   Commencing the fuzz ....`
`   starting fuzzing method (authenticateUser)`
`   <<< Baseline XML Payload with Random data val's >>>`
`   `

<?xml version="1.0" encoding="UTF-8"?>

`  `<SOAP-ENV:Envelope SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/"
   xmlns:SOAP-ENC="http://schemas.xmlsoap.org/soap/encoding/"
   xmlns:xsi="http://www.w3.org/1999/XMLSchema-instance" xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/"
   xmlns:xsd="http://www.w3.org/1999/XMLSchema">
`  `<SOAP-ENV:Body>
`  `<authenticateUser SOAP-ENC:root="1">
`  `<v1 xsi:type="xsd:string">`xdeiykUzTnXTlFPrEiyJvAszywDojsxbAQNDxVnysdjJrQKCYqGsrNeTQaHWfAZIuhcrohfygMilBDCTCJRGvplQi`</v1>
`  `<v2 xsi:type="xsd:string">`suDtTvYwFdbJxDSuvgnnUhzzXbsFrLQuTKfPPNTejarrVATMXUqD`</v2>
`  `<v3 xsi:type="xsd:string">`gGdVVAKWMmARMSBBlZhQdnBHzVVHGfgHwUoxFItflzKaTbxMNppRtWevzQxCJcXhdF`</v3>
`  `</authenticateUser>
`  `</SOAP-ENV:Body>
`  `</SOAP-ENV:Envelope>
`   <<<<<<<<<<<<<<<<<<<<<<<<>>>>>>>>>>>>>>>>>>>>>>>>>>>`
`   Fuzzing completed for method (authenticateUser)`

And here is a snippet from the results output of the run above:

`   Method          Request Params                                  IDS Evasion     Response    Http Info   Round Trip`
`   authenticateUser    {'in0': '/*', 'in1': '/*', 'in2': '/*'}     None            0           HTTP Log    2.88 S`
`   authenticateUser    {'in0': '\\00', 'in1': '\\00', 'in2': '\\00'}   None            0           HTTP Log    276.2158 M`

### Discovery / IDS Evasion

Now here is a run utilizing one of the IDS Evasion techniques:

`  python WSFuzzer.py -h `<http://jboss_target.example.com>
`   Running WSFuzzer 1.9`
`   If you would like to establish the directory name for the results then type it in now (leave blank for the default): mytest`
`   0) Basic Discovery (faster but less accurate)`
`  1) Advanced Discovery (slower and more intrusive but more thorough and accurate)`
`  2) Advanced Discovery (like #1) with port scanning first`
`   Probe Type: 2`
`  Beginning TCP port for scan: 1`
`  Ending TCP port for scan: 9090`
`   Open TCP ports discovered for target localhost:`
`  [0] 80`
`  [1] 8080`
`  [2] 8088`
`  Pick one via numeric index (i.e. 1 for [1]): 0`
`   Would you like to Spider the target on top of the advanced probe: y`
`   Checking 10077696 maximum number of dir combo's based on a depth of 7`
`   Discovered WSDL links:`
`  0 => `<http://jboss_target.example.com/ws4ee/services/ERSService?wsdl>
`  1 => `<http://jboss_target.example.com/ws4ee/services/AuditService?wsdl>
`  2 => `<http://jboss_target.example.com/ws4ee/services/SyncService?wsdl>
`  3 => `<http://jboss_target.example.com/ws4ee/services/ThumbnailService?wsdl>
`  4 => `<http://jboss_target.example.com/ws4ee/services/OfficeDataService?wsdl>
`  5 => `<http://jboss_target.example.com/ws4ee/services/TestService?wsdl>
`  6 => `<http://jboss_target.example.com/ws4ee/services/LogsService?wsdl>
`  7 => `<http://jboss_target.example.com/ws4ee/services/LoginService?wsdl>
`  8 => `<http://jboss_target.example.com/ws4ee/services/AdminService?wsdl>
`  9 => `<http://jboss_target.example.com/ws4ee/services/VersionService?wsdl>
`  10 => `<http://jboss_target.example.com/ws4ee/services/UserService?wsdl>
`  11 => `<http://jboss_target.example.com/ws4ee/services/IKSService?wsdl>
`  12 => `<http://jboss_target.example.com/ws4ee/services/ExcelService?wsdl>
`  13 => `<http://jboss_target.example.com/ws4ee/services/AdminService2?wsdl>
`  14 => `<http://jboss_target.example.com/ws4ee/services/DirService?wsdl>
`   Please choose ONE link, via numeric index, from the above list`
`   7`
`   Method(0): authenticateUser`
`  Params:`
`  in0(string)`
`  in1(string)`
`  in2(string)`
`   Method(1): setToken`
`  Params:`
`  in0(string)`
`   Select the methods you want to Fuzz(ex: 0,1,2,3 or A for All)`
`  Methods: 0`
`   Would you like to attack all the chosen params simultaneously? n`
`  Method: authenticateUser`
`  Parameter: in0 Type: string`
`  Choose fuzz type(ex. 1)`
`  0) Do not fuzz this parameter`
`  1) Dictionary (One entry per line)`
`  FuzzType: 1`
`   Fuzzing using dictionary`
`  Input name of dictionary(full path): attack1.txt`
`  Dictionary Chosen: attack1.txt`
`   Would you like to enable automated fuzzing to augment what you have already chosen?`
`  This option generates a lot of traffic, mostly with a bad attitude &->`
`  Answer: y`
`   adding parameter`
`  Parameter: in1 Type: string`
`  Choose fuzz type(ex. 1)`
`  0) Do not fuzz this parameter`
`  1) Dictionary (One entry per line)`
`  FuzzType: 0`
`   Not fuzzing this param`
`   adding parameter`
`  Parameter: in2 Type: string`
`  Choose fuzz type(ex. 1)`
`  0) Do not fuzz this parameter`
`  1) Dictionary (One entry per line)`
`  FuzzType: 1`
`   Fuzzing using dictionary`
`  Input name of dictionary(full path): attack2.txt`
`  Dictionary Chosen: attack2.txt`
`   Would you like to enable automated fuzzing to augment what you have already chosen?`
`  This option generates a lot of traffic, mostly with a bad attitude &->`
`  Answer: n`
`  adding parameter`
`   Would you like to enable IDS evasion(y/n)?`
`  Answer: y`
`  Choose an option for IDS Evasion.`
`  0) null method processing - ** Windows targets only`
`  1) random URI (non-UTF8) encoding`
`  2) directory self-reference (/./)`
`  3) premature URL ending`
`  4) prepend long random string`
`  5) fake parameter`
`  6) TAB as request spacer`
`  7) random case sensitivity - ** Windows targets only`
`  8) directory separator (\) - ** Windows targets only`
`  10) URI (non-UTF8) encoding`
`  R) choose an option at random`
`  Option: 1`
`   Shall I begin Fuzzing(y/n)?`
`  Answer: y`
`   Commencing the fuzz ....`
`   starting fuzzing method (authenticateUser)`
`   Generated 6101 Attack Strings ...`
`   <<< Baseline XML Payload with Random data val's >>>`
`   `

<?xml version="1.0" encoding="UTF-8"?>

`  `<SOAP-ENV:Envelope SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/"
   xmlns:SOAP-ENC="http://schemas.xmlsoap.org/soap/encoding/"
   xmlns:xsi="http://www.w3.org/1999/XMLSchema-instance" xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/"
   xmlns:xsd="http://www.w3.org/1999/XMLSchema">
`  `<SOAP-ENV:Body>
`  `<authenticateUser SOAP-ENC:root="1">
`  `<v1 xsi:type="xsd:string">`xdeiykUzTnXTlFPrEiyJvAszywDojsxbAQNDxVnysdjJrQKCYqGsrNeTQaHWfAZIuhcrohfygMilBDCTCJRGvplQi`</v1>
`  `<v2 xsi:type="xsd:string">`suDtTvYwFdbJxDSuvgnnUhzzXbsFrLQuTKfPPNTejarrVATMXUqD`</v2>
`  `<v3 xsi:type="xsd:string">`gGdVVAKWMmARMSBBlZhQdnBHzVVHGfgHwUoxFItflzKaTbxMNppRtWevzQxCJcXhdF`</v3>
`  `</authenticateUser>
`  `</SOAP-ENV:Body>
`  `</SOAP-ENV:Envelope>
`   <<<<<<<<<<<<<<<<<<<<<<<<>>>>>>>>>>>>>>>>>>>>>>>>>>>`
`   Fuzzing completed for method (authenticateUser)`

And here is a snippet from the results output of the run above:

`   Method          Request Params                            IDS Evasion                                                       Response ... `
`   authenticateUser    {'in0': '/*', 'in1': None, 'in2': None}   /L%75g%68%53e%72vic%65/%41o%74hS%65%72vic%65S%65rv%69%63%65       0 ...           `
`   authenticateUser    {'in0': '\\00', 'in1': None, 'in2': None} /L%75%74i%53%65%72v%69%63%65/%41o%74%68Servi%63%65%53%65rv%69%63e 0 ...`

## IDS Evasion

The following options are currently available for purposes of IDS
Evasion:

0\) null method processing - \*\* Windows targets only
1\) random URI (non-UTF8) encoding
2\) directory self-reference (/./)
3\) premature URL ending
4\) prepend long random string
5\) fake parameter
6\) TAB as request spacer
7\) random case sensitivity - \*\* Windows targets only
8\) directory separator (\\) - \*\* Windows targets only
10\) URI (non-UTF8) encoding
11\) double percent hex encoding - \*\* Windows targets only
12\) double nibble hex encoding - \*\* Windows targets only
13\) first nibble hex encoding - \*\* Windows targets only
14\) second nibble hex encoding - \*\* Windows targets only
R) choose an option at random
Working with the following target URI: "/WSDigger_WS/WSDigger_WS.asmx"
here is an idea of what the URI data would look like when IDS Evasion is
in use for the HTTP POST's:

`   * null method processing: %00%20/WSDigger_WS/WSDigger_WS.asmx`
`    * random URI (non-UTF8): /%57SDi%67g%65r%5fW%53/%57%53D%69gge%72_%57%53.asm%78`
`    * directory self-reference (/./): /./WSDigger_WS/./WSDigger_WS.asmx`
`    * premature URL ending: /%20HTTP/1.1%0D%0A%0D%0AAccept%3A%20PTdOoYWl2A/../../WSDigger_WS/WSDigger_WS.asmx`
`    * prepend long random string: /UCD8SiuHKgBhOrUmmdRtn15khQD17fWScHMz6Wa3x65ihPOzBPCkj2M3e4Lr0lwAYgx0zrDAh7ZOUlAqE1vHpqvIFKj2hHQjUS4VdyUyOewrIDnEsaX5`
`     WrpOYIphWuzZIT3J1nezbYxjwvg0R5u6QVbBJFiafkY2t5mIPexZd9Zwq9f9Nu3lHRJzRauoDP2VpewGimw9TVrcynp0NJFCEefV6ETCMbhdn9fUPC3dYN8`
`     MyubOeLQqOMWDKI4y35prsntMfGX2WWbRFii912f75zVuaYDOR5CxVopXT6bU7eDbCea8YSAZAWxdt0kuGtEmFbH46WXl6cInovsY3nLmTgZ77XX`
`     4JncWWatypv34az9iuMmr0GqyCgOuxLIW0600zGhTlAuZYf3I6rs0Lm4NHaEmLi7ZNdPywNV0IUs2Wwlu2EsbHcTXnNbZ00Za2ixKuIJGqVKTrgS7LhfP5e`
`      16rR2D9mvBWkxVXIHhj30iniGoHhRl1XPs2mnO0ROb6CS0Xy3Nquzv/../WSDigger_WS/WSDigger_WS.asmx`
`    * fake parameter: /eLCk3rV3v1.html%3fyW0TziI2SP=/..//WSDigger_WS/WSDigger_WS.asmx`
`    * TAB as request spacer: /WSDigger_WS/WSDigger_WS.asmx`
`    * random case sensitivity: /WSDiggER_WS/WSDIgGER_WS.AsmX`
`    * directory separator (\): /WSDigger_WS\WSDigger_WS.asmx`
`    * URI (non-UTF8): /%57%53%44%69%67%67%65%72%5f%57%53/%57%53%44%69%67%67%65%72%5f%57%53%2e%61%73%6d%78`
`    * double percent hex encoding: /%2557%2553%2544%2569%2567%2567%2565%2572%255f%2557%2553%2557%2553%2544%2569%2567%2567%2565%2572%255f%2557%2553%252e%2561%2573%256d%2578`
`    * double nibble hex encoding: /%%35%37%%35%33%%34%34%%36%39%%36%37%%36%37%%36%35%%37%32%%35%66%%35%37%%35%33/%%35%37%%35%33%%34%34`
`     %%36%39%%36%37%%36%37%%36%35%%37%32%%35%66%%35%37%%35%33%%32%65%%36%31%%37%33%%36%64%%37%38`
`    * first nibble hex encoding: /%%357%%353%%344%%369%%367%%367%%365%%372%%35f%%357%%353/%%357%%353%%344%%369%%367%%367%%365%%372%%35f`
`     %%357%%353%%32e%%361%%373%%36d%%378`
`    * second nibble hex encoding: /%5%37%5%33%4%34%6%39%6%37%6%37%6%35%7%32%5%66%5%37%5%33/%5%37%5%33%4%34%6%39%6%37%6%37%6%35%7%32%5%66`
`     %5%37%5%33%2%65%6%31%7%33%6%64%7%38`

## Future Development

‡ More types of dynamic and intelligent XML content based attacks
‡ Further development of attack vectors for:
   o WS-Security
   o SAML
   o XML Security (Digital Signatures, XML Encryption, etc)
‡ Different results output formats (possibly AVDL, NBE, etc)

## Known Limitations/Issues

‡ We have gotten reports from a few users stating that the automated
fuzzing is causing client side memory errors. Admittedly the automated
fuzzing generates a lot of data and is intense :-) But that is one of
the MO's of attacks so this is not accidental. As of version 1.7 we have
toned down these type of attacks a bit and it seems to be playing nicer.
So keep us posted on these types of issues but remember that the point
with some of these attack vectors is to break the rules and force
anomalies in order to see how the server side target holds up. In other
words dont write us complaining about the fact that the tool is
generating and sending bad XML, yes that is one of the things this tool
purposely does.
‡ There is no GUI - Not quite sure that is entirely a limitation.

## Feedback and Participation

We hope you find the OWASP WSFuzzer Project useful. Please contribute to
the Project by volunteering for one of the Tasks, sending your comments,
questions, and suggestions to owasp@owasp.org. To join the OWASP
WSFuzzer Project mailing list or view the archives, please visit the
[subscription
page.](http://lists.owasp.org/mailman/listinfo/owasp-wsfuzzer)

WSFuzzer is intended to benefit all of us in this application security
field. It is entirely open source and to keep this tool as a useful
player in a pen testers toolkit the project can use help in the areas
of:

`   * Python coding`
`   * regular testing of the tool`
`   * web services security expertise`
`   * plain old feedback`

If one person has even 2 of these 3 qualifications then that person
would be an ideal addition to this project. If you are interested drop a
note to wsfuzzer \[at\] neurofuzz dot com.
Additionally any feedback is useful since the SOAP and Web Services
space is so wide in scope.

## Project Contributors

Current software vision/development/engineering for WSFuzzer is
performed by:

Andres Andreu \<andres \[at\] neurofuzz dot com\>
Cosmin Banciu \<ccbanciu \[at\] gmail dot com\>

QA testing services performed by:

Shelly Saunders \<shelly \[at\] poppywood dot eu\>
Cynthia Gonzalez \<cynth dot gonzalez \[at\] gmail dot com\>
Christopher Elias \<chris dot ec dot pr \[at\] gmail dot com\>

## Project Sponsors

[neuroFuzz, LLC](http://www.neurofuzz.com)

<http://images.sourceforge.net/images/project-support.jpg> [Make a
Donation](http://sourceforge.net/donate/index.php?group_id=155697)

[WSFuzzer Project](Category:OWASP_Project "wikilink") [Category:OWASP
Download](Category:OWASP_Download "wikilink") [Category:OWASP
Tool](Category:OWASP_Tool "wikilink")