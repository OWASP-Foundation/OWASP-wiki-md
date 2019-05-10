` `

`    <td ``>Jeder mit Netzwerkzugriff kann Anfragen an die Anwendung senden.`
`Können anonyme Benutzer auf private Seiten zugreifen oder normale Benutzer auf privilegierte Seiten?`

</td>

`    <td ``>Ein angemeldeter Benutzer ändert den URL auf eine Seite für privilegierte Benutzer. Erhält er Zugriff?`

Anonyme Benutzer könnten auf ungeschützte, private Seiten zugreifen.

</td>

`    <td colspan=2 ``>In Anwendungen wird der Zugriff auf Seiten nicht immer verlässlich abgesichert. Manchmal wird Zugriffsschutz durch Konfiguration realisiert, die ggf. auch fehlerhaft sein kann. Manchmal vergessen die Entwickler auch nur, die notwendige Prüfung zu implementieren.`
`Solche Fehler lassen sich einfach entdecken. Die größte Schwierigkeit besteht darin, herauszufinden, welche angreifbaren Seiten (URLs) existieren.`

</td>

`    <td ``>Solche Fehler erlauben es Angreifern, Funktionen zu nutzen, für die sie nicht berechtigt sind.`
`Administrative Funktionen sind ein wesentliches Ziel bei diesem Angriffstyp.`

</td>

`    <td ``>Betrachten Sie den Wert der Geschäftsprozesse der betroffenen Funktionen und Daten.`
`Bedenken Sie ebenfalls die Auswirkung auf Ihre Reputation im Falle eines Bekanntwerdens der Schwachstelle.`

</td>

**Szenario 1**: Der Angreifer ruft die Zieladressen einfach direkt auf.
Die folgenden URLs erfordern eine Anmeldung. Für den Aufruf von
“admin_getappInfo” sind darüber hinaus administrative Rechte
erforderlich:
http://example.com/app/<span style="color:black;">**getappInfo**</span>
http://example.com/app/<span style="color:red;">**admin_getappInfo**</span>
 Erhält ein nicht angemeldeter Benutzer Zugriff, ist dies eine
Schwachstelle. Erhält ein angemeldeter, nicht-administrativer Benutzer
Zugriff auf “<span style="color:red;">**admin_getappInfo**</span>”, ist
dies ebenfalls eine Schwachstelle und könnte dazu führen, dass ein
Angreifer auf weitere administrative Seiten Zugriff erhält.
**Szenario 2**: Eine Anwendung nutzt den Parameter ‘action‘, um
spezifische Aufrufe zu ermöglichen. Unterschiedliche “Actions” erfordern
dabei unterschiedliche Rollen. Wird dies nicht geprüft, handelt es sich
um eine Schwachstelle.  Die Anwendung sollte ein zentrales, möglichst
einfach aufgebautes und widerspruchsfreies Modul zur Autorisierung
verwenden, das leicht analysierbar ist und von allen Funktionen
aufgerufen wird. Häufig werden diese Schutzfunktionen von externen
Komponenten bereitgestellt.

1.  Der Prozess zur Rechtevergabe sollte einfach sein. Ebenso dessen
    Aktualisierung und Prüfung. Verwenden Sie nie hart kodierte
    Berechtigungsvergaben.
2.  Berechtigungszuweisung sollte standardmäßig keine Rechte zulassen
    und explizite Rechte für Zugriffe erfordern.
3.  Wenn die Funktion in einem Workflow eingebunden wird, stellen Sie
    sicher, dass die Rechte während des gesamten Prozesses erhalten
    bleiben.

**Hinweis:** Viele Anwendungen blenden lediglich die Links zu
privilegierten Funktionen aus. Dies ist jedoch <u>kein</u> wirksamer
Schutz. Der Zugriff muss ebenfalls in der zentralen Berechtigungsprüfung
kontrolliert werden.

# **JAVA**

### Zugriffssteuerung über den Web-Container (Declarative Access Control)

Die Autorisierung übernimmt der Web-Container. Die Steuerung erfolgt
über die Konfigurationsdatei web.xml (Deployment Descriptor). Es ist
kein Programmieraufwand notwendig.

  - Konfigurationsdatei 'WEB-INF/web.xml' des Webservers (Auszug):

<security-constraint>
: <web-resource-collection>

  -

      -
        <web-resource-name>Restricted Resources</web-resource-name>
        <description>Only for Authenticated Users</description>
        <url-pattern>/\*</url-pattern>
        <http-method>GET</http-method>
        <http-method>POST</http-method>

    </web-resource-collection>

    <auth-constraint>

      -
        <role-name>AuthorizedUser</role-name>

    </auth-constraint>

</security-constraint>

<security-constraint>
: <web-resource-collection>

  -

      -
        <web-resource-name>MyLogin</web-resource-name>
        <description>Access to Login</description>
        <url-pattern>/login.jsp</url-pattern>
        <http-method>GET</http-method>
        <http-method>POST</http-method>

    </web-resource-collection>

