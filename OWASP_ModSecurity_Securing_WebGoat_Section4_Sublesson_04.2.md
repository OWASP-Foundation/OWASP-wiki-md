4\. Authentication Flaws -\> 4.2 Forgot Password

### Lesson overview

The WebGoat lesson overview is included with the WebGoat lesson
solution.

### Lesson solution

Refer to the zip file with the WebGoat lesson solutions. See Appendix A
for more information.

### Strategy

This lesson illustrates using a weak secret password, favorite color,
which can be guessed eventually. The project member chose to take a
broader view in mitigating this vulnerability and using a couple of
features of ModSecurity in ways not done in other lessons.

A configurable account lockout mechanism (maximum retry count) is
implemented using Lua persistence. The per-user configurable parameters
are: (1) the number of retries allowable before the account is locked
out for further use; (2) the interval (in minutes) that time has elapsed
after being locked out that the account is reactivated.

Appending JavaScript to the end of the response body - a very unsung
useful feature of ModSecurity - is also used to alter the response back
to the user.

We will show the implementation, then after discuss how this solution
can be extended and used as a temporary authentication mechanism.

### Implementation

First, let's go through the steps.

At the beginning of the lesson, the user is asked for their user name:

![Image:OWASP_ModSecurity_Securing_WebGoat_Forgot_password_javascript0.jpg](OWASP_ModSecurity_Securing_WebGoat_Forgot_password_javascript0.jpg
"Image:OWASP_ModSecurity_Securing_WebGoat_Forgot_password_javascript0.jpg")

The user is asked to provide an answer to the secret question:

![Image:OWASP_ModSecurity_Securing_WebGoat_Forgot_password_javascript1.jpg](OWASP_ModSecurity_Securing_WebGoat_Forgot_password_javascript1.jpg
"Image:OWASP_ModSecurity_Securing_WebGoat_Forgot_password_javascript1.jpg")

If the answer is wrong, the user receives an error message and is
prompted again:

![Image:OWASP_ModSecurity_Securing_WebGoat_Forgot_password_javascript2.jpg](OWASP_ModSecurity_Securing_WebGoat_Forgot_password_javascript2.jpg
"Image:OWASP_ModSecurity_Securing_WebGoat_Forgot_password_javascript2.jpg")

There is no limit on the number of retries, a scenario which exists in
many web applications. A hint is given that the administrator may have
an account name of 'admin' and therefore eventually the admin's secret
question can be guessed.

The first step of the solution is a little tricky: we have to keep track
of the user name from the request/response cycle of the first page to
the 2nd page that guesses the answer to the secret question. In the real
world, to take into account concurrency, we would set a cookie for this
scenario, but for our purpose we we to keep it simple and show the main
points of the solution.

The user name is displayed when an incorrect response; e.g.
<font face="Courier New">'\* Incorrect response for admin. Please try
again\!'</font>. So at this point we have the user name and know that
they have guessed the secret question; for our purpose, the retry count
is technically still 0.

We are using Lua scripts and Lua persistence.

The Lua code to extract the user name from this string is:

    _, _, currentuser = string.find(tbuff, "%* Incorrect response for (%w+)%.")

Let's look at the data file format:

    Entry{
      username = "global",
      retry = 2,
      interval = 15,
      lockedout = "no",
      current = "no"
    }

    Entry{
      username = "webgoat",
      retry = 0,
      interval = 0,
      lockedout = "no",
      current = "no"
    }

    Entry{
      username = "admin",
      retry = 0,
      interval = 0,
      lockedout = "no",
      current = "no"
    }

The 'global' entry contains the configurable values for the number of
retries that are going to be allowed and the interval (in minutes) that
needs to elapse before the user's account is reactivated. Here, 2
retries are allowed, and if the user's account is locked and the time
interval between retry attempts is 15 minutes, the account will be
reactivated.

Where the Lua scripts have to make changes to the data file, a
read/write operation is performed. In one case, only a read operation is
necessary. Keep in mind that the data file can be edited at any time (if
using \*nix, be sure to restore the original owner and group name) to
observe and experiment with the values and results.

