` `

`    <td ``>Jeder mit Zugriff auf Ihre vertraulichen Daten (Backups inkl.) ist zu betrachten. Das betrifft die Speicherung, die Übertragung und auch die Daten im Browser der Kunden. Externe und interne Bedrohungen sind relevant.`

</td>

`    <td ``>`

Angreifer brechen i.d.R. nicht die Verschlüsselung selbst. Stattdessen
stehlen sie Schlüssel, führen Seiten- oder MITM-Angriffe aus oder
stehlen Klartext vom Server, während der Übertragung oder aus dem
Browser des Kunden heraus.

</td>

`    <td colspan=2  ``>`

Fehlende Verschlüsselung vertraulicher Daten ist die häufigste
Schwachstelle. Die Nutzung von Kryptographie erfolgt oft mit schwacher
Schlüsselerzeugung und -verwaltung und der Nutzung schwacher
Algorithmen, insbesondere für das Password Hashing. Browser
Schwachstellen sind verbreitet und leicht zu finden, aber nur schwer
auszunutzen. Ein eingeschränkter Zugriff lässt ext. Angreifer Probleme
auf dem Server i.d.R. nur schwer finden und ausnutzen.

</td>

`    <td ``>`

Fehler kompromittieren regelmäßig vertrauliche Daten. Es handelt sich
hierbei oft um sensitive Daten wie personenbezogene Daten, Benutzernamen
und Passwörter oder Kreditkarteninformationen.

</td>

`    <td ``>`

Betrachten Sie den Wert verlorener Daten und die Auswirkungen auf die
Reputation des betroffenen Unternehmens. Hat es ggf. auch juristische
Konsequenzen, wenn die Daten bekannt werden?

</td>

**Szenario 1**: Eine Anwendung verschlüsselt Kreditkartendaten
automatisch bei der Speicherung in einer Datenbank. Das bedeutet aber
auch durch SQL-Injection erlangte Kreditkartendaten in diesem Fall
automatisch entschlüsselt werden. Die Anwendung hätte die Daten mit eine
Public Key verschlüsseln sollen und nur nachgelagerte Anwendungen und
nicht die Webanwendung selbst hätten die Daten mit dem Private Key
entschlüsseln dürfen.
**Szenario 2**: Eine Webseite schützt die authentisierten Seiten nicht
mit SSL. Der Angreifer stiehlt das Sitzungscookie des Nutzers durch
einfaches Mitlesen der Kommunikation (z.B. in einem offenen WLAN). Durch
Wiedereinspielen dieses Cookies übernimmt der Angreifer die Sitzung des
Nutzers und erlangt Zugriff auf die privaten Daten des Nutzers.
**Szenario 3**: Die Passwortdatenbank benutzt Hashwerte ohne Salt zur
Speicherung der Passwörter. Eine Schwachstelle in der Downloadfunktion
erlaubt dem Angreifer den Zugriff auf die Datei. Zu allen Hashes kann
über eine Rainbowtabelle mit vorausberechneten Hashes der Klartext
gefunden werden.
Eine Übersicht über alle Tücken unsicherer Kryptografie, SSL-Verwendung
und Datensicherheit liegt weit außerhalb der Top 10. Für alle
vertraulichen Daten sollten Sie zumindest:

1.  Klärung der Bedrohungen, vor denen die Daten zu schützen sind (z. B.
    Innen- und Außentäter) und sicherstellen, dass vertrauliche Daten
    bei der Übertragung/Speicherung geeignet durch Verschlüsselung
    geschützt werden.
2.  Kein unnötiges Speichern vertraulicher Daten. Löschung nicht mehr
    benötigter Daten. Daten, die es nicht gibt, können auch nicht
    gestohlen werden.
