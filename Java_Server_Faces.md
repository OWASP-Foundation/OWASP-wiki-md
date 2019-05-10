## Status

Under review 10/3/2008

## Web security.. before you start

This document is about security in web applications developed using the
Java Server Faces (JSF) framework. The reader should be aware of the
meaning of common terms of both JSF (converters, validators, managed
beans) and web security (injection etc.)

## JSF Standards and roles

JavaServer Faces (JSF) is a Java-based Web application framework that
implements the Model-View-Controller pattern and simplifies the
development of web interfaces for Java EE applications.

In a standard MVC JSF are meant to provide the V (of view) and part of
the C (of Control). JSF components can present almost any basic
interface model. The framework also provides part of the Control layer
including:

  - Navigation Handling
  - Error Handling
  - Action and event Management
  - Input validation
  - Value conversion

These elements are defined by the JSF standard (JCP 127) so that any
attacker will have knowledge of the architecture and life cycle of a JSF
based application. JSF does not implement its own security model but
instead relies on standard JEE security. This means that both
application server security model, JAAS or other ACL implementations can
be used with the JSF framework without any integration effort. But
Access Control is just one part of security - all aspects should be
implemented in a secure manner in order to consider the application
itself secure.

## Client-side state saving

A JSF application can save the state of its components in the client
response or on the server. Saving state on the client may be required
because some users turn off cookies support, but it can increase
response times when connections are slow. Saving state on the server may
have the disadvantage of high memory consumption for the user, but it
does minimize bandwidth requirements. Since client-side state saving
stores data in the client , it should be used wisely, or not used at
all. An attacker that can manipulate a user's data could manage a data
tampering or worst, a privilege escalation exploit. Unencrypted data is
quite easy to manipulate and most of the client-side saved data are
serialized Java objects which can contain a wealth of sensitive data. If
you plan to use client-side state saving carefully consider which
information you decide to store in the POJO/DTO in order to minimise
these risks.

## Components

### Converters

Converter could be a source of threat since it converts string in Java
objects. An attacker could inject malicious code or tampered data to
make the converter itself misbehave and expose protected data. The
converter system is not insecure by itself, but conversion, since it is
a security touch point for business logic and persistent data, should be
handled carefully. Input should **always** be validated **after** being
converted. In JSF lingo you should **always** have a validator if a
conversion occurs. See next section on how to implement a security aware
validator.

### Validators

Validation is your chance to verify that the input is as expected. This
means that the input should be validated both from a domain view and
from a security view. If input represents a string that in your domain
should be from 10 to 254 characters long, the same string should be
validated also to prevent SQL Injection and XSS attacks. Since many
security checks are done using dictionary algorithms it's useful to have
a validator that implements those checks and extends it to implement
your domain validator. For example:

`public class TenToHundredsValidator extends SecureValidator() {`
`   public void validate(...) {`
`      `
`      super.validate(...); // Do security checks`
`      `
`      domainvalidate(....);`
`   }`
`}          `
`  `

### ManagedBeans

Managed beans are the gears of JSF based application. Developers can
access FacesContext statically and this is potentially dangerous. This
is a common short cut for everything in the JSF layer, but manipulating
this data could be harmful. Relying on security principals, and software
engineering, is always a good approach. Calls such as:

`   FacesContext.getCurrentInstance().getExternalContext().getRequestParameter("name")`

are dangerous because the whole validation stack is bypassed. You can
read parameters but consider them as tainted input. Use Validators
described above also if you are not in the validation phase . Validators
are also an effective way to refactor your validation code and to
prevent code repetition. FacesContext also allows access to user
principal data; this data could be used to verify if the current user
can actually execute the business logic in the managed Bean. This
practice should be adopted in favour of rendering or not the
commandLinks that lead to the action of the managed Bean. A structured
adoption of an execution based security framework , such as ACEGI (see
the Appendix), could be a good enforcement of the security of the
managed bean.

### Custom components

If the use of custom components is required in the application, the
security depends on how the components are developed. Third party
components should be delivered with a security report and support from
the specific vendor or community. If you develop custom components you
should be aware of the same old security issues of web development:

  - Do not trust request parameter
  - Do not trust cookies
  - Always consider that session could be hijacked

Since the component tree is assembled server side it can be trusted so
if your custom component needs to read data from a sibling component it
should be considered a safe operation although you will have to make
assumptions on element names of the tree.

## Implementations

Since more than one JSF Implementation exists, bugs of the
implementation should be first on the security list.

### MyFaces

