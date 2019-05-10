`    <td ``>Nicht authentifizierte Angreifer sowie authentifizierte Nutzer könnten versuchen, Zugangsdaten anderer zu stehlen. In Betracht kommen außerdem Innentäter, die ihre Handlungen verschleiern wollen.`

</td>

`    <td ``>Angreifer nutzen Lücken bei der Authentifizierung oder im Sessionmanagement (z.B. ungeschützte Nutzerkonten, Passwörter, Session-IDs), um sich eine fremde Identität zu verschaffen.`

</td>

`    <td colspan=2  ``>`

Obwohl es sehr schwierig ist, ein sicheres Authentifizierungs- und
Session-Management zu implementieren, setzen Entwickler häufig auf
eigene Lösungen. Diese haben dann oft Fehler bei Abmeldung und
Passwortmanagement, bei der Wiedererkennung des Benutzers, bei Timeouts,
Sicherheitsabfragen usw. Das Auffinden dieser Fehler kann sehr schwierig
sein, besonders wenn es sich um individuelle Implementierungen handelt.

</td>

`    <td ``>Diese Fehler führen zur Kompromittierung von Benutzerkonten. Ein erfolgreicher Angreifer hat alle Rechte des Opfers. Privilegierte Zugänge sind oft Ziel solcher Angriffe.`

</td>

`    <td ``>Betrachten Sie den Geschäftswert der betroffenen Daten oder Anwendungsfunktionen. Betrachten Sie weiterhin Auswirkungen auf das Unternehmen beim Bekanntwerden der Schwachstelle.`

</td>

**Szenario 1:** Eine Flugbuchungsanwendung fügt die Session-ID in die
URL ein:
http://example.com/sale/saleitems;<span style="color:red;">**jsessionid=2P0OC2JDPXM0OQSNDLPSKHCJUN2JV**</span>?dest=Hawaii
Ein authentifizierter Anwender möchte dieses Angebot seinen Freunden
mitteilen. Er versendet obigen Link per E-Mail, ohne zu wissen, dass er
seine Session-ID preisgibt. Nutzen seine Freunde den Link, können sie
seine Session sowie seine Kreditkartendaten benutzen.

**Szenario 2:** Anwendungs-Timeouts sind falsch konfiguriert. Ein
Anwender benutzt einen öffentlichen PC, um die Anwendung aufzurufen.
Anstatt die "Abmelden"-Funktion zu benutzen, schließt der Anwender nur
den Browser. Der Browser ist auch eine Stunde später noch
authentifiziert, wenn ein potentieller Angreifer ihn öffnet.

**Szenario 3:** Ein Angreifer erlangt Zugang zur nicht richtig gehashten
Passwortdatenbank des Systems. Damit fallen alle Zugangsdaten quasi im
Klartext in die Hände des Angreifers.  Wir empfehlen Organisationen und
Unternehmen, ihren Entwicklern folgende Mittel bereitzustellen:

