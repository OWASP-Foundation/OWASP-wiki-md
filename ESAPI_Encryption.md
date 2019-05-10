## Feature Overview

TODO

## Possible Enhancements

  - Potentially rename Seal and Unseal to better describe what they do
  - seal() should include an HMAC or integrity check to ensure that the
    encrypted data has not been tampered with (see
    [CWE-649](http://cwe.mitre.org/data/definitions/649.html)). (NOTE:
    By default, ESAPI crypto already ensures message authenticity and
    seal() uses that, so this likely would be redundant. -Kevin W. Wall)

<!-- end list -->

  - The API should include support for key rotation; indicated key used
    for encryption of data

<!-- end list -->

  - The API should allow key management to be externalized, to allow
    developers to integrate their own key management strategies (such as
    a PKI).

<!-- end list -->

  - The documentation for each method should indicate whether it is
    designed to protect integrity, confidentiality, or both; and whether
    it is suitable for encrypting transient items (such as hidden form
    fields) or is designed for long-term storage.

<!-- end list -->

  - Get rid of JavaEncryptor as a singleton. It causes numerous problems
    and makes some things impossible if one wishes to only interact with
    it through the Encryptor interface level.

<!-- end list -->

  - Make it simpler to use different cipher algorithms or key sizes for
    symmetric encryption. This requires a major kludge today that is not
    at all thread safe without explicit locks. (It was so bad in fact,
    that the method to support this kludge was immediately deprecated\!)

<!-- end list -->

  - Change sign() / validateSignature() so they can use persistent
    asymmetric keys and store public / private keys used with asymmetric
    crypto operations in a PKCS\#12 or JKS key store.

<!-- end list -->

  - Create separate properties file for ESAPI crypto properties. Name it
    "ESAPI-Encryptor.properties" or something similar. (Google Issue
    \#48.)

<!-- end list -->

  - Provide tamper-evident logging using cryptographic primitives as
    well as mechanism to verify that logs produced in such a manner have
    not been tampered with.1

<!-- end list -->

  - Support for encrypting files.

<!-- end list -->

  - Support for format perserving encryption. (See
    [1](http://www.voltage.com/technology/Technology_FormatPreservingEncryption.htm)
    and
    [2](http://csrc.nist.gov/groups/ST/toolkit/BCM/documents/proposedmodes/ffsem/ffsem-spec.pdf))