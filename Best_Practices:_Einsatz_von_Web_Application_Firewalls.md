\=

<center>

**Best Practices: Einsatz von Web Application Firewalls**

</center>

\=

Version 1.0.2, März 2008, wiki September 2008

Autor: OWASP German Chapter

unter Mitwirkung von:

Maximilian Dermann

Mirko Dziadzka

Boris Hemkemeier

Achim Hoffmann

Alexander Meisel

Matthias Rohr

Thomas Schreiber

## Abstrakt

Webanwendungen aller Art, ob Webshop oder Partnerportal, werden in den
letzten Jahren nachweislich immer stärker zur Zielscheibe von
Hackerangriffen. Dabei verwenden die Angreifer Methoden, die gezielt
potenzielle Schwachstellen der Webanwendungssoftware selbst ausnutzen –
und deshalb von klassischen IT-Sicherheitssystemen wie
Netzwerk-Firewalls oder IDS-/IPS-Systemen nicht oder nur unzureichend
erkannt werden. OWASP entwickelt Tools und Best Practices um Entwickler,
Projektleiter und Securitytester bei der Entwicklung und beim Betrieb
sicherer Webanwendungen zu unterstützen. Einen weiteren Schutz gegen
Angriffe, insbesondere für bereits produktive Webanwendungen, bietet
eine noch relativ neue Klasse von IT-Sicherheitssystemen, sogenannte
*Web Application Firewalls* (im folgenden einfach *WAF*), oft auch *Web
Application Shields* oder *Web Application Security Filter* genannt.

Um z. B. den derzeit gültigen Sicherheitsstandard der
Kreditkartenindustrie (PCI DSS - Payment Card Industry Data Security
Standard v.1.1) zu erfüllen, muss u. a. entweder ein regelmäßiger
Sorcecode-Review oder der Einsatz einer WAF nachgewiesen werden.

Das Dokument wendet sich vornehmlich an technische Entscheider -
speziell Betriebsverantwortliche, Sicherheitsverantwortliche,
Applikationseigner (Fachabteilung, technisch
Anwendungsverantwortlicher), die den Einsatz einer WAF im Unternehmen
evaluieren. Spezielles Augenmerk wurde – wo immer möglich – auf die
Darstellung von Aufwandsabschätzungen gelegt – auch im Vergleich zu
möglichen Alternativen wie z. B. Änderungen im Sourcecode.

Bei der Entscheidungsfindung bzgl. des Einsatzes von WAFs kann neben der
Wichtigkeit der Webapplikation für das Unternehmen z. B. Umsatz oder
Image – der im Dokument erläuterte Begriff des *Zugriff*” auf eine
Webapplikation ein gutes Kriterium sein. Anschaulich gesprochen misst
der *Zugriff* auf eine spezielle Webapplikation durch ein Unternehmen,
inwieweit das Unternehmen tatsächlich zeitnah notwendige Änderungen des
Source Codes der Applikation selbst durchführen bzw. sicher durch Dritte
herbeiführen lassen kann. Wie die unten stehende Grafik illustriert,
kann eine Webapplikation, auf die das Unternehmen keinen Zugriff hat,
sinnvollerweise nur von einer WAF geschützt werden (hoher Nutzen der
WAF), während selbst bei einer Applikation in vollem Zugriff eine WAF
als zentrale Servicestelle für diverse Dienste wie sicheres
Session-Management, die für alle Applikationen gleich gelöst werden
können, und als geeignete Mittel für proaktive Schutzmaßnahmen wie
z. B. URL-Encryption immer noch erheblichen Zusatznutzen bietet.

![Best_Practice_WAF-chart-DE.png](Best_Practice_WAF-chart-DE.png
"Best_Practice_WAF-chart-DE.png")

Weitere Schwerpunkte sind Best Practices für die organisatorischen
Abläufe bei Installation und Betrieb einer WAF sowie - gerade für
größere Unternehmen – eine Erweiterung der Prozess-Organisation um die
Rolle *Anwendungsverantwortlicher WAF*.

## Über

Dieses Dokument wurde vom *OWASP German Chapter* erarbeitet. Die Autoren
sind Mitarbeiter von Unternehmen, die über den Einsatz und Betrieb von
WAFs beraten, WAFs einsetzen und/oder WAFs herstellen.

## Autoren

|                                                             |                    |                                                   |                      |                                                                |  |                                       |                                                    |
| ----------------------------------------------------------- | ------------------ | ------------------------------------------------- | -------------------- | -------------------------------------------------------------- |  | ------------------------------------- | -------------------------------------------------- |
| style="border-bottom:1px solid black" width="24%"           |                    | style="border-bottom:1px solid black" width="24%" |                      | style="border-bottom:1px solid black" width="24%"              |  | style="border-bottom:1px solid black" | <small>aktualisiert E-Mail-Adressen (2012)</small> |
| style="vertical-align:top;float:right;padding-right:0.5em;" | Maximilian Dermann | maximilian.dermann(at)lht.dlh.de                  | Lufthansa Technik AG |                                                                |  |                                       |                                                    |
| style="vertical-align:top;float:right;padding-right:0.5em;" | Mirko Dziadzka     | mirko.dziadzka(at)artofdefence.com                | art of defence GmbH  | <small>mirko.dziadzka(at)riverbed.com</small>                  |  |                                       |                                                    |
| style="vertical-align:top;float:right;padding-right:0.5em;" | Boris Hemkemeier   | boris(at)owasp.org                                | OWASP German Chapter |                                                                |  |                                       |                                                    |
| style="vertical-align:top;float:right;padding-right:0.5em;" | Achim Hoffmann     | achim.hoffmann(at)securenet.de                    | SecureNet GmbH       | <small>achim.hoffmann(at)sicsec.de, achim(at)owasp.org</small> |  |                                       |                                                    |
| style="vertical-align:top;float:right;padding-right:0.5em;" | Alexander Meisel   | alexander.meisel(at)artofdefence.com              | art of defence GmbH  | <small>alex.meisel(at)riverbed.com</small>                     |  |                                       |                                                    |
| style="vertical-align:top;float:right;padding-right:0.5em;" | Matthias Rohr      | matthias.rohr(at)securenet.de                     | SecureNet GmbH       | <small>matthias.rohr(at)owasp.org</small>                      |  |                                       |                                                    |
| style="vertical-align:top;float:right;padding-right:0.5em;" | Thomas Schreiber   | thomas.schreiber(at)securenet.de                  | SecureNet GmbH       |                                                                |  |                                       |                                                    |

## Terminologie

Die in diesem Dokument verwendeten Fachbegriffe sind nicht weiter
erklärt, sondern werden als bekannt vorausgesetzt. Auf ein Glossar
wurde bewusst verzichtet damit der Umfang überschaubar bleibt und sich
der Inhalt auf das Eigentliche - *Einsatz von Web Application Firewalls*
- konzentriert.

Ausführliche Begriffserklärungen und weiterführende Beschreibungen im
Zusammenhang mit WAS - Web Application Security - finden sich in:

  - <http://www.owasp.org/index.php/Category:AttackOWASP>
    Category:Attack
  - <http://www.owasp.org/index.php/Category:ThreatOWASP>
    Category:Threat
  - <http://www.owasp.org/index.php/Category:VulnerabilityOWASP>
    Category:Vulnerability
  - <http://www.webappsec.org/projects/threat/v1/WASC-TC-v1_0.de.docWASTCWeb>
    Application Security Consortium: Web Security Threat Classification
  - <http://www.webappsec.org/projects/wafec/> WAFECWeb Application
    Security Consortium: Web Application Firewall Evaluation Criteria
  - <http://www.owasp.org/images/9/9c/OWASPAppSecEU2006_WAFs_WhenAreTheyUseful.pptOWASP>
    WAFs When Are They Useful

## Lizenz

Dieses Werk ist unter einem

*Creative Commons Namensnennung-Weitergabe unter gleichen Bedingungen
2.0 Deutschland Lizenzvertrag*

lizenziert. Um die Lizenz anzusehen, gehen Sie bitte zu
<http://creativecommons.org/licenses/by-sa/2.0/de/> oder schicken Sie
einen Brief an Creative Commons, 171 Second Street, Suite 300, San
Francisco, California 94105, USA .

![CC-15.png](CC-15.png "CC-15.png")

# Einführung und Zielsetzung dieses Dokuments

## Einführung

Egal ob Internet-Filiale einer Bank, Online-Shop, Kunden-, Partner- oder
Mitarbeiterportal - jede dieser Webanwendungen ist aufgrund der *always
on* Natur des Internets für ihre Kunden - aber auch für Angreifer - rund
um die Uhr erreichbar. Angriffe wie SQL-Injection, Cross Site Scripting
oder Session Hijacking zielen dabei auf Schwachstellen in den
Webanwendungen selbst - und nicht auf solche auf der Netzwerk-Ebene.
Deshalb können sie auch durch klassische IT-Sicherheitssysteme wie
Firewall oder IDS/IPS-Systeme nicht bzw. allenfalls unzureichend
abgewehrt werden.

Grundlegend aus technischer Sicht ist dabei, dass das Web, speziell das
Protokoll HTTP, nicht für die heute üblichen komplexen Anwendungen
konzipiert wurde. Viele Schwachstellen haben hier ihren Ursprung:
beispielsweise ist HTTP zustandslos, d. h. Sessions oder Zustände der
Applikation müssen separat definiert und sicher implementiert werden.
Diese Schwachstellen werden noch verstärkt durch die hohe Komplexität
der häufig eingesetzten Web-Scripts, Frameworks und Web-Technologien.

Neben der neuen Einführung von Industriestandards z. B.
Datensicherheitsstandard der Kredit­kartenindustrie (PCI DSS v1.1)
sorgen auch erste bekannt gewordene Einbrüche in Deutschland wie z. B.
der Verlust von ca. 70.000 Kundendaten inkl. Kreditkarteninformationen
beim Online-Tickethändler *kartenhaus.de* für ein erhöhtes Interesse an
möglichen Schutzmaßnahmen gegen Angriffsmethoden auf Anwendungsebene.

Dieses Dokument befasst sich mit einer Klasse von Schutzsystemen, den
*Web Application Firewalls* (WAF), die gerade zur Absicherung bereits
produktiver Webanwendungen besonders geeignet sind.

## Begriffsdefinition WAF - Web Application Firewall

