## Review code for input validation

### Introduction

Input validation is one of the most effective technical controls for
application security. It can mitigate numerous vulnerabilities including
cross-site scripting, various forms of injection, and some buffer
overflows. Input validation is more than checking form field values.

All data from users needs to be considered untrusted. Remember one of
the top rules of secure coding is “Don’t trust user input”. Always
validate user data with the full knowledge of what your application is
trying to accomplish.

Regular expressions can be used to validate user input, but the more
complicated the regular express are the more chance it is not full proof
and has errors for corner cases. Regular expressions are also very hard
fro QA to test. Regular expressions may also make it hard for the code
reviewer to do a good review of the regular expressions.

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

### .Net Request Validation

One solution is to use .Net “Request Validation”. Using request
validation is a good start on validating user data and is useful. The
downside is too generic and not specific enough to meet all of our
requirements to provide full trust of user data.

You can never use request validation for securing your application
against cross-site scripting attacks.

The following example shows how to use a static method in the Uri class
to determine whether the Uri provided by a user is valid.

`var isValidUri = Uri.IsWellFormedUriString(passedUri, UriKind.Absolute);`

However, to sufficiently verify the Uri, you should also check to make
sure it specifies http or https. The following example uses instance
methods to verify that the Uri is valid.

`var uriToVerify = new Uri(passedUri);`
`var isValidUri = uriToVerify.IsWellFormedOriginalString();`
`var isValidScheme = uriToVerify.Scheme == "http" `

| | uriToVerify.Scheme == "https";

Before rendering user input as HTML or including user input in a SQL
query, encode the values to ensure malicious code is not included.

You can HTML encode the value in markup with the \<%: %\> syntax, as
shown below.

<span>`<%: userInput %>`</span>

Or, in Razor syntax, you can HTML encode with @, as shown below.

<span>`@userInput`</span>

The next example shows how to HTML encode a value in code-behind.

`var encodedInput = Server.HtmlEncode(userInput);`

### Managed Code and NonManaged code

Both Java and .Net have the concept of managed and non-managed code. To
offer some of these protections during the invocation of native code, do
not declare a native method public. Instead, declare it private and
expose the functionality through a public wrapper method. A wrapper can
safely perform any necessary input validation prior to the invocation of
the native method:

### Java Sample code to call a Native Method with Data Validation in place

`       public final class NativeMethodWrapper {`
`           private native void nativeOperation(byte[] data, int offset, `
`                                        int len);`

`           public void doOperation(byte[] data, int offset, int len) {`
`               // copy mutable input`
`               data = data.clone();`

`               // validate input`
`               // Note offset+len would be subject to integer overflow.`
`               // For instance if offset = 1 and len = Integer.MAX_VALUE,`
`               //   then offset+len == Integer.MIN_VALUE which is lower`
`               //   than data.length.`
`               // Further,`
`               //   loops of the form`
`               //       for (int i=offset; i<offset+len; ++i) { ... }`
`               //   would not throw an exception or cause native code to`
`               //   crash.`

`               if (offset < 0 `

| | len \< 0 | | offset \> data.length - len) {

`                     throw new IllegalArgumentException();`
`               }`

`               nativeOperation(data, offset, len);`
`           }`
`       }`

### Data validations checklist for the Code Reviewer.

  - Ensure that a Data Validation mechanism is present.
  - Ensure all input that can (and will) be modified by a malicious user
    such as HTTP headers, input fields, hidden fields, drop down lists,
    and other web components are properly validated.
  - Ensure that the proper length checks on all input exist.
  - Ensure that all fields, cookies, http headers/bodies, and form
    fields are validated.
  - Ensure that the data is well formed and contains only known good
    chars if possible.
  - Ensure that the data validation occurs on the server side.
  - Examine where data validation occurs and if a centralized model or
    decentralized model is used.
  - Ensure there are no backdoors in the data validation model.

<!-- end list -->

  - "Golden Rule: All external input, no matter what it is, is examined
    and validated."

Resources: <http://msdn.microsoft.com/en-us/library/vstudio/system.uri>