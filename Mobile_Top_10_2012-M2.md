`    <td ``>Threat Description `

</td>

`    <td ``> Attack Vector Description `

</td>

`    <td colspan=2  ``>Security Weakness Description `

</td>

`    <td ``>Technical Impacts`

</td>

`    <td ``>Business Impacts `

</td>

The M2 category is one that is always in heavy debate. It encompasses
almost everything that a mobile application can do badly that does not
take place on the phone. Which is exactly the argument… should it be
listed at all? Don’t we have Top Ten lists for Web Applications? Don’t
we have one for cloud too?

In fact, we do. If we could be altogether sure that everyone who wanted
information on mobile security also stopped by those projects… it would
be a perfect world. Unfortunately, after two rounds of data collection
from some of the world’s top assessment teams, we find that server side
issues are so prevalent in mobile applications that we cannot ignore
them in the Risk listing. M2 is only .52% lower in prevalence than M1
(Insecure Data Storage) and almost always trumps M1 findings in terms of
overall risk. While not statistically validated we feel that several
factors lead to bad mobile application server code (and on a larger
scale mobile insecurity in general):

  - Rush to market
  - Lack of security knowledge because of the new-ness of the languages
  - Easy access to frameworks that don’t prioritize security
  - Higher than average outsourced development
  - Lower security budgets for mobile applications
  - Assumption that the mobile OS takes full responsibility for security
  - Weakness due to cross-platform development and compilation

Secure coding and configuration practices must be used on server-side of
the mobile application. For specific vulnerability information refer to
the OWASP Web Top Ten or Cloud Top Ten projects. We will try and link
references to those projects and other OWASP projects that provide more
robust descriptions.

If you look below, you can see that there is a ton of surface area to
cover when thinking about M2:

![CloudTT_thum.png](CloudTT_thum.png
"CloudTT_thum.png")![WebTT_thumb.png](WebTT_thumb.png
"WebTT_thumb.png")

### The Worst Offenders

While we cannot go over all of these, what we can do is list
vulnerability types that we see most often within mobile applications:

  - Poor Web Services Hardening
    Logic flaws
      -
        [Testing for business logic
        flaws](https://www.owasp.org/index.php/Testing_for_business_logic_\(OWASP-BL-001\))
        [Business Logic Security Cheat
        Sheet](https://www.owasp.org/index.php/Business_Logic_Security_Cheat_Sheet)
    Weak Authentication
      -
        [OWASP Top Ten Broken Authentication
        Section](https://www.owasp.org/index.php/Top_10_2013-A2-Broken_Authentication_and_Session_Management)
        [Authentication Cheat
        Sheet](https://www.owasp.org/index.php/Authentication_Cheat_Sheet)
        [Developers Guide for
        Authentication](https://www.owasp.org/index.php/Guide_to_Authentication)
        [Testing for
        Authentication](https://www.owasp.org/index.php/Testing_for_authentication)
    Weak or no session management
    Session fixation
    Sensitive data transmitted using GET method

<!-- end list -->

  - Insecure web server configurations
    Default content
    Administrative interfaces

<!-- end list -->

  - Injection (SQL, XSS, Command) on both web services and
    mobile-enabled websites

<!-- end list -->

  - Authentication flaws

<!-- end list -->

  - Session Management flaws

<!-- end list -->

  - Access control vulnerabilities

<!-- end list -->

  - Local and Remote File Includes

References