`   <td colspan=2 ``>`

Angreifer brechen i.d.R. nicht die Verschlüsselung selbst. Stattdessen
stehlen sie Schlüssel, führen manuell Seiten- oder MITM-Angriffe aus
bzw. stehlen Klartext vom Server, während der Übertragung oder aus dem
Browser des Benutzers. Bereits zuvor entwendete Passwort-Datenbanken
können mithilfe von Grafikkarten per Brute-Force aufgebrochen werden.

</td>

`   <td colspan=2  ``>`

`In den letzten Jahren war dies die Angriffsart, die am häufigsten wirksam war. Fehlende Verschlüsselung vertraulicher Daten ist hierbei die häufigste Schwachstelle. Das Nutzen von Kryptographie erfolgt oft mit schwacher Schlüsselerzeugung und -verwaltung und der Nutzung schwacher Algorithmen, Protokolle und Verfahren (Cipher) insbesondere für Passwort-Hashes. Server-Schwachstellen bei der Transport-verschlüsselung können einfach erkannt werden, hingegen ist dies für gespeicherte Daten schwierig. `

</td>

`   <td colspan=2  ``>`

`Fehler kompromittieren regelmäßig alle vertraulichen Daten. Es handelt sich hierbei oft auch um sensible personenbezogene Daten wie Patienten-, Personal-, Login-Daten oder Kreditkarteninformationen, die aufgrund gesetzlicher oder regulatorischen Vorgaben zu schützen sind, wie z.B. die DSGVO der EU oder nationale Datenschutz-Gesetze. `

</td>

Zunächst müssen Sie den Schutzbedarf der übertragenen und der
gespeicherten Daten bestimmen. Beispielsweise benötigen Passwörter,
Kreditkartendaten, Patientendaten, Personaldaten und
Geschäftsgeheimnisse einen erhöhten Schutz, insbeson-dere wenn dies in
Datenschutzgesetzen, wie z.B. der Daten-schutz-Grundverordnung (DSGVO)
der EU oder regulatorisch, wie z.B. im Finanzwesen dem PCI Data Security
Standard (PCI DSS), gefordert wird. Folgendes ist zu klären:

  - Werden Daten in Klartext übertragen? Dies betrifft insbesondere
    Protokolle wie z.B. HTTP, SMTP oder FTP. Das Internet ist hier
    besonders gefährlich. Überprüfen Sie auch interne Übertragungen,
    z.B. zwischen Load-Balancern, Web-Servern und Backend-Systemen.
  - Werden sensible Daten im Klartext gespeichert, inkl. Backups?
  - Werden veraltete oder schwache Kryptoverfahren genutzt, z.B. per
    Default-Einstellung oder veraltetem Code?
  - Werden vordefinierte, schwache oder alte Schlüssel zur
    Verschlüsselung benutzt oder gibt es kein ordnungsgemäßes
    Schlüsselmanagement inkl. Schlüsselwechsel?
  - Wird die Verschlüsselung nicht verbindlich erzwungen, z.B. fehlen
    Vorgaben für den Browser z.B. im HTTP-Header.
  - Prüft der Client (z.B. APP, Mail-Prg) Serverzertifikate richtig?

Vgl. auch ASVS <u>[Crypto
(V7)](:Category:OWASP_Application_Security_Verification_Standard_Project "wikilink")</u>,
<u>[Data Protection
(V9)](:Category:OWASP_Application_Security_Verification_Standard_Project "wikilink")</u>
und <u>[SSL/TLS
(V10)](:Category:OWASP_Application_Security_Verification_Standard_Project "wikilink")</u>.

