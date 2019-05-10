## Status

This article is in DRAFT

## Overview of Session Fixation

A detailed overview on session fixation can be found here: [Session
Fixation](Session_Fixation "wikilink")

## Countermeasures

  - Session ID should be regenerated after login, and switching in and
    out of SSL

` session.invalidate();`
` session=request.getSession(true);`

Comment: Please note that JBOSS has proven to NOT regenerate a new
session id via this method as of December 2007.

  - Disable URL rewriting

Comment: What threat does this mitigate?
Answer: Disabling of URL rewriting mitigates Session Hijacking/Session
Sniffing via session id's being exposed in a GET parameter of your url's
(as well as being stored in your browser history, proxy servers, etc).
See [Session hijacking attack](Session_hijacking_attack "wikilink")