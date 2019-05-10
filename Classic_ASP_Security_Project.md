## Overview

Classic ASP 2.0 and 3.0 applications are still largely used as this
technology is more than 10 years old and was largely used. there are
thousands of sites on the wild that need guidance on the security arena.
This is where OWASP can come up and provide help for “making the Web a
better place” and continue spreading the word on security. I have always
be a passionate of the technology (regardless of its inconveniences such
as being old and DLL-hell prone) and I am really exited on the idea of
sharing my knowledge of this area to the world and what best that though
OWASP.

### Objectives

Create a secure framework for Classic ASP application by complementing
existing OWASP projects with documentation for this particular
technology and the creation of security libraries.

### Deliverables and Progress

<table border="1" cellpadding="3" cellspacing="0">

<tr>

<th>

Activity

</th>

<th width="20%">

Status

</th>

</tr>

<tr>

<td>

  - Creation of a Common Object Repository for ASP applications based on
    OWASP ESAPI Project including objects and/or references to libraries
    for security applications all this aligned with OWASP Top10 and
    OWASP Guide.

</td>

<td>

Done - March 16th, 2009

</td>

</tr>

<tr>

<td>

  - Create Documentation aligned to OWASP Code Review Project Checklist
    providing additional technology-specific checks
    </td>
    <td>
    Done - Jun 8, 2008
    </td>

</tr>

<tr>

<td>

  - Addition of expression for Code Review Tool to support Classic ASP
    applications
    </td>
    <td>
    Done - Jun 12, 2008
    </td>

</tr>

<tr>

<td>

  - Implementation of Version 1 of Stinger for ASP either by using an
    installable COM library or ISAPI.

</td>

<td>

Done - Aug 3rd, 2008

</td>

</tr>

<tr>

<td>

  - This same module will compliment the OWASP Validation Documentation
    Project.

</td>

<td>

Done - Aug 7th, 2008

</td>

</tr>

</table>

### Installing and Using the Software

#### Stinger

Stinger 1.0 for Classic ASP is implemented in pure VBScript code, thus
there is no need to install any software other than MSXML (you usually
you have it as part of IE) in order for it to work given that it has
extensive use of XML.

1.  Unzip [StingerASP1.0.zip](:Image:StingerASP1.0.zip "wikilink")
2.  Start creating rule files on the `/rules` folder named after your
    files. For example, you would create a `Default.svdl.asp` rules file
    for your `Default.asp` page.
3.  Include the `Stinger.asp` page in your `default.asp` page
4.  Instantiate Stringer class and call the validate method

I strongly recommend you see the example `default.asp` page included in
the zip file it is very self explanatory. Also the `Default.svdl.asp`
include examples of how to create rules for input fields.

**Notice:** If you make use of complex dynamic pages with variable
number of fields you can use Programatic rules to handle the different
scenarios you are handling in the single page. You will see an example
of it in the comments into the `default.asp` sample page.

#### ESAPI (Draft)

Classic ASP for ESAPI uses a modified version of ESAPI for .NET as a
baseline (thus you will need .NET 2.0 to run it) for some important
operations that would be hard or impossible to implement, like
encryption, using pure VBScript. So here are the steps for it to work:

1.  Unzip
    [OWASP_Classic_ASP_ESAPI.zip](:Image:OWASP_Classic_ASP_ESAPI.zip "wikilink")
2.  Open the `Owasp.Esapi.csproj` project with Visual Studio 2005 or
    ahead and compile it (notice you will be requested a password, that
    password is on a `OWASP_Key_Pass.txt` text file on the main folder.
    Also notice the password is not used for security reasons, but only
    to avoid conflicts of versions on the DLLs)
3.  Once that you compiled the project successfully it will register
    itself to be used and the default.asp page should work fine.

All the methods implemented in the default.asp are fully implemented and
are usable, unless otherwise is explained in the
[default.asp](:Image:Default.zip "wikilink") page.

## Feedback

*'Notice that although I tested the software created as part of this
project, It might be not stable enough for production so I recommend you
to make additional and extensive testing before deploying, at least
until the project reaches release level*

[Let me
know](mailto:johnccr@yahoo.com?subject=About%20Classic%20ASP%20Security%20Software)
about any issue you face so I can improve the implementation, a Google
code repository will be available soon.

[Category:OWASP Project](Category:OWASP_Project "wikilink")
[Category:OWASP Document](Category:OWASP_Document "wikilink")
[Category:OWASP Alpha Quality
Tool](Category:OWASP_Alpha_Quality_Tool "wikilink") [Category:OWASP
Project](Category:OWASP_Project "wikilink")