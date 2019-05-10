## current O2 support

  - Dedicated O2 Module
    [O2_Scanner_MsCatNet](http://deploy.o2-ounceopen.com/O2_Scanner_MsCatNet/)
    with support for
      - finding target dlls (recursive search on local directories)
      - triggering scans
      - converting CAT.NET Results into O2's Findings schema

## description

(from [CAT.NET
download](https://connect.microsoft.com/Downloads/DownloadDetails.aspx?SiteID=734&DownloadID=23328&wa=wsignin1.0)
page)

''"...Code Analysis Tool for .NET is a static analysis tool to detect
common software security vulnerabilities. CAT.NET 2.0 has been
re-written from the ground up implementing the original tainted analysis
algorithm developed by Ben Livshits but using the Phoenix compiler
infrastructure to provide a solid and scalable core data flow security
analysis engine. CAT.NET 2.0 will initially ship around February as a
Visual Studio 2010 Power Tool, only available to customers who have a
licensed copy of Visual Studio 2010 and then as an integrated part of
the Visual Studio product in late 2010. ..." ''

## download

  - [CAT.NET 2.0 CTP (current
    version)](https://connect.microsoft.com/Downloads/DownloadDetails.aspx?SiteID=734&DownloadID=23328)
    (requires registration with Microsoft) , .NET Framework 4.0
  - [CAT.NET v1 CTP - 32 bit (old
    version)](http://www.microsoft.com/downloads/details.aspx?FamilyId=0178e2ef-9da8-445e-9348-c93f24cc9f9d&displaylang=en)
    , .NET Framework 2.0
  - [O2 Scanner -
    MsCatNet](http://deploy.o2-ounceopen.com/O2_Scanner_MsCatNet/)

## other relevant links

  - [Microsoft Information Security Tools team Connect
    site](https://connect.microsoft.com/site/sitehome.aspx?SiteID=734)
  - [Microsoft IT’s Information Security (InfoSec)
    group](http://msdn.microsoft.com/en-us/security/dd547422.aspx)
  - [OWASP .NET Project](:Category:OWASP_.NET_Project "wikilink")

## related blog posts

  - [InfoSec A\&P Suite: How to Install &
    Configure](http://blogs.msdn.com/ace_team/archive/2009/11/30/infosec-a-p-suite-how-to-install-configure-the-tools.aspx)
  - [New Tool In My Pouch: CAT.NET And
    Anti-XSS 3.0](http://it.toolbox.com/blogs/programming-life/new-tool-in-my-pouch-catnet-and-antixss-30--35613)
  - [InfoSec Assessment & Protection (A\&P) Suite
    Released](http://blogs.msdn.com/infosec/archive/2009/11/16/infosec-assessment-protection-a-p-suite-released.aspx)
  - [Security tools from
    Microsoft](http://teamfoundationserver.wordpress.com/2009/11/25/security-tools-from-microsoft/)
    (Tobias had some issues running the latest version)
  - from main CAT.NET Blog
      - [The CAT.NET 2.0 Configuration Analysis
        Engine](http://blogs.msdn.com/securitytools/archive/2009/12/01/the-cat-net-2-0-configuration-analysis-engine.aspx)
      - [How to Run CAT.NET 2.0
        CTP](http://blogs.msdn.com/securitytools/archive/2009/11/12/how-to-run-cat-net-2-0-ctp.aspx)
      - [Some New Software Security Tools for Web Developers – (CTP
        Releases](http://blogs.msdn.com/securitytools/archive/2009/11/11/some-new-software-security-tools-for-web-developers-ctp-releases.aspx)
      - [Implementation Ideas for the CAT.NET 2.0 Tainted Variable
        Analysis
        Algorithm](http://blogs.msdn.com/securitytools/archive/2009/07/08/implementation-ideas-for-the-cat-net-2-0-tainted-variable-analysis-algorithm.aspx)
      - [New Build of CAT.NET (Version - 1.1.1.9) – Please
        Upgrade](http://blogs.msdn.com/securitytools/archive/2009/06/27/new-build-of-cat-net-version-1-1-1-9-please-upgrade.aspx)
      - [Running CAT.NET as a Custom MSBuild
        Task](http://blogs.msdn.com/securitytools/archive/2009/06/01/running-cat-net-as-a-custom-msbuild-task.aspx)
      - [CAT.NET – How Big Do Your Project Files Grow
        ?](http://blogs.msdn.com/securitytools/archive/2009/05/20/cat-net-how-big-do-your-project-files-grow.aspx)
  - FxCop
      - [FxCop &
        StyleCop](http://burgerminds.wordpress.com/2009/06/28/fxcop-stylecop/)
  - VS2010
      - [Code Analysis in Visual
        Studio 2010](http://rcosic.wordpress.com/2009/04/06/code-analysis-in-visual-studio-2010/)

## videos

  - [Architecture Behind
    CAT.NET](http://channel9.msdn.com/posts/Jossie/Architecture-behind-CATNET/)
  - [Assessment and Protection
    Suite](http://channel9.msdn.com/posts/Jossie/Assessment-and-Protection-Suite/)
    -*"... Anil Revuru (RV) and Mark Curphey, from Microsoft Information
    Security, introduce what would be in the future a suite of tools
    that will help you assess your code as well as protect it. This is
    called the Assessment & Protection (A\&P) Suite and it includes the
    following tools: Web Protection Library (WPL) – which includes
    Anti-XSS, SRE, mitigation of SQL Injection, CSRF among others
    CAT.NET Web Application Configuration Analyzer (WACA) and room for
    more future add-ons ..."*
  - [MSDN Webcast: Managing Cross-Site Scripting Using CAT.NET and
    AntiXSS
    (Level 200)](http://msevents.microsoft.com/cui/WebCastEventDetails.aspx?culture=en-US&EventID=1032398772&CountryCode=US)
  - WACA & WPL
      - [Using Web Application Configuration Analyzer (WACA) - CTP
        Version](http://channel9.msdn.com/posts/Jossie/Web-Application-Configuration-Analizer-WACA)
      - [Web Application Configuration Analyzer
        (WACA)](http://channel9.msdn.com/posts/Jossie/Web-Application-Configuration-Analyzer-WACA)
      - [Enhanced Web Protection
        Library](http://channel9.msdn.com/posts/Jossie/Enhanced-Web-Protection-Library/)
      - [Using the Web Protection Library (WPL) - CTP
        Version](http://channel9.msdn.com/posts/Jossie/Using-the-Web-Protection-Library-WPL-CTP-Version/)