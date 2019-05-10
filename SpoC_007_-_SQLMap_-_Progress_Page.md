## Accomplished objectives for OWASP Spring of Code 2007

  - **\[100%\]** Add support for Oracle database management system
  - **\[100%\]** Add support to extract database users password hash
  - **\[100%\]** Extend inband SQL injection functionality to all other
    possible queries
  - **\[100%\]** Add Microsoft SQL Server database fingerprint
  - **\[100%\]** Add a fuzzer class with the aim to parse html page
    looking for standard database error messages consequently improving
    database fingerprinting
  - **\[100%\]** Add support for SQL injection on HTTP *Cookie* and
    *User-Agent* headers
  - **\[100%\]** Add support for query ETA (Estimated Time of Arrival)
    real time calculation
  - **\[100%\]** Improve Google dorking support to take advantage of
    remote hosts affected by SQL injection to perform other command line
    argument actions
  - **\[100%\]** Improve logging functionality

## Changes in sqlmap during OWASP Spring of Code 2007

### May 2007

  - **\[SpoC\]** Added support to extract database users password hash
    on MySQL and PostgreSQL
  - **\[SpoC\]** Improved Google dorking support to take advantage of
    remote hosts affected by SQL injection to perform other command line
    argument actions
  - **\[SpoC\]** Added support for query ETA (Estimated Time of Arrival)
    real time calculation (*--eta*)
  - **\[SpoC\]** Added Microsoft SQL Server extensive DBMS fingerprint
    checks based upon extensive infogathering on *@@version* matching on
    an XML file to get also the exact patching level of the DBMS
  - **\[SpoC\]** Improved logging functionality: passed from banal
    *print* to Python native logging library
  - Added DBMS fingerprint based also upon HTML error messages parsing
    by a *xml.sax* function/class (defined in *lib/parser.py*) which
    read an XML file defining default error messages for each supported
    DBMS
  - Added the possibility to specify *mssql*, *pgsql* as *--remote-dbms*
    values

### June 2007

  - **\[SpoC\]** Improved UNION SELECT check so now it works with five
    different DBMS because it uses the *xml/errors.xml* file to
    recognize HTML error messages and correctly identify if the inband
    SQL injection performed provided good results or not
  - Updated documentation
  - Layout fixes

### July 2007

  - **\[SpoC\]** Extended inband SQL injection functionality
    (*--union-use*) to all other possible queries since it only worked
    with *-e* and *--file* on all DMBS plugins
  - **\[SpoC\]** Added a fuzzer function with the aim to parse html page
    looking for standard database error messages consequently improving
    database fingerprinting (*txt/fuzz_vectors.txt*,
    *Common.passiveFuzzing()*, *lib/settings.py* and DBMS plugins)
  - **\[SpoC\]** Reviewed HTTP request library (*lib/request.py*) to
    support the extended inband SQL injection functionality. Splitted
    *getValue()* into *getInband()* and *getBlind()*
  - **\[SpoC\]** Major enhancements in common library and added
    *checkForBrackets()* method to check if the bracket(s) are needed to
    perform a UNION query SQL injection attack
  - Implemented *--dump-all* functionality to dump entire DBMS data from
    all databases tables
  - Imlemented in *Dump.dbTableValues()* method the CSV file dumped data
    automatic saving in *csv/* folder by default
  - Added DB2, Informix and Sybase DBMS error messages and minor
    improvements in *xml/errors.xml*
  - Renamed DMBS plugins

### September 2007

  - Major improvement in all three DBMS plugins so now sqlmap does not
    get entire databases' tables structure when all of
    database/table/column are specified to be dumped. Some more minor
    fixes in all three DBMS plugins
  - Important fixes in *lib/option.py* to make sqlmap properly work also
    with python 2.5 and handle the CSV dump files creation work also
    under Windows operating system, function *__setCSVDir()* and fixed
    also in *lib/dump.py*
  - Minor enhancement in *lib/injection.py* to randomize the number
    requested to test the presence of a SQL injection affected parameter
    and implemented the possibilities to break (*q*) the for cycle when
    using the google dork option (*-g*)
  - Minor fix in *lib/request.py* to properly encode the url to request
    in case the "fixed" part of the url has blank spaces
  - More minor layout enhancements in some libraries
  - Updated ChangeLog and TODO documentation files

### October 2007

  - **\[SpoC\]** Added support for Oracle database management system
  - **\[SpoC\]** Added support to extract database users password hash
    on Microsoft SQL Server
  - Added support to exclude DBMS system databases' when enumeration
    tables and dumping their entries, *--exclude-sysdbs*
  - Major code refactoring: strongly slightned and adapted plugins code
    and DBMS strictly specific methods, centralized the queries method
    to *lib/query.php* and the queries to an XML file,
    *xml/queries.xml*, implemented a function and a class to parse such
    XML file, renamed a lot of functions and variables to let the name
    be more self explained
  - Minor fix in other libraries to avoid *extra* parameter when calling
    *UnionUse.unionUse()*
  - Enhancement in plugins so the column type is not more enumerated
    when it's not necessary to dump table entries, since we need to know
    in this case only the column name
  - Major fix in plugins and in *lib/dump.py* to sort both column names
    and entries when dumping table entries
  - Major fix in plugins to correctly handle the *-C* command line
    argument to dump table values from
  - Code refactoring in *lib/request.py* *getInband()* method
  - Major code review and restyling in plugins
  - Minor layout improvement in *lib/resume.py*
  - Minor fix in *getValue()* call in plugins
  - Minor fix in *lib/option.py* to correctly handle one-line User-Agent
    file
  - Added *__cleanupParameters()* method in *lib/option.py*
  - Some enhancement in *lib/dump.py* to correctly handle also the *-e*
    command line argument
  - Updated all documentation files, mainly README
    ([HTML](http://sqlmap.svn.sourceforge.net/viewvc/*checkout*/sqlmap/doc/README.html)
    and
    [PDF](http://sqlmap.svn.sourceforge.net/viewvc/*checkout*/sqlmap/doc/README.pdf))

### November 2007

  - **\[SpoC\]** Added support for SQL injection on HTTP *Cookie* and
    *User-Agent* headers
  - Added *lib/smdict.py* with *sqlmapDict* object definition used as
    the "knowledge base" for *self.args* and for queries object
  - Added *Common.getDocRoot()* and *Common.getDirectories()* functions
    for further development ;)
  - Added *Common.setDbms()* function to be used by plugin modules to
    set *self.args.fingerprint* and save remote DBMS value in log file
  - Added Oracle DBMS 11i detection in Oracle plugin
  - Updated documentation files
  - Complete code refactoring and cleanup
  - sqlmap 0.5 is out with all SpoC objectives accomplished and a lot of
    enhancements implemented too

## Links

  - [sqlmap
    ChangeLog](http://sqlmap.svn.sourceforge.net/viewvc/*checkout*/sqlmap/doc/ChangeLog)
  - [sqlmap last SVN revision log
    message](http://sqlmap.svn.sourceforge.net/viewvc/sqlmap?view=rev)