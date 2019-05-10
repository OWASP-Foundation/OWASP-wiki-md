## What is SQL Injection?

SQL injection is a code bug that has been around for years, but which
continues to pose a major risk to Internet applications. OWASP report
that of all the pages on their wiki, SQL injection pages are the most
accessed. The bug occurs when:

  - Untrusted input is accepted by an application
  - Subsequent SQL commands are not protected from the above untrusted
    input

The classic example is a database table for holding usernames and
passwords. The web application provides the user with a login screen,
such as:

\<<todo insert image>\>

The code on the server that accepts the username and password value
treat the input as strings:

<code>

`String username = form.username.value();`
`String password = form.username.value();`

</code>

Now these values a passed to the database handling code, which develps a
query database table for usernames and passwords is normally accessed by
the following code:

<code>

`String sql_command = "select password from user_password_table where username = '" + username + "';";`

</code>

... which results in the SQL command being issued to the database,
returning the password which can then be checked (in whatever form is
necessary):

<code>

`select password from user_password_table where username = 'johndoe';`

</code>

## So how can SQL be injected?

Because the above code sample treats the input form the user as a
string, and appends that string to the hardcoded SQL command, any user
who wished to insert SQL syntax into the input can affect the resultant
SQL command. As example, if a user enters the string "blah'; drop table
user_password_table; --" as the username, then the resulting SQL
command issued by the database handling code will be:

<code>

`select password from user_password_table where username = 'blah'; drop table user_password_table; --';`

</code>

This now drastically changes the intention of the SQL command, where
now:

  - The first part of the command gets the password from the table for
    username 'blah' -

<code>

`select password from user_password_table where username = 'blah';`

</code>

  - The second part drops the table 'user_password_table' -

<code>

`drop table user_password_table;`

</code>

  - The third part ensures the SQL syntax is valid by commenting out the
    rest of the hardcoded SQL command with two hyphens -

<code>

`--';`

</code>

As can be seen, now the user password table is deleted and the
application has experianced a massive security issue.

## What types of SQL Injection issues are there?

Over time attackers have found different ways to cause problems through
SQL injection attacks, depending on what access the database user has,
and what information is returned to the user.

### Classic SQL Injection

This can occur when untrusted input is used in an SQL command that is
returning database information to the web UI, for example in a search
feature where the rows returned from the SQL query are used to populate
the result set shown to the user. Take an application that allows a user
to search for their outstanding transactions their account number, where
the user enters the account number "1234567890" into a search box:

<code>

`String acct_no = form.account_number.value();`

</code>

... and then this acct_no is used to search the transactions table:

<code>

`String txn_query = "select * from txn_table where account_num = '" + acct_no + '";";`

</code>

This should only return rows from the database table where the account
number is a match.

Now if the attacker inserts some SQL syntax to their account number
input, for example "1234567890' OR 1=1 --" the resultant SQL query
becomes:

<code>

`select * from txn_table where account_num = '1234567890' OR 1=1 -- ';`

</code>

... which will return all rows in the txn_table since 1=1 is always
true. Now the UI code that returns the searched DB rows will display
transactions for all customers, and a data leak has occured. Also this
SQL command will probably not raise any flags as the command executed
correctly, meaning the application will not know their DB table has been
leaked. When you see news reports of millions of passwords being leaked
from various companies, this could have been how it was done.

### Blind SQL Injection

So if the UI being developed does not return search results, an SQL
cannot occur? Unfortunately attackers can still glean information based
on the error responses from various UI elements. Blind SQL injection is
a type of attack that asks the database true or false questions and
determines the answer based on the applications response. Effectively
the attacker uses SQL queries to determine what error responses are
returned for valid SQL, and which responses are returned for invalid
SQL. Then the attacker can probe; for example check if a table called
"user_password_table" exists. Once they have that information, they
could use an attack like the one described above to maliciously delete
the table, or attempt to return information from the table (does the
username "john" exist?).

Blind SQL injections can also use timings instead of error messages,
e.g. if invalid SQL takes 2 seconds to respond, but valid SQL returns in
0.5 seconds, the attacker can use this information.

## How to I protect against SQL Injection?

There are two main ways to prevent SQL injection:

1.  Check/Sanatize all client input
2.  Don't use the string value of any untrusted (client) input in the
    SQL command.

Checking for both of these provide a defense in depth approach - if one
check fails, the other check should still prevent the SQL injection
attack. As seen above, the common mistake is to use the string value of
the client input as part of the SQL string, and this allows SQL syntax
included in the client input to change the effect of the intended SQL.
The best way to prevent the client input being used in this way is to
use parameterized SQL queries.

