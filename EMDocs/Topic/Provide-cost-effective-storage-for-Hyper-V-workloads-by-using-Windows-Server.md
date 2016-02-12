---
title: Provide cost-effective storage for Hyper-V workloads by using Windows Server
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.technology: 
  - techgroup-storage
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e70fcb94-0576-4582-a1e0-8c41f8d745cc
---
# Provide cost-effective storage for Hyper-V workloads by using Windows Server
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>
      <legacyBold>Who is this guide intended for?</legacyBold> Service providers (hosters) that offer Infrastructure-as-a-Service (IaaS) and large organizations that are setting up private clouds.</para>
    <para>
      <legacyBold>How can this guide help you?</legacyBold> You can use this solution guide to understand the high-level design and implementation for one particular file server-based storage solution for Hyper-V compute clusters. Other solutions are possible, but we don’t describe them here.</para>
    <para>The solution uses Storage Spaces with storage tiers, a Scale-Out File Server cluster, and easily managed Server Message Block (SMB) file shares to create a software-defined storage solution that maximizes storage performance, reduces costs, and scales compute resources and storage independently.</para>
    <table border="1"><tbody><tr><TD><mediaLink>
<image xlink:href="4d53ae40-1dbf-4872-ad03-d40f354c6691"/>
</mediaLink></TD><TD><para>Did you know that Microsoft Azure provides similar functionality in the cloud? Learn more about Microsoft Azure <externalLink><linkText>storage</linkText><linkUri>http://aka.ms/y03tdi</linkUri></externalLink> and <externalLink><linkText>virtualization</linkText><linkUri>http://aka.ms/f9bh7g</linkUri></externalLink> solutions.</para><para>Create a hybrid solution in Microsoft Azure:
 