In diesem Dokument verstehen wir unter einer WAF eine Schutzlösung auf
Webanwendungsebene, die technisch nicht von der Anwendung selbst
abhängig ist. Der Fokus in diesem Dokument liegt auf der Darstellung
und Bewertung der Schutzmethoden und -funktionen, die eine WAF
bereitstellt. Aspekte der technischen Implementierung in die vorhandene
IT-Infrastruktur - ob als Hardware-Appliance, als Software-Plug-In in
die Webserver oder auch als Add-On für bereits bestehende
Infrastruktur-Komponenten wie z. B. Loadbalancer oder Netzwerk-Firewalls
- werden nur gestreift. Insbesondere wird hier - im Unterschied zur
Definition bei WAFEC - nicht vorausgesetzt, dass eine WAF als separate
Hardware-Appliance vor den Webservern stehen muss - was gerade in
großen, schnell wachsenden Infrastrukturen sicher nicht die beste
Implementierungsvariante darstellt.

## Zielgruppe und Zielsetzung

Das Dokument wendet sich vornehmlich an technische Entscheider -
speziell Betriebsverantwortliche, Sicherheitsverantwortliche,
Applikationseigner (Fachabteilung, technisch Anwendungsverantwortliche),
die den Einsatz einer WAF im Unternehmen evaluieren. Spezielles
Augenmerk wurde - wo immer möglich - auf die Darstellung von
Aufwandsabschätzungen gelegt. Weitere Schwerpunkte sind Best Practices
für die organisatorischen Abläufe bei Installation und Betrieb einer
WAF sowie - gerade für größere Unternehmen - eine Erweiterung der
Prozess-Organisation um die Rolle des *Anwendungsverantwortlicher WAF*.

# Charakteristika von Webapplikationen hinsichtlich Web Application Security

## Übergeordnete Aspekte im Unternehmen

Bezüglich der Bedeutung der Sicherheit der im Unternehmen eingesetzten
Webapplikationen müssen - gerade bei größeren Unternehmen - viele
Aspekte berücksichtigt werden.

Einer der wichtigsten ist allein die Anzahl der produktiven
Webanwendungen im Unternehmen. Groß-Unternehmen betreiben - inhouse oder
extern - oft deutlich mehr als 100 Webapplikationen. Auch wenn eine
Priorisierung jeder einzelnen Webanwendung hinsichtlich der Bedeutung
für den Unternehmenserfolg unerlässlich und sehr sinnvoll ist, so ist
doch prinzipiell festzuhalten, dass alle inhouse betriebenen
Webanwendungen - je nach Architektur - mittels geeigneter
Angriffsmethoden einen Zugriff auf die unternehmensinternen Systeme
ermöglichen können. Deshalb sollten auch auf den ersten Blick -
unwichtige - Webanwendungen zumindest gegen bekannte Angriffe
abgesichert werden.

Bei der Priorisierung hinsichtlich der Bedeutung der Webanwendung für
den Unternehmenserfolg spielen insbesondere folgende Punkte eine
Hauptrolle:

  - Zugriff auf personenbezogene Daten von Kunden, Partnern und/oder
    Mitarbeitern
  - Zugriff auf Betriebsgeheimnisse
  - unabdingbare Voraussetzung für die Durchführung betriebskritischer
    Prozesse
  - Relevanz für die Erreichung betriebswichtiger Zertifizierungen.

Mögliche Auswirkungen der Nicht-Verfügbarkeit oder des Datenverlusts der
Webanwendungen beinhalten z. B.:

  - Unterbrechung betrieblicher Prozesse (auch bei Kunden oder Partnern)
  - Imageverlust
  - Schadenersatzforderungen
  - Entzug von Genehmigungen
  - Verlust von Betriebsgeheimnissen.

Andere Aspekte wie Risiken und Kosten siehe 4.3 und 6.4.

## Technische Aspekte jeder einzelnen Webapplikation des Unternehmens

Die Entscheidung über geeignete Sicherheitsmaßnahmen für eine
Webapplikation ist maßgeblich von der jeweiligen Phase der Anwendung im
Entwicklungsprozess abhängig. So können in der Designphase noch
geeignete Werkzeuge für die Implementierung sowie Test- und
Quality-Assurance-Tools ausgewählt werden, ggfs. können auch noch die
Entwickler hinsichtlich Web Application Security geschult und die
relevanten Zeitschienen bis zur Produktivsetzung verlängert werden.

Für bereits fertig gestellte oder produktive Anwendungen sind
hinsichtlich nachträglich möglicher Sicherheitsmaßnahmen ganz andere
Punkte von Bedeutung, wie z. B.:

  - vollständige Dokumentation der Architektur und des Sourcecodes bzw.
    Verfügbarkeit der Entwickler der Webapplikation
  - Wartungsverträge für alle Komponenten der Anwendungsarchitektur
  - kurze Fehlerbehebungszeiten durch den Hersteller von eingesetzten
    Dritt-Produkten

Nur falls diese Punkte erfüllt sind, kann überhaupt - ohne Betrachtung
des entstehenden Aufwands - eine Absicherung der Applikation innerhalb
der bestehenden Anwendungsinfrastruktur erfolgen.

# Fähigkeiten von Web Application Firewalls (WAFs) im Überblick

## Einordnung von WAFs im Gesamtbereich Web Application Security

Grundsätzlich gilt, dass jede Webapplikation möglichst sicher entwickelt
werden sollte. Denn je später eine Schwachstelle im Lebenszyklus einer
Webapplikation erkannt wird, desto höher ist das damit verbundene Risiko
eines Einbruchs - und oft auch der Aufwand für die Behebung.

Neben entsprechenden Trainingsmaßnahmen z. B. anhand der
OWASP-Richtlinien wird die Applikations-Entwicklung hier durch
verschiedene Werkzeuge wirkungsvoll unterstützt. Tools wie z. B.
*Stinger* sind in der Regel auf ein Framework - im Beispiel J2EE -
bezogen; sie sind Teil der Applikation (auch wenn man sie auch zu
fertigen J2EE-konformen Applikationen hinzufügen kann) und damit
organisatorisch in der Regel dem normalen Applikation-Releasezyklus
unterworfen. Im Kern stellen sie eine wirksame Hilfe für den Entwickler
dar, seine - spezielle - Applikation sicherer zu machen. Im Unterschied
zu WAFs sind sie aber immer eher Teil der Applikation. Diese Tools
werden in diesem Dokument an verschiedenen Stellen, insbesondere beim
Vergleich des Aufwands von verschiedenen Schutzmaßnahmen, erwähnt, sie
sind aber selbst nicht im Fokus des Dokuments.

In der Entwicklungsphase helfen Methoden z. B. der statischen
Sourcecode-Analyse, Schwachstellen des Codes rechtzeitig zu erkennen und
zu beseitigen. Hinzu kommen Penetrationstests - am besten durch
Experten, die auch im Produktivbetrieb Schwachstellen des externen
Verhaltens der Webapplikation aufdecken.

In diesem Zusammenhang ist es die Hauptfunktion einer WAF,
Schwachstellen, die Webapplikationen in ihrem externen Verhalten
aufweisen, mit möglichst geringem Aufwand so abzusichern, dass sie von
Angreifern nicht ausgenutzt werden können. Aufgrund der ohnehin hohen
Komplexität einer typischen Anwendungsinfrastruktur - Webserver,
Applikationsserver, eingesetzte Frameworks - sowie der typischen
Komponenten einer Webapplikation - Session-Handling mit Cookies,
Input-Validation etc. - ist dies bereits eine sehr komplexe Aufgabe.

Haupteinsatzziel einer WAF ist deshalb die nachträgliche Absicherung
bereits bestehender, oft produktiver Webapplikationen, bei denen
notwendige Änderungen innerhalb der Applikation grundsätzlich nicht mehr
oder nur noch mit unverhältnismäßig hohem Aufwand erfolgen kann. Dies
gilt besonders für solche Schwachstellen, die z. B. durch einen
Penetrationstest oder auch durch eine Analyse des Source Codes
aufgedeckt wurden und - insbesondere kurzfristig - nicht innerhalb der
Applikation gefixt werden können. Grundvoraussetzung der WAF ist
hierbei, dass sie - über einen Grundschutz durch ein Blacklisting, also
der Beschreibung bekannter Angriffsmuster hinaus - die Möglichkeit eines
- vernünftig zu bedienenden - Whitelistings anbietet. Beim Whitelisting
beschreibt das Regelwerk der WAF genau von der Anwendung gewünschte
Verhalten; die Konfiguration geeigneter Whitelists wird oft durch
Lernmodi unterstützt.

Darüber hinaus bieten einige WAFs auch Funktionalitäten an, die über den
reinen Absicherungs-Charakter hinausgehen und deshalb auch schon im
Designprozess berücksichtigt werden können, um unnötigen Aufwand zu
vermeiden. Die WAF wird so zur zentralen Servicestelle für die
Erledigung von Aufgaben werden, die naturgemäß auf Seiten der Anwendung
liegen, aber für alle Anwendungen auf gleiche Weise zu lösen sind.
Beispiele hierfür sind das sichere Session-Management für alle
Anwendungen auf der Basis von Cookie-Stores, zentrale Authentisierung
und Autorisierung, die Zusammenführung aller relevanten Fehlermeldungen
und Logfiles oder die Möglichkeit proaktiver Schutzmechanismen wie z.B.
URL-Encryption.

Die folgende Tabelle zeigt anhand der wichtigsten derzeit bekannten
Schwachstellen bzw. Angriffsmethoden von Webapplikationen, welchen
Schutz WAFs hier bieten. Dabei werden in der Regel die genutzten
Funktionen der WAF genannt, wobei nicht unbedingt alle am Markt
angebotenen WAFs über alle genannten Funktionen verfügen.

## Typische Schutzmechanismen von WAFs am Beispiel konkreter Schwachstellen

In der folgenden Tabelle sind für typische Bedrohungen, Schwachstellen
und Angriffe (Spalte Problem) die möglichen Schutzmechanismen (Spalte
Maßnahme) aufgeführt, und in der Spalte WAF bewertet wie gut eine WAF
die Anwendung schützen kann. Die Bewertungen sind:

  - **+** kann eine WAF sehr gut
  - **-** kann die WAF schlecht oder gar nicht
  - **\!** abhängig von WAF/Anwendung/Anforderungen
  - **=** kann teilweise von einer WAF übernommen

