Here is a typical list of web application security requirements that
shows how you can use ESAPI to implement them. All the requirements that
are handled automatically by ESAPI have been left out.

# Using Security Controls

## Authentication

| ID             | width="45%" | Requirement                                                                                                                                                                       | width="45%" | Code Example |
| -------------- | ----------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------- | ------------ |
| align="center" | **AU001**   | All site interaction from page containing the login form to the page confirming logout (inclusive) must use SSL.                                                                  | TBD         |              |
| align="center" | **AU002**   | All requests for pages that require authentication shall call the `ESAPI.authenticator().login()` method.                                                                         | TBD         |              |
| align="center" | **AU003**   | The application shall provide the user with a logout link on every page that invokes the `ESAPI.authenticator().logout()` method.                                                 | TBD         |              |
| align="center" | **AU004**   | Form fields used for passwords must use `type=password` to mask the password from view.                                                                                           | TBD         |              |
| align="center" | **AU005**   | The application shall never put passwords into HTML, including repopulating form fields.                                                                                          | TBD         |              |
| align="center" | **AU006**   | The application shall use the `FIXME` to set a "remember me" cookie for automatic authentication, but only if a user specifically authorizes it.                                  | TBD         |              |
| align="center" | **AU007**   | The application shall include Javascript in all pages that protects against being nested or framed in other websites.                                                             | TBD         |              |
| align="center" | **AU008**   | The application shall reauthenticate users with `User.checkPassword()` before allowing access to sensitive transactions.                                                          | TBD         |              |
| align="center" | **AU009**   | Link and form URLs for all transactions shall be updated with the `HTTPUtilities.addCSRFToken()` method to add a CSRF token.                                                      | TBD         |              |
| align="center" | **AU010**   | All HTTP requests for transactions shall be verified using the `HTTPUtilities.verifyCSRFToken()` method to check that the request is not forged.                                  | TBD         |              |
| align="center" | **AU011**   | Account creation and registration functions should protect against automated tools.                                                                                               | TBD         |              |
| align="center" | **AU012**   | The application shall generate strong passwords for users with the `Authenticator.generateStrongPassword()` method.                                                               | TBD         |              |
| align="center" | **AU013**   | The application shall verify the strength of any user provided password with the `Authenticator.verifyPasswordStrength()` method.                                                 | TBD         |              |
| align="center" | **AU014**   | The application shall verify the strength of any user account name with the `Authenticator.verifyAccountNameStrength()` method.                                                   | TBD         |              |
| align="center" | **AU015**   | The application shall display information upon login about the last successful (`User.getLastLoginTime()`) and last failed (`User.getLastFailedLoginTime()`) login date and time. | TBD         |              |

## Session Management

| ID             | width="45%" | Requirement                                                                                                                      | width="45%" | Code Example |
| -------------- | ----------- | -------------------------------------------------------------------------------------------------------------------------------- | ----------- | ------------ |
| align="center" | **AC001**   | Only the container provided JSESSIONID should be used as a session identifier.                                                   | TBD         |              |
| align="center" | **AC001**   | Every page should contain an obvious link to the logout function.                                                                | TBD         |              |
| align="center" | **AC001**   | The JSESSIONID and any other session identifiers must never be disclosed in links, html content, log files or any other storage. | TBD         |              |
| align="center" | **AC001**   | The JSESSIONID and any other session identifiers must never be used as an identifier for any other purpose.                      | TBD         |              |
| align="center" | **AC001**   | URL rewriting must never be enabled.                                                                                             | TBD         |              |
| align="center" | **AC001**   | Call `ESAPI.authentiator().logoff()` to end the user's session.                                                                  | TBD         |              |

## Access Control

