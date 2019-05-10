## Brief Summary

A race condition is a flaw that produces an unexpected result when the
timing of actions impact other actions. An example may be seen on a
multithreaded application where actions are being performed on the same
data. Race conditions, by their very nature, are difficult to test for.

## Description of the Issue

Race conditions may occur when a process is critically or unexpectedly
dependent on the sequence or timings of other events. In a web
application environment, where multiple requests can be processed at a
given time, developers may leave concurrency to be handled by the
framework, server, or programming language. The following simplified
example illustrates a potential concurrency problem in a transactional
web application and relates to a joint savings account in which both
users (threads) are logged into the same account and attempting a
transfer.

Account A has 100 credits.
Account B has 100 credits.

Both User 1 and User 2 want to transfer 10 credits from Account A to
Account B. If the transaction was correct the outcome should be:

Account A has 80 credits.
Account B has 120 credits.

However, due to concurrency issues, the following result could be
obtained:

User 1 checks the value of Account A (=100 credits)
User 2 checks the value of Account A (=100 credits)
User 2 takes 10 credits from Account A (=90 credits) and put it in
Account B (=110 credits)
User 1 takes 10 credits from Account A (Still believed to contain 100
credits) (=90 credits) and puts it into Account B (=120 credits).

Result: Account A has 90 credits.
Account B has 120 credits.

Another example can be seen in OWASP's WebGoat project in the Thread
Safety lesson, and shows how a shopping cart can be manipulated to
purchase items for less than their advertised price. This, as with the
example above, is due to the data changing between the time of check and
its time of use.

## Black Box testing and example

Testing for race conditions is problematic due to their nature, and
external influences on testing including server load, network latency,
etc. will all play a part in the presence and detection of the
condition.

However, testing can be focused on specific transactional areas of the
application, where time-of-read to time-of-use of specific data
variables could be adversely affected by concurrency issues.

Black Box testing attempts to force a race condition may include the
ability to make multiple simultaneous requests while observing the
outcome for unexpected behavior.

Examples of such areas are illustrated in the paper "On Race
Vulnerabilities in Web Applications", cited in the further reading
section. The authors suggest that it may be possible in certain
circumstances to:

  - Create multiple user accounts with the same username.
  - Bypass account lockouts against brute forcing.

Testers should be aware of the security implications of race conditions
and their factors surrounding their difficulty of testing.

## Gray Box testing and example

Code review may reveal likely areas of concern for concurrency issues.
More information on reviewing code for concurrency issues can be seen at
OWASP Code Review Guide's [Reviewing Code for Race
Conditions](Reviewing_Code_for_Race_Conditions "wikilink")

## References

iSec Partners - Concurrency attacks in Web Applications
<http://isecpartners.com/files/iSEC%20Partners%20-%20Concurrency%20Attacks%20in%20Web%20Applications.pdf>
B. Sullivan and B. Hoffman - Premature Ajax-ulation and You
<https://www.blackhat.com/presentations/bh-usa-07/Sullivan_and_Hoffman/Whitepaper/bh-usa-07-sullivan_and_hoffman-WP.pdf>
Thread Safety Challenge in WebGoat -
<http://www.owasp.org/index.php/OWASP_WebGoat_Project>
R. Paleari, D. Marrone, D. Bruschi, M. Monga - On Race Vulnerabilities
in Web Applications
<http://security.dico.unimi.it/~roberto/pubs/dimva08-web.pdf>