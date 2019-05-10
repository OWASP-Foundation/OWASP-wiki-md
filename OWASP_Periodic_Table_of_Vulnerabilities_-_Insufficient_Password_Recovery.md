[Return to Periodic Table Working
View](OWASP_Periodic_Table_of_Vulnerabilities#Periodic_Table_of_Vulnerabilities "wikilink")

## Insufficient Password Recovery

### Root Cause Summary

Weak password recovery processes allow stronger password authentication
schemes to be bypassed. Non-existent password recovery processes are
expensive to support or result in denial-of-service conditions.

### Browser / Standards Solution

None

### Perimeter Solution

None

### Generic Framework Solution

The framework should provide all of the following configurable options,
and require at least one of them for self-service password resets:

  - [Security
    questions](Choosing_and_Using_Security_Questions_Cheat_Sheet "wikilink")
      - Require a minimum of three different questions
      - Support configuration-based, pre-defined questions as well as
        user-defined questions
      - Store answers for each user according to the same security
        requirements as passwords (hashed with salt)
  - Email reset
      - Application emails a password reset link with an expiring nonce
        to the email address on file
  - SMS reset
      - Application sends an alphanumeric token to the cell phone number
        on file
      - The application redirects the user to a form where the token
        must be entered

While the user is authenticating via one of the above methods, the
following security principles should be applied:

  - The reset flow should never send an actual password to the user at
    any time over any channel
  - The reset form should not expose an account enumeration
    vulnerability:
      - Token-based reset forms should claim to have sent the token
        whether the account exists or not.
      - Secret-question-based reset forms should ask random questions
        (seeded with the user id so they are the same each time) if the
        account does not exist.
  - Reset tokens should only be valid for a short period of time (\<24
    hours, configurable).
  - Only the most recent reset token should be valid at any given time.
  - The reset form should only be usable for a given account once during
    any given time period (\~24 hours, configurable) in order to prevent
    denial-of-service, SMS/email bombing, and circumvention of password
    history rules.
  - The reset token should be invalidated as soon as it is used.
  - The current password should be valid until a successful reset is
    complete (also limits denial-of-service).
  - All existing sessions for the user should be automatically
    terminated when a successful reset is complete.

Once the user successfully completes the alternate channel
authentication, the framework should prompt for a new password to be
entered twice, to ensure it is correct. The user should be notified via
email or some other method whenever a successful password change takes
place.

### Custom Framework Solution

None

### Custom Code Solution

None

### Discussion / Controversy

Secret questions are fairly controversial. Email/SMS side-channel
authentication is preferred.

### References

[OWASP Forgot Password Cheat
Sheet](Forgot_Password_Cheat_Sheet "wikilink")
[OWASP Security Questions Cheat
Sheet](Choosing_and_Using_Security_Questions_Cheat_Sheet "wikilink")
\[<http://projects.webappsec.org/w/page/13246942/Insufficient%20Password%20Recovery>|
Insufficient Password Recovery (WASC)\]