## Status

This guide is out of date and incomplete. Please see [Transport Layer
Protection Cheat
Sheet](Transport_Layer_Protection_Cheat_Sheet "wikilink") for
information on TLS/SSL configuration and best practice.

## What is SSL

SSL is the abbreviation of Secured Socket Layer. It is a protocol
enabling to settle a secured communication between two hosts. The origin
host is viewed as an SSL client and the destination host as an SSL
server.

SSL has also been normalised as the TLS (Transport Layer Security)
protocol.

**SSL is used on top of a transport layer protocol** like TCP or UDP,
and **underneath an application layer protocol** like HTTP or FTP in
order to secure it.

SSL enables :

  - authentication of the destination host for the origin host or mutual
    authentication of both the origin and the destination hosts
  - data confidentiality through encryption
  - data integrity checking through hashing.

SSL relies on two types of encryption :

  - public key encryption in the initiation phase, where authentication
    takes place
  - secret key encryption when a session has been established and data
    is sent between two peers which trust each other.

**SSL only secures the communication between two endpoints** : in the
origin and destination points, data is in clear text, unless it is
encrypted by another means, at the application level.

## See Also

[Transport_Layer_Protection_Cheat_Sheet](Transport_Layer_Protection_Cheat_Sheet "wikilink")

[Category:OWASP Best
Practices](Category:OWASP_Best_Practices "wikilink")