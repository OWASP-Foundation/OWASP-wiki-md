`   <td ``>An attacker will typically download the targeted app from an app store and analyze it within their own local environment using a suite of different tools. `

</td>

`    <td ``>An attacker must perform an analysis of the final core binary to determine its original string table, source code, libraries, algorithms, and resources embedded within the app. Attackers will use relatively affordable and well-understood tools like IDA Pro, Hopper, otool, strings, and other binary inspection tools from within the attacker's environment.`

</td>

`    <td colspan=2 ``>Generally, all mobile code is susceptible to reverse engineering.  Some apps are more susceptible than others.  Code written in languages / frameworks that allow for dynamic introspection at runtime (Java, .NET, Objective C, Swift) are particularly at risk for reverse engineering.  Detecting susceptibility to reverse engineering is fairly straight forward.  First, decrypt the app store version of the app (if binary encryption is applied).  Then, use the tools outlined in the "Attack Vectors" section of this document against the binary. Code will be susceptible if it is fairly easy to understand the app's controlflow path, string table, and any pseudocode/source-code generated by these tools.`

</td>

`    <td ``>An attacker may exploit reverse engineering to achieve any of the following:`

  - Reveal information about back end servers;
  - Reveal cryptographic constants and ciphers;
  - Steal intellectual property;
  - Perform attacks against back end systems; or
  - Gain intelligence needed to perform subsequent code modification.

</td>

`    <td ``>The business impacts from reverse engineering are quite varied. They include the following:`

  - Intellectual Property theft;
  - Reputational Damage;
  - Identity Theft; or
  - Compromise of Backend Systems.

</td>

Generally, most applications are susceptible to reverse engineering due
to the inherent nature of code. Most languages used to write apps today
are rich in metadata that greatly aides a programmer in debugging the
app. This same capability also grealy aides an attacker in understanding
how the app works.

An app is said to be susceptible to reverse engineering if an attacker
can do any of the following things:

  - Clearly understand the contents of a binary's string table
  - Accurately perform cross-functional analysis
  - Derive a reasonably accurate recreation of the source code from the
    binary

Although most apps are susceptible to reverse engineering, it's
important to examine the potential business impact of reverse
engineering when considering whether or not to mitigate this risk. See
the examples below for a small sampling of what can be done with reverse
engineering on its own.

In order to prevent effective reverse engineering, you must use an
obfuscation tool. There are many free and commercial grade obfuscators
on the market. Conversely, there are many different deobfuscators on the
market. To measure the effectiveness of whatever obfuscation tool you
choose, try deobfuscating the code using tools like IDA Pro and Hopper.

A good obfuscator will have the following abilities:

  - Narrow down what methods / code segments to obfuscate;
  - Tune the degree of obfuscation to balance performance impact;
  - Withstand de-obfuscation from tools like IDA Pro and Hopper;
  - Obfuscate string tables as well as methods

**Scenario \#1:** String Table Analysis:

The attacker runs 'strings' against the unencrypted app. As a result of
the string table analysis, the attacker discovers a hardcoded
connectivity string that contains authentication credentials to a
backend database. The attacker uses those credentials to gain access to
the database. The attacker steals a vast array of PII data about the
app's users.

**Scenario \#2:** Cross-Functional Analysis:

The attacker uses IDA Pro against an unencrypted app. As a result of the
string table analysis combined with functioanl cross-referencing, the
attacker discovers Jailbreak detection code. The attacker uses this
knowledge in a subequent code-modification attack to disable jailbreak
detection within the mobile app. The attacker then deploys a version of
the app that exploits method swizzling to steal customer information.

**Scenario \#3:** Source Code Analysis:

Consider a banking Android application. The APK file can be easily
extracted using 7zip/Winrar/WinZip/Gunzip. Once extracted, the attacker
has manifest file, assets, resources and most importantly classes.dex
file.

