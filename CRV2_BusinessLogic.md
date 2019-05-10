## 1\. Business Logic Understanding

**Why to understand Business Logic?** A security review of the
application should uncover the commonly known security flaws as well as
the ones related to business logic of the application. And in order to
enumerate the business logic flaws it is important to develop
familiarity with its context/scope of the application.

**What points do we need to understand?**

The reviewer must develop familiarity with:

  - Application features and Business Rules: The reviewer must
    understand all the features of the application and capture all the
    business restrictions/rules related to them.

<!-- end list -->

  - Sensitive Data: The reviewer should also make a note of all the
    entities like account numbers, passwords that are sensitive to the
    application. The categorizing the data entities based on their
    sensitivity will help the reviewer to determine the impact of any
    kind of data loss in the application.

<!-- end list -->

  - User roles and access rights: It is important to understand the type
    of users allowed to access the application. Generally, an
    application that is accessible only for the internal users of an
    organization might be exposed to threats that are different than the
    one that is available for anyone on the Internet. Hence, knowing the
    users of the application and its deployed environment would allow
    the reviewer to realize the threat agents correctly. In addition to
    this, the different privileges levels present in the application
    must also be understood. It would help the reviewer to enumerate
    different security violations/privilege escalation attacks that can
    be applicable to the application.

<!-- end list -->

  - Application type – It refers to understanding whether the
    application is browser based application, a desktop based standalone
    application, a web-service, a mobile applications or a hybrid
    application. Different type of application faces different kinds of
    security threats and understanding the type of the application would
    help the reviewer to look for specific security flaws, determine
    correct threats agents and highlight necessary controls suitable to
    the application.

## 2\. Code Layout Understanding

**Why to understand Application?** It is required to understand the
design and the architecture of the application before reviewing its code
for security flaws. It would help the reviewer to understand the data
flow for any feature, familiarize with all the entry and exit points
present in the application and other integrations involved in it. A gist
of all the components present in the application and the way they
interact is helpful in threat modeling the whole system and defining a
proper scope of the security review.

**What points do we need to understand?**

One must understand:

  - Design: Generally applications have a well-defined code layout if
    they are developed using MVC design principle. Applications can have
    their own custom design or they may use some well-known design
    frameworks like Struts/Spring etc. The reviewer must understand the
    design of the application mainly with respect to the points listed
    below.

<!-- end list -->

  -   - Where are the application properties/configuration parameters
        stored?
      - How is the business class identified for any feature/URL?
      - What types of classes get executed for any processing any
        request? (e.g.: centralized controller, command classes, view
        pages etc.)
      - How is the view rendered to the users for any request? What are
        the components used to render the view (e.g.: Custom tags)

If the application is developed using an inbuilt/well-known design
framework the answers to the most of these questions would be
pre-defined. But, in case it is custom then these information will
surely aid the review process, mainly in capturing the data flow and
internal validations.

It will be also helpful to capture information regarding the following
elements, if they are used in the application design:

  -   - Design pattern like DAO, Business Delegate, etc.
      - Data Access Frameworks
      - Use of external API’s
      - Data Validation logic

<!-- end list -->

  -   - Is there any centralized validation logic present in the
        application like filters, request interceptors, etc.?
      - Is there is any common validation class/routine? When does it
        get invoked?

Architecture: Knowing the architecture of the application goes a long
way in understanding the security threats that can be applicable to the
application. Architecture of the application will also throw light on
the different servers used by the application (database server, web
server, etc.). Thus it will aid the reviewer to look for security flaws
pertaining to them or use this information in determining the
exploitability factor for any attack.

The reviewer must know about:

  -   - Entry points: The reviewer must understand all the sources
        through which the application accepts and processes the data
        like:
          - Web service Integrations
          - Invocation of external processes
          - Use of external files and data feeds
      - Trust boundaries: This to understand what is treated as trusted
        inputs by the application.

Both these points will aid the reviewer to understand all the critical
areas of the application and understand where all does it need to
enforce necessary validations before processing the inputs/commands.

Thus the knowledge about the design and the architecture of the
application would allow the reviewer to assess attack surfaces & come
with possible threats to the application.

**What methods can we follow?**

  - Discussions with the application design and development teams
  - Review of available documentation like Use Case diagrams, Design
    documents
  - Application walkthrough
  - Prior knowledge of the reviewer about the domain
  - Study of existing technologies and frameworks used by the
    application