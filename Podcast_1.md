**[OWASP Podcast Series](OWASP_Podcast "wikilink") \#1**

<b>Recorded November 21, 2008</b>
[<http://images.apple.com/itunes/overview/images/overview-icon-itunes20081106.jpg>](http://itunes.apple.com/WebObjects/MZStore.woa/wa/viewPodcast?id=300769012)
[<https://www.owasp.org/images/d/d3/Feed-icon-32x32.png>](http://www.owasp.org/download/jmanico/podcast.xml)
[direct
download](http://www.owasp.org/download/jmanico/owasp_podcast_1.mp3)

## Participants

`- Arshan Dabirsiaghi is the the Director of Research for Aspect Security.`
`- Jeremiah Grossman is the CTO of Whitehat.`
`- Jim Manico is a Web Application Architect and Security Engineer for Aspect Security. `
`- Jeff Williams is the CEO of Aspect Security and also volunteers as one of the chairs of the OWASP Foundation.`

## Recap OWASP EU Summit

`- Talked with Adobe rep`
`- Figured out the charter for ISWG`
`- OWASP Live CD `<http://www.owasp.org/index.php/Category:OWASP_Live_CD_Project>
`- Press coverage is hilarious`
`- OWASP Education Project `<http://www.owasp.org/index.php/Category:OWASP_Education_Project>
`- `[`Clickjacking``
 ``trends`](http://www.google.com/trends?q=xss%2C+clickjacking)

## Builder vs Breaker

`- is this a real skill gap?`
`- easier to build/defend`
`- fixing stuff is boring (kuza55)`

## We've reached Application Security Tipping Point

`- Chris Wysopal (Zero in a bit)`
`- Attacks are getting simpler (and we're barely fixing old vulns)`
`- Assets are moving more and more to the web`
`- New technology  =  make all same mistakes again`
`- Aspect never wanted to be NGS - but everything is broken`
`- Just this morning, hilarious SSO product bypass (thats all we'll say, not method/verb tampering)`

## Canonicalization is a nightmare

`- mod_security turns off Unicode validation by default`
`- another commercial WAF bypassable by default with invalid UTF-8`
`- any byte-based validation is failure on the web (or unmanaged langs)`

## Securing WebGoat with mod_security

`- Summer of Code project with Stephen Craig Evans`
`- very interesting Lua scripting capability`
`- stateful WAFing is possible with Lua`
`- `[`Modsecurity``   ``and``
 ``HTTPOnly`](http://blog.modsecurity.org/2008/12/helping-protect-cookies-with-httponly-flag.html)