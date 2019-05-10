# Intro

Device cookies as additional authenticator for users devices have been
discussed and used in practice for some time already. For example, it
was discussed by Marc Heuse at
[PasswordsCon 14](http://video.adm.ntnu.no/serier/5493ea75d5589). Marc
speculates on various techniques for blocking online attacks and comes
to notion of "device cookie" as good protection alternative (see his
[talk](http://video.adm.ntnu.no/pres/549401c165887) on Hydra at
PasswordsCon 14, specifically from 32:50). As well as Alec Muffett at
the same conference mentions "datr cookie" from Facebook (look from
10:15 of his [talk](http://video.adm.ntnu.no/pres/54b660049af94)).

The main idea behind the protocol is to issue a special “device” cookie
to every client (browser) when it is used to successfully authenticate a
user in a system. The device cookie can be used to:

  - Distinguish between known/trusted and unknown/untrusted clients
  - Establish universal temporary lockouts for all untrusted clients
  - Lockout trusted clients individually.

# Why?

There are few well-known ways to [deal with online
attacks](Blocking_Brute_Force_Attacks "wikilink"):

  - Temporary account lockout
  - Use CAPTCHA to slow down attacker

Other tricks, like producing confusing answers for attacker are more
like “security by obscurity” and cannot be used as first-class
protection mechanism.

Temporary account lockout after several failed attempts is too simple of
a target for DoS attacks against legitimate users. There is variation of
this method that locks out pair of account/IP. It is better in regarding
to DoS issues but have security downsides:

  - Attacks from botnets can be effective
  - Attacks through proxies can be effective

Moreover, it is not so trivial to implement account/IP lockout. Consider
multiple proxies with chaining addresses in “X-Forwarded-For” header or
IPv6.

The method described in this writing may be viewed as variant of
account/IP blocking. But it proposes to use a browser cookie instead of
an IP address. Thus it may be more predictable from security perspective
and easier to implement.

# Protocol

Protocol parameters:

  - T - time period
  - N - max number of authentication attempts allowed during *T*

The sign ∎ hereafter states for end of algorithm.

**Entry point for authentication request**

  -
    1\. if the incoming request contains a device cookie:
      -
        a. *validate device cookie*
        b. if device cookie is not valid then proceed to step 2.
        c. if the device cookie is in the lockout list
          -
            reject authentication attempt∎
        d. else
          -
            *authenticate user*∎
    2\. if authentication from untrusted clients is locked out for the
    specific user
      -
        reject authentication attempt∎
    3\. else
      -
        *authenticate user*∎

**Authenticate user**

1.  check user credentials
2.  if credentials are valid
      -
        a. *issue new device cookie to user’s client*
        b. proceed with authenticated user
3.  else
      -
        a. *register failed authentication attempt*
        b. finish with failed user’s authentication

**Register failed authentication attempt**

1.  register a failed authentication attempt with following information:
    { user, time, device cookie (if present) }.
2.  depending on whether a valid device cookie is present in the
    request, count the number of failed authentication attempts within
    period *T* either for
      -
        a. all untrusted clients
        **or**
        b. a specific device cookie
3.  if number of failed attempts within period *T* \> *N*
      -
        a. if a valid device cookie is presented
          -
            put the device cookie into the lockout list for device
            cookies until now+*T*
        b. else
          -
            lockout all authentication attempts for a specific user from
            all untrusted clients until now+*T*

**Issue new device cookie to user’s client** Issue a browser cookie with
a value like “LOGIN,NONCE,SIGNATURE”, where

  - LOGIN - user’s login name (or internal ID) corresponding to an
    authenticated user
  - NONCE - nonce of sufficient length or random value from CSRNG source
  - SIGNATURE - HMAC(secret-key, “LOGIN,NONCE”)
  - secret-key - server’s secret cryptographic key.

**Validate device cookie**

1.  Validate that the device cookie is formatted as described above
2.  Validate that SIGNATURE == HMAC(secret-key, “LOGIN,NONCE”)
3.  Validate that LOGIN represents the user who is actually trying to
    authenticate

## Notes

  - Putting the device cookie in a lockout list has the same effect as
    if the client had no device cookie. So clients with device cookies
    are potentially allowed to make *N* \* 2 failed authentication
    attempts before actual lockout.
  - Issuing a new device cookie after each successful authentication
    allows us to avoid making decisions in situations like - “Should the
    system block a device cookie if there were registered *N*-1 failed
    attempts, then one successful authentication, and then again 1
    failed attempt? All within period *T*.”

# Implementation Tips

It is good idea to use standard format for device cookies. So, if the
size of a cookie is not an issue, it is recommended to use
[JWT](https://jwt.io/).

The following standard
[claims](https://tools.ietf.org/html/rfc7519#page-9) can be used:

  - **sub** : LOGIN
  - **jti** : NONCE

**Important**: If you already use JWT for storing session tokens or
other security stuff make sure you cannot confuse device cookies with
other types of tokens. There are two possible ways to mitigate this
threat:

1.  Use different signature / encryption keys for different token types
2.  Add **aud** claim into device cookie token that unambiguously refers
    to brute force protection subsystem (e.g. "aud" :
    "brute-force-protection" or "device cookie").

# Threat Analysis

<table>
<thead>
<tr class="header">
<th><p>style="width:20%"</p></th>
<th><p>Threat</p></th>
<th><p>style="width:40%"</p></th>
<th><p>Threat details</p></th>
<th><p>style="width:40%"</p></th>
<th><p>Mitigation</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Online attack against one user</p></td>
<td><p>Attacker performs a guessing attack against a specific account from an untrusted client(s).</p></td>
<td><p>As long as the lockout for untrusted clients blocks authN attempts for a specific user from all untrusted clients, the number of guesses is restricted with (<em>N/T</em>)*24h per day.</p>
<p>E.g. for <em>N</em> = 10 and <em>T</em> = 1h, any attacker will be limited with 240 attempts per day per user or 87600 attempts per user/year regardless of how large the botnet in his possession is.</p>
<p>If there is a <a href="http://password-policy-testing.wikidot.com/results#toc5">good password policy</a> in place that limits minimum number attempts to <a href="http://research.microsoft.com/pubs/227130/WhatsaSysadminToDo.pdf">10<sup>6</sup></a> then the targeted attack will last (on average) 5 years.</p></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>Online attack using stolen device cookies</p></td>
<td><p>Attacker performs long-running guessing attack against specific account(s) from known clients.</p>
<p>Using valid device cookies allows the attacker to scale attacks linearly, e.g. each device cookie adds extra <em>N</em> attempts per <em>T</em> for specific user.</p></td>
<td><p>There may be two ways to steal device cookies:</p>
<ul>
<li>Using physical access to a known client</li>
<li>Active attack against a remote client</li>
</ul>
<p>In both cases if the attacker can steal device cookies on a regular basis he may have enough power to steal not only device cookies but also session cookies or even passwords. However in our security model this attack is irrelevant if device cookies are adequately protected (use <strong>Secure</strong> and <strong>HttpOnly</strong> flags).</p>
<p><strong>Proposal</strong>: Accidental access to one device cookie contributes little to attack speed. Applications may implement persistent lockout for certain device cookies to address such cases. E.g. permanently lockout a device cookie after <em>N</em>*10 failed attempts.</p></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Online attack against multiple users</p></td>
<td><p>Attacker performs guessing attack against a specific number of accounts from untrusted clients.</p>
<p>Attacker may try the same password from a long list against many (all) accounts in a system without reaching <em>N</em> failed attempts per account during period <em>T</em>.</p></td>
<td><p>There is no specific mitigation for this threat in the protocol.</p>
<p>Good password policy may be a sufficient countermeasure for such attacks.</p>
<p>Additionally an application may temporarily require CAPTCHA solving for authentication from <strong>untrusted</strong> clients in case there are too many authentication attempts for different accounts during a specified period of time.</p></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>Spoof device cookie</p></td>
<td><p>Attacker may try to forge a valid device cookie for any user in a system.</p></td>
<td><p>Proper crypto implementation: HMAC and random secret key.</p></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Tamper with existing device cookie</p></td>
<td><p>Attacker may try to tamper with a device cookie valid for one user to make it suitable for another.</p></td>
<td><p>Proper crypto implementation: HMAC and random secret key.</p></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>DoS for specific account</p></td>
<td><p>Attackers may cause permanent lockout for all untrusted devices for a specific user. Thus the user may be blocked from loggging into the system as he would need to login from a <strong>new device</strong> or to login after <strong>cleaning up his browser cache</strong>.</p></td>
<td><p>Issue a valid device cookie after visiting password reset link (an actual password reset is not necessary). Thus, if the user demonstrates his possession of a personal email account then the system may trust a client to try entering his credentials.</p></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>DoS for specific account when client is used by different accounts</p></td>
<td><p>There are situations when the same client is legitimately used to authenticate different users. For example, a family-shared PC or tablet. Thus, after successful authentication of one user another legitimate user will be treated as user of untrusted client and will be susceptible to a DoS attack.</p></td>
<td><p>Cases where the same client is shared between legitimate users may be considered out of scope by default.</p>
<p>If such cases are critical for application usability, it may deal with them by issuing device cookies with names that contain LOGIN and analyze them accordingly.</p></td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>