</security-constraint>

<security-constraint>
: <web-resource-collection>

  -

      -
        <web-resource-name>Public Resources</web-resource-name>
        <description>Some public pages</description>
        <url-pattern>/index.jsp</url-pattern>
        <url-pattern>/public/\*</url-pattern>
        <http-method>GET</http-method>

    </web-resource-collection>

</security-constraint>

-----

tbd.  tbd. --------------------\>

  - [<u>OWASP Proactive
    Controls:</u>](OWASP_Proactive_Controls "wikilink") [<u>Kapitel über
    'Implement Access
    Controls'</u>](OWASP_Proactive_Controls#6:_Implement_Access_Controls "wikilink")
  - [<u>OWASP Top 10-2007 on Failure to Restrict URL
    Access</u>](Top_10_2007-Failure_to_Restrict_URL_Access "wikilink")
  - [<u>ESAPI Access Control
    API</u>](http://owasp-esapi-java.googlecode.com/svn/trunk_doc/latest/org/owasp/esapi/AccessController.html)
  - [<u>OWASP Development Guide: Chapter on
    Authorization</u>](Guide_to_Authorization "wikilink")
  - [<u>OWASP Testing Guide: Testing for Path
    Traversal</u>](Testing_for_Path_Traversal "wikilink")
  - [<u>OWASP Article on Forced
    Browsing</u>](Forced_browsing "wikilink")

\----- deleted Links:

  - [<u>JAAS_Tomcat_Login_Module: Configure the security constraints
    in
    web.xml</u>](JAAS_Tomcat_Login_Module#5_-_Configure_the_security_constraints_in_web.xml "wikilink")
  - [<u>Declarative_Access_Control_in_Java</u>](Declarative_Access_Control_in_Java "wikilink")

\-----------------------\>

  - [<u>Codereview-Deployment:
    Protecting_JSP_Pages</u>](Codereview-Deployment#Protecting_JSP_Pages "wikilink")
  - [<u>Web App Access Control
    Design</u>](http://secappdev.org/handouts/2012/Jim%20Manico%20&%20%20Eoin%20Keary/Final%20-%20Access%20Control%20Module%20v4.1.pdf)

Weitere Anforderungen an den Zugriffsschutz sind in der [<u>ASVS
requirements area for Access Control
(V4)</u>](https://www.owasp.org/index.php/ASVS) enthalten, deutsche
Übersetzung (Ver 1.0):
([<u>PDF</u>](http://owasp-asvs.googlecode.com/svn/trunk/documentation/asvs-webapp-release-2009-de.pdf),
[<u>Word</u>](http://owasp-asvs.googlecode.com/svn/trunk/documentation/asvs-webapp-release-2009-de.doc))

  - [<u>CWE Entry 285 on Improper Access Control
    (Authorization)</u>](http://cwe.mitre.org/data/definitions/285.html)

# **PHP**

### Zugriffssteuerung über den Web-Container (Declarative Access Control)

Die Autorisierung übernimmt der Web-Container. Die Steuerung erfolgt
über die Konfigurationsdatei .... (Deployment Descriptor). Es ist kein
Programmieraufwand notwendig.

  - Konfigurationsdatei '....' des Webservers (Auszug):

...
: ...

  -

      -
        ...


tbd.  tbd.

  - [<u>OWASP Top 10-2007 on Failure to Restrict URL
    Access</u>](https://www.owasp.org/index.php/Top_10_2007-Failure_to_Restrict_URL_Access)
  - [<u>ESAPI Access Control
    API</u>](http://owasp-esapi-java.googlecode.com/svn/trunk_doc/latest/org/owasp/esapi/AccessController.html)
  - [<u>OWASP Development Guide: Chapter on
    Authorization</u>](https://www.owasp.org/index.php/Guide_to_Authorization)
  - [<u>OWASP Testing Guide: Testing for Path
    Traversal</u>](https://www.owasp.org/index.php/Testing_for_Path_Traversal)
  - [<u>OWASP Article on Forced
    Browsing</u>](https://www.owasp.org/index.php/Forced_browsing)

Weitere Anforderungen an den Zugriffsschutz sind in der [<u>ASVS
requirements area for Access Control
(V4)</u>](https://www.owasp.org/index.php/ASVS) enthalten, deutsche
Übersetzung (Ver 1.0):
([<u>PDF</u>](http://owasp-asvs.googlecode.com/svn/trunk/documentation/asvs-webapp-release-2009-de.pdf),
[<u>Word</u>](http://owasp-asvs.googlecode.com/svn/trunk/documentation/asvs-webapp-release-2009-de.doc))

  - [<u>CWE Entry 285 on Improper Access Control
    (Authorization)</u>](http://cwe.mitre.org/data/definitions/285.html)

\-- weitere Programmiersprachen oder evtl Anti-Beispiele --- \>

# **Test**

tbd Text

tbd Text

tbd Text

(ganze Breite) Text

\---------------------------------------------\> <headertabs />