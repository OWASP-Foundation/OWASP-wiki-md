**WebScarab** can use SSL Certificates in two ways.

First, when you use the proxy to intercept a request to an SSL-protected
site, WebScarab makes use of its own internal SSL certificate to
negotiate an SSL connection with your browser. Obviously, the
certificate that WebScarab presents does not match what your browser is
expecting, and so your browser warns you that your communication may be
intercepted. Since this is actually our objective, we can simply accept
the warning, and choose to continue.

Secondly, the SSL-protected site you are connecting to may require a
client-side SSL certificate, in order to identify you. This is known as
mutual authentication, and is normally handled by your browser.

## Configuring certificates

### Server certificates

If, for some reason, you want to change the certificate that WebScarab
uses to negotiate connections, you will have to rebuild the WebScarab
JAR file, and replace the existing server.p12 file with your own
PKCS\#12 formatted file. The password protecting the PKCS\#12 file
should be "password", as this is what WebScarab expects.

Here is an example of using the OpenSSL tool to create your own
self-signed server certificate:

` openssl genrsa 1024 > server.key`
` `
` openssl req -new -x509 -nodes -sha1 -days 3650 -key server.key > server.crt`
` `
` openssl pkcs12 -export -out server.p12 -in server.crt -inkey server.key -name "WebScarab"`

The information that you put into the various fields when prompted is
unimportant for WebScarab. If the default WebScarab key is inadequate
for your purposes, you will most likely have a better idea of what
information is important to you (or your client) than anything that I
can tell you.

### Client certificates

Since mutual authentication via SSL does not transit across the proxy
(since we now have two connections\!), we need to arrange for WebScarab
to present your client certificate to the server. This can be somewhat
tricky, depending on what kind of certificate you have.

#### PKCS\#12

WebScarab allows you to access client side certificates stored in
PKCS\#12-formatted files, or (if you are using Java 5 or later) by
accessing a PKCS\#11-compliant device, for example, a smart-card, or
Hardware Security Module (HSM). This functionality is accessed via the
Tools-\>Certificates menu option.

![Image:WebScarab certificate manager
empty.png](WebScarab_certificate_manager_empty.png
"Image:WebScarab certificate manager empty.png")

The simplest way to provide a client certificate is via a PKCS\#12 file.

![Image:WebScarab certificate manager adding
pkcs12.png](WebScarab_certificate_manager_adding_pkcs12.png
"Image:WebScarab certificate manager adding pkcs12.png")

![Image:WebScarab certificate manager
pkcs12.png](WebScarab_certificate_manager_pkcs12.png
"Image:WebScarab certificate manager pkcs12.png")

At this stage, WebScarab will not actually use the certificate, it is
just aware of its existence. To activate the certificate, select the Key
Store and the certificate that you wish to use, and hit "Activate
Selected Alias". It will ask you for a password to access the individual
certificate inside the key store. For a PKCS\#12 file, this is almost
always the same password that you used when exporting it. However it CAN
be different, which is why you are asked twice.

WebScarab can be configured with multiple Key Stores, making it easy to
test with different SSL certificates.

#### PKCS\#11

WebScarab also supports using PKCS\#11-compliant devices, if your Java
Runtime Environment does. Sun's Java 5 (a.k.a Java 1.5) and later
distributions have native support for PKCS\#11.

Use the PKCS\#11 tab when adding a Key Store to specify the shared
library path, and the PIN/password to access the smart card. Then select
the smart card Key Store, and the specific certificate, and activate
that Alias.

## Getting certificates into PKCS\#12 files

Since WebScarab requires the certificate to be in a PKCS\#12 file
(unless it is in a hardware device), you may need to perform some
conversion to achieve this.

If your certificate is in PEM or DER format, you can use the OpenSSL
command line tool to perform the conversion:

`openssl pkcs12 -export -out mycert.p12 -in mycert.crt -inkey mycert.key -name "My Certificate"`

If, for example, the certificate is located in the IE certificate store,
you can try to export the certificate to a "PFX" file, which is
essentially a PKCS\#12-formatted file. This may not be possible, since
IE has the ability to specify that you cannot export the private key of
a particular certificate. If this is set, you cannot create a working
PKCS\#12 key file. If you have the opportunity to set this property
while enrolling to your application, make sure to allow yourself to
export the key later. You can choose an arbitrary password

[Category:How To](Category:How_To "wikilink") [Category:OWASP WebScarab
Project](Category:OWASP_WebScarab_Project "wikilink")