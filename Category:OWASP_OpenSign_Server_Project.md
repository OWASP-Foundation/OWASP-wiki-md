<table>
<thead>
<tr class="header">
<th><p>width="700" align="center"</p></th>
<th><p><br />
</p></th>
<th><p>width="500" align="center"</p></th>
<th><p><br />
</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>align="right"</p></td>
<td><figure>
<img src="OWASP_Inactive_Banner.jpg" title="OWASP_Inactive_Banner.jpg" alt="OWASP_Inactive_Banner.jpg" width="800" /><figcaption>OWASP_Inactive_Banner.jpg</figcaption>
</figure></td>
<td><p>align="right"</p></td>
<td></td>
</tr>
</tbody>
</table>

# User Documentation

This section describes the installation and usage of the server and
client binaries, which can be downloaded above. As all applications are
written in pure Java the following instructions are not bound to a
specific platform.

## Requirements

  - Java runtime 1.6
  - Optional: MySql DB

## Installation

On default nothing besides the unpacking of the binary-packages has to
be done for installing server and client application. If one wants to
enable specific settings it is recommended to follow the instructions of
the readme.txt files, which are located in the root of each directory
after unpacking. Note that the server will run in memory on default,
which is only good for testing as the data is lost by shutting down the
server. However, this behaviour can easily be changed by the use of a
MySql DB (please refer to: readme.txt).

## Server Usage

Open a console and brows into folder OpenSignServer-1.0. Following
command will start the server application:

`  java -jar jar\OpenSignServer-1.0.jar`

The web-based user interface is accessible at: <http://localhost:8080/>

![Open_sign_server_home.jpg](Open_sign_server_home.jpg
"Open_sign_server_home.jpg")

Following links are accessible:

**Home:** Initial page

**Certificate Authoriy:** This link allows, on the one hand,
unauthenticated users to brows the X.509 hierarchy, starting from the
root node down to the leaves, and on the other hand authenticated users
to issue certification requests. Once issued certificates are easily
accessible and may be downloaded in PEM or binary format.

**Registration:** Form for registration of new users with the OpenSign
server. New users have to enter some personal details and have to select
an issuer (super-node), within the X.509 hierarchy, which needs to
approve the registration request before the user will be able to use
this service.

**MySettings:** This link is only accessible if a user is authenticated.
Every user may maintain his profile her. Furthermore, if a user is
dedicated as issuer, a list of all sub-nodes is shown. As the issuer is
responsible for maintaining the sub-nodes, it is his choice to decide
whether to approve a particular user to use the certification service or
not. Once a user is approved, the issuer may also decide if he can act
as an issuer himself or not.

**Login:** User Login

## Client Usage

Open a console and brows into folder OSSJClient-1.0. To start the client
enter following command:

`  java -jar OSSJClient-[version].jar [command]`

Executing the client application without the command-parameter, will
print a list of all possible commands to the console. All commands take
mandatory and optional parameter, which are also depicted by calling a
command without any parameter.

The possible commands are:

**verifycert**

This command takes a certificate file and verifies it. Additionally, the
application downloads and verifies the certificate chain. A detailed
transcript is printed to the console.

**getcert**

This command retrieves a certificate from a OpenSign resource (e.g.
root/owasp/user1) and either prints it to the console or stores it in a
file. Furthermore, the format of the certificate may be chosen (PEM or
binary).

**csr**

This command processes a certificate sign request. The request is sent
to the server, which takes the login credentials and checks if the user
is approved to have a OpenSign certificate and if so a certificate is
generated and sent to the user in return.

## Steps for setting up the X.509 Hierarchy

**1. Update the root-account**

By starting the server the first time the root account is created and a
private key plus corresponding certificate are generated. This account
serves as admin-account for the server and as root-node of the X.509
Hierarchy. It is necessary to reset the password, which can by done by
loging in using the username: "root" and the password "123" and by
navigating to "MySettings".

**2. Creating an own issuer-account**

As it is recommended not to use the root-account for all the issuing
procedures it is necessary to set up an account which is a sub-node from
the root-account. This account is further on used to maintain a set of
end-users. In the first step the person, responsible for the
issuer-account, has to register. In the second step, the owner of the
root-account will need to log in and approve this request and grant this
user issuer privileges. Once these settings are stored, the OpenSign
server will generate a certificate for the issuer, which is publicly
available on the issuers profile.

Registering the issuer-account:
![Image:Open_sign_server_reg.jpg](Open_sign_server_reg.jpg
"Image:Open_sign_server_reg.jpg")

Enabling the issuer-account by the root user:
![Image:Open_sign_server_approve_issuer.jpg](Open_sign_server_approve_issuer.jpg
"Image:Open_sign_server_approve_issuer.jpg")

3\. End user registration

Users may register and select the previously generated issuer-account
(“owasp”) as their desired issuer. However, before they can use their
account the issuer has to approve them first.

Registration of an end-user:
![Image:Open_sign_server_reg_user.jpg](Open_sign_server_reg_user.jpg
"Image:Open_sign_server_reg_user.jpg")

4\. Certificate issuance

It is possible to obtain a certificate by issuing a certificate sign
request by use of the web-interface or by use of the client application.
The form online can be found at: localhost:8080/csr. The processing of a
certificate sign request with the client application is described above
(command: csr).

