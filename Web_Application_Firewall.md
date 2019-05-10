# Description

A **web application firewall (WAF)** is an [application
firewall](https://en.wikipedia.org/wiki/Application_firewall) for HTTP
applications. It applies a set of rules to an HTTP conversation.
Generally, these rules cover common attacks such as [cross-site
scripting (XSS)](Cross-site_Scripting_\(XSS\) "wikilink") and [SQL
injection](SQL_Injection "wikilink").

While proxies generally protect clients, WAFs protect servers. A WAF is
deployed to protect a specific web application or set of web
applications. A WAF can be considered a [reverse
proxy](https://en.wikipedia.org/wiki/Reverse_proxy).

WAFs may come in the form of an appliance, server plugin, or filter, and
may be customized to an application. The effort to perform this
customization can be significant and needs to be maintained as the
application is modified.

# OWASP Projects

  - The [OWASP ModSecurity CRS
    Project's](https://www.owasp.org/index.php/Category:OWASP_ModSecurity_Core_Rule_Set_Project)
    goal is to provide an easily "pluggable" set of generic attack
    detection rules that provide a base level of protection for any web
    application.
  - Consider the [Web Application Firewall Evaluation Criteria Project
    (WAFEC)](https://www.owasp.org/index.php/WASC_OWASP_Web_Application_Firewall_Evaluation_Criteria_Project)
    to help evaluate commercial and open source web application
    firewalls.

# References

  - <https://en.wikipedia.org/wiki/Web_application_firewall>

[Category: OWASP WAF](Category:_OWASP_WAF "wikilink")