This page will have information about how to analyze the MVC Part of the
Spring Framework using O2

### Spring MVC info

  - [Spring MVC 3.0 MVC Binding
    Rules](http://diniscruz.blogspot.com/2009/09/spring-mvc-30-mvc-binding-rules.html)

### O2 support for Spring MVC

<http://deploy.o2-ounceopen.com/O2_Cmd_SpringMvc/>

### Vulnerabilities in the JPetStore sample application

Start by downloading the files from
<http://deploy.o2-ounceopen.com/DemoFiles/SpringMvc/>

#### Auto-Binding on EditOwner.do

Draft explanation:

    Install a clean copy of pet clinic on Tomcat.
    Use Firefox + LiveHttpHeaders or similar
    List the owners.
    Select owner 2 (Betty Davis).
    Click edit.
    Make a trivial change.
    Click edit again.
    Use LiveHttpHeaders replay to replay the previous edit but modify the POST body
    from:
    firstName=Betty&lastName=Davis&address=638+Cardinal+Ave&city=Sun+Prairie&telephone=6085551749

    to:
    firstName=Betty&lastName=Davis&address=638+Cardinal+Ave&city=Sun+Prairie&telephone=6085551749&pets[0].owner.id=3

    The upshot is that you end up over-writing owner 3 with Betty Davis's info even
    though the URL that the POST goes to is:
    http://localhost:8080/petclinic/editOwner.do?ownerId=2