<table>
<tbody>
<tr class="odd">
<td><p>Problem</p></td>
<td><center>
<p>WAF</p>
</center></td>
<td><p>Maßnahme</p></td>
</tr>
<tr class="even">
<td><p>Cookieschutz</p></td>
<td><center>
<p>+</p>
</center>
<center>
<p>+</p>
</center>
<center>
<p>!</p>
</center>
<center>
<p>!</p>
</center></td>
<td><p>Cookies können signiert werden</p>
<p>Cookies können verschlüsselt werden</p>
<p>Cookies können vollständig versteckt bzw. ausgetauscht werden (Cookie-Store)</p>
<p>Cookies können an die anfragende IP gebunden werden</p></td>
</tr>
<tr class="odd">
<td><p>Information-Leakage</p></td>
<td><center>
<p>+</p>
</center></td>
<td><p>Cloaking-Filter, ausgehende Seiten können "bereinigt" werden (Fehlermeldungen, Kommentare, unerwünschte Informationen)</p></td>
</tr>
<tr class="even">
<td><p>Session-Riding (CSRF)</p></td>
<td><center>
<p>+</p>
</center></td>
<td><p>URL-Encryption / Token</p></td>
</tr>
<tr class="odd">
<td><p>Session-Timeout</p></td>
<td><center>
<p>!</p>
</center></td>
<td><p>Timeout für aktive und inaktive (idle) Sessions kann festgelegt werden (wenn die WAF die Sessions selbst verwaltet)</p>
<p>Auch wenn die Sessions von der Applikation bereitgestellt werden, kann die WAF diese bei entsprechender Konfiguration erkennen und terminieren.</p></td>
</tr>
<tr class="even">
<td><p>Session-Fixation</p></td>
<td><center>
<p>=</p>
</center></td>
<td><p>kann verhindert werden, wenn die WAF die Sessions selbst verwaltet</p></td>
</tr>
<tr class="odd">
<td><p>Session-Hijacking</p></td>
<td><center>
<p>-</p>
</center></td>
<td><p>Schutz nur schwer möglich, WAF kann aber bei Unregelmäßigkeiten (z. B. wechselnde IP) alarmieren oder bei wechselnder IP die Session terminieren</p></td>
</tr>
<tr class="even">
<td><p>File-Upload</p></td>
<td><center>
<p>+</p>
</center></td>
<td><p>Virenprüfung (meist durch externe Systeme) via ICAP an die WAF angebunden</p></td>
</tr>
<tr class="odd">
<td><p>Parameter-Tampering</p></td>
<td><center>
<p>+</p>
</center>
<center>
<p>+</p>
</center></td>
<td><p>zusätzlich/anstatt Data-Validation (siehe unten) kann Parameter-Manipulation durch URL-Encryption (GET) und Parameter-Encryption (GET- und POST) verhindert werden</p>
<p>Site-Usage-Enforcement, d. h. Reihenfolge der URLs kann festgelegt oder erkannt werden</p></td>
</tr>
<tr class="even">
<td><p>Forced-Browsing</p></td>
<td><center>
<p>+</p>
</center>
<center>
<p>+</p>
</center></td>
<td><p>kann durch URL-Encryption verhindert werden</p>
<p>Site-Usage-Enforcement</p></td>
</tr>
<tr class="odd">
<td><p>Path-Traversal (URL) Link-Validation</p></td>
<td><center>
<p>+</p>
</center>
<center>
<p>+</p>
</center></td>
<td><p>kann durch URL-Encryption verhindert werden</p>
<p>Site-Usage-Enforcement</p></td>
</tr>
<tr class="even">
<td><p>Path-Traversal (Parameter), Path.Manipulation</p></td>
<td><center>
<p>+</p>
</center></td>
<td><p>siehe Parameter-Tampering und Data-Validation</p></td>
</tr>
<tr class="odd">
<td><p>Logging</p></td>
<td><center>
<p>+</p>
</center></td>
<td><p>alle oder nur bestimmte/erlaubte Teile der Daten eines Requests und der damit verbundenen Prüfungen können protokolliert werden</p></td>
</tr>
<tr class="even">
<td><p>Priv. Escalation</p></td>
<td><center>
<p>-</p>
</center></td>
<td><p>Privilege-Escalation kann nicht, bzw. nur bedingt durch z. B. Cookie-/Parameter-Encryption geprüft werden</p></td>
</tr>
<tr class="odd">
<td><p>Logische Ebene</p></td>
<td><center>
<p>-</p>
</center></td>
<td><p>Anwendungslogik, die über die Gültigkeit von URLs und Formfeldern hinausgeht, kann durch eine WAF i. d. R. nicht geprüft werden</p></td>
</tr>
<tr class="even">
<td><p>Anti-Automation</p></td>
<td><center>
<p>=</p>
</center></td>
<td><p>automatische Angriffe können teilweise erkannt und geblockt werden (z. B. Anzahl Requests/Zeitintervall, identische Requests, usw.)</p></td>
</tr>
<tr class="odd">
<td><p>Applikations-DoS (moderat)</p></td>
<td><center>
<p>=</p>
</center>
<center>
<p>=</p>
</center></td>
<td><p>Transaktionen, IP, User blocken</p>
<p>Verbindungen, Sessions können beendet werden</p></td>
</tr>
<tr class="even">
<td><p>SSL</p></td>
<td><center>
<p>+</p>
</center>
<center>
<p>++</p>
</center></td>
<td><p>WAF kann SSL mit vorgegebener Verschlüsselungsstärke erzwingen (je nach Infrastruktur-Szenario)</p>
<p>SSL-Terminierung an der WAF, Weitergabe der SSL-Daten (z. B. Client-Zertifikat) an Anwendung</p>
<p>SSL-Verbindung von WAF zur Anwendung möglich</p></td>
</tr>
<tr class="odd">
<td><p>Data-Validation (bezogen auf Feld/Inhalt/Kontext/Appl)</p></td>
<td><center>
<p>+</p>
</center>
<center>
<p>+</p>
</center>
<center>
<p>!</p>
</center>
<center>
<p>-</p>
</center></td>
<td><p>kann sehr feingranular (Länge, konstanter Wert/Wertebereich z. B. bei SELECT, Zeichenbereich) geprüft werden; Validierung mit Whitelist und/oder Blacklist (Signatur) möglich</p>
<p>Regeln können teilweise automatisch erstellt werden</p>
<p>teilweise hohe Abhängigkeit zur Anwendung, bestimmte Felder (hidden Form) bzw. vorgegebene Parameter in der URL können aber von der WAF automatisch verifiziert werden</p>
<p>Gefahr durch <em>false positives</em>, insbesondere bei geschäftskritische Anwendungen problematisch</p></td>
</tr>
<tr class="even">
<td><p>Data-Validation (generell/global)</p></td>
<td><center>
<p>+</p>
</center></td>
<td><p>HTTP(w3c)-Konformität, eine WAF führt eine Kanonalisierung der Daten durch, so dass sie der Anwendung in normalisierter Form vorliegen</p></td>
</tr>
<tr class="odd">
<td><p>Buffer-Overflow</p></td>
<td><center>
<p>+</p>
</center></td>
<td><p>siehe Data-Validation [[1]]</p></td>
</tr>
<tr class="even">
<td><p>Format-String-Attack</p></td>
<td><center>
<p>=</p>
</center></td>
<td><p>kann mittels Data-Validation erkannt werden, wenn entsprechende Zeichen oder Strings gefiltert werden (in der Praxis schwierig, da dazu genaue Kenntnis der Funktionsweise der Anwendung erforderlich ist)</p>
<p>Für einen Großteil der Hidden Input Felder kann dies auch ohne Kenntnisse der Anwendung geschehen</p></td>
</tr>
<tr class="odd">
<td><p>Cross-Site-Scripting</p></td>
<td><center>
<p>=</p>
</center></td>
<td><p>mittels Data-Validation kann nur <em>reflected XSS</em> erkannt und verhindert werden, <em>persistent XSS</em> kann nicht erkannt werden, <em>DOM-based XSS</em> nur bedingt, wenn ein Teil des Angriffs in Parametern des Requests transportiert wird</p></td>
</tr>
<tr class="even">
<td><p>Cross-Site-Tracing</p></td>
<td><center>
<p>+</p>
</center></td>
<td><p>Beschränkung der HTTP-Methode auf z. B. GET, POST</p></td>
</tr>
<tr class="odd">
<td><p>WebDAV</p></td>
<td><center>
<p>+</p>
</center></td>
<td><p>Beschränkung auf z. B. nur lesende WebDAV-Methoden</p></td>
</tr>
<tr class="even">
<td><p>Code-Injection (PHP, perl, java)</p></td>
<td><center>
<p>+</p>
</center></td>
<td><p>siehe Data-Validation [[2]]</p></td>
</tr>
<tr class="odd">
<td><p>Command-Injection</p></td>
<td><center>
<p>+</p>
</center></td>
<td><p>siehe Data-Validation [[3]]</p></td>
</tr>
<tr class="even">
<td><p>SQL-Injection</p></td>
<td><center>
<p>+</p>
</center></td>
<td><p>siehe Data-Validation [[4]]</p></td>
</tr>
<tr class="odd">
<td><p>LDAP-Injection</p></td>
<td><center>
<p>+</p>
</center></td>
<td><p>siehe Data-Validation [[5]]</p></td>
</tr>
<tr class="even">
<td><p>XML-/XPath-Injection</p></td>
<td><center>
<p>+</p>
</center></td>
<td><p>siehe Data-Validation [[6]]</p></td>
</tr>
<tr class="odd">
<td><p>just-in-time-Patching(Hotfix-Patching)</p></td>
<td><center>
<p>+</p>
</center></td>
<td><p>mittels Data-Validation (siehe oben) können neu erkannte Schwachstellen und/oder Angriffe (<em>Zero Day Exploit</em>) in der WAF abgewehrt werden</p></td>
</tr>
<tr class="even">
<td><p>HTTP-Response-Splitting</p>
<p>(HTTP-Splitting)</p></td>
<td><center>
<p>!</p>
</center></td>
<td><p>kann mittels Data-Validation in URL und/oder Parametern nur dann erkannt werden, wenn <em>%0d%0a</em> gefiltert wird - dies kann aber auf fast allen Eingabefeldern gemacht werden, ohne die Funktionalität der Applikation zu beeinträchtigen</p></td>
</tr>
<tr class="odd">
<td><p>HTTP-Request-Smuggling[7]</p></td>
<td><center>
<p>+</p>
</center></td>
<td><p>wird durch strenge Prüfung der Standardkonformität jedes Requests verhindert</p></td>
</tr>
</tbody>
</table>

# Nutzen und Risiken von Web Application Firewalls im Überblick

Die hier dargestellten Nutzenpotenziale von WAFs werden insbesondere
anhand des detaillierten Überblicks im nächsten Kapitel ausführlich
begründet. Dieses Kapitel dient vornehmlich der Zusammenfassung für
Entscheider, die das folgende Kapitel nur im Überblick durcharbeiten
wollen.

## Hauptnutzen von WAFs

Der Hauptnutzen von WAFs liegt in der nachträglichen Absicherung des
externen Verhaltens von bereits fertig gestellten, produktiven
Webapplikationen mit vertretbarem Aufwand und ohne Änderung der
Applikation selbst.

