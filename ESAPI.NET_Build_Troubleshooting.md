## Targeting .NET Framework \<v3.5

This doesn't appear to work at this time. The MS Anti-XSS library v3.1
(latest ver) seems to require v3.5 of the .NET framework in order to
build properly. As the .NET ESAPI depends on this, it doesn't appear to
be possible to use the .NET ESAPI with previous versions of the .NET
framework. I tried installing and referencing v1.5 (instead of v3.1) of
the ms-antiXSS lib but still get this error when trying to build ESAPI
targeting .NET v2 or v3.0.

*"Error 2 The type or namespace name HashSet could not be found (are you
missing a using directive or an assembly reference?)
Esapi\\Runtime\\ContextRuleHandler.cs 15 17 Esapi"*

## Finding the MS AntiXSS Library

The Esapi.csproj file from SVN has a hint path for the AntiXSS module
which probably will not work in your environment. Thus on my system
after loading the project, and expanding the references tab in Solution
Explorer, there was an exclamation mark next to AntiXSSLibrary and
attempts to build the Esapi bailed out.

To resolve this, click on the AntiXSSLibrary reference, and then go down
and click on the Path option and set it to the location on your
filesystem where the

On my system this is: "D:\\Program Files\\Microsoft Information
Security\\Microsoft Anti-Cross Site Scripting Library
v3.1\\Library\\AntiXSSLibrary.dll"

## Fixing the FXCop Path

I also noticed that after successful builds, I'd get errors about VS
being unable to find the FxCopCmd.exe binary.

Find FxCopCmd.exe on your system, and then click on the Properties pages
for the Esapi, EsapiTest and Swingset projects, and click on Build
Events. Modify the post build event command line to refer to the proper
location of your installed FxCopCmd.exe, or just delete it or rem it out
if you don't want to run FxCop after each successful build.

[Back to the ESAPI .NET
Page](http://www.owasp.org/index.php/Category:OWASP_Enterprise_Security_API#tab=.NET)