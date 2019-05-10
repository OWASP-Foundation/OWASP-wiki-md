    This document is currently under development - Please use the Discussion page for threaded conversation

# Proposed Migration Roadmap

  - ESAPI 2.1
      - Create new package **org.owasp.esapi.core**
      - Create new set of Interfaces in new package with each extending
        it's **org.owasp.esapi** counterpart
      - Deprecate methods in **org.owasp.esapi** Interfaces
  - ESAPI 2.5
      - Remove deprecated methods that were deprecated at or before
        ESAPI 2.0
      - Introduce new ServiceLocator API
  - ESAPI 3.0
      - Seperate Core API into it's own artifact/project called
        ESAPI-Core
      - Create new set of artifacts as outlined in
        [ESAPI_Project_Structure](ESAPI_Project_Structure "wikilink")
      - Introduce Core API Testing Suite

# Core API Specification

## AccessController

The AccessController is responsible for determining if the currently
logged in user has access to a given resource. The resource can be
anything that implements the [Resource](#Resource "wikilink") Interface.

### Changes from ESAPI 2.0

  - Removed deprecated methods
  - Added Generic Stereotypes to the Resource and Context parameters)

### StereoTypes

| Parameter | Description                                                                                                                                                 |
| --------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------- |
| R         | A class that implements the [Resource](#Resource "wikilink") Interface and represents the [Resource](#Resource "wikilink") the user is requesting access to |
| Context   | Any object that represents the current context of the Authorization request - this is generally a Key-Value map                                             |

### Methods

#### \<R extends Resource,Context\> void assertAuthorized(Resource resource, Context context) throws AccessDeniedException

Assert that the currently logged in user can access the given
[Resource](#Resource "wikilink") with the given Context parameters

##### Parameters

| Parameter | Default Value | Description                                                                                                                                                                       |
| --------- | ------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| resource  |               | The resource that the user is attempting to access                                                                                                                                |
| context   |               | The context of the request. This could be any type of object - for instance if requesting access to data, the context may be the resource identifier for the identified resource. |

##### Exceptions

| Exception                                                  | Description                                                                                                                                |
| ---------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------ |
| [AccessDeniedException](#AccessDeniedException "wikilink") | If the assertion evaluates to false, an AccessControlException will be thrown with contextual information as to the reason for the failure |

#### \<R extends Resource,Context\> boolean isAuthorized(Resource resource, Context context)

Determine if the given resource is accessible by the currently logged in
[User](#User "wikilink")

##### Parameters

| Parameter | Default Value | Description                                                                                                                                                                       |
| --------- | ------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| resource  |               | The resource that the user is attempting to access                                                                                                                                |
| context   |               | The context of the request. This could be any type of object - for instance if requesting access to data, the context may be the resource identifier for the identified resource. |

##### Return

Returns true if the resource is accessible to the currently logged in
user and false if it is not.

## AccessReferenceMap<Key>

The AccessReferenceMap interface is used to map from a set of internal
direct object references to a set of indirect references that are safe
to disclose publicly. This can be used to help protect database keys,
filenames, and other types of direct object references. As a rule,
developers should not expose their direct object references as it
enables attackers to attempt to manipulate them.

Indirect references are handled as strings, to facilitate their use in
HTML. Implementations can generate simple integers or more complicated
random character strings as indirect references. Implementations should
probably add a constructor that takes a list of direct references.

Note that in addition to defeating all forms of parameter tampering
attacks, there is a side benefit of the AccessReferenceMap. Using random
strings as indirect object references, as opposed to simple integers
makes it impossible for an attacker to guess valid identifiers. So if
per-user AccessReferenceMaps are used, then request forgery (CSRF)
attacks will also be prevented.

### StereoTypes

| Parameter | Description                                                   |
| --------- | ------------------------------------------------------------- |
| Key       | The type of object to use for a key in the AccessReferenceMap |

### Methods

#### <Type> Key addDirectReference(Type direct)

Adds a direct reference to the AccessReferenceMap, then generates and
returns an associated indirect reference.

##### StereoTypes

| Parameter | Description                       |
| --------- | --------------------------------- |
| Type      | The type for the direct reference |

##### Parameters

| Parameter | Default Value | Description          |
| --------- | ------------- | -------------------- |
| direct    |               | The direct reference |

##### Return

The key for the added Direct Reference

#### <Type> Type getDirectReference(Key key)

Get the original direct object reference from an indirect reference.
Developers should use this when they get an indirect reference from a
request to translate it back into the real direct reference. If an
invalid indirect reference is requested, then an AccessControlException
is thrown. If a type is implied the requested object will be cast to
that type, if the object is not of the requested type, a
AccessControlException will be thrown to the caller.

##### StereoTypes

| Parameter | Description                       |
| --------- | --------------------------------- |
| Type      | The type for the direct reference |

##### Parameters

| Parameter | Default Value | Description            |
| --------- | ------------- | ---------------------- |
| key       |               | The indirect reference |

##### Return

The direct reference

##### Exceptions

| Exception                                                  | Description                                                                 |
| ---------------------------------------------------------- | --------------------------------------------------------------------------- |
| [AccessDeniedException](#AccessDeniedException "wikilink") | If the requested reference does not exist or the implied type is incorrect. |

#### <Type> Key getIndirectReference(Type directReference)

Get a safe indirect reference to use in place of a potentially sensitive
direct object reference.

##### StereoTypes

| Parameter | Description                       |
| --------- | --------------------------------- |
| Type      | The type for the direct reference |

##### Parameters

| Parameter | Default Value | Description          |
| --------- | ------------- | -------------------- |
| direct    |               | The direct reference |

##### Return

The indirect reference

#### <Type> Key removeDirectReference(Type directReference)

Removes a direct reference and its associated indirect reference from
the AccessReferenceMap.

#### <Type> void update(Set<Type> directReferences)

Updates the access reference map with a new set of direct references,
maintaining any existing indirect references associated with items that
are in the new list.

## Authenticator

### Methods

#### User login() throws AuthenticationException

#### void logout() throws AuthenticationException

## Codec

### Methods

#### String encode(char c)

#### String decode(String s)

## Encoder

### Methods

#### String encode(String s)

#### String decode(String s)

#### void addCodec(Codec c)

#### Set<Codec> getCodecs()

#### void setCodecs(Set<Codec> codecs)

## Encryptor

### Methods

#### PlainText decrypt(CipherText cipherText, SecretKey secretKey) throws EncryptionException

#### CipherText encrypt(PlainText plainText, SecretKey secretKey) throws EncryptionException

#### MessageDigest hash(PlainText plainText, Salt salt, Integer iterations) throws EncryptionException

#### String seal(String data, Long timestamp) throws EncryptionException

#### String sign(String data) throws EncryptionException

#### String unseal(String sealedData) throws EncryptionException

#### void verifySeal(String sealedData) throws DataIntegrityException

#### void verifySignature(String signature, String data) throws InvalidSignatureException

## Executor

### Methods

#### ExecutorResult executeSystemCommand(ExecutorTarget target, Encoder encoder) throws ExecutionException

## ExecutorResult

### Methods

#### String getErrorOutput()

#### String getStandardOutput()

#### Integer getExitValue()

## ExecutorTarget

### Methods

#### *native* FileHandle getExecutable()

#### *native* Handle getWorkingDirectory()

#### OrderedMap\<String,String\> getParameters()

## IntrusionDetector

### Methods

#### void addEvent(String eventName, String message)

#### void addException(Throwable exception)

## LogFactory

Still thinking this one through

## Logger

Still thinking this one through

## Randomizer

### Methods

#### Boolean getRandomBoolean()

#### Byte\[\] getRandomBytes(Integer len)

#### String getRandomFilename(String extension)

#### String getRandomUUID()

#### Integer getRandomInteger(Integer min, Integer max)

#### Long getRandomLong(Long min, Long max)

#### Float getRandomReal(Float min, Float max)

\==== String getRandomString(Integer len, char\[\] charSet=) ===

## Resource

Marker Interface for Resources that a user can request access to.

## ServiceLocator

## User

### Methods

#### <Type> Type getAccountID()

#### String getAccountName()

#### Long getExpirationTime()

#### Integer getFailedLoginCount()

#### Long getLastFailedLoginTime()

#### String getLastHostAddress()

#### Long getLastLoginTime()

#### Long getLastPasswordChangeTime()

#### String getLocale()

#### Set<String> getRoles()

#### String getScreenName()

#### Boolean isAnonymous()

#### Boolean isEnabled()

#### Boolean isExpired()

#### Boolean isInRole(String role)

#### Boolean isLocked()

#### Boolean isLoggedIn()

## Validator

### Methods

#### <Type> Boolean isValid(Type data)

#### <Type> void assertValid(Type data)

## Exceptions

### AccessDeniedException

### AccountDisabledException

### AccountLockedException

### AuthenticationException

### EncodingException

### EncryptionException

### EnterpriseSecurityException

### EnterpriseSecurityRuntimeException

### ExecutionException

### IncorrectCredentialsException

# Web API Specification

This API describes the components that can be used in the context of a
Web Application.

## ClientCookie

### Methods

#### String getName()

#### void setName(String name)

#### String getValue()

#### void setValue(String value)

#### Integer getMaxAge()

#### void setMaxAge(Integer maxAge)

#### String getDomain()

#### void setDomain(String domain)

#### String getPath()

#### void setPath(String path)

#### Boolean isHttpOnly()

#### void setHttpOnly(Boolean httpOnly)

#### Boolean isSecure()

#### void setSecure(Boolean secure)

## SecureHttpRequest

### Methods

#### void assertSecureChannel()

#### void assertSecureRequest()

#### ClientCookie getCookie(String name)

#### List<FileHandle> getFileUploads()

#### <T> T getAttribute(String name)

#### String getHeader(String header)

#### String getParameter(String name)

#### void sendForward(String url)

#### void verifyCsrfToken() throws CsrfException

## SecureHttpResponse

### Methods

#### void addCookie(ClientCookie cookie)

#### void addHeader(String key, String value)

#### void killCookies()

#### void sendRedirect(String url)

#### void setContentType(String contentType)

#### void setNoCacheHeaders()

## SecureHttpSession

### Methods

#### <T> T getAttribute(String key)

## URLResource

### Extends

  - [Resource](#Resource "wikilink")

### Methods

## WebUser

### Methods

#### String getCsrfToken()

#### void resetCsrfToken()

#### void addSession(SecureHttpSession session)

#### void removeSession(SecureHttpSession session)

# Mobile API Specification

# Desktop API Specification

[Category:OWASP Enterprise Security
API](Category:OWASP_Enterprise_Security_API "wikilink")