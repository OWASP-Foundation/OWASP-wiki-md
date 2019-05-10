## IT Foundation Tier of Cloud (or Data Center)

This layer contains the IT hardware and underlying datacenter
technologies that enable clouds. The critical components of a cloud
enabled datacenter are

  - Computing Hardware
  - Storage/Filers
  - Networking
  - Virtualization Technologies (Xen, VMWare,...)
  - Load Balancers and Management (both in hardware and software)
  - ….

Some of the areas that IT foundation/Data Center tier needs to deal with
are

  - Physical location of the DC (geography)
  - Availability of Resources like Power, Network (ISPs), Cooling
  - Scaling of computing hardware ( small servers vs. big super domes)
  - Logical Segregation Architecture (especially when dealing with
    Multi-Tenancy)
  - People (Controlling Administrative Access)

## Security Risks

### 1\. Data Center Disaster Recovery and Failovers

One of the biggest risk user's of a Cloud Foundation layer face is to
handle disaster recovery and failover scenarios. Due to complexity of
the virtualized data center and multi-dependency on underlying
components MTBF (Mean time between Failures) becomes very low. There has
been multiple incidents logged every week related to these \[3\].

Incident \[1\] with Xero a SaaS provider in New Zealand that went
offline due to power failure in one of the 9 datacenters used by the
underlying infrastructure provider Rackspace is a good example that
shows how inter dependencies if not mapped properly can cause failures.
In this case the underlying service provider had 9 global data centers
and failure of one should have been transparent to the customers.

### 2\. Logical Isolation of Resources for Multi-Tenancy

If the Cloud DC is to be used by multiple tenants. An architecture to
support logical separation of the resources at all the layers is
essential i.e. Computing (Virtualization) , Networking (Virtual Switches
and VLANs) and Storage (logical separation of files with access
controls) is required. Due to logical nature of these controls a lot
will be dependent on keeping a very tight control on the configurations,
that maintain these logical controls.

Google docs flaw that allowed unauthorized users to see personal files
\[6\] is a good example.

### 3\. Administrative Access Controls

Like in any Data Center, administrators generally will still have full
access to all the resources. E.g. ability to clone a given
Virtual-Machine or add a span port to snoop the traffic or even directly
access a sensitive customer file. A very tight control starting with the
background check of the administrator to full audit-ability and spot
monitoring of all the activities performed by the administrative users
is required.

An administrator at Amazon accidentally deleted cloud resources causing
outages \[7\].

### 4\. Domino Effect and Dependencies in Cloud

As compared to the traditional 3 tier application architecture
(Web/App/DB) most of the cloud applications/services have a very complex
dependency. A cloud service may be using another Mashup or web service
provisioned by another Cloud vendor. This can create Domino effect
scenario where failure or delays in one service can impact multiple
dependent services.

Virtualization and logical controls are still dependent on the
underlying hardware. Failure in one can put unexpected load on to other
resources making them fall one by one.

An Active-Active architecture where another hot standby active component
takes up making the handover transparent to the consuming services.

### 5\. Backups and Data Loss

Storage within a Cloud solution many times is distributed across the
data centers and have complex logical controls over the data such as
encryption to keep multiple tenants segregated. IT foundation layer
needs to ensure that the data gets backed up properly to ensure minimal
data loss in case of any failures. It also need to ensure that the
service or application can still perform if one of the node or DC is
down. Amazon EC2 had an outage in 2007 that wiped out customer data
\[8\].

There have also been incident where a storage provider (Mediamax \[5\])
seized operation leaving the data owned by the users/consumers
inaccessible and in limbo.

Cloud Computing Wiki \[4\] is another good resource to look at incidents
related to Cloud Computing.

## Reference:

1.  <http://www.nbr.co.nz/article/xero-taken-offline-massive-us-data-centre-failure-104349>
2.  <http://dcsblog.burtongroup.com/>
3.  <http://www.datacenterknowledge.com/archives/2009/07/06/the-day-after-a-brutal-week-for-uptime/>
4.  <http://wiki.cloudcommunity.org/wiki/CloudComputing:Incidents_Database>
5.  <http://www.demo.com/community/?q=node/160512>
6.  <http://www.scmagazineus.com/Google-Docs-flaw-could-allow-others-to-see-personal-files/article/116703/?DCMP=EMC-SCUS_Newswire>
7.  <http://www.theregister.co.uk/2008/08/28/flexiscale_outage/>
8.  <http://www.datacenterknowledge.com/archives/2007/10/02/amazon-ec2-outage-wipes-out-data/>

__NOTOC__ <headertabs/>

[Category:OWASP Cloud ‐ 10
Project](Category:OWASP_Cloud_‐_10_Project "wikilink")