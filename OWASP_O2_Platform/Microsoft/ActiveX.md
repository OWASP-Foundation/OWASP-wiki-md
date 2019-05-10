This page contains information on how to test ActiveX controls

## Security Issues with ActiveX

{list the common problems with ActiveX}

## Tools to test ActiveX for Buffer Overflows

  - <http://digitaloffense.net/tools/axman/>

## using O2

One strategy to test ActiveX with O2 would be to create a .NET stub
around it and then use it to invoke the ActiveX methods

The OWASP .NET tool (couple years old)
[DN_BOFinder](DN_BOFinder "wikilink") ([download from
SF](http://sourceforge.net/projects/owasp/files/dotNET/DN_BOFinder/DN_BOFinder_V0.2.zip/download))
is a .NET Fuzzer which is able to intelligently fuzz .NET assemblies and
the COM objects it exposes (see also
[Buffer_OverFlow_in_ILASM_and_ILDASM](Buffer_OverFlow_in_ILASM_and_ILDASM "wikilink")

## Research Links

  - on consuming COM & ActiveX from .NET
      - [.NET ActiveX dll and
        regasm](http://bytes.com/topic/net/answers/717125-net-activex-dll-regasm)
      - [How to create Activex Control using C\# and Use it in ASP.NET
        webform?](http://bytes.com/topic/asp-net/answers/308854-how-create-activex-control-using-c-use-asp-net-webform)
      - [ASP.NET ActiveX Object Windows API
        Access](http://bytes.com/topic/asp-net/answers/760244-asp-net-activex-object-windows-api-access)

[Category:OWASP .NET Project](Category:OWASP_.NET_Project "wikilink")