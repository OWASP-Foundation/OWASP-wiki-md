Security code review aims to identify security flaws in the application
related to its features and design along with their exact root causes.
With the increasing complexity of the applications and the advent of new
technologies the traditional way of testing may fail to detect all the
security flaws present in the applications. Thus, there is a need to
understand the code of the application, external components,
technologies and configurations to be able to uproot all the flaws in
different kinds of applications. Such a deep dive into the application
code also helps in determining exact mitigation techniques that can be
used to avert the security flaws. Let’s look in further detail of the
benefits of security code reviews.

  - **Root cause analysis (Source to sink)** – There are various reasons
    why security flaws manifest in the application like lack of
    validation, parameter mishandling etc. During the assessment, the
    code is thoroughly studied and such flaws are checked. In the
    process the exact root cause of the flaws are captured. The complete
    data flow is traced and source to sink analysis is carried out.
    Source to sink analysis here means to determine what are possible
    inputs to the application i.e. source, and how are they being
    processed by it. Sink refers an insecure code pattern like for
    instance, a dynamic SQL query. So, its analyzing what is the source
    (input) and the sink (vulnerable code pattern) for any
    vulnerability. Consider a scenario where the source is a user input.
    It flows through the different classes/components of the application
    and finally falls into a concatenated SQL query i.e. a sink, and
    there is no proper validation being applied to it in the path. In
    this case the application will be vulnerable to SQL Injection
    attack, as identified by the source to sink analysis. Such an
    analysis exactly helps in understanding which vulnerable inputs can
    lead to a possibility of an exploit in the application.

<!-- end list -->

  - **Design Analysis** – Design is an important aspect of security code
    review. The dynamic testing approach does not involve design
    analysis, which also serves as it one of the limitations. The design
    flaws are difficult to uncover and requires knowledge of the entire
    data flow, input sources, integrations and all the configurations of
    the application. Thus, the flaws related to mishandling of non-user
    inputs and external integrations like server to server, which are
    unlikely to get covered in a dynamic testing approach can be easily
    determined in a security code review. It covers the end-to-end
    analysis of the application

<!-- end list -->

  - **All Instances of the Vulnerabilities** – Once a flaw is identified
    the next step of the security code review process is to enumerate
    its all the possible instances present in the application. Through
    security code reviews we can uncover insecure patterns present in
    all the files of the application. Here, all insecure instances
    includes the list of different the insecure code patterns that lead
    to a vulnerability and all of their occurrences. For instance, an
    application can be vulnerable to XSS vulnerability because of use of
    unvalidated inputs in insecure display methods like scriplets,
    response.write method etc. at several places.

<!-- end list -->

  - **Uncommon Security Flaws** – Security code reviews is very specific
    to the application being reviewed. It may highlight some flaws that
    are new or specific to the code implementation of the application
    like insecure termination of execution flow, synchronization error
    etc. These flaws can only be uncovered if we understand the
    application code flow and its logic well. Thus, security code review
    is not just about scanning the code for set of unknown insecure code
    patterns. But it also involves understanding the code implementation
    of the application and enumerating the flaws specific to it.

<!-- end list -->

  - **Limitations of Existing Security Controls** – The application
    being reviewed might have been designed with some security controls
    in place like centralized blacklist validation etc. or there could
    be some inbuilt validation/security controls present in the
    application platform being used. These security controls must be
    studied carefully to identify if they are fool-proof. According to
    the implementation of the control, the nature of attack or any
    specific attack vector that can be used to bypass it, must be
    analysed. Enumerating the weakness in the existing security control
    is another important aspect of the security code reviews.

<!-- end list -->

  - **Specific Recommendations** – The security code reviews also helps
    to come up with mitigation techniques that can best suit the
    application, instead of a generic one.