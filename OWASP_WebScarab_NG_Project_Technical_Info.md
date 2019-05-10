**WebScarab (Next Generation) Technical Information**

## Accessing the HSQL Database

WebScarab-NG defaults to using the HSQLDB database libraries. If you are
interested in digging into the DB manually, here's what you need to
know.

### Getting the JAR

Since WebScarab-NG is only available via Java Web Start at the moment,
the HSQLDB libraries are unlikely to be anywhere convenient. So download
the [|
jar](http://dawes.za.net/rogan/webscarab-ng/webstart/hsqldb-1.8.0.1.jar),
and place it somewhere handy.

### Accessing the DB

HSQLDB comes with a graphical client that allows you to explore the
database, and execute arbitrary SQL.

You can invoke it by running:

`   $ java -cp hsqldb-1.8.0.1.jar org.hsqldb.util.DatabaseManager`

It will prompt you to connect to the DB, by providing a URL. Simply copy
and paste the same URL that you see in the WebScarab-NG dialog.

NOTE: Since it is run "in-process" in WebScarab-NG, it is not possible
to access it concurrently from another application. You may be
successful running HSQLDB in server mode, and specifying an appropriate
URL to WS-NG when it starts, but keep in mind that (at the moment) WS-NG
executes "SHUTDOWN" on the DB as it exits, in order to have a clean DB
file, and no redo logs, etc. This could be changed if necessary.

### Important tables

Once you have the DB open, it is just SQL ;-)

The key table is the "conversations" table.

`   conversations.createTable.hsqldb=\`
`        CREATE CACHED TABLE conversations (\`
`                session_id INT NOT NULL, \`
`                id INTEGER GENERATED BY DEFAULT AS IDENTITY\`
`                        (START WITH 1) PRIMARY KEY,\`
`                source_id INT NOT NULL,\`
`                request_date TIMESTAMP NOT NULL,\`
`                request_method_id INT NOT NULL,\`
`                request_uri_id INT NOT NULL,\`
`                request_version_id INT NOT NULL,\`
`                request_content_id CHAR(32),\`
`                response_version_id INT NOT NULL,\`
`                response_status CHAR(3) NOT NULL,\`
`                response_message_id INT NOT NULL,\`
`                response_content_id CHAR(32)\`
`        )`

This keeps a record of every conversation that WS-NG knows about. The
columns should be quite self-explanatory.

This table works in conjunction with the headers and named_values
tables to record the request and response headers, as well as the blobs
table to record the request and response content. The blobs table is
indexed by the MD5 sum of the content.

So it is quite easy to reconstruct a conversation by finding the entry
in the conversations table, getting the headers from the
headers/named_values tables, and the content from the blobs table. And
obviously, the other fields are indexed into appropriate tables
(method_id -\> methods, uri_id -\> uris, etc)

Comments on my normalization are welcome - it's been almost 15 years
since my databases class at university\!

### Database schema changes

Databases created by versions of WebScarab-NG before 20070118 will be
incompatible with versions after that date. Certain table columns were
renamed to make it easier to accommodate other databases, by avoiding
keywords, etc.

If you have an early DB, and would like to regain access to it, you need
to run the following script using the DatabaseManager as described
above:

`ALTER TABLE conversations ALTER COLUMN session RENAME TO session_id;`
`ALTER TABLE conversations ALTER COLUMN source RENAME TO source_id;`
`ALTER TABLE conversations ALTER COLUMN date RENAME TO request_date;`
`ALTER TABLE conversations ALTER COLUMN request_method RENAME TO request_method_id;`
`ALTER TABLE conversations ALTER COLUMN request_uri RENAME TO request_uri_id;`
`ALTER TABLE conversations ALTER COLUMN request_version RENAME TO request_version_id;`
`ALTER TABLE conversations ALTER COLUMN request_content_key RENAME TO request_content_id;`
`ALTER TABLE conversations ALTER COLUMN response_version RENAME TO response_version_id;`
`ALTER TABLE conversations ALTER COLUMN response_message RENAME TO response_message_id;`
`ALTER TABLE conversations ALTER COLUMN response_content_key RENAME TO response_content_id;`
`ALTER TABLE blobs ALTER COLUMN key RENAME TO id;`
`ALTER TABLE blobs ALTER COLUMN size RENAME TO blob_size;`
`ALTER TABLE blobs ALTER COLUMN blob RENAME TO blob_content;`
`ALTER TABLE headers ALTER COLUMN conversation RENAME TO conversation_id;`

which will rename the columns for you.

## Feedback

If you have any comments or suggestions for WebScarab-NG, please feel
free to send them to the [OWASP WebScarab mailing
list](http://lists.owasp.org/mailman/listinfo/owasp-webscarab)

Your feedback is much appreciated, and will be carefully considered for
future releases of WebScarab-NG.

## Project Contributors

The WebScarab-NG project is run by Daniel Brzozowski. He can be
contacted at ![<File:Db.png>](Db.png "File:Db.png").

[Category:OWASP WebScarab NG
Project](Category:OWASP_WebScarab_NG_Project "wikilink")