Dies gilt einerseits mit einer Art *Grundschutz* gegen bekannte
Angriffsmethoden bzw. Schwachstellen auf der Basis von Blacklists: So
sieht z. B. der Datensicherheitsstandard der Kreditkartenindustrie (PCI
DSS v.1.1) in seiner derzeit gültigen Version den Einsatz einer WAF -
alternativ zu regelmäßigen Code-Reviews durch Spezialisten - als
ausreichende Maßnahme zum Schutz der verwendeten Webapplikationen vor.
Die WAF ist also hier ein geeignetes Werkzeug zur Einhaltung von
Industrie-Standards bzw. auch von rechtlichen Vorgaben.

Besonders deutlich wird der Nutzen von WAFs im Falle von z. B. durch
Penetrationstests oder Sourcecode-Reviews entdeckter konkreter
Schwachstellen. Selbst wenn die Schwachstelle in der Applikation zeitnah
und mit vertretbarem Aufwand gefixt werde könnte, so kann die geänderte
Version meist erst im nächsten Wartungsintervall, oft 2-4 Wochen später,
eingespielt werden (Patch-Dilemma). Bei einer WAF mit Whitelisting kann
hier zeitnah die Schwachstelle nach außen gefixt werden (Hotfix), so
dass sie bis zur nächsten planmäßigen Wartung nicht ausgenutzt werden
kann. Besonders schnell sind hier WAFs, die z. B. mit Source Code
Analyse-Tools so zusammenarbeiten können, dass erkannte Schwachstellen
automatisch zu Regelvorschlägen für die WAF führen.

Besondere Bedeutung kommt einer WAF im Falle von produktiven
Webapplikationen zu, die selbst wiederum aus vielen Komponenten
bestehen, die durch den Betreiber nicht rasch geändert werden können -
z. B. im Falle von schlecht dokumentierten Anwendungen oder eingesetzten
Dritt-Produkten ohne hinreichende Wartungszyklen. Hier ist eine WAF die
einzige Möglichkeit, zeitnah Schwachstellen - nach außen - abfangen zu
können.

## Zusatznutzen von WAFs - abhängig von deren Funktionalitäten

Weitere erhebliche Nutzenpotentiale sind in der zentralen Rolle der WAF
begründet. Die Fehlersuche wird erheblich erleichtert, wenn bei vielen
Anwendungen nicht jede einzelne separat Fehlermeldungen generiert,
sondern diese zentral an der WAF zur Verfügung stehen und dort
ausgewertet werden können. Gleiches gilt z. B. für alle Aspekte des
Monitoring und Reporting. Als zentrale Servicestelle kann die WAF
Aufgaben übernehmen, die für jede Anwendung auf gleiche Weise zu lösen
sind. Ein gutes Beispiel hierfür ist das sichere Session-Management für
alle Anwendungen auf der Basis von Cookie Stores.

Viele WAFs bieten auch proaktive Schutzmechanismen wie z. B.
URL-Encryption oder Site-Usage-Enforcement, um die Angriffsfläche mit
geringem Aufwand möglichst zu minimieren. Zudem erhöht der Einsatz einer
WAF die Robustheit der Webanwendungen nach außen.

Je nach Implementierungsart bieten WAFs auch weiteren Zusatznutzen. Eine
Hardware-Appliance vor den Webservern kann oft SSL-Verbindungen
terminieren und verfügt auch über Loadbalancer-Fähigkeiten. Dies ist
manchmal im Unternehmen wünschenswert, kann aber auch durch
entsprechende Web-Application-Security-Add-Ons bereits eingesetzter
Produkte geleistet werden. In Hochsicherheitsumgebungen verbieten jedoch
häufig die vorhandenen Sicherheitsrichtlinien die Terminierung von
SSL-Verbindungen vor den Webservern. Hier sind dann WAFs, die als
Plug-In in den Webserver implementiert werden, besonders geeignet.

Die WAF kann auch eine SSL-Terminierung bereitstellen, wenn die zu
schützende Anwendung bzw. deren Web- oder Applikationsserver diese
Fähigkeit nicht hat.

## Risiken beim Einsatz von WAFs

Beim Einsatz einer WAF ist zu beachten, dass ein Eingriff in die
vorhandene IT-, Web- und evtl. Applikations-Infrastruktur erforderlich
ist. Je nach Ausführung der WAF - z. B. Hardware-Appliance vs. Embedded
WAF - zeichnen sich auch Mehraufwände und Risiken ab:

  - yet-another-proxy-Argument (erhöhte Komplexität der
    IT-Infrastruktur)
  - Organisatorische Aufwände (siehe 8.2 Rollenmodell beim Betrieb von
    WAFs)
  - Trainingsaufwand
      - Bei jedem Releasewechsel der Webanwendung
      - Testaufwände
  - False Positives (mit u. U. hohem Business-Impact)
  - Komplexere Fehlersuche
      - Auch WAFs haben/machen Fehler
      - Zuständigkeit, Verantwortlichkeit bei systemübergreifenden
        Fehlersituationen
  - Evtl. Einfluss auf die Webanwendung wenn die WAF z. B. die
    Anwendungssession terminiert
  - Wirtschaftlichkeit

# Schutz gegen OWASP-TOP10 - WAFs und andere Methoden im Vergleich

Dieses Kapitel befasst sich mit den verschiedenen Schutzmöglichkeiten
für die sogenannten *OWASP-Top10-Schwachstellen*. Dabei werden
exemplarisch drei verschiedene Webanwendungsklassen zugrunde gelegt:

  - T1: eine Webanwendung in der Design-Phase, neue Anwendung
  - T2: eine bereits produktive Anwendung (z. B. mit MVC-Architektur),
    die einfach anpassbar ist
  - T3: eine produktive Anwendung, die nicht oder nur sehr schwer
    anpassbar ist

Am Beispiel dieser drei Klassen werden Schutzmaßnahmen innerhalb der
Applikation bzw. der Applikations-Architektur selbst, unter Einsatz von
WAFs sowie durch Vorgaben einer entsprechenden Policy detailliert
dargestellt sowie hinsichtlich des hierfür nötigen Aufwands bewertet. An
einigen Stellen finden sich Hinweise auf spezielle Funktionalitäten von
WAFs bzw. Annahmen über die verwendete Applikations-Infrastruktur, da
diese nicht allgemein zutreffen.

Wie die unten aufgeführte Tabelle deutlich zeigt, ist der Einsatz von
WAFs gerade im Falle bereits produktiver Anwendungen sehr häufig mit dem
geringsten Aufwand verbunden. Im Falle von bereits produktiven
Anwendungen, die nicht oder nur schwer anpassbar sind, ist der Einsatz
von WAFs in einigen Punkten sogar die einzig mögliche Schutzmaßnahme.

In der folgenden Tabelle sind für die Bedrohungen (Spalte Top 10)
Kommentare und Hinweise (Spalte Kommentar) für die jeweiligen
Anwendungsklassen T1, T2, T3, den Einsatz einer WAF oder durch Umsetzung
einer Policy (Spalte Typ) aufgeführt, und bewertet (Spalte Aufwand) wie
groß der für eine sichere Implementierung notwendige Aufwand jeweils
ist. Die Bewertungen sind:

  - **1** mit geringem Aufwand
  - '''2 '''mit mittlerem Aufwand
  - '''3 '''mit hohem Aufwand)
  - '''- '''gewöhnlich nicht umsetzbar