| ID             | width="45%" | Requirement                                                                                                                                                                                                            | width="45%" | Code Example |
| -------------- | ----------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------- | ------------ |
| align="center" | **AC001**   | The application shall use `assertAuthorizedForURL()` to verify authorization before allowing access to each URL.                                                                                                       | TBD         |              |
| align="center" | **AC002**   | The application shall use `assertAuthorizedForFunction()` to verify authorization before allowing access to each business function.                                                                                    | TBD         |              |
| align="center" | **AC003**   | The application shall use `assertAuthorizedForFile()` to verify authorization before allowing access to files.                                                                                                         | TBD         |              |
| align="center" | **AC004**   | The application shall use `assertAuthorizedForData()` to verify authorization before allowing access to data.                                                                                                          | TBD         |              |
| align="center" | **AC005**   | The application shall use `assertAuthorizedForService()` to verify authorization before allowing access to each backend service.                                                                                       | TBD         |              |
| align="center" | **AC006**   | The application shall use `isAuthorizedFor*` methods to verify authorization before including user interface controls in HTML output.                                                                                  | TBD         |              |
| align="center" | **AC007**   | The application shall use `AccessReferenceMap.getIndirectReference()` to reference all application objects such as filenames, directory paths, and database keys.                                                      | TBD         |              |
| align="center" | **AC008**   | The application shall prevent access to all resources that should not be directly accessed by users (such as resources, XML files, JSP files, properties) by storing them in a protected directory, such as `WEB-INF`. | TBD         |              |
| align="center" | **AC009**   | The application shall use `HTTPUtilities.sendSafeForward()` for all forwards, to ensure that they cannot be used to bypass access checks.                                                                              | TBD         |              |
| align="center" | **AC0010**  | The appplication must use only trusted data used in access control decisions.                                                                                                                                          | TBD         |              |
| align="center" | **AC0011**  | Administrative functions for the application shall be deployed as a separate application with increased authentication controls.                                                                                       | TBD         |              |

## Input Validation

| ID             | width="45%" | Requirement                                                                                                                                                               | width="45%" | Code Example |
| -------------- | ----------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------- | ------------ |
| align="center" | **AC001**   | The application shall avoid the use of hidden fields.                                                                                                                     | TBD         |              |
| align="center" | **AC001**   | The application shall avoid the use of custom cookies or other HTTP headers.                                                                                              | TBD         |              |
| align="center" | **AC001**   | The application shall add all custom cookies with `ESAPI.httpUtilities().safeAddCookie()` or `ESAPI.httpUtilities().safeSetCookie()` to ensure they are properly secured. | TBD         |              |
| align="center" | **AC001**   | The application shall perform validation at the boundary of all major application components.                                                                             | TBD         |              |
| align="center" | **AC001**   | All input must be validated against a strict whitelist pattern using the Validator.\* methods before used.                                                                | TBD         |              |
| align="center" | **AC001**   | The application shall process all requests containing file uploads with HTTPUtilities.safeFileUpload() to safely extract uploaded files from a multipart HTTP request.    | TBD         |              |
| align="center" | **AC001**   | If custom headers must be used, the HttpUtilities.safeAddHeader() and .safeSetHeader() must be used to prevent header injection.                                          | TBD         |              |
| align="center" | **AC001**   | All requests must be validated with the HTTPUtilities.validateHTTPRequest() method to ensure global whitelist character set validation on all incoming HTTP requests.     | TBD         |              |
| align="center" | **AC001**   | Ensure that all input is validated on the server, even if it has already been validated on the client.                                                                    | TBD         |              |
| align="center" | **AC001**   | All redirects must use HTTPUtilities.safeSendRedirect() to check redirect target against an allowable set or pattern for valid destinations.                              | TBD         |              |

## Encoding

| ID             | width="45%" | Requirement                                                                                                                               | width="45%" | Code Example |
| -------------- | ----------- | ----------------------------------------------------------------------------------------------------------------------------------------- | ----------- | ------------ |
| align="center" | **AC001**   | All data sent to interpreters or external systems must be encoded with the appropriate Encoder.encodeFor\*() method to prevent injection. | TBD         |              |
| align="center" | **AC001**   | The application shall use to                                                                                                              | TBD         |              |

## Data Protection

| ID             | width="45%" | Requirement                                                                                                                                               | width="45%" | Code Example |
| -------------- | ----------- | --------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------- | ------------ |
| align="center" | **AC001**   | Requests containing sensitive data should use the POST method.                                                                                            | TBD         |              |
| align="center" | **AC001**   | Pages containing sensitive data should call the \[HTTPUtilities.setCachingHeaders()\] method to set appropriate caching headers.                          | TBD         |              |
| align="center" | **AC001**   | Use the \[Encryptor.encrypt()\] method to encrypt and the \[Encryptor.decrypt()\] method to decrypt all sensitive information before storing.             | TBD         |              |
| align="center" | **AC001**   | Use the \[Encryptor.hash()\] method to generate message digests for integrity purposes.                                                                   | TBD         |              |
| align="center" | **AC001**   | Data that expires after an elapsed time should be generated with the \[Encryptor.seal()\] method and verified with the \[Encryptor.verifySeal()\] method. | TBD         |              |
| align="center" | **AC001**   | The application shall use to                                                                                                                              | TBD         |              |
| align="center" | **AC001**   | The application shall use to                                                                                                                              | TBD         |              |

