## Managing Projects

### What is a Tiger Project?

Tiger project is a logical grouping of test targets and tests to be
performed as a whole. Each Tiger project consists of zero or more
targets, each containing zero or more tests (although projects without
any targets and tests are not very meaningful).

### Starting a New Project

A blank project is created automatically when you start Tiger. If you
need to create a project based on a project template, or simply another
blank project, do this:

  - To create a project based on a project template, from the File menu,
    select New.
  - To create a blank project, click the New button on the toolbar, or
    press **Ctrl+N**. Alternatively, from the **File** menu, select
    **New** and choose the "Blank Project" template.

### Opening an Existing Project

To open an existing project, either

  - Click the **Open** toolbar button, or
  - From the **File** menu, select **Open**

Tiger projects have the **.tgp** file extension.

### Saving Your Project

To save your project, either

  - Click the **Save** toolbar button, or
  - From the **File** menu, select **Save** (to save the project using
    its current file name and location) or **Save As** (to save the
    project under a new name and/or at a new location)

### Saving Your Project as a Project Template

You can also save your project as a template. That way, you and other
users can quickly create new projects based on your project. After your
template is imported (currently, there is no GUI for this, just place
your **.tgpt** file in the **Project Templates** subfolder), it will
appear in the **New Project** dialog (displayed when you select **New**
from the **File** menu, or press **Ctrl+N**) and new projects can easily
be created based on it.

**Note**: Typically, users will want to run the same tests, but not on
the same servers as you did in your project, so it’s a good idea to
clear the Path properties of your project targets before saving the
project as a template.

Tiger currently ships with the **Tiger ASP.NET Module** template, which
contains tests for some well known ASP.NET 2.0 vulnerabilites.

![Image:new_project_dialog.png](new_project_dialog.png
"Image:new_project_dialog.png")

*Figure: The New Project dialog box*

## Managing Targets

### What is a Tiger Target?

Tiger target is a web site or virtual directory upon which tests are to
be performed. Each target contains zero or more tests to be performed.
Essentially, target is defined by its *path* (a http or https prefixed
URL, without the document name, query and fragment. If needed, all of
those can be provided at the test level).

Each project can contain multiple targets, and each target can contain
multiple tests.

### Adding a Target

You can add targets to your project by

  - Selecting **Add Target** from the **Project** menu
  - Right-clicking the project node in the Project Explorer, and
    selecting **Add Target** from the shortcut menu that appears.

### Configuring a Target

#### Path

The **Path** property of the target object must be set to a valid *http*
or *https* scheme URL of the web site or virtual directory containing
tests to be executed. Otherwise, you won’t be able to run the project.

Additionally, the **Tests** collection should contain one or more Test
objects. Although technically possible, creating a target with no
associated tests does not make much sense (unless, of course, you plan
to add tests later).

### Deleting a Target

To delete a target from your project, right-click on it in the Project
Explorer window. Then select **Delete** from the shortcut menu. After
you confirm the deletion, the target (along with all the tests it
contained) is gone.

## Managing Tests

### What is a Tiger Test?

Tiger test is a web page or service that is to be called during the
execution of a project, using the supplied parameters and specified HTTP
method. The outcome of that call is later evaluated by a set of various
conditions. If those conditions are met, they generate *alerts*
(essentially signals that something is wrong). Generation of such alerts
is the ultimate goal of running any Tiger project.

Each test is associated with a target, which defines the scheme, host,
port and virtual path parts of the virtual directory that contains that
particular test. (Please note that Tiger supports only the *http* and
*https* schemes.)

### Adding a Test

To add a new test to your project (or, more precisely, target), do one
of the following:

  - Select the target to add a test to and, from the **Project** menu,
    select **Add Test**.
  - Right-click on the target in the Project Explorer and select **Add
    Test** from the shortcut menu.

### Configuring a Test

#### Relative Path

