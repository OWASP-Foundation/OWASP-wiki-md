<webgoat/>[WebGoat User Guide Table of
Contents](WebGoat_User_Guide_Table_of_Contents "wikilink") __TOC__

In order to start using WebGoat, Tomcat must be launched using the
startup script/bat in the Tomcat bin directory. For WebGoat to operate
it must have permission to run as a server and allow some uncommon web
behavior. When WebGoat is running it will make the host machine
vulnerable to attack.

If the machine is connected to the internet it should be disconnected.

Running a personal firewall may prevent WebGoat from operating
correctly. Disable any personal firewall while running WebGoat.

From a browser, the Tomcat server can be accessed on localhost port 80,
e.g. <u><http://127.0.0.1></u>

WebGoat resides in the WebGoat directory, and the lessons can be found
at: <u><http://127.0.0.1/WebGoat/attack></u>.

The WebGoat application enforces role based security. A login dialog
requests credentials. Login as userid=guest, password=guest.

![WebGoat_Sign_In_Page.gif](WebGoat_Sign_In_Page.gif
"WebGoat_Sign_In_Page.gif")

After a successful login the Tomcat server will show the WebGoat welcome
page.

![WebGoat_Welcome_Page.gif](WebGoat_Welcome_Page.gif
"WebGoat_Welcome_Page.gif")

[WebGoat User Guide Table of
Contents](WebGoat_User_Guide_Table_of_Contents "wikilink")

[Category:OWASP WebGoat
Project](Category:OWASP_WebGoat_Project "wikilink")