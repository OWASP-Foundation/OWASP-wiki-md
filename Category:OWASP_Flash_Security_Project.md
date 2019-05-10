#### Main

## Overview

The OWASP Flash Security Project is an open project for sharing
knowledge in order to raise awareness of Flash application security.

## Goals

The OWASP Flash Security Project aims to share guidelines, tools and
resources for securing Flash applications.



## Table of Contents

|                                                                                                                                   |                                                                                                              |                                                                                                                                   |                                                                                                                       |
| --------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------- |
| **Research**                                                                                                                      | **References**                                                                                               | **Tools**                                                                                                                         | **Libraries**                                                                                                         |
| [Videos](http://www.owasp.org/index.php/Category:OWASP_Flash_Security_Project#Videos)                                             | [References](http://www.owasp.org/index.php/Category:OWASP_Flash_Security_Project#References)                | [OWASP Tools](http://www.owasp.org/index.php/Category:OWASP_Flash_Security_Project#OWASP_Tools)                                   | [3rd Party Libs](http://www.owasp.org/index.php/Category:OWASP_Flash_Security_Project#Third-party_Security_Libraries) |
| [White Papers/Presentations](http://www.owasp.org/index.php/Category:OWASP_Flash_Security_Project#White_Papers_.2F_Presentations) | [Specifications](http://www.owasp.org/index.php/Category:OWASP_Flash_Security_Project#Useful_Specifications) | [Static Analysis](http://www.owasp.org/index.php/Category:OWASP_Flash_Security_Project#Static_Analysis)                           |                                                                                                                       |
| [Articles](http://www.owasp.org/index.php/Category:OWASP_Flash_Security_Project#Articles)                                         |                                                                                                              | [Disassemblers](http://www.owasp.org/index.php/Category:OWASP_Flash_Security_Project#Disassemblers)                               |                                                                                                                       |
| [Example Vulnerabilities](http://www.owasp.org/index.php/Category:OWASP_Flash_Security_Project#Example_Vulnerabilities)           |                                                                                                              | [Decompilers](http://www.owasp.org/index.php/Category:OWASP_Flash_Security_Project#Decompilers)                                   |                                                                                                                       |
|                                                                                                                                   |                                                                                                              | [Obfuscators/De-obfuscators](http://www.owasp.org/index.php/Category:OWASP_Flash_Security_Project#Obfuscators_.2F_De-obfuscators) |                                                                                                                       |
|                                                                                                                                   |                                                                                                              | [LSO Editors](http://www.owasp.org/index.php/Category:OWASP_Flash_Security_Project#Local_Shared_Object_Editors)                   |                                                                                                                       |
|                                                                                                                                   |                                                                                                              | [AMF Tools](http://www.owasp.org/index.php/Category:OWASP_Flash_Security_Project#AMF_Tools)                                       |                                                                                                                       |
|                                                                                                                                   |                                                                                                              | [Analysis/Defense](http://www.owasp.org/index.php/Category:OWASP_Flash_Security_Project#Analysis)                                 |                                                                                                                       |



## Videos

  - [How to Develop Secure Flash Platform
    Apps](http://tv.adobe.com/show/how-to-develop-secure-flash-platform-apps/)
    An Adobe TV series discussing how to author and test secure Flash
    applications. The presentations cover common vulnerabilities in SWF
    content and how to avoid them. Each video is about 5-10 minutes long
    and is by Peleus Uhley.

<!-- end list -->

  - [Creating Secure ActionScript
    Applications](http://tv.adobe.com/watch/max-2010-develop/creating-secure-actionscript-applications/)
    An hour long video targeted at developers and QEs on creating secure
    Flash applications from Adobe MAX 2010. Adobe MAX is Adobe's
    developer conference. The talk is by Peleus Uhley.

<!-- end list -->

  - [Assessing, Testing & Validating Flash
    Content](http://vimeo.com/15506137) A 45 minute talk from OWASP
    AppSec USA 2010 on how to assess and test Flash applications. The
    talk is by Peleus Uhley.

<!-- end list -->

  - [Understanding the Flash Player Security
    Model](http://tv.adobe.com/#vi+f15384v1102) Deneb Meketa of Adobe
    gives a one hour presentation at the Adobe MAX 2008 conference in
    San Francisco entitled, "Flash Security: Why and how." This
    presentation provides a good overview of several aspects of Flash
    Player's security model. Approximately 1 hour long.

<!-- end list -->

  - [Billy Wins A
    Cheeseburger](http://h30431.www3.hp.com/index.jsp?fr_story=3a98c704f7ef61299c19ef1f648f1acb1a5aeab8&rf=bm)
    A video by HP that explains a basic Flash vulnerability that can be
    found by decompilers. Approximately 3 minutes long.

<!-- end list -->

  - [Blinded by Flash: Widespread Security Risks Flash Developers Don't
    See](http://securitytube.net/Hacking-Flash-Applications-for-Fun-and-Profit-\(Blackhat\)-video.aspx)
    Prajakta Jagdale describes the attack surface flash applications
    have based on various things developers overlook. In this
    presentation she talks about the basic cross domain security model
    between flash applets, Cross Site Scripting attacks on Flash
    applications, Data injection attacks, Flash malware, decompilation
    of Flash swf files, code and binary obfuscation and many other
    attack vectors which a malicious attacker could use to hack Flash
    applications. Approximately 1 hour long.

<!-- end list -->

  - [Deblaze - A Remote Method Enumeration Tool for Flex
    Servers](https://media.defcon.org/dc-17/video/DEFCON%2017%20Hacking%20Conference%20Presentation%20By%20Jon%20Rose%20-%20Deblaze%20A%20Remote%20Method%20Enumeration%20Tool%20for%20Flex%20Servers%20-%20Video%20and%20Slides.m4v)
    This is an excellent 20 minute presentation from DefCon 17 by Jon
    Rose on how to test AMF services using the deBlaze tool that he
    authored.

<!-- end list -->

  - [RIA Security: Real-World Lessons from Flash and
    Silverlight](http://technet.microsoft.com/en-us/security/ee460903.aspx#ria)
    Jesse Collins from Microsoft's Silverlight team and Peleus Uhley
    from Adobe's Flash team discuss common threats to RIA applications.
    Approximately 1 hour long.



## White Papers / Presentations

**Flash**

  - **Flash Parameter Injection**
    [pdf](http://blog.watchfire.com/FPI.pdf), IBM Rational Application
    Security Team, [OWASP
    AppSec 2008](http://www.owasp.org/index.php/OWASP_NYC_AppSec_2008_Conference),
    24th September 2008, NYC, NY (USA)

<!-- end list -->

  - **Testing Flash Applications using WebScarab**
    [pdf](https://www.owasp.org/images/5/58/Testing_Flash_Applications.pdf),
    Martin Clausen - Deloitte [Denmark Chapter
    Meeting](http://www.owasp.org/index.php/Denmark), 12th March 2008,
    Denmark

<!-- end list -->

  - **Testing Flash Applications**
    [ppt](http://www.owasp.org/images/8/8c/OWASPAppSec2007Milan_TestingFlashApplications.ppt),
    Stefano Di Paola, [Owasp
    Appsec 2007](http://www.owasp.org/index.php/6th_OWASP_AppSec_Conference_-_Italy_2007/Agenda),
    17th May 2007, Milan (Italy).

<!-- end list -->

  - **Testing and Exploiting Flash Applications**
    [pdf](http://events.ccc.de/camp/2007/Fahrplan/attachments/1320-FlashSec.pdf),
    Fukami, Chaos Computer Camp, 2007

<!-- end list -->

  - **Finding Vulnerabilities in Flash Applications**
    [ppt](http://www.owasp.org/images/d/d8/OWASP-WASCAppSec2007SanJose_FindingVulnsinFlashApps.ppt),
    Stefano Di Paola, [Owasp
    Appsec 2007](http://www.owasp.org/index.php/7th_OWASP_AppSec_Conference_-_San_Jose_2007/Agenda),
    15th November 2007, San Jose, CA (USA)

<!-- end list -->

  - **Neat, New, and Ridiculous Flash Hacks** - whitepaper:
    [pdf](http://www.blackhat.com/presentations/bh-dc-10/Bailey_Mike/BlackHat-DC-2010-Bailey-Neat-New-Ridiculous-flash-hacks-wp.pdf),
    presentation:[pdf](http://www.blackhat.com/presentations/bh-dc-10/Bailey_Mike/BlackHat-DC-2010-Bailey-Neat-New-Ridiculous-flash-hacks-slides.pdf),
    Mike Bailey, Black Hat DC 2010, Washington, DC (USA)


**AMF**

  - **AMF Testing Made Easy** - whitepaper:
    [pdf](https://media.blackhat.com/bh-us-12/Briefings/Carettoni/BH_US_12_Carettoni_AMF_Testing_WP.pdf),
    presentation:
    [pdf](https://media.blackhat.com/bh-us-12/Briefings/Carettoni/BH_US_12_Carettoni_AMF_Testing_Slides.pdf),
    Luca Carettoni, Black Hat USA 2012, Las Vegas, NV (USA). This
    presentation discusses how to use the
    [Blazer](http://code.google.com/p/blazer/) tool with Burp to conduct
    AMF testing.

<!-- end list -->

  - **Pentesting Adobe Flex Applications** -
    [pdf](http://www.gdssecurity.com/l/OWASP_NYNJMetro_Pentesting_Flex.pdf),
    Marcin Wielgoszewski, April 2010 OWASP NYC Chapter Meeting, NYC, NY
    (USA)

<!-- end list -->

  - **DeBlaze: A remote enumeration tool for Flex servers**
    [pdf](http://www.defcon.org/images/defcon-17/dc-17-presentations/defcon-17-jon_rose-deblaze.pdf),
    Jon Rose,
    [DefCon 17](http://www.defcon.org/html/links/dc-archives/dc-17-archive.html#Rose),
    31st July 2009, Las Vegas, NV (USA)


**University Research**

  - **ActionScript bytecode verification with co-logic programming**
    [pdf](http://portal.acm.org/citation.cfm?id=1554339.1554342), Brian
    W. DeVries, Gopal Gupta, Kevin W. Hamlen, Scott Moore, and Meera
    Sridhar of The University of Texas at Dallas, Proceedings of the ACM
    SIGPLAN Fourth Workshop on Programming Languages and Analysis for
    Security 2009.

<!-- end list -->

  - **Creating a more sophisticated security platform for Flash, AIR and
    others** [ppt](http://www.utdallas.edu/~mxs072100/Adobe.ppt)
    Presented at Adobe Systems, Inc. by Meera Sridhar, November, 2009

<!-- end list -->

  - **ActionScript In-Lined Reference Monitoring in Prolog**
    [pdf](http://www.utdallas.edu/~mxs072100/padl.pdf), Meera Sridhar
    and Kevin W. Hamlen of The University of Texas at Dallas,
    Proceedings of the Twelfth Symposium on Practical Aspects of
    Declarative Languages (PADL), Jan 2010.

<!-- end list -->

  - **ActionScript In-lined Reference Monitoring in Prolog**
    [pptx](http://www.utdallas.edu/~mxs072100/padl10.pptx) Presented at
    PADL 2010, Madrid, Spain by Meera Sridhar.



## Articles

**Development**

  - [Creating more secure SWF web
    applications](http://www.adobe.com/devnet/flashplayer/articles/secure_swf_apps.html)
    This Adobe Developer Center article discusses secure ActionScript
    programming practices.

<!-- end list -->

  - [Cross-domain policy file usage recommendations for Flash
    Player](http://www.adobe.com/devnet/flashplayer/articles/cross_domain_policy.html)
    This Adobe Developer Center article discusses some of the common
    security issues that you should consider when deciding how to use a
    cross-domain policy file on your server.

<!-- end list -->

  - [Flash Player 10 Security Model: Stakeholders and
    Sandboxes](http://www.insideria.com/2010/03/flash-player-10-security-model.html)
    This is an article that condenses the official Flash Player Security
    Model down to a one page article discussing the stakeholders and
    sandboxes.

<!-- end list -->

  - [AMFPHP Security Basics](http://theflashblog.com/?p=419) This a blog
    covering how to secure AMFPHP version 1.9 and higher. AMFPHP is
    server-side code that receives AMF requests from Flash clients.

<!-- end list -->

  - [Securely Deploying Cross-Domain Policy
    files](http://blogs.adobe.com/asset/2009/11/securely_deploying_cross-domai.html)
    This Adobe ASSET blog provides 5 tips for securely deploying
    cross-domain policy files.

<!-- end list -->

  - [Securing your Flash
    Application](http://askmeflash.com/article/16/securing-your-flash-application)
    A quick ten item checklist of high level things to look for in your
    SWF before shipping.

<!-- end list -->

  - [Security Domains, Application Domains, and More in
    ActionScript 3.0](http://www.senocular.com/flash/tutorials/contentdomains/)
    A fairly in depth article by Senocular.com explaining security
    domains, application domains, cross-domain policy files,
    allowDomain() and more.

**Penetration Testing**

  - [A Lazy Pen Tester’s Guide to Testing Flash
    Applications](http://www.ivizsecurity.com/blog/web-application-security/testing-flash-applications-pen-tester-guide/)
    A short blog describing some of the basic steps of testing Flash
    applications by iViZ.

<!-- end list -->

  - [Penetrating Intranets through Adobe Flex
    Applications](http://www.gdssecurity.com/l/b/2010/03/17/penetrating-intranets-through-adobe-flex-applications/)
    A short blog (03/17/2010) by Marcin Wielgoszewski of Gothan Digital
    Science introducing the
    [Blazentoo](http://www.gdssecurity.com/l/t/d.php?k=Blazentoo) tool
    and how to take advantage of open BlazeDS proxies.

<!-- end list -->

  - [Pentesting Adobe Flex Applications with a Custom AMF
    Client](http://www.gdssecurity.com/l/b/2009/11/11/pentesting-adobe-flex-applications-with-a-custom-amf-client/)
    A short blog (11/11/2009) by Marcin Wielgoszewski of Gothan Digital
    Science on how to write custom pyAMF-based clients for testing Flex
    services.

<!-- end list -->

  - [Client-side Remote File Inclusion in
    Flash](http://erlend.oftedal.no/blog/?blogid=103) This blog
    discusses how to perform cross-site scripting attacks against
    applications that read in XML configuration files.

<!-- end list -->

  - [Flash
    Security](http://code.google.com/p/doctype/wiki/ArticleFlashSecurity)
    A Google code article on different types of cross-site scripting and
    crossdomain.xml attacks.

**Updates to the Flash Player Security Model**

  - [The Flash Player sandbox
    bridge](http://www.adobe.com/devnet/security/articles/flash-player-sandbox-bridge.html)
    - This Adobe Developer Center article describes how the new
    LoaderInfo sandbox bridge APIs can be used as a safer alternative to
    Security.allowDomain(\*).

<!-- end list -->

  - [Understanding the security changes in Flash Player 10.1 and
    AIR 2](http://www.adobe.com/devnet/flashplayer/articles/fplayer10.1_air2_security_changes.html)
    - This Adobe Developer Center article describes the new changes that
    affect security in Flash Player 10.1 and AIR. This article discusses
    a new feature, LoaderContext.allowCodeImport, which can help in
    safely loading remote content via loadBytes(). It also discusses
    minor changes in behavior that may require action by the developer.

<!-- end list -->

  - [Understanding the security changes in Flash
    Player 10](http://www.adobe.com/devnet/flashplayer/articles/fplayer10_security_changes.html)
    - This Adobe Developer Center article describes the new changes that
    affect security in the Flash Player 10. This includes information on
    changes to socket timing, policy file strictness, upload and
    download, RTMFP and full screen mode.

<!-- end list -->

  - [User-initiated action requirements in Flash
    Player 10](http://www.adobe.com/devnet/flashplayer/articles/fplayer10_uia_requirements.html)
    - This Adobe Developer Center article describes the new
    user-initiated action requires in Flash Player 10. These
    requirements include chances to FileReference, Clipboard,
    full-screen mode and pop-up windows.

<!-- end list -->

  - [Preparing for the Flash Player 9 April 2008 Security
    Update](http://www.adobe.com/devnet/flashplayer/articles/flash_player9_security_update.html)
    - This Adobe Developer Center article describes the new mitigations
    for DNS Rebinding (socket policy files), cross-site flashing and the
    introduction of cross-domain header meta-policies to help address
    attacks such as the UPnP attack.

<!-- end list -->

  - [Security Changes in Flash
    Player 9](http://www.adobe.com/devnet/flashplayer/articles/fplayer9_security.html)
    This Adobe Developer Center article describes the important changes
    that need to be made to existing crossdomain.xml and socket policy
    files. All websites that use cross-domain or socket policy files
    will need to implement these changes in order to be compatible with
    Adobe's new format. After the implementation of Phase II, Adobe will
    no longer support the old format.



## Example Vulnerabilities

*The intent of this section is to provide real-world examples of
exploitation. This can be useful for consultants to help demonstrate to
clients that these techniques have been used in the wild. In some
instances, these examples include individual SWFs that were copied to
hundreds of web sites. Therefore, a consultant should look for these
specific SWFs on a website when performing an assessment to ensure that
they have a current version.*

  - [Cross-site Scripting through Flash in Gmail Based
    Services](http://blog.watchfire.com/wfblog/2010/03/cross-site-scripting-through-flash-in-gmail-based-services.html)
    - This is an example of a cross-site scripting vulnerability that
    was the result of passing tainted data to ExternalInterface.call.

<!-- end list -->

  - [XSS Vulnerabilities in Common Flash
    Files](http://docs.google.com/Doc?docid=ajfxntc4dmsq_14dt57ssdw) -
    This paper by Rich Cannings shows sample attack URLs for individual
    SWFs that are hosted across hundreds of websites. The techniques
    demonstrated in this paper for achieving cross-site scripting
    including using javascript: URLs, asfunction: URLs, and loading
    malicious child SWFs (aka cross-site Flashing).

<!-- end list -->

  - [clickTAG Cross-site
    scripting](http://lists.grok.org.uk/pipermail/full-disclosure/2003-April/004514.html)
    - It is very common for Flash-based advertisements to accept a
    FlashVar called, clickTAG. If the clickTAG FlashVar is passed
    directly to a browser navigation API, such as getURL, then the
    attacker can achieve cross-site scripting by changing the clickTAG
    URL to a javascript: URL. Cross-site scripting as the result of a
    manipulated clickTAG FlashVar is the most common manifestation of
    cross-site scripting in Flash content.

<!-- end list -->

  - [I used to know what you watched on
    YouTube](http://jeremiahgrossman.blogspot.com/2008/09/i-used-to-know-what-you-watched-on.html)
    - Jeremiah Grossman's blog post regarding his attack on
    youTube.com's "\*.google.com" cross-domain permission.



## References

  - [OWASP Testing Guide: Testing for cross-site
    flashing](http://www.owasp.org/index.php/Testing_for_Cross_site_flashing_\(OWASP-DV-004\))
    - Covers finding both cross-site scripting and cross-site flashing.

<!-- end list -->

  - [Adobe Flash Player Developer Center Security
    section](http://www.adobe.com/devnet/flashplayer/security.html) -
    Where Adobe posts articles and information related to Flash Player
    security.

<!-- end list -->

  - [Adobe Flash Player 10 Security
    Model](http://www.adobe.com/devnet/flashplayer/articles/flash_player10_security_wp.html)

<!-- end list -->

  - [Adobe Flash Player 9 Security
    Model](http://www.adobe.com/devnet/flashplayer/articles/flash_player_9_security.pdf)

<!-- end list -->

  - [Adobe Security Bulletins and
    Advisories](http://www.adobe.com/support/security/) This is where
    Adobe posts all of their security advisories and bulletins.

<!-- end list -->

  - [Applying Flex
    Security](http://help.adobe.com/en_US/Flex/4.0/UsingSDK/WS2db454920e96a9e51e63e3d11c0bf69084-7f9b.html)
    The security chapter from the Adobe Flex 4 manual.

<!-- end list -->

  - [Flash Player
    Security](http://help.adobe.com/en_US/ActionScript/3.0_ProgrammingAS3/WS5b3ccc516d4fbf351e63e3d118a9b90204-7d23.html)
    The security chapter from the Programming ActionScript 3.0 section
    the Flash CS4 Documentation.

<!-- end list -->

  - [Developing and Loading
    Sub-applications](http://help.adobe.com/en_US/Flex/4.0/UsingSDK/WS2db454920e96a9e51e63e3d11c0bf69084-7d14.html)
    This Flex SDK framework allows two or more untrusted SWFs to pass
    limited information between each other through the use of Shared
    Events.


\== Useful Specifications ==

  - [SWF File Format Specification](http://www.adobe.com/devnet/swf/)
    This documents the file format and structure of SWF files.

<!-- end list -->

  - [AVM2
    Specification](http://www.adobe.com/devnet/actionscript/articles/avm2overview.pdf)
    Describes the Flash ActionScript Virtual Machine used for
    ActionScript 3.0 code.

<!-- end list -->

  - [AMF3
    Specification](http://opensource.adobe.com/wiki/download/attachments/1114283/amf3_spec_05_05_08.pdf)
    The specification for version 3 of AMF used by Flash Player.

<!-- end list -->

  - [AMF0
    Specification](http://opensource.adobe.com/wiki/download/attachments/1114283/amf0_spec_121207.pdf?version=1)
    The specification for the first generation of AMF (AMF 0) used by
    Flash Player.

<!-- end list -->

  - [RTMP Specification](http://www.adobe.com/devnet/rtmp/) This is the
    specification for the Real Time Messaging Protocol used by SWF
    content

<!-- end list -->

  - [Video File Format Specification](http://www.adobe.com/devnet/flv/)
    The FLV/F4V open specification documents the file formats for
    storing media content used to deliver streaming audio and video for
    playback in Adobe® Flash® Player and Adobe AIR™ software.

<!-- end list -->

  - [Cross-domain Policy File
    Specification](http://www.adobe.com/devnet/articles/crossdomain_policy_file_spec.html)
    This document serves as a reference for the structure and use of
    cross-domain policy files.

<!-- end list -->

  - [Tamarin Open Source
    Project](http://www.mozilla.org/projects/tamarin/) The Tamarin
    virtual machine is used within the Adobe Flash Player and is also
    being adopted for use by projects outside Adobe. The Tamarin
    just-in-time compiler (the "NanoJIT") is a collaboratively developed
    component used by both Tamarin and Mozilla TraceMonkey.



## Third-party Security Libraries

  - [AS3Crypto](http://crypto.hurlant.com/) - An ActionScript 3.0
    cryptography library.

<!-- end list -->

  - [as3corelib](http://code.google.com/p/as3corelib/) - An Adobe
    sponsored Google Code project that contains ActionScript 3.0
    implementations of WS-Security, SHA, MD5 and other utilities.

<!-- end list -->

  - [Alchemy ActionScript 3 Crypto
    Wrapper](http://labs.adobe.com/wiki/index.php/Alchemy:Libraries) -
    An Adobe labs project to port OpenSSL to ActionScript using Alchemy
    (previously known as Flacc). Includes the SHA1, SHA2, MD5, PKCS12
    and AES from OpenSSL.

<!-- end list -->

  - [flash-validators](http://code.google.com/p/flash-validators/) - An
    Adobe sponsored Google Code project that contains ActionScript 2.0
    and ActionScript 3.0 data validation libraries.

<!-- end list -->

  - [Protected Messaging
    Adaptor](http://bugs.adobe.com/jira/browse/BLZ-415) - This addition
    to the latest version of BlazeDS protects against an attack that
    allows an untrusted individual to subscribe to wildcard sub-topics.
    This threat is described within this
    [blog](http://www.jamesward.com/blog/2009/07/22/protected-messaging-in-flex-with-blazeds-and-lcds/)
    by James Ward.

<!-- end list -->

  - [Flex
    validators](http://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/mx/validators/package-detail.html)
    - Validation routines contained within the Adobe Flex SDK.



## OWASP Tools

  - [SWFIntruder](https://www.owasp.org/index.php/Category:SWFIntruder)
    OWASP Flash security testing tool


\== Static Analysis ==

  - [FlexPMD](http://opensource.adobe.com/wiki/display/flexpmd/FlexPMD)
    Performs general code analysis with a few security checks.

<!-- end list -->

  - [Fortify Static Code
    Analyzer](https://www.fortify.com/products/hpfssc/source-code-analyzer.html)
    **($)** Fortify's SCA supports searching for vulnerabilities within
    ActionScript 3.0, Flex 3 and Flex 4 applications.

<!-- end list -->

  - [FlashDiggity](http://www.bishopfox.com/resources/tools/google-hacking-diggity/attack-tools/#searchdiggity-v-3)
    FlashDiggity is part of the SearchDiggity tool created by the Bishop
    Fox consulting firm. It will decompile the SWF and use regular
    expressions to search for strings that are security related.
    FlashDiggity automates Google/Bing
    searching/downloading/decompiling/analysis of SWF files to identify
    Flash vulnerabilities and information disclosures.

<!-- end list -->

  - [SWFScan](http://h30499.www3.hp.com/t5/Following-the-White-Rabbit-A/SWFScan-FREE-Flash-decompiler/ba-p/5440167)
    This Windows tool decompiles a SWF and performs static analysis to
    identify common vulnerabilities for both ActionScript 2.0 and
    ActionScript 3.0 content.



## Disassemblers

  - [Adobe SWF
    Investigator](http://labs.adobe.com/technologies/swfinvestigator/)
    An Adobe Labs project that performs disassembly of ActionScript 2
    and ActionScript 3. Also shows SWF Tag information.

<!-- end list -->

  - [Flasm](http://flasm.sourceforge.net/) Flasm provides both
    disassembly and assembly functionality.

<!-- end list -->

  - [Nemo440](http://www.docsultant.com/nemo440/) Nemo440 is an AIR
    based ActionScript 3.0 disassembler.

<!-- end list -->

  - [swfdump](http://opensource.adobe.com/svn/opensource/flex/sdk/trunk/bin/)
    The Adobe Flex SDK, when built with ant, creates the swfdump utility
    ([overview](http://blogs.adobe.com/gosmith/2008/02/disassembling_a_swf_with_swfdu_1.html)).

<!-- end list -->

  - [ErlSWF](http://code.google.com/p/erlswf/) A SWF disassembly tool
    based authored in Erlang

<!-- end list -->

  - [abcdump](http://www.masonchang.com/2008/06/building-abcdump.html)
    The abcdump tool can be built from the tamarin source tree to
    disassemble AS3 byte code.

<!-- end list -->

  - [010Editor](http://www.sweetscape.com/010editor/) This commercial
    tool has a
    [template](http://www.sweetscape.com/010editor/templates/files/SWFTemplate.bt)
    for analyzing AS2 byte code.

<!-- end list -->

  - [swfutils](http://segfaultlabs.com/swfutils) An ActionScript 3
    library for disassembling SWF files.

<!-- end list -->

  - [RABCDAsm](https://github.com/CyberShadow/RABCDAsm#readme) RABCDAsm
    is a collection of utilities including an ActionScript 3
    assembler/disassembler, and a few tools to manipulate SWF files.

<!-- end list -->

  - [Yogda AVM2 Workbench](http://yogda.2ka.org/) Yogda® is a
    development tool for intermediate/advanced actionscript programmers.
    It includes an AVM2 disassembler.



## Decompilers

  - [Flash Decompiler Trillix](http://www.flash-decompiler.com/)
    **($):** Windows and Mac versions. Supports ActionScript 2.0 and
    ActionScript 3.0, Flash 5, 6, 7, 8, 9, 10, Flash CS5 and Flex. Able
    to extract resources,edit SWF elements and provide a source FLA
    file. Costs @ $80 plus tax/shipping.

<!-- end list -->

  - [SWFWire Inspector](http://www.swfwire.com/inspector) An open source
    AIR application for viewing images, shapes, and even
    syntax-highlighted ActionScript 3 within SWF files.

<!-- end list -->

  - [SWFScan](https://h30406.www3.hp.com/campaigns/2009/wwcampaign/1-5TUVE/index.php?key=swf)
    This Windows tool decompiles a SWF and performs static analysis to
    identify common vulnerabilities for both ActionScript 2.0 and
    ActionScript 3.0 content.

<!-- end list -->

  - [Flare](http://www.nowrap.de/flare.html) Flare ActionScript 2.0
    decompiler for Windows, Linux and Mac OS X.

<!-- end list -->

  - [Buraks ActionScript Viewer](http://www.buraks.com/asv/) **($):** An
    ActionScript 2.0 and ActionScript 3.0 decompiler that is able to
    extract resources and provide a rough FLA file. Costs @ $80 plus
    tax/shipping.

<!-- end list -->

  - [SoThink Flash
    Decompiler](http://www.sothink.com/product/flashdecompiler/)
    **($):** An ActionScript 2.0 and ActionScript 3.0 decompiler that is
    able to extract resources and provide a rough FLA file. Costs @ $80
    plus tax/shipping.

<!-- end list -->

  - [Dump Flash
    Decompiler](http://www.dcomsoft.com/download/dfdinstall.exe)
    Freeware program that treats compressed and decompressed SWF-files
    and shows the detailed structure in the tree form. Windows.

<!-- end list -->

  - [JPEXS Free Flash Decompiler
    (FFDec)](http://www.free-decompiler.com/flash/) JPEXS Free Flash
    Decompiler (FFDec) is free opensource Flash SWF Decompiler. Program
    can view source code of ActionScript 1/2 or 3 parts, export it or
    edit (p-code editor for AS3). Texts or images can be edited or
    replaced. The SWF decompiler can also export shapes, images, sounds
    or movies. SWF to FLA format conversion is also available.



## Obfuscators / De-obfuscators

It should be noted that no obfuscator can protect a SWF from being
reverse engineered. An attacker will always be able to extract data from
SWFs if they believe it is worth the effort. Obfuscators are only serve
as a deterrent for preventing casual inspection of the SWF.

It should also be noted that some obfuscators generate SWFs that do not
conform to the Adobe SWF file format specification. Flash Player may
still be able to play them but they do not conform to the spec. This
could lead to some security tools such as Blitzablieter rejecting them
as potentially malicious.

  - [Sulo](https://github.com/F-Secure/Sulo) Sulo is an open-source
    project from F-Secure. It can log decrypted strings from
    SecureSWF-protected files and it can dynamically save swf objects
    loaded with Loader.loadBytes() to disk.

<!-- end list -->

  - [SWF Reader](http://sourceforge.net/p/swf-reader/wiki/Home/) SWF
    Reader can edit and deobfuscate SWFs. It has implemented a few
    deobfuscators for AS2 and AS3 Flash but mostly concentrates on AS3
    SWFs

<!-- end list -->

  - [SWF Revealer](http://www.buraks.com/swfrul/) There are two versions
    of Buraks SWF Revealer. This link points to one version. There is
    another version is which is an add-on to Buraks ActionScript Viewer.

<!-- end list -->

  - [SWF ID](http://swfid.zz.mu/) Detect common SWF protectors, SWF
    obfuscators, SWF cryptors and SWF compilers.

<!-- end list -->

  - [DComSoft SWF Protector](http://www.dcomsoft.com/) **($):**
    ActionScript 2.0/3.0 obfuscator for protecting your SWF files from
    Flash Decompilers. Available for Windows, Mac OS, Linux. Costs
    approximately $40.



## Local Shared Object Editors

  - [Adobe SWF
    Investigator](http://labs.adobe.com/technologies/swfinvestigator/)
    Cross-platform tool for viewing and editing LSOs.

<!-- end list -->

  - [Flashbug](http://blog.coursevector.com/flashbug) An extension for
    the Firefox Firebug plugin.

<!-- end list -->

  - [SolVE](http://solve.sourceforge.net/) Cross-platform Local Shared
    Object editor and viewer.

<!-- end list -->

  - [.sol Editor](http://sourceforge.net/projects/soleditor/) Windows
    based Local Shared Object editor



## AMF Tools

  - [Adobe SWF
    Investigator](http://labs.adobe.com/technologies/swfinvestigator/)
    Allows sending of custom messages, simple fuzzing and service
    identification of AMF endpoints.

<!-- end list -->

  - [Flashbug](http://blog.coursevector.com/flashbug) An extension for
    the Firefox Firebug plugin that allows you to view AMF data sent to
    and from the page to the server.

<!-- end list -->

  - [DeBlaze](http://deblaze-tool.appspot.com/) A free tool that
    attempts to identify AMF services through brute force, dictionary
    attacks.

<!-- end list -->

  - [Blazentoo](http://www.gdssecurity.com/l/t/d.php?k=Blazentoo)
    Blazentoo is an Adobe AIR application that can be used to exploit
    insecure Adobe BlazeDS and LiveCycle Data Services ES servers.
    Blazentoo provides the ability to seamlessly browse web content,
    abusing insecurely configured Proxy Services.

<!-- end list -->

  - [Blazer](http://code.google.com/p/blazer/) Blazer is a custom AMF
    messages generator with fuzzing capabilities, developed as Burp
    Suite plugin. It is designed and implemented to make AMF testing
    easy, and yet allows researchers to control fully the entire
    security testing process.

<!-- end list -->

  - [WebScarab](http://www.owasp.org/index.php/Category:OWASP_WebScarab_Project)
    Full AMF support is currently checked into the main branch of the
    WebScarab project. It has not been rolled into the SourceForge or
    Java Web Start versions of the WebScarab project at the time of this
    writing.

<!-- end list -->

  - [WebScarab AMF
    Plugin](http://code.google.com/p/webscarab-amf-plugin/) This is a
    google code project to add AMF support as a plugin to WebScarab.

<!-- end list -->

  - [AMF Parser](http://amfparser.codeplex.com/) AMFParser plugin for
    Fiddler2 web debugger. It can be used for parsing and displaying AMF
    data inside HTTP's POST requests and responses.

<!-- end list -->

  - [pinta](http://code.google.com/p/pinta/) Pinta is a utility that
    allows a developer to test services by making custom AMF service
    calls, and viewing detailed output. This Google Code project is
    based on Adobe AIR.

<!-- end list -->

  - [Charles Proxy](http://www.charlesproxy.com/) **($):** This is a
    basic HTTP proxy but it provides support for interpreting AMF
    communications. Costs approximately $50.

<!-- end list -->

  - [Burp Suite
    Professional](http://releases.portswigger.net/2009/08/v1214.html)
    **($):** The 1.2.124 version of Burp Suite Pro adds AMF support to
    all tools except for Burp Intruder and Burp Scanner is updated to
    automatically place attack payloads within string-based AMF values.

<!-- end list -->

  - [AMF
    Shell](http://george.hedfors.com/content/action-message-format-amf-shell)
    AMF Shell is a command line utility based on Python that enumerates
    services and allows the user to send customized AMF messages to a
    server.



## Cross-Domain Tools

  - [Cross-domain Policy
    Analyzer](http://web.appsec.ws/Tools/Crossdomain.swf) A tool to test
    your cross-domain policy file by Jason Calvert of WhiteHat Security.



## Analysis

  - [Certifying IRM for ActionScript
    Bytecode](http://www.utdallas.edu/~mxs072100/ASIRM_project.html)
    This page contains the binaries for Meera Sridhar's research into
    using In-lined Reference Monitors to rewrite ActionScript bytecode
    for the purposes of policy enforcement. This project is currently
    targeted at AVM2 code.

<!-- end list -->

  - [Blitzablieter](http://blitzableiter.recurity.com/) Blitzablieter is
    a project currently run by Recurity Labs and the German government.
    The goal is to prevent malicious SWFs from entering a network
    through normalization and policy enforcement. This project currently
    handles AVM1 code.

<!-- end list -->

  - [Wepawet](http://wepawet.iseclab.org/) Wepawet is a service for
    detecting and analyzing web-based malware. It currently handles
    Flash, JavaScript, and PDF files. It is currently run by University
    of California, Santa Barbara.

<!-- end list -->

  - [SWFRETools](https://github.com/sporst/SWFREtools/) The SWFRETools
    are a collection of tools built for vulnerability analysis of the
    Adobe Flash player and for malware analysis of malicious SWF files.
    The tools are partly written in Java and partly in Python and are
    licensed under the GPL 2.0 license.



## Project Contributors

The Flash Security project is run by [Peleus
Uhley](:User:Puhley "wikilink").

## Project Sponsors

The Flash Security project is sponsored by
[[MindedLogo.PNG](Image: "wikilink")](http://www.mindedsecurity.com)

#### Project Identification

__NOTOC__ <headertabs />


__NOTOC__ <headertabs />

[Category:Inactive_Projects](Category:Inactive_Projects "wikilink")