The scheme, host, port and virtual path parts of the virtual directory
are defined by the target containing that particular test. The other
parts of the test URL (namely, the file name, query and fragment) can
be, if needed, supplied by the test itself, using its **Relative Path**
property. Supplying a value for that property, however, is not mandatory
(this allows you test the default document of the target’s virtual
directory).

This division of the URL parts between the target and test objects may
seem awkward at first, but it allows you to redirect execution of a
bunch of tests to a different server (or virtual directory) just by
changing one property value (specifically, the **Path** property of the
Target object).

#### Method

Tests can be invoked using the standard GET or POST HTTP methods. You
can define which one to use via the **Method** property. The default is
GET.

#### Parameters

Tiger supports passing parameters to tests. Basically, a parameter is a
pair of strings where the first value in the pair represents the name of
the parameter, and the other represents the actual value to be passed.

How the parameters are ultimately passed to the test is determined by
the value of the **Method** property.

#### Alerts

After a test has finished executing, its response is matched against a
set of conditions. If one of these condition is met, an alert is
generated. Alerts notify the user that something is wrong (although
nothing prevents you from defining alerts to be generated when something
is right) with the web site or application being tested.

Each alert is defined by its alert condition, message and type. More
info on alerts is provided in the ["Managing
Alerts"](#Managing_Alerts "wikilink") section.

### Deleting a Test

To delete a test from your project, right-click on it in the Project
Explorer window. Then select **Delete** from the shortcut menu. After
you confirm the deletion, the test (along with all the parameters and
alerts it contained) is gone.

## Managing Alerts

Alerts are the final result of executing tests. After a test has
finished executing, its response is matched against a set of conditions
that you defined. If one of these conditions is met, an alert (including
a descriptive message that you defined) is displayed to the user.

Although tests without alerts defined for them are of a questionable
usefulness, they are allowed. They can be used for automating access to
a set of pages. For example, you might define a test project to
'warm-up" a web application before you give a demo of it (so no one will
think it is slower that it actually is ;).

### Adding an Alert

To add a new alert to your test

  - Right-click on the test in the Project Explorer and select **Add
    Alert** from the shortcut menu.

### Specifying Alert Conditions

Once you have created the alert, the most important thing to do is to
specify the condition that defines when this alert is going to be
generated. Tiger supports these types of conditions:

  - Response status code is equal to the value you specified
  - Response status code is not equal to the value you specified
  - Response body contains the text you specified
  - Response body does not contain the text you specified
  - Response body contains a match for the regular expression you
    specified
  - Response body des not contain a match for the regular expression you
    specified
  - Logical AND combination of two conditions, including other AND and
    OR conditions
  - Logical OR combination of two conditions, including other AND and OR
    conditions

These basic conditions allow for creation of very complex tests,
although most often alert conditions tend to be quite simple.

#### Creating a condition

Without a condition defined, a test is not considered valid and it
cannot be run. Conditions are created using the condition editor. To
display it, in the Project Explorer, select the alert you want to define
condition for. Then, in the Property window, click the **Condition**
property. The ellipsis button will show up. Click on it, and finally the
condition editor appears.

Initially, it looks like this:

![Image:condition_start.png](condition_start.png
"Image:condition_start.png")

To add a condition, right-click the placeholder element. A shortcut menu
appears:

![Image:condition_menu.png](condition_menu.png
"Image:condition_menu.png")

Select the type of condition you want to add. If you made a mistake,
right click on the condition and select Delete from the shortcut menu.
Repeat the process until you are done. Here’s an example of a not too
complex condition:

![Image:condition_complete.png](condition_complete.png
"Image:condition_complete.png")

### Specifying Alert Type

Alert type defines how serious the problem is. There are three types of
alerts:

  - **Red** alert, intended to indicate most serious problems
  - **Orange** alert
  - **Yellow** alert, intended to indicate not-so-serious problems

The default alert type is Red.

### Specifying Alert Message

Alert message is a descriptive text that will be displayed to the user
if the alert is generated (i.e. if the alert condition is met).

### Alert Ordering Matters\!

