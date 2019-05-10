## Introduction

Hopefully, whether you are a Java programmer or not, you read Jeff
Williams' article last week on how Java developers should learn from
what Microsoft is doing in security. This is good advice for all of us.
Rather than fall into political wars, we need to look at the good and
bad of other technologies and see how they can be applied to our
situation. That is exactly what Microsoft did in developing .NET. They
looked at various technologies, languages, architectures, tools, etc. in
determining the approach for .NET. We will look at one of those concepts
this week and how .NET takes ideas from Java and C++ and provides a
significant security improvement over previous ASP applications. Let's
look in on David, a would be attacker, who is trying his best to
compromise a typical ASP application.

## Everything's Coming up Errors

David absent mindedly brushed the hair out of his eyes, took another sip
from his Dilbert coffee mug, and focused his eyes on the computer screen
in front of him. Over the past hour, David had been attacking the web
site of Sample Company, looking for a vulnerability to exploit that
would grant him access to their corporate database. Finding a
vulnerability had been the easy part. Within minutes of accessing the
site, David had located a SQL Injection vulnerability that could allow
him to access all of the information in the database, if he could just
determine how to exploit it. But that was where things began to fall
apart. Although he would never admit it to anyone, David was a little
out of his league here. He envisioned himself as an elite hacker and had
certainly been able to impress his friends on occasion. However, now
that he was beyond his simple bag of tricks, he found himself confused
as to what approach to take.

He rose and looked out the window at the rain hitting the pavement
below. He felt he was close to getting in, but all he had been able to
do up to this point was generate errors. Every time he tried to work
around one error, he just seemed to be faced with a new one. The phone
ringing jarred David from his thoughts. His best friend, Johnny, was on
the line. Twenty minutes and two cups of coffee later, David hung up the
phone. Johnny and he had been talking about a girl that Johnny was
interested in. He had been pursuing her for weeks with no progress to
speak of. A few days ago Johnny had decided to take a different approach
and play it cool. He had called to let David know that there seemed to
be some progress. Johnny was pretty excited about the whole thing. David
figured that once she got to know Johnny, it would all wear off. David
sat down and tried to gather his thoughts again.

As he looked over the error messages he had generated, David thought
about how he was in the same position Johnny had been a few days ago. He
decided to take the same approach and stop what he was doing and try a
different slant. Rather than looking at the error messages as failures,
he started to look at what they might be telling him. Within a few
minutes, David realized he was on to something. While he did not have
direct access to the database, he had learned more information than he
had realized at first. He scrawled his thoughts on a scrap of notebook
paper and sat back to study them further.

The error message on his screen read:

Microsoft OLE DB Provider for SQL Server error '80040e14' Column
'newsTBL.NEWS_ID' is invalid in the select list because it is not
contained in an aggregate function and there is no GROUP BY clause.
G:\\WEBSITES\\WWW.SAMPLECOMPANY.COM/internal/dbSys.inc, line 241

From that, David felt like he had learned a lot of information. Some of
the information he realized he now was aware of included:

:\* The application uses OLE DB to communicate to the database

:\* The application uses Microsoft SQL Server as the database

:\* SQL commands can be passed to the database

:\* There is a table called newsTBL in the database

:\* The newsTBL table contains a field called NEWS_ID

:\* The application is stored in the G:\\Websites\\www.samplecompany.com
directory on the web server

:\* There is a directory called internal on the website

:\* There is an internal file called dbSys.inc on the website

:\* Line 241 of the dbSys.inc page contains code to execute a SQL
statement

## Application Attacks for Dummies

Now that his focus had changed, David found many of the errors he had
generated during his attacks had not been useless, but had generated
useful information he had simply overlooked. In an earlier set of
attacks, David had generated the following error message over and over:

"All queries in an SQL statement containing a UNION operator must have
an equal number of expressions in their target lists."

However, when he had exactly six columns in the SQL command he was
trying to inject, he received a different error message about the data
types not matching. Before, he had simply been frustrated. Now he
realized that the system had been telling him that there were six
columns being selected in the SQL command of the application.

In a similar fashion, errors David had generated such as:

:\* "Invalid object name 'tblUsers'."

:\* "The number '99999999999999999999999999999999999999999999999999' is
out of the range for numeric representation (maximum precision 38)."

:\* "Syntax error converting the nvarchar value 'tblAdmin' to a column
of data type int."

