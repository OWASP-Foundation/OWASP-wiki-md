Scala language , just as JAVA , offers different types of Security
Frameworks you can work with. Depending on the task, here we offer some
general guidelines regarding the proper use of them The following table
contains the most popular ones and their security in terms of modules
and implementation

# Security Frameworks

The following Scala frameworks contain modules that help developers
implement secure features such as Authentenciation, Authorization, CRSF
or SQLInjection

| Framework                                                                                           | Authentication | Authorization | CSRF | XSS | SQLInjection |
| --------------------------------------------------------------------------------------------------- | -------------- | ------------- | ---- | --- | ------------ |
| [Play](https://www.playframework.com/documentation/2.0.4/ScalaSecurity)                             |                | ✓             |      | ✓   |              |
| [Deadbolt 2](http://deadbolt.ws/#service)                                                           |                |               |      | ✓   |              |
| [Play-pac4j](https://github.com/pac4j/play-pac4j)                                                   |                | ✓             |      | \-  |              |
| [Scala-oauth2-provider](https://auth0.com/authenticate/scala/oauth2/)                               |                | ✓             |      | \-  |              |
| [SecureSocial](http://www.securesocial.ws/)                                                         |                | ✓             |      | \-  |              |
| [Silhouette - Play Framework Library](https://www.silhouette.rocks/)                                |                | ✓             |      | \-  |              |
| [Lift](https://liftweb.net/)                                                                        |                | ✓             |      | ✓   |              |
| [Akka (Akka-http)](https://index.scala-lang.org/akka/akka-http/akka-http-core/10.0.10?target=_2.12) |                | ✓             |      | ✓   |              |
| [Spray](http://spray.io/)                                                                           |                | ✓             |      | ✓   |              |

## Secure Coding - Scala Frameworks

The following is a series of documents regarding the security
configurations for the above mentioned frameworks
<https://www.owasp.org/index.php/Scala_Frameworks/Play>

## Vulnerable Framework Components

It is essential that developers implement regular dependency checks of
their components, since most Scala projects will make use of the above
mentioned frameworks. Consider using
<https://www.owasp.org/index.php/OWASP_Dependency_Check> Which has a
Scala plugin for this purpose
<https://github.com/albuch/sbt-dependency-check>

## Reference

<https://www.47deg.com/blog/security-frameworks-for-scala/>

[Category:Technology](Category:Technology "wikilink")
[Category:Language](Category:Language "wikilink")
[Category:Scala](Category:Scala "wikilink")