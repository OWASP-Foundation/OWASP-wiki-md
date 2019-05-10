Auf dem OWASP-Project-Summit 2017 entschieden sich aktive Teilnehmer und
Community-Mitglieder für eine risikobasierten Reihenfolge mit bis zu
zwei vorausschauend aufgenommenen Schwachstellenklassen. Die Reihenfolge
wurde teilweise durch quantitative Daten und teilweise durch qualitative
Erhebungen bestimmt.

Für die Umfrage haben wir die Schwachstellenkategorien gesammelt, die
zuvor als "an der Schwelle" identifiziert oder im Feedback zu 2017 RC1
in der Top 10 Mailingliste erwähnt wurden. Wir haben sie in eine
Rangliste aufgenommen und die Befragten gebeten, die vier wichtigsten
Schwachstellen zu bewerten, die ihrer Meinung nach in die OWASP Top 10 -
2017 aufgenommen werden sollten. Die Umfrage war vom 2. August bis 18.
September 2017 offen. 516 Antworten wurden ausgewertet und die
Schwachstellen entsprechend geordnet.

<center>

<table style="align:center; border-collapse: collapse; text-align:center; margin: 0px 5px 0px 5px; border: 3px solid #444444; background-color: {{Top 10:BackgroundColor
|year=2017 }}; padding=2;">

<tr style="background-color: {{Top 10:BorderColor
|year=2017}}; height: 2em; font-size: 130%; color: #FFFFFF;  text-shadow: 2px 2px 8px #444444; ">

<th style="border: 3px solid #444444;">

</th>

<th style="border: 3px solid #444444; text-align:left;">

</th>

<th style="border: 3px solid #444444;">

</th>

</tr>

<tr>

<td style="border: 3px solid #444444;">

1

</td>

<td style="border: 3px solid #444444; text-align:left;">

Exposure of Private Information ('Privacy Violation') \[CWE-359\]

</td>

<td style="border: 3px solid #444444;">

748

</td>

</tr>

<tr>

<td style="border: 3px solid #444444;">

2

</td>

<td style="border: 3px solid #444444; text-align:left;">

Cryptographic Failures \[CWE-310/311/312/326/327\]

</td>

<td style="border: 3px solid #444444;">

584

</td>

</tr>

<tr>

<td style="border: 3px solid #444444;">

3

</td>

<td style="border: 3px solid #444444; text-align:left;">

Deserialization of Untrusted Data \[CWE-502\]

</td>

<td style="border: 3px solid #444444;">

514

</td>

</tr>

<tr>

<td style="border: 3px solid #444444;">

4

</td>

<td style="border: 3px solid #444444; text-align:left;">

Authorization Bypass Through User-Controlled Key (IDOR & Path Traversal)
\[CWE-639\] 

</td>

<td style="border: 3px solid #444444;">

493

</td>

</tr>

<tr>

<td style="border: 3px solid #444444;">

5

</td>

<td style="border: 3px solid #444444; text-align:left;">

Insufficient Logging and Monitoring \[CWE-223 / CWE-778\]

</td>

<td style="border: 3px solid #444444;">

440

</td>

</tr>

</table>

</center>

