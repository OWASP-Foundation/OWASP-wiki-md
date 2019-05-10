This page contains research notes on Microsoft's SharePoint MOSS and WSS

## Resources

#### Microsoft resources

  - [Security Architecture for SharePoint Products and
    Technologies](http://office.microsoft.com/download/afile.aspx?AssetID=AM102437421033)
    (Word Doc)
  - [SharePoint Community Portal](http://sharepoint.microsoft.com)
  - [Downloadable book: Security for Office SharePoint
    Server 2007](http://technet.microsoft.com/en-us/library/cc262619.aspx)
    - [link to 277 page Doc
    file](http://go.microsoft.com/fwlink/?LinkID=94375)
  - [SharePoint End User
    Security](http://blogs.msdn.com/arpans/archive/2008/05/09/sharepoint-end-user-security.aspx)

#### Other Resources and Documentation

  - [SharePoint Security
    Concepts](http://www.finalcandidate.com/en/tandp/Pages/SharePointSecurityConcepts.aspx)
    - contains a number of other links to more material
  - [SharePoint Security Best
    Practices](http://blogs.gartner.com/neil_macdonald/2009/02/25/sharepoint-security-best-practices/)
    - $995 Gartner report
  - [Microsoft Office SharePoint Server 2007 Security
    Model](http://sharepointmagazine.net/technical/administration/microsoft-office-sharepoint-server-2007-security-model)
  - [SharePoint Security Concerns Simply a Lack of
    Governance?](http://www.cmswire.com/cms/enterprise-cms/sharepoint-security-concerns-simply-a-lack-of-governance-003551.php)
  - [Governance Key for SharePoint
    Implementations](http://www.cmswire.com/cms/enterprise-cms/governance-key-for-sharepoint-implementations-003123.php)
  - [SearchSecurity – Securing SharePoint: SharePoint security best
    practices](http://www.bishopfox.com/files/articles/2012/Information%20Security%20Magazine%20JulyAug2012-SharePoint.pdf)
    - Information Security Magazine July/Aug2012 - Volume 14 - Locking
    Down Sharepoint - Businesses love Microsoft’s collaboration software
    but can forget to secure it.

#### Presentations

  - Bishop Fox - HackCon 2011 - Oslo, Norway - February 16, 2011 :
    [SharePoint Security: Advanced SharePoint Security Tips and
    Tools](http://www.bishopfox.com/files/slides/2011/HackCon%202011%20-%20SharePoint%20Security%20-%20Feb2011.pdf)
  - OWASP Houston Chapter - August 12, 2009 : [SharePoint Auditing and
    Penetration
    Testing](http://owasp.icrew.org/downloads/OWASP_ShohnTrojacek.pdf)
    Presentation by: Shohn Trojacek
  - from Denim group:
      - [Securing SharePoint (PDF
        Format)](http://www.denimgroup.com/media/pdfs/DenimGroup_SecuringSharePoint_TASSCCTEC2009_20090326.pdf)
        - TASSCC Technology Education Conference in Austin, March 26,
        2009
      - [Securing Sharepoint (PDF
        Format)](http://www.denimgroup.com/media/pdfs/DenimGroup_SecuringSharePoint_TRISC_20090324.pdf)
        - Texas Regional Infrastructure Security Conference (TRISC) in
        Austin, March 24, 2009
      - [A Primer to SharePoint
        Security](http://sp.meetdux.com/archive/2009/07/08/a-primer-to-sharepoint-security.aspx)
        - video

#### Other interesting resources

  - [MOSS Security jobs (in
    Australia)](http://www.indeed.com.au/jobs?q=Moss+Security&l=)
  - [Articles on CMSWire about
    SharePoint](http://www.cmswire.com/news/topic/sharepoint)

#### Other Blogs and Articles

  - [Microsoft SharePoint: A Weak Link In Enterprise
    Security?](http://www.darkreading.com/security/app-security/showArticle.jhtml?articleID=212903345)
    - Dark Reading

#### Security related technical articles

  - [How to Programmatically Disable Code Access
    Security](http://www.sharepointsecurity.com/sharepoint/sharepoint-security/how-to-programmatically-disable-code-access-security/)

## Published Security issues

### SharePoint related vulnerabilities and its status

  - {Note: Add MSRC case}
  - <http://milw0rm.com/exploits/8704> &
    <http://milw0rm.com/sploits/2009-IIS-Advisory.pdf>

## MOSS Security related WebParts, Tools & services

#### Open Source

  - From CodePlex (see more on this search for [SharePoint
    Security](http://www.codeplex.com/site/search?ProjectSearchText=Sharepoint%20Security)
      - [SharePoint Security
        Templates](http://securitytemplates.codeplex.com/) (CodePlex)
      - [SharePoint Security Configuration
        Feature](http://spsecurity.codeplex.com/)
      - [Sharepoint Access Checker Web
        Part](http://accesschecker.codeplex.com)
      - [Site Security Management
        Utility](http://sitesecuritymgmt.codeplex.com/)
      - [CryptoCollaboration For
        SharePoint](http://cryptocollaboration.codeplex.com/)

#### Commercially Supported

  - [ARB Security Solutions
    (www.sharepointsecurity.com)](http://www.sharepointsecurity.com)
  - [AbsoluteProof for MS
    SharePoint](http://www.surety.com/Offerings/AbsoluteProof/For-MS-SharePoint.aspx)
    - related article [Surety Releases AbsoluteProof for
    SharePoint](http://www.cmswire.com/cms/enterprise-cms/surety-releases-absoluteproof-for-sharepoint-002471.php)
  - [Sharepoint case study (marketing
    doc)](http://www.avepoint.com/assets/pdf/Social_Security_Administration_Case_Study.pdf)

## Dangerous MOSS APIs

Map the security implications of MOSS APIs, for example:

  - which APIs (if badly used)are vulnerable to: XSS, CSRF, SQL
    Injection
  - configuration settings that have security implications

## SharePoint Hacking

#### SharePoint Hacking Tools

  - [SharePoint Enumerator | Professionally
    Evil](http://extensions.professionallyevil.com/beef.php) - This is a
    collection of 4 modules that help enumerate the SharePoint server
    the victim is connected to.
  - [Sparty](http://sparty.secniche.org/) - MS Sharepoint and Frontpage
    Auditing Tool
  - [SPScan](https://github.com/toddsiegel/spscan) - SharePoint scanner
    and fingerprinter based on WPScan
  - [McAfee Network Discovery for Microsoft
    SharePoint](http://www.mcafee.com/us/downloads/free-tools/sharepoint-discovery.aspx)
  - [Bishop Fox - SharePoint Hacking Diggity
    Project](http://www.bishopfox.com/resources/tools/sharepoint-hacking-diggity/)
    - SharePoint hacking tools project page. Currently includes such
    hacking tools as:
      - [SharePoint – Google and Bing Diggity Dictionary
        Files](http://www.bishopfox.com/resources/tools/sharepoint-hacking-diggity/attack-tools/#google-and-bing-hacking-dictionary-files)
        - New GoogleDiggity input dictionary file containing 121 queries
        that allow users to uncover SharePoint specific vulnerabilities
        exposed via the Google search engine. This dictionary helps
        assessors locate exposures of common SharePoint administrative
        pages, web services, and site galleries that an organization
        typically would not want to be made available to the public, let
        alone indexed by Google. Recently, we’ve also created a Bing
        hacking dictionary (124 Bing queries) that can be imported into
        BingDiggity and used to identify SharePoint exposures as well.
      - [SharePoint Hacking Alerts for Google and
        Bing](http://www.bishopfox.com/resources/tools/sharepoint-hacking-diggity/attack-tools/#sharepoint-hacking-alerts-for-google-and-bing)
        - SharePoint Hacking Alerts provide real-time vulnerability
        updates from both the Google and Bing search engines. These
        convenient RSS feeds help locate exposures of common SharePoint
        administrative pages, web services, and site galleries that an
        organization typically would not want to be made available to
        the public, let alone indexed by Google and Bing. [Google
        Alerts](http://www.google.com/alerts) have been created for all
        SharePoint related search strings, which generate a new alert
        each time newly indexed pages by Google match one of those
        regular expressions. Microsoft Bing’s \&format=rss directive was
        used to turn Bing searches into RSS feeds.
      - [SharePointURLBrute](http://www.bishopfox.com/resources/tools/sharepoint-hacking-diggity/attack-tools/#sharepointurlbrute)
        - SharePointURLBrute is a new SharePoint hacking utility
        developed to help assessors quickly test user access to 101
        common SharePoint administrative pages (e.g. “Add Users” page
        -\> /_layouts/aclinv.aspx) by automating forceful browsing
        attacks.
      - [SharePoint
        UserDispEnum](http://www.bishopfox.com/resources/tools/sharepoint-hacking-diggity/attack-tools/#sharepoint-userdispenum)
        - UserDispEnum is a new SharePoint user enumeration tool that
        exploits insecure access controls to the
        /_layouts/UserDisp.aspx?ID=1 page. This utility cycles through
        the integer ID values from 1 onward to identify valid users,
        account names, and other related profile information that can be
        easily extracted from the SharePoint user profiles. For real,
        live examples of SharePoint site deployments insecurely exposing
        this functionality to anonymous users on the Internet, see
        Google results of:
        “http://www.google.com/\#q=inurl:”/_layouts/userdisp.aspx”.
        Users can leverage [Bishop Fox’s GoogleDiggity hacking
        tools](http://www.bishopfox.com/resources/tools/google-hacking-diggity/)
        to identify these exposures within their own organization, and
        then employ the UserDispEnum tool to exploit them during
        penetration tests.
      - [SharePoint DLP
        Tools](http://www.bishopfox.com/resources/tools/sharepoint-hacking-diggity/attack-tools/#sharepoint-dlp-tools)
        - COMING SOON – Bishop Fox's data loss prevention (DLP) tools
        for Microsoft SharePoint. SharePoint DLP Tools utilize
        administrative web services to help automate the searching of
        SharePoint files and lists for SSNs, credit card numbers,
        passwords, and other common information disclosures.

#### SharePoint Hacking Presentations

  - **2008**
      - [hak5 - Episode 407 - Toorcon 2008: Robin Wood, Dan
        Griffin](http://www.youtube.com/watch?v=DYudvh9cfZM) - see 11:10
        minute mark in video for interview with Dan Griffin about
        SharePoint Hacking.
  - **2012**
      - [Bishop Fox - SharePoint Hacking Diggity Project -
        Presentations](http://www.bishopfox.com/resources/tools/sharepoint-hacking-diggity/presentation-slides/):
          - OWASP L.A. 2012 - Los Angeles, CA - February 22, 2012 :
            [SharePoint Hacking: Advanced SharePoint Security Tips and
            Tools](http://www.bishopfox.com/files/slides/2012/OWASP%20LA%20-%20SharePoint%20Hacking%20-%2022Feb2012.pdf)
  - **2013**
      - [TMI: Assessing and Exploiting SharePoint at
        DerbyCon 3.0](http://www.youtube.com/watch?feature=player_embedded&v=AAObW2fcB_s)
      - [Sparty - Blackhat
        USA 2013](https://media.blackhat.com/us-13/Arsenal/us-13-Sood-Sparty-Slides.pdf)
        Sparty : A Frontpage and Sharepoint Auditing Tool

## WebParts Security

  - Security ratings & mappings of MOSS Deployed Web Parts
  - Security ratings & mappings of 3rd Part Web Parts