Multiple alerts can be defined for one test. (This feature is most often
used to define different types of alerts for the same test, although
that is not a requirement). For example, you can generate a red alert if
the test manages to start the operating system shell and execute certain
executable, and yellow alert if it manages to start the shell, but fails
to execute that particular executable).

However, keep in mind that the evaluation of alert conditions will stop
when a first condition is met. (So, in the previous scenario, you won’t
get both red and orange alert, which is usually what you want).

One important consequence of this is that you should always specify your
alerts in particular order: the most serious alerts should be tested
before the not-so-serious ones.

## Managing Test Parameters

In order to allow for flexibility when running tests, Tiger supports
passing parameters to tests. These parameters usually alter the behavior
of the test in some way, and are standard parameters used in almost
every Web application (so the chances are that you are already familiar
with the concept). Parameters are passed to tests using the standard GET
or POST method (depending on how you configured the **Method** property
of the test).

### Adding a Parameter

To add a new parameter to your test, do one of the following:

  - Select the test you want to add a parameter to and, from the
    **Project** menu, select **Add Test Parameter**.
  - Right-click on the test in the Project Explorer and select **Add
    Parameter** from the shortcut menu.

### Configuring a Parameter

When configuring a parameter, it is necessary to specify its name.
Although most often you will specify a value for it, it is not required
that you do so. Encoding the parameter value during the test invocation
is done automatically, so don’t encode it yourself.

### Deleting a Parameter

To delete a test parameter, right-click on it in the Project Explorer,
and select **Delete** from the shortcut menu.

## Testing a Test

You don’t have to run the whole project in order to check if you
configured a test right. You can "test a test" by right-clicking on it,
and selecting **Test Run** from the shortcut menu.

## Running Your Project

### Starting the Project

After everything is set up, you run your project by

  - Selecting **Run** from the **Project** menu
  - Clicking the **Run** toolbar button
  - Pressing **F5**

The tests start, and the current status of each individual test is
denoted by an icon and descriptive text.

### Stopping the Project

Sometimes a test can take very long time to execute. If you don’t want
to wait for the test(s) to finish, you can stop the project, effectively
cancelling all the currently executing tests. You can stop the project
by

  - Selecting **Stop** from the **Project** menu
  - Clicking the **Stop** toolbar button

Note that stopping the project does not affect tests that have already
finished executing in any way.

### Finding Out the Test Status

You can determine the status of a certain test by looking at the icon
displayed before its name. A descriptive message is displayed as well.
Here are the meanings of the icons used:

![Image:running.gif](running.gif "Image:running.gif") - The test is
currently executing.

![Image:red_flag.gif](red_flag.gif "Image:red_flag.gif") - The test has
finished executing and a red alert has been generated.

![Image:orange_flag.gif](orange_flag.gif "Image:orange_flag.gif") - The
test has finished executing and an orange alert has been generated.

![Image:yellow_flag.gif](yellow_flag.gif "Image:yellow_flag.gif") - The
test has finished executing and a yellow alert has been generated.

![Image:test_succeeded.gif](test_succeeded.gif
"Image:test_succeeded.gif") - The test execution has succeeded, but no
alerts have been generated.

![Image:test_failed.gif](test_failed.gif "Image:test_failed.gif") - The
test execution has failed.

![Image:test_cancelled.png](test_cancelled.png
"Image:test_cancelled.png") - The test has been cancelled by the user.

## Viewing, Printing and Exporting Project Results

After all the tests are finished executing, you can examine the results
in the main Tiger window, or view a report by clicking the **View
Report** button.

![Image:tiger_hover_info.png](tiger_hover_info.png
"Image:tiger_hover_info.png")

*Figure: examining the test results in the main Tiger window*

![Image:project_report.png](project_report.png
"Image:project_report.png")

*Figure: A simple project results report*

From there, you can print the report and/or save it in the HTML format.

To print the report

  - Click the **Print** toolbar button

To save the report as HTML

  - Click the **Save** toolbar button