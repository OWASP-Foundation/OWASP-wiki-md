## ESAPI 2.1

  - Remove JavaEncryptor as singleton (required so we can use persistent
    asymmetric key pairs and create dsigs that persist across a JVM
    instance).
  - Add simpler means to use different cipher algorithms and/or key
    sizes. (Requires a major kludge today, which is not really
    thread-safe.
  - Support for persist asymmetric key pairs in either Java or PKCS\#12
    key stores.
  - Separate out crypto properties from rest of ESAPI.propertie. (i.e.,
    Google Issue \#48).
  - Componentization
      - Create ESAPI-Core project
          - Deprecate the HttpUtilities interface and break up into
            logical utility classes
          - Break interfaces out from the rest of the RI code to be
            considered \*core\*
          - Redesign of the Locator to act more as a Service Registry
            and true Service Locator
          - Redesign of the ESAPI Configuration
            ([Issue 93](https://code.google.com/p/owasp-esapi-java/issues/detail?id=93)
            and
            [Issue 86](https://code.google.com/p/owasp-esapi-java/issues/detail?id=86))
          - Design and implement component registration into Service
            Registry
      - Break Reference Implementations into Components
          - ESAPI-Logger-Log4J, ESAPI-Logger-Apache,
            ESAPI-Crypto-JavaEncryptor, ESAPI-IDS-AppSensor, etc.

## ESAPI 3.0

  - Add support for / integration with some key management system.

## Future Plans

  - Crypto
      - Provide tamper-evident logging using cryptographic primitives
      - File-based encryption
  - Internationalization
  - Documentation
      - Guide to fixing specific vulnerabilities with ESAPI
      - How to integrate into existing app
      - Threat Model for each control (assumptions and coverage)

__NOTOC__