**'[Back to SpoC 007 Selection
page](http://www.owasp.org/index.php/OWASP_Spring_Of_Code_2007_Selection)**

**AoC Candidate**: EdFinkler

**Project coordinator**: Andrew v d Stock

**Project Progress**: 100% Complete, [Progress
Page](SpoC_007_-_Inspekt:_Input_filtering_and_validation_library_for_PHP_-_Progress_Page "wikilink")

## EdFinkler - Inspekt: Input filtering and validation library for PHP

### About Me

I received a Bachelor's Degree in English from Indiana University in
1997. I've been a web developer since 1996, and a PHP developer since
1999. I worked for four years as Supervisor of Web Development at Golden
Dome Media, and have spent my last six years as Web and Security Archive
Administrator for CERIAS, the [Center for Education and Research in
Information Assurance and Security](http://www.cerias.purdue.edu), at
Purdue University.

I am a member of the [PHP Security Consortium](http://phpsec.org), and
creator/project lead on PHPSecInfo, a [PHP environment security auditing
tool](http://phpsecinfo.com). I regularly speak on web application
security issues, and am an advocate of secure programming practices via
CERIAS and as a member of the PHP and larger web development community.

### The state of PHP application development

The state of application development in PHP is worrisome. Reviewing the
NIST NVD data from 2006 reveals that **over 40% of all vulnerabilities
reported were PHP application vulnerabilities** -- not vulnerabilities
in the language itself, but errors in proper coding practice. I believe
that to address the widespread problem of insecure PHP application
development, new development paradigms are required. The typical
approach of easy, direct interaction with input is inherently
problematic, even for a programmer with strong security practices. The
developer should be forced to consider his or her expectations for the
data, and apply appropriate filtering/validation to ensure that those
expectations are correct. For the cases where raw input is required, the
developer should be forced to **demonstrate clear intent**, much moreso
than simply using the assignment operator. This will, I believe, make it
**easier to develop secure applications in PHP**, and **harder to
develop insecure ones**.

### Creating a new paradigm

We have a strong foundation for a new paradigm in
[Zend_Filter_Input](http://funkatron.com/wp/wp-content/ZFI_docs.pdf),
a component of the Zend Framework developed by PHP security expert
[Chris Shiflett](http://shiflett.org). Disappointingly, the component
was dropped from the framework, a move I and many others strongly
disagreed with. After some discussions with Chris and others, I feel
that the best approach would be to resurrect Zend_Filter_Input, making
it framework-independent and addressing existing limitations.

### The details and examples

Essentially, this system would act as a sort of "firewall" API between
user input and the rest of the application. By default, the constructor
would take an array, assign it to an internal property, and set the
passed array to NULL. By setting up filter objects from the standard
user input superglobals, developers would be forced to access all data
via the filter system's API. A developer must demonstrate clear intent
in order to get unfiltered data.

### Usage examples

Note that in these examples, I've used the name "InputFilter" for the
filter system. This will likely change when I can come up with something
snazzier.

    // Typical ZFI-style usage
    $f_post = new InputFilter($_POST);


    // $_POST['searchtext'] == "<strong>hello</strong>";
    $comment = $f_post->noTags('comment');
    // $comment === "hello";
    $comment_raw = $f_post->getRaw('comment');
    //$comment_raw === "<strong>hello</strong>";


    // makePostFilter would be a helper method that retrieves the $_POST array,
    // wraps the data in an InputFilter, and nullifies the $_POST array
    $f_post = InputFilter::makePostFilter();


    // get email
    if ( $email = $f_post->isEmail('email') ) {
          echo "Valid email address";
    } else {
        echo "Not a valid email address";
    }

    // automatically strip all html tags and bbcode tags from POST input.
    // This kind of input restriction would also be configurable via
    // external conf files
    $restrictions = array('noHTML','stripBBCode');
    $f_post = InputFilter::makePostFilter($restrictions);

### Bootstrap file example

    <?php
        // standard bootstrap file
        require '/path/to/inputfilterclass.php';

        $if = new InputFilter();
        $if->loadConfig('/path/to/configfile/inputfilter.conf');
        $if->buildStandardFilters(); // builds from $_GET, $_POST, $_COOKIE, $_SERVER

        // the make*Filter methods use a singleton pattern to retrieve prebuilt filter objects
        $f_post = $if->makePostFilter();
        $f_get  = $if->makeGetFilter();
        $f_cookie = $if->makeCookieFilter();
        $f_server = $if->makeServerFilter();

        // $_POST, $_GET, $_COOKIE and $_SERVER are now all NULL
        // Only way to access this data is via the $f_* objects

    ?>

### Key improvements over Zend_Filter_Input

  - Provide retrieval and filtering support for multidimensional arrays
  - Provide solutions for scoping issues (avoid the need for "global"
    keywords everywhere)
  - A variety of helper methods to reduce code verbosity
  - Block deprecated HTTP_\*_VARS and other ways to grab input data
    without filtering
  - Auto-restrictions on input defined programatically or via
    configuration files
  - Compatible with PHP4 and PHP5
  - Self contained; not reliant on external libraries
  - Able to work with a wide variety of frameworks and app
    architectures; easily "pluggable" into any given web app

### Responsibilities

I expect to be responsible for all development and documentation. I will
rely on the expertise of various members of the PHP security community
for input and criticism, and hope to receive advocacy support from them
as well. The development process will be open, and I intend to release
code throughout to gather feedback.

### Development milestones

Dates assume an April 9th start

  - April 16th: Untethering the Zend_Filter_Input code from the Zend
    Framework
  - April 23rd: Rewriting PHP5-specific portions to work in PHP4
  - May 1st: Development of approach to address scoping issues (a big
    plus of the $_\* superglobals is that they are always available in
    all scopes automatically)
  - May 3rd: Initial release of code (continues throughout at
    appropriate points)
  - May 10th: Addition of a variety of "helper" methods to make filtered
    input object creation and interaction easier
  - May 20th: Addition of automatic input "restriction" filters
  - July 1st: Addition of input filtering system configuration via
    external config files
  - July 1st: Full API doc generated from phpDoc-style documentation
  - July 9th: Detailed usage documentation, including examples of
    bootstrapping and methods of integration with various frameworks.
    Example source code included.
  - July 9th: PEAR channel for packaged distribution
  - Ongoing: Advocacy. PR via interviews and news items about releases;
    writing articles demonstrating the system for various sources;
    presentations via the web and at major PHP conferences.
  - Ongoing: Work with major PHP app devs and framework devs to
    integrate the system -- or encourage the development of similar
    approaches -- within their projects.

**[Back to SpoC 007 Selection
page](http://www.owasp.org/index.php/OWASP_Spring_Of_Code_2007_Selection)**