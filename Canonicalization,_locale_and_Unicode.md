[Development Guide Table of
Contents](Guide_Table_of_Contents "wikilink")__TOC__

## Objective

To ensure the application is robust when subjected to encoded,
internationalized and Unicode input.

## Platforms Affected

All.

## Relevant COBIT Topics

DS11.9 – Data processing integrity

## Description

Applications are rarely tested for Unicode exploits, and yet many are
vulnerable due to the same sort of issues which allows HTTP Request
Smuggling to work – every browser, web server, web application firewall
or HTTP inspection agent, and other device treats user locale handling
in different (and usually confusing) manner.

Canonicalization deals with the way in which systems convert data from
one form to another. Canonical means the simplest or most standard form
of something. Canonicalization is the process of converting something
from one representation to the simplest form.

Web applications have to deal with lots of canonicalization issues from
URL encoding to IP address translation. When security decisions are made
based on less than perfectly canonicalized data, the application itself
must be able to deal with unexpected input safely.

'''NB: To be secure against canonicalization attacks does not mean that
every application has to be internationalized, but all applications
should be safe when Unicode and malformed representations are entered.
'''

## Unicode

Unicode Encoding is a method for storing characters with multiple bytes.
Wherever input data is allowed, data can be entered using
[Unicode](Unicode_Encoding "wikilink") to disguise malicious code and
permit a variety of attacks. RFC 2279 references many ways that text can
be encoded.

Unicode was developed to allow a Universal Character Set (UCS) that
encompasses most of the world's writing systems. Multi-octet characters,
however, are not compatible with many current applications and
protocols, and this has led to the development of a few UCS
transformation formats (UTF) with varying characteristics. UTF-8 has the
characteristic of preserving the full US-ASCII range. It is compatible
with file systems, parsers and other software relying on US-ASCII
values, but it is transparent to other values.

The importance of UTF-8 representation stems from the fact that
web-servers/applications perform several steps on their input of this
format. The order of the steps is sometimes critical to the security of
the application. Basically, the steps are "URL decoding" potentially
followed by "UTF-8 decoding", and intermingled with them are various
security checks, which are also processing steps.

If, for example, one of the security checks is searching for "..", and
it is carried out before UTF-8 decoding takes place, it is possible to
inject ".." in their overlong UTF-8 format. Even if the security checks
recognize some of the non-canonical format for dots, it may still be
that not all formats are known to it.

Consider the ASCII character "." (dot). Its canonical representation is
a dot (ASCII 2E). Yet if we think of it as a character in the second
UTF-8 range (2 bytes), we get an overlong representation of it, as C0
AE. Likewise, there are more overlong representations: E0 80 AE, F0 80
80 AE, F8 80 80 80 AE and FC 80 80 80 80 AE.

|  |                           |  |                                                         |
|  | ------------------------- |  | ------------------------------------------------------- |
|  | UCS-4 Range               |  | UTF-8 Encoding                                          |
|  | *0x00000000-0x0000007F*   |  | *0xxxxxxx*                                              |
|  | *0x00000080 - 0x000007FF* |  | *110xxxxx 10xxxxxx*                                     |
|  | *0x00000800-0x0000FFFF*   |  | *1110xxxx 10xxxxxx 10xxxxxx*                            |
|  | *0x00010000-0x001FFFFF*   |  | *11110xxx 10xxxxxx 10xxxxxx 10xxxxxx*                   |
|  | *0x00200000-0x03FFFFFF*   |  | *111110xx 10xxxxxx 10xxxxxx 10xxxxxx 10xxxxxx*          |
|  | *0x04000000-0x7FFFFFFF*   |  | *1111110x 10xxxxxx 10xxxxxx 10xxxxxx 10xxxxxx 10xxxxxx* |
|  |                           |  |                                                         |

Consider the representation C0 AE of a ".". Like UTF-8 encoding
requires, the second octet has "10" as its two most significant bits.
Now, it is possible to define 3 variants for it, by enumerating the rest
of the possible 2 bit combinations ("00", "01" and "11"). Some UTF-8
decoders would treat these variants as identical to the original symbol
(they simply use the least significant 6 bits, disregarding the most
significant 2 bits). Thus, the 3 variants are C0 2E, C0 5E and C0 FE.

