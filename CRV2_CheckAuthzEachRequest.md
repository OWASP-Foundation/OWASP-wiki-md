Authorization is as important as authentication. Every *functionality*
as well as every *data access* should be authorized. For data access
authorization, application logic should check if the data belongs to the
authenticated user, or if the user should be able to access that data.

Functionality authorization can be achieved through access control lists
on small systems (such as an embedded system such as a router), but not
via ACLs in an enterprise application. The complexity of an
authorization model can not be implemented by ACLs, and will definitely
lead to human-errors that put the integrity of the system at risk.

### Role Based Access Control for Functionality

RBAC means assigning users to roles, and then roles to permissions. This
is a more logical modeling of actual system authorization. On top of
that, allows administrators to fine-grain and re-check role-permission
assignments, and make sure that every role has exactly the permissions
it is supposed to have (and nothing more or less). Then assigning users
to roles will yield minimal human-error.

There are 4 levels of RBAC standardized by NIST, level 3 and 4 are
almost never found. Level 2 introduces role hierarchy on top of level 1
(the simple RBAC), and has a better matching to enterprise model.
Extended level 2 introduces hierarchical permissions as well, as one
permission per functionality is required in a system, and in big
systems, the number of available permissions soon introduce
human-errors. Depending on the size of the application, usage of
different levels of RBAC systems is strongly advised.

**Unfortunately** There are not many fast enough implementations of the
RBAC model, since it is very complex within. OWASP RBAC project
introduces a very fast NIST Level 2 Extended RBAC implementation.

### Authorization Checklist

1.  Every entry point should be authorized. Every functionality that an
    application performs, is a function, and should be authorized.
    Authorization should be check for every dynamic (generated)
    application access.
2.  Every function should be authorized. Changing password, logging out,
    editing a certain record, and etc. are sample functions. Everything
    should be authorized.
3.  Authorization checks should be fast and easy. Requiring multiple
    lines of complicated code for a single authorization is not
    recommended.
4.  Authorization can be forced, or checked (depending on tolerance of
    application). For example:

`  if ($RBAC->hasAuthority($CurrentUser,"/users/passwords/change")) ShowChangePasswordLink(); //checked authority for visual manipulation in a view`
`  `
`  $RBAC->authorize("/users/passwords/change"); //force authorization on a user management model`
`  ChangePassword(...);`

In case that a forced authorization fails, a HTTP 403 not authorized
page can be shown. If the user is not logged in yet, a login page with
not authorized error is more appropriate.