1.  <b>Zentrale Mechanismen für eine wirksame Authentifizierung und
    Session-Management</b>, die folgendes leisten:
    1.  Einhaltung aller Anforderungen an Authentifizierung und
        Session-Management aus dem OWASP Einhaltung aller Anforderungen
        an Authentifizierung und Session-Management aus dem OWASP
        [Application Security Verification Standard](ASVS "wikilink")
        (ASVS) V2 und V3.
    2.  Eine einfache Schnittstelle für Entwickler. Als gutes Beispiel
        können die [ESAPI Authenticator and User
        APIs](http://owasp-esapi-java.googlecode.com/svn/trunk_doc/latest/org/owasp/esapi/Authenticator.html)
        herangezogen werden.
2.  Schwachstellen, die XSS oder den Diebstahl von Session-IDs
    ermöglichen, sind unter allen Umständen zu vermeiden. Siehe
    \[\[Germany/Projekte/Top 10 fuer Entwickler-2013/| A3\]\].

# **JAVA**

<b>Erfinde das Sessionmanagement nicht neu\!</b> Die verbreiteten
Plattformen (wie Tomcat, Websphere, u.a.) liefern das alles schon mit.
Grundsätzliche Anforderungen an das Session Management:

  - SessionID mit TLS schützen (wie alle Authentifizierungsdaten)
    (-\>web.xml)
  - die SessionID hat in der URL nichts verloren (-\>web.xml)
  - nach jeder erfolgreichen Authentifizierung eine neue SessionID
    generieren
  - für die Erzeugung der SessionID einen kryptografisch sicheren
    Zufallszahlengenerator verwenden (Entropy mindestens 128bit)
  - Durch den <b>Server bzw. die Anwendung</b> sollte ein absolutes
    Session-Timeout <b>und</b> ein 'Inaktivitäts-Timeout' durchgesetzt
    werden
  - Expire und Max-Age Attribute (-\>web.xml):

:\* Session-Cookies (ohne Timeout): Weder 'Expire', noch 'Max-Age'
setzen, damit das Cookie im Browser nicht dauerhaft gespeichert wird

:\* Beim Benutzen von permanenten Cookies sollten aus
Kompatibilitätsgründen beide Werte gesetzt werden; der Timeout von
Cookies sollte so schnell wie möglich erfolgen (beim Ansichern von
Transaktionen im Onlinebanking ist ein Wert von ca 10 Min. mittlerweile
Standard)

  - beim Logout/TimeOut wird die SessionID auf dem Server ungültig
    gemacht, dasselbe sollte auch auf dem Client erfolgen (z.B. Cookie
    mit einem ungültigen Wert überschrieben und einen 'Expire'-Wert in
    der Vergangenheit setzen)
  - grundsätzlich das Secure-Attribut für Cookies benutzen (-\>web.xml),
    Voraussetzung: Absicherung der Verbindung mittels https
  - für Cookies das httponly-Attribut setzen (-\>web.xml)
  - Domain-und Pfad-Attribut in Cookies so eng wie möglich setzen
    (-\>web.xml)

**Beispiel:**

  - Konfigurationsdatei 'WEB-INF/web.xml' des Webservers (Auszug):

<session-config>

  -

    <session-timeout>10</session-timeout>

     

    <tracking-mode>COOKIE</tracking-mode>

     

    <cookie-config>

      -
        <secure>true</secure>
        <http-only>true</http-only>

    </cookie-config>

<session-config>
<security-constraint>

  -
    <web-resource-collection>
      -
        <web-resource-name>Entire Application</web-resource-name>
        <url-pattern>/\*</url-pattern>
    </web-resource-collection>
    <user-data-constraint>
      -
        <transport-guarantee>CONFIDENTIAL</transport-guarantee>
    </user-data-constraint>

</security-constraint>

<context-param>

  -
    <param-name>sessionCookieDomain</param-name>
    <param-value>.domain.tld</param-value>
    <param-name>sessionCookiePath</param-name>
    <param-value>/something</param-value>

</context-param>

Einen umfangreicheren Überblick über Anforderungen und zu vermeidende
Probleme gibt [ASVS requirements areas for Authentication (V2) and
Session Management (V3)](ASVS "wikilink").

  - [OWASP Authentication Cheat
    Sheet](Authentication_Cheat_Sheet "wikilink")
  - [OWASP Forgot Password Cheat
    Sheet](Forgot_Password_Cheat_Sheet "wikilink")
  - [OWASP Session Management Cheat
    Sheet](Session_Management_Cheat_Sheet "wikilink")
  - [OWASP Proactive Controls:](OWASP_Proactive_Controls "wikilink")
    [Kapitel über 'Implement Identity and Authentication
    Controls'](OWASP_Proactive_Controls#5:_Implement_Identity_and_Authentication_Controls "wikilink")
  - [OWASP Development Guide: Kapitel über
    Authentifikation](:Category:OWASP_Guide_Project "wikilink")
  - [OWASP Testing Guide: Kapitel über
    Authentifikation](Testing_for_authentication "wikilink")
  - [OWASP Testing Guide: Kapitel über Session
    Management](Testing_for_Session_Management "wikilink")
  - [OWASP Testing Guide: Abschitt über
    Logout](Testing_for_Logout_and_Browser_Cache_Management_%28OWASP-AT-007%29 "wikilink")

<!-- end list -->

  - [CWE Entry 287 on Improper
    Authentication](http://cwe.mitre.org/data/definitions/287.html)
  - [CWE Entry 384 on Session
    Fixation](http://cwe.mitre.org/data/definitions/384.html)

# **PHP**

<b>Erfinde das Sessionmanagement nicht neu\!</b> PHP liefert das alles
schon mit.
Grundsätzliche Anforderungen an das Session Management:

  - SessionID mit TLS schützen (wie alle Authentifizierungsdaten)
    (-\>php.ini)
  - die SessionID hat in der URL nichts verloren (-\>php.ini)
  - nach jeder erfolgreichen Authentifizierung eine neue SessionID
    generieren
  - für die Erzeugung der SessionID einen kryptografisch sicheren
    Zufallszahlengenerator verwenden (Entropy mindestens 128bit)
  - der Timeout von Cookies sollte so schnell wie möglich erfolgen (beim
    Onlinebanking ist ein Wert von ca 10 Min. mittlerweile Standard)
    (-\>php.ini)
  - beim Logout/TimeOut wird die SessionID auf dem Server ungültig
    gemacht
  - grundsätzlich das Secure-Attribut für Cookies benutzen (-\>php.ini)
  - für Cookies das httponly-Attribut setzen (-\>php.ini)
  - Domain-und Pfad-Attribut in Cookies so eng wie möglich setzen
    (-\>php.ini)

<!-- end list -->

  - Konfigurationsdatei 'php.ini':

session.cookie_secure = On

session.cookie_httponly = On

session.use_trand_sid = Off

session.use_only_cookies = On

session.hash_function = sha512

tbd Text

tbd Text

(ganze Breite) Text

<headertabs />