## R9:Infrastructure Security

The security of the data hosted within an application is totally
dependent upon the security of the infrastructure components that make
up the platform for the application. Failure to take "best practices"
into account can lead to a loss of data, reputation, or availability,
and may even have regulatory/legal ramifications.


Security Risks



1.  Default configurations of systems and network devices. A system,
    application or network device "fresh out of the box" is likely to be
    running old versions of its software, and not be up-to-date with
    regards to security updates. Furthermore, standard configurations,
    passwords, exploits etc. are well known and the details of those
    circulate freely on the Internet, and will mean these systems are
    much more likely to become compromised.
2.  All services, even active, unused ones, may contain security related
    bugs that potentially can be exploited, and malicious parties are
    actively scanning the Internet. Running such services even though
    one isn't actually using it for any purposes, will therefore
    needlessly increase the likelyhood of an organizations
    infrastructure becoming the target of an exploit.
3.  Compromised services may be used as "hop-off" points to other
    services, unless they are contained. For example, a compromised web
    service may lead to a compromised backend database, if the database
    can be reached directly from the web tier.
4.  Active network protocols, and open ports, may be exploited even if
    they are not used in the solution architecture.
5.  Administrative access may be abused, either deliberately by the
    administrators, or through compromised administrative accounts.
    Furthermore administrative access can cause disruption through
    accidents
6.  All code (application, OS, network) will contain security related
    bugs, and configurations may contain configuration mistakes, that
    can be exploited.



Countermeasures



1.
2.  Hardening of operating systems, applications and configurations. The
    purpose of this is to reduce the risk of an exploit via a vulnerable
    system service, application, unused or insecure default accounts
    etc. There are many approaches to this, and

3.  Tiering of the solution architecture. A tiered solution architecture
    will mean that a system directly exposed to for example the Internet
    is less likely to be used by a perpetrator as a hop-off point deeper
    into the organization's infrastructure. "Flat" networks where for
    example an Internet-facing system can talk directly a backend
    database server should be looked at with scrutiny.

4.  Isolation of infrastructure components, for example through the use
    of network ACLs, to reduce the

5.  Role-based administrative access and restricted administrative
    privileges. Any organization should try to restrict administrative
    access to resources to people who "need to know", and to ensure that
    roles are well defined. For example, if database administrators,
    system administrators and network administrators have clearly
    defined and delineated roles, the risk of an incident via an
    individual maliciously using his privileges, or makes an accidental
    mistake, will be reduced.

6.  Regular vulnerability assessments. Every organization should do
    regular risk assessments of their infrastructure, as well as
    vulnerability assessments of code they develop. Where
    customer/client/partner information is involved, the organizations
    must expect that the other parties have an interest in knowing how
    their data is protected, and only independent assessments/audits are
    likely to be accepted as trustworthy.


References

1.  Center for Internet Security (CISecurity)
    <http://www.cisecurity.org/>
2.  SANS Institute - Reading Room: <http://www.sans.org/reading_room/>

__NOTOC__ <headertabs />

[Category:OWASP_Cloud_‐_10_Project](Category:OWASP_Cloud_‐_10_Project "wikilink")