had actually disclosed information about the database schema, the table
names, column names, field sizes, etc. David began to think how the
error messages acted as a debugger. Whenever he made a syntax error in
the attack, the error messages actually assisted him in finding where
the errors were and how to tweak the attack. If the application
developers had realized how much information they were disclosing when
they created this "attacker debugger", they would never have released
the application.

David began following the directions from the error messages and within
a few minutes, he had coaxed the application into revealing the field
names and data types of the SQL command he had been attacking.

Armed with this new approach, David was able to extract the rest of the
database schema as well as the data stored in the tables. Now that he
had a debugger to assist him, David felt a lot more powerful and
couldn't wait to take on the next application. He poured a fresh cup of
coffee and realized he needed to call Johnny to let him know about some
real progress.

## .NET Error Handling

Michael read the memo from the architecture team with great interest. As
the lead developer for one of the new .NET projects, these new
guidelines on error handling would need to fit in with the architecture
he was planning. Michael sat back to think about last fall, when the
company realized that an attacker had walked through their entire
database and extracted information at will. When suspicions arose that
an attacker had compromised the system, Sample Company brought in an
outside security consultant who had demonstrated how the attacks had
been conducted and the role that error messages had played in the
attack. From the error messages in the logs, it appeared the attacker
had not been an elite hacker, but had still been able to compromise the
system within a few hours. Michael remembered the long nights and
weekends as they painstakingly went through all of their applications,
applying patches and retesting the code.

While .NET was not a silver bullet, Michael realized that it did offer
some techniques that could greatly assist his team in trying to handle
errors in a secure manner. Michael remembered implementing ASP code such
as "On Error Resume Next" and trying to make sure they hadn't missed any
of the pages. The new features of .NET would allow them to implement
superior error handling with significantly less risk.

Michael read one of the paragraphs again:

  -

      -
        "On .NET applications, there are multiple distinct mechanisms,
        which can be used to help prevent these types of error messages
        from being displayed to a user. These mechanisms may be used
        independently, or multiple techniques may be used in combination
        to provide complete coverage."

Michael decided to implement a combination technique where he used
contextual error handling such as Exceptions and Page_Error events for
handling errors where he could provide more context to the error message
or logs. For a safety net, he would use backup techniques, such as the
Application_Error event or the Application Configuration File to ensure
no error messages were missed and inadvertently disclosed to an
attacker. These techniques fit well into the new n-tier architecture
Michael was proposing and would hopefully help in keeping Michael from
spending more weekends patching his application. He understood from last
year's assessments that error handling would not prevent any of the
attacks and that other measures would have to be taken to prevent such
vulnerabilities as SQL Injection. However, Michael was determined to
avoid creating another attacker debugger and making things any easier
that necessary for the next would be hacker.

## Conclusion

If application developers realized how much information they disclose
when they routinely create these types of "attacker debuggers", they
would not sleep so easily. We often make the job of the attacker so easy
that applications can be compromised with little effort. We disclose so
much information that even an incompetent attacker can figure out how to
exploit the application.

Part of the problem is due to a lack of understanding by application
developers. This is the issue we try to deal with at OWASP through the
Guide, Top Ten List, columns and various other mechanisms. The other
part of the problem is due to tools and languages that make secure error
handling difficult to implement. In this area, Microsoft has taken a big
leap forward with .NET from the ASP error handling model.

Whichever technique or combination of techniques are utilized, all
exceptions from the database, file handling, etc. should be caught and
logged, but never displayed back to the user. Only general error
messages should be displayed back to the user to avoid disclosing
internal or sensitive information to an attacker.

## For More Information

:\# [Exception
Handling](http://support.microsoft.com/default.aspx?scid=http://support.microsoft.com:80/support/kb/articles/Q301/2/83.ASP&NoWebContent=1)

:\# [Page_Error, Application_Error and Application Configuration
File](http://support.microsoft.com/default.aspx?scid=kb;en-us;306355)

:\# [OWASP Top Ten List - Error
Handling](Improper_Error_Handling "wikilink")

-----

[Jeremy Poteet](mailto:jpoteet@appdefense.com?subject=feedback) is one
of the leaders for the OWASP Guide and an active member of the OWASP
Testing Methodology Project. He also acts as the liaison officer for the
WAS-TC at OASIS and is a member of the AVDL TC. He is the Chief Security
Officer for [appDefense](http://www.appdefense.com/) and a CISSP. Jeremy
is the co-author of "Extreme Programming with Ant" and was the winner of
eWeek's OpenHack IV competition.

[Category:OWASP Columns](Category:OWASP_Columns "wikilink")
[Category:OWASP Code Review
Project](Category:OWASP_Code_Review_Project "wikilink")