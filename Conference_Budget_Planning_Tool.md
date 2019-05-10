## Overview

Tool for planning conference budgets and submitting proposal budgets to
the the OWASP Foundation through the [OWASP Conference Management
System](https://ocms.owasp.org/). The tool was originally designed for
AppSec conferences but can be used for a conference of any size.

### Status

The tool is currently in Alpha release so please be gentle. This version
of the tool is populated with some notional AppSec budget data as an
example. Submit any issues to [the OWASP Staff Contact Us
Form](http://owasp4.owasp.org/contactus.html)

### Download

[Conference Budget Planning Tool
v0.3](https://docs.google.com/spreadsheet/ccc?key=0AsFE6Oyqbn2cdGpsbElBcXpYcmFwWmY1NXR5X2RjTGc&hl=en_US)
- Google Doc Version w/ sample data

### Customization

The tool is mostly designed to be customized. When customizing it's
important to keep a few points in mind.

  - On most tabs there is a Total in cell B4. The Dashboard pulls it's
    data from this cell so it is required.
  - Attendance numbers must be changed on the Attendance tab, all other
    tabs reference this number except for ...
  - the Training tab contains all the attendance information for the
    training classes

As the tool stands, it will automatically update items and re-calculate
the finances when source cells are updated. So be careful when modifying
this functionality.

## Organization

The tool is broken up into a series of 15 tabs each with it's own
function.

### Dashboard

Overview. Mostly Locked.

You can use this page to run some projections for break even points. To
do this run the Goal Seek function (see Excel help for this) with the
"Set Cell" of B15, "To Value" of 0 and "By changing cell" of
"Attendance\!B9".

### Attendance

This sheet is primarily a "read only" sheet that references information
from other parts of the tool (see field comments for source location).
Items that can be changed on this sheet (and subsequently updated
throughout the tool) are the "Paid Attendees" and "Conference Comps"
items. All other attendance records should be updated on their
respective tabs.

### Venue

Use this sheet to itemize any venue related expenses/credits. Any rental
fees associated with venue rental should be recorded here (eg. speaking
rooms, breakout rooms, vendor expo, training rooms, reception rental …)
Audio/Visual or other expenses should be placed in the A/V Tab. An
example of common expenses has been provided. If your conference has
both catering and venue costs with one vendor, please split between the
two sheets. Enter any credits as negative values.

### Catering

Use this sheet to itemize any venue related expenses/credits related to
**DAILY** catering expenses. Please track any "Catering" items under
entertainment expenses for networking events or hosted events. An
example of common expenses has been provided. Please tailor to your
conference requirements. Enter any credits as negative values.

### Accommodations

Use this sheet to itemize any venue related expenses/credits related to
conference provided accommodation expenses. It is customary for
conferences to cover the accommodations of key conference staff, board
members and committee members. Enter any credits as negative values.

### Training

Use this sheet to itemize any training classes that will be offered at
the conference. The totals entered here will be automatically updated as
revenue on the dashboard and the participation of trainers and attendees
will automatically be updated where appropriate. Profit margins are
based on a 75/25 split with OWASP/Vendor. Enter any costs as negative
values as this sheet is counted to revenue.

### Sponsors

This sheet outlines all of the sponsorship revenue and complementary
event tickets for the conference. Sponsorship opportunities are
conference specific, but common offerings and prices are listed in the
outlined box below. Revenues and complementary tickets will
automatically be updated throughout the tool. Enter any costs as
negative values as this sheet is counted to revenue.

### Schwag

OWASP has a relationship to purchase conference schwag from
[Crestline](http://www.crestline.com/). Enter any schwag items with unit
cost below. The \# of Attendees will be automatically populated form the
Attendance tab. Enter the additional margin for purchase and the totals
will be calculated automatically. Enter any credits as negative values.

### Travel

Use this sheet to itemize any expenses/credits related to conference
provided travel expenses. It is customary for conferences to cover the
direct travel accommodations of board members and committee members as
well as a reasonable per diem for expenses.

### Entertainment

Use this sheet to itemize any venue related expenses/credits related to
**any special events**. Examples include musical guests, networking
events, staff/speaker events, or dinners. Please track any catering
items for these events here. An example of common expenses has been
provided. Please tailor to your conference requirements but ensure that
the total cost appears in cell B4 for use on the dashboard. Enter any
credits as negative values.

### Audio Visual (AV)

Use this sheet to itemize any venue related expenses/credits related to
Audio Visual requirements. Be sure to sum up any guaranteed minimums in
cell B5. Enter any credits as negative values.

### Promotion

Use this sheet to itemize expenses/credits related to
promotion/advertising costs. Enter any credits as negative values.

### Contests

Use this sheet to itemize expenses/credits related to conference
contests/prizes. Enter any credits as negative values.

### Signage and Booklets

Use this sheet to outline any expenses or credits related to Signage or
other printed materials. Enter any credits as negative values.

### Misc

For anything that doesn't fit anywhere else