It is thus possible to form illegal UTF-8 encodings, in two senses:

  - A UTF-8 sequence for a given symbol may be longer than necessary for
    representing the symbol.

<!-- end list -->

  - A UTF-8 sequence may contain octets that are in incorrect format
    (i.e. do not comply with the above 6 formats).

To further "complicate" things, each representation can be sent over
HTTP in several ways:

**In the raw**. That is, without URL encoding at all. This usually
results in sending non-ASCII octets in the path, query or body, which
violates the HTTP standards. Nevertheless, most HTTP servers do get
along just fine with non-ASCII characters.

**Valid URL encoding**. Each non-ASCII character (more precisely, all
characters that require URL encoding - a superset of non ASCII
characters) is URL-encoded. This results in sending, say, %C0%AE.

**Invalid URL encoding**. This is a variant of valid URL encoding,
wherein some hexadecimal digits are replaced with non-hexadecimal
digits, yet the result is still interpreted as identical to the
original, under some decoding algorithms. For example, %C0 is
interpreted as character number ('C'-'A'+10)\*16+('0'-'0') = 192.
Applying the same algorithm to %M0 yields ('M'-'A'+10)\*16+('0'-'0') =
448, which, when forced into a single byte, yields (8 least significant
bits) 192, just like the original. So, if the algorithm is willing to
accept non-hexadecimal digits (such as 'M'), then it is possible to have
variants for %C0 such as %M0 and %BG.

It should be kept in mind that these techniques are not directly related
to Unicode, and they can be used in non-Unicode attacks as well.

<http://www.example.com/cgi-bin/bad.cgi?foo=>../../bin/ls%20-al

URL Encoding of the example attack:

<http://www.example.com/cgi-bin/bad.cgi?foo=>..%2F../bin/ls%20-al

Unicode encoding of the example attack:

<http://www.example.com/cgi-bin/bad.cgi?foo=>..%c0%af../bin/ls%20-al

<http://www.example.com/cgi-bin/bad.cgi?foo=>..%c1%9c../bin/ls%20-al

<http://www.example.com/cgi-bin/bad.cgi?foo=>..%c1%pc../bin/ls%20-al

<http://www.example.com/cgi-bin/bad.cgi?foo=>..%c0%9v../bin/ls%20-al

<http://www.example.com/cgi-bin/bad.cgi?foo=>..%c0%qf../bin/ls%20-al

<http://www.example.com/cgi-bin/bad.cgi?foo=>..%c1%8s../bin/ls%20-al

<http://www.example.com/cgi-bin/bad.cgi?foo=>..%c1%1c../bin/ls%20-al

<http://www.example.com/cgi-bin/bad.cgi?foo=>..%c1%9c../bin/ls%20-al

<http://www.example.com/cgi-bin/bad.cgi?foo=>..%c1%af../bin/ls%20-al

<http://www.example.com/cgi-bin/bad.cgi?foo=>..%e0%80%af../bin/ls%20-al

<http://www.example.com/cgi-bin/bad.cgi?foo=>..%f0%80%80%af../bin/ls%20-al

<http://www.example.com/cgi-bin/bad.cgi?foo=>..%f8%80%80%80%af../bin/ls%20-al

### How to protect yourself

A suitable canonical form should be chosen and all user input
canonicalized into that form before any authorization decisions are
performed. Security checks should be carried out after UTF-8 decoding is
completed. Moreover, it is recommended to check that the UTF-8 encoding
is a valid canonical encoding for the symbol it represents.

<u><http://www.ietf.org/rfc/rfc2279.txt?number=2279> </u>

## Input Formats

Web applications usually operate internally as one of ASCII, ISO 8859-1,
or Unicode (Java programs are UTF-16 example). Your users may be using
another locale, and attackers can choose their locale and character set
with impunity.

### How to determine if you are vulnerable

Investigate the web application to determine if it asserts an internal
code page, locale, or culture.

If the default character set, locale is not asserted it will be one of
the following:

  - HTTP Posts. Interesting tidbit: All HTTP posts are required to be
    ISO 8859-1, which will lose data for most double byte character
    sets. You must test your application with your supported browsers to
    determine if they pass in fully encoded double byte characters
    safely

