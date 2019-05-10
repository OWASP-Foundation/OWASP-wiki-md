<table>
<thead>
<tr class="header">
<th><p>width="700" align="center"</p></th>
<th><p><br />
</p></th>
<th><p>width="500" align="center"</p></th>
<th><p><br />
</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>align="right"</p></td>
<td><figure>
<img src="OWASP_Inactive_Banner.jpg" title="OWASP_Inactive_Banner.jpg" alt="OWASP_Inactive_Banner.jpg" width="800" /><figcaption>OWASP_Inactive_Banner.jpg</figcaption>
</figure></td>
<td><p>align="right"</p></td>
<td></td>
</tr>
</tbody>
</table>

#### Main

**Current Version: 0.80 (Public Beta)**

**Sponsor: Foundstone & [SPI
Dynamics](http://64.233.183.104/search?q=cache:3KOC8rvncLQJ:www.spydynamics.com/news/pr/pr30707.html+SPIDynamics+OSG&hl=en&ct=clnk&cd=1&gl=uk&client=firefox-a)
& OWASP Spring of Code 2007**
[OWASP Site Generator's SpoC 007 Progress
Page](SpoC_007_-_OWASP_Site_Generator "wikilink")

## Description

OWASP SiteGenerator allows the creating of dynamic websites based on XML
files and predefined vulnerabilities (some simple, some complex)
covering .Net languages and web development architectures (for example,
navigation: Html, Javascript, Flash, Java, etc...).

## Uses

  - Evaluation of Web Application Security Scanners
  - Evaluation of Web Application Firewalls
  - Developer Training
  - Web Honeypots
  - Web Application hacking contests (or evaluations)
  - Whatever your mind can come up with\!

## Downloads

  - Installer: [SiteGenerator
    Installer](http://downloads.sourceforge.net/owasp/OSG_v0.80.msi?use_mirror=easynews)
    (Version 0.80) - Updated 03/05/2007
  - Source Code:
    [Current_SiteGenerator_Source.zip](http://owasp.cvs.sourceforge.net/*checkout*/owasp/dotnet/SiteGenerator/SiteGenerator.zip)
    (Version 0.80)

## Accessing SVN for SiteGenerator

  - One way is to browse the SVN online by going to the [SiteGenerator
    Source
    Tree](http://owasp-code-central.googlecode.com/svn/trunk/labs/SiteGenerator/)
  - Another way is to configure your SVN client to download the source
    locally.

## Installation and configuration notes

  - Before you install the website portion please confirm the following.
      - There is an application pool that is configured to run under the
        System account
      - A website that is pointed to where you want the Site
        Generatorator web portion to be installed
      - Configure the website to run Asp.Net 2.0
      - Make sure there is an application for that website and have it
        set to the application pool created in the first step
      - Add a IIS wildcard Application Mapping (accessible via Home
        Directory -\> Configuration) to
        C:\\WINDOWS\\Microsoft.NET\\Framework\\v2.0.50727\\aspnet_isapi.dll
        and untick the 'Verify that file exists'
          - Note: On Windows XP the OK button might appear disable. You
            will need to browse to the file and then select the location
            and also put a dot in from of the asterik (i.e. .\*) for the
            OK button to be enabled
      - Make sure Default.htm is one of the files included in the
        default document list (in the 'Documents' tab)
      - Configure the Website's IP Address to be 127.0.0.1, and click on
        the Advanced button to add a new host header mapping
  - Run the Installer
  - Point the website's document root to the install
    dir\\sitegenerator_contentpages and make sure the IIS user has
    correct permissions
  - Click on the SiteGenerator link that was placed on your desktop

If all goes well you now can browse to your localhost and see the
default SiteGenerator's website. If you see a blank page, try
http://\<SITE NAME\>/Default.htm (you might be getting a cached version
of http://\<SITE NAME\>)

Note that the SQL Injection vulnerabilities expect that you have the
latest version of HacmeBank (v2.0) installed in your box.

## Introduction to SiteGenerator

  - This tool has been sponsored by Foundstone, BUT (and it is a big
    but) it is being released under the Owasp .Net Project and an Open
    Source Licence. So Kudos for Foundstone for doing this and I hope
    they get good exposure from it

<!-- end list -->

  - The main objective of the tool is to create dynamic websites based
    on XML files which will 'map' to a database containing hundreds of
    different vulnerabilities (some simple to detect/exploit, some
    harder) covering multiple

languages and web development architectures (for example navigation:
Html, JavaScript, Flash, Java, etc...)

  - There are many ways this tool can be used, here are just a couple
    starting ideas:
      - As a training tool since it allows the creation of multiple
        websites with multiple variations of vulnerabilities
      - As a Web Application Honeypot (since we are able to create
        dynamic ( i.e. false) websites and track / monitor in real-time
        all requests made)
      - As a test ground for newly discovered vulnerabilities types and
        its exploit vectors
      - As a benchmark for Web Security Scanners

<!-- end list -->

  - The Web Security Scanner benchmarking and testing is the most
    obvious short-term application for this tool, but I think that as it
    evolves the others will be proven to be as (if not more) valuable

<!-- end list -->

  - On the Web Security Scanner issue:
      - My main hope is that the Web Security Scanner Companies will see
        this tool as an opportunity and work with the Owasp .Net project
        (and other groups that want to be involved) in a productive and
        constructive way
      - Although in the short term some Web Security Scanners might have
        some bad results (well, at least when compared with what their
        Marketing machine publishes :) in the medium term, as they adapt
        and improve their scanning techniques, everybody will benefit
      - One of the core objectives of the tool (when thinking about
        benchmarking Web Security Scanners) is to be able to create real
        and measurable metrics. For example:
          - Scanner X was able to detect 65% of the vulnerabilities
            where Scanner Y was able to detect 90%
          - Scanner X made 10000 to detect those 65% (over a period of
            16h) where scanner Y made 4000 request (over a period of
            10h)
              - 20% of Scanner X results where false positives, where
                Scanner Y had 50% false positives
              - Scanner X was able to deal with Html and JavaScript
                navigation, Scanner Y was able to deal with Html,
                JavaScript and Flash, and both where NOT able to deal
                with Java based navigation systems
              - Scanner X is not able to go more than 40 levels deep,
                Scanner Y is able to go up at least 100 levels deep (if
                not more)
              - etc, etc, etc
      - There will be two main types of tests that can be done in the
        short term:
          - Provide the links to all different types of vulnerabilities
            existent in the database, and see how many can the scanner
            correctly identify? and
          - When multiple types of website architectures and navigation
            techniques are used, how many vulnerabilities is the scanner
            able to detect?
      - In order to test (and further improve the tool) I want to take
        this opportunity to ask the Web Application Security Scanners
        that subscribe to this list (which I believe all do) to give the
        Owasp .Net project a temporary licence to their product so that
        we can use it during development and during some basic
        benchmarking that we might do (and NO, I will not sign an NDA
        that doesn't allow me to publish the data collected, in fact I
        will not sign ANY NDA with ANY web application security scanner
        company)
      - Note that at the moment I (Dinis) have no plans to do a full
        benchmarking exercise since I don't have the time required, but
        I know of at least one group of experienced security consultants
        which is starting such project (and I will be supporting them).
        If anybody else is interested in doing a similar benchmarking
        project please contact me directly

<!-- end list -->

  - Regarding how the tool works, here is a brief technical description:

There are two main components: A webserver (which can be IIS or a custom
webserver) and a GUI application (written in C\# 2.0). The GUI
Application is responsible for handling all mappings (from the virtual
requests to the actual pages on disk). The two main components talk over
tcp on port 4,000, the GUI application listens for requests from the web
server and then returns an answer to the webserver

The current version is hardcoded to IIS, although in the code there is
support for using a custom .Net webserver. This IIS version uses an
HttpHander to capture all requests and communicate with the GUI
Application (called SiteGeneratorGUI)

The dynamic websites are defined by XML files like this (which are
edited on the GUI Application using the WYSIWYG Altova Authentic Browser
Object (SPS files created via Altova's StyleVision application)):

<?xml version="1.0" encoding="utf-8" ?>

`  `<SiteGenerator name="SiteGenerator Demo" xmlns:ipo="<nowiki>http://www.altova.com/IPO</nowiki>"
    ns="<nowiki>http://www.xmlspy.com/schemas/orgchart</nowiki>" xmlns:xsi="<nowiki>http://www.w3.org/2001/XMLSchema-instance</nowiki>">
`         `<site>
`             `<folder name="">
`                `<file mappedTo="aspx/Default.aspx" name="HelloWorld.aspx" />
`                `<folder name="htm" />
`                `<folder name="aspx">
`                    `<file mappedTo="aspx/pages.htm" name="pages.htm" />
`                    `<file mappedTo="aspx/xss.aspx" name="xss.aspx" />
`                    `<file mappedTo="aspx/SqlInjection_Easy.aspx" name="SqlInjection.aspx" />
`                    `<file mappedTo="aspx/SqlInjection_Hard.aspx" name="SqlInjection2.aspx" />
`                `</folder>
`                `<folder name="flash">
`                     `<file mappedTo="flash/cromas_xml.swf" name="cromas_xml.swf" />
`                     `<file mappedTo="flash/cromas_xml.htm" name="menu.htm" />
`                     `<file mappedTo="/flash/cromas_menu.xml" name="cromas_menu.xml" />
`                `</folder>
`             `</folder>
`        `</site>
`  `</SiteGenerator>

SiteGeneratorGUI.exe and IIS will map the virtual name "HelloWorld.aspx"
to the file on disk "aspx/Default.aspx" . For example:

<http://localhost/HelloWorld.aspx> --\> F:\\Owasp
SiteGenerator\\SiteGenerator_ContentPages\\aspx\\Default.aspx

So to create new websites all you need to do is to create a new XML file

Then to create new vulnerabilities type, all you need to create in an
Aspx page and map it to the xml file

## How To Use SiteGenerator

SiteGenerator contains four different screens that can be used they are
further explained below. In all of the screen shots you will see a
bottom pane this contains all the information that is flowing from the
website to the fat client. Clicking on "Clear Received Data" will clear
out the bottom text area and the information found on the file
transformations log tab.

**Edit / Create Dynamic Websites Tab**

![Image:sg_maintain_websites_ss.jpg](sg_maintain_websites_ss.jpg
"Image:sg_maintain_websites_ss.jpg")

This area allows users to create a basic website that could be used. You
can also remove a website and modify it using the word like widget.

Select the root path for the site "/" you can choose the default page
this can be another page that you have previously mapped or a specific
path to a file.

*' File Transformations Log*'

![Image:sg_file_transformations_tab.jpg](sg_file_transformations_tab.jpg
"Image:sg_file_transformations_tab.jpg")

This tab allows a user to see how the transformations are working. For
example you could make sure that the new mapping for f00.aspx actually
was converted to /test123/test.aspx.

**Web Browser Tab**

![Image:sg_webrowser_tab_ss.jpg](sg_webrowser_tab_ss.jpg
"Image:sg_webrowser_tab_ss.jpg")

This tab will allow for a user to browse to the generated website
instead of using a normal browser.

**Website Creator Tab**

![Image:Sg_website_creator_tab_ss.jpg](Sg_website_creator_tab_ss.jpg
"Image:Sg_website_creator_tab_ss.jpg")

This tab allows a user to initially create the files for a given
website.

## Development Notes

[OSG_Dev_Notes](OSG_Dev_Notes "wikilink")

#### Project Identification

__NOTOC__ <headertabs />

[link not working](Category:FIXME "wikilink") [Category:OWASP .NET
Project](Category:OWASP_.NET_Project "wikilink") [SiteGenerator
Project](Category:OWASP_Project "wikilink")