<br/>- <externalLink><linkText>Learn about cost-effective, highly responsive solid-state storage for Azure virtual machines</linkText><linkUri>http://aka.ms/xmo126</linkUri></externalLink><br/>- <externalLink><linkText>Move VM’s between Hyper-V and Microsoft Azure</linkText><linkUri>http://aka.ms/vf75zq</linkUri></externalLink></para></TD></tr></tbody></table><para>The following diagram illustrates the problem and scenario that this solution guide is addressing.</para>
    <para>
      <legacyBold>Storage for virtualized workloads</legacyBold>
    </para>
    <mediaLink>
      <image xlink:href="90f78e10-5ee9-4fa4-b311-2b4d6a83792b"/>
    </mediaLink>
    <para/>
    <alert class="note">
      <para>Make sure to look over the <link xlink:href="e70fcb94-0576-4582-a1e0-8c41f8d745cc#BKMK_Challenges">Challenges for this solution</link> section to see some of the difficult areas where we and our hardware partners are doing ongoing work. For a list of recent changes to this topic, see the <link xlink:href="e70fcb94-0576-4582-a1e0-8c41f8d745cc#BKMK_History">Change History</link> section of this topic.</para>
    </alert>
    <para>
      <legacyBold>In this solution guide:</legacyBold>
    </para>
    <list class="bullet">
      <listItem>
        <para>
          <link xlink:href="e70fcb94-0576-4582-a1e0-8c41f8d745cc#BKMKScenario">Scenario, problem statement, and goals</link>
        </para>
      </listItem>
      <listItem>
        <para>
          <link xlink:href="e70fcb94-0576-4582-a1e0-8c41f8d745cc#BKMKStrategy">What is the recommended planning and design approach for this solution?</link>
        </para>
      </listItem>
      <listItem>
        <para>
          <link xlink:href="e70fcb94-0576-4582-a1e0-8c41f8d745cc#BKMKSteps">What are the high-level steps to implement this solution?</link>
        </para>
      </listItem>
    </list>
  </introduction>
  <section address="BKMKScenario">
    <title>Scenario, problem statement, and goals</title>
    <content>
      <para>This section describes the scenario, problem statement, and goals for this solution guide. </para>
      <para>
        <legacyBold>Scenario</legacyBold>
      </para>
      <para>In this scenario, we’re assuming that you’re either a medium-sized hosting provider offering managed services (including infrastructure as a service), or a large organization looking to set up private clouds. You’re providing enterprises the ability to move an increasing variety of their workloads to the cloud, hosted on Hyper-V virtual machines. But these new workloads come with a staggering amount of data…</para>
      <para>
        <legacyBold>Problem statement</legacyBold>
      </para>
      <para>As you’re no doubt painfully aware, storage represents one of the biggest expenses for hosting cloud services. Data requirements keep growing, and while hard disk prices are falling, you’ve probably been purchasing an increasing number of solid state drives (SSDs) in an attempt to increase performance. The overall effect is that storage continues to be expensive to acquire and operate.</para>
      <para>Your existing storage options involve expensive storage area networks (SANs) that use a Fibre Channel fabric, though you might also consider iSCSI in instances when performance isn’t critical. While these options can provide flexible storage configurations, they have some of the following drawbacks:</para>
      <list class="bullet">
        <listItem>
          <para>Fibre Channel (and even iSCSI) SANs are quite expensive.</para>
        </listItem>
        <listItem>
          <para>SANs can be complex to set up and maintain.</para>
        </listItem>
      </list>
      <para>As such, the overall problem that you want to solve is:</para>
      <list class="bullet">
        <listItem>
          <para>
            <embeddedLabel>How can you provide resilient and high-performance storage for your Hyper-V hosts while keeping costs down?</embeddedLabel>
          </para>
        </listItem>
      </list>
      <para>
        <legacyBold>Organization goals</legacyBold>
      </para>
      <para>Basically you’re looking for a storage solution that provides the following:</para>
      <list class="bullet">
        <listItem>
          <para>
            <embeddedLabel>Continuous availability</embeddedLabel> - You need to provide remote storage that is continuously available to keep downtime to an absolute minimum.</para>
        </listItem>
        <listItem>
          <para>
            <embeddedLabel>Scalable storage</embeddedLabel> - You need to provide hundreds of terabytes of storage with high levels of throughput to the thousands of virtual machines that you want to host (this solution provides roughly 150-600 TB of capacity for 1,000-8,192 virtual machines with around 75 GB per virtual machine).</para>
        </listItem>
        <listItem>
          <para>
            <embeddedLabel>High performance</embeddedLabel> - You need storage that can provide great performance for each virtual machine and service.</para>
        </listItem>
        <listItem>
          <para>
            <embeddedLabel>Efficient management</embeddedLabel> - You need efficient and powerful management tools that help you set up and manage the entire cloud platform solution, which consists of hundreds of disks, and dozens of server nodes.</para>
        </listItem>
        <listItem>
          <para>
            <embeddedLabel>Low cost</embeddedLabel> - You need to keep storage from consuming your entire budget.</para>
        </listItem>
      </list>
    </content>
  </section>
  <section address="BKMKStrategy">
    <title>What is the recommended planning and design approach for this solution?</title>
    <content>
      <para>This section defines one solution that we recommend for the problem and goals described above. This solution focuses on the storage portion of a cloud platform that consists of the following three parts: </para>
      <list class="bullet">
        <listItem>
          <para>
            <legacyBold>Compute</legacyBold> - Tenant workloads are hosted on a compute cluster running Hyper-V virtual machines.</para>
        </listItem>
        <listItem>
          <para>
            <legacyBold>Storage</legacyBold> - Virtual machines are stored on a high-performance file server cluster.</para>
        </listItem>
        <listItem>
          <para>
            <legacyBold>Management</legacyBold> - The compute and file server clusters are managed by a management cluster.</para>
        </listItem>
      </list>
      <para>The following diagram illustrates the storage portion of this solution:</para>
      <para>
        <legacyBold>Windows Server-based Storage for Virtual Machines Solution Architecture</legacyBold>
      </para>
      <mediaLink>
        <image xlink:href="7a67cf17-203c-4eb5-a394-b8b64e2e060b"/>
      </mediaLink>
      <para/>
      <para>The following table lists the elements that are part of this solution design and describes the reason for the design choice. </para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Solution design element</para>
            </TD>
            <TD>
              <para>
                How it supports this solution</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>Multiple storage enclosures</para>
            </TD>
            <TD>
              <para>Multiple just-a-bunch-of-disks (JBOD) enclosures house low-cost industry standard Serial Attached SCSI (SAS) hard disks (HDDs) and solid state disks (SSDs) without the expense of SAN devices.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>File servers running <token>winblue_server_2</token></para>
            </TD>
            <TD>
              <para>The JBOD enclosures are connected to standard four-node file server clusters running <token>winblue_server_2</token> using inexpensive (non-RAID) SAS controllers.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Clustered storage pools</para>
            </TD>
            <TD>
              <para>All disks in the enclosures are added to clustered storage pools using Storage Spaces, obviating the need to manage individual disks. </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Storage spaces</para>
            </TD>
            <TD>
              <para>Virtual disks called storage spaces are created from free space in the storage pools. These storage spaces provide software-defined resiliency levels—in this solution we use three-way mirrors that provide high performance while preserving data in the event that two disk failures occur.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Storage tiers</para>
            </TD>
            <TD>
              <para>Storage spaces are created with storage tiers that automatically move frequently accessed data to SSD storage and infrequently accessed data to hard disk (HDD) storage, combining the performance of SSDs with the capacity of HDDs.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Failover Clustering</para>
            </TD>
            <TD>
              <para>Failover Clustering is set up on Windows Server file servers so that if one file server fails, the storage pools it’s hosting can fail over to other nodes of the cluster. The compute cluster and management nodes also use Failover Clustering so that virtual machines can fail over to other nodes.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Unified CSV namespace and Scale-Out File Server</para>
            </TD>
            <TD>
              <para>By using cluster shared volumes (CSV) and creating a clustered file server role with the Scale-Out File Server option, all cluster nodes can simultaneously write to the same storage, increasing performance and availability.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Continuously available file shares</para>
            </TD>
            <TD>
              <para>Continuously available file shares hosted on the scale-out file server let you store Hyper-V virtual machine configuration files and virtual hard disks in easy-to-manage, remotely accessible file shares without sacrificing performance or availability.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Hyper-V</para>
            </TD>
            <TD>
              <para>Hyper-V enables you to create and manage a virtualized computing and management environment by using virtualization technology that is built in to Windows Server. </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>System Center Virtual Machine Manager</para>
            </TD>
            <TD>
              <para>You can manage all virtual machines by using System Center Virtual Machine Manager, running on the management cluster.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Windows Server Update Services</para>
            </TD>
            <TD>
              <para>You can use Windows Server Update Services, running on the management cluster in conjunction with Cluster-Aware Updating, Virtual Machine Manager, and optionally System Center Configuration Manager to deploy software updates to all nodes and virtual machines on the management and compute clusters.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>System Center Operations Manager</para>
            </TD>
            <TD>
              <para>You can monitor this solution by using System Center Operations Manager, running on the management cluster.</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>
        <?Comment KC: Later, it would be good to add a bulleted list of planning considerations – just the high-level categories that you detail in your guide. 2014-01-20T16:07:00Z  Id='55?>To<?CommentEnd Id='55'
    ?> design the hardware and software configuration for each cluster in this solution, see the <link xlink:href="3314f967-8a2c-48c6-bfc7-3137cc30a075">Cost-Effective Storage for Cloud Hosting Planning and Design Guide</link>.</para>
    </content>
    <sections>
      <section address="BKMK_Challenges">
        <title>Challenges for this solution</title>
        <content>
          <para>Here are some of the challenges involved with this solution as well as some strategies to address them.</para>
          <list class="bullet">
            <listItem>
              <para>
                <embeddedLabel>Firmware and driver issues </embeddedLabel>
              </para>
              <para>To reduce firmware and driver issues, especially at scale, we recommend purchasing all production hardware from a vendor that tests and supports the hardware as an integrated solution with Storage Spaces. <externalLink><linkText>Microsoft Cloud Platform (CPS) Powered by Dell</linkText><linkUri>http://www.microsoft.com/en-us/server-cloud/products/cloud-platform-system/</linkUri></externalLink> is an example of such a solution. It's also important to follow each vendor's recommendations on the latest recommended driver and firmware versions to use.</para>
              <para>Also run the Validate a Configuration Wizard and resolve every issue prior to setting up each cluster. For more information, see <legacyLink xlink:href="c05d69b4-1c61-4422-8409-4343a839478c">Validate Hardware for a Failover Cluster</legacyLink>.</para>
            </listItem>
            <listItem>
              <para>
                <embeddedLabel>Difficulty completely erasing previous Storage Spaces and Failover Clustering information from JBODs and physical disks</embeddedLabel>
              </para>
              <para>This isn’t usually a problem with new hardware, but if you’re using existing hardware to test the configuration, use the cmdlets in the Storage Windows PowerShell module to completely erase all Storage Spaces and Failover Clustering data from the physical disks and JBODs before setting up the solution. In some cases power cycling the JBODs can help remove persistent reservation info from the devices.</para>
              <alert class="tip">
                <para>See <externalLink><linkText>Completely Clearing an Existing Storage Spaces Configuration</linkText><linkUri>http://gallery.technet.microsoft.com/Completely-Clearing-an-ab745947</linkUri></externalLink> for a script that can help completely erase everything from a Storage Spaces configuration.</para>
              </alert>
            </listItem>
            
            <listItem>
              <para>
                <embeddedLabel>Large scale of solution</embeddedLabel>
              </para>
              <para>This solution requires a significant hardware investment to set up for testing purposes. You can work around this by starting with a smaller solution for testing. For example, you could use a file server cluster with two nodes and two JBODs, a simpler management cluster, and fewer compute nodes. When you’re comfortable with the solution in your lab, you can add nodes and JBODs to the file server cluster, though you’ll have to recreate the storage spaces to ensure that data is stored across all enclosures with enclosure awareness support.</para>
            </listItem>
          </list>
        </content>
      </section>
    </sections>
  </section>
  <section address="BKMKSteps" DoNotNumber="false">
    <title>What are the high-level steps to implement this solution?</title>
    <content>
      <para>You can use the steps in this section to implement the solution. Make sure to verify the correct deployment of each step before proceeding to the next step.</para>
      <list class="ordered">
        <listItem>
          <para>
            <legacyBold>Design your solution and purchase certified hardware</legacyBold>
          </para>
          <para>Use the <externalLink><linkText>Software-Defined Storage Design Considerations Guide</linkText><linkUri>http://technet.microsoft.com/library/mt243829.aspx</linkUri></externalLink> to plan and design your storage solution. You can also use <link xlink:href="3314f967-8a2c-48c6-bfc7-3137cc30a075">Cost-Effective Storage for Cloud Hosting Planning and Design Guide</link> to get an overview of a large-scale design for storage, compute, and management clusters.</para>
        </listItem>
        <listItem>
          <para>
            <legacyBold>Rack and cable all hardware</legacyBold>
          </para>
          <para>Hook up your file server cluster, management cluster, compute cluster, and the network switches that they connect to. Don’t connect this hardware to any external networks yet.</para>
        </listItem>
        <listItem>
          <para>
            <embeddedLabel>Update all firmware</embeddedLabel>
          </para>
          <para>Update the firmware for your JBODs, disks, servers, network switches, and HBAs to the certified versions as you bring hardware online.</para>
        </listItem>
        <listItem>
          <para>
            <legacyBold>Deploy <token>winblue_server_2</token> on the management cluster</legacyBold>
          </para>
          <para>Install <token>winblue_server_2</token> with the Server Core installation option on the management cluster to reduce the amount of software updates that apply to the server (assuming that you’re not using an existing management cluster). Use a laptop plugged into the management network to remotely configure all nodes, or install Windows Server with the GUI installation option.</para>
        </listItem>
        <listItem>
          <para>
            <legacyBold>Install Hyper-V and create virtual machines for AD DS, DNS, and DHCP on the management cluster</legacyBold>
          </para>
          <para>Install the Hyper-V server role and then use Hyper-V Manager or Windows PowerShell to create a virtual machine on one node of the management cluster for AD DS, DNS, and DHCP. This virtual machine isn’t highly available (these services replicate and load-balance without clustering), and you should store the operating system virtual hard disk (.vhdx) file on the local hard disk of one of the nodes. Repeat this two more times on two other nodes so that you have three virtual machines on three separate nodes. You’ll create more virtual machines after setting up Failover Clustering on the management cluster later in the set up procedure.</para>
          <para>For more information, see <legacyLink xlink:href="243b5705-96c9-4ec7-9ec5-c68a22b0d42d">Install Hyper-V and create a virtual machine</legacyLink>.</para>
          <alert class="note">
            <para>After setting up this solution, you can optionally create highly available virtual machines running AD DS, DNS, and DHCP and retire the stand-alone virtual machines created in this step. Doing so can make management more logical as all virtual machines are highly available, and stored on the file server cluster.</para>
          </alert>
        </listItem>
        <listItem>
          <para>
            <legacyBold>Deploy AD DS, DNS, and DHCP</legacyBold>
          </para>
          <para>If you’re installing a new management cluster, install AD DS on each of the virtual machines (three domain controllers) and create a new forest for your server clusters, with Active Directory-integrated DNS zones, and DHCP scopes for the storage network and the management network. </para>
          <para>For more information, see <legacyLink xlink:href="4fff7ac7-b90f-41d0-8c87-9ffe08dc6c01">Install Active Directory Domain Services (Level 100)</legacyLink> and <legacyLink xlink:href="1c1a6be6-1581-471c-a4a9-a654d7f1d88f">Step-by-Step: Configure DHCP for Failover</legacyLink>.</para>
        </listItem>
        <listItem>
          <para>
            <legacyBold>Set up the file server cluster</legacyBold>
          </para>
          <para>Use the following steps to set up the file server cluster:</para>
          <alert class="note">
            <para>
              <token>vmmblue_2</token> can quickly create a scale-out file server from the four bare-metal nodes of your file server cluster. The only problem is that you probably want to store the virtual hard disk files for <token>vmmblue_2</token> on the file server cluster that isn’t yet set up. You can optionally work around this chicken and egg problem by installing <token>vmmblue_2</token> in a non-highly available configuration on the management cluster, use it to set up the file server cluster, and then set up <token>vmmblue_2</token> again in a highly available configuration (stored on the file server cluster).</para>
          </alert>
          <list class="ordered">
            <listItem>
              <para>
                <legacyBold>Install <token>winblue_server_2</token></legacyBold>
              </para>
              <para>Install Windows Server with the Server Core installation option on the nodes of the file server cluster, with the operating system installed on the local hard disk of each node.</para>
            </listItem>
            <listItem>
              <para>(Optional) <legacyBold>Wipe existing Storage Spaces and Failover Cluster configuration data</legacyBold></para>
              <para>If your JBODs and servers were previously used for something else, completely erase all Storage Spaces and Failover Clustering data from the physical disks and JBODs. For a script that can help completely erase everything (and we do mean everything, so be careful!) from a Storage Spaces configuration, see <externalLink><linkText>Completely Clearing an Existing Storage Spaces Configuration</linkText><linkUri>http://gallery.technet.microsoft.com/Completely-Clearing-an-ab745947</linkUri></externalLink>.</para>
            </listItem>
            <listItem>
              <para>
                <legacyBold>Validate physical disks and enclosures</legacyBold>
              </para>
              <para>Check all physical disks to make sure that they’re healthy, show the correct MediaType, and are showing as eligible for pooling. Also confirm that the JBODs are showing enclosure information properly.</para>
              <para>For a script that can validate your physical disks and enclosures and perform some performance and health checks, see <externalLink><linkText>Storage Spaces Physical Disk Validation Script</linkText><linkUri>http://gallery.technet.microsoft.com/scriptcenter/Storage-Spaces-Physical-7ca9f304</linkUri></externalLink>.</para>
            </listItem>
            <listItem>
              <para>
                <legacyBold>Create clustered storage pools</legacyBold>
              </para>
              <para>Validate and optimize the cluster networking configuration, labeling each network (for example, storage network and management network), and then create three clustered storage pools with four SSDs and 16 HDDs from each of the four JBODs, for a total of 80 disks per pool. </para>
              <para>For detailed steps to set up the failover cluster and create storage pools, see <legacyLink xlink:href="7b33931e-7971-49b0-b385-b1e5a90d94fe">Deploy Clustered Storage Spaces</legacyLink>.</para>
            </listItem>
            <listItem>
              <para>
                <legacyBold>Create a Scale-Out File Server</legacyBold>
              </para>
              <para>Next create a clustered file server role with the Scale-Out File Server option.</para>
              <para>For more information, see <externalLink><linkText>Deploy Scale-Out File Server</linkText><linkUri>http://technet.microsoft.com/library/hh831359.aspx</linkUri></externalLink>.</para>
            </listItem>
            <listItem>
              <para>
                <legacyBold>Create the witness disk for the file server cluster</legacyBold>
              </para>
              <para>Use Server Manager or the <system>New-VirtualDisk</system> cmdlet to create a 3 GB two-way mirror space without storage tiers for use as the witness disk for the file server cluster, and then configure the cluster quorum. </para>
              <para>For more information, see <legacyLink xlink:href="e5cef0e4-cf8e-48be-a5bc-2182d416fab1#BKMK_steps_changing">Configure the cluster quorum</legacyLink>.</para>
            </listItem>
            <listItem>
              <para>
                <legacyBold>Create storage tiers, storage spaces, partitions, volumes, and CSVs</legacyBold>
              </para>
              <para>Create your storage spaces according to your design, and then create one partition, one volume, and one CSV per storage <?Comment JG: Probably by using New-Volume 2014-01-20T16:07:00Z  Id='56?>space<?CommentEnd Id='56'
    ?>.</para>
            </listItem>
            <listItem>
              <para>
                <legacyBold>Create continuously available file shares for the management cluster virtual machines</legacyBold>
              </para>
              <para>Create one continuously available SMB file share per CSV used by the virtual machines on the management cluster, and grant full control permissions to the computer accounts of each <?Comment JG: I think because the Hyper-V failover cluster hasn’t been set up yet. 2014-01-20T16:07:00Z  Id='57?>node of the management cluster<?CommentEnd Id='57'
    ?>, the SYSTEM account, and the Domain Administrators group.</para>
              <para>For more information, see <legacyLink xlink:href="5a169fa2-f5c8-4c0d-a122-79ecdbdebc98#BKMK_Step3">Step 3: Create an SMB file share</legacyLink></para>
            </listItem>
          </list>
        </listItem>
        <listItem>
          <para>
            <legacyBold>Set up the management cluster and the rest of the management virtual machines</legacyBold>
          </para>
          <para>Use the following steps to set up Failover Clustering on the management cluster and create highly available virtual machines for the rest of your management and infrastructure services (you already set up AD DS, DNS, and DHCP in stand-alone virtual machines). Most virtual machines are highly available virtual machines, but for some services you might want to use guest clustering to create a cluster between virtual machines. </para>
          <list class="ordered">
            <listItem>
              <para>
                <legacyBold>Install Failover Clustering and set up the Hyper-V cluster</legacyBold>
              </para>
              <para>Use the following topic to create the management cluster and configure Hyper-V to support highly available virtual machines <legacyLink xlink:href="636c67f7-de15-4e23-ad6a-119a8d43d819">Deploy a Hyper-V Cluster</legacyLink>.</para>
            </listItem>
            <listItem>
              <para>
                <embeddedLabel>Set up Cluster-Aware Updating</embeddedLabel>
              </para>
              <para>Set up Cluster-Aware Updating to make it easy to update the cluster while minimizing or eliminating downtime. For more information, see <legacyLink xlink:href="a8e6dfbb-9d98-4130-86ac-9f6f00241e02">Cluster-Aware Updating Overview</legacyLink>.</para>
            </listItem>
            <listItem>
              <para>
                <legacyBold>Deploy SQL Server</legacyBold>
              </para>
              <para>Deploy SQL Server to support <token>vmmblue_2</token>. For more information, see the following topics:</para>
              <list class="bullet">
                <listItem>
                  <para>
                    <externalLink>
                      <linkText>Always On Failover Cluster Instances (SQL Server)</linkText>
                      <linkUri>http://technet.microsoft.com/library/ms189134.aspx</linkUri>
                    </externalLink>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <externalLink>
                      <linkText>Install SQL Server with SMB fileshare as a storage option</linkText>
                      <linkUri>http://technet.microsoft.com/library/hh759341.aspx</linkUri>
                    </externalLink>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <externalLink>
                      <linkText>Create a New SQL Server Failover Cluster (Setup)</linkText>
                      <linkUri>http://technet.microsoft.com/library/ms179530.aspx</linkUri>
                    </externalLink>
                  </para>
                </listItem>
              </list>
            </listItem>
            <listItem>
              <para>
                <legacyBold>Deploy <token>vmmblue_2</token></legacyBold>
              </para>
              <para>Deploy <token>vmmblue_2</token> on a guest cluster. <token>vmmblue_2</token> is used to deploy and manage the compute nodes and other network components for this solution.</para>
              <para>For more information see the following topics:</para>
              <list class="bullet">
                <listItem>
                  <para>
                    <externalLink>
                      <linkText>Installing a Highly Available VMM Management Server</linkText>
                      <linkUri>http://technet.microsoft.com/library/gg610675.aspx</linkUri>
                    </externalLink>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <legacyLink xlink:href="d25a2cb3-0932-47c9-b2e4-0e0c7ae9dd6a">Deploy a Guest Cluster Using a Shared Virtual Hard Disk</legacyLink>
                  </para>
                </listItem>
              </list>
            </listItem>
            <listItem>
              <para>
                <legacyBold>Deploy Windows Server Update Services</legacyBold>
              </para>
              <para>Use <token>vmmblue_2</token> in conjunction with Windows Server Update Services to update all virtual machines in this solution. </para>
              <para>For more information, see <externalLink><linkText>Managing Fabric Updates in VMM</linkText><linkUri>http://technet.microsoft.com/library/gg675084.aspx</linkUri></externalLink> (or <legacyLink xlink:href="5ad27d64-0749-4b84-a8c1-21ffe5bccd3f">Deploy Windows Server Update Services in Your Organization</legacyLink> if you’re not using <token>vmmblue_2</token>).</para>
            </listItem>
          </list>
        </listItem>
        <listItem>
          <para>
            <legacyBold>Deploy the compute nodes and clusters</legacyBold>
          </para>
          <para>Once your infrastructure is set up, use <token>vmmblue_2</token> or Windows PowerShell to deploy the compute nodes from bare-metal, and set them up in a failover cluster, with <token>vmmblue_2</token> and Windows Server Update Services providing updates to the cluster nodes.</para>
          <para>For more information, see <externalLink><linkText>Administering System Center 2012 - Virtual Machine Manager</linkText><linkUri>http://technet.microsoft.com/library/gg610615.aspx</linkUri></externalLink>.</para>
        </listItem>
        <listItem>
          <para>
            <legacyBold>Set up your tenant networking </legacyBold>
          </para>
          <para>To set up your tenant networking, see <link xlink:href="08bcdb9d-c03a-40b3-8a78-b472d1a35161">Hybrid Cloud Multi-Tenant Networking Solution Guide</link>.</para>
        </listItem>
        <listItem>
          <para>
            <legacyBold>Deploy your tenant virtual machines</legacyBold>
          </para>
          <para>After your tenant networking is set up, use <token>vmmblue_2</token> or Windows PowerShell to deploy your tenant virtual machines.</para>
        </listItem>
      </list>
    </content>
  </section>
  <section DoNotNumber="false">
    <title>See also</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Content type</para>
            </TD>
            <TD>
              <para>References</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>Product evaluation/Getting started</para>
            </TD>
            <TD>
              <list class="bullet">
                <listItem>
                  <para>
                    <externalLink>
                      <linkText>Achieving Over 1-Million IOPS from Hyper-V VMs in a Scale-Out File Server Cluster Using Windows Server 2012 R2</linkText>
                      <linkUri>http://www.microsoft.com/download/details.aspx?id=42960</linkUri>
                    </externalLink>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <externalLink>
                      <linkText>Enterprise Strategy Group Lab Validation Report: Microsoft Windows Server 2012 Storage and Networking Analysis.</linkText>
                      <linkUri>http://download.microsoft.com/download/8/0/F/80FCCBEF-BC4D-4B84-950B-07FBE31022B4/ESG-Lab-Validation-Windows-Server-Storage.pdf</linkUri>
                    </externalLink>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <externalLink>
                      <linkText>Test Lab Guide: Windows Server 2012 R2 Hyper-V Network Virtualization with System Center 2012 R2 VMM</linkText>
                      <linkUri>http://www.microsoft.com/download/details.aspx?id=39284</linkUri>
                    </externalLink>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <externalLink>
                      <linkText>Windows Server 2012 R2 Private Cloud Virtualization and Storage Poster and Mini-Posters</linkText>
                      <linkUri>http://www.microsoft.com/download/details.aspx?id=41665</linkUri>
                    </externalLink>
                  </para>
                </listItem>
              <listItem><para><externalLink><linkText>Microsoft Cloud Platform System Storage Performance</linkText><linkUri>https://www.microsoft.com/en-us/download/details.aspx?id=45917&amp;WT.mc_id=Blog_WS_Announce_TTD</linkUri></externalLink></para></listItem></list>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Planning</para>
            </TD>
            <TD>
              <list class="bullet">
                <listItem>
                  <para>
                    
                  <externalLink><linkText>Software-Defined Storage Design Considerations Guide</linkText><linkUri>http://technet.microsoft.com/library/mt243829.aspx</linkUri></externalLink></para>
                </listItem><listItem><para><externalLink><linkText>Software-Defined Storage Design Calculator</linkText><linkUri>http://aka.ms/sdscalc</linkUri></externalLink></para></listItem>
                <listItem>
                  <para>
                    <externalLink>
                      <linkText>Storage Spaces - Designing for Performance</linkText>
                      <linkUri>http://social.technet.microsoft.com/wiki/contents/articles/15200.storage-spaces-designing-for-performance.aspx</linkUri>
                    </externalLink>
                  </para>
                </listItem>
              </list>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Deployment</para>
            </TD>
            <TD>
              <list class="bullet">
                <listItem>
                  <para>
                    <externalLink>
                      <linkText>Windows Server 2012 IaaS Build Tables: Step-by-Step with PowerShell Examples</linkText>
                      <linkUri>http://gallery.technet.microsoft.com/Windows-Server-2012-IaaS-e4533522</linkUri>
                    </externalLink>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <legacyLink xlink:href="d266e62d-8a95-4c03-9276-9aa6ac0c0474">Building Your Cloud Infrastructure: Converged Data Center with File Server Storage</legacyLink>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <legacyLink xlink:href="a8e6dfbb-9d98-4130-86ac-9f6f00241e02">Cluster-Aware Updating Overview</legacyLink>
                  </para>
                </listItem>
              </list>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Community resources</para>
            </TD>
            <TD>
              <list class="bullet">
                <listItem>
                  <para>
                    <externalLink>
                      <linkText>The File Services and Storage TechNet Forum</linkText>
                      <linkUri>http://social.technet.microsoft.com/forums/en-US/winserverfiles/threads/</linkUri>
                    </externalLink>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <externalLink>
                      <linkText>Hyper-V in the Windows Server forum</linkText>
                      <linkUri>http://social.technet.microsoft.com/Forums/en-US/winserverhyperv/threads</linkUri>
                    </externalLink>
                  </para>
                </listItem>
              </list>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Related solutions</para>
            </TD>
            <TD>
              <list class="bullet">
                <listItem>
                  <para>
                    <link xlink:href="08bcdb9d-c03a-40b3-8a78-b472d1a35161">Hybrid Cloud Multi-Tenant Networking Solution Guide</link>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <externalLink>
                      <linkText>Windows Azure Pack for Windows Server</linkText>
                      <linkUri>http://technet.microsoft.com/library/dn296435.aspx</linkUri>
                    </externalLink>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <legacyLink xlink:href="d266e62d-8a95-4c03-9276-9aa6ac0c0474">Building Your Cloud Infrastructure: Converged Data Center with File Server Storage</legacyLink>
                  </para>
                </listItem>
              </list>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Related technologies</para>
            </TD>
            <TD>
              <list class="bullet">
                <listItem>
                  <para>
                    <legacyLink xlink:href="4cb00829-8d05-4499-8adc-7506e159f857">File and Storage Services Overview</legacyLink>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <externalLink>
                      <linkText>System Center Virtual Machine Manager</linkText>
                      <linkUri>http://technet.microsoft.com/library/gg610610.aspx</linkUri>
                    </externalLink>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <legacyLink xlink:href="6eeffe4f-3558-495b-bcea-c640fe4d6c49">Failover Clustering Overview</legacyLink>
                  </para>
                </listItem>
              </list>
            </TD>
          </tr>
        </tbody>
      </table>
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
          <tr><TD><para>July 15th, 2015</para></TD><TD><list class="bullet"><listItem><para>Added links to the newly released <externalLink><linkText>Software-Defined Storage Design Considerations Guide</linkText><linkUri>http://technet.microsoft.com/library/mt243829.aspx</linkUri></externalLink> and updated the guidance on avoiding compatibility issues.</para></listItem></list></TD></tr><tr>
            <TD>
              <para>February 7th, 2014</para>
            </TD>
            <TD>
              <list class="bullet">
                <listItem>
                  <para>Added a Tip in the <link xlink:href="e70fcb94-0576-4582-a1e0-8c41f8d745cc#BKMK_Challenges">Challenges for this solution</link> section that links to a script that can clean out existing Storage Spaces and Failover Clustering configuration data.</para>
                </listItem>
                <listItem>
                  <para>In the <link xlink:href="e70fcb94-0576-4582-a1e0-8c41f8d745cc#BKMKSteps">What are the high-level steps to implement this solution?</link> section, added steps to optionally clean out existing Storage Spaces and Failover Cluster configuration data and to validate physical disks prior to adding them to the storage pools.</para>
                </listItem>
                <listItem>
                  <para>Updated art</para>
                </listItem>
              </list>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>January 22nd, 2014</para>
            </TD>
            <TD>
              <list class="bullet">
                <listItem>
                  <para>Preliminary publication</para>
                </listItem>
              </list>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics/>
</developerConceptualDocument>
