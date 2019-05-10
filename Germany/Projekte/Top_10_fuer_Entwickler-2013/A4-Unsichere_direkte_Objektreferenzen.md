` `

`    <td ``>Denken Sie an verschiedene Typen von Nutzern, die auf Ihr System zugreifen. Gibt es Nutzer, die nur eingeschränkten Zugriff auf bestimmte Daten Ihres Systems haben sollen?`

</td>

`    <td ``>Der Angreifer ist autorisiert, auf ein Systemobjekt zuzugreifen. Durch einfache Änderung eines Parameters kann er auf Objekte zugreifen, für die er nicht autorisiert ist.`

</td>

`    <td colspan=2  ``>Webanwendungen nutzen oft den internen Namen oder die Kennung eines Objektes, um auf dieses zu verweisen. Anwendungen prüfen dabei nicht immer, ob der Nutzer für den Zugriff auf diese autorisiert ist. Dies führt zu unsicheren direkten Objektreferenzen. Tester können Parameter ändern, um diese Schwachstellen zu entdecken. Code-Analysen zeigen schnell, ob die Autorisierung in geeigneter Weise geprüft wird.`

</td>

`    <td ``>Diese Schwachstelle gefährdet alle Daten, die via Parameter referenziert werden können. Angreifer können auf alle verfügbaren Daten dieser Art zugreifen, außer der Namensraum ist dünn besetzt.`

</td>

`    <td ``>Prüfen Sie sorgfältig den geschäftlichen Wert ungeschützt verfügbarer Daten. Berücksichtigen Sie auch die geschäftlichen Auswirkungen, die mit der Veröffentlichung der Schwachstelle verbunden sein können.`

</td>

Die Anwendung nutzt ungeprüfte Daten in einem SQL-Aufruf, der
Account-Informationen abfragt: String query = "SELECT \* FROM accts
WHERE account = ?";
PreparedStatement pstmt = connection.prepareStatement(query , ... );
<span style="color:red">pstmt.setString( 1,
request.getParameter("acct"));</span>
ResultSet results = pstmt.executeQuery(); Ein Angreifer ändert den
Parameter ‘acct’ im Browser, um beliebige Zugangsnummern abzufragen.
Wenn keine Prüfung erfolgt, können Angreifer nicht nur auf ihren
eigenen, sondern auf jeden gewünschten Account Zugriff erhalten.
http://example.com/app/accountInfo?acct=notmyacct

Um unsichere direkte Objektreferenzen zu verhindern, muss der Schutz
eines jeden Objektes (z.B. Objektnummer, Dateiname), das für Nutzer
erreichbar ist, gewährleistet werden:

1.  <b>Indirekte Objektreferenzen verwenden\!</b> Dies verhindert den
    direkten Angriff auf nicht autorisierte Ressourcen. So sollte eine
    Auswahlbox mit sechs für den Nutzer verfügbaren Objekten die Ziffern
    1 bis 6 als Referenzen enthalten, statt deren echte
    Datenbankschlüssel. Die Anwendung muss dann diese indirekten
    Objektreferenzen den echten Datenbankschlüsseln zuordnen. Die OWASP
    ESAPI enthält Referenzzuordnungen für sequentiellen wie wahlfreien
    Zugriff, die von Entwicklern zur Vermeidung direkter Referenzen
    genutzt werden können.
2.  <b>Zugriffe prüfen\!</b> Jeder Abruf direkter Objektreferenzen aus
    nicht vertrauenswürdigen Quellen muss eine Prüfung der
    Zugriffsberechtigung beinhalten, um die Autorisierung für das
    angefragte Objekt sicherzustellen.

# **JAVA**

#### Indirekte Objektreferenzen verwenden\!

  - ESAPI

