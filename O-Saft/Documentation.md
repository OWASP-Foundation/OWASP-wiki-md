## O-Saft

This is O-Saft's documentation as you get with:

`o-saft.pl --help`

<small>On Windows following must be used

`o-saft.pl --help --v`

</small>

__TOC__ -- position left does not work as it overlaps some texts

<table>
<tbody>
<tr class="odd">
<td><div>
<p>__TOC__</p>
</div></td>
</tr>
</tbody>
</table>

\--\>

-----

#### NAME

  -
    o-saft.pl - OWASP SSL advanced forensic tool
    OWASP SSL audit for testers

#### DESCRIPTION

  -
    This tools lists information about remote target's SSL certificate
    and tests the remote target according given list of ciphers.
    Note: Throughout this description `$0` is used as an alias for the
    program name `o-saft.pl` .

#### SYNOPSIS

` o-saft.pl [COMMANDS ..] [OPTIONS ..] target [target target ...]`

  -

    Where \[COMMANDS\] and \[OPTIONS\] are described below and `target`

    is a hostname either as full qualified domain name or as IP address.

    Multiple commands and targets may be combined.

    All commands and options can also be specified in a rc-file, see

    [RC-FILE](#RC-FILE "wikilink") below.

<!-- end list -->

  -
    I.g. all commands start with a `+` character and options start with
    `-` or `--` characters. Anything else is treated as target name.

#### QUICKSTART

  -
    Before going into a detailed description of the purpose and usage,
    here are some examples of the most common use cases:

:\* Show supported (enabled) ciphers of target:

`   o-saft.pl +cipher --enabled example.tld`

:\* Show supported (enabled) ciphers with their DH parameters:

`   o-saft.pl +cipher-dh example.tld`

:\* Test all ciphers, even if not supported by local SSL implementation:

`   o-saft.pl +cipherall example.tld`

:\* Show details of certificate and connection of target:

`   o-saft.pl +info example.tld`

:\* Check certificate, ciphers and SSL connection of target:

`   o-saft.pl +check example.tld`

:\* Check connection to target for vulnerabilities:

`   o-saft.pl +vulns example.tld`

:\* Check for all known ciphers (independant of SSL library):

`   o-saft.pl example.tld --range=full`
`   checkAllCiphers.pl example.tld`
`   checkAllCiphers.pl example.tld --range=full --v`

:\* Get the certificate's Common Name for a bunch of servers:

`   o-saft.pl +cn example.tld some.tld other.tld`

:\* List more usage examples

`   o-saft.pl --help=examples`

:\* List all available commands:

`   o-saft.pl --help=commands`

:\* Get table of contents for complete help

`   o-saft.pl --help=toc`

:\* Show just one section, for example SECURITY, from help

`   o-saft.pl --help=SECURITY`

:\* Start the simple GUI

`   o-saft.tcl`

:\* Start the simple GUI which uses *o-saft.pl* in a Docker image

`   o-saft.tcl --docker`

  -
    For more specialised test cases, refer to the
    [COMMANDS](#COMMANDS "wikilink") and [OPTIONS](#OPTIONS "wikilink")
    sections below. For more examples please refer to
    [EXAMPLES](#EXAMPLES "wikilink") section.

<!-- end list -->

  -
    For more details, please see
    [INSTALLATION](#INSTALLATION "wikilink") below.

#### WHY?

  -
    Why a new tool for checking SSL security and configuration when
    there
    are already a dozen or more such good tools in existence (in 2012)?

<!-- end list -->

  -
    **Unique features:**
      - working in closed environments, i.e. **without internet
        connection**
      - checking availability of ciphers **independent of installed
        library**
      - checking for **all possible ciphers** (up to 65535 per SSL
        protocol)
      - mainly same results on all platforms.

<!-- end list -->

  -
    Currently available tools suffer from some or all of following
    issues:

:\* lack of tests of unusual SSL certificate configurations

:\* may return different results for the same checks on a given target

:\* missing tests for modern SSL/TLS functionality

:\* missing tests for specific, known SSL/TLS vulnerabilities

:\* no support for newer, advanced, features e.g. CRL, OCSP, EV

:\* limited capability to create your own customised tests

  -
    Other reasons or problems are that other tools are either binary or
    use additional binaries and hence not portable to other platforms.

<!-- end list -->

  -
    In contrast to (all?) most other tools, including openssl, it can be
    used to \`ask simple questions' like \`does target support STS' just
    by
    calling:

`   o-saft.pl +hsts_sts example.tld`

  -
    For more, please see [EXAMPLES](#EXAMPLES "wikilink") section below.
    If it should run on systems with old software (perl or perl
    modules),
    please see [DEBUG](#DEBUG "wikilink") section below.

#### SECURITY

  -
    This tool is designed to be used by people doing security or
    forensic
    analyses. Hence no malicious input is expected.

<!-- end list -->

  -
    There are no special security checks implemented. Some parameters
    are
    roughly sanatised according unwanted characters. In particular there
    are no checks according any kind of code injection.

<!-- end list -->

  -
    Care should be taken, when additional tools and modules are
    installed
    as described in [INSTALLATION](#INSTALLATION "wikilink") below. In
    particular it is recommended
    to do these installations into directoies specially prepared for use
    with `o-saft.pl` . No other tools of your system should use these
    installations
    i.e. by accident or because your environment variables point to
    them.

<!-- end list -->

  -
    Note that compilation and installation of additional tools
    (*openssl*,
    *Net::SSLeay*, etc.) uses known insecure configurations and
    features\!
    This is essential to make `o-saft.pl` able to check for such
    insecurities.

<!-- end list -->

  -
    It is highly recommended to do these installations and use the tools
    on a separate testing system.

<!-- end list -->

  -
    **DO NOT USE THESE INSTALLATIONS ON PRODUCTIVE SYTEMS.**

#### TECHNICAL INFORMATION

  -
    It is important to understand, which provided information is based
    on
    data returned by underlaying (used) libraries and the information
    computed directly.

##### OpenSSL, libssl, libcrypto

  -
    In general the tool uses perl's *Net::SSLeay(1)* module which itself
    is based on libssl and/or libssleay library of the operating system.
    It's possible to use other versions of these libraries, see options:

:\* --exe-path=PATH --exe=PATH

:\* --lib-path=PATH --lib=PATH

:\* --envlibvar=NAME

  -
    The external *openssl(1)* is called to extract some information from
    its output. The version of openssl can be controlled with following
    options:

:\* --openssl=TOOL

:\* --no-openssl

:\* --force-openssl

:\* --exe-path=PATH --exe=PATH

  -
    Above applies to all commands except *+cipherall* and *+cipherraw*
    which
    uses no other libraries.

<!-- end list -->

  -
    OpenSSL is recommended to be used for libssl and libcrypto. Versions
    0.9.8k to 1.0.2e (Jan. 2016) are known to work. However, versions
    be-
    for 1.0.0 may not provide all informations.
    LibreSSL is not recommended, because some functionallity considered
    insecure, has been removed.
    For more details, please see
    [INSTALLATION](#INSTALLATION "wikilink") below.

##### Certificates and CA

  -
    All checks according the validity of the certificate chain are based
    on the root CAs installed on the system. NOTE that *Net::SSLeay(1)*
    and *openssl(1)* may have their own rules how and where to find the
    root CAs. Please refer to the documentation on your system for these
    tools. However, there are folloing options to tweak these rules:

:\* --ca-file=FILE

:\* --ca-path=DIR

:\* --ca-depth=INT

##### Commands and options

  -
    All arguments starting with `+` are considered
    [COMMANDS](#COMMANDS "wikilink") for this
    tool. All arguments starting with `--` are considered
    [OPTIONS](#OPTIONS "wikilink") for
    this tool.

<!-- end list -->

  -
    Reading any data from STDIN or here-documents is not yet supported.
    It's reserved for future use.

##### Environment variables

  -
    Following environment variables are incorporated:
      - OPENSSL - if set, full path to openssl executable
      - OPENSSL_CONF - if set, full path to openssl's openssl.cnf or
    directory where to find openssl.cnf
      - LD_LIBRARY_PATH - used and extended with definitions from
        options

##### Requirements

  -
    For checking all ciphers and all protocols with *+cipherall*
    command,
    **just perl (5.x) without any modules** is required.
    For *+info* and *+check* (and all related) commands, perl (5.x) with
    following modules (minimal version) is required:

:\* IO 1.25 (2011)

:\* IO::Socket:INET 1.37 (2011)

:\* IO::Socket:SSL 1.90 (2013)

:\* Net::DNS 0.66 (2011)

:\* Net::SSLeay 1.49 (2012)

  -
    However, it is recommended to use the most recent version of the
    mod-
    ules which then gives more accurate results and less warnings. If
    the
    modules are missing, they can be installed i.e. with:

`  cpan Net::SSLeay`

  -
    Note: if you want to use advanced features of openssl or
    Net::SSLeay,
    please see [INSTALLATION](#INSTALLATION "wikilink") section how to
    compile and install the tools
    fully customized.

<!-- end list -->

  -
    Also an *openssl* executable should be available, but is not
    mandatory.

<!-- end list -->

  -
    For checking DH parameters of ciphers, openssl 1.0.2 or newer should
    be available. If an older version of openssl is found, we try hard
    to
    extract the DH parameters from the data returned by the server, see
    *+cipher-dh* command.

<!-- end list -->

  -
    If you need to run on systems with older perl or perl module
    versions
    please refer to the [DEBUG](#DEBUG "wikilink") section for more
    inofrmation.

#### RESULTS

  -
    All output is designed to be easily parsed by postprocessors. Please
    see [OUTPUT](#OUTPUT "wikilink") section below for details.

<!-- end list -->

  -
    For the results, we have to distinguish those returned by *+cipher*
    command and those from all other tests and checks like *+check* or
    *+info* command.

###### \+cipher

  -
    The cipher checks will return one line for each tested cipher. It
    contains at least the cipher name, `yes` or `no` whether it's
    supported or not, and a security qualification. It may look like:

`   AES256-SHA       yes    HIGH`
`   NULL-SHA         no     weak`

  -
    Depending on the used *--legacy=\** option the format may differ
    and also contain more information. For details see *--legacy=\**
    option below.

<!-- end list -->

  -
    The text for security qualifications are mainly those returned by
    openssl (version 1.0.1): LOW, MEDIUM, HIGH and WEAK.
    The same texts but with all lower case characters are used if the
    qualification was adapted herein. Following rules for adjusting the
    qualification were used:

:\* weak:

:\*\* all \*NULL\* ciphers

:\*\* all \*RC4\* ciphers

:\*\* all \*EXPORT\* ciphers

:\*\* all \*anon\* (aka ADH aka DHA) ciphers

:\*\* all \*CBC\* and \*CBC3\* (aka 3DES) ciphers

:\* low:

:\* high:

:\*\* all \*AES(128 |256)\* ciphers

:\*\* all \*CAMELLIA\* ciphers

###### \+check

  -
    These tests return a line with a label describing the test and a
    test result for it. The idea is to report `yes` if the result
    is considered "secure" and report the reason why it is considered
    insecure otherwise. Example of a check considered secure:

`       Label of the performed check:           yes`

  -
    Example of a check considered insecure:

`       Label of the performed check:           no (reason why)`

  -
    Note that there are tests where the results appear confusing when
    first viewed, like for www.wi.ld:

`       Certificate is valid according given hostname:  no (*.wi.ld)`
`       Certificate's wildcard does not match hostname: yes`

  -
    This can for example occur with:

`       Certificate Common Name:                *.wi.ld`
`       Certificate Subject's Alternate Names:  `<DNS:www.wi.ld>

  -
    Please check the result with the *+info* command also to verify
    if the check sounds reasonable.

###### \+info

  -
    The test result contains detailed information. The labels there
    are mainly the same as for the "+check" command.

#### COMMANDS

  -
    There are commands for various tests according the SSL connection to
    the target, the targets certificate and the used ciphers.

<!-- end list -->

  -
    All commands are preceded by a `+` to easily distinguish from other
    arguments and options. However, some *--OPT* options are treated as
    commands for historical reason or compatibility to other programs.

<!-- end list -->

  -
    The most important commands are (in alphabetical order):

<!-- end list -->

  -
    *+check* *+cipher* *+info* +http'' *+list* *+quick* *+sni*
    *+sni_check* *+version*

<!-- end list -->

  -
    A list of all available commands will be printed with

`   o-saft.pl --help=cmds`

  -
    The description of all other commands will be printed with

`   o-saft.pl --header --help=commands`

  -
    The summary and internal commands return requested information or
    the
    results of checks. These are described below.

<!-- end list -->

  -
    Note that some commands may be a combination of other commands, see:

`   o-saft.pl --header --help=intern`

  -
    The following sub-sections only describe the commands, which do more
    than giving a simple information from the target. All other commands
    can be listed with:

`   $0 --header --help=commands`

  -
    The final sub-sections [Notes about
    commands](#Notes_about_commands "wikilink") describes some notes
    about special commands and related commands.

##### Commands for information about this tool

  -
    All these commands will exit after execution (cannot be used
    together
    with other commands).

###### \+ciphers

  -
    Show ciphers offered by local SSL implementation.

<!-- end list -->

  -
    This commands prints the ciphers in format like `openssl ciphers`
    does. It also accepts the *-v* and *-V* option. The *--legacy=TYPE*
    option can be used as described for *+list* command.
    Use *+list* command for more information according ciphers.

###### \+list

  -
    Show all ciphers known by this tool. This includes cryptogrphic
    details of the cipher and some internal details about the rating.

<!-- end list -->

  -
    In contrast to *+ciphers* command *+list* uses TAB characters
    instead of spaces to seperate columns. It also prints table header
    lines by default.

<!-- end list -->

  -
    Different output formats are used for the *--legacy* option:
      - \--legacy=simple - tabular output of cipher values
      - \--legacy=full - as *--legacy=simple* but more data
      - \--legacy=openssl - output like with *+cipher* command
      - \--legacy=ssltest - output like `ssltest --list`

\-- disabled since VERSION 15.01.07

  -
    Use *--v* option to show more details.

\--\>

###### \+VERSION

  -
    Just show version and exit.

###### \+version

  -
    Show version information for both the program and the Perl modules
    that it uses, then exit.

<!-- end list -->

  -
    Use *--v* option to show more details.

###### \+libversion

  -
    Show version of openssl.

###### \+quit

  -
    Show internal data and exit, used for testing and debugging only.
    Please see [TESTING](#NTESTING "wikilink") below.

##### Commands to check SSL details

  -
    Following (summary, internal) commands are simply a shortcut for
    a list of other commands. For details of the list use:

`   o-saft.pl --help=intern`

###### \+check

  -
    Check the SSL connection for security issues. Implies *+cipher* .

###### \+host +target

  -
    Print details about the targets hostname, DNS, etc.
    These details are usually printed only for the *+check* and *+info*
    command, but not for any individual command.

###### \+http

  -
    Perform HTTP checks (like STS, redirects etc.).

###### \+info

  -
    Overview of most important details of the SSL connection.

<!-- end list -->

  -
    Use *--v* option to show details also, which span multiple lines.

###### \+info--v

  -
    Overview of all details of the SSL connection. This is a shortcut
    for all commands listed below but not including *+cipher*.

<!-- end list -->

  -
    This command is intended for debugging as it prints some details
    from the used *Net::SSLinfo* module.

###### \+quick

  -
    Quick overview of checks. Implies *--enabled* and *--label=short*.

###### \+pfs

  -
    Check if servers offers ciphers with prefect forward secrecy (PFS)

###### \+protocols

  -
    Check for protocols supported by target.

###### \+vulns

  -
    Check for various vulnerabilities.

###### \+sts +hsts

  -
    Various checks according STS HTTP header.
    This option implies *--http*, means that *--no-http* is ignored.

###### \+sni

  -
    Check for Server Name Indication (SNI) usage.

###### \+sni_check +check_sni

  -
    Check for Server Name Indication (SNI) usage and validity of all
    names (CN, subjectAltName, FQDN, etc.).

###### \+bsi

  -
    Various checks according BSI TR-02102-2 and TR-03116-4 compliance.

###### \+ev

  -
    Various checks according certificate's extended Validation (EV).

<!-- end list -->

  -
    Hint: use option *--v --v* to get information about failed checks.

###### \+sizes

  -
    Check length, size and count of some values in the certificate.

###### \+s_client

  -
    Dump data retrieved from `openssl s_client ...` call. Should be
    used for debugging only.
    It can be used just like openssl itself, for example:

`        openssl s_client -connect host:443 -no_sslv2`

###### \+dump

  -
    Dumps internal data for SSL connection and target certificate.
    This is mainly for debugging and should not be used together with
    other commands (except *+cipher*).
    Each key-value pair is enclosed in `#{` and `#}` .

<!-- end list -->

  -
    Using *--trace --trace* dumps data of *Net::SSLinfo* too.

###### \+exec

  -
    Command used internally when requested to use other libraries.
    This command should not be used directly.

##### Commands to test ciphers provided by target

  -
    Beside the description of the commands itself here, please see also
    [\#Notes about commands](#Notes_about_commands "wikilink") below.

###### \+cipher

  -
    Check target for ciphers, either all ciphers or ciphers specified
    with *--cipher=\** option.

<!-- end list -->

  -
    Note that ciphers not supported by the local SSL implementation
    are not checked by default, use *+cipherall* or *+cipherraw* command
    for that.

<!-- end list -->

  -
    Use *--v* option to see all ciphers being checked.

###### \+cipherraw

  -
    Check target for all possible ciphers.
    Does not depend on local SSL implementation.

<!-- end list -->

  -
    In contrast to *+cipher* this command has some options to tweak
    the cipher tests, connection results, and some strange behaviours
    of the target. See [\#Options for cipherall and cipherraw
    command](#Options_for_cipherall_and_cipherraw_command "wikilink")
    for details.

###### \+cipherall

  -
    Same as *+cipherraw* but ouput format similat to *+cipher* command.

###### \+cipher-default

  -
    Lists the cipher selected by the server for each protocol sometimes
    referred to as "default cipher".
    For each protocol the two selected ciphers are shown, one returned
    by the server if the cipher list in the ClientHello is sorted with
    the strongest cipher first, and one returned if the cipher list in
    the ClientHello is sorted with strongest cipher last.
    See [\#Notes about commands](#Notes_about_commands "wikilink") for
    details.

###### \+cipher-dh

  -
    Checked target for ciphers. All ciphers supported by the server are
    printed with their DH or ECDH paramaters (if available).
    ciphers.

###### \+cipher-null +null

  -
    Check if target accepts NULL ciphers.

###### \+cipher-adh +adh

  -
    Check if target accepts ciphers with anonymous key exchange.

###### \+cipher-exp +export

  -
    Check if target accepts EXPORT ciphers.

###### \+cipher-cbc +cbc

  -
    Check if target accepts CBC ciphers.

###### \+cipher-des +des

  -
    Check if target accepts DES ciphers.

###### \+cipher-rc4

  -
    Check if target accepts RC4 ciphers.

###### \+cipher-edh +edh

  -
    Check if target supports ephemeral ciphers.

###### \+cipher-pfs

  -
    Check if target supports ciphers with PFS.

###### \+cipher-strong

  -
    Check if target selects strongest cipher.

###### \+cipher-weak

  -
    Check if target selects weak cipher (oposite of *+cipher-strong*).

##### Discrete commands to test SSL connection and certificate details

  -
    Discrete commands, please see:

`   o-saft.pl --help=commands`

##### Notes about commands

###### \+cipher vs. +cipherall

  -
    *+cipher* can only check for ciphers - more precise: cipher suites -
    provided by the local SSL implementation (i.e. libssl).
    *+cipherall* can check for any cipher, as it just uses the cipher's
    integer value in the range 0 .. 65532.

###### \+cipherall vs. +cipherraw

  -
    These commands are identical, just the output format is different.

###### \+cipher vs. +cipher-default

  -
    Both commands show the default cipher foreach protocol.

<!-- end list -->

  -
    *+cipher* lists a summary of ciphers selected by the server for each
    protocol requested by the user (for example by using options like:
    *--sslv3* *--tlsv1* etc.). When the --v option is used, all selected
    ciphers for all known protocols are listed. This summary focuses on
    counts for various ciphers.

<!-- end list -->

  -
    *+cipher-default* lists the selected cipher by the server for each
    protocol.

###### \+cipher-selected vs. +cipher-default

  -
    *+cipher-selected* lists the cipher selected by the server if no
    particular
    protocol was specified and the system's default cipher list is send
    in the ClientHello to the server.

<!-- end list -->

  -
    *+cipher-default* lists the selected cipher by the server for each
    protocol.

###### \+cipher-strong vs. +cipher-default

  -
    *+cipher-strong* shows the result of the check if strong ciphers are
    preferred by the server. It is a check command.

<!-- end list -->

  -
    *+cipher-default* lists the cipher selected by the server for each
    protocol. It is a information command.

<!-- end list -->

  -
    It is not possible to check if a server uses 'SSLHonorCipherOrder'.
    Even if it is used (switched on), it is not possible to check the
    specified order of the ciphers.

<!-- end list -->

  -
    I. g. it is expected that the order is according the cipher suite's
    strength, meaning the most strongest first, and the weakest last.
    It does not make sense to use an order where a weak cipher preceeds
    a stronger one. Such a (mis-)configuration should be detected.

<!-- end list -->

  -
    Having this in mind, the algorithm to detect a proper cipher order
    is as simply as follows:

`   1. pass sorted cipher list with strongest cipher first`
`   2. pass sorted cipher list with strongest cipher last`

  -
    if the server returns the same cipher for both checks, it's assumed
    that it prefers to use the most strongest cipher. In this case it's
    obvious that 'SSLHonorCipherOrder' is set (exceptions see below).

<!-- end list -->

  -
    *+cipherall* uses a more accurate algorithm to detect the server's
    cipher order.

<!-- end list -->

  -
    **Exceptions:**
    If either, the server or the client, uses only one cipher suite in
    the list, SSLHonorCipherOrder cannot be detected at all.
    The same happens, if only one cipher in the client's list matches a
    cipher in the server's list.

###### \+extensions vs. +tlsextensions

  -
    *+extensions* shows the "Certificate extensions" and
    *+tlsextensions*
    will show the TLS protocol extensions.
    Use *+tlsextdebug* to show more informations about the TLS protocol
    extensions.

###### \+http2 +spdy +spdy3 +spdy31 +spdy4 +prots

  -
    These commands are just an alias for the *+protocols* command.

###### \+hostname vs. +wildhost vs. +altname vs. +rfc_2818

  -
    The commands *+cn* and *+altname* print the information stored in
    the certificate.
    The command *+hostname* checks if the given hostname matches the CN
    value in the certificate. Note that wildcard names in the CN, only
    allow to contain one '\*'.
    The command *+wildcard* checks if the given hostname does not match
    any name specified in the certificate's "subjectAltname". This check
    is usefull if the certificate and the configuration must comply to
    RFC 6125 or EV certificates.

#### OPTIONS

  -
    All options are written in lowercase. Words written in all capital
    in
    the description here is text provided by the user.

##### Options for help and documentation

###### \--h

###### \--help

  -
    WYSIWYG

\====== --help=help ======

  -
    Show available options to show descriptions (this Options section).

\====== --help=cmds======

  -
    Show available commands.

\====== --help=commands======

  -
    Show available commands with short description.

\====== --help=opt======

  -
    Show available options; short form.

\====== --help=options======

  -
    Show available options with their description.

\====== --help=checks======

  -
    Show available checks.

\====== --help=tools======

  -
    Description of tools around O-Saft, when, where and how to use.

\====== --help=cmd======

  -
    Show additional and user specified commands.

\====== --help=cfg-cmd======

  -
    Show additional and user specified commands. Output can be use in
    [RC-FILE](#RC-FILE "wikilink") or as option.

\====== --help=check-cfg --help=cfg-check======

  -
    Show texts used as labels in output for checks (see *+check*) ready
    for use in [RC-FILE](#RC-FILE "wikilink") or as option.

\====== --help=data======

  -
    Show available informations.

\====== --help=data-cfg --help=cfg-data --help=cfg-info======

  -
    Show texts used as labels in output for data (see *+info*) ready
    for use in [RC-FILE](#RC-FILE "wikilink") or as option.

\====== --help=hint======

  -
    Show texts used in hint messages.

\====== --help=hint-cfg --help=cfg-hint======

  -
    Show texts used in hint messages ready for use in
    [RC-FILE](#RC-FILE "wikilink") or as
    option.

\====== --help=text======

  -
    Show texts used in various messages.

\====== --help=text-cfg --help=cfg-text======

  -
    Show texts used in various messages ready for use in
    [RC-FILE](#RC-FILE "wikilink") or
    as option.

\====== --help=legacy======

  -
    Show possible legacy formats (used as value in
    [--legacy=KEY](#--legacy=KEY "wikilink")).

\====== --help=compliance======

  -
    Show available compliance checks.

\====== --help=intern======

  -
    Show internal commands.

\====== --help=range======

  -
    Show list of cipherranges (see
    [\#--cipherrange=RANGE--cipherrange=RANGE](#--cipherrange=RANGE--cipherrange=RANGE "wikilink")).

\====== --help=alias======

  -
    Show alias for commands and options.

\====== --help=pattern======

  -
    Show list of cipher pattern (used for
    [--cipher=CIPHER](#--cipher=CIPHER "wikilink")).

\====== --help=score======

  -
    Show score value for each check.
    Value is printed in format to be used for *--cfg_score=KEY=SCORE*.

<!-- end list -->

  -
    Note that the sequence of options is important. Use the options
    *--trace* and/or *--cfg_score=KEY=SCORE* before *--help=score*.

\====== --help=toc --help=content======

  -
    Show headlines from help textsUseful to get an overview.

\====== --help=SECTION======

  -
    Show `SECTION` from documentation, see
    [--help=toc](#--help=toc "wikilink") for a list.
    Example:

`     o-saft.pl --help=EXAMPLES`

\====== --help=regex======

  -
    Show regular expressions used internally.

\====== --help=gen-html======

  -
    Show help text in HTML format.

\====== --help=gen-pod======

  -
    Show help text in POD format.

\====== --help=gen-wiki======

  -
    Show help text in mediawiki format.

\====== --help=gen-cgi======

  -
    Generate HTML page with o-saft.cgi as form action..

\====== --help=error --help=warning --help=problem ======

  -
    Show [KNOWN PROBLEMS](#KNOWN_PROBLEMS "wikilink") section with
    description of known error and
    warning messages.

\====== --help=FAQ ======

  -
    Show [KNOWN PROBLEMS](#KNOWN_PROBLEMS "wikilink") and
    [LIMITATIONS](#LIMITATIONS "wikilink") section.

\====== --help=glossar======

  -
    Show common abbreviation used in the world of security.

\====== --help=links======

  -
    Show list of URLs related to SSL/TLS.

\====== --help=rfc======

  -
    Show list of RFC related to SSL/TLS.

\====== --help=todo======

  -
    Show known problems and bugs.

\====== --help=exit======

  -
    Show possible *--exit=KEY* options. Used for debugging only.

\====== --help=program.code======

  -
    For developers.

##### Options for all commands (general)

###### \--dns

  -
    Do DNS lookups to map given hostname to IP, do a reverse lookup.

###### \--no-dns

  -
    Do not make DNS lookups.
    Note that the corresponding IP and reverse hostname may be missing
    in some messages then.

\====== --host=HOST======

  -
    Specify `HOST` as target to be checked. Legacy option.

\====== --port=PORT======

  -
    Specify target's `PORT` to be used. Legacy option.

\====== --host=HOST --port=PORT HOST:PORT HOST======

  -
    When giving more than one HOST argument, the sequence of the given
    HOST argument and the given *--port=PORT* and the given
    *--host=HOST*
    options are important.
    The rule how ports and hosts are mapped is as follows:
    \* HOST:PORT arguments are used as is (connection to HOST on PORT)
    \* only HOST is given, then previous specified *--port=PORT* is used
    Note that URLs are treated as HOST:PORT, if they contain a port.
    Example:

`   o-saft.pl +cmd host-1 --port 23 host-2 host-3:42 host-4`

  -
    will connect to:

`      host-1:443`
`      host-2:23`
`      host-3:42`
`      host-4:23`

\====== --proxyhost=PROXYHOST --proxy=PROXYHOST:PROXYPORT======

  -
    Make all connection to target using `PROXYHOST`.

<!-- end list -->

  -
    Also possible is: *--proxy=PROXYUSER:PROXYPASS@PROXYHOST:PROXYPORT*

\====== --proxyport=PROXYPORT======

  -
    Make all connection to target using PROXYHOST:PROXYPORT.

\====== --proxyuser=PROXYUSER======

  -
    Specify username for proxy authentication.

\====== --proxypass=PROXYPASS======

  -
    Specify password for proxy authentication.
    *--proxy=PROXYUSER:PROXYPASS@PROXYHOST:PROXYPORT* is also possible.

###### \--starttls

  -
    Use `STARTTLS` command to start a TLS connection via SMTP.
    This option is a shortcut for *--starttls=SMTP*

\====== --starttls=PROT======

  -
    Use `STARTTLS` command to start a TLS connection via protocol.
    `PROT` may be any of: `SMTP`, `IMAP`, `IMAP2`, `POP3`, `FTPS`,
    `LDAP`, `RDP`, `XMPP`

<!-- end list -->

  -
    For *--starttls=SMTP* see *--dns-mx* also to use MX records instead
    of host

\====== --starttls-delay=SEC======

  -
    Number of seconds to wait before sending a packet, to slow down the
    `STARTTLS` requests. Default is 0.
    This may prevent blocking of requests by the target due to too much
    or too fast connections.
    Note: In this case there is an automatic suspension and retry with
    a longer delay.

###### \--cgi, --cgi-exec

  -
    Internal use for CGI mode only.

##### Options for SSL tool

###### \--no-rc

  -
    Do not read [RC-FILE](#RC-FILE "wikilink") .

###### \--rc

  -
    Read [RC-FILE](#RC-FILE "wikilink") if exists, from directory where
    program was found.

\====== --rc=path/to/FILE ======

  -
    Read [RC-FILE](#RC-FILE "wikilink") `path/to/FILE` if exists.

###### \--exitcode

  -
    The exit status code will be greater 0, if any of following applies:
      - any check returns `no`
      - insecure protocols are available
      - insecure ciphers are supported
      - ciphers without PFS are supported
    In particular, the status code will be the total count of all these
    checks. The status code will also be printed at end, like:

`   # EXIT 23`

  -
    Parts of these checks can be diasabled, see *--exitcode-\** options
    below.

<!-- end list -->

  -
    Use *--v* or *--exitcode-v* to see details about the performed
    checks.

<!-- end list -->

  -
    Functionality implemented experimental, may change in future.

###### \--exitcode-v

  -
    Print information about persormed checks.

###### \--exitcode-quiet

  -
    Do not print status code at end.

###### \--exitcode-no-checks

  -
    Do not count checks with result 'no' for *--exitcode* .

###### \--exitcode-no-low --exitcode-no-weak --exitcode-no-medium

  -
    Do not count `LOW`, `WEAK` or `MEDIUM` security ciphers for
    *--exitcode* .

###### \--exitcode-no-ciphers

  -
    Do not count any ciphers for *--exitcode* .

###### \--exitcode-no-ciphers

  -
    Do not count any ciphers for *--exitcode* .

###### \--exitcode-no-pfs

  -
    Do not count ciphers without PFS for *--exitcode* .

###### \--openssl-s_client --s_client

  -
    Use `openssl s_slient ...` call to retrieve more informations from
    the SSL connection. This is disabled by default on Windows because
    of performance problems. Without this option (default on Windows \!)
    following informations are missing:

`      compression, expansion, renegotiation, resumption,`
`      selfsigned, verify, chain, protocols, DH parameters`

  -
    See *Net::SSLinfo* for details.

<!-- end list -->

  -
    If used together with *--trace*, s_client data will also be printed
    in debug output of *Net::SSLinfo*.

###### \--no-openssl

  -
    Do not use external `openssl` tool to retrieve informations. Use of
    `openssl` is disabled by default on Windows.
    Note that this results in some missing informations, see above.

\====== --openssl=TOOL======

  -
    `TOOL` can be a path to openssl executable; default: openssl

\====== --openssl-cnf=FILE --openssl-conf=FILE======

  -
    `FILE` path of directory or full path of openssl.cnf

<!-- end list -->

  -
    If set, environment variable OPENSSL_CONF will be set to given path
    (or file) when *openssl(1)* is started. Please see openssl's man
    page
    for details about specifying alternate openssl.cnf files.

###### \--openssl-ciphers --force-openssl

  -
    Use openssl to check for supported ciphers; default: IO::Socket

<!-- end list -->

  -
    This option forces to use `openssl s_slient -connect CIPHER ..` to
    check if a cipher is supported by the remote target. This is useful
    if the *--lib=PATH* option doesn't work (for example due to changes
    of the API or other incompatibilities).

\====== --exe-path=PATH --exe=PATH======

  -
    `PATH` is a full path where to find openssl.

\====== --lib-path=PATH --lib=PATH======

  -
    `PATH` is a full path where to find libssl.so and libcrypto.so

<!-- end list -->

  -
    See [HACKER's INFO](#HACKER's_INFO "wikilink") below for a detailed
    description how it works.

\====== --envlibvar=NAME======

  -
    `NAME` is the name of a environment variable containing additional
    paths for searching dynamic shared libraries.
    Default is LD_LIBRARY_PATH .

<!-- end list -->

  -
    Check your system for the proper name, i.e.:
    DYLD_LIBRARY_PATH, LIBPATH, RPATH, SHLIB_PATH .

###### \--ssl-error

  -
    The connection to a target may fail, or even block, due to various
    reasons, for example lost network at all, blocking at firewall, etc.
    In particular when checking ciphers with
    [+cipher](++cipher "wikilink") , this may result
    in long delays until results are printed.
    Using this option stops trying to do more connections to the target
    when [--ssl-error-max=CNT](#--ssl-error-max=CNT "wikilink")
    consecutive errors occoured, or if the total
    amount of errors increases
    [--ssl-error-total=CNT](#--ssl-error-total=CNT "wikilink").

\====== --ssl-error-max=CNT======

  -
    Max. amount of consecutive errors (default: 5).

\====== --ssl-error-timeout=SEC======

  -
    Timeout in seconds when a failed connection is treated as error and
    then counted (default: 1).

\====== --ssl-error-total=CNT======

  -
    Max. total amount of errors (default: 10).

###### \--ssl-lazy

  -
    I.g. this tools tries to identify available functionality according
    SSL versions from the underlaying libraries. Unsupported versions
    are then disables and a warning is shown.
    Unfortunately some libraries have not implemented all functions to
    check availability of a specific SSL version, which then results in
    a compile error.

<!-- end list -->

  -
    This option disables the strict check of availability.
    If the underlaying library doesn't support the required SSL version
    at all, following error may occour:

`      Can't locate auto/Net/SSLeay/CTX_v2_new.al in @INC ...`

\====== --timeout=SEC======

  -
    Timeout in seconds when connecting to the target (default: 2).

###### \-v

  -
    Print list of ciphers in style like: `openssl ciphers -v`.
    Option used with *+ciphers* command only.

###### \-V

  -
    Print list of ciphers in style like: `openssl ciphers -V`.
    Option used with *+ciphers* command only.

##### Options for SSL connection to target

\====== --cipher=CIPHER======

  - `CIPHER` can be any string accepeted by openssl or following:
  - `yeast` use all ciphers from list defined herein, see *+list*

<!-- end list -->

  -
    Beside the cipher names accepted by openssl, CIPHER can be the name
    of the constant or the (hex) value as defined in openssl's files.
    Currently supported are the names and constants of openssl 1.0.1k .
    Example:

<!-- end list -->

  - \--cipher=DHE_DSS_WITH_RC4_128_SHA
  - \--cipher=0x03000066
  - \--cipher=66

<!-- end list -->

  -
    will be mapped to DHE-DSS-RC4-SHA

<!-- end list -->

  -
    Note: if more than one cipher matches, just one will be selected.
    Default is `ALL:NULL:eNULL:aNULL:LOW` as specified in Net::SSLinfo

###### \--socket-reuse

  -
    TCP socket will be reused for next connection attempt even if SSL
    connection failed.

###### \--no-socket-reuse

  -
    Close TCP socket and then reopen for next connection attempt if SSL
    connection failed.

<!-- end list -->

  -
    This is useful for some servers which may return an "TLS alert" if
    the connection fails and then fail again on the same socket.

###### \--ignore-no-connect

  -
    A simple check if the target can be connected will be performed by
    default. If this check fails, the target will be ignored, means no
    more reuqested checks will be done. As this connection check some-
    times fails due to various reasons, the check can be disabled using
    this option.

###### \--no-md5-cipher

  -
    Do not use \*-MD5 ciphers for other protocols than SSLv2.
    This option is only effective with *+cipher* command.

<!-- end list -->

  -
    The purpose is to avoid warnings from IO::Socket::SSL like:

`        Use of uninitialized value in subroutine entry at lib/IO/Socket/SSL.pm line 430.`

  -
    which occours with some versions of IO::Socket::SSL when a \*-MD5
    ciphers will be used with other protocols than SSLv2.

<!-- end list -->

  -
    Note that these ciphers will be checked for SSLv2 only.

###### \--SSL, -protocol SSL

###### \--no-SSL

  - `SSL` can be any of:

<!-- end list -->

  -
    ssl, ssl2, ssl3, sslv2, sslv3, tls1,
    tls1, tls11, tls1.1, tls1-1, tlsv1, tlsv11, tlsv1.1, tlsv1-1
    (and similar variants for tlsv1.2).
    For example *--tls1* *--tlsv1* *--tlsv1_1* are all the same.

<!-- end list -->

  -
    (*--SSL* variants): Test ciphers for this SSL/TLS version.
    (*--no-SSL* variants): Don't test ciphers for this SSL/TLS version.

###### \--no-tcp

  -
    Shortcut for:
    *--no-sslv2 --no-sslv3 --no-tlsv1 --no-tlsv11 --no-tlsv12
    --no-tlsv13*

###### \--tcp

  -
    Shortcut for: *--sslv2 --sslv3 --tlsv1 --tlsv11 --tlsv12 --tlsv13*

###### \--no-udp

  -
    Shortcut for:
    *--no-dtlsv09 --no-dtlsv1 --no-dtlsv11 --no-dtlsv12 --no-dtlsv13*

###### \--udp

  -
    Shortcut for: *--dtlsv09 --dtlsv1 --dtlsv11 --dtlsv12 --dtlsv13*

###### \--nullsslv2

  -
    This option forces to assume that SSLv2 is enabled even if the
    target does not accept any ciphers.

<!-- end list -->

  -
    The target server may accept connections with SSLv2 but not allow
    any cipher. Some checks verify if SSLv2 is enabled at all, which
    then would result in a failed test.
    The default behaviour is to assume that SSLv2 is not enabled if no
    ciphers are accepted.

###### \--http

  -
    Make a HTTP request if cipher is supported.

<!-- end list -->

  -
    If used twice debugging will be enabled using environment variable
    `HTTPS_DEBUG` .

###### \--no-http

  -

    Do not make HTTP request.

###### \--sni

  -

    Make SSL connection in SNI mode.

###### \--no-sni

  -
    Do not make SSL connection in SNI mode (default: SNI mode).

###### \--sni-toggle --toggle-sni

  -
    Test with and witout SNI mode (*+cipherall* only).

###### \--force-sni

  -
    Do not check if SNI seems to be supported by *Net::SSLeay(1)*.
    Older versions of openssl and its libries do not support SNI or the
    SNI support is implemented buggy. By default it's checked if SNI is
    properly supported. With this option this check can be disabled.

<!-- end list -->

  -
    Be warned that this may result in improper results.

\====== --servername=NAME====== ====== --sni-name=NAME======

  -
    If in SNI mode is active, see *--sni* above, `NAME` is used instead
    of
    hostname for connections to the target. If SNI mode is not active,
    see *--no-sni* above, `NAME` is not used. The default is undefined,
    which forces to use the given FQDN.

<!-- end list -->

  -
    This is useful, for example when an IP instead of a FQDN was given,
    where a correct hostname (i.g. a FQDN) needs to be specified.

<!-- end list -->

  -
    Note: i.g. there is no need to use this option, as a correct value
    for the SNI name will be choosen automatically (except for IPs).
    However, it is kind of fuzzing ...even setting to an empty string
    is possible.

<!-- end list -->

  -
    Limitation: the same `NAME` is used for all targets, if more than
    one target was specified.

###### \--no-cert

  -

    Do not get data from target's certificate, return empty string.

###### \--no-cert --no-cert

  -

    Do not get data from target's certificate, return default string

    of *Net::SSLinfo* (see *--no-cert-text TEXT* option).

\====== --no-cert-text=TEXT======

  -

    Set `TEXT` to be returned from `Net::SSLinfo.pm` if no certificate

    data is collected due to use of *--no-cert*.

\====== --ca-depth=INT======

  -

    Check certificate chain to depth `INT` (like openssl's -verify).

\====== --ca-file=FILE======

  -

    Use `FILE` with bundle of CAs to verify target's certificate chain.

\====== --ca-path=DIR======

  -

    Use `DIR` where to find CA certificates in PEM format.

###### \--no-nextprotoneg

  -
    Do not use `-nextprotoneg` option for openssl.

\====== --proto-alpn=NAME======

  -
    Name of protocol to be added to list of applcation layer protocols
    (ALPN), which is used for any connection to the targets.
    See *--cipher-alpn=NAME* also.

\====== --proto-npn=NAME======

  -
    Name of protocol to be added to list of next protocol negotiations
    (NPN), which is used for any connection to the targets.
    See *--cipher-npn=NAME* also.

###### \--ssl-compression --compression

  -
    Use SSL option "compression" for connection.

###### \--no-ssl-compression --no-compression

  -
    Use SSL option "no compression" for connection (default: don't use)

###### \--no-reconnect

  -
    Do not use `-reconnect` option for openssl.

###### \--no-tlsextdebug

  -

    Do not use `-tlsextdebug` option for openssl.

\====== --sclient-opt=VALUE======

  -

    Argument or option passed to openssl s_client command.

##### Options for *+cipher* command

\====== --cipher-alpn=NAME======

  -
    Name of protocol to be added to list of applcation layer protocols
    (ALPN), which is used for cipher checks.

:\* *--cipher-alpn=,* sets empty list.

:\* *--cipher-alpn=,,* sets list to empty element "".

\====== --cipher-npn=NAME======

  -
    Name of protocol to be added to list of next protocol negotiations
    (NPN), which is used for cipher checks.

:\* *--cipher-lpn=,* sets empty list.

:\* *--cipher-lpn=,,* sets list to empty element "".

  -
    Note: setting empty list or element most likely does not work with
    openssl executable (i.e. --force-openssl).

\====== --cipher-curve=NAME======

  -
    Name of ecliptic curve to be added to list of ecliptic curves (EC),
    which is used for cipher checks.

:\* *--cipher-curve=,* sets empty list.

:\* *--cipher-curve=,,* sets list to empty element "".

  -
    Note: setting empty list or element most likely does not work with
    openssl executable (i.e. *--force-openssl*).

##### Options for cipherall and cipherraw command

\====== --range=RANGE ====== ====== --cipherrange=RANGE======

  -
    Specify range of cipher constants to be tested by *+cipherall* .
    Following `RANGE`s are supported (see also
    [--cipherrange=RANGE](#--cipherrange=RANGE "wikilink")):

<!-- end list -->

  - `rfc` all ciphers defined in various RFCs
  - `shifted` `rfc`, shifted by 64 bytes to the right
  - `long` like `rfc` but more lazy list of
  - `huge` all constants 0x03000000 .. 0x0300FFFF
  - `safe` all constants 0x03000000 .. 0x032FFFFF
  - `full` all constants 0x03000000 .. 0x0300FFFF
  - `SSLv2` all ciphers according RFC for SSLv2

<!-- end list -->

  -
    Note: `SSLv2` is the internal list used for testing SSLv2 ciphers.
    It does not make sense to use it for other protocols; however ...

\====== --slow-server-delay=SEC======

  -
    Additional delay in seconds after the server is connected using a
    proxy or before starting STARTTLS.
    This is useful when connecting via slow proxy chains or connecting
    to slow servers before sending the STARTTLS sequence.

\====== --ssl-maxciphers=CNT ======

  -
    Maximal number of ciphers sent in a sslhello (default: 32).

###### \--ssl-double-reneg

  -
    Send SSL extension "reneg_info" even if list of ciphers includes
    TLS_EMPTY_RENEGOTIATION_INFO_SCSV (default: do not include)

###### \--ssl-nodata-nocipher

  -
    Do not abort testing for next cipher when the target responds with
    "NoData" times out. Useful for TLS intolerant servers.
    By default testing for ciphers is aborted when the target responds
    with "noData message.

###### \--ssl-use-ecc

  -
    Use supported elliptic curves. Default on.

###### \--ssl-use-ec-point

  -
    Use TLS "ec_point_formats" extension. Default on.

###### \--ssl-use-reneg

  -
    Test for ciphers with "secure renegotiation" flag set.
    Default: don't set "secure renegotiation" flag.

\====== --ssl-retry=CNT======

  -
    Number of retries when connection timed-out (default: 2).

\====== --ssl-timeout=SEC======

  -
    Number of seconds to wait until connection is qualified as timeout.

###### \--dns-mx, --mx

  -
    Get DNS MX records for given target and check the returned targets.
    (only useful with *--starttls=SMTP*)

##### Options for checks and results

  -

    Options used for *+check* command:

###### \--enabled

  -

    Only print result for ciphers accepted by target.

###### \--disabled

  -

    Only print result for ciphers not accepted by target.

###### \--ignorecase

  -

    Checks are done case insensitive.

###### \--no-ignorecase

  -
    Checks are done case sensitive. Default: case insensitive.
    Currently only checks according CN, alternate names in the target's
    certificate compared to the given hostname are effected.

###### \--ignore-no-reply

  -
    When checking for the TLS "heartbeat" extension, the server may not
    respond at all, which would result in a "no reply" message. This
    marks the check for *+heartbleed* as `no`.
    I.g. a server is not vulnerable to the heartbleed attack if the
    TLS "heartbeat" extension is disabled. Hence the check result `no`
    may be mis-leading. This option treats the "no reply" result as
    "not vulnerable" and returns `yes` then.

<!-- end list -->

  -
    Note: if the server does not respond for this check, does not mean
    that the "heartbeat" extension is switched off. If unsure, disable
    this lazy check with *--no-ignore-no-reply* .

##### Options for output format

  -

\====== --label=TYPE======

  -
    Defines the format of the descriptive text(label) for *+check* and
    *+info* command.

<!-- end list -->

  -
    Following `TYPE`s are supported:

\====== --label=long======

  -
    Prints full text for labels:

` Certificate Common Name:  some.tld`

\====== --label=short======

  -
    Prints short less descriptive text for labels:

` Common Name:              some.tld`

\====== --label=key======

  -
    Internal format: print name of key instead of text as label. Key is
    Prints name of key instead of text as label. The key is that of the
    internal data structure(s).

` [cn]                      some.tld`

\====== --legacy=TOOL======

  -
    For compatibility with other tools, the output format used for the
    result of the *+cipher* command can be adjusted to mimic the format
    of other SSL testing tools.

<!-- end list -->

  -
    The argument to the *--legacy=TOOL* option is the name of the tool
    to be simulated.

<!-- end list -->

  -
    Following `TOOL`s are supported:

<!-- end list -->

  - `sslaudit` format of output similar to sslaudit
  - `sslcipher` format of output similar to ssl-cipher-check
  - `ssldiagnos` format of output similar to ssldiagnos
  - `sslscan` format of output similar to sslscan
  - `ssltest` format of output similar to ssltest
  - `ssltestg` format of output similar to ssltest -g
  - `ssltest-g` format of output similar to ssltest -g
  - `sslyze` format of output similar to sslyze
  - `ssl-cipher-check` same as sslcipher
  - `ssl-cert-check` format of output similar to ssl-cert-check
  - `testsslserver` format of output similar to TestSSLServer.jar
  - `thcsslcHeck` format of output similar to THCSSLCheck

<!-- end list -->

  -
    Note that these legacy formats only apply to output of the checked
    ciphers. Other texts like headers and footers are adapted slightly.

<!-- end list -->

  -
    Please do not expect identical output as the `TOOL` when using these
    options, it's a best guess and should be parsable in a very similar
    way.

\======--legacy=TYPE====== ======--legacy=compact======

  -
    Internal format: mainly avoid tabs and spaces format is as follows:

`Some Label:<-- anything right of colon is data`

\======--legacy=full======

  -
    Internal format: pretty print each label in its own line, followed
    by data prepended by tab character (useful for *+info* only).

\====== --legacy=owasp======

  -
    Results for cipher checks use rating from OWASP Cipher Cheat Sheet.

\======--legacy=quick======

  -
    Internal format: use tab as separator; ciphers are printed with bit
    length (implies *--tab*).

\======--legacy=simple======

  -
    Internal default format.

\====== --format=FORM======

  -
    This option is used to specify the format of the result lines. This
    covers the value of the result line only.

<!-- end list -->

  - `raw` Print raw data as passed from *Net::SSLinfo* .

<!-- end list -->

  -
    Note: all data will be printed as is, without additional label
    or formatting. It's recommended to use the option in conjunction
    with exactly one command. Otherwise the user needs to know how
    to "read" the printed data.

<!-- end list -->

  - `hex` Convert some data to hex: 2 bytes separated by `:`.
  - `0x` Convert some data with hex values:

<!-- end list -->

  -
    2 bytes preceded by `0x` and separated by a space.

<!-- end list -->

  - `/x` Same as *--format=\\x*
  - `\x` Convert some data with hex values:

<!-- end list -->

  -
    2 bytes preceded by `\x` and no separating char.

###### \--header

  -

    Print formatting header. Default for *+check*, *+info*, *+quick*.

    and *+cipher* only.

###### \--no-header

  -
    Do not print formatting header.
    Usefull if raw output should be passed to other programs.

<!-- end list -->

  -
    Note: must be used on command line to inhibit all header lines.

\======--ignore-cmd=CMD====== ======--ignore-output=CMD======
======--no-cmd=CMD====== ======--no-output=CMD======

  -
    Do not print output (data or check result) for command `CMD`.
    `CMD` is any valid command, see [COMMANDS](#COMMANDS "wikilink"),
    without leading `+`.
    Option can be used multiple times.

###### \--score

  -

    Print scoring results. Default for *+check*.

###### \--no-score

  -

    Do not print scoring results.

\====== --separator=CHAR======

  -

\====== --sep=CHAR======

  -

    `CHAR` will be used as separator between label and value of the

    printed results. Default is `:`

###### \--tab

  -
    `TAB` character (0x09, \\t) will be used as separator between label
    and value of the printed results.
    As label and value are already separated by a `TAB` character, this
    options is only useful in conjunction with the *--legacy=compact*
    option.

###### \--showhost

  -
    Prefix each printed line with the given hostname (target).
    The hostname will be followed by the separator character.

\======--std-format=utf8====== ======--std-format=crlf======

\======--std-format=raw====== ======--std-format=unix======
======--std-format=CHARSET======

  -
    This option is used to specify the general output format for STDOUT
    and STDERR. All results are written to STDOUT, errors and warnings
    may also be written to STDERR . The default is `:unix:utf8`, which
    is the perlish definition used internally.

<!-- end list -->

  -
    Following values are supported:

:\* `raw`

:\* `unix` Print raw data, binary in bytes without conversion.

  -
    Note: binary here just means characters (as all output is text).

:\* `utf8` Convert all characters to UTF-8.

:\* `crlf` Use CR LF as end of line.

:\* `CHARSET` `CHARSET` can be any of the local installed character

  -
    sets, like UTF-8, UTF-16LE, CP1252, iso-8859-7, etc..
    This conversion may print its own warnings.

<!-- end list -->

  -
    The option can be used multiple times with different values.
    To reset the default behaviour, either `raw` or `unix` must be
    used. Obviously, they must be used first. All other values are used
    additionally.
    Note: `utf8` just defines the format of the characters, it does no
    further checks on the converted characters. In contrast, `UTF-8` is
    used as real encoding and does some checks.

<!-- end list -->

  -
    For more details, please see "perldoc -f binmode" .

<!-- end list -->

  -
    Currently (Jan. 2018), these options must be used before any
    *--help*
    option.

###### \--win-CR

  -
    Obsolete, please use *--std-format=crlf* .

##### Options for compatibility with other programs

  -
    Please see other programs for detailed description (if not
    obvious:).
    Note that often only the long form options are accepted as most
    short
    form options are ambiguous.
    If other programs use the same option,but with a different
    behaviour,
    then thes other options are not supported.
    For a list of supported options, please see:

` o-saft.pl --help=alias`

  -
    Following list contains only those options not shown with:

` o-saft.pl --help=alias`

`Tool's Option        (Tool)          o-saft.pl Option`
`--------------------+---------------+---------------------------`
` --checks CMD        (TLS-Check.pl)  same as `*`+CMD`*
` -h, -h=HOST         (various tools) same as `*`--host``   ``HOST`*
` -p, -p=PORT         (various tools) same as `*`--port``   ``PORT`*
` -t HOST             (ssldiagnos)    same as `*`--host``   ``HOST`*
` --protocol SSL      (ssldiagnos)    same as `*`--SSL`*
` --UDP               (ssldiagnos)    same as `*`--udp`*
` --insecure          (cnark.pl)      ignored`
` --nopct --nocolor   (ssldiagnos)    ignored`
` --timeout, --grep   (ssltest.pl)    ignored`
` -r,  -s,  -t,  -x   (ssltest.pl)    ignored`
` -connect, -H, -u, -url, -U          ignored`
` -noSSL                              same as `*`--no-SSL`*
` -no_SSL                             same as `*`--no-SSL`*
`--------------------+---------------+---------------------------`

  -
    For definition of `SSL` see *--SSL* and *--no-SSL* above.

##### Options for customization

  -

    For general descriptions please see
    [CUSTOMIZATION](#CUSTOMIZATION "wikilink") section below.

\====== --cfg_cmd=CMD=LIST======

  -
    Redefine list of commands. Sets %cfg{cmd-CMD} to `LIST`. Commands
    can be written without the leading `+`.
    If `CMD` is any of the known internal commands, it will be redifned.
    If `CMD` is a unknown command, it will be created.

<!-- end list -->

  -
    Example:

`   `*`--cfg_cmd=sni=sni``   ``hostname`*

  -
    To get a list of commands and their settings, use:

`   o-saft.pl --help=intern`

  -
    Main purpose is to reduce list of commands or to print them sorted.
    An example *+preload* can be found in `.o-saft.pl` .

\====== --cfg_score=KEY=SCORE======

  -
    Redefine value for scoring. Sets %checks{KEY}{score} to SCORE.
    Most score values are set to 10 by default. Values `0` .. `100` are
    allowed.

<!-- end list -->

  -
    To get a list of current score settings, use:

`   o-saft.pl --help=score`

  -
    For deatils how scoring works, please see
    [SCORING](#SCORING "wikilink") section.

<!-- end list -->

  -
    Use the *--trace-key* option for the *+info* and/or *+check*
    command to get the values for KEY.

\====== --cfg_checks=KEY=TEXT --cfg_data=KEY=TEXT======

  -
    Redefine texts used for labels in output. Sets %data{KEY}{txt} or
    %checks{KEY}{txt} to `TEXT`.

<!-- end list -->

  -
    To get a list of preconfigured labels, use:

`   o-saft.pl --help=cfg_checks`
`   o-saft.pl --help=cfg_data`

  -

\====== --cfg_text=CIPHER=value======

  -
    Redefine the security value (i.e. HIGH) in the cipher description.
    Example:

`   o-saft.pl --cfg-cipher=NULL-MD5=no-security-at-all ...`

\====== --cfg_text=KEY=TEXT======

  -
    Redefine general texts used in output. Sets %text{KEY} to `TEXT`.

<!-- end list -->

  -
    To get a list of preconfigured texts, use:

`   o-saft.pl --help=cfg_text`

  -
    Note that \\n, \\r and \\t are replaced by the corresponding
    character
    when read from [RC-FILE](#RC-FILE "wikilink").

\====== --cfg_text=FILE======

  -
    Read definitions for %text{KEY}="my text" from file `FILE`.

\====== --cfg_hint=KEY=TEXT======

  -
    Redefine texts used for hints. Sets %cfg{hints}{KEY} to `TEXT`.

<!-- end list -->

  -
    To get a list of preconfigured texts, use:

`   o-sat.pl --help=cfg-hint`

\====== --call=METHOD======

  -

    See [Options for SSL tool](#Options_for_SSL_tool "wikilink")

###### \--usr

  -

    Execute functions defined in o-saft-usr.pm.

###### \--usr-\*

###### \--user-\*

  -
    Options ignored, but stored as is internal in $cfg{usr-args} .
    These options can be used in o-saft-usr.pm or o-saft-dbx.pm.

###### \--experimental

  -

    Use experimental functionality.

    Some functionality of this tool is under development and only used

    when this option is given.

##### Options for tracing and debugging

  -

###### \--n --dry-run

  -
    Do not execute, just show commands (only useful in conjunction with
    using openssl).

##### Difference --trace vs. --v

  -
    While *--v* is used to print more data, *--trace* is used to print
    more information about internal data such as procedure names and/or
    variable names and program flow.

###### \--v

###### \--verbose

  -
    Print more information about checks.
    Note that this option should be first otherwise some debug messages
    are missing.
    Note that *--v* is different from *-v* (see above).

###### \--v --v

  -
    Print remotely checked ciphers.

###### \--v-cipher --cipher-v

  -
    Print remotely checked ciphers.
    In contrast to *--v --v* above, this just prints the ciphers while
    being checked, but no other verbose messages.

\-- no longer implemented (8/2015)

###### \--v --v --v

  -
    Print remotely checked ciphers one per line.

###### \--v --v --v --v

  -
    Print processed ciphers (check, skip, etc.).

\--\>

###### \--trace

  -
    Print debugging messages.

###### \--trace --trace

  -
    Print more debugging messages and pass `trace=2` to Net::SSLeay and
    Net::SSLinfo.

###### \--trace --trace --trace

  -
    Print more debugging messages and pass `trace=3` to Net::SSLeay and
    Net::SSLinfo.

###### \--trace --trace --trace --trace

  -
    Print processing of all command line arguments.

###### \--trace-cli

  -
    Print complete command line first. Used for internal testing.

###### \--trace--

  -

###### \--trace-arg

  -
    Print command line argument processing.

###### \--trace-cmd

  -
    Trace execution of command processing (those given as *+\**).

###### \--trace@

  -

###### \--trace-key

  -
    Print some internal variable names in output texts (labels).
    Variable names are prefixed to printed line and enclosed in `#` .
    Example without --trace-key :

`      Certificate Serial Number:          deadbeef`

  -
    Example with --trace-key :

`      #serial#          Certificate Serial Number:          deadbeef`

  -

\====== --trace=VALUE======

  -
    Alias for [--trace-VALUE](#--trace=VALUE "wikilink") options (see
    above).

<!-- end list -->

  -
    Trace Option Alias Option

<!-- end list -->

  - \--trace=1 same as --trace
  - \--trace=2 same as --trace --trace
  - \--trace=arg same as --trace-arg
  - \--trace=cmd same as --trace-cmd
  - \--trace=key same as --trace-key

###### \--trace-time

  -

    Prints timestamp in trace output. More timestamps are printed if

    used together with *--trace-cmd*.

\====== --trace=FILE======

  -
    Use `FILE` instead of the default [RC-FILE](#RC-FILE "wikilink"),
    i.e. `.o-saft.pl`.

###### \--trace-me

  -
    Print debugging messages for `o-saft.pl` only, but not any modules.

###### \--trace-not-me

  -
    Print debugging messages for modules only, but not `o-saft.pl`
    istself.

###### \--trace-sub +traceSUB

  -
    Print formatted list of internal functions with their description.
    Not to be intended in conjunction with any target check.

###### \--hint

  -
    Print hint messages (\!\!Hint:).

###### \--no-hint

  -
    Do not print hint messages (\!\!Hint:).

###### \--warning

  -
    Print warning messages (\*\*WARNING:).

###### \--no-warning

  -
    Do not print warning messages (\*\*WARNING:).

\====== --exit=KEY======

  -
    Terminate `o-saft.pl` at specified `KEY`. Please see
    [TESTING](#TESTING "wikilink") below.

##### Options vs. Commands

  -
    For compatibility with other programs and lazy users, some arguments
    looking like options are silently taken as commands. This means that
    *--THIS* becomes *+THIS* then. These options are:

:\* *--help*

:\* *--abbr*

:\* *--todo*

:\* *--chain*

:\* *--default*

:\* *--fingerprint*

:\* *--list*

:\* *--version*

  -
    Take care that this behaviour may be removed in future versions as
    it
    conflicts with those options and commands which actually exist,
    like:

:\* *--sni* vs. *+sni*

#### LAZY SYNOPSIS

##### Commands

  -
    Following strings are treated as a command instead of target names:

:\* ciphers

:\* s_client

:\* version

  -
    A warning will be printed.

##### Options

  -
    We support following options, which are all identical, for lazy
    users
    and for compatibility with other programs.

###### Option Variants

  -
    *--port PORT*
    *--port=PORT*

<!-- end list -->

  -
    This applies to most such options, *--port* is just an example.
    When used in the [RC-FILE](#RC-FILE "wikilink"), the
    *--OPTION=VALUE* variant must be used.

###### Option Names

  -

    Dash `-`, dot `.` and/or underscore `_` in option names are
    optional,

    all following are the same:

    *--no.dns*

    *--no-dns*

    *--no_dns*

    *--nodns*

    This applies to all such options, *--no-dns* is just an example.

##### Targets

  -

    Following syntax is supported also:

`   o-saft.pl http://some.tld other.tld:3889/some/path?a=b`

  -

    Note that only the hostname and the port are used from an URL.

##### Options vs. Commands

  -

    See [Options vs. Commands](#Options_vs._Commands "wikilink") in
    [OPTIONS](#OPTIONS "wikilink") section above

#### CHECKS

  -
    All SSL related check performed by the tool will be described here.

##### General Checks

  -
    Lookup the IP of the given hostname (FQDN), and then tries to
    reverse
    resolve the FQDN again.

##### SSL Ciphers

  -
    Check which ciphers are supported by target. Please see
    [RESULTS](#RESULTS "wikilink") for
    details of this check.

##### SSL Connection

###### heartbeat

  -
    Check if "heartbead" extension is supported by target.

###### poodle

  -
    Check if target is vulnerable to POODLE attack (SSLv3 enabled).

###### robot

  -
    Check if target is vulnerable to ROBOT attack (server offers ciphers
    with RSA encryption).

###### sloth

  -
    Check if target is vulnerable to SLOTH attack (server offeres
    RSA-MD5
    or ECDSA-MD5 ciphers).

###### sweet32

  -
    Check if target is vulnerable to Sweet32 attack (server offers CBC
    or
    CBC3 or DES or 3DES ciphers).

<!-- end list -->

  -
    Note that FIPS-140 compliance requires 3DES ciphers, hence compliant
    systems are then vulnerable to Sweet32 attacks.

###### ALPN

  -
    Check if target supports ALPN. Following messages are evaluated:

`   ALPN protocol: h2-14`
`   No ALPN negotiated`

  -
    Please see also CHECKS [ALPN and NPN](#ALPN_and_NPN "wikilink")
    below.

##### SSL Vulnerabilities

###### ADH

  -
    Check if ciphers for anonymous key exchange are supported: ADH

|DHA .

  -
    Such key exchanges can be sniffed.

###### EDH

  -
    Check if ephemeral ciphers are supported: DHE

|EDH .

  -
    They are necessary to support Perfect Forward Secrecy (PFS).

###### BEAST

  -
    Check if ciphers with CBC for protocol SSLv1, SSLv3 or TLSv1 are
    used.
    TLSv1.2 checks are not yet implemented.

###### CRIME

  -
    Connection is vulnerable if target supports SSL-level compression.

###### DROWN

  -
    Connection is vulnerable if target supports SSLv2 (with at least one
    cipher).

###### FREAK

  -
    Attack Against SSL/TLS to downgrade to EXPORT ciphers.
    Currently (2018) a simple check is used: SSLv3 enabled and EXPORT
    ciphers supported by server.
    See CVE-2015-0204 and <https://freakattack.com/> .

###### HEARTBLEED

  -
    Check if target is vulnerable to heartbleed attack, see
    CVE-2014-0160
    and <http://heartbleed.com/> .

###### HEIST

  -
    Not implemented.

<!-- end list -->

  -
    There are no checks for the HEIST attack implemented, because this
    is
    an attack on TCP/IP rather than SSL/TLS on top of TCP/IP.

###### KCI

  -
    Not implemented.

<!-- end list -->

  -
    To perform a MiTM attack with Key Compromise Impersonation, the
    atta-
    cker needs to engage the victim to install and use a client
    certificate.
    This is considered a low risk and hence not tested here.

###### Logjam

  -
    Check if target is vulenerable to Logjam attack.
    Check if target suports EXPORT ciphers and/or DH Parameter is less
    than 2048 bits.

###### Lucky 13

  -
    Check if CBC ciphers are offered.
    NOTE the recommendation to be safe againts Lucky 13 was to use RC4
    ciphers. But they are also subjetc to attacks (see below). Hence the
    check is only for CBC ciphers.

###### RC4

  -
    Check if RC4 ciphers are supported.
    They are assumed to be broken.
    Note that *+rc4* reports the vulnerabilitiy to the RC4 Attack, while
    *+rc4_cipher* simply reports if RC4 ciphers are offered. However
    the
    the check, and hence the result, is the same.

###### PFS

  -
    Check if DHE ciphers are used. Also check if the TLS session ticket
    is random or not used at all.
    Currently (2018) only a simple check is used: only DHE ciphers used.
    TLSv1.2 checks are not yet implemented.

###### POODLE

  -
    Check if target is vulnerable to POODLE attack (just check if SSLv3
    is enabled).

###### Practical Invalid Curve Attack

  -
    This attack allows an attacker to read the servers private key if
    the
    server does not check properly the passed points for a ecliptic
    curve
    when EDH ciphers are used.

<!-- end list -->

  -
    This check will not send multiple invalid points, but only checks if
    the server closes the connection or responds with no matching
    cipher.

###### ROBOT

  -
    Bleichebacher's Oracle attack against SSL/TLS ciphers.

<!-- end list -->

  -
    Not implemented.
    <https://robotattack.org/>

###### SLOTH

  -
    Currently (2016) we check for ciphers with ECDSA, RSA-MD5.
    Checking the TLS extension 'tls-unique' is not yet implemented.

###### Sweet32

  -
    Currently (2016) we check for ciphers with CBC or CBC3 or DES or
    3DES.

##### Target (server) Configuration and Support

###### BEAST, BREACH, CRIME, DROWN, FREAK, Logjam, Lucky 13, POODLE, RC4, ROBOT, SLOTH, Sweet32

  -
    See above.

###### Renegotiation

  -
    Check if the server allows client-side initiated renegotiation.

###### Version rollback attacks

  -
    NOT YET IMPLEMENTED
    Check if the server allows changing the protocol.

###### DH Parameter

  -
    Check if target's DH Parameter is less 512 or 2048 bits.

##### Target (server) Certificate

###### Certificate Hashes

  -
    Check that fingerprint is not MD5.
    Check that certificate private key signature is SHA2 or better.

###### Root CA

  -
    Provided certificate by target should not be a Root CA.

###### Self-signed Certificate

  -
    Certificate should not be self-signed.

###### FQDN is listed in subjectAltname (RFC2818)

  -
    The FQDN must be listed in the certificates subjectAltname.
    The check command *+rfc_2818_names* is based on the info command
    *+verify_hostname* . The check was added in 05/2017 because
    browsers
    started to complain if the FQDN is not part of the subjectAltname.

###### IP in CommonName or subjectAltname (RFC6125)

  -
    NOT YET IMPLEMENTED

###### Basic Constraints

  -
    Certificate extension Basic Constraints should be `CA:FALSE`.

###### OCSP, CRL, CPS

  -
    Certificate should contain URL for OCSP and CRL.

###### Private Key encyption

  -
    Certificates signature key supports encryption.

###### Private Key encyption well known

  -
    Certificates signature key encryption algorithm is well known.

###### Public Key encyption

  -
    Certificates public key supports encryption.

###### Public Key encyption well known

  -
    Certificates public key encryption algorithm is well known.

###### Public Key Modulus size

  -
    Some (historic) SSL implementations are subject to buffer overflow
    if
    the key exceeds 16384 or 32768 bits. The check is against 16384
    bits.

###### Public Key Modulus Exponent size

  -
    The modulus exponent should be = 65537 as it is a prime number and
    an
    easy to calculate exponent.
    If the exponent is less than 65537, "Boradcast" attacks are
    possible.

<!-- end list -->

  -
    However, some (mainly historic) SSL implementations may have
    problems
    to connect because they are not able to do the crypt mathematics
    with
    exponenents larger than 65536.

<!-- end list -->

  -
    If ecliptive curves are used, the result for these checks is always
    `no (<<N/A ...)`.

###### Sizes and Lengths of Certificate Settings

  -
    Serial Number \<= 20 octets (RFC5280, 4.1.2.2. Serial Number)

<!-- end list -->

  -
    ...

###### DV-SSL - Domain Validation Certificate

  -
    The Certificate must provide:

<!-- end list -->

  - Common Name `/CN=` field
  - Common Name `/CN=` in `subject` or `subjectAltname` field
  - Domain name in `commonName` or `altname` field

###### EV-SSL - Extended Validation Certificate

  -
    This check is performed according the requirements defined by the
    CA/
    Browser Forum <https://www.cabforum.org/contents.html> .
    The Certificate must provide:
      - DV - Domain Validation Certificate (see above)
      - Organization name `/O=` Cn *subject* field
      - Organization name must be less to 64 characters
      - Business Category `/businessCategory=` in `subject` field
      - Registration Number `/serialNumber=` in `subject` field
      - Address of Place of Business in `subject` field

<!-- end list -->

  -
    Required are: `/C=`, `/ST=`, `/L=`

<!-- end list -->

  -
    Optional are: `/street=`, `/postalCode=`
      - Validation period does not exceed 27 month

<!-- end list -->

  -
    See [LIMITATIONS](#LIMITATIONS "wikilink") also.

##### Target (server) HTTP(S) Support

###### STS header (see RFC 6797)

  -
    Using STS is no perfect security. While the very first request using
    http: is always prone to a MiTM attack, MiTM is possible to
    following
    requests again, if STS is not well implemented on the server.
      - Request with http: should be redirected to https:
      - Redirects should use status code 301 (even others will work)
      - Redirect's Location header must contain schema https:
      - Redirect's Location header must redirect to same FQDN
      - Redirect may use Refresh instead of Location header (not
        RFC6797)
      - Redirects from HTTP must not contain STS header
      - Answer from redirected page (HTTPS) must contain STS header
      - Answer from redirected page for IP must not contain STS header
      - STS header must contain includeSubDirectoy directive
      - STS header max-age should be less than 1 month
      - STS must not be set in http-equiv attribute of a meta TAG

###### STS header preload attribute (*+preload*)

  -
    To satisfy the requirements on <https://hstspreload.appspot.com/>
    the
    HSTS header must:
      - have the max-age with at least 18 weeks (10886400 seconds)
      - have the includeSubDomains attribute
      - have the preload attribute
      - redirect to https first, then to sub-domains (if redirected)
      - have an HSTS header in each redirect to https.

<!-- end list -->

  -
    Additionally, the site must have:
      - a valid certificate
      - serve all subdomains over https.

<!-- end list -->

  -
    Except the last requirement, *+preload* will do the checks.
    Note that *+preload* is defined in `.o-saft.pl` only.

###### Public Key Pins header

  -
    TBD - to be described ...

##### Sizes

  -
    Mainly in the certificate various counts, lengths and sizes of
    values
    are checked and reported. All commands for these checks start with
    `+cnt_` or `+len_`. Up to now, there is no `yes` or `no` value
    for these checks.

<!-- end list -->

  -
    Following commands will check the value to be in a specific range to
    become `yes` or `no`:
      - \+sts_maxage1d - yes if HSTS maxage \< 1 day
      - \+sts_maxage1m - yes if HSTS maxage \< 1 month
      - \+sts_maxage1y - yes if HSTS maxage \< 1 year
      - \+sts_maxage18 - yes if HSTS maxage \< 18 weeks (5 months)
      - \+sts_maxagexy - yes if HSTS maxage \> 1 year
      - \+modulus_exp_1 - Public Key Modulus Exponent \<\>1
      - \+modulus_exp_65537 - Public Key Modulus Exponent =65537
      - \+modulus_exp_oldssl - Public Key Modulus Exponent \<65537
      - \+modulus_size_oldssl - Public Key Modulus \<16385 bits

<!-- end list -->

  -
    For some details of these cjecks, please see the description above
    at
    "Public Key Modulus Exponent size"

<!-- end list -->

  -
    The recommendations for DH parameters (RSA and ecliptice curve) are
    are checked as follows:
      - \+dh_512 - DH Parameter \>= 512 bits
      - \+dh_2048 - DH Parameter \>= 2048 bits
      - \+ecdh_256 - DH Parameter \>= 256 bits (ECDH)
      - \+ecdh_512 - DH Parameter \>= 512 bits (ECDH)
    Note that only one of the checks `+dh_*` and `+ecdh_*` can return
    `yes`.

##### ALPN and NPN

  -
    The commands for the checks to report `yes` or `no`, are *+hasalpn*
    and *+hasnpn*.
    Both, the Application Layer Protocol Negotiation (ALPN) and the Next
    Protocol Negotiation (NPN) will be tested. The commands for that
    are:
      - \+alpns
      - \+npns
    Each, ALPN and NPN, is tested separately with all known protocols.
    The test sets only one protocol, tries to make a connection and then
    checks if the protocol was accepted by the server. The collected
    list
    of protocols will be printed with the aforementioned commands, or
    the
    *+info* command. Note the difference for the commands
    *+next_protocols*
    and *+alpns*, where *+next_protocols* simply reports what the
    server
    itself advertises, while *+alpns* reports what the server supports
    if
    asked for.

##### Compliances

  -
    Note that it is not possible to satisfy all following compliances.
    Best
    match is: *PSF* and *ISM* and *PCI* and *lazy BSI TR-02102-2*.

<!-- end list -->

  -
    In general it is difficult to satisfy all conditions of a
    compliances,
    and it is also difficult to check all these conditions. That's why
    some
    of the compliances checks are not completely implemented, for
    details
    please see blow.

<!-- end list -->

  -
    Note that output of results of some checks is disabled in the
    [RC-FILE](#RC-FILE "wikilink")
    by default. A "\!\!Hint:" message will be printed, if any of these
    checks
    are used.

:\* FIPS-140

:\* ISM

:\* PCI

:\* BSI TR-02102 (2016-01)

:\* BSI TR-03116-4

:\* RFC 2818

:\* RFC 6125

:\* RFC 6797

:\* RFC 7525

###### BSI TR-02102-2 (*+tr-02102+* *tr-02102-* *+bsi*)

  -
    Checks if connection and ciphers are compliant according TR-02102-2,
    see
    <https://www.bsi.bund.de/SharedDocs/Downloads/DE/BSI/Publikationen>
    /TechnischeRichtlinien/TR02102/BSI-TR-02102-2_pdf.pdf?__blob=publicationFile

<!-- end list -->

  -
    (following headlines are taken from TR-02102-2 Version 2016-01)

:\* 3.1.3 Schlüssellängen bei EC-Verfahren

:\* 3.2 SSL/TLS_Versionen

  -
    Only TLSv1.2 allowed (except for *+tr-02102-* which also allows
    TLSv1.1)

:\* 3.3.1 Empfohlene Cipher Suites

  -
    Allows only \*DHE-\*-SHA256, \*DHE-\*-SHA384, \*DH-\*-SHA256 and
    \*DH-\*-SHA384 ciphers and PSK ciphers with ephermeral keys.
    For *+tr-02102+* they must be AES-GCM, *+tr02102-* also allows
    AES-CBC.

:\* 3.3.2 Übergangsregelungen

  -
    SHA1 temporary allowed. SHA256 and SHA384 recommended.
    RC4 not reocmmended.
    Use of SHA1 will only be checked for *+tr-02102+*

:\* 3.4.1 Session Renegotation

  -
    Only server-side (secure) renegotiation allowed (see RFC5280).

:\* 3.4.2 Verkürzung der HMAC-Ausgabe

  -
    Truncated HMAC according RFC 6066 not recommended.

:\* 3.4.3 TLS-Kompression und der CRIME-Angriff

  -
    No TLS compression.

:\* 3.4.4 Der Lucky 13-Angriff

:\* 3.4.5 Die "Encrypt-thn-MAC"-Erweiterung

  -
    Use of AES-GCM ciphers only.
    Use of Encrypt-then-MAC according RFC 7366 cannot be checked.

:\* 3.4.6 Die Heartbeat-Erweiterung

  -
    Target must not support the heartbeat extension.

:\* 3.4.7 Die Extended Master Secret Extension

  -
    Use of Extended Master Secret Extension according RFC 7627 cannot
    be checked.

:\* 3.5 Authentisierung der Kommunikationspartner

  -
    Not checked as only applicable for VPN connections.

:\* 3.6 Domainparameter und Schlüssellängen

  -
    Check if signature key is \> 2000 bits.

:\* 3.6.1 Verwendung von elliptischen Kurven

  -
    \*\*NOT YET IMPLEMENTED\*\*

<!-- end list -->

  -
    Use only following curves according RFC 5639 and RFC 7027:
    brainpoolP256r1, brainpoolP384r1, brainpoolP512r1

<!-- end list -->

  -
    Use of secp256r1 and secp384r1 temporary allowed.

:\* 4.1 Schlüsselspeicherung

  -
    This requirement is not testable from remote.

:\* 4.1 Umgang mit Ephemeralschlüsseln

  -
    This requirement is not testable from remote.

:\* 4.3 Zufallszahlen

  -
    This requirement is not testable from remote.

###### BSI TR-03116-4 (*+tr-03116+* *+tr-03116-* *+bsi*)

  -
    Checks if connection and ciphers are compliant according TR-03116-4,
    see
    <https://www.bsi.bund.de/SharedDocs/Downloads/DE/BSI/Publikationen>
    /TechnischeRichtlinien/TR03116/BSI-TR-03116-4.pdf?__blob=publicationFile

<!-- end list -->

  -
    (following headlines are taken from there)

:\* 2.1.1 TLS-Versionen und Sessions

  -
    Allows only TLS 1.2.

:\* 2.1.2 Cipher Suites

  -
    Cipher suites must be ECDHE-ECDSA or -RSA with AES128 and SHA265.
    For curiosity, stronger cipher suites with AES256 and/or SHA384 are
    not not allowed. To follow this curiosity the *+bsi-tr-03116-*
    (lazy)
    check allows the stronger cipher suites ;-)

:\* 2.1.1 TLS-Versionen und Sessions

  -
    The TLS session lifetime must not exceed 2 days.

:\* 2.1.4.2 Encrypt-then-MAC-Extension

:\* 2.1.4.3 OCSP-Stapling

  -
    MUST have `OCSP Stapling URL`.

:\* 4.1.1 Zertifizierungsstellen/Vertrauensanker

  -
    Certificate must provide all root CAs. (NOT YET IMPLEMENTED).

<!-- end list -->

  -
    Should use a small certificate trust chain.

:\* 4.1.2 Zertifikate

  -
    Must have `CRLDistributionPoint` or `AuthorityInfoAccess`.

<!-- end list -->

  -
    End-user certificate must not be valid longer than 3 years.
    Root-CA certificate must not be valid longer than 5 years.

<!-- end list -->

  -
    Certificate extension `pathLenConstraint` must exist, and should be
    a small value ("small" is not defined).

<!-- end list -->

  -
    All certificates must contain the extension `KeyUsage`.

<!-- end list -->

  -
    Wildcards for `CN` or `Subject` or `SubjectAltName` are not allowed
    in any certificate.

<!-- end list -->

  -
    EV certificates are recommended (NOT YET checked properly).

:\* 4.1.3 Zertifikatsverifikation

  -
    Must verify all certificates in the chain down to their root-CA.
    (NOT YET IMPLEMENTED).

<!-- end list -->

  -
    Certificate must be valid according issue and expire date.

<!-- end list -->

  -
    All Checks must be doen for all certificates in the chain.

:\* 4.1.4 Domainparameter und Schlüssellängen

  -
    This requirement is not testable from remote.

:\* 4 5.2 Zufallszahlen

  -
    This requirement is not testable from remote.

###### RFC 2818 (*+rfc2818*)

  -
    Check if the FQDN is listed in the certificates `subjectAltname`.

###### RFC 6125 (*+rfc6125*)

  -
    Checks values `CommonName`, `Subject` and `SubjectAltname` of the
    certificate for:
      - must all be valid characters for DNS
      - must not contain more than one wildcards
      - must not contain invalid wildcards
      - must not contain invalid IDN characters

###### RFC 6797 (*+rfc6797*)

  -
    Same as STS header *+hsts* .

###### RFC 7525 (*+rfc7525*)

  -
    Checks if connection and ciphers are compliant according RFC 7525.
    See <http://tools.ietf.org/rfc/rfc7525.txt>
    (following headlines are taken from there)

:\* 3.1.1. SSL/TLS Protocol Versions

  -
    SSLv2 and SSLv3 must not be supportetd.
    TLSv1 should only be supported if there is no TLSv1.1 or TLSv1.2.
    Either TLSv1.1 or TLSv1.2 must be supported, prefered is TLSv1.2.

:\* 3.1.2. DTLS Protocol Versions

  -
    DTLSv1 and DTLSv1.1 must not be supported.

:\* 3.1.3. Fallback to Lower Versions

  -
    (check implecitely done by 3.1.1, see above)

:\* 3.2. Strict TLS

  -
    Check if server provides Strict Transport Security.
    (STARTTLS check NOT YET IMPLEMENTED).

:\* 3.3. Compression

  -
    Compression on TLS must not be supported.

:\* 3.4. TLS Session Resumption

  -
    Server must support resumtion and random session tickets.
    (Randomnes of session tickets implemented YET experimental.)

<!-- end list -->

  -
    Check if ticket is authenticated and encrypted NOT YET IMPLEMENTED.

:\* 3.5. TLS Renegotiation

  -
    Server must support renegotiation.

:\* 3.6. Server Name Indication

  -
    (Check for SNI support implemented experimental.)

:\* 4. Recommendations: Cipher Suites

:\* 4.1. General Guidelines

:\* 4.2. Recommended Cipher Suites

  -
    Check for recommended ciphers.

:\* 4.3. Public Key Length

  -
    DH parameter must be at least 256 bits or 2048 its with EC.
    (Check currently, 4/2016, based on openssl which may not provide DH
    parameters for all ciphers.)

:\* 4.5. Truncated HMAC

  -
    TLS extension "truncated hmac" must not be used.

:\* 6. Security Considerations

:\* 6.1. Host Name Validation

  -
    Given hostname must matches hostname in certificate's subject.

:\* 6.2. AES-GCM

:\* 6.3. Forward Secrecy

:\* 6.4. Diffie-Hellman Exponent Reuse

  -
    (NOT YET IMPLEMENTED).

:\* 6.5. Certificate Revocation

  -
    OCSP and CRL Distrbution Point in cetificate must be defined.

#### OUTPUT

  -
    All output is designed to make it easily parsable by postprocessors.
    Following rules are used:

:\* Lines for formatting or header lines start with `=`.

:\* Lines for verbosity or tracing start with `#`.

:\* Errors and warnings start with `**`, hints start with `!!`.

:\* Empty lines are comments ;-)

:\* Label texts end with a separation character; default is `:`.

:\* Label and value for all checks are separated by at least one TAB
character.

:\* Texts for additional information are enclosed in `<<` and `>>`.

:\* `N/A` is used when no proper informations was found or provided.

  -
    Replace `N/A` by whatever you think is adequate: "No answer",
    "Not available", "Not applicable", ...

<!-- end list -->

  -
    Lines not described above, will have the form (be default):

`        Label for information or check:  TABresult`

  -
    For more details on these lines, please refer to
    [RESULTS](#RESULTS "wikilink") above.

<!-- end list -->

  -
    When used in *--legacy=full* or *--legacy=simple* mode, the output
    may contain formatting lines for better (human) readability.

##### Errors, Warnings, Hints

  -
    Errors, warnings and hints may be part of the output as needed.
    While
    errors and warnings are printed immediately as they occour during
    the
    program flow, hints are printed right after the corresponding
    result.

<!-- end list -->

  -
    Errors and warnings start with a unique 3-digit number.

<!-- end list -->

  -
    Hints print an additional explanation of a specific result. They are
    are defined statically in the program code, or can be added on
    demand
    by using the option *--cfg-hint=KEY=TEXT* .

##### Postprocessing Output

  -
    It is recommended to use the *--legacy=quick* option, if the output
    should be postprocessed, as it omits the default separation
    character
    (`:` , see above) and just uses on single tab character (0x09, \\t
    or
    TAB) to separate the label text from the text of the result.
    Example:

`        Label of the performed checkTABresult`

  -
    More examples for postprocessing the output can be found here:
    <https://github.com/OWASP/O-Saft/blob/master/contrib>

#### CUSTOMIZATION

  -
    This tools can be customized as follows:

<!-- end list -->

  - Using command line options

<!-- end list -->

  -
    This is a simple way to redefine specific settings. Please see
    [CONFIGURATION OPTIONS](#CONFIGURATION_OPTIONS "wikilink") below.

<!-- end list -->

  - Using Configuration file

<!-- end list -->

  -
    A configuration file can contain multiple configuration settings.
    Syntax is simply KEY=VALUE. Please see [CONFIGURATION
    FILE](#CONFIGURATION_FILE "wikilink") below.

<!-- end list -->

  - Using resource files

<!-- end list -->

  -
    A resource file can contain multiple command line options. Syntax
    is the same as for command line options iteself. Each directory
    may contain its own resource file. Please see
    [RC-FILE](#RC-FILE "wikilink") below.

<!-- end list -->

  - Using debugging files

<!-- end list -->

  -
    These files are --nomen est omen-- used for debugging purposes.
    However, they can be (mis-)used to redefine all settings too.
    Please see [DEBUG-FILE](#DEBUG-FILE "wikilink") below.

<!-- end list -->

  - Using user specified code

<!-- end list -->

  -
    This file contains user specified program code. It can also be
    (mis-)used to redefine all settings. Please see
    [USER-FILE](#USER-FILE "wikilink") below.

<!-- end list -->

  -
    Customization is done by redefining values in internal data
    structure
    which are: %cfg, %data, %checks, %text, %scores .

<!-- end list -->

  -
    Unless used in [DEBUG-FILE](#DEBUG-FILE "wikilink") or
    [USER-FILE](#USER-FILE "wikilink"), there is no need to know
    these internal data structures or the names of variables; the
    options
    will set the proper values. The key names being part of the option,
    are printed in output with the *--trace-key* option.

<!-- end list -->

  -
    I.g. texts (values) of keys in %data are those used in output of the
    `Informations` section. Texts of keys in %checks are used for output
    in `Performed Checks` section. And texts of keys in %text are used
    for additional information lines or texts (mainly beginning with
    `=`).

###### Configuration File vs. RC-FILE vs. DEBUG-FILE

  - CONFIGURATION FILE

<!-- end list -->

  -
    Configuration Files must be specified with one of the *--cfg_\**
    options. The specified file can be a valid path. Please note that
    only the characters: a-zA-Z_0-9,.\\/()- are allowed as pathname.
    Syntax in configuration file is: `KEY=VALUE` where `KEY` is any
    key as used in internal data structure.
    the keys in output).

<!-- end list -->

  - RC-FILE

<!-- end list -->

  -
    Resource files are searched for and used automatically.
    For details see [RC-FILE](#RC-FILE "wikilink") below.

<!-- end list -->

  - DEBUG-FILE

<!-- end list -->

  -
    Debug files are searched for and used automatically.
    For details see [DEBUG-FILE](#DEBUG-FILE "wikilink") below.

<!-- end list -->

  - USER-FILE

<!-- end list -->

  -
    The user program file is included only if the *--usr* option was
    used. For details see [USER-FILE](#USER-FILE "wikilink") below.

##### CONFIGURATION OPTIONS

  -
    Configuration options are used to redefine texts and labels or score
    settings used in output. The options are:

:\* *--cfg-cmd=CMD=LIST*

:\* *--cfg-checks=KEY=TEXT*

:\* *--cfg-data=KEY=TEXT*

:\* *--cfg-hint=KEY=TEXT*

:\* *--cfg-text=KEY=TEXT*

:\* *--cfg-cipher=CIPHER=TEXT*

  -
    `KEY` is the key used in the internal data structure, and `TEXT` is
    the
    value to be set for this key. Note that unknown keys will be ignored
    silently.

<!-- end list -->

  -
    If `KEY=TEXT` is an exiting filename, all lines from that file are
    read and set. For details see [CONFIGURATION
    FILE](#CONFIGURATION_FILE "wikilink") below.

<!-- end list -->

  -
    `CIPHER` must be a valid cipher suite name as shown with:

`   o-saft.pl ciphers`

  -
    NOTE that such configuration options should be used before any
    *--help*
    or *--help=\** option, otherwise the changed setting is not visible.

##### CONFIGURATION FILE

  -
    Note that the file can contain `KEY=TEXT` pairs for any kind of the
    configuration as given by the [--cfg_CFG](#--cfg_CFG "wikilink")
    option.

<!-- end list -->

  -
    For example when used with
    [--cfg_text=FILE](#--cfg_text=FILE "wikilink") only values for
    %text
    will be set, when used with
    [\#--cfg_data=FILE--cfg_data=FILE](#--cfg_data=FILE--cfg_data=FILE "wikilink")
    only values for %data
    will be set, and so on. `KEY` is not used when `KEY=TEXT` is an
    existing
    filename. Though, it's recommended to use a non-existing key, i.e.:
    *--cfg-text=my_file=some/path/to/private/file* .

##### RC-FILE

  -
    The rc-file will be searched for in the working directory only.

<!-- end list -->

  -
    The name of the rc-file is the name of the program file prefixed by
    a
    `.` (dot), for example: `.o-saft.pl`.

<!-- end list -->

  -
    A rc-file can contain any of the commands and options valid for the
    tool itself. The syntax for them is the same as on command line.
    Each
    command or option must be in a single line. Any empty or comment
    line
    will be ignored. Comment lines start with `#` or `=`.

<!-- end list -->

  -
    Note that options with arguments must be used as `KEY=VALUE` instead
    of `KEY VALUE`.

<!-- end list -->

  -
    Configurations options must be written like `--cfg-CFG=KEY=VALUE`
    where `CFG` is any of: `cmd`, `check`, `data`, `text` and `KEY` is
    any key from internal data structure (see above).

<!-- end list -->

  -
    All commands and options given on command line will overwrite those
    found in the rc-file.

##### DEBUG-FILE

  -
    All debugging functionality is defined in *o-saft-dbx.pm*, which
    will
    be searched for using paths available in perl's `@INC` variable.

<!-- end list -->

  -
    Syntax in this file is perl code. For details see
    [DEBUG](#DEBUG "wikilink") below.

##### USER-FILE

  -
    All user functionality is defined in *o-saft-usr.pm*, which will be
    searched for using paths available in perl's `@INC` variable.

<!-- end list -->

  -
    Syntax in this file is perl code.

<!-- end list -->

  -
    All functions defined in *o-saft-usr.pm* are called when the option
    *--usr* was given. The functions are defined as empty stub, any code
    can be inserted as need. Please see *perldoc o-saft-usr.pm* to see
    when and how these functions are called.

##### SHELL TWEAKS

  -
    Configuring the shell environment where the tool is startet, must be
    done before the tools starts. It is not really a task for the tool
    itself, but it can simplify your life, somehow.

<!-- end list -->

  -
    There exist customizations for some commonly used shells, please see
    the files in the `./contrib/` directory.

##### COMMANDS

  -
    The option *--cfg-cmd=CMD=LIST* can be used to define own commands.
    When configuring own commands, `CMD` must not be one of the commands
    listed with *--help=intern* and `CMD` must constist only of digits
    and
    letters.

<!-- end list -->

  -
    Examples in *.o-saft.pl* are *+preload* and *+ciphercheck* .

#### CIPHER NAMES

  -
    While the SSL/TLS protocol uses integer numbers to identify ciphers,
    almost all tools use some kind of \`human readable' texts for cipher
    names.

<!-- end list -->

  -
    These numbers (which are most likely written as hex values in source
    code and documentations) are the only true identifier, and we have
    to
    rely on the tools that they use the proper integers.

<!-- end list -->

  -
    As such integer or hex numbers are difficult to handle by humans, we
    decided to use human readable texts. Unfortunately no common
    standard
    exists how to construct the names and map them to the correct
    number.
    Some, but by far not all, oddities are described in [Name
    Rodeo](#Name_Rodeo "wikilink").

<!-- end list -->

  -
    The rules for specifying cipher names are:

<!-- end list -->

  -

      - 1\. textual names as defined by IANA (see \[IANA\])
      - 2\. mapping of names and numbers as defined by IANA (see
        \[IANA\])
      - 3\. `-` and `_` are treated the same
      - 4\. abbreviations are allowed, as long as they are unique
      - 5\. beside IANA, openssl's cipher names are preferred
      - 6\. name variants are supported, as long as they are unique
      - 7\. hex numbers can be used

<!-- end list -->

  -
    \[IANA\]
    <http://www.iana.org/assignments/tls-parameters/tls-parameters.txt>
    September 2013

<!-- end list -->

  -
    \[openssl\] ... openssl 1.0.1

<!-- end list -->

  -
    If in any doubt, use *+list* to get an idea about the mapping.
    Use *--help=regex* to see which regex are used to handle all these
    variants herein.

<!-- end list -->

  -
    Mind the traps and dragons with cipher names and what number they
    are
    actually mapped to. In particular when *--lib*, *--exe* or
    *--openssl*
    options are in use. Always use these options with *+list* command
    too.

##### Name Rodeo

  -
    As said above, the SSL/TLS protocol uses integer numbers to identify
    ciphers, but almost all tools use some kind of human readable texts
    for cipher names.

<!-- end list -->

  -
    For example the cipher commonly known as `DES-CBC3-SHA` is
    identified
    by `0x020701c0` (in openssl) and has
    `SSL2_DES_192_EDE3_CBC_WITH_SHA`
    as constant name. A definition is missing in IANA, but there is
    `TLS_RSA_WITH_3DES_EDE_CBC_SHA` . Thers is also `0x000A` for the
    same
    cipher `DES-CBC3-SHA`. Both are valid, first one when used with
    SSLv2,
    and second one when used with SSLv3.
    It's the responsibility of each tool to map the human readable
    cipher
    name to the correct (hex, integer) identifier.

<!-- end list -->

  -
    For example Firefox uses `dhe_dss_des_ede3_sha`, which is what?

<!-- end list -->

  -
    Furthermore, there are different acronyms for the same thing in use.
    For example `DHE` and `EDH` both mean "Ephemeral Diffie-Hellman".
    Comments in the *openssl(1)* sources mention this. And for curiosity
    these sources use both in cypher names but allow `EDH` as shortcut
    only in openssl's "ciphers" command. Wonder about (up to 1.0.1h):

`   openssl ciphers -V EDH`
`   openssl ciphers -V DHE`
`   openssl ciphers -V EECDH`
`   openssl ciphers -V ECDHE`

  -
    Next example is `ADH` which is also known as `DH_anon` or `DHAnon`
    or `DHA` or `ANON_DH`.

<!-- end list -->

  -
    You think this is enough? Then have a look how many acronyms are
    used
    for "Tripple DES".

<!-- end list -->

  -
    Compared to above, the interchangeable use of `-` vs. `_` in human
    readable cipher names is just a very simple one. However, see
    openssl
    again what following means (returns):

`   openssl ciphers -v RC4-MD5`
`   openssl ciphers -v RC4+MD5`
`   openssl ciphers -v RC4:-MD5`
`   openssl ciphers -v RC4:!MD5`
`   openssl ciphers -v RC4!MD5`

  -
    Looking at all these oddities, it would be nice to have a common
    unique
    naming scheme for cipher names. We have not. As the SSL/TLS protocol
    just uses a number, it would be natural to use the number as uniq
    key
    for all cipher names, at least as key in our internal sources.

<!-- end list -->

  -
    Unfortunately, the assignment of ciphers to numbers changed over the
    years, which means that the same number refers to a different cipher
    depending on the standard, and/or tool, or version of a tool you
    use.

<!-- end list -->

  -
    As a result, we cannot use human readable cipher names as identifier
    (aka unique key), as there are to many aliases for the same cipher.
    And also the number cannot be used as unique key, as a key may have
    multiple ciphers assigned.

#### KNOWN PROBLEMS

  -
    This section describes knwon problems, and known error messages
    which
    may occour when using *o-saft.pl*. This sections can be used as FAQ
    too
    as it gives hints and workarounds.

##### Segmentation fault

  -
    Sometimes the program terminates with a `Segmentation fault`. This
    mainly happens if the target does not return certificate
    information.
    If so, the *--no-cert* option may help.

##### \*\*WARNING: empty result from openssl; ignored at ...

  -
    This most likely occurs when the provided cipher is not accepted by
    the server, or the server expects client certificates.

##### \*\*WARNING: unknown result from openssl; ignored at ...

  -
    This most likely occurs when the openssl executable is used with a
    very slow connection. Typically the reason is a connection timeout.
    Try to use *--timeout=SEC* option.
    To get more information, use *--v* *--v* and/or *--trace* also.

##### \*\*WARNING: undefined cipher description

  -
    May occour if ciphers are checked, but no description is available
    for
    them herein. This results in printed cipher checks like:

`        EXP-KRB5-RC4-MD5                no       `<undef>`>`

  -
    instead of:

`        EXP-KRB5-RC4-MD5                no       weak`

##### \*\*WARNING: Can't make a connection to your.tld:443; no initial data

##### \*\*WARNING: Can't make a connection to your.tld:443; target ignored

  -
    This message occours if the underlaying SSL library (i.e. libssl.a)
    was not able to connect to the target. Known observed reasons are:
      - target does not support SSL protocol on specified port
      - target expects a client certificate in ClientHello message

<!-- end list -->

  -
    More details why the connection failed can be seen using *--trace=2*
    .

<!-- end list -->

  -
    If the targets supports SSL, it should be at least possible to check
    for supported ciphers using *+cipherall* instead of *+cipher* .

##### Use of uninitialized value $headers in split ... do_httpx2.al)

  -
    The warning message (like follows or similar):

<!-- end list -->

  -
    Use of uninitialized value $headers in split at
    blib/lib/Net/SSLeay.pm
    (autosplit into blib/lib/auto/Net/SSLeay/do_httpx2.al) line 1290.

<!-- end list -->

  -
    occurs if the target refused a connection on port 80.
    This is considered a bug in *Net::SSLeay*.
    Workaround to get rid of this message: use *--no-http* option.

##### invalid SSL_version specified at ... IO/Socket/SSL.pm

  -
    This error may occur on systems where a specific SSL version is not
    supported. Subject are mainly SSLv2, SSLv3 TLSv1.3 and DTLSv1.
    For DTLSv1 the full message looks like:

`      invalid SSL_version specified at C:/programs/perl/perl/vendor/lib/IO/Socket/SSL.`

  -
    See also [Note on SSL versions](#Note_on_SSL_versions "wikilink") .

<!-- end list -->

  -
    Workaround: use options like: *--no-sslv2* *--no-sslv3*
    *--no-tlsv13* *--no-dtlsv1*

##### Use of uninitialized value $_\[0\] in length at (eval 4) line 1.

  -
    This warning occours with IO::Socket::SSL 1.967, reason is unknown.
    It seems not to harm functionality, hence no workaround, just
    ignore.

##### Use of uninitialized value in subroutine entry at lib/IO/Socket/SSL.pm line 430.

  -
    Some versions of IO::Socket::SSL return this error message if \*-MD5
    ciphers are used with other protocols than SSLv2.

<!-- end list -->

  -
    Workaround: use *--no-md5-cipher* option.

##### Can't locate auto/Net/SSLeay/CTX_v2_new.al in @INC ...

  -
    Underlaying library doesn't support the required SSL version.
    See also [Note on SSL versions](#Note_on_SSL_versions "wikilink") .

<!-- end list -->

  -
    Workaround: use *--ssl-lazy* option, or corresponding *--no-SSL*
    option.

##### Read error: Connection reset by peer (,199725) at blib/lib/Net/SSLeay.pm (autosplit into blib/lib/auto/Net/SSLeay/tcp_read_all.al) line 535.

  -
    Error reported by some Net::SSLeay versions. Reason may be a
    timeout.
    This error cannot be omitted or handled properly.

<!-- end list -->

  -
    Workaround: try to use same call again (no guarantee,
    unfortunatelly)

##### Odd number of elements in anonymous hash at Net/SSLinfo.pm line 1613.

  -
    This warning from perl have been observed when the connection to the
    target to check for supported ciphers cannot be established.

<!-- end list -->

  -
    This message can be ignored.

##### openssl: ...some/path.../libssl.so.1.0.0: no version information available (required by openssl)

  -
    Mismatch of openssl executable and loaded underlaying library. This
    most likely happens when options *--lib=PATH* and/or *--exe=PATH*
    are
    used. See also [Note on SSL
    versions](#Note_on_SSL_versions "wikilink") .

<!-- end list -->

  -
    Hint: use following commands to get information about used
    libraries:

`  o-saft.pl +version`
`  o-saft.pl --v --v +version`

##### Integer overflow in hexadecimal number at ...

  -
    This error message may occour on 32-bit systems if perl was not com-
    piled with proper options. I.g. perl automatically converts the
    value
    to a floating pont number.
    Please report a bug with output of following command:

`  o-saft.pl +s_client +dump your.tld`

##### \<<openssl did not return DH Paramter>\>

  -
    Text may be part of a value. This means that all checks according DH
    parameters and logkam attack cannot be done.

<!-- end list -->

  -
    Workaround: try to use --openssl=TOOL option.

<!-- end list -->

  -
    This text may appears in any of the compliance checks (like
    +rfc7525)
    which may be a false positive. For these checks openssl is also used
    to get the DH Parameter.

<!-- end list -->

  -
    Workaround: not available yet

\=====No output with +help and/or --help=todo =====

  -
    On some (mainly Windows-based) systems using

`  o-saft.pl +help`
`  o-saft.pl --help`

  -
    does not print anything.

<!-- end list -->

  -
    Workaround: use *--v* option.

`  o-saft.pl +help --v`

  -
    or

`  o-saft.pl +help `

| more

##### Character set (like UTF-8) not recognized in some tools

  -
    Some tools do not diplay all characters properly, i.e. some versions
    of podviewer. It is not the obligation of this tool to fix well
    known
    bugs in other tools. However, we can offer workarounds.

<!-- end list -->

  -
    Workaround: generate the affected output using *--std-format=\**
    options
    For example:

`   o-saft.pl --no-rc --std-format=raw --help=gen-pod`

##### \*\*WARNING: on MSWin32 additional option --v required, sometimes ...

  -
    On some (mainly Windows-based) systems this may happen when calling
    for example:

`  o-saft.pl --help=FAQ`

  -
    which then may produce:

`  **WARNING: on MSWin32 additional option  --v  required, sometimes ...`
`  === reading: ./.o-saft.pl (RC-FILE done) ===`
`  === reading: Net/SSLinfo.pm (O-Saft module done) ===`
`  **USAGE: no command given`
`  # most common usage: `
`    o-saft.pl +info   your.tld`
`    o-saft.pl +check  your.tld`
`    o-saft.pl +cipher your.tld`
`  # for more help use:`
`    o-saft.pl --help `

  -
    Workaround: use full path to perl.exe, for example

`  C:\Programs\perl\bin\perl.exe o-saft.pl --help=FAQ`

##### Performance Problems

  -
    There are various reasons when the program responds slow, or seems
    to
    hang. Performance issues are most likely a target-side problem. Most
    common reasons are (no specific order):

:\* a) DNS resolver problems

  -

      -
        Try with *--no-dns*

:\* b) target does not accept connections for https

  -

      -
        Try with *--no-http*

:\* c) target's certificate is not valid

  -

      -
        Try with *--no-cert*

:\* d) target expects that the client provides a client certificate

  -

      -
        No option provided yet ...

:\* e) target does not handle Server Name Indication (SNI)

  -

      -
        Try with *--no-sni*

:\* f) use of external openssl(1) executable

  -

      -
        Use *--no-openssl*

:\* g) target does not respond at all and/or blocks

  -

      -
        Use *--ssl-error*
        For a detailed description, please see [Connection
        Problems](#Connection_Problems "wikilink").

<!-- end list -->

  -
    Other options which may help to get closer to the problem's cause:
    *--trace-time*, *--timeout=SEC*, *--trace*, *--trace-cmd*

<!-- end list -->

  -
    Using *--trace=time* should show following times:
      - DNS: 1 - 10 sec
      - no SNI: 1 - 10 sec
      - connection test: 1 - 5 sec
      - need_default: \<5 sec
      - need_cipher: 1 - 60 sec (+cipher with socket)
      - need_cipher: 1 - 20 sec (+cipherraw)
      - prepare checks: 2 - 20 sec
      - info: \<1 sec
      - check: \<1 sec

#### LIMITATIONS

##### Commands

  -
    Some commands cannot be used together with others, for example:
    *+cipher*, *+ciphers*, *+list*, *+libversion*, *+version*, *+check*,
    *+help*,
    *+protocols* .

<!-- end list -->

  -
    *+quick* should not be used together with other commands, it returns
    strange output then.

<!-- end list -->

  -
    *+protocols* requires *openssl(1)* with support for `-nextprotoneg`
    option. Otherwise the value will be empty.

##### Options

  -
    The option *--port=PORT* must preceed *--host=HOST* for a target
    like
    *HOST:PORT* .

<!-- end list -->

  -
    The characters `+` and `=` cannot be used for
    [--separator==CHAR](#--separator=CHAR "wikilink") option.

<!-- end list -->

  -
    Following strings should not be used in any value for options:
    `+check`, `+info`, `+quick`, `--header`
    as they my trigger the -*--header* option unintentional.

<!-- end list -->

  -
    The used *timeout(1)* command cannot be defined with a full path
    like
    *openssl(1)* can with the *--openssl=path/to/openssl*.

<!-- end list -->

  -
    [--cfg_text=FILE](#--cfg_text=FILE "wikilink") cannot be used to
    redefine the texts `yes` and `no`
    as used in the output for *+cipher* command.

##### Checks (general)

###### \+constraints

  -
    This check is only done for the certificate provided by the target.
    All other certificate in the chain are not checked.

<!-- end list -->

  -
    This is currently (2018) a limitation in *o-saft.pl*.

##### Broken pipe

  -
    This error message most likely means that the connection to
    specified
    target was not possible (firewall or whatever reason).

##### Target Certificate Chain Verification

  -
    The systems default capabilities i.e. libssl.so, openssl, are used
    to
    verify the target's certificate chain. Unfortunately various systems
    have implemented different approaches and rules how identify and how
    to report a successful verification. As a consequence this tool can
    only return the same information about the chain verification as the
    used underlying tools. If that information is trustworthy depends on
    how trustworthy the tools are.

<!-- end list -->

  -
    These limitations apply to following commands:

:\* *+verify*

:\* *+selfsigned*

  -
    Following commands and options are useful to get more information:

:\* *+chain_verify*, *+verify*, *+error_verify*, *+chain*,
*+s_client*

:\* *--ca-file*, *--ca-path*, *--ca-depth*

##### User Provided Files

  -
    Please note that there cannot be any guarantee that the code
    provided
    in the [DEBUG-FILE](#DEBUG-FILE "wikilink") *o-saft-usr.pm* or
    [USER-FILE](#USER-FILE "wikilink") *o-saft-usr.pm*
    will work flawless. Obviously this is the user's responsibility.

##### Problems and Errors

  -
    Checking the target for supported ciphers may return that a cipher
    is
    not supported by the server misleadingly. Reason is most likely an
    improper timeout for the connection. See *--timeout=SEC* option.

<!-- end list -->

  -
    If the specified targets accepts connections but does not speak SSL,
    the connection will be closed after the system's TCP/IP-timeout.
    This
    script will hang (about 2-3 minutes).

<!-- end list -->

  -
    If reverse DNS lookup fails, an error message is returned as
    hostname,
    like: `<<gethostbyaddr() failed`\>\>.
    Workaround to get rid of this message: use *--no-dns* option.

<!-- end list -->

  -
    All checks for EV are solely based on the information provided by
    the
    certificate.

<!-- end list -->

  -
    Some versions of openssl (\< 1.x) may not support all required
    options
    which results in various error messages or --more worse-- may not be
    visibale at all. Available functionalitity of openssl will be
    checked
    for right at the beginning Proper Warnings and hints are printed.
    Following table shows the openssl option and how to disbale it
    within
    o-saft:

:\* -nextprotoneg *--no-nextprotoneg*

:\* -reconnect *--no-reconnect*

:\* -tlsextdebug *--no-tlsextdebug*

:\* -alpn *--no-alpn*

##### Connection Problems

  -
    Sometimes the connection cannot be established. This may have
    various
    reasons. Unfortunaly this script seems to hang then. In particular
    when checking for ciphers with *+cipher* or *+cipherall* . The
    reason
    is most likely that the server does not respond to the TCP/IP
    request
    and hence the script closes the connection after the configured
    time-
    out (see *--timeout=SEC* option).

<!-- end list -->

  -
    Continous connection attempts can be inhibited with the
    *--ssl-error*
    option, which is set by default. Avoiding further connections
    results
    in a loss of information and consequentely leading to wrong checks.

<!-- end list -->

  -
    It is a trade-off to wait for all information done accurately, or to
    get the results quickly. The logic to stop connecting for
    *--ssl-error*
    can be controlled with following additional options:
      - \--ssl-error-max=CNT - max. continous errors
      - \--ssl-error-timeout=SEC - timeout when to treat a failure as
        error
      - \--ssl-error-total=CNT - max. amount of errors

<!-- end list -->

  -
    This means that no more connections are made when more than
      - \--ssl-error-max errors occour sequentialy
    or
      - \--ssl-error-total errors occoured

<!-- end list -->

  -
    Examples:
      - `--ssl-error-max=3`
      - `--ssl-error-timeout=6`
      - `--ssl-error-total=6`
    no more connections are made if for example any sequence of timeouts
    occour:

` 0 5 2 2                   - --ssl-error-max matches `
` 0 1 3 0 0 0 4 1 2 2 2     - --ssl-error-max matches`
` 0 5 0 2 0 2 2 0 2 0 2     - --ssl-error-total matches`

  -
    This allows to fine-tune the condition when to stop connecting to
    the
    target. For example, continous but not consecutive timeouts may
    indi-
    cate a bad or instable network connection, but not that the target
    to
    be connected blocks. In such a case sequence of timeouts like
    follows
    may be observed (assuming `--ssl-error-max=3`):

` 0 5 1 2 2 2 4 2 3 2 3 3 3 2`
`       ^                 ^____ stop for --ssl-error-timeout=3`
`       `

|______________________ stop for
--ssl-error-timeout=2

  -
    On normal (even slow) network connections dozens of connections per
    second are usual, hence the timeout is always 0 or 1. Based on that
    experience *--ssl-error* is enabled and set with defaults as
    follows:
      - `--ssl-error-max=5`
      - `--ssl-error-timeout=1`
      - `--ssl-error-total=10`

##### Poor Systems

  -
    Use of *openssl(1)* is disabled by default on Windows due to various
    performance problems. It needs to be enabled with *--openssl*
    option.

<!-- end list -->

  -
    On Windows the usage of `openssl s_client` needs to be enabled using
    [--s_client](#--s_client "wikilink") option.

<!-- end list -->

  -
    On Windows it's a pain to specify the path for
    [--openssl=TOOL](#--openssl=TOO "wikilink") option.
    Variants are:

:\* --openssl=/path/to/openssl.exe

:\* --openssl=X:/path/to/openssl.exe

:\* --openssl=\\path\\to\\openssl.exe

:\* --openssl=X:\\path\\to\\openssl.exe

:\* --openssl=\\\\path\\\\to\\\\openssl.exe

:\* --openssl=X:\\\\path\\\\to\\\\openssl.exe

  -
    You have to fiddle around to find the proper one.

##### Debug and Trace Output

  -
    When both [--trace-key](#--trace-key "wikilink") and
    [--trace-cmd](#--trace-cmd "wikilink") options are used, output is
    mixed, obviously. Hint: output for
    [--trace-cmd](#--trace-cmd "wikilink") always contains "CMD".

<!-- end list -->

  -
    Any *--trace\** option implies
    [--trace-time](#--trace-time "wikilink") .

#### DEPENDENCIES

  -
    All perl modules and all private moduels and files will be searched
    for using paths available in perl's `@INC` variable. `@INC` will
    be prepended by following paths:

:\* .

:\* ./lib

:\* INSTALL_PATH

:\* INSTALL_PATH/lib

  -
    Where `INSTALL_PATH` is the path where the tool is installed.
    To see which files have been included use:

`   o-saft.pl +version --v --user`

##### Perl Modules

  - *IO::Socket::SSL(1)*
  - *IO::Socket::INET(1)*
  - *Net::SSLeay(1)*
  - *Net::SSLinfo(1)*
  - *Net::SSLhello(1)*

##### Additional Files used if requested

  - *.o-saft.pl*
  - *o-saft-dbx.pm*
  - *o-saft-man.pm*
  - *o-saft-usr.pm*
  - *o-saft-README*
  - *o-saft-docker*

#### INSTALLATION

  -
    The tool can be installed in any path. It just requres the modules
    as
    described in [DEPENDENCIES](#DEPENDENCIES "wikilink") above.
    However, it's recommended that the
    modules *Net::SSLhello* and *Net::SSLinfo* are found in the
    directory
    `./Net/` where `o-saft.pl` is installed.

<!-- end list -->

  -
    For security reasons, most modern libraries disabled or even removed
    insecure or "dirty" functionality. As this tool's purpose is to find
    such insecure settings, functions, etc., it needs these dirty things
    enabled. What we need is (incomplete list):

:\* insecure protocols like SSLv2, SSLv3

:\* more more ciphers enabled, like NULL-MD5, AECDH-NULL-SHA, etc.

:\* some SSL extensions and options

  -
    Therefore we recommend to compile and install at least following:

:\* openssl with SSLv2, SSLv3 and more ciphers enabled

:\* Net::SSLeay compiled with openssl version as described before.

  -
    Please read the [SECURITY](#SECURITY "wikilink") section first
    before following the install
    instructions below.

##### OpenSSL

  -
    Currently (since 18.06.18) it is recommend to build openssl using

`   contrib/install_openssl.sh`

  -
    Other possibilities are:
      - compiling openssl using following sources
    <!-- end list -->
      -
        <https://github.com/PeterMosmans/openssl/>
        see [Example: Compile
        OpenSSL](#Example:_Compile_OpenSSL "wikilink"),
    <!-- end list -->
      - use any of the precomiled versions provided by
        <https://testssl.sh/>

<!-- end list -->

  -
    The sources are available at
      - <https://github.com/PeterMosmans/openssl/archive/1.0.2-chacha.zip>
    A precomiled static versions are available at
      - <https://github.com/drwetter/testssl.sh/tree/master/bin>

<!-- end list -->

  -
    For all following installation examples we assume:
      - openssl-1.0.2-chacha.zip or openssl-1.0.2d.tar.gz
      - /usr/local as bae installation directory
      - a bourne shell (sh) compatible shell

##### Example: Precompiled OpenSSL

  -
    Simply download the tarball or zip file for your platform, unpack
    it,
    and install (copy) the binaries into a directory of your choice.

##### Example: Compile OpenSSL

  -
    OpenSSL can be used from <http://openssl.org/> or, as recommended,
    from
    <https://github.com/PeterMosmans/openssl/> .

<!-- end list -->

  -
    **OpenSSL-chacha**
    Compiling and installing the later is as simple as:

`   unzip openssl-1.0.2-chacha.zip`
`   cd openssl-1.0.2-chacha`
`   ./config --shared -Wl,-rpath=/usr/local/lib`
`   make`
`   make test`
`   make install`

  -
    which will install openssl, libssl.so, libcrypto.so and some include
    files as well as the include files in /usr/local/ .
    The shared version of the libraries are necessary for Net::SSLeay.

<!-- end list -->

  -
    **OpenSSL.org**
    Building openssl from the offical openssl.org sources requires some
    patching before compiling and installing the libraries and binaries.

<!-- end list -->

  -
    Example with openssl-1.0.2d:

`  echo == unpack tarball`
`  tar xf openssl-1.0.2d.tar.gz`
`  cd openssl-1.0.2d`

`  echo == backup files to be modified`
`  cp ssl/s2_lib.c{,.bak}`
`  cp ssl/s3_lib.c{,.bak}`
`  cp ssl/ssl3.h{,.bak}`
`  cp ssl/tls1.h{,.bak}`

`  echo == patch files`
`  vi ssl/tls1.h         +/TLS1_ALLOW_EXPERIMENTAL_CIPHERSUITES/`
`           # define TLS1_ALLOW_EXPERIMENTAL_CIPHERSUITES  1`
`  vi ssl/ssl3.h ssl/s{2,3}_lib.c   +"/# *if 0/"`
`           #==> remove all   # if 0  and corresponding  #endif`
`           #    except if lines contain:`
`           #        _FZA`
`           #        /* Fortezza ciphersuite from SSL 3.0`
`           #        /* Do not set the compare functions,`
`           #        if (s->shutdown & SSL_SEND_SHUTDOWN)`

`  echo == configure with static libraries`
`  echo omitt the zlib options if zlib-1g-dev is not installed`
`  echo omitt the krb5 options if no kerberos libraries available`
`  ./config --prefix=/usr/local --openssldir=/usr/local/ssl \`
`      enable-zlib zlib zlib-dynamic enable-ssl2 \`
`      enable-krb5 --with-krb5-flavor=MIT \`
`      enable-mdc2 enable-md2  enable-rc5  enable-rc2 \`
`      enable-cms  enable-ec   enable-ec2m enable-ecdh enable-ecdsa \`
`      enable-gost enable-seed enable-idea enable-camellia \`
`      enable-rfc3779 enable-ec_nistp_64_gcc_128 \`
`      experimental-jpake -fPIC \`
`      -DTEMP_GOST_TLS -DTLS1_ALLOW_EXPERIMENTAL_CIPHERSUITES \`
`      shared`

`  echo == make binaries and libraries`
`  make depend`
`  make`
`  make test`
`  make install`

`  echo == if you want static binaries and libraries`
`  make clean`
`  echo same ./config as before but without shared option`
`  ./config --prefix=/usr/local --openssldir=/usr/local/ssl \`
`      enable-zlib zlib zlib-dynamic enable-ssl2 \`
`      enable-krb5 --with-krb5-flavor=MIT \`
`      enable-mdc2 enable-md2 enable-rc5 enable-rc2 \`
`      enable-cms  enable-ec   enable-ec2m enable-ecdh enable-ecdsa \`
`      enable-gost enable-seed enable-idea enable-camellia \`
`      enable-rfc3779 enable-ec_nistp_64_gcc_128 \`
`      experimental-jpake -fPIC \`
`      -DTEMP_GOST_TLS -DTLS1_ALLOW_EXPERIMENTAL_CIPHERSUITES`
`  make depend`
`  make`
`  make test`
`  echo next make will overwrite the previously installed dynamic`
`  echo shared openssl binary with the static openssl binary`
`  make install`

##### Example: Compile Net::SSLeay

  -
    To enable support for ancient protocol versions, *Net::SSLeay* must
    be
    compiled manually after patching 'SSLeay.xs' (see below).
    Reason is, that *Net::SSLeay* enables some functionality for SSL/TLS
    according the identified openssl version. There is, currently
    (2015),
    no possibility to enable this functionality by passing options on to
    the configuration script `perl Makefile.PL`.

`   echo == unpack tarball`
`   tar xf Net-SSLeay-1.72.tar.gz`
`   cd Net-SSLeay-1.72`

`   echo == patch files`
`   echo "edit SSLeay.xs and change some #if as described below"`
`   env OPENSSL_PREFIX=/usr/local perl Makefile.PL PREFIX=/usr/local \`
`         INC=/usr/local/include  DEFINE=-DOPENSSL_BUILD_UNSAFE=1`
`   make`
`   make install`
`   cd /tmp && o-saft.pl +version`

  -
    SSLeay.xs needs to be changed as follows:

<!-- end list -->

  - search for

`   #ifndef OPENSSL_NO_SSL2`
`   #if OPENSSL_VERSION_NUMBER < 0x10000000L`
` `
`   const SSL_METHOD *`
`   SSLv2_method()`
` `
`   #endif`
`   #endif`
` `
`   #ifndef OPENSSL_NO_SSL3`
`   #if OPENSSL_VERSION_NUMBER < 0x10002000L`

`   const SSL_METHOD *`
`   SSLv3_method()`

`   #endif`
`   #endif`

  - and replace by

`   const SSL_METHOD *`
`   SSLv2_method()`

`   const SSL_METHOD *`
`   SSLv3_method()`

  -
    Note that *Net::SSLeay* will be installed in `/usr/local/` then.
    This
    can be adapted to your needs by passing another path to the `PREFIX`
    and `DESTDIR` parameter.

<!-- end list -->

  -
    Following command can be used to check which methods are avilable in
    Net::SSLeay, hence above patches can be verified:

`    perl -MLNet::SSLinfo -le print Net::SSLinfo::ssleay_test();`

##### Testing OpenSSL

  -
    After installation as descibed above finished, openssl may be
    tested:

`   echo already installed openssl (found with PATH environment)`
`   openssl ciphers -v`
`   openssl ciphers -V -ssl2`
`   openssl ciphers -V -ssl3`
`   openssl ciphers -V ALL`
`   openssl ciphers -V ALL:COMPLEMENTOFALL`
`   openssl ciphers -V ALL:eNULL:EXP`

`   echo own compiled and installed openssl `
`   /usr/local/openssl ciphers -v`
`   /usr/local/openssl ciphers -V -ssl2`
`   /usr/local/openssl ciphers -V -ssl3`
`   /usr/local/openssl ciphers -V ALL`
`   /usr/local/openssl ciphers -V ALL:COMPLEMENTOFALL`
`   /usr/local/openssl ciphers -V ALL:eNULL:EXP`

The difference should be obvious. Note, the commands using
`ALL:COMPLEMENTOFALL` and `ALL:eNULL:EXP` should return the same result.

##### Testing Net::SSLeay

  -
    As we want to test the separately installed *Net::SSLeay*, it is
    best
    to do it with `o-saft.pl` itself:

`   o-saft.pl +version`

  -
    we should see a line similar to follwong at the end of the output:

`   Net::SSLeay   1.72  /usr/local/lib/x86_64-linux-gnu/perl/5.20.2/Net/SSLeay.pm`

  -
    Now check for supported (known) ciphers:

`   o-saft.pl ciphers -V`

  -
    we should see lines similar to those of the last
    `/usr/local/openssl`
    call. However, it should contain more cipher lines.

##### Stand-alone Executable

  -
    Some people asked for a stand-alone executable (mainly for Windows).
    Even perl is a scripting language there are situations where a
    stand-
    alone executable would be nice, for example if the installed perl
    and
    its libraries are outdated, or if perl is missing at all.

<!-- end list -->

  -
    Currently (2016) there are following possibilities to generate such
    a
    stand-alone executable:

<!-- end list -->

  - perl with PAR::Packer module

`     pp -C -c o-saft.pl`
`     pp -C -c o-saft.pl -M Net::DNS -M Net::SSLeay -M IO::Socket \`
`                        -M Net::SSLinfo -M Net::SSLhello -M osaft`
`     pp -C -c checkAllCiphers.pl`
`     pp -C -c checkAllCiphers.pl -M Net::DNS`

  - ActiveState perl with its perlapp

`     perlapp --clean o-saft.pl`
`     perlapp --clean o-saft.pl -M Net::DNS -M Net::SSLeay -M IO::Socket \`
`                 -M Net::SSLinfo -M Net::SSLhello -M osaft`
`     perlapp --clean checkAllCiphers.pl`
`     perlapp --clean checkAllCiphers.pl -M Net::DNS -M osaft`

  - perl2exe from IndigoSTar

`     perl2exe o-saft.pl`
`     perl2exe checkAllCiphers.pl`

  -
    For details on building the executable, for example how to include
    all required modules, please refer to the documentation of the tool.
      - <http://search.cpan.org/~rschupp/PAR-Packer-1.030/lib/PAR/Packer.pm>
      - <http://docs.activestate.com/pdk/6.0/PerlApp.html>
      - <http://www.indigostar.com>

<!-- end list -->

  -
    Note that pre-build executables (build by perlapp, perl2exe) cannot
    be provided due to licence problems.
    Also note that using stand-alone executable have not been tested the
    same way as the `o-saft.pl` itself. Use them at your own risk.

#### DOCKER

  -
    The tool can be used inside a Docker image. With *o-saft-docker* and
    a
    *Dockerfile* (both are part of the distribution), a proper Docker
    image
    will be build easily. o-saft-docker can also be used to run commands
    with *o-saft.pl* inside the Docker image, example:

`  o-saft-docker +info some.tld`

  -
    For more details, please refer to:

`  o-saft-docker -help`
`  o-saft-docker usage`

#### SEE ALSO

  - *openssl(1)*, *Net::SSLeay(1)*, *Net::SSLhello*, *Net::SSLinfo*,
    *timeout(1)*
  - <http://www.openssl.org/docs/apps/ciphers.html>
  - *IO::Socket::SSL(1)*, *IO::Socket::INET(1)*
  - *o-saft-docker*, *o-saft-docker-dev*, *Dockerfile*, *docker*

#### HACKER's INFO

##### Note on SSL versions

  -
    Automatically detecting the supported SSL versions of the
    underlaying
    system is a hard job and not always possible. Reasons could be:

<!-- end list -->

  - used perl modules (*Socket::SSL*, *Net::SSLeay*) does not handle
    errors

<!-- end list -->

  -
    properly. Erros may be:

`  invalid SSL_version specified at ... IO/Socket/SSL.pm`

`  Use of uninitialized value in subroutine entry at lib/IO/Socket/SSL.pm`

  - the underlaying libssl does not support the version, which then may

<!-- end list -->

  -
    result in segmentation fault

<!-- end list -->

  - the underlaying libssl is newer than the perl module and the module

<!-- end list -->

  -
    has not been reinstalled. This most often happens with *Net::SSLeay*
    This can be detected with (see version numbers for *Net::SSLeay*):

`   o-saft.pl +version`

  - perl (in particular a used module, see above) may bail out with a

<!-- end list -->

  -
    compile error, like

`   Can't locate auto/Net/SSLeay/CTX_v2_new.al in @INC ...`

  -
    We try to detect unsupported versions and disable them
    automatically,
    a warning like follwoing is shown then:

`   **WARNING: SSL version SSLv2 not supported by openssl`

  -
    If problems occour with SSL versions, following commands and options
    may help to to get closer to the reason or can be used as
    workaround:

`   o-saft.pl +version`
`   o-saft.pl +version `

| grep versions

`   o-saft.pl +version `

| grep 0x

`   o-saft.pl +protocols your.tld`
`   o-saft.pl +protocols your.tld --no-rc`

  -
    If problems occour with SSL versions, following commands and options
    Checking for SSL version is done at one place in the code, search
    for

`    supported SSL versions`

##### Using private libssl.so and libcrypt.so

  -
    For all cryptographic functionality the libraries installed on the
    system will be used. This is in particular perl's *Net:SSLeay*
    module,
    the system's *libssl.so* and *libcrypt.so* and the *openssl*
    executable.

<!-- end list -->

  -
    It is possible to provide your own libraries, if the perl module and
    the executable are linked using dynamic shared objects (aka shared
    library, position independent code).
    The appropriate option is *--lib=PATH* .

<!-- end list -->

  -
    On most systems these libraries are loaded at startup of the
    program.
    The runtime loader uses a preconfigured list of directories where to
    find these libraries. Also most systems provide a special
    environment
    variable to specify additional paths to directories where to search
    for libraries, for example the `LD_LIBRARY_` variable.
    This is the default environment variable used herein. If your system
    uses another name it must be specified with the *--envlibvar=NAME*
    option, where `NAME` is the name of the environment variable.

##### Understanding *--exe=PATH*, *--lib=PATH*, *--openssl=FILE*

  -
    If any of [--exe=PATH](#--exe=PATH "wikilink") or
    [--lib=PATH](#--lib=PATH "wikilink") is provided, the pragram calls
    (`exec`) itself recursively with all given options, except the
    option
    itself. The environment variables `LD_LIBRARY_PATH` and `PATH` are
    set before executing as follows:

:\* prepend `PATH` with all values given with
[--exe=PATH](#--exe=PATH "wikilink")

:\* prepend `LD_LIBRARY_PATH` with all values given with
[--lib=PATH](#--lib=PATH "wikilink")

  -
    This is exactly, what [Cumbersome
    Approach](#Cumbersome_Approach "wikilink") below describes. So these
    option simply provide a shortcut for that.

<!-- end list -->

  -
    Note that [--openssl=TOOL](#--openssl=TOOL "wikilink") is a full
    path to the *openssl* executable
    and will not be changed. However, if it is a relative path, it might
    be searched for using the previously set `PATH` (see above).

<!-- end list -->

  -
    Note that `LD_LIBRARY_PATH` is the default. It can be changed with
    the [--envlibvar=NAME](#--envlibvar=NAME "wikilink") option.

<!-- end list -->

  -
    While *--exe* mainly impacts the openssl executable, *--lib* also
    impacts o-saft.pl itself, as it loads other shared libraries if
    found.

<!-- end list -->

  -
    Bear in mind that all these options can affect the behaviour of the
    openssl subsystem, influencing both which executable is called and
    which shared libraries will be used.

<!-- end list -->

  -
    NOTE that no checks are done if the options are set proper. To
    verify
    the settings, following commands may be used:

`   o-saft.pl --lib=YOU-PATH --exe=YOUE-EXE +version`
`   o-saft.pl --lib=YOU-PATH --exe=YOUE-EXE --v +version`
`   o-saft.pl --lib=YOU-PATH --exe=YOUE-EXE --v --v +version`

  -
    Why so many options? Exactly as described above, these options allow
    the users to tune the behaviour of the tool to their needs. A common
    use case is to enable the use of a separate openssl build
    independent
    of the openssl package used by the operating system. This allows the
    user fine grained control over openssl's encryption suites which are
    compiled/available, without affecting the core system.

##### Caveats

  -
    Depending on your system and the used modules and executables, it
    can
    be tricky to replace the configured shared libraries with own ones.
    Reasons are:
    a) the linked library name contains a version number,
    b) the linked library uses a fixed path,
    c) the linked library is searched at a predefined path,
    d) the executable checks the library version when loaded.

<!-- end list -->

  -
    Only the first one a) can be circumvented. The last one d) can often
    be ignored as it only prints a warning or error message.

<!-- end list -->

  -
    To circumvent the "name with version number" problem try following:

<!-- end list -->

  - 1\. use *ldd* (or a similar tool) to get the names used by
    *openssl*:

<!-- end list -->

  -
    ldd /usr/bin/openssl

<!-- end list -->

  -
    which returns something like:

<!-- end list -->

  -
    libssl.so.0.9.8 =\> /lib/libssl.so.0.9.8 (0x00007f940cb6d000)
    libcrypto.so.0.9.8 =\> /lib/libcrypto.so.0.9.8 (0x00007f940c7de000)
    libdl.so.2 =\> /lib/x86_64-linux-gnu/libdl.so.2
    (0x00007f940c5d9000)
    libz.so.1 =\> /lib/x86_64-linux-gnu/libz.so.1 (0x00007f940c3c1000)
    libc.so.6 =\> /lib/x86_64-linux-gnu/libc.so.6 (0x00007f940c02c000)
    /lib64/ld-linux-x86-64.so.2 (0x00007f940cdea000)

<!-- end list -->

  -
    Here only the first two libraries are important. Both, libcrypto.so
    and libssl.so need to be version "0.9.8" (in this example).

<!-- end list -->

  - 2\. create a directory for your libraries, i.e.:

<!-- end list -->

  -
    mkdir /tmp/dada

<!-- end list -->

  - 3\. place your libraries there, assuming they are:

<!-- end list -->

  -
    /tmp/dada/libssl.so.1.42
    /tmp/dada/libcrypto.so.1.42

<!-- end list -->

  - 4\. create symbolic links in that directory:

<!-- end list -->

  -
    ln -s libssl.so.1.42 libssl.so.0.9.8
    ln -s libcrypto.so.1.42 libcrypto.so.0.9.8

<!-- end list -->

  - 5\. test program with following option:

`   o-saft.pl +libversion --lib=/tmp/dada`
`   o-saft.pl +list --v   --lib=/tmp/dada`

  -
    or:

`   o-saft.pl +libversion --lib=/tmp/dada -exe=/path/to-openssl`
`   o-saft.pl +list --v   --lib=/tmp/dada -exe=/path/to-openssl`

  - 6\. start program with your options, i.e.:

`   o-saft.pl --lib=/tmp/dada +ciphers`

  -
    This works if *openssl(1)* uses the same shared libraries as
    *Net:SSLeay(1)*, which most likely is the case.

<!-- end list -->

  -
    It's tested with Unix/Linux only. It may work on other platforms
    also
    if they support such an environment variable and the installed
    *Net::SSLeay(1)* and *openssl(1)* are linked using dynamic shared
    objects.

<!-- end list -->

  -
    Depending on compile time settings and/or the location of the used
    tool or lib, a warning like following may occur:

`  WARNING: can't open config file: /path/to/openssl/ssl/openssl.cnf`

  -
    This warning can be ignored, usually as *req* or *ca* sub commands
    of
    openssl is not used here.
    To fix the problem, either use *--openssl-cnf=FILE* option or set
    the
    the environment variable OPENSSL_CONF properly.

###### Cumbersome Approach

  -
    A more cumbersome approach to call this program is to set following
    environment variables in your shell:

`  PATH=/tmp/dada-1.42/apps:$PATH`
`  LD_LIBRARY_PATH=/tmp/dada-1.42`

###### Windows Caveats

  -
    I.g. the used libraries on Windows are *libeay32.dll* and
    *ssleay32.dll*.

<!-- end list -->

  -
    Windows also supports the `LD_LIBRARY_PATH` environment variable. If
    it
    does not work as expected with that variable, it might be possible
    to
    place the libs in the same directory as the corresponding executable
    (which is found by the `PATH` environment variable).

##### Using CGI mode

  -
    This script can be used as CGI application. Output is the same as in
    common CLI mode, using 'Content-Type:text/plain'. Keep in mind that
    the used modules like *Net::SSLeay* will write some debug messages
    on STDERR instead STDOUT. Therefore multiple *--v* and/or *--trace*
    options behave slightly different.

<!-- end list -->

  -
    No additional external files like [RC-FILE](#RC-FILE "wikilink") or
    [DEBUG-FILE](#DEBUG-FILE "wikilink") are read
    in CGI mode; they are silently ignored.
    Some options are disabled in CGI mode because they are dangerous or
    don't make any sense.

###### WARNING

  -
    There are no input data validation checks implemented herein. All
    input data is url-decoded once and then used verbatim.
    More advanced checks must be done outside before calling this tool.

<!-- end list -->

  -
    It's not recommended to run this tool in CGI mode.
    You have been warned\!

##### Using user specified code

  -
    There are some functions called within the program flow, which can
    be
    filled with any perl code. Empty stubs of the functions are prepared
    in *o-saft-usr.pm*. See also [USER-FILE](#USER-FILE "wikilink").

#### DEBUG

##### Debugging, Tracing

  -
    Following options and commands are useful for hunting problems with
    SSL connections and/or this tool. Note that some options can be
    given
    multiple times to increase amount of listed information. Also keep
    in
    mind that it's best to specify *--v* as very first argument.

<!-- end list -->

  -
    Note that the file *o-saft-dbx.pm* is required, if any *--trace\**
    or *--v* option is used.

###### Commands

  - *+dump*
  - *+libversion*
  - *+s_client*
  - *+todo*
  - *+version*

###### Options

  - *--v*
  - *--v--*
  - *--trace*
  - *--trace-arg*
  - *--trace-cmd*
  - *--trace-key*

<!-- end list -->

  -
    Empty or undefined strings are written as `<`<undefined>`>` in
    texts.
    Some parameters, in particular those of HTTP responses, are written
    as `<`<response>`>`. Long parameter lists are abbreviated with
    `...`.

###### Output

  -
    When using *--v* and/or *--trace* options, additional output will
    be prefixed with a `#` (mainly as first, left-most character.
    Following formats are used:

:\* \#\[space\]

  -
    Addition text for verbosity (*--v* options).

:\* \#\[variable name\]\[TAB\]

  -
    Internal variable name (*--trace-key* options).

:\* \#o-saft.pl::

:\* \#Net::SSLinfo::

  -
    Trace information for *--trace* options.

:\* \#{

  -
    Trace information from `NET::SSLinfo` for *--trace* options.
    These are data lines in the format: \#{ variable name : value \#}
    Note that `value` here can span multiple lines and ends with \#}

###### Using outdated modules

  -
    The tools was designed to work with old perl modules too. When using
    old modules, a proper `**WARNING:` will be printed. These warinings
    cannot be switched of using --no-warning .
    The warning also informs about the missing functionality or check.

<!-- end list -->

  -
    I.g. it is best to install newer versions of the module if possible.
    A good practice to check if modules are available in a proper
    version
    is to call:

` o-saft.pl +version`
` o-saft.pl +version --v --v`

  -
    Following example shows the result without warnings:

`     === reading: ./.o-saft.pl (RC-FILE done) ===`
`     === reading: Net/SSLhello.pm (O-Saft module done) ===`
`     === reading: Net/SSLinfo.pm (O-Saft module done) ===`
`     === ./o-saft.pl 16.09.09 ===`
`         Net::SSLeay::`
`            ::OPENSSL_VERSION_NUMBER()    0x268443744`
`            ::SSLeay()                    0x268443744`
`         Net::SSLeay::SSLeay_version()    OpenSSL 1.0.2-chacha (1.0.2f-dev)`
`     = openssl =`
`         version of external executable   OpenSSL 1.0.2-chacha (1.0.2f-dev)`
`         external executable              /opt/openssl-chacha/bin/openssl`
`         used environment variable (name) LD_LIBRARY_PATH`
`         environment variable (content)   <`<undef>`>`
`         path to shared libraries         `
`         full path to openssl.cnf file    <`<undef>`>`
`         common openssl.cnf files         /usr/lib/ssl/openssl.cnf \`
`                                          /etc/ssl/openssl.cnf \`
`                                          /System//Library/OpenSSL/openssl.cnf \`
`                                          /usr/ssl/openssl.cnf`
`         URL where to find CRL file       <`<undef>`>`
`         directory with PEM files for CAs /opt/tools/openssl-chacha/ssl/certs`
`         PEM format file with CAs         /etc/ssl/certs/ca-certificates.crt`
`         common paths to PEM files for CAs /etc/ssl/certs /usr/lib/certs \`
`                                           /System/Library/OpenSSL`
`         common PEM filenames for CAs     ca-certificates.crt \`
`                                          certificates.crt certs.pem`
`         number of supported ciphers      177`
`         openssl supported SSL versions   SSLv3 TLSv1 TLSv11 TLSv12`
`         o-saft.pl known SSL versions     SSLv2 SSLv3 TLSv1 TLSv11 TLSv12 TLSv13 \`
`                                          DTLSv09 DTLSv1 DTLSv11 DTLSv12 DTLSv13`
`     = o-saft.pl +cipherall =`
`         default list of ciphers          0x03000000 .. 0x030000FF, 0x0300C000 .. 0x0300C0FF, \`
`                                          0x0300CC00 .. 0x0300CCFF, 0x0300FE00 .. 0x0300FFFF,`
`                                          `
`     = Required (and used) Modules =`
`         @INC                 ./ ./lib . /bin /usr/share/perl5 \`
`                              /usr/lib/x86_64-linux-gnu/perl5/5.20 \`
`                              /usr/lib/x86_64-linux-gnu/perl/5.20 \`
`                              /usr/share/perl/5.20 /usr/local/lib/site_perl .`
`     =   module name            VERSION  found in`
`     =   ----------------------+--------+------------------------------------------`
`         IO::Socket::INET       1.35     /usr/lib/x86_64-linux-gnu/perl/5.20/IO/Socket/INET.pm`
`         IO::Socket::SSL        2.002    /usr/share/perl5/IO/Socket/SSL.pm`
`         Net::DNS               0.81     /usr/lib/x86_64-linux-gnu/perl5/5.20/Net/DNS.pm`
`         Net::SSLeay            1.72     /usr/lib/x86_64-linux-gnu/perl5/5.20/Net/SSLeay.pm`
`         Net::SSLinfo           16.06.01 Net/SSLinfo.pm`
`         Net::SSLhello          16.05.16 Net/SSLhello.pm`
`         osaft                  16.05.10 osaft.pm`

  -
    Following example shows the result with warnings:

`     === reading: ./.o-saft.pl (RC-FILE done) ===`
`     === reading: ./Net/SSLhello.pm (O-Saft module done) ===`
`     **WARNING: ancient Net::SSLeay 1.35 < 1.49; cannot use ::initialize at /Net/SSLinfo.pm line 481.`
`     === reading: ./Net/SSLinfo.pm (O-Saft module done) ===`
`     **WARNING: ancient perl has no 'version' module; version checks may not be accurate; at o-saft.pl line 1662.`
`     **WARNING: ancient Net::SSLeay 1.35 < 1.49 detected; at o-saft.pl line 1687.`
`     **WARNING: ancient IO::Socket::SSL 1.22 < 1.37 detected; at o-saft.pl line 1687.`
`     **WARNING: ancient version IO::Socket::SSL 1.22 < 1.90 does not support SNI or is known to be buggy; SNI disabled; at o-saft.pl line 5905.`
`     !!Hint: --force-openssl can be used to disables this check`
`     **WARNING: ancient version Net::SSLeay 1.35 < 1.49  may throw warnings and/or results may be missing; at o-saft.pl line 5934.`
`     **WARNING: SSL version 'TLSv11': not supported by Net::SSLeay; not checked`
`     **WARNING: SSL version 'TLSv12': not supported by Net::SSLeay; not checked`
`     **WARNING: SSL version 'TLSv13': not supported by Net::SSLeay; not checked`
`     === o-saft.pl 16.09.09 ===`
`         Net::SSLeay::`
`            ::OPENSSL_VERSION_NUMBER()    0x9470143`
`     **WARNING: ancient version Net::SSLeay 1.35 < 1.49; cannot compare SSLeay with openssl version at o-saft.pl line 4778.`
`            ::SSLeay()                    0x1.35`
`     **WARNING: ancient version Net::SSLeay 1.35 < 1.49; detailed version not available at o-saft.pl line 4806.`
`     = openssl =`
`         version of external executable   OpenSSL 0.9.8y 5 Feb 2013`
`         external executable              /usr/bin/openssl`
`         used environment variable (name) LD_LIBRARY_PATH`
`         environment variable (content)   <`<undef>`>`
`         path to shared libraries`
`         full path to openssl.cnf file    <`<undef>`>`
`         common openssl.cnf files         /usr/lib/ssl/openssl.cnf \`
`                                          /etc/ssl/openssl.cnf \`
`                                          /System//Library/OpenSSL/openssl.cnf \`
`                                          /usr/ssl/openssl.cnf`
`         URL where to find CRL file       <`<undef>`>`
`         directory with PEM files for CAs /System/Library/OpenSSL/certs`
`         PEM format file with CAs         <`<undef>`>`
`         common paths to PEM files for CAs /etc/ssl/certs /usr/lib/certs /System/Library/OpenSSL`
`         common PEM filenames for CAs     ca-certificates.crt certificates.crt certs.pem`
`         number of supported ciphers      43`
`         openssl supported SSL versions   SSLv2 SSLv3 TLSv1`
`         o-saft.pl known SSL versions     SSLv2 SSLv3 TLSv1 TLSv11 TLSv12 TLSv13 \`
`                                          DTLSv09 DTLSv1 DTLSv11 DTLSv12 DTLSv13`
`     **WARNING: ancient version Net::SSLeay 1.35 < 1.49; cannot compare SSLeay with openssl version at o-saft.pl line 4778.`
`     **WARNING: used openssl version '9470143' differs from compiled Net:SSLeay '1.35'; ignored`
`     = o-saft.pl +cipherall =`
`         default list of ciphers          0x03000000 .. 0x030000FF, 0x0300C000 .. 0x0300C0FF,`
`                                          0x0300CC00 .. 0x0300CCFF, 0x0300FE00 .. 0x0300FFFF,`
`     = Required (and used) Modules =`
`         @INC                 ./ ./lib /bin /Library/Perl/Updates/5.10.0 \`
`                              /System/Library/Perl/5.10.0/darwin-thread-multi-2level \`
`                              /System/Library/Perl/5.10.0 \`
`                              /Library/Perl/5.10.0/darwin-thread-multi-2level \`
`                              /Library/Perl/5.10.0 \`
`                              /Network/Library/Perl/5.10.0/darwin-thread-multi-2level \`
`                              /Network/Library/Perl/5.10.0 \`
`                              /Network/Library/Perl \`
`                              /System/Library/Perl/Extras/5.10.0/darwin-thread-multi-2level \`
`                              /System/Library/Perl/Extras/5.10.0 .`
`     =   module name            VERSION  found in`
`     =   ----------------------+--------+------------------------------------------`
`         IO::Socket::INET       1.31     /System/Library/Perl/5.10.0/darwin-thread-multi-2level/IO/Socket/INET.pm`
`         IO::Socket::SSL        1.22     /System/Library/Perl/Extras/5.10.0/IO/Socket/SSL.pm`
`         Net::DNS               0.65     /System/Library/Perl/Extras/5.10.0/darwin-thread-multi-2level/Net/DNS.pm`
`         Net::SSLeay            1.35     /System/Library/Perl/Extras/5.10.0/darwin-thread-multi-2level/Net/SSLeay.pm`
`         Net::SSLinfo           16.06.01 ./Net/SSLinfo.pm`
`         Net::SSLhello          16.05.16 ./Net/SSLhello.pm`
`         osaft                  16.05.10 /osaft.pm`

  -
    Please keep in mind that the shown version numbers and the shown
    line
    numbers are examples and may differ on your system.

<!-- end list -->

  -
    When starting `o-saft.pl` with outdated modules, more `**WARNING:`
    will
    be shown. The warnings depend on the installed version of the
    module.
    `o-saft.pl` is known to work with at least:
      - *IO::Socket::INET* 1.31, *IO::Socket::SSL* 1.22, *Net::DNS*
        0.66, *Net::SSLeay* 1.30

#### TESTING

  -
    When talking about "testing the tool", functionl tests are meant. So
    this section describes "developer" rather than "user" options.

<!-- end list -->

  -
    Testing the tool is a challenging task. Beside the oddities
    described
    elsewhere, for example [Name Rodeo](#Name_Rodeo "wikilink"), there
    are a bunch of problems
    and error which may occour during runtime.

<!-- end list -->

  -
    Makefiles are used for testing functionality and code quality during
    development. These tests are implemented in the `./t/` directory,
    see
    the `Makefile.*` there.

<!-- end list -->

  -
    Following options and commands are available to improve testing.
    They
    mainly can simulate error conditions or stop execution properly
    (they
    are not intended for other use cases):

###### \+quit

  -
    Stop execution after processing all arguments and before precessing
    any target. The runtime configuration is complete at this point.

\======--exit=KEY======

  -
    Terminate `o-saft.pl` at specified `KEY`. For available `KEY` please
    see:

`   o-saft.pl --help=exit`
`   grep exit= o-saft.pl`

\======--cfg-init=KEY=VALUE======

  -
    With this option values in the internal %cfg hash can be set:

`   $cfg{KEY} = VALUE`

  -
    Only (perl) scalars or arrays can be set. The type will be detected
    automatically.

<!-- end list -->

  -
    Example, this option can be used to change the text used as prefix
    in each output line triggerd by the *--v* option:

`   o-saft.pl --cfg-init=prefix_verbose="#VERBOSE: "`

  -
    or the text used as prefix triggerd by the *--trace* option:

`   o-saft.pl --cfg-init=prefix_trace="#TRACE: "`

###### \--v

  -
    Print more information about checks.

###### \--trace

  -
    Print debugging messages.

<!-- end list -->

  -
    For more details, please see [Options for tracing and
    debugging](#Options_for_tracing_and_debugging "wikilink") .

#### EXAMPLES

  -
    ($0 in all following examples is the name of the tool)

##### General

`   o-saft.pl +cipher some.tld`
`   o-saft.pl +info   some.tld`
`   o-saft.pl +check  some.tld`
`   o-saft.pl +quick  some.tld`
`   o-saft.pl +help=commands`
`   o-saft.pl +list`
`   o-saft.pl +list --v`
`   o-saft.pl +certificate  some.tld`
`   o-saft.pl +fingerprint  some.tld 444`
`   o-saft.pl +after +dates some.tld`

##### Some Specials

  - Get an idea how messages look like

`   o-saft.pl +check --cipher=RC4 some.tld`

  - Check for Server Name Indication (SNI) usage only

`   o-saft.pl +sni some.tld`

  - Check for SNI and print certificate's subject and altname

`   o-saft.pl +sni +cn +altname some.tld`

  - Check for all SNI, certificate's subject and altname issues

`   o-saft.pl +sni_check some.tld`

  - Only print supported ciphers

`   o-saft.pl +cipher --enabled some.tld`

  - Only print unsupported ciphers

`   o-saft.pl +cipher --disabled some.tld`

  - Test for a specific ciphers

`   o-saft.pl +cipher --cipher=ADH-AES256-SHA some.tld`

  - Test all ciphers, even if not supported by local SSL implementation

`   o-saft.pl +cipherraw some.tld`
`   o-saft.pl +cipherall some.tld`
`   o-saft.pl +cipherall some.tld --range=full`
`   checkAllCiphers.pl example.tld --range=full --v`

  - Show supported (enabled) ciphers with their DH parameters:

`   o-saft.pl +cipher-dh some.tld`

  - Test using a private libssl.so, libcrypto.so and openssl

`   o-saft.pl +cipher --lib=/foo/bar-1.42 --exe=/foo/bar-1.42/apps some.tld`

  - Test using a private openssl

`   o-saft.pl +cipher --openssl=/foo/bar-1.42/openssl some.tld`

  - Test using a private openssl also for testing supported ciphers

`   o-saft.pl +cipher --openssl=/foo/bar-1.42/openssl --force-openssl some.tld`

  - Show current score settings

`   o-saft.pl --help=score`

  - Change a single score setting

`   o-saft.pl --cfg_score=http_https=42   +check some.tld `

  - Use your private score settings from a file

`   o-saft.pl --help=score > magic.score`

  -
    \# edit as needed: magic.score

`   o-saft.pl --cfg_score    magic.score  +check some.tld`

  - Use your private texts in output

`   o-saft.pl +check some.tld --cfg_text=desc=my special description`

  - Use your private texts from RC-FILE

`   o-saft.pl --help=cfg_text >> .o-saft.pl`

  -
    \# edit as needed: .o-saft.pl

`   o-saft.pl +check some.tld`

  - Use your private hint texts in output

`   o-saft.pl +check some.tld --cfg-hint=renegotiation="my special hint text"`

  - Get the certificate's Common Name for a bunch of servers:

`   o-saft.pl +cn example.tld some.tld other.tld`
`   o-saft.pl +cn example.tld some.tld other.tld --showhost --no-header`

  - Generate simple parsable output

`   o-saft.pl --legacy=quick --no-header +info  some.tld`
`   o-saft.pl --legacy=quick --no-header +check some.tld`
`   o-saft.pl --legacy=quick --no-header --trace-key +info  some.tld`
`   o-saft.pl --legacy=quick --no-header --trace-key +check some.tld`

  - Generate simple parsable output for multiple hosts

`   o-saft.pl --legacy=quick --no-header --trace-key --showhost +check some.tld other.tld`

  - Just for curiosity

`   o-saft.pl some.tld +fingerprint --format=raw`
`   o-saft.pl some.tld +certificate --format=raw `

| openssl x509 -noout -fingerprint

##### Specials for hunting problems with connections etc.

  - Show command line argument processing

`   o-saft.pl +info some.tld --trace-arg`

  - Simple tracing

`   o-saft.pl +cn   some.tld --trace`
`   o-saft.pl +info some.tld --trace`

  - A bit more tracing

`   o-saft.pl +cn   some.tld --trace --trace`

  - Show internal variable names in output

`   o-saft.pl +info some.tld --trace-key`

  - Show internal argument processeing

`   o-saft.pl +info --trace-arg some.tld`

  - Show internal control flow

`   o-saft.pl +info some.tld --trace-cmd`

  - Show internal timing

`   o-saft.pl +info some.tld --trace-time`

  - Show checking ciphers

`   o-saft.pl +cipher some.tld --v --v`

\-- following no longer implemented (8/2016)

  - List checked ciphers one per line

`   o-saft.pl +cipher some.tld --v --v -v`

  - Show processing of ciphers

`   o-saft.pl +cipher some.tld --v --v --v -v`

\--\>

  - Show values retrieved from target certificate directly

`   o-saft.pl +info some.tld --no-cert --no-cert --no-cert-text=Value-from-Certificate`

  - Show certificate CA verifications

`   o-saft.pl some.tld +chain_verify +verify +error_verify +chain`

  - Avoid most performance and timeout problems (don't use --v)

`   o-saft.pl +info some.tld --no-dns --no-sni --ignore-no-conn`
`   o-saft.pl +info some.tld --no-dns --no-sni --no-cert --no-http --no-openssl`

  - Identify timeout problems

`   o-saft.pl +info some.tld --trace-cmd`

this will show lines containing:

`    #O-Saft  CMD: test ...`

#### ATTRIBUTION

  -
    Based on ideas (in alphabetical order) of:
    cnark.pl, SSLAudit.pl sslscan, ssltest.pl, sslyze.py, testssl.sh

<!-- end list -->

  -
    O-Saft - OWASP SSL advanced forensic tool
    Thanks to Gregor Kuznik for this title.

<!-- end list -->

  -
    *cipherraw* and most proxy functionality implemented by Torsten
    Gigler.

<!-- end list -->

  -
    For re-writing some docs in proper English, thanks to Robb Watson.

<!-- end list -->

  -
    Code to check heartbleed vulnerability adapted from
    Steffen Ullrich (08. April 2014):
    <https://github.com/noxxi/p5-scripts/blob/master/check-ssl-heartbleed.pl>

<!-- end list -->

  -
    Colouration inspired by <https://testssl.sh/> .

#### AUTHOR

[Achim Hoffmann](User:achim "wikilink")

#### VERSION

  -
    @(\#) 16.09.16

-----

<small> Content of this wiki page generated with:

`o-saft.pl --no-warning --no-header --help=gen-wiki`

</small>

[Category:OWASP Project](Category:OWASP_Project "wikilink")
[Category:OWASP_Builders](Category:OWASP_Builders "wikilink")
[Category:OWASP_Defenders](Category:OWASP_Defenders "wikilink")
[Category:OWASP_Tool](Category:OWASP_Tool "wikilink")
[Category:SSL](Category:SSL "wikilink")
[Category:Test](Category:Test "wikilink")