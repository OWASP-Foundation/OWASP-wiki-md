# Overview Strongly Named assemblies

During the build process either QA or Developers are going to publish
the code into executable formats. Usually this consists of an exe or and
one or several DLL’s. During the build/publish process a decision needs
to be made to sign or not sign the code. Signing your code is called
creating “strong names” by Microsoft. If you create a project using
Visual Studio and use Microsofts “Run code analysis” most likely your
will encounter a Microsoft design error if the code is not strong named;
“Warning 1 CA2210 : Microsoft.Design : Sign 'xxx.exe' with a strong name
key.”

Code review needs to be aware if strong naming is being used, benefits
and what threat vectors strong naming helps prevent or understand the
reasons for not using strong naming.

A strong name is a method to sign an assembly’s identity using its text
name, version number, culture information, a public key and a digital
signature.(Solis, 2012)

  - Strong naming guarantees a unique name for that assembly.

<!-- end list -->

  - Strong names protect the version lineage of an assembly. A strong
    name can ensure that no one can produce a subsequent version of your
    assembly. Users can be sure that a version of the assembly they are
    loading comes from the same publisher that created the version the
    application was built with.

The above two point are very important if you are going to use Global
Assembly Cache (GAC).

  - Strong names provide a strong integrity check and prevent spoofing.
    Passing the .NET Framework security checks guarantees that the
    contents of the assembly have not been changed since it was built.
    Note, however, that strong names in and of themselves do not imply a
    level of trust like that provided, for example, by a digital
    signature and supporting certificate. If you use the GAC assemblies
    remember the assemblies are not verified each time they load since
    the GAC by design is a locked-down, admin-only store.

What strong names can’t prevent is a malicious user from stripping the
strong name signature entirely, modifying the assembly, or re-signing it
with the malicious user’s key.

The code reviewer needs to understand how the strong name private key
will be kept secure and managed. This is crucible if you decide strong
name signatures are a good fit for your organization.

If principle of least privilege is used so code is not or less
susceptible to be access by the hacker and the GAC is not being used
strong names provides less benefits or no benefits at all.

## How to use Strong Naming

### Signing tools

In order to create a Strongly name assembly there are a set of tools and
steps that you need to follow

### Using Visual Studio

In order to use Visual Studio to create a Strongly Named Assembly, it is
necessary to have a copy of the public/private key pair file. Its is
also possible to create this pair key in Visual Studio

In Visual Studio 2005, the C\#, Visual Basic, and Visual J\# integrated
development environments (IDEs) allow you to generate key pairs and sign
assemblies without the need to create a key pair using Sn.exe(Strong
Name Tool). These IDEs have a Signing tab in the Project Designer. . The
use of the AssemblyKeyFileAttribute to identify key file pairs has been
made obsolete in Visual Studio 2005.

The following figure ilustrates the process done by the compiler
![<File:StrongNameAssembly.png>](StrongNameAssembly.png
"File:StrongNameAssembly.png")

### Using Strong Name tool

The Sign Tool is a command-line tool that digitally signs files,
verifies signatures in files, or time stamps files. The Sign Tool is not
supported on Microsoft Windows NT, Windows Me, Windows 98, or Windows
95. In case you aren't using the "Visual Studio Command Prompt" (Start
\>\> Microsoft Visual Studio 2010 \>\> Visual Studio Tools \>\> Visual
Studio Command Prompt (2010)) you can locate sn.exe at
%ProgramFiles%\\Microsoft SDKs\\Windows\\v7.0A\\bin\\sn.exe

The following command creates a new, random key pair and stores it in
keyPair.snk.

`sn -k keyPair.snk`

The following command stores the key in keyPair.snk in the container
MyContainer in the strong name CSP.

`sn -i keyPair.snk MyContainer`

The following command extracts the public key from keyPair.snk and
stores it in publicKey.snk.

`sn -p keyPair.snk publicKey.snk`

The following command displays the public key and the token for the
public key contained in publicKey.snk.

`sn -tp publicKey.snk`

The following command verifies the assembly MyAsm.dll.

`sn -v MyAsm.dll`

The following command deletes MyContainer from the default CSP.

`sn -d MyContainer`

### Using the Assembly Linker(AI.exe)

This tool is automatically installed with Visual Studio and with the
Windows SDK. To run the tool, we recommend that you use the Visual
Studio Command Prompt or the Windows SDK Command Prompt (CMD Shell).
These utilities enable you to run the tool easily, without navigating to
the installation folder. For more information, see Visual Studio and
Windows SDK Command Prompts.

If you have Visual Studio installed on your computer: On the taskbar,
click Start, click All Programs, click Visual Studio, click Visual
Studio Tools, and then click Visual Studio Command Prompt. -or- If you
have the Windows SDK installed on your computer: On the taskbar, click
Start, click All Programs, click the folder for the Windows SDK, and
then click Command Prompt (or CMD Shell).

At the command prompt, type the following:

`al sources options`

#### Remarks

All Visual Studio compilers produce assemblies. However, if you have one
or more modules (metadata without a manifest), you can use Al.exe to
create an assembly with the manifest in a separate file. To install
assemblies in the cache, remove assemblies from the cache, or list the
contents of the cache, use the Global Assembly Cache Tool (Gacutil.exe).

The following command creates an executable file t2a.exe with an
assembly from the t2.netmodule module. The entry point is the Main
method in MyClass.

`al t2.netmodule /target:exe /out:t2a.exe /main:MyClass.Main`

## Use Assembly attributes

You can insert the strong name information in the code directly. For
this, depending on wherethe key file is located you can use
AssemblyKeyFileAttribute or AssemblyKeyNameAttribute

## Use Compiler options :use /keyfile or /delaysign

Safeguarding the key pair from developers is necessary to maintain and
guarantee the integrity of the assemblies. The public key is should be
accessible, but access to the private key is restricted to only a few
individuals. When developing assemblies with strong names, each assembly
that references the strong-named target assembly contains the token of
the public key used to give the target assembly a strong name. This
requires that the public key be available during the development
process. You can use delayed or partial signing at build time to reserve
space in the portable executable (PE) file for the strong name
signature, but defer the actual signing until some later stage
(typically just before shipping the assembly). You can use /keyfile or
/delaysign in C\# and VB.NET (MSDN)

## References

<http://msdn.microsoft.com/en-us/library/wd40t7ad(v=vs.80>).aspx

<http://msdn.microsoft.com/en-us/library/c405shex(v=vs.110>).aspx

<http://msdn.microsoft.com/en-us/library/k5b5tt23(v=vs.80>).aspx

<http://msdn.microsoft.com/en-us/library/t07a3dye(v=vs.80>).aspx

<http://msdn.microsoft.com/en-us/library/t07a3dye(v=vs.110>).aspx