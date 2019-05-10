`   <td colspan=2 ``>`

Angreifer haben Zugriff auf Millionen gültiger Benutzerdatensätze um
diese als Prüfgrundlage zu nutzen, Listen mit administrativen
Standard-zugängen, Werkzeuge zum Durchführen von Bruteforce- und
Wörterbuch-Angriffen. Angriffe auf die Authentifizierung sind gut
erforscht, insbesondere in Bezug auf nicht erloschene Session-Token.

</td>

`   <td colspan=2  ``>`

`Aufgrund des Designs und der Implementierung von Identitäts- und Zugriffsprüfungen sind Fehler in der Authentifizierung weit verbreitet. Sitzungsverwaltung („Session Management“) ist die Grundlage zur Prüfung von Authentisierung und Zugriffsberechtigung und in zustandsbehafteten Anwendungen vorhanden.`
`Angreifer können fehlerhafte Authentifizierung mit manuellen Methoden erkennen und mithilfe automatisierter Tools mit Passwortlisten und Wörterbuchangriffen ausnutzen. `

</td>

`   <td colspan=2  ``>`

`Um ein System zu kompromittieren, genügt es einem Angreifer, nur wenige Zugänge oder den einen administrativen Zugang zu erlangen. Abhängig vom Zweck der Anwendung ermöglicht ihm das z. B. Geldwäsche, Sozialbetrug, Identitätsdiebstahl oder die Veröffentlichung hochsensibler Informationen. `

</td>

