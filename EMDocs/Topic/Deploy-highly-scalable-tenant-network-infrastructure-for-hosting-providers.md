---
title: Deploy highly scalable tenant network infrastructure for hosting providers
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 08bcdb9d-c03a-40b3-8a78-b472d1a35161
---
# Deploy highly scalable tenant network infrastructure for hosting providers
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>
      <legacyBold>How can this guide help you?</legacyBold>  As a medium-sized hosting provider you can use this solution guide to understand the solution design and implementation steps we recommend to deploy a scalable network infrastructure to support infrastructure as service (IaaS). Provisioning tenant networks can be expensive to operate and complex to manage.</para>
    <para>This guide helps you deploy a prescriptive and tested IaaS virtual network infrastructure solution that is cost-effective, flexible, scalable, and easy to manage. In addition, it provides your tenants with a simpler, cost-effective way to connect their datacenters to yours to deploy their hybrid cloud solutions.</para>
    <alert class="tip">
      <para>If you aren’t familiar with network virtualization concepts, review <legacyLink xlink:href="bf1dba9d-1960-4dd2-a5e2-99466a02044b">Hyper-V Network Virtualization Overview [w8]</legacyLink> and <legacyLink xlink:href="405a1b66-c9ba-49fa-9200-cd1364e92ab1">Hyper-V Network Virtualization technical details</legacyLink>.</para>
      <para>If you aren’t familiar with the network virtualization concepts in <token>vmmblue_1</token> (VMM), we strongly recommend that you set up and run a test lab using the following test lab guide before you do any planning and design: <externalLink><linkText>Test Lab Guide: Windows Server 2012 R2 Hyper-V Network Virtualization with System Center 2012 R2 VMM</linkText><linkUri>http://www.microsoft.com/download/details.aspx?id=39284</linkUri></externalLink>.</para>
      <para>The test lab guide will help you understand <token>vmmblue_2</token> concepts, and will help make it easier to plan, design, and deploy this solution.</para>
      <para>Also review the VMM concepts presented in <externalLink><linkText>Microsoft System Center: Building a Virtualized Network Solution</linkText><linkUri>http://blogs.msdn.com/b/microsoft_press/archive/2014/02/18/free-ebook-microsoft-system-center-building-a-virtualized-network-solution.aspx</linkUri></externalLink> for more information about planning and design considerations in a VMM-based solution.</para>
    </alert>
    <para>
      <legacyBold>In this solution guide:</legacyBold>
    </para>
    <list class="bullet">
      <listItem>
        <para>
          <link xlink:href="08bcdb9d-c03a-40b3-8a78-b472d1a35161#BKMKGoals">Scenario, problem statement, and goals</link>
        </para>
      </listItem>
      <listItem>
        <para>
          <link xlink:href="08bcdb9d-c03a-40b3-8a78-b472d1a35161#BKMKStrategy">What is the recommended design for this solution?</link>
        </para>
      </listItem>
      <listItem>
        <para>
          <link xlink:href="08bcdb9d-c03a-40b3-8a78-b472d1a35161#BKMKWhy">Why are we recommending this design?</link>
        </para>
      </listItem>
      <listItem>
        <para>
          <link xlink:href="08bcdb9d-c03a-40b3-8a78-b472d1a35161#BKMKSteps">What are the steps to implement this solution?</link>
        </para>
      </listItem>
      <listItem>
        <para>
          <link xlink:href="08bcdb9d-c03a-40b3-8a78-b472d1a35161#BKMKOptions">Optional configurations</link>
        </para>
      </listItem>
    </list>
    <para>The following diagram illustrates the problem that this guide addresses. An individual gateway must be provisioned for each tenant, which requires significant configuration and VLANs only scale up to about 1,000 tenants. </para>
    <para>
      <legacyBold>Tenants connecting to a hosting provider</legacyBold>
    </para>
    <mediaLink>
      <image xlink:href="0cbcf689-78f6-40a6-88a8-f3adea43579c" />
    </mediaLink>
  </introduction>
  <section address="BKMKGoals">
    <title>Scenario, problem statement, and goals</title>
    <content>
      <para>This section describes the scenario, problem, and goals for an example organization.</para>
      <para>
        <legacyBold>Scenario</legacyBold>
      </para>
      <para>A medium-sized hosting provider offers IaaS to its customers. They recently started offering a virtual network service, based on customer demand. </para>
      <para>The Marketing Department within the hosting provider has been so successful marketing the virtual networking service that the customer demand for it is increasing fast.</para>
      <para>
        <legacyBold>Problem statement</legacyBold>
      </para>
      <para>The hosting provider’s current virtual network service offering doesn’t scale well, and is inefficient and expensive to operate. For example:</para>
      <list class="bullet">
        <listItem>
          <para>Their current design requires two gateways for every tenant (for redundancy), and each pair of gateways requires a public IP address. As the number of tenants has increased, the number of gateways required to support them has increased linearly. This is difficult for the hosting provider to manage. Adding two gateways per tenant is not a cost-effective solution for them.</para>
        </listItem>
        <listItem>
          <para>If a tenant needs to connect multiple sites, then each tenant site also requires a separate gateway.</para>
        </listItem>
        <listItem>
          <para>They’re not currently using an industry standard routing <?Comment A: I changed this a bit, but I wasn't sure if you were saying they're not using one, or one doesn't exist. If one doesn't exist, change accordingly. 2014-05-14T13:33:00Z  Id='0?>protocol<?CommentEnd Id='0'
    ?>, which requires an administrator to manually administer network routes. This is inefficient and subject to configuration errors. </para>
        </listItem>
        <listItem>
          <para>The current design utilizes VLANs for network isolation.  Their network switches only support 1,000 VLANs, which limits their ability to scale beyond that.  Moving a tenant virtual machine to a different host located on a different physical location often requires an IP address change and switch reconfiguration. This issue makes moving tenant virtual machines very difficult and provides them little flexibility in their datacenter infrastructure.</para>
        </listItem>
      </list>
      <para>
        <legacyBold>Organization goals</legacyBold>
      </para>
      <para>The hosting provider needs high availability, cost efficiency, and simplified management to deliver better and cost competitive services to meet their increased customer demand. They want to implement a new solution with the following attributes:</para>
      <list class="bullet">
        <listItem>
          <para>The ability to deploy gateways that can connect multiple tenant networks and multiple sites per tenant at the same time.</para>
        </listItem>
        <listItem>
          <para>The ability to use an industry standard routing protocol, and enable a scalable virtual network isolation protocol that isn’t limited by current VLAN technologies.</para>
        </listItem>
        <listItem>
          <para>The ability to provide isolated tenant networks using a technology that scales well as the number of tenants and their workloads increase.</para>
        </listItem>
        <listItem>
          <para>A manageable virtual network design that has an easy-to-use management interface that allows them to manage their virtual networks, IP address spaces, and gateways all in one location. This makes it easier and more efficient for them to manage many tenants at a time.</para>
        </listItem>
        <listItem>
          <para>The ability to provide a common self-service portal for tenants, which allows them to efficiently place their computing resources where they best meet their business needs.</para>
        </listItem>
        <listItem>
          <para>The ability to provide easy-to-follow guidance for their customers so that they can easily connect their on-premises network to the hosting provider’s through a secure site-to-site virtual private network (VPN). This guidance will include router configuration guidance that details required protocols, settings, and end-point addresses.</para>
        </listItem>
      </list>
    </content>
  </section>
  <section address="BKMKStrategy">
    <title>What is the recommended design for this solution?</title>
    <content>
      <para />
      <para>The following diagram shows the recommended design for this solution, which connects each tenant’s network to the hosting provider’s multi-tenant gateway using a single site-to-site VPN tunnel. This enables the hosting provider to support approximately 100 tenants on a single gateway cluster, which decreases both the management complexity and cost. Each tenant must configure their own gateway to connect to the hosting provider gateway. The gateway then routes each tenant’s network data and uses the “Network Virtualization using Generic Routing Encapsulation” (NVGRE) protocol for network virtualization.</para>
      <para>
        <legacyBold>Multi-tenant networking solution design</legacyBold>
      </para>
      <mediaLink>
        <image xlink:href="956c5ab9-44b0-4fdf-9b21-d9a015d398e5" />
      </mediaLink>
      <para />
      <para />
      <para>The following table lists the elements that are part of this solution design and describes the reason for the design choice.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Solution design element</para>
            </TD>
            <TD>
              <para>Why is it included in this solution?</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>
                <token>winblue_server_2</token>
              </para>
            </TD>
            <TD>
              <para>Provides the operating system base for this solution. We recommend using the Server Core installation option to reduce security attack exposure and to decrease software update frequency.</para>
            </TD>
            <TD>
              <para />
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <token>winblue_server_2</token> Gateway</para>
            </TD>
            <TD>
              <para>Is integrated with <token>vmmblue_2</token> to support simultaneous, multi-tenant site-to-site VPN connections and network virtualization using NVGRE. For an overview of this technology, see <legacyLink xlink:href="e39e8b8c-a23c-4dbd-b895-d1e3f2885e9e">Windows Server Gateway</legacyLink>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Microsoft SQL Server 2012</para>
            </TD>
            <TD>
              <para>Provides database services for <token>vmmblue_2</token>and <token>katal_2</token>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <token>vmmblue_1</token>
              </para>
            </TD>
            <TD>
              <para>Manages virtual networks (using NVGRE for network isolation), fabric management, and IP addressing. For an overview of this product, see <externalLink><linkText>Configuring Networking in VMM Overview</linkText><linkUri>http://technet.microsoft.com/library/gg610596.aspx</linkUri></externalLink>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Windows Server Failover Clustering</para>
            </TD>
            <TD>
              <para>All the physical hosts are configured as failover clusters for high availability, as well as many of virtual machine guests that host management and infrastructure workloads.</para>
              <para>The site-to-site VPN gateway can be deployed in 1+1 configuration for high availability. For more information about Failover Clustering, see <legacyLink xlink:href="6eeffe4f-3558-495b-bcea-c640fe4d6c49">Failover Clustering Overview [Role/Tech Overview]</legacyLink>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Scale-out File Server</para>
            </TD>
            <TD>
              <para>Provides file shares for server application data with reliability, availability, manageability, and high performance. This solution uses two scale-out file servers: one for the domain that hosts the management servers and one for the domain that hosts the gateway servers. These two domains have no trust relationship. The scale-out file server for the gateway domain is implemented as a virtual machine guest cluster. The scale-out file server for the gateway domain is needed because you will not be able to access a scale-out file server from an untrusted domain.</para>
              <para>For an overview of this feature, see <legacyLink xlink:href="0a6029b2-9390-414f-b486-98d31d033ff0">Scale-Out File Server for Application Data Overview [ScaleOut_FS]</legacyLink>.</para>
              <para>For a more in-depth discussion of possible storage solutions, see <link xlink:href="e70fcb94-0576-4582-a1e0-8c41f8d745cc">Provide cost-effective storage for Hyper-V workloads by using Windows Server</link>.</para>
              <para />
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Site-to-site VPN</para>
            </TD>
            <TD>
              <para>Provides a way to connect a tenant site to the hosting provider site. This connection method is cost-effective and VPN software is included with Remote Access in <token>winblue_server_2</token>. (Remote Access brings together Routing and Remote Access service (RRAS) and Direct Access). Also, VPN software and/or hardware is available from multiple suppliers.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <token>katal_2</token>
              </para>
            </TD>
            <TD>
              <para>Provides a self-service portal for tenants to manage their own virtual networks. <token>katal_2</token> provides a common self-service experience, a common set of management APIs, and an identical website and virtual machine hosting experience. Tenants can take advantage of the common interfaces, such as Service Provider Foundation) which frees them to move their workloads where it makes the most sense for their business or for their changing requirements. Though <token>katal_2</token> is used for the self-service portal in this solution, you can use a different self-service portal if you choose.</para>
              <para>For an overview of this product, see <externalLink><linkText>Windows Azure Pack for Windows Server</linkText><linkUri>http://technet.microsoft.com/library/dn296435.aspx</linkUri></externalLink></para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>System Center 2012 R2 Orchestrator</para>
            </TD>
            <TD>
              <para>Provides Service Provider Foundation (SPF), which exposes an extensible OData web service that interacts with VMM. This enables service providers to design and implement multi-tenant self-service portals that integrate IaaS capabilities that are available on System Center 2012 R2.</para>
            </TD>
            <TD>
              <para />
            </TD>
          </tr>
        </tbody>
      </table>
      <para>
        <token>winblue_server_2</token> together with <token>vmmblue_1</token> (VMM) give hosting providers a multi-tenant gateway solution that supports multiple host-to-host VPN tenant connections, Internet access for tenant virtual machines by using a gateway NAT feature, and forwarding gateway capabilities for private cloud implementations. Hyper-V Network Virtualization provides tenant virtual network isolation with <externalLink><linkText>NVGRE</linkText><linkUri>http://tools.ietf.org/html/draft-sridharan-virtualization-nvgre-00</linkUri></externalLink>, which allows tenants to bring their own address space and allows hosting providers better scalability than is possible using VLANs for isolation.</para>
      <para>The components of the design are separated onto separate servers because they each have unique scaling, manageability, and security requirements.</para>
      <para>For more information about the advantages of HNV and Windows Server Gateway, see:</para>
      <list class="bullet">
        <listItem>
          <para>
            <legacyLink xlink:href="bf1dba9d-1960-4dd2-a5e2-99466a02044b">Hyper-V Network Virtualization Overview [w8]</legacyLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="e39e8b8c-a23c-4dbd-b895-d1e3f2885e9e">Windows Server Gateway</legacyLink>
          </para>
        </listItem>
      </list>
      <para>VMM offers a user interface to manage the gateways, virtual networks, virtual machines and other fabric items.</para>
      <para>When planning this solution, you need to consider the following:</para>
      <list class="bullet">
        <listItem>
          <para>High availability design for the servers running Hyper-V, guest virtual machines, SQL server, gateways, VMM, and other services</para>
          <para>You’ll want to ensure that your design is fault tolerant and is capable of supporting your stated availability terms.</para>
        </listItem>
        <listItem>
          <para>Tenant virtual machine Internet access requirements</para>
          <para>Consider whether or not your tenants want their virtual machines to have Internet access. If so, you will need to configure the NAT feature when you deploy the gateway.</para>
        </listItem>
        <listItem>
          <para>Infrastructure physical hardware capacity and throughput</para>
          <para>You’ll need to ensure that your physical network has the capacity to scale out as your IaaS offering expands.</para>
        </listItem>
        <listItem>
          <para>Site-to-site connection throughput</para>
          <para>You’ll need to investigate the throughput you can provide your tenants and whether site-to-site VPN connections will be sufficient. </para>
        </listItem>
        <listItem>
          <para>Network isolation technologies</para>
          <para>This solution uses NVGRE for tenant network isolation. You’ll want to investigate if you have or can obtain hardware that can optimize this this protocol. For example, network interface cards, switches, and so on. </para>
        </listItem>
        <listItem>
          <para>Authentication mechanisms</para>
          <para>This solution uses two Active Directory domains for authentication; one for the infrastructure servers and one for the gateway cluster and scale-out file server for the gateway. If you don’t have an Active Directory domain available for the infrastructure, you’ll need to prepare a domain controller before you start deployment. </para>
        </listItem>
        <listItem>
          <para>IP addressing</para>
          <para>You’ll need to plan for the IP address spaces used by this solution.</para>
        </listItem>
      </list>
      <alert class="important">
        <para>If you use jumbo frames in you network environment, you may need to plan for some configuration adjustments before you deploy. For more information, see <externalLink><linkText>Windows Server 2012 R2 Network Virtualization (NVGRE) MTU reduction</linkText><linkUri>http://social.technet.microsoft.com/wiki/contents/articles/23833.windows-server-2012-r2-network-virtualization-nvgre-mtu-reduction.aspx</linkUri></externalLink>.</para>
      </alert>
      <para>
        <embeddedLabel>Determine your tenant requirements</embeddedLabel>
      </para>
      <para>To help with capacity planning, you need to determine your tenant requirements. These requirements will then impact the resources that you need to have available for your tenant workloads. For example, you might need more Hyper-V hosts with more RAM and storage, or you might need faster LAN and WAN infrastructure to support the network traffic that your tenant workloads generate.</para>
      <para>Use the following questions to help you plan for your tenant requirements.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Design consideration</para>
            </TD>
            <TD>
              <para>Design effect</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>How many tenants do you expect to host, and how fast do you expect that number to grow?</para>
            </TD>
            <TD>
              <para>Determines how many Hyper-V hosts you’ll need to support your tenant workloads.</para>
              <para>Using Hyper-V Resource Metering may help you track historical data on the use of virtual machines and gain insight into the resource use of the specific servers. For more information, see <externalLink><linkText>Introduction to Resource Metering</linkText><linkUri>http://blogs.technet.com/b/virtualization/archive/2012/08/16/introduction-to-resource-metering.aspx</linkUri></externalLink> on the Microsoft Virtualization Blog.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>What kind of workloads do you expect your tenants to move to your network? </para>
            </TD>
            <TD>
              <para>Can determine the amount of RAM, storage, and network throughput (LAN and WAN) that you make available to your tenants.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>What is your failover agreement with your tenants?</para>
            </TD>
            <TD>
              <para>Affects your cluster configuration and other failover technologies that you deploy.</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>For more information about physical compute planning considerations, see section “3.1.6 Physical compute resource: hypervisor” in the Design options guide in <externalLink><linkText>Cloud Infrastructure Solution for Enterprise IT</linkText><linkUri>http://www.microsoft.com/download/details.aspx?id=36795</linkUri></externalLink>.</para>
      <para>
        <embeddedLabel>Determine your failover cluster strategy</embeddedLabel>
      </para>
      <para>Plan your failover cluster strategy based on your tenant requirements and your own risk tolerance. For example, the minimum we recommend is to deploy the management, compute, and gateway hosts as two-node clusters. You can choose to add more nodes to your clusters, and you can guest cluster the virtual machines running SQL, <token>vmmblue_2</token>, <token>katal_2</token>, and so on. </para>
      <para>For this solution, you configure the scale-out file servers, compute Hyper-V hosts, management Hyper-V hosts, and gateway Hyper-V hosts as failover clusters. You also configure the SQL, <token>vmmblue_2</token>, and gateway guest virtual machines as failover clusters. This configuration provides protection from potential physical computer and virtual machine failure.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Design consideration</para>
            </TD>
            <TD>
              <para>Design effect</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>What is your risk tolerance for unavailability of applications and services?</para>
            </TD>
            <TD>
              <para>Add nodes to your failover clusters to increase the availability of applications and services.</para>
            </TD>
          </tr>
          <tr>
            <TD />
            <TD />
          </tr>
          <tr>
            <TD />
            <TD />
          </tr>
        </tbody>
      </table>
      <para>
        <embeddedLabel>Determine your SQL high availability strategy</embeddedLabel>
      </para>
      <para>You’ll need to choose a SQL option for high availability for this solution. SQL Server 2012 has several options:</para>
      <list class="bullet">
        <listItem>
          <para>
            <legacyBold>AlwaysOn Failover Cluster Instances</legacyBold>
          </para>
          <para>This option provides local high availability through redundancy at the server-instance level—a failover cluster instance.</para>
        </listItem>
        <listItem>
          <para>
            <legacyBold>AlwaysOn Availability Groups</legacyBold>
          </para>
          <para>This option enables you to maximize availability for one or more user databases.</para>
        </listItem>
      </list>
      <para>For more information see <externalLink><linkText>Overview of SQL Server High-Availability Solutions</linkText><linkUri>http://technet.microsoft.com/library/ms190202.aspx</linkUri></externalLink>.</para>
      <para>For the SQL high availability option for this solution, we recommend AlwaysOn Failover Cluster Instances. With this design, all the cluster nodes are located in the same network, and shared storage is available, which makes it possible to deploy a more reliable and stable failover cluster instance. If shared storage is not available and your nodes span different networks, AlwaysOn Availability Groups might be a better solution for you.</para>
      <para>
        <embeddedLabel>Determine your gateway requirements</embeddedLabel>
      </para>
      <para>You need to plan how many gateway guest clusters are required. The number you need to deploy depends on the number of tenants that you need to support. The hardware requirements for your gateway Hyper-V hosts also depend on the number tenants that you need to support and the tenant workload requirements.</para>
      <para>For Windows Server Gateway configuration recommendations, see <legacyLink xlink:href="f8ba42a9-8afa-440e-9244-3f12406309a1">Windows Server Gateway Hardware and Configuration Requirements</legacyLink>.</para>
      <?Comment VEH: source: Charley Wen 2014-06-19T10:37:00Z  Id='1?>
      <para>For capacity planning purposes, we recommend one gateway guest cluster per 100 tenants.<?CommentEnd Id='1'
    ?></para>
      <para>The design for this solution is for tenants to connect to the gateway through a site-to-site VPN. Therefore, we recommend deploying a Windows Server gateway using a VPN. You can configure a two-node Hyper-V host failover cluster with a two-node guest failover cluster using predefined service templates available on the Microsoft Download Center (for more information, see <externalLink><linkText>How to Use a Server Running Windows Server 2012 R2 as a Gateway with VMM</linkText><linkUri>http://go.microsoft.com/fwlink/p/?LinkId=329037</linkUri></externalLink>).</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Design consideration</para>
            </TD>
            <TD>
              <para>Design effect</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>How will your tenants connect to your network?</para>
            </TD>
            <TD>
              <list class="bullet">
                <listItem>
                  <para>If tenants connect through a site-to-site VPN, you can use Windows Server Gateway as your VPN termination and gateway to the virtual networks.</para>
                  <para>This is the configuration that is covered by this planning and design guide. </para>
                </listItem>
                <listItem>
                  <para>If you use a non-Microsoft VPN device to terminate the VPN, you can use Windows Server Gateway as a forwarding gateway to the tenant virtual networks.</para>
                </listItem>
                <listItem>
                  <para>If a tenant connects to your service provider network through a packet-switched network, you can use Windows Server Gateway as a forwarding gateway to connect them to their virtual networks.</para>
                </listItem>
              </list>
              <alert class="important">
                <para>You must deploy a separate forwarding gateway for each tenant that requires a forwarding gateway to connect to their virtual network.</para>
              </alert>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>
        <embeddedLabel>Plan your network infrastructure</embeddedLabel>
      </para>
      <para>For this solution, you use <token>vmmblue_2</token> to define logical networks, <?Comment VEH: A VMM element 2014-06-19T10:40:00Z  Id='2?>VM networks<?CommentEnd Id='2'
    ?>, port profiles, logical switches, and gateways to organize and simplify network assignments. Before you create these objects, you need to have your logical and physical network infrastructure plan in place.</para>
      <para>In this step, we provide planning examples to help you create your network infrastructure plan.</para>
      <para>The diagram shows the networking design that we recommend for each of the physical nodes in the management, compute, and gateway clusters.</para>
      <para>
        <legacyBold>Networking design for cluster nodes</legacyBold>
      </para>
      <mediaLink>
        <image xlink:href="2333ca64-d59d-4091-b74f-ebd49870432a" />
      </mediaLink>
      <para />
      <para>You need to plan for several subnet and VLANs for the different traffic that is generated, such as management/infrastructure, network virtualization, external (outward bound), clustering, storage, and live migration. You can use VLANs to isolate the network traffic at the switch.</para>
      <para>For example, this design recommends the networks listed in the following table. Your exact line speeds, addresses, VLANs, and so on may differ based on your particular environment.</para>
      <para>
        <legacyBold>Subnet/VLAN plan</legacyBold>
      </para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Line speed (Gb/S)</para>
            </TD>
            <TD>
              <para>Purpose</para>
            </TD>
            <TD>
              <para>Address</para>
            </TD>
            <TD>
              <para>VLAN</para>
            </TD>
            <TD>
              <para>Comments</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>1</para>
            </TD>
            <TD>
              <para>Management/Infrastructure</para>
            </TD>
            <TD>
              <para>172.16.1.0/23</para>
            </TD>
            <TD>
              <para>2040</para>
            </TD>
            <TD>
              <para>Network for management and infrastructure. Addresses can be static or dynamic and are configured in Windows.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>10</para>
            </TD>
            <TD>
              <para>Network Virtualization</para>
            </TD>
            <TD>
              <para>10.0.0.0/24</para>
            </TD>
            <TD>
              <para>2044</para>
            </TD>
            <TD>
              <para>Network for the <?Comment VEH: UI element 2014-06-19T10:40:00Z  Id='3?>VM network<?CommentEnd Id='3'
    ?> traffic. Addresses must be static and are configured in <token>vmmblue_2</token>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>10</para>
            </TD>
            <TD>
              <para>External</para>
            </TD>
            <TD>
              <para>131.107.0.0/24</para>
            </TD>
            <TD>
              <para>2042</para>
            </TD>
            <TD>
              <para>External, Internet-facing network. Addresses must be static and are configured in <token>vmmblue_2</token>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>1</para>
            </TD>
            <TD>
              <para>Clustering</para>
            </TD>
            <TD>
              <para>10.0.1.0/24</para>
            </TD>
            <TD>
              <para>2043</para>
            </TD>
            <TD>
              <para>Used for cluster communication. Addresses can be static or dynamic and are configured in Windows.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>10</para>
            </TD>
            <TD>
              <para>Storage</para>
            </TD>
            <TD>
              <para>10.20.31.0/24</para>
            </TD>
            <TD>
              <para>2041</para>
            </TD>
            <TD>
              <para>Used for storage traffic. Addresses can be static or dynamic and are configured in Windows.</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para />
      <para>
        <legacyBold>VMM logical network plan</legacyBold>
      </para>
      <para>This design recommends the logical networks listed in the following table. Your logical networks may differ based on your particular needs.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Name</para>
            </TD>
            <TD>
              <para>IP pools and network sites</para>
            </TD>
            <TD>
              <para>Notes</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>External</para>
            </TD>
            <TD>
              <list class="bullet">
                <listItem>
                  <para>Rack01_External</para>
                  <list class="bullet">
                    <listItem>
                      <para>131.107.0.0/24, VLAN 2042</para>
                    </listItem>
                    <listItem>
                      <para>All Hosts</para>
                    </listItem>
                  </list>
                </listItem>
              </list>
            </TD>
            <TD>
              <para />
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Host Networks</para>
            </TD>
            <TD>
              <list class="bullet">
                <listItem>
                  <para>Rack01_LiveMigration</para>
                  <list class="bullet">
                    <listItem>
                      <para>10.0.3.0, VLAN 2045</para>
                    </listItem>
                    <listItem>
                      <para>All Hosts</para>
                    </listItem>
                  </list>
                </listItem>
                <listItem>
                  <para>Rack01_Storage</para>
                  <list class="bullet">
                    <listItem>
                      <para>10.20.31.0, VLAN 2041</para>
                    </listItem>
                    <listItem>
                      <para>All Hosts</para>
                    </listItem>
                  </list>
                </listItem>
              </list>
            </TD>
            <TD>
              <para />
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Infrastructure</para>
            </TD>
            <TD>
              <list class="bullet">
                <listItem>
                  <para>Rack01_Infrastructure</para>
                  <list class="bullet">
                    <listItem>
                      <para>172.16.0.0/24, VLAN 2040</para>
                    </listItem>
                    <listItem>
                      <para>All Hosts</para>
                    </listItem>
                  </list>
                </listItem>
              </list>
            </TD>
            <TD>
              <para />
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Network Virtualization</para>
            </TD>
            <TD>
              <list class="bullet">
                <listItem>
                  <para>Rack01_NetworkVirtualization</para>
                  <list class="bullet">
                    <listItem>
                      <para>10.0.0.0/24, VLAN 2044</para>
                    </listItem>
                    <listItem>
                      <para>All Hosts</para>
                    </listItem>
                  </list>
                </listItem>
              </list>
            </TD>
            <TD>
              <para />
            </TD>
          </tr>
        </tbody>
      </table>
      <para />
      <para>
        <legacyBold>VMM <?Comment VEH: A VMM UI element 2014-06-19T10:40:00Z  Id='4?>VM network<?CommentEnd Id='4'
    ?> plan</legacyBold>
      </para>
      <para>This design uses the VM networks listed in the following table. Your VM networks may differ based on your particular needs.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Name</para>
            </TD>
            <TD>
              <para>IP pool address range</para>
            </TD>
            <TD>
              <para>Notes</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>External</para>
            </TD>
            <TD>
              <para>None</para>
            </TD>
            <TD>
              <para />
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Live migration</para>
            </TD>
            <TD>
              <para>10.0.3.1 – 10.0.3.254</para>
            </TD>
            <TD>
              <para />
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Management</para>
            </TD>
            <TD>
              <para>None</para>
            </TD>
            <TD>
              <para />
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Storage</para>
            </TD>
            <TD>
              <para>10.20.31.1 – 10.20.31.254</para>
            </TD>
            <TD>
              <para />
            </TD>
          </tr>
        </tbody>
      </table>
      <para>After you install <token>vmmblue_2</token>, you can create a logical switch and uplink port profiles. You then configure the hosts on your network to use a logical switch, together with virtual network adapters attached to the switch. For more information about logical switches and uplink port profiles, see <externalLink><linkText>Configuring Ports and Switches for VM Networks in VMM</linkText><linkUri>http://technet.microsoft.com/library/jj721570.aspx</linkUri></externalLink>.</para>
      <para>This design uses the following uplink port profiles, as defined in VMM:</para>
      <para>
        <legacyBold>VMM uplink port profile plan</legacyBold>
      </para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Name</para>
            </TD>
            <TD>
              <para>General property</para>
            </TD>
            <TD>
              <para>Network configuration</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>Rack01_Gateway</para>
            </TD>
            <TD>
              <list class="bullet">
                <listItem>
                  <para>Load Balancing Algorithm: Host Default</para>
                </listItem>
                <listItem>
                  <para>Teaming mode: LACP</para>
                </listItem>
              </list>
            </TD>
            <TD>
              <para>Network sites:</para>
              <list class="bullet">
                <listItem>
                  <para>Rack01_External, Logical Network: External</para>
                </listItem>
                <listItem>
                  <para>Rack01_LiveMigration, Logical Network: Host Networks</para>
                </listItem>
                <listItem>
                  <para>Rack01_Storage, Logical Network: Host Networks</para>
                </listItem>
                <listItem>
                  <para>Rack01_Infrastructure, Logical Network: Infrastructure</para>
                </listItem>
                <listItem>
                  <para>Network Virtualization_0, Logical Network: Network Virtualization</para>
                </listItem>
              </list>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Rack01_Compute</para>
            </TD>
            <TD>
              <list class="bullet">
                <listItem>
                  <para>Load Balancing Algorithm: Host Default</para>
                </listItem>
                <listItem>
                  <para>Teaming mode: LACP</para>
                </listItem>
              </list>
            </TD>
            <TD>
              <para>Network sites:</para>
              <list class="bullet">
                <listItem>
                  <para>Rack01_External, Logical Network: External</para>
                </listItem>
                <listItem>
                  <para>Rack01_LiveMigration, Logical Network: Host Networks</para>
                </listItem>
                <listItem>
                  <para>Rack01_Storage, Logical Network: Host Networks</para>
                </listItem>
                <listItem>
                  <para>Rack01_Infrastructure, Logical Network: Infrastructure</para>
                </listItem>
                <listItem>
                  <para>Network Virtualization_0, Logical Network: Network Virtualization</para>
                </listItem>
              </list>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Rack01_Infrastructure</para>
            </TD>
            <TD>
              <list class="bullet">
                <listItem>
                  <para>Load Balancing Algorithm: Host Default</para>
                </listItem>
                <listItem>
                  <para>Teaming mode: LACP</para>
                </listItem>
              </list>
            </TD>
            <TD>
              <para>Network sites:</para>
              <list class="bullet">
                <listItem>
                  <para>Rack01_LiveMigration, Logical Network: Host Networks</para>
                </listItem>
                <listItem>
                  <para>Rack01_Storage, Logical Network: Host Networks</para>
                </listItem>
                <listItem>
                  <para>Rack01_Infrastructure, Logical Network: Infrastructure</para>
                </listItem>
              </list>
            </TD>
          </tr>
        </tbody>
      </table>
      <para />
      <para>This design deploys the following logical switch using these uplink port profiles, as defined in VMM:</para>
      <para>
        <legacyBold>VMM logical switch plan</legacyBold>
      </para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Name</para>
            </TD>
            <TD>
              <para>Extension</para>
            </TD>
            <TD>
              <para>Uplink</para>
            </TD>
            <TD>
              <para>Virtual port</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>VMSwitch</para>
            </TD>
            <TD>
              <para>Microsoft Windows Filtering Platform</para>
            </TD>
            <TD>
              <list class="bullet">
                <listItem>
                  <para>Rack01_Compute</para>
                </listItem>
                <listItem>
                  <para>Rack01_Gateway</para>
                </listItem>
                <listItem>
                  <para>Rack01_Infrastructure</para>
                </listItem>
              </list>
            </TD>
            <TD>
              <list class="bullet">
                <listItem>
                  <para>High bandwidth</para>
                </listItem>
                <listItem>
                  <para>Infrastructure</para>
                </listItem>
                <listItem>
                  <para>Live migration workload</para>
                </listItem>
                <listItem>
                  <para>Low bandwidth</para>
                </listItem>
                <listItem>
                  <para>Medium bandwidth</para>
                </listItem>
              </list>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>The design isolates the heaviest traffic loads on the fastest network links. For example, the storage network traffic is isolated from the network virtualization traffic on separate fast links. If you must use slower network links for some of the heavy traffic loads, you could use NIC teaming.</para>
      <alert class="important">
        <para>If you use jumbo frames in you network environment, you may need to make some configuration adjustments when you deploy. For more information, see <externalLink><linkText>Windows Server 2012 R2 Network Virtualization (NVGRE) MTU reduction</linkText><linkUri>http://social.technet.microsoft.com/wiki/contents/articles/23833.windows-server-2012-r2-network-virtualization-nvgre-mtu-reduction.aspx</linkUri></externalLink>.</para>
      </alert>
      <para>
        <embeddedLabel>Plan your Windows Azure Pack deployment</embeddedLabel>
      </para>
      <para>If you use <token>katal_2</token> for your tenant self-service portal, there are numerous options you can configure to offer your tenants. This solution includes some of the VM Cloud features, but there are many more options available to you—not only with VM Clouds, but also with Web Site Clouds, Service Bus Clouds, SQL Servers, MySQL Servers, and more. For more information about <token>katal_2</token> features, see <externalLink><linkText>Windows Azure Pack for Windows Server</linkText><linkUri>http://technet.microsoft.com/library/dn296435.aspx</linkUri></externalLink>. </para>
      <para>After reviewing the <token>katal_2</token> documentation, determine which services you want to deploy. Since this solution only uses the Windows Azure Pack as an optional component, it only utilizes some of the Web Site Clouds features, using an Express deployment, with all the <token>katal_2</token> components installed on a single virtual machine. If you use <token>katal_2</token> as your production portal however, you should use a distributed deployment and plan for the additional resources required.</para>
      <para>To determine your host requirements for a production distributed deployment, see <externalLink><linkText>Windows Azure Pack architecture</linkText><linkUri>http://technet.microsoft.com/library/dn296433.aspx</linkUri></externalLink>. </para>
      <para>Use a distributed deployment if you decide to deploy <token>katal_2</token> in production. If you want to evaluate <token>katal_2</token> features before deploying in production, use the Express deployment. For this solution, you use the Express deployment to demonstrate the Web Site Clouds service. You deploy <token>katal_2</token> on a single virtual machine located on the compute cluster so that the web portals can be accessed from the external (Internet) network. Then, you deploy a virtual machine running Service Provider Foundation on a virtual machine located on the management cluster.</para>
    </content>
  </section>
  <section address="BKMKWhy">
    <title>Why are we recommending this design?</title>
    <content>
      <para>The design includes failover clusters to provide high availability and scalability for the solution. </para>
      <para>The following diagram shows the four types of failover clusters that are deployed. Each failover cluster isolates the roles required for the solution.</para>
      <mediaLink>
        <image xlink:href="9d0a97d9-bf7f-4120-a869-4f7bd495d8dc" />
      </mediaLink>
      <para />
      <para>The following table shows the physical hosts that we recommend for this solution. The number of nodes used was chosen to represent the minimum needed to provide high availability. You can add additional physical hosts to further distribute the workloads to meet your specific requirements. Each host has <legacyBold>4</legacyBold> physical network adapters to support the networking isolation requirements of the design. We recommend that you use a 10 GB/s or faster network infrastructure. 1 Gb/s might be adequate for infrastructure and cluster traffic.</para>
      <para>
        <legacyBold>Physical host recommendation</legacyBold>
      </para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Physical hosts</para>
            </TD>
            <TD>
              <para>Role in solution</para>
            </TD>
            <TD>
              <para>Virtual machine roles </para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>2 hosts configured as a failover cluster</para>
              <para />
            </TD>
            <TD>
              <para>
                <legacyBold>Management/infrastructure cluster:</legacyBold>
              </para>
              <para>Provides Hyper-V hosts for management/infrastructure workloads (VMM, SQL, Service Provider Foundation, guest clustered scale-out file server for gateway domain, domain controller).</para>
            </TD>
            <TD>
              <list class="bullet">
                <listItem>
                  <para>Guest clustered SQL</para>
                </listItem>
                <listItem>
                  <para>Guest clustered VMM</para>
                </listItem>
                <listItem>
                  <para>Guest clustered scale-out file server for gateway domain</para>
                </listItem>
                <listItem>
                  <para>Service Provider Foundation endpoint </para>
                </listItem>
              </list>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>2 hosts configured as a failover cluster</para>
            </TD>
            <TD>
              <para>
                <legacyBold>Compute cluster:</legacyBold>
              </para>
              <para>Provides Hyper-V hosts for tenant workloads and <token>katal_1</token>.</para>
            </TD>
            <TD>
              <list class="bullet">
                <listItem>
                  <para>Tenant </para>
                </listItem>
                <listItem>
                  <para>
                    <token>katal_2</token> portal accessible from public networks</para>
                </listItem>
              </list>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>2 hosts configured as a failover cluster</para>
            </TD>
            <TD>
              <para>
                <legacyBold>Storage cluster:</legacyBold>
              </para>
              <para>Provides scale-out file server for management and infrastructure cluster storage.</para>
            </TD>
            <TD>
              <para>None (this cluster just hosts file shares)</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>2 hosts configured as a failover cluster</para>
            </TD>
            <TD>
              <para>
                <legacyBold>Windows Server gateway cluster:</legacyBold>
              </para>
              <para>Provides Hyper-V hosts for the gateway virtual machines.</para>
              <para>For gateway physical host and gateway virtual machine configuration recommendations, see <legacyLink xlink:href="f8ba42a9-8afa-440e-9244-3f12406309a1">Windows Server Gateway Hardware and Configuration Requirements</legacyLink>.</para>
            </TD>
            <TD>
              <para>Guest clustered gateway</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section address="BKMKSteps">
    <title>What are the steps to implement this solution?</title>
    <content>
      <alert class="important">
        <para>When you deploy Hyper-V hosts and virtual machines, it is extremely important to apply all available updates for the software and operating systems used in this solution. If you don’t do this, your solution many not function as expected.</para>
      </alert>
      <para>You can use the steps in this section to implement the solution. Make sure to verify the correct deployment of each step before proceeding to the next step.</para>
      <alert class="note">
        <para>If you want to print or export a customized set of solution topics, see <externalLink><linkText>Print/Export Multiple Topics – Help</linkText><linkUri>http://technet.microsoft.com/library/export/help/?returnUrl=%2fen-US%2flibrary%2fff630950.aspx</linkUri></externalLink>.</para>
      </alert>
      <list class="ordered">
        <listItem>
          <para>
            <legacyBold>Deploy (or identify) an Active Directory domain.</legacyBold>
          </para>
          <para>Your management, compute, and scale-out file servers will join this domain. Or alternatively, identify an existing Active Directory domain that can host your servers.</para>
        </listItem>
        <listItem>
          <para>
            <legacyBold>Deploy (or identify) a second Active Directory domain.</legacyBold>
          </para>
          <para>This second Active Directory domain will host your Hyper-V host gateway servers and a scale-out file server for gateway storage. This second Active Directory domain should have no trust relationship with your infrastructure domain for security considerations.</para>
          <alert class="important">
            <para>Ensure both domains can resolve names in the other domain. For example, you can configure a forwarder at each DNS server to point to the DNS server in the other domain.</para>
          </alert>
        </listItem>
        <listItem>
          <para>
            <legacyBold>Deploy the storage nodes and clusters for the management domain.</legacyBold>
          </para>
          <para>A scale-out file server hosts the storage for this solution as file shares. This scale-out file server is configured on physical hosts in the management domain. An additional scale-out file server for the gateway domain is implemented in virtual machines later on the management cluster. For more information about deploying a scale-out file server, see <externalLink><linkText>Deploy Scale-Out File Server</linkText><linkUri>http://technet.microsoft.com/library/hh831359.aspx</linkUri></externalLink>.</para>
        </listItem>
        <listItem>
          <para>
            <legacyBold>Deploy the management nodes and clusters.</legacyBold>
          </para>
          <alert class="note">
            <para>You’ll need to create a temporary virtual switch using Hyper-V Manager so you can install and configure your virtual machines. After VMM is installed, you can define a logical switch in VMM, delete the virtual switch defined in Hyper-V, and configure your hosts to use a virtual switch based on the logical switch defined in VMM. </para>
          </alert>
          <para>This host cluster will host the SQL server, VMM, Service Provider Foundation (SPF) server, and scale-out file server (for the gateway domain) virtual machines. The scale-out file server for the gateway domain is implemented in virtual machines and joined to the gateway domain. For more information, see the following topics:</para>
          <list class="bullet">
            <listItem>
              <para>
                <legacyLink xlink:href="6eeffe4f-3558-495b-bcea-c640fe4d6c49">Failover Clustering Overview [Role/Tech Overview]</legacyLink>
              </para>
            </listItem>
            <listItem>
              <para>
                <legacyLink xlink:href="d25a2cb3-0932-47c9-b2e4-0e0c7ae9dd6a">Deploy a Guest Cluster Using a Shared Virtual Hard Disk [2012R2]</legacyLink>
              </para>
            </listItem>
          </list>
          <alert class="important">
            <para>Deploy all the virtual machines on one host cluster node for now. After the networking features are configured in VMM, you load balance the virtual machines across the host cluster nodes.</para>
          </alert>
          <list class="ordered">
            <listItem>
              <para>Deploy the SQL guest cluster.</para>
              <para>For information about deploying a SQL Server failover cluster instance, see the following topics:</para>
              <list class="bullet">
                <listItem>
                  <para>
                    <externalLink>
                      <linkText>AlwaysOn Failover Cluster Instances (SQL Server)</linkText>
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
              <para>Deploy VMM.</para>
              <para>For information about how to do this, see <externalLink><linkText>Deploying System Center 2012 - Virtual Machine Manager</linkText><linkUri>http://technet.microsoft.com/library/gg610669.aspx</linkUri></externalLink>. For this solution, you use VMM to deploy and manage your gateway and other network features.</para>
              <list class="ordered">
                <listItem>
                  <para>Install VMM on a guest cluster.</para>
                  <para>For information about how to do this, see the following topics: </para>
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
                        <externalLink>
                          <linkText>How to Install a VMM Management Server on an Additional Node of a Cluster</linkText>
                          <linkUri>http://technet.microsoft.com/library/hh411279.aspx</linkUri>
                        </externalLink>
                      </para>
                    </listItem>
                  </list>
                  <para />
                </listItem>
                <listItem>
                  <para>Add a library server, using a share on your scale-out file server. For more information, see <externalLink><linkText>How to Add a VMM Library Server or VMM Library Share</linkText><linkUri>http://technet.microsoft.com/library/gg610579.aspx</linkUri></externalLink>. When you are prompted to type the computer name, type the name you used when you configured the scale-out file server role. Do not use the cluster name.</para>
                  <alert class="important">
                    <para>When you add a library server, ensure that you use a user account that is different from your VMM service account. If you don’t do this, VMM will silently fail to add the library server and you won’t see any job history indicating an error has occurred.</para>
                  </alert>
                </listItem>
                <listItem>
                  <para>Disable the <ui>Create logical networks automatically</ui> setting before you add any hosts. You’ll manually create logical networks with specific settings later. This setting is located in <ui>Settings</ui>, <ui>Network Settings</ui>.</para>
                </listItem>
                <listItem>
                  <para>Add the designated Hyper-V hosts as VMM hosts.</para>
                  <para>Add the management cluster and the Scale-Out File Server cluster. You’ll add the compute host cluster later.</para>
                  <para>You should add the Scale-Out File Server cluster in the <ui>Fabric</ui>, <ui>Storage</ui>, <ui>File Servers</ui> category. You should add the management cluster (and eventually the compute cluster) under <ui>All Hosts</ui>. To help organize the hosts, you should create additional host groups (for example, <ui>Compute</ui>, and <ui>Management</ui>) and place the appropriate clusters in the host groups.</para>
                  <alert class="important">
                    <para>When you deploy a scale-out file server for the gateway domain, you need to open the public <ui>Windows Remote Management (HTTP-In)</ui> port on both nodes of the guest cluster. This port needs to be opened because the VMM server and gateway cluster exist in separate, untrusted domains and that port is not open by default for the Public profile.</para>
                  </alert>
                  <para>For more information, see <externalLink><linkText>Adding Windows Servers as Hyper-V Hosts in VMM Overview</linkText><linkUri>http://technet.microsoft.com/library/gg610646.aspx</linkUri></externalLink>.</para>
                  <para>To see an example procedure, see “To add HNVHOST1, HNVHOST2, and HNVHOST3 as VMM Hosts” in <externalLink><linkText>Test Lab Guide: Windows Server 2012 R2 Hyper-V Network Virtualization with System Center 2012 R2 VMM</linkText><linkUri>http://www.microsoft.com/download/details.aspx?id=39284</linkUri></externalLink>.</para>
                </listItem>
                <listItem>
                  <para>Add file share storage.</para>
                  <para>After you add the cluster, you can configure storage locations for the virtual machines that are deployed to nodes in the cluster. Open the <ui>Properties</ui> page for the cluster and add a share from your scale-out file server on the <ui>File Share Storage</ui> page.</para>
                </listItem>
                <listItem>
                  <para>Create the planned logical networks and associated IP pools.</para>
                  <para>For this solution, you can create a logical network for External (Internet), Infrastructure, Host Networks (with Cluster IP Pool and Live Migration IP Pool), and Network Virtualization networks. Note that these are sample names—you can use your own names according to your plan. Create the appropriate IP pools for each logical network according to your plan, making sure that the IP address ranges don’t overlap with any existing IP addresses in use.</para>
                  <para>You configure the Host Networks logical network as a <ui>VLAN-based independent network</ui>, and configure the others as <ui>One connected network</ui>.</para>
                  <para>For more information, see <externalLink><linkText>How to Create a Logical Network in VMM</linkText><linkUri>http://technet.microsoft.com/library/gg610588.aspx</linkUri></externalLink>.</para>
                  <para>To see an example procedure in a test environment, see “Define logical networks with associated IP pools” in <externalLink><linkText>Test Lab Guide: Windows Server 2012 R2 Hyper-V Network Virtualization with System Center 2012 R2 VMM</linkText><linkUri>http://www.microsoft.com/download/details.aspx?id=39284</linkUri></externalLink>.</para>
                </listItem>
                <listItem>
                  <para>Create VM networks for the Infrastructure, External (Internet), Live Migration, and Storage logical networks.</para>
                  <para>Create an IP address pool for the Storage and Live Migration networks, using the appropriate address range according to your plan.</para>
                  <para>For more information, see <externalLink><linkText>How to Create a VM Network in VMM in System Center 2012 R2</linkText><linkUri>http://technet.microsoft.com/library/dn249413.aspx</linkUri></externalLink>.</para>
                  <para>To see an example procedure in a test environment, see “Define VM networks” in <externalLink><linkText>Test Lab Guide: Windows Server 2012 R2 Hyper-V Network Virtualization with System Center 2012 R2 VMM</linkText><linkUri>http://www.microsoft.com/download/details.aspx?id=39284</linkUri></externalLink>.</para>
                </listItem>
                <listItem>
                  <para>Create the uplink port profiles.</para>
                  <para>Create a Gateway, Compute, and Infrastructure Uplink port profile. Configure the <ui>Host Default</ui> Load balancing algorithm and the Link Aggregation Control Protocol (<ui>LACP</ui>) teaming mode (assuming that your switch supports LACP). Select all the network sites for the network configuration of your Compute and Gateway port profile, and the Live Migration, Storage, and Infrastructure sites for your Infrastructure profiles.</para>
                  <para>For more information, see <externalLink><linkText>Configuring Ports and Switches for VM Networks in VMM</linkText><linkUri>http://technet.microsoft.com/library/jj721570.aspx</linkUri></externalLink>.</para>
                  <para>To see an example procedure in a test environment, see “Create port profiles and logical switches” in <externalLink><linkText>Test Lab Guide: Windows Server 2012 R2 Hyper-V Network Virtualization with System Center 2012 R2 VMM</linkText><linkUri>http://www.microsoft.com/download/details.aspx?id=39284</linkUri></externalLink>.</para>
                </listItem>
                <listItem>
                  <para>Create the logical switch.</para>
                  <para>Select the <?Comment VEH: This is a UI element and shouldn’t be changed. 2014-02-17T18:09:00Z  Id='5?>Microsoft Windows Filtering Platform<?CommentEnd Id='5'
    ?> for the Extensions, select Team for the Uplink mode, and add the three uplink port profiles that you created previously.</para>
                  <para>Add the following virtual ports: High bandwidth, Infrastructure, Live migration workload, Low bandwidth, and Medium bandwidth.</para>
                </listItem>
                <listItem>
                  <para>Create a teamed virtual switch on a management node.</para>
                  <para>Add a virtual switch to the management host cluster node. This is the node that doesn’t have any virtual machines associated with it.</para>
                  <para>To do this in VMM, locate the host node on the Fabric, Servers pane, open the; <ui>Properties</ui> page and add a virtual switch on the <ui>New Virtual Switch</ui> page. </para>
                  <para>Add your two fastest physical adapters to form a team and choose the Infrastructure Uplink port profile. Then add two virtual network adapters for Live Migration and Storage.</para>
                  <para />
                  <para>When you’re done, verify that your virtual switch looks similar to the following:</para>
                  <para />
                  <mediaLink>
                    <image xlink:href="bd01c21b-1f56-4f17-b627-f0b34f979d35" />
                  </mediaLink>
                  <para />
                  <mediaLink>
                    <image xlink:href="3dca69ca-5778-45ed-889a-edace5897631" />
                  </mediaLink>
                  <para />
                  <mediaLink>
                    <image xlink:href="7515fd9c-b947-4e6b-a10c-ddc3dc36d383" />
                  </mediaLink>
                  <para />
                  <alert class="important">
                    <para>You might need to make some configuration changes to the physical switch ports that these network adapters are connected to. If you’re using LACP for teaming, you’ll need to configure the switch ports for LACP. If your switch ports are configured in Access Mode (for untagged packets), you need to configure them in Trunk Mode, because tagged packets will be coming from the teamed adapters.</para>
                  </alert>
                  <para>For more information, see <externalLink><linkText>How to Configure Network Settings on a Host by Applying a Logical Switch in VMM</linkText><linkUri>http://technet.microsoft.com/library/jj628156.aspx</linkUri></externalLink>.</para>
                  <alert class="tip">
                    <para>For troubleshooting purposes, you can use the following <token>wps_2</token> cmdlets:</para>
                    <para>
                      <codeInline>Get-NetLbfoTeam</codeInline>, <codeInline>Get-NetLbfoTeamMember</codeInline>, and <codeInline>Get-NetLbfoTeamNic</codeInline></para>
                    <para>To see other related cmdlets, type <codeInline>Get-command *lbfo*</codeInline>.</para>
                  </alert>
                </listItem>
                <listItem>
                  <para>Configure your migration settings.</para>
                  <para>Now that you have your live migration adapter configured on the virtual switch, you can configure your migration settings on each node’s <ui>Property</ui>, <ui>Migration Settings</ui> page. Configure your desired settings, and ensure your live migration subnet address has been added and is at the top of the list. The subnet is actually entered as a single IP address with a 32-bit mask: x.x.x.x/32. So, if your live migration virtual network adapter’s address is 10.0.3.6, then the Migration Settings page may look similar to the following:</para>
                  <para />
                  <mediaLink>
                    <image xlink:href="7ec13703-58ce-42ba-9423-a6083138d3aa" />
                  </mediaLink>
                </listItem>
                <listItem>
                  <para>Live migrate your virtual machines.</para>
                  <para>Now that you have a host configured with a virtual switch configured using VMM, you can migrate your virtual machines to it so you can prepare the other node the same way.</para>
                  <para>
                    <?Comment VEH: Intentionally keeping this click stream. 2014-05-09T09:56:00Z  Id='6?>To migrate your virtual machines, in VMM, select the <ui>VMs and Services</ui> workspace, select the node in your management cluster that has the virtual machines running on it, right-click the running virtual machine, and click <ui>Migrate Virtual Machine</ui>. Select the other node and move the virtual machine.<?CommentEnd Id='6'
    ?></para>
                </listItem>
                <listItem>
                  <para>Delete the virtual switch that was originally created using Hyper-V Manager.</para>
                  <para>Now that you have moved the virtual machines, you can delete the original virtual switch that you created with Hyper-V Manager.</para>
                </listItem>
                <listItem>
                  <para>Create a new teamed virtual switch using VMM.</para>
                  <para>After you delete the old virtual switch, you can create a new teamed virtual switch like you did with the previous node. Follow the previous step to create the virtual switch on this node using VMM.</para>
                </listItem>
                <listItem>
                  <para>Live migrate some virtual machines back.</para>
                  <para>Now that you have both nodes configured with a teamed virtual switch using VMM, you can migrate some of the virtual machines back. For example, move one of the SQL guest cluster nodes so that you have the guest cluster nodes split across the host cluster nodes. Do this for all the other guest clusters.</para>
                </listItem>
              </list>
              <para>After this step is complete, you should have both of your management host cluster nodes installed with the management virtual machines and the host node networking configured through VMM.</para>
            </listItem>
          </list>
        </listItem>
        <listItem>
          <para>
            <legacyBold>Deploy the compute nodes and clusters</legacyBold>.</para>
          <para>This Hyper-V cluster hosts the tenant virtual machines and the Windows Azure Pack portal server.</para>
          <para>You can install the compute Hyper-V cluster in a similar manner that you installed the management cluster: </para>
          <list class="ordered">
            <listItem>
              <para>Deploy the Hyper-V hosts and join the management domain.</para>
            </listItem>
            <listItem>
              <para>Cluster the hosts and add the cluster to your VMM Compute Host group.</para>
            </listItem>
            <listItem>
              <para>Create the teamed virtual switch and the live migration and storage virtual adapters for both host nodes like you did for both of the management nodes. When you team the physical adapters, use the Compute Uplink port profile for the adapters. </para>
            </listItem>
            <listItem>
              <para>Add file share storage.</para>
              <para>Configure a storage location for the virtual machines deployed to nodes in the cluster. Open the Properties page for the cluster and add a share from your scale-out file server on the File Share Storage page.</para>
            </listItem>
          </list>
        </listItem>
        <listItem>
          <para>
            <legacyBold>Deploy the gateway</legacyBold>.</para>
          <para>To deploy the Windows Server gateway in <token>winblue_server_2</token>, you deploy a dedicated Hyper-V host cluster and then deploy the gateway virtual machines using VMM. The Windows Server gateway provides a connection point for multiple tenant site-to-site VPN connections. You follow a similar procedure to deploy the physical hosts, but then you use a VMM service template to deploy the guest cluster virtual machines.</para>
          <para>To deploy the Windows Server gateway, use the following procedure:</para>
          <list class="ordered">
            <listItem>
              <para>Deploy the Hyper-V hosts and join the gateway domain.</para>
            </listItem>
            <listItem>
              <para>Cluster the hosts and add the cluster to your VMM Gateway Host group.</para>
            </listItem>
            <listItem>
              <para>Create the teamed virtual switch and the live migration and storage virtual adapters for both host nodes like you did for both of the management and compute nodes. When you team the physical adapters, use the Gateway Uplink port profile for the adapters.</para>
            </listItem>
            <listItem>
              <para>Add file share storage.</para>
              <para>Configure a storage location for the virtual machines that are deployed to nodes in the cluster. Open the <ui>Properties</ui> page for the cluster and add a share from your scale-out file server on the <ui>File Share Storage</ui> page.</para>
            </listItem>
            <listItem>
              <para>Ensure that you have a file share available from VMM (where you have a <token>winblue_server_2</token> .vhd or .vhdx file available). This file will be used by the VMM service template to deploy the gateway virtual machines.</para>
            </listItem>
            <listItem>
              <para>Configure hosts as gateway hosts.</para>
              <para>You must configure each gateway Hyper-V host as a dedicated network virtualization gateway. <?Comment VEH: Intentionally leaving this click stream in 2014-05-09T14:04:00Z  Id='7?>In VMM, right-click a gateway host and click <ui>Properties</ui>. Click <ui>Host Access</ui> and click the check box for <ui>This host is a dedicated network virtualization gateway, as a result is not available for placement of virtual machines requiring network virtualization.<?CommentEnd Id='7'
    ?></ui> </para>
            </listItem>
            <listItem>
              <para>To deploy the gateway virtual machines, follow the procedures in the following topic: <externalLink><linkText>How to Use a Server Running Windows Server 2012 R2 as a Gateway with VMM</linkText><linkUri>http://technet.microsoft.com/library/dn249417.aspx</linkUri></externalLink> and deploy using the 3-NIC HA Gateway service template.</para>
              <para>The service template that you use to deploy the gateway includes a Quick Start Guide document. This document includes some information to setup the infrastructure for the gateway deployment. This information is similar to the information provided in this solution guide. You can skip the infrastructure steps in the Quick Start Guide that are already covered in this solution guide. </para>
              <para>When you reach the final configuration steps and run the Add a network service wizard, your Connection String page will look similar to the following:</para>
              <para />
              <mediaLink>
                <image xlink:href="80fc7c64-b0ff-48a0-8572-4ec9e2cd45b0" />
              </mediaLink>
              <para />
              <para />
              <para>And the Connectivity property of your gateway network service will look similar to the following: </para>
              <para />
              <mediaLink>
                <image xlink:href="6370e3a1-9624-45be-94fd-6979de352df6" />
              </mediaLink>
            </listItem>
          </list>
          <para>After this step is complete, verify that two jobs in the log have completed successfully:</para>
          <list class="bullet">
            <listItem>
              <para>Update network service device</para>
            </listItem>
            <listItem>
              <para>Add connection network service device</para>
            </listItem>
          </list>
          <alert class="tip">
            <para>If you need to deploy a gateway guest cluster on a regular basis (for example, to address resource demands), you can customize the service template using the Service Template Designer. For example, you can customize the <ui>OS Configuration</ui> settings to join a specific domain, use a specific product key, or use a specific computer name configuration. </para>
          </alert>
          <alert class="caution">
            <para>Do not modify the gateway service template to make the virtual machines highly available. The gateway service template intentionally leaves the <ui>Make this virtual machine highly available</ui> check box in the <ui>Advanced\Availability</ui> area unchecked. The virtual machines are configured as nodes of a guest cluster, but it’s important to not change this setting. Otherwise, during failover, the customer addresses (CA) won’t associate with the new provider address (PA) and the gateway will not function properly. </para>
          </alert>
        </listItem>
        <listItem>
          <para>
            <legacyBold>Verify gateway functionality</legacyBold>.</para>
          <para>Verify that there is connectivity between a test virtual machine and the hosts located on a test tenant network.</para>
          <para>Use the following steps to verify that your gateway and VM networks are functioning correctly.</para>
          <list class="ordered">
            <listItem>
              <para>Establish a site-to-site VPN connection.</para>
              <para>How you connect your test tenant network will vary depending on the equipment you use to establish the VPN connection. Remote Access (which brings together Direct Access and Routing and Remote Access service (RRAS)) is one way to connect to your gateway. To see an example procedure using RRAS to connect to the gateway, see “Install RRAS on Contoso EDGE1 and create a site-to-site VPN connection to GatewayVM1 running on HNVHOST3” in <externalLink><linkText>Test Lab Guide: Windows Server 2012 R2 Hyper-V Network Virtualization with System Center 2012 R2 VMM</linkText><linkUri>http://www.microsoft.com/download/details.aspx?id=39284</linkUri></externalLink>.</para>
              <alert class="tip">
                <para>To connect other VPN devices, the connectivity requirements are similar to the Windows Azure VPN connection requirements. For more information, see <externalLink><linkText>About VPN Devices for Virtual Network</linkText><linkUri>http://msdn.microsoft.com/library/windowsazure/jj156075.aspx</linkUri></externalLink></para>
              </alert>
            </listItem>
            <listItem>
              <para>View the site-to-site VPN connection on your gateway.</para>
              <para>After you establish the VPN connection, you can use some <token>wps_2</token> commands and some new ping options to verify the VPN connection. </para>
              <para>To see an example procedure in a test environment, see “To view the S2S VPN connections on GatewayVM1” in <externalLink><linkText>Test Lab Guide: Windows Server 2012 R2 Hyper-V Network Virtualization with System Center 2012 R2 VMM</linkText><linkUri>http://www.microsoft.com/download/details.aspx?id=39284</linkUri></externalLink>.</para>
            </listItem>
            <listItem>
              <para>
                <legacyBold>Deploy test tenant virtual machines.</legacyBold>
              </para>
              <para>After you verify that you have a successful site-to-site connection to your gateway, you can deploy a test virtual machine and connect it to the test VM network on your hosting service provider network.</para>
              <para>To see an example procedure in a test environment, see “Step 2: Deploy Tenant Virtual Machines” in <externalLink><linkText>Test Lab Guide: Windows Server 2012 R2 Hyper-V Network Virtualization with System Center 2012 R2 VMM</linkText><linkUri>http://www.microsoft.com/download/details.aspx?id=39284</linkUri></externalLink>.</para>
            </listItem>
            <listItem>
              <para>Verify test VM network connectivity and HNV site-to-site operation.</para>
              <para>After you deploy your test virtual machine, you should verify that it has network connectivity to remote resources in the tenant on-premises network over the Internet through the multi-tenant site-to-site gateway.</para>
              <para>To see an example procedure in a test environment, see “Verify network connectivity for the APP2 virtual machines” in <externalLink><linkText>Test Lab Guide: Windows Server 2012 R2 Hyper-V Network Virtualization with System Center 2012 R2 VMM</linkText><linkUri>http://www.microsoft.com/download/details.aspx?id=39284</linkUri></externalLink>.</para>
            </listItem>
          </list>
        </listItem>
        <listItem>
          <para>
            <legacyBold>Deploy Windows Server IPAM (recommended)</legacyBold>.</para>
          <para>Windows Server IPAM is integrated with VMM to manage the IP address space for your customer and fabric infrastructure. For more information, see <legacyLink xlink:href="6cf9b2c8-41b8-493e-add5-f09ef72fa01d">Deploy IPAM Server</legacyLink>.</para>
          <para>To see an example procedure in a test environment, see “Step 6: Install and configure IPAM on HNVHOST2” in <externalLink><linkText>Test Lab Guide: Windows Server 2012 R2 Hyper-V Network Virtualization with System Center 2012 R2 VMM</linkText><linkUri>http://www.microsoft.com/download/details.aspx?id=39284</linkUri></externalLink>.</para>
          <para />
          <para>After IPAM has been deployed, configure the IPAM VMM plug-in. For more information, see <externalLink><linkText>How to Add an IPAM Server in VMM in System Center 2012 R2</linkText><linkUri>http://technet.microsoft.com/library/dn249418.aspx</linkUri></externalLink>.</para>
          <para>To see an example procedure in a test environment, see “To configure the IPAM VMM plugin on HNVHOST2” in <externalLink><linkText>Test Lab Guide: Windows Server 2012 R2 Hyper-V Network Virtualization with System Center 2012 R2 VMM</linkText><linkUri>http://www.microsoft.com/download/details.aspx?id=39284</linkUri></externalLink>.</para>
          <para>After this step is complete, verify that you can view the virtualized address space in IPAM. </para>
          <para>To see an example procedure in a test environment, see “To use IPAM to view the virtualized address space” in <externalLink><linkText>Test Lab Guide: Windows Server 2012 R2 Hyper-V Network Virtualization with System Center 2012 R2 VMM</linkText><linkUri>http://www.microsoft.com/download/details.aspx?id=39284</linkUri></externalLink>.</para>
        </listItem>
        <listItem>
          <para>
            <legacyBold>Deploy a self-service tenant portal</legacyBold>.</para>
          <para>A tenant self-service portal allows your tenants to create their own virtual networks and virtual machines with minimal hosting service provider involvement. Service providers can design and implement multi-tenant self-service portals that integrate IaaS capabilities that are available on System Center 2012 R2. Service Provider Foundation exposes an extensible OData web service that interacts with VMM.</para>
          <para>
            <token>katal_2</token> is a Microsoft self-service portal solution that integrates with VMM using SPF. It offers a web site portal similar to Windows Azure, so if your tenants are also Windows Azure customers, they will already be familiar with the user interface presented in <token>katal_2</token>. To demonstrate <token>katal_2</token> features for this solution, an express <token>katal_2</token> deployment is used. This deploys the required features on a single server. If you want to deploy <token>katal_2</token> in production, you should use the distributed deployment. For more information, see <externalLink><linkText>Windows Azure Pack installation requirements</linkText><linkUri>http://technet.microsoft.com/library/dn296442.aspx</linkUri></externalLink>.</para>
          <list class="ordered">
            <listItem>
              <para>Create the WAPPortal virtual machine.</para>
              <para>Review <externalLink><linkText>Express deployment hardware and software prerequisites</linkText><linkUri>http://technet.microsoft.com/library/dn469325.aspx</linkUri></externalLink> and then create the WAPPortal virtual machine on your compute cluster.</para>
            </listItem>
            <listItem>
              <para>Install software prerequisites.</para>
              <para>Follow the procedure in <externalLink><linkText>Install software prerequisites</linkText><linkUri>http://technet.microsoft.com/library/dn469335.aspx</linkUri></externalLink>.</para>
            </listItem>
            <listItem>
              <para>Install an express deployment of Windows Azure Pack.</para>
              <para>Follow the procedure in <externalLink><linkText>Install an express deployment of Windows Azure Pack</linkText><linkUri>http://technet.microsoft.com/library/dn296439.aspx</linkUri></externalLink>.</para>
            </listItem>
            <listItem>
              <para>Review the topics under <externalLink><linkText>Provision Virtual Machine Clouds</linkText><linkUri>http://technet.microsoft.com/library/dn457797.aspx</linkUri></externalLink>, and then review the guidance in <externalLink><linkText>Requirements for using VM Clouds</linkText><linkUri>http://technet.microsoft.com/library/dn457804.aspx</linkUri></externalLink>. </para>
            </listItem>
            <listItem>
              <para>Using VMM, create a cloud.</para>
              <para>For example, you could use the Create Cloud Wizard to create a cloud with the following properties: </para>
              <para />
              <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
                <thead>
                  <tr>
                    <TD>
                      <para>Properties</para>
                    </TD>
                    <TD>
                      <para>Settings</para>
                    </TD>
                  </tr>
                </thead>
                <tbody>
                  <tr>
                    <TD>
                      <para>General</para>
                    </TD>
                    <TD>
                      <para>Name: Gold</para>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>Resources</para>
                    </TD>
                    <TD>
                      <para>Host Group: Compute</para>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>Logical Networks</para>
                    </TD>
                    <TD>
                      <para>Network Virtualization</para>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>Port Classifications</para>
                    </TD>
                    <TD>
                      <para>High Bandwidth</para>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>Storage</para>
                    </TD>
                    <TD>
                      <para>Remote Storage</para>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>Library</para>
                    </TD>
                    <TD>
                      <para>VMM-Lib (a share located on the scale-out file server)</para>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>Capacity</para>
                    </TD>
                    <TD>
                      <para>Cloud Capacity: set to your desired capacity</para>
                    </TD>
                  </tr>
                </tbody>
              </table>
              <para>For more information about creating a cloud in VMM, see <externalLink><linkText>How to Create a Private Cloud from Host Groups</linkText><linkUri>http://technet.microsoft.com/library/gg610567.aspx</linkUri></externalLink>.</para>
            </listItem>
            <listItem>
              <para>Install Service Provider Foundation on a separate virtual machine located on the management and infrastructure cluster using the procedure in <externalLink><linkText>How to Install Service Provider Foundation for System Center 2012 SP1</linkText><linkUri>http://technet.microsoft.com/library/jj642898.aspx</linkUri></externalLink>.</para>
            </listItem>
            <listItem>
              <para>Configure SPF for use with <token>katal_2</token>, as described in <externalLink><linkText>Configuring Portals for Service Provider Foundation</linkText><linkUri>http://technet.microsoft.com/library/jj871728.aspx</linkUri></externalLink> in the “Configuring Windows Azure Pack for Windows Server” section.</para>
              <para>After you have completed the procedure to register the SPF endpoint for virtual machine clouds, you should see the cloud that you created in VMM on the <token>katal_2</token> administrator portal.</para>
            </listItem>
            <listItem>
              <para>From the <token>katal_2</token> administrator portal, author a plan that you can use to test with. For example, you could author a plan called <legacyBold>Gold Plan</legacyBold> with the following properties:</para>
              <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
                <thead>
                  <tr>
                    <TD>
                      <para>Properties</para>
                    </TD>
                    <TD>
                      <para>Settings</para>
                    </TD>
                  </tr>
                </thead>
                <tbody>
                  <tr>
                    <TD>
                      <para>Name</para>
                    </TD>
                    <TD>
                      <para>Gold Plan</para>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>Services</para>
                    </TD>
                    <TD>
                      <para>Virtual Machine Clouds</para>
                    </TD>
                  </tr>
                </tbody>
              </table>
              <para>After the plan is created, click it to continue the configuration. Click the <ui>Virtual Machine Clouds</ui> service and configure the <ui>VMM Management Server</ui>, <ui>Virtual Machine Cloud</ui>, and usage limits. Click <ui>Save</ui> to complete the virtual machine clouds configuration. Click the back button and finally click <ui>Change Access</ui> to make the plan public.</para>
            </listItem>
            <listItem>
              <para>Create a <token>katal_2</token> Gallery Resource. Tenants can use the Gallery to place virtual machines on their virtual networks. For more information, see <externalLink><linkText>Downloading and Installing Windows Azure Pack Gallery Resource</linkText><linkUri>http://social.technet.microsoft.com/wiki/contents/articles/20194.downloading-and-installing-windows-azure-pack-gallery-resource.aspx</linkUri></externalLink>. </para>
            </listItem>
            <listItem>
              <para>From the <token>katal_2</token> tenant portal logon page, click <ui>Sign Up</ui> to sign up a test tenant account.</para>
              <para>Proceed through the tenant portal, add a subscription and choose a plan. </para>
            </listItem>
            <listItem>
              <para>After the account has been created, create a new virtual network for the tenant using <ui>Custom Create</ui>.</para>
              <para>When you’re done creating the network, verify that it exists in VMM under <ui>VM Networks</ui>.</para>
            </listItem>
            <listItem>
              <para>Establish a site-to-site VPN connection with the test tenant like you did previously when you created a manual test virtual network.</para>
            </listItem>
            <listItem>
              <para>Create a new virtual machine role using the Gallery that you created previously.</para>
            </listItem>
            <listItem>
              <para>After the test virtual machine has been created, verify that it has connectivity back to the tenant network through the site-to-site VPN tunnel.</para>
            </listItem>
          </list>
        </listItem>
      </list>
    </content>
  </section>
  <section address="BKMKOptions">
    <title>Optional configurations</title>
    <content>
      <para>This section describes optional configurations to add functionality to this solution.</para>
    </content>
    <sections>
      <section>
        <title>Deploy a forwarding gateway to support Internet connected virtual machines</title>
        <content>
          <para>You may have tenants that want to deploy virtual machines that are directly connected to the Internet.  They may have connection needs that require no NAT in the connection path.</para>
          <para>Or, you may have tenants that need connectivity directly to a physical network. For example a VLAN with co-located hardware or a packet switched network (such as a multiprotocol label switching (MPLS) network).</para>
          <para>You can support these requirements using a forwarding gateway connected to a VM network used exclusively for directly connected virtual machines. You then create subnets on the VM network for each tenant. You can use extended port access control lists to isolate each of the tenant virtual machines and control the network traffic in and out of their virtual machines.</para>
          <para>Here’s how to do it:</para>
          <list class="ordered">
            <listItem>
              <para>Deploy a gateway using the service template in the same way as in the original solution.</para>
            </listItem>
            <listItem>
              <para>Note the cluster front end IP address and name of the new VM gateway cluster. You will use this information in the connection string used in the next step.</para>
            </listItem>
            <listItem>
              <para>Create a new network service in VMM to deploy the forwarding gateway service. Use a connection string similar to the following:
</para>
              <para>
                <codeInline>VMHost=gateway-cl.adatum-gw.lab;GatewayVM=FGWCL01.adatum-gw.lab;BackendSwitch=VMSwitch;DirectRoutingMode=True;FrontEndServerAddress=131.107.0.55</codeInline>
              </para>
              <alert class="note">
                <para>Notice the new parameters in this connection string: <codeInline>DirectRoutingMode</codeInline> and <codeInline>FrontEndServerAddress</codeInline>.</para>
              </alert>
            </listItem>
            <listItem>
              <para>Create a VM subnet that is configured for direct routing, using the new forwarding gateway as the gateway device.</para>
              <list class="ordered">
                <listItem>
                  <para>Create separate subnets for each tenant. For example:</para>
                  <para />
                  <mediaLink>
                    <image xlink:href="8157c52f-3ea2-47f7-85c6-d107b572c342" />
                  </mediaLink>
                </listItem>
              </list>
            </listItem>
            <listItem>
              <para>Place tenant virtual machines in their respective subnets.</para>
            </listItem>
            <listItem>
              <para>To isolate the virtual machines, use <externalLink><linkText>extended port access control lists</linkText><linkUri>http://technet.microsoft.com/library/dn375962.aspx</linkUri></externalLink> and run the cmdlets on the VMM host. Configure the ports and protocols required for the tenant virtual machines.</para>
              <para />
              <alert class="important">
                <para>Before running the following cmdlets, you must install the Hyper-V PowerShell module on the VMM host. The PowerShell cmdlet to do that is <codeInline>Install-WindowsFeature hyper-v-powershell</codeInline></para>
              </alert>
              <para>Example:</para>
              <code>$vm = get-scvirtualMachine -Name "<legacyItalic>&lt;computername&gt;</legacyItalic>"
Add-VMNetworkAdapterExtendedAcl -ComputerName $vm.vmhost.fqdn –VMName $vm.Name –Direction in  –Action Allow -Weight 15 -localport 68 -Protocol udp –Stateful $true
Add-VMNetworkAdapterExtendedAcl -ComputerName $vm.vmhost.fqdn -VMName $vm.Name -Direction out -Action allow -Weight 12 -RemotePort 53 -Protocol udp -Stateful $true
Add-VMNetworkAdapterExtendedAcl -ComputerName $vm.vmhost.fqdn -VMName $vm.Name -Direction out -Action allow -Weight 11 -LocalPort 443 -Protocol tcp -Stateful $true
Add-VMNetworkAdapterExtendedAcl -ComputerName $vm.vmhost.fqdn -VMName $vm.Name -Direction out -Action allow -Weight 10 -LocalPort 80 -Protocol tcp -Stateful $true
Add-VMNetworkAdapterExtendedAcl -ComputerName $vm.vmhost.fqdn –VMName $vm.Name –Direction in  –Action Allow -Weight 10 -localport 80 -Protocol tcp –Stateful $true
Add-VMNetworkAdapterExtendedAcl -ComputerName $vm.vmhost.fqdn -VMName $vm.Name -Direction out -Action deny  -Weight 1
Add-VMNetworkAdapterExtendedAcl -ComputerName $vm.vmhost.fqdn -VMName $vm.Name -Direction in  -Action deny  -Weight 1</code>
              <para />
              <para>Example to remove port ACLs from a virtual machine:</para>
              <code>$vm = get-scvirtualMachine -Name "<legacyItalic>&lt;computername&gt;</legacyItalic>"
Get-VMNetworkAdapterExtendedacl -ComputerName $vm.vmhost.fqdn -VMName $vm.Name | Remove-VMNetworkAdapterExtendedAcl</code>
            </listItem>
          </list>
        </content>
      </section>
      <section>
        <title>Troubleshooting tip</title>
        <content>
          <para>If your newly deployed forwarding gateway is not properly forwarding packets to the VM subnet configured for direct routing, double check that you followed the previous procedure correctly. If you are still experiencing problems, check to make sure the frontend interfaces on the forwarding gateway are configured for forwarding. To do this, check the following</para>
          <list class="ordered">
            <listItem>
              <para>Logon to one of the forwarding gateway guest cluster virtual machines.</para>
            </listItem>
            <listItem>
              <para>From a Windows PowerShell administrator command prompt, use <codeInline>Get-NetIPInterface</codeInline> to examine the IP interfaces. Note the <codeInline>ifIndex</codeInline> number for the interface associated with your frontend network. </para>
            </listItem>
            <listItem>
              <para>Use <codeInline>Get-NetIPInterface –InterfaceIndex <legacyItalic>&lt;ifindex for frontend interface&gt;</legacyItalic> | fl</codeInline>, and examine the Forwarding parameter.</para>
            </listItem>
            <listItem>
              <para>If the Forwarding parameter is Disabled, enable it using the following command: <codeInline>Get-NetIPInterface –InterfaceIndex <legacyItalic>&lt;ifindex for frontend interface&gt;</legacyItalic> | Set-NetIpInterface –Forwarding  Enabled</codeInline></para>
            </listItem>
            <listItem>
              <para>Repeat for each node in the forwarding gateway guest cluster.</para>
            </listItem>
            <listItem>
              <para>Repeat your test to verify that the forwarding gateway is properly forwarding packets to the VM network.</para>
            </listItem>
          </list>
        </content>
      </section>
    </sections>
  </section>
  <section>
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
              <para>Product evaluation/getting started</para>
            </TD>
            <TD>
              <para>
                <externalLink>
                  <linkText>Test Lab Guide: Windows Server 2012 R2 Hyper-V Network Virtualization with System Center 2012 R2 VMM</linkText>
                  <linkUri>http://www.microsoft.com/download/details.aspx?id=39284</linkUri>
                </externalLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Planning and design</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="6d06931d-13dd-4063-87b8-f4968d6b7848">Deploy highly scalable tenant network infrastructure for hosting providers: planning and design guide</legacyLink>
              </para>
              <para>
                <externalLink>
                  <linkText>Microsoft System Center: Building a Virtualized Network Solution</linkText>
                  <linkUri>http://blogs.msdn.com/b/microsoft_press/archive/2014/02/18/free-ebook-microsoft-system-center-building-a-virtualized-network-solution.aspx</linkUri>
                </externalLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Reference</para>
            </TD>
            <TD>
              <para />
              <list class="bullet">
                <listItem>
                  <para>
                    <externalLink>
                      <linkText>Hyper-V Network Virtualization Overview</linkText>
                      <linkUri>http://technet.microsoft.com/library/jj134230.aspx</linkUri>
                    </externalLink>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <externalLink>
                      <linkText>Network Virtualization technical details</linkText>
                      <linkUri>http://technet.microsoft.com/library/jj134174.aspx</linkUri>
                    </externalLink>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <externalLink>
                      <linkText>Hyper-V Network Virtualization Gateway Architectural Guide</linkText>
                      <linkUri>http://technet.microsoft.com/library/jj618319.aspx</linkUri>
                    </externalLink>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <externalLink>
                      <linkText>Adopting Network Virtualization – Part I</linkText>
                      <linkUri>http://blogs.technet.com/b/scvmm/archive/2013/11/25/adopting-network-virtualization-part-i.aspx</linkUri>
                    </externalLink>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <externalLink>
                      <linkText>Adopting Network Virtualization – Part II</linkText>
                      <linkUri>http://blogs.technet.com/b/scvmm/archive/2013/11/27/adopting-network-virtualization-part-ii.aspx</linkUri>
                    </externalLink>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <externalLink>
                      <linkText>Adopting Network Virtualization - Part III</linkText>
                      <linkUri>http://blogs.technet.com/b/scvmm/archive/2013/12/05/adopting-network-virtualization-part-iii.aspx</linkUri>
                    </externalLink>
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
                      <linkText>Networking Blog</linkText>
                      <linkUri>http://blogs.technet.com/b/networking/</linkUri>
                    </externalLink>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <externalLink>
                      <linkText>What’s New in 2012 R2: Hybrid Networking</linkText>
                      <linkUri>http://blogs.technet.com/b/in_the_cloud/archive/2013/08/14/what-s-new-in-2012-r2-hybrid-networking.aspx</linkUri>
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
                    <link xlink:href="3314f967-8a2c-48c6-bfc7-3137cc30a075">Provide cost-effective storage for Hyper-V workloads by using Windows Server: planning and design guide</link>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <link xlink:href="e70fcb94-0576-4582-a1e0-8c41f8d745cc">Provide cost-effective storage for Hyper-V workloads by using Windows Server</link>
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
                    <externalLink>
                      <linkText>Network Virtualization using Generic Routing Encapsulation</linkText>
                      <linkUri>http://tools.ietf.org/html/draft-sridharan-virtualization-nvgre-00</linkUri>
                    </externalLink>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <legacyLink xlink:href="0e27c024-36f7-4a36-8987-5590f13a45e2">IP Address Management (IPAM) Overview</legacyLink>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <externalLink>
                      <linkText>Virtual Machine Manager</linkText>
                      <linkUri>http://technet.microsoft.com/library/gg610610.aspx</linkUri>
                    </externalLink>
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
                    <legacyLink xlink:href="6eeffe4f-3558-495b-bcea-c640fe4d6c49">Failover Clustering Overview [Role/Tech Overview]</legacyLink>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <externalLink>
                      <linkText>Border Gateway Protocol (BGP) with Windows Server 2012 R2</linkText>
                      <linkUri>http://blogs.technet.com/b/networking/archive/2013/10/11/border-gateway-protocol-bgp-with-windows-server-2012-r2.aspx</linkUri>
                    </externalLink>
                  </para>
                </listItem>
              </list>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics />
</developerConceptualDocument>