<table>
<tbody>
<tr class="odd">
<td><p>colspan="2"</p></td>
<td><center>
<p><strong>Top10</strong></p>
</center></td>
<td><center>
<p><strong>Typ</strong></p>
</center></td>
<td><p><strong>Kommentar</strong></p></td>
<td><center>
<p><strong>Aufwand</strong></p>
</center></td>
</tr>
<tr class="even">
<td><center>
<p>A1</p>
</center></td>
<td><p>Cross-Site Scripting (XSS)</p></td>
<td><p>colspan="3"</p></td>
<td><table>
<tbody>
<tr class="odd">
<td><center>
<p>T1</p>
</center></td>
<td><p>z. B. durch konsequenten Taglib-Einsatz (Java), oder Controls (ASP.NET), zusätzlicher Frameworks (PHPIDS).</p></td>
<td><center>
<p>1</p>
</center></td>
</tr>
<tr class="even">
<td><center>
<p>T2</p>
</center></td>
<td><p>Eingabe-Enkodierung lässt sich nur schwer (z. B. mittels OWASP Stinger) einbauen, besser geht es hier mit einer vorgelagerten WAF. Bei .NET-Anwendungen lässt sich XSS-Filter aktivieren.</p></td>
<td><center>
<p>3</p>
</center>
<center>
<p>(.NET: 2)</p>
</center></td>
</tr>
<tr class="odd">
<td><center>
<p>T3</p>
</center></td>
<td><p>Bei .NET-Anwendungen XSS-Filter aktivieren.</p></td>
<td><center>
<p>-(.NET: 2)</p>
</center></td>
</tr>
<tr class="even">
<td><center>
<p>WAF</p>
</center></td>
<td><p>WAF ermöglicht in diesem Fall keine Ausgabevalidierung, da sie den Kontext der Daten nicht kennt. Die Validierung muss schon bei der Eingabe erfolgen und kann eventuell mit der Ausgabe korreliert werden</p></td>
<td><center>
<p>2</p>
</center></td>
</tr>
<tr class="odd">
<td><center>
<p>P</p>
</center></td>
<td></td>
<td><center>
<p>-</p>
</center></td>
</tr>
</tbody>
</table></td>
<td></td>
</tr>
<tr class="odd">
<td><center>
<p>A2</p>
</center></td>
<td><p>Injection Flaws</p></td>
<td><p>colspan="3"</p></td>
<td><table>
<tbody>
<tr class="odd">
<td><center>
<p>T1</p>
</center></td>
<td><p>Kann durch Verwendung eines OR-Mappers (z. B. Hibernate) oder konsequente Parametrisierung aller Eingaben (z. B. Stored Procedures oder besser: Prepared Statements) vermieden werden. Andere Injection Flaws (z. B. bei XML) lassen sich ggf. nur mit dedizierter Ausgabenkodierung vermeiden.</p></td>
<td><center>
<p>1</p>
</center></td>
</tr>
<tr class="even">
<td><center>
<p>T2</p>
</center></td>
<td><p>Aufwendig, da programmatische Anpassungen notwendig.</p></td>
<td><center>
<p>3</p>
</center></td>
</tr>
<tr class="odd">
<td><center>
<p>T3</p>
</center></td>
<td><p>-</p></td>
<td><center>
<p>-</p>
</center></td>
</tr>
<tr class="even">
<td><center>
<p>WAF</p>
</center></td>
<td><p>WAF mit Blacklisting:</p>
<p>kann hier prinzipiell nur nach bestimmten Zeichen oder Zeichenketten suchen und die Verarbeitung vermeiden. Probleme bestehen bei diesem Ansatz grundsätzlich im Abdeckungsgrad sowie bei möglichen Filter-Evasion-Angriffen (z. B. bei Mehrfachkodierung) falls keine Eingabenormalisierung stattfindet. Das funktioniert sehr gut bei bekannten Angriffen (z. B. SQL-Injection), aber sicherlich weniger gut bei der WAF unbekannten bzw. proprietären Protokollen.</p>
<p>Zusätzlich können durch URL Encryption und Hidden-Form-Parameter-Protection Injection-Angriffe auf einen Teil der Eingabedaten wirksam verhindert werden. Ein Beispiel hierfür sind Artikelnummern in einem Webshop, die klassischerweise gerne für SQL-Injection Angriffe benutzt werden, jedoch eigentlich nie für den Benutzer direkt manipulierbar sein müssen.</p>
<p>WAF mit Whitelisting:</p>
<p>Für alle anderen Eingabefelder bietet sich ein Whitelist-Ansatz an. Hier kann die WAF nach einer Lernphase Vorschläge für die einzelnen Felder vorgeben. Damit lassen sich zwar nicht alle, aber ein Großteil der Eingabefelder gegen alle Arten von Injection-Angriffen absichern.</p></td>
<td><center>
<p>2</p>
</center></td>
</tr>
<tr class="odd">
<td><center>
<p>P</p>
</center></td>
<td><p>Im Falle von SQL-Injection: Vorgaben für Datenbankzugriffsrechte, sonst wenig bis keine Möglichkeit.</p></td>
<td><center>
<p>-</p>
</center></td>
</tr>
</tbody>
</table></td>
<td></td>
</tr>
<tr class="even">
<td><center>
<p>A3</p>
</center></td>
<td><p>Malicious File Execution</p></td>
<td><p>colspan="3"</p></td>
<td><table>
<tbody>
<tr class="odd">
<td><center>
<p>T1</p>
</center></td>
<td><p>Einbinden von Uploadscannern bzw. Whitelisting der erlaubten remote inclusions,</p></td>
<td><center>
<p>2</p>
</center></td>
</tr>
<tr class="even">
<td><center>
<p>T2</p>
</center></td>
<td></td>
<td><center>
<p>3</p>
</center></td>
</tr>
<tr class="odd">
<td><center>
<p>T3</p>
</center></td>
<td><p>-</p></td>
<td><center>
<p>-</p>
</center></td>
</tr>
<tr class="even">
<td><center>
<p>WAF</p>
</center></td>
<td><p>Whitelisting der Parameter für das erlaubte Einbinden von systemfremden URL</p>
<p>- Einbinden von Upload Scannern via ICAP Protokoll</p>
<p>- Responseanalyse, um das Anzeigen kritischer Daten (teilweise auch Fehlermeldungen) zu verhindern.</p></td>
<td><center>
<p>1-2</p>
</center></td>
</tr>
<tr class="odd">
<td><center>
<p>P</p>
</center></td>
<td><p>Vorgaben für Deploymentplattform, Vorgaben für Zugriffsrechte</p></td>
<td><center>
<p>2</p>
</center></td>
</tr>
</tbody>
</table></td>
<td></td>
</tr>
<tr class="odd">
<td><center>
<p>A4</p>
</center></td>
<td><p>Insecure Direct Object Reference</p></td>
<td><p>colspan="3"</p></td>
<td><table>
<tbody>
<tr class="odd">
<td><center>
<p>T1</p>
</center></td>
<td><p>Implementierung einer Objekt-Virtualisierung ist sehr aufwendig, da Datenbank-Objekte häufig von verwendeten Frameworks auf Parameter abgebildet werden (OR-Mapper). Schutz erfordert zahlreiche programmatische Prüfungen.</p></td>
<td><center>
<p>3</p>
</center></td>
</tr>
<tr class="even">
<td><center>
<p>T2</p>
</center></td>
<td><p>Verhinderung von ID-Manipulation macht meist Code-Anpassungen notwendig. Schutz erfordert zahlreiche programmatische Prüfungen.</p></td>
<td><center>
<p>3</p>
</center></td>
</tr>
<tr class="odd">
<td><center>
<p>T3</p>
</center></td>
<td><p>-</p></td>
<td><center>
<p>-</p>
</center></td>
</tr>
<tr class="even">
<td><center>
<p>WAF</p>
</center></td>
<td><p>Schutz vor ID-Manipulation mittels ID-Virtualisierung bzw. hidden Parameter-Protection.</p></td>
<td><center>
<p>1</p>
</center></td>
</tr>
<tr class="odd">
<td><center>
<p>P</p>
</center></td>
<td><p>Verwenden von Impersonifikation und Delegation.</p></td>
<td><center>
<p>3</p>
</center></td>
</tr>
</tbody>
</table></td>
<td></td>
</tr>
<tr class="even">
<td><center>
<p>A5</p>
</center></td>
<td><p>Cross-Site Request Forgery (CSRF)</p></td>
<td><p>colspan="3"</p></td>
<td><table>
<tbody>
<tr class="odd">
<td><center>
<p>T1</p>
</center></td>
<td><p>Mit spezifischer Anwendungsarchitektur lösbar.</p></td>
<td><center>
<p>1</p>
</center></td>
</tr>
<tr class="even">
<td><center>
<p>T2</p>
</center></td>
<td><p>Hoher Aufwand. Meistens programmatische Änderungen erforderlich.</p></td>
<td><center>
<p>3</p>
</center></td>
</tr>
<tr class="odd">
<td><center>
<p>T3</p>
</center></td>
<td><p>-</p></td>
<td><center>
<p>-</p>
</center></td>
</tr>
<tr class="even">
<td><center>
<p>WAF</p>
</center></td>
<td><p>Kann mittels Page-Token oder URL-Encryption unterbunden werden.</p></td>
<td><center>
<p>1</p>
</center></td>
</tr>
<tr class="odd">
<td><center>
<p>P</p>
</center></td>
<td></td>
<td><center>
<p>-</p>
</center></td>
</tr>
</tbody>
</table></td>
<td></td>
</tr>
<tr class="odd">
<td><center>
<p>A6.1</p>
</center></td>
<td><p>Information Leakage</p></td>
<td><p>colspan="3"</p></td>
<td><table>
<tbody>
<tr class="odd">
<td><center>
<p>T1</p>
</center></td>
<td><p>Toolgestütztes Testen mit hoher Testabdeckung und entsprechendem Fokus.</p></td>
<td><center>
<p>2</p>
</center></td>
</tr>
<tr class="even">
<td><center>
<p>T2</p>
</center></td>
<td><p>Toolgestütztes Testen mit hoher Testabdeckung und entsprechendem Fokus.</p></td>
<td><center>
<p>2</p>
</center></td>
</tr>
<tr class="odd">
<td><center>
<p>T3</p>
</center></td>
<td><p>-</p></td>
<td><center>
<p>-</p>
</center></td>
</tr>
<tr class="even">
<td><center>
<p>WAF</p>
</center></td>
<td><p>Automatisches Ausfiltern von Kommentaren möglich.</p>
<p>Site Usage Enforcement kann den Zugriff auf vorhandene aber nichtveröffentlichte (nicht verlinkte) Dokumente verhindern. Klassisches Beispiel sind Backup Files auf dem Webserver, die Datenbankpasswörter im Klartext enthalten und deren URL vom Angreifer geraten wird.</p></td>
<td><center>
<p>1-2</p>
</center></td>
</tr>
<tr class="odd">
<td><center>
<p>P</p>
</center></td>
<td><p>Vorgaben für Programmierer und Autoren, keine Kommentare einzutragen. Vorgaben für die Gestaltung von Fehlermeldungen.</p></td>
<td><center>
<p>2</p>
</center></td>
</tr>
</tbody>
</table></td>
<td></td>
</tr>
<tr class="even">
<td><center>
<p>A6.2</p>
</center></td>
<td><p>Improper Error Handling</p></td>
<td><p>colspan="3"</p></td>
<td><table>
<tbody>
<tr class="odd">
<td><center>
<p>T1</p>
</center></td>
<td><p>Je nach Plattform deklarativ konfigurierbar.</p></td>
<td><center>
<p>1</p>
</center></td>
</tr>
<tr class="even">
<td><center>
<p>T2</p>
</center></td>
<td><p>Je nach Plattform deklarativ konfigurierbar.</p></td>
<td><center>
<p>1</p>
</center></td>
</tr>
<tr class="odd">
<td><center>
<p>T3</p>
</center></td>
<td><p>Je nach Plattform deklarativ konfigurierbar.</p></td>
<td><center>
<p>1 / -</p>
</center></td>
</tr>
<tr class="even">
<td><center>
<p>WAF</p>
</center></td>
<td><p>Schwer zu erkennen.</p></td>
<td><center>
<p>2</p>
</center></td>
</tr>
<tr class="odd">
<td><center>
<p>P</p>
</center></td>
<td><p>-</p></td>
<td><center>
<p>-</p>
</center></td>
</tr>
</tbody>
</table></td>
<td></td>
</tr>
<tr class="odd">
<td><center>
<p>A7.1</p>
</center></td>
<td><p>Broken Authentication</p></td>
<td><p>colspan="3"</p></td>
<td><table>
<tbody>
<tr class="odd">
<td><center>
<p>T1</p>
</center></td>
<td><p>Anbindung an ein zentrales Access Management System mit angemessenen Sicherheitsstandards</p></td>
<td><center>
<p>1</p>
</center></td>
</tr>
<tr class="even">
<td><center>
<p>T2</p>
</center></td>
<td><p>Anbindung an ein zentrales Access Management System mit angemessenen Sicherheitsstandards. Evtl. programmatische Anpassungen erforderlich.</p></td>
<td><center>
<p>2</p>
</center></td>
</tr>
<tr class="odd">
<td><center>
<p>T3</p>
</center></td>
<td><p>-</p></td>
<td><center>
<p>-</p>
</center></td>
</tr>
<tr class="even">
<td><center>
<p>WAF</p>
</center></td>
<td><p>Abhängig von Fähigkeiten der WAF.</p>
<p>WAF kann Authentisierung unabhängig von der Applikation vornehmen und damit ohne Änderung der Applikation eine Anbindung an eine zentrale Authentisierungsinfrastruktur ermöglichen.</p></td>
<td><center>
<p>2</p>
</center></td>
</tr>
<tr class="odd">
<td><center>
<p>P</p>
</center></td>
<td><p>Vorgaben hinsichtlich Passwortkomplexität.</p></td>
<td><center>
<p>2</p>
</center></td>
</tr>
</tbody>
</table></td>
<td></td>
</tr>
<tr class="even">
<td><center>
<p>A7.2</p>
</center></td>
<td><p>Session Management</p></td>
<td><p>colspan="3"</p></td>
<td><table>
<tbody>
<tr class="odd">
<td><center>
<p>T1</p>
</center></td>
<td><p>Auf Designebene z. B. mittels Session-Manager-Design-Pattern, sonst zahlreiche Möglichkeiten. Implementierungsaufwand teilweise abhängig von Applikationsserver, siehe auch Brok, wenn das Session-Management vom Access-Management-System übernommen wird.</p></td>
<td><center>
<p>2</p>
</center></td>
</tr>
<tr class="even">
<td><center>
<p>T2</p>
</center></td>
<td><p>größtenteils zentral einbaubar (mittels Filter, Listener oder gehärteter Serverkonfiguration); dennoch teilweise großer Implementierungs- und Testaufwand; siehe auch Brok, wenn das Session Management vom Access Management System übernommen wird.</p></td>
<td><center>
<p>2-3</p>
</center></td>
</tr>
<tr class="odd">
<td><center>
<p>T3</p>
</center></td>
<td><p>Abhängig vom Applikationsserver, teilweise konfigurierbar.</p></td>
<td><center>
<p>-</p>
</center></td>
</tr>
<tr class="even">
<td><center>
<p>WAF</p>
</center></td>
<td><p>Härtung eines unsicheren Session-Managements über verschiedene Techniken möglich (z. B. Page-Tokens).</p></td>
<td><center>
<p>1</p>
</center></td>
</tr>
<tr class="odd">
<td><center>
<p>P</p>
</center></td>
<td><p>-</p></td>
<td><center>
<p>-</p>
</center></td>
</tr>
</tbody>
</table></td>
<td></td>
</tr>
<tr class="odd">
<td><center>
<p>A8</p>
</center></td>
<td><p>Insecure Cryptographic Storage</p></td>
<td><p>colspan="3"</p></td>
<td><table>
<tbody>
<tr class="odd">
<td><center>
<p>T1</p>
</center></td>
<td><p>Verwendung von Crypto-APIs.</p></td>
<td><center>
<p>1</p>
</center></td>
</tr>
<tr class="even">
<td><center>
<p>T2</p>
</center></td>
<td><p>Verwendung von Crypto-APIs. Nachträgliche Implementierung erfordert zahlreiche programmatische Anpassungen.</p></td>
<td><center>
<p>3</p>
</center></td>
</tr>
<tr class="odd">
<td><center>
<p>T3</p>
</center></td>
<td><p>-</p></td>
<td><center>
<p>-</p>
</center></td>
</tr>
<tr class="even">
<td><center>
<p>WAF</p>
</center></td>
<td><p>-</p></td>
<td><center>
<p>-</p>
</center></td>
</tr>
<tr class="odd">
<td><center>
<p>P</p>
</center></td>
<td><p>Vorgaben zur Speicherung von sensiblen Daten.</p></td>
<td><center>
<p>-</p>
</center></td>
</tr>
</tbody>
</table></td>
<td></td>
</tr>
<tr class="even">
<td><center>
<p>A9</p>
</center></td>
<td><p>Insecure Communiations</p></td>
<td><p>colspan="3"</p></td>
<td><table>
<tbody>
<tr class="odd">
<td><center>
<p>T1</p>
</center></td>
<td><p>Deklarativ im Applikations- bzw. Webserver konfigurierbar.</p></td>
<td><center>
<p>1</p>
</center></td>
</tr>
<tr class="even">
<td><center>
<p>T2</p>
</center></td>
<td><p>Deklarativ im Applikations- bzw. Webserver konfigurierbar. Sehr hoher Aufwand wenn URL-Schema (HTTP) hardcoded wurde.</p></td>
<td><center>
<p>1 / -</p>
</center></td>
</tr>
<tr class="odd">
<td><center>
<p>T3</p>
</center></td>
<td><p>Deklarativ im Applikations- bzw. Webserver konfigurierbar (wenn Zugang besteht). Nicht möglich, wenn URL-Schema (HTTP) hardcoded wurde.</p></td>
<td><center>
<p>1 / -</p>
</center></td>
</tr>
<tr class="even">
<td><center>
<p>WAF</p>
</center></td>
<td><p>Kann HTTP-Anwendungen mit HTTPS absichern.</p></td>
<td><center>
<p>1</p>
</center></td>
</tr>
<tr class="odd">
<td><center>
<p>P</p>
</center></td>
<td><p>-</p></td>
<td><center>
<p>-</p>
</center></td>
</tr>
</tbody>
</table></td>
<td></td>
</tr>
<tr class="odd">
<td><center>
<p>A10</p>
</center></td>
<td><p>Failure to Restrict URL Access</p></td>
<td><p>colspan="3"</p></td>
<td><table>
<tbody>
<tr class="odd">
<td><center>
<p>T1</p>
</center></td>
<td><p>Verwendung eines Front Controllers mit Gateway. Code muss dennoch an verschiedenen Stellen (z.B. im Service) Benutzerzugehörigkeit programmatisch prüfen. Lücken möglich.</p></td>
<td><center>
<p>1-2</p>
</center></td>
</tr>
<tr class="even">
<td><center>
<p>T2</p>
</center></td>
<td><p>Je nach Anwendung unterschiedlich. URL-Zugriffsrechte bei J2EE und .NET deklarativ konfigurierbar. Verhinderung von ID-Manipulation macht meist Code-Anpassungen notwendig.</p></td>
<td><center>
<p>2-3</p>
</center></td>
</tr>
<tr class="odd">
<td><center>
<p>T3</p>
</center></td>
<td><p>Je nach Anwendung unterschiedlich. URL-Zugriffsrechte bei J2EE und .NET deklerativ konfigurierbar.</p></td>
<td><center>
<p>3</p>
</center></td>
</tr>
<tr class="even">
<td><center>
<p>WAF</p>
</center></td>
<td><p>Benutzer kann mittels Page-Token oder URL-Encryption auf Seiten eingeschränkt werden, die er von der Anwendung als Link erhält. Die Anwendung darf hierzu allerdings geschützte Links nicht anzeigen (Limited-Access-Pattern).</p>
<p>Mit Site-Usage-Enforcement kann der Benutzer nur auf verlinkten Content gelangen. Auch können bestimmte URLs/Teilbäume durch Whitelist/Blacklist Ansätze ausgeschlossen werden (z. B. allow access nur für *.html, *.php, *.gif, *.jpg - aber nicht für *.bak oder andere Extensions).</p></td>
<td><center>
<p>1</p>
</center></td>
</tr>
<tr class="odd">
<td><center>
<p>P</p>
</center></td>
<td><p>-</p></td>
<td><center>
<p>-</p>
</center></td>
</tr>
</tbody>
</table></td>
<td></td>
</tr>
</tbody>
</table>