(Beispiel mit kleineren Anpassungen aus ESAPI übernommen)  Set fileSet =
new HashSet();
fileSet.addAll(...); // add direct references (e.g. File objects)
AccessReferenceMap map = new AccessReferenceMap( fileSet );
// store the map somewhere safe - like the session\!
String indRef = map.getIndirectReference( file1 );
String secureHref = "http://www.your-URL.yourTLD/esapi?file=" + indRef
);
...
// if the indirect reference doesn't exist, it's likely an attack
// getDirectReference throws an AccessControlException
// you should handle as appropriate
String indref = request.getParameter( "file" );
File file = (File)map.getDirectReference( indref );
[**Quelle:
ESAPI**](http://owasp-esapi-java.googlecode.com/svn/trunk_doc/latest/org/owasp/esapi/AccessReferenceMap.html)

#### Zugriffe prüfen\!

  - (A) InjectionChecker für Parameter Prüfung

public class InjectionChecker {

  -
    public static void check(String value)
      -
        throws InjectionCheckException {
        // see Topic A1
        ...
        if(checkFailed) {
          -
            throw new InjectionCheckException("...");
        }
    }

}

;(B) PermissionChecker für Prüfungung der Zugriffsrechte  public class
PermissionChecker {

  -
    public void check(String username, Action action,
      -

          -
            Class\<? extends Object\> objectType, String objectId)

        throws PermissionCheckException{

        ...

        if(checkFailed) {

          -
            throw new PermissionCheckException("...");

        }
    }

}

;(C) Pseudo Code für Zugriffsprüfung bei direkten Objektreferenzen  //
Parameter Wert aus dem Request abfragen
String acct = request.getParameter("acct");
InjectionChecker.check(acct);

// Informationen für die Zugriffsprüfung zustammenstellen
String username = getUsername(request);
Action action = Action.READ; // (e.g. READ, WRITE, DELETE)
Class\<? extends Object\> objectType = ObjectBean.class;
String objectId = acct;

// Zufriffsprüfung durchführen
PermissionChecker permissionChecker = getPermissionChecker();
check(username, action, objectType, objectId);

// nach erfolgreicher Prüfung kann der Parameterwert
// verwendet werden
String query = "SELECT \* FROM accts WHERE account_id = ?";
PreparedStatement pstmt = connection.prepareStatement(query , ... );
pstmt.setString( 1, acct);
ResultSet results = pstmt.executeQuery();

-----

\----------\>

  - [OWASP Top 10-2007 on Insecure Dir Object
    References](https://www.owasp.org/index.php/Top_10_2007-Insecure_Direct_Object_Reference)
  - [ESAPI Access Reference Map
    API](http://owasp-esapi-java.googlecode.com/svn/trunk_doc/latest/org/owasp/esapi/AccessReferenceMap.html)
  - [ESAPI Access Control
    API](http://owasp-esapi-java.googlecode.com/svn/trunk_doc/latest/org/owasp/esapi/AccessController.html)
    (siehe isAuthorizedForData(), isAuthorizedForFile(),
    isAuthorizedForFunction() )

Für weitere Anforderungen an Zugangskontrollen siehe
: [ASVS requirements area for Access Control
(V4)](https://www.owasp.org/index.php/ASVS).

  - [CWE Entry 639 on Insecure Direct Object
    References](http://cwe.mitre.org/data/definitions/639.html)
  - [CWE Entry 22 on Path
    Traversal](http://cwe.mitre.org/data/definitions/22.html) (Beispiel
    für einen Angriff über direkte Objektreferenzen)

# **PHP**

  - (A) Teilüberschrift

Funktion {

  -
    eingerückt;
      -
        zweifach eingerückt;
    ...

}
tbd Text

Text

  - [OWASP Top 10-2007 on Insecure Dir Object
    References](https://www.owasp.org/index.php/Top_10_2007-Insecure_Direct_Object_Reference)
  - [ESAPI Access Reference Map
    API](http://owasp-esapi-java.googlecode.com/svn/trunk_doc/latest/org/owasp/esapi/AccessReferenceMap.html)
  - [ESAPI Access Control
    API](http://owasp-esapi-java.googlecode.com/svn/trunk_doc/latest/org/owasp/esapi/AccessController.html)
    (siehe isAuthorizedForData(), isAuthorizedForFile(),
    isAuthorizedForFunction() )

Für weitere Anforderungen an Zugangskontrollen siehe
: [ASVS requirements area for Access Control
(V4)](https://www.owasp.org/index.php/ASVS).

  - [CWE Entry 639 on Insecure Direct Object
    References](http://cwe.mitre.org/data/definitions/639.html)
  - [CWE Entry 22 on Path
    Traversal](http://cwe.mitre.org/data/definitions/22.html) (Beispiel
    für einen Angriff über direkte Objektreferenzen)

# **.NET**


;(A) Methoden definieren (im Beispiel ohne Fehlerbehandlung)  public
static class IndirectReferenceMap {

  -
    public static int GetDirectReference(Guid indirectReference)
    {
      -
        var map = (Dictionary\<Guid,
        int\>)HttpContext.Current.Session\["IndirMap"\];
        return map\[indirectReference\];
    }

<!-- end list -->

  -
    public static Guid GetIndirectReference(int directReference)
    {
      -
        var map = (Dictionary\<int,
        Guid\>)HttpContext.Current.Session\["DirMap"\];
        return map == null ?
        AddDirectReference(directReference)
        : map\[directReference\];
    }

<!-- end list -->

  -
    private static Guid AddDirectReference(int directReference)
    {
      -
        var indirectReference = Guid.NewGuid();
        HttpContext.Current.Session\["DirMap"\] = new Dictionary\<int,
        Guid\>
        { {directReference, indirectReference } };
        HttpContext.Current.Session\["IndirMap"\] = new
        Dictionary\<Guid, int\>
        { {indirectReference, directReference } };
        return indirectReference;
    }

}

;(B) Bei der Ausgabe die indirekte Referenz nutzen (Service-Aufruf mit
AJAX)  service.GetCustomer('\<%= IndirectReferenceMap.

  -
    GetIndirectReference(GetCustomerId()) %\>', onSuccess, null, null);


;(C) Bei der Verarbeitung mithilfe der indirekten Referenz auf das
originale Objekt zugreifen  public Customer GetCustomer(Guid indirectId)
{

  -
    var customerId =
    IndirectReferenceMap.GetDirectReference(indirectId);

...  [**Quelle: OWASP Top 10 for .NET developers part 4: Insecure direct
object
reference**](http://www.troyhunt.com/2010/09/owasp-top-10-for-net-developers-part-4.html)
tbd Text

tbd Text

(ganze Breite) Text

  - [OWASP Top 10-2007 on Insecure Dir Object
    References](https://www.owasp.org/index.php/Top_10_2007-Insecure_Direct_Object_Reference)
  - [ESAPI Access Reference Map
    API](http://owasp-esapi-java.googlecode.com/svn/trunk_doc/latest/org/owasp/esapi/AccessReferenceMap.html)
  - [ESAPI Access Control
    API](http://owasp-esapi-java.googlecode.com/svn/trunk_doc/latest/org/owasp/esapi/AccessController.html)
    (siehe isAuthorizedForData(), isAuthorizedForFile(),
    isAuthorizedForFunction() )

Für weitere Anforderungen an Zugangskontrollen siehe
: [ASVS requirements area for Access Control
(V4)](https://www.owasp.org/index.php/ASVS).

  - [CWE Entry 639 on Insecure Direct Object
    References](http://cwe.mitre.org/data/definitions/639.html)
  - [CWE Entry 22 on Path
    Traversal](http://cwe.mitre.org/data/definitions/22.html) (Beispiel
    für einen Angriff über direkte Objektreferenzen)
  - [OWASP Top 10 for .NET developers (Troy
    Hunt)](http://asafaweb.com/OWASP%20Top%2010%20for%20.NET%20developers.pdf)

\-- weitere Programmiersprachen oder evtl Anti-Beispiele --- \>

# **Test**

tbd Text

tbd Text

tbd Text

(ganze Breite) Text

\---------------------------------------------\> <headertabs />

[Category:OWASP Top 10 fuer
Entwickler](Category:OWASP_Top_10_fuer_Entwickler "wikilink")