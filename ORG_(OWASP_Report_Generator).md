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

The ORG (OWASP Report Generator) is a tool for Security Consultants that
supports the documentation and reporting of security vulnerabilities
discovered during security audits.

Currently [**Mark Roxberry**](:User:Mroxberr "wikilink") leads this
project. Formerly the project leader was [Dinis
Cruz](User:Dinis.cruz "wikilink") with strong contributions from [Mike
de Libero](User:medelibero "wikilink"). Mike was sponsored under an
OWASP Autumn of Code 2006 sponsorship to work on ORG.

## Downloads

The latest release of ORG's installer can be found at (updated on
1/15/2007) - Please note that the installer will not work on Windows x64
bit architecutre (you have to use the source code from the zip file
below - . [Report Generator
Installer](http://sourceforge.net/project/downloading.php?group_id=64424&use_mirror=osdn&filename=ORG_v0.88.msi)

The source code for latest stable version can be downloaded from here
(updated on 11/1/2006): [Report Generator
Source](http://prdownloads.sourceforge.net/owasp/ReportGenerator.zip)

This project is in active development and the latest version can be
obtained from [Google
SVN](http://owasp-code-central.googlecode.com/svn/trunk/labs/ReportGenerator)

**Instructions for using the zip file**

1\) Unzip the files

2\) Run regAuthenticPlugin.bat to register the AuthenticPlugin

3\) Open the solution in VS.Net 2k5. You can use any version of VS but
the primary version used for development is the express edition.

4\) More than likely you need to modify the references area to use the
local files for \[IxInterop|AxInterop\].XMLSPYPLUGIN.

5\) For Windows 64bit, do the following: In the project properties,
select "Build Events" then in Post-build event command line add the
following lines:

call "$(DevEnvDir)..\\tools\\vsvars32.bat"

editbin.exe /NXCOMPAT:NO "$(TargetPath)"

6\) Then try and compile and you should be good to go. If not contact
Mike and we will work with you to get it all straightened out and so we
can adjust this process.

## ORG Development

The current version under development is v0.86 and you can see the
change log here: [ORG (Owasp Report Generator) - Change
Log](ORG_\(Owasp_Report_Generator\)_-_Change_Log "wikilink")

The current Todo is here: [ORG (Owasp Report Generator) - To
Do](ORG_\(Owasp_Report_Generator\)_-_To_Do "wikilink")

## Getting setup for an assessment

**Step 1)** Create a profile for you to use on your computer. You can do
this on the first screen that will be encountered when running ORG.

![Image:Profile_ss.jpg](Profile_ss.jpg "Image:Profile_ss.jpg")

Once the information has been inputted click on “Start Pen Test
Reporter” and you are ready to start adding new projects.

**Step 2)** The next step is to create a project. With the “Current and
Archived Projects” window open make sure that the project metadata tab
is selected. From there in the lower left hand corner you will see an
area to type in a new project and then click “Add”. You will then see a
window like the one below.

![Image:Project_setup_ss.jpg](Project_setup_ss.jpg
"Image:Project_setup_ss.jpg")

You can now type in the pertinent information about your project. After
that you are ready to identify your targets and start attacking (i.e.
the fun part\!).

**Step 3)** Next click on the targets tab, this will allow you to define
the targets for your assessment. Below is a screen shot of an example of
a target during an assessment.

![Image:Org_target_ss.jpg](Org_target_ss.jpg
"Image:Org_target_ss.jpg")

The above area gives you the logistics of the target things like name,
IP(s), the type of target and common dns names. The bottom area allows
you to put files related to the target.

You can also import in targets from an NMap scan if you use the xml
output file option. To do import targets click the “Import Targets”
button and select the saved scan.

**Step 4)** After defining the attack targets you can specify the
individual tasks you wish to perform on the targets. A screen like the
one below should be shown.

![Image:Org_target_tasks_ss.jpg](Org_target_tasks_ss.jpg
"Image:Org_target_tasks_ss.jpg")

Using this screen you can manage the tasks that need to be done for an
assessment, things like information gathering, auditing of source code
and other tasks that are normally done during a security audit. You can
specify the state of each task with the drop down in the status column.

We now have all the background information but we need a way to let our
customers know what we have found that is where the findings tab comes
into play.

## Recording assessment findings

During an assessment you can record all your findings using the findings
tab in the projects form. All findings must be associated to a target.
An example findings window is below. These findings will later be added
to reports that you will give to your customers.

