Last revision (mm/dd/yy): **01/22/2013**

    This type of article aims to provide to development team a easy/quick way to perform automated audit
    tests against their web application projects over implementation phase.

## Description

This page has the objective to show an example SQLMap command to
automate the auditing of a web application for SQL injection
vulnerabilities. SQLMap is an open source penetration testing tool that
automates the process of detecting and exploiting SQL injection flaws
and taking over of database servers. ([SQLMap
homepage](http://sqlmap.sourceforge.net)).

*This command line does not replace a manual audit but can be useful to
perform a first validation*.

## Command line

    python sqlmap.py -v 2 --url=http://mysite.com/index --user-agent=SQLMAP --delay=1 --timeout=15 --retries=2
    --keep-alive --threads=5 --eta --batch --dbms=MySQL --os=Linux --level=5 --risk=4 --banner --is-dba --dbs --tables --technique=BEUST
    -s /tmp/scan_report.txt --flush-session -t /tmp/scan_trace.txt --fresh-queries > /tmp/scan_out.txt

**Options used to specify HTTP communication behaviors:**

  - \-v: Set the verbosity level of output messages ([Option details
    section](http://sqlmap.sourceforge.net/doc/README.html#toc5.1)).
  - \--url: Run sqlmap against a single target URL ([Option details
    section](http://sqlmap.sourceforge.net/doc/README.html#toc5.2)).
  - \--user-agent: Providing custom User-Agent ([Option details
    section](http://sqlmap.sourceforge.net/doc/README.html#toc5.3)).
  - \--delay: Number of seconds to hold between each HTTP(S) request
    ([Option details
    section](http://sqlmap.sourceforge.net/doc/README.html#toc5.3)).
  - \--timeout: Number of seconds to wait before considering the HTTP(S)
    request timed out ([Option details
    section](http://sqlmap.sourceforge.net/doc/README.html#toc5.3)).
  - \--retries: Maximum number of retries when the HTTP(S) connection
    timeouts ([Option details
    section](http://sqlmap.sourceforge.net/doc/README.html#toc5.3)).
  - \--keep-alive: Use persistent HTTP(s) connections ([Option details
    section](http://sqlmap.sourceforge.net/doc/README.html#toc5.4)).
  - \--threads: Maximum number of concurrent HTTP(S) requests that
    sqlmap is allowed to do ([Option details
    section](http://sqlmap.sourceforge.net/doc/README.html#toc5.4)).
  - \--eta: Calculate and show in real time the estimated time of
    arrival to retrieve each query output. This is shown when the
    technique used to retrieve the output is any of the blind SQL
    injection type ([Option details
    section](http://sqlmap.sourceforge.net/doc/README.html#toc5.15)).
  - \--batch: This will leave sqlmap to go with a default behaviour
    whenever user's input would be required ([Option details
    section](http://sqlmap.sourceforge.net/doc/README.html#toc5.15)).

**Options used to specify audit behaviors:**

  - \--dbms: Force back-end DBMS to this value ([Option details
    section](http://sqlmap.sourceforge.net/doc/README.html#toc5.5)).
  - \--os: Force back-end DBMS operating system to this value ([Option
    details
    section](http://sqlmap.sourceforge.net/doc/README.html#toc5.5)).
  - \--level: Level of tests to perform from 1 to 5, default is 1
    ([Option details
    section](http://sqlmap.sourceforge.net/doc/README.html#toc5.6)).
  - \--risk: Specifies the risk of tests to perform from 1 to 3, default
    is 1 ([Option details
    section](http://sqlmap.sourceforge.net/doc/README.html#toc5.6)).
  - \--banner: Try to retrieve the database management systems product
    banner ([Option details
    section](http://sqlmap.sourceforge.net/doc/README.html#toc5.9)).
  - \--is-dba: Detect if the current database management system session
    user is a database administrator ([Option details
    section](http://sqlmap.sourceforge.net/doc/README.html#toc5.9)).
  - \--dbs: Try to enumerate the list of databases ([Option details
    section](http://sqlmap.sourceforge.net/doc/README.html#toc5.9)).
  - \--tables: Try to enumerate DBMS database tables ([Option details
    section](http://sqlmap.sourceforge.net/doc/README.html#toc5.9)).
  - \--technique: SQL injection techniques to test for, default is BEUST
    ([Option details
    section](http://sqlmap.sourceforge.net/doc/README.html#toc5.7)),
      - B: Boolean-based blind SQL injection
      - E: Error-based SQL injection
      - U: UNION query SQL injection
      - S: Stacked queries SQL injection
      - T: Time-based blind SQL injection

**Options used to specify scan information's' saving behaviors:**

  - \-s: Save and resume all data retrieved on a session file ([Option
    details
    section](http://sqlmap.sourceforge.net/doc/README.html#toc5.15)).
  - \--flush-session: Flush the content of file specified by '-s' in
    order to avoid the caching mechanisms implemented by default in
    sqlmap ([Option details
    section](http://sqlmap.sourceforge.net/doc/README.html#toc5.15)).
  - \-t: Log all HTTP traffic into a textual file ([Option details
    section](http://sqlmap.sourceforge.net/doc/README.html#toc5.15)).
  - \--fresh-queries: Ignores query results stored in session file
    ([Option details
    section](http://sqlmap.sourceforge.net/doc/README.html#toc5.15)).

Extract from SQLMap documentation about SQL injection techniques
identified by B/E/U/S/T
(http://sqlmap.sourceforge.net/doc/README.html\#toc1.3):

    [B]oolean-based blind SQL injection, also known as inferential SQL injection: sqlmap replaces or appends to the affected parameter
     in the HTTP request, a syntatically valid SQL statement string containing a SELECT sub-statement, or any other SQL statement whose
     the user want to retrieve the output. For each HTTP response, by making a comparison between the HTTP response headers/body with
    the original request, the tool inference the output of the injected statement character by character. Alternatively, the user can
    provide a string or regular expression to match on True pages. The bisection algorithm implemented in sqlmap to perform this technique
    is able to fetch each character of the output with a maximum of seven HTTP requests. Where the output is not within the clear-text plain
    charset, sqlmap will adapt the algorithm with bigger ranges to detect the output.

    [E]rror-based SQL injection: sqlmap replaces or append to the affected parameter a database-specific syntatically wrong statement and
     parses the HTTP response headers and body in search of DBMS error messages containing the injected pre-defined chain of characters and
    the statement output within. This technique works when the web application has been configured to disclose back-end database management
    system error messages only.

    [U]NION query SQL injection, also known as inband SQL injection: sqlmap appends to the affected parameter a syntatically valid SQL statement
     string starting with a UNION ALL SELECT. This techique works when the web application page passes the output of the SELECT statement within
    a for cycle, or similar, so that each line of the query output is printed on the page content. sqlmap is also able to exploit partial
    (single entry) UNION query SQL injection vulnerabilities which occur when the output of the statement is not cycled in a for construct
    whereas only the first entry of the query output is displayed.

    [S]tacked queries SQL injection, also known as multiple statements SQL injection: sqlmap tests if the web application supports stacked queries
     then, in case it does support, it appends to the affected parameter in the HTTP request, a semi-colon (;) followed by the SQL statement to be
     executed. This technique is useful to run SQL statements other than SELECT like, for instance, data definition or data manipulation statements
    possibly leading to file system read and write access and operating system command execution depending on the underlying back-end database
    management system and the session user privileges.

    [T]ime-based blind SQL injection, also known as full blind SQL injection: sqlmap replaces or appends to the affected parameter in the HTTP request,
     a syntatically valid SQL statement string containing a query which put on hold the back-end DBMS to return for a certain number of seconds.
    For each HTTP response, by making a comparison between the HTTP response time with the original request, the tool inference the output of
     the injected statement character by character. Like for boolean-based technique, the bisection algorithm is applied.

## Report

The python script below can be used to generate a HTML report from the
stdout of the command line (redirected to "/tmp/scan_out.txt" in the
SQLMap command line):

    ###########################################
    # Script to generate a HTML report from a
    # SQLMap stdout output
    #
    # Author : Dominique Righetto
    #          dominique.righetto@owasp.org
    # Date   : March 2012
    ###########################################
    import sys
    #I/O paths, take SQLMap STDOUT file from script parameter
    stdout_file_path = sys.argv[1]
    report_file_path = stdout_file_path + ".html"
    #Open STDOUT file in read mode
    file_handle_read = open(stdout_file_path,"r")
    #Open REPORT file in write mode
    file_handle_write = open(report_file_path,"w")
    #Initialize HTML report stream
    file_handle_write.write("<html ns=\"http://www.w3.org/1999/xhtml\" lang=\"en\" xml:lang=\"en\">")
    file_handle_write.write("<head><link rel=\"StyleSheet\" href=\"style.css\" type=\"text/css\" media=\"screen\" /><title>SQLMap HTML Report</title></head>")
    file_handle_write.write("<body><table id=\"myStyle\">")
    file_handle_write.write("<thead><tr><th scope=\"col\">Test datetime</th><th scope=\"col\">Test description</th></tr></thead>")
    file_handle_write.write("<tbody>")
    #Flag to know is global audit is OK
    cannot_find_injectable_parameter = False
    #Read STDOUT file line by line
    for line in file_handle_read:
        if (line.strip().startswith("[")) and (line.find("[*]") == -1):
            #Check for special message indicating audit global status
            if(line.lower().find("all parameters are not injectable") > -1):
                cannot_find_injectable_parameter = True
            #Report generation
            line_part = line.strip().split(" ")
            if (line_part[2].lower() == "testing"):
                #Extract useful informations
                execution_datatime = line_part[0]
                execution_trace = ""
                count = 2
                while(count < len(line_part)):
                    execution_trace = execution_trace + " " + line_part[count]
                    count = count + 1
                #Write report HTML line
                file_handle_write.write("<tr><td>" + line_part[0] + "</td><td>" + execution_trace + "</td></tr>")
    file_handle_write.write("</tbody></table>")
    #Write global audit stauts line
    if(cannot_find_injectable_parameter):
        file_handle_write.write("<h1 class=\"success\">SQLMap cannot find injectable parameters !</h1>")
    else:
        file_handle_write.write("<h1 class=\"fail\">SQLMap can find injectable parameters !</h1>")
    #Finalize report HTML stream
    file_handle_write.write("</body></html>")
    #Close I/O stream
    file_handle_write.close()
    file_handle_read.close()
    #Print some informations
    print "Report generated to " + report_file_path

To generate the report use the command line below:

    python SQMReportGenerator.py /tmp/scan_out.txt

The report will be generated into the same location than the input file
using source file name and adding ".html" extension as report name.

The script use an external CSS file named "style.css" (located into the
same location than the report) to format report.

A CSS sample is available below:

    body
    {
        line-height: 1.6em;
    }
    .success
    {
        font-family: "Lucida Sans Unicode", "Lucida Grande", Sans-Serif;
        text-align: center;
        color: green;
    }
    .fail
    {
        font-family: "Lucida Sans Unicode", "Lucida Grande", Sans-Serif;
        text-align: center;
        color: red;
    }
    #myStyle
    {
        font-family: "Lucida Sans Unicode", "Lucida Grande", Sans-Serif;
        font-size: 12px;
        margin: 45px;
        width: 75%;
        text-align: left;
        border-collapse: collapse;
        border: 1px solid #6cf;
    }
    #myStyle th
    {
        padding: 20px;
        font-weight: normal;
        font-size: 13px;
        color: #039;
        text-transform: uppercase;
        text-align: center;
        border-right: 1px solid #0865c2;
        border-top: 1px solid #0865c2;
        border-left: 1px solid #0865c2;
        border-bottom: 1px solid #fff;
    }
    #myStyle td
    {
        padding: 10px 20px;
        color: #669;
        border-right: 1px dashed #6cf;
    }

Example of generated report:

![SQLMapExampleReport.png](SQLMapExampleReport.png
"SQLMapExampleReport.png")

## Remark about scan scheduling

The scan take a while then it's recommended to schedule is execution:

  - During the night for a daily audit case.
  - During the week-end for a weekly audit case.

[Category:Code Snippet](Category:Code_Snippet "wikilink")
[Category:Automated Audit](Category:Automated_Audit "wikilink")
[Category:Externally Linked
Page](Category:Externally_Linked_Page "wikilink")
[Category:Python](Category:Python "wikilink")