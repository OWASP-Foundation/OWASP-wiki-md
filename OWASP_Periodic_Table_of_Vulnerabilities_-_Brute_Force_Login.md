[Return to Periodic Table Working
View](OWASP_Periodic_Table_of_Vulnerabilities#Periodic_Table_of_Vulnerabilities "wikilink")

## Brute Force Login

### Root Cause Summary

The application does not prevent attackers from trying many
username/password combinations in rapid succession in order to guess
account credentials.

### Browser / Standards Solution

None

### Perimeter Solution

The perimeter should detect brute force login attempts and help prevent
denial of service against the login functionality of the application.
The perimeter should signal to the application when a username or
password is under attack, and accept signals from the application when a
certain username or password has been temporarily locked out.

### Generic Framework Solution

The framework should track failed login attempts even for non-existent
accounts, so that the lockout feature doesn't expose an account
enumeration vulnerability.

The framework should track all unique accounts tried unsuccessfully for
a particular password, using a hash of the password with a static salt
as a key to prevent password exposure. When the threshold is reached,
the application should prevent all logins using that password to any
account, much like the account lockout.

The framework should be capable of sending notifications to perimeter
technologies to help enforce lockouts or global CAPTCHA.

The lockout period should only be temporary, so as to prevent long-term
denial of service against a user account. The framework should provide
an interface for an administrator or customer service representative to
white-list IPs for an account to log in from, in case of a targeted,
sustained, long-term denial of service attack against a specific user.

The framework should expose and implement configurable rules about
failed login attempts with secure defaults, including:

  - Account lockout
      - Maximum consecutive failures before account lockout (e.g. 5)
      - Initial lockout period (e.g. 5 minutes) per password and per
        user account
      - Account lockout escalation pattern (e.g. linear, geometric,
        exponential) - for instance, the lockout period might double
        after each set of consecutive failures and a different pattern
        might apply for usernames or passwords
      - Maximum lockout interval (e.g. 24 hours) to put a cap on the
        escalation pattern
      - Total number of non-existent accounts to track (allows
        operations to scale the defense based on available
        infrastructure)
      - URL/file for account lockout error message content
  - Fixed-password, variable-account attack protection
      - Total number of passwords to track (allows operations to scale
        defense based on available infrastructure)
      - Total number of unique accounts unsuccessfully attempted for a
        password before locking out the password
      - URL/file for password lockout error message content
  - CAPTCHA
      - Maximum consecutive failures before requiring CAPTCHA (e.g. 3)
      - Number of global authentication attempts per time period before
        global CAPTCHA is triggered (e.g. 1000 per minute)
      - Global CAPTCHA enforcement period after an event (e.g. 4 hours)
      - CAPTCHA(s) to be used (may select multiple for possible added
        difficulty) - should support popular CAPTCHAs in use as well as
        provide an API for custom CAPTCHAs (though not recommended)
  - Authentication delay
      - Maximum consecutive failures before enforcing an authentication
        delay (e.g. 3)
      - Delay in milliseconds between login attempts after delay is
        triggered (e.g. 2000)

### Custom Framework Solution

None

### Custom Code Solution

None

### Discussion / Controversy

Perimeter solutions can certainly independently detect brute-force login
attacks and even help enforce account lockout, but it is better to
maintain control over the lockout rules and account management within
the application.

The application may signal to the perimeter when accounts are
locked/unlocked or a global CAPTCHA is triggered so it can help prevent
a denial-of-service condition against the login functionality.

Framework and perimeter solution designers may wish to collaborate to
define an open standard for communicating information about account
lockouts, brute force attacks, and anti-automation measures.

### References

[Blocking brute force
attacks](Blocking_Brute_Force_Attacks "wikilink")
\[<http://www.captcha.net/>| The Official CAPTCHA Site\]