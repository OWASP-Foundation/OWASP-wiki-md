### Current Status

  - 16th January, 2008

As of 16th January, The OpenPGP Secure Session Manager is fully
functional. A new release of mod_openpgp and Enigform will happen
before the end of January. OWASP made this possible. Thanks to Dinis
Cruz and Paulo Coimbra for their support and interest in this project.
And thanks to all the Internet community that has sent me feedback and
kudos\! :) -- Buanzo

## Older Status Reports

  - 7th November, 2007

As of 7th November, 2007, mod_openpgp, the Server-side Enigform
component for Apache, supports OpenPGP-Encrypted HTTP Request
Decryption. This means an HTTP client can send an encrypted HTTP
request, using the Server's public key, and it will be decrypted and
correctly served by the server.

This is a HUGE feature bump, of roughly 1200 lines of C code.

It's much more of what I expected to implement for the OWASP SPOC
duration, so I'll be applying for the 2nd half of my funding now.

Also, I've implemented most of the Secure Session Initiation Protocol,
but problems with some Apache DB APIs are slowing this much more than I
expected. I hope to work out all the issues, or I'll have to release a
simplified version. I just hope the Decryption support is enough to
apply for the 2nd half of funding.

  - 9th July, 2007

As of 9th July, 2007, Enigform has been enhanced with remote site
OpenPGP discovery, Public Key Import. Kyle Huff has joined the
development team, and the Session Protocol has been proposed. Regarding
Encryption, mod_openpgp supports encrypted http requests, but Enigform
support for this is in research stage.Microsoft support will be last
stage, once Enigform 1.0 and mod_openpgp 1.0 are released.

## Project Links

  - [Enigform Development Site](http://enigform.mozdev.org)
  - [Addons.Mozilla.Org - Stable Releases Installation
    Page](https://addons.mozilla.org/en-US/firefox/addon/4531)
  - [Enigform Freshmeat Page](http://freshmeat.net/projects/enigform)
  - [Official Enigform
    Forum](http://foros.buanzo.com.ar/viewforum.php?f=35)

[Back to Project
page](SpoC_007_-_Enigform:_Firefox_Addon_for_OpenPGP_signing_of_HTTP_requests "wikilink")