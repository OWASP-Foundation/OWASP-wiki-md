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
    post](https://drive.google.com/open?id=1VDIeT0Wfrt2_v5hY6by984H5fya56xe7E_rZDird8qg)
    (publicly available)
  - [Google Sheet of mail lists, most recent post and owner(s) of the
    list](https://docs.google.com/spreadsheets/d/1_Fn1t_-tcw3duCC0QMhKXEMqdKcHvqsi21e7LuiOphM/edit?usp=sharing)
    (only available to Foundation Staff since it contains email
    addresses of list owners)
  - [Google Groups Help
    pages](https://support.google.com/groups/?hl=en#topic=9216)
  - [Form to request early migration to Google
    Groups](https://goo.gl/forms/e0C1r9SfXizp83AM2)
  - [Documented process to create a Google
    Group](https://drive.google.com/open?id=12T-7Dh11GmPGXBKYHStBPRgBHm_AnUTifMQ6Ip1h2MM)
    (for staff)
  - [Instructions on 3 different ways to join a Google Group at
    OWASP](https://drive.google.com/open?id=1TBzgvB8Tb0aAZnEy2qYzLnrzJuRzK_T91Em09DVf5YA)
      - [Instructions translated to
        Japanese](https://drive.google.com/open?id=1sSZQRYZvsBbvu9c-okKID53RlmIc79xS8zRRnguR1uk)
  - [Mapping of old Mailman list names to new Google Group
    names](https://drive.google.com/open?id=1JZepIwS0JA6-eHc3HcIQjmzrIXi-7ugf2QwxWylYCt8)

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

# Milestones

  - 2019-01-29 - \[Matt\] Review the inventory of lists to determine
    which are inactive - **DONE (**total lists = 875)
  - 2019-02-12 - \[Matt\] Use the data above to retire any inactive list
    - **DONE** (total lists = 181, 693 inactive lists removed)
  - 2019-02-26 - \[Matt\] Complete Staff Project Plan - **DONE**
  - 2019-02-26 - \[Matt\] Socialize this plan on the leaders list -
    **DONE**
  - 2019-02-28 - \[Matt\] Review remaining list for any that can be
    retired due to ownership (e.g. owned by staff and unused) or mail in
    the last calendar year is SPAM - **DONE** (total lists = 139)
  - 2019-03-01 - \[Matt\] Send email to all list owners about his plan
    and an overview of the migration effort - **DONE**
  - 2019-03-06 - \[Matt, Harold, Dawn\] Review remaining lists and
    remove any projects or chapters which are inactive. A new Google
    Group can be created for chapters/projects that become active again
    - **DONE**
  - 2019-03-08 - \[Matt\] Create Google Groups for all remaining mail
    lists - **DONE**
  - 2019-03-08 - \[Matt\] Send out a reminder to all remaining lists
    about the transition - **DONE**
  - 2019-03-15 - \[Matt\] Send out 2nd reminder to all remaining lists
    about the transition - **DONE**
  - 2019-03-19 - \[Matt\] Send out an additional reminder to all
    remaining lists about the transition - **DONE**
  - 2019-03-22 - \[Matt\] Final notification email sent to all remaining
    lists - **DONE**
  - 2019-03-22 - \[Matt\] Cut over to Google Groups - inbound email to
    lists.owasp.org set to bounce - **DONE**
  - 2019-03-24 - \[Matt\] Turn off Mailman on lists.owasp.org - inbound
    email to lists.owasp.org will fail - **DONE**
  - 2019-03-25 - \[Matt\] Post migration email via MailChimp "inviting
    to join other lists" and capture non-opt-in - **DONE**
  - 2019-03-27 - \[Matt\] Migrate static archives from lists.owasp.org
    to a new host - **DONE**
  - 2019-03-27 - \[Matt\] Remove lists.owasp.org MX records in DNS and
    update the wiki main menu to point at Google Groups instead of
    lists.owasp.org - **DONE**
  - 2019-03-29 - \[Matt\] Retire lists.owasp.org server at Rackspace -
    **DONE**
  - 2019-04-01 - \[Harold\] Close discourse.owasp.org account - **exact
    date TBD**

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
  - Google Groups used to assist communication during the migration
      - [Google Group of all Mailman list
        owners](https://groups.google.com/a/owasp.org/forum/?hl=en#!forum/mailman-list-owners)
        - mailman-list-owners@owasp.org
      - [Google Group used to join the remaining
        lists](https://groups.google.com/a/owasp.org/forum/?hl=en#!forum/retiring-mailman)
        and post announcements to them - retiring-mailman@owasp.org
        (private list)

# Leadership

  - This is a Foundation staff run initiative including
      - Matt Tesauro - primary point of contact
      - Harold Blankenship - staff representation for project mail lists
      - Dawn Aitken - staff representation for chapter mail lists

## FAQ

**(Q1)** My list is no longer showing on mailman and/or emails to it are
bouncing back with something like:

`reason: 550 permanent failure for one or more recipients (OLD_LIST_NAME@lists.owasp.org:550 5.1.1 <OLD_LIST_NAME@lists.owasp.org>... User unknown`

**(A1)** You list didn't have any email traffic for over 1 calendar year
and was archived. If you fill out the [form to request early migration
to Google Groups](https://goo.gl/forms/e0C1r9SfXizp83AM2), we can
re-create that list in Google Groups for you.

**(Q2)** How do my existing Mailman user join the new Google Group? Do
they need to have an Google or @owasp.org account?

**(A2)** There's several ways to join one of the new Google Groups -
they are documented fully
[here](https://drive.google.com/open?id=1TBzgvB8Tb0aAZnEy2qYzLnrzJuRzK_T91Em09DVf5YA).
And <u>**you don't have to have a Google account to join our Google
Groups**</u>.

Other translations of instructions on joining a Google Group at OWASP

  - [Japanese](https://drive.google.com/open?id=1sSZQRYZvsBbvu9c-okKID53RlmIc79xS8zRRnguR1uk)

**(Q3)** Do I need to have a Google account, an @owasp.org email or
provide my phone number/mobile number to participate in Google Groups at
OWASP?

**(A3)** No, all you need is an email address and you can participate in
any of the OWASP Foundation Google Groups. For specifics on how to join
a Google Group without a Google or @owasp.org email address, see part 2
of this
[document](https://drive.google.com/open?id=1TBzgvB8Tb0aAZnEy2qYzLnrzJuRzK_T91Em09DVf5YA)
- also available in
[Japanese](https://drive.google.com/open?id=1sSZQRYZvsBbvu9c-okKID53RlmIc79xS8zRRnguR1uk).

[Category:Staff Projects](Category:Staff_Projects "wikilink")