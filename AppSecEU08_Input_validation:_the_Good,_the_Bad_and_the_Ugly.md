This talk discusses input validation design choices and recommends
practices that provide developers a fighting chance to survive
architectural decay as an application matures.

The OWASP 2004 Top Ten adviced never to trust user input. Although
fundamentally sound, it led to many maintenance nightmares and insecure
web applications. This talk argues that the enthusiasm for input
validation must be tempered by a resolve to eliminate code duplication
to maintain sanity and security. I will show this is possible, even in
the face of apparently conflicting objectives, namely usability and
protection against malicious users.

The discussion is illustrated by a case study of a well-intentioned but
flawed attempt at implementing meticulous input validation. The
application's validation code is scattered throughout the code base. I
investigate what can be done to improve the code. However, writing
elegant validation code is found to be very hard in current mainstream
technologies, so I also explore some promising alternatives.