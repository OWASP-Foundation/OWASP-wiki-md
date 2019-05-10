WIP 21/11/2008

## No authentication

Public access to the resources (APEX_PUBLIC_USER is being used, unless
you specify another user in the dads.conf[1](1 "wikilink"))

\==Open door credentials Log in with just a username, no password. Only
use this in the development / testing stage.

## ApEx build-in credentials

Use the usermanagement that ApEx supplies. This also known as cookie
users. (Use this for quick prototyping, accoring to Scott Spendoli)

## Database account authentication

Use the database roles/users. The connection is still made using the
credentials specified in the dads.conf [1](1 "wikilink")

## Custom authentication

LDAP/OID/AD/SSO

[1If](1 "wikilink") you have read through the official Oracle HTML DB
documentation, you will note that it refers to a file named marvel.conf
instead of dads.conf. Whenever the Oracle HTML DB documentation refers
to the file marvel.conf, it means the dads.conf configuration file\!