  - This API is designed to automatically take care of many aspects of
    application security, making these issues invisible to the
    developers.
  - The ESAPI architecture is very simple, just a collection of classes
    that encapsulate the key security operations most applications need.
    ESAPI is designed to make it easy to retrofit security into existing
    applications, as well as providing a solid foundation for new
    development. New development projects should consider integrating
    ESAPI into their framework to make even more of the security happen
    automatically. ESAPI comes with an ESAPI filter that minimizes the
    changes required to your base application.
  - The ESAPI covers most of the key security challenges facing
    application developers. ESAPI provides the capability for developers
    to create applications that are protected against almost all of the
    risks described in the OWASP [Top Ten](Top_Ten "wikilink"). Compare
    this coverage with automated scanning and static analysis tools, and
    then consider how your time is best spent.
    <http://owasp-esapi-java.googlecode.com/svn/trunk/doc/org/owasp/esapi/doc-files/OWASPTopTen.jpg>
  - There are two key parts to the ESAPI:
      - A set of interfaces,
      - A reference implementation.
  - By using the ESAPI, applications across an organization will be
    easier to develop, more consistent, and easier to update in a single
    place. The use of the ESAPI will make it much easier for static
    analysis tools to verify an application, as the ESAPI calls can be
    built into the ruleset.