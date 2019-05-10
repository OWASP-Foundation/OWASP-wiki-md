[WebGoat User Guide Table of
Contents](WebGoat_User_Guide_Table_of_Contents "wikilink")__TOC__

All you have to do is implement the abstract methods in LessonAdapter.

WebGoat uses the Element Construction Set from the Jakarta project. You
should read up on the API for ECS at
<u><http://jakarta.apache.org/site/downloads/downloads_ecs.cgi></u>.

WebGoat uses WTP. You can find more information about Eclipse WTP here
<http://www.eclipse.org/webtools/>.

## Step 1: Set up the framework

Source for the class NewLesson.java

## Step 2: Implement createContent

Creating the content for a lesson is fairly simple. There are two main
parts:

1.  Handle the input from the user’s last request
2.  Generate the next screen for the user

This all happens within the createContent method. Remember that each
lesson should be handled on a single page. Therefore it is important to
design the lesson to work on one page.

**Sample createContent Method**

A good generic pattern for the createContent method is shown below:

`// define a constant for the filed name`
`Private static final String INPUT = “input”;`
`Protected Element createContent(WebSession s)`
`{`
` ElementContainer ec = new ElementContainer();`
` try`
` {`
`   // get some input from the user`
`   // see ParameterParser for details`
`   String userInput = s.getParser().getStringParameter(INPUT, “”);         `
`   // do something with the input`
`   // -- SQL query?`
`   // -- Runtime.exec?`
`   // -- Some other dangerous thing`
`   // generate some output – a string and an input field`
`   ec.addElement(new StringElement(“Enter a string: “));`
`   ec.addElement( new Input(Input.TEXT, INPUT, userinput));`
` }`
` catch (Exception e)`
` {`
`    s.setMessage(“Error generating “ + this.getClass().getName());`
`    e.printStackTrace();`
` }`
` return(ec);`
`}`

ECS is quite powerful. See the Encoding lesson for an example of how to
use it to create a table with rows and rows of output.

## Step 3: Implement the other methods

The LessonAdapter class requires more methods to make a lesson fully
functional. These methods allow the WebGoat user to navigate to the
lesson and display lesson information. Each method is fairly simple and
should only take a few minutes to implement.

Additional LessonAdapter Methods

|  |   |  |                 |  |                                                                                                  |
|  | - |  | --------------- |  | ------------------------------------------------------------------------------------------------ |
|  |   |  | **Method**      |  | ***'Description***'                                                                              |
|  | 1 |  | getHints        |  | Return hints to the framework one at a time                                                      |
|  | 2 |  | getCredits      |  | Return credits to the framework for display                                                      |
|  | 3 |  | getInstructions |  | This method will load the instructions HTML file from lesson_plans directory if you create one. |
|  | 4 |  | getRanking      |  | Sets the order of the lessons within a category. The lowest ranked lesson appears at the top.    |
|  | 5 |  | getTitle        |  | The title is rendered as HTML                                                                    |
|  |   |  |                 |  |                                                                                                  |
|  |   |  |                 |  |                                                                                                  |

` protected List getHints()`
` {`
`     // Hints will be returned to the user in the order they`
`     // appear below. The user must click on “next hint”`
`     // before the hint will be didplayed.`
`     List hints = new ArrayList();`
`     hints.add( "There are no hints defined." );`
`     return hints;`
` }`
` public Element getCredits()`
` {`
`     return new StringElement("");`
` }`
` /*`
`  * Gets the ranking attribute of the LessonAdapter object. `
`         * The ranking denotes the order in which`
`         * the menu item will appear in menu list for each category. The`
`         * lowest number will appear as the first lesson.`
`  *`
`  * @return    The ranking value`
`  */`
` public Integer getRanking()`
` {`
`   return new Integer(10);`
` }`
` /**`
`  *  Fill in a descriptive title for this lesson. `
`         *  This will appear above the control area at the `
`         *  top of the page. This field will be rendered as html.`
`  *`
`  * @return    The title value`
`  */`
` public String getTitle()`
` {`
`   return "Untitled Lesson " + getScreenId();`
` }`

## Step 4: Build and test <this must have changed in v4>

After the new lesson is implemented ant can be used to build and deploy
the new web application. First you want to remove the webgoat.war and
the webgoat directory from the webapps directory. Next, cd to the
webgoat directory and type:

` `*`ant``   ``install`*` `

This will compile the new lesson and “install” the path into Tomcat. The
lesson only needs to be installed once. If changes are made to the web
application and another test is needed type:

` `*`ant``   ``reload`*

## Step 5: Give back to the community

If you have come up with a lesson that you think helps to teach people
about web application security, please contribute it by sending it to
the people who maintain the WebGoat application.

[WebGoat User Guide Table of
Contents](WebGoat_User_Guide_Table_of_Contents "wikilink")

[Category:OWASP WebGoat
Project](Category:OWASP_WebGoat_Project "wikilink")