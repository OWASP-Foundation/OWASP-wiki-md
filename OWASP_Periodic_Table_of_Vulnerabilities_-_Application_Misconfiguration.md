[Return to Periodic Table Working
View](OWASP_Periodic_Table_of_Vulnerabilities#Periodic_Table_of_Vulnerabilities "wikilink")

## Application Misconfiguration

### Root Cause Summary

Software applications are very complex; to ease installation and
configuration of the application, many software packages come
preconfigured with vulnerabilities right out of the box. Application
misconfigurations are not coding issues. They are options and/or
features in the application that can be easily exploited, such as:

  - Special access mechanisms
  - Default usernames and passwords
  - Default configuration file settings
  - Security settings at the lowest possible level

Due to the complexity of configuration, certain combinations of settings
might expose vulnerabilities, though each individual setting may be safe
on its own.

### Browser / Standards Solution

None

### Perimeter Solution

All application permissions, configurable components and files should be
given least privilege for the specific platform and technology stack.
The application should prominently warn users/administrators when an
insecure setting is in use (as it might be temporarily during deployment
or in a staging environment).

### Generic Framework Solution

None

### Custom Framework Solution

None

### Custom Code Solution

None

### Discussion / Controversy

Application misconfiguration is not a coding issue and can be difficult
secure due to the complexities of applications and networks and is a
perfect example of the “Security, Functionality, and Ease of Use
Triangle”. The easier the application is to use the less secure it may
be.

### References

[Application Misconfiguration WASC
TC](http://projects.webappsec.org/w/page/13246914/Application%20Misconfiguration)
[CAPEC-348 WASC Threat Classification 2.0 – WASC – 15 Application
Misconfiguration](http://capec.mitre.org/data/definitions/348.html)