# Kriterien zur Einsatz-Entscheidung von WAFs

## Unternehmensweite Kriterien

Kernkriterien in diesem Bereich sind:

  - Bedeutung der Webapplikation(en) für den Unternehmenserfolg
    (Umsatzanteil, Image)
  - Bedeutung des Verlusts der Daten der Webapplikation (Kundendaten,
    Unternehmens­geheimnisse, Image)
  - Anzahl der Webapplikationen
  - rechtliche Rahmenbedingungen bzw. Industriestandards
  - Komplexität
  - Betriebsaufwände
  - Performance
  - Skalierbarkeit

## Kriterien hinsichtlich einer Webapplikation

Im Folgenden wird der Begriff des *Zugriffs* des Unternehmens auf die
Webapplikation eingeführt und erläutert. Die Checkliste im Anhang 8.1
dient dazu, für jede Webapplikation den Grad des Zugriffs anhand eines
Punktesystems individuell zu bestimmen.

Der *Zugriff des Unternehmens auf eine Webapplikation* soll ein Maß
dafür sein, inwieweit das Unternehmen notwendige Änderungen der
Webapplikation - also letztlich des Sourcecodes der Applikation -
zeitnah selbst durchführen bzw. veranlassen und durchsetzen kann.

Eine Webapplikation in der Design-Phase (siehe T1 in 5) kann hier als
Spezialfall einer *Webapplikation mit optimalem Zugriff* betrachtet
werden.

Das andere Extrem einer *Webapplikation ohne Zugriff* ist beispielsweise
eine Applikation, die aus vielen nicht dokumentierten Komponenten
besteht, deren Entwickler ebenfalls nicht mehr kontaktiert werden können
und die Dritt-Softwareprodukte verwendet, die seitens des Herstellers -
bei Open-Source-Projekten seitens der Community - nicht mehr gepflegt
werden (siehe T3 in 5).

Wichtige Kriterien, um das Maß des Zugriffs auf eine Webapplikation zu
bestimmen, sind:

  - vollständige Dokumentation der Architektur und des Sourcecodes bzw.
    Verfügbarkeit auf Entwickler der Webapplikation
  - Wartungsverträge für alle Komponenten der Anwendungsarchitektur
  - kurze Fehlerbehebungszeiten durch den Hersteller von eingesetzten
    Dritt-Produkten (Portale, Frameworks, SAP, usw.).

Weitere wesentliche Kriterien pro Webapplikation sind in der genannten
Checkliste im Anhang aufgeführt.

## Bewertung und Zusammenfassung

Mithilfe der Checkliste im Anhang 8.1 kann der Grad des Zugriffs für
jede Webapplikation ermittelt werden. Daraus lässt sich auch ein
Mittelwert des Zugriffs für alle Webapplikationen eines Unternehmens
ermitteln, wobei allerdings zu beachten ist, dass für den
Unternehmenserfolg oder das Image besonders wichtige Applikationen auch
entsprechend hoch gewichtet werden müssen.

Als Leitfaden bei der Entscheidungsfindung für den Nutzen des Einsatzes
einer WAF im Unternehmen kann dabei folgende Darstellung hilfreich sein:

![Best_Practice_WAF-chart-DE.png](Best_Practice_WAF-chart-DE.png
"Best_Practice_WAF-chart-DE.png")

Hat ein Unternehmen alle Webapplikationen im vollen Zugriff, so bringt
der Einsatz einer WAF vor allem Aufwandsminimierungen im Betrieb -
insbesondere aufgrund der in 3 genannten Zusatznutzen einer WAF als
zentralen Servicestelle sowie einiger vergleichsweise einfach zu
implementierender Schutzmechanismen, siehe 4.

Ist auf die Webapplikationen praktisch kein Zugriff vorhanden, so ist
der Einsatz einer WAF unbedingt sinnvoll, da nur so geeignete
Schutzmaßnahmen implementiert werden können.

Mit abnehmendem Zugriff auf die Webapplikation - und abhängig von ihrer
Bedeutung und Komplexität - wächst der Nutzen aus dem Einsatz einer WAF
sehr rasch - von einer *Second Line of Defense* zu einer echten
*Vollversiegelung* der Webapplikation nach außen mittels Whitelisting -
da eine WAF im Vergleich oft den geringsten Zusatzaufwand für die
notwendige Absicherung verursacht.

