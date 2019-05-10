Here is the outline I propose of evaluation categories:

`1.Performance - critical for edge device parsing xml steam and performing de/encryption, signing`

`2. Administrative `
`a) Audit and Logging`
`b) Monitoring`
`c) General`
` - security of product's components, interfaces, hardware compliance`
` - ease of use, installation`

`3. XML Gateway capabilities`
`Routing capabilities available`
`Supporing for WS-routing, WSCI, WS-Coordination, WS-Security, WS-SecureConversation, etc) `

`4. XML Firewall capabilities`
`XML threats covered `
`   a) Unauthorized access`
`     - Authentication (WS-Security token replay)`
`     - Auth/Authorization (Canonicalization of inputs, principle spoofing, modification of SAML attributes)`
`     - Interoperability with rights/privilege standards (XACML, WS-Policy)`
`     - Interoperability with authentication SSO (SAML, WS-Federation, ADFS. XKMS)`
`     - unsafe code (format string, CSS, parameter tempering, buffer overflow, sql injection, race conditions, malformed content)`
`     - malicious code (virus scanning)`
`   b) Data Tempering`
`      - message capture/update/replay ( checksum spoofing, principle spoofing, timestamp spoofing, canonization for DSig, intelligent tampering)`
`      - unsafe application code (SQL injection)`
`   c) Information Disclosure`
`     - probing (eavesdropping, forceful browsing, directory traversal, WSDL scanning, error messages, registry disclosure)`
`     - external reference (Schema poisoning, routing detours, external entity)`
`     - unsafe application code (XML Injection, URL String attack, external references)`
`   d) Denial of Service`
`     - coercive parsing (recursive payloads, oversized payloads, replay-flooding)`
`     - unrestrained registries ( UDDI, ebXML Spoofing)`
`     - unsafe application code (inadvertent XML parsing DoS)`