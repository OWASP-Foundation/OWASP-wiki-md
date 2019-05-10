Notes about Dinis Cruz work on [ORG (Owasp Report
Generator)](ORG_\(Owasp_Report_Generator\) "wikilink")

## Change Log on CVS Files

  - note: in the current version one needs to copy the contents of the
    VulnReport_Files to the ..\\Application (Exe)\\v0.83
  - Mike has added the Altova component to the CVS (11Mb :) ) but it
    works :)

## Configuring CVS access using tortoise CVS behind a proxy (to be added to project documentation)

NOTE: This is now out of date since we use Google's code SubVersion,
which is much easier to use and setup

These are the steps you need to take:

  - Install the latest version of Tortoise CVS (from
    <http://www.tortoisecvs.org/>)
  - Create a connection using Putty to your proxy with the following
    tunnel:
      - Source port: 22
      - Destination: 66.35.250.83:22
  - try SSHing into 127.0.0.1:22 you should get a ssh login priompt
    (after accepting sourceforge ssh fingerprint)
  - on the place where you want the project to be located, click on CVS
    Checkout and use these settings:
      - Protocol: Secure Shell(:ssh:)
      - Server: 127.0.0.1
      - Repository folder: /cvsroot/owasp
      - User name: {username}:{password} (only use this for testing ,
        once it is working see this for details on how to use ssh keys
        <http://blogs.sun.com/alanbur/entry/using_netbeans_with_sourceforge>)
      - Module: dotnet/ReportGenerator
  - click on 'Fetch List' to test connections (you should get no errors)