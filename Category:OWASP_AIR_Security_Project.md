## Overview

OWASP's AIR Security Project is an open project for sharing a knowledge
base in order to raise awareness around the subject of AIR application
security.

<B>What is AIR?</B>
The Adobe AIR runtime allows developers to build cross-platform desktop
applications. AIR allows developers to create their applications through
ActionScript, HTML, JavaScript or a combination of those languages.
While developers can use web languages for the purposes of creating
code, AIR applications are standalone desktop applications with no
relationship to the end-user's web browser.

AIR requires that all applications be digitally signed so that end-users
can verify the author application. AIR supports digitally signing the
application with both self-signed certificates as well as those verified
by a trusted CA. The install experience for installing the application
is similar to the Microsoft experience for installing an executable. If
the application is signed by a trusted CA, then the end-user will
receive a dialog showing the author's information from the certificate.
If the application is self-signed, the user will receiving a warning and
no information from the certificate will be shown. AIR requires
administrative privileges on the OS to install the application. Once the
application is installed, the application will run with the privileges
of the user who starts the application. Applications are registered with
the OS so that the add/remove functionality of the OS can be used to
install or uninstall the application.

To install an application, AIR provides it's own download manager and
install dialogues in order to provide a consistent cross-platform
experience. The download and install of the application can be launched
from a SWF badge that is hosted on the website. The SWF merely calls an
API to tell the AIR runtime start the download process and provides the
URL of the application to be downloaded. The end-user will be provided
with an Open/Save/Cancel dialogue. The Open button will lead the user to
the certificate verification dialog and the following application
install choices such as install location. AIR also allows the developer
to choose to make their application available to be launched from the
browser.

By default, AIR applications can not be launched from the web browser
but it is possible. Typically, applications that wanted to be launched
from the web browser would register a scheme with the OS. However,
custom schemes have lead to several security issues. To solve this, AIR
instead allows a SWF hosted on the website to launch the application.
The SWF can call the AIR application and provide arguments within the
call through a formally defined API within ActionScript.

AIR contains two security sandboxes for separating privilege within the
application. The application sandbox is the fully privileged sandbox
that provides the APIs for desktop interaction. Certain restrictions
exist within this sandbox to drive developers towards secure programming
practices. There is also a non-application sandbox for loading untrusted
content from the web. Content loaded within the non-application sandbox
will execute with traditional web browser sandbox permissions.
Developers can choose to expose functionality from the application
sandbox to the non-application sandbox through the use of a sandbox
bridge. This must be done manually by the developer and the developer
explicitly chooses the variables or functions that are exposed.



## Goals

