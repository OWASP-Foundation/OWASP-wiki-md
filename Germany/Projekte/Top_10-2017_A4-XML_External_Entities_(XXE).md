`   <td colspan=2 ``>`

Angreifer können anfällige XML Verarbeiter instrumentalisieren, wenn sie
XML direkt hochladen können oder schädliche Inhalte in ein XML-Dokument
aufnehmen können, wobei sie anfälligen Code, Abhängigkeiten oder
Integrationen ausnutzen.

</td>

`   <td colspan=2  ``>`

`Standardmäßig erlauben viele ältere XML-Prozessoren die Spezifikation einer externen Entität, also einer URI, die während der XML-Verarbeitung dereferenziert und ausgewertet wird. `<u>[`SAST`](Source_Code_Analysis_Tools "wikilink")</u>`-Tools  können dies erkennen, indem sie Abhängigkeiten und Konfigura-tionen überprüfen. `<u>[`DAST`](:Category:Vulnerability_Scanning_Tools "wikilink")</u>`-Tools erfordern zusätzliche manuelle Schritte, um dieses Problem zu erkennen und auszunutzen. Manuelle Tester müssen geschult werden, wie man auf XXE testet, was Stand 2017 typischerweise selten passiert. `

</td>

`   <td colspan=2  ``>`

`Diese Fehler können ausgenutzt werden, um Daten zu extrahieren, eine Remote-Anfrage vom Server auszuführen, interne Systeme zu scannen, einen Denial-of-Service-Angriff oder auch andere Angriffe durchzuführen.`
`Die Auswirkungen auf das Unternehmen hängen vom Schutzbedarf der Anwendung und ihrer Daten ab. `

</td>

