## R1:Accountability and Data Ownership

__NOTOC__ <headertabs/> A traditional data center of an organization
is under complete control of that organization. The organization
logically and physically protects the data it owns. For economical
reasons, an organization may choose to use a public cloud for hosting
its business services. In this case, the organization loses control of
its data. This poses critical security risks that the organization needs
to carefully consider and mitigate.

The severity of risks depends on the sensitivity of the data stored in
the cloud. Informal blogs, twitter posts, public news, and newsgroup
messages are examples of less sensitive data. The risk of hosting such
data in the cloud is low. On the contrary, data such as health-related
records, criminal records, credit history, and payroll information is
highly sensitive business data. There are serious business and legal
ramifications if such data is compromised. Therefore, the risk of
hosting such data in the cloud is very high.

Since data in the cloud is physically in control of the cloud provider,
the foremost risk is that of ensuring confidentiality of the stored
data. Encryption can be employed to ensure confidentiality. If the cloud
provider uses multi-tenancy architecture, then separate encryption keys,
one per cloud consumer, should be employed.

A cloud provider may physically store a consumer's data in various
countries. Such architecture poses several risks. For example, a country
has its own legal system, and the cloud provider operating in that
country is bound to that system. The laws of a country may force a cloud
provider to permit legal officials to access the data, and any
encryption keys, stored in that country's geographical boundary. The
physical location of data can additionally have economic ramifications.
For example, the tax rules vary based on the country in which sales
orders are processed. A cloud consumer may not be able to benefit
economically by processing orders in a country that offers lowest tax
rates, since the cloud provider may store orders data in any country.

A cloud provider may store the consumer's data in its premises, or
employ an Infrastructure-As-A-Provider (IAAS) for data storage. The
provider may use multi-tenancy architecture which collocates data of
multiple cloud consumers in one physical storage. This architecture may
lack appropriate controls to ensure that a cloud consumer can access
only its own data, and not the data of other consumers. If the cloud
consumers are competitors in their business domain, then such such lack
of control can pose serious business risks for the consumers.

Upon a request to delete some data, a cloud provider may only nominally
delete it, and leave traces that can be used to reconstruct the original
data. Such reconstructed data can be stolen, and misused, posing a
significant risk to the cloud consumer.

To mitigate various data related risks, an organization that uses a
cloud for conducting business should do the following:

1\. Understand how the cloud provider secures the data and how the
provider detects and reports a compromise.

2\. Know the geographical location of the data storage, and ensure that
the provider will not store data in a restricted country.

3\. Know the situations in which a third party or a government can sieze
the data from the provider. The provider should provide advanced
notification of such event.

4\. Ensure that the cloud provider appropriately protects data based on
the data classification as specified by the consumer, and to address the
concerns of privacy laws such as HIPPA.

5\. The provider by default denies all access to the consumer's data.
The consumer organization can explicitly grant access with specific
privilege to desired parties.

6\. The provider encrypts the data at rest, and the data in transit.

7\. The provider logically isolates the data of multiple consumers in
such a way so as to prevent any unauthorized access, modification, or
deletion of the data.

8\. Understand how the cloud provider manages ecnryption for multiple
consumers. Instead of a single encryption key for all consumers, the
provider should use (atleast) one key per consumer.

9\. Verify that the provider destroys deleted data in such a way that it
cannot be later recreated.

10\. In case of a data breach, make the cloud provider pay certain
penalty.

Real-world incident: On July 15, 2009, Twitter disclosed that a hacker
accessed a substantial amount of company data stored on Google Apps by
first hijacking a Twitter employee's official e-mail account. Though the
breach had more to do with weak passwords and password resets, the
incident has nevertheless drawn fresh attention to broader security and
privacy concerns related to cloud computing.

[Category:OWASP Cloud ‐ 10
Project](Category:OWASP_Cloud_‐_10_Project "wikilink")