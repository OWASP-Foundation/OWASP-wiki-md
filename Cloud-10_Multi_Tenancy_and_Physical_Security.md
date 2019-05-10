## R7: Multi Tenancy and Physical Security

Multi-tenancy in cloud means sharing of resources and services to run
software instances serving multiple consumers and client organizations
(tenants). It means physical resources (such as computing, networking,
storage) and services are shared, also the administrative functionality
and support may also be shared. One of the big driver for providers is
to reduce cost by sharing and reusing resources among tenants.

In a multi-tenant environment a lot more security dependence on the
logical segregation (at multiple layers) rather than the physical
separation of resources. Some of the cloud providers due to mult-tenancy
may not allow audit and assessment by a particular tenant within their
shared infrastructure.

## Security Risks

1.  **Inadequate Logical Security Controls**: Physical resources (CPU,
    networking, storage/databases, application stack) are shared between
    multiple tenants. That means dependence on logical segregation and
    other controls to ensure that one tenant deliberately or
    inadvertently can not interfere with the security ( confidentiality,
    integrity, availability) of the other tenants.
2.  **Malicious or Ignorant Tenants**: If the provider has weaker
    logical controls between tenants, a malicious or an ignorant tenant
    may reduce the security posture of other tenants.
3.  **Shared Services can become single point of failure**: If the
    provider has not architected well the common services, they can
    easily become single point of failure due to misuse or abuse by a
    tenant.
4.  **Uncoordinated Change Controls and Mis configurations**: When
    multiple tenants are sharing the underlying infrastructure all
    changes needs to be well coordinated and tested .
5.  **Co-mingled Tenant Data** : To reduce cost providers may be storing
    the data from multiple tenants in same database table-spaces and
    backup tapes. Data destruction can become a challenge in
    multi-tenancy especially if data is stored in the shared media
    (databases, backups, archives).
6.  **Performance Risks** :One tenant’s heavy use of the service may
    impact the quality of service provided to other tenants.
7.  **XaaS Specific Risks**
    1.  **SaaS**: Multiple clients (tenants) may be sharing the same
        application stack ( database, app/web servers, networking). That
        means the data from multiple tenants may get stored in the same
        database, may get backed up and archived together, may be moving
        on common networking devices (unencrypted), and managed by
        common application processes. This puts a heavy emphasis on
        logical security built within the application to separate one
        tenant's users from others.
    2.  **PaaS**: Platform stack is shared among the tenants.
        Vulnerability in the platform stack can allow bleeding between
        tenants. Shared data backups and archives.
    3.  **IaaS**: Cross Virtual machine attacks. Cross network traffic
        listening. Co-residents with lower security posture, where they
        are less concerned about keeping their hosts hardened and
        patched \[5\]. Especially when these hosts gets compromised and
        owned by the attackers.

## Countermeasures

1.  **Architecting for Multi-Tenancy** : Providers need to architect for
    multi-tenants, rather than making services that are not designed for
    multi-tenancy to work. Multi-tenancy architecture should take into
    account logical segregation, strengthen common services and single
    point of failures. Also provide more transparency to
    consumers/tenants \[12\].
2.  **Data Encryption**: For encrypting the data and keeping it separate
    from other tenants , strong encryption complemented by tenant-owned
    key management is required. In a virtualized environment, this means
    that encryption can be done granularly on a per-VM basis, with key
    management owned by the tenant and not the service provider \[1\].
3.  **Controlled Change Management** : eployment of the changes
    (especially to common shared services) should be well planned .
    Usage of feathered release cycles to migrate tenants to new
    infrastructure. For SaaS providers tenants should be progressively
    migrated to newer underlying infrastructure. (Providers need to plan
    extra resources for these activities). Providers should have a
    dependency mapping of tenants to underlying resources and services.
    So that any change in the underlying resources can be well planned.
4.  **Transparency/Audit-ability of Administrative Access**: Tenants
    should have knowledge on administrative access to all their
    resources/services. One of the way is to have audit-ability of admin
    access enabled at all the layers of stack (OS, networking,
    applications , databases) that can be auditable by the tenants.
    Provider may still be doing the administration but under strong
    auditable environment.
5.  **Virtual Private Cloud (VPC)** : It is a private cloud existing
    within a shared or public cloud. A VPC is a way to partition a
    public cloud (multi-tenancy) into quarantined virtual infrastructure
    \[3\] and link it back to the tenants internal resources by
    encrypted network links.
6.  **Third Party Assessments**: Alternate assessment options or
    contractual exceptions if the auditing is required as per the
    consumer's security posture but provider does not allow it \[6\].
7.  **Tenant Isolation** : Tenants can always negotiate or demand from
    the cloud provider to have their own separate physical
    infrastructure, databases, storage, networking gears,.. . Isolation
    does play a great role in the security field. However, it does
    increase the cost for tenants/clients.

## Related Incidence

1.  **Wordpress Outage June 2010**

WordPress that houses high profile blogging sites (such as CNN,
Techcrunch), 3 data centers (1300 servers , 10 million blogs) had an
outage due to config changes done by programmer (to a database field).
It impacted a large set of tenants on this multitenant blogging service
\[7,8,9\].

## Reference:

1.  <http://chucksblog.emc.com/chucks_blog/2010/01/thoughts-on-secure-multitenancy.html>
2.  <http://aws.amazon.com/vpc/>
3.  <http://www.elasticvapor.com/2008/05/virtual-private-cloud-vpc.html>
4.  <http://blogs.gartner.com/thomas_bittman/2009/01/08/virtual-cloud-privacy-is-gray/>
5.  <http://people.csail.mit.edu/tromer/papers/cloudsec.pdf>
6.  <http://www.cloudsecurityalliance.org/csaguide.pdf>
7.  <http://smoothspan.wordpress.com/2010/06/11/wordpress-and-the-dark-side-of-multitenancy/>
8.  <http://techcrunch.com/2010/06/10/wordpress-gives-us-the-vip-treatment-goes-down-on-us-again/>
9.  <http://hakre.wordpress.com/2010/06/14/wordpress-outage-feedback/>
10. <http://en.blog.wordpress.com/2010/06/14/downtime/>
11. <http://www.enterpriseirregulars.com/14980/security-risks-of-multi-tenancy/>
12. <http://salesforcechannel.com/video/Multitenant-Magic-Under-the-Cov>
13. <http://natishalom.typepad.com/nati_shaloms_blog/2010/03/multitenancy-does-it-have-to-be-that-hard.html>

__NOTOC__ <headertabs/>

[Category:OWASP Cloud ‐ 10
Project](Category:OWASP_Cloud_‐_10_Project "wikilink")