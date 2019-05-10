__TOC__

## Introduction

Input validation is one of the most effective technical controls for
application security. It can mitigate numerous vulnerabilities including
cross-site scripting, various forms of injection, and some buffer
overflows. Input validation is more than checking form field values. The
chapter on transactional analysis talks about this.

### Data Validation

All external input to the system should undergo input validation. The
validation rules are defined by the business requirements for the
application. If possible, an exact match validator should be
implemented. Exact match only permits data that conforms to an expected
value. A "Known good" approach (white-list), which is a little weaker,
but more flexible, is common. Known good only permits characters/ASCII
ranges defined within a white-list. Such a range is defined by the
business requirements of the input field. The other approaches to data
validation are "known bad," which is a black list of "bad characters".
This approach is not future proof and would need maintenance. "Encode
bad" would be very weak, as it would simply encode characters considered
"bad" to a format which should not affect the functionality of the
application.

### Business Validation

Business validation is concerned with business logic. An understanding
of the business logic is required prior to reviewing the code which
performs such logic. Business validation could be used to limit the
value range or a transaction inputted by a user or reject input which
does not make too much business sense. Reviewing code for business
validation can also include rounding errors or floating point issues
which may give rise to issues such as integer overflows which can
dramatically damage the bottom line.

### Canonicalization

Canonicalization is the process by which various equivalent forms of a
name can be resolved to a single standard name, or the "canonical" name.

The most popular encodings are UTF-8, UTF-16, and so on (which are
described in detail in RFC 2279). A single character, such as a
period/full-stop (.), may be represented in many different ways: ASCII
2E, Unicode C0 AE, and many others.

With the myriad ways of encoding user input, a web application's filters
can be easily circumvented if they're not carefully built.

### Bad Example

`public static void main(String[] args) {`
`    File x = new File("/cmd/" + args[1]);`
`    String absPath = x.getAbsolutePath();`
`}`

### Good Example

`public static void main(String[] args) throws IOException {`
`    File x = new File("/cmd/" + args[1]);`
`    String canonicalPath = x.getCanonicalPath();`
`}`

### References

**See Reviewing code for Data Validation (in this guide)** [Reviewing
code for Data Validation](Reviewing_Code_for_Data_Validation "wikilink")

**See the OWASP ESAPI Project**

The [OWASP ESAPI](ESAPI "wikilink") project provides a reference
implementation of a security API which can assist in providing security
controls to an application.

[Category:OWASP Code Review
Project](Category:OWASP_Code_Review_Project "wikilink")