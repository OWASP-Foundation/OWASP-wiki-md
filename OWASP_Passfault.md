# Main

<div style="width:100%;height:160px;border:0,margin:0;overflow: hidden;">

![Passfault-header.png](Passfault-header.png "Passfault-header.png")

</div>

<div style="width:100%;height:90px;border:0,margin:0;overflow: hidden;">

![_lab_big.jpg](_lab_big.jpg "_lab_big.jpg")

</div>

<table>
<tbody>
<tr class="odd">
<td><h2 id="owasp_passfault">OWASP Passfault</h2>
<p>OWASP Passfault evaluates the strength of passwords accurately enough to predict the time to crack. It makes creating passwords and password policies significantly more intuitive and simple. Passwords don't have to be annoying!</p>
<h2 id="introduction">Introduction</h2>
<p>OWASP Passfault is more ...</p>
<dl>
<dt>Accurate : Measures the size of password patterns and identifies more weak passwords, yet allows strong passwords that don't match traditional password policies<br />
Informative : Provides detailed analysis of the password and sub patterns within the password, so users quickly learn how to make strong passwords without training.<br />
Simple : Presents the password strength as the "time to crack" to help communicate the risk of poor paswords, providing the incentive to create stronger passwords.<br />
Powerful : Empowers administrators to know and control the strength and risk of the organization's passwords.</dt>

</dl>
<h2 id="description">Description</h2>
<p>When setting a password, OWASP Passfault examines the password, looking for common patterns. It than measures the <em>size of the patterns and combinations of patterns</em>. The end result is a more academic and accurate measurement of password strength.</p>
<p>When setting a password policy, OWASP Passfault simplifies configuration to one simple meaningful measurement: <strong>the number of passwords found in the password patterns</strong>. This measurement is made more intuitive and meaningful with an estimated time to crack.</p>
<h2 id="licensing">Licensing</h2>
<p>OWASP Passfault is free to use. It is licensed under the <a href="http://www.apache.org/licenses/LICENSE-2.0">Apache License version 2.0</a> .</p></td>
<td><h2 id="what_is_passfault">What is Passfault?</h2>
<p>OWASP Passfault provides:</p>
<ul>
<li>Password Strength Evaluation</li>
<li>Password Policy Replacement</li>
</ul>
<h2 id="presentation">Presentation</h2>
<figure>
<img src="Passfault-prezi-thumbnail.png" title="Passfault-prezi-thumbnail.png" alt="Passfault-prezi-thumbnail.png" /><figcaption>Passfault-prezi-thumbnail.png</figcaption>
</figure>
<h2 id="articles">Articles</h2>
<p><em>Your Passwords don't Suck, its your Policies</em> <a href="http://www.zdnet.com/blog/identity/your-passwords-dont-suck-its-your-policies/482">ZDNet</a></p>
<p><em>Redefining Password Strength and Creation</em> <a href="http://midsizeinsider.com/en-us/article/passfault-redefining-password-strength">MidsizeInsider, IBM</a></p>
<p><em>How long would it take to crack your password</em> <a href="http://nakedsecurity.sophos.com/2012/05/25/how-long-would-it-take-to-crack-your-password/">Naked Security, Sophos</a></p>
<h2 id="research">Research</h2>
<p><em>Passfault: an Open Source Tool for Measuring Password Complexity and Strength</em> <embed src="Artigo-Passfault.pdf" title="fig:File:Artigo-Passfault.pdf" /></p>
<p><em>General Framework for Evaluating Password Complexity and Strength</em> <a href="http://arxiv.org/abs/1512.05814">Cornell University Library</a> "...This is something that has not been captured by any previous password strength or complexity measures, with the exception of [OWASP] Passfault"</p></td>
<td><h2 id="quick_download">Quick Download</h2>
<p><a href="https://github.com/owasp/passfault/releases">downloads</a></p>
<h2 id="demo_page">Demo Page</h2>
<p><a href="https://passfault.appspot.com/password_strength.html">demo site</a></p>
<h2 id="project_leader">Project Leader</h2>
<p><a href="User:Cam_Morris" title="wikilink">Cam Morris</a></p>
<h2 id="related_projects">Related Projects</h2>
<p><a href="Password_Storage_Cheat_Sheet" title="wikilink">Password_Storage_Cheat_Sheet</a></p>
<h2 id="ohloh">Ohloh</h2>
<p><a href="https://www.ohloh.net/p/passfault">https://www.ohloh.net/p/passfault</a></p></td>
</tr>
</tbody>
</table>

# FAQs

## Demo Site

  - Does the Demo Site capture or log passwords?
    No, of course not