| Forms containing sensitive data should include the "autocomplete=off"
attribute on the FORM tag as well as individual form elements. | The
application shall use an EncryptedProperties to store all security
relevant data, such as passwords, credentials, codes, configuration
information, addresses, etc…

## Using Services Securely

| ID             | width="45%" | Requirement                  | width="45%" | Code Example |
| -------------- | ----------- | ---------------------------- | ----------- | ------------ |
| align="center" | **AC001**   | The application shall use to | TBD         |              |

## Error Handling

| ID             | width="45%" | Requirement                  | width="45%" | Code Example |
| -------------- | ----------- | ---------------------------- | ----------- | ------------ |
| align="center" | **AC001**   | The application shall use to | TBD         |              |

## Logging and Intrusion Detection

| ID             | width="45%" | Requirement                  | width="45%" | Code Example |
| -------------- | ----------- | ---------------------------- | ----------- | ------------ |
| align="center" | **AC001**   | The application shall use to | TBD         |              |

## Secure Configuration and Deployment

| ID        | width="45%"                                                                                          | Requirement | width="45%" | Code Example |
| --------- | ---------------------------------------------------------------------------------------------------- | ----------- | ----------- | ------------ |
| **SC001** | Production code shall not contain code not intended for use, such as debug, test, and dead code.     | TBD         |             |              |
| **SC002** | The application's source code shall not contain secrets that would compromise security if disclosed. | TBD         |             |              |
| **SC003** | The application team shall run code quality tools such as FindBugs and PMD to find quality problems. | TBD         |             |              |

# Avoiding Specific Risks

## Cross Site Scripting

| ID             | width="45%" | Requirement                  | width="45%" | Code Example |
| -------------- | ----------- | ---------------------------- | ----------- | ------------ |
| align="center" | **AC001**   | The application shall use to | TBD         |              |

## Cross Site Request Forgery

| ID             | width="45%" | Requirement                  | width="45%" | Code Example |
| -------------- | ----------- | ---------------------------- | ----------- | ------------ |
| align="center" | **AC001**   | The application shall use to | TBD         |              |

## Thread Safety Problems

| ID             | width="45%" | Requirement                                                                                                                                   | width="45%" | Code Example |
| -------------- | ----------- | --------------------------------------------------------------------------------------------------------------------------------------------- | ----------- | ------------ |
| align="center" | **AC001**   | The application shall avoid the use of shared storage, such as class variables, instance variables, or singletons, in all multithreaded code. | TBD         |              |

## Denial of Service

| ID             | width="45%" | Requirement                  | width="45%" | Code Example |
| -------------- | ----------- | ---------------------------- | ----------- | ------------ |
| align="center" | **AC001**   | The application shall use to | TBD         |              |

# Banned APIs

The following calls are dangerous and should be replaces with the safer
calls provided by ESAPI.

