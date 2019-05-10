**A Guide to Building Secure Web Applications and Web Services**

2.1 (DRAFT 3) February 2006 OWASP Foundation

[Development Guide Table of
Contents](Guide_Table_of_Contents "wikilink") __TOC__

## Dedication

To my fellow procrastinators and TiVo addicts, this book proves that
given enough “tomorrows,” anything is possible. --Andrew van der Stock

## Copyright and license

© 2001 – 2006 OWASP Foundation. The Development Guide is licensed under
the GNU Free Documentation License, a copy of which is found in the
Appendix. PERMISSION IS GRANTED TO COPY, DISTRIBUTE, AND/OR MODIFY THIS
DOCUMENT PROVIDED THIS COPYRIGHT NOTICE AND ATTRIBUTION TO OWASP IS
RETAINED.

## Editors

The Development Guide has had several editors over various editions, all
of whom have contributed immensely as authors, project managers, and
editors over the lengthy period of the Development Guide’s gestation.
Development Guide 2.x series editors:

Andrew van der Stock Adrian Wiesmann

## Authors and Reviewers

The Development Guide would not be where it is today without the
generous gift of volunteer time and effort from many individuals. The
following people helped develop Development Guide 2.x:

<table>
<tbody>
<tr class="odd">
<td><p>valign="top"</p></td>
<td><ul>
<li>Ernesto Arroyo</li>
<li>José Pedro Arroyo</li>
<li>Derek Browne</li>
<li>Izhar By-Gad</li>
<li>Daniel Cornell</li>
<li>Martin Eizner</li>
<li>David Endler</li>
<li>Raoul Endres</li>
<li>Brian Greidanus</li>
<li>Dennis Groves</li>
<li>Darrel Grundy</li>
</ul></td>
<td><p>valign="top"</p></td>
<td><ul>
<li>Robert Hansen</li>
<li>William Hau</li>
<li>Michael Howard</li>
<li>Sverre Huseby</li>
<li>Abraham Kang</li>
<li>Eoin Keary</li>
<li>Amit Klein</li>
<li>Neal Krawetz</li>
<li>Erik Lee</li>
<li>Frank Lemmon</li>
<li>Hal Lockhart</li>
</ul></td>
<td><p>valign="top"</p></td>
<td><ul>
<li>Gene McKenna</li>
<li>Kevin McLaughlin</li>
<li>Roy McNamara</li>
<li>K.K. Mookhey</li>
<li>Richard Parke</li>
<li>Denis Pilipchuk</li>
<li>Jeremy Poteet</li>
<li>Michael Scovetta</li>
<li>Mikael Simonsson</li>
<li>Tim Smith</li>
<li>Ray Stirbei</li>
</ul></td>
<td><p>valign="top"</p></td>
<td><ul>
<li>Steve Taylor</li>
<li>Christopher Todd</li>
<li>Nigel Tranter</li>
<li>Andrew van der Stock</li>
<li>Adrian Wiesmann</li>
</ul></td>
</tr>
</tbody>
</table>

## Revision History

|  |                    |  |                          |  |           |  |                                                                                      |
|  | ------------------ |  | ------------------------ |  | --------- |  | ------------------------------------------------------------------------------------ |
|  | **Date**           |  | **Version**              |  | **Pages** |  | **Notes**                                                                            |
|  | July 26, 2005      |  | 2.0 Blackhat Edition     |  | 280 pages |  | Andrew van der Stock, Guide Lead                                                     |
|  | July 27, 2005      |  | 2.0.1 Blackhat Edition++ |  | 293 pages |  | Cryptography chapter review from Michael Howard incorporated                         |
|  | September 12, 2005 |  | 2.1 DRAFT 1              |  | X pages   |  | Changes from many sources New SQA chapter from Frank Lemmon                          |
|  | January 2006       |  | 2.1 DRAFT 2              |  | X pages   |  | Changes from Bill Pollock New chapters from Erick Lee New revisions from Dan Cornell |
|  | February 2006      |  | 2.1 DRAFT 3              |  | X pages   |  | Ajax chapter Many chapters back from reviewers                                       |
|  |                    |  |                          |  |           |  |                                                                                      |

[Development Guide Table of
Contents](Guide_Table_of_Contents "wikilink")

[Category:OWASP_Guide_Project](Category:OWASP_Guide_Project "wikilink")