## Brief Summary

Many XML applications are invoked by passing them parameters using HTTP
GET queries. These are sometimes known as “REST-style" Web Services
(REST = Representational State Transfer). These Web Services can be
attacked by passing malicious content on the HTTP GET string (e.g.,
extra long parameters (2048 chars), SQL statements/injection (or OS
Injection parameters).

## Description of the Issue

Given that REST Web services are in effect HTTP-In -\> WS-Out, attack
patterns, they are very similar to regular HTTP attack vectors,
discussed throughout the guide. For example, in the following HTTP
request with query string *"/?viewDetail=detail-10293"*, the HTTP GET
parameter is *"detail-10293"*.

## Black Box Testing and example

Say we had a Web Service which accepts the following HTTP GET query
string:

`https://www.ws.com/accountinfo?accountnumber=12039475&userId=asi9485jfuhe92`

The response would be similar to:

<?xml version="1.0" encoding="ISO-8859-1"?>

`<Account="12039475">`
<balance>`€100`</balance>

<body>

Bank of Bannana account info

</body>

</Account>

Testing the data validation on this REST web service is similar to
generic application testing:

Try vectors such as:

`https://www.ws.com/accountinfo?accountnumber=12039475'`*`'``
 ``exec``   ``master..xp_cmdshell``   ``'net``   ``user``   ``Vxr``
 ``pass``   ``/Add`*`'&userId=asi9485jfuhe92`

## Grey Box Testing and example

Upon the reception of an HTTP request the code should do the following:

Check:

1.  Maximum and minimum length
2.  Validate payload
3.  If possible, implement the following data validation stratigies:
    "exact match", "known good" and "known bad", in this order.
4.  Validate parameter names and existence.

## References

**Withepapers**

  - The OWASP [Fuzz
    vectors](OWASP_Testing_Guide_Appendix_C:_Fuzz_Vectors "wikilink")
    list