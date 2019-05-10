# Session Management

A web session is a sequence of network HTTP request and response
transactions associated to the same user. Session management or state is
needed by web applications that require the retaining of information or
status about each user for the duration of multiple requests. Therefore,
sessions provide the ability to establish variables – such as access
rights and localization settings – which will apply to each and every
interaction a user has with the web application for the duration of the
session.

Code reviewer needs to understand what session techniques the developers
used, and how to spot vulnerabilities that may create potential security
risks.

Web applications can create sessions to keep track of anonymous users
after the very first user request. An example would be maintaining the
user language preference. Additionally, web applications will make use
of sessions once the user has authenticated. This ensures the ability to
identify the user on any subsequent requests as well as being able to
apply security access controls, authorized access to the user private
data, and to increase the usability of the application. Therefore,
current web applications can provide session capabilities both pre and
post authentication.

![Session-Management-Diagram_Cheat-Sheet.png](Session-Management-Diagram_Cheat-Sheet.png
"Session-Management-Diagram_Cheat-Sheet.png")
The session ID or token binds the user authentication credentials (in
the form of a user session) to the user HTTP traffic and the appropriate
access controls enforced by the web application. The complexity of these
three components (authentication, session management, and access
control) in modern web applications, plus the fact that its
implementation and binding resides on the web developer’s hands (as web
development framework do not provide strict relationships between these
modules), makes the implementation of a secure session management module
very challenging.

The disclosure, capture, prediction, brute force, or fixation of the
session ID will lead to session hijacking (or sidejacking) attacks,
where an attacker is able to fully impersonate a victim user in the web
application. Attackers can perform two types of session hijacking
attacks, targeted or generic. In a targeted attack, the attacker’s goal
is to impersonate a specific (or privileged) web application victim
user. For generic attacks, the attacker’s goal is to impersonate (or get
access as) any valid or legitimate user in the web application.

With the goal of implementing secure session IDs, the generation of
identifiers (IDs or tokens) must meet the following properties:

1.  The name used by the session ID should not be extremely descriptive
    nor offer unnecessary details about the purpose and meaning of the
    ID.
2.  It is recommended to change the default session ID name of the web
    development framework to a generic name, such as “id”.
3.  The session ID length must be at least 128 bits (16 bytes) (The
    session ID value must provide at least 64 bits of entropy).
4.  The session ID content (or value) must be meaningless to prevent
    information disclosure attacks, where an attacker is able to decode
    the contents of the ID and extract details of the user, the session,
    or the inner workings of the web application.
5.  It is recommended to create cryptographically strong session IDs
    through the usage of cryptographic hash functions such as SHA1 (160
    bits).

## Recommendation: Require cookies.

Require cookies when your application includes authentication. Code
reviewer needs to understand what information is stored in the
application cookies. Risk management is needed to address if sensitive
information is stored in the cookie requiring SSL for the cookie

### .Net ASPX

The following example shows how to specify in the Web.config file that
Forms Authentication requires a cookie that is transmitted over SSL.

<authentication mode="Forms">
` `<forms loginUrl="member_login.aspx"
    cookieless="UseCookies"
    requireSSL="true"
    path="/MyApplication" />
</authentication>

The ASP.NET session identifier is a randomly generated number encoded
into a 24-character string consisting of lowercase characters from a to
z and numbers from 0 to 5.

The SessionID value by default is sent in a cookie with each request to
the ASP.NET application.

## Custom Session frameworks

Web development frameworks, such as J2EE, ASP .NET, PHP, and others,
provide their own session management features and associated
implementation. It is recommended to use these built-in frameworks
versus building a home made one from scratch, as they are used worldwide
on multiple web environments and have been tested by the web application
security and development communities over time.

This code shows a developer who is replacing the default session
management in .Net with his own custom class. The secure code reviewer
needs to understand why a custom session class is being used and if if a
risk assessment has been done on the custom session management class.

### .Net ASPX

<httpModules>
` `<remove name="SessionID" />
` `<add name="SessionID"
       type="Samples.AspNet.Session.GuidSessionIDManager" />
</httpModules>

### PHP

