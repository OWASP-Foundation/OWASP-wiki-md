The following list represents the current O2 supported technologies and
how they can be consumed by multiple O2 Modules.

Note that adding support for a new technology , tool or framework is
usually quite an easy task (since there are numerous O2 APIs that can be
easily reused or modified).

If you have a particular need please send a request to the [O2 mailing
list](https://lists.owasp.org/mailman/listinfo/owasp-o2-platform)

### Findings Creation

  - **Open Source or Free Tools**
      - O2 Tool CSharpScripts -
        [download](http://deploy.o2-ounceopen.com/O2_Tool_CSharpScripts)
      - [Microsoft
        CAT.NET](OWASP_O2_Platform/Microsoft/CAT.NET "wikilink") v1.0
        (not the latest release)
      - FindBugs -
        [download](http://findbugs.sourceforge.net/downloads.html) ,
        [see XSD and O2 object
        model](OWASP_O2_Platform/Docs/O2Findings_Schema/O2AssesmentLoad_FindBugs "wikilink")
      - OWASP CodeCrawler -
        [download](:Category:OWASP_Code_Crawler "wikilink") , [see XSD
        and O2 object
        model](OWASP_O2_Platform/Docs/O2Findings_Schema/O2AssesmentLoad_CodeCrawler "wikilink")
      - WebScarab logs (original version, not the NG one) -
        [download](:Category:OWASP_WebScarab_Project#Download "wikilink")
        , [see XSD and O2 object
        model](OWASP_O2_Platform/Docs/O2Findings_Schema/O2AssesmentLoad_WebScarab "wikilink")

<!-- end list -->

  - **Require Paid-for license**
      - Ounce 6.x (now called IBM AppScan Source Edition) - [see XSD and
        O2 object
        mode](OWASP_O2_Platform/Docs/O2Findings_Schema/O2AssessmentLoad_OunceV6 "wikilink")
      - Ounce 7.x (now called IBM AppScan Source Edition) - [see XSD and
        O2 object
        mode](OWASP_O2_Platform/Docs/O2Findings_Schema/O2AssessmentLoad_OunceV6_1 "wikilink")
      - IBM AppScan developer Edition - [see XSD and O2 object
        mode](OWASP_O2_Platform/Docs/O2Findings_Schema/O2AssesmentLoad_AppScanDE "wikilink")
      - Fortify (very basic support) - [see XSD and O2 object
        mode](OWASP_O2_Platform/Docs/O2Findings_Schema/O2AssesmentLoad_Fortify "wikilink")

### Cir Creation

  - **Open Source or Free Tools**
      - Using O2 Modules
          - .NET Framework Assemblies (\*.dll , \*.exe)
          - Java class files (\*.class, \*.jar. \*.war)

<!-- end list -->

  - **Requiring Paid-for license**
      - Ounce 6.x (now called IBM AppScan Source Edition)
          - .NET, Java, C/C++, VB6, ASP Classic and (under internal beta
            at the moment) PHP

### Trigger Scans

  - **Open Source or Free Tools**
      - CAT.NET v1.0 (have not tested the latest release)
  - **Requiring Paid-for license**
      - Ounce 6.x (now called IBM AppScan Source Edition)

### Framework Support

  - [Spring Framework
    (MVC)](OWASP_O2_Platform/Spring_Framework/MVC "wikilink")
  - Struts