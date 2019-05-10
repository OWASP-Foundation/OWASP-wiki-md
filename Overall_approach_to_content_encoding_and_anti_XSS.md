When untrusted data is to be rendered to the UI it MUST under both input
validation and encoding. Encoding is of significant importance given it
can protect the user from client side scripting attacks. XSS
(Cross-Site-Scripting) attacks may consist of exploiting or breaching a
users system:

\-Session Hijacking
–Site Defacement
–Network Scanning
–Undermining CSRF Defenses
–Site Redirection/Phishing
–Load of Remotely Hosted Scripts
–Data Theft
–Keystroke Logging
The following is a suggested encoding matrix. when reviewing code is is
important the untrusted data undergoes one of the following encoding
schemes depending on the context of where is data sits on the page.

![<File:xss-encoding-table.png>](xss-encoding-table.png
"File:xss-encoding-table.png")