The Lua script responsible for handling the HTTP responses for this
lesson is 'secret-question-result_04-2.lua'.

After obtaining the user name, we loop through all of the users in the
data file: <font face="Courier New">'dofile(datafile)'</font>

This calls the function 'Entry'; first that particular user's data is
saved to local variables:

```
  function Entry (b)
    local username = b.username
    retry = b.retry
    interval = b.interval
    local lockedout = b.lockedout
    local current = b.current
    local currentuser = currentuser
```

Next:

```
  if username == currentuser then
    current = "yes"
    retry = retry + 1
    if lockedout == "yes" then
      str1 = string.format("Luascript: current user '%s' account is locked!", username)
      m.log(9, str1)
      retstr = str1
    end
  else
    current = "no"
  end
```

The user is set to current or not. If it is the current user, we
increase the retry count and if the account is locked out, we set the
script's return screen to non-nil, which will trigger the SecRuleAction
in phase 4 of this lesson's ModSecurity configuration file; we will go
over this later in this lesson - view either
'rulefile_04-2a_forgot-password.conf' or
'rulefile_04-2b_forgot-password.conf'.

The last step of the loop (the function 'Entry') is to add the user's
updated information to a string buffer:

```
  -- build buffer and write back to disk
  outstr = string.format("Entry{\n  username = \"%s\",\n  retry = %d,\n  \
    interval = %d,\n  lockedout = \"%s\",\n  current = \"%s\"\n}\n\n", \
    username, retry, interval, lockedout, current)
  tbuff = tbuff .. outstr
```

When the function is over, we write the file:

```
  local fh2 = io.open(datafile, "w+")
  if fh2 == nil then    -- don't fail open
    str1 = string.format("Luascript: Error in creating file: %s;\n", datafile)
    m.log(9, str1)
    retstr = str1
  else
    fh2:write(tbuff)
    fh2:flush()
    fh2:close()
  end
```

Finally, the return value is returned to SecRuleAction:

```
  if retstr == "" then
    retstr = nil
  end
  return retstr
```

A nil value means nothing bad happened.

Now, let's take a look how we process the HTTP request. The Lua script,
which is heavily commented, is 'secret-question-guess_04-2.lua'.

It is necessary to distinguish between 2 different types of requests
that are received.

The 1st request is when the user enters the user name. The POST body
parameters 'Username=admin\&SUBMIT=Submit' are retrieved:

```
  loginuser = m.getvar("ARGS_POST.Username", "none")
  local submitvalue = m.getvar("ARGS_POST.SUBMIT", "none")
```

The function for processing this request, Entry0, is called if the
proper conditions are met:

```
  if loginuser ~= nil and submitvalue ~= nil and submitvalue == "Submit" then
    str1 = string.format("Luascript: Entering Entry0 with user name: %s\n", loginuser)
    m.log(9, str1)
    Entry = Entry0
    dofile(datafile)
    return retstr
  end
```

The 2nd request is when the user is making a guess for the secret
question. If no other sublessons of the lesson are being used - only
'rulefile_00_initialize.conf' and either
'rulefile_04-2a_forgot-password.conf' or
'rulefile_04-2b_forgot-password.conf' - then we don't need to filter
to call the 2nd function. If it is desirable to filter, add the
conditional statement as done previously with the POST parameters as
<font face="Courier New">''Color=green\&SUBMIT=Submit'</font>.

```
  Entry = Entry1
  dofile(datafile)
```

Let's examine what each function does.

'Entry0' loops and processes each user in the data file. First, each
entry's values are copied to local variables as previously shown.

Next, we get the configurable value from the user 'global' that we need,
'interval'; note that 'global' always has to be the first entry in the
data file.

```
    if username == "global" then
      g_interval = interval
    end
```

The next section of the function is:

```
    if username == loginuser and lockedout == "yes" then
      num1 = os.time()
    if num1 >= (interval + g_interval*60) then
      str1 = string.format("Luascript: User %s is locked out but global \
            interval has been exceeded\n;", username)
      m.log(9, str1)
      retstr = nil
    else
      str1 = string.format("Luascript: Entry0 - User %s is locked out!\n;", username)
      m.log(9, str1)
      retstr = str1
    end
    end
```

