The OWASP Top 10 2013 contains a new entry: [A9 - Using Components with
Known
Vulnerabilities](https://www.owasp.org/index.php/Top_10_2013-A9-Using_Components_with_Known_Vulnerabilities).
SafeNuGet can currently be used to scan .NET applications to identify
any known vulnerable components.

The problem with using known vulnerable components was described very
well in a paper by Jeff Williams and Arshan Dabirsiaghi titled, "[The
Unfortunate Reality of Insecure
Libraries](https://www.aspectsecurity.com/uploads/downloads/2012/03/Aspect-Security-The-Unfortunate-Reality-of-Insecure-Libraries.pdf)".
The gist of the paper is that we as a development community include
third party libraries in our applications that contain well known
published vulnerabilities (such as those at the [National Vulnerability
Database](http://web.nvd.nist.gov/view/vuln/search)).

OWASP SafeNuGet is an MSBuild task which will warn developers if they
are using NuGet packages with known vulnerabilities.

More information about SafeNuGet can be found on the [Github SafeNuGet
site](https://github.com/owasp/SafeNuGet).

For a similar tool for java see
[OWASP_Dependency_Check](OWASP_Dependency_Check "wikilink")

# Project About

[Category:OWASP Project](Category:OWASP_Project "wikilink")