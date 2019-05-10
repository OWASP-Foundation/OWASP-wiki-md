

## Description

The principle of defense-in-depth is that layered security mechanisms
increase security of the system as a whole. If an attack causes one
security mechanism to fail, other mechanisms may still provide the
necessary security to protect the system. For example, it is not a good
idea to totally rely on a firewall to provide security for an
internal-use-only application, as firewalls can usually be circumvented
by a determined attacker (even if it requires a physical attack or a
[social engineering](Social_Engineering "wikilink") attack of some
sort). Other security mechanisms should be added to complement the
protection that a firewall affords (e.g., surveillance cameras, and
security awareness training) that address different attack vectors.

Implementing a defense-in-depth strategy can add to the complexity of an
application, which runs counter to the “simplicity” principle often
practiced in security. That is, one could argue that adding new
protection functionality adds additional complexity that might bring new
risks with it. The total risk to the system needs to be weighed. For
example, an application with username/password-based authentication may
not benefit from increasing the required password length from eight
characters to 15 characters as the added complexity may result in users
writing their passwords down, thus decreasing the overall security to
the system; however, adding a smart-card requirement to authenticate to
the application would enhance the security of the application by adding
a complementary layer to the authentication process.

## Examples

### Vulnerable Administrative Interface

  -
    A failed authentication control to the [Administrative
    Interface](Administrative_Interface "wikilink") is unlikely to be
    enable to anonymous attack on the system as a whole if it correctly
    gates access to production management networks, checks for
    administrative user authorization, and logs all access.

## Related [Vulnerabilities](Vulnerabilities "wikilink")

TBD

## Related [Controls](Controls "wikilink")

The Principle of Defense-in-Depth does not relate to a particular
control or subset of controls. It is a design principle to guide the
selection of controls for an application to ensure its resilience
against different forms of attack, and to reduce the probability of a
single-point of failure in the security of the system.

## References

  - [National Security Agency Defense In Depth
    Guide](http://www.nsa.gov/ia/_files/support/defenseindepth.pdf)
  - [CLASP Security Principles](CLASP_Security_Principles "wikilink")

[Category:OWASP ASDR Project](Category:OWASP_ASDR_Project "wikilink")
[Category:Principle](Category:Principle "wikilink")