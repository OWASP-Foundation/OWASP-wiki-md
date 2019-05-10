**Esimerkki** Example.comin pääkäyttäjä saa viestin, jossa on linkki
"Katso video". Linkin takana on sivusto, mikä näyttää videon, mutta
lisäksi yksi kuva haetaan osoitteesta "<https://internaladmin.example>
piste com/firewalladmin/dropallrules.cgi?confirm=yes". Käyttäjä on
valmiiksi kirjautunut vain sisäverkossa näkyvään palomuurin
hallintaliittymään, ja tämä kutsu poistaa kaikki example.com:in
palomuurisäännöt, mikä helpottaa hyökkääjän toimia.

**Suositus** Toteuta evästeissä kulkevan istuntotunnisteen lisäksi
jokaiseen sovelluskutsuun yhtenä parametrina satunnainen arvo, jota
hyökkääjä ei voi etukäteen tietää.

TODO: Käännä seuraavat

Cross site request forgery is not a new attack, but is simple and
devastating. A CSRF attack forces a logged-on victim’s browser to send a
request to a vulnerable web application, which then performs the chosen
action on behalf of the victim. The malicious code is often not on the
attacked site. This is why it is called "Cross Site".

This vulnerability is extremely widespread, as any web application that

  - Has no authorization checks for vulnerable actions
  - Will process an action if a default login is able to be given in the
    request (e.g.
    http://www.example.com/admin/doSomething.ctl?username=admin\&passwd=admin)
  - Authorizes requests based only on credentials that are automatically
    submitted such as the session cookie if currently logged into the
    application, or “Remember me” functionality if not logged into the
    application, or a Kerberos token if part of an Intranet
    participating in integrated logon with Active Directory

is at risk. Unfortunately, today, most web applications rely solely on
automatically submitted credentials such as session cookies, basic
authentication credentials, source IP addresses, SSL certificates, or
Windows domain credentials.

This vulnerability is also known by several other names including
Session Riding, One-Click Attacks, Cross Site Reference Forgery, Hostile
Linking, and Automation Attack. The acronym XSRF is also frequently
used. OWASP and MITRE have both standardized on the term Cross Site
Request Forgery and CSRF.

## Environments Affected

All web application frameworks are vulnerable to CSRF.

## Vulnerability

A typical CSRF attack against a forum might take the form of directing
the user to invoke some function, such as the application’s logout page.
The following tag in any web page viewed by the victim will generate a
request which logs them out:

<img src="<nowiki>http://www.example.com/logout.php"></nowiki>

If an online bank allowed its application to process requests, such as
transfer funds, a similar attack might allow:

`<img
src="http://www.example.com/transfer.do?frmAcct=document.form.frmAcct&`
`toAcct=4345754&toSWIFTid=434343&amt=3434.43">`

[link below not working](category:FIXME "wikilink") Jeremiah Grossman in
his BlackHat 2006 talk [Hacking Intranet Sites from the
outside](http://www.whitehatsec.com/presentations/whitehat_bh_pres_08032006.tar.gz),
demonstrated that it is possible to force a user to make changes to
their DSL router without their consent; even if the user does not know
that the DSL router has a web interface. Jeremiah used the router’s
default account name to perform the attack.

All of these attacks work because the user’s authorization credential
(typically the session cookie) is automatically included with such
requests by the browser, even though the attacker didn’t supply that
credential.

If the tag containing the attack can be posted to a vulnerable
application, then the likelihood of finding logged in victims is
significantly increased, similar to the increase in risk between stored
and reflected XSS flaws. XSS flaws are not required for a CSRF attack to
work, although any application with XSS flaws is susceptible to CSRF
because a CSRF attack can exploit the XSS flaw to steal any
non-automatically submitted credential that might be in place to protect
against a CSRF attack. Many application worms have used both techniques
in combination.

When building defenses against CSRF attacks, you must also focus on
eliminating XSS vulnerabilities in your application since such flaws can
be used to get around most CSRF defenses you might put in place.

## Verifying Security

The goal is to verify that the application protects against CSRF attacks
by generating and then requiring some type of authorization token that
is not automatically submitted by the browser.

Automated approaches: Few automated Automated scanners can detect CSRF
vulnerabilities today, even though CSRF detection can be somewhat
automated given a sufficiently capable application scanning
engines.engine. However, if your application scanner picks up a
cross-site scripting vulnerability and you have no anti-CSRF
protections, you are very likely to be at risk from pre-canned CSRF
attacks.

Manual approaches: Penetration testing is a quick way to verify that
CSRF protection is in place. To verify that the mechanism is strong and
properly implemented, checking the code is the most efficient course of
action.

## Protection

Applications must ensure that they are not relying on credentials or
tokens that are automatically submitted by browsers. The only solution
is to use a custom token that the browser will not ‘remember’ and then
automatically include with a CSRF attack.

The following strategies should be inherent in all web applications:

  - **Ensure that there are no XSS vulnerabilities in your application**
    (see A1 – Cross Site Scripting)
  - **Insert custom random tokens into every form and URL** that will
    not be automatically submitted by the browser. For example,

<code>

<form action="/transfer.do" method="post">

</code>

<input type="hidden" name="8438927730" value="43847384383">
<code>`…`

</form>

</code>

and then verify that the submitted token is correct for the current
user. Such tokens can be unique to that particular function or page for
that user, or simply unique to the overall session. The more focused the
token is to a particular function and/or particular set of data, the
stronger the protection will be, but the more complicated it will be to
construct and maintain

  - **For sensitive data or value transactions, re-authenticate or use
    transaction signing** to ensure that the request is genuine. Set up
    external mechanisms such as e-mail or phone contact in order to
    verify requests or notify the user of the request.
  - **Do not use GET requests (URLs) for sensitive data or to perform
    value transactions.** Use only POST methods when processing
    sensitive data from the user. However, the URL may contain the
    random token as this creates a unique URL, which makes CSRF almost
    impossible to perform.
  - '''POST alone is insufficient a protection. '''You must also combine
    it with random tokens, out of band authentication or
    re-authentication to properly protect against CSRF
  - For ASP.NET,''' **[set a
    ViewStateUserKey](http://msdn2.microsoft.com/en-us/library/ms972969.aspx)**.
    '''(See references). This provides a similar type of check to a
    random token as described above.

While these suggestions will diminish your exposure dramatically,
advanced CSRF attacks can bypass many of these restrictions. The
strongest technique is the use of unique tokens, and eliminating all XSS
vulnerabilities in your application.

## Samples

  - <http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2007-0192>
  - <http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2006-5116>
  - MySpace Samy Interview
    <http://blog.outer-court.com/archive/2005-10-14-n81.html>
  - An attack which uses Quicktime to perform CSRF attacks
      - <http://www.computerworld.com/action/article.do?command=viewArticleBasic&articleId=9005607&intsrc=hm_list>

## Related Articles

  - [Cross-Site Request Forgery](Cross-Site_Request_Forgery "wikilink")
  - [Testing for CSRF](Testing_for_CSRF_\(OWASP-SM-005\) "wikilink")
  - [CSRF Guard](CSRF_Guard "wikilink")
  - [PHP CSRF Guard](PHP_CSRF_Guard "wikilink")

## References

  - CWE: CWE-352 (Cross-Site Request Forgery)
  - WASC Threat Classification: No direct mapping, but the following is
    a close match:
      - <http://www.webappsec.org/projects/threat/classes/abuse_of_functionality.shtml>
  - RSnake, "What is CSRF?",
    <http://ha.ckers.org/blog/20061030/what-is-csrf/>

\[\[category:FIXME|links not working

  - Jeremiah Grossman, slides and demos of “Hacking Intranet sites from
    the outside”
      - <http://www.whitehatsec.com/presentations/whitehat_bh_pres_08032006.tar.gz>

<!-- end list -->

  - Microsoft, ViewStateUserKey details,
      - [<http://msdn2.microsoft.com/en-us/library/ms972969.aspx#securitybarriers_topic2>](http://msdn2.microsoft.com/en-us/library/ms972969.aspx)

\]\]