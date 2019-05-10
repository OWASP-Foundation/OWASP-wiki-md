So about once a year or so someone realizes that Mailman will send the
password for the list(s) you're a member of...

To keep me from digging through my email and re-hashing the same old,
same old, here's my opinion of all this:

  - OWASP is using Mailman 2.x - the current stable branch of this
    software
      - Mailman 2.x stores password in the clear
      - Mailman 2.x will send your password to you via email (and
        therefore in the clear)
      - Mailman 3.x is still in Alpha - the latest version is 3.0.0b3
        according to their [Launchpad
        site](https://launchpad.net/mailman)
          - Mailman 3.x stores passwords as hashes
          - I'm not sure how password resets are done in the 3.x branch
  - **By the way:** This is an *email* system - everything is going out
    in the clear over SMTP.

I will say that Mailman has generally been rock solid in terms of
handling the lists. We've had issues with mail to and from the lists but
none of them were caused by Mailman. Like a lot of \*nix tools, it does
what it says rather well and nothing more.

So we have a couple of choices:

1.  Stay where we are with Mailman 2.x
2.  Upgrade to Mailman 3.x
3.  Move off of Mailman to something else

So lets think about those...

**Stay with Mailman 2.x**

  - It works. We currently handle thousands of posts a day with little
    or no interaction by admins
  - It has momentum - its what people who've been part of the community
    for a while know and expect
  - We've disabled password reminders so if you get sent a password via
    email its because:
      - You just joined a list
      - You've requested your password be sent to you (aka a reset)
  - If you've done one of the above, prudent, best practice would
    already be protecting you because:
      - You want to check that that password actually works so you go to
        the web interface and log in
          - While you're there, you set a password over SSL and that one
            hasn't been transmitted in the clear.
      - You use a unique password for each list which isn't a password
        for any other site or anything you really care about (e.g online
        banking)
          - I'm on multiple OWASP lists and the number of different
            passwords == number of lists of which I'm a member all of
            which are 22+ random characters
          - There's nice things like LastPass, Keypass, PasswordSafe,
            etc to hold all these things in for you already
      - Once you're on a list, you don't really NEED your password in
        99% of the use cases.

If you're really upset that the list just sent your password to you,
simply use it in the web interface for the list and reset it over a
nice, warm SSL/TLS connection. Then, never use it again because you
probably won't need to anyway.

**Upgrade to Mailman 3.x**

  - Somehow running alpha software doesn't seem that awesome to me.
  - We've have enough furor when people suggest changing to something
    else as it is. (more on this later)
  - Passwords will now be hashed to get this we just had to
      - Setup a new server
      - Get the MTA working (MTA == Mail Transfer Agent or SMTP server)
      - Get DNS records (MX, PTR, SPF, DKIM, etc) setup for this server
      - Get a web server setup, configured, hardened on this server
          - Get a TLS/SSL cert for this new web server
      - Get Mailman 3.x setup, configured, hardened on this server
      - Get list archiving setup, configured, hardened on this server
      - Get the existing archives moved over to this server
      - Test all of the above to make sure it works as expected
      - Backup the old server - just in case
      - Take the lists off-line
          - Make sure incoming SMTP is spooled somewhere so posts aren't
            lost
      - Move the existing Mailman data from the old server to the new
        server
      - Update DNS to point to the new server
      - Return the SMTP flow back on but now pointing to the new server
      - Test everything again to make sure things are working right.
      - Do a final backup of the old server
      - Turn off the old server

Which seems like a really expensive cost for hashing passwords on an
email system which will be sending everything over SMTP anyway.

'''Move off of Mailman to something else '''

  - Sounds easy, right, not so much. We either need to:
      - Find a service that works internationally and fits what the
        community wants
          - Did you know that Google Groups is blocked in China?
          - Did you know about the 4 or 5 efforts to get forum's up and
            running and how each of those failed?
          - How about Reddit? OWASP has that and its not getting any
            real traction.
          - Have you ever tried to convince 36,000+ cats to do something
            in unison? (There's over 36,000 users on Mailman currently)
      - Find another piece of software
          - Go through the install/configure steps listed above under
            "Upgrade to Mailman 3.x"
          - All while not knowing how it will perform in the field after
            you are done
          - Still have the cat herding problem.
  - If you're lucky, one of the above will actually gain some traction
      - Now you'll have two systems to keep up with, both of which will
        have problems because they are software.
      - Mailman will continue to live on for some % of the community
      - Added problem of the community having multiple "list-like"
        things

**So if you want to help**

  - Start a Global Initiative
    [here](https://www.owasp.org/index.php/OWASP_Initiatives_Global_Strategic_Focus)
      - Suggest something better
      - Gather community members to your cause
      - Get it done - OWASP is all about empowering the community to
        experiment
  - Work with the Mailman project
      - Do a code review of password handling
      - Provide patches
      - Fix this for everybody

To sum things up:

`   `**`"Keep``   ``the``   ``stones``   ``you``   ``are``   ``about``
 ``to``   ``throw``   ``in``   ``your``   ``pocket.``   ``Use``
 ``those``   ``stones``   ``to``   ``build``   ``a``   ``bridge."`**
`                -- Michael Coates on the `[`Leaders-list`](http://lists.owasp.org/pipermail/owasp-leaders/2013-February/008832.html)

NOTE: For those that tweet, I don't want to have a discussion about
this, at 144 characters at a time, beyond a link to this page, sorry.