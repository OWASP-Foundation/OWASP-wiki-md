# ASP.NET Configurations

Sensitive data passes across networks. This data might include
passwords, credit card numbers, social security numbers, you name it. To
protect against disclosure of this information from unwelcome users, it
is essential to protect the data in transit from unwanted alteration.

Since web requests through physical tiers of an application crosses
different communication channels, it must be considered how the
application must be secure for each of these channels. Most of the
security configurations in ASP.NET occurs on different files found in
the application such as the web.config file or in the IIS server such as
the policy files. The following information highlights the most
important aspects to secure communications in ASP.NET applications

## IIS 7 Configurations

In IIS 7 there is a new configuration system which affects the hierarchy
level and how one file can inherit from another. The following figure
resumes how this work and the location of each file (Aguilar, 2006)

![<File:ConfigNETdiagram.png>](ConfigNETdiagram.png
"File:ConfigNETdiagram.png")

### Filtering Requests and URL Rewriting

Request Filtering was introduced in IIS7 and it has replaced the
functionality UrlScan add-on for IIS 6.0. This built-in security feature
allows to filter undesired URL request but it is also possible to
configure different kinds of filtering. To begin with, it is important
to understand how the IIS pipeline works when a request is done. The
following diagram shows the order in these modules

![<File:FilteringUrl.gif>](FilteringUrl.gif "File:FilteringUrl.gif")

(Yakushev, 2008)

Request filtering can be setup through the IIS interface or on the
web.config file. Example:

<configuration>

`  <system.webServer>`
`     `<security>
`        `<requestFiltering>
`           `<denyUrlSequences>
`              `<add sequence=".." />
`              `<add sequence=":" />
`           `</denyUrlSequences>
`           `<fileExtensions allowUnlisted="false" />
`           `<requestLimits maxUrl="2048" maxQueryString="1024" />
`           `<verbs allowUnlisted="false" />
`        `</requestFiltering>
`     `</security>
`  </system.webServer>`

</configuration>

(Yakushev, 2008) This can also be done through the application code ,
for example:

`using System;`
`using System.Text;`
`using Microsoft.Web.Administration;`
`internal static class Sample`
`{`
`   private static void Main()`
`   {`
`      using (ServerManager serverManager = new ServerManager())`
`      {`
`         Configuration config = serverManager.GetWebConfiguration("Default Web Site");`
`         ConfigurationSection requestFilteringSection = config.GetSection("system.webServer/security  `
`         /requestFiltering");`
`        ConfigurationElementCollection denyUrlSequencesCollection =   `
`        requestFilteringSection.GetCollection("denyUrlSequences");`
`        ConfigurationElement addElement = denyUrlSequencesCollection.CreateElement("add");`
`        addElement["sequence"] = @"..";`
`        denyUrlSequencesCollection.Add(addElement);`
`        ConfigurationElement addElement1 = denyUrlSequencesCollection.CreateElement("add");`
`        addElement1["sequence"] = @":";`
`        denyUrlSequencesCollection.Add(addElement1);`
`        ConfigurationElement addElement2 = denyUrlSequencesCollection.CreateElement("add");`
`        addElement2["sequence"] = @"\";`
`        denyUrlSequencesCollection.Add(addElement2);`
`        serverManager.CommitChanges();`
`      }`
`   }`
`}`

(Yakushev, 2008)

### Filtering Double –Encoded Requests

This attack technique consists of encoding user request parameters twice
in hexadecimal format in order to bypass security controls or cause
unexpected behavior from the application. It's possible because the
webserver accepts and processes client requests in many encoded forms.

By using double encoding it’s possible to bypass security filters that
only decode user input once. The second decoding process is executed by
the backend platform or modules that properly handle encoded data, but
don't have the corresponding security checks in place.

Attackers can inject double encoding in pathnames or query strings to
bypass the authentication schema and security filters in use by the web
application.

There are some common characters sets that are used in Web applications
attacks. For example, Path Traversal attacks use “../” (dot-dot-slash) ,
while XSS attacks use “\<” and “\>” characters. These characters give a
hexadecimal representation that differs from normal data.