## Wirtschaftlichkeitsbetrachtung

Die Wirtschaftlichkeit der Anschaffung und des Betriebs einer WAF kann
aus mehreren Blickwinkeln betrachtet werden:

  - Vermeidung von wirtschaftlichen Schäden durch erfolgreiche Angriffe
    auf Webapplikation
  - Geringere Kosten für die als notwendig erkannte Absicherung von
    Webapplikation gegenüber anderen Optionen
  - Einsparungen durch die Nutzungen von zentralen Diensten die von
    einer WAF für mehrere Webanwendungen zur Verfügung gestellt werden
    und somit nicht mehr in jeder Anwendung selbst implementiert bzw.
    konfiguriert werden müssen.

Bei der Absicherung von Anwendungen, auf die kein ausreichender Zugriff
besteht (siehe 6.2), deren Schutz aber trotzdem als notwendig erachtet
wird können die Kosten für den Einsatz einer WAF entweder als
strategische Investition betrachtet, oder, sofern realitätsnah, gegen
die Kosten einer Ablösung der fraglichen Anwendung gerechnet werden.

Die Kosten für den Einsatz einer WAF setzen sich in der Regel aus den
folgenden Komponenten zusammen:

  - Lizenzkosten
  - Lizenzwartung
  - Projektkosten für die Evaluierung und Einführung einer WAF
  - (anteilige) Kosten für den Betrieb der notwenigen Plattform
  - Personalkosten für den oder die Anwendungsverantwortlichen WAF
  - Aufwände in Projekten für die Abstimmung mit dem
    Anwendungsverantwortlichen WAF.

# Best Practices bei Einführung und Betrieb von WAFs

## Aspekte der vorhandenen Web-Infrastruktur

### Zentrale oder dezentrale Infrastruktur - absehbare Veränderungen

Grundsätzlich ist festzuhalten, dass sich WAFs in die bestehende
Web-Infrastruktur - und deren geplante oder absehbare Veränderungen -
einfügen müssen - und nicht umgekehrt die Infrastruktur wegen der
Implementierung einer WAF grundlegend geändert werden sollte.

Entsprechend kann eine WAF in einer zentralen Infrastruktur, die sich
absehbar nicht wesentlich ändert, auch als zentrale
Infrastruktur-Komponente z. B. als Hardware-Appliance installiert
werden, während bei einer ohnehin bereits dezentralen, möglicherweise
schnell wachsenden Infrastruktur - z. B. bei einem großen Online-Shop -
ein verteilter WAF-Ansatz, z. B. als Plug-In in die vorhandenen
Webserver - besser passend ist. Hinsichtlich der Infrastruktur-Aspekte
besonders flexibel sind WAF-Produkte, die einen grundsätzlich verteilten
Implementationsansatz mit einer zentralen Administration verbinden und
so die Vorteile aus beiden Szenarien verbinden.

Erwähnenswert - und mit Blick auf zukünftige Entwicklungen
voraussichtlich immer wichtiger - ist auch die Möglichkeit der dank
Virtualisierung gesharten Infrastrukturen. Gerade hier ist bei der
Auswahl der WAF zu berücksichtigen, dass auch die WAF sich nahtlos in
diesen virtualisierten Ansatz mit einschließen lässt.

### Performance-Kriterien

Hinsichtlich der technischen Performance ist darauf zu achten, dass die
angestrebte WAF-Infrastruktur die wesentlichen Performance-Kennzahlen
der vorhandenen Web-Infrastruktur unterstützt. Reine Aussagen bezüglich
des GB-Durchsatzes von Hardware sind hier nicht unbedingt zielführend,
da in der Praxis oftmals nicht erreichbar. Wichtiger sind typische
Kennzahlen einer Webapplikation wie Anzahl der gleichzeitigen Benutzer
der Applikation und daraus abgeleitet die Anzahl der HTTP-Requests pro
Zeiteinheit im Mittel und in Spitzenlastzeiten. Hierbei ist zu beachten,
dass viele Applikationen Hochlastphasen haben, die nur selten auftreten,
z. B. während des Weihnachtsgeschäfts im Falle eines Webshops.

## Organisatorische Aspekte

### Einhaltung bestehender Security Policies

Soweit möglich sollten bestehende Security Policies durch die
Implementierung einer WAF nicht geändert werden müssen.

Als typisches Beispiel ist hier die SSL-Terminierung - vor den
Webservern - zu nennen. Diese ist, insbesondere in
Hochsicherheitsinfrastrukturen, oft durch die bestehenden
Sicherheitsrichtlinien ausgeschlossen und kann auch durch den Einsatz
einer geeigneten WAF - als Plug-In in den Webserver hinter der im
Webserver ohnehin vorgenommenen SSL-Terminierung - aufrecht erhalten
werden.

### Neues Rollenmodell: Anwendungsverantwortlicher WAF

Der nachhaltig erfolgreiche Einsatz von WAFs hängt entscheidend davon
ab, dass auch nach dem Einmalaufwand der Inbetriebnahme das
Zusammenspiel der WAF mit allen weiteren Komponenten der
Anwendungsinfrastruktur reibungslos funktioniert. Dazu zählen einerseits
offensichtliche Punkte wie Verständnis und passende
Reaktionsmöglichkeiten auf Fehler- und Alarmmeldungen der WAF, aber
auch Aspekte wie die Anpassung des Regelwerks der WAF bei gewünschten
Änderungen der zu schützenden Applikationen. Um die Chancen, die eine
WAF als zentrale Servicestelle für z. B. Sicheres Session-Management
etc. bietet, voll nutzen zu können, ist zudem eine gute Zusammenarbeit
mit der Anwendungsentwicklung notwendig.

Mit anderen Worten: Um das volle Potential einer WAF zu nutzen, genügt
es nicht, die WAF als reine Infrastrukturkomponente zu betrachten.

Deshalb schlagen wir hier - neben der Rolle eines
*Plattformverantwortlichen WAF*, die ähnlich eines
*Plattformverantwortlichen Netzwerk-Firewall* für die infrastrukturellen
Aspekte der WAF verantwortlich ist - die neue Rolle eines
*Anwendungsverantwortlichen WAF* für jede Anwendung vor, der, bildlich
gesprochen, die Brücke zwischen der WAF und der fachlichen Anwendung
darstellt. Er muss exzellente Kenntnisse der WAF besitzen, um diese
konfigurieren und für die spezielle Anwendung überwachen zu können. Er
muss die Anwendung gut kennen, um Meldungen der WAF einordnen und
bewerten zu können. In der Regel wird ein *Anwendungsverantwortlicher
WAF* die WAF-Konfiguration für mehrere Anwendungen betreuen. Ein
Beispiel wäre die Betreuung der WAF für alle webbasierten SAP-Systeme,
während das Shopsystem von einem anderen Anwendungsverantwortlichen WAF
betreut wird.

Eine ausführliche Beschreibung des vorgeschlagenen Rollenmodells findet
sich in Anhang 8.3.

## Iteratives Vorgehen bei der Implementierung - vom Grundschutz zur Vollversiegelung

Als Best Practice bei der Implementierung und beim Betrieb von WAFs hat
sich ein iteratives Vorgehen bewährt.

### Schritt 1: Festlegung der Rollenverteilung / Einbindung der Anwendungsentwicklung

Zunächst müssen die Verantwortlichkeiten - idealerweise auf Basis des
oben vorgestellten Rollenkonzepts - definiert werden. Erfolgt die
Webapplikationsentwicklung inhouse, so ist diese möglichst frühzeitig in
den Prozess mit einzubinden. Damit wird erreicht, dass möglichst bald
alle noch nicht produktiv gesetzten Applikationen die zentralen
Funktionen der WAF nutzen, was die Sicherheit erhöht und Zeit und Geld
spart. Außerdem werden mögliche Hürden auf persönlicher Ebene frühzeitig
abgebaut.

### Schritt 2: Grundschutz für alle Webapplikationen

Unabhängig von den Charakteristika der jeweiligen Webapplikation wird
zunächst ein *Grundschutz*, in der Regel als Blacklisting umgesetzt,
aktiviert. Erste Auswertungen zeigen in der Regel erste erfolgreiche
Abwehrmaßnahmen, oder zeigen False Positives - d. h. zu streng
eingestellte Regeln -, gleichzeitig werden die organisatorischen Abläufe
eingeübt.

### Schritt 3: Erstellung einer Prioritätenliste aller vorhandenen Webapplikationen

Grundlage dieser Prioritätenliste kann - neben den übergeordneten
Kriterien wie Image-Verlust usw. - das Maß des Zugriffes auf die
Webapplikation gemäß Checkliste im Anhang 8.1 sein.

### weitere Schritte: Vollversiegelung der Webapplikationen gemäß Prioritätenliste

In der Regel unterstützt durch Lernmodi der WAF oder
Sourcecode-Review/Penetrationsstest, werden die Webapplikationen Schritt
für Schritt gemäß der Prioritätenliste mit Whitelist-Regelwerken nach
außen *vollversiegelt*. Der *Anwendungsverantwortliche WAF* sorgt hier
in Zusammenarbeit mit dem fachlichen Anwendungsverantwortlichen für die
jederzeit reibungslose Verfügbarkeit der Anwendung nach außen - auch
während der Regelwerksumstellung.

# Anhänge

## Checkliste: Zugriff auf eine Webapplikation unter Security-Gesichtspunkten

Zur Bewertung des *Zugriffs* den ein Unternehmen auf die Webapplikation
hat, kann folgende Checkliste dienen. Je mehr Punkte aufaddiert werden,
umso besser ist der Zugriff auf eine Webapplikation.

