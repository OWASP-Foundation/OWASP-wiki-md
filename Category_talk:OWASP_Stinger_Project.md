\>\> In working with Stinger over the past year I have found some issues
in the way that Stinger implemented handling of the HTTP request. In
short, it overlooked the fact that a parameter can have multiple values.
This has been corrected and will be available for download within the
next week or two.

This seems only partially correct. You are correct in stating that
Stinger does not properly process a parameter with multiple values.
Rather, Stinger simply keeps the first value and discards the rest (see
MutableHttpRequest.java). The configuration rules for this first
parameter value are still applied and enforced before it is utilized by
the target application. Although this behavior may result in functional
problems with regards to the protected application (ex. application
expects multiple values), I do not see where the security risk is
present as the one kept value is still evaluated against the declarative
rules. Just a heads up.

\-Eric

## getParameterValues(String name)

This function in MutableHttpRequest does not work like the one in
HttpServletRequest\!

`   public String[] getParameterValues(String name) {`
`       String[] values = new String[1];`
`       `
`       values[0] = parameters.get(name);`
`       `
`       return values;`
`   }`

Giving the function a parameter name that was not present in the
request, it returns an array of size 1 containing a null value\! The
same function in HttpServletRequest directly returns null.

Another thing that you already described on the Stinger Project main
page is, that this function can not handle multiple values. It always
returns only the first parameter value of the list. When do you think
the next release is available?

Andreas

## Licensing

Can you confirm the version of the LGPL Stinger is licensed under? The
project page
[1](http://www.owasp.org/index.php/Category:OWASP_Stinger_Project) links
to an LGPL 3.0 page [2](http://www.gnu.org/copyleft/lesser.html),
whereas 19 of 20 source files indicate that it's licensed under LGPL
2.1?

Jim