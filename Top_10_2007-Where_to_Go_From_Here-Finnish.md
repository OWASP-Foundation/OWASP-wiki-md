The OWASP Top 10 is just the beginning of your web application security
journey.

*The world's six billion people can be divided into two groups: group
one, who know why every good software company ships products with known
bugs; and group two, who don't. Those in group 1 tend to forget what
life was like before our youthful optimism was spoiled by reality.
Sometimes we encounter a person in group two Ã¢ÂÂ¦who is shocked that
any software company would ship a product before every last bug is
fixed.* *Eric Sink, Guardian May 25, 2006*

Most of your users and customers are in group two. How you deal with
this problem is an opportunity to improve your code and the state of web
application security in general. Billions of dollars are lost every
year, and many millions of people suffer identity theft and fraud due to
the vulnerabilities discussed in this document.

## For Architects and Designers

To properly secure your applications, you must know what you are
securing (asset classification), know the threats and risks of
insecurity, and address these in a structured way. Designing any
non-trivial application requires a good dose of security.

  - **Ensure that you apply "just enough" security** **based upon threat
    risk modeling and asset classification**. However, as compliance
    laws (SOX, HIPAA, Basel, etc.) place increasing burdens, it may be
    appropriate to invest more time and resources than satisfies the
    minimum today, particularly if best practice is well known and is
    considerably tougher than the minimum
  - **Ask questions about business requirements**, particularly missing
    non-functional requirements
  - Work through the [OWASP Secure Software Contract
    Annex](OWASP_Secure_Software_Contract_Annex "wikilink") with your
    customer
  - **Encourage safer design** Ã¢ÂÂ include defense in depth and
    simpler constructs through using threat modeling (see \[HOW1\] in
    the book references)
  - **Ensure that you have considered confidentiality, integrity,
    availability , and non-repudiation**
  - **Ensure your designs are consistent with security policy and
    standards**, such as COBIT or PCI DSS 1.1

## For Developers

Many developers already have a good handle on web application security
basics. To ensure effective mastery of the web application security
domain requires practice. Anyone can destroy (i.e. perform penetration
testing) Ã¢ÂÂ it takes a master to build secure software. Aim to
become a master.

  - Consider [joining OWASP](Membership "wikilink") and attending [local
    chapter](:Category:OWASP_Chapter "wikilink") meetings
  - **Ask for secure code training** if you have a training budget. Ask
    for a training budget if you donÃ¢ÂÂt have one
  - **Design your features securely** Ã¢ÂÂ consider defense in depth
    and simplicity in design
  - **Adopt coding standards** which encourage safer code constructs
  - **Refactor existing code to use safer constructs** in your chosen
    platform, such as parameterized queries
  - *'Review the **[OWASP Development
    Guide](OWASP_Guide_Project "wikilink")** and start applying selected
    controls to your code*'. Unlike most security guides, it is designed
    to help you build secure software, not break it
  - **Test your code for security defects** and make this part of your
    unit and web testing regime
  - **Review the book references**, and see if any of them are
    applicable to your environment

## For Open Source Projects

Open source is a particular challenge for web application security.
There are literally millions of open source projects, from one developer
personal projects through to major projects such as Apache, Tomcat, and
large scale web applications, such as PostNuke.

  - Consider [joining OWASP](Membership "wikilink") and attending [local
    chapter](:Category:OWASP_Chapter "wikilink") meetings
  - If your project has more than 4 developers, **consider making at
    least one developer a security person**
  - **Design your features securely** Ã¢ÂÂ consider defense in depth
    and simplicity in design
  - **Adopt coding standards which encourage safer code constructs**
  - **Adopt the responsible disclosure policy** to ensure that security
    defects are handled properly
  - **Review the book references**, and see if any of them are
    applicable to your environment

## For Application Owners

Application owners in commercial settings are often time and resource
constrained. Application owners should:

  - Work through the [OWASP Secure Software Contract
    Annex](OWASP_Secure_Software_Contract_Annex "wikilink") with the
    software producers
  - **Ensure business requirements include non-functional requirements
    (NFRs) such as security requirements**
  - **Encourage designs which include secure by default features**,
    defense in depth and simplicity in design
  - **Employ (or train) developers who have a strong security
    background**
  - **Test for security defects** throughout the project: design, build,
    test, and deployment
  - **Allow resources, budget and time in the project plan to remediate
    security issues**

## For C-level Executives

Your organization must have a secure development life cycle (SDLC) in
place that suits your organization. Vulnerabilities are much cheaper to
fix in development than after your product ships. A reasonable SDLC not
only includes testing for the Top 10, it includes:includes:

  - For off the shelf software, **ensure purchasing policies and
    contracts include security requirements**
  - For custom code, '''adopt secure coding principles in your policies
    and standards '''
  - **Train your developers in secure coding techniques** and ensure
    they keep these skills up to date
  - **Include security-relevant code analysis tools in your budget**
  - **Notify your software producers of the importance of security to
    your bottom line**
  - **Train your architects, designers, and business people in web
    application security fundamentals**
  - **Consider using third-party code auditors**, who can provide an
    independent assessment
  - **Adopt responsible disclosure practices** and build a process to
    properly respond to vulnerability reports for your products