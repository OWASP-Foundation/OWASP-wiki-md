`   <td colspan=2 ``>`

Attackers will often attempt to exploit unpatched flaws or access
default accounts, unused pages, unprotected files and directories, etc
to gain unauthorized access or knowledge of the system.

</td>

`   <td colspan=2  ``>`

`Security misconfiguration can happen at any level of an application stack, including the network services, platform, web server, application server, database, frameworks, custom code, and pre-installed virtual machines, containers, or storage. Automated scanners are useful for detecting misconfigurations, use of default accounts or configurations, unnecessary services, legacy options, etc. `

</td>

`   <td colspan=2  ``>`

`Such flaws frequently give attackers unauthorized access to some system data or functionality. Occasionally, such flaws result in a complete system compromise.`
`The business impact depends on the protection needs of the application and data. `

</td>

The application might be vulnerable if the application is:

  - Missing appropriate security hardening across any part of the
    application stack, or improperly configured permissions on cloud
    services.
  - Unnecessary features are enabled or installed (e.g. unnecessary
    ports, services, pages, accounts, or privileges).
  - Default accounts and their passwords still enabled and unchanged.
  - Error handling reveals stack traces or other overly informative
    error messages to users.
  - For upgraded systems, latest security features are disabled or not
    configured securely.
  - The security settings in the application servers, application
    frameworks (e.g. Struts, Spring, ASP.NET), libraries, databases,
    etc. not set to secure values.
  - The server does not send security headers or directives or they are
    not set to secure values.
  - The software is out of date or vulnerable (see
    <b><u>[text=documentRootTop10New]({{Top_10:LanguageFile "wikilink")</u></b>).

Without a concerted, repeatable application security configuration
process, systems are at a higher risk.

Secure installation processes should be implemented, including:

  - A repeatable hardening process that makes it fast and easy to deploy
    another environment that is properly locked down. Development, QA,
    and production environments should all be configured identically,
    with different credentials used in each environment. This process
    should be automated to minimize the effort required to setup a new
    secure environment.
  - A minimal platform without any unnecessary features, components,
    documentation, and samples. Remove or do not install unused features
    and frameworks.
  - A task to review and update the configurations appropriate to all
    security notes, updates and patches as part of the patch management
    process (see
    <b><u>[text=documentRootTop10New]({{Top_10:LanguageFile "wikilink")</u></b>).
    In particular, review cloud storage permissions (e.g. S3 bucket
    permissions).
  - A segmented application architecture that provides effective, secure
    separation between components or tenants, with segmentation,
    containerization, or cloud security groups (ACLs).
  - Sending security directives to clients, e.g. <u>[Security
    Headers](OWASP_Secure_Headers_Project "wikilink")</u>.
  - An automated process to verify the effectiveness of the
    configurations and settings in all environments.

<b>Scenario \#1</b>: The application server comes with sample
applications that are not removed from the production server. These
sample applications have known security flaws attackers use to
compromise the server. If one of these applications is the admin
console, and default accounts weren't changed the attacker logs in with
default passwords and takes over.

<b>Scenario \#2</b>: Directory listing is not disabled on the server. An
attacker discovers they can simply list directories. The attacker finds
and downloads the compiled Java classes, which they decompile and
reverse engineer to view the code. The attacker then finds a serious
access control flaw in the application.

<b>Scenario \#3</b>: The application server's configuration allows
detailed error messages, e.g. stack traces, to be returned to users.
This potentially exposes sensitive information or underlying flaws such
as component versions that are known to be vulnerable.

<b>Scenario \#4</b>: A cloud service provider has default sharing
permissions open to the Internet by other CSP users. This allows
sensitive data stored within cloud storage to be accessed.

  - <u>[OWASP Testing Guide: Configuration
    Management](Testing_for_configuration_management "wikilink")</u>
  - <u>[OWASP Testing Guide: Testing for Error
    Codes](Testing_for_Error_Code_\(OWASP-IG-006\) "wikilink")</u>
  - <u>[OWASP Security Headers
    Project](OWASP_Secure_Headers_Project "wikilink")</u>

For additional requirements in this area, see the Application Security
Verification Standard <u>[V19
Configuration](ASVS_V19_Configuration "wikilink")</u>.

  - <u>[NIST Guide to General Server
    Hardening](https://csrc.nist.gov/publications/detail/sp/800-123/final)</u>
  - <u>[CWE-2: Environmental Security
    Flaws](https://cwe.mitre.org/data/definitions/2.html)</u>
  - <u>[CWE-16:
    Configuration](https://cwe.mitre.org/data/definitions/16.html)</u>
  - <u>[CWE-388: Error
    Handling](https://cwe.mitre.org/data/definitions/388.html)</u>
  - <u>[CIS Security Configuration
    Guides/Benchmarks](https://www.cisecurity.org/cis-benchmarks/)</u>
  - <u>[Amazon S3 Bucket Discovery and
    Enumeration](https://blog.websecurify.com/2017/10/aws-s3-bucket-discovery.html)</u>