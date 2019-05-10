1.  REDIRECT
    [Staff-Projects/Mailman-EOL](Staff-Projects/Mailman-EOL "wikilink")

# Overview

Since very early in OWASP's history, Mailman has been used to facilitate
communication between various members of the community. While Mailman
has served the community well for years, the decision has been made to
migrate from a self-hosted Mailman installation to Google Groups. The
migration will allow the community to continue to have an email address
to reach a particular segments of the community just like Mailman
provides but without the administrative burden of running a server for
Mailman. The reasons for this migration were stated at length on the
leaders list
[here](https://lists.owasp.org/pipermail/owasp-leaders/2019-February/019675.html)
but are summarized below in no particular order:

  - Mailman is old software and doesn't follow current security best
    practices.
      - It sends passwords in the clear which has been repeatedly
        pointed out by the community for quite some time as noted
        [here](About_Mailman_at_OWASP "wikilink").
      - It has a single shared password for overall site administration
        for the staff to use to oversee the installation
      - If a mail list has 2+ list owners, they must share a password
        for managing the list
  - Mailman has an extremely dated UI/web interface. This makes OWASP
    appear out of date/out of touch to new, potential community members
  - Since the Foundation has a very small staff, administering a server
    takes away staff time from focusing on OWASP's mission / [core
    purpose](https://www.owasp.org/index.php/About_The_Open_Web_Application_Security_Project#Core_Purpose).
  - The Anti-SPAM gateway service from Barracuda, which was previously
    donated, is ending on March 24th, 2019.
  - Due to the current climate of increased privacy and the existence of
    the GDPR, the migration will allow the membership in our lists to be
    reviewed/audited by the current user base (aka opt-in).
  - Mailman does not get the use it formerly had \~80% of the lists are
    inactive/dormant/abandoned - some numbers:
      - 875 - total lists prior to initial review/clean-up
      - 181 - lists of the 875 which had at least 1 email to them in the
        last calendar year
      - 693 - lists with no email posts in over 1 year

In 2017, the current community manager (Tiffany Long) suggested a
migration from Mailman to Discourse. This was the original direction of
efforts until it was reconsidered at the 2019 Staff Summit, a face to
face meeting to plan out 2019. Instead, Mailman will be migrated to
Google Groups. The following reasons were crucial in the choice of
Google Groups

  - Functionally equivalent to Mailman as a 'mail list'
  - Already part of the G-Suite donation from Google
  - Can be run for $0 cost and with 0 administration of the underlying
    infrastructure
  - Includes Anti-SPAM filtering that is already part of our G-Suite
    email infrastructure
  - Inbound and outbound email handled by Google email infrastructure -
    no need to run a MTA (mail server)
  - Mobile-friendly, modern UI and significantly better TLS
    configuration for web interactions
  - Has robust admin and permissions available via G-Suite Admin tool

# Project Links

  - [Mailman legacy install](https://lists.owasp.org/mailman/listinfo)
  - [Mailman stats](https://lists.owasp.org/pipermail/stats/) - created
    via monthly cron job / run manually
  - [Google Sheet of mail lists and their most recent
    post](https://docs.google.com/spreadsheets/d/1VDIeT0Wfrt2_v5hY6by984H5fya56xe7E_rZDird8qg/edit?usp=sharing)
    (publicly available)
  - [Google Sheet of mail lists, most recent post and owner(s) of the
    list](https://docs.google.com/spreadsheets/d/1_Fn1t_-tcw3duCC0QMhKXEMqdKcHvqsi21e7LuiOphM/edit?usp=sharing)
    (only available to Foundation Staff since it contains email
    addresses of list owners)
  - [Google Groups Help
    pages](https://support.google.com/groups/?hl=en#topic=9216)
  - [Form to request early migration to Google
    Groups](https://goo.gl/forms/mmYMglHD9EXrEznm1)

# Goals

Overall Goal: Migration of any active list from lists.owasp.org to
Google Groups by March 24, 2019.

Details:

  - Active is defined as a list which as received at least 1 non-SPAM
    email in the last 12 months as of 2019-01-29 when initial activity
    reporting was run
      - Mail lists for inactive projects and chapters will not be
        migrated
      - Archives on lists.owasp.org will be migrated to a static host
        under the same URL scheme as before
  - **High-level Workflow**
      - Announce plan
      - Email notifications of cut-over date
          - Instruct list members to join the new list but continue to
            post to lists until 2019-03-22
          - 3 notifications will go out to all lists
      - Setup new Google Groups for migrating lists, ordered by most
        recent post as of this
        [spreadsheet](https://docs.google.com/spreadsheets/d/1VDIeT0Wfrt2_v5hY6by984H5fya56xe7E_rZDird8qg/edit?usp=sharing)
      - If requested, any list can be migrated prior to the cut-over
        date by completing [this
        form](https://goo.gl/forms/mmYMglHD9EXrEznm1).
      - Hard cut-over to Google Groups on 2019-03-22
      - 2019-03-24 - Service from Barracuda is disabled & inbound email
        to lists.owasp.org will fail.
  - **Timeline**
      - 2019-02-26 - Create this plan
      - 2019-02-26 - Socialize this plan on the leaders list
      - 2019-02-28 - Complete review of remaining mail lists
      - 2019-03-01 - Send email to all list owners about his plan and an
        overview of the migration effort
      - 2019-03-06 - Complete review of Project lists with Harold &
        Chapter lists with Dawn to remove inactive projects/chapters
        from the migration effort
      - 2019-03-08 - Send out a reminder to all remaining lists of the
        transition
      - 2019-03-15 - Send out 2nd reminder to all remaining lists on the
        transition
      - 2019-03-22 - Final notification email sent to all remaining
        lists
      - 2019-03-22 - Inbound email to lists.owasp.org set to bounce
      - 2019-03-24 - Inbound email to lists.owasp.org will fail
      - 2019-03-25 - Retire lists.owasp.org server at Rackspace and
        migrate static archives to new host

# Milestones

  - Review the inventory of lists to determine which are inactive -
    **DONE (**total lists = 875)
  - Use the data above to retire any inactive list - **DONE** (total
    lists = 181, 693 inactive lists removed)
  - Complete Staff Project Plan - **DONE**
  - Review remaining list for any that can be retired due to ownership
    (e.g. owned by staff and unused) or mail in the last calendar year
    is SPAM - **In Process**
  - Review remaining lists and remove any projects or chapters which are
    inactive. A new Google Group can be created for chapters that become
    active again
  - Send out initial communication to all lists which will be migrated,
  - Create Google Groups for all remaining mail lists
  - Send out 2nd communication to all lists which will be migrated
  - Send out final notice to all lists
  - Cut over to Google Groups
  - Migrate static archives from lists.owasp.org to a new host
  - Retire lists.owasp.org server at Rackspace

# Communications

The following lists communications where the retirement of Mailman was
discussed publicly

  - Posts to Leaders lists (prior to creation of staff projects
    template)
      - <https://lists.owasp.org/pipermail/owasp-leaders/2019-January/019608.html>
      - <https://lists.owasp.org/pipermail/owasp-leaders/2019-January/019613.html>
      - <https://lists.owasp.org/pipermail/owasp-leaders/2019-February/019663.html>
      - <https://lists.owasp.org/pipermail/owasp-leaders/2019-February/019675.html>
      - <https://lists.owasp.org/pipermail/owasp-leaders/2019-February/019700.html>
  - Posts to the Blog and Connector
      - <https://owasp.blogspot.com/2018/12/december-2018-connector.html>
        & [December
        Connector](https://us17.campaign-archive.com/?u=a8012c9e2e384bf8ea8d7deb7&id=31f131180e)
      - <https://owasp.blogspot.com/2019/02/owasp-community-our-instance-of-mailman.html>
      - <https://owasp.blogspot.com/2019/02/owasp-community-and-chapter-reminders.html>
      - [February
        Connector](https://mailchi.mp/90cc34fc2cdd/0rleggjjx3-222491)
  - Leaders Meetings
      - AppSec EU 2018 (London) Leaders Meeting -
        [recording](https://www.youtube.com/watch?v=vy6R0SbJrS8&list=PLpr-xdpM8wG9yT6HD6YeCbf6wymhAAqRb&index=6&t=0s)
      - AppSec US 2018 (San Jose) Leaders Meeting - recordings -
        [part 1](https://www.youtube.com/watch?v=sGEfVNuFIZk&t=0s&list=PLpr-xdpM8wG-ma2GOBmdpGGfnVPVwFFQd&index=6)
        &
        [part 2](https://www.youtube.com/watch?v=Wxqtiwzz90c&t=0s&list=PLpr-xdpM8wG-ma2GOBmdpGGfnVPVwFFQd&index=7)
  - Board Meetings
      - [October 2016](October_11,_2016 "wikilink") - Migration from
        Mailman raised by Tiffany in her [Community Manager
        Report](https://docs.google.com/document/d/1-4fIJfiLa8l02Hf1XBMqRYEiY2z6g4qwln-_ZLQ6GIs/edit)

# Leadership

  - This is a Foundation staff run initiative including
      - Matt Tesauro - primary point of contact
      - Harold Blankenship - staff representation for project mail lists
      - Dawn Aitken - staff representation for chapter mail lists

[Category:Staff Projects](Category:Staff_Projects "wikilink")