Some people report the use of stored procedures as a solution against
SQL injection, however this might not be the case. Inside a stored
procedure the coder could easily use string concatentation to insert the
string values into the SQL query, and this would still expose the
function to SQL injection - there is no, automatic, property in stored
procedures that prevent SQL injections. From an application developers
point of view, it can be better to implement the SQL injection
countermeasures in your application code, as you will have fully control
of this, the stored procedures could be modified outside of the
application source code, and any checks that the application developer
assumed were there, could be removed accidentially.

### Sanatize Client Input

Check client input against a list of valid input characters (sometimes
called a 'whitelist'). This can had advantages in that it can prevent
other types of injection attacks including XSS, command injection, etc.
If your input field for 'Age' should only contain numbers, check the
string value passed by the client for the following:

  - Only contains numeric characters (0-9)
  - Is between a lower and upper bound (e.g. 18 \< value \< 130 )
  - If an attacker attempted to inject SQL, e.g. value of "25 '; drop
    table x; --" then this input check will reject the age parameter
    value as it contains invalid characters.

For input strings that are textual, ensure certain characters such as
single tick " ' ", hyphen "-", semi-colon ";", etc are not allowed in
the input.

### Parameterized SQL Queries

Parameterized SQL queries (also called prepared statements) allow the
SQL query string to be defined in such a way that the client input can't
be treated as part of the SQL syntax. Take the following example:

<code>

`String query = "SELECT id, firstname, lastname FROM authors WHERE forename = ? and surname = ?";`
`PreparedStatement pstmt = connection.prepareStatement( query );`
`pstmt.setString( 1, firstname );`
`pstmt.setString( 2, lastname );`

</code>

In this example the string 'query' is constructed in a way that it does
not rely on any client input, and the 'PreparedStatement' is constructed
from that string. When the client input is to be entered into the SQl,
the 'setString' function is used and the first question mark "?" is
replaced by the string value of 'firstname', the second question mark is
replaced by the value of 'lastname'. When the 'setString' function is
called, this function automatically checks that no SQL syntax is
contained within the string value. Most prepared statement APIs allow
you to specify the type that should be entered, e.g. 'setInt', or
'setBinary', etc.

### Safe String Contatenation?

So does this mean you can't use string concatentation at all in your DB
handling code? It is possible to use string concatenation safely, but it
does increase the risk of an error, even without an attacker attempting
to inject SQL syntax into your application.

You should never use string concatentation in combination with the
client input. value Take an example where the existance (not the value)
of a client input variable "surname" is used to construct the SQL query
of the prepared statement;

<code>

`String query = "Select id, firstname, lastname FROM authors WHERE forename = ?";`
`if (lastname!= NULL && lastname.length != 0)`
`{`
`     query += " and surname = ?";`
`});`

`query += ";";`

`PreparedStatement pstmt = connection.prepareStatement( query );`
`pstmt.setString( 1, firstname);`

`if (lastname!= NULL `

| | lastname.length \!= 0)

`{`
`     pstmt.setString( 2, lastname );`
`}`

</code>

Here the value of 'lastname' is not being used, but the existance of it
is being evaluated. However there is still a risk when the SQL statement
is larger and has more complex business logic involved in creating it.
Take the following example where the function will search based on
firstname or lastname:

<code>

`String query = "select id, firstname, lastname FROM authors"; `

`if ( firstname != NULL && firstname.length != 0 )`
`{`
`     query += "WHERE forename = ?;"`
`}`

`if ( lastname!= NULL && lastname.length != 0 )`
`{`
`     query += "WHERE surname = ?;"`
`}`

`PrepartedStatement pstmt = connection.prepareStatement( query ):`

</code>

This logic will be fine when either firstname, or lastname is given,
however if neither were given then the SQL statement would not have any
WHERE clause, and the entire table would be returned. This is not an SQL
injection (the attacker has done nothing to cause this situation, except
not passing two values) however the end result is the same, information
has been leaked from the database, despite the fact that a parameterized
query was used.

For this reason, the advice is to avoid using string concatenation to
create SQL query strings, even when using parameterized queries,
especially if the concatenation involves building any items in the where
clause.

### Using Flexible Parameterized Statements

Functional requirements often need the SQL query being executed to be
flexible based on the user input, e.g. if the end user specifies a time
span for their transaction search then this should be used, or they
might wish to query based on either surname or forename, or both. In
this case the safe string concatenation above could be used, however
from a maintenance point of view this could invite future programmers to
misunderstand the difference between safe concatenation and the unsafe
version (using input string values directly).

One option for flexible parameterized Statements is to use 'if'
statements to select the correct query based on the input values
provided, for example:

<code>

`String query;`
`PreparedStatement pstmt;`

`if ( (firstname!= NULL && firstname.length != 0) &&`
`     lastname!= NULL && lastname.length != 0) )`
`{`
`     query = "Select id, firstname, lastname FROM authors WHERE forename = ? and surname = ?:";`
`     pstmt = connection.prepareStatement( query );`
`     pstmt.setString( 1, firstname );`
`     pstmt.setString( 2, lastname );`
`}`
`else if (firstname != NULL && firstname.length != 0)`
`{`
`     query = "Select id, firstname, lastname FROM authors WHERE forename = ?:";`
`     pstmt = connection.prepareStatement( query );`
`     pstmt.setString( 1, firstname );`
`}`
`else if (lastname != NULL && lastname.length != 0)`
`{`
`     query = "Select id, firstname, lastname FROM authors WHERE surname= ?:";`
`     pstmt = connection.prepareStatement( query );`
`     pstmt.setString( 1, lastname);`
`}`
`else`
`{`
`     throw NameNotSpecifiedException();`
`}`

</code>

Another option is to use inheritance to select the correct DB query
object from a family of queries that are supported. This option works
better when the SQL queries are larger and more variable, and has the
advantage of allowing the programmer to perform specific checks on the
items returned from each query. Using inheritance is also cleaner in
terms of extensibility (simply add another DB query class without
modifying existing DB queries). An example would be:

<code>

`abstract class DBQuery {`
`     public abstract PreparedStatement createQuery (String[] args) {`
`     }`
`}`


`class ForenameDBQuery extends DBQuery {`
`     public PreparedStatement createQuery (String[] args) {`
`          PreparedStatement pstmt = "Select id, firstname, lastname FROM authors WHERE forename = ?:";`
`          pstmt = connection.prepareStatement( query );`
`          pstmt.setString( 1, args[0]);`
`          return pstmt;`
`     }`
`}`

` `
`class SurnameDBQuery extends DBQuery {`
`     public PreparedStatement createQuery (String[] args) {`
`          PreparedStatement pstmt = "Select id, firstname, lastname FROM authors WHERE surname= ?:";`
`          pstmt = connection.prepareStatement( query );`
`          pstmt.setString( 1, args[0]);`
`          return pstmt;`
`     }`
`}`
` `

`class FornameSurnameDBQuery extends DBQuery {`
`     public PreparedStatement createQuery (String[] args) {`
`          PreparedStatement pstmt = "Select id, firstname, lastname FROM authors WHERE surname= ? and forename = ?:";`
`          pstmt = connection.prepareStatement( query );`
`          pstmt.setString( 1, args[0]);`
`          pstmt.setString( 2, args[1]);`
`          return pstmt;`
`     }`
`}`
` `

`class DBInterface {`
`     public static doQuery (String firstname, String lastname) {`
`          String[] queryArguments = new String[2];`
`          PreparedStatement pstmt;`

`          DBQuery query;`

`          if ( (firstname!= NULL && firstname.length != 0) &&`
`               lastname!= NULL && lastname.length != 0) )`
`          {`
`               query = new FornameSurnameDBQuery();`
`               queryArguments[0] = firstname;`
`               queryArguments[1] = lastname;`

`               pstmt = query.createQuery(queryArguments);`
`          }`
`          else if (firstname != NULL && firstname.length != 0)`
`          {`
`               query = new FornameDBQuery();`
`               queryArguments[0] = firstname;`

`               pstmt = query.createQuery(queryArguments);`
`          }`
`          else if (lastname != NULL && lastname.length != 0)`
`          {`
`               query = new SurnameDBQuery();`
`               queryArguments[0] = lastname;`

`               pstmt = query.createQuery(queryArguments);`
`          }`
`          else`
`          {`
`                throw NameNotSpecifiedException();`
`          }`
`}`

</code>

This example of inheritance is simplistic to simply show the concept. It
could be extended/improved to contain the prepared statement within a
child object, or perform the output set checking described below.

### Output Set Checking

One further check you can perform, if the SQL query is returning a
result set, is to look at the attributes of the response and ensure it
is within the expected parameters. If only one result row should be
returned for both 'firstname' and 'lastname', then that can be checked,
however a search for 'lastname' could return multiple responses, but
still not the entire table. The business could decide that regardless of
the function, a maximum of 50 results will be returned, hence a whole
database table is unlikely to be leaked.

Other checks can be done on the values of the result set, e.g. ensuring
the firstname in the result rows is the same one that was used in the
query, or checking a customer Id against the authorization settings of
the current logged in user.