<!-- end list -->

  - HTTP Gets. Depends on the previously rendered page and per-browser
    implementations, but URL encoding is not properly defined for double
    byte character sets. IE can be optionally forced to do all submits
    as UTF-8 which is then properly canonicalized on the server

<!-- end list -->

  - .NET: Unicode (little endian)

<!-- end list -->

  - JSP implementations, such as Tomcat: UTF8 - see “javaEncoding” in
    web.xml by many servlet containers

<!-- end list -->

  - Java: Unicode (UTF-16, big endian, ***or*** depends on the OS during
    JVM startup)

<!-- end list -->

  - PHP: Set in php.ini, ISO 8859-1.

**NB: Many PHP functions make (invalid) assumptions as to character set
and may not work properly when changed to another character set. Test
your application with the new character set thoroughly\!**

### How to protect yourself

  - Determine your application’s needs, and set both the asserted
    language locale and character set appropriately.

## Locale assertion

The web server should always assert a locale and preferably a country
code, such as “en_US”, “fr_FR”, “zh_CN”

### How to determine if you are vulnerable

Use a HTTP header sniffer or even just telnet against your web server:

    HEAD / HTTP1.0

Should display something like this:

    HTTP/1.1 200 OK

    Date: Sun, 24 Jul 2005 08:13:17 GMT

    Server: Apache/1.3.29

    Connection: close

    Content-Type: text/html;''''' charset=iso-8859-1'

### How to protect yourself

Review and implement these guidelines:

<u><http://www.w3.org/International/technique-index></u>

At a minimum, select the correct output locale and character set.

## Double (or n-) encoding

Most web applications only check once to determine if the input is has
been de-encoded into the correct Unicode values. However, an attacker
may have doubly encoded the attack string.

### How to determine if you are vulnerable

  - Use XSS Cheat Sheet double encoder utility to double encode a XSS
    string

<u><http://ha.ckers.org/xss.html></u>

  - If the resultant injection is a successful XSS output, then your
    application is vulnerable

<!-- end list -->

  - This attack may also work against:

<!-- end list -->

1.  Filenames
2.  Non-obvious items like report types, and language selectors
3.  Theme names

### How to protect yourself

  - Assert the correct locale and character set for your application

<!-- end list -->

  - Use HTML entities, URL encoding, and so on to prevent Unicode
    characters being treated improperly by the many divergent browser,
    server, and application combinations

<!-- end list -->

  - Test your code and overall solution extensively

## HTTP Request Smuggling

[HTTP Request Smuggling](HTTP_Request_Smuggling "wikilink") (HRS) is an
issue detailed in depth by Klein, Linhart, Heled, and Orrin in a
whitepaper found in the references section. The basics of HTTP Request
Smuggling is that many larger solutions use many components to provide a
web application. The differences between the firewall, web application
firewall, load balancers, SSL accelerators, reverse proxies, and web
servers allow a specially crafted attack to bypass all the controls in
the front-end systems and directly attack the web server.

The types of attack they describe are:

  - Web cache poisoning

<!-- end list -->

  - Firewall/IDS/IPS evasion

<!-- end list -->

  - Forward and backward HRS techniques

<!-- end list -->

  - Request hijacking

<!-- end list -->

  - Request credential hijacking

Since the whitepaper, several examples of real life HRS have been
discovered.

### How to determine if you are vulnerable

  - Review the whitepaper

<!-- end list -->

  - Review your infrastructure for vulnerable components

### How to protect yourself

  - Minimize the total number of components that may interpret the
    inbound HTTP request

<!-- end list -->

  - Keep your infrastructure up to date with patches

## Further Reading

  - IDS Evasion using Unicode

<u><http://online.securityfocus.com/print/infocus/1232></u>

  - W3C Internationalization Home Page

<u><http://www.w3.org/International/></u>

  - HTTP Request Smuggling

<u><http://www.cgisecurity.com/lib/http-request-smuggling.pdf></u>

  - XSS Cheat Sheet

<u><http://ha.ckers.org/xss.html></u>

[Development Guide Table of
Contents](Guide_Table_of_Contents "wikilink")

[Category:OWASP_Guide_Project](Category:OWASP_Guide_Project "wikilink")
[Category:Canonicalization](Category:Canonicalization "wikilink")
[Category:Encoding](Category:Encoding "wikilink") [Category:Externally
Linked Page](Category:Externally_Linked_Page "wikilink")