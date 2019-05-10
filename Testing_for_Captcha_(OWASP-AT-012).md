### WARNING: CAPTCHA protection is an ineffective security mechanism and should be perceived as a "rate limiting" protection only\!

Most current used CAPTCHA images can be easily cracked in a fully
automated way using online cracking services. Commercial services are
usually very cheap and provide a simple API for most programming
languages.
**In security critical applications** it is more suitable to use
**alternative verification channels** (SMS authentication, OTP tokens
etc).

Example of Google reCAPTCHA cracked in 7 seconds by commercial automated
cracking service:
![<File:Image2.jpeg>](Image2.jpeg "File:Image2.jpeg")
Price: US¢1.390
Uploaded: Sun Nov 17 20:03:13 2013
Solved: Sun Nov 17 20:03:23 2013
**Text: 270 35524452**

Most CAPTCHA images can be cracked in 1-15 seconds; therefore, CAPTCHA
should be perceived as a rate limiting protection only which stops the
attacker for a limited amount of time.

## Brief Summary


CAPTCHA ("Completely Automated Public Turing test to tell Computers and
Humans Apart") is a type of challenge-response test used by web
applications to ensure that the response is not generated by a
computer.

## Description of the Issue

Despite the above-described CAPTCHA weakness, it can be still used
against:

  - Automated sending of many GET/POST requests in a short time where it
    is undesirable (e.g., SMS/MMS/email flooding), CAPTCHA provides a
    rate limiting function
  - ~~[Enumeration
    attacks](https://www.owasp.org/index.php/Testing_for_user_enumeration)
    (login, registration or password reset forms are often vulnerable to
    enumeration attacks - without CAPTCHA the attacker can gain valid
    usernames, phone numbers or any other sensitive information in a
    short time)~~
  - ~~Automated creation/using of the account that should be used only
    by humans (e.g., creating webmail accounts, stop spamming)~~
  - ~~Automated posting to blogs, forums and wikis, whether as a result
    of commercial promotion, or harassment and vandalism~~
  - ~~Any automated attacks that massively gain or misuse sensitive
    information from the application~~
  - **Simple** enumeration attacks, **simple** spambots/adbots,
    **simple** DOS attacks and **less sophisticated** attackers


**Using CAPTCHAs as a CSRF protection is not recommended (because there
are stronger [CSRF
countermeasures](https://www.owasp.org/index.php/Testing_for_CSRF_\(OWASP-SM-005\)#How_to_Prevent_CSRF_Vulnerabilites)).**

## Common CAPTCHA vulnerabilities and attacks

  - **Generated CAPTCHA is weak**
      - Be aware that most current CAPTCHAs can be considered to be
        weak, and easily crackable using existing CAPTCHA cracking
        services (see below)

<!-- end list -->

  - **Client-side storage and hidden fields**
      - The value of decoded CAPTCHA is sent by the client (as a GET
        parameter or as a hidden field of POST form). This value is
        often:
          - Encrypted by a simple algorithm and can be easily decrypted
            by observing of multiple decoded CAPTCHA values
          - Hashed by a weak hash function (e.g., MD5) that can be
            easily broken

<!-- end list -->

  - **The Chosen CAPTCHA text attack**
      - Rarely CAPTCHA is verified on the client side or verified on the
        server side but generated on the client side (in javascript)
  - **Arithmetic CAPTCHAs**
      - If arithmetic questions are displayed in cleartext, it is
        trivial to bypass this CAPTCHA, just parse the HTML content,
        extract the arithmetic question and solve it
  - **Limited set CAPTCHAs**
      - If generated CAPTCHA questions have a very limited set of
        possible answers, it is trivial to gain all of them, solve and
        use them subsequently (CAPTCHA Rainbow Tables can be built using
        CAPTCHA cryptographic hashes and the corresponding solutions)

<!-- end list -->

  - **The Chosen CAPTCHA identifier attack**
      - Sometimes the application returns CAPTCHA to the user but does
        not store its ID or solution in the HTTP session (does not keep
        track of what ID of which CAPTCHA image is sent to the user).
        This ID is subsequently extracted by the application from the
        received HTTP request and then used to perform CAPTCHA solution
        lookup for verification. This behaviour can be exploited by
        solving a single CAPTCHA, recording its unique ID and then
        submitting this stored ID of the already decoded CAPTCHA over
        multiple requests (the ID of a CAPTCHA could be a hash of the
        decoded CAPTCHA or any unique identifier)

<!-- end list -->

  - **CAPTCHA fixation**
      - Exploits a potential race condition in the CAPTCHA
        implementation relying on unique IDs for finite CAPTCHA set:

<!-- end list -->

1.  Client requests a CAPTCHA from the server with a valid SESSIONID.
2.  The server picks a random CAPTCHA identifier from the finite set of
    CAPTCHAs it has.
3.  The client is redirected to another URL containing the CAPTCHA
    identifier from where the CAPTCHA should be retrieved.
4.  The client follows the redirect and requests for a CAPTCHA image
    with the given identifier.
5.  The server stores CAPTCHA identifier in the session.
6.  CAPTCHA image is returned.

<!-- end list -->

  -   - By not storing the CAPTCHA identifier in the HTTP session before
        sending the identifier to the client, the server exposes itself
        to CAPTCHA fixation attacks. An attacker can complete steps 1 to
        3 and manipulate the request in step 4 to request any CAPTCHA
        identifier for which the correct solution is already known. Once
        the attacker-supplied CAPTCHA identifier is stored inside the
        HTTP Session at step 4, the corresponding CAPTCHA solution can
        be provided to bypass the protection.

<!-- end list -->

  - **In-session CAPTCHA brute-forcing**
      - The application does not destroy the HTTP session when the given
        CAPTCHA is already solved - by re-using the session ID of a
        known CAPTCHA it is possible to bypass another CAPTCHA protected
        page

## Solution

Because the CAPTCHA cracking attacks are still improving (and will
improve in the future), CAPTCHA should be perceived **as a rate-limiting
protection only**.
If it is implemented, the following considerations should be taken into
account:

  - No CAPTCHA information (except the image itself) should be stored on
    the client side
  - The client should have no "control" over the CAPTCHA content
  - CAPTCHA images should be always randomly generated without
    possibility to perform image preprocessing, segmentation and
    classification
  - CAPTCHA images should not be reused.

## Black Box testing and example

  - Use an intercepting fault injection proxy (e.g.,
    [WebScarab](https://www.owasp.org/index.php/Category:OWASP_WebScarab_Project)
    or BurpSuite) to:
      - Identify all parameters which are sent (in addition to the
        decoded CAPTCHA value) from the client to the server in order to
        check if these parameters contain encrypted or hashed values of
        decoded CAPTCHA and CAPTCHA ID number
      - Try to send an old decoded CAPTCHA value with an old CAPTCHA ID
        (if the application accepts them, it is vulnerable to replay
        attacks)
      - Try to send an old decoded CAPTCHA value with an old session ID
        (if the application accepts them, it is vulnerable to replay
        attacks)

<!-- end list -->

  - Find out if similar CAPTCHAs have already been broken.
  - Verify if the set of possible answers for a CAPTCHA is limited and
    can be easily determined.

## Gray Box testing and example

Audit the application source code in order to reveal:

  - Used CAPTCHA implementation and version - there are many known
    vulnerabilities in widely used CAPTCHA implementations, see
    <http://osvdb.org/search?request=captcha>
  - If the application sends encrypted or hashed value from the client,
    verify if used encryption or hash algorithm is sufficiently strong

## References

**CAPTCHA decoders:**

  - (Commercial) [www.deathbycaptcha.com](http://www.deathbycaptcha.com)
  - (Commercial) [www.bypasscaptcha.com](http://www.bypasscaptcha.com)
  - (Commercial) [www.beatcaptcha.com](http://www.beatcaptchas.com)
  - (Commercial) [www.antigate.com](http://www.antigate.com)
  - (Commercial) [www.imagetyperz.com](http://www.imagetyperz.com)
  - (Commercial) [www.expertdecoders.com](http://www.expertdecoders.com)

**Analysis tools:**

  - [TesserCap](https://github.com/gursev/TesserCap)

**Articles:**

  - [Attacking CAPTCHAs for Fun and
    Profit](http://www.mcafee.com/au/resources/white-papers/foundstone/wp-attacking-captchas-for-fun-profit.pdf)
  - [Bypassing CAPTCHAs by Impersonating CAPTCHA
    Providers](http://www.mcafee.com/au/resources/white-papers/foundstone/wp-bypassing-captchas.pdf)
  - [TesserCap—A Visual CAPTCHA Solving
    Tool](http://www.mcafee.com/us/resources/white-papers/foundstone/wp-tessercap-visual-captcha-tool.pdf)
  - [CAPTCHA Re-Riding
    Attack](http://gursevkalra.blogspot.sk/2012/03/captcha-re-riding-attack.html)
  - [CAPTCHA Hax With
    TesserCap](http://gursevkalra.blogspot.sk/2011/11/captcha-hax-with-tessercap.html)
  - [Attacks Against Captcha
    Systems](http://www.slideshare.net/DefCamp/attacks-against-captchasystems)
  - [The Robustness of Google
    CAPTCHAs](http://homepages.cs.ncl.ac.uk/jeff.yan/google.pdf)