The OWASP AIR Security Project aims is to produce guidelines, references
and tools around AIR Application Security. Additional information on
Flash security can be found within the [OWASP Flash Security
Project](http://www.owasp.org/index.php/Category:OWASP_Flash_Security_Project)


\== Articles ==

**Overviews**

[Introduction to the AIR Security
Model](http://www.adobe.com/devnet/air/articles/introduction_to_air_security.html)
An Adobe blog introducing the AIR security model at a high level.

**Signing code**

[Digitally Signing Adobe AIR
Applications](http://www.adobe.com/devnet/air/articles/signing_air_applications.html)
An Adobe Developer Center article on how to sign and test AIR
applications.

[Code Signing in Adobe
AIR](http://www.ddj.com/web-development/210004209) An in depth, Dr.
Dobb's Journal article on code signing in Adobe AIR.

**Updating**

[Managing Adobe AIR updates with
ColdFusion 8](http://www.adobe.com/devnet/coldfusion/articles/managing_air_updates_with_coldfusion.html)
An Adobe Developer Center article on how to push out updates to AIR
applications.

[Building AIR applications that can be easily
updated](http://www.adobe.com/devnet/air/articles/tips_building_air_apps.html)
An Adobe Developer Center article by David Daraedt on leveraging AIR's
auto-update capabilities.

[Using the Adobe AIR update
framework](http://www.adobe.com/devnet/air/flex/quickstart/update_framework.html)
A Flex quick start guide to the AIR Update framework.

[Remote Plugins and Modules in
AIR](http://weblogs.macromedia.com/emalasky/archives/2008/04/remote_plugins.cfm)
An Adobe blog entry on how to load remote modules in AIR applications.

[Writing a Secure Plugin Architecture for AIR
Applications](http://blogs.adobe.com/air/2010/03/writing_a_secure_plugin_architecture_for_air_applications.html).
An Adobe blog on how to extend your application through plugins.

**Cryptography**

[Storing encrypted
data](http://help.adobe.com/en_US/AIR/1.5/devappsflex/WS5b3ccc516d4fbf351e63e3d118666ade46-7e31.html)
Adobe's developer documentation regarding secure storage options.

[EncryptedLocalStore
class](http://livedocs.adobe.com/flex/3/langref/index.html?flash/data/EncryptedLocalStore.html&flash/data/class-list.html)
The AIR documentation reference for the Encrypted Local Store class.

[Using encryption with SQL
databases](http://help.adobe.com/en_US/AIR/1.5/devappsflex/WS8AFC5E35-DC79-4082-9AD4-DE1A2B41DAAF.html)
Adobe's developer documentation on encrypting SQL databases.

[Using the EncryptionKeyGenerator class to obtain a secure encryption
key](http://help.adobe.com/en_US/AIR/1.5/devappsflex/WS44EC31A7-61B1-4e0a-8C61-D720AA95DE03.html)
Adobe's developer documentation on generating keys.

[Creating and validating XML
signatures](http://www.adobe.com/devnet/air/flex/quickstart/xml_signatures.html)
An Adobe Developer Center article on leveraging the
XMLSignatureValidator API in Adobe AIR.

[Considerations for using encryption with a
database](http://help.adobe.com/en_US/AIR/1.5/devappsflex/WS34990ABF-C893-47ec-B813-9C9D9587A398.html)
Adobe AIR documentation on SQL database encryption options.

**SQL Injection**

[Using parameters in
statements](http://help.adobe.com/en_US/AIR/1.5/devappsflex/WS5b3ccc516d4fbf351e63e3d118666ade46-7d42.html)
Adobe AIR documentation on using parametrized queries.

[SQLStatement.parameters
property](http://livedocs.adobe.com/flex/3/langref/index.html?flash/data/SQLStatement.html#parameters&flash/data/class-list.html)
Property reference from the Adobe AIR documentation.



## Presentations

\[1\] Maintaining Security With Adobe AIR
[ppt](http://weblogs.macromedia.com/emalasky/archives/MAX2008_MaintainSecurityWithAdobeAIR.pdf)
[video](http://tv.adobe.com/#vi+f15384v1025) The session on AIR security
presented at MAX 2008 by Ethan Malasky and Peleus Uhley.

\[2\] Designing Secure AIR Applications
[video](http://onair.adobe.com/blogs/videos/2008/06/23/ethan-malasky-developing-secure-air-applications/)
A video recording of Adobe's Ethan Malasky presenting on AIR Security.

\[3\] Adobe AIR Data Privacy and Security
[zip](http://probertson.com/resources/2009/06/09/air-data-privacy-security-slides-links.zip)
A May 20, 2009 presentation from the 360 |Flex conference in
Indianapolis, IN.



## Useful Frameworks

[Adobe AIR Update
Framework](http://labs.adobe.com/wiki/index.php/Adobe_AIR_Update_Framework)
A beta framework for including good update capabilities within your
application.



## References

\[1\] [AIR 1.5
Security](http://help.adobe.com/en_US/AIR/1.5/air_security/) The Adobe
AIR 1.5 security white paper.

\[2\] [AIR 1.0
Security](http://download.macromedia.com/pub/air/documentation/1/air_security.pdf)
The Adobe AIR 1.0 security white paper.

\[3\] [AIR Security with
Flex](http://livedocs.adobe.com/flex/3/html/help.html?content=security_1.html)
This section of the *Developing Adobe® AIR™ Applications with HTML and
Ajax* manual covers security topics such as best practices for
developers, AIR sandboxes and Flex security.

\[4\] [AIR Security with
HTML](http://help.adobe.com/en_US/AIR/1.5/devappshtml/WS5b3ccc516d4fbf351e63e3d118666ade46-7fa3.html)
This section of the *Developing Adobe® AIR™ Applications with HTML and
Ajax* manual covers security topics such as best practices for
developers, AIR sandboxes, and HTML security.

\[5\] [Adobe Security Bulletins and
Advisories](http://www.adobe.com/support/security/) This is where Adobe
posts all of their security advisories and bulletins.

\[6\] [AIR for IT
Administrators](http://www.adobe.com/products/air/it_administrators/)
This is the Adobe documentation geared towards IT administrators who
deploy AIR throughout their desktop environments.



## Useful Specifications

[AVM2
Specification](http://www.adobe.com/devnet/actionscript/articles/avm2overview.pdf)
Describes the Flash ActionScript Virtual Machine used for ActionScript
3.0 code.

[AMF3
Specification](http://opensource.adobe.com/wiki/download/attachments/1114283/amf3_spec_05_05_08.pdf)
The specification for version 3 of AMF used by Flash Player.

[AMF0
Specification](http://opensource.adobe.com/wiki/download/attachments/1114283/amf0_spec_121207.pdf?version=1)
The specification for the first generation of AMF (AMF 0) used by Flash
Player.

[RTMP Specification](http://www.adobe.com/devnet/rtmp/) This is the
specification for the Real Time Messaging Protocol used by SWF content

[FLV/F4V Specification](http://www.adobe.com/devnet/flv/) The FLV/F4V
open specification documents the file formats for storing media content
used to deliver streaming audio and video for playback in Adobe® Flash®
Player and Adobe AIR™ software.

[Cross-domain policy file
specification](http://www.adobe.com/devnet/articles/crossdomain_policy_file_spec.html)
This document serves as a reference for the structure and use of
cross-domain policy files.



## Related Projects

[OWASP Flash Security
Project](http://www.owasp.org/index.php/Category:OWASP_Flash_Security_Project)

[Air Security Project](Category:OWASP_Project "wikilink")