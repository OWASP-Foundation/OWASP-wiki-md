{{ Top_10:SubsectionTableBeginTemplate

`  | type=main`

}} {{ Top_10_2010:SubsectionAdvancedTemplate

`  | type= `
`  |subsection=freetext`
`  |position=firstWhole`
`  |title=Was hat sich von Version 2013 zu 2017 verändert?`
`  |year=2017|language=de`

}}

Die Veränderungen haben in den letzten vier Jahren zugenommen, folglich
wurden auch die OWASP Top 10 aktualisiert. Wir haben sie vollständig
umgestaltet: die Methodik und den Prozess der Datenerhebung erneuert,
mit der Community vollständig transparent zusammengearbeitet, die
Risiken neu priorisiert, die Beschreibung der Risiken jeweils
runderneuert und die Referenzen zu aktuellen Frameworks und
Programmiersprachen angepasst. In den letzten Jahren hat sich die
eingesetzte Technologie und Architektur von Anwendungen signifikant
geändert:

  - Microservices, die in node.js und Spring Boot geschrieben werden,
    ersetzen traditionelle monolithische Anwendungen. Micro-services
    bringen neue Herausforderungen an die IT-Sicherheit mit, wie z.B.
    Vertrauensbeziehungen zwischen Microservices, Containern und das
    Management der Anmeldedaten. Alter Code, der nie dafür geschrieben
    wurde, aus dem Internet erreichbar zu sein, wird nun via APIs oder
    RESTful Web-Service nach außen geöffnet, z.B. mittels
    Single-Page-Anwendungen (SPA) oder für mobile Apps. Architekturelle
    Annahmen für den Code, wie z.B. vertrauenswürdige Nutzer, sind nicht
    mehr gültig.
  - Single-Page-Anwendungen, die in JavaScript-Frameworks, wie z.B.
    Angular oder React geschrieben wurden, unterstützen die Entwicklung
    von sehr modularen Clients mit einem großen Funktionsumfang. Das
    Verlagern von Funktionen auf den Client, die traditionell auf dem
    Server lagen, erzeugt weitere Herausforderungen für die
    IT-Sicherheit.
  - JavaScript ist inzwischen die meistgenutzte Sprache im Web, mit
    node.js auf den Servern und modernen Web-Frameworks wie Bootstrap,
    Electron, Angular oder React auf dem Client. 

### Neue Risiken, auf Basis der Datenerhebung:

  - <b><u>[text=documentRootTop10New]({{Top_10:LanguageFile "wikilink")</u></b>
    ist eine neue Kategorie, die hauptsächlich per
    <u>[Source-Code-Analyse-Sicherheits-Test-Tools](Source_Code_Analysis_Tools "wikilink")</u>
    (SAST) gefunden wurde.

### Neue Risiken, auf Basis der Expertenumfrage in der Community

Wir haben die Community gebeten, zwei Risiken zu wählen, die zukünftig
von größerer Bedeutung sein werden. Aufgrund der Ergebnisse der
Expertenumfrage mit über 500 Einsendungen wurden nach dem Streichen von
Risiken, die bereits aufgrund der Datenerhebung enthalten waren (z.B.
Verlust der Vertraulichkeit sensibler Daten und XXE), folgende Risiken
aufgenommen:

  - <b><u>[text=documentRootTop10New]({{Top_10:LanguageFile "wikilink")</u></b>,
    die ein externes Ausführen von beliebigem Code und die Manipulation
    von sensiblen Daten-Objekten auf betroffenen Plattformen ermöglicht.
  - <b><u>[text=documentRootTop10New]({{Top_10:LanguageFile "wikilink")</u></b>,
    das zum Übersehen oder zu beträchtlichen Verzögerungen beim Erkennen
    von bösartigen Aktivitäten oder digitalen Einbrüchen und dem
    Bearbeiten der Sicherheitsvorfälle sowie der digitalen Forensik
    führen kann.

### Zusammengeführt oder aus den Top 10 ausgeschieden, jedoch nicht vergessen:

  - <b><u>[text=documentRootTop10]({{Top_10:LanguageFile "wikilink")</u></b>
    und
    <b><u>[text=documentRootTop10]({{Top_10:LanguageFile "wikilink")</u></b>
    zusammengeführt (=vereint) zu
    <b><u>[text=documentRootTop10New]({{Top_10:LanguageFile "wikilink")</u></b>.
  - <b><u>[text=documentRootTop10]({{Top_10:LanguageFile "wikilink")</u></b>,
    da viele Frameworks Maßnahmen gegen
    <u>[CSRF](Cross-Site_Request_Forgery_\(CSRF\) "wikilink")</u>)
    beinhalten, wurde diese Kategorie nur noch in 5% der Anwendungen
    gefunden.
  - <b><u>[text=documentRootTop10]({{Top_10:LanguageFile "wikilink")</u></b>,
    das noch in ca. 8% der Anwendungen auftrat, wurde insbes. durch XXE
    verdrängt.



<center>

| OWASP Top 10 - 2013                                                            | <b>⇒</b>                                                                       | OWASP Top 10 - 2017                        |
| ------------------------------------------------------------------------------ | ------------------------------------------------------------------------------ | ------------------------------------------ |
| <u>[text=documentRootTop10]({{Top_10:LanguageFile "wikilink")</u>              | style="font-size:141%; text-align:center;"                                     | <b>⇒</b>                                   |
| <u>[text=documentRootTop10]({{Top_10:LanguageFile "wikilink")</u>              | style="font-size:141%; text-align:center;"                                     | <b>⇒</b>                                   |
| <u>[text=documentRootTop10]({{Top_10:LanguageFile "wikilink")</u>              | style="font-size:141%; text-align:center;"                                     | <b>⇘</b>                                   |
| <u>[text=documentRootTop10]({{Top_10:LanguageFile "wikilink")</u> - \[mit A7\] | style="font-size:141%; text-align:center; background-color: \#FFFFFF;"         | <b>∪</b>                                   |
| <u>[text=documentRootTop10]({{Top_10:LanguageFile "wikilink")</u>              | style="font-size:141%; text-align:center;"                                     | <b>⇘</b>                                   |
| <u>[text=documentRootTop10]({{Top_10:LanguageFile "wikilink")</u>              | style="font-size:141%; text-align:center;"                                     | <b>⇗</b>                                   |
| style="background-color: \#F2F1FF;"                                            | <u>[text=documentRootTop10]({{Top_10:LanguageFile "wikilink")</u> - \[mit A4\] | style="font-size:141%; text-align:center;" |
| <u>[text=documentRootTop10]({{Top_10:LanguageFile "wikilink")</u>              | style="font-size:141%; text-align:center; background-color: \#FFFFFF;"         | <b>☒</b>                                   |
| <u>[text=documentRootTop10]({{Top_10:LanguageFile "wikilink")</u>              | style="font-size:141%; text-align:center;"                                     | <b>⇒</b>                                   |
| <u>[text=documentRootTop10]({{Top_10:LanguageFile "wikilink")</u>              | style="font-size:141%; text-align:center; background-color: \#FFFFFF;"         | <b>☒</b>                                   |

</center>