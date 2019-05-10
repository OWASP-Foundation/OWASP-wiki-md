Willkommen zu den OWASP Top 10 2013\! Diese Neufassung erweitert eine
der Kategorien aus der 2010-Edition um verbreitete, wichtige
Schwachstellen und gewichtet einige der anderen neu entsprechend der
sich ändernden Häufigkeit. Neu im Rampenlicht erscheint die Sicherheit
von Plattformkomponenten. Dieses Risiko wird durch das Schaffen einer
eigenen Kategorie
([text=documentRootTop10DeveloperEdition]({{Top_10:LanguageFile "wikilink"))
in dieser Ausgabe besser gewürdigt.

Die OWASP Top 10 für 2013 basieren auf acht Datenerhebungen von sieben
auf Anwendungssicherheit spezialisierten Firmen, darunter vier
Beratungsunternehmen und drei Software/SaaS-Anbieter. Diese Daten
umfassen mehr als 500.000 Schwachstellen in hunderten von Unternehmen
und tausenden von Anwendungen. Die Top 10 Themen wurden entsprechend
diesen Statistiken ausgewählt und priorisiert, zusammen mit einmütigen
Schätzungen zur Ausnutzbarkeit, Auffindbarkeit und den Auswirkungen.

Es ist das Hauptziel der OWASP Top 10, Entwickler, Designer, Architekten
und Führungskräfte von Organisationen und Unternehmen über die Risiken
der wichtigsten Schwachstellen von Webanwendungen aufzuklären. Die Top
10 stellen grundlegende Techniken zum Schutz gegen diese hochriskanten
Probleme vor. Sie zeigen auch auf, wie es danach weitergeht.

**Hören Sie nicht bei 10 auf\!** Es gibt hunderte von Problemen, die die
Sicherheit von Webanwendungen beeinflussen können, wie im [OWASP
Developer’s Guide](OWASP_Guide_Project "wikilink") und der [OWASP Cheat
Sheet Series](Cheat_Sheets "wikilink") dargestellt. Diese sollten
Pflichtlektüre für jeden Entwickler von Webanwendungen sein. Anleitungen
zum Aufspüren von Schwachstellen werden durch die Dokumente [OWASP
Testing
Guide](https://www.owasp.org/index.php/Category:OWASP_Testing_Project)
und [OWASP Code Review
Guide](https://www.owasp.org/index.php/Category:OWASP_Code_Review_Project)
bereitgestellt.

**Kontinuierliche Änderungen.** Die Top 10 werden sich fortlaufend
verändern. Auch ohne eine einzige Zeile Code in Ihrer Anwendung zu
ändern, können Sie sich als verwundbar für einen Angriff erweisen,
falls neue Lücken bekannt oder Angriffsmethoden verbessert werden.
Beachten Sie den Hinweis am Ende in *„Nächste Schritte für Entwickler,
Prüfer und Organisationen“*.

**Denken Sie weiter\!** Wenn Sie bereit sind, nicht mehr nur
Schwachstellen nachzurennen und statt dessen den Fokus auf starke
Sicherheitsmaßnahmen in Anwendungen richten, nutzen Sie den [Application
Security Verification Standard (ASVS) zur Entwicklung und
Überprüfung](ASVS "wikilink").

**Nutzen Sie Werkzeuge sinnvoll\!** Sicherheitsschwachstellen können
komplex und in Unmengen von Code versteckt sein. In vielen Fällen ist
ein effizienter Ansatz zum Finden und Beseitigen von Schwachstellen der
Einsatz von Experten, die mit den richtigen Werkzeugen umgehen können.

**Schauen Sie über den Tellerrand\!** Machen Sie Sicherheit zu einem
integrierten Bestandteil Ihrer IT-Organisation. Informieren Sie sich
über das [Open Software Assurance Maturity Model
(SAMM)](https://www.owasp.org/index.php/Category:Software_Assurance_Maturity_Model).

Unser Dank gilt Jeff Williams und Dave Wichers von [Aspect
Security](https://www.aspectsecurity.com/), die die OWASP Top 10 seit
2003 vorantreiben.

Darüber hinaus bedanken wir uns bei den weiteren Organisationen, die
Informationen zur Verbreitung von Schwachstellen bereitgestellt haben:

  - [Aspect Security](https://www.aspectsecurity.com/)
  - [HP](http://www.hpenterprisesecurity.com/) –
    [Statistics](http://www.hpenterprisesecurity.com/collateral/whitepaper/HP2012CyberRiskReport_0313.pdf)
    (Fortify und WebInspect)
  - [Minded Security](http://www.mindedsecurity.com/) –
    [Statistics](http://blog.mindedsecurity.com/2013/02/real-life-vulnerabilities-statistics.html)
  - [Softtek](http://www.softtek.com/) –
    [Statistics](https://www.softtek.com/webdocs/special_pdfs/WP-State-of-the-art-2013.pdf)
  - [Trustwave, Spiderlabs](https://www.trustwave.com/spiderlabs/) –
    [Statistics](http://www2.trustwave.com/rs/trustwave/images/2013-Global-Security-Report.pdf)
    (siehe Seite 50)
  - [Veracode](http://www.veracode.com/) –
    [Statistics](http://info.veracode.com/rs/veracode/images/VERACODE-SOSS-V4.PDF)
  - [WhiteHat Security Inc.](https://www.whitehatsec.com/) –
    [Statistics](http://owasptop10.googlecode.com/files/WPstats_winter11_11th.pdf)

Wir danken auch jedem, der zu den Vorgänger-Editionen der Top 10
beigetragen hat. Folgende Personen haben in signifikanter Weise an der
vorliegenden Fassung mitgewirkt:

  - Adam Baso ([Wikimedia
    Foundation](http://wikimediafoundation.org/wiki/Home))
  - Mike Boberski (Booz Allen Hamilton)
  - Torsten Gigler
  - Neil Smithline – ([MorphoTrust USA](http://www.MorphoTrust.com)) für
    das Erstellen des Top 10-Wikis und das Feedback

Das englische Original der Top 10 - 2013 finden Sie
[hier](https://www.owasp.org/index.php/Category:OWASP_Top_Ten_Project).

Die deutsche Übersetzung der Top 10 - 2013 kann
[hier](Germany/Projekte/Top_10 "wikilink") heruntergeladen werden.

Die Top 10 wurden und werden weltweit [in viele
Sprachen](https://www.owasp.org/index.php/Category:OWASP_Top_Ten_Project#tab=Translation_Efforts_2)
übersetzt.