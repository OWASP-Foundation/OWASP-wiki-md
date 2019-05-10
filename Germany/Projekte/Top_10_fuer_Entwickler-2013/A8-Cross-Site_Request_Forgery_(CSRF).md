`    <td ``>Jeder, der einem Browser Inhalte unterschieben kann, die nicht beabsichtigte Requests auslösen. Hierfür kommt jede Website oder jede HTML-Quelle in Betracht, die der Nutzer verwendet.`

</td>

`    <td ``>Durch Image-Tags, XSS oder andere Techniken löst das Opfer unbeabsichtigt einen gefälschten HTTP-Request für eine Anwendung aus. `<u>`Falls der Nutzer authentifiziert ist`</u>`, wird dieser Angriff Erfolg haben.`

</td>

`    <td colspan=2  ``>`[`CSRF`](CSRF "wikilink")` nutzt aus, dass es bei den meisten Webanwendungen möglich ist, die Inhalte eines Requests für eine bestimmte Aktion vorherzusagen.`

Da Browser Informationen zum Session-Management automatisch mitsenden,
kann ein Angreifer gefälschte Requests auf bösartigen Websites
hinterlegen, die von autorisierten und gewollten Requests nicht
unterschieden werden können.

CSRF-Schwächen sind leicht durch Penetrationstests oder
Quellcode-Analysen auffindbar.

</td>

`    <td ``>Angreifer können über den Browser des Opfers alle zustandsändernden Aktionen auslösen, für das es berechtigt ist, z.B. Ändern  von Daten, Aufgeben von Bestellungen, Logout und Login, usw.`

</td>

`    <td ``>`

Betrachten Sie den Geschäftswert der betroffenen Daten oder Funktionen.
Es bleibt die Unsicherheit, ob der Nutzer die Aktion ausführen wollte.
Bedenken Sie mögliche Auswirkungen auf Ihre Reputation.

</td>

Die Anwendung erlaubt es einem Benutzer, einen **zustandsändernden
Request** auszulösen, der kein geheimes Token beinhaltet, wie z.B.:
**http://example.com/app/transferFunds?amount=1500\&destinationAccount=4673243243**

Dadurch kann ein Angreifer einen Request erzeugen, der Geld vom Konto
des Opfers auf das Konto des Angreifers transferiert. Diesen bettet der
Angreifer „unsichtbar“ in ein Image-Tag oder ein Iframe ein und
hinterlegt ihn in einer beliebigen Website:  **\<img
src="http://example.com/app/transferFunds?<span style="color: red;">amount=1500\&destinationAccount=attackersAcct\#"
width="0" height="0" /\>**</span>

Wenn das Opfer eine präparierte Seite besucht, während es bereits auf
**example.com authentifiziert** ist, werden diese **untergeschobenen
Requests** automatisch gültige Session-Informationen mit versenden. Die
Requests sind somit unbeabsichtigt autorisiert.

Um CSRF zu verhindern, sollte jede Eingabeseite einen Token beinhalten.
Der Token sollte unvorhersagbar und für jede Session, besser für jedes
Formular, einzigartig sein und vom Server geprüft werden.

1.  Die bevorzugte Methode, das Token einzubetten, ist ein
    Hidden-Input-Feld. Damit wird der Token-Wert im Body des Requests
    und nicht im URL übertragen (erleichtert sonst Ausspähung).
2.  Ein solches Token kann auch direkt in den URL geschrieben oder als
    URL-Parameter übergeben werden. Jedoch birgt diese Vorgehensweise
    das Risiko, dass der URL dem Angreifer in die Hände fällt und somit
    das geheime Token kompromittiert ist.
    OWASPs [CSRF Guard](CSRFGuard "wikilink") kann genutzt werden, um
    automatisch solche Token in Java EE, .NET oder PHP Anwendungen
    einzubinden. OWASPs [ESAPI](ESAPI "wikilink") beinhaltet
    Token-Generatoren und Validatoren, die Entwickler einsetzen können,
    um ihre Transaktionen zu schützen.
