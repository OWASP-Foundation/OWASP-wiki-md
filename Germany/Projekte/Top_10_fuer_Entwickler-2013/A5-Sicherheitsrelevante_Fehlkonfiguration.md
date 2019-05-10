` `

`    <td ``>Nicht authentifizierte Angreifer sowie authentifizierte Nutzer könnten versuchen, Zugangsdaten anderer zu stehlen. In Betracht kommen außerdem Innentäter, die ihre Handlungen verschleiern wollen.`

</td>

`    <td ``>Angreifer benutzen Standardkonten, inaktive Seiten, ungepatchte Fehler, ungeschützte Dateien und Verzeichnisse etc., um unautorisierten Zugang zum oder Kenntnis über das Zielsystem zu erlangen.`

</td>

`    <td colspan=2 ``>Sicherheitsrelevante Fehlkonfiguration kann auf jeder Ebene der Anwendung, inkl. Plattform, Web- und Anwendungsserver, oder Datenbank vorkommen. Die Zusammenarbeit zwischen Entwicklern und Administratoren ist wichtig, um eine sichere Konfiguration aller Ebenen zu gewährleisten. Automatisierte Scanner können oft fehlende Sicherheitspatches, Fehlkonfigurationen, Standardkonten, nicht benötigte Dienste, usw. erkennen.`

</td>

`    <td ``>Diese Fehler geben Angreifern häufig unautorisierten Zugriff auf Systemdaten oder -funktionalitäten.`

Manchmal führen sie zur kompletten Kompromittierung des Zielsystems.

</td>

`    <td ``>`

Ein System könnte unbemerkt kompromittiert werden. Alle Daten könnten
gestohlen oder nach und nach verändert werden.
Hohe Wiederherstellungskosten können entstehen.

</td>

**<u>Szenario 1</u>**: Die Administratorkonsole mit Standardkonto wurde
automatisch installiert und nicht entfernt. Angreifer entdecken dies,
melden sich über das Standardkonto an und kapern das System.
**<u>Szenario 2</u>**: Directory Listings wurden nicht deaktiviert.
Angreifer nutzen dies, um in den Besitz aller Dateien zu kommen. Sie
laden alle existierenden Java-Klassen herunter, dekompilieren diese und
entdecken einen schwerwiegenden Fehler in der Zugriffskontrolle.
**<u>Szenario 3</u>**: Die Konfiguration des Anwendungsservers erlaubt
es, Stack Traces an Benutzer zurückzugeben. Dadurch können potentielle
Fehler im Backend offengelegt werden. Angreifer nutzen zusätzliche
Informationen in Fehlermeldungen aus.
**<u>Szenario 4</u>**: Der Applikationsserver wird mit
Beispielapplikationen ausgeliefert, die auf dem Produktivsystem nicht
entfernt wurden. Diese Beispielapplikationen besitzen bekannte
Sicherheitsschwachstellen, die Angreifer ausnutzen können um den Server
zu kompromittieren.
Alle folgenden Empfehlungen sollten berücksichtigt werden:

1.  Ein wiederholbarer Härtungsprozess, der eine schnelle und einfache
    Verteilung einer neuen, abgesicherten Umgebung erlaubt.
    Entwicklungs-, QA-, und Produktionsumgebungen sollten identisch
    konfiguriert sein (mit unterschiedlichen Passwörtern pro Umgebung).
    Der Prozess sollte automatisiert sein, um den nötigen Aufwand bei
    Erstellung einer neuen, sicheren Umgebung zu minimieren.
