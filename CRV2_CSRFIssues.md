Having CSRF-proof forms and actions is a complex task, and very prone to
human-error. The most effective means of mitigating it is incorporating
it into a widget library, for example OWASP PHP Security Widget library,
which automaticlaly uses CSRF protection.

CSRF Protection for GET and COOKIE elements is hard and not recommended,
therefore all operations that change the state of the application in
someway should be implemented using HTTP Post (or other HTTP state
changing requests).

Generally, CSRF protection is achieved by generating cryptographically
secure, **required** parameters into HTML forms, and checking them back
when they are submitted. If they are submitted and valid, they should
get expired.