Um eine Anwendung gegen Angriffe auf die Authentisierung zu schützen,
müssen die Nutzeridentität, Anmeldung und die Sitzungsverwaltung
überprüft werden. Folgende Fehler in der Authentisierung können
vorhanden sein:

  - Automatisierte Angriffe wie "<u>[Credential
    Stuffing](Credential_stuffing "wikilink")</u>" werden ermöglicht.
  - Bruteforce oder andere automatisierte Angriffe sind möglich.
  - Schwache oder bekannte Passwörter wie "Passwort\!" oder
    "admin/admin" sind erlaubt, Standardpasswörter unverändert.
  - Funktionen um Zugangsdaten oder Passwörter wiederherzustellen sind
    schwach, wie z. B. "wissensbasierte Antworten", die nicht sicher
    sein können.
  - Speicherung von Passwörtern im Klartext, verschlüsselt oder mit
    schwachen Hashes (vgl.
    <u><b>[text=documentRootTop10New]({{Top_10:LanguageFile "wikilink")</b></u>).
  - Keine oder nicht wirksame Mehrfaktor-Authentisierung
  - Die Sitzungs-ID wird im URL exponiert (z. B. URL rewriting)
  - Kein Wechsel der Sitzungs-ID nach einer erfolgreichen Anmeldung.
  - Sitzungs-IDs werden nicht korrekt ungültig gemacht, d.h.
    Benutzersitzungen oder Authentisierungs-Token (wie z.B.
    Single-Sign-On (SSO)-Token) werden nach einer Abmeldung, nach einer
    festen Zeit oder bei Nicht-Aktivität nicht explizit ungültig
    gemacht.

<!-- end list -->

  - Sofern es möglich ist, implementieren Sie
    Mehrfaktor-Authentisierung, um automatisierte Angriffe zu
    verhindern.

Im Auslieferungszustand sollten keine Standardbenutzer angelegt sein.
Dies gilt besonders für administrative Benutzer.

  - Es sollten Prüfungen zum Verhindern schwacher Passwörter
    implementiert sein. So können Passwörtern gegen eine Liste
    <u>[der 10000 beliebtesten
    Passwörter](https://github.com/danielmiessler/SecLists/tree/master/Passwords)</u>.
    geprüft werden.
  - Die Prüfung der Länge, Komplexität und Häufigkeit des
    Passwortwechsels sollte sich an den Vorgaben der
    <u>[NIST 800-63](https://pages.nist.gov/800-63-3/sp800-63b.html#memsecret)</u>
    o. anderen Vorgaben mit nachweisbarer Sicherheit orientieren.
  - Funktionen zur Benutzerregistrierung, Wiederherstellung von
    Zugangsdaten und API Zugängen sollten gegen das automatische
    Durchsuchen nach gültigen Benutzernamen geschützt sein, in dem bei
    allen fehlerhaften Anmeldeversuchen dieselbe Fehlermeldung
    ausgegeben wird.
  - Begrenzen Sie die Gesamtanzahl der Anmeldeversuche oder setzen Sie
    Verzögerungen ein. Fehlerhafte Anmeldungen müssen protokolliert und
    Administratoren informiert werden, wenn Anomalien oder Angriffe
    erkannt werden.
  - Es sollten serverseitige, sichere und etablierte Sitzungsmanager
    verwendet werden, die eine zufällig vergebene Sitzungs-ID mit hoher
    Entropie verwenden. Sitzungs-IDs sollten nicht in der URL stehen,
    sicher gespeichert und nach Abmeldung, Inaktivität oder einer
    gewissen Zeitenspanne entwertet werden.

<b>Szenario 1:</b> <u>[Credential
Stuffing](Credential_stuffing "wikilink")</u> oder die Verwendung
<u>[von Passwortlisten](https://github.com/danielmiessler/SecLists)</u>
sind übliche Angriffe. Sofern eine Anwendung keine automatisierte
Erkennung von „Credential Stuffing“ implementiert, können gültige
Benutzerdaten durchprobiert und auf Gültigkeit geprüft werden.

<b>Szenario 2:</b> Die meisten Angriffe sind erfolgreich, weil weiterhin
auf passwortbasierte Verfahren als einzigen Faktor gesetzt wird. Ehemals
als Best-Practice anerkannte Verfahren wie Passwortwechsel und
Komplexitätsanforderungen führen nur dazu, dass Benutzer Passwörter
wiederverwenden und schwache Passwörter vergeben. Organisationen sind
aufgefordert, diese Vorgehensweise entsprechend NIST 800-53 zu
verhindern und Mehrfaktor-Authentisierung zu benutzen.

<b>Szenario 3:</b> Die automatische Abmeldung bei Inaktivität ist nicht
korrekt implementiert. Ein Nutzer verwendet einen öffentlichen Computer,
um auf die Anwendung zuzugreifen. Anstatt die Abmeldefunktion zu nutzen,
schließt der Benutzer lediglich den Browsertab. Eine Stunde später nutzt
ein Angreifer denselben Browser und stellt fest, dass der Nutzer immer
noch angemeldet ist.

  - <u>[OWASP Proactive Controls: Implement Identity and Authentication
    Controls](OWASP_Proactive_Controls#5:_Implement_Identity_and_Authentication_Controls "wikilink")</u>
  - <u>[OWASP Application Security Verification Standard: V2
    Authentication](:Category:OWASP_Application_Security_Verification_Standard_Project "wikilink")</u>
  - <u>[OWASP Application Security Verification Standard: V3 Session
    Management](:Category:OWASP_Application_Security_Verification_Standard_Project "wikilink")</u>
  - <u>[OWASP Testing Guide:
    Identity](Testing_Identity_Management "wikilink")</u>,
    <u>[Authentication](Testing_for_authentication "wikilink")</u>
  - <u>[OWASP Cheat Sheet:
    Authentication](Authentication_Cheat_Sheet "wikilink")</u>
  - <u>[OWASP Cheat Sheet: Credential
    Stuffing](Credential_Stuffing_Prevention_Cheat_Sheet "wikilink")</u>
  - <u>[OWASP Cheat Sheet: Forgot
    Password](Forgot_Password_Cheat_Sheet "wikilink")</u>
  - <u>[OWASP Cheat Sheet: Session
    Management](Session_Management_Cheat_Sheet "wikilink")</u>
  - <u>[OWASP Automated Threats
    Handbook](OWASP_Automated_Threats_to_Web_Applications "wikilink")</u>

<!-- end list -->

  - <u>[NIST 800-63b: 5.1.1 Memorized
    Secrets](https://pages.nist.gov/800-63-3/sp800-63b.html#memsecret)</u>
  - <u>[CWE-287: Improper
    Authentication](https://cwe.mitre.org/data/definitions/287.html)</u>
  - <u>[CWE-384: Session
    Fixation](https://cwe.mitre.org/data/definitions/384.html)</u>