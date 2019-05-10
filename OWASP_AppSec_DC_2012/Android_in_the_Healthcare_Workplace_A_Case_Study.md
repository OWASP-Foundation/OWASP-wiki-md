<noinclude></noinclude> __NOTOC__

## The Presentation

With Android tablets and phones taking over the market share of the
mobile landscape; companies are starting to develop enterprise
applications for this. I work for a Home Health company, basically think
of visiting nurses. We have a 75% mobile workforce and we migrated our
primary platform to Android. Having the need to verify our vendor's
claims, I decided to test the app from a standard web app perspective.
The application is designed for the mobile staff to sync their work back
to the "cloud." What I found was truly alarming. Not only was the app
NOT using SSL, it was very easy for me to analyze the packets and get
information out of them which would allow me to gain access to PHI. In
order for the application to be configured, only two pieces of
information are need; the server name and agent ID. Both I was able to
get in plaintext and hex out of the captured packets. With this
information I would be able to configure the application and impersonate
the agent id I captured. This could potentially allow me to access
several hundred patient records which are protected by HIPAA.

## The Speakers

<table>

<tr>

<td>

### Thomas Richards

![Owasp_logo_normal.jpg](Owasp_logo_normal.jpg
"Owasp_logo_normal.jpg")Thomas Richards is an IT professional located in
Rochester, NY. He currently is responsible for network and system
administration for a medium sized Healthcare company. He has always had
an interest in the security field and currently holds the OSCP, OSWP,
GPEN, and Security+ certifications.

In his spare time he conducts vulnerability research and is an active
participant in his local 2600 group.

</td>

</tr>

</table>

<noinclude></noinclude>