<table>
<thead>
<tr class="header">
<th><p>width="700" align="center"</p></th>
<th><p><br />
</p></th>
<th><p>width="500" align="center"</p></th>
<th><p><br />
</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>align="right"</p></td>
<td><figure>
<img src="OWASP_Inactive_Banner.jpg" title="OWASP_Inactive_Banner.jpg" alt="OWASP_Inactive_Banner.jpg" width="800" /><figcaption>OWASP_Inactive_Banner.jpg</figcaption>
</figure></td>
<td><p>align="right"</p></td>
<td></td>
</tr>
</tbody>
</table>

# FHR FAQ

## What is FHR?

Simply put, FHR is a repository of hashes of files. But the idea is to
go beyond just keeping a list of hashes: I want the repository to
indicate when the file in question is (part of) a malware or when a file
is recognized as benign. Thus, anyone could see the hash of a file to
see if it corresponds to a malware file or an already known good file.

## Aren't there already other sources for this information?

Yes, and one of the ideas of the project is to aggregate and leverage
information from already existing sources. For example, NIST has the
[NSRL](http://www.nsrl.nist.gov), which provides hashes of known benign
files. The problem is that NIST provides this information in a text file
whose download is over 1GB in size. Other known sources are Team Cymru's
[MHR](http://www.team-cymru.org/Services/MHR/), [SANS Institute's hash
database](http://isc.sans.edu/tools/hashsearch.html) and [Virus
Total](http://www.virustotal.com). In addition to aggregating the
information, one of the main goals for FHR is to allow free access to
its database.

## Isn't free access to a database that contains malware dangerous?

Yes, it's dangerous, but the project repository will not contain
malware. The repository will only have the hashes of malware, which
poses no danger.

## Detecting malware using only hashes is not good strategy.

Certainly, and the project is not intended to replace the current
anti-virus scanners. However, the creation of hashes is more efficient
and easier than creating generic virus detection algorithms and it is a
strategy which is being used as a complement to traditional antivirus
products. Several commercial products include uses of cloud computing as
part of their strategies. Unfortunately, the producers of these
technologies do not allow queries to their hash databases. With FHR, the
goal is to create a freely available database to be used by everyone.

## Will the FHR be integrated into antivirus systems?

We intend to develop clients to the FHR database that can scan
workstations and query FHR's database to try to identify malware. These
clients will be created as a proof of concept and will be open source.
It would be great if some antivirus vendors start supporting FHR, but
only time will tell.

## Technically, how does the FHR work?

As expected, the core of the system is its database of hashes. Today
this database runs on MySQL. Around this database, we can develop
several query interfaces. Some ideas of protocols for querying the FHR
database are:

  - DNS
  - web
  - web services
  - JSON

The current codebase includes a DNS-based query interface.

## What data are available in the database?

We currently have the a little more than 20 million files in the
database. These come mainly from the NSRL and we included several PE
files from Windows Vista and other common software. For each registered
file, we have the following information:

  - SHA-1
  - MD5
  - source
  - date when the system saw the hash / file for the first time (not
    available for the files from NIST)
  - status (GOOD, MALWARE, UNKNOWN, SUSPICIOUS)
  - size
  - certainty (a percentage that indicates the degree of certainty about
    the status of the file).

## Testing the system

To query the FHR, add the suffix .hash.sapao.net to the MD5 or SHA-1
hash (in hex format) of the file. For example:

` dig 84C0C5914FF0B825141BA2C6A9E3D6F4.hash.sapao.net`

or

` dig TXT 84C0C5914FF0B825141BA2C6A9E3D6F4.hash.sapao.net`

will query the database for the hash
**84C0C5914FF0B825141BA2C6A9E3D6F4**.

## If the database is free, where can I get it?

The database is big and difficult to make available for download. We
have however an Amazon AWS snapshot of the database disk. The snapshot
ID is snap-5aacdd27 and its name is FHRDatabase.

To find the snapshot, log in the AWS Console, select the EC2 tab, and
then select "Snapshops" under the "Elastic Block Store" option on the
left pane. Select "Public Snapshots" on the filter dropbox and search
for the ID or name.

IMPORTANT: Please note that the snapshot is in US East region. So assure
you are in that AWS region by selecting "US East (N. Virginia)" on the
dropdown list next to your name on the top right menu of AWS Console.

The snapshot contains a Linux disk with the MySQL Database files. Mount
it into your own instance and you will have access to all the files.

# Roadmap

[Projects/OWASP_File_Hash_Repository/Roadmap](Projects/OWASP_File_Hash_Repository/Roadmap "wikilink")

# Documentation

## Database schema

The FHR database contains a single table, called File, described below:

    mysql> show columns from File in FHR;
    +-----------+------------+------+-----+---------+----------------+
    | Field
    | Type
    | Null
    | Key
    | Default
    | Extra
    |
    +-----------+------------+------+-----+---------+----------------+
    | idFile
    | int(11)
    | NO
    | PRI
    | NULL
    | auto_increment
    |
    | SHA1
    | char(40)
    | YES
    | MUL
    | NULL
    |
    |
    | MD5
    | char(32)
    | YES
    | MUL
    | NULL
    |
    |
    | size
    | mediumtext
    | YES
    |
    | NULL
    |
    |
    | source
    | char(10)
    | YES
    |
    | NULL
    |
    |
    | date
    | date
    | YES
    |
    | NULL
    |
    |
    | status
    | char(10)
    | NO
    |
    | NULL
    |
    |
    | certainty
    | float
    | YES
    |
    | NULL
    |
    |
    +-----------+------------+------+-----+---------+----------------+
    8 rows in set (0.00 sec)

## Server Implementation Details

The DNS server is implemented in Java and is based on the EagleDNS
server, which uses the dnsjava library.

### EagleDNS extensions

The EagleDNS server is easily extended. It is based on the concept of
Zone Providers, which provide specific implementations for the backend
storage of zone data. The server provides two basic providers, one for
loading data from simple zone files and another for loading data from a
database.

At first glance, it could seem that the database zone provider would be
a perfect fit for FHR, but upon a closer examination, we quickly find
out that it is not the case. The main reason is that EagleDNS uses the
dnsjava Zone class to represent zone data. This implementation requires
all zone data to be held in memory, which would be impossible for FHR
since it will contain millions of entries, each corresponding to a DNS
record.

So we had to extend EagleDNS by implementing its ZoneProvider interface.
And we also needed to extend the dnsjava Zone class functionality. This
created a problem since the Zone class was not implemented to be
extended. This required us to change the dnsjava source code and
recompile this library before being able to implement all
FHRZoneProvider class.

The diffs for the dnsjava classes are available at
[OWASP_File_Hash_Repository/dnsjava_diffs](OWASP_File_Hash_Repository/dnsjava_diffs "wikilink")

### The FHRZoneProvider rationale

TODO.

# Project About

__NOTOC__ <headertabs />

[Category:OWASP_Tool](Category:OWASP_Tool "wikilink")
[Category:OWASP_Alpha_Quality_Tool](Category:OWASP_Alpha_Quality_Tool "wikilink")
[Category:OWASP Project](Category:OWASP_Project "wikilink")