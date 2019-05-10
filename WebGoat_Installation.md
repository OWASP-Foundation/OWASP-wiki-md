<webgoat/>[WebGoat User Guide Table of
Contents](WebGoat_User_Guide_Table_of_Contents "wikilink") __TOC__

WebGoat is a platform independent environment. It utilizes Apache Tomcat
and the JAVA development environment. Installers are provided for
Microsoft Windows and UN\*X environments, together with notes for
installation on other platforms.

## Installing Java and Tomcat

**Note**: This may no longer be necessary for v5.

### Installing Java

1.  Install and deploy the appropriate version from
    <http://java.sun.com/downloads/> (1.4.1 or later)

### Installing Tomcat

1.  Install and deploy core Tomcat from
    <http://tomcat.apache.org/download-55.cgi>

`Since the 5.5 version of Tomcat has been archived, the link above is not working anymore. `
` I suggest to follow the "which version?" link to identify the latest stable version: `<http://tomcat.apache.org/whichversion.html>` `
` At the moment the latest stable release is 7.0.50 : `<http://tomcat.apache.org/download-70.cgi>` `

` NOTE: WebGoat includes a very old version of catalina-4.1.9.jar.`
` To run WebGoat on Tomcat 7, you'll need to expand the war file`
` and delete this file from WEB-INF/lib`

## Installing to Windows

1.  Unzip WebGoat-OWASP_Standard-5.2.zip to your working environment.
2.  To start Tomcat, browse to the WebGoat directory unzipped above and
    double click "webgoat.bat"
3.  Start your browser and browse to:
    <u><http://localhost/WebGoat/attack></u> This link is
    case-sensitive. Make sure to use a large ‘W’ and ‘G’.

## Installing to Linux

1.  Unzip WebGoat-OWASP_Standard-x.x.zip to your working directory.
2.  Change "1.5" on lines 17, 19, and 23 of webgoat.sh to "1.6".
3.  Since the latest version runs on a privileged port, you will need to
    start/stop WebGoat & Tomcat either:

<!-- end list -->

1.  on port 80 as root:
        sudo sh webgoat.sh start80
        sudo sh webgoat.sh stop
2.  or on port 8080:
        sh webgoat.sh start8080
        sh webgoat.sh stop

</li>

</ol>

## Installing to OS X (Tiger 10.4+)

1.  Unzip WebGoat-OWASP_Standard-x.x.zip to your working directory.
2.  Change "1.5" on line 10 of webgoat.sh to "1.6".
3.  Since the latest version runs on a privileged port, you will need to
    start/stop WebGoat & Tomcat either:

<!-- end list -->

1.  on port 80 as root:
        sudo sh webgoat.sh start80
        sudo sh webgoat.sh stop
2.  or on port 8080:
        sh webgoat.sh start8080
        sh webgoat.sh stop

</li>

</ol>

## Installing on FreeBSD

1.  Install Tomcat and Java from the ports collection:
        cd /usr/ports/www/tomcat55
        sudo make install
2.  You will be required to manually [download the Java
    JDK](http://www.FreeBSDFoundation.org/cgi-bin/download?download=diablo-caffe-freebsd6-i386-1.5.0_07-b01.tar.bz2)
    to install it. Instructions are given by the ports system about when
    and how to do this.
3.  Unzip WebGoat-OWASP_Standard-x.x.zip to your working directory.
4.  Change "1.5" on lines 17, 19, and 23 of webgoat.sh to "1.6".
5.  Since the latest version runs on a privileged port, you will need to
    start/stop WebGoat & Tomcat either:

<!-- end list -->

1.  on port 80 as root:
        sudo sh webgoat.sh start80
        sudo sh webgoat.sh stop
2.  or on port 8080:
        sh webgoat.sh start8080
        sh webgoat.sh stop

</li>

</ol>

## Running

1.  Start your browser and browse to:
    <u><http://localhost/WebGoat/attack></u>. Notice the capital 'W' and
    'G'

`Warning: The "WebGoat" part of the path (the "context root") should exactly match (case-sensitive) the `
`war (web archive) that gets deployed. When you launch WebGoat, the console will have a line like:`

`INFO: Deploying web application archive webgoat.war`

`This means that your URL will be `<u><http://localhost/webgoat/attack></u>` -- note the lowercase "webgoat"`

1.  Login in as: user = guest, password = guest

## Building

Skip these instructions if you are only interested in running WebGoat.

WebGoat is built using eclipse WTP 1.5.x. Please read the instructions
at [Goodle
code](http://webgoat.googlecode.com/svn/trunk/webgoat/README.txt) to
build the WebGoat application.

## Installing WAR file to existing Tomcat server

Place the .war file in your Tomcat webapps directory (it will self
extract). You'll need to resolve several issues that are outlined in the
[Webgoat FAQ](http://code.google.com/p/webgoat/wiki/FAQ).

Return to the [WebGoat User Guide Table of
Contents](WebGoat_User_Guide_Table_of_Contents "wikilink")

[Category:OWASP WebGoat
Project](Category:OWASP_WebGoat_Project "wikilink")