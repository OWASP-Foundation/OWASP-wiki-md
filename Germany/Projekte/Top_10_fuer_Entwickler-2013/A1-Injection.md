` `

`    <td ``>Jeder, der Daten, die nicht ausreichend geprüft werden, an das System übermitteln kann: externe und interne Nutzer sowie Administratoren.`

</td>

`    <td ``>Der Angreifer sendet einfache text-basierte Angriffe, die die Syntax des Zielinterpreters missbrauchen. Fast jede Datenquelle kann einen Injection-Vektor darstellen, einschließlich interner Quellen.`

</td>

`    <td colspan=2  ``>`[`Injection-Schwachstellen`](Injection_Flaws "wikilink")` `

tauchen auf, wenn eine Anwendung nicht vertrauenswürdige Daten an einen
Interpreter weiterleitet. Sie sind weit verbreitet, besonders in
veraltetem Code. Sie finden sich in SQL-, LDAP-, XPath und
NoSQL-Anfragen, in Betriebssystembefehlen sowie in XML, SMTP-Headern,
Parametern, etc. Injection-Schwachstellen lassen sich durch
Code-Prüfungen einfach, durch externe Tests aber in der Regel nur
schwer entdecken. Angreifer setzen dazu Scanner und Fuzzer ein.

</td>

`    <td ``>Injection kann zu Datenverlust oder -verfälschung, Fehlen von Zurechenbarkeit oder Zugangssperre führen. Unter Umständen kann es zu einer vollständigen Systemübernahme kommen.`

</td>

`    <td ``>`

Der Wert betroffener Daten für das Unternehmen sowie die
Laufzeitumgebung des Interpreters sind zu berücksichtigen. Daten können
entwendet, verändert, gelöscht werden. Kann ein Image-Schaden entstehen?

</td>

**Szenario 1:** Die Anwendung nutzt ungeprüfte Eingabedaten bei der
Konstruktion der <span style="color:red;">**verwundbaren**</span>
SQL-Abfrage: <span style="color:red;">String query = "SELECT \* FROM
accounts WHERE custID='" + **request.getParameter("id")** +"'";</span>