3.  Aktive Rückbestätigung vom Benutzer (erneute Authentifizierung,
    CAPTCHA-Eingabe, usw.) kann auch vor CSRF schützen.

# **JAVA**

#### ESAPI

*' /\*\* (A) CSRF-Token erzeugen \*\*/ **
private String csrfToken = resetCSRFToken();

**/\*\* (B) In zu schützenden FORM-Seiten (B1), oder Urls (B2) das
CSRF-Token als 'hidden field' hinzufügen, vgl [ESAPI
DefaultHTTPUtilities.java](http://code.google.com/p/owasp-esapi-java/source/browse/trunk/src/main/java/org/owasp/esapi/reference/DefaultHTTPUtilities.java)\*\*/**

**/\*\* (B1) das CSRF-Token als 'hidden field' in den GET-Request
hinzufügen \*\*/*'
example.jsp
...
\<%

  -
    <span style="color: green;">**String csrfTokenFieldName =
    org.owasp.esapi.HTTPUtilities.CSRF_TOKEN_NAME;**</span>
    <span style="color: green;">**String csrfToken =
    ESAPI.httpUtilities().getCSRFToken();**</span>

%\>
<span style="color: green;">**\<input type="hidden"
id="\<%=csrfTokenFieldName%\>" value="\<%=csrfToken%\>"/\>**</span>
...
**/\*\* (B2) das CSRF-Token als URL Parameter in den GET-Request
hinzufügen, jedoch \*\*/**
**/\*\* höheres Risiko, dass die URL und damit das Token dem Angreifer
in die Hände fällt \*\*/**
\<%

  -
    String unprotectedHref = "/main?function=TransferFunds\&solution";
    <span style="color: green;">**String betterProtectedHref =
    ESAPI.httpUtilities().addCSRFToken(unprotectedHref);**</span>

%\>
<span style="color: green;">**\<a href='\<%=betterProtectedHref%\>'
target="_blank"\>Transfer Funds\</a\>**</span>

**/\*\* (C) Beim Empfang der Daten das CSRF-Token prüfen (GET-Request)
\*\*/**
try {

  -
    <span style="color: green;">**ESAPI.httpUtilities().verifyCSRFToken(request);**</span>
    } catch( IntrusionException e ) {
    // log intrusion exception
    // abort request and deny access

}
**/\*\* (D) Beim Abmelden bzw. Timeout die Session ungültig machen
\*\*/**
User user = ESAPI.authenticator().logout;

#### CSRF Guard

  - /\*\* Parameter für CsrfGuard und Java EE-Filter im Deployment
    \*\*/
    /\*\* Descriptor des Webserver-Containers definieren (web.xml-Datei)
    \*\*/

<context-param>

  -
    <param-name>Owasp.CsrfGuard.Config</param-name>
    <param-value>WEB-INF/Owasp.CsrfGuard.properties</param-value>

</context-param>
<context-param>

  -
    <param-name>Owasp.CsrfGuard.Config.Print</param-name>
    <param-value>true</param-value>

</context-param>
<listener>

  -
    <listener-class>org.owasp.csrfguard.CsrfGuardListener</listener-class>

</listener>
<span style="color: green;">**\<filter\>**</span>

  -
    <span style="color: green;">**\<filter-name\>CSRFGuard\</filter-name\>**</span>
    <span style="color: green;">**\<filter-class\>org.owasp.csrfguard.CsrfGuardFilter\</filter-class\>**</span>

<span style="color: green;">**\</filter\>**</span>
<span style="color: green;">**\<filter-mapping\>**</span>

  -
    <span style="color: green;">**\<filter-name\>CSRFGuard\</filter-name\>**</span>
    <span style="color: green;">**\<url-pattern\>/\*\</url-pattern\>**</span>

<span style="color: green;">**\</filter-mapping\>**</span>

vgl
<u>[Owasp.CsrfGuard.Test](https://github.com/esheri3/OWASP-CSRFGuard/tree/master/Owasp.CsrfGuard.Test)</u>
Die Parameter in der Datei 'Owasp.CsrfGuard.properties' gemäß
<u>[CSRFGuard_3_Configuration](CSRFGuard_3_Configuration "wikilink")</u>
einstellen.

\--- altes Beispiel
---------------------------------------------------------------------------------

  - /\*\* Ein sicheres CSRF-Token erzeugen ('size' Bytes,
    BASE64-kodiert): \*\*/


private String generateCSRFToken(int size) throws
NoSuchAlgorithmException {

  -
    SecureRandom sr = null;
    byte\[\] random = new byte\[size\];
    BASE64Encoder encoder = new BASE64Encoder();


: sr = SecureRandom.getInstance("SHA1PRNG");

  -
    sr.nextBytes(random);
    return encoder.encode(random);

}

;Beim Empfang der Daten das CSRF-Token prüfen Der OWASP CSRF Java EE
Filter prüft, ob der CSRF-Token gültig ist und führt doChain() aus, bzw.
gibt eine Fehlerseite bei einem negativen Ergebnis aus.
vgl [How_CSRFGuard_Works](How_CSRFGuard_Works "wikilink")
-----------------------------------------------------\>

#### Java Server Faces (JSF)

JSF sendet ab Version 2.2 automatisch sichere CSRF-Token mit.

-----

...
Tbd: konfig
...
\---------------------\>

-----

#### Tbd\!\!

  - {Soll so etwas rein?}

Z.B. Keine Bookmarks auf ausgefüllte Eingabe-Formulare, Suchergebnisse;
Frameworks funktionieren teilweise nicht für Web 2.0
-----------------------\>

  - [OWASP CSRF Prevention Cheat
    Sheet](Cross-Site_Request_Forgery_\(CSRF\)_Prevention_Cheat_Sheet "wikilink")
  - [OWASP CSRF Article](CSRF "wikilink")
  - [OWASP CSRFGuard - CSRF Defense Tool](CSRFGuard "wikilink")
  - [OWASP CSRFGuard -
    CSRFGuard_3_Installation](CSRFGuard_3_Installation "wikilink")
  - [OWASP CSRFGuard -
    CSRFGuard_3_Configuration](CSRFGuard_3_Configuration "wikilink")
  - [ESAPI Project Home Page](ESAPI "wikilink")
  - [ESAPI HTTPUtilities Class with AntiCSRF
    Tokens](http://owasp-esapi-java.googlecode.com/svn/trunk_doc/latest/org/owasp/esapi/HTTPUtilities.html)
  - [ESAPI-Java-Wiki](http://code.google.com/p/owasp-esapi-java/wiki/Welcome)
  - [OWASP Testing Guide: Chapter on CSRF
    Testing](Testing_for_CSRF_\(OWASP-SM-005\) "wikilink")
  - [OWASP CSRFTester - CSRF Testing Tool](CSRFTester "wikilink")

<!-- end list -->

  - [CWE Entry 352 on
    CSRF](http://cwe.mitre.org/data/definitions/352.html)
  - [John Melton's Weblog: The OWASP Top Ten and ESAPI
    –Part 5–](http://www.jtmelton.com/2010/05/16/the-owasp-top-ten-and-esapi-part-6-cross-site-request-forgery-csrf)

# **PHP**

...

  -
    ...


...

  -
    ...



...
Tbd: konfig
...

  - [OWASP CSRF Prevention Cheat
    Sheet](Cross-Site_Request_Forgery_\(CSRF\)_Prevention_Cheat_Sheet "wikilink")
  - [OWASP CSRF Article](CSRF "wikilink")
  - [OWASP CSRFGuard - CSRF Defense Tool](CSRFGuard "wikilink")
  - [ESAPI Project Home Page](ESAPI "wikilink")
  - [OWASP Testing Guide: Chapter on CSRF
    Testing](Testing_for_CSRF_\(OWASP-SM-005\) "wikilink")
  - [OWASP CSRFTester - CSRF Testing Tool](CSRFTester "wikilink")

<!-- end list -->

  - [CWE Entry 352 on
    CSRF](http://cwe.mitre.org/data/definitions/352.html)
  - [John Melton's Weblog: The OWASP Top Ten and ESAPI
    –Part 5–](http://www.jtmelton.com/2010/05/16/the-owasp-top-ten-and-esapi-part-6-cross-site-request-forgery-csrf)

# **.NET**

#### ASP.NET Web Formulare

(noch unbearbeitet =\> tbd)
If you don't use Viewstate, then look to the default master page of the
ASP.NET Web Forms default template for a manual anti-CSRF token.
private const string AntiXsrfTokenKey = "__AntiXsrfToken";
private const string AntiXsrfUserNameKey = "__AntiXsrfUserName";
private string _antiXsrfTokenValue;
protected void Page_Init(object sender, EventArgs e)
{
: // The code below helps to protect against XSRF attacks

  -
    var requestCookie = Request.Cookies\[AntiXsrfTokenKey\];
    Guid requestCookieGuidValue;
    if (requestCookie \!= null && Guid.TryParse(requestCookie.Value, out
    requestCookieGuidValue))
    {
      -
        // Use the Anti-XSRF token from the cookie
        _antiXsrfTokenValue = requestCookie.Value;
        Page.ViewStateUserKey = _antiXsrfTokenValue;
    } else {
      -
        // Generate a new Anti-XSRF token and save to the cookie
        _antiXsrfTokenValue = Guid.NewGuid().ToString("N");
        Page.ViewStateUserKey = _antiXsrfTokenValue;
        var responseCookie = new HttpCookie(AntiXsrfTokenKey)
        {
          -
            HttpOnly = true,
            Value = _antiXsrfTokenValue
        };
        if (FormsAuthentication.RequireSSL &&
        Request.IsSecureConnection)
        {
          -
            responseCookie.Secure = true;
        }
        Response.Cookies.Set(responseCookie);
    }
    Page.PreLoad += master_Page_PreLoad;

}  [**Quelle: .NET Security Cheat
Sheet**](.NET_Security_Cheat_Sheet "wikilink")
tbd Text

tbd Text

  - {Soll so etwas rein?}

Z.B. Keine Bookmarks auf ausgefüllte Eingabe-Formulare, Suchergebnisse;
Frameworks funktionieren teilweise nicht für Web 2.0

  - [OWASP CSRF Prevention Cheat
    Sheet](Cross-Site_Request_Forgery_\(CSRF\)_Prevention_Cheat_Sheet "wikilink")
  - [OWASP CSRF Article](CSRF "wikilink")
  - [OWASP CSRFGuard - CSRF Defense Tool](CSRFGuard "wikilink")
  - [OWASP CSRFGuard -
    CSRFGuard_3_Installation](CSRFGuard_3_Installation "wikilink")
  - [OWASP CSRFGuard -
    CSRFGuard_3_Configuration](CSRFGuard_3_Configuration "wikilink")
  - [ESAPI Project Home Page](ESAPI "wikilink")
  - [ESAPI HTTPUtilities Class with AntiCSRF
    Tokens](http://owasp-esapi-java.googlecode.com/svn/trunk_doc/latest/org/owasp/esapi/HTTPUtilities.html)
  - [ESAPI-Java-Wiki](http://code.google.com/p/owasp-esapi-java/wiki/Welcome)
  - [OWASP Testing Guide: Chapter on CSRF
    Testing](Testing_for_CSRF_\(OWASP-SM-005\) "wikilink")
  - [OWASP CSRFTester - CSRF Testing Tool](CSRFTester "wikilink")
  - [.NET Security Cheat Sheet](.NET_Security_Cheat_Sheet "wikilink")

<!-- end list -->

  - [CWE Entry 352 on
    CSRF](http://cwe.mitre.org/data/definitions/352.html)
  - [OWASP Top 10 for .NET developers (Troy
    Hunt)](http://asafaweb.com/OWASP%20Top%2010%20for%20.NET%20developers.pdf)

\-- weitere Programmiersprachen oder evtl Anti-Beispiele --- \>

# **Test**

tbd Text

tbd Text

(ganze Breite) Text

Text

Text

\------------------------------\> <headertabs />