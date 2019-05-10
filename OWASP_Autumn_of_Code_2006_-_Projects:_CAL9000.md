**AoC Candidate:** Chris

**Project Coordinator:** Andrew van der Stock

**Project Progress:** 100% Complete - [Progress
Page](OWASP_Autumn_of_Code_2006_-_Projects:_CAL9000_-_Progress "wikilink")

## Background and Motivation

**History Behind Project**

  - I got tired of hunting around for information and tools that I
    needed in order to do assessments, so I thought that it wouldn't be
    too hard (ha\!) to put them all together into one tool.

**Problem to be Addressed**

  - Helps take some of the monotony and guesswork out of manual testing.

**Benefit to OWASP Members and Community**

  - CAL9000 is a collection of web application security testing tools
    that complement the feature set of current web proxies and automated
    scanners. It gives testers flexibility and functionality for more
    effective manual testing efforts.

## Goals and Deliverables

**Plan of Approach**

  - Get up. Code. Drink. Sleep. Repeat 100 times.

**Deliverables** Listed below are the upgrades that I guarantee that I
would be able to implement by year-end 2006.

XSS Attack Library Page -

  - Allow filtering of attacks based upon what browsers they are
    effective in.
  - Allow users to create/edit/delete their own attacks that will
    persist even if the RSnake XSS attack file is updated.
  - Allow display of all user-defined attacks in a print-ready format.
  - Enhance RegEx testing functionality. At a minimum, allow
    user-defined regex flags and replacement strings. Include
    show/replace/split matches and the ability to test the regex against
    code.

HTTP Requests Page -

  - Give users (near)full control over generating and sending HTTP
    Requests. (There are some browser-dependent restrictions)
  - Allow users to define HTTP Method Type,Authentication Type w/values,
    Schema, FQDN, Port, Absolute path of URL, Parameter, Query String,
    Request Headers/Body.
  - Allow Quick encoding of an entire request field or selected
    text(Url, Hex, Unicode, Base64, Md5 encoding types).
  - Allow users to quickly include from a list of Header Names and
    common Header Values, depending on the Name. (Or use their own)
  - Allow users to quickly include Browser-specific Headers/Values.
  - Allow users to quickly include Method-specific Headers/Values.
  - Allow users to include Request Name/Value pairs and add them to the
    Query String or the Response Body.
  - All Request/Response results will be saved in persistent History and
    easily redisplayed.

HTTP Responses Page -

  - Display Target URL, Response Status/Headers/Body.
  - Allow users to view Response Body as it would appear in a browser.
  - Allow users to extract and view Scripts/Forms/Cookies from the
    response.
  - Allow users to delete Scripts and Forms from Response Body and view
    the effect on the rendering of the page.
  - Allow display of Request/Response pairs in a print-ready format.

Misc Tools Page -

  - Allow user-defined characters for the String Generator.

Testing Checklist Page -

  - Retain the current testing tips and add a testing checklist based on
    the OWASP Testing Guide. Include the ability for users to
    create/edit/delete their own checklist items and also
    create/edit/delete their results/notes for each test.
  - Allow display of all checklist items and results in a print-ready
    format.

Automater Page -

  - Allow users to create/edit/delete lists of attack strings and define
    the insertion points in a request. CAL9000 will automatically send a
    request for each attack string. Results will be available for review
    in the History. (Basically, this is a scanner where the user gets to
    define the tests)

## Risks and Rewards

**Main Risks**

  - No social life for several months.

**Rewards of Successful Project**

  - Get an AoC t-shirt.