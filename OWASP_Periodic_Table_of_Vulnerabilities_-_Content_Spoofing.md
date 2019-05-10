[Return to Periodic Table Working
View](OWASP_Periodic_Table_of_Vulnerabilities#Periodic_Table_of_Vulnerabilities "wikilink")

## Content Spoofing

### Root Cause Summary

The application displays user-defined content in the URL or page body in
a way that makes it appear to be legitimate site content.

### Browser / Standards Solution

Define a new 40X status code that can be used instead of the current
strategy employed by many sites of using a 200 response code for missing
content or a 30x redirect, which is handled in the following way:

  - The URL bar is overwritten with the contents of the Location header,
    which is restricted to a URL from the same origin as the original
    request.
  - The response body specified by the server is displayed. If not
    specified, the browser substitutes a generic 404 page.

### Perimeter Solution

None

### Generic Framework Solution

None

### Custom Framework Solution

The framework must clearly segregate user-defined content from
site-defined content.

### Custom Code Solution

None

### Discussion / Controversy

Some argue that the information leakage risk of replying with 404 for
missing content vs. 200 for actual content is significant. Replying with
200 for everything may have SEO implications. URL Content spoofing risk
may not be clearly defined enough to show need for standards-based
solution.

### References

[Content Spoofing](Content_Spoofing "wikilink")
[Content Spoofing
(WASC)](http://projects.webappsec.org/w/page/13246917/Content%20Spoofing)