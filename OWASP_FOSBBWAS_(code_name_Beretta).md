Download: <http://www.devcafe.co.uk/beretta/downloads.htm>

This project aims to create a:

  - Commercial quality open source black box web application scanner
    that is:
      - Extensible
      - Customizable
      - Scaleable
      - Robust
      - User Friendly
      - Methodical
  - The objective is to:
      - Help developers to create secure and robust Web applications
      - Help System administrators and professional Pen-Tester to
        identify vulnerable Web Applications
      - Create tests for the OASIS WAS database, [OWASP Testing
        Guide](http://prdownloads.sourceforge.net/owasp/OWASPTesting_PhaseOne.pdf?download)
        and

[OWASP PenTesting
Checklist](http://prdownloads.sourceforge.net/owasp/OWASPWebAppPenTestList1.1.pdf?download)

## Installation

  - Unzip the downloaded files (duh..\!)
  - Restore the Beretta Db file to your SQL 2000 database server and
    create a user to access this database
  - Move the unzipped Beretta application directory to somewhere in your
    web server root
  - Set the necessary NTFS permissions
  - Create a virtual directory in IIS to this newly created directory
  - Modify the Web.config keys databaseConnection, and siteRoot to the
    relevant values.
  - Modify the Web.config key "outputDir" to be the physical path of the
    "output" directory beneath the web application root. XML scan
    reports will be created here
  - Make sure \~/output/ has write permissions for the user ASP.net is
    running under
  - Open up an internet browser and browse to the virtual directory you
    created
  - Enter login details (defaults below)

Username: admin Password: pass

  - You should now be logged into the application. Foundstones hacme
    bank is a good place to start experimenting with Beretta.

[link not working](Category:FIXME "wikilink") [Category:OWASP .NET
Project](Category:OWASP_.NET_Project "wikilink")