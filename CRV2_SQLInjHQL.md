## Hibernate Query Language (HQL)

Hibernate facilitates the storage and retrieval of Java domain objects
via Object/Relational Mapping (ORM).

It is a very common misconception that ORM solutions, like hibernate,
are SQL Injection proof. Hibernate allows the use of "native SQL" and
defines a proprietary query language, called HQL (Hibernate Query
Language); the former is prone to SQL Injection and the later is prone
to HQL (or ORM) injection.

## Bad Java Code Examples

`List results = session.createQuery("from Items as item where item.id = " + currentItem.getId()).list();`

NHibernate is the same as Hibernate except it is an ORM solution for
Microsoft .Net platform. NHibernate is also vulnerable to SQL injection
if used my dynamic queries.

## Bad .Net Code Example

`string userName = ctx.GetAuthenticatedUserName();`
`String query = "SELECT * FROM Items WHERE owner = '" `
`+ userName + "' AND itemname = '"  `
`+ ItemName.Text + "'";`
`List items = sess.CreateSQLQuery(query).List()`

## Code Reviewer Action

Code reviewer needs to make sure any data used in an HQL query uses HQL
parameterized queries so that it would be used as data and not as code.