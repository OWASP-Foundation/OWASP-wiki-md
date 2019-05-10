CAPTCHA (an acronym for "**C**ompletely **A**utomated **P**ublic
**T**uring test to tell **C**omputers and **H**umans **A**part".) is an
access control technique.

CAPTCHA is used to prevent automated software from gaining access to
webmail services like Gmail, Hotmail and Yahoo to create e-mail spam,
automated postings to blogs, forums and wikis for the purpose of
promotion(commercial, and or political) or harassment and vandalism and
automated account creation.

CAPTCHA’s have proved useful and their use has been upheld in court.
Circumventing CAPTCHA has been upheld in US Courts as a violation
Digital Millennium Copyright Act anti-circumvention section 1201(a)(3)
and European Directive 2001/29/EC.

Code review of CAPTCHA’s the reviewer needs to pay attention to the
following rules to make sure the CAPTCHA is built with strong security
principals.

1.  Do not allow the user to enter multiple guesses after an incorrect
    attempt.
2.  The software designer and code review need to understand the statics
    of guessing. I.e. One CAPTCHA design shows four (3 cats and 1 boat)
    pictures, User is requested to pick the picture where it is not in
    the same category of the other pictures. Automated software will
    have a success rate of 25% by always picking the first picture.
    Second depending on the fixed pool of CAPTCHA images over time an
    attacker can create a database of correct answers then gain 100%
    access.
3.  Consider using a key being passed to the server that uses a HMAC
    (Hash-based message authentication code) the answer.

Text base CAPTCHA’s should adhere to the following security design
principals...

1.  Randomize the CAPTCHA length: Don’t use a fixed length; it gives too
    much information to the attacker.
2.  Randomize the character size: Make sure the attacker can’t make
    educated guesses by using several font sizes / several fonts.
3.  Wave the CAPTCHA: Waving the CAPTCHA increases the difficulty for
    the attacker.
4.  Don’t use a complex charset: Using a large charset does not improve
    significantly the CAPTCHA scheme’s security and really hurts human
    accuracy.
5.  Use anti-recognition techniques as a means of strengthening CAPTCHA
    security: Rotation, scaling and rotating some characters and using
    various font sizes will reduce the recognition efficiency and
    increase security by making character width less predictable.
6.  Keep the line within the CAPTCHAs: Lines must cross only some of the
    CAPTCHA letters, so that it is impossible to tell whether it is a
    line or a character segment.
7.  Use large lines: Using lines that are not as wide as the character
    segments gives an attacker a robust discriminator and makes the line
    anti-segmentation technique vulnerable to many attack techniques.

CAPTCHA does create issues for web sites that must be ADA (Americans
with Disabilities Act of 1990) compliant. Code reviewer may need to be
aware of web accessibilities and security to review the CAPTCHA
implementation where web site is required to be ADA complaint by law.

Examples of a CAPTCHA

***How do I upload an image(s)***

References:

1.  UNITED STATES of AMERICA vs KENNETH LOWSON, KRISTOFER KIRSCH, LOEL
    STEVENSON Federal Indictment. February 23, 2010. Retrieved
    2012-01-02.
2.  <http://www.google.com/recaptcha/captcha>
    [1](http://www.google.com/recaptcha/captcha)
3.  <http://www.ada.gov/anprm2010/web%20anprm_2010.htm>
    [2](http://www.ada.gov/anprm2010/web%20anprm_2010.htm)
4.  Inaccessibility of CAPTCHA - Alternatives to Visual Turing Tests on
    the Web <http://www.w3.org/TR/turingtest/>
    [](http://www.w3.org/TR/turingtest/)

**Notes from Renchie Joan...**

If we can add a small section like, what are the uses of CAPTCHA when
mapped to vulnerability categories. eg,: Since CAPTCHA is basically a
challenge-response process, it can be used an effective mechanism
against XSRF (CSRF) attack.

Or in preventing Dictionary attacks in a login screen.

Please let me know if you also think these are relevant and fit in the
scope of the guide. If yes, then we will discuss and work on it.