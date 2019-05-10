` `

`    <td ``>Einige verwundbare Software-Komponenten (z.B. Bibliotheken von Frameworks) können von Tools erkannt und automatisch ausgenutzt werden. Dadurch steigt die Zahl der Bedrohungsquellen ins Unermessliche.`

</td>

`    <td ``>Ein Angreifer erkennt Komponenten mit Schwachstellen mittels Scan, oder manueller Analyse. Er passt den Exploit an und führt den Angriff aus. Bei tief eingebetteten Komponenten ist dies schwieriger.`

</td>

`    <td colspan=2  ``>So gut wie jede Anwendung ist von diesem Problem betroffen, da die meisten Entwicklungs-Teams wenig darauf achten, dass die benutzten Komponenten bzw. Bibliotheken aktuell sind. Häufig kennen sie nicht einmal alle Komponenten, oder machen sich keine Gedanken über deren Version.`
`Die rekursive Abhängigkeit von weiteren Bibliotheken verschlechtert die Situation weiter.`

</td>

`    <td ``>Die ganze Bandbreite von Schwachstellen ist möglich, inkl. Injection, Fehler in der Zugriffskontrolle, XSS usw. Die Auswirkungen können von minimal bis hin zur vollständigen Übernahme des Servers und der Daten reichen.`

</td>

`    <td ``>Betrachten Sie was jede einzelne Lücke der Anwendung für Ihren Geschäftsbetrieb bedeuten kann. Es kann vollkommen harmlos bis hin zu existenzbedrohend sein.`

</td>

