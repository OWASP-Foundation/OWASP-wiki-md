**Overview of Changes from RC2**

  - Encryption Refactor
  - Java 5 Generics
  - Thread-Safety Overhaul
  - Documentation Cleanup
  - Bug Fixes from Issue Tracker

**Detailed Changelog from RC2**

# ChangeLog

  - <span class="changelog_date">2009-07-21 00:05</span>
    <span class="changelog_author">manico.james</span>
  - <span class="changelog_revision">\[\#r569 \[r569\]\]</span>
    <span class="changelog_files">.</span>
    <span class="changelog_message">ESAPI 2.0 quality branch for the
    many very talented newcomers to experiement with.</span>
  - <span class="changelog_date">2009-07-22 05:54</span>
    <span class="changelog_author">chrisisbeef</span>
  - <span class="changelog_revision">\[\#r571 \[r571\]\]</span>
    <span class="changelog_files">src/main/java/org/owasp/esapi/reference/AbstractAccessReferenceMap.java</span>
    <span class="changelog_message">New AbstractAccessReferenceMap to
    combine functionality between the 2 reference implmentations.

    The new reference implementations are backed by ConcurrentHashMap
    instead of HashMap to promote thread-safety as an aspect of
    security. They also leverage Java5 generics to allow strict typing
    of both direct references to objects and the type of key that is the
    indirect objects, allowing for complex key-types to be generated and
    used as indirect references.</span>
  - <span class="changelog_date">2009-07-22 05:56</span>
    <span class="changelog_author">chrisisbeef</span>
  - <span class="changelog_revision">\[\#r572 \[r572\]\]</span>
    <span class="changelog_files">src/main/java/org/owasp/esapi/AccessReferenceMap.java,
    src/main/java/org/owasp/esapi/reference/IntegerAccessReferenceMap.java,
    src/main/java/org/owasp/esapi/reference/RandomAccessReferenceMap.java</span>
    <span class="changelog_message">Adjusted reference implementations
    to extend the new AbstractAccessReferenceMap instead of directly
    implementing the AccessReferenceMap interface. Added Java5
    generics.</span>
  - <span class="changelog_date">2009-07-22 06:53</span>
    <span class="changelog_author">chrisisbeef</span>
  - <span class="changelog_revision">\[\#r573 \[r573\]\]</span>
    <span class="changelog_files">src/main/java/org/owasp/esapi/HTTPUtilities.java,
    src/main/java/org/owasp/esapi/reference/DefaultHTTPUtilities.java</span>
    <span class="changelog_message">Updated for thread-safety and Java5
    Generics.</span>
  - <span class="changelog_date">2009-07-24 07:43</span>
    <span class="changelog_author">chrisisbeef</span>
  - <span class="changelog_revision">\[\#r575 \[r575\]\]</span>
    <span class="changelog_files">pom.xml</span>
    <span class="changelog_message">Added AntiSamy dependency repository
    and adjusted dependency descriptor.</span>
  - <span class="changelog_date">2009-07-24 07:53</span>
    <span class="changelog_author">chrisisbeef</span>
  - <span class="changelog_revision">\[\#r576 \[r576\]\]</span>
    <span class="changelog_files">src/main/java/org/owasp/esapi/filters/RequestRateThrottleFilter.java</span>
    <span class="changelog_message">Modified synchronized block to block
    on session.getId().intern()</span>
  - <span class="changelog_date">2009-07-24 08:30</span>
    <span class="changelog_author">chrisisbeef</span>
  - <span class="changelog_revision">\[\#r577 \[r577\]\]</span>
    <span class="changelog_files">src/main/java/org/owasp/esapi/HTTPUtilities.java,
    src/main/java/org/owasp/esapi/reference/DefaultHTTPUtilities.java,
    src/test/java/org/owasp/esapi/reference/HTTPUtilitiesTest.java</span>
    <span class="changelog_message">Add new methods to retrieve typed
    attributes from the session and request from either the current
    calling thread or the passed in request/session</span>
  - <span class="changelog_date">2009-07-24 21:39</span>
    <span class="changelog_author">chrisisbeef</span>
  - <span class="changelog_revision">\[\#r578 \[r578\]\]</span>
    <span class="changelog_files">src/main/java/org/owasp/esapi/User.java,
    src/main/java/org/owasp/esapi/reference/DefaultUser.java,
    src/main/java/org/owasp/esapi/reference/FileBasedAuthenticator.java,
    src/main/java/org/owasp/esapi/util/StringUtils.java</span>
    <span class="changelog_message">FileBasedAuthenticator:
    1\. Updated source to take advantage of Java5 generics and
    auto-boxing.
    2\. Added similarity check to the generateStrongPassword method
    using recursion using the Levenshtein Distance algorythm.
    3\. Corrected some small bugs such as inserting the
    user.getAccountName() into the passwordMap instead of the user and
    there were
    a few places where we were creating an AuthenticationException but
    not throwing it.
    4\. Made a few performance enhancements with loops.

    User/DefaultUser:
    1\. Updated source to take advantage of Java5 Generics

    StringUtils:
    1\. New util class to hold String analysis and transformation
    utility methods</span>
  - <span class="changelog_date">2009-07-25 05:06</span>
    <span class="changelog_author">chrisisbeef</span>
  - <span class="changelog_revision">\[\#r579 \[r579\]\]</span>
    <span class="changelog_files">src/main/java/org/owasp/esapi/Authenticator.java</span>
    <span class="changelog_message">Corrected a typo in the
    JavaDocs</span>
  - <span class="changelog_date">2009-07-28 03:02</span>
    <span class="changelog_author">kevin.w.wall</span>
  - <span class="changelog_revision">\[\#r580 \[r580\]\]</span>
    <span class="changelog_files">src/main/resources/.esapi/ESAPI.properties</span>
    <span class="changelog_message">Updated regex for Validator.FileName
    and Validator.DirectoryName to exclude empty names.
    I.e., changed regex from {0,255} to {1,255}.</span>
  - <span class="changelog_date">2009-07-28 03:15</span>
    <span class="changelog_author">kevin.w.wall</span>
  - <span class="changelog_revision">\[\#r581 \[r581\]\]</span>
    <span class="changelog_files">src/test/resources/.esapi/ESAPI.properties</span>
    <span class="changelog_message">Updated regex for Validator.FileName
    and Validator.DirectoryName to exclude empty names.
    I.e., changed regex from {0,255} to {1,255}.</span>
  - <span class="changelog_date">2009-07-28 03:45</span>
    <span class="changelog_author">kevin.w.wall</span>
  - <span class="changelog_revision">\[\#r582 \[r582\]\]</span>
    <span class="changelog_files">src/main/java/org/owasp/esapi/codecs/Base64.java</span>
    <span class="changelog_message">Added 3 CHECKME comments as well as
    new logging in exception and fixed one spelling
    error.</span>
  - <span class="changelog_date">2009-08-04 03:26</span>
    <span class="changelog_author">kevin.w.wall</span>
  - <span class="changelog_revision">\[\#r583 \[r583\]\]</span>
    <span class="changelog_files">src/main/java/org/owasp/esapi/codecs/Base64.java</span>
    <span class="changelog_message">1) Enhanced initial CHECKME comment
    about tracker Harder version vs forking from his version.
    2\) Combined 5 separate logging entries in caught exception with one
    logging entry to prevent interleaving of logs by other threads
    making log hard to read. Still have CHECKME comment there as not
    sure if format is satisfactory with everyone. (Some may prefer one
    very long line.)
    3\) Changed caught exception to log warning rather than error,
    reasoning that if exception not rethrown but rather simply swallowed
    this doesn't justify being called an error. (OTOH, one could argue
    if your JRE is missing UTF-8 encoding, it is probably FUBAR and thus
    you might want it to be an error.) Rather than debating the merits
    on my own, I left CHECKME comment that we can discuss the approach
    during inspection.</span>
  - <span class="changelog_date">2009-08-04 03:38</span>
    <span class="changelog_author">kevin.w.wall</span>
  - <span class="changelog_revision">\[\#r584 \[r584\]\]</span>
    <span class="changelog_files">src/main/java/org/owasp/esapi/reference/JavaEncryptor.java</span>
    <span class="changelog_message">Changes to JavaEncrytor CTOR, and
    hash(), sign(), verifySignature()
    member functions to account for preferred byte encoding (defaults to
    UTF-8)
    rather using than native platform byte encoding that can vary from
    one
    platform to the next.

    Updated main()'s javadoc and changed System.out.println from using
    "\\n" to
    the Java property line.separator which should pick the correct
    line
    terminator as per native OS. Defaults to newline in unusual event
    that
    line.separator property is not set.

    Completed Javadoc for main().

    NB: These changes could conceivably affect those that were running
    on a
    platform where UTF-8 is not the native encoding (e.g., Windows OS)
    resulting
    in a different master secret. If this is a problem we can revert
    back to previous
    version or user could change encoding in ESAPI.properties. However,
    I'd rather
    cause issues now rather than later when many more are using it. I
    still need to
    check the EncryptorTest. I think it will be OK with these changes,
    but have not
    yet verified that it didn't write something out to a file that it
    later reads back
    in. If so, that may break too.</span>
  - <span class="changelog_date">2009-08-04 04:03</span>
    <span class="changelog_author">kevin.w.wall</span>
  - <span class="changelog_revision">\[\#r585 \[r585\]\]</span>
    <span class="changelog_files">src/main/java/org/owasp/esapi/waf/ESAPIWebApplicationFirewallFilter.java</span>
    <span class="changelog_message">1) Changed e.printStackTrace() to
    logger.error() message plus exception.
    2\) Changed encoding in redirectUserToErrorPage() from default
    encoding to character encoding used by
    InterceptingHttpServletResponse object.</span>
  - <span class="changelog_date">2009-08-05 04:51</span>
    <span class="changelog_author">neil.matatall</span>
  - <span class="changelog_revision">\[\#r586 \[r586\]\]</span>
    <span class="changelog_files">src/main/java/org/owasp/esapi/Encoder.java,
    src/main/java/org/owasp/esapi/EncoderConstants.java,
    src/main/java/org/owasp/esapi/StringUtilities.java,
    src/main/java/org/owasp/esapi/ValidationErrorList.java,
    src/main/java/org/owasp/esapi/ValidationRule.java,
    src/main/java/org/owasp/esapi/reference/validation/BaseValidationRule.java,
    src/main/java/org/owasp/esapi/reference/validation/CreditCardValidationRule.java,
    src/main/java/org/owasp/esapi/reference/validation/DateValidationRule.java,
    src/main/java/org/owasp/esapi/reference/validation/HTMLValidationRule.java,
    src/main/java/org/owasp/esapi/reference/validation/IntegerValidationRule.java,
    src/main/java/org/owasp/esapi/reference/validation/NumberValidationRule.java,
    src/main/java/org/owasp/esapi/reference/validation/StringValidationRule.java</span>
    <span class="changelog_message">Moved Encoder constants to own
    class, EncoderConstants per
    <https://lists.owasp.org/pipermail/owasp-esapi/2009-August/000680.html>
    StringUtilities: converted union to use varargs
    ValidationErrorList: Now uses generics
    ValidationRule: documented each method, removed unecessary
    declarations

    BaseValidationRule: fixed whitelist implementation, added
    whitelist(String, Set) updated docs, cleaned up findbugs findings
    CreditCardValidationRule: cleaned up code, abstracted
    validCreditCardFormat to allow for custom validation (currently uses
    Luhn validation), renamed getCCRule because it was misleading, added
    getter method for the ccRule
    DateValidation: fixed sanitize implementation to be consistent with
    the interface, code Cleanup
    HTMLValidationRule: fixed sanitize implementation to be consistent
    with the interface, code cleanup
    IntegerValidationRule: fixed sanitize implementation to be
    consistent with the interface, code cleanup
    NumberValidationRule: fixed sanitize implementation to be consistent
    with the interface, code cleanup
    StringValidationRule: Cleanup</span>
  - <span class="changelog_date">2009-08-06 04:06</span>
    <span class="changelog_author">neil.matatall</span>
  - <span class="changelog_revision">\[\#r587 \[r587\]\]</span>
    <span class="changelog_files">src/main/java/org/owasp/esapi/EncoderConstants.java,
    src/main/java/org/owasp/esapi/util/CollectionsUtil.java</span>
    <span class="changelog_message">Moved arrayToSet method from
    EncoderConstants to new CollectionsUtil class. Renamed method from
    array2Set.</span>
  - <span class="changelog_date">2009-08-06 04:15</span>
    <span class="changelog_author">neil.matatall</span>
  - <span class="changelog_revision">\[\#r588 \[r588\]\]</span>
    <span class="changelog_files">src/main/java/org/owasp/esapi/SecurityConfiguration.java,
    src/main/java/org/owasp/esapi/Validator.java,
    src/main/java/org/owasp/esapi/reference/DefaultSecurityConfiguration.java,
    src/main/java/org/owasp/esapi/reference/DefaultValidator.java</span>
    <span class="changelog_message">Updated classes to use
    generics.</span>
  - <span class="changelog_date">2009-08-07 02:46</span>
    <span class="changelog_author">kevin.w.wall</span>
  - <span class="changelog_revision">\[\#r589 \[r589\]\]</span>
    <span class="changelog_files">src/main/resources/.esapi/ESAPI.properties</span>
    <span class="changelog_message">Changed regular expressions for
    Validator.SystemCommand,
    Validator.HTTPParameterName, HTTPCookieName, and
    Validator.HTTPHeaderName
    properties from matching '0 to N' of character class to '1 to N' of
    same,
    where N varies depending on the property. (Note: I suppose it's
    debatable
    whether or not one should allow an empty SystemCommand. A small
    group
    of us decided not, but this should be reviewed.)

    Props to Craig Younkins for pointing these out.</span>
  - <span class="changelog_date">2009-08-07 02:48</span>
    <span class="changelog_author">kevin.w.wall</span>
  - <span class="changelog_revision">\[\#r590 \[r590\]\]</span>
    <span class="changelog_files">src/test/resources/.esapi/ESAPI.properties</span>
    <span class="changelog_message">Changed regular expressions for
    Validator.SystemCommand,
    Validator.HTTPParameterName, HTTPCookieName, and
    Validator.HTTPHeaderName
    properties from matching '0 to N' of character class to '1 to N' of
    same,
    where N varies depending on the property. (Note: I suppose it's
    debatable
    whether or not one should allow an empty SystemCommand. A small
    group
    of us decided not, but this should be reviewed.)

    Props to Craig Younkins for pointing these out.</span>
  - <span class="changelog_date">2009-08-14 04:22</span>
    <span class="changelog_author">kevin.w.wall</span>
  - <span class="changelog_revision">\[\#r591 \[r591\]\]</span>
    <span class="changelog_files">src/test/java/org/owasp/esapi/util,
    src/test/java/org/owasp/esapi/util/ThePrefectClass.java</span>
    <span class="changelog_message">Auxiliary class used with
    ObjFactoryTest class.</span>
  - <span class="changelog_date">2009-08-14 05:05</span>
    <span class="changelog_author">kevin.w.wall</span>
  - <span class="changelog_revision">\[\#r592 \[r592\]\]</span>
    <span class="changelog_files">src/main/java/org/owasp/esapi/util/ObjFactory.java</span>
    <span class="changelog_message">New generic class used to create
    various ESASPI classes from
    org.owasp.esapi.ESAPI. This class is generally reusable as
    well.</span>
  - <span class="changelog_date">2009-08-14 05:28</span>
    <span class="changelog_author">kevin.w.wall</span>
  - <span class="changelog_revision">\[\#r593 \[r593\]\]</span>
    <span class="changelog_files">src/main/java/org/owasp/esapi/CipherText.java</span>
    <span class="changelog_message">Interface to represent general
    ciphertext. This interface is in preparation for a rewrite of
    the Encryptor interface that will allow a more general encryption
    mechanism with other
    cipher modes. (The goal is to get rid of the cryptographically weak
    ECB mode and replace
    it with CBC mode or another equally strong mode. Note all other
    modes require IVs.)</span>
  - <span class="changelog_date">2009-08-14 05:31</span>
    <span class="changelog_author">kevin.w.wall</span>
  - <span class="changelog_revision">\[\#r594 \[r594\]\]</span>
    <span class="changelog_files">src/main/java/org/owasp/esapi/reference/DefaultCipherText.java</span>
    <span class="changelog_message">This class will ultimately be the
    reference ESAPI implementation of the new CipherText
    interface.

    Note that this class is just stubbed out at this time. Work on it
    continues.</span>
  - <span class="changelog_date">2009-08-14 05:36</span>
    <span class="changelog_author">kevin.w.wall</span>
  - <span class="changelog_revision">\[\#r595 \[r595\]\]</span>
    <span class="changelog_files">src/main/java/org/owasp/esapi/reference/JavaEncryptor.java</span>
    <span class="changelog_message">Replaced some of the older
    collection classes with their generic
    equivalents (e.g., TreeMap).

    Some documentation corrections.

    Added stubs for new encrypt and decrypt methods using the new
    CipherText
    interface.</span>
  - <span class="changelog_date">2009-08-14 05:38</span>
    <span class="changelog_author">kevin.w.wall</span>
  - <span class="changelog_revision">\[\#r596 \[r596\]\]</span>
    <span class="changelog_files">src/main/java/org/owasp/esapi/Encryptor.java</span>
    <span class="changelog_message">Some Javadoc improvements.

    Added the new encrypt and decrypt methods using the new CipherText
    interface.</span>
  - <span class="changelog_date">2009-08-14 05:40</span>
    <span class="changelog_author">kevin.w.wall</span>
  - <span class="changelog_revision">\[\#r597 \[r597\]\]</span>
    <span class="changelog_files">src/main/java/org/owasp/esapi/errors/ConfigurationException.java</span>
    <span class="changelog_message">Moved ConfigurationException class
    to org.owasp.esapi.errors package with most
    of the other ESAPI exceptions. Also changed it so that it extends
    RuntimeException
    rather than just Exception so these may be treated as unchecked
    exceptions
    thus simplifying the client's code.</span>
  - <span class="changelog_date">2009-08-14 05:41</span>
    <span class="changelog_author">kevin.w.wall</span>
  - <span class="changelog_revision">\[\#r598 \[r598\]\]</span>
    <span class="changelog_files">src/main/java/org/owasp/esapi/waf/ESAPIWebApplicationFirewallFilter.java</span>
    <span class="changelog_message">Changed import to reflect new
    package for ConfigurationException.</span>
  - <span class="changelog_date">2009-08-14 05:42</span>
    <span class="changelog_author">kevin.w.wall</span>
  - <span class="changelog_revision">\[\#r599 \[r599\]\]</span>
    <span class="changelog_files">src/main/java/org/owasp/esapi/waf/ConfigurationException.java</span>
    <span class="changelog_message">Removing. This class was moved to
    the org.owasp.esapi.errors package.
    (Hope this commit will actually remove it from here. We'll
    see.)</span>
  - <span class="changelog_date">2009-08-14 05:43</span>
    <span class="changelog_author">kevin.w.wall</span>
  - <span class="changelog_revision">\[\#r600 \[r600\]\]</span>
    <span class="changelog_files">src/main/java/org/owasp/esapi/waf/configuration/ConfigurationParser.java</span>
    <span class="changelog_message">Changed import to reflect new
    package for ConfigurationException.</span>
  - <span class="changelog_date">2009-08-14 05:46</span>
    <span class="changelog_author">kevin.w.wall</span>
  - <span class="changelog_revision">\[\#r601 \[r601\]\]</span>
    <span class="changelog_files">src/main/resources/.esapi/ESAPI.properties</span>
    <span class="changelog_message">Updated with new properties in
    preparation for the new, more general, encryption / decryption
    facilities using the CipherText interface.

    Also updated many of the related comments.</span>
  - <span class="changelog_date">2009-08-14 05:47</span>
    <span class="changelog_author">kevin.w.wall</span>
  - <span class="changelog_revision">\[\#r602 \[r602\]\]</span>
    <span class="changelog_files">src/test/java/org/owasp/esapi/util/ObjFactoryTest.java</span>
    <span class="changelog_message">New Junit tests for
    ObjFactory.</span>
  - <span class="changelog_date">2009-08-14 05:55</span>
    <span class="changelog_author">kevin.w.wall</span>
  - <span class="changelog_revision">\[\#r603 \[r603\]\]</span>
    <span class="changelog_files">src/test/java/org/owasp/esapi/reference/EncoderTest.java</span>
    <span class="changelog_message">Changes to use generics instead of
    the older collection classes.

    Changes to use UTF-8 encoding rather than the native encoding of
    wherever the JVM is running at the time. (This is mostly in case
    we want to persist some encoded data to use as a test
    baseline.)</span>
  - <span class="changelog_date">2009-08-14 05:56</span>
    <span class="changelog_author">kevin.w.wall</span>
  - <span class="changelog_revision">\[\#r604 \[r604\]\]</span>
    <span class="changelog_files">src/test/java/org/owasp/esapi/reference/ValidatorTest.java</span>
    <span class="changelog_message">Changes to use UTF-8 encoding rather
    than the native encoding of
    wherever the JVM is running at the time. (This is mostly in case
    we want to persist some encoded data to use as a test
    baseline.)</span>
  - <span class="changelog_date">2009-08-14 05:59</span>
    <span class="changelog_author">kevin.w.wall</span>
  - <span class="changelog_revision">\[\#r605 \[r605\]\]</span>
    <span class="changelog_files">src/test/java/org/owasp/esapi/reference/HTTPUtilitiesTest.java</span>
    <span class="changelog_message">Changes encoding to use the standard
    response encoding rather than using
    the native encoding of wherever the JVM is running at the
    time.</span>
  - <span class="changelog_date">2009-08-14 06:03</span>
    <span class="changelog_author">kevin.w.wall</span>
  - <span class="changelog_revision">\[\#r606 \[r606\]\]</span>
    <span class="changelog_files">src/test/java/org/owasp/esapi/reference/EncryptorTest.java</span>
    <span class="changelog_message">Added TODO about adding new test
    that persists encrypted data so we can test
    encrypting / decrypting across different OSes and
    architectures.</span>
  - <span class="changelog_date">2009-08-14 06:12</span>
    <span class="changelog_author">kevin.w.wall</span>
  - <span class="changelog_revision">\[\#r607 \[r607\]\]</span>
    <span class="changelog_files">src/main/java/org/owasp/esapi/ESAPI.java</span>
    <span class="changelog_message">Refactored a half-dozen or so code
    fragments of code like this:
    String accessControllerName =
    securityConfiguration().getAccessControlImplementation();
    try {
    Class theClass = Class.forName(accessControllerName);
    accessController = (AccessController)theClass.newInstance();
    } catch ( ClassNotFoundException ex ) {
    System.out.println( ex + " AccessController class (" +
    accessControllerName + ") must be in class path.");
    } catch( InstantiationException ex ) {
    System.out.println( ex + " AccessController class (" +
    accessControllerName + ") must be concrete.");
    } catch( IllegalAccessException ex ) {
    System.out.println( ex + " AccessController class (" +
    accessControllerName + ") must have a no-arg constructor.");
    }

    with the much simpler refactored code that looks like this:
    String accessControllerName =
    securityConfiguration().getAccessControlImplementation();
    accessController =
    (new ObjFactory()).make(accessControllerName,
    "AccessController");</span>
  - <span class="changelog_date">2009-08-20 00:48</span>
    <span class="changelog_author">kevin.w.wall</span>
  - <span class="changelog_revision">\[\#r609 \[r609\]\]</span>
    <span class="changelog_files">src/main/java/org/owasp/esapi/util/ObjFactory.java</span>
    <span class="changelog_message">Add private CTOR to prevent
    instantiation.</span>
  - <span class="changelog_date">2009-08-20 21:35</span>
    <span class="changelog_author">chrisisbeef</span>
  - <span class="changelog_revision">\[\#r610 \[r610\]\]</span>
    <span class="changelog_files">src/main/java/org/owasp/esapi/codecs/CSSCodec.java,
    src/main/java/org/owasp/esapi/codecs/Codec.java,
    src/main/java/org/owasp/esapi/codecs/HTMLEntityCodec.java,
    src/main/java/org/owasp/esapi/codecs/JavaScriptCodec.java,
    src/main/java/org/owasp/esapi/codecs/PercentCodec.java</span>
    <span class="changelog_message">Updated code to use Java5 Generics
    and new API's</span>
  - <span class="changelog_date">2009-08-25 03:38</span>
    <span class="changelog_author">kevin.w.wall</span>
  - <span class="changelog_revision">\[\#r611 \[r611\]\]</span>
    <span class="changelog_files">documentation/ESAPI_2.0_ReleaseNotes_CryptoChanges.html</span>
    <span class="changelog_message">New file -- Explains why we are
    making changes to the Encryptor encrypt / decrypt methods in ESAPI
    Java 2.0 and gives some examples of use.</span>
  - <span class="changelog_date">2009-08-25 03:42</span>
    <span class="changelog_author">kevin.w.wall</span>
  - <span class="changelog_revision">\[\#r612 \[r612\]\]</span>
    <span class="changelog_files">src/main/resources/.esapi/ESAPI.properties</span>
    <span class="changelog_message">Summarized crypto changes, added new
    properties to support new Encryptor encrypt / decrypt methods,
    briefly explained backward compatibility for Encryptor.</span>
  - <span class="changelog_date">2009-08-25 03:47</span>
    <span class="changelog_author">kevin.w.wall</span>
  - <span class="changelog_revision">\[\#r613 \[r613\]\]</span>
    <span class="changelog_files">src/main/java/org/owasp/esapi/CipherText.java</span>
    <span class="changelog_message"> Untested\! Made Serializable, added
    several new methods, flushed out Javadoc.</span>
  - <span class="changelog_date">2009-08-25 03:49</span>
    <span class="changelog_author">kevin.w.wall</span>
  - <span class="changelog_revision">\[\#r614 \[r614\]\]</span>
    <span class="changelog_files">src/main/java/org/owasp/esapi/Encryptor.java</span>
    <span class="changelog_message"> Flushed out Javadoc. Added 2 new
    methods (encrypt() and decrypt() that take a SecretKey).</span>
  - <span class="changelog_date">2009-08-25 03:53</span>
    <span class="changelog_author">kevin.w.wall</span>
  - <span class="changelog_revision">\[\#r615 \[r615\]\]</span>
    <span class="changelog_files">src/main/java/org/owasp/esapi/ESAPI.java</span>
    <span class="changelog_message">Added some comments for discussion
    (marked 'DISCUSS').</span>
  - <span class="changelog_date">2009-08-25 03:54</span>
    <span class="changelog_author">kevin.w.wall</span>
  - <span class="changelog_revision">\[\#r616 \[r616\]\]</span>
    <span class="changelog_files">src/main/java/org/owasp/esapi/PreparedString.java</span>
    <span class="changelog_message"> Fixed Javadoc so it wouldn't
    prematurely die.</span>
  - <span class="changelog_date">2009-08-25 03:56</span>
    <span class="changelog_author">kevin.w.wall</span>
  - <span class="changelog_revision">\[\#r617 \[r617\]\]</span>
    <span class="changelog_files">src/main/java/org/owasp/esapi/Randomizer.java</span>
    <span class="changelog_message">Added new method, getRandomBytes(int
    n).</span>
  - <span class="changelog_date">2009-08-25 03:58</span>
    <span class="changelog_author">kevin.w.wall</span>
  - <span class="changelog_revision">\[\#r618 \[r618\]\]</span>
    <span class="changelog_files">src/main/java/org/owasp/esapi/SecurityConfiguration.java</span>
    <span class="changelog_message"> Fixed misc Javadoc, added several
    new mthods to support new Encryptor encrypt / decrypt
    methods.</span>
  - <span class="changelog_date">2009-08-25 03:59</span>
    <span class="changelog_author">kevin.w.wall</span>
  - <span class="changelog_revision">\[\#r619 \[r619\]\]</span>
    <span class="changelog_files">src/main/java/org/owasp/esapi/codecs/Hex.java</span>
    <span class="changelog_message">New class to do hexadecimal encoding
    / decoding.</span>
  - <span class="changelog_date">2009-08-25 04:04</span>
    <span class="changelog_author">kevin.w.wall</span>
  - <span class="changelog_revision">\[\#r620 \[r620\]\]</span>
    <span class="changelog_files">src/main/java/org/owasp/esapi/reference/DefaultCipherText.java</span>
    <span class="changelog_message">Untested\! Completed implementation
    and Javadoc.</span>
  - <span class="changelog_date">2009-08-25 04:05</span>
    <span class="changelog_author">kevin.w.wall</span>
  - <span class="changelog_revision">\[\#r621 \[r621\]\]</span>
    <span class="changelog_files">src/main/java/org/owasp/esapi/reference/DefaultRandomizer.java</span>
    <span class="changelog_message">Untested\! Implemented new
    gentRandomBytes(int) method.</span>
  - <span class="changelog_date">2009-08-25 04:07</span>
    <span class="changelog_author">kevin.w.wall</span>
  - <span class="changelog_revision">\[\#r622 \[r622\]\]</span>
    <span class="changelog_files">src/main/java/org/owasp/esapi/reference/DefaultSecurityConfiguration.java</span>
    <span class="changelog_message">Untested\! - Implemented new methods
    to support new Encryptor encrypt / decrypt methods, Javadoc
    corrections.</span>
  - <span class="changelog_date">2009-08-25 04:09</span>
    <span class="changelog_author">kevin.w.wall</span>
  - <span class="changelog_revision">\[\#r623 \[r623\]\]</span>
    <span class="changelog_files">src/main/java/org/owasp/esapi/reference/JavaEncryptor.java</span>
    <span class="changelog_message"> Untested\! Lots of Javadoc changes.
    Implemented 2 new encrypt() and 2 new decrypt() methods.</span>
  - <span class="changelog_date">2009-08-25 04:12</span>
    <span class="changelog_author">kevin.w.wall</span>
  - <span class="changelog_revision">\[\#r624 \[r624\]\]</span>
    <span class="changelog_files">src/main/java/org/owasp/esapi/util/CipherSpec.java</span>
    <span class="changelog_message">Untested\! New class. A Serializable
    class that carries all info about a specific cipher specification
    that was used to encrypt some particular ciphertext (other than the
    SecretKey of course). Main intent is to be used with CipherText, but
    may be used alone.</span>
  - <span class="changelog_date">2009-08-25 04:15</span>
    <span class="changelog_author">kevin.w.wall</span>
  - <span class="changelog_revision">\[\#r625 \[r625\]\]</span>
    <span class="changelog_files">src/main/java/org/owasp/esapi/util/CryptoHelper.java</span>
    <span class="changelog_message">Untested\! New class. Some static
    methods to simplify encryption and decryption of plaintext Strings,
    to be used as a replacement for the deprecated Encryptor encrypt()
    and decrypt() methods if ESAPI users find the newer methods too
    inconvenient to use.</span>
  - <span class="changelog_date">2009-08-25 04:18</span>
    <span class="changelog_author">kevin.w.wall</span>
  - <span class="changelog_revision">\[\#r626 \[r626\]\]</span>
    <span class="changelog_files">src/main/java/org/owasp/esapi/util/ObjFactory.java</span>
    <span class="changelog_message">Mostly tested (except for one or 2
    'catch' clauses). Fixed some Javadoc. Made CTOR public (probably is
    a way to just do this using a static method, but it wasn't obvious
    and I didn't want to screw with it). Improved some internal
    documentation. Added OWASP copyright notice.</span>
  - <span class="changelog_date">2009-08-25 04:20</span>
    <span class="changelog_author">kevin.w.wall</span>
  - <span class="changelog_revision">\[\#r627 \[r627\]\]</span>
    <span class="changelog_files">src/main/java/org/owasp/esapi/util/StringUtils.java</span>
    <span class="changelog_message">Added new notNullOrEmpty() method
    used in assertions. (untested).</span>
  - <span class="changelog_date">2009-08-25 05:12</span>
    <span class="changelog_author">kevin.w.wall</span>
  - <span class="changelog_revision">\[\#r628 \[r628\]\]</span>
    <span class="changelog_files">src/main/resources/owasp-esapi-dev.jks</span>
    <span class="changelog_message">New keystore file for DEVELOPMENT
    only. It is self-signed. Purpose is for jar signing.
    Note that passphrases for both the keystore and the private key is
    'changeme' (without
    the quotes). Modified pom.xml to use this.</span>
  - <span class="changelog_date">2009-08-25 05:14</span>
    <span class="changelog_author">kevin.w.wall</span>
  - <span class="changelog_revision">\[\#r629 \[r629\]\]</span>
    <span class="changelog_files">pom.xml</span>
    <span class="changelog_message">Try to fix the jar signing by using
    new self-signed Java keystore file. Still needs lots of work. See
    comments regarding this therein.</span>
  - <span class="changelog_date">2009-08-26 04:02</span>
    <span class="changelog_author">kevin.w.wall</span>
  - <span class="changelog_revision">\[\#r630 \[r630\]\]</span>
    <span class="changelog_files">src/main/java/org/owasp/esapi/util/StringUtils.java</span>
    <span class="changelog_message">Duh\! Fix brainfart \#1 (don't code
    even _simple_ stuff when your sleepy :); fixed notNullOrEmpty()
    Fix spelling error in Javadoc.</span>
  - <span class="changelog_date">2009-08-26 04:02</span>
    <span class="changelog_author">kevin.w.wall</span>
  - <span class="changelog_revision">\[\#r631 \[r631\]\]</span>
    <span class="changelog_files">src/test/java/org/owasp/esapi/util/StringUtilsTest.java</span>
    <span class="changelog_message">New JUnit test for StringUtils
    class.</span>
  - <span class="changelog_date">2009-08-26 04:08</span>
    <span class="changelog_author">kevin.w.wall</span>
  - <span class="changelog_revision">\[\#r632 \[r632\]\]</span>
    <span class="changelog_files">target/ESAPI-2.0-javadoc.jar</span>
    <span class="changelog_message">Jar containing latest ESAPI Java 2.0
    javadoc.
    This will have to do until we can post the actual (unjarred) Javadoc
    somewhere.</span>
  - <span class="changelog_date">2009-08-30 04:17</span>
    <span class="changelog_author">kevin.w.wall</span>
  - <span class="changelog_revision">\[\#r633 \[r633\]\]</span>
    <span class="changelog_files">src/test/java/org/owasp/esapi/util/CipherSpecTest.java</span>
    <span class="changelog_message">New - JUnit test for
    org.owasp.esapi.util.CipherSpec class.</span>
  - <span class="changelog_date">2009-08-30 04:20</span>
    <span class="changelog_author">kevin.w.wall</span>
  - <span class="changelog_revision">\[\#r634 \[r634\]\]</span>
    <span class="changelog_files">src/main/java/org/owasp/esapi/util/CipherSpec.java</span>
    <span class="changelog_message">Changes made to CipherSpec as result
    of JUnit testing. Biggest change had to
    do with being able to hand cipher transformation specified like
    this:
    Cipher cipher = Cipher.getInstance("AES"); // No mode or padding
    scheme given.
    CipherSpec cipherSpec = new CipherSpec(cipher);

    For those I used "ECB" for cipher mode and "NoPadding" for padding
    scheme
    which seems to be the defaults I've run across, at least for SunJCE
    and AES,
    DES, and DESede.</span>
  - <span class="changelog_date">2009-08-30 04:21</span>
    <span class="changelog_author">kevin.w.wall</span>
  - <span class="changelog_revision">\[\#r635 \[r635\]\]</span>
    <span class="changelog_files">src/main/resources/.esapi/ESAPI.properties</span>
    <span class="changelog_message">Added some more comments to try to
    clarify things a bit.</span>
  - <span class="changelog_date">2009-08-30 04:23</span>
    <span class="changelog_author">kevin.w.wall</span>
  - <span class="changelog_revision">\[\#r636 \[r636\]\]</span>
    <span class="changelog_files">src/test/resources/.esapi/ESAPI.properties</span>
    <span class="changelog_message">Bring this ESAPI.properties in line
    with the one under src/main directory.</span>
  - <span class="changelog_date">2009-08-30 04:25</span>
    <span class="changelog_author">kevin.w.wall</span>
  - <span class="changelog_revision">\[\#r637 \[r637\]\]</span>
    <span class="changelog_files">src/main/java/org/owasp/esapi/reference/DefaultSecurityConfiguration.java</span>
    <span class="changelog_message">Change to make IV type case
    insensitive.
    Added comment for discussion at future code inspection.</span>
  - <span class="changelog_date">2009-09-06 19:46</span>
    <span class="changelog_author">kevin.w.wall</span>
  - <span class="changelog_revision">\[\#r641 \[r641\]\]</span>
    <span class="changelog_files">src/main/java/org/owasp/esapi/ESAPI.java</span>
    <span class="changelog_message">Changes to comments targeted for
    discussion of code inspection.</span>
  - <span class="changelog_date">2009-09-06 19:47</span>
    <span class="changelog_author">kevin.w.wall</span>
  - <span class="changelog_revision">\[\#r642 \[r642\]\]</span>
    <span class="changelog_files">src/main/java/org/owasp/esapi/Encryptor.java</span>
    <span class="changelog_message">Change signature and Javadoc for new
    encryption method. (Can't overwrite key as SecretKey.)</span>
  - <span class="changelog_date">2009-09-06 19:51</span>
    <span class="changelog_author">kevin.w.wall</span>
  - <span class="changelog_revision">\[\#r643 \[r643\]\]</span>
    <span class="changelog_files">src/main/java/org/owasp/esapi/CipherText.java</span>
    <span class="changelog_message">Removed method to obtain the nonce
    used for the MIC. (Now a private method in DefaultCipherText.).

    Many minor changes to Javadoc. Lots of other comment changes.</span>
  - <span class="changelog_date">2009-09-06 19:52</span>
    <span class="changelog_author">kevin.w.wall</span>
  - <span class="changelog_revision">\[\#r644 \[r644\]\]</span>
    <span class="changelog_files">src/main/java/org/owasp/esapi/codecs/Hex.java</span>
    <span class="changelog_message">Improved / clarified Javadoc for
    fromHex() method.</span>
  - <span class="changelog_date">2009-09-06 19:54</span>
    <span class="changelog_author">kevin.w.wall</span>
  - <span class="changelog_revision">\[\#r645 \[r645\]\]</span>
    <span class="changelog_files">src/main/resources/.esapi/ESAPI.properties</span>
    <span class="changelog_message">Added comment that AES cipher block
    size is 16 bytes. (Most block ciphers have block size of 8
    bytes.)</span>
  - <span class="changelog_date">2009-09-06 19:55</span>
    <span class="changelog_author">kevin.w.wall</span>
  - <span class="changelog_revision">\[\#r646 \[r646\]\]</span>
    <span class="changelog_files">src/test/java/org/owasp/esapi/util/ThePrefectClass.java</span>
    <span class="changelog_message">Comment change.</span>
  - <span class="changelog_date">2009-09-06 19:57</span>
    <span class="changelog_author">kevin.w.wall</span>
  - <span class="changelog_revision">\[\#r647 \[r647\]\]</span>
    <span class="changelog_files">src/test/java/org/owasp/esapi/util/ObjFactoryTest.java</span>
    <span class="changelog_message">Added new test
    (testNullorEmptyTypeName()) where typeName is null or empty
    string.</span>
  - <span class="changelog_date">2009-09-06 19:59</span>
    <span class="changelog_author">kevin.w.wall</span>
  - <span class="changelog_revision">\[\#r648 \[r648\]\]</span>
    <span class="changelog_files">src/test/java/org/owasp/esapi/util/CryptoHelperTest.java</span>
    <span class="changelog_message">New JUnit test class for unit
    testing of org.owasp.esapi.util.CryptoHelper class.</span>
  - <span class="changelog_date">2009-09-06 20:01</span>
    <span class="changelog_author">kevin.w.wall</span>
  - <span class="changelog_revision">\[\#r649 \[r649\]\]</span>
    <span class="changelog_files">src/test/java/org/owasp/esapi/util/CipherSpecTest.java</span>
    <span class="changelog_message">Added commented out line to show
    effects of CipherSpec.toString() method.
    Should probably write test for this, but no time for now.</span>
  - <span class="changelog_date">2009-09-06 20:04</span>
    <span class="changelog_author">kevin.w.wall</span>
  - <span class="changelog_revision">\[\#r650 \[r650\]\]</span>
    <span class="changelog_files">src/main/java/org/owasp/esapi/util/CryptoHelper.java</span>
    <span class="changelog_message">Bug fixes found from unit testing.
    Polish Javadoc.
    Added new method to generate a random SecretKey.</span>
  - <span class="changelog_date">2009-09-06 20:07</span>
    <span class="changelog_author">kevin.w.wall</span>
  - <span class="changelog_revision">\[\#r651 \[r651\]\]</span>
    <span class="changelog_files">src/main/java/org/owasp/esapi/util/CipherSpec.java</span>
    <span class="changelog_message">Bug fixes found from unit testing.
    Default blocksize now 16 bytes, to correspond to AES blocksize.
    Changes to some Java assertions.
    New toString() method.</span>
  - <span class="changelog_date">2009-09-06 20:10</span>
    <span class="changelog_author">kevin.w.wall</span>
  - <span class="changelog_revision">\[\#r652 \[r652\]\]</span>
    <span class="changelog_files">src/main/java/org/owasp/esapi/reference/JavaEncryptor.java</span>
    <span class="changelog_message">Bug fixes found from unit testing.
    Polish Javadoc.
    (Note: JUnit testing not complete.)</span>
  - <span class="changelog_date">2009-09-06 20:11</span>
    <span class="changelog_author">kevin.w.wall</span>
  - <span class="changelog_revision">\[\#r653 \[r653\]\]</span>
    <span class="changelog_files">src/test/java/org/owasp/esapi/reference/DefaultCipherTextTest.java</span>
    <span class="changelog_message">New JUnit test for unit testing
    org.owasp.esapi.reference.DefaultCipherText.</span>
  - <span class="changelog_date">2009-09-06 20:15</span>
    <span class="changelog_author">kevin.w.wall</span>
  - <span class="changelog_revision">\[\#r654 \[r654\]\]</span>
    <span class="changelog_files">src/main/java/org/owasp/esapi/reference/DefaultCipherText.java</span>
    <span class="changelog_message">Bug fixes found from unit testing.
    Major code reorganization to use Enum's and EnumSet's.
    Polished Javadoc and lots of other comment changes.
    Reorganized code--all private methods now at the end.
    Added public toString() method.</span>
  - <span class="changelog_date">2009-09-08 01:58</span>
    <span class="changelog_author">kevin.w.wall</span>
  - <span class="changelog_revision">\[\#r655 \[r655\]\]</span>
    <span class="changelog_files">src/main/java/org/owasp/esapi/SecurityConfiguration.java</span>
    <span class="changelog_message">Added setCipherTransformation()
    method to allow a way (albeit kludgy) to
    use an alternate cipher algorithm without having to change
    ESAPI.properties.</span>
  - <span class="changelog_date">2009-09-08 01:59</span>
    <span class="changelog_author">kevin.w.wall</span>
  - <span class="changelog_revision">\[\#r656 \[r656\]\]</span>
    <span class="changelog_files">src/main/java/org/owasp/esapi/reference/DefaultEncryptedProperties.java</span>
    <span class="changelog_message">Added TODO in setProperty()
    method.</span>
  - <span class="changelog_date">2009-09-08 01:59</span>
    <span class="changelog_author">kevin.w.wall</span>
  - <span class="changelog_revision">\[\#r657 \[r657\]\]</span>
    <span class="changelog_files">src/main/java/org/owasp/esapi/reference/DefaultSecurityConfiguration.java</span>
    <span class="changelog_message">Implemented new
    setCipherTransformation() method.</span>
  - <span class="changelog_date">2009-09-08 02:01</span>
    <span class="changelog_author">kevin.w.wall</span>
  - <span class="changelog_revision">\[\#r658 \[r658\]\]</span>
    <span class="changelog_files">src/main/java/org/owasp/esapi/reference/JavaEncryptor.java</span>
    <span class="changelog_message">Use CryptoHelper.generateSecretKey()
    to generate master secret.
    Added few comments for discussion.
    Changes and bug fixes to encrypt() and decrypt() methods,
    especially
    to deal with DES and DESede key size idiosyncrasies.</span>
  - <span class="changelog_date">2009-09-08 02:01</span>
    <span class="changelog_author">kevin.w.wall</span>
  - <span class="changelog_revision">\[\#r659 \[r659\]\]</span>
    <span class="changelog_files">src/test/java/org/owasp/esapi/AllTests.java</span>
    <span class="changelog_message">Added test suites for
    org.owasp.esapi.util classes.</span>
  - <span class="changelog_date">2009-09-08 02:02</span>
    <span class="changelog_author">kevin.w.wall</span>
  - <span class="changelog_revision">\[\#r660 \[r660\]\]</span>
    <span class="changelog_files">src/test/java/org/owasp/esapi/reference/EncryptorTest.java</span>
    <span class="changelog_message">Add some sunny day tests for new
    encryption / decryption. (Still needs work.)
    Did lots of testing of error cases while debugging but didn't codify
    into JUnit
    test cases.</span>
  - <span class="changelog_date">2009-09-08 02:03</span>
    <span class="changelog_author">kevin.w.wall</span>
  - <span class="changelog_revision">\[\#r661 \[r661\]\]</span>
    <span class="changelog_files">src/test/java/org/owasp/esapi/util/CipherSpecTest.java</span>
    <span class="changelog_message">Added suite() method.</span>
  - <span class="changelog_date">2009-09-08 02:03</span>
    <span class="changelog_author">kevin.w.wall</span>
  - <span class="changelog_revision">\[\#r662 \[r662\]\]</span>
    <span class="changelog_files">src/test/java/org/owasp/esapi/util/CryptoHelperTest.java</span>
    <span class="changelog_message">Added suite() method.</span>
  - <span class="changelog_date">2009-09-08 02:03</span>
    <span class="changelog_author">kevin.w.wall</span>
  - <span class="changelog_revision">\[\#r663 \[r663\]\]</span>
    <span class="changelog_files">src/test/java/org/owasp/esapi/util/ObjFactoryTest.java</span>
    <span class="changelog_message">Added Javadoc comments to suite()
    method.</span>
  - <span class="changelog_date">2009-09-08 02:04</span>
    <span class="changelog_author">kevin.w.wall</span>
  - <span class="changelog_revision">\[\#r664 \[r664\]\]</span>
    <span class="changelog_files">src/test/java/org/owasp/esapi/util/StringUtilsTest.java</span>
    <span class="changelog_message">Added Javadoc comments to suite()
    method.</span>
  - <span class="changelog_date">2009-09-08 02:39</span>
    <span class="changelog_author">kevin.w.wall</span>
  - <span class="changelog_revision">\[\#r665 \[r665\]\]</span>
    <span class="changelog_files">src/main/java/org/owasp/esapi/CipherText.java</span>
    <span class="changelog_message">Changes for Javadoc.</span>
  - <span class="changelog_date">2009-09-08 02:40</span>
    <span class="changelog_author">kevin.w.wall</span>
  - <span class="changelog_revision">\[\#r666 \[r666\]\]</span>
    <span class="changelog_files">src/main/java/org/owasp/esapi/Encryptor.java</span>
    <span class="changelog_message">Changes for Javadoc.</span>
  - <span class="changelog_date">2009-09-08 02:40</span>
    <span class="changelog_author">kevin.w.wall</span>
  - <span class="changelog_revision">\[\#r667 \[r667\]\]</span>
    <span class="changelog_files">src/main/java/org/owasp/esapi/ESAPI.java</span>
    <span class="changelog_message">Changes for Javadoc.</span>
  - <span class="changelog_date">2009-09-08 02:40</span>
    <span class="changelog_author">kevin.w.wall</span>
  - <span class="changelog_revision">\[\#r668 \[r668\]\]</span>
    <span class="changelog_files">src/main/java/org/owasp/esapi/StringUtilities.java</span>
    <span class="changelog_message">Changes for Javadoc.</span>
  - <span class="changelog_date">2009-09-08 02:40</span>
    <span class="changelog_author">kevin.w.wall</span>
  - <span class="changelog_revision">\[\#r669 \[r669\]\]</span>
    <span class="changelog_files">src/main/java/org/owasp/esapi/ValidationErrorList.java</span>
    <span class="changelog_message">Changes for Javadoc.</span>
  - <span class="changelog_date">2009-09-08 02:41</span>
    <span class="changelog_author">kevin.w.wall</span>
  - <span class="changelog_revision">\[\#r670 \[r670\]\]</span>
    <span class="changelog_files">src/main/java/org/owasp/esapi/reference/accesscontrol/FileBasedACRs.java</span>
    <span class="changelog_message">Changes for Javadoc.</span>
  - <span class="changelog_date">2009-09-08 02:41</span>
    <span class="changelog_author">kevin.w.wall</span>
  - <span class="changelog_revision">\[\#r671 \[r671\]\]</span>
    <span class="changelog_files">src/main/java/org/owasp/esapi/reference/DefaultCipherText.java</span>
    <span class="changelog_message">Changes for Javadoc.</span>
  - <span class="changelog_date">2009-09-08 02:41</span>
    <span class="changelog_author">kevin.w.wall</span>
  - <span class="changelog_revision">\[\#r672 \[r672\]\]</span>
    <span class="changelog_files">src/main/java/org/owasp/esapi/reference/IntegerAccessReferenceMap.java</span>
    <span class="changelog_message">Changes for Javadoc.</span>
  - <span class="changelog_date">2009-09-08 02:41</span>
    <span class="changelog_author">kevin.w.wall</span>
  - <span class="changelog_revision">\[\#r673 \[r673\]\]</span>
    <span class="changelog_files">src/main/java/org/owasp/esapi/util/CipherSpec.java</span>
    <span class="changelog_message">Changes for Javadoc.</span>
  - <span class="changelog_date">2009-09-08 02:42</span>
    <span class="changelog_author">kevin.w.wall</span>
  - <span class="changelog_revision">\[\#r674 \[r674\]\]</span>
    <span class="changelog_files">src/test/java/org/owasp/esapi/reference/SafeFileTest.java</span>
    <span class="changelog_message">Changes for Javadoc.</span>
  - <span class="changelog_date">2009-09-24 22:53</span>
    <span class="changelog_author">chrisisbeef</span>
  - <span class="changelog_revision">\[\#r676 \[r676\]\]</span>
    <span class="changelog_files">src/main/java/org/owasp/esapi/errors/EnterpriseSecurityException.java</span>
    <span class="changelog_message">Updated documentation per fortify
    scan.
    <https://owasp.fortify.com/teamserver/audit/82/index.html?id=716023303C20DF2DB1578438A33572BC&t=d>

    Intent is to make the documentation clear that when getting the user
    message when it has been set by an unknown source, or when setting
    it when creating a new instance of the exception to sanitize the
    user message to ensure that it is safe for display to the user as it
    is intended.</span>
  - <span class="changelog_date">2009-10-16 03:52</span>
    <span class="changelog_author">kevin.w.wall</span>
  - <span class="changelog_revision">\[\#r692 \[r692\]\]</span>
    <span class="changelog_files">src/main/java/org/owasp/esapi/PlainText.java</span>
    <span class="changelog_message">New class. Roughly corresponds to
    CipherText, but for plaintext; provided after discussion on
    OWASP-ESAPI mailing list.</span>
  - <span class="changelog_date">2009-10-16 03:53</span>
    <span class="changelog_author">kevin.w.wall</span>
  - <span class="changelog_revision">\[\#r693 \[r693\]\]</span>
    <span class="changelog_files">src/test/java/org/owasp/esapi/PlainTextTest.java</span>
    <span class="changelog_message">JUnit 4 test for PlainText
    class.</span>
  - <span class="changelog_date">2009-10-16 03:55</span>
    <span class="changelog_author">kevin.w.wall</span>
  - <span class="changelog_revision">\[\#r694 \[r694\]\]</span>
    <span class="changelog_files">src/main/java/org/owasp/esapi/errors/ConfigurationException.java</span>
    <span class="changelog_message">Some Javadoc changes /
    improvements.</span>
  - <span class="changelog_date">2009-10-16 03:59</span>
    <span class="changelog_author">kevin.w.wall</span>
  - <span class="changelog_revision">\[\#r695 \[r695\]\]</span>
    <span class="changelog_files">src/main/java/org/owasp/esapi/reference/LegacyJavaEncryptor.java</span>
    <span class="changelog_message">Provide "legacy" (cough, cough)
    String-based encryption / decryption methods with ESAPI Java 1.4 and
    earlier versions. Note that these methods use the cryptographically
    weak ECB cipher mode and provide no mechanism for proving
    authenticity of the ciphertext.</span>
  - <span class="changelog_date">2009-10-16 04:00</span>
    <span class="changelog_author">kevin.w.wall</span>
  - <span class="changelog_revision">\[\#r696 \[r696\]\]</span>
    <span class="changelog_files">src/test/java/org/owasp/esapi/reference/LegacyEncryptorTest.java</span>
    <span class="changelog_message">JUnit 4 test case for new
    LegacyEncryptor class.</span>
  - <span class="changelog_date">2009-10-16 04:01</span>
    <span class="changelog_author">kevin.w.wall</span>
  - <span class="changelog_revision">\[\#r697 \[r697\]\]</span>
    <span class="changelog_files">src/main/java/org/owasp/esapi/util/StringUtils.java</span>
    <span class="changelog_message">Minor Javadoc change.</span>
  - <span class="changelog_date">2009-10-16 04:04</span>
    <span class="changelog_author">kevin.w.wall</span>
  - <span class="changelog_revision">\[\#r698 \[r698\]\]</span>
    <span class="changelog_files">documentation/ESAPI_2.0_ReleaseNotes_CryptoChanges.html</span>
    <span class="changelog_message">Completed new sections of ESAPI 2.0
    crypto changes intended for release notes. Still some work left to
    do on this.</span>

[Category:OWASP Enterprise Security
API](Category:OWASP_Enterprise_Security_API "wikilink")