## Code Signing and Verification

This section describes the steps required for code-signing and
verification supported by the OpenSign infrastructure.

**Signing**

1\. Local generation of the private code-signing key. The key should be
stored in a password-protected keystore.

2\. Generation of a certificate sign request (CSR)

3\. Processing the CSR by making use of the web-interface or the client
application. Either way a certificate is returned on success.
Furthermore, a copy of the certificate is stored within the
server-infrastructure.

4.Signing the code module by making use of the previously generated key.

**Verification**

1\. Downloading the certificate by browsing the OpenSign X.509 hierarchy
online or by use of the client application, which is the recommended
option.

2\. Importing the certificate as a trusted certificate in the local
key-store.

3\. Verifying the signed code module by use of the public key embedded
in the downloaded certificate.

# Releases

## OpenSign Server

### Version 1.0 (26st of October 08)

  - This version is working with the Java client version 1.0
  - An "About" button has been added

### Version 0.5 (14th of October 08)

  - Users must now be enabled to use the certification service by the
    the issuer above in order to build up chains of trust
  - The settins page for issuers got extended for maintaining the
    subordinate entities
  - Several server pages got enhanced in terms of functionality and
    design

### Version 0.4 (28th of August 08)

  - Certificate chains are now set up properly. This includes the right
    values in the certificate as well as appropriate key-handling of the
    key store. Dummy code got removed broadly.
  - This version supports the use of OSSJClient version 0.9 for commands
    "getcert", "verifycert" and "csr"

### Version 0.3 (21st of July 08)

  - Easy extendable persistence layer, which is set up using Hibernate –
    Annotations.
  - Possibility to run server in memory, whereas data is lost when the
    server process is terminated, or to run the server on top of a MYSQL
    database.
  - Logging mechanism got enhanced which involves means to pipe the log
    information from OpenSign server as well as from Jetty and Hibernate
    to a log file.
  - Same functionality as version 0.2 from a user point of view.

### Version 0.2 (14th of July 08)

  - Demo-wise set up of an X.509 hierarchy intending to provide code
    siging certificates. This involves one root issuer, an unlimited
    number of sub-issuers and end-users.
  - End-users may issue a certificate sign request and obtain the
    certificate in return.
  - Demo accounts of to end-users ("user1", "user2") and two issuers
    ("root", "user3") each with password "123".
  - Possibility for registering new end-users and issuers.
  - Session handling - login, logout of users
  - Storage of issuer key-pair's and all certificates in server side key
    store.
  - Public access of all certificates in the system, with support of
    binary and PEM format. Eg.: Certificate from root issuer may be
    retrieved
      -
        \- in binary format (default):
        <http://localhost:8080/root?property=cert>
        \- or PEM formatted:
        <http://localhost:8080/root?property=cert&responseFormat=PEM>
  - User/resource profile, which is accessible at the resource path
    without further parameters, eg.: <http://localhost:8080/root/user1>

### Version 0.1 (1st of July 08)

  - Access of root certificate via HTTP-GET <http://localhost:8080/ca>
  - Certificate issuing by sending a Certificate Signing Request
    (PEM-formatted PKCS\#10 structure) via HTTP-POST to
    <http://localhost:8080/ca/csr>

## OpenSign Client

### Version 1.0 (26st of October 08)

  - This version has been modified to work with the server version 1.0

### Version 0.9 (28th of August 08)

  - Commands supported: "getcert", "verifycert" and "csr"

-----

# Roadmap

## OpenSign Server

**Goal**

The goal of the Opensign Server (OSS) is to serve as trusted third party
in order to prove the integrity and authenticity of binaries. To meet
this goal following roadmap will be implemented:

**Version 0.1**

This version is a proof of concept implementation, which shows that
processing a Certificate Signing Request (CSR) and issuing a X.509
certificate is working in an efficient way. Furthermore the generation
and distributing of the root certificate is also supported.

**Version 0.2**

The server is enhanced by the possibility to support certificate issuing
for multiple users. In this case users must be authenticated before
generating a certificate.

**Version 0.3**

User management is done through the persistence layer, where Hibernate
is the technology of choice. It is now possible to dynamically add users
through the web-interface.

**Version 0.4**

The role of the Review is introduced. Users must be associated with a
Reviewer before being able to generate a certificate.

**Version 0.5**

The web-interface is enriched with dynamically generated sites which
allows the maintenance of the system depending of the user role.

**Version 1.0**

Well tested and documented PKI for code signing which is running online
at: www.???.com. **This is the goal for Summer of Code 2008\!**

**Version 2.0**

The second version of the OSS allows the server side code signing. Code
modules are uploaded, virus scanned and signed by a corresponding key.
No client side key management is required. Furthermore, this service has
a downloading area where anybody can download the signed modules.

## OpenSign Client

### Java Client

**Version 1.0**

Command line application, extending Java keytools functionality to make
use of the OpenSign infrastructure to sign and verify Jar archives.

# Future development

[Category:OWASP Project](Category:OWASP_Project "wikilink")
[Category:OWASP Tool](Category:OWASP_Tool "wikilink") [Category:OWASP
Download](Category:OWASP_Download "wikilink") [Category:OWASP Alpha
Quality Tool](Category:OWASP_Alpha_Quality_Tool "wikilink")