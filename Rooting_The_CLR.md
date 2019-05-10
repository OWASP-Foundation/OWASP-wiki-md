\[draft page, there is still tons of information to add here\]

## Rooting the CLR presentation - London DotNet User Group 22nd March

**Mp3 of presentation**:

  - [Rooting the CLR
    presentation](http://69.10.155.160/mp3/Owasp%20-%20Rooting%20the%20CLR.mp3)
    as delivered to the London Dot Net User Group on the 22nd March

**Description**:

In this presentation Dinis Cruz will show how the .Net Framework can be
modified in real-time using Rootkit-like techniques. This is possible
due to the fundamental security design flaw within the .Net framework
where the entire Framework (i.e. all dlls) are loaded into the .Net
process. This creates a scenario where there is nothing stopping a
malicious Full Trust .Net assembly or unmanaged code executed in that
process to 'patch' the CLR itself. Demos include:

  - CLR patch that allows calls to private methods to succeed
  - CLR patch that allows corrupted Strong Named assemblies to be
    executed (i.e. ILDASM a signed .Net assembly, change it, ILASM it
    back into .exe format, and execute it without any exception been
    thrown)
  - Load core .Net framework dlls that come from directories under my
    control (for example c:\\fusion.dll)
  - MSIL Patch on all Deny and Demand methods so that they always return
    without any exception being thrown, which disables most CAS
    protections in the running assembly (the only caveat with this demo
    is that the 'MSIL patch' must be applied before those methods are
    JITED)
  - Extra demo: Unpathed ILDASM / ILASM buffer overflow

[link not working](Category:FIXME "wikilink") [Category:OWASP .NET
Project](Category:OWASP_.NET_Project "wikilink")