It is better to only read the data file if possible, which is done here.
If the user is locked out but the interval between lock out time and now
has been exceeded, we will let the user through and in the 2nd function
deal with this condition so nil is returned in the function and the main
body (to return nil to the SecRuleAction). If the user is locked out, we
return non-nil (the string message is recorded in the audit log and the
debug file, irrespective of the explicit log entry
<font face="Courier New">'m.log(9, str1)'</font> to the debug file), the
SecRuleAction will trigger, and the user will receive a message that
they have been locked out (which will be shown later).

For the 2nd function, 'Entry1', remember that we are on the page that is
guessing the color. In this function, though, we will make changes to
the data file according to the results.

First, retrieve the 'global' user's configuration parameters but this
time we need the retry maximum count also:

```
  if username == "global" then
    g_retry = retry
    g_interval = interval
  end
```

Next:

```
  if current == "yes" then
    if lockedout == "yes" then
      -- check if time interval exceeded; if so, unlock account
      num1 = os.time()
      if num1 >= (interval + g_interval*60) then
        lockedout = "no"
        retry = 0
        interval = 0
      else
        -- question: do we want to set a new interval to the current time? IMO, yes
        interval = os.time()
        retstr = "Luascript: Entry1 - account already locked!"
      end
    end

    if lockedout == "no" then
      -- have to be real careful here that both are integers;
      -- if not, then function will return suddenly with nil
      if retry >= g_retry then
        lockedout = "yes"
        interval = os.time()  -- record the second that user was locked
        retstr = "Luascript: account is now locked!"
      end
    end
  end
```

If the user is not the current user, nothing changes.

If the user is current, check if their account is currently locked.

If yes, check if the max interval time has been exceeded; if yes, then
set the user lockout to "no", and reset the retry and interval values to
0; if no, reset the interval time to the current time (optional) and set
'retstr' so that it is denoted that the user is locked out and the
SecRuleAction will be triggered.

If the account is not locked out, check if the retry count has been
reached; if so, mark the account as locked out and reset the interval.

Note, that a conditional 'if lockedout == "no", then, else' was not
used. If the account was originally locked out but changed to not locked
out, that user is processed in the 'lockedout == "no" section as a
safety check (and if one wants to add other logic here).

Also, note that the return value to SecRuleAction as currently
implemented only returns boolean: either nil (nothing bad happened) or
non-nil (changing ModSecurity to accept nil or a string as a return
value should be possible because the return string is written to the log
files). In our case, the bottom line is the same: the user is locked
out, but the causes are different.

Finally, at end of the function each user's values appended to a buffer,
then after exiting the function the buffer is written back for a new
data file (the code for this has been previously shown).

We jump up now to the ModSecurity rules. Two alternatives have been
given, 'rulefile_04-2a_forgot-password.conf' and
'rulefile_04-2a_forgot-password.conf'; they differ as to how to notify
the user that they have been locked out.

First, 'rulefile_04-2a_forgot-password.conf':

Recall that the HTTP request triggers all of the processing when a user
has made an incorrect guess; the error message
<font face="Courier New">'\* Incorrect response for admin. Please try
again\!'</font> (see Figure 3 at the beginning of this page) is our cue
that a certain user has failed at making a correct guess.

Here is the rule:

```
  SecRule TX:MENU "!@eq 500" "phase:4,t:none,pass,skip:1"

  # parse response body and process Lua script
  SecRuleScript "/etc/modsecurity/data/secret-question-result_04-2.lua" \
    "phase:4,t:none,log,auditlog,allow,msg:'Luascript: Writing RESPONSE \
    BODY extracting user name from error message in secret-question-result_4-2.lua'"
```

We don't care about the result of the script (nil or non-nil) because we
do the heavy lifting in the HTTP request Lua script. The rules for this
are:

