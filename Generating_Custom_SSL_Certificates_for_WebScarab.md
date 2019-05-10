When using WebScarab to proxy SSL conversations, you may want to avoid
the somewhat annoying warnings for an unrecognized certificate. You can
generate a custom SSL certificate to remove these warning messages and
it's rather straight forward if you have a sufficiently recent version
of WebScarab (initial support was added on 2008/08/05). Read on to see
how.

## Background

Below is an illustration of what happens when WebScarab is used as a
intercepting proxy for SSL connections.

```
 --------           -----------           ---------
| server
|<--[1]-->
| WebScarab
|<--[2]-->
| browser
|
 --------           -----------           ---------
```

For \[1\], you are using the "real" SSL certificate from the website you
are browsing to. That SSL certificate is signed by a recognized
certificate authority (CA). The thing that makes those CA's special is
that browsers know about them and trust them. For example in Firefox:

1.  Open Edit -\> Preferences -\> Advanced -\> Encryption
2.  View Certificates button
3.  Authorities tab

to see a list of built-in trusted CA's. The only thing that needs to
trust this certificate is WebScarab, which trusts all certificates,
whether valid or not.

For \[2\], you are using the the self-signed server.p12 certificate
which comes with WebScarab. The difference between \[1\] and \[2\] is
that the CA which signed that certs is NOT built into browsers so they
do not trust them by default. Additionally, the domain name of this
certificate will not match the domain your browser is accessing. The
default is the webscarab CA and a host name of webscarab.

## Generating a Certificate

Since your browser doesn't trust the CA which signed server.p12 in \[2\]
above, you've got two choices:

1.  Instruct the browser to trust the certificate. This will work for
    the CA part but not for the host name. You will still be prompted by
    the browser so this doesn't really help much, and is not advised
    anyway, due to the fact that lots of people have this CA cert, and
    could use it to create SSL certificate for arbitrary sites. I know
    that you can have Firefox trust the CA used in \[2\] permanently -
    though it's a bunch of clicks in Firefox 3 - about 6 or 7 clicks and
    you still have the host name mis-match issue.

<!-- end list -->

1.  Use a .p12 file & CA certificate. You'll have to have WebScarab use
    the new .p12 file and install the CA certificate into your browser.

There is a script to do this in the WebScarab Git repository. You can
get it
[here](http://dawes.za.net/gitweb.cgi?p=webscarab.git;a=blob;f=doc/cert.sh;h=b0fdbdf7991a00573d490e9353f9c601e7a8242e;hb=HEAD).

The script will create a server-specific key and certificate for the
site provided as a parameter on the command line. If this is the first
time the script is being run, it will also create a CA cert which you
can then import into your browser(s).

If you called that script like:

    $ ./cert.sh www.example.com

It will generate a bunch of output and create a www.example.com.p12 file
for WebScarab and a ca_cert.pem file (this is the CA used to sign
www.example.com.p12). The script will run fine on Linux (I just tried
it) and possibly OS X but will only work on Windows under Cygwin.

Take the www.example.com.p12 (assuming you ran the script like above)
and let WebScarab know about it. To do this you will need to place it in
${WEBSCARAB_HOME}/certs/. WebScarab checks in that directory whenever a
request is made for an SSL site, for a file <sitename>.p12, and will use
it in preference to the default server cert if one is found.

Take the ca_cert.pem file and configure your browser to trust that CA.
For Firefox:

1.  Open Edit -\> Preferences -\> Advanced -\> Encryption
2.  View Certificates button
3.  Authorities
4.  Click the Import button and navigate to the ca_cert.pem file

Make sure you at least check the box "Trust this CA to identify web
sites." option when you are importing - it will bring up a window with
that information.

For IE, I don't know off the top of my head. Try this
[link](http://www.library.jcu.edu.au/LibraryGuides/certificate.shtml)
except for instead of downloading it you can right-click on the
ca_cert.pem file and select "Install Certificate"

FYI: Firefox and IE will both need to be configured if both are used as
they keep their lists of trusted CAs in different places.

**Added Bonus** If you keep the working directory for cert.sh
(recommended\!), you can create new custom SSL certificates and not need
to import a new CA cert. If you know all the domains you'll be testing,
you can run cert.sh multiple times and just restart WebScarab once to
get them all recognized.

For the curious, this is the directory structure the cert.sh script
creates:

    ./
    |-- cert.sh
    |-- sslcerts
    |
    |-- ca_cert.pem
    |
    |-- certindex.txt
    |
    |-- certindex.txt.attr
    |
    |-- certindex.txt.old
    |
    |-- certs
    |
    |   `-- 100001.pem
    |
    |-- openssl.cnf
    |
    |-- private
    |
    |
    |-- ca_key.pem
    |
    |   `-- www.example.com-key.pem
    |
    |-- serial
    |
    |-- serial.old
    |
    |-- www.example.com-cert.pem
    |   `-- www.example.com-req.pem
    `-- www.example.com.p12

    3 directories, 14 files

## Notes

1.  I was not precise in terms and used SSL and HTTPS loosely in the
    above. This process would also applies to TLS - I just didn't want
    to type SSL/TLS over and over.
2.  Matt Tesauro was the author of this document. If you have
    corrections, feel free to make them yourself (its a Wiki after all)
    or contact Matt at mtesauro (at) gmail.com

[Category:OWASP WebScarab
Project](Category:OWASP_WebScarab_Project "wikilink")