2.  Ein Prozess, der zeitnah neuentwickelte Softwareupdates auf allen
    ausgerollten Umgebungen ermöglicht. Davon sind auch alle
    Bibliotheken und Komponenten betroffen (siehe
    [text=documentRootTop10DeveloperEdition]({{Top_10:LanguageFile "wikilink")).
3.  Eine robuste Anwendungsarchitektur, mit effektiver und sicherer
    Trennung und Absicherung einzelner Komponenten.
4.  Periodisch durchgeführte Tests und Audits helfen zukünftige
    Fehlkonfigurationen oder fehlende Patches zu erkennen und zu
    vermeiden.

# **JAVA**

Bitte setzen Sie die oben genannten Empfehlungen auf allen Ebenen von
der Anwendung, den Libraries, der Middleware bis hin zur
IT-Infrastruktur um. ---------- keine weiteren Sporachtypischen
Beispiele  Tbd

#### Tbd

Tbd

#### Tbd

Tbd  ----------------------------\>

  - [OWASP Development Guide: Chapter on
    Configuration](Configuration "wikilink")
  - [OWASP Code Review Guide: Chapter on Error
    Handling](Error_Handling "wikilink")
  - [OWASP Proactive Controls:](OWASP_Proactive_Controls "wikilink")
    [Kapitel über 'Error and Exception
    Handling'](OWASP_Proactive_Controls#10:_Error_and_Exception_Handling "wikilink")
  - [OWASP Testing Guide: Configuration
    Management](Testing_for_configuration_management "wikilink")
  - [OWASP Testing Guide: Testing for Error
    Codes](Testing_for_Error_Code_\(OWASP-IG-006\) "wikilink")
  - [OWASP Top 10 2004 - Insecure Configuration
    Management](A10_2004_Insecure_Configuration_Management "wikilink")

Weitere Informationen unter [ASVS requirements area for Security
Configuration (V12)](http://www.owasp.org/index.php/ASVS#tab=Download)

  - [PC Magazine Article on Web Server
    Hardening](http://www.pcmag.com/article2/0,2817,11525,00.asp)
  - [CWE Entry 2 on Environmental Security
    Flaws](http://cwe.mitre.org/data/definitions/2.html)
  - [CIS Security Configuration
    Guides/Benchmarks](https://benchmarks.cisecurity.org/downloads/latest/)

# **PHP**

Bitte setzen Sie die oben genannten Empfehlungen auf allen Ebenen von
der Anwendung, den Libraries, der Middleware bis hin zur
IT-Infrastruktur um.

#### speziell für PHP:

In der Datei php.ini bietet PHP Konfigurationsmöglichkeiten für
Umgebungsvariablen an. Hier kann bspw. bestimmt werden, ob ein Cookie
nur bei HTTP-Abfragen oder auch durch JavaScript ausgelesen werden darf.
Zur Laufzeit können die Parameter ebenfalls über die Funktion ini_set()
gesetzt werden. Das PHP-Projekt Psecio (siehe
<https://github.com/psecio/iniscan/>) bietet ein Werkzeug zur
Überprüfung der php.ini an, mit welchem Schwachstellen in der
Konfigurationsdatei aufgedeckt werden können.

Wichtige Parameter sind dabei u.a.:

  - open_basedir "/var/www/project" ; Ggf. auch /tmp erlauben,
    Einstellung bevorzugt in der Webserver-Konfiguration vornehmen
  - session.cookie_secure=On
  - session.use_only_cookies=On
  - session.cookie_httponly=On
  - allow_url_fopen=Off

#### ModSecurity

Die Benutzung einer Webfirewall wie modsecurity, welches sich als Modul
in den Webserver einbindet, ist empfehlenswert. Zentrale Komponente sind
die "corerules", in welchen zwischen Warnungen und Fehlern unterschieden
wird. In der Konfiguration des Webservers kann angegeben werden, welche
Aktion bei einem Regelverstoß durchgeführt werden soll. Verstößt eine
Anfrage gegen hinterlegte Regeln, kann die Ausführung der Anfrage
gestoppt oder der Regelverstoß protokolliert werden.

-----

#### Tbd

Tbd  ----------------\>

  - [OWASP Development Guide: Chapter on
    Configuration](Configuration "wikilink")
  - [OWASP Code Review Guide: Chapter on Error
    Handling](Error_Handling "wikilink")
  - [OWASP Proactive Controls:](OWASP_Proactive_Controls "wikilink")
    [Kapitel über 'Error and Exception
    Handling'](OWASP_Proactive_Controls#10:_Error_and_Exception_Handling "wikilink")
  - [OWASP Testing Guide: Configuration
    Management](Testing_for_configuration_management "wikilink")
  - [OWASP Testing Guide: Testing for Error
    Codes](Testing_for_Error_Code_\(OWASP-IG-006\) "wikilink")
  - [OWASP Top 10 2004 - Insecure Configuration
    Management](A10_2004_Insecure_Configuration_Management "wikilink")

Weitere Informationen unter [ASVS requirements area for Security
Configuration (V12)](http://www.owasp.org/index.php/ASVS#tab=Download)

  - [PC Magazine Article on Web Server
    Hardening](http://www.pcmag.com/article2/0,2817,11525,00.asp)
  - [CWE Entry 2 on Environmental Security
    Flaws](http://cwe.mitre.org/data/definitions/2.html)
  - [CIS Security Configuration
    Guides/Benchmarks](http://cisecurity.org/en-us/?route=downloads.benchmarks)
  - [ModSecurity](http://www.modsecurity.org/)

\-- weitere Programmiersprachen oder evtl Anti-Beispiele --- \>

# **Test**

tbd Text

tbd Text

tbd Text

(ganze Breite) Text

\-----------------------------------------------------------------------\>
<headertabs />

[Category:OWASP Top 10 fuer
Entwickler](Category:OWASP_Top_10_fuer_Entwickler "wikilink")