For example, “../” (dot-dot-slash) characters represent %2E%2E%2f in
hexadecimal representation. When the % symbol is encoded again, its
representation in hexadecimal code is %25. The result from the double
encoding process ”../”(dot-dot-slash) would be %252E%252E%252F:

`   The hexadecimal encoding of “../” represents "%2E%2E%2f" `

`   Then encoding the “%” represents "%25" `

`   Double encoding of “../” represents "%252E%252E%252F"`

If you do not want IIS to allow doubled-encoded requests to be served,
use the following (IIS Team,2007) :

<configuration>
`  <system.webServer>`
`   `<security>
`     `<requestFiltering
       allowDoubleEscaping="false">
`     `</requestFiltering>
`   `</security>
`  </system.webServer>`
</configuration>

### Filter High Bit Characters

This allows or rejects all requests to IIS that contain non-ASCII
characters . When this occurs error code 404.12. is displayed to the
user . The UrlScan(IIS6 add-on) equivalent is AllowHighBitCharacters.

<configuration>
` <system.webServer>`
`  `<security>
`    `<requestFiltering
     allowHighBitCharacters="true">
`    `</requestFiltering>
`  `</security>
` </system.webServer>`
</configuration>

### Filter Based on File Extensions

Uisng this filter you can allow IIS to a request based on file
extensions, the error code logged is 404.7. The AllowExtensions and
DenyExtensions options are the UrlScan equivalents.

` `<configuration>
`  <system.webServer>`
`   `<security>
`    `<requestFiltering>
`     `<fileExtensions allowUnlisted="true" >
`     `<add fileExtension=".asp" allowed="false"/>
`     `</fileExtensions>
`    `</requestFiltering>
`   `</security>
`  </system.webServer>`
` `</configuration>

### Filter Based on Request Limits

When IIS rejects a request based on request limits, the error code
logged is: • 404.13 if the content is too long. • 404.14 if the URL is
too large. • 404.15 if the query string is too long. This can be used to
limit a long query string or too much content sent to an application
which you cannot change the source code to fix the issue.

` `<configuration>
`   <system.webServer>`
`     `<security>
`      `<requestFiltering>
`       `<requestLimits
         maxAllowedContentLength="30000000"
         maxUrl="260"
         maxQueryString="25"
         />
`      `</requestFiltering>
`     `</security>
`    </system.webServer>`
`  `</configuration>

### Filter by Verbs

When IIS reject a request based on this feature, the error code logged
is 404.6. This corresponds to the UseAllowVerbs, AllowVerbs, and
DenyVerbs options in UrlScan. In case you want the application to use
only certain type of verb, it is necessary to firt set the allowUnlisted
to ‘false’ and then set the verbs that you would like to allow(see
example)

`  `<configuration>
`   <system.webServer>`
`    `<security>
`     `<requestFiltering>
`      `<verbs allowUnlisted="false">
`        `<add verb="GET" allowed="true" />
`      `</verbs>
`     `</requestFiltering>
`    `</security>
`   </system.webServer>`
</configuration>

### Filter Based on URL Sequences

This feature defines a list of sequences that IIS reject when it is part
of a request. When IIS reject a request for this feature, the error code
logged is 404.5.This corresponds to the DenyUrlSequences feature in
UrlScan. This is a very powerful feature. This avoids a given character
sequence from ever being attended by IIS:

`  `<configuration>
`   <system.webServer>`
`     `<security>
`      `<requestFiltering>
`        `<denyUrlSequences>
`          `<add sequence=".."/>
`        `</denyUrlSequences>
`      `</requestFiltering>
`     `</security>
`    </system.webServer>`
`  `</configuration>

### Filter Out Hidden Segments

In case you want IIS to serve content in binary directory but not the
bin, you can apply this configuration.

<configuration>

`  <system.webServer>`
`     `<security>
`       `<requestFiltering>
`         `<hiddenSegments>
`           `<add segment="BIN"/>
`         `</hiddenSegments>
`       `</requestFiltering>
`     `</security>
`    </system.webServer>`
`  `</configuration>

## Password protection and sensitive information