```
  SecRule ARGS:menu "!@eq 500" "phase:2,t:none,skip:2"

  # action is triggered if script returns non-nil value
  SecRuleScript "/etc/modsecurity/data/secret-question-guess_04-2.lua" \
    "phase:2,t:none,log,auditlog,deny,severity:3,msg:'Authentication Flaws \
    - 4.2 Forgot Password',tag:'PASSWORD_RETRY', \
    redirect:/_error_pages_/lesson04-2.html"

  SecAction "phase:2,allow:request,t:none,log,auditlog, \
    msg:'Luascript: user account not locked out'"
```

(Note: previously, it was explained why the lessons are filtered by menu
number and the reasons for using
<font face="Courier New">'ARGS:menu'</font> in Phase 2 and
<font face="Courier New">'TX:MENU'</font> in Phase 4)

Very simply, if the user's account is locked out, they get redirected to
an error page.

The 2nd ruleset, rulefile_04-2b_forgot-password.conf, offers a more
elegant solution. Inside the Lua script, a non-nil value is returned
when the user's account is locked out. Instead of passing through the
response body and processing the result in the request body in
'rulefile_04-2a_forgot-password.conf', we do the opposite:

```
  SecRule TX:MENU "!@eq 500" "phase:4,t:none,pass,skip:1"

  # parse response body and process Lua script
  SecRuleScript "/etc/modsecurity/data/secret-question-result_04-2.lua" \
    "phase:4,chain,t:none,log,auditlog,allow,msg:'Luascript: Writing RESPONSE \
    BODY and appending javascript in secret-question-result_4-2.lua'"

  SecRule RESPONSE_CONTENT_TYPE "^text/html" \
    "append:'<script language=\"JavaScript1.2\" type=\"text/javascript\"> \
    var idvar = document.getElementById(\"message\"); idvar.innerHTML = \"\"; \
    idvar.innerHTML = \"<BR> * TOO MANY RETRY ATTEMPTS; YOUR ACCOUNT IS NOW \
    LOCKED!\"; document.form.SUBMIT.disabled = true;</script>'"
```

The JavaScript appended to the response body, instead of redirecting to
an error page, looks like this:

![Image:OWASP_ModSecurity_Securing_WebGoat_Forgot_password_javascript3.jpg](OWASP_ModSecurity_Securing_WebGoat_Forgot_password_javascript3.jpg
"Image:OWASP_ModSecurity_Securing_WebGoat_Forgot_password_javascript3.jpg")

Compare this with Figure 3. The original error message, in bright red
color, has been replaced with <font face="Courier New">'\* TOO MANY
RETRY ATTEMPTS; YOUR ACCOUNT IS NOW LOCKED\!'</font> and the Submit
button has been disabled. The advantages of this approach are: (1) the
user stays in "the same place" in the web site; (2) the look and feel of
the web site is retained; the look and feel would have to be
incorporated in a new error HTML page.

### Comments

In the real world, a file locking mechanism would need to be placed on
the data file which could be implemented easily by creating or checking
for an empty file like 'file.lock'. There doesn't seem to be an elegant
'sleep' or 'wait' capability in Lua script, so the rare occurrence that
a request file lock is already used, an error message would have to be
returned to the user saying "please try again".

What has been shown in this sublesson?

1.  The use of Lua persistence
2.  A configurable account lock out (maximum retry count) mechanism
3.  Appending JavaScript to a response body to alter the HTML page's
    content and behavior.
4.  A business logic flaw has been mitigated by a Web Application
    Firewall

The basic concepts demonstrated here can be extended and be used in real
world examples, such as:

1.  A web site's authentication has no maximum retry count or account
    lock out mechanism.
2.  A web site (or areas of a web site), previous open to the public,
    require protection via an authentication mechanism.

The Lua scripts can be modified to tie into other authentication
credential storage mechanisms (if the capability is supported in the
language).

### Reviewer comments

In looking at this lesson, there are a few security issues we need to
address:

Issue 1 - Attackers who are attempting to enumerate valid usernames. If
you submit an invalid one the html response text includes info stating
as such. We can track this.