Then using Dex to Jar converter, an attacker can easily convert it to
jar file. In next step, Java Decompiler (like JDgui) will provide you
the code.

  - [OWASP Reverse Engineering and Code Modification Prevention
    Project](https://www.owasp.org/index.php/OWASP_Reverse_Engineering_and_Code_Modification_Prevention_Project)

<span id="ReferenceItem1">\[1\] Arxan Research: [State of Security in
the App Economy,
Volume 2](https://www.arxan.com/assets/1/7/State_of_Security_in_the_App_Economy_Report_Vol._2.pdf),
November 2013:

  -
    *“Adversaries have hacked 78 percent of the top 100 paid Android and
    iOS apps in 2013.”*</span>

<span id="ReferenceItem2">\[2\] HP Research: [HP Research Reveals Nine
out of 10 Mobile Applications Vulnerable to
Attack](http://www8.hp.com/us/en/hp-news/press-release.html?id=1528865#.UuwZFPZvDi5),
18 November 2013:

  -
    *"86 percent of applications tested lacked binary hardening, leaving
    applications vulnerable to information disclosure, buffer overflows
    and poor performance. To ensure security throughout the life cycle
    of the application, it is essential to build in the best security
    practices from conception."*</span>

<span id="ReferenceItem3">\[3\] North Carolina State University:
[Dissecting Android Malware: Characterization and
Evolution](http://www.csc.ncsu.edu/faculty/jiang/pubs/OAKLAND12.pdf), 7
September 2011:

  -
    *“Our results show that 86.0% of them (Android Malware) repackage
    legitimate apps to include malicious payloads; 36.7% contain
    platform-level exploits to escalate privilege; 93.0% exhibit the
    bot-like capability.”*</span>

<span id="ReferenceItem4">\[4\] Tech Hive: [Apple Pulls Ripoff Apps from
its Walled
Garden](http://www.techhive.com/article/249310/apple_pulls_ripoff_apps_from_its_walled_garden.html)Feb
4th, 2012:

  -
    *“While Apple is known for screening apps before they are allowed to
    sprout up in its walled garden, clearly fake apps do get in. Once
    they do, getting them out depends on developers who raise a
    fuss.”*</span>

<span id="ReferenceItem5">\[5\] Tech Crunch: [Developer Spams Google
Play With RipOffs of Well-Known Apps…
Again](http://techcrunch.com/2014/01/02/developer-spams-google-play-with-ripoffs-of-well-known-apps-again/),
January 2 2014:

  -
    *“It’s not uncommon to search the Google Play app store and find a
    number of knock-off or “fake” apps aiming to trick unsuspecting
    searchers into downloading them over the real thing.”*</span>

<span id="ReferenceItem6">\[6\] Extreme Tech: [Chinese App Store Offers
Pirated iOS Apps Without the Need To
Jailbreak](http://www.extremetech.com/mobile/153849-chinese-app-store-offers-pirated-ios-apps-without-the-need-to-jailbreak),
April 19 2013:

  -
    *“The site offers apps for free that would otherwise cost money,
    including big-name titles.”*</span>

<span id="ReferenceItem7">\[7\] OWASP: [Architectural Principles That
Prevent Code Modification or Reverse
Engineering](https://www.owasp.org/index.php/Architectural_Principles_That_Prevent_Code_Modification_or_Reverse_Engineering),
January 11th 2014.</span>

<span id="ReferenceItem8">\[8\] Gartner report: Avoiding Mobile App
Development Security Pitfalls, 24 May 2013:

  -
    *"For critical applications, such as transactional ones and
    sensitive enterprise applications, hardening should be
    used."*</span>

<span id="ReferenceItem9">\[9\] Gartner report: Emerging Technology
Analysis: Mobile Application Shielding, March 26th, 2013:

  -
    *"As more regulated and sensitive data applications move to mobile
    platforms the need to increase data protection increases. Mobile
    application shielding presents the opportunity to security providers
    to offer higher data protection standards to mobile platforms that
    exceed mobile OS security."*</span>

<span id="ReferenceItem10">\[10\] Gartner report: Proliferating Mobile
Transaction Attack Vectors and What to Do About Them, March 1st, 2013:

  -
    *"Use mobile application security testing services and
    self-defending application utilities to help prevent hacking
    attempts."*</span>

<span id="ReferenceItem11">\[11\] Gartner report: Select a Secure Mobile
Wallet for Proximity, March 1st, 2013:

  -
    *"Application hardening can fortify sensitive business code against
    hacking attempts, such as reverse engineering”*</span>

<span id="ReferenceItem12">\[12\] Forrester paper: Choose The Right
Mobile Development Solutions For Your Organization, May 6th 2013:

  -
    *“5 Key Protections: Data Protection, App Compliance, App-Level
    Threat Defense, Security Policy Enforcement, App Integrity”*</span>

<span id="ReferenceItem13">\[13\] John Wiley and Sons, Inc: [iOS
Hacker's
Handbook](http://www.amazon.com/iOS-Hackers-Handbook-Charlie-Miller/dp/1118204123),
Published May 2012, ISBN 1118204123.</span>

<span id="ReferenceItem14">\[14\] McGraw Hill Education: [Mobile Hacking
Exposed](http://mobilehackingexposed.com/), Published July 2013, ISBN
0071817018.</span>

<span id="ReferenceItem15">\[15\] Publisher Unannounced: [Android
Hacker's
Handbook](http://www.amazon.com/Android-Hackers-Handbook-Joshua-Drake/dp/111860864X),
To Be Published April 2014.</span>

<span id="ReferenceItem16">\[16\] Software Development Times: [More
than 5,000 apps in the Google Play Store are copied APKs, or
'thief-ware'](http://sdt.bz/66393#ixzz2sHa7dFMp), November 20 2013:

  -
    *“In most cases, the 2,140 copycat developers that were found
    reassembled the apps almost identically, adding new advertising SDKs
    to siphon profits away from the original developers.*</span>

<span id="ReferenceItem17">\[17\] InfoSecurity Magazine: [Two Thirds of
Personal Banking Apps Found Full of
Vulnerabilities](http://www.infosecurity-magazine.com/view/36376/two-thirds-of-personal-banking-apps-found-full-of-vulnerabilities/),
January 3 2014:

  -
    *“But one of his more worrying findings came from disassembling the
    apps themselves ... what he found was hardcoded development
    credentials within the code. An attacker could gain access to the
    development infrastructure of the bank and infest the application
    with malware causing a massive infection for all of the
    application’s users.”*</span>

<span id="ReferenceItem18">\[18\] InfoSecurity Magazine: [Mobile Malware
Infects Millions; LTE Spurs
Growth](http://www.infosecurity-magazine.com/view/36686/mobile-malware-infects-millions-lte-spurs-growth/),
January 29 2014:

  -
    *"Number of mobile malware samples is growing at a rapid clip,
    increasing by 20-fold in 2013... It is trivial for an attacker to
    hijack a legitimate Android application, inject malware into it and
    redistribute it for consumption. There are now binder kits available
    that will allow an attacker to automatically inject malware into an
    existing application"*</span>