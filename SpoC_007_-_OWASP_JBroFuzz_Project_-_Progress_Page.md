JBroFuzz has reached the 50% mark in terms of development for the SpoC
007.

Tested on mac osx, win32 and a few linux flavours. Current version is
0.7. Get it from the [Download
Section](http://www.sourceforge.net/projects/jbrofuzz).

Below is a list of things completed:

`   * [Done] Open Source Tab`

Given a domain name, by submitting five google searches, JBroFuzz will
yield back the corresponding email addresses available for that domain.
This is really useful for enumerating or recovering valid username
formats, etc.

`   * [Done] TCP Fuzzing tab allowing graph outputs`

Once fuzzing has been performed on any interface, a user can select the
Bro button in order to get a normalised plot of the fuzzing responses
obtained. This is really useful in terms of minimising time to analyse
any results.

`   * [Done] TCP Sniffing tab update thread Agent Queue`

TCP Sniffing has become more robust. A complete re-write of how
exceptions are handled has made the listener a lot more stable.

`   * [Done] Update Generators file format`

The file format has been updated to include a number of generators. This
work ties in as a continuation towards using the XSSDB from GNU Citizen.

The upcoming code in order to complete the code are as follows:

`   * Include all XSS Generators from GNU Citizen`
`   * New (pure) HTTP/S Fuzzing Tab using HTTPClient`
`   * Include SOAP and XML fuzzing `
`   * NTLM Brute Force over HTTP/S Tab`
`   * Blind SQL Injection Fuzzing Tab`