<!-- end list -->

  - How can I be sure the Demo Site doesn't capture or log passwords?
    You can't, There is no way to verify what is uploaded to appspot
    (google is hosting the demo site) However, you can look at the code:
    <https://github.com/c-a-m/passfault/blob/master/jsonService/src/main/java/org/owasp/passfault/web/PassfaultServlet.java>
    We took the following steps to ensure the passwords don't get
    logged:

<!-- end list -->

  - GETs are blocked so no urls will have accidental passwords stored in
    the logs
  - passwords are read directly from the input stream to prevent parsing
    into Java Strings
  - the memory is cleared as soon as analysis is complete.
  - HTTPS is required on this URL (using the appspot domain)

To be extra cautious, download the code and execute it locally. (See the
readme) <https://github.com/c-a-m/passfault/blob/master/README.txt>

  - Why do you need to pass the password over the wire?\! Isn't that
    insecure? Others do it in javascript-client why don't you?
    Passfault's mission is to replace password policies, not just be a
    cute strength meter. It was intended to be used by the sites that
    already take and use your passwords. With that use-case, adding
    Passfault doesn't lessen security in any way. Plus it has the added
    benefit that we can store LOTS of password lists and do some
    in-depth analysis that can't be done client-side.

<!-- end list -->

  - Does 2FA (two-factor authentication) make Passfault obsolete?
    No, not if one of the factors is password authentication. 2FA
    lessens the risk of passwords, but if you no longer care about
    password security then you shouldn't use passwords for
    authentication at all. If you still use passwords, you should have
    an *effective* password policy.

<!-- end list -->

  - Some argue that password policies make passwords less secure, does
    that apply to Passfault?
    Researchers have found that, of all techniques used by password
    policies, only the required length had an effect on the overall
    strength, and even that claim is dubious. Passfault works different
    and we claim we can do better, a lot better, than any traditional
    password policy.

<!-- end list -->

  - How does Passfault compare to zxcvbn?
    Passfault is very similar to zxcvbn in it's approach to password
    analysis. In fact it is the only comparable tool that we know of,
    and the only alternative we endorse. zxcvbn presents the strength in
    units of "entropy", this measurement could be derived from
    passfault's "pattern size", however we feel that the "time-to-crack"
    help convey to the end user it's real risk (the downside to this is
    that really large numbers don't mean much to users, 10 years, or 10
    million years, still feels like a long way away. Entropy is
    logarithmic so it shows this better. However entropy units are not
    intuitive to users.). We also search for a few more patterns that we
    think are valuable.

<!-- end list -->

  - Why java - I hate java. If it were only in language *x* I'd use
    it.
    Passfault is packaged up in docker as a microservice. You'd probably
    want to run passfault as a microservice anyway, so forget that it's
    java and just run with it. That said, we welcome any ports to
    typescript or any other language.

Discuss with us more on twitter [1](https://twitter.com/c4mm0r) or join
the email list: [2](https://lists.owasp.org/mailman/listinfo/passfault)

# Acknowledgements

## Volunteers

OWASP Passfault is developed by a worldwide team of volunteers. The
primary contributors to date have been:

  - Cam Morris
  - Bernardo Araujo Rodrigues
  - Ray Stone
  - New Jersey Institute of Technology students contributed to release
    0.8 (Highlander):
      - Michael Glassman
      - Georgina Matias
      - Scott Sands
      - Brandon Lyew
      - Kevin Sealy
      - Llina Ljoljevski
  - University of Florida Students contibuted to release 0.7 (Gator):
      - Neeti Pathak
      - Carlos Vasquez
      - Chelsea Metcalf
      - Yang Ou

## Others

  - Partnet Inc. has donated paid labor on OWASP Passfault
  - JetBrains has donated professional licenses for [IntelliJ
    IDEA](https://www.jetbrains.com/idea/). If you are developing on
    OWASP Passfault contact the project leader and be sure to get a
    license\!

# Getting Involved

  - Join the [OWASP Passfault Mailing
    list](http://https://lists.owasp.org/mailman/listinfo/passfault)
  - See the Roadmap
  - Peruse the [open issues](https://github.com/c-a-m/passfault/issues)
  - Fork the code on [github](https://github.com/c-a-m/passfault).
  - If contribute significantly to the project contact the project
    leader for a [professional license of IntelliJ IDEA by
    JetBrains](https://www.jetbrains.com/idea/features/editions_comparison_matrix.htm)
    (Thanks JetBrains\!)

# Roadmap

# Project About

__NOTOC__ <headertabs />

[Category:OWASP Project](Category:OWASP_Project "wikilink")
[Category:OWASP_Builders](Category:OWASP_Builders "wikilink")
[Category:OWASP_Defenders](Category:OWASP_Defenders "wikilink")
[Category:OWASP_Document](Category:OWASP_Document "wikilink")