Für alle vertraulichen Daten sollten Sie zumindest:

  - Legen Sie den Schutzbedarf der verarbeiteten, gespeicherten und
    übertragenen Daten gemäß Klassen fest. Berücksichtigen Sie dabei
    auch Datenschutzgesetze, regulatorische und Geschäfts-Anforderungen.
  - Legen Sie Maßnahmen je Klasse fest.
  - Kein unnötiges Speichern vertraulicher Daten. Sofortiges Löschen
    nicht mehr benötigter Daten oder PCI-DSS-konformes Speichern von
    Ersatzwerten (Tokenisierung) oder gar gekürzten (trunkierten)
    Werten. Daten, die es nicht gibt, können auch nicht gestohlen
    werden.
  - Verschlüsseltes Speichern von sensitiven Daten.
  - Aktuelle, starke Algorithmen und Schlüssel (z.B. gemäß BSI
    <u>[TR-02102](https://www.bsi.bund.de/DE/Publikationen/TechnischeRichtlinien/tr02102/index_htm.html)</u>)
    u. wirksames Schlüsselmanagement verwenden.
  - Nutzen von Transportverschlüsselung mit sicheren Protokollen, wie
    z.B. TLS mit priorisierten Ciphern, die ausschließlich Perfect
    Forward Secrecy (PFS) und sichere Parameter nutzen. Konfigurieren
    von Anweisungen wie z.B. HTTP Strict Transport Security
    (<u>[HSTS](HTTP_Strict_Transport_Security_Cheat_Sheet "wikilink")</u>)
    zum obligatorischen Verschlüsseln.
  - Deaktivieren des Caches für den Empfang sensibler Daten.
  - Passwörter mit einem speziellen, adaptiven Salting-Hash-Algorithmus
    mit hohem Rechenaufwand (=Verzögerung) speichern
    (<u>[Argon2](https://www.cryptolux.org/index.php/Argon2)</u>,
    <u>[scrypt](https://wikipedia.org/wiki/Scrypt)</u>,
    <u>[bcrypt](https://wikipedia.org/wiki/Bcrypt)</u> oder
    <u>[PBKDF2](https://wikipedia.org/wiki/PBKDF2)</u>).
  - Unabhängige Überprüfung der Wirksamkeit der Einstellungen.

<b>Szenario 1:</b> Eine Anwendung verschlüsselt Kreditkartendaten
automatisch bei der Speicherung in einer Datenbank. Das bedeutet aber
auch, dass durch SQL-Injection erlangte Kreditkartendaten in diesem Fall
automatisch entschlüsselt werden.

<b>Szenario 2:</b> Eine Webseite benutzt kein TLS, erzwingt dies nicht
auf allen Seiten oder lässt schwache Verschlüsselung zu. Der Angreifer
liest die Kommunikation mit (z.B. in einem offenen WLAN), ersetzt HTTPS-
durch HTTP-Verbindungen, hört diese ab und stiehlt das Sitzungscookie.
Durch Wiedereinspielen dieses Cookies übernimmt der Angreifer die
(authentifizierte) Sitzung des Nutzers und erlangt Zugriff auf dessen
private Daten. Anstatt dessen kann der Angreifer auch die übertragenen
Daten ändern, z.B. den Empfänger einer Überweisung.

<b>Szenario 3:</b> Die Passwortdatenbank benutzt einfache Hashwerte oder
Hashes ohne Salt zur Speicherung der Passwörter. Eine Schwachstelle in
der Downloadfunktion erlaubt dem Angreifer den Zugriff auf die
Passwortdatei. Zu Hashes ohne Salt kann über vorausberechnete
Rainbow-Tabellen der Klartext gefunden werden. Hashes, die über einfache
oder schnelle Funktionen be-rechnet wurden, können mittels Grafikkarte
gebrochen werden.

  - <u>[OWASP Proactive Controls: Protect
    Data](OWASP_Proactive_Controls#7:_Protect_Data "wikilink")</u>
  - <u>[OWASP Application Security Verification
    Standard](:Category:OWASP_Application_Security_Verification_Standard_Project "wikilink")</u>
    (V7,9, 10)
  - <u>[OWASP Cheat Sheet: Transport Layer
    Protection](Transport_Layer_Protection_Cheat_Sheet "wikilink")</u>
  - <u>[OWASP Cheat Sheet: User Privacy
    Protection](User_Privacy_Protection_Cheat_Sheet "wikilink")</u>
  - <u>[OWASP Cheat Sheet:
    Password](Password_Storage_Cheat_Sheet "wikilink")</u> und
    <u>[Cryptographic
    Storage](Cryptographic_Storage_Cheat_Sheet "wikilink")</u>
  - <u>[OWASP Security Headers
    Project](OWASP_Secure_Headers_Project "wikilink")</u>
  - <u>[Cheat Sheet:
    HSTS](HTTP_Strict_Transport_Security_Cheat_Sheet "wikilink")</u>
  - <u>[OWASP Testing Guide: Testing for weak
    cryptography](Testing_for_weak_Cryptography "wikilink")</u>

<!-- end list -->

  - <u>[CWE-202: Exposure of sens. information through data
    queries](https://cwe.mitre.org/data/definitions/202.html)</u>
  - <u>[CWE-310: Cryptographic
    Issues](https://cwe.mitre.org/data/definitions/310.html)</u>
  - <u>[CWE-311: Missing
    Encryption](https://cwe.mitre.org/data/definitions/311.html)</u>
  - <u>[CWE-312: Cleartext Storage of Sensitive
    Information](https://cwe.mitre.org/data/definitions/312.html)</u>
  - <u>[CWE-319: Cleartext Transmission of Sensitive
    Information](https://cwe.mitre.org/data/definitions/319.html)</u>
  - <u>[CWE-326: Weak
    Encryption](https://cwe.mitre.org/data/definitions/326.html)</u>
  - <u>[CWE-327: Broken/Risky
    Crypto](https://cwe.mitre.org/data/definitions/327.html)</u>
  - <u>[CWE-359: Exposure of Private Information (Privacy
    Violation)](https://cwe.mitre.org/data/definitions/359.html)</u>
  - <u>[BSI TR-02102 Kryptographische Verfahren: Empfehlungen und
    Schlüssellängen](https://www.bsi.bund.de/DE/Publikationen/TechnischeRichtlinien/tr02102/index_htm.html)</u>