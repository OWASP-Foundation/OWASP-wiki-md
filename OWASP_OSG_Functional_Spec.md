**[Back to SpoC 007 OSG
page](https://www.owasp.org/index.php/SpoC_007_-_OWASP_Site_Generator)**

### Overview

Currently it is hard to use OSG. There are a few things we want to
improve in OSG to improve usability and increase adoption of OSG.

1\) Clean-up the user interface (UI) so it is more intuitive and
explorable. 2) Be able to create a library of exploitable code that
highlights common mistakes by developers and administrators. This area
will be used for dynamically generating websites and web services on the
fly. Currently a new page needs to be created for each exploit and
transmission method.

### Components of OSG

## Controller

This is a desktop application that opens up a port that listens for
requests from given web page. The server will take a given site and URL
and pass back one of the two following things: 1) The page rendered from
a template. The template will be a master page in ASP.Net it will
control the layout of the site and the actual content will be defined at
the page level. 2) The pages physical file location. Aspx files not
needed really as everything will get built on the fly. A few physical
files we will need to know are the controls and master pages.

` NOTE: It is not uncommon for the old-school OSG devs to refer to this as the desktop client but in reality it is the server.`

## Client

The client is a web site or virtual folder that has an HTTPModule that
talks with the server asking for the proper page to display to the user.

### UI Changes

TBD.

### Library specification

QUESTION: DOES THIS MAKE SENSE, WHAT IS MISSING? SHOULD THIS BE AN
ABSTRACT CLASS INSTEAD?

The following interface will be used for each exploit:

` interface IExploit {`
` /*`
`  * Description: This will be used for returning a form or web page to a calling site.`
`  * `
`  * Precondition: This string will be used on a web page and not something like a web service`
`  *`
`  * Postcondition: The HTML is returned and is ready to be used. `
`  */`
` public string getExploitHtml();`
` /*`
`  * Description: This method will be used for processing the form that was returned in the getExploitHtml call. `
`  *`
`  * Precondition: The HTTPRequest object is accessible`
`  */`
` public string processExploitForm(); How are the form values passed on to this method? -Borismaletic 3/12/08 4:00 AM  Dude this is a functional spec not a dev-level spec.  It is to give you the general idea of how it will work.  Nothing here is set in stone, it is just some guidelines.  If you want a dev spec I should just create the program myself. -Medelibero 3/16/08 10:11 AM`
` // Returns a web method defintion for use in a WSDL (is this even possible???)`
` public string getWSDLDefinition(); Is this the idea here to create some test form that invokes the service based on this WSDL? Something like what Visual Studio does for asmx files (when opened in the browser)? -Borismaletic 3/12/08 4:01 AM `
` /*`
`  * Description: This handle the processing of the Web Service Method. `
`  */`
` public string processWebServiceMethod(); // What parameters does this need?  An Array? `
` }`

### HTTPModule

The HTTPModule is the translator between the client and the server. How
it works is every site request will initially get handled by the
HTTPModule. What the role of the HTTPModule will be is to look at the
request and load the proper template and vulnerability values for the
request. If the request does not tie to an existing page the default
page should be displayed for the folder or site (folder gets
precedence). The HTTPModule will also have to figure out in what format
the data should be returned. For example if there is a POST request and
we need to parse the data the HTTPModule should load the correct form
parser and parse the form and return a response.

### Central Vulnerability Database

The central vulnerability database will be an area hosted on a web
server (NOTE: Need to find out where this is) that will store all the
vulnerabilities/web test cases. The OSG “server” and httpmodule will use
this information to show available vulnerabilities and to pull down the
information they need. This means that this central area will need to
have a web service accessible to anyone. Given OWASPs nature this needs
to be done with security in mind so that it can withstand any assault
since we don’t want some insecure on OWASP.

Along with a web service trusted OWASP members will need to be able to
go in and manage the available vulnerabilities. We also need to allow
for user submissions. A user submission will not automatically be
authorized but instead will be put in a “bucket” for the trusted OWASP
members to review and authorize.

### Interface between the HTTPModule and the Controller

Description: This area will describe the interface/communication between
the HTTPModule and the Controller. Communication will happen when a new
request comes in the HTTPModule will ask the Controller what page and
information should actually be rendered.

Details: My thought is to have the two components talk via .Net
remoting. In both of the areas there will be a configuration file
specifying the port it needs to listen to or connect to. The HTTPModule
will initiate the connection and send over the data. The data should be
packaged in a class that would look something like.

The httpmodule will send this

` Public class osgRequest {`
`   /* This will hold the URI that was request */`
`   public string RequestURI {`
`       // TODO: implement`
`   }`
`   /* This will hold the value from HttpRequest.Method, letting us know if it is a post, get, etc..*/`
`   public string RequestMethod {`
`      // TODO: implement`
`   }`
`   /* This will hold a unique transaction ID, my thoughts are a GUID , the HTTPModule will need`
`       to keep track of valid transaction IDs so it can handle multiple requests*/`
`   public string transactionId {`
`      // TODO: implement`
`   }`
` }`

The controller will return this

` public class osgResponse {`
`   /* Holds the transactionID received from the osgRequest object */  `
`   public string transactionID {`
`      // TODO: implement`
`   }`
`   /* Specifies the physical file location, if needed */`
`   public string PhysicalFileLocation {`
`      // TODO: Implement`
`   }`
`   /* Holds the template location */`
`   public string DisplayTemplateLocation {`
`      // TODO: implement`
`   }`
`   /* This holds an object that implements the IExploit interface */`
`   public ***** Exploit {`
`      // TODO: implement`
`   }`
` }`

### Changes Required

  - New UI and probably a whole new desktop application
  - A new HTTPModule that leverages the new vulnerability library
  - An eye on making the web site portion of the program working on
    multiple web servers
  - Create a better unified installer that sets up the initial web site
    along with installing all the bit correctly (this will use WiX)
  - Make the websites be able to work under virtual directories
  - Investigate the possibility of multiple web sites working at once
    against a OSG "server"
  - Currently whenever a new site has to be created vulnerabilities have
    to be duplicated and are not dynamically loaded from a library of
    vulnerabilities. On top of this the pages always have to be manually
    edited causing for user pain and very little point of OSG being
    there. A user should be able to supply the pages and using tags like
    you will find in .Net for adding web-controls they will be able to
    specify where the vulnerability will be located. That is what the
    user stories are for..they are examples..-Medelibero 3/16/08 10:10
    AM An example of this would be very useful. I am still trying to
    visualize the solution. -Borismaletic 3/12/08 4:13 AM
  - A central store for the majority of vulnerabilities.

**[Back to SpoC 007 OSG
page](https://www.owasp.org/index.php/SpoC_007_-_OWASP_Site_Generator)**