---
title: Provide cost-effective storage for Hyper-V workloads by using Windows Server: planning and design guide
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.technology: 
  - hyper-v
  - server-message-block-(smb)
  - techgroup-storage
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3314f967-8a2c-48c6-bfc7-3137cc30a075
---
# Provide cost-effective storage for Hyper-V workloads by using Windows Server: planning and design guide
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This guide describes how to plan and design one particular storage solution for compute clusters that host virtual machines running on Windows Server and Hyper-V as part of a cloud service platform. This software-defined storage solution uses an easily-managed Windows Server file server cluster in conjunction with just-a-bunch-of-disks (JBOD) enclosures and Storage Spaces for high performance, cost-effective storage, obviating the need for expensive SAN devices when implementing a cloud platform.</para>
    
    <para>For a list of recent changes to this topic, see the <link xlink:href="3314f967-8a2c-48c6-bfc7-3137cc30a075#BKMK_History">Change History</link> section of this topic.</para>
    <para>If you haven’t already, you should read the <link xlink:href="e70fcb94-0576-4582-a1e0-8c41f8d745cc">Using Windows Server to Provide Storage for Hyper-V Workloads Solution Guide</link> – it provides an introduction to this solution and is meant to be used with this topic.</para>
    <para>We assume that you want to target an initial deployment of roughly 100 tenants (with eight virtual machines per tenant), with the ability to expand the solution to roughly 500 tenants over time. For more flexible and comprehensive design guidance, see <externalLink><linkText>Software-Defined Storage Design Considerations Guide</linkText><linkUri>http://technet.microsoft.com/library/mt243829.aspx</linkUri></externalLink>.</para>
    <para>Use the following steps and design decisions to plan for implementing Windows Server-based storage for Hyper-V workloads.</para>
    <para>
      <legacyBold>In this guide:</legacyBold>
    </para>
    <list class="bullet">
      <listItem>
        <para>
          <link xlink:href="3314f967-8a2c-48c6-bfc7-3137cc30a075#BKMK_Step1">Step 1: Design the file server cluster</link>
        </para>
      </listItem>
      <listItem>
        <para>
          <link xlink:href="3314f967-8a2c-48c6-bfc7-3137cc30a075#BKMK_Step2">Step 2: Design the management cluster</link>
        </para>
      </listItem>
      <listItem>
        <para>
          <link xlink:href="3314f967-8a2c-48c6-bfc7-3137cc30a075#BKMK_Step3">Step 3: Design the compute cluster</link>
        </para>
      </listItem>
      <listItem>
        <para>
          <link xlink:href="3314f967-8a2c-48c6-bfc7-3137cc30a075#BKMK_NextSteps">Next steps</link>
        </para>
      </listItem>
    </list>
  </introduction>
  <section address="BKMK_Step1">
    <title>Step 1: Design the file server cluster</title>
    <content>
      <para>In this step, you design the file server cluster used to provide the storage to virtual machines in this solution.</para>
    </content>
    <sections>
      <section>
        <title>1.1. Design the file server cluster hardware</title>
        <content>
          <para>Here are the hardware components we recommend for the file server clusters. Note that we recommend purchasing all production hardware from a vendor that tests and supports the hardware as an integrated solution with Storage Spaces. </para>
          <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
            <thead>
              <tr>
                <TD>
                  <para>Component</para>
                </TD>
                <TD>
                  <para>Guidelines</para>
                </TD>
              </tr>
            </thead>
            <tbody>
              <tr>
                <TD>
                  <para>Storage enclosures</para>
                </TD>
                <TD>
                  <list class="bullet">
                    <listItem>
                      <para>Four identical storage enclosures (240 disks total in four enclosures)</para>
                      <para>With four enclosures an entire enclosure can fail and storage spaces will remain online (assuming that there aren’t too many failed disks in the remaining enclosures). </para>
                      
                    </listItem>
                    <listItem>
                      <para>SAS-connected 60-disk storage enclosures</para>
                      
                    </listItem>
                    <listItem>
                      <para>Each storage enclosure must be connected via two SAS connections through a Host Bus Adapter (HBA) to all nodes of the file server clusters </para>
                      <para>This maximizes performance and eliminates a single point of failure. To support this requirement, ideally each storage enclosure and server node would have twice the number of SAS ports as the number of nodes (8 ports on the enclosure and 8 ports on each node). </para>
                    </listItem>
                  </list>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>Physical disks</para>
                </TD>
                <TD>
                  <list class="bullet">
                    <listItem>
                      <para>48 7200 rpm HDDs per storage enclosure (192 HDDs total in four enclosures)</para>
                      <para>7,200 rpm HDDs provide lots of capacity while consuming less power and costing less than higher rotational speed HDDs, but they still provide good performance in this solution when matched with a sufficient number of SSDs.</para>
                      <para>When using 4 TB HDDs and 800 GB SSDs in four 60-bay enclosures, this solution provides about 804 TB of raw storage pool capacity per file server cluster. After resiliency, storage for backups, and free space for repairing storage spaces is factored in, this yields roughly 164 TiB of space for compute and management virtual machines (TiB is a terabyte calculated using binary - base 2 - notation instead of decimal - base 10 - notation).</para>
                    </listItem>
                    <listItem>
                      <para>12 SSDs per storage enclosure (48 SSDs total in four storage enclosures)</para>
                      <para>Storage Spaces uses SSDs to create a faster storage tier for frequently accessed data. It also uses SSDs for a persistent write back cache that reduces the latency of random writes. </para>
                      <para>For more information, see <legacyLink xlink:href="5de72fb5-e1e3-43a7-a176-d17cdf4d312e">What's New in Storage Spaces in Windows Server</legacyLink>.</para>
                    </listItem>
                    <listItem>
                      <para>All disks must be dual-port SAS disks</para>
                      <para>This enables each disk to be connected to all nodes of the failover cluster via SAS expanders included in the storage enclosures.</para>
                    </listItem>
                  </list>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>File server clusters</para>
                </TD>
                <TD>
                  <list class="bullet">
                    <listItem>
                      <para>One four-node file server cluster</para>
                      <para>With four nodes, all storage enclosures are connected to all nodes and you can maintain good performance even if two nodes fail, reducing the urgency of maintenance.</para>
                    </listItem>
                    <listItem>
                      <para>One file server cluster hosts the storage for one compute cluster </para>
                      <para>If you add a compute cluster, also add another four-node file server cluster. You can add up to four file server clusters and four compute clusters per management cluster. The first file server cluster also hosts the storage for the management cluster.</para>
                      <para>Additional clusters (also called scale units) let you increase the scale of your environment to support more virtual machines and tenants.</para>
                    </listItem>
                  </list>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>Cluster nodes</para>
                </TD>
                <TD>
                  <list class="bullet">
                    <listItem>
                      <para>Two six-core CPUs </para>
                      <para>The file server cluster doesn’t need the most powerful CPUs because most traffic is handled by RDMA network cards, which process network traffic directly.</para>
                    </listItem>
                    <listItem>
                      <para>64 GB of RAM</para>
                      <para>You don’t need a lot of RAM because the file server cluster uses storage tiers, which prevents the usage of a CSV cache (typically one of the largest consumers of RAM on a clustered file server).</para>
                    </listItem>
                    <listItem>
                      <para>Two HDDs set up in a RAID-1 (mirror) using a basic RAID controller</para>
                      <para>This is where Windows Server is installed on each node. As an option, you can use one or two SSDs. SSDs cost more, but use less power and provide faster startup, setup, and recovery times as well as increased reliability. You can use a single SSD to reduce costs if you’re OK with reinstalling Windows Server on the node if the SSD fails.</para>
                    </listItem>
                  </list>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>Cluster node HBAs</para>
                </TD>
                <TD>
                  <list class="bullet">
                    <listItem>
                      <para>Two identical 4 port 6 Gbps SAS HBAs </para>
                      <para>Each of the HBAs has one connection to every storage enclosure so that there are two connections in total to every storage enclosure. This maximizes throughput and provides redundant paths, and can’t have built-in RAID functionality. </para>
                    </listItem>
                  </list>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>Cluster node network interface cards</para>
                </TD>
                <TD>
                  <list class="bullet">
                    <listItem>
                      <para>One dual-port 10 gigabit Ethernet network interface card with RDMA support</para>
                      <para>This card acts as the storage network interface between the file server cluster and the compute and management clusters, each of which store their virtual hard disk files on the file server cluster. </para>
                      <para>The card requires RDMA support to maximize performance and iWARP if you want to use routers in-between racks of clusters, which can be relevant when adding additional compute and file server clusters to the solution. This card uses SMB 3 and SMB Direct to provide fault tolerance, with each port connected to a separate subnet.</para>
                      <para>For a list of certified network interface cards with RDMA support, see the <externalLink><linkText>Windows Server Catalog</linkText><linkUri>http://windowsservercatalog.com/results.aspx?&amp;chtext=&amp;cstext=&amp;csttext=&amp;chbtext=&amp;bCatID=1468&amp;cpID=0&amp;avc=10&amp;ava=0&amp;avq=46&amp;OR=1&amp;PGS=25&amp;ready=0</linkUri></externalLink>.</para>
                    </listItem>
                    <listItem>
                      <para>One dual-port gigabit or 10 gigabit Ethernet network interface card without RDMA support</para>
                      <para>This card communicates between the management cluster and the file server cluster, with each port connected to a separate subnet. It doesn’t need RDMA support because it communicates with the Hyper-V virtual switches on the management and compute clusters, which can’t use RDMA communication.</para>
                      <para>For a list of certified network interface cards, see the <externalLink><linkText>Windows Server Catalog</linkText><linkUri>http://windowsservercatalog.com/results.aspx?&amp;chtext=&amp;cstext=&amp;csttext=&amp;chbtext=&amp;bCatID=1468&amp;cpID=0&amp;avc=10&amp;ava=0&amp;avq=0&amp;OR=1&amp;PGS=25&amp;ready=0</linkUri></externalLink>.</para>
                    </listItem>
                    <listItem>
                      <para>One gigabit Ethernet network interface for remote management</para>
                      <para>This integrated lights-out (ILO), baseboard management controller (BMC), or onboard networking adapter connects to your management network. </para>
                    </listItem>
                  </list>
                </TD>
              </tr>
            </tbody>
          </table>
        </content>
      </section>
      <section address="BKMK_DesignFileServer">
        <title>1.2. Design the file server cluster software configuration</title>
        <content>
          <para>Here are the software components we recommend for the file server clusters.</para>
          <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
            <thead>
              <tr>
                <TD>
                  <para>Technology</para>
                </TD>
                <TD>
                  <para>Guidelines</para>
                </TD>
              </tr>
            </thead>
            <tbody>
              <tr>
                <TD>
                  <para>Operating system</para>
                </TD>
                <TD>
                  <list class="bullet">
                    <listItem>
                      <para>
                        <token>winblue_server_standard_2</token> with the Server Core installation option</para>
                      <para>Using <token>winblue_server_standard_2</token> saves money over using a more expensive edition, and the Server Core installation option keeps the security footprint low, which in turns limits the amount of software updates that you need to install on the file server cluster.</para>
                    </listItem>
                  </list>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>Failover Clustering</para>
                </TD>
                <TD>
                  <list class="bullet">
                    <listItem>
                      <para>One Scale-Out File Server</para>
                      <para>This clustered file server enables you to host continuously available file shares that are simultaneously accessible on multiple nodes.</para>
                    </listItem>
                  </list>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>MPIO</para>
                </TD>
                <TD>
                  <list class="bullet">
                    <listItem>
                      <para>Enable Multipath I/O (MPIO) on each node</para>
                      <para>This combines the multiple paths to physical disks in the storage enclosures, providing resiliency and load balancing across physical paths.</para>
                    </listItem>
                  </list>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>Storage pools</para>
                </TD>
                <TD>
                  <list class="bullet">
                    <listItem>
                      <para>Three clustered storage pools per file server cluster</para>
                      <para>This helps minimize the time required to fail over the storage pool to another node.</para>
                    </listItem>
                    <listItem>
                      <para>5 SSDs and 16 HDDs from each of the four storage enclosures per workload pool, for a total of 84 disks per pool for your primary workloads.  </para>
                      <para>This provides enough SSDs to enable you to create the appropriate storage spaces, with the data distributed across the storage enclosures so that any storage enclosure can fail without resulting in downtime for your tenants (as long as there aren’t too many failed disks in the remaining storage enclosures).</para>
                    </listItem><listItem><para>2 SSDs and 16 HDDs from each of the four storage enclosures for a backup pool, with a total of 72 disks in this pool.</para><para>The SSDs in the backup pool are designated as journal disks to enhance the write performance of the virtual disks, which use the dual-parity resiliency type.</para></listItem>
                    <listItem>
                      <para>No hot spare disks</para>
                      <para>Instead always keep at least 21.9 TiB of free HDD space in each of the storage pools, plus and 1.5 TiB of free SSD space  in each of the workload pools. This enables Storage Spaces to automatically rebuild storage spaces with up to one failed SSD and 3 failed HDDs by copying data to multiple disks in the pool, drastically reducing the time it takes to recover from the failed disk when compared to using hot spares.</para>
                      <para>In this solution with 4 TB HDDs and 800 GB SSDs, this means keeping 23.4 TB of free space per workload pool.</para>
                      <para>For more information on how we come up with these numbers, see <externalLink><linkText>Software-Defined Storage Design Considerations Guide</linkText><linkUri>http://technet.microsoft.com/library/mt243829.aspx</linkUri></externalLink> and the <externalLink><linkText>Software-Defined Storage Design Calculator</linkText><linkUri>http://aka.ms/sdscalc</linkUri></externalLink>.</para>
                    </listItem>
                  </list>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>Storage spaces</para>
                </TD>
                <TD>
                  <list class="bullet">
                    <listItem>
                      <para>Eight storage spaces per workload storage pool</para>
                      <para>This distributes load across each node in the cluster (two storage spaces per node, per pool).</para>
                    </listItem>
                    <listItem>
                      <para>Use three-way mirror spaces for workload data </para>
                      <para>Mirror spaces provide the best performance and data resiliency for hosting virtual machines. Three-way mirror spaces ensure that there are at least three copies of data, allowing any two disks to fail without data loss. We don’t recommend parity spaces for hosting virtual machines due to their performance characteristics. </para>
                    </listItem>
                    <listItem>
                      <para>Use the following settings to construct your three-way mirror spaces with storage tiers, the default write-back cache size, and enclosure awareness. We recommend four columns for this configuration for a balance of high throughput and low latency.</para>
                      <para>For more information, see <externalLink><linkText>Software-Defined Storage Design Considerations Guide</linkText><linkUri>http://technet.microsoft.com/library/mt243829.aspx</linkUri></externalLink>.</para>
                      <table>
                        <thead>
                          <tr>
                            <TD>
                              <para>Setting</para>
                            </TD>
                            <TD>
                              <para>Value</para>
                            </TD>
                          </tr>
                        </thead>
                        <tbody>
                          <tr>
                            <TD>
                              <para>
                                <codeInline>ResiliencySettingName</codeInline>
                              </para>
                            </TD>
                            <TD>
                              <para>
                                <codeInline>Mirror</codeInline>
                              </para>
                            </TD>
                          </tr>
                          <tr>
                            <TD>
                              <para>
                                <codeInline>NumberOfDataCopies</codeInline>
                              </para>
                            </TD>
                            <TD>
                              <para>
                                <codeInline>3</codeInline>
                              </para>
                            </TD>
                          </tr>
                          <tr>
                            <TD>
                              <para>
                                <codeInline>NumberOfColumns</codeInline>
                              </para>
                            </TD>
                            <TD>
                              <para>
                                <codeInline>4</codeInline>
                              </para>
                            </TD>
                          </tr>
                          <tr>
                            <TD>
                              <para>
                                <codeInline>StorageTierSizes</codeInline>
                              </para>
                            </TD>
                            <TD>
                              <para>SSD: <codeInline>.54 TiB</codeInline>; HDD: <codeInline>8.79 TiB</codeInline> (assuming 800 GB SSDs and 4 TB HDDs)</para>
                            </TD>
                          </tr>
                          <tr>
                            <TD>
                              <para>
                                <codeInline>IsEnclosureAware</codeInline>
                              </para>
                            </TD>
                            <TD>
                              <para>
                                <codeInline>$true</codeInline>
                              </para>
                            </TD>
                          </tr>
                        </tbody>
                      </table>
                    </listItem>
                    <listItem>
                      <para>All storage spaces use fixed provisioning </para>
                      <para>Fixed provisioning enables you to use storage tiers and failover clustering, neither of which work with thin provisioning.</para>
                    </listItem>
                    <listItem>
                      <para>Create one additional 4 GB two-way mirror space without storage tiers</para>
                      <para>This storage space is used as a witness disk for the file server cluster, and is used for file share witnesses for the management and compute clusters. This helps the file server cluster maintain its integrity (quorum) in the event of two failed nodes or network issues between nodes. </para>
                    </listItem><listItem><para>For your backup pool, use the following settings to create 16 virtual disks using the dual-parity resiliency type and 7 columns.</para><table>
                        <thead>
                          <tr>
                            <TD>
                              <para>Setting</para>
                            </TD>
                            <TD>
                              <para>Value</para>
                            </TD>
                          </tr>
                        </thead>
                        <tbody>
                          <tr>
                            <TD>
                              <para>
                                <codeInline>ResiliencySettingName</codeInline>
                              </para>
                            </TD>
                            <TD>
                              <para>
                                <codeInline>Parity</codeInline>
                              </para>
                            </TD>
                          </tr>
                          <tr>
                            <TD>
                              <para>
                                <codeInline>NumberOfDataCopies</codeInline>
                              </para>
                            </TD>
                            <TD>
                              <para>
                                <codeInline>3</codeInline>
                              </para>
                            </TD>
                          </tr>
                          <tr><TD><para><codeInline>Size</codeInline></para></TD><TD><para><codeInline>7.53 TiB</codeInline></para></TD></tr><tr>
                            <TD>
                              <para>
                                <codeInline>NumberOfColumns</codeInline>
                              </para>
                            </TD>
                            <TD>
                              <para>
                                <codeInline>7</codeInline>
                              </para>
                            </TD>
                          </tr>
                          
                          <tr>
                            <TD>
                              <para>
                                <codeInline>IsEnclosureAware</codeInline>
                              </para>
                            </TD>
                            <TD>
                              <para>
                                <codeInline>$true</codeInline>
                              </para>
                            </TD>
                          </tr>
                        </tbody>
                      </table></listItem>
                  </list>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>Partitions</para>
                </TD>
                <TD>
                  <list class="bullet">
                    <listItem>
                      <para>One GPT partition per storage space</para>
                      <para>This helps keep the solution simpler.</para>
                    </listItem>
                  </list>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>Volumes</para>
                </TD>
                <TD>
                  <list class="bullet">
                    <listItem>
                      <para>One volume formatted with the NTFS file system per partition/storage space</para>
                      <para>ReFS isn’t recommended for this solution in this release of Windows Server.</para>
                    </listItem><listItem><para>Enable Data Deduplication on the virtual disks used for storing backups.</para></listItem>
                  </list>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>CSV</para>
                </TD>
                <TD>
                  <list class="bullet">
                    <listItem>
                      <para>One CSV volume per volume (with one volume and partition per storage space)</para>
                      <para>This enables the load to be distributed to all nodes in the file server cluster. Don’t create a CSV volume on the 4 GB storage space used to maintain cluster quorum.</para>
                    </listItem>
                  </list>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>BitLocker Drive Encryption</para>
                </TD>
                <TD>
                  <list class="bullet">
                    <listItem>
                      <para>Test BitLocker Drive Encryption performance before using widely</para>
                      <para>You can use BitLocker Drive Encryption to encrypt all data in storage on each CSV volume, improving physical security, but doing so can have a significant performance impact on the solution.</para>
                    </listItem>
                  </list>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>Continuously available file shares</para>
                </TD>
                <TD>
                  <list class="bullet">
                    <listItem>
                      <para>One continuously available SMB file share per CSV volume/volume/partition/storage space</para>
                      <para>This makes management simpler (one share per underlying storage space), and enables the load to be distributed to all nodes in the file server cluster.</para>
                    </listItem>
                    <listItem>
                      <para>Test the performance of encrypted data access (SMB 3 encryption) on file shares before deploying widely</para>
                      <para>You can use SMB 3 encryption to help protect data on file shares that require protection from physical security breaches where an attacker has access to the datacenter network, but doing so eliminates most of the performance benefits of using RDMA network adapters.</para>
                    </listItem>
                  </list>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>Updates</para>
                </TD>
                <TD>
                  <list class="bullet">
                    <listItem>
                      <para>Use Windows Server Update Services in conjunction with <token>vmmblue_2</token></para>
                      <para>Create three to four computer groups in Windows Server Update Services (WSUS) for the file server nodes, adding one or two to each group. With this setup, you can update one server first and monitor its functionality, then update the rest of the servers one at a time so that load continues to be balanced across the remaining servers. </para>
                      <para>For more information, see <externalLink><linkText>Managing Fabric Updates in VMM</linkText><linkUri>http://technet.microsoft.com/library/gg675084.aspx</linkUri></externalLink> (or <legacyLink xlink:href="5ad27d64-0749-4b84-a8c1-21ffe5bccd3f">Deploy Windows Server Update Services in Your Organization</legacyLink> if you’re not using <token>vmmblue_2</token>).</para>
                    </listItem>
                    <listItem>
                      <para>Use Cluster-Aware Updating for UEFI and firmware updates</para>
                      <para>Use Cluster-Aware Updating to update anything that can’t be distributed via WSUS. This probably means the BIOS (UEFI) for the cluster nodes along with the firmware for network adapters, SAS HBAs, drives, and the storage enclosures.</para>
                    </listItem>
                  </list>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>Data Protection Manager</para>
                </TD>
                <TD>
                  <list class="bullet">
                    <listItem>
                      <para>You can use Data Protection Manager (DPM) to provide crash-consistent backups of the file server cluster. You can also use DPM and Hyper-V replication for disaster recovery of virtual machines on the compute cluster.</para>
                    </listItem>
                  </list>
                </TD>
              </tr>
            </tbody>
          </table>
        </content>
      </section>
    </sections>
  </section>
  <section address="BKMK_Step2">
    <title>Step 2: Design the management cluster</title>
    <content>
      <para>In this step, you design the management cluster that runs all of the management and infrastructure services for the file server and compute clusters. </para>
      <alert class="note">
        <para>This solution assumes that you want to use the System Center suite of products, which provide powerful tools to streamline setting up, managing, and monitoring this solution. However, you can alternatively accomplish all tasks via Windows PowerShell and Server Manager (though you’ll probably find Windows PowerShell to be more appropriate due to scale of this solution). If you choose to forgo using System Center, you probably don’t need as powerful a management cluster as described here, and you might be able to use existing servers or clusters.</para>
      </alert>
    </content>
    <sections>
      <section>
        <title>2.1. Design the management cluster hardware</title>
        <content>
          <para>Here are the hardware components we recommend for the cluster that runs all of the management and infrastructure services for the file server and compute clusters.</para>
          <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
            <thead>
              <tr>
                <TD>
                  <para>Component</para>
                </TD>
                <TD>
                  <para>Guidelines</para>
                </TD>
              </tr>
            </thead>
            <tbody>
              <tr>
                <TD>
                  <para>Management cluster</para>
                </TD>
                <TD>
                  <list class="bullet">
                    <listItem>
                      <para>One 4-node failover cluster</para>
                      <para>Using four nodes provides the ability to tolerate one cluster node in the management cluster failing; use six nodes to be resilient to two nodes failing. One management cluster using Virtual Machine Manager can support up to 8,192 virtual machines.</para>
                    </listItem>
                  </list>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>Cluster nodes</para>
                </TD>
                <TD>
                  <list class="bullet">
                    <listItem>
                      <para>Two eight-core CPUs</para>
                      <para>The virtual machines on this cluster do a significant amount of processing, requiring a bit more CPU power than the file server cluster.</para>
                    </listItem>
                    <listItem>
                      <para>128 GB of RAM</para>
                      <para>Running the management virtual machines requires more RAM than is needed by the file server cluster.</para>
                    </listItem>
                    <listItem>
                      <para>Two HDDs set up in a RAID-1 (mirror) using a basic RAID controller</para>
                      <para>This is where Windows Server is installed on each node. As an option, you can use one or two SSDs. SSDs cost more, but use less power and provide faster startup, setup, and recovery times as well as increased reliability. You can use a single SSD to reduce costs if you’re OK with reinstalling Windows Server on the node if the SSD fails.</para>
                    </listItem>
                  </list>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>Network interface cards</para>
                </TD>
                <TD>
                  <list class="bullet">
                    <listItem>
                      <para>One dual-port 10 gigabit Ethernet network interface card with RDMA support</para>
                      <para>This card communicates between the management cluster and the file server cluster for access to the .vhdx files used by the management virtual machines. The card requires RDMA support to maximize performance and iWARP if you want to use routers in-between racks of file server and management clusters, which can be relevant when adding additional file server clusters to the solution. This card uses SMB 3 and SMB Direct to provide fault tolerance, with each port connected to a separate subnet.</para>
                      <para>For a list of certified network interface cards with RDMA support, see the <externalLink><linkText>Windows Server Catalog</linkText><linkUri>http://windowsservercatalog.com/results.aspx?&amp;chtext=&amp;cstext=&amp;csttext=&amp;chbtext=&amp;bCatID=1468&amp;cpID=0&amp;avc=10&amp;ava=0&amp;avq=46&amp;OR=1&amp;PGS=25&amp;ready=0</linkUri></externalLink>.</para>
                    </listItem>
                    <listItem>
                      <para>One dual-port gigabit or 10 gigabit Ethernet network interface card without RDMA support</para>
                      <para>This card handles management traffic between all clusters. The card requires support for Virtual Machine Queue (VMQ), Dynamic VMQ, <?Comment JG: Fromhttp://technet.microsoft.com/en-us/library/hh831630.aspx. Or should we say this?promiscuousmode with multiple VLANs 2014-01-03T15:11:00Z  Id='50?>802.1Q VLAN tagging<?CommentEnd Id='50'
    ?>, and GRE offload (NVGRE). The card uses NIC Teaming to make its two ports, each connected to a separate subnet, fault tolerant. </para>
                      <para>The card can’t make use RDMA because RDMA requires direct access to the network card, and this card needs to communicate with Hyper-V virtual switches (which obscure direct access to the network card). It uses the NIC teaming technology for fault tolerance instead of SMB Direct so that protocols other than SMB can make use of the redundant network connections. You should use Quality of Service (QoS) rules to prioritize traffic on this connection.</para>
                      <para>For a list of certified network interface cards with NVGRE support, see the <externalLink><linkText>Windows Server Catalog</linkText><linkUri>http://windowsservercatalog.com/results.aspx?&amp;chtext=&amp;cstext=&amp;csttext=&amp;chbtext=&amp;bCatID=1468&amp;cpID=0&amp;avc=10&amp;ava=0&amp;avq=44&amp;OR=1&amp;PGS=25&amp;ready=0</linkUri></externalLink>.</para>
                    </listItem>
                    <listItem>
                      <para>One gigabit Ethernet network interface for remote management</para>
                      <para>This integrated lights-out (ILO), baseboard management controller (BMC), or onboard networking adapter connects to your management network.</para>
                    </listItem>
                  </list>
                </TD>
              </tr>
            </tbody>
          </table>
        </content>
      </section>
      <section>
        <title>2.2. Design the management cluster software configuration</title>
        <content>
          <para>The following list describes at a high level the software components we recommend for the management cluster:</para>
          <list class="bullet">
            <listItem>
              <para>
                <token>winblue_server_datacenter_2</token>
              </para>
            </listItem>
            <listItem>
              <para>Failover Clustering</para>
            </listItem>
            <listItem>
              <para>Cluster-Aware Updating</para>
            </listItem>
            <listItem>
              <para>Hyper-V</para>
            </listItem>
          </list>
          <para>The following list describes at a high level the services that you should run in virtual machines on the management cluster:</para>
          <list class="bullet">
            <listItem>
              <para>Active Directory Domain Services (AD DS), DNS Server, and DHCP Server</para>
            </listItem>
            <listItem>
              <para>Windows Server Update Services</para>
            </listItem>
            <listItem>
              <para>Windows Deployment Services</para>
            </listItem>
            <listItem>
              <para>Microsoft SQL Server</para>
            </listItem>
            <listItem>
              <para>System Center Virtual Machine Manager</para>
            </listItem>
            <listItem>
              <para>System Center Virtual Machine Manager Library Server</para>
            </listItem>
            <listItem>
              <para>System Center Operations Manager</para>
            </listItem>
            <listItem>
              <para>System Center Data Protection Manager</para>
            </listItem>
            <listItem>
              <para>A management console (Windows Server with the GUI installation option)</para>
            </listItem>
            <listItem>
              <para>Additional virtual machines are required depending on the services you’re using, such as Windows Azure Pack, and System Center Configuration Manager.</para>
            </listItem>
          </list>
          <alert class="note">
            <para>Create identical virtual switches on all nodes so that each virtual machine can fail over to any node and maintain its connection to the network.</para>
          </alert>
        </content>
      </section>
    </sections>
  </section>
  <section address="BKMK_Step3">
    <title>Step 3: Design the compute cluster</title>
    <content>
      <para>In this step, you design the compute cluster that runs the virtual machines that provide services to tenants.</para>
    </content>
    <sections>
      <section>
        <title>2.1. Design the compute cluster hardware</title>
        <content>
          <para>Here are the hardware components we recommend for the compute clusters. These clusters house tenant virtual machines.</para>
          <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
            <thead>
              <tr>
                <TD>
                  <para>Component</para>
                </TD>
                <TD>
                  <para>Guidelines</para>
                </TD>
              </tr>
            </thead>
            <tbody>
              <tr>
                <TD>
                  <para>Hyper-V compute clusters</para>
                </TD>
                <TD>
                  <list class="bullet">
                    <listItem>
                      <para>Each compute cluster contains 32 nodes and hosts up to 2,048 Hyper-V virtual machines. When you’re ready to add extra capacity, you can add up to three additional compute clusters (and associated file server clusters for a total of 128 nodes hosting 8,192 virtual machines for 512 tenants (assuming 8 VMs per tenant).</para>
                      <para>See <legacyLink xlink:href="1db68a42-6cd8-48fb-95ce-19aa79bf2ec7">Hyper-V scalability in Windows Server 2012 and Windows Server 2012 R2</legacyLink> for more information.</para>
                    </listItem>
                  </list>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>Cluster nodes</para>
                </TD>
                <TD>
                  <list class="bullet">
                    <listItem>
                      <para>Two eight-core CPUs</para>
                      <para>Two eight-core CPUs are sufficient for a general mix of workloads, but if you intend to run a lot of computation heavy workloads in your tenant virtual machines, select higher performance CPUs.</para>
                    </listItem>
                    <listItem>
                      <para>128 GB of RAM </para>
                      <para>Running the large number of virtual machines (probably 64 per node while all nodes of the cluster are running) requires more RAM than is needed by the file server cluster. Use more RAM if you want to provide more than 2 GB per virtual machine on average.</para>
                    </listItem>
                    <listItem>
                      <para>Two HDDs set up in a RAID-1 (mirror) using a basic RAID controller</para>
                      <para>This is where Windows Server is installed on each node. As an option, you can use one or two SSDs. SSDs cost more, but use less power and provide faster startup, setup, and recovery times as well as increased reliability. You can use a single SSD to reduce costs if you’re OK with reinstalling Windows Server on the node if the SSD fails.</para>
                    </listItem>
                  </list>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>Network interface cards</para>
                </TD>
                <TD>
                  <list class="bullet">
                    <listItem>
                      <para>One dual-port 10 gigabit Ethernet network interface card with RDMA support</para>
                      <para>This card communicates with the file server cluster for access to the .vhdx files used by virtual machines. The card requires RDMA support to maximize performance and iWARP if you want to use routers in-between racks of file server and management clusters, which can be relevant when adding additional file server clusters to the solution. This card uses SMB 3 and SMB Direct to provide fault tolerance, with each port connected to a separate subnet.</para>
                      <para>For a list of certified network interface cards with RDMA support, see the <externalLink><linkText>Windows Server Catalog</linkText><linkUri>http://windowsservercatalog.com/results.aspx?&amp;chtext=&amp;cstext=&amp;csttext=&amp;chbtext=&amp;bCatID=1468&amp;cpID=0&amp;avc=10&amp;ava=0&amp;avq=46&amp;OR=1&amp;PGS=25&amp;ready=0</linkUri></externalLink>.</para>
                    </listItem>
                    <listItem>
                      <para>One dual-port gigabit or 10 gigabit Ethernet network interface card without RDMA support</para>
                      <para>This card handles management and tenant traffic. The card requires support for Virtual Machine Queue (VMQ), Dynamic VMQ, 802.1Q VLAN tagging, and GRE offload (NVGRE). The card uses NIC Teaming to make its two ports, each connected to a separate subnet, fault tolerant. </para>
                      <para>The card can’t make use RDMA because RDMA requires direct access to the network card, and this card needs to communicate with Hyper-V virtual switches (which obscure direct access to the network card). It uses the NIC teaming technology for fault tolerance instead of SMB Direct so that protocols other than SMB can make use of the redundant network connections. You should use Quality of Service (QoS) rules to prioritize traffic on this connection.</para>
                      <para>For a list of certified network interface cards with NVGRE support, see the <externalLink><linkText>Windows Server Catalog</linkText><linkUri>http://windowsservercatalog.com/results.aspx?&amp;chtext=&amp;cstext=&amp;csttext=&amp;chbtext=&amp;bCatID=1468&amp;cpID=0&amp;avc=10&amp;ava=0&amp;avq=44&amp;OR=1&amp;PGS=25&amp;ready=0</linkUri></externalLink>.</para>
                    </listItem>
                    <listItem>
                      <para>One gigabit Ethernet network interface for remote management</para>
                      <para>This integrated lights-out (ILO), baseboard management controller (BMC), or onboard networking adapter connects to your management network and enables you to use System Center Virtual Machine Manager to set up the cluster node from bare-metal hardware. The interface must have support for Intelligent Platform Management Interface (IPMI) or Systems Management Architecture for Server Hardware (SMASH).</para>
                    </listItem>
                  </list>
                </TD>
              </tr>
            </tbody>
          </table>
        </content>
      </section>
      <section>
        <title>2.2. Design the compute cluster software configuration</title>
        <content>
          <para>The following list describes at a high level the software components we recommend for the compute cluster:</para>
          <list class="bullet">
            <listItem>
              <para>
                <token>winblue_server_datacenter_2</token>
              </para>
            </listItem>
            <listItem>
              <para>Failover Clustering</para>
            </listItem>
            <listItem>
              <para>Hyper-V</para>
            </listItem>
            <listItem>
              <para>Data Center Bridging</para>
            </listItem>
            <listItem>
              <para>Cluster-Aware Updating</para>
            </listItem>
          </list>
        </content>
      </section>
    </sections>
  </section>
  <section address="BKMK_NextSteps">
    <title>Next steps</title>
    <content>
      <para>After you have completed the planning steps, see <link xlink:href="e70fcb94-0576-4582-a1e0-8c41f8d745cc#BKMKSteps">What are the high-level steps to implement this solution?</link>.</para>
    </content>
  </section>
  <section>
    <title>See also</title>
    <content>
      <list class="bullet">
        <listItem><para>
            <link xlink:href="e70fcb94-0576-4582-a1e0-8c41f8d745cc">Using Windows Server to Provide Storage for Hyper-V Workloads Solution Guide</link>
          </para>
        </listItem><listItem>
          <para><externalLink><linkText>Software-Defined Storage Design Considerations Guide</linkText><linkUri>http://technet.microsoft.com/library/mt243829.aspx</linkUri></externalLink></para></listItem>
      </list>
    </content>
  </section>
  <section address="BKMK_History">
    <title>Change History</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Date</para>
            </TD>
            <TD>
              <para>Description</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr><TD><para>July 15th, 2015</para></TD><TD><para>Updated guidance for virtual disk design, and added links to <externalLink><linkText>Software-Defined Storage Design Considerations Guide</linkText><linkUri>http://technet.microsoft.com/library/mt243829.aspx</linkUri></externalLink>, which provides more detailed and up-to-date storage design information.</para></TD></tr><tr>
            <TD>
              <para>June 18th, 2014</para>
            </TD>
            <TD>
              <para>Updated guidance around how much free space to set aside in each pool for rebuilding storage spaces, and updated virtual disk sizes and other numbers accordingly</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>April 2nd, 2014</para>
            </TD>
            <TD>
              <para>Removed Windows Catalog links to SAS disks and SAS HBAs because the links were confusing</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>January 22nd, 2014</para>
            </TD>
            <TD>
              <para>Preliminary publication</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics/>
</developerConceptualDocument>
