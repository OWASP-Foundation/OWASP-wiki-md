-----

| Bedro-   :   Angriffs-
hungs-  vektoren
quellen | Schwachstelle | Auswirkungen | | Anwendungsspezifisch :
Exploitability 3 | Prevalence 2 : Detectability 3 | Technical 3 :
Geschäftlich ? | ------------------\>

`   <td colspan=2 ``>`

Beinahe jede Datenquelle kann einen Vektor für Injection darstellen:
Umge-bungsvariablen, Parameter, externe und interne Webservices können
von jedem Nutzer, unabhängig von seiner jeweiligen Rolle, ausgenutzt
werden.
<u>[Injection flaws](Injection_Flaws "wikilink")</u>
Injection-Schwachstellen treten dann auf, wenn ein Angreifer bösartige
Daten an einen Interpreter zur Verarbeitung schicken kann.

</td>

`   <td colspan=2  ``>`

Injection Schwachstellen sind weit verbreitet, insbe-sondere in altem,
ungewarteten Legacy-Code. Oft findet man sie in SQL-, NoSQL-, ORM-,
LDAP- oder Xpath-Querys, ebenso bei Betriebssystem-Kommandos („OS
Command Injection“), in XML- Parsern, SMTP-Headern und Expression
Languages.
Injection-Schwachstellen sind durch das Prüfen des Quellcodes leicht zu
finden. Schwachstellen-Scanner und Fuzzer können Angreifer beim
Auffinden von Injection-Schwachstellen unterstützen.

</td>

`   <td colspan=2  ``>`

`Injection kann zu Datenverlust, -verfälschung, oder Offenlegung gegenüber unauthorisierten Dritten, Verlust der Zurechenbarkeit oder Zugangssperre führen. Unter Umständen kann es zu einer vollständigen Systemübernahme kommen. Die Auswirkungen auf das Unternehmen hängen vom Schutzbedarf der Anwendung und ihrer Daten ab. `

</td>

Eine Anwendung ist für diesen Angriff verwundbar, wenn:

  - Daten, die vom Nutzer stammen, nicht ausreichend validiert,
    gefiltert oder durch geeignete Sanitizer-Funktionen laufen.
  - Dynamische Anfragen oder nicht-parametrisierte Aufrufe ohne ein dem
    Kontext (SQL, LDAP, XML usw.) entsprechendes Escaping direkt einem
    Interpreter übergeben werden.
  - Bösartige Daten innerhalb von ORM („Objekt Relationales
    Mapping“)-Suchparametern genutzt werden können, um vertrauliche
    Datensätze eines Dritten zu extrahieren.
  - Bösartige Daten direkt oder als Teil zusammengesetzter dynamischer
    SQL-Querys, Befehle oder Stored Procedures genutzt werden können.

Injection ist u.a. bei der Verwendung von SQL, NoSQL, ORM-Frameworks,
Betriebssystem-Kommandos, LDAP, Expression Language (EL) , Object Graph
Navigation Language (OGNL) oder XML zu finden. Das Grundkonzept eines
Injection-Angriffs ist für alle Interpreter gleich. Ein Quellcode Review
ist eine sehr gute Methode, um Injection-Schwachstellen zu finden, dicht
gefolgt vom gründlichen (ggf. automatisierten) Testen aller Parameter
und Variablen wie z.B. Eingabe-Felder und Header-, URL-, Cookies-,
JSON-, SOAP- und XML-Eingaben. Statische
(<u>[SAST](Source_Code_Analysis_Tools "wikilink")</u>, Quellcode-Ebene)
und dynamische
(<u>[DAST](:Category:Vulnerability_Scanning_Tools "wikilink")</u>,
laufende Anwendung) Test-Werkzeuge können von Organisationen für ihre
CI/CD-Pipeline genutzt werden, um neue Schwachstellen noch vor einer
möglichen Produktivnahme aufzuspüren.

