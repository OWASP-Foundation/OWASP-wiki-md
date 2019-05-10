**Esimerkki** Sovelluksen kautta on mahdollista käsitellä
luottamuksellisia tiedostoja, jotka ovat pääsynhallinnan takana.
Tiedostoihin on linkit, jotka on tallennettu hakemistossa
/salaiset_kansiot/. Mikäli sovellus rajoittaa pääsyn tiedostoihin
ainoastaan näyttämällä valikossa valtuutetut tiedostot, on hyökkääjän
mahdollista arvata luottamuksellisten tiedostojen nimiä tai luoda niihin
linkkejä muualta.

Toinen esimerkki on pääkäyttäjätoiminnallisuus, joka on piiloitettu
polkuun /hallinta/lisaa_kayttaja.do. Jos sovellus olettaa, että
ainoastaan pääkäyttäjän valikkorakenteen kautta käytetään tätä kutsua,
on mahdollista että kuka tahansa voi lisätä sovellukseen uusia
käyttäjiä, mikäli polku on tiedossa tai arvattavissa.

**Suositus** Tarkasta jokaisen pyynnön kohdalla, että käyttäjällä on
valtuutettu suorittamaan pyynnön.

TODO: Käännä seuraavat

Frequently, the only protection for a URL is that links to that page are
not presented to unauthorized users. However, a motivated, skilled, or
just plain lucky attacker may be able to find and access these pages,
invoke functions, and view data. Security by obscurity is not sufficient
to protect sensitive functions and data in an application. Access
control checks must be performed before a request to a sensitive
function is granted, which ensures that the user is authorized to access
that function.

## Environments Affected

All web application frameworks are vulnerable to failure to restrict URL
access.

## Vulnerability

The primary attack method for this vulnerability is called "forced
browsing", which encompasses guessing links and brute force techniques
to find unprotected pages. Applications frequently allow access control
code to evolve and spread throughout a codebase, resulting in a complex
model that is difficult to understand for developers and security
specialists alike. This complexity makes it likely that errors will
occur and pages will be missed, leaving them exposed.

Some common examples of these flaws include:

  - "Hidden" or "special" URLs, rendered only to administrators or
    privileged users in the presentation layer, but accessible to all
    users if they know it exists, such as /admin/adduser.php or
    /approveTransfer.do. This is particularly prevalent with menu code.
  - Applications often allow access to "hidden" files, such as static
    XML or system generated reports, trusting security through obscurity
    to hide them.
  - Code that enforces an access control policy but is out of date or
    insufficient. For example, imagine /approveTransfer.do was once
    available to all users, but since SOX controls were brought in, it
    is only supposed to be available to approvers. A fix might have been
    to not present it to unauthorized users, but no access control is
    actually enforced when requesting that page.
  - Code that evaluates privileges on the client but not on the server,
    as in this [attack on
    MacWorld 2007](http://grutztopia.jingojango.net/2007/01/your-free-macworld-expo-platinum-pass_11.html),
    which approved "Platinum" passes worth $1700 via JavaScript on the
    browser rather than on the server.

## Verifying Security

The goal is to verify that access control is enforced consistently in
the presentation layer and the business logic for all URLs in the
application.

Automated approaches: Both vulnerability scanners and static analysis
tools have difficulty with verifying URL access control, but for
different reasons. Vulnerability scanners have difficulty guessing
hidden pages and determining which pages should be allowed for each
user, while static analysis engines struggle to identify custom access
controls in the code and link the presentation layer with the business
logic.

Manual approaches: The most efficient and accurate approach is to use a
combination of code review and security testing to verify the access
control mechanism. If the mechanism is centralized, the verification can
be quite efficient. If the mechanism is distributed across an entire
codebase, verification can be more time-consuming. If the mechanism is
enforced externally, the configuration must be examined and tested.

## Protection

Taking the time to plan authorization by creating a matrix to map the
roles and functions of the application is a key step in achieving
protection against unrestricted URL access. Web applications must
enforce access control on every URL and business function. It is not
sufficient to put access control into the presentation layer and leave
the business logic unprotected. It is also not sufficient to check once
during the process to ensure the user is authorized, and then not check
again on subsequent steps. Otherwise, an attacker can simply skip the
step where authorization is checked, and forge the parameter values
necessary to continue on at the next step.

Enabling URL access control takes some careful planning. Among the most
important considerations are:

  - **Ensure the access control matrix is part of the business,
    architecture, and design of the application**
  - **Ensure that all URLs and business functions are protected by an
    effective access control mechanism** that verifies the user’s role
    and entitlements prior to any processing taking place. Make sure
    this is done during every step of the way, not just once towards the
    beginning of any multi-step process
  - '''Perform a penetration test '''prior to deployment or code
    delivery to ensure that the application cannot be misused by a
    motivated skilled attacker
  - **Pay close attention to include/library files**, especially if they
    have an executable extension such as .php. Where feasible, they
    should be kept outside of the web root. They should verify that they
    are not being directly accessed, e.g. by checking for a constant
    that can only be created by the library’s caller
  - **Do not** **assume that users will be unaware of special or hidden
    URLs or APIs**. Always ensure that administrative and high privilege
    actions are protected
  - **Block access to all file types that your application should never
    serve**. Ideally, this filter would follow the "accept known good"
    approach and only allow file types that you intend to serve, e.g.,
    .html, .pdf, .php. This would then block any attempts to access log
    files, xml files, etc. that you never intend to serve directly.
  - **Keep up to date with virus protection and patches** to components
    such as XML processors, word processors, image processors, etc.,
    which handle user supplied data

## Samples

  - <http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2007-0147>
  - <http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2007-0131>
  - <http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2006-1227>

## References

  - CWE: CWE-425 (Direct Request), CWE-288 (Authentication Bypass by
    Alternate Path), CWE-285 (Missing or Inconsistent Access Control)
  - WASC Threat Classification:
    <http://www.webappsec.org/projects/threat/classes/predictable_resource_location.shtml>
  - OWASP, [Forced browsing](Forced_browsing "wikilink")
  - OWASP Development Guide, [Guide to
    Authorization](Guide_to_Authorization "wikilink")