**Szenario 2:** Blindes Vertrauen in den Einsatz eines Frameworks (hier
z.B. Hibernate Query Language (HQL)): <span style="color:red;">Query
unsafeHQLQuery = session.createQuery("from accounts where
custID='"+**request.getParameter("id")**+"'");</span> Der Angreifer
verändert in beiden Fällen den 'id'-Parameter im Browser und sendet:
<span style="color:red;"><b>' or '1'='1</b></span>. Zum Beispiel: Der
Angreifer verändert den 'id'-Parameter im Browser und übermittelt:
<span style="color:red;"><b>' or '1'='1</b></span>.
http://example.com/app/accountView?id=<b><span style="color: red;">' or
'1'='1</span></b> Das ändert die Logik der Anfrage so, dass in diesem
Fall alle Datensätze der Tabelle 'accounts' zurückgegeben werden.
Schlimmstenfalls werden durch Injections Daten verändert oder sogar
Stored Procedures gestartet.  Das Verhindern von Injection erfordert die
konsequente Trennung von Eingabedaten und Befehlen.

1.  Der bevorzugte Ansatz ist die Nutzung einer sicheren API, die den
    Aufruf von Interpretern vermeidet oder eine typ-gebundene
    Schnittstelle bereitstellt. Seien Sie vorsichtig bei APIs, z. B.
    Stored Procedures, die trotz Parametrisierung anfällig für Injection
    sein können.
2.  Wenn eine typsichere API nicht verfügbar ist, sollten Sie
    Metazeichen unter Berücksichtigung der jeweiligen Syntax sorgfältig
    entschärfen. [OWASP's ESAPI](ESAPI "wikilink") stellt hierfür viele
    [spezielle
    Routinen](http://owasp-esapi-java.googlecode.com/svn/trunk_doc/latest/org/owasp/esapi/Encoder.html)
    bereit.
3.  Auch die Eingabeprüfung gegen Positivlisten ("white list") wird
    empfohlen, ist aber kein vollständiger Schutz, da viele Anwendungen
    Metazeichen in den Eingaben erfordern. Ist der Einsatz von
    Sonderzeichen notwendig, können diese nur unter Beachtung von Punkt
    1 und 2 (s.o.) sicher verwendet werden.

<b>Anmerkung:</b> Die beschriebenen Maßnahmen sind auf dem
(Anwendungs-)Server umzusetzen bzw. durchzusetzen, optional können sie
teilweise <u>zusätzlich</u> auf dem Client (z.B. Eingabeprüfung per Java
Skript) realisiert werden, um den Benutzer frühzeitig über
Falscheingaben zu informieren.

# **JAVA**

#### Prepared Statements (Parameterized Queries) \[nur für SQL, empfohlene Lösung\]

  - Java - Standard

String custname = request.getParameter("customerName"); // This should
REALLY be validated too
// perform input validation to detect attacks
String query = "SELECT account_balance FROM user_data WHERE
<span style="color: green;">**user_name = ?**</span> ";
<span style="color: green;">**PreparedStatement pstmt =
connection.prepareStatement( query );
pstmt.setString( 1, custname);**</span>
<span style="color: green;">**ResultSet results = pstmt.executeQuery(
);**</span>
;Java - Hibernate Beispiel mit Hibernate Query Language (HQL):
Empfehlung des Projekts 'Top 10 für Entwickler' für komplexe Abfragen,
vgl auch [OWASP Query_Parameterization Cheat
Sheet](Query_Parameterization_Cheat_Sheet "wikilink"):  @Entity //
declare as entity;
<span style="color: green;">**@NamedQuery(**</span>

  -
    <span style="color: green;">*' name="findByDescription",*'</span>
    <span style="color: green;">*' query="FROM Inventory i WHERE
    i.productDescription = :productDescription"*'</span>

<span style="color: green;">**)**</span>
public class Inventory implements Serializable {

  -
    @Id
    private long id;
    private String productDescription;

}

// use case
String userSuppliedParameter =
request.getParameter("Product-Description"); // This should REALLY be
validated too
// perform input validation to detect attacks
<span style="color: green;">**List<Inventory> list =**</span>

  -
    <span style="color: green;">**session.getNamedQuery("findByDescription")**</span>
    <span style="color: green;">**.setParameter("productDescription",
    userSuppliedParameter).list();**</span>

weitere Beispiele [SANS:
fix-sql-injection-in-java-hibernate](http://software-security.sans.org/developer-how-to/fix-sql-injection-in-java-hibernate)

Beispiel mit Hibernate Criteria Queries (Empfehlung des Projekts 'Top 10
für Entwickler'): --- vgl
<http://lists.owasp.org/pipermail/owasp_top_10_fuer_entwickler/2013-July/000051.html>

`     und `<http://lists.owasp.org/pipermail/owasp_top_10_fuer_entwickler/2013-July/000053.html>` --->`

String userSuppliedParameter =
request.getParameter("Product-Description"); // This should REALLY be
validated too
// perform input validation to detect attacks
<span style="color: green;">*' Inventory inv =
*'</span>

  -
    <span style="color: green;">*' (Inventory)
    session.createCriteria(Inventory.class).add(Restrictions.eq("productDescription",
    userSuppliedParameter)).uniqueResult();*'</span>



#### Benutzereingaben sorgfältig prüfen und entschärfen (Escaping All User Supplied Input)
\[bisher nur für SQL\]

Die Metazeichen sind je Backend-Typ und meist auch je Backend-Hersteller
unterschiedlich (z.B. Datenbank-Hersteller), vgl [OWASP's
ESAPI](ESAPI "wikilink").  Codec ORACLE_CODEC = new OracleCodec();
//added
String query = "SELECT user_id FROM user_data WHERE user_name = '"
+
: <span style="color: green;">**ESAPI.encoder().encodeForSQL(
ORACLE_CODEC, //added**</span>
: <span style="color: green;">**req.getParameter("userID") )**</span> +
"' and user_password = '" +
: <span style="color: green;">**ESAPI.encoder().encodeForSQL(
ORACLE_CODEC, //added**</span>
: <span style="color: green;">**req.getParameter("pwd") )**</span> +"'";
Anmerkung: Die beschriebenen Maßnahmen sind auf dem (Anwendungs-)Server
erforderlich, optional können sie teilweise <u>zusätzlich</u> auf dem
Client (z.B. per Java Skript) umgesetzt werden, um den Benutzer
frühzeitig über Falscheingaben zu informieren.  ---- gelöscht String
custname = request.getParameter("customerName"); // This should REALLY
be validated
<span style="color: green;">**try {**</span>

  -
    <span style="color: green;">**CallableStatement cs =
    connection.prepareCall**</span>
    : <span style="color: green;">**("{call
    sp_getAccountBalance(?)}");**</span>
    <span style="color: green;">**cs.setString(1, custname);ResultSet
    results = cs.executeQuery();</span>
    : <span style="color: green;">**// … result set handling'''</span>

<span style="color: green;">**} catch (SQLException se) {**</span>
: <span style="color: green;">**// … logging and error
handling**</span>
<span style="color: green;">**}**</span> ----\>

#### Benutzereingaben sorgfältig mittels Positivlisten prüfen ([<u>White List Input Validation</u>](Input_Validation_Cheat_Sheet "wikilink"))

Diese Technik sollte bei SQL nur als Zusatzmaßnahme, oder als Notlösung
für alte Software in Betracht gezogen werden, für die anderen Typen ist
sie die einzige, bekannte Maßnahme. Die Benutzereingaben sind zunächst
zu normalisieren (= kanonisieren). APIs, wie [OWASP's
ESAPI](ESAPI "wikilink") erledigen dies automatisch. Beschränken Sie bei
den [<u>Regeln für die
Postivlisten</u>](Input_Validation_Cheat_Sheet "wikilink") die erlaubten
Zeichen, ggf. die erlaubte Zeichenfolge und den gültigen Wertebereich
bzw. die Länge der erwarteten Eingabe. Seien Sie besonders vorsichtig,
wenn Sie Zeichen erlauben möchten, die das Backend als Metazeichen
benutzt, z.B. <b>'</b> und <b>"</b> (vgl [<u>Potenziell gefährliche
Zeichen für
Interpreter</u>](https://www.bsi.bund.de/SharedDocs/Downloads/DE/BSI/Grundschutz/Download/Vorabversionen/Baustein_Webanwendungen_Hilfsmittel.pdf)).
Wandeln Sie diese jeweils in ungefährliche Zeichen um, z.B. mittels
Kodierung vor der weiteren Verarbeitung (Encoding, z.B. in ' und ").
Anmerkung: Die beschriebenen Maßnahmen sind auf dem (Anwendungs-)Server
erforderlich, optional können sie teilweise <u>zusätzlich</u> auf dem
Client (z.B. per Java Skript) umgesetzt werden, um den Benutzer
frühzeitig über Falscheingaben zu informieren.  //performing input
validation
ESAPI.validator().getValidInput
...
String query = "SELECT user_id FROM user_data WHERE user_name = '" +
...
...
\--- TEST, noch nicht geprüft\!\!\! //performing input validation
<span style="color: green;">**String
validatedName=ESAPI.validator().getValidInput("PersonName",
form.getName, "Validator.Name", 32, false);**</span>
<span style="color: green;">**String
validatedStreet=ESAPI.validator().getValidInput("StreetName",
form.getStreet, "Validator.Name", 48, false);**</span>
//performing encoding Encoder encoder = ESAPI.encoder(); String
safeName=encoder.encodeForHTML(validatedName); String
safeStreet=encoder.encodeForHTML(validatedStreet); String query =
"SELECT phone_number FROM user_data WHERE name = '" +
: safeName + "' and street = '" + safeStreet +"'";

.esapi/validation.properties: /\* zusätzliche Filter ggf. anhand [OWASP
Validation Regex Repository](Validation_Regex_Repository "wikilink")
erstellen\*/ Validator.Name=^\[a-zA-ZäöüßáàéèôÄÖÜÁÀÉÈ\]+((\[',.
-\]\[a-zA-Z\[a-zA-ZäöüßáàéèôÄÖÜÁÀÉÈ\]
\])?\[a-zA-Z\[a-zA-ZäöüßáàéèôÄÖÜÁÀÉÈ\]\]\*)\*$ ---\>

  - [OWASP SQL Injection Prevention Cheat
    Sheet](SQL_Injection_Prevention_Cheat_Sheet "wikilink")
  - [OWASP Proactive Controls:](OWASP_Proactive_Controls "wikilink")
    Kapitel über ['Parameterize
    Queries'](OWASP_Proactive_Controls#2:_Parameterize_Queries "wikilink"),
    ['Encode Data'](OWASP_Proactive_Controls#3:_Encode_Data "wikilink")
    und ['Validate all
    Inputs'](OWASP_Proactive_Controls#4:_Validate_All_Inputs "wikilink")
  - [OWASP Injection Flaws Article](Command_Injection "wikilink")
  - [ESAPI Encoder
    API](http://owasp-esapi-java.googlecode.com/svn/trunk_doc/latest/org/owasp/esapi/Encoder.html)
  - [ESAPI Input Validation
    API](http://owasp-esapi-java.googlecode.com/svn/trunk_doc/latest/org/owasp/esapi/Validator.html)
  - [ASVS: Output Encoding/Escaping Requirements
    (V6)](http://www.owasp.org/index.php/ASVS#tab=Downloads)
  - [OWASP Testing Guide: Chapter on SQL Injection
    Testing](Testing_for_SQL_Injection_\(OWASP-DV-005\) "wikilink")
  - [OWASP Code Review Guide: Chapter on SQL
    Injection](Reviewing_Code_for_SQL_Injection "wikilink")
  - [OWASP Code Review Guide: Command
    Injection](Reviewing_Code_for_OS_Injection "wikilink")
  - [OWASP Appsec: Episode 2 - Injection Attacks
    (Video)](http://www.youtube.com/watch?v=pypTYPaU7mM)

<!-- end list -->

  - [CWE Entry 77 on Command
    Injection](http://cwe.mitre.org/data/definitions/77.html)
  - [CWE Entry 89 on SQL
    Injection](http://cwe.mitre.org/data/definitions/89.html)
  - [Hibernate - ORM](http://hibernate.org/orm/documentation)
  - [BSI: IT-Grundschutz Baustein Webanwendungen: 'Hilfsmittel'
    (Potenziell gefährliche Zeichen für
    Interpreter)](https://www.bsi.bund.de/SharedDocs/Downloads/DE/BSI/Grundschutz/Download/Vorabversionen/Baustein_Webanwendungen_Hilfsmittel.pdf)

# **PHP**

#### Prepared Statements (Parameterized Queries)

PHP - PDO  $stmt = $dbh-\>prepare("INSERT INTO REGISTRY (name, value)
VALUES (:name, :value)");

$stmt-\>bindParam(':name', $name);

$stmt-\>bindParam(':value', $value);
vgl [OWASP Query_Parameterization Cheat
Sheet](Query_Parameterization_Cheat_Sheet "wikilink")

PHP - mysqli  $stmt = $mysqli-\>prepare(

`   'SELECT * `
`    FROM foo `
`    WHERE bar = ?'`

);

$stmt-\>bind_param(

`   's', `
`   $value `

);

#### Benutzereingaben sorgfältig prüfen und entschärfen (Escaping All User Supplied Input)

Diese Technik sollte bei SQL nur als Zusatzmaßnahme, oder als Notlösung
für alte Software in Betracht gezogen werden, für die anderen Typen ist
sie die einzige, bekannte Maßnahme. Die Metazeichen sind je Backend-Typ
und meist auch je Backend-Hersteller unterschiedlich (z.B.
Datenbank-Hersteller), vgl [OWASP's ESAPI für Java](ESAPI "wikilink").
Hier besteht die Gefahr, dass das escapen an einer Stelle vergessen
wird, was die Sicherung komplett aushebeln würde.
Manueller String Filter:

$stmt = $mysqli-\>query( 'SELECT \* FROM foo WHERE bar = ' .
$mysqli-\>real_escape_string($input) );

tbd Text

(optional) Text

# **.NET**

#### Prepared Statements (Parameterized Queries) \[nur für SQL\]

var conn = new SqlConnection(connString);
using (var command = new SqlCommand("GetProducts", conn))
{
: <span style="color: green;">**command.CommandType =
CommandType.StoredProcedure;**</span>
: <span style="color: green;">**command.Parameters.Add("@CategoryID",
SqlDbType.Int).Value = catID;**</span>
: <span style="color: green;">**command.Connection.Open();**</span>
: <span style="color: green;">**grdProducts.DataSource =
command.ExecuteReader();**</span>
: <span style="color: green;">**grdProducts.DataBind();**</span>
}  vgl [OWASP Top 10 for .NET developers part 1:
Injection](http://www.troyhunt.com/2010/05/owasp-top-10-for-net-developers-part-1.html)

tbd: Register für .NET, bitte befüllen
Text

#### Benutzereingaben sorgfältig prüfen und entschärfen (Escaping All User Supplied Input)

Diese Technik sollte bei SQL nur als Zusatzmaßnahme, oder als Notlösung
für alte Software in Betracht gezogen werden, für die anderen Typen ist
sie die einzige, bekannte Maßnahme. Die Metazeichen sind je Backend-Typ
und meist auch je Backend-Hersteller unterschiedlich (z.B.
Datenbank-Hersteller), vgl [OWASP's ESAPI](ESAPI "wikilink").

Manueller Filer für eine Zahl:  var catID =
Request.QueryString\["CategoryID"\];
<span style="color: green;">**var positiveIntRegex = new
Regex(@"^0\*\[1-9\]\[0-9\]\*$");**</span>
<span style="color: green;">**if(\!positiveIntRegex.IsMatch(catID))**</span>
<span style="color: green;">**{**</span>
: <span style="color: green;">**lblResults.Text = "An invalid CategoryID
has been specified.";**</span>
: <span style="color: green;">**return;**</span>
<span style="color: green;">**}**</span>  vgl [OWASP Top 10 for .NET
developers part 1:
Injection](http://www.troyhunt.com/2010/05/owasp-top-10-for-net-developers-part-1.html)

(optional) Text

\-- weitere Programmiersprachen oder evtl Anti-Beispiele

# **Test**

tbd Text

tbd Text

tbd Text

(optional) Text

\-----------------------------------------------------\> <headertabs />