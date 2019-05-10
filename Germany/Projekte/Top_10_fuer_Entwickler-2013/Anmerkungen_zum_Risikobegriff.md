Obwohl die früheren [<u>OWASP Top 10</u>](Top10 "wikilink")-Versionen
von und vor [<u>2007</u>](Top_10_2007 "wikilink") darauf ausgelegt
waren, die häufigsten „Schwachstellen” zu identifizieren, waren diese
Dokumente eigentlich immer um Risiken herum aufgebaut. Dies verursachte
bei einigen Anwendern, die eine wasserdichte Schwachstellen-
Klassifizierung suchten, eine gewisse nachvollziehbare Verwirrung. Ab
der [<u>OWASP Top 10 in der Version von
2010</u>](Top_10_2010 "wikilink") wird nun der Fokus auf den
Risikobegriff deutlicher dargestellt, indem noch expliziter darauf
eingegangen wird, wie dieses Risiko durch das Zusammenspiel von
Bedrohungsquellen, Angriffsvektoren, Schwachstellen und den Auswirkungen
auf die Technik und die Geschäftsprozesse des Unternehmens entsteht.
Die Methodik der Risikobewertung für die Top 10 basiert auf der
<u>[OWASP Risk Rating
Methodology](OWASP_Risk_Rating_Methodology "wikilink")</u>. Für jeden
Punkt der Top 10 schätzten wir das typische Risiko ab, das die
entsprechende Schwachstelle in einer üblichen Webanwendung verursacht,
indem wir die allgemeinen Wahrscheinlichkeits- und Auswirkungs-Faktoren
für die jeweilige Schwachstelle betrachteten. Dann sortierten wir die
Top 10 gemäß der Schwachstellen, die im Allgemeinen das größte Risiko in
einer Anwendung verursachen.

Zur Umsetzung entwickelten wir eine Methodik der Risikobewertung für die
Top 10 basierend auf der <u>[OWASP Risk Rating
Methodology](OWASP_Risk_Rating_Methodology "wikilink")</u>. Für jeden
Punkt der Top 10 schätzten wir das typische Risiko ab, das die
entsprechende Schwachstelle in einer üblichen Webanwendung verursacht,
indem wir die allgemeinen Wahrscheinlichkeits- und Auswirkungs-Faktoren
für die jeweilige Schwachstelle betrachteten. Dann sortierten wir die
Top 10 gemäß der Schwachstellen, die im Allgemeinen das größte Risiko in
einer Anwendung verursachen.
Die <u>[OWASP Risk Rating
Methodology](OWASP_Risk_Rating_Methodology "wikilink")</u> definiert
zahlreiche Faktoren, die helfen, das Risiko einer gefundenen
Schwachstelle zu bewerten. Unabhängig davon ist die Top 10 eher
allgemein gehalten und geht weniger auf spezifische Sicherheitslücken
realer Anwendungen ein. Daher können wir niemals so genau wie die
Verantwortlichen sein, die das Risiko für ihre eigenen Anwendungen
abschätzen. Sie selbst können am Besten beurteilen, wie hoch der
konkrete Schutzbedarf der Anwendung ist, wie wichtig die verarbeiteten
Daten sind, wer oder was die Bedrohungsquellen darstellen und wie das
System entwickelt wurde und betrieben wird.
Unsere Methodik beinhaltet drei Wahrscheinlichkeits-Faktoren für jede
Schwachstelle („Verbreitung”, „Auffindbarkeit“ und „Ausnutzbarkeit”) und
einen Faktor zur „Technischen Auswirkung”. Die Verbreitung einer
Schwachstelle muss üblicherweise nicht abgeschätzt werden. Hierfür haben
uns verschiedene Organisationen (vgl. Danksagung in der Einleitung (E)
auf Seite 3) Statistiken zur Verfügung gestellt, die wir zu einer Top 10
Liste des Wahrscheinlichkeits-Faktors für die „Verbreitung“ gemittelt
haben. Diese Daten wurden dann mit den beiden anderen
Wahrscheinlichkeits-Faktoren für „Auffindbarkeit” und „Ausnutzbarkeit”
kombiniert, um eine Bewertung der Wahrscheinlichkeit für jede
Schwachstelle zu berechnen. Dieser Wert wurde im Folgenden mit den
geschätzten üblichen „Technischen Auswirkungen” des jeweiligen Punktes
der Top 10 multipliziert, um so zu einer Gesamtbewertung der
letztendlichen Risiko-Einstufung zu gelangen.
Dieser Ansatz berücksichtigt die Wahrscheinlichkeit der Bedrohungsquelle
nicht, ebenso wenig wie irgendwelche technischen Details der betroffenen
Anwendung. Jeder dieser Faktoren könnte die Gesamtwahrscheinlichkeit,
dass ein Angreifer eine bestimmte Schwachstelle findet und ausnutzt,
signifikant beeinflussen. Dieses Bewertungsschema berücksichtigt auch
nicht die Auswirkungen auf das jeweilige Unternehmen und die
Geschäftsprozesse. <u>Ihre Organisation oder Ihr Unternehmen</u> wird
für sich selbst – unter Berücksichtigung der Firmenkultur, der
Industriestandards und Regulierungsanforderungen – entscheiden müssen,
welches Sicherheits- Risiko durch Anwendungen sie oder es bereit ist zu
tragen. Es ist nicht Sinn und Zweck der OWASP Top 10, Ihnen diese
Risiko-Analyse abzunehmen.
Das folgende Diagramm zeigt exemplarisch unsere Abschätzung des Risikos
für
[text=documentRootTop10DeveloperEdition]({{Top_10:LanguageFile "wikilink").
Anzumerken ist, dass XSS so stark verbreitet ist, dass es als einziger
Punkt den Verbreitungsgrad „AUSSERGEWÖHNLICH HÄUFIG“ mit dem
Verbreitungs-Wert 0 erhalten hat. Alle anderen Werte bewegen sich
zwischen „SEHR HÄUFIG“, „HÄUFIG“ und „SELTEN“ (Werte 1 bis 3).

<td>

 

</td>

<td style="text-align: center; padding: 4px; font-size: 200%; font-weight: bold; border: 3px solid #444444;">

2

</td>

<td style="text-align: center; padding: 4px; font-size: 200%; font-weight: bold; border: 3px solid #444444;">

0

</td>

<td style="text-align: center; padding: 4px; font-size: 200%; font-weight: bold; border: 3px solid #444444;">

1

</td>

<td style="text-align: center; padding: 4px; font-size: 200%; font-weight: bold; border: 3px solid #444444;">

2

</td>

<td>

 

</td>

</tr>

<tr>

<td>

 

</td>

<td colspan="3"  style="border: #4d953d 1px solid; background-color: #D9D9D9; text-align: center; padding: 4px;">

<span style="font-weight: bold; font-size: 150%; color: red;">Bewertung
der Wahrscheinlichkeit: 1</span>
     (= Mittel aus Ausnutzbarkeit, Verbreitung und Auffindbarkeit)

</td>

<td style="text-align: center; padding: 4px; font-size: 200%; font-weight: bold; solid #444444;">

\* 2  

</td>

<td>

 

</td>

</tr>

<tr>

<td>

 

</td>

<td>

 

</td>

<td colspan="3"  style="border: #4d953d 1px solid; background-color: #D9D9D9; text-align: center; padding: 4px;">

<span style="font-weight: bold; font-size: 150%; color: red;">Risiko-Einstufung:
2</span>
     (= Wahrscheinlichkeit \* Auswirkung)

</td>

<td>

 

</td>