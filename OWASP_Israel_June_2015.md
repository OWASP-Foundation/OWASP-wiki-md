Our second meeting in 2015 for the Israel chapter of OWASP took place on
June 16, at 17:00, in Microsoft's Herzeliya office, 13 Shenkar St.,
Building Gev-Yam 5. Around 120 people attended.

This time, OWASP Israel joined forces with the Israel chapter of CSA\!
This was a joint meeting, with both chapters hosting. This was a great
opportunity to expand our horizons, hear different relevant topics, and
network with slightly different group of people.

Some pictures from the event:
<https://drive.google.com/folderview?id=0B8J0WK4IGF11MElhR08tb1hDVkE&usp=sharing>

## Agenda:

''' 17:00 – 17:45
''' **Gathering, food, and drinks (KOSHER)**

''' 17:45 – 18:10
''' ''' Introductions and Opening Notes '''

''' 18:10 – 18:50
''' ''' One Key to Rule Them All: Detecting the Skeleton Key Malware
*'
*' Itai Grady & Tal Be’ery, Microsoft ''' ([download
presentation](Media:OWASPIL-2015-06-16_Skeleton_Key_Malware_Detection.pptx "wikilink"))

Identity is one of the cornerstones of application security. On Windows
domains, identity is managed through Active Directory (AD) Domain
service on the Domain Controller (DC), and many applications are
integrated with AD. Therefore, it should come as no surprise that
attackers are actively targeting the DC in order to gain rogue access to
applications and servers.

Earlier this year, Dell Secureworks had shared a report on an advanced
attack campaign utilizing a dedicated DC malware, named “Skeleton Key”
Malware. The Skeleton Key malware modifies the DC behavior to accept
authentications specifying a secret ”Skeleton key” (i.e. “master key”)
password, thus enabling the attackers to login to any application as any
domain user without installing any additional malware while keeping the
original users’ authentication behavior.

In this talk, we will explore the unique interaction between such
malware functionality and the Kerberos authentication protocol; We will
put a special emphasis on its manifestation over the network traffic. We
will also share a script that implements the remote detection of the
skeleton key malware functionality.

''' 18:50 – 19:30
''' ''' Software Defined Networks are emerging – How will it affect
security? *'
*' Almog Ohayon, Javelin Networks ''' ([download
presentation](Media:OWASPIL-2015-06-16_Software-Defined-Networks-Security.pdf "wikilink"))

Software-Defined Networking beyond its technological impact is first of
all a mindset changer, it makes network engineers think like developers
and push them into a world of API’s and automation.

SDN and NFV will help companies to achieve faster deployments, better
security, better performance, and reduction of capital and operational
expenses.

We live in a world where business growth and agility are strong
requirements from investors and owners and no one wants infrastructure
slower him down.

I spent 4 months in the Silicon Valley trying to have better
understating from the world most advanced business and technical
leaders, people who created the SDN “world”, startup companies who are
trying to disrupt the market with new solutions and I will share with
you my technical and business perspective of the last 2 years.

''' 19:30 – 19:50
''' ''' Coffee break & desserts '''

''' 19:50 – 20:30
''' ''' Outsmarting researchers: Fraudsters and their security practices
*'
*' Julia Karpin, F5 Networks ''' ([download
presentation](Media:OWASPIL-2015-06-16_Outsmarting_Researchers-Fraudsters_and_their_Security.pdf "wikilink"))

Attackers, or “fraudsters” as we call them in the financial malware
world are security people too. They are proficient in cryptography,
software developing paradigms and security concepts. They incorporate
these well-known concepts into their infrastructure although not always
very successfully 

During the research of different malware types, we encountered
interesting ways and tricks the fraudsters implement in order to protect
their “proprietary” software and secure their communication channels,
the details of these tricks will be the main focus of this talk. Of
course the banking institutes they are targeting have a few tricks up
their sleeves as well. This arms race will also be discussed during this
talk.

[Category:Israel](Category:Israel "wikilink")