| ID             | width="30%" | Banned Call                       | width="30%"                                                                                                                                                   | ESAPI Replacement | width="30%" | Code Example |
| -------------- | ----------- | --------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------- | ----------- | ------------ |
| align="center" | **BAN001**  | System.out.println()              | [Logger.\*](http://owasp-esapi-java.googlecode.com/svn/trunk/javadoc/org/owasp/esapi/ILogger.html)                                                            | TBD               |             |              |
| align="center" | **BAN002**  | Throwable.printStackTrace()       | [Logger.\*](http://owasp-esapi-java.googlecode.com/svn/trunk/javadoc/org/owasp/esapi/ILogger.html)                                                            | TBD               |             |              |
| align="center" | **BAN003**  | Runtime.exec()                    | [Executor.safeExec()](http://owasp-esapi-java.googlecode.com/svn/trunk/javadoc/org/owasp/esapi/IExecutor.html)                                                | TBD               |             |              |
| align="center" | **BAN004**  | Session.getId()                   | [Randomizer.getRandomString](http://owasp-esapi-java.googlecode.com/svn/trunk/javadoc/org/owasp/esapi/interfaces/IRandomizer.html) (better not to use at all) | TBD               |             |              |
| align="center" | **BAN005**  | ServletRequest.getUserPrincipal() | [Authenticator.getCurrentUser()](http://owasp-esapi-java.googlecode.com/svn/trunk/javadoc/org/owasp/esapi/IAuthenticator.html)                                | TBD               |             |              |
| align="center" | **BAN006**  | ServletRequest.isUserInRole()     | [AccessController.isAuthorized\*()](http://owasp-esapi-java.googlecode.com/svn/trunk/javadoc/org/owasp/esapi/IAccessController.html)                          | TBD               |             |              |
| align="center" | **BAN007**  | Session.invalidate()              | [Authenticator.logout()](http://owasp-esapi-java.googlecode.com/svn/trunk/javadoc/org/owasp/esapi/IAuthenticator.html)                                        | TBD               |             |              |
| align="center" | **BAN008**  | Math.Random.\*                    | [Randomizer.\*](http://owasp-esapi-java.googlecode.com/svn/trunk/javadoc/org/owasp/esapi/IRandomizer.html)                                                    | TBD               |             |              |
| align="center" | **BAN009**  | File.createTempFile()             | [Randomizer.getRandomFilename()](http://owasp-esapi-java.googlecode.com/svn/trunk/javadoc/org/owasp/esapi/IRandomizer.html)                                   | TBD               |             |              |
| align="center" | **BAN010**  | ServletResponse.setContentType()  | [HTTPUtilities.setContentType()](http://owasp-esapi-java.googlecode.com/svn/trunk/javadoc/org/owasp/esapi/IHTTPUtilities.html)                                | TBD               |             |              |
| align="center" | **BAN011**  | ServletResponse.sendRedirect()    | [HTTPUtilities.safeSendRedirect()](http://owasp-esapi-java.googlecode.com/svn/trunk/javadoc/org/owasp/esapi/IHTTPUtilities.html)                              | TBD               |             |              |
| align="center" | **BAN012**  | RequestDispatcher.forward()       | [HTTPUtilities.safeSendForward()](http://owasp-esapi-java.googlecode.com/svn/trunk/javadoc/org/owasp/esapi/IHTTPUtilities.html)                               | TBD               |             |              |
| align="center" | **BAN013**  | ServletResponse.addHeader()       | [HTTPUtilities.safeSetHeader()/safeSetHeader()](http://owasp-esapi-java.googlecode.com/svn/trunk/javadoc/org/owasp/esapi/IHTTPUtilities.html)                 | TBD               |             |              |
| align="center" | **BAN014**  | ServletResponse.addCookie()       | [HTTPUtilities.safeAddCookie()](http://owasp-esapi-java.googlecode.com/svn/trunk/javadoc/org/owasp/esapi/IHTTPUtilities.html)                                 | TBD               |             |              |
| align="center" | **BAN015**  | ServletRequest.isSecure()         | [HTTPUtilties.isSecureChannel()](http://owasp-esapi-java.googlecode.com/svn/trunk/javadoc/org/owasp/esapi/IHTTPUtilities.html)                                | TBD               |             |              |
| align="center" | **BAN016**  | Properties.\*                     | [EncryptedProperties.\*](http://owasp-esapi-java.googlecode.com/svn/trunk/javadoc/org/owasp/esapi/IEncryptedProperties.html)                                  | TBD               |             |              |
| align="center" | **BAN017**  | ServletContext.log()              | [Logger.\*](http://owasp-esapi-java.googlecode.com/svn/trunk/javadoc/org/owasp/esapi/ILogger.html)                                                            | TBD               |             |              |
| align="center" | **BAN018**  | java.security and javax.crypto    | [Encryptor.\*](http://owasp-esapi-java.googlecode.com/svn/trunk/javadoc/org/owasp/esapi/IEncryptor.html)                                                      | TBD               |             |              |
| align="center" | **BAN019**  | java.net.URLEncoder/Decoder       | [Encoder.encodeForURL()/decodeForURL()](http://owasp-esapi-java.googlecode.com/svn/trunk/javadoc/org/owasp/esapi/IEncoder.html)                               | TBD               |             |              |
| align="center" | **BAN020**  | java.sql.Statement.execute        | PreparedStatement.execute                                                                                                                                     | TBD               |             |              |
| align="center" | **BAN021**  | ServletResponse.encodeURL         | [HTTPUtilities.safeEncodeURL()](http://owasp-esapi-java.googlecode.com/svn/trunk/javadoc/org/owasp/esapi/IHTTPUtilities) (better not to use at all)           | TBD               |             |              |
| align="center" | **BAN022**  | ServletResponse.encodeRedirectURL | [HTTPUtilities.safeEncodeRedirectURL()](http://owasp-esapi-java.googlecode.com/svn/trunk/javadoc/org/owasp/esapi/IHTTPUtilities) (better not to use at all)   | TBD               |             |              |

[Category:OWASP Enterprise Security
API](Category:OWASP_Enterprise_Security_API "wikilink")