In PHP, a session handled by cookies is created when
[session_start()](http://php.net/manual/en/function.session-start.php)
is called. All security related options for session cookies are in PHP's
configuration file php.ini and can be also be set with
[session_set_cookie_params()](http://php.net/manual/en/function.session-set-cookie-params.php).

`session.use_cookies = 1`
`session.use_only_cookies = 1`
`session.cookie_httponly = 1`
`session.cookie_secure = 1`

See <http://php.net/manual/en/session.configuration.php> for more
information.

## Session Expiration

In review session handling code the reviewer needs to understand what
expiration timeouts are needed by the web application or if default
session timeout are being used. Insufficient session expiration by the
web application increases the exposure of other session-based attacks,
as for the attacker to be able to reuse a valid session ID and hijack
the associated session, it must still be active. Remember for secure
coding one of our goals is to reduce the attack surface of our
application.

### .Net ASPX

ASPX the developer can change the default time out for a session. This
code in the web.config file sets the timeout session to 15 minutes. The
default timeout for a aspx session is 30 minutes.

<configuration>
` <system.web>`
`   `<sessionState
      mode="InProc"
      cookieless="true"
      timeout="15" />
` </system.web>`
</configuration>

## Session Logout/Ending.

Web applications should provide mechanisms that allow security aware
users to actively close their session once they have finished using the
web application.

.Net ASPX Session.Abandon() method destroys all the objects stored in a
Session object and releases their resources. If you do not call the
Abandon method explicitly, the server destroys these objects when the
session times out. You should use it when the user logs out.
Session.Clear() Removes all keys and values from the session. Does not
change session ID. Use this command if you if you don't want the user to
relogin and reset all the session specific data.

## Session Attacks

Generally three sorts of session attacks are possible:

1.  Session Hijacking: stealing someone's session-id, and using it to
    impersonate that user.
2.  Session Fixation: setting someone's session-id to a predefined
    value, and impersonating them using that known value
3.  Session Elevation: when the importance of a session is changed, but
    its ID is not.

## Session Hijacking

1.  Mostly done via XSS attacks, mostly can be prevented by HTTP-Only
    session cookies (unless Javascript code requires access to them).
2.  (charly proposes to eliminate this...) It's generally a good idea
    for Javascript not to need access to session cookies, as preventing
    all flavors of XSS is usually the toughest part of hardening a
    system.
3.  Session-ids should be placed inside cookies, and not in URLs. URL
    informations are stored in browser's history, and HTTP Referrers,
    and can be accessed by attackers.
4.  (...and add this) As cookies can be accessed by default from
    javascript and preventing all flavors of XSS is usually the toughest
    part of hardening a system, there is an attribute called "HTTPOnly",
    that forbids this access. The session cookie should has this
    attribute set. Anyway, as there is no need to access a session
    cookie from the client, you should get suspicious about client side
    code that depends on this access.
5.  Geographical location checking can help detect simple hijacking
    scenarios. Advanced hijackers use the same IP (or range) of the
    victim.
6.  An active session should be warned when it is accessed from another
    location.
7.  An active users should be warned when s/he has an active session
    somewhere else (if the policy allows multiple sessions for a single
    user).

## Session Fixation

1.  If the application sees a new session-id that is not present in the
    pool, it should be rejected and a new session-id should be
    advertised. This is the sole method to prevent fixation.
2.  All the session-ids should be generated by the application, and then
    stored in a pool to be checked later for. Application is the sole
    authority for session generation.

## Session Elevation

1.  Whenever a session is elevated (login, logout, certain
    authorization), it should be rolled.
2.  Many applications create sessions for visitors as well (and not just
    authenticated users). They should definitely roll the session on
    elevation, because the user expects the application to treat them
    securely after they login.
3.  When a down-elevation occurs, the session information regarding the
    higher level should be flushed.
4.  Sessions should be rolled when they are elevated. Rolling means that
    the session-id should be changed, and the session information should
    be transferred to the new id.

## Server-Side Defenses for Session Management.

### .NET ASPX

### Generate a new session ID

Generating new session Id's helps prevent, session rolling, fixation,
hijacking.

`public class GuidSessionIDManager : SessionIDManager {`
`   public override string CreateSessionID(HttpContext context){`
`return Guid.NewGuid().ToString();`
`   }`
`   public override bool Validate(string id) {`
`try{`
`       Guid testGuid = new Guid(id);`
`       if (id == testGuid.ToString())`
`         return true;`
`     }catch(Exception e) { throw e }`
`     return false;`
`   }`
` }`