Anwendungen und insbesondere XML-basierte Webservices oder nachgelagerte
Integrationen können in folgenden Fällen anfällig für Angriffe sein:

  - Die Anwendung akzeptiert direkt XML oder XML-Uploads, insbesondere
    aus nicht vertrauenswürdigen Quellen oder fügt nicht
    vertrauenswürdige Daten in XML-Dokumente ein, die dann von einem
    XML-Prozessor analysiert werden.
  - Die XML-Prozessoren in der Anwendung oder SOAP-basierte Webservices
    haben <u>[Document Type Definitions
    (DTDs)](https://en.wikipedia.org/wiki/Document_type_definition)</u>
    aktiviert. Da der genaue Mechanismus zum Deaktivieren der
    DTD-Verarbeitung je nach Prozessor variiert, ist es empfehlenswert,
    eine Referenz wie den <u>[OWASP Cheat Sheet 'XXE
    Prevention'](XML_External_Entity_\(XXE\)_Prevention_Cheat_Sheet "wikilink")</u>.
  - Wenn Ihre Anwendung SAML für die Identitätsverarbeitung im Rahmen
    von föderierter Sicherheit oder für Single Sign On (SSO) Zwecke
    verwendet. SAML verwendet XML für Identitätsbekundungen und kann
    daher anfällig sein.
  - Wenn die Anwendung SOAP vor Version 1.2 verwendet, ist sie
    wahrscheinlich anfällig für XXE-Angriffe, wenn XML-Entitäten an das
    SOAP-Framework übergeben werden.
  - Die Anfälligkeit für XXE-Angriffe bedeutet wahrscheinlich, dass die
    Anwendung anfällig für Denial-of-Service-Angriffe, einschließlich
    des sogenannten "Billion Laughs" Angriffs, ist.

Die Schulung von Entwicklern ist unerlässlich, um XXE zu identifizieren
und zu beheben. Zusätzlich:

  - Verwenden Sie möglichst weniger komplexe Datenformate, wie JSON und
    vermeiden Sie die Serialisierung sensibler Daten.
  - Patchen oder aktualisieren Sie alle XML-Prozessoren und
    Bibliotheken, die von der Anwendung oder dem zugrunde liegenden
    Betriebssystem verwendet werden. Verwenden Sie Werkzeuge zur Prüfung
    von Abhängigkeiten. Aktualisieren Sie auf SOAP 1.2 oder höher.
  - Deaktivieren Sie die Verarbeitung von externen XML-Entitäten und
    DTDs in allen XML-Parsern in der Anwendung, gemäß dem <u>[OWASP
    Cheat Sheet 'XXE
    Prevention'](XML_External_Entity_\(XXE\)_Prevention_Cheat_Sheet "wikilink")</u>.
    Implementierung einer positiven serverseitigen Eingabevalidierung
    ("White-listing"), -filterung oder -bereinigung, um bösartige Daten
    in XML-Dokumenten, Headern oder Knoten zu verhindern.
  - Vergewissern Sie sich, dass die Upload-Funktionalität für XML- oder
    XSL-Dateien eingehende XML-Daten mithilfe der XSD-Validierung oder
    ähnlichem validiert.
  - <u>[SAST](Source_Code_Analysis_Tools "wikilink")</u>-Tools können
    helfen, XXE im Quellcode zu erkennen, jedoch ist die manuelle
    Codeüberprüfung die beste Alternative in großen, komplexen
    Anwendungen mit vielen Integrationen.
  - Wenn dies nicht möglich ist, sollten Sie die Verwendung von
    virtuellen Patches, API-Sicherheitsgateways oder Web Application
    Firewalls (WAFs) in Betracht ziehen, um XXE-Angriffe zu erkennen, zu
    überwachen und zu blockieren.

Zahlreiche öffentliche XXE-Probleme wurden entdeckt, darunter auch
Angriffe auf Embedded-Geräte. XXE tritt an vielen unerwarteten Stellen
auf, einschließlich tief verschachtelter Abhängigkeiten. Der einfachste
Weg, wenn möglich, ist das Hochladen einer bösartigen XML-Datei:

<b>Szenario 1:</b> Der Angreifer versucht, Daten vom Server zu
extrahieren:

<b><span style="color:red;"> \<?xml version="1.0"
encoding="ISO-8859-1"?\>

  -
    \<\!DOCTYPE foo \[
    \<\!ELEMENT foo ANY \>
    \<\!ENTITY xxe SYSTEM "file:///etc/passwd" \>\]\>
    \<foo\>\&xxe;\</foo\>

</span></b>

<b>Szenario 2:</b> Ein Angreifer durchsucht das private Netzwerk des
Servers, indem er die obige ENTITY-Zeile ändert zu:
<b><span style="color:red;">

  -
    \<\!ENTITY xxe SYSTEM "https://192.168.1.1/private" \>\]\>

</span></b>

<b>Szenario 3:</b> Ein Angreifer versucht einen
Denial-of-Service-Angriff, indem er eine potenziell endlose Datei
einfügt: <b><span style="color:red;">

  -
    \<\!ENTITY xxe SYSTEM "file:///dev/random" \>\]\>

</span></b>

  - <u>[OWASP Application Security Verification
    Standard](:Category:OWASP_Application_Security_Verification_Standard_Project#tab=Home "wikilink")</u>
  - <u>[OWASP Testing Guide: Testing for XML
    Injection](Testing_for_XML_Injection_\(OTG-INPVAL-008\) "wikilink")</u>
  - <u>[OWASP XXE
    Vulnerability](XML_External_Entity_\(XXE\)_Processing "wikilink")</u>
  - <u>[OWASP Cheat Sheet: XXE
    Prevention](XML_External_Entity_\(XXE\)_Prevention_Cheat_Sheet "wikilink")</u>
  - <u>[OWASP Cheat Sheet: XML
    Security](XML_Security_Cheat_Sheet "wikilink")</u>

<!-- end list -->

  - <u>[CWE-611: Improper Restriction of
    XXE](https://cwe.mitre.org/data/definitions/611.html)</u>
  - <u>[Billion Laughs
    Attack](https://ioactive.com/die-laughing-from-a-billion-laughs/)</u>
  - <u>[SAML Security XML External Entity
    Attack](https://secretsofappsecurity.blogspot.tw/2017/01/saml-security-xml-external-entity-attack.html)</u>
  - <u>[Detecting and exploiting XXE in SAML
    Interfaces](https://web-in-security.blogspot.tw/2014/11/detecting-and-exploiting-xxe-in-saml.html)</u>