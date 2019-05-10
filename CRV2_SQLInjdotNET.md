.NET

Framework 1.0 & 2.0 might be more vulnerable to SQL injections than the
later versions of .NET. Thanks to the proper implementation and use of
design patters already embedded in ASP.NET such as MVC(also depending on
the version), it is possible to create applications free from SQL
injections, however, there might be times where a developer might prefer
to use SQL code directly in the code.

Example.

A developer creates a webpage with 3 fields and submit button, to search
for employees on . Field name, lastname + id

The developer implements a dynamic SQL statement or Stored procedure in
the code such as this one:

`//example sql statement`
`SqlDataAdapter thisCommand = new SqlDataAdapter(`
`         "SELECT name, lastname FROM employees WHERE ei_id = '" + `
`         idNumber.Text + "'", thisConnection);`

`//example stored procedures`
`SqlDataAdapter thisCommand = new SqlDataAdapter(`
`                               "SearchEmployeeSP '" + `
`                                idNumber.Text + "'", thisConnection);`

The first code is equivalent to the following sql statement, which gets
executed:

`SELECT name, lastname FROM employees WHERE idNumber = '567892'`
` `

A hacker can then insert the following statement and execute the
following code:

`SELECT name, lastname FROM authors WHERE au_id = ''; DROP DATABASE pubs --'`

The semicolon ";" provides SQL with a signal that it has reached the end
of the sql statement, however, the hacker uses this to continue the
statement with the malicious SQL code

` ; DROP DATABASE pubs`

## Parameter collections

Parameter collections such as SqlParameterCollection provide type
checking and length validation. If you use a parameters collection,
input is treated as a literal value, and SQL Server does not treat it as
executable code, and therefore the payload can not be injected. Using a
parameters collection lets you enforce type and length checks. Values
outside of the range trigger an exception. Make sure you handle the
exception correctly. Example of the SqlParameterCollection:

`using System.Data;`
`using System.Data.SqlClient;`
`using (SqlConnection conn = new SqlConnection(connectionString)) {`
`DataSet dataObj = new DataSet();`
`SqlDataAdapter sqlAdapter = new SqlDataAdapter( "StoredProc", conn); sqlAdapter.SelectCommand.CommandType =   `
`CommandType.StoredProcedure;`
`//specify param type`
`sqlAdapter.SelectCommand.Parameters.Add("@usrId", SqlDbType.VarChar, 15);  `
`sqlAdapter.SelectCommand.Parameters["@usrId "].Value = UID.Text; // Add data from user sqlAdapter.Fill(dataObj); // `
`populate and execute proc`
`}`