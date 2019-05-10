## Brief Summary

This section describes testing replay vulnerabilities of a web service.
The threat for a replay attack is that the attacker can assume the
identity of a valid user and commit some nefarious act without
detection.

## Description of the Issue

A replay attack is a
"[man-in-the-middle](Man-in-the-middle_attack "wikilink")" type of
attack where a message is intercepted and replayed by an attacker to
impersonate the original sender. For web services, as with other types
of HTTP traffic, a sniffer such as Ethereal or Wireshark can capture
traffic posted to a web service and using a tool like
[WebScarab](OWASP_WebScarab_Project "wikilink"), a tester can resend a
packet to the target server. A tester can attempt to resend the original
message or change the message in order to compromise the host server.

## Black Box testing and example

**Testing for Replay Attack Vulnerabilities:**

1\. Using Wireshark on a network, sniff traffic and filter for web
service traffic. Another alternative is to install WebScarab and use it
as a proxy to capture http traffic

![Image: ReplayWireshark1.jpg](_ReplayWireshark1.jpg
"Image: ReplayWireshark1.jpg")

2\. Using the packets captured by ethereal, use TCPReplay to initiate
the replay attack by reposting the packet. It may be necessary to
capture many packets over time to determine session id patterns in order
to assume a valid session id for the replay attack. It is also possible
to manually post captured HTTP traffic, by using WebScarab.

![Image: ReplayWebScarab1.jpg](_ReplayWebScarab1.jpg
"Image: ReplayWebScarab1.jpg")

**Result Expected:**

The tester can assume the identity of a user.

## Gray Box testing and example

'''Testing for Replay Attack vulnerabilities

1\. Does the web service employ some means of preventing the replay
attack such as pseudo random Session tokens, Nonces with MAC addresses,
or Timestamping? Here is an example of an attempt to randomize session
tokens: (from MSDN Wicked Code -
<http://msdn.microsoft.com/msdnmag/issues/04/08/WickedCode/default.aspx?loc=&fig=true#fig1>).

`   string id = GetSessionIDMac().Substring (0, 24); `
`   ...`
`   private string GetSessionIDMac (string id, string ip, `
`       string agent, string key) `
`   { `
`       StringBuilder builder = new StringBuilder (id, 512); `
`       builder.Append (ip.Substring (0, ip.IndexOf ('.', `
`           ip.IndexOf ('.') + 1))); `
`       builder.Append (agent); `
`       using (HMACSHA1 hmac = new HMACSHA1 `
`           (Encoding.UTF8.GetBytes (key))) { `
`           return Convert.ToBase64String (hmac.ComputeHash `
`              (Encoding.UTF8.GetBytes (builder.ToString ()))); `
`       } `
`   } `

2\. Can the site employ SSL? SSLv3.1 or TLSv1.0 will prevent
unauthorized attempts to replay messages: [Transport Layer
Protection](Transport_Layer_Protection_Cheat_Sheet#Benefits "wikilink").

## References

**Whitepapers**

  - W3C: "Web Services Architecture" - <http://www.w3.org/TR/ws-arch/>

**Tools**

  - [OWASP WebScarab](OWASP_WebScarab_Project "wikilink")
  - Ethereal - <http://www.ethereal.com/>
  - Wireshark - <http://www.wireshark.org/> (recommended instead of
    Ethereal - same developers, same codebase)
  - TCPReplay - <http://tcpreplay.synfin.net/trac/wiki/manual>