Die durch Schwachstellen in Komponenten verursachten Lücken können von
minimalen Risiken bis zu ausgeklügelter Malware führen, die für
gerichtete Angriffe geeignet ist. Die Komponenten laufen meist mit allen
Anwendungsrechten, wodurch ein Mangel in <u>jeder</u> Komponente
schwerwiegend sein kann. Folgende
<span style="color:red;">**verwundbare**</span> Komponenten wurden 22
Millionen Mal in 2011 heruntergeladen:

  - [<span style="color:red;">Apache CXF Authentication
    Bypass</span>](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2012-3451) – Durch
    das Fehlen eines Identifikations-Tokens, konnten Angreifer beliebige
    Web-Services aufrufen (Apache CXF ist ein Web-Service-Framework,
    nicht zu verwechseln mit dem Apache Application Server).
  - [<span style="color:red;">Spring Remote Code
    Execution</span>](http://www.infosecurity-magazine.com/view/30282/remote-code-vulnerability-in-spring-framework-for-java/) – Der
    Missbrauch der ‘Expression Language‘ in Spring ermöglichte
    Angreifern das Ausführen von beliebigem Code auf dem Server.

Jede Anwendung, die eine der beiden Bibliotheken benutzt, ist
angreifbar, da sie beide direkt von Benutzern ansprechbar sind. Bei
anderen Bibliotheken kann dies schwieriger sein.

Eine Option wäre, nur selbstgeschriebene Komponenten zu benutzen. Dies
ist jedoch nicht sehr realistisch. Die meisten Framework-Projekte
bringen keine Sicherheits-Patches für alte Versionen heraus. Meist
werden die Lücken einfach in der nächsten Version behoben. Deshalb ist
es sehr wichtig, diese neuen Versionen einzusetzen.

Software-Projekte sollten folgende Prozesse etabliert haben:

1.  Übersicht aller Komponenten und Versionen, die Sie direkt oder
    indirekt benutzen (z.B.
    [Versions-Plugin](http://mojo.codehaus.org/versions-maven-plugin/)).
2.  Laufendes Beobachten der Sicherheit dieser Komponenten mithilfe
    aktueller, frei zugänglichen Datenbanken, Mailing-Listen der
    Projekte und von Sicherheitsseiten.
3.  Entwickeln Sie Richtlinien zum Einsatz von Komponenten, für die
    Entwicklung von Software, das Durchführen von Sicherheitstests und
    akzeptable Lizenzbedingungen.
4.  Ggf. sollten Sie erwägen, Sicherheitsschichten einzuziehen, die Ihre
    Komponenten weiter härten (z.B. unbenutzte Funktionen sperren, oder
    Lücken schließen).

# **JAVA**

#### Erkennen aller verwendeten Software-Komponenten

Verschaffen Sie sich einen Überblick über alle, vom Programm benutzten
Software-Komponenten, deren Abhängigkeiten (rekursive Abfrage der
benutzten Komponenten), sowie den Versionsständen.
Beispiele für Tools, die Sie dabei unterstützen:

  - [OWASP Dependency Check](OWASP_Dependency_Check "wikilink")
  - [Versions-Plugin für
    Maven](http://mojo.codehaus.org/versions-maven-plugin)
  - weitere kommerzielle Produkte: [vgl
    Top10-Mail-Liste](http://lists.owasp.org/pipermail/owasp-topten/2013-September/001239.html)

#### Sicherheits-(CERT-)Meldungen für die verwendeten Versionen prüfen

Um herauszufinden, ob diese Versionen von Schwachstellen betroffen sind,
ist es notwendig, die oben genannten Schwachstellen-Datenbanken
regelmäßig, in kurzen Abständen zu durchsuchen, sowie sich mithilfe
von Mailing-Listen und weiteren Meldungen zeitnah über mögliche Lücken
zu informieren.

Am einfachsten geht dies mithilfe von Tools:

  - [OWASP Dependency Check](OWASP_Dependency_Check "wikilink")

Falls eine benutzte Komponente verwundbar ist, sollten Sie genau prüfen,
ob Ihre Anwendung verwundbare Teile der Komponente nutzt und ob der
Fehler Auswirkungen hat, um die Sie sich kümmern müssen.
Verwenden des OWASP-Plugins im Maven-Build (pom.xml):

  -
    <reporting>
      -
        <plugins>
          -
            <plugin>
              -
                <groupId>org.owasp</groupId>
                <artifactId>dependency-check-maven</artifactId>
                <version>RELEASE</version>
                \<\!-- Proxy configuration, if needed ----
                <configuration>
                  -
                    <proxyUrl>yourserver</proxyUrl>
                    <proxyPort>yourport</proxyPort>
                </configuration>
                \----------------------------------------\>
            </plugin>
        </plugins>
    </reporting>


**Anmerkung:**
Theoretisch sollte es einfach sein, herauszufinden, ob die Anwendung
verwundbare Komponenten, oder Bibliotheken benutzt. Leider enthalten
Berichte über Sicherheitslücken kommerzieller oder von
Open-Source-Software nicht immer automatisch auswertbare, exakte
Versions-Angaben der verwundbaren Komponenten. Ferner benutzen nicht
alle Bibliotheken ein verständliches Versionsnummerierungs-Schema.
Darüber hinaus werden nicht alle Schwachstellen an zentrale
Schwachstellen-Datenbanken, wie CVE und NVD gemeldet.

#### Entwickeln Sie Ihre Richtlinien zum Einsatz von Software-Komponenten

Um die Anzahl der, zu prüfenden Software-Komponenten und deren Versionen
handhabbar zu halten, empfiehlt es sich, eine eigene Richtlinie dazu zu
erstellen und durchzusetzen. Im Idealfall stellen Sie Ihren Entwicklern
für bestimmte Aufgaben freigegebene Software-Komponenten (z.B.
Bibliotheken) zur Verfügung.

  - [OWASP Dependency Check](OWASP_Dependency_Check "wikilink")
  - [OWASP Good Component Practices
    Project](OWASP_Good_Component_Practices_Project "wikilink")

<!-- end list -->

  - [Versions-Plugin für
    Maven](http://mojo.codehaus.org/versions-maven-plugin)
  - [The Unfortunate Reality of Insecure
    Libraries](https://www.aspectsecurity.com/uploads/downloads/2012/03/Aspect-Security-The-Unfortunate-Reality-of-Insecure-Libraries.pdf)
  - [Open Source Software
    Security](http://en.wikipedia.org/wiki/Open_source_software_security)
  - [Addressing Security Concerns in Open Source
    Components](http://www.sonatype.com/content/download/1025/10060/file/sonatype_executive_security_brief_final.pdf)
  - [MITRE Common Vulnerabilities and Exposures](http://cve.mitre.org/)
  - [Beispiel einer 'Mass Assignment'-Schwachstelle, die inzwischen in
    ActiveRecord, ein 'Ruby on Rails-GEM', beboben
    wurde](http://web.nvd.nist.gov/view/vuln/detail?vulnId=CVE-2013-0277)

# **PHP**

#### Tbd

tbd
<span style="color: green;">'''tbd</span>

#### Tbd

<span style="color: green;">**tbd</span>
: <span style="color: green;">**tbd</span>
:: <span style="color: green;">'''tbd</span>

#### Tbd

<span style="color: green;">**tbd</span>
: <span style="color: green;">**tbd</span>
:: <span style="color: green;">'''tbd</span>

  - tbd \!\!

<!-- end list -->

  - tbd\!\!

# **.NET**

#### Tbd

tbd
<span style="color: green;">'''tbd</span>

#### Tbd

<span style="color: green;">**tbd</span>
: <span style="color: green;">**tbd</span>
:: <span style="color: green;">'''tbd</span>

#### Tbd

<span style="color: green;">**tbd</span>
: <span style="color: green;">**tbd</span>
:: <span style="color: green;">'''tbd</span>

  - [OWASP SafeNuGet (für .NET Bibliotheken durch
    NuGet)](OWASP_SafeNuGet "wikilink")
  - [OWASP Dependency Check (für Java,
    ...)](OWASP_Dependency_Check "wikilink")
  - [OWASP Good Component Practices
    Project](OWASP_Good_Component_Practices_Project "wikilink")

<!-- end list -->

  - [Versions-Plugin für
    Maven](http://mojo.codehaus.org/versions-maven-plugin)
  - [The Unfortunate Reality of Insecure
    Libraries](https://www.aspectsecurity.com/uploads/downloads/2012/03/Aspect-Security-The-Unfortunate-Reality-of-Insecure-Libraries.pdf)
  - [Open Source Software
    Security](http://en.wikipedia.org/wiki/Open_source_software_security)
  - [Addressing Security Concerns in Open Source
    Components](http://www.sonatype.com/content/download/1025/10060/file/sonatype_executive_security_brief_final.pdf)
  - [MITRE Common Vulnerabilities and Exposures](http://cve.mitre.org/)
  - [Beispiel einer 'Mass Assignment'-Schwachstelle, die inzwischen in
    ActiveRecord, ein 'Ruby on Rails-GEM', beboben
    wurde](http://web.nvd.nist.gov/view/vuln/detail?vulnId=CVE-2013-0277)

\-- weitere Programmiersprachen oder evtl Anti-Beispiele --- \>

# **Test**

tbd Text

tbd Text

tbd (ganze Breite) Text

Text

Text

\-----------------------------------------------------------\>
<headertabs />