Um Injection zu verhindern, müssen Eingabedaten und Kommandos (bzw.
Querys) konsequent getrennt bleiben.

  - Die besten Methoden dafür sind entweder eine sichere API, die die
    direkte Interpreter-Nutzung vollständig vermeidet, bzw. die eine
    parametrisierte, typgebundene Schnittstelle anbietet oder die
    korrekte Verwendung eines ORM-Frameworks.
    <b>Anmerkung:</b> Stored Procedures können - auch parametrisiert -
    immer noch SQL-Injection ermöglichen, wenn PL/SQL oder T-SQL
    Anfragen und Eingabedaten konkateniert oder mit EXECUTE IMMEDIATE
    oder exec() ausgeführt werden.
  - Für die serverseitige Eingabe-Validierung empfiehlt sich die Nutzung
    eines Positivlisten(“Whitelist”)-Ansatzes. Dies ist i.A. kein
    vollständiger Schutz, da viele Anwendungen Sonder- und Meta-Zeichen
    z.B. für Textfelder oder Mobile Apps benötigen.
  - Für jede noch verbliebene dynamische Query müssen Sonder- und
    Meta-Zeichen für den jeweiligen Interpreter mit der richtigen
    Escape-Syntax entschärft werden.
    <b>Anmerkung:</b> Ein Escaping von SQL-Bezeichnern, wie z.B. die
    Namen von Tabellen oder Spalten usw. ist nicht möglich.
    Falls Nutzer solche Bezeichner selbst eingeben können, so ist dies
    durchaus gefährlich. Dies ist eine übliche Schwachstelle bei
    Software, die Reports aus einer Datenbank erstellt.
  - Querys sollten LIMIT oder andere SQL-Controls verwenden, um den
    möglichen Massen-Abfluss von Daten zu verhindern.

<b>Szenario 1:</b> Eine Anwendung nutzt ungeprüfte Eingabedaten für den
Zusammenbau der folgenden verwundbaren SQL-Abfrage:
<b><span style="color:red;"> String query = "SELECT \* FROM accounts
WHERE custID='" + request.getParameter("id") + "'"; </span></b>

<b>Szenario 2:</b> Auch das blinde Vertrauen in Frameworks kann zu
Querys führen, die ganz analog zu obigem Beispiel verwundbar sind (z.B.
Hibernate Query Language (HQL)):
<b><span style="color:red;"> Query HQLQuery = session.createQuery("FROM
accounts WHERE custID='" + request.getParameter("id") + "'");'''
</span></b> In beiden Fällen kann ein Angreifer den ‘id’-Parameter in
seinem Browser ändern und sendet: <b>' or '1'='1</b>. Zum Beispiel so:
<b><span style="color:red;"> http://example.com/app/accountView?id=' or
'1'='1 </span></b>

Hierdurch wird die Logik der Anfrage verändert, so dass alle Datensätze
der Tabelle „accounts“ ohne Einschränkung auf einen Kunden zurückgegeben
werden.
Gefährlichere Attacken wären z.B. das Ändern oder Löschen von Daten oder
das Aufrufen von Stored Procedures.

  - <u>[OWASP Proactive Controls: Parameterize
    Queries](OWASP_Proactive_Controls#2:_Parameterize_Queries "wikilink")</u>
  - <u>[OWASP ASVS: V5 Input Validation and
    Encoding](:Category:OWASP_Application_Security_Verification_Standard_Project "wikilink")</u>
  - <u>[OWASP Testing Guide: SQL
    Injection](Testing_for_SQL_Injection_\(OTG-INPVAL-005\) "wikilink")</u>,
    <u>[Command
    Injection](Testing_for_Command_Injection_\(OTG-INPVAL-013\) "wikilink")</u>,
    <u>[ORM
    injection](Testing_for_ORM_Injection_\(OTG-INPVAL-007\) "wikilink")</u>
  - <u>[OWASP Cheat Sheet: Injection
    Prevention](Injection_Prevention_Cheat_Sheet "wikilink")</u>
  - <u>[OWASP Cheat Sheet: SQL Injection
    Prevention](SQL_Injection_Prevention_Cheat_Sheet "wikilink")</u>
  - <u>[OWASP Cheat Sheet: Injection Prevention in
    Java](Injection_Prevention_Cheat_Sheet_in_Java "wikilink")</u>
  - <u>[OWASP Cheat Sheet: Query
    Parameterization](Query_Parameterization_Cheat_Sheet "wikilink")</u>
  - <u>[OWASP Automated Threats to Web Applications –
    OAT-014](OWASP_Automated_Threats_to_Web_Applications "wikilink")</u>

<!-- end list -->

  - <u>[CWE-77: Command
    Injection](https://cwe.mitre.org/data/definitions/77.html)</u>
  - <u>[CWE-89: SQL
    Injection](https://cwe.mitre.org/data/definitions/89.html)</u>
  - <u>[CWE-564: Hibernate
    Injection](https://cwe.mitre.org/data/definitions/564.html)</u>
  - <u>[CWE-917: Expression Language
    Injection](https://cwe.mitre.org/data/definitions/917.html)</u>
  - <u>[PortSwigger: Server-side template
    injection](https://portswigger.net/kb/issues/00101080_serversidetemplateinjection)</u>