Issue 2 – Once a specific valid username is identified, the attacker
then starts a targeted attack to guess answers to the password hint
(favorite color).

Issue 3 – Attackers can initiate reverse brute force attacks – this is
when an attacker cycles through different valid user accounts and
submits the same common answer to the question (submitting Blue as the
answer to different usernames).

Your approach seems to address issue \#2 above as you are
monitoring/correlating the answers submitted with the username. The main
issue that I see with your use of temporary lockouts is that you have to
be careful not to lock out legitimate clients. In this case, you are
using the Lua script to lock out anyone from accessing the targeted
account which would be a denial of service attack against legit users.
It is for this reason that I would recommend a more targeted blocking
scheme aimed at the JSESSIONID value instead of the account name. This
approach is not foolproof, however, as attackers could potentially cycle
through different JSESSIONIDs for evasion. WebGoat will redirect the
user back to the start page if the JSESSIONID is missing or invalid and
therefore it is deemed as an acceptable countermeasure as it would
require the attacker log authenticate again.

What we need to do is to also address issues 1 and 2. The key to doing
this is to leverage the JSESSIONID handed out by WebGoat to store/track
data. We can then add additional logic checks. Here is an example rule
set which looks to achieve the same basic protections as your Lua
scripts.

    #
    # Initiate the session and user collections.
    #

    SecAction "phase:1,t:none,pass,setsid:%{REQUEST_COOKIES.JSESSIONID}"

    #
    # For Sublesson 4.2 - Capture the submitted username for tracking/display in Mod audit logs
    #

    SecRule ARGS:Username ".*" \
    "phase:2,t:none,pass,log,setvar:session.username=%{args.username}, \
    expirevar:session.username=60,setuid:%{args.username}"

    #
    # Identify a failed username attempt by inspecting the html response payload
    # Set the time interval for inspection to be 60 seconds
    #

    SecRule RESPONSE_BODY "\* Not a valid username\. Please try again\." \
    "phase:4,t:none,log,pass,setvar:session.failed_username=+1, \
    expirevar:session.failed_username=60"

    #
    # Identify a failed question attempt by inspecting the html response payload
    # Set the time interval for inspection to be 60 seconds
    #

    SecRule RESPONSE_BODY "\* Incorrect response for .* Please try again\!" \
    "phase:4,t:none,log,pass,setvar:session.failed_question=+1, \
    expirevar:session.failed_question=60"

    #
    # Evaluate the failed username value.
    # If it is above 5 in 60 seconds, set blocking variable.
    # The temporary timeout setting is for 5 minutes.
    #

    SecRule SESSION:FAILED_USERNAME "@gt 5" "phase:4,t:none,pass,nolog,setvar:session.blocked1=1, \
    expirevar:session.blocked1=300"

    #
    # Evaluate the failed question value.  If it is above 3 in 60 seconds, set blocking variable.
    # The temporary timeout setting is for 5 minutes.
    #

    SecRule SESSION:FAILED_QUESTION "@gt 3" "phase:4,t:none,pass,nolog,setvar:session.blocked2=1, \
    expirevar:session.blocked2=300"

    #
    # If the session block1 variable is set, then redirect client to failure page
    #

    SecRule SESSION:BLOCKED1 "@eq 1" "phase:1,t:none,deny,redirect:/_error_pages_/lesson04-2.html, \
    msg:'Authentication Flaws. 4.2 Forgot Password. Too Many Failed Usernames.', \
    tag:'PASSWORD_RETRY'"

    #
    # If the session block variable is set, then redirect client to failure page
    #

    SecRule SESSION:BLOCKED2 "@eq 1" \
    "phase:1,t:none,deny,redirect:/_error_pages_/lesson04-2.html, \
    msg:'Authentication Flaws. 4.2 Forgot Password. Too Many Failed Question \
    Attempts.',tag:'PASSWORD_RETRY'"

I do like your use of Content Injection of adding JS to alter the html
text and to disable the Submit button display, however this doesn’t
really do anything to prevent an attacker from re-submitting more data.
They don’t need to have the submit button enabled in order to re-submit
their data.