The web.config files might include sensitive information in the
connection strings such as database passwords, mail server user names
among others.

Sections that are required to be encrypted are:

<appSettings>`. This section contains custom application settings.`
<connectionStrings>`. This section contains connection strings.`
<identity>`. This section can contain impersonation credentials.`
<sessionState>`. This section contains the connection string for the out-of-process session state provider.`

Passwords and user names contained in a <connectionstring> section
should be encrypted. ASP.NET allows you to encrypt this information by
using the functionality aspnet_regiis .This utility is found in the
installed .NET framework under the folder

`%windows%\Microsoft.NET\Framework\v2.0.50727`

You can specify the section you need to encrypt by using the command:

`aspnet_regiis -pef sectiontobeencryoted .`

## Encrypting sections in Web.Config file

Even though encrypting sections is possible, not all sections can be
encrypted, specifically, sections that are read before user code is run.
The following sections cannot be encrypted:

`*`<processModel>
`*`<runtime>
`*`<mscorlib>
`*`<startup>
`*<system.runtime.remoting>`
`*`<configProtectedData>
`*`<satelliteassemblies>
`*`<cryptographySettings>
`*`<cryptoNameMapping>
`*`<cryptoClasses>

## Machine-Level RSA key container or User-Level Key Containers

Encrypting a single file has its disadvantages when this file is moved
to another servers. In this case, the user of an RSA key container is
strongly advice. The RSAProtectedConfigurationProvider supports
machine-level and user-level key containers for key storage.

RSA machine key containers are stored in the following folder:

`\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys`

### User Key Container

When the application that needs to be protected is in a shared hosting
environment and protection of sensitive data cannot be accessible to
other applications, the user key container is strongly recommended. In
this case each application should have a separate identity. RSA
user-level key containers are stored in the following folder:

`\Documents and Settings\{UserName}\Application Data\Microsoft\Crypto\RSA`

## IIS configurations

Depending on the version of IIS that must be configured, it is important
to revise some of its settings which can comprise security in the
server.

### Trust level

The trust level is a set of Code Access Security permissions granted to
an application within a hosting environment. These are defined using
policy files. Depending on the trust level that must be configured, it
is possible to grant FULL, HIGH, MEDIUM, LOW or MINIMAL level. The
ASP.NET host does not apply any additional policy to applications that
are running at the full-trust level.

Example:

`<system.web>`
`  `<securityPolicy>
`    `<trustLevel name="Full" policyFile="internal"/>
`  `</securityPolicy>
`</system.web>`

#### Lock Trust Levels

In the .NET framework web.config file is possible to lock applications
from changing their trust level This file is found at:

` C:\Windows\Microsoft.NET\Framework\{version}\CONFIG`

The following example shows how to lock 2 different application
configuration trust levels (MSDN, 2013)

<configuration>
`  `<location path="application1" allowOverride="false">
`    <system.web>`
`      `<trust level="High" />
`    </system.web>`
`  `</location>
`  `<location path="application2" allowOverride="false">
`    <system.web>`
`      `<trust level="Medium" />
`    </system.web>`
`  `</location>
</configuration>

## References

Yakushev Ruslan , 2008 "IIS 7.0 Request Filtering and URL Rewriting "
available at
<http://www.iis.net/learn/extensions/url-rewrite-module/iis-request-filtering-and-url-rewriting>
(Last accessed on 14 July, 2013)

OWASP, 2009 "Double Encoding" available at
<https://www.owasp.org/index.php/Double_Encoding> (Last accessed on 14
July, 2013)

IIS Team, 2007 "Use Request Filtering " available at
<http://www.iis.net/learn/manage/configuring-security/use-request-filtering>
(Last accessed on 14 July, 2013)

Aguilar Carlos ,2006 "The new Configuration System in IIS 7" available
at
<http://blogs.msdn.com/b/carlosag/archive/2006/04/25/iis7configurationsystem.aspx>
(Last accessed on 14 July, 2013)

MSDN, 2013 . How to: Lock ASP.NET Configuration Settings available at
<http://msdn.microsoft.com/en-us/library/ms178693.aspx> (Last accessed
on 14 July, 2013)