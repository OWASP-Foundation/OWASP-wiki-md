2010 OWASP Infrastructure

1.  Web Server
    1.  Fedora Linux
    2.  Hosts
        1.  Wiki
        2.  MySQL
        3.  Virtual Domain for ads.owasp.org
            1.  Runs openx ad server for banner ads on owasp.org site.
    3.  Sends and receives email
    4.  Current hardware running at \~50-60% usage
        1.  Dell PowerEdge 1325
        2.  Dual Core, 4 GB RAM, 2 mirrored drives
        3.  240 GB drive
            1.  \~ 39% full (84 GB)
            2.  \~4 GB in DB backups of the wiki (done nightly)
        4.  Backed up 2x per month locally and on Aspect hardware
2.  List Server
    1.  Fedora
    2.  Hosts
        1.  lists.owasp.org (mailman email lists)
        2.  MySQL
    3.  Sends and receives email
    4.  Current hardware
        1.  Dell 750 PowerEdge
        2.  4 GB RAM, 80 GB mirrored drives
        3.  Frequently chokes on owasp mail list volume - esp sends to
            owasp-all list
3.  Gmail handles email for owasp.org email domain
4.  DNS managed by the current ISP (Verio)