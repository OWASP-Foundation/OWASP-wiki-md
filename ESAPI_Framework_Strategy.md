the esapi should

be defined such that it can be used on behalf of applications by
frameworks including containers (unless the nature of the functionality
is such that it can only work from the application). another way this
was said, is such that the api is compatible with ioc.

share the representations of authentication state employed by the
underlying framework or runtime environment.

leverage the access control primitives (e.j. Java permissions) employed
by the underlying framework or runtime environment

where the api must be embedded in the app, consider separation of the
specification of the logical effect of what must be achieved (in the
app) from the details of how it will be accomplished, such that
different mechanisms can be bound to achieve the effect, such as the
case with Java Annotations.