## What is FxCop?

FxCop is a free code analysis tool developed by Microsoft, use to
analyze MSIL (Microsoft Intermediate Language) generated from any
managed language (including C\# and VB.NET).

FxCop is a standalone .NET 2.0 application, downloadable from the
locations referenced below. A modified version of the FxCop codebase is
integrated into Microsoft Visual Studio 2005 and 2008. While the
rulebase for each is mostly the same, there are notable differences
between the two (see the Rules comparison spreadsheet
[below](FxCop#References "wikilink")), and the compiled format for
custom rules is different; thus, one cannot generally develop custom
rules that can be used natively in both contexts.

## Resources

### Tool, Documentation and Community

  - Download - [FxCop
    v1.36](http://www.microsoft.com/downloads/details.aspx?FamilyID=9aeaa970-f281-4fb0-aba1-d59d7ed09772)
  - Download - [FxCop
    v1.35](http://code.msdn.microsoft.com/codeanalysis)
  - Download - [FxCop v1.32 (*via
    archive.org*)](http://web.archive.org/web/*/http://www.gotdotnet.com/team/fxcop/FxCopInstall1.32.EXE)
    - only necessary if you wish to perform analysis of code written in
    Visual Studio 2003 or earlier.
  - Download - [Rules comparison
    spreadsheet](http://code.msdn.microsoft.com/codeanalysis/Release/ProjectReleases.aspx?ReleaseId=556)
    - documenting the rules differences between those shipped with FxCop
    and the Visual Studio Code Analysis feature
  - Documentation -
    [FxCop](http://msdn.microsoft.com/library/bb429476.aspx) - MSDN
    documentation for FxCop
  - Forum - [Visual Studio Code Analysis and Code
    Metrics](http://forums.microsoft.com/MSDN/ShowForum.aspx?ForumID=98&SiteID=1)
    - MSDN forum to discuss issues and ideas regarding FxCop and the
    Visual Studio Code Analysis features
  - Wikipedia - [FxCop article](http://en.wikipedia.org/wiki/Fxcop)
  - Blog - [Microsoft Code Analysis Team
    blog](http://blogs.msdn.com/fxcop/) - addresses both the standalone
    FxCop tool as well as the Visual Studio Code Analysis feature
  - Blog - [Dave's Box](http://davesbox.com/) - personal blog written by
    a member of Microsoft's Code Analysis team
  - Article - [Run FxCop from
    Code](http://blogs.microsoft.co.il/blogs/sasha/archive/2007/02/10/Run-FxCop-from-Code.aspx)
  - Article - [Writing Real Unit Tests for your Custom FxCop
    Rules](http://weblogs.asp.net/rosherove/archive/2007/02/24/writing-real-unit-tests-for-your-custom-fxcop-rules.aspx)
  - Article - [FxCop and Code Analysis: Writing Your Own Custom
    Rules](http://www.binarycoder.net/fxcop/) - the definitive tutorial
    by Jason Kresowaty

### Custom Rules and other third-party Enhancements

  - [JSL FxCop (CodePlex)](http://www.codeplex.com/JSLFxCop) -
    open-source utility to help build custom FxCop rules, as well as
    many custom rules.
  - [Community Static Analysis Rules
    (CodePlex)](http://www.codeplex.com/CSAR) - "a community-based
    project for creating a set of static analysis rules to extend those
    provided by the FxCop team."
  - [TeachNaGeamhradh FxCop Rules
    (SourceForge)](http://sourceforge.net/projects/tngfxcoprules/) - "A
    growing collection of rules and experimentation with FxCop to
    provide a comprehensive list of rules that are useful against the
    .Net assemblies."
  - [Lephone FxCop Rules
    (CodePlex)](http://www.codeplex.com/LephoneFxCopRules) - a small set
    of custom rules
  - [CustomFxCop (CodePlex)](http://code.msdn.microsoft.com/InfoXchange)
    - implements "...new rule sets to check variable naming conventions
    in a project. This will really help projects to automate their code
    review process."
  - [findbugs-FxCop (Google
    Code)](http://code.google.com/p/findbugs-fxcop/) - "This project
    will produce custom rules for FxCop, that will look for coding
    mistakes similar to those found by FindBugs, such as infinite
    recursive loops and ignored return values."
  - [Custom FxCop rule : checking for IDataReader in method parameters
    (Archive.org)](http://web.archive.org/web/20040724165715/http://tatochip.com/archive/2004/07/19/2678.aspx)
    - a single FxCop rule in source code form
  - [Custom FxCop rule: demonstrates extracting literal arguments from
    method call
    (Archive.org)](http://web.archive.org/web/20060313113313/www.gotdotnet.com/Community/UserSamples/Details.aspx?SampleGuid=14DEFFCB-9C2B-4C38-BEEC-AB860084E372)
    - a single FxCop rule in source code form
  - [Custom FxCop rules: No Numerals in Variable Names, Naming Constants
    (Archive.org)](http://web.archive.org/web/20070826010853/www.gotdotnet.com/Community/UserSamples/Details.aspx?SampleGuid=B397F7AD-4811-45DE-9A6A-33F818994CB1)
    - two FxCop rules in source code form
  - [Custom FxCop 1.32 rule: detects calls to specific API
    (Archive.org)](http://web.archive.org/web/20060427042023/www.gotdotnet.com/Community/UserSamples/Details.aspx?SampleGuid=01D9F014-5F73-4D66-8E74-C658944180DD)
    - a single FxCop 1.32 rule in source code form
  - [Custom FxCop 1.32 rule: detects calls to specific API
    (Archive.org)](http://web.archive.org/web/20060313113430/www.gotdotnet.com/Community/UserSamples/Details.aspx?SampleGuid=0BE37E51-6A0E-4E8E-A61F-84A388000859)
    - a single FxCop 1.32 rule in source code form
  - [Custom FxCop 1.32 rules
    (Archive.org)](http://web.archive.org/web/20060313113604/www.gotdotnet.com/Community/UserSamples/Details.aspx?SampleGuid=BFBB8D82-678A-4E58-A305-5B00FDE900DB)
    - some FxCop 1.32 rules in source code form

<!-- end list -->

  - [Custom FxCop rules "My FxCop rules"
    (Archive.org)](http://web.archive.org/web/20060313113604/http://www.gotdotnet.com/Community/UserSamples/Download.aspx?SampleGuid=BFBB8D82-678A-4E58-A305-5B00FDE900DB)
    - some FxCop rules \[*broken link*\]
  - [TechEd 2004 presentation & samples by Michael Murray
    (Archive.org)](http://web.archive.org/web/20060313113924/http://www.gotdotnet.com/Community/UserSamples/Download.aspx?SampleGuid=18919BD2-6502-43B3-BF3D-35C5E57DA06D)
    - "Code Correctness with FxCop 1.30" \[*broken link*\]

<!-- end list -->

  - [FxDeputy (SourceForge)](http://sourceforge.net/projects/fxdeputy/)
    - "This project is of use to anyone writing rules for the FxCop
    checker for .NET. This provides a framework that will allow you to
    tag tests with attributes that will provide you with control of what
    tests are run against your rules."
  - [FxCopUnit (ASP.NET
    blogs)](http://weblogs.asp.net/rosherove/archive/2007/02/24/introducing-fxcopunit-a-framework-for-integrated-fxcop-rule-testing.aspx)
    - "A framework for integrated FxCop rule testing"
  - [FxCop Delta (CodePlex)](http://www.codeplex.com/fxcopdelta) - "a
    custom check-in policy for Visual Studio Team System that runs FxCop
    rules before performing a check-in."
  - [FinRad Statistics Collector for FxCop
    (CodePlex)](http://www.codeplex.com/FinRadFxCopStats) - "...intended
    to help development teams to track the progress of an FxCop backlog
    cleanup effort."
  - [FxCopReportAll.xsl
    (Archive.org)](http://web.archive.org/web/20070825153755/www.gotdotnet.com/Community/UserSamples/Details.aspx?SampleGuid=BCFB8E54-989A-4464-BDB0-3C3B9B3F1346)
    - GotDotNet sample "style sheet for report that shows all Active and
    Excluded Messages."
  - *([CustomRules in
    FxCop](http://code.msdn.microsoft.com/CustomRulesinFxcop) - **DEAD
    CodePlex project**)*

### Similar Tools for .NET code analysis

  - [Agent Smith Plugin](http://code.google.com/p/agentsmithplugin/) -
    "Agent Smith is C\# code style validation plugin for ReSharper
    (Visual Studio plugin)."
  - [Agent Johnson Plugin](http://code.google.com/p/agentjohnsonplugin/)
    - "Plugin for JetBrains ReSharper", performing limited code
    analysis, refactoring and fixups on C\# code.
  - [Smokey (Google Code)](http://code.google.com/p/smokey/) - tool
    similar to FxCop for analysing managed code; has 220 separate rules.
  - [Phoenix](http://research.microsoft.com/phoenix/) - an SDK from MS
    Research labelled as "...the software optimization and analysis
    framework that is the basis for all future Microsoft® compiler
    technologies. The Phoenix framework is an extensible system that can
    be adapted to read and write binaries and Microsoft Intermediate
    Language assemblies and represent the input files in an Intermediate
    Representation, which can be analyzed and manipulated by
    applications by using the Phoenix API."
  - [Gendarme](http://www.mono-project.com/Gendarme) - "Gendarme is a
    extensible rule-based tool to find problems in .NET applications and
    libraries. Gendarme inspects programs and libraries that contain
    code in ECMA CIL format (Mono and .NET) and looks for common
    problems with the code, problems that compiler do not typically
    check or have not historically checked."
  - [md-codeanalysis](http://code.google.com/p/md-codeanalysis/) -
    "MonoDevelop.CodeAnalysis is an addin that integrates both Gendarme
    and Smokey into MonoDevelop."