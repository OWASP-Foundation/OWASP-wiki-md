  - One of the priorities of this project is to allow developers to do
    whatever they choose, without enforcing RFC compliance. This is
    important for a security testing library, as often the most
    interesting behavior manifests outside the RFCs\! Keep in mind that
    a lot of the safety nets that exist in libraries that enforce RFC
    compliance do not exist in this library, and that as the developer,
    you need to be prepared to deal with the consequences\!
  - Another priority is to accurately deliver whatever is specified by
    the client, and similarly, to accurately reflect whatever is
    returned by the server, rather than coloured by the parsing and
    normalisation performed by the library.
  - In order to achieve byte for byte accuracy with what was sent by the
    client, and received from the server, OWASP Proxy does the bare
    minimum of message parsing. The basic storage of an HTTP message is
    as an array of byte (a byte for byte copy of what was read from the
    network), rather than parsed out into convenient pieces. The library
    does provide convenience methods for accessing interesting parts of
    the message, such as headers, content, etc, but the message itself
    is always stored as a large byte\[\].
  - The Request and Response objects that you may deal with also do not
    decode the message bodies for you. If the message was sent using
    chunked encoding, the message body will show the individual chunks
    that were sent. Of course, again, there are also classes which allow
    you to obtain the actual entity body, with appropriate decoding.
  - As mentioned above, one objective is correctness. By this I mean
    correctly handling whatever the major browsers send to it, and
    successfully retrieving whichever resource was requested. Failure to
    do so will be addressed as soon as possible.
  - Other than that, there is no intention to add major new features to
    the library above those required to fulfill its purpose as a
    Listener and a HTTP client implementation.