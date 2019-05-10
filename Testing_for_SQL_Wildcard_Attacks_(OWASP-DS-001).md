## Brief Summary

SQL Wildcard Attacks are about forcing the underlying database to carry
out CPU-intensive queries by using several wildcards. This vulnerability
generally exists in search functionalities of web applications.
Successful exploitation of this attack will cause Denial of Service.

## Description of the Issue

SQL Wildcard attacks might affect all database back-ends but mainly
affect SQL Server because the MS SQL Server LIKE operator supports extra
wildcards such as "\[\]","\[^\]","_" and "%".
In a typical web application, if you were to enter "foo" into the search
box, the resulting SQL query might be:

`SELECT * FROM Article WHERE Content LIKE '%foo%'`

In a decent database with 1-100000 records the query above will take
less than a second. The following query, in the very same database, will
take about 6 seconds with only 2600 records.

`SELECT TOP 10 * FROM Article WHERE Content LIKE '%_[^!_%/%a?F%_D)_(F%)_%([)({}%){()}£$&N%_)$*£()$*R"_)][%](%[x])%a][$*"£$-9]_%'`

So, if the tester wanted to tie up the CPU for 6 seconds they would
enter the following to the search box:

`_[^!_%/%a?F%_D)_(F%)_%([)({}%){()}£$&N%_)$*£()$*R"_)][%](%[x])%a][$*"£$-9]_`

## Black Box testing and example

**Testing for SQL Wildcard Attacks:**
Craft a query which will not return a result and includes several
wildcards. You can use one of the example inputs below.
Send this data through the search feature of the application. If the
application takes more time generating the result set than a usual
search would take, it is vulnerable.

### Example Attack Inputs to send

  - '%_\[^\!_%/%a?F%_D)_(F%)_%(\[)({}%){()}£$\&N%_)$\*£()$\*R"_)\]\[%\](%\[x\])%a\]\[$\*"£$-9\]_%'
  - '%64_\[^\!_%65/%aa?F%64_D)_(F%64)_%36(\[)({}%33){()}£$\&N%55_)$\*£()$\*R"_)\]\[%55\](%66\[x\])%ba\]\[$\*"£$-9\]_%54'
    *bypasses modsecurity*
  - _\[r/a)_ _(r/b)_ _(r-d)_
  - %n\[^n\]y\[^j\]l\[^k\]d\[^l\]h\[^z\]t\[^k\]b\[^q\]t\[^q\]\[^n\]\!%
  - %_\[aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa\[\! -z\]@$\!_%

...
**Result Expected:**
If the application is vulnerable, the response time should be longer
than usual.


### How to craft search strings for testing

  - Queries should return as few results as possible or even none at
    all. In this way, we can be sure that we actually forced the
    database server to search all records.
  - During the OR combinations, every OR statement should be different,
    otherwise the database will optimize it. Changing one character is
    enough.
  - In Microsoft SQL Server, every character after an open bracket
    **\[** causes unusually long execution time. This can be used to
    improve the effect, for example:
      - LIKE '%_\[a\[\! -z\]@$\!_% - 1050 ms.
      - LIKE '%_\[aaaaaaaaa\[\! -z\]@$\!_%' - 1600 ms.
      - LIKE '%_\[aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa\[\!
        -z\]@$\!_%' - 3700 ms.
  - Longer queries will generally result in longer execution time. Craft
    the longest possible query allowed by the application.
  - Starting with % and ending with % will generally cause longer
    running queries.
  - Some search implementations may cache search results. During the
    testing, every search query should be slightly different to avoid
    this.
  - Performance is always about experimenting. Try different
    combinations to find the most expensive queries for that particular
    target system and data.

## Gray Box testing and example

**Testing for SQL Wildcard Attacks:**

Query execution times can be observed in the database server, if certain
queries take longer time it can be an indication of SQL wildcard
attacks.

To test against application layer DoS attacks, it's important to watch
HTTP logs and analyze response times. If the response times of certain
pages in certain queries is longer than usual, those pages might be
susceptible to SQL wildcard attacks.

## References

**Whitepapers**
\* [DoS Attacks Using SQL
Wildcards](http://www.portcullis.co.uk/uplds/wildcard_attacks.pdf)
**Tools**
\* Testing can be done manually. Also, a [fuzzer](Fuzzing "wikilink")
can employed to automate the process.