## Capture the Flag Overview

Test your skills with a capture the flag (CTF) hacking competition
created specifically for SnowFROC by members of the Boulder OWASP
chapter.

Competitors will be provided a series of web applications containing a
variety of vulnerabilities. Each discovered vulnerability will earn
points. The harder the hack, the more points earned. At the end of the
day, the team with the most points wins.

## Rules

All conference attendees may participate in the CTF tournament for no
additional cost. If you would prefer to attend the general conference
proceedings, the competition will be made available to attendees after
SnowFROC ends.

### Format

Contestants will be provided a virtual machine which will run locally on
self-provided devices. This is a BYOD event and all contestants are
responsible for providing their own machine. No "loaners" will be made
available.

All contestant machines should have:

  - A virtual machine player that supports .vmdk files, such as [VMware
    Player](http://www.vmware.com/products/player/),
    [VirtualBox](https://www.virtualbox.org/wiki/Downloads), or
    [Parallels](http://www.parallels.com/).
  - Appropriate penetration testing tool
    ([BackTrack](http://www.backtrack-linux.org),
    [SamuraiWTF](http://samurai.inguardians.com/), [Mantra
    OS](OWASP_Mantra_OS "wikilink"), and [OWASP ZAP](ZAP "wikilink")
    will fit in well).

### Acceptable behavior

Competitors are only permitted to attack targets running on their local
systems. Network traffic will be monitored to ensure there will be:

  - No attacking the
    [scoreboard](SnowFROC2013_CTF_Scoreboard "wikilink"). Misuse will
    result in punitive action.
  - No targeting the VM. Do not mount the VM and harvest flags from
    within.
  - No attacking other teams, whether through coercion, DoS, theft,
    sabotage, or other malicious activity.
  - No collusion. Work only within your own team.

### Prizes

Small prizes will be awarded to winners. Anyone who worked on the
project or who has access to project-related repositories is ineligible
to win prizes.

Both team and individual prizes will be awarded based on merit and other
achievements. -- Team prizes will be awarded to:

  - The team with the most points;
  - The team who completed the story first (or, as a tiebreaker, the
    team with the most plot-specific points);
  - The team who took the shortest amount of time to complete Acts I-IV;

Individual prizes will be awarded to:

  - The person who solved the hardest challenge (worth the most points);
  - The person who solved the most challenges (raw number);
  - The person who scored the most points (total sum);

\--\>

## Getting Started

### Content acquisition

This information will be released closer to the day of the event.

### Installation and configuration instructions

  - Add the following entries to your hosts file:

` 10.50.65.12 training.theagency.owasp, theagency.owasp`
` 10.56.65.87 theagency.owasp, Im.theagency.owasp`
` 10.50.65.26 www.pla.owasp, secretlogin.pla.owasp, download.pla.owasp, www.pla.pt`
` 10.50.65.187 shadowcorp.owasp`
` 198.19.147.198 ctf.snowfroc.com`

  - The first network adapter must be a bridge network adapter.
  - Configure the second network adapter to be a host-only network on
    your VM with IP address 10.50.65.254/24
  - Load the .vmdk files
  - Make sure you are using a browser other than Internet Explorer which
    for security reasons is not supported by the scoreboard.

<!-- end list -->

  - Make sure you are on the CTFSnowFROC wifi network (or plugged in
    directly at a table).

<!-- end list -->

1.  Start by copying VM over to your machine. While that is going on,
    move on to the next steps.
2.  Make sure hosts file has the entries provided above.
3.  Within VirtualBox, go to file --\> preferences --\> network --\> add
    host only network adapter.
4.  Edit this new adapter - put in 10.50.65.254 255.255.255.0
5.  In the VirtualBox main page- go to New, give the VM a name, set type
    to BSD, click next, set mem to at least 1 GB, Use Existing Virtual
    HD. Point it to the ctf.vmdk file you copied onto your machine.
    Create.
6.  Select VM in the VirtualBox main window, at top click settings. go
    to network, adapter 1, change to "Bridged Adapter". Adpater 2,
    enable network adapter, make it a host only adapter and select the
    adapter you created earlier. Hit ok.
7.  Start VM. Follow directions provided in VM.

### Registration instructions

Coming soon.

### Gameplay instructions