3.  Sicherstellen, dass starke Algorithmen und Schlüssel (z.B. gemäß
    FIPS-140, [BSI
    TR-02102-2)](https://www.bsi.bund.de/SharedDocs/Downloads/DE/BSI/Publikationen/TechnischeRichtlinien/TR02102/BSI-TR-02102-2.pdf)
    verwendet werden.
4.  Sicherstellen, dass Passwörter mit einem speziell für Passwortschutz
    entwickelten Algorithmus gespeichert werden
    ([bcrypt](http://en.wikipedia.org/wiki/Bcrypt),
    [PBKDF2](http://en.wikipedia.org/wiki/PBKDF2) oder
    [scrypt](http://en.wikipedia.org/wiki/Scrypt)).
5.  Deaktivieren der Autovervollständigung und des Cachings in
    Formularen mit vertraulichen Informationen.

# **JAVA**

#### JAVA-Teil 1: Kryptografisch unsichere Speicherung

Ein einfaches Beispiel für die Veschlüsselung von Texten, hier mit dem
AES-128 Algorithmus. Die Auswahl an Verschlüsselungsparametern wie
beispielsweise Algorithmus, Ciphermodus oder Schlüssellänge ist groß und
kommt immer auf die jeweiligen Daten und die Anwendung an.  String
plainText = "HelloWorld";

// password setzen
String password = "my128bitPassword";

// CBC Cipher immer mit einem zufällig erzeugten
// Initialization Vector (IV) initialisieren (Länge 16 Byte)
byte\[\] ivBytes = new byte\[16\];
(new SecureRandom()).nextBytes(ivBytes);

// den Schlüssel erzeugen
SecretKeySpec key = new SecretKeySpec(password.getBytes(), "AES");

// Container für die Verschlüsselungs Parameter
IvParameterSpec paramSpec = new IvParameterSpec(ivBytes);

// Chiffrierer erzeugen und initialisieren
// Algorithmus: AES
// Modus: CBC
// Padding: PKCS5Padding
Cipher cipher = Cipher.getInstance("AES/CBC/PKCS5Padding");
cipher.init(Cipher.ENCRYPT_MODE, key, paramSpec);

// Verschlüsselung durchführen
byte\[\] encrypted = cipher.doFinal(plainText.getBytes());
Die Benutzung der ESAPI erleichtert die Handhabung, da neben einer
großen Bandbreite an Verschlüsselungs-, Hash-, und Signaturalgorithmen
auch Methoden für die Schlüsselerzeugung und -verwaltung unterstüzt
werden. Nach Initialisierung der Parameter in der Konfigurationsdatei
ESAPI.properties, reduziert sich die eigentliche Verschlüsselung eines
Textes beispielsweise zu:  CipherText ciphertext =

  -

      -
        ESAPI.encryptor().encrypt( new PlainText(myplaintext) );

Beispiele für das Hashen von Passwörtern. Um die Sicherheit zu erhöhen
sollte jedes Passwort mit einem Zufallswert (Salt) berechnet und
gespeichert werden sowie möglichst viele Iterationen beim Hashing
genutzt werden.  String password = "mypassword";
// salt anlegen und mit zufälligen Bytes befüllen
byte\[\] salt = new byte\[8\];
(new SecureRandom()).nextBytes(salt);
// Hash-Generator anlegen (verwendeter Algorithmus ist SHA-256)
// und mit salt initialisieren (=\> höhere Sicherheit gegen Angriffe)
MessageDigest digest = MessageDigest.getInstance("SHA-256");
digest.reset();
digest.update(salt);
byte\[\] input = digest.digest(password.getBytes("UTF-8"));

// Hash in mehreren Iterationen (n = 100.000) berechnen
// mehr Iterationen verlangsamen Angriffe (signifikant?)
for (int i = 0; i \< 100000; i++) {

  -
    digest.reset();
    input = digest.digest(input);

}
// am Ende der Iterationen enthält input den berechneten Hash
;PBKDF2 Sicherer ist allerdings die Nutzung einer PBKDF2 (Password-Based
Key Derivation Function 2) wie im folgenden Beispiel:  public byte\[\]
generatePBKDF2Hash(String password)

  -
    throws NoSuchAlgorithmException, InvalidKeySpecException {
    : byte\[\] salt = new byte\[20\];
      -
        // salt mit zufälligen Bytes befüllen
        (new SecureRandom()).nextBytes(salt);

        int iterations = 10000;
        int keyLength = 160;
        // neuen Schlüssel erzeugen
        SecretKeyFactory factory =
        SecretKeyFactory.getInstance("PBKDF2WithHmacSHA1");
        PBEKeySpec pbeKeySpec = new PBEKeySpec(password, salt,
        iterations, keyLength);
        SecretKey mySecretKey = factory.generateSecret(pbeKeySpec);

}
byte\[\] hash = generatePBKDF2Hash(password).getEncoded();

;bcrypt Eine weiterer empfohlener Algorithmus ist bcrypt, hier
bespielsweise unter Verwendung der jBCrypt-Bibliothek (siehe
Referenzen).  String hashed = BCrypt.hashpw(password,
BCrypt.gensalt(12));  Zu bcrypt gibt es mittlerweile eine noch sicherere
Variante scrypt, der Link zu einer Beispielimplementierung findet sich
bei den Referenzen.

Um geheime Schlüssel sicher, aber auch gleichzeitig einfach zugänglich
und austauschbar aufzubewahren empfiehlt sich eine spezielle
Schlüsseldatei, wie beispielweise der Java KeyStore. In dieser Datei
werden die Schlüssel mit einem Master-Password gesichert, die Datei
selbst sollte getrennt von den verschlüsselten Daten abgelegt werden:

// Erzeugung eines symmetrischen Schlüssels mittels der vorher
beschriebenen PBKDF2
String password = "mypassword";
byte\[\] mySecretKey = generatePBKDF2Hash(password);

// neuen KeyStore für symmetrische Schlüssel erzeugen
KeyStore ks = KeyStore.getInstance("JCEKS");
ks.load(null, null);

// Schlüssel speichern
KeyStore.ProtectionParameter passwordProtection =
: new KeyStore.PasswordProtection(password); KeyStore.SecretKeyEntry
entry = new KeyStore.SecretKeyEntry(mySecretKey);
ks.setEntry("beispielkey", entry, passwordProtection);

// KeyStore in Datei speichern
FileOutputStream fos = new FileOutputStream("SecretKeyStoreDatei");
ks.store(fos,password);
fos.close();

  - Einen umfangreicheren Überblick über die Anforderungen, gibt es
    unter [ASVS requirements on Cryptography (V7), Data Protection (V9)
    und Communications Security (V10)](ASVS "wikilink").
  - [OWASP Cryptographic Storage Cheat
    Sheet](Cryptographic_Storage_Cheat_Sheet "wikilink")
  - [OWASP Password Storage Cheat
    Sheet](Password_Storage_Cheat_Sheet "wikilink")
  - [OWASP Transport Layer Protection Cheat
    Sheet](Transport_Layer_Protection_Cheat_Sheet "wikilink")
  - [OWASP Testing Guide: Chapter on SSL/TLS
    Testing](Testing_for_SSL-TLS "wikilink")
  - [OWASP SSL Advanced Forensic Tool (O-SAFT)](O-Saft "wikilink")
  - [OWASP Proactive Controls:](OWASP_Proactive_Controls "wikilink")
    [Kapitel über 'Protect
    Data'](OWASP_Proactive_Controls#7:_Protect_Data "wikilink")

<!-- end list -->

  -
    Älter:

<!-- end list -->

  - [OWASP Top 10-2007 on Insecure Cryptographic
    Storage](Top_10_2007-Insecure_Cryptographic_Storage "wikilink")
  - [OWASP Development Guide: Chapter on
    Cryptography](Guide_to_Cryptography#Insecure_transmission_of_secrets "wikilink")
  - [OWASP Code Review Guide: Chapter on
    Cryptography](Codereview-Cryptography "wikilink")

<!-- end list -->

  - [CWE Entry 310 on Cryptographic
    Issues](http://cwe.mitre.org/data/definitions/310.html)
  - [CWE Entry 312 on Cleartext Storage of Sensitive
    Information](http://cwe.mitre.org/data/definitions/312.html)
  - [CWE Entry 319 on Cleartext Transmission of Sensitive
    Information](http://cwe.mitre.org/data/definitions/319.html)
  - [CWE Entry 326 on Weak
    Encryption](http://cwe.mitre.org/data/definitions/326.html)
  - [Reine Java Implementierung von
    BCrypt](http://www.mindrot.org/projects/jBCrypt)
  - [Beispielimplementierung von SCrypt](https://github.com/wg/scrypt)
  - [SSL LABS: 'SSL/TLS Deployment Best
    Practices'](https://www.ssllabs.com/projects/best-practices/index.html)
  - [BSI: 'TR-02102-2
    Teil 2'](https://www.bsi.bund.de/DE/Publikationen/TechnischeRichtlinien/tr02102/index_htm.html)
  - [ENISA: 'Study on cryptographic
    protocols'](https://www.enisa.europa.eu/activities/identity-and-trust/library/deliverables/study-on-cryptographic-protocols)
  - [bettercrypto.org:](https://bettercrypto.org) ['Applied Crypto
    Hardening
    (DRAFT)'](https://bettercrypto.org/static/applied-crypto-hardening.pdf)
  - [MozillaWiki: Security/Server Side
    TLS](https://wiki.mozilla.org/Security/Server_Side_TLS)

# **JAVA2**

#### JAVA-Teil 2: Unzureichende Absicherung der Transportschicht

  - Absicherung der Transportschicht (beim Deployment)

Um die Verschlüsselung auf der Transportebene sollte sich der Entwickler
nie selbst kümmern, sondern dies immer dem Webserver überlassen. Im
J2EE-Deployment-Descriptor der Anwendung (= web.xml) ist die folgende
Konfiguration vorzunehmen, um sicherzustellen, dass nur ausschließlich
über https kommuniziert wird:

<security-constraint>

  -
    <web-resource-collection>
      -
        <web-resource-name>Protected Context</web-resource-name>
        <url-pattern>/\*</url-pattern>
    </web-resource-collection>
    <user-data-constraint>
      -
        <transport-guarantee>CONFIDENTIAL</transport-guarantee>
    </user-data-constraint>

</security-constraint>
Für Session-Cookies ist immer das Attribute SECURE zu setzen:
<session-config>

  -
    <cookie-config>
      -
        <secure>
          -
            true
        </secure>
    </cookie-config>

</session-config>
In der Server-Configuration ist sicherzustellen, dass nur TLS und SSL3
unterstützt werden. Das Speichern von vertraulichen Inhalten am Client
oder auf einem Proxy kann über den Header Cache-Control verhindert
werden:  Header set Cache-Control "no-cache, no store, must-revalidate"

Weitere Hinweise im [Transport Layer Protection Cheat
Sheet](https://www.owasp.org/index.php/Transport_Layer_Protection_Cheat_Sheet)

  - Absicherung der Transportschicht (auf dem Webserver - Teil 1)

<b>Sichere Verschlüsselung</b>

  - Nutzen Sie aktuelle Empfehlungen zur SSL/TLS-Sicherheit, das Thema
    ist derzeit sehr(\!) dynamisch. Z.B.:

:\* [SSL LABS: 'SSL/TLS Deployment Best
Practices'](https://www.ssllabs.com/projects/best-practices/index.html)

:\* [BSI TR-02102
Teil 2](https://www.bsi.bund.de/DE/Publikationen/TechnischeRichtlinien/tr02102/index_htm.html)

  - aktuelle Verschlüsselungsbibliotheken einsetzen, die aktuelle
    Protokolle und Verfahren unterstützen
  - Nur sichere Verschlüsselungsprotokolle unterstützen (TLS1.2, TLS1.1,
    ggf auch TLS1.0)
  - Die Verschlüsselungsverfahren auf dem Server priorisieren
  - sichere, ephemerale Verschlüsselungsverfahren (Cipher-Suites), die
    'Forward Secrecy' unterstützen (z.B. DHE_RSA, ECDHE_RSA) mit hoher
    Prio versehen. Derzeit sollte dabei DHE bevorzugt werden (bei
    ausreichender CPU), da es an vertrauenswürdigen Kurven für ECDHE
    mangelt, vgl <http://safecurves.cr.yp.to>,
    [1](https://www.schneier.com/blog/archives/2013/09/the_nsa_is_brea.html#c1675929);
    Teilweise sind bereits [Brainpool
    Curves](http://www.researchgate.net/profile/Johannes_Merkle/publication/260050106_Standardisierung_der_Brainpool-Kurven_fr_TLS_und_IPSec/file/60b7d52f36a0cc2fdd.pdf)
    für TLS implementiert
    [(RFC 7027)](https://tools.ietf.org/html/rfc7027). Aussichtsreiche,
    neue Kurven sind
    ['Curve25519'](https://tools.ietf.org/html/draft-josefsson-tls-curve25519-06)
    und
    ['Ed448-Goldilocks'](http://sourceforge.net/p/ed448goldilocks/wiki/Home/),
    die gerade für TLS definiert werden (vgl [RFC 7748 - Elliptic Curves
    for Security](https://tools.ietf.org/html/rfc7748)),
    [IANA](http://www.iana.org/assignments/tls-parameters/tls-parameters.xhtml#tls-parameters-8)
    und
    [DRAFT-ietf-tls-rfc4492bis](https://tools.ietf.org/html/draft-ietf-tls-rfc4492bis-17)
  - sichere Schlüssellängen für assymetrische und symmetrische Verfahren
    (gem. BSI TR-02102 Teil 2):

:\* Schlüsseleinigung und Authentisierung: DHE(-Parameter), RSA, DSS:
3000 bits für RSA; ECDHE: 256 bits

:\* (symmetrische) Verschlüsselung: AES: 128 bits

  - RC4 und andere schwache oder exotische Cipher <u>abschalten</u> (vgl
    (see [2](https://tools.ietf.org/html/rfc7465),
    [3](http://tools.ietf.org/html/rfc5469)), <u>ohne</u> den Zugriff
    von (noch) unterstützten Browsern, oder Suchmaschinen-Bots
    (Webcrawlern) zu verlieren.
  - Richtlinie erstellen, welche Browser und Betriebssysteme,
    unterstützt werden sollen, sowie welche Protokolle und welche
    Cipher für die verschlüsselte Verbindung jeweils ausgewählt werden
    sollen (z.B. vorübergehend noch TLSv1,
    TLS_RSA_WITH_AES_128_CBC_SHA).
  - Empfehlungen für den 'Cipher-String' auf Grundlage der oben
    genannten Anforderungen (inkl. Priorität) anhand folgender
    Szenarien:

:\* <b>Cipher-String 'A+'</b> (Advanced+, eingeschränkte Kompatibilität,
z.B. auf die neueren Browser-Versionen)

::\* Empfohlen, wenn Sie die benutzten Server und Clients steuern (z.B.
freigeben) und die Kompatibilität vorab prüfen können; Nutzt nur die
stärksten Perfect-Forward-Secrecy-Cipher (PFS-Cipher)

::\* Protokoll: TLSv1.2 (und neuer)

:\* <b>Cipher-String 'A'</b> (Advanced, bessere Kompatibilität, z.B. die
meisten neueren Browser-Versionen)

::\* Empfohlen, wenn Sie die benutzten Server und Clients steuern (z.B.
freigeben) und die Kompatibilität vorab prüfen können, wenn 'A+' zu sehr
einschränkt; Nutzt die stärkeren PFS-Cipher

::\* Protokoll: TLSv1.2 (und neuer)

:\* <b>Cipher-String 'B'</b> (Broad Compatibility, weitgehende
Kompatibilität)

::\* Empfohlen, wenn Sie nur die benutzten Server steuern; Nutzt nur
PFS-Cipher; Streben Sie mittelfristig 'A' für https an

::\* Protokoll: TLSv1.0, besser: TLSv1.1 (und neuer)

:\* <b>Cipher-String 'C'</b> (Widest Compatibility, weitgehende
Kompatibilität, auch zu Alt-Browsern und älteren, noch gepatchten
Bibliotheken sowie anderen Anwendungs-Protokollen, wie z.B. IMAPS)

::\* Noch nutzbar, wenn Sie nur die benutzten Server steuern und
Alt-Client-Systeme noch unterstützen; PFS-Cipher werden bis auf DHE mit
SHA-1 bevorzugt (um potentielle Inkompatibilitäten zu vermeiden);
Bestehende Risiken der zusätzlichen Verfahren (z.B. auch ohne PFS)
sollten bewusst eingegangen werden; Streben Sie mittelfristig 'A' für
https an, sonst mind. 'B'

::\* Protokoll: TLSv1.0 (und neuer)

:\* <b>Cipher-String 'C-'</b> (Legacy, weitgehende Kompatibilität zu
uralten Browsern und alten, noch gepatchten Bibliotheken,
Laufzeitumgebungen sowie anderen Anwendungs-Protokollen, z.B. SMTP)

::\* Nutzen Sie diese Cipher-Zusammenstellung nur, wenn Sie 3DES
(=TLS_RSA_WITH_3DES_EDE_CBC_SHA, =DES-CBC3-SHA) für richtig alte
Systeme anbieten <u>müssen</u>; PFS-Cipher werden bis auf DHE mit SHA-1
bevorzugt (um potentielle Inkompatibilitäten zu vermeiden); Bestehende
Risiken der zusätzlichen Verfahren (z.B. auch ohne PFS, 3DES) sollten
bewusst eingegangen werden; Streben Sie kurzfristig 'C' an

::\* Protokoll: TLSv1.0 (und neuer)

:\* Tabelle der Cipher:

  -

      -
        {| border="1" cellspacing="1" cellpadding="1"
        style="border-collapse:collapse; text-align: center;
        font-size:84%;"

|- style="font-size: 119%; background-color:\#DCDCDC;" \!
style="text-align:left;" |Cipher-Name:
IANA, \[openssl\] \! style="width: 8%;" | Cipher-Hex-Wert \!
style="width:11%;" | Advanced+ (A+) \! style="width:11%;" | Advanced (A)
\! style="width:11%;" | Broad
Compatibility (B) \! style="width:11%;" | Widest
Compatibility (C) \! style="width:11%;" | Legacy (C-) |-
style="background-color:\#B9FFC5;"

| style="text-align:left" |
TLS_DHE_RSA_WITH_AES_256_GCM_SHA384,
\[DHE-RSA-AES256-GCM-SHA384\] | | 0x009f | | 1 | | 1 | | 1 | | 1 | | 1
|- style="background-color:\#B9FFC5;" | style="text-align:left" |
TLS_DHE_RSA_WITH_AES_128_GCM_SHA256,
\[DHE-RSA-AES128-GCM-SHA256\] | | 0x009e | | 2 | | 2 | | 2 | | 2 | | 2
|- style="background-color:\#B9FFC5;" | style="text-align:left" |
TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384,
\[ECDHE-RSA-AES256-GCM-SHA384\] | | 0xc030 | | 3 | | 3 | | 3 | | 3 | | 3
|- style="background-color:\#B9FFC5;" | style="text-align:left" |
TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256,
\[ECDHE-RSA-AES128-GCM-SHA256\] | | 0xc02f | | 4 | | 4 | | 4 | | 4 | | 4
|- style="background-color:\#E3FFE3;" | style="text-align:left" |
TLS_DHE_RSA_WITH_AES_256_CBC_SHA256,
\[DHE-RSA-AES256-SHA256\] | | 0x006b | | | | 5 | | 5 | | 5 | | 5 |-
style="background-color:\#E3FFE3;" | style="text-align:left" |
TLS_DHE_RSA_WITH_AES_128_CBC_SHA256,
\[DHE-RSA-AES128-SHA256\] | | 0x0067 | | | | 6 | | 6 | | 6 | | 6 |-
style="background-color:\#E3FFE3;" | style="text-align:left" |
TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA384,
\[ECDHE-RSA-AES256-SHA384\] | | 0xc028 | | | | 7 | | 7 | | 7 | | 7 |-
style="background-color:\#E3FFE3;" | style="text-align:left" |
TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA256,
\[ECDHE-RSA-AES128-SHA256\] | | 0xc027 | | | | 8 | | 8 | | 8 | | 8 |- |
style="text-align:left" | TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA,
\[ECDHE-RSA-AES256-SHA\] | | 0xc014 | | | | | | 9 | | 9 | | 9 |- |
style="text-align:left" | TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA,
\[ECDHE-RSA-AES128-SHA\] | | 0xc013 | | | | | | 10 | | 10 | | 10 |-
style="background-color:\#F4F6F8;" | style="text-align:left" |
TLS_RSA_WITH_AES_256_GCM_SHA384,
\[AES256-GCM-SHA384\] | | 0x009d | | | | | | | | 11 | | 11 |-
style="background-color:\#F4F6F8;" | style="text-align:left" |
TLS_RSA_WITH_AES_128_GCM_SHA256,
\[AES128-GCM-SHA256\] | | 0x009c | | | | | | | | 12 | | 12 |-
style="background-color:\#F4F6F8;" | style="text-align:left" |
TLS_RSA_WITH_AES_256_CBC_SHA256,
\[AES256-SHA256\] | | 0x003d | | | | | | | | 13 | | 13 |-
style="background-color:\#F4F6F8;" | style="text-align:left" |
TLS_RSA_WITH_AES_128_CBC_SHA256,
\[AES128-SHA256\] | | 0x003c | | | | | | | | 14 | | 14 |-
style="background-color:\#F4F6F8;" | style="text-align:left" |
TLS_RSA_WITH_AES_256_CBC_SHA,
\[AES256-SHA\] | | 0x0035 | | | | | | | | 15 | | 15 |-
style="background-color:\#F4F6F8;" | style="text-align:left" |
TLS_RSA_WITH_AES_128_CBC_SHA,
\[AES128-SHA\] | | 0x002f | | | | | | | | 16 | | 16 |-
style="background-color:\#FFFF88;" | style="text-align:left" |
TLS_RSA_WITH_3DES_EDE_CBC_SHA,
\[DES-CBC3-SHA\] | | 0x000a | | | | | | | | | | 17 |- |
style="text-align:left" | TLS_DHE_RSA_WITH_AES_256_CBC_SHA,
\[DHE-RSA-AES256-SHA\] | | 0x0039 | | | | | | 11 | | 17 | | 18 |- |
style="text-align:left" | TLS_DHE_RSA_WITH_AES_128_CBC_SHA,
\[DHE-RSA-AES128-SHA\] | | 0x0033 | | | | | | 12 | | 18 | | 19 |}

::<b>Anmerkungen:</b>
\- Die Nummer gibt die Position der jeweiligen Priorisierung an
\- Da ältere Internet-Explorer- und Java-Versionen <u>keine</u>
Diffie-Hellman-Parameter \>1024 bit unterstützen wurden die Verfahren
'TLS_DHE_RSA_WITH_AES_256_CBC_SHA' und
'TLS_DHE_RSA_WITH_AES_128_CBC_SHA' am Ende angeordnet, um
Inkompatibilitäten mit Altversionen zu vermeiden; Alternative: Diese
Verfahren ganz weglassen.
:\* Beispiel-Cipher-Strings für OpenSSL:

  -

      -
        {| border="1" cellspacing="1" cellpadding="1"
        style="border-collapse:collapse; text-align: left;
        font-size:84%;"

|- style="font-size: 119%; background-color:\#EAECF0;" \!Cipher-String |
| OpennSSL-Syntax |- style="background-color:\#B9FFC5;" |
style="font-size: 119%;" | <b>Advanced+ (A+)</b> | |
DHE-RSA-AES256-GCM-SHA384:DHE-RSA-AES128-GCM-SHA256:ECDHE-RSA-AES256-GCM-SHA384:ECDHE-RSA-AES128-GCM-SHA256
|- style="background-color:\#E3FFE3;" | style="font-size: 119%;" |
<b>Advanced (A)</b> | |
DHE-RSA-AES256-GCM-SHA384:DHE-RSA-AES128-GCM-SHA256:ECDHE-RSA-AES256-GCM-SHA384:ECDHE-RSA-AES128-GCM-SHA256:DHE-RSA-AES256-SHA256:DHE-RSA-AES128-SHA256:ECDHE-RSA-AES256-SHA384:ECDHE-RSA-AES128-SHA256
|- | style="font-size: 119%;" | <b>Broad Compatibility (B)</b> | |
DHE-RSA-AES256-GCM-SHA384:DHE-RSA-AES128-GCM-SHA256:ECDHE-RSA-AES256-GCM-SHA384:ECDHE-RSA-AES128-GCM-SHA256:DHE-RSA-AES256-SHA256:DHE-RSA-AES128-SHA256:ECDHE-RSA-AES256-SHA384:ECDHE-RSA-AES128-SHA256:ECDHE-RSA-AES256-SHA:ECDHE-RSA-AES128-SHA:DHE-RSA-AES256-SHA:DHE-RSA-AES128-SHA
|- style="background-color:\#F4F6F8;" | style="font-size: 119%;" |
<b>Widest Compatibility (C)</b> | |
DHE-RSA-AES256-GCM-SHA384:DHE-RSA-AES128-GCM-SHA256:ECDHE-RSA-AES256-GCM-SHA384:ECDHE-RSA-AES128-GCM-SHA256:DHE-RSA-AES256-SHA256:DHE-RSA-AES128-SHA256:ECDHE-RSA-AES256-SHA384:ECDHE-RSA-AES128-SHA256:ECDHE-RSA-AES256-SHA:ECDHE-RSA-AES128-SHA:AES256-GCM-SHA384:AES128-GCM-SHA256:AES256-SHA256:AES128-SHA256:AES256-SHA:AES128-SHA:DHE-RSA-AES256-SHA:DHE-RSA-AES128-SHA
|- style="background-color:\#FFFF88;" | style="font-size: 119%;" |
<b>Legacy (C-)</b> | |
DHE-RSA-AES256-GCM-SHA384:DHE-RSA-AES128-GCM-SHA256:ECDHE-RSA-AES256-GCM-SHA384:ECDHE-RSA-AES128-GCM-SHA256:DHE-RSA-AES256-SHA256:DHE-RSA-AES128-SHA256:ECDHE-RSA-AES256-SHA384:ECDHE-RSA-AES128-SHA256:ECDHE-RSA-AES256-SHA:ECDHE-RSA-AES128-SHA:AES256-GCM-SHA384:AES128-GCM-SHA256:AES256-SHA256:AES128-SHA256:AES256-SHA:AES128-SHA:DES-CBC3-SHA:DHE-RSA-AES256-SHA:DHE-RSA-AES128-SHA
|}

  - TLS/SSL-Konfiguration des Webservers härten:

:\* nur sichere Server-initiierte Renegotiation

:\* <u>keine</u> Komprimierung

:\* Einstellungen aller virtuellen Server (virtualHosts) prüfen

:\* Bei Einsatz von Server Name Indication (SNI), prüfen, welcher Server
der Default-Server ist. Alte Browser bzw. Betriebssysteme, ohne
SNI-Unterstützung erreichen nur diesen\!

:\* Prüfen der, von der installierten OpenSSL-Version unterstützten
Cipher

:\* Reduktion der SSL-Extensions auf das notwendige Maß, z.B.
Deaktivieren von Heart-Beat (vgl [Heartbleed](http://heartbleed.com)),
kein Aktivieren von unsicheren Extension-DRAFTS wie z.B. Additional
random, Opaque PRF Input (vgl.
[DualECTLS](http://dualec.org/DualECTLS.pdf))

  - Konfigurations-Beispiel für Apache inkl. Cipher String 'A':

SSLProtocol +TLSv1.2                  \# for Cipher-String 'A+', 'A'
\#SSLProtocol +TLSv1.2 +TLSv1.1 +TLSv1 \# for Cipher-String 'B', 'C',
'C-'
SSLCompression off
SSLHonorCipherOrder on
SSLCipherSuite
'DHE-RSA-AES256-GCM-SHA384:DHE-RSA-AES128-GCM-SHA256:ECDHE-RSA-AES256-GCM-SHA384:ECDHE-RSA-AES128-GCM-SHA256:DHE-RSA-AES256-SHA256:DHE-RSA-AES128-SHA256:ECDHE-RSA-AES256-SHA384:ECDHE-RSA-AES128-SHA256'
\#optional kann
':\!aNULL:\!eNULL:\!LOW:\!3DES:\!MD5:\!EXP:\!PSK:\!DSS:\!RC4:\!SEED:\!ECDSA:\!ADH:\!IDEA'
ergänzt werden.  <b>Anmerkungen:</b> - Der Cipher-String mit den
SSL-Cipher-Suites wurde als Whitelist formuliert, um die serverseitige
Kompatibilität mit alten Versionen von OpenSSL zu erhöhen.
\- Überwachen Sie die Performance Ihres Servers, der Verbindungsaufbau
mit DHE ist ca. 2,4 Mal CPU-intensiver als mit ECDHE (vgl [\[Vincent
Bernat, 2011\]](http://vincent.bernat.im/en/blog/2011-ssl-perfect-forward-secrecy.html#some-benchmarks),
[\[nmav's
Blog, 2011\]](http://nmav.gnutls.org/2011/12/price-to-pay-for-perfect-forward.html))

  - Prüfen der Cipher-Einstellungen mittels openssl, z.B. Cipher-String
    'A':

openssl ciphers -V
"DHE-RSA-AES256-GCM-SHA384:DHE-RSA-AES128-GCM-SHA256:ECDHE-RSA-AES256-GCM-SHA384:ECDHE-RSA-AES128-GCM-SHA256:DHE-RSA-AES256-SHA256:DHE-RSA-AES128-SHA256:ECDHE-RSA-AES256-SHA384:ECDHE-RSA-AES128-SHA256"
\#add optionally
':\!aNULL:\!eNULL:\!LOW:\!MD5:\!EXP:\!PSK:\!DSS:\!RC4:\!SEED:\!ECDSA:\!ADH:\!IDEA'
to protect older Versions of OpenSSL
\#use openssl ciphers -v "..." for openssl \< 1.0.1: <small>

`0x00,0x9F - DHE-RSA-AES256-GCM-SHA384   TLSv1.2 Kx=DH     Au=RSA  Enc=AESGCM(256) Mac=AEAD`
`0x00,0x9E - DHE-RSA-AES128-GCM-SHA256   TLSv1.2 Kx=DH     Au=RSA  Enc=AESGCM(128) Mac=AEAD`
`0xC0,0x30 - ECDHE-RSA-AES256-GCM-SHA384 TLSv1.2 Kx=ECDH   Au=RSA  Enc=AESGCM(256) Mac=AEAD`
`0xC0,0x2F - ECDHE-RSA-AES128-GCM-SHA256 TLSv1.2 Kx=ECDH   Au=RSA  Enc=AESGCM(128) Mac=AEAD`
`0x00,0x6B - DHE-RSA-AES256-SHA256       TLSv1.2 Kx=DH     Au=RSA  Enc=AES(256)    Mac=SHA256`
`0x00,0x67 - DHE-RSA-AES128-SHA256       TLSv1.2 Kx=DH     Au=RSA  Enc=AES(128)    Mac=SHA256`
`0xC0,0x28 - ECDHE-RSA-AES256-SHA384     TLSv1.2 Kx=ECDH   Au=RSA  Enc=AES(256)    Mac=SHA384`
`0xC0,0x27 - ECDHE-RSA-AES128-SHA256     TLSv1.2 Kx=ECDH   Au=RSA  Enc=AES(128)    Mac=SHA256`

</small>  <b>Achtung/CAUTION</b>: Der Cipher-String wurde nur mit
einzelnen, älteren OpenSSL-Versionen getestet, es können ungewollt
weitere Cipher-Suiten dadurch benutzt werden. (ONLY tested with some
elder Versions of OpenSSL\!)


<b>sichere Zertifikate</b>
\* Nutzen Sie eine vertrauenswürdige Zertifizierungsstelle (CA) für
öffentlich erreichbare, verschlüsselte Webserver; Prüfen Sie die
Vergabe-Politik der CA.

  - zeitgemäße, starke Verfahren mit sicheren Schlüssellängen (vgl. [BSI
    TR-02102-2
    Teil 2](https://www.bsi.bund.de/DE/Publikationen/TechnischeRichtlinien/tr02102/index_htm.html):
    2000 bits bzw. (nach 2015:) 3000 bits für RSA), auch für alle
    Zwischenzertifikate und das Root-Zertifikat der CA.
  - Angabe der 'Fully Qualified Names' und bei 'www' auch des
    Domänennamens im Zertifikat, damit ein Redirekt möglich ist (z.B.
    von 'https://example.com' zu 'https://www.example.com').
  - Dedizierte Zuertifikate, je Server; <u>keine</u> 'Sammelzertifikate'
    (Wildcard-Zertifikate, z.B.
    <span style="color:red;">\*.example.com</span>)
  - Überwachung der Gültigkeit der Zertifikate
  - IP-Adressen in Zertifikaten <u>vermeiden</u>, <u>keine</u>
    [RFC 1918](https://tools.ietf.org/html/rfc1918)-Adressen (z.B.
    <span style="color:red;">192.168.1.1</span>)
  - stellen Sie die, zum Verifizieren benötigte Zertifikats-Kette auf
    dem Webserver zur Verfügung (auch die Zwischenzertifikate)
  - Nutzen Sie Ihre Zeritifikate nur für Dienste mit einem
    vergleichbaren Sicherheitsniveau (vermeiden Sie z.B. das Zertifikat
    eines Webservers auch für Email-Dienste zu nutzen)


<b>Testen der Einstellungen und des Zertifikats:</b>

  - [OWASP Testing Guide: Chapter on SSL/TLS
    Testing](Testing_for_SSL-TLS_%28OWASP-CM-001%29 "wikilink")
  - [OWASP 'O-Saft' (OWASP SSL audit for testers / OWASP SSL advanced
    forensic tool)](O-Saft "wikilink")
  - [SSL LABS Server Test](https://www.ssllabs.com/ssltest)
  - weitere Tools: [Testing for Weak SSL/TLS Ciphers, Insufficient
    Transport Layer Protection
    (OTG-CRYPST-001)-Tools](Testing_for_Weak_SSL/TLS_Ciphers,_Insufficient_Transport_Layer_Protection_\(OTG-CRYPST-001\)#Tools "wikilink")


Weitere Details im [Transport Layer Protection Cheat
Sheet](Transport_Layer_Protection_Cheat_Sheet "wikilink") und [OWASP
Testing Guide: Chapter on SSL/TLS
Testing](Testing_for_SSL-TLS "wikilink").
Links mit Beispielen für viele Plattformen:

  - [bettercrypto.org:](https://bettercrypto.org) ['Applied Crypto
    Hardening
    (DRAFT)'](https://bettercrypto.org/static/applied-crypto-hardening.pdf)
  - [MozillaWiki: Security/Server Side
    TLS](https://wiki.mozilla.org/Security/Server_Side_TLS)

<!-- end list -->

  - Absicherung der Transportschicht (auf dem Webserver - Teil 2)

<b>Wirksamer Schutz gegen Man In The Middle-Angriffe</b>
Die Sicherheitskonfiguration unter Option 2a hat noch eine
Schwachstelle, so das MITM (Man In The Middle attack) nicht zuverlässig
verhindert wird. MITM erzeugt einen Zertifikatsfehler am Client, der
üblicherweise aber (durch den Anwender) ignoriert wird. Deshalb wurde
der HTTP-Header "HTTP Strict Transport Security (HSTS)" eingeführt.
Damit werden kompatible Browser (Firefox, Chrome, Opera aber bisher
NICHT IE) angewiesen, dass

  - der Browser den http-Request ausschließlich über https verschickt
    (auch falls die Seite mit http aufgerufen wird).
  - der Anwender Zertifikatsfehler im Browser nicht mehr ignorieren
    kann.


Konfiguration im Apache:  Header set Strict-Transport-Security

  -
    "max-age=16070400; includeSubDomains"


Da der HSTS-Header nur über https übermittelt wird ist zusätzlich ein
Redirect nötig:

  -
    \<VirtualHost \*:80\>
      -
        ServerAlias \*
        RewriteEngine On
        RewriteRule ^(.\*)$ https://%{HTTP_HOST}$1 \[redirect=301\]
    </VirtualHost>


;Quellen:

[HTTP Strict Transport
Security](HTTP_Strict_Transport_Security "wikilink")
[AppSecTutorial Series -
Episode 4](http://www.youtube.com/watch?v=zEV3HOuM_Vw&feature=youtube_gdata)

  - Einen umfangreicheren Überblick über die Anforderungen, gibt es
    unter [ASVS requirements on Cryptography (V7), Data Protection (V9)
    und Communications Security (V10)](ASVS "wikilink").
  - [OWASP Cryptographic Storage Cheat
    Sheet](Cryptographic_Storage_Cheat_Sheet "wikilink")
  - [OWASP Password Storage Cheat
    Sheet](Password_Storage_Cheat_Sheet "wikilink")
  - [OWASP Transport Layer Protection Cheat
    Sheet](Transport_Layer_Protection_Cheat_Sheet "wikilink")
  - [OWASP Testing Guide: Chapter on SSL/TLS
    Testing](Testing_for_SSL-TLS "wikilink")
  - [OWASP SSL Advanced Forensic Tool (O-SAFT)](O-Saft "wikilink")

<!-- end list -->

  -
    Älter:

<!-- end list -->

  - [OWASP Top 10-2007 on Insecure Cryptographic
    Storage](Top_10_2007-Insecure_Cryptographic_Storage "wikilink")
  - [OWASP Development Guide: Chapter on
    Cryptography](Guide_to_Cryptography#Insecure_transmission_of_secrets "wikilink")
  - [OWASP Code Review Guide: Chapter on
    Cryptography](Codereview-Cryptography "wikilink")

<!-- end list -->

  - [CWE Entry 310 on Cryptographic
    Issues](http://cwe.mitre.org/data/definitions/310.html)
  - [CWE Entry 312 on Cleartext Storage of Sensitive
    Information](http://cwe.mitre.org/data/definitions/312.html)
  - [CWE Entry 319 on Cleartext Transmission of Sensitive
    Information](http://cwe.mitre.org/data/definitions/319.html)
  - [CWE Entry 326 on Weak
    Encryption](http://cwe.mitre.org/data/definitions/326.html)
  - [Reine Java Implementierung von
    BCrypt](http://www.mindrot.org/projects/jBCrypt)
  - [Beispielimplementierung von SCrypt](https://github.com/wg/scrypt)
  - [SSL LABS: 'SSL/TLS Deployment Best
    Practices'](https://www.ssllabs.com/projects/best-practices/index.html)
  - [BSI: 'TR-02102-2
    Teil 2'](https://www.bsi.bund.de/DE/Publikationen/TechnischeRichtlinien/tr02102/index_htm.html)
  - [ENISA: 'Study on cryptographic
    protocols'](https://www.enisa.europa.eu/activities/identity-and-trust/library/deliverables/study-on-cryptographic-protocols)
  - [bettercrypto.org:](https://bettercrypto.org) ['Applied Crypto
    Hardening
    (DRAFT)'](https://bettercrypto.org/static/applied-crypto-hardening.pdf)
  - [MozillaWiki: Security/Server Side
    TLS](https://wiki.mozilla.org/Security/Server_Side_TLS)

# **PHP**

Um vorerstellte Hash-Tabellen zu verhindern, kann jedem Datensatz eine
zufällige Zeichenfolge hinzugefügt werden, welche als Salt (Deutsch:
Salz) bezeichnet wird. Ein Beispiel für die sichere Erstellung eines
Hashwerts ist im Folgendemn gegeben. Dafür muss das GIT-Projekt
[4](https://github.com/ircmaxell/password_compat) eingebunden werden, ab
PHP-Version 5.5 ist dies im Kern enthalten. Das Salt wird bspw. bei
einem Linuxsystem in der Funktion password_hash() durch Zugriff auf
/dev/urandom erstellt. Der Rückgabewert der Funktion ist eine
Zeichenkette und beinhaltet u.a. den Hashwert, das Salt und den
genutzten Algorithmus. Die Kosten, welche die Anzahl der
Hash-Iterationen angeben, können über den dritten Parameter festgelegt
werden.  $options = \[

  -
    'cost' =\> 12,

\];
$inputHash = password_hash($_GET\['password'\], CRYPT_SHA256,
$options);
storeHash($user, $inputHash); // Speichere Hash
$hash = getHash($user); // Hole Hash aus der Datenbank
// Prüfe eingegebenes Passwort gegen gespeichertes Passwort:
$isPasswordVerified = password_verify($_GET\['password'\], $hash);
if($isPasswordVerified) {

  -
    // Password korrekt

} else {

  -
    throw new PasswordVerificationException("");

}

  - Einen umfangreicheren Überblick über die Anforderungen, gibt es
    unter [ASVS requirements on Cryptography (V7), Data Protection (V9)
    und Communications Security (V10)](ASVS "wikilink").
  - [OWASP Cryptographic Storage Cheat
    Sheet](Cryptographic_Storage_Cheat_Sheet "wikilink")
  - [OWASP Password Storage Cheat
    Sheet](Password_Storage_Cheat_Sheet "wikilink")
  - [OWASP Transport Layer Protection Cheat
    Sheet](Transport_Layer_Protection_Cheat_Sheet "wikilink")
  - [OWASP Testing Guide: Chapter on SSL/TLS
    Testing](Testing_for_SSL-TLS "wikilink")
  - [OWASP SSL Advanced Forensic Tool (O-SAFT)](O-Saft "wikilink")

<!-- end list -->

  -
    Älter:

<!-- end list -->

  - [OWASP Top 10-2007 on Insecure Cryptographic
    Storage](Top_10_2007-Insecure_Cryptographic_Storage "wikilink")
  - [OWASP Development Guide: Chapter on
    Cryptography](Guide_to_Cryptography#Insecure_transmission_of_secrets "wikilink")
  - [OWASP Code Review Guide: Chapter on
    Cryptography](Codereview-Cryptography "wikilink")

<!-- end list -->

  - [CWE Entry 310 on Cryptographic
    Issues](http://cwe.mitre.org/data/definitions/310.html)
  - [CWE Entry 312 on Cleartext Storage of Sensitive
    Information](http://cwe.mitre.org/data/definitions/312.html)
  - [CWE Entry 319 on Cleartext Transmission of Sensitive
    Information](http://cwe.mitre.org/data/definitions/319.html)
  - [CWE Entry 326 on Weak
    Encryption](http://cwe.mitre.org/data/definitions/326.html)
  - [Funktionsweise der Funktion
    password_hash](http://www.php.net/manual/en/function.password-hash.php)
  - [SSL LABS: 'SSL/TLS Deployment Best
    Practices'](https://www.ssllabs.com/projects/best-practices/index.html)
  - [BSI: 'TR-02102-2
    Teil 2'](https://www.bsi.bund.de/DE/Publikationen/TechnischeRichtlinien/tr02102/index_htm.html)
  - [ENISA: 'Study on cryptographic
    protocols'](https://www.enisa.europa.eu/activities/identity-and-trust/library/deliverables/study-on-cryptographic-protocols)
  - [bettercrypto.org:](https://bettercrypto.org) ['Applied Crypto
    Hardening
    (DRAFT)'](https://bettercrypto.org/static/applied-crypto-hardening.pdf)
  - [MozillaWiki: Security/Server Side
    TLS](https://wiki.mozilla.org/Security/Server_Side_TLS)

\-- weitere Programmiersprachen oder evtl Anti-Beispiele --- \>

# **Test**

tbd
Text

tbd
Text

tbd
Text

(ganze Breite)
Text

\------------------------------------------------\> <headertabs />