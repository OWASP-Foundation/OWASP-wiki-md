Die Bedrohungen für die Sicherheit von Anwendungen ändern sich
permanent. Schlüsselfaktoren dieser Weiterentwicklung sind die
Fortschritte, die Angreifer machen, Veröffentlichungen neuer
Technologien mit neuen Schwachstellen oder integrierte Abwehrmechanismen
und der Einsatz immer komplexerer Systeme. Um mit dieser Entwicklung
Schritt zu halten, aktualisieren wir die OWASP Top 10 regelmäßig. In der
vorliegenden Version 2013 gibt es die folgenden Änderungen:

1.  Die Häufigkeit der Kategorie „*Fehler in Authentifizierung und
    Session Management*“ ist den Daten nach gestiegen. Wir glauben, dass
    dies nicht an einer tatsächlichen Steigerung der Häufigkeit liegt,
    sondern daran, dass dieser Bereich stärker in den Fokus geraten ist.
    Daher sind die Risiken A2 und A3 in ihrer Reihenfolge getauscht
    worden
2.  „*Cross-Site Request Forgery (CSRF)*” rutschte aufgrund unserer
    Datenbasis in der Häufigkeit von 2010-A5 auf 2013-A8. CSRF ist seit
    6 Jahren in den OWASP Top 10 zu finden. Wir glauben, dass sich daher
    in dieser Zeit Organisationen, Firmen und Entwickler von Frameworks
    genug mit diesem Thema beschäftigt haben, um die Zahl von
    CSRF-Schwachstellen in produktiven Anwendungen signifikant zu
    senken.
3.  Wir haben die Kategorie „*Mangelhafter URL-Zugriffschutz*” aus den
    OWASP Top 10 2010 erweitert und verallgemeinert:
    \+     2010-A8:„*Mangelhafter URL-Zugriffschutz*” ist nun zu
    2013-A7: „*Fehlerhafte Autorisierung auf Anwendungsebene*” geworden.
    Um den Zugriffsschutz und die Autorisierung auf Anwendungsebene
    sicherzustellen gibt es viele Möglichkeiten, eben nicht nur die URL.
4.  2010-A7 und A9 wurden zusammengefasst, um daraus 2013-A6: „*Verlust
    der Vertraulichkeit sensibler Daten*“ zu machen:
    \-     Diese neue Kategorie wurde durch das Zusammenlegen von
    2010-A7 – „*Kryptografisch unsichere Speicherung*“ und 2010-A9 –
    „*Unzureichende Absicherung der Transportschicht*“ zusätzlich mit
    den Risiken sensibler Daten im Browser geschaffen. Sie beinhaltet
    den Schutz der Vertraulichkeit sensibler Daten (anders als die
    Zugriffskontrollen aus 2013-A4 und 2013-A7) vom Moment der Eingabe
    über den Transport zum Server, die Verarbeitung und die Speicherung
    im Server bis hin zur erneuten Auslieferung an den Benutzer.
5.  Wir haben 2013-A9: „*Verwendung von Komponenten mit bekannten
    Schwachstellen*” hinzugefügt::
    \+     Dieser Punkt wurde als Teil von 2010-A6 –
    „*Sicherheitsrelevante Fehlkonfiguration*” erwähnt, nun aber zur
    eigenen Kategorie gemacht: Die generelle Zunahme und die steigende
    Komplexität von komponentenbasierten Entwicklungen hat das Risiko,
    Komponenten mit bekannten Schwachstellen einzusetzen, signifikant
    erhöht.

<center>

| OWASP Top 10 - 2010 (alt)                                                | OWASP Top 10 - 2013 (neu)                                                                                                 |
| ------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------- |
| [A1-{{Top_10_2010:ByTheNumbers](Top_10_2010-A1 "wikilink")             | [text=documentRootTop10]({{Top_10:LanguageFile "wikilink")                                                                |
| [A3-{{Top_10_2010:ByTheNumbers](Top_10_2010-A3 "wikilink")             | [text=documentRootTop10]({{Top_10:LanguageFile "wikilink")                                                                |
| [A2-{{Top_10_2010:ByTheNumbers](Top_10_2010-A2 "wikilink")             | [text=documentRootTop10]({{Top_10:LanguageFile "wikilink")                                                                |
| [A4-{{Top_10_2010:ByTheNumbers](Top_10_2010-A4 "wikilink")             | [text=documentRootTop10]({{Top_10:LanguageFile "wikilink")                                                                |
| [A6-{{Top_10_2010:ByTheNumbers](Top_10_2010-A6 "wikilink")             | [text=documentRootTop10]({{Top_10:LanguageFile "wikilink")                                                                |
| [A7-{{Top_10_2010:ByTheNumbers](Top_10_2010-A7 "wikilink")             | [text=documentRootTop10]({{Top_10:LanguageFile "wikilink")                                                                |
| [A8-{{Top_10_2010:ByTheNumbers](Top_10_2010-A8 "wikilink")             | [text=documentRootTop10]({{Top_10:LanguageFile "wikilink")                                                                |
| [A5-{{Top_10_2010:ByTheNumbers](Top_10_2007-A5 "wikilink")             | [text=documentRootTop10]({{Top_10:LanguageFile "wikilink")                                                                |
| [\<Teil von A6: {{Top_10_2010:ByTheNumbers](Top_10_2010-A6 "wikilink") | [text=documentRootTop10]({{Top_10:LanguageFile "wikilink")                                                                |
| [A10-{{Top_10_2010:ByTheNumbers](Top_10_2010-A10 "wikilink")           | [text=documentRootTop10]({{Top_10:LanguageFile "wikilink")                                                                |
| [A9-{{Top_10_2010:ByTheNumbers](Top_10_2010-A9 "wikilink")             | Zusammen mit [2010-A7](Top_10_2010-A7 "wikilink") nun im neuen [text=documentRootTop10]({{Top_10:LanguageFile "wikilink") |

</center>