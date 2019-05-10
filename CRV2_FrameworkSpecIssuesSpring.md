## Spring Mass assignment

The mass assignment problem relates to the universal web framework
pattern of automatic binding request parameters into model objects. See
also MVC/.NET section previously <link here>

Model objects are an object-oriented representation of user input. They
provide methods to get, set etc associated parameters from user input.
The following frameworks provide a mechanism for binding request
parameters into request bound objects based on matching request
parameter names to object attribute names (based on matching public
getter and setter methods).

1.  .NET MVC --\> Controller method Parameters
2.  Struts 1 --\> ActionForms
3.  Struts 2 --\> Action Attributes
4.  spring mvc --\> Command Object
5.  Ruby Rails & Grails --\> bound request parameters to objects

### Anti-Pattern

### Example Code

`   public class User{ <-- `**`object``   ``to``   ``place``
 ``request``   ``data`**
`         public long id;`
`         public String fname;`
`         public String lname;`
`         public boolean isAdmin;`
`   }`

`   <form action”/updateUser” method=”post” > <-- `**`intened``
 ``use`**
`         `<input name=”user.fname” />
`         `<input name=”user.lname” />
`   `

</form>

The attacker may post a request such as

`   <form action”/updateUser” method=”post” > `
`         `<input name=”user.fname” value="Eoin" />
`         `<input name=”user.lname” value = "OWASP" />
`         `**`<input``   ``name=”user.isAdmin”``   ``=``   ``"True"``
 ``/>`**`<-- `**`injection`**
`   `

</form>

This shall update the user Object isAdmin boolean even though the
developer did not intend to do so.

## What to look for

When reviewing ORM code such as applications using the frameworks above
it is important to veify they they are protected against mass binding
attacks. It is suggested to look for the following...

1 **Rails**: In Ruby on Rails, **attr_accessible** allows you to
specify which attributes of a model can be altered via mass-assignment
(most notably by update_attributes(attrs) and new(attrs)). Any
attribute names you pass as parameters will be alterable via
mass-assignment, and all others won’t be.

Check config/application.rb for

`   config.active_record.whitelist_attributes = true`

And also at the top of each model object

`   attr_accessible :fname, :lname`

**2 .NET MVC**

Bind(include = "name") should be used to define which attributes can be
updated.

`   `**`[Bind(Include``   ``=``   ``"fname")]`**
`   public class Enquiry `
`   {`
`       public string fname { get; set; }`
`       public boolean isAdmin{ get; set; }`
`   }`

3 Grails: See
<http://blog.adamcreeger.com/2012/03/grails-rails-github-and-mass-assignment.html>

4 Spring MVC: Use **DataBinder.setAllowedFields()**
<http://static.springsource.org/spring/docs/current/javadoc-api/org/springframework/validation/DataBinder.html>