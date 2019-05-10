# Ruby On Rails Stored Anti-pattern

Ruby on rails, version 3.0 has an in built function to validate input,
especially any attempt to submit XSS code, however, if the developer
decides to bypass this validation mechanism, by passing variables to the
front end with tags intact, the developer will change the .erb file
(ruby markup)with the following (similar) code.

`  <%= raw @product.name %>   `
`  <%= @product.name.html_safe %>  These are examples of how NOT to do it!`
`  <%= content_tag @product.name %>`

Unfortunately, any field that uses raw like this will be a potential XSS
target

## Reference

<https://www.owasp.org/index.php/Ruby_on_Rails_Cheatsheet>