<table>
<tbody>
<tr class="odd">
<td><p>Kriterium</p></td>
<td><center>
<p>Punkte</p>
</center></td>
<td><p>Kommentar</p></td>
</tr>
<tr class="even">
<td><p>Dokumentation vollständig</p>
<p>Die Dokumentation der Applikation ist insoweit vollständig, als dass potenzielle Schwachstellen in Bezug auf die Sicherheit erkannt und beseitigt werden können. Dies betrifft insbesondere die Architekturdokumentation und die Dokumentation des Sourcecodes</p></td>
<td><center>
<p>2</p>
</center></td>
<td><p>Wichtig ist vor allem eine detaillierte Architekturdokumention, sowie eine Beschreibung der Schnittstellen zwischen den einzelnen Komponenten und eine Beschreibung der Validierungen, die an diesen Schnittstellen stattfinden. Üblicherweise gibt es Dokumentation in diesem Detailgrad nicht.</p></td>
</tr>
<tr class="odd">
<td><p>Entwickler verfügbar</p>
<p>Die Entwickler, die die Applikation ursprünglich entworfen und implementiert haben stehen für Anpassungen noch zur Verfügung.</p></td>
<td><center>
<p>3</p>
</center></td>
<td></td>
</tr>
<tr class="even">
<td><p>Wartungsverträge für alle Komponenten vorhanden</p>
<p>Für die Applikation und alle in der Applikation eingesetzten Komponenten (Webserver, Applikationsserver, Datenbank, usw.) existieren Verträge, die eine Behebung von Fehlern beinhalten oder bei Open-Source-Komponenten existiert eine aktive Community, die diese Komponenten weiterentwickelt.</p></td>
<td><center>
<p>5</p>
</center></td>
<td><p>Kein Wartungsvertrag, keine Möglichkeit von Bugfixes.</p></td>
</tr>
<tr class="odd">
<td><p>Fehlerbehebungszeiten durch den Hersteller sind kurz.</p>
<p>Die Reaktionszeiten des Herstellers vom Eingang einer Fehlermeldung bis zur Behebung liegen bei kritischen Fehlern unter einer Woche. Dies können entweder vertraglich geregelte Fehlerbehebungszeiten oder empirische Fehlerbehebungszeiten, z.  B. bei Open-Source-Produkten sein.</p></td>
<td><center>
<p>3</p>
</center></td>
<td><p>Ist wichtig, hilft aber nur begrenzt.</p></td>
</tr>
<tr class="even">
<td><p>Automatisierte Tests vorhanden</p>
<p>Zur Qualitätssicherung der Applikation existieren automatisierte Tests, die einen hohen Testabdeckungsgrad abbilden und bei neuen Releases genutzt werden.</p></td>
<td><center>
<p>1</p>
</center></td>
<td><p>Tests tendieren dazu, zu überprüfen, ob die gewünschte Funktionalität vorhanden ist. Security in diesem Umfeld bedeutet aber, dass die nicht gewünschte Funktionalität nicht vorhanden ist -&gt; bringt normalerweise nicht viel.</p></td>
</tr>
<tr class="odd">
<td><p>Quellcode-Analyse wurde durchgeführt</p>
<p>Während der Entwicklung und Weiterentwicklung der Applikation wurde eine automatisierte Quellcode-Analyse (Whiteboxtest) mit dem Fokus auf Applikationssicherheit durchgeführt.</p></td>
<td><center>
<p>3</p>
</center></td>
<td><p>Die Analyse muss von einem Spezialisten durchgeführt werden, unabhängig ob automatisiert oder von externen Experten.</p></td>
</tr>
<tr class="even">
<td><p>Geringe Komplexität</p>
<p>In die Erstellung der Applikation sind inklusive aller Weiterentwicklungen weniger als 1.000 Stunden reiner Implementierungsaufwand (ohne Projektleitung) geflossen.</p></td>
<td><center>
<p>1</p>
</center></td>
<td><p>Erfahrungsgemäß ist die Komplexität am besten anhand des Implementierungsaufwands messbar. <em>Lines of Code</em> oder <em>Function Points</em> liefern doch sehr unterschiedliche Ergebnisse, je nachdem wer gerade zählt. Es sollte hier eher die Komplexität der Architektur, nicht der Implementierungsaufwand betrachtet werden.</p></td>
</tr>
<tr class="odd">
<td><p>Zentraler Controller vorhanden</p>
<p>Die Architektur der Applikation beinhaltet einen zentralen Controller, über den sämtliche Eingaben in die Applikation und aus der Applikation heraus laufen (MVC).</p></td>
<td><center>
<p>3</p>
</center></td>
<td></td>
</tr>
<tr class="even">
<td><p>Sicherheits-Framework wird genutzt</p>
<p>Die Applikation nutzt ein Sicherheitsframework das u. a. Validatoren/Filter für Ein- und Ausgabe zur Verfügung stellt.</p></td>
<td><center>
<p>4</p>
</center></td>
<td><p>Das bedeutet erstmal, dass der Entwickler mitgedacht hat. Schon mal eine sehr gute und wichtige Sache, siehe letzten Punkt.</p></td>
</tr>
<tr class="odd">
<td><p>Sicherheitsaudit wurde durchgeführt</p>
<p>Über die Applikation wurde ein Sicherheitsaudit/Penetrationstest durchgeführt und alle im Audit erkannten Schwachstellen wurden behoben.</p></td>
<td><center>
<p>2</p>
</center></td>
<td></td>
</tr>
<tr class="even">
<td><p>Entwickler wurden in Security Fragen geschult und sind erfahren.</p></td>
<td><center>
<p>5</p>
</center></td>
<td><p>Das wichtigste sind immer geschulte Entwickler!</p></td>
</tr>
</tbody>
</table>

## Rollenmodell beim Betrieb von WAFs

Das hier beschriebene Rollenmodell sollte vor allem dann umgesetzt
werden, wenn die WAF - über die Funktion als *Second Line of Defense*
und eine Grundabsicherung hinaus - zum Schutz der Webapplikationen
Aufgaben im Sinne des im Dokument beschriebenen Whitelistings übernimmt
und deshalb möglichst eng an das externe Verhalten der Webapplikation
angepasst wird.

Die Einführung einer WAF wird üblicherweise im Rahmen eines Projektes
durchgeführt. Entscheidend für den nachhaltig erfolgreichen Betrieb
einer WAF ist jedoch ein Rollenmodell, in welchem die
Verantwortlichkeiten aller Beteiligten im gesamten
Softwareentwicklungszyklus definiert sind. Eine WAF besitzt einerseits
Charakteristika einer Infrastrukturkomponente, andererseits ist ihr
Verhalten äußerst anwendungsspezifisch. Ihre Konfiguration und Verhalten
kann sich sogar zwischen verschiedenen Releases derselben Anwendung
deutlich unterscheiden. Die Konfiguration einer WAF ist weit
umfangreicher als die einer klassischen Firewall. Sehr grob vereinfacht
wird nicht mehr eine einzelne IP einer Anwendung, sondern jedes
Eingabefeld einer Anwendung konfiguriert.

In größeren IT-Organisationen werden der Betrieb der Netze, zu denen die
Firewall gehört, und der Anwendungen von verschiedenen Einheiten,
manchmal sogar von verschiedenen Firmen, durchgeführt. Die meisten
Betriebskonzepte folgen dieser organisatorischen Trennung mit einer
Rollenverteilung, die klar zwischen Aufgaben auf Infrastrukturebene
(Netzwerk und Betriebssystem) und auf Anwendungsebene unterscheiden.

Es wird wie bei einer Firewall die Rolle eines
*Plattformverantwortlichen WAF* benötigt, der für die Betriebsaspekte
der WAF zuständig ist. Wir schlagen hier die neue Rolle eines
*Anwendungs­verantwortlicher WAF* vor, die zwischen der Plattform WAF
und der individuellen Anwendung angesiedelt ist. Es wird weiterhin der
Anwendungsverantwortliche benötigt. Dieser braucht sich aber keine
tieferen Kenntnisse der WAF anzueignen.

Der *Anwendungsverantwortliche WAF* ist die Brücke zwischen der WAF und
der fachlichen Anwendung. Er muss exzellente Kenntnisse der WAF
besitzen, um diese konfigurieren und für die spezielle Anwendung
überwachen zu können. Er muss die Anwendung gut kennen, um Meldungen
der WAF einordnen und bewerten zu können. In der Regel wird ein
*Anwendungsverantwortlicher WAF* die WAF-Konfiguration für mehrere
Anwendungen betreuen. Ein Beispiel wäre die Betreuung der WAF für alle
webbasierten SAP-Systeme, während das Shopsystem von einem anderen
*Anwendungs­verantwortlichen WAF* betreut wird.

Damit werden einerseits die spezifischen Anforderungen an den sicheren
und effizienten Betrieb einer WAF berücksichtigt und andererseits
bestehen weiterhin die klassischen Rollen Infrastruktur- oder
*Plattformverantwortlicher* und *Anwendungsverantwortlicher* aus stark
strukturierten Organisationen unverändert fort.

## Die Rollen im Einzelnen

### Plattformverantwortlicher WAF

Aufgaben:

  - Planung der Betriebsarchitektur der WAF
  - Verantwortlich für Betrieb und Support der WAF inklusive
    Kapazitätsplanung
  - Einrichtung und Koordinierung Zuordnung von URLs zu individuellen
    Anwendungen
  - Patch- und Versionsmanagement der WAF
  - Verwaltung und Administration der Anwendungsverantwortlichen WAF

Kenntnisse:

  - Kenntnisse der WAF, ihres Betriebs, der Administration und des
    Autorisierungskonzepts

### Anwendungsverantwortlicher WAF (je Anwendung)

Aufgaben:

  - Implementation und Betreuung der anwendungsspezifischen
    Konfiguration der WAF
  - Monitoring und Analyse der Logfiles (zumindest im Second Level)
  - Ansprechpartner für Fehlermeldungen, insbesondere
    False-Positives-Analyse in Zusammen­arbeit mit dem
    Anwendungsverantwortlichen
  - Enge Zusammenarbeit mit Anwendungsverantwortlichen und
    Plattformverantwortlichen WAF
  - Test der WAF-Funktionalitäten für die Anwendung, insbesondere bei
    Versionsänderungen der Anwendung

Kenntnisse

  - Tiefe Kenntnisse der Konfiguration der WAF in Bezug auf
    anwendungsspezifische Schutzmechanismen
  - Sehr gute Kenntnisse des äußeren Verhaltens der Anwendung,
    insbesondere Eingabe, Ausgabe, Uploads, Downloads, Zeichensätze usw.

### Anwendungsverantwortlicher

  - Betrieb oder Entwicklung der fachlichen, zu schützenden Anwendung
  - Kenntnis der Anwendungsarchitektur, der fachlichen Eingabefelder,
    liefert diese an den Anwendungsverantwortlichen WAF.

-----

[Category:OWASP Project](Category:OWASP_Project "wikilink") [Best
Practices: Einsatz von Web Application
Firewalls](Category:OWASP_Project "wikilink") [Best Practices: Use of
Web Application Firewalls](Category:OWASP_Project "wikilink")
[Category:OWASP Best
Practices](Category:OWASP_Best_Practices "wikilink") [Category:OWASP
Document](Category:OWASP_Document "wikilink") [Category:OWASP
Download](Category:OWASP_Download "wikilink") [Category:OWASP
WAF](Category:OWASP_WAF "wikilink")
[Category:OWASP_Builders](Category:OWASP_Builders "wikilink")
[Category:OWASP_Defenders](Category:OWASP_Defenders "wikilink")
[Category:SAMM-EH-3](Category:SAMM-EH-3 "wikilink")

1.
2.
3.
4.
5.
6.
7.  <sup>Grundschutz mit Blacklisting meist ausreichend, weitere
    Möglichkeiten durch Kombination von Blacklisting und
    Whitelisting</sup>