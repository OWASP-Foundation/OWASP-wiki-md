  -
    ''This page concerns an attack called an [SQL
    Injection](SQL_Injection "wikilink")

An SQL injection attack consists of insertion or "injection" of an SQL
query via the input data from the client to the application.

## Prevention

1\. Leverage frameworks

  - Paramaterized queries
  - "Point and Click" query generation

2\. Input validation

  - Always ensure that you receive what you expect
  - White list the validation (vs. black list)
  - Validate type, length, format, and range
  - Escape special characters
  - Always validate on the server side - DON'T have the client perform
    validation

3\. ACLs

  - Execute queries with least privilege

### Parameterized Queries and Stored Procs

There are two complementary and successful methods of mitigating SQL
Injection attacks:

  - Parameterized queries using bound, typed parameters
  - Careful use of parameterized stored procedures.

Parameterized queries are the easiest to adopt, and work in fairly
similar ways among the three major technologies in use today:

  - PHP
  - J2EE
  - .NET

### Parameterized Stored Procedures

The use of parameterized stored procedures is an effective mechanism to
avoid most forms of SQL Injection. In combination with parameterized
bound queries, it is very unlikely that SQL injection will occur within
your application. However, there are a number of caveats to bear in
mind:

  - Use of dynamic code execution features will allow SQL Injection:

<tt> create proc VulnerableDynamicSQL(@userName nvarchar(25)) as

` declare @sql nvarchar(255)`
` set @sql = 'select * from users where UserName = ''' `
`   + @userName + ''''`
` exec sp_executesql @sql`

</tt>
[1](http://dotnetjunkies.com/WebLog/chris.taylor/archive/2004/10/13/28370.aspx)

The above example still allows SQL Injection as it allows dynamic
injection of arbitrary string data. This gotchya is also true of Java /
PL/SQL and MySQL's stored procedure support.

### Least privilege connections

Always use accounts with the minimum privilege necessary for the
application at hand, never “sa”, “dba”, “admin”, or the equivalent.

### WARNING: Escaping table names

No SQL Injection mitigation or escaping allows the safe escaping of
table names. This seems to be a common issue with PHP forum software.

`$tablename = mysql_real_escape_string($tablename)`

is simply not safe and cannot be made so. In general:

  - Avoid using dynamic table names if at all possible.
  - If you have to use dynamic table names, do not accept them from the
    user if at all possible.
  - If you have to allow dynamic user choice of table names, ONLY use
    whitelists of acceptable characters for table names and enforce
    table name length limits. In particular, many database systems have
    a wide range of unacceptable characters and these change between
    major releases.

## How to Locate potentially vulnerable code

A secure way to build SQL statements is to construct all queries with
PreparedStatement instead of Statement and/or to use parameterized
stored procedures. Parameterized stored procedures are compiled before
user input is added, making it impossible for a hacker to modify the
actual SQL statement.

The account used to make the database connection must have “Least
privilege” If the application only requires read access then the account
must be given read access only.

Avoid disclosing error information: Weak error handling is a great way
for an attacker to profile SQL injection attacks. Uncaught SQL errors
normally give too much information to the user and contain things like
table names and procedure names.

## Best practices when dealing with DB’s

Use Database stored procedures, but even stored procedures can be
vulnerable. Use parametrized queries instead of dynamic SQL statements.
Data validate all external input: Ensure that all SQL statements
recognize user inputs as variables, and that statements are precompiled
before the actual inputs are substituted for the variables in Java.

## SQL Injection Example:

```

String DRIVER = "com.ora.jdbc.Driver";

String DataURL = "jdbc:db://localhost:5112/users";

String LOGIN = "admin";

String PASSWORD = "admin123";

Class.forName(DRIVER);

//Make connection to DB
Connection connection = DriverManager.getConnection(DataURL, LOGIN, PASSWORD);

String Username = request.getParameter("USER"); // From HTTP request

String Password = request.getParameter("PASSWORD"); // From HTTP request

int iUserID = -1;

String sLoggedUser = "";

String sel = "SELECT User_id, Username FROM USERS WHERE Username = '" +Username + "' AND Password = '" + Password + "'";

Statement selectStatement = connection.createStatement ();
ResultSet resultSet = selectStatement.executeQuery(sel);


if (resultSet.next()) {

       iUserID = resultSet.getInt(1);
       sLoggedUser = resultSet.getString(2);
}

PrintWriter writer = response.getWriter ();

if (iUserID >= 0) {
       writer.println ("User logged in: " + sLoggedUser);
} else {

       writer.println ("Access Denied!")
}
```

When SQL statements are dynamically created as software executes, there
is an opportunity for a security breach as the input data can truncate
or malform or even expand the original SQL query\!

Firstly the request.getParameter retrieves the data for the SQL query
directly from the HTTP request without any Data validation (Min/Max
length, Permitted characters, malicious characters). This error gives
rise to the ability to input SQL as the payload and alter the
functionality in the statement.

The application places the payload directly into the statement causing
the SQL vulnerability:

String sel = "SELECT User_id, Username FROM USERS WHERE Username = '"
Username + "' AND Password = '" + Password + "'";

## .NET

Parameter collections such as SqlParameterCollection provide type
checking and length validation. If you use a parameters collection,
input is treated as a literal value, and SQL Server does not treat it as
executable code and therefore the payload can not be injected. Using a
parameters collection lets you enforce type and length checks. Values
outside of the range trigger an exception. Make sure you handle the
exception correctly. Example of the SqlParameterCollection:

```

using System.Data;

using System.Data.SqlClient;

using (SqlConnection conn = new SqlConnection(connectionString))
{
  DataSet dataObj = new DataSet();

  SqlDataAdapter sqlAdapter = new SqlDataAdapter( "StoredProc", conn);

  sqlAdapter.SelectCommand.CommandType = CommandType.StoredProcedure;

 //specify param type

  sqlAdapter.SelectCommand.Parameters.Add("@usrId", SqlDbType.VarChar, 15);

  sqlAdapter.SelectCommand.Parameters["@usrId "].Value = UID.Text; // Add data from user

  sqlAdapter.Fill(dataObj); // populate and execute proc

}
```

**Stored procedures don’t always protect against SQL injection:**

```

CREATE PROCEDURE dbo.RunAnyQuery
@parameter NVARCHAR(50)

AS
        EXEC sp_executesql @parameter
GO
```

The above procedure shall execute any SQL you pass to it. The directive
sp_executesql is a system stored procedure in Microsoft® SQL Server™

Lets pass it.

```

DROP TABLE ORDERS;
```

Guess what happens? So we must be careful of not falling into the “We’re
secure, we are using stored procedures” trap\!

**Bold text**

## References

1.  MS SQL example
2.  [Michael Sutton "Revisiting SQL
    Injection"](https://www.owasp.org/index.php/Image:Sutton_-_Revisiting_SQL_Injection.pdf)
    presentation to Boulder OWASP Feb 2007.

[Category:Security Focus Area](Category:Security_Focus_Area "wikilink")