Die Offenlegung privater Informationen ist eindeutig die am höchsten
eingestufte Schwachstelle, passt aber sehr gut als zusätzlicher
Schwerpunkt in die bestehende
<b><u>[text=documentRootTop10New]({{Top_10:LanguageFile "wikilink")</u></b>.
Kryptographische Fehler können ebenfalls in diese Kategorie aufgenommen
werden. Unsichere Deserialisierung wurde auf Platz drei eingestuft, so
dass sie als
<b><u>[text=documentRootTop10New]({{Top_10:LanguageFile "wikilink")</u></b>
in die Top 10 aufgenommen wurde. Das viertplatzierte Thema
"User-Controlled Key" ist in
<b><u>[text=documentRootTop10New]({{Top_10:LanguageFile "wikilink")</u></b>
mit enthalten. Es ist gut, dass es in der Umfrage einen hohen Rang
einnimmt, da es bisher noch nicht viele Daten über
Autorisierungsschwachstellen gibt. Das auf Platz 5 gelistete Thema ist
"Insufficient Logging and Monitoring", passt unserer Meinung nach gut zu
den Top 10 und wurde deshalb als
<b><u>[text=documentRootTop10New]({{Top_10:LanguageFile "wikilink")</u></b>
aufgenommen. Wir sind an einem Punkt gelangt, an dem Anwendungen in der
Lage sein müssen, mögliche Angriffsindizien zu definieren, eine
geeignete Protokollierung zu erzeugen und eine angemessene Alarmierung,
Eskalation und Reaktion auszulösen.

Traditionell wurden bisher eher quantitative Daten gesammelt und
analysiert: Wie viele Schwachstellen wurden in getesteten Anwendungen
gefunden? Wie bekannt ist, melden Werkzeuge traditionell alle gefundenen
Funde einer Schwachstelle. Menschen berichten traditionell über einen
einzelnen Befund mit einer Reihe von Beispielen. Dies macht es sehr
schwierig, die beiden Berichtsstile auf vergleichbare Weise zu
aggregieren.

In 2017 wurde die Häufigkeitsrate anhand der Anzahl der Anwendungen je
Datensatz berechnet, die eine oder mehrere Schwachstellen eines
bestimmten Typs aufwiesen. Die Daten von vielen größeren Mitwirkenden
wurden auf zwei Arten zur Verfügung gestellt. Die erste war traditionell
die Häufigkeit, bei der jedes gefundene Auftreten einer Schwachstelle
gezählt wurde, während die zweite die Anzahl der Anwendungen ist, in
denen die jeweilige Schwachstelle (ein oder mehrere Male) gefunden
wurde. Obwohl nicht perfekt, erlaubt uns dies, die Daten von ‚Human
Assisted Tools‘ (automatisierte Tests) und ‚Tool Assisted Humans‘
(manuelle Tests) zu vergleichen. Die Rohdaten und Analysearbeiten sind
auf <u>[GitHub
verfügbar](https://github.com/OWASP/Top10/tree/master/2017/datacall)</u>.
Wir beabsichtigen, dies in den zukünftigen Versionen der Top 10 durch
einen strukturierteren Ansatz weiter zu verbessern.

Wir haben mehr als 40 Einreichungen für die Datenerhebung erhalten. Da
viele von ihnen aus dem ursprünglichen Datenaufruf für den RC1 stammten,
der sich auf die Auftrittshäufigkeit konzentrierte, haben wir die
anwendungsbezogenen Daten von 23 Mitwirkenden verwendet, die \~114.000
Anwendungen umfassen. Wo immer möglich, haben wir einen einjährigen
Zeitblock von Daten gleicher Anwendungen verwendet. Die Mehrzahl der
gemeldeten Anwendungen sind einmal enthalten, obwohl es möglicherweise
einige Dubletten bei den gemeldeten Anwendungen von Veracode gibt. Die
23 verwendeten Datensätze wurden als ‚‚Human Assisted Tools‘ bzw. ‚Tool
Assisted Humans‘ klassifiziert. Anomalien in den ausgewählten Daten mit
der Häufigkeit von über 100% wurden auf max. 100% angepasst. Um die
Auftretungshäufigkeit zu berechnen, haben wir den Prozentsatz all der
Anwendungen kalkuliert, bei denen festgestellt wurde, dass sie den
jeweiligen Schwachstellentyp enthalten. Die Häufigkeit einer
Schwachstelle ging bei der Berechnung des jeweiligen Risikowertes über
den Risiko-Faktor 'Verbreitung' ein und wurde so in der Rangfolge der
Top 10 berücksichtigt.