![Image:Org_findings_ss.jpg](Org_findings_ss.jpg
"Image:Org_findings_ss.jpg")

You can add screenshots to the additional details area of the findings
screen as well. To create findings use the “Add Finding” area. This will
give you a blank slate and initially use the simple mode.

You can change the template for the editor by using the drop down
labeled “Editor Template To Use”. There are two other options besides
simple mode they are: Authentic – All Fields Mode and Windows Explorer.
The all fields mode allows you to specify more detailed information.
While, the windows explorer mode allows you to add other artifacts
related to this finding, like code excerpts, PoC code, etc…

After we are done finding all the holes in our targets we need to report
them to our customers.

## Reporting Our Findings

**Step 1)** Click on the “Report Contents” tab and fill out the
information there. This will be later used for the executive summary and
other reports that need to be ran. Below is an example screen of the
report contents filled out.

![Image:Org_report_contents_tab_ss.jpg](Org_report_contents_tab_ss.jpg
"Image:Org_report_contents_tab_ss.jpg")

Click on ”Save Report Contents” and we are ready for the next step
generating a report.

**Step 2)** The first thing to do is click on the “Report Pdf” tab.
Select the xslt you wish to use for the report then select “FOP” for
what you want to create the report with. Then click on “Create report
files using”. After clicking on the button a small PDF reader will show
up on the form. You can then save the report to wherever you wish. An
example screen shot is below.

![Image:Org_pdf_report_ss.jpg](Org_pdf_report_ss.jpg
"Image:Org_pdf_report_ss.jpg")

The other way to create reports is by click on the reports button at the
very top. You will see a screen like the one below.

![Image:Org_reports_ss.jpg](Org_reports_ss.jpg
"Image:Org_reports_ss.jpg")

## Adding new entries into drop downs

A user has the ability to modify the values in the drop downs in the
targets, findings, project details and target tasks by modifying the any
sps files under <Application_Path>/VulnReport_Files/sps/.

## ORG Active Developers

  - [ORG (Owasp Report Generator) - Mike de
    Libero](ORG_\(Owasp_Report_Generator\)_-_Mike_de_Libero "wikilink")
  - [ORG (Owasp Report Generator) - Dinis
    Cruz](ORG_\(Owasp_Report_Generator\)_-_Dinis_Cruz "wikilink")

Other related [OWASP .Net Project
Downloads](https://sourceforge.net/project/showfiles.php?group_id=64424&package_id=105632)

## Building the Installer

ORG is built using the WiX installer [1](http://wix.sourceforge.net/).
The assumption is that the folder housing the WiX libraries is in your
search path.

  - Setup a directory like the below screen shot
      - **Note** the following files can be found in the Google SVN:
        BuildInstaller.bat, FOP.zip.txt, regAuthenticPlugin.bat,
        ORG_v0.88.wxs, ORG_CONFIG_FILEs.zip.txt,
        AuthenticPlugin.zip.txt, AxInterop.PdfLib.dll,
        AxInterop.SHDocVw.dll, AxInterop.XMLSPYPLUGINLib.dll,
        ICSharpCode.TextEditor.dll, ICSharpCode.TextEditor.dll,
        Interop.SHDocVw.dll, Interop.XMLSPYPLUGINLib.dll,
        SharpZipLib.dll

![Image:Org_installer_files_ss.gif](Org_installer_files_ss.gif
"Image:Org_installer_files_ss.gif")

  - Run the batch script BuildInstaller.bat

When a new version of the installer needs to be built the ID for the
product element needs to be replaced along with the version information.

\-- ==== Project Identification ====  --\>

#### Project Identification

__NOTOC__ <headertabs />

[Report Generator)](Category:OWASP_Project "wikilink") [Category:OWASP
.NET Project](Category:OWASP_.NET_Project "wikilink") [Category:OWASP
Tool](Category:OWASP_Tool "wikilink") [Category:OWASP
Download](Category:OWASP_Download "wikilink") [Category:OWASP Alpha
Quality Tool](Category:OWASP_Alpha_Quality_Tool "wikilink") [Report
Generator)](Category:OWASP_Project "wikilink") [Category:OWASP .NET
Project](Category:OWASP_.NET_Project "wikilink") [Category:OWASP
Tool](Category:OWASP_Tool "wikilink") [Category:OWASP
Download](Category:OWASP_Download "wikilink") [Category:OWASP Alpha
Quality Tool](Category:OWASP_Alpha_Quality_Tool "wikilink")