There aren't major or critical security bugs registered in the current
stable release of MyFaces (1.1.5). Client state saving is still the weak
point and should be used wisely. My Faces comes also with a Security
Extension (http://wiki.apache.org/myfaces/SecurityContext) that allows
to safely and easily retrieve authenticated user details.

The MyFaces resource filter could be a source of threat. It is designed
to expose resources from a jar file and could therefore, be considered,
potentially dangerous. Note there aren't any claimed security flaws nor
exploits in the resource filter, but the nature of this component makes
it a good target for attackers. Since all it has to do is serve data it
is recommended that a dispatcher be added to the filter mapping element.
This should lower the possibility of an attacker successfully
manipulating the server request. For more information see:
<http://myfaces.apache.org/tomahawk/extensionsFilter.html>

There is also an easy way to enable encryption when using *client save
state*

`   `<context-param>
`       `<param-name>`org.apache.myfaces.secret`</param-name>
`       `<param-value>`NzY1NDMyMTA=`</param-value>
`   `</context-param>

Supported encryption methods are BlowFish, 3DES, AES and are definde bya
a context parameter

`   `<context-param>
`       `<param-name>`org.apache.myfaces.algorithm`</param-name>
`       `<param-value>`Blowfish`</param-value>
`   `</context-param>

You can find more info at
<http://wiki.apache.org/myfaces/Secure_Your_Application>

### SUN Reference Implementation

Quoting from the documentation: *There are several ways for a web
application to store session state on the client tier. One possible
solution is to use Cookies to store the state on the client. However,
cookies have limitations in size and are not ideal in cases where you
want to store session state on the client. The state that needs to be
stored on the client is first serialized into a byte array. This byte
array is then encrypted using industrial-strength 3DES with
cipher-block-chaining (CBC) and an initialization vector. To make the
content tamper-resistant, we then create a message authentication code
(using SHA1 algorithm) from the encrypted content and the initialization
vector. The initialization vector, the message authentication code, and
the encrypted content is then combined in a single byte array. Finally,
this resulting byte array is converted into a base64 string which is
stored in a hidden FORM field on the client. This solution is secure
because it uses a strong crypto algorithm and also uses a MAC for
tamper-resistance. We also generate all the random numbers (for example,
to generate the initialization vectors and the password) using the
cryptographically-secure SecureRandom class. Note that the encryption
keys are NEVER sent to the client or sent on the wire. These keys are
used only on the server-side to encrypt and decrypt the state. One
challenge is to decide what encryption keys to use. The encryption keys
should not be known to the client, but still be associated with the
client. We solve this problem by generating these keys from a password
that is generated randomly and stored in the HttpSession. This strategy
for key generation through password is pluggable in our solution and can
be changed if needed.*

### ICE Faces

Starting from the idea that AJAX on Its Own Doesn't Corrupt Web Security
ICE faces implements a component suite with ajax support by maintainig a
continuous sync between the dom sent to the browser and a dom
representation on the server. javascript is used to send commands to the
server and invoke the logic in the java layer. Since dom model and
javascript is involved a Javascript debugging tool with value injection
or dom injection capability could be of some use in pick locking the
app.

As stated in ICEFaces manual " the client is untrusted, SO DON'T TRUST
IT\!\!" : it means that is up to the application designer to implement a
robust security logic behind the scenes. In another point of view the
developer could focus on implementing server side security since with
the server-side-dom architecture the thin client is even thinner.

The component that refresh the two dom , called IntervalRenderer, uses a
persistent ServletRequest stored on the server. Unfortunately, this
request does not contain sufficient information to perform the
isUserInRole() check. This kind of check is possible only on stadar
render request phase.

To address this, a small amount of integration will be required either
between ICEfaces and acegi-security or ICEfaces and the application
server. Acegi-security (see appendix one ) is likely preferable as it
will be more portable.

## Apendix I

### ACEGI Integration

Acegi Security is a powerful, flexible security solution for enterprise
software, with a particular emphasis on applications that use Spring. If
used in combination with jsf, the managed beans could become more
"security aware" since acegi do not only perform authentication but also
authorization in business layer. Acegi is a convenient way to manage
security in all the layers of our application. This is a valuable thing
especially when authorization is strongly coupled with business logic
(approval work flows etc).

In order to use a custom JSF-Acegi login we have to provide a valid
Security Context (*userName* and *password* are properties of the
managed bean)

`UsernamePasswordAuthenticationToken authReq = new UsernamePasswordAuthenticationToken(userName, password);`
`Authentication auth = getAuthenticationManager().authenticate(authReq);`
`SecurityContext secCtx = SecurityContextHolder.getContext();`
`secCtx.setAuthentication(auth);`

We can override the standard ACEGI navigation with custom, logic driven,
navigation reading security context and routing the outcome.

More information can be found at here
[1](http://www.javakaffee.de/blog/2006/07/04/jsfacegi-authentication-with-a-backing-bean/)

ACEGI can be integrated also in the rendering via custom components
[2](http://cagataycivici.wordpress.com/2006/01/19/acegi_jsf_components_hit_the/)
which basically wrap the standard ACEGI tag library in JSF components.
This conveniently solve the *stage zero* of profiling: display or not a
widget in the page.

Including a JSF based form for login in a page could be a little tricky,
bu using MyFaces tomahawk components it can be done easely.

The form will look like

`<%@ taglib uri="`<http://myfaces.apache.org/tomahawk>`" prefix="t"%>`
<t:inputText id="j_username" forceId="true" value="#{backingBean.customerId}" size="40" maxlength="80"></t:inputText>
<t:inputSecret id="j_password" forceId="true" value="#{backingBean.password}" size="40" maxlength="80" redisplay="true"></t:inputSecret>
<h:commandButton action="login" value="#{messages.page_signon}"/>
<h:messages id="messages" layout="table" globalOnly="true" showSummary="true" showDetail="false"/>

A navigation rule to follow ACEGI requirements

<navigation-rule>
`       `<from-view-id>`/login.jsp`</from-view-id>
`       `<navigation-case>
`               `<from-outcome>`login`</from-outcome>
`               `<to-view-id>`/j_acegi_security_check.jsp`</to-view-id>
`       `</navigation-case>
</navigation-rule>

And finaly ACEGI is told which page do the login

<bean id="formAuthenticationProcessingFilter" class="org.acegisecurity.ui.webapp.AuthenticationProcessingFilter">
`       `<property name="filterProcessesUrl">
`               `<value>`/j_acegi_security_check.jsp`</value>
`       `</property>
`       `<property name="authenticationFailureUrl">
`               `<value>`/login.faces`</value>
`       `</property>
`       ...`

[Category:Java](Category:Java "wikilink")