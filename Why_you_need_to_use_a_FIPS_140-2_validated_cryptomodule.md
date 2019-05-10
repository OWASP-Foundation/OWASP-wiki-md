If you are performing an application security verification according to
the [OWASP Application Security Verification Standard
(ASVS)](::Category:OWASP_Application_Security_Verification_Standard_Project "wikilink")
verification requirements, you will need to make sure that any
cryptographic functions are being performed by a FIPS 140-2 validated
cryptomodule.

![Asvs_cryptomodule.gif](Asvs_cryptomodule.gif "Asvs_cryptomodule.gif")
A cryptomodule, whether it is a software library or a hardware device,
basically consists of three parts:

  - Components that *implement cryptographic algorithms* (symmetric and
    asymmetric algorithms, hash algorithms, random number generator
    algorithms, and message authentication code algorithms)

<!-- end list -->

  - Components that *call and manage cryptographic functions* (inputs
    and outputs include cryptographic keys and so-called critical
    security parameters)

<!-- end list -->

  - A *physical container around the components* that implement
    cryptographic algorithms and the components that call and manage
    cryptographic functions

The security of a cryptomodule and its services depends on the correct
implementation and integration of *each* of these three parts. While
most folks understand that implementing cryptographic algorithms
correctly is a hard thing to do, most do not understand that calling and
managing cryptographic functions and their inputs and outputs, and
ensuring the secure construction of the physical container around the
components, are equally important in determining the security of a
cryptomodule and its services.

Using a FIPS 140-2 validated cryptomodule provides a greater chance that
the cryptomodule is providing the services that you are expecting from
it.

References:

  - CMVP: <http://csrc.nist.gov/groups/STM/cmvp/index.html>
  - CAVP: <http://csrc.nist.gov/groups/STM/cavp/index.html>

[Category:OWASP Application Security Verification Standard
Project](Category:OWASP_Application_Security_Verification_Standard_Project "wikilink")
[Category:How To](Category:How_To "wikilink")