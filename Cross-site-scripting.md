`REDIRECT `[`Cross-site``   ``Scripting``
 ``(XSS)`](Cross-site_Scripting_\(XSS\) "wikilink")

## Description

Cross-Site Scripting attacks are an instantiation of injection problems,
in which malicious scripts are injected into the otherwise benign and
trusted web sites.

Cross-Site Scripting (XSS) vulnerabilities occur when:

1\. Data enters a Web application through an untrusted source, most
frequently a web request. 2. The data is included in dynamic content
that is sent to a web user without being validated for malicious code.

The malicious content sent to the web browser often takes the form of a
segment of JavaScript, but may also include HTML, Flash or any other
type of code that the browser may execute. The variety of attacks based
on XSS is almost limitless, but they commonly include transmitting
private data like cookies or other session information to the attacker,
redirecting the victim to web content controlled by the attacker, or
performing other malicious operations on the user's machine under the
guise of the vulnerable site.

Consequences

  - Confidentiality: The most common attack performed with cross-site
    scripting involves the disclosure of information stored in user
    cookies.

<!-- end list -->

  - Access control: In some circumstances it may be possible to run
    arbitrary code on a victim's computer when cross-site scripting is
    combined with other flaws

Exposure Period

  - Implementation: If bulletin-board style functionality is present,
    cross-site scripting may only be deterred at implementation time.

Platform

  - Language: Any
  - Platform: All (requires interaction with a web server supporting
    dynamic content)

Required Resources

  - Any

Severity

  - Medium

Likelihood of Exploit

  - Medium

Discussion

Cross-site scripting attacks can occur wherever an untrusted user has
the ability to publish content to a trusted web site. Typically, a
malicious user will craft a client-side script, which - when parsed by a
web browser - performs some activity (such as sending all site cookies
to a given E-mail address).

If the input is unchecked, this script will be loaded and run by each
user visiting the web site. Since the site requesting to run the script
has access to the cookies in question, the malicious script does also.

There are several other possible attacks, such as running "Active X"
controls (under Microsoft Internet Explorer) from sites that a user
perceives as trustworthy; cookie theft is however by far the most
common.

All of these attacks are easily prevented by ensuring that no script
tags - or for good measure, HTML tags at all - are allowed in data to be
posted publicly.

## Examples

Cross-site scripting attacks may occur anywhere that possibly malicious
users are allowed to post unregulated material to a trusted web site for
the consumption of other valid users.

The most common example can be found in bulletin-board web sites which
provide web based mailing list-style functionality.

**Example 1**

The following JSP code segment reads an employee ID, eid, from an HTTP
request and displays it to the user.

```
       <% String eid = request.getParameter("eid"); %>
       ...
       Employee ID: <%= eid %>
```

The code in this example operates correctly if eid contains only
standard alphanumeric text. If eid has a value that includes
meta-characters or source code, then the code will be executed by the
web browser as it displays the HTTP response.

Initially this might not appear to be much of a vulnerability. After
all, why would someone enter a URL that causes malicious code to run on
their own computer? The real danger is that an attacker will create the
malicious URL, then use e-mail or social engineering tricks to lure
victims into visiting a link to the URL. When victims click the link,
they unwittingly reflect the malicious content through the vulnerable
web application back to their own computers. This mechanism of
exploiting vulnerable web applications is known as Reflected XSS.

**Example 2**

The following JSP code segment queries a database for an employee with a
given ID and prints the corresponding employee's name.

```
       <%...
        Statement stmt = conn.createStatement();
        ResultSet rs = stmt.executeQuery("select * from emp where id="+eid);
        if (rs != null) {
         rs.next();
         String name = rs.getString("name");
       %>

       Employee Name: <%= name %>
```

As in Example 1, this code functions correctly when the values of name
are well-behaved, but it does nothing to prevent exploits if they are
not. Again, this code can appear less dangerous because the value of
name is read from a database, whose contents are apparently managed by
the application. However, if the value of name originates from
user-supplied data, then the database can be a conduit for malicious
content. Without proper input validation on all data stored in the
database, an attacker can execute malicious commands in the user's web
browser. This type of exploit, known as Stored XSS, is particularly
insidious because the indirection caused by the data store makes it more
difficult to identify the threat and increases the possibility that the
attack will affect multiple users. XSS got its start in this form with
web sites that offered a "guestbook" to visitors. Attackers would
include JavaScript in their guestbook entries, and all subsequent
visitors to the guestbook page would execute the malicious code.

As the examples demonstrate, XSS vulnerabilities are caused by code that
includes unvalidated data in an HTTP response. There are three vectors
by which an XSS attack can reach a victim:

  - As in Example 1, data is read directly from the HTTP request and
    reflected back in the HTTP response. Reflected XSS exploits occur
    when an attacker causes a user to supply dangerous content to a
    vulnerable web application, which is then reflected back to the user
    and executed by the web browser. The most common mechanism for
    delivering malicious content is to include it as a parameter in a
    URL that is posted publicly or e-mailed directly to victims. URLs
    constructed in this manner constitute the core of many phishing
    schemes, whereby an attacker convinces victims to visit a URL that
    refers to a vulnerable site. After the site reflects the attacker's
    content back to the user, the content is executed and proceeds to
    transfer private information, such as cookies that may include
    session information, from the user's machine to the attacker or
    perform other nefarious activities.

<!-- end list -->

  - As in Example 2, the application stores dangerous data in a database
    or other trusted data store. The dangerous data is subsequently read
    back into the application and included in dynamic content. Stored
    XSS exploits occur when an attacker injects dangerous content into a
    data store that is later read and included in dynamic content. From
    an attacker's perspective, the optimal place to inject malicious
    content is in an area that is displayed to either many users or
    particularly interesting users. Interesting users typically have
    elevated privileges in the application or interact with sensitive
    data that is valuable to the attacker. If one of these users
    executes malicious content, the attacker may be able to perform
    privileged operations on behalf of the user or gain access to
    sensitive data belonging to the user.

`  * A source outside the application stores dangerous data in a database or other data store, and the dangerous data is subsequently read back into the application as trusted data and included in dynamic content.`

**Example 3 (real)**

Taking guestbook as another example. If the application doesn't validate
the input data, in a very easy way the attacker may try to steal the
cookie from the authenticated user. All the attacker has to do is to
place in the comment field the following code:

    <SCRIPT type="text/javascript">
    var adr = '../evil.php?cakemonster=' + escape(document.cookie);
    </SCRIPT>

Above code will pass an escaped content of the cookie (according to RFC
content must be escaped before sending it via HTTP protocol with GET
method) to the evil.php script in "cakemonster" variable.

## Related Threats

## Related Attacks

  - [XSS Attacks](XSS_Attacks "wikilink")
  - [Invoking untrusted mobile
    code](Invoking_untrusted_mobile_code "wikilink")

## Related Vulnerabilities

  - [:Category:Input Validation
    Vulnerability](:Category:Input_Validation_Vulnerability "wikilink")

## Related Countermeasures

  - [:Category:Input Validation
    Control](:Category:Input_Validation_Control "wikilink")
  - [HTML Entity Encoding](HTML_Entity_Encoding "wikilink")

## Categories