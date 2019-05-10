`    <td ``>When designing a mobile application, commonly data is exchanged in a client-server fashion. When this data is exchanged it traverses both the carrier network and the internet. For sensitive data, if the application is coded poorly, threat agents can use techniques to view this sensitive data while it's travelling across the wire. The following threat agents exist:`

  - Users local to your network (compromised or monitored wifi)
  - Carrier or network devices (routers, cell towers, proxys, etc)
  - Malware pre-exisiting on your phone

</td>

`    <td ``> The exploitabilty factor of monitoring a network for insecure communications ranges. Monitoring traffic over a carriers network is harder than that of monitoring a local coffee shops traffic. In general targeted attacks are easier to perform.  `

</td>

`    <td colspan=2  ``> Unfortunately, mobile applications frequently do not protect network traffic. They may use SSL/TLS during authentication, but not elsewhere, exposing data and session IDs to interception. In addition, the existence of transport security does not mean it is implemented to it's full potential.`

Detecting basic flaws is easy. Just observe the phone's network traffic.
More subtle flaws require inspecting the design of the application and
the applications configuration.

</td>

`    <td ``>Such flaws expose individual users’ data and can lead to account theft. If an admin account was compromised, the entire site could be exposed. Poor SSL setup can also facilitate phishing and MITM attacks.`

</td>

`    <td ``>Consider the business value of the data exposed on the communications channel in terms of its confidentiality and integrity needs, and the need to authenticate both participants.`

</td>

The best way to find out if an application has sufficient transport
layer protection is to look at the application traffic through a proxy.
Find the answers to the following questions:

1.  Are all connections, not just ones to servers you own, properly
    encrypted?
2.  Are the SSL certificates in date?
3.  Are the SSL certificates self signed?
4.  Does the SSL use high enough cipher strengths?
5.  Will your application accept user accepted certificates as
    authorities?

**General Best Practices:**

  - Assume that the network layer is not secure and may potentially be
    hostile and eavesdropping.
  - Enforce the use of SSL/TLS for all transport channels in which
    sensitive information, session tokens, or other sensitive data is
    going to be communicated to a backend API or web service.
  - Remember to account for outside entities like 3rd party analytics
    companies, social networks, etc, and use their SSL versions even
    when an application runs a routine via the browser/webkit. Mixed SSL
    sessions should be avoided and may expose the user’s session ID.
  - Use strong, industry standard encryption algorithms and appropriate
    key lengths.
  - Use certificates signed by a trusted CA provider.
  - Never allow self-signed certificates, and consider certificate
    pinning for security conscious applications.
  - Do not disable or ignore SSL chain verification.
  - Only establish a secure connection after verifying the identity of
    the endpoint server with trusted certificates in the key chain.
  - Alert users through the UI if an invalid certificate is detected.
  - Do not send sensitive data over alternate channels, such as SMS,
    MMS, or notifications.

**iOS Specific Best Practices**

Default classes in iOS handle SSL cipher strength and negotiation very
well as of recent releases. The trouble comes when code is introduced to
bypass these defaults to accommodate development hurdles. In addition to
the above general practices:

  - Ensure that certificates are valid and fail closed.
  - When using CFNetwork, consider using the Secure Transport API to
    designate trusted client certificates. In almost all situations,
    NSStreamSocketSecurityLevelSSLv3 or NSStreamSocketSecurityLevelTLSv1
    should be used for higher standard cipher strength.
  - After development ensure all NSURL calls (or wrappers of NSURL) do
    not allow self signed or invalid certificates such as the NSURL
    class method setAllowsAnyHTTPSCertificate.
  - Consider using certificate pinning by exporting your certificate,
    including it in your app bundle, and anchoring it for your trust
    object. Using the NSURL method
    connection:willSendRequestForAuthenticationChallenge: will now
    accept your cert.

**Android Specific Best Practices**

  - Remove all code after the development cycle that may allow the
    application to accept all certificates such as
    org.apache.http.conn.ssl.AllowAllHostnameVerifier or
    SSLSocketFactory.ALLOW_ALL_HOSTNAME_VERIFIER. This is equivalent
    to trusting all certificates.

Example Scenarios

  - [Fortify On Demand Blog - Exploring The OWASP Mobile Top 10: M3
    Insufficient Transport Layer
    Protection](http://h30499.www3.hp.com/t5/Fortify-Application-Security/Exploring-The-OWASP-Mobile-Top-10-M3-Insufficient-Transport/ba-p/5966473)
  - [OWASP](https://www.owasp.org/index.php/IOS_Developer_Cheat_Sheet)[IOS
    Developer Cheat
    Sheet](https://www.owasp.org/index.php/IOS_Developer_Cheat_Sheet)
  - [blog.securemacprogramming.com - SSL Pinning for Cocoa
    Touch](http://blog.securemacprogramming.com/2011/12/on-ssl-pinning-for-cocoa-touch/)
  - [Why Eve and Mallory Love Android: An Analysis of Android SSL
    (In)Security](http://www2.dcsec.uni-hannover.de/files/android/p50-fahl.pdf)
  - [Fortify VulnCat - A Taxonimy of Software Security
    Errors](http://www.hpenterprisesecurity.com/vulncat/en/vulncat/index.html)