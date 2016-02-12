---
title: Virtualization Fabric Design Considerations Guide
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0a72c21e-9430-4b2c-a53b-87f23cf85c00
---
# Virtualization Fabric Design Considerations Guide
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>
      <embeddedLabel>Who is this guide intended for?</embeddedLabel> Information technology (IT) professionals within medium to large organizations who are responsible for designing a virtualization fabric that supports many virtual machines. Through the remainder of this document, these individuals are referred to as <placeholder>fabric administrators</placeholder>. People who administer virtual machines hosted on the fabric are referred to as virtual machine administrators, but they are not a target audience for this document. Within your organization, you may have the responsibility of both roles.</para>
    <para>
      <embeddedLabel>How can this guide help you?</embeddedLabel> You can use this guide to understand how to design a virtualization fabric that is able to host many virtual machines in your organization. In this document, the collection of servers and hypervisors, and the storage and networking hardware that are used to host the virtual machines within an organization is referred to as a <placeholder>virtualization fabric</placeholder>. The following graphic shows an example virtualization fabric.</para>
    <mediaLink>
      <image xlink:href="9ae94fbe-07e9-486c-9c20-fc9fe439b066"/>
    </mediaLink>
    <para>
      <embeddedLabel>Figure  SEQ Figure \* ARABIC 1:</embeddedLabel> <externalLink><linkText>Example virtualization fabric</linkText><linkUri>http://aka.ms/Tdxs0r</linkUri></externalLink></para>
    <para>
      <embeddedLabel>Note:</embeddedLabel> Each diagram in this document exists on a separate tab of the <externalLink><linkText>Virtualization Fabric Design Considerations Diagrams</linkText><linkUri>http://aka.ms/Tdxs0r</linkUri></externalLink> document, which you can download by clicking the figure name in each table caption.</para>
    <para>Although all virtualization fabrics contain servers for storage and hosting virtual machines, in addition to the networks that connect them, every organization’s virtualization fabric design will likely be different than the example illustrated in Figure 1 due to different requirements. </para>
    <para>This guide details a series of steps and tasks that you can follow to assist you in designing a virtualization fabric that meets your organization’s unique requirements. Throughout the steps and tasks, the guide presents the relevant technologies and feature options available to you to meet functional and service quality (such as availability, scalability, performance, manageability, and security) level requirements.</para>
    <para>Though this document can help you design a manageable virtualization fabric, it does not discuss design considerations and options for managing and operating the virtualization fabric with a product such as Microsoft System Center 2012 or System Center 2012 R2. For more information, see <externalLink><linkText>System Center 2012</linkText><linkUri>http://technet.microsoft.com/library/hh546785.aspx</linkUri></externalLink> in the TechNet library.</para>
    <para>This guide helps you design a virtualization fabric by using <externalLink><linkText>Windows Server 2012 R2 and Windows Server 2012</linkText><linkUri>http://technet.microsoft.com/library/hh801901.aspx</linkUri></externalLink> and vendor-agnostic hardware. Some features discussed in the document are unique to Windows Server 2012 R2, and they are called out throughout the document.</para>
    <para>
      <embeddedLabel>Assumptions:</embeddedLabel> You have some experience deploying Hyper-V, virtual machines, virtual networks, Windows Server file services, and Failover Clustering, and some experience deploying physical servers, storage, and network equipment. </para>
    <para>
      <embeddedLabel>
        <placeholder>Additional resources</placeholder>
      </embeddedLabel>
    </para>
    <para>Before designing a virtualization fabric, you may find the information in the following documents helpful:</para>
    <list class="bullet">
      <listItem>
        <para>
          <externalLink>
            <linkText>Microsoft Cloud Services Foundation Reference Architecture – Reference Model</linkText>
            <linkUri>http://blogs.technet.com/b/cloudsolutions/archive/2013/08/15/cloud-services-foundation-reference-architecture-reference-model.aspx</linkUri>
          </externalLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <externalLink>
            <linkText>Microsoft Cloud Services Foundation Reference Architecture – Principles, Concepts, and Patterns</linkText>
            <linkUri>http://blogs.technet.com/b/cloudsolutions/archive/2013/08/15/cloud-services-foundation-reference-architecture-principles-concepts-and-patterns.aspx</linkUri>
          </externalLink>
        </para>
      </listItem>
    </list>
    <para>Both of these documents provide foundational concepts that are observed across multiple virtualization fabric designs and can serve as a basis for any virtualization fabric design.</para>
    <para>
      <embeddedLabel>Feedback:</embeddedLabel> To provide feedback about this document, send e-mail to <externalLink><linkText>virtua@microsoft.com</linkText><linkUri>mailto:virtua@microsoft.com</linkUri></externalLink>.</para>
  <table border="1"><tbody><tr><TD><mediaLink>
<image xlink:href="0cb7e04f-96fb-461a-bcdf-9763335d2d07"/>
</mediaLink></TD><TD><para>Did you know that Microsoft Azure provides similar functionality in the cloud? Learn more about <externalLink><linkText>Microsoft Azure virtualization solutions</linkText><linkUri>http://aka.ms/f9bh7g</linkUri></externalLink>.</para><para>Create a hybrid virtualization solution in Microsoft Azure:
 
<br/>- <externalLink><linkText>Move VM’s between Hyper-V and Microsoft Azure</linkText><linkUri>http://aka.ms/vf75zq</linkUri></externalLink></para></TD></tr></tbody></table></introduction>
  <section>
    <title>Design considerations overview</title>
    <content>
      <para>The remainder of this document provides a set of steps and tasks that you can follow to design a virtualization fabric that best meets your requirements. The steps are presented in an ordered sequence. Design considerations you learn in later steps may require you to change decisions you made in earlier steps however, due to conflicts. Every attempt is made to alert you to potential design conflicts throughout the document though. </para>
      <para>You will arrive at the design that best meets your requirements only after iterating through the steps as many times as necessary to incorporate all of the considerations within the document. </para>
      <para>
        <link xlink:href="0a72c21e-9430-4b2c-a53b-87f23cf85c00#BKMK_Step1">Step 1: Determine virtual machine resource requirements</link>
      </para>
      <para>
        <link xlink:href="0a72c21e-9430-4b2c-a53b-87f23cf85c00#BKMK_Step2">Step 2: Plan for virtual machine configuration</link>
      </para>
      <para>
        <link xlink:href="0a72c21e-9430-4b2c-a53b-87f23cf85c00#BKMK_Step3">Step 3: Plan for server virtualization host groups</link>
      </para>
      <para>
        <link xlink:href="0a72c21e-9430-4b2c-a53b-87f23cf85c00#BKMK_Step4">Step 4: Plan for server virtualization hosts</link>
      </para>
      <para>
        <link xlink:href="0a72c21e-9430-4b2c-a53b-87f23cf85c00#BKMK_Step5">Step 5: Plan for virtualization fabric architecture concepts</link>
      </para>
      <para>
        <link xlink:href="0a72c21e-9430-4b2c-a53b-87f23cf85c00#BKMK_Step6">Step 6: Plan for initial capability characteristics</link>
      </para>
    </content>
  </section>
  <section address="BKMK_Step1">
    <title>Step 1: Determine virtual machine resource requirements</title>
    <content>
      <para>The first step in designing a virtualization fabric is to determine the resource requirements of the virtual machines that the fabric will host. The fabric must include the physical hardware necessary to meet those requirements. The virtual machine resource requirements are dictated by the operating systems and applications that run within the virtual machines. For the remainder of this document, the combination of the operating system and applications that run within a virtual machine is referred to as a workload. The tasks in this step help you define the resource requirements for your workloads.</para>
      <para>
        <embeddedLabel>Tip:</embeddedLabel> Rather than assessing the resource requirements of your existing workloads and then designing a virtualization fabric that is able to support each of them, you may decide to design a virtualization fabric that can meet the needs of most common workloads instead. Then separately address the workloads that have unique needs. </para>
      <para>Examples of such virtualization fabrics are those offered by public cloud providers, such as Microsoft Azure (Azure). For more information, see <externalLink><linkText>Virtual Machine and Cloud Service Sizes for Azure</linkText><linkUri>http://msdn.microsoft.com/library/azure/dn197896.aspx</linkUri></externalLink>. </para>
      <para>Public cloud providers typically offer a selection of virtual machine configurations that meet the needs of most workloads. If you decide to take this approach, you can skip directly to <link xlink:href="0a72c21e-9430-4b2c-a53b-87f23cf85c00#BKMK_Step2">Step 2, Task 5</link> in this document. Additional benefits to using this approach are:</para>
      <list class="bullet">
        <listItem>
          <para>When you decide to migrate some of your on-premises virtual machines to a public cloud provider, if your on-premises virtual machine configuration types are similar to those of your public provider, migrating the virtual machines will be easier than if the configuration types are different.</para>
        </listItem>
        <listItem>
          <para>It may allow you to more easily forecast capacity requirements and enable a self-service provisioning capability for your virtualization fabric. This means that virtual machine administrators within the organization can automatically self-provision new virtual machines without involvement from the fabric administrators.</para>
        </listItem>
      </list>
    </content>
    <sections>
      <section>
        <title>Task 1: Determine workload resource requirements</title>
        <content>
          <para>Each workload has requirements for the following resources. The first thing you’ll want to do is answer the following questions listed for each of your workloads.</para>
          <list class="bullet">
            <listItem>
              <para>
                <embeddedLabel>Processor:</embeddedLabel> What processor speed or architecture (Intel or AMD) or number of processors are required?</para>
            </listItem>
            <listItem>
              <para>
                <embeddedLabel>Network:</embeddedLabel> In gigabits per second (Gbps), what network bandwidth is required for inbound and outbound traffic? What’s the maximum amount of network latency the workload can tolerate to function properly? </para>
            </listItem>
            <listItem>
              <para>
                <embeddedLabel>Storage:</embeddedLabel> How many gigabytes (GB) of storage do the application and operating system files of the workload require? How many GBs of storage does the workload require for its data? How many input/output operations per second (IOPS) does the workload require to its storage? </para>
            </listItem>
            <listItem>
              <para>
                <embeddedLabel>Memory:</embeddedLabel> In gigabytes (GB), how much memory does the workload require? Is the workload non-uniform memory access (NUMA) aware?</para>
            </listItem>
          </list>
          <para>In addition to understanding the previous resource requirements, it’s important to also determine:</para>
          <list class="bullet">
            <listItem>
              <para>Whether the resource requirements are minimum or recommended.</para>
            </listItem>
            <listItem>
              <para>What are the peak and average requirement for each of the hardware requirements on an hourly, daily, weekly, monthly, or annual basis.</para>
            </listItem>
            <listItem>
              <para>The number of minutes of downtime per month that are acceptable for the workload and the workload’s data. In determining this, factor in the following:</para>
              <list class="bullet">
                <listItem>
                  <para>Does the workload run on only one virtual machine, or does it run on a collection of virtual machines acting as one, such as a collection of network load-balanced servers all running the same workload? If you are using a collection of servers, the expressed downtime should be clear about whether it applies to each server in the collection, all servers in the collection, or at the collection level.</para>
                </listItem>
                <listItem>
                  <para>Working and non-working hours. For example, if nobody will use the workload between the hours of 9:00 P.M. and 6:00 A.M., but it’s critical that it is available as much as possible between the hours of 6:00 A.M. and 9:00 P.M., with an acceptable amount of downtime per month of only ten minutes, this requirement should be specified.</para>
                </listItem>
              </list>
            </listItem>
            <listItem>
              <para>The amount of data loss that is acceptable in the event of an unexpected failure of the virtual infrastructure. This is expressed in minutes because virtual infrastructure replication strategies are typically time-based. Although no data loss is often expressed as a requirement, consider that achieving it often comes at a premium price, and it might also come with lower performance.</para>
            </listItem>
            <listItem>
              <para>Whether the workload files and/or its data must be encrypted on disk and whether its data must be encrypted between the virtual machines and its end users.</para>
            </listItem>
          </list>
          <para>You have the following options available for determining the previous resource requirements.</para>
          <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
            <thead>
              <tr>
                <TD>
                  <para>Option</para>
                </TD>
                <TD>
                  <para>Advantages</para>
                </TD>
                <TD>
                  <para>Disadvantages</para>
                </TD>
              </tr>
            </thead>
            <tbody>
              <tr>
                <TD>
                  <para>Manually assess and log resource utilization</para>
                </TD>
                <TD>
                  <para>Able to report on whatever you choose</para>
                </TD>
                <TD>
                  <para>Can require significant manual effort</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>Use the <externalLink><linkText>Microsoft Assessment and Planning Toolkit</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=389047</linkUri></externalLink> to automatically assess and log resource utilization</para>
                </TD>
                <TD>
                  <list class="bullet">
                    <listItem>
                      <para>Creates a variety of resource utilization reports</para>
                    </listItem>
                    <listItem>
                      <para>Doesn’t require an agent to be installed on the workload</para>
                    </listItem>
                  </list>
                </TD>
                <TD>
                  <para>Reports may or may not provide all the data you require</para>
                </TD>
              </tr>
            </tbody>
          </table>
          <para/>
          <para>
            <embeddedLabel>Note:</embeddedLabel> If you choose to determine your resource requirements manually, you can download <externalLink><linkText>Virtualization Fabric Design Considerations Guide Worksheets</linkText><linkUri>http://aka.ms/P0anp3</linkUri></externalLink> and enter the information in the Workload resource req. worksheet. This guide references specific worksheets in that document.</para>
        </content>
      </section>
      <section>
        <title>Task 2: Define workload characterizations</title>
        <content>
          <para>You can define any number of workload characterizations in your environment. The following examples were selected because each of them requires a different configuration of virtualization fabric components, which will be discussed further in later steps.</para>
          <list class="bullet">
            <listItem>
              <para>
                <embeddedLabel>Stateless:</embeddedLabel> Write no unique information to their local hard disk after they’re initially provisioned and assigned unique computer names and network addresses. They may however, write unique information to separate storage, such as a database. Stateless workloads are optimal for running on a virtualization fabric because a “master” image can be created for the virtual machine. This image can be easily copied and booted on the virtualization fabric to add scale to the workload or to quickly replace a virtual machine that becomes unavailable in the event of a virtualization host failure. An example of a stateless workload is a web server running a front-end web application.</para>
            </listItem>
            <listItem>
              <para>
                <embeddedLabel>Stateful:</embeddedLabel> Write unique information to their local hard disk after they’re initially provisioned and assigned unique computer names and network addresses. They may also write unique information to separate storage, such as a database. Stateful workloads typically require more complex provisioning and scaling strategies than stateless workloads. High availability strategies for stateful workloads might require shared state with other virtual machines. An example of a stateful workload is the SQL Server Database Engine.</para>
            </listItem>
            <listItem>
              <para>
                <embeddedLabel>Shared stateful:</embeddedLabel> Stateful workloads that require some shared state with other virtual machines. These workloads often use Failover Clustering in Windows Server to achieve high availability, which requires access to shared storage. An example of a shared stateful workload is Microsoft System Center – Virtual Machine Manager. </para>
            </listItem>
            <listItem>
              <para>
                <embeddedLabel>Other:</embeddedLabel> Characterizes workloads that may not run at all, or not run optimally, on a virtualization fabric. Attributes of such workloads are that they require:</para>
              <list class="bullet">
                <listItem>
                  <para>Access to physical peripherals. An example of such an application is a telephony workload that communicates with a telephony network adapter in a physical host.</para>
                </listItem>
                <listItem>
                  <para>Resource requirements much higher than most of your other workloads. An example is a real-time application that requires less than one millisecond latency between application tiers. </para>
                </listItem>
              </list>
              <para>These applications may or may not run on your virtualization fabric, or they may require very specific hardware or configuration that is not shared by most of your other workloads.</para>
            </listItem>
          </list>
          <para>
            <embeddedLabel>Note:</embeddedLabel> You can define your workload characterizations in the <externalLink><linkText>Settings</linkText><linkUri>http://aka.ms/P0anp3</linkUri></externalLink> worksheet and then select the appropriate characterization for each workload in the <externalLink><linkText>Workload resource req.</linkText><linkUri>http://aka.ms/P0anp3</linkUri></externalLink> worksheet.</para>
        </content>
      </section>
    </sections>
  </section>
  <section address="BKMK_Step2">
    <title>Step 2: Plan for virtual machine configuration</title>
    <content>
      <para>In this step, you’ll define the types of virtual machines you’ll need to meet the resource requirements and characterizations of the workloads you defined in Step 1.</para>
    </content>
    <sections>
      <section>
        <title>Task 1: Define compute configuration</title>
        <content>
          <para>In this task, you’ll determine the amount of memory and processors that each virtual machine requires. </para>
        </content>
        <sections>
          <section>
            <title>Task 1a: Define virtual machine generation type</title>
            <content>
              <para>Windows Server 2012 R2 introduced generation 2 virtual machines. Generation 2 virtual machines support hardware and virtualization features that are not supported in generation 1 virtual machines. It’s important to make the right decision for your requirements, because after a virtual machine has been created, its type cannot be changed. </para>
              <para>A generation 2 virtual machine provides the following new functionality: </para>
              <list class="bullet">
                <listItem>
                  <para>PXE boot by using a standard network adapter</para>
                </listItem>
                <listItem>
                  <para>Boot from a SCSI virtual hard disk</para>
                </listItem>
                <listItem>
                  <para>Boot from a SCSI virtual DVD</para>
                </listItem>
                <listItem>
                  <para>Secure Boot (enabled by default) </para>
                </listItem>
                <listItem>
                  <para>UEFI firmware support </para>
                </listItem>
              </list>
              <para>Generation 2 virtual machines support the following guest operating systems:</para>
              <list class="bullet">
                <listItem>
                  <para>Windows Server 2012 R2 </para>
                </listItem>
                <listItem>
                  <para>Windows Server 2012 </para>
                </listItem>
                <listItem>
                  <para>64-bit versions of Windows 8.1</para>
                </listItem>
                <listItem>
                  <para>64-bit versions of Windows 8</para>
                </listItem>
                <listItem>
                  <para>Specific versions of Linux. For a list of distribution and versions that support generation 2 virtual machines, see <externalLink><linkText>Linux Virtual Machines on Hyper-V</linkText><linkUri>http://technet.microsoft.com/library/dn531030.aspx</linkUri></externalLink>.</para>
                </listItem>
              </list>
              <para>The following table lists the advantages and disadvantages of generation 1 and generation 2 virtual machines. </para>
              <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
                <thead>
                  <tr>
                    <TD>
                      <para>Option</para>
                    </TD>
                    <TD>
                      <para>Advantages</para>
                    </TD>
                    <TD>
                      <para>Disadvantages</para>
                    </TD>
                  </tr>
                </thead>
                <tbody>
                  <tr>
                    <TD>
                      <para>Generation 1</para>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Supports all supported Hyper-V guest operating systems</para>
                        </listItem>
                        <listItem>
                          <para>Provides compatibility with Azure virtual machines</para>
                        </listItem>
                        <listItem>
                          <para>Supports previous versions of Hyper-V</para>
                        </listItem>
                      </list>
                    </TD>
                    <TD>
                      <para>No access to new virtual machine functionality</para>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>Generation 2</para>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Supports new functionality</para>
                        </listItem>
                        <listItem>
                          <para>Provides slight improvement in virtual machine boot and guest installation times</para>
                        </listItem>
                        <listItem>
                          <para>Uses SCSI devices or a standard network adapter to boot a virtual machine</para>
                        </listItem>
                        <listItem>
                          <para>Prevents unauthorized firmware, operating systems, or UEFI drivers from running when Secure Boot is enabled</para>
                        </listItem>
                      </list>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Limited support for guest operating systems</para>
                        </listItem>
                        <listItem>
                          <para>Not compatible with Azure virtual machines </para>
                        </listItem>
                        <listItem>
                          <para>No support for RemoteFX </para>
                        </listItem>
                        <listItem>
                          <para>No support for virtual floppy disk </para>
                        </listItem>
                      </list>
                    </TD>
                  </tr>
                </tbody>
              </table>
              <para/>
              <para>
                <embeddedLabel>Important:</embeddedLabel> Linux generation 2 virtual machines do not support Secure Boot. When you create a virtual machine and you intend to install Linux, you must turn off Secure Boot in the virtual machine settings. </para>
              <para>
                <embeddedLabel>Additional information:</embeddedLabel>
              </para>
              <para>
                <externalLink>
                  <linkText>Generation 2 Virtual Machine Overview</linkText>
                  <linkUri>http://technet.microsoft.com/library/dn282285.aspx</linkUri>
                </externalLink>
              </para>
            </content>
          </section>
          <section address="BKMK_Step2Task1b">
            <title>Task 1b: Define memory</title>
            <content>
              <para>You should plan the size of your virtual machine memory as you typically do for server applications on a physical computer. It should reasonably handle the expected load at ordinary times and at peak times. Insufficient memory can significantly increase response times and CPU or I/O usage. </para>
              <para>
                <embeddedLabel>
                  <placeholder>Static Memory or Dynamic Memory</placeholder>
                </embeddedLabel>
              </para>
              <para>
                <embeddedLabel>Static memory</embeddedLabel> is the amount of memory assigned to the virtual machine. It is always allocated when the virtual machine is started and it does not change when the virtual machine is running. All of the memory is assigned to the virtual machine during startup and memory that is not being used by the virtual machine is not available to other virtual machines. If there is not enough memory available on the host to allocate to the virtual machine when it is started, the virtual machine will not start. </para>
              <para>Static memory is good for workloads that are memory intensive and for workloads that have their own memory management systems, such as SQL Server. These types of workloads will perform better with static memory.</para>
              <para>
                <embeddedLabel>Note:</embeddedLabel> There is no setting to enable static memory. Static memory is enabled when the Dynamic Memory setting is not enabled. </para>
              <para>
                <embeddedLabel>Dynamic Memory</embeddedLabel> allows you to better use the physical memory on a system by balancing the total physical memory across multiple virtual machines, allocating more memory to virtual machines that are busy, and removing memory for less-used virtual machines. This can lead to higher consolidation ratios, especially in dynamic environments such as in the Virtual Desktop Infrastructure (VDI) or web servers.</para>
              <para>When using static memory, if a virtual machine is assigned 10 GB of memory and it is only using 3 GB, the remaining 7 GB of memory is not available for use by other virtual machines. When a virtual machine has Dynamic Memory enabled, the virtual machine only uses the amount of memory that is required, but not below the minimum RAM that is configured. This frees up more memory for other virtual machines. </para>
              <para>The following table lists the advantages and disadvantages for static memory and Dynamic Memory.</para>
              <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
                <thead>
                  <tr>
                    <TD>
                      <para>Option</para>
                    </TD>
                    <TD>
                      <para>Advantages</para>
                    </TD>
                    <TD>
                      <para>Disadvantages</para>
                    </TD>
                  </tr>
                </thead>
                <tbody>
                  <tr>
                    <TD>
                      <para>Static memory</para>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Provides virtual machines with available configured memory at all times</para>
                        </listItem>
                        <listItem>
                          <para>Provides better performance</para>
                        </listItem>
                        <listItem>
                          <para>Can be used with virtual NUMA</para>
                        </listItem>
                      </list>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Memory not being used by a virtual machine cannot be allocated to another virtual machine.</para>
                        </listItem>
                        <listItem>
                          <para>Virtual machines will not start if there is not enough memory available.</para>
                        </listItem>
                      </list>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>Dynamic Memory</para>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Provides improved virtual machine density when running idle or low load workloads </para>
                        </listItem>
                        <listItem>
                          <para>Allows allocating memory that is not being used so that it can be used by other virtual machines</para>
                        </listItem>
                      </list>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>You can oversubscribe the configured memory. </para>
                        </listItem>
                        <listItem>
                          <para>Additional overhead is required to manage memory allocations. </para>
                        </listItem>
                        <listItem>
                          <para>Not compatible with virtual NUMA.</para>
                        </listItem>
                        <listItem>
                          <para>Not compatible with workloads that implement their own memory managers.</para>
                        </listItem>
                      </list>
                    </TD>
                  </tr>
                </tbody>
              </table>
              <para/>
              <para>The following are the memory configuration settings: </para>
              <list class="bullet">
                <listItem>
                  <para>
                    <embeddedLabel>Startup RAM:</embeddedLabel> Specifies the amount of memory required to start the virtual machine. The value needs to be high enough to allow the guest operating system to start, but should be as low as possible to allow for optimal memory utilization and potentially higher consolidation ratios. </para>
                </listItem>
                <listItem>
                  <para>
                    <embeddedLabel>Minimum RAM:</embeddedLabel> Specifies the minimum amount of memory that should be allocated to the virtual machine after the virtual machine has started. The value can be set as low as 32 MB to a maximum value equal to the Startup RAM value. This setting is only available when Dynamic Memory is enabled.</para>
                </listItem>
                <listItem>
                  <para>
                    <embeddedLabel>Maximum RAM:</embeddedLabel> Specifies the maximum amount of memory that this virtual machine is allowed to use. The value can be set from as low as the value for Startup RAM to as high as 1 TB. However, a virtual machine can use only as much memory as the maximum amount supported by the guest operating system. For example, if you specify 64 GB for a virtual machine running a guest operating system that supports a maximum of 32 GB, the virtual machine cannot use more than 32 GB. This setting is only available when Dynamic Memory is enabled. </para>
                </listItem>
                <listItem>
                  <para>
                    <embeddedLabel>Memory weight:</embeddedLabel> Provides Hyper-V with a way to determine how to distribute memory among virtual machines if there is not enough physical memory available in the host to give every virtual machine its requested amount of memory. Virtual machines with a higher memory weight take precedence over virtual machines with lower memory weights.</para>
                </listItem>
              </list>
              <para>
                <embeddedLabel>Notes:</embeddedLabel>
              </para>
              <list class="bullet">
                <listItem>
                  <para>Dynamic Memory and virtual NUMA features cannot be used at the same time. A virtual machine that has Dynamic Memory enabled effectively has only one virtual NUMA node, and no NUMA topology is presented to the virtual machine regardless of the virtual NUMA settings. </para>
                </listItem>
                <listItem>
                  <para>When installing or upgrading the operating system of a virtual machine, the amount of memory that is available to the virtual machine during the installation and upgrade process is the value specified as Startup RAM. Even if Dynamic Memory has been configured for the virtual machine, the virtual machine only uses the amount of memory that is configured in the Startup RAM setting. Ensure that the Startup RAM value meets the minimum memory requirements of the operating system during the installation or upgrade procedures. </para>
                </listItem>
                <listItem>
                  <para>Guest operating system running in the virtual machine must support Dynamic Memory. </para>
                </listItem>
                <listItem>
                  <para>Complicated database applications like SQL Server or Exchange Server implement their own memory managers. Consult with workload’s documentation to determine if the workload is compatible with Dynamic Memory.</para>
                </listItem>
              </list>
              <para>
                <embeddedLabel>Additional information:</embeddedLabel> </para>
              <para>
                <externalLink>
                  <linkText>Dynamic Memory Overview</linkText>
                  <linkUri>http://technet.microsoft.com/library/hh831766.aspx</linkUri>
                </externalLink>
              </para>
            </content>
          </section>
          <section>
            <title>Task 1c: Define processor</title>
            <content>
              <para>The following configuration settings must be determined for configuring virtual machines: </para>
              <list class="bullet">
                <listItem>
                  <para>Determine the number of processors required for each virtual machine. This will often be the same as the number of processors required by the workload. Hyper-V supports a maximum of 64 virtual processors per virtual machine.</para>
                </listItem>
                <listItem>
                  <para>Determine resource control for each virtual machine. Limits can be set to ensure that no virtual machine is able to monopolize the processor resources of the virtualization host.</para>
                </listItem>
                <listItem>
                  <para>Define a NUMA topology. For high-performance NUMA-aware workloads, you can specify the maximum number of processors, the memory amount allowed on a single virtual NUMA node, and the maximum number of nodes allowed on a single processor socket. For more information, read <externalLink><linkText>Hyper-V Virtual NUMA Overview</linkText><linkUri>http://technet.microsoft.com/library/dn282282.aspx#BKMK_VM_Settings</linkUri></externalLink>.</para>
                </listItem>
              </list>
              <para>
                <embeddedLabel>Note:</embeddedLabel> Virtual NUMA and Dynamic Memory cannot be used at the same. When you are trying to decide whether to use Dynamic Memory or NUMA, answer the following questions. If the answer to both is Yes, enable virtual NUMA and do not enable Dynamic Memory.</para>
              <list class="ordered">
                <listItem>
                  <para>Is the workload running in the virtual machine NUMA-aware?</para>
                </listItem>
                <listItem>
                  <para>Will the virtual machine consume more resources, processors, or memory than are available on a single physical NUMA node?</para>
                </listItem>
              </list>
              <para/>
            </content>
          </section>
          <section>
            <title>Task 1d: Define supported operating systems</title>
            <content>
              <para>You need to confirm that the operating system required by your workload is supported as a guest operating system. Consider the following:</para>
              <list class="bullet">
                <listItem>
                  <para>
                    <legacyLink xlink:href="0a3a974c-1714-47c8-88ca-8c1124dda369">Supported Windows Guest Operating Systems for Hyper-V in Windows Server 2012 R2 and Windows 8.1</legacyLink>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <legacyLink xlink:href="91958199-798d-4ac5-a019-3ed95c0cd2b8">Supported Windows Guest Operating Systems for Hyper-V in Windows Server 2012 and Windows 8</legacyLink>
                  </para>
                </listItem>
                <listItem>
                  <para>For Linux: For information about supported Linux distributions, see <externalLink><linkText>Linux Virtual Machines on Hyper-V</linkText><linkUri>http://technet.microsoft.com/library/dn531030.aspx</linkUri></externalLink>. </para>
                </listItem>
              </list>
              <para>
                <embeddedLabel>Note:</embeddedLabel> Hyper-V includes a software package for supported guest operating systems that improves performance and integration between the physical computer and the virtual machine. This collection of services and software drivers is referred to as integration services. For the best performance, your virtual machines should be running the latest integration services. </para>
              <para>
                <embeddedLabel>
                  <placeholder>Licensing</placeholder>
                </embeddedLabel>
              </para>
              <para>You need to ensure that the guest operating systems are properly licensed. Please review the vendor’s documentation for any specific licensing requirements when you are running a virtualized environment. </para>
              <para>Automatic Virtual Machine Activation (AVMA) is a feature that was introduced in Windows Server 2012 R2. AVMA binds the virtual machine activation to the licensed virtualization server and activates the virtual machine when it starts up. This eliminates the need to enter licensing information and activate each virtual machine individually. </para>
              <para>AVMA requires that the host is running Windows Server 2012 R2 Datacenter and that the guest virtual machine operating system is Windows Server 2012 R2 Datacenter, Windows Server 2012 R2 Standard, or Windows Server 2012 R2 Essentials.</para>
              <para>
                <embeddedLabel>Note:</embeddedLabel> You need to configure AVMA on each host deployed in your virtualization fabric. </para>
              <para>
                <embeddedLabel>Additional information:</embeddedLabel>
              </para>
              <para>
                <externalLink>
                  <linkText>Automatic Virtual Machine Activation</linkText>
                  <linkUri>http://technet.microsoft.com/library/dn303421.aspx</linkUri>
                </externalLink>
              </para>
            </content>
          </section>
          <section>
            <title>Task 1e: Define virtual machine naming convention</title>
            <content>
              <para>Your existing computer naming strategy might indicate where the computer or server is physically located. Virtual machines can move from host to host, even to and from different datacenters, so the existing naming strategy might no longer be applicable. An update to the existing naming convention to indicate that the computer is running as a virtual machine can help locate where the virtual machine is running. </para>
            </content>
          </section>
        </sections>
      </section>
      <section>
        <title>Task 2: Define network configuration</title>
        <content>
          <para>Each virtual machine will receive or send different types of network traffic. Each type of network traffic will have different performance, availability, and security requirements. </para>
          <para>Generation 1 virtual machines can have a maximum of 12 network adapters—4 legacy network adapters and 8 virtual network adapters. Generation 2 virtual machines do not support legacy network adapters, so the maximum number of adapters that is supported is 8. </para>
        </content>
        <sections>
          <section>
            <title>Task 2a: Determine network traffic types</title>
            <content>
              <para>Each virtual machine will send and receive different types of data, such as:</para>
              <list class="bullet">
                <listItem>
                  <para>Application data</para>
                </listItem>
                <listItem>
                  <para>Data backup</para>
                </listItem>
                <listItem>
                  <para>Communications with client computers, servers, or services</para>
                </listItem>
                <listItem>
                  <para>Intracluster communication, if the workload is part of a guest virtual machine failover cluster</para>
                </listItem>
                <listItem>
                  <para>Support </para>
                </listItem>
                <listItem>
                  <para>Storage</para>
                </listItem>
              </list>
              <para>If you already have existing networks that are dedicated to different types of network traffic, you may choose to use those for this task. If you’re defining new network designs to support your virtualization fabric, for each virtual machine, you can define which types of network traffic it will support. </para>
            </content>
          </section>
          <section address="BKMK_Step2Task2b">
            <title>Task 2b: Define network traffic performance options</title>
            <content>
              <para>Each network traffic type has maximum bandwidth and minimum latency requirements. The following table shows the strategies that can be used to meet different network performance requirements.</para>
              <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
                <thead>
                  <tr>
                    <TD>
                      <para>Strategy</para>
                    </TD>
                    <TD>
                      <para>Advantages</para>
                    </TD>
                    <TD>
                      <para>Disadvantages</para>
                    </TD>
                  </tr>
                </thead>
                <tbody>
                  <tr>
                    <TD>
                      <para>Separation of traffic types to different physical network adapters</para>
                    </TD>
                    <TD>
                      <para>Separates traffic so it is not being shared by other traffic types </para>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Separate physical network adapters must be installed on the host for each network traffic type. </para>
                        </listItem>
                        <listItem>
                          <para>Additional hardware is required for each network that requires network high availability. </para>
                        </listItem>
                        <listItem>
                          <para>Does not scale well with a large number of networks.</para>
                        </listItem>
                      </list>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>Hyper-V bandwidth management (<externalLink><linkText>Hyper-V QoS</linkText><linkUri>http://technet.microsoft.com/library/hh831679.aspx</linkUri></externalLink>)</para>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Provides QoS for virtual network traffic</para>
                        </listItem>
                        <listItem>
                          <para>Enforce minimum bandwidth and maximum bandwidth for a traffic flow, which is identified by a Hyper-V Virtual Switch port number.</para>
                        </listItem>
                        <listItem>
                          <para>Configure minimum bandwidth and maximum bandwidth per Hyper-V virtual switch port by using either PowerShell cmdlets or Windows Management Instrumentation (WMI).</para>
                        </listItem>
                        <listItem>
                          <para>Configure multiple virtual network adapters in Hyper-V and specify QoS on each virtual network adapter individually.</para>
                        </listItem>
                        <listItem>
                          <para>Provides a supplement to QoS policy for the physical network.</para>
                        </listItem>
                      </list>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Software QoS and hardware QoS should not be used at the same time on the same network adapter.</para>
                        </listItem>
                        <listItem>
                          <para>You need to properly plan QoS policy for the network and Hyper-V so they do not override each other. </para>
                        </listItem>
                        <listItem>
                          <para>When you set the mode for quality of service for a virtual switch, it cannot be changed. </para>
                        </listItem>
                        <listItem>
                          <para>You cannot migrate virtual machines to a host with a virtual switch that is set to use a different QoS mode.</para>
                        </listItem>
                        <listItem>
                          <para>Migration will be blocked when absolute values that configured for a virtual machine cannot be honored.</para>
                        </listItem>
                      </list>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>SR-IOV</para>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Provides the lowest network latency for a virtual machine</para>
                        </listItem>
                        <listItem>
                          <para>Provides the highest network I/O for a virtual machine</para>
                        </listItem>
                        <listItem>
                          <para>Reduces the CPU overhead required for virtual networking</para>
                        </listItem>
                      </list>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>You need an SR-IOV-capable network adapter and driver in the host and each virtual machine where a virtual function is assigned.</para>
                        </listItem>
                        <listItem>
                          <para>SR-IOV enabled virtual network adapters cannot be part of the NIC Team on the host. </para>
                        </listItem>
                        <listItem>
                          <para>For network high availability, two or more SR-IOV network adapters need to be installed on the host, and NIC Teaming needs to be configured in the virtual machine. </para>
                        </listItem>
                        <listItem>
                          <para>SR-IOV should only be used by trusted workloads because the traffic bypasses the Hyper-V switch and has direct access to the physical network adapter. </para>
                        </listItem>
                        <listItem>
                          <para>Configuring virtual switch port ACLs, Hyper-V QoS, RouterGuard, and DHCPGuard will prevent SR-IOV from being used. </para>
                        </listItem>
                        <listItem>
                          <para>SR-IOV is not supported for virtual machines running in Azure.</para>
                        </listItem>
                      </list>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>
                        <externalLink>
                          <linkText>Virtual receive-side scaling</linkText>
                          <linkUri>http://technet.microsoft.com/library/dn383582.aspx</linkUri>
                        </externalLink>
                      </para>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Supports virtual receive-side scaling, which allows virtual machines to distribute network processing load across multiple virtual processors (vCPUs) to increase network throughput within virtual machines</para>
                        </listItem>
                        <listItem>
                          <para>Provides compatibility with:</para>
                          <list class="bullet">
                            <listItem>
                              <para>NIC Teaming</para>
                            </listItem>
                            <listItem>
                              <para>Live migration</para>
                            </listItem>
                            <listItem>
                              <para>NVGRE</para>
                            </listItem>
                          </list>
                        </listItem>
                      </list>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Virtual receive-side scaling requires the physical network adapter to support Virtual Machine Queue (VMQ), and it must be enabled on the host. </para>
                        </listItem>
                        <listItem>
                          <para>Not compatible with an SR-IOV-enabled virtual network adapter.</para>
                        </listItem>
                        <listItem>
                          <para>Virtual machines must be running Windows Server 2012 R2 or Windows 8.1.</para>
                        </listItem>
                        <listItem>
                          <para>Disabled by default if the VMQ adapter is less than 10 Gbps.</para>
                        </listItem>
                      </list>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>Jumbo frames</para>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Allows more data to be transferred with each Ethernet transaction, reducing the number of frames that need to be transmitted</para>
                        </listItem>
                        <listItem>
                          <para>Used typically for communication with storage, but can be used for all types of communication</para>
                        </listItem>
                        <listItem>
                          <para>Reduces the overhead on the virtual machines, networking equipment, and the end server the data is being sent to</para>
                        </listItem>
                        <listItem>
                          <para>Configured for communication within a datacenter where you can control the maximum transmission unit (MTU) settings at all hops</para>
                        </listItem>
                      </list>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Provides a slightly lower error detection probability.</para>
                        </listItem>
                        <listItem>
                          <para>Each network device along the path needs to support Jumbo Frames and be configured with the same or higher MTU setting. Use the <embeddedLabel>Ping</embeddedLabel> command to verify end-to-end MTU settings.</para>
                        </listItem>
                        <listItem>
                          <para>If one hop along the way does not support Jumbo Frames or is configured with a smaller MTU, the packets will be dropped. </para>
                        </listItem>
                      </list>
                    </TD>
                  </tr>
                </tbody>
              </table>
            </content>
          </section>
          <section>
            <title>Task 2c: Define network traffic availability options</title>
            <content>
              <para>NIC Teaming, also known as load balancing and failover (LBFO), allows multiple network adapters to be placed in a team for the purposes of bandwidth aggregation and traffic failover. This maintains connectivity in the event of a network component failure. NIC Teaming is typically configured on the host, and when you create the virtual switch, it is bound to network adapter team.</para>
              <para>The network switches that are deployed determine the NIC Teaming mode. The default settings in Windows Server 2012 R2 should be sufficient for the majority of deployments. </para>
              <para>
                <embeddedLabel>Note:</embeddedLabel> SR-IOV is not compatible with NIC Teaming. For more information about SR-IOV, see <link xlink:href="0a72c21e-9430-4b2c-a53b-87f23cf85c00#BKMK_Step2Task2b">Step 2, Task 2b: Define network traffic performance options</link>.</para>
              <para>Additional information:</para>
              <para>
                <externalLink>
                  <linkText>NIC Teaming Overview</linkText>
                  <linkUri>http://technet.microsoft.com/library/hh831648.aspx</linkUri>
                </externalLink>
              </para>
            </content>
          </section>
          <section>
            <title>Task 2d: Define network traffic security options</title>
            <content>
              <para>Each network traffic type can have different security requirements, for example, requirements related to isolation and encryption. The following table explains strategies that can be used to meet various security requirements. </para>
              <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
                <thead>
                  <tr>
                    <TD>
                      <para>Strategy</para>
                    </TD>
                    <TD>
                      <para>Advantages</para>
                    </TD>
                    <TD>
                      <para>Disadvantages</para>
                    </TD>
                  </tr>
                </thead>
                <tbody>
                  <tr>
                    <TD>
                      <para>Separation on different network adapters</para>
                    </TD>
                    <TD>
                      <para>Separate traffic from other network traffic</para>
                    </TD>
                    <TD>
                      <para>Does not scale well. The more networks you have, the more network adapters you need to install and manage on the host.</para>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>IPsec with IPsec <externalLink><linkText>Task Offloading</linkText><linkUri>http://technet.microsoft.com/library/jj679878.aspx#bkmk_ipsecto</linkUri></externalLink></para>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Supports IPsec offloading for encryption of network traffic to and from virtual machines using Hyper-V</para>
                        </listItem>
                        <listItem>
                          <para>Encrypts traffic while it is traversing the network</para>
                        </listItem>
                      </list>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Setup is complex</para>
                        </listItem>
                        <listItem>
                          <para>Can make troubleshooting issues more difficult because traffic to and from the hosts and virtual machines cannot be opened</para>
                        </listItem>
                        <listItem>
                          <para>Increased processor utilization when physical network adapters in the host do not support IPsec offloading</para>
                        </listItem>
                      </list>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>VLAN tagging</para>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Used by most companies already</para>
                        </listItem>
                        <listItem>
                          <para>Compatible with QoS policies</para>
                        </listItem>
                        <listItem>
                          <para>Supports <externalLink><linkText>Private VLANs</linkText><linkUri>http://technet.microsoft.com/library/jj679878.aspx#bkmk_pvlan</linkUri></externalLink></para>
                        </listItem>
                        <listItem>
                          <para>Supports <externalLink><linkText>VLAN trunk mode</linkText><linkUri>http://technet.microsoft.com/library/jj679878.aspx#bkmk_pvlan</linkUri></externalLink> for virtual machines</para>
                        </listItem>
                        <listItem>
                          <para>Reduces the number of physical adapters that need to be installed in the host</para>
                        </listItem>
                      </list>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Limited to 4094 VLANs</para>
                        </listItem>
                        <listItem>
                          <para>Configuration is required for switches, hosts, and virtual machines </para>
                        </listItem>
                        <listItem>
                          <para>Incorrect changes to VLAN configuration settings can lead to server-specific or system-wide network issues</para>
                        </listItem>
                      </list>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>
                        <externalLink>
                          <linkText>Hyper-V Network Virtualization</linkText>
                          <linkUri>http://technet.microsoft.com/library/jj134230.aspx</linkUri>
                        </externalLink>
                      </para>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Provides flexible workload placement, including network isolation and IP address reuse without VLANs </para>
                        </listItem>
                        <listItem>
                          <para>Enables easier movement of workloads to the cloud</para>
                        </listItem>
                        <listItem>
                          <para>Supports live migration across subnets without the need to inject a new IP address on the new server</para>
                        </listItem>
                        <listItem>
                          <para>Enables multi-tenant networking solutions </para>
                        </listItem>
                        <listItem>
                          <para>Provides simplified network design and improved server and network resource use. The rigidity of VLANs with the dependency of virtual machine placement on a physical network infrastructure typically results in overprovisioning and under use.</para>
                        </listItem>
                      </list>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Management of Hyper-V Network Virtualization requires System Center 2012 R2 - Virtual Machine Manager or a non-Microsoft management solution. </para>
                        </listItem>
                        <listItem>
                          <para>A Hyper-V Network Virtualization gateway is required to allow communication outside of the virtual network.</para>
                        </listItem>
                      </list>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>
                        <externalLink>
                          <linkText>DHCPGuard</linkText>
                          <linkUri>http://technet.microsoft.com/library/jj679878.aspx#bkmk_dhcp</linkUri>
                        </externalLink>
                      </para>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Blocks the virtual machine from making DHCP offers over the virtual network</para>
                        </listItem>
                        <listItem>
                          <para>Configured on a per virtual network adapter basis</para>
                        </listItem>
                        <listItem>
                          <para>Does not stop the virtual machine from receiving an address from a DHCP server</para>
                        </listItem>
                      </list>
                    </TD>
                    <TD>
                      <para>Minimal impact on performance when enabled</para>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>
                        <externalLink>
                          <linkText>RouterGuard</linkText>
                          <linkUri>http://technet.microsoft.com/library/jj679878.aspx#bkmk_router</linkUri>
                        </externalLink>
                      </para>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Blocks the following packets:</para>
                          <list class="bullet">
                            <listItem>
                              <para>ICMPv4 Type 5 (redirect message)</para>
                            </listItem>
                            <listItem>
                              <para>ICMPv4 Type 9 (router advertisement)</para>
                            </listItem>
                            <listItem>
                              <para>ICMPv6 Type 134 (router advertisement)</para>
                            </listItem>
                            <listItem>
                              <para>ICMPv6 Type 137 (redirect message)</para>
                            </listItem>
                          </list>
                        </listItem>
                        <listItem>
                          <para>Configured on a per virtual network adapter basis</para>
                        </listItem>
                      </list>
                    </TD>
                    <TD>
                      <para>Minimal impact on performance when enabled</para>
                    </TD>
                  </tr>
                </tbody>
              </table>
              <para/>
              <para>
                <embeddedLabel>Design decision</embeddedLabel> - You can download <externalLink><linkText>Virtualization Fabric Design Considerations Guide Worksheets</linkText><linkUri>http://aka.ms/P0anp3</linkUri></externalLink> and change the sample data in the Virtual machine configs. worksheet to capture the decisions you make for all previous tasks in this step. For subsequent design decisions, this document references specific worksheets in this guide where you can enter your data.</para>
            </content>
          </section>
          <section>
            <title>Task 2e: Define virtual network adapters</title>
            <content>
              <para>With an understanding of the types of traffic required by the virtual machines, in addition to the performance, availability, and security strategies for the traffic, you can determine how many virtual network adapters each virtual machine will require. </para>
              <para>A virtual network adapter is connected to a virtual switch. There are three types of virtual switches:</para>
              <list class="bullet">
                <listItem>
                  <para>External virtual switch</para>
                </listItem>
                <listItem>
                  <para>Internal virtual switch</para>
                </listItem>
                <listItem>
                  <para>Private virtual switch</para>
                </listItem>
              </list>
              <para>The external virtual switch provides the virtual machine with access to the physical network through the network adapter that is associated with the virtual switch it is connect to. A physical network adapter in the host can only be associated with a single external switch. </para>
              <para>Generation 1 virtual machines can have a maximum of 12 network adapters—4 legacy network adapters and 8 virtual network adapters. Generation 2 virtual machines do not support legacy network adapters, so the maximum adapters supported is 8. A virtual network adapter can have one VLAN ID assigned to it, unless it is configured in trunk mode.</para>
              <para>If you are going to assign virtual machine traffic to different VLANs, a network adapter that supports VLANs must be installed in the host and assigned to the virtual switch. You can set the VLAN ID for the virtual machine in the properties of the virtual machine. The VLAN ID that is set in the virtual switch is the VLAN ID that will be assigned to the virtual network adapter assigned to the host operating system.</para>
              <para>
                <embeddedLabel>Note:</embeddedLabel> If you have a virtual machine that requires access to more networks than available adapters, you can enable VLAN trunk mode for a virtual machine network adapter by using the <externalLink><linkText>Set-VMNetworkAdapterVlan</linkText><linkUri>http://technet.microsoft.com/library/hh848475.aspx</linkUri></externalLink> Windows PowerShell cmdlet.</para>
            </content>
          </section>
          <section>
            <title>Task 2f: Define IP addressing strategy</title>
            <content>
              <para>You need to determine how you will assign IP addresses to your virtual machines. If you don't, you can have IP address conflicts, which can have a negative impact on other virtual machines and physical devices on the network. </para>
              <para>Additionally, unauthorized DHCP servers can cause havoc on your network infrastructure, and they can be especially difficult to track down when the server is running as a virtual machine. You can protect your network against unauthorized DHCP servers running on a virtual machine by enabling DHCPGuard in the settings of your virtual machines. DHCPGuard protects against a malicious virtual machine representing itself as a DHCP server for man-in-the-middle attacks. </para>
              <para>
                <embeddedLabel>Additional information:</embeddedLabel>
              </para>
              <para>
                <externalLink>
                  <linkText>Dynamic Host Configuration Protocol (DHCP) Overview</linkText>
                  <linkUri>http://technet.microsoft.com/library/hh831825.aspx</linkUri>
                </externalLink>
              </para>
              <para>
                <externalLink>
                  <linkText>DHCPGuard</linkText>
                  <linkUri>http://technet.microsoft.com/library/jj679878.aspx#bkmk_dhcp</linkUri>
                </externalLink>
              </para>
              <para>
                <externalLink>
                  <linkText>IP Address Management (IPAM) Overview</linkText>
                  <linkUri>http://technet.microsoft.com/library/hh831353.aspx</linkUri>
                </externalLink>
              </para>
            </content>
          </section>
        </sections>
      </section>
      <section>
        <title>Task 3: Define storage configuration</title>
        <content>
          <para>To determine your storage configuration, you need to define the data types that the virtual machines will store and the type of storage they need.</para>
        </content>
        <sections>
          <section>
            <title>Task 3a: Define data types</title>
            <content>
              <para>The following table lists the types of data that a virtual machine may need to store and where that type of data is often stored.</para>
              <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
                <thead>
                  <tr>
                    <TD>
                      <para>Data type</para>
                    </TD>
                    <TD>
                      <para>Storage location for data type</para>
                    </TD>
                  </tr>
                </thead>
                <tbody>
                  <tr>
                    <TD>
                      <para>Operating system files</para>
                    </TD>
                    <TD>
                      <para>Within a virtual hard disk file that is stored by the virtualization host. Storage considerations for the virtualization host are addressed further in Step 4: Plan for server virtualization hosts below.</para>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>Windows page file</para>
                    </TD>
                    <TD>
                      <para>Often stored in the same location as the operating system files.</para>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>Application program files</para>
                    </TD>
                    <TD>
                      <para>Often stored in the same location as the operating system files.</para>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>Application configuration data</para>
                    </TD>
                    <TD>
                      <para>Often stored in the same location as the operating system files.</para>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>Application data</para>
                    </TD>
                    <TD>
                      <para>Often stored separately from the application and operating system files. For example, if the application was a database application, the database files are often stored on a high availability, efficient, network-based, storage solution that is separate from the location where the operating system or application program files are stored.</para>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>Clustered Shared Volumes (CSV) and disk witness (required for guest virtual machine clustering)</para>
                    </TD>
                    <TD>
                      <para>Often stored separately from the application and operating system files.</para>
                      <list class="bullet">
                        <listItem>
                          <para>CSV storage is where clustered applications store data so that it is available to all nodes in the cluster. </para>
                        </listItem>
                        <listItem>
                          <para>A disk witness is a disk in the cluster storage that is designated to hold a copy of the cluster configuration database. A failover cluster has a disk witness only if this is specified as part of the quorum configuration.</para>
                        </listItem>
                      </list>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>Crash dump files</para>
                    </TD>
                    <TD>
                      <para>Often stored in the same location as the operating system files.</para>
                    </TD>
                  </tr>
                </tbody>
              </table>
            </content>
          </section>
          <section>
            <title>Task 3b: Define storage types</title>
            <content>
              <para>The following table lists the types of storage that might be used for the data types defined in Step 2, Task 2a above.</para>
              <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
                <thead>
                  <tr>
                    <TD>
                      <para>Storage type</para>
                    </TD>
                    <TD>
                      <para>Considerations</para>
                    </TD>
                  </tr>
                </thead>
                <tbody>
                  <tr>
                    <TD>
                      <para>Virtual IDE disk</para>
                    </TD>
                    <TD>
                      <para>Generation 1 virtual machines:</para>
                      <list class="bullet">
                        <listItem>
                          <para>2 IDE controllers, and each controller can support a maximum of 2 IDE devices for a maximum of 4 IDE devices.</para>
                        </listItem>
                        <listItem>
                          <para>The startup disk, also known as the boot disk, must be attached to one of the IDE devices as a virtual hard disk or as a physical disk. </para>
                        </listItem>
                      </list>
                      <para>Generation 2 virtual machines do not support IDE devices.</para>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>Virtual SCSI</para>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>4 virtual SCSI controllers are supported with each controller supporting up to 64 devices for a total of 256 SCSI devices.</para>
                        </listItem>
                        <listItem>
                          <para>Because generation 2 virtual machines only support a SCSI drive, generation 2 virtual machines support SCSI boot disks.</para>
                        </listItem>
                      </list>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>iSCSI initiator in the virtual machine</para>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Take advantage of storage on SANs without installing Fibre Channel adapters in the host.</para>
                        </listItem>
                        <listItem>
                          <para>Cannot be used for the boot disk. </para>
                        </listItem>
                        <listItem>
                          <para>Use network QoS policies to ensure proper bandwidth availability for storage and other network traffic. </para>
                        </listItem>
                        <listItem>
                          <para>Not compatible with Hyper-V Replica. When using a SAN storage backend, use the SAN replication options provided by your storage vendor.</para>
                        </listItem>
                      </list>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>Virtual Fibre Channel</para>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Requires one or more Fibre Channel host bus adapters (HBAs) or Fibre Channel over Ethernet (FCoE) converged network adapters in each host that will host virtual machines with virtual Fibre Channel adapters.</para>
                        </listItem>
                        <listItem>
                          <para>HBA and FCoE drivers must support virtual Fibre Channel.</para>
                        </listItem>
                        <listItem>
                          <para>An NPIV-enabled SAN. </para>
                        </listItem>
                        <listItem>
                          <para>Requires additional configuration to support live migration. For additional information about live migration and virtual Fibre Channel, see <externalLink><linkText>Hyper-V Virtual Fibre Channel Overview.</linkText><linkUri>http://technet.microsoft.com/library/hh831413.aspx</linkUri></externalLink></para>
                        </listItem>
                        <listItem>
                          <para>Not compatible with <externalLink><linkText>Hyper-V Replica</linkText><linkUri>http://technet.microsoft.com/library/jj134172.aspx</linkUri></externalLink>. When using SAN storage, you should use the SAN replication options provided by your storage vendor.</para>
                        </listItem>
                        <listItem>
                          <para>A virtual machine can have up to four virtual ports. </para>
                        </listItem>
                        <listItem>
                          <para>Virtual Fibre Channel LUNs cannot be used as boot media for the virtual machine.</para>
                        </listItem>
                      </list>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>SMB 3.0</para>
                    </TD>
                    <TD>
                      <para>Access files stored on Server Message Block (SMB) 3.0 shares from within the virtual machine.</para>
                    </TD>
                  </tr>
                </tbody>
              </table>
            </content>
          </section>
          <section>
            <title>Task 3c: Define virtual hard disk format and type</title>
            <content>
              <para>If you are using the virtual hard disk storage type, you must first select the VHD format that you’ll use from the options listed in the following table.</para>
              <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
                <thead>
                  <tr>
                    <TD>
                      <para>Disk format</para>
                    </TD>
                    <TD>
                      <para>Advantages</para>
                    </TD>
                    <TD>
                      <para>Disadvantages</para>
                    </TD>
                  </tr>
                </thead>
                <tbody>
                  <tr>
                    <TD>
                      <para>VHD</para>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Supported by all versions of Hyper-V</para>
                        </listItem>
                        <listItem>
                          <para>Supported by both on-premises implementations and Azure</para>
                        </listItem>
                      </list>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Maximum storage capacity is 2040 GB</para>
                        </listItem>
                        <listItem>
                          <para>Maximum virtual hard disk supported by Azure is 1 TB</para>
                        </listItem>
                        <listItem>
                          <para>Not supported by generation 2 virtual machines</para>
                        </listItem>
                      </list>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>
                        <externalLink>
                          <linkText>VHDX</linkText>
                          <linkUri>http://technet.microsoft.com/library/hh831446.aspx</linkUri>
                        </externalLink>
                      </para>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Maximum storage capacity is 64 terabytes (TB)</para>
                        </listItem>
                        <listItem>
                          <para>Protection against data corruption during power failure</para>
                        </listItem>
                        <listItem>
                          <para>Improved alignment of the virtual hard disk format to work well on large sector disks</para>
                        </listItem>
                        <listItem>
                          <para>A 4-KB logical sector virtual disk that allows for increased performance when used by applications and workloads that are designed for 4 KB sectors</para>
                        </listItem>
                        <listItem>
                          <para>Can be used as shared storage for virtual machines that require Failover Clustering</para>
                        </listItem>
                      </list>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Not currently supported by virtual machines in Azure </para>
                        </listItem>
                        <listItem>
                          <para>Cannot be used with versions of Hyper-V prior to Windows Server 2012 </para>
                        </listItem>
                      </list>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>
                        <externalLink>
                          <linkText>Shared VHDX</linkText>
                          <linkUri>http://technet.microsoft.com/library/dn281956.aspx</linkUri>
                        </externalLink>
                      </para>
                    </TD>
                    <TD>
                      <para>Used for shared storage for guest virtual machine clusters</para>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Requires Windows Server 2012 R2 on the host running Hyper-V</para>
                        </listItem>
                        <listItem>
                          <para>Supported guest operating systems for guest clusters that use a shared virtual hard disk include Windows Server 2012 R2 and Windows Server 2012. To support Windows Server 2012 as a guest operating system, Windows Server 2012 R2 Integration Services must be installed within the guest (virtual machine).</para>
                        </listItem>
                        <listItem>
                          <para>The following features are not compatible with shared VHDX:</para>
                          <list class="bullet">
                            <listItem>
                              <para>Hyper-V Replica</para>
                            </listItem>
                            <listItem>
                              <para>Resizing the virtual hard disk while any of the configured virtual machines are running</para>
                            </listItem>
                            <listItem>
                              <para>Live storage migration</para>
                            </listItem>
                            <listItem>
                              <para>Host-level VSS backups. Guest-level backups should be performed by using the same methods that you would use for a cluster running on physical servers.</para>
                            </listItem>
                            <listItem>
                              <para>Virtual machine checkpoints</para>
                            </listItem>
                            <listItem>
                              <para>Storage QoS</para>
                            </listItem>
                          </list>
                        </listItem>
                      </list>
                    </TD>
                  </tr>
                </tbody>
              </table>
              <para/>
              <para>Next, select the type of disk you will use from the options listed in the following table.</para>
              <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
                <thead>
                  <tr>
                    <TD>
                      <para>Disk type</para>
                    </TD>
                    <TD>
                      <para>Advantages</para>
                    </TD>
                    <TD>
                      <para>Disadvantages</para>
                    </TD>
                  </tr>
                </thead>
                <tbody>
                  <tr>
                    <TD>
                      <para>Fixed</para>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Less likely to suffer from fragmentation than other disk types</para>
                        </listItem>
                        <listItem>
                          <para>Lower CPU overhead than other disk types</para>
                        </listItem>
                        <listItem>
                          <para>After the VHD file is created, there is less concern about available disk space than there is with the other disk types</para>
                        </listItem>
                        <listItem>
                          <para>Supported by both on-premises implementations and Azure</para>
                        </listItem>
                      </list>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>A created virtual hard disk requires all of the space to be available, even if the virtual machine is not using all of the space.</para>
                        </listItem>
                        <listItem>
                          <para>The virtual hard disk will fail to create if there is not enough storage space available.</para>
                        </listItem>
                        <listItem>
                          <para>Unused space in the virtual hard disk cannot be allocated to other virtual hard disks.</para>
                        </listItem>
                      </list>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>Dynamic</para>
                    </TD>
                    <TD>
                      <para>Only uses disk space as required, rather than using all that’s been provisioned</para>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Not currently supported by Azure, though dynamic disks can be converted to fixed disks</para>
                        </listItem>
                        <listItem>
                          <para>It is important to monitor free disk space when using dynamic virtual hard disks. If disk space is not available for a dynamic virtual hard disk to grow, the virtual machine will enter a paused-critical state.</para>
                        </listItem>
                        <listItem>
                          <para>Virtual hard disk file can become fragmented</para>
                        </listItem>
                        <listItem>
                          <para>Slightly higher CPU overhead for read and write operations than there is for the fixed disk type</para>
                        </listItem>
                      </list>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>Differencing</para>
                    </TD>
                    <TD>
                      <para>Can use less disk space if multiple differencing disks use the same parent</para>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Not currently supported by Azure</para>
                        </listItem>
                        <listItem>
                          <para>Changes made to a parent disk can cause data inconsistency in the child disk</para>
                        </listItem>
                        <listItem>
                          <para>Slightly higher CPU overhead for read and write operations for high I/O intensive workloads</para>
                        </listItem>
                      </list>
                    </TD>
                  </tr>
                </tbody>
              </table>
              <para/>
              <para>Consider the following when you are selecting a virtual hard disk file type and format:</para>
              <list class="bullet">
                <listItem>
                  <para>When you use the VHDX format, a dynamic disk can be used because it offers resiliency guarantees in addition to space savings that are associated with allocating space only when there is a need to do so. </para>
                </listItem>
                <listItem>
                  <para>A fixed disk can also be used, irrespective of the format, when the storage on the hosting volume is not actively monitored. This ensures that sufficient disk space is present when the VHD file is expanded at run time.</para>
                </listItem>
                <listItem>
                  <para>Checkpoints (formerly known as snapshots) of a virtual machine create a differencing virtual hard disk to store writes to the disks. Having only a few checkpoint s can elevate the CPU usage of storage I/O, but they might not noticeably affect performance (except in highly I/O-intensive server workloads). </para>
                  <para>However, having a large chain of checkpoints can noticeably affect performance because reading from the virtual hard disks can require checking for the requested blocks in many differencing disks. Keeping short checkpoint chains is important for maintaining good disk I/O performance.</para>
                </listItem>
              </list>
            </content>
          </section>
          <section>
            <title>Task 3d: Define which storage type to use for each data type</title>
            <content>
              <para>After you define the data types and storage types that virtual machines will store, you can determine which storage type and which virtual disk format and type you’ll use for each data type.</para>
            </content>
          </section>
        </sections>
      </section>
      <section>
        <title>Task 4: Define virtual machine availability strategy</title>
        <content>
          <para>Though fabric administrators are responsible for the availability of the fabric, virtual machine administrators are ultimately responsible for the availability of their virtual machines. As a result, the virtual machine administrator must understand the capabilities of the fabric to design the appropriate availability strategy for their virtual machines. </para>
          <para>The following tables analyze three availability strategies for virtual machines running workloads with the characterizations that are defined in Step 1, Task 2 above. Typically, the fabric administrator informs virtual machine administrators in advance when planned downtime activities are scheduled for the fabric so that virtual machine administrators can plan accordingly. The three availability strategies are:</para>
          <list class="bullet">
            <listItem>
              <para>
                <link xlink:href="0a72c21e-9430-4b2c-a53b-87f23cf85c00#BKMK_Stateless">Stateless</link>
              </para>
            </listItem>
            <listItem>
              <para>
                <link xlink:href="0a72c21e-9430-4b2c-a53b-87f23cf85c00#BKMK_Stateful">Stateful</link>
              </para>
            </listItem>
            <listItem>
              <para>
                <link xlink:href="0a72c21e-9430-4b2c-a53b-87f23cf85c00#BKMK_SharedStateful">Shared stateful</link>
              </para>
            </listItem>
          </list>
        </content>
        <sections>
          <section address="BKMK_Stateless">
            <title>Stateless</title>
            <content>
              <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
                <thead>
                  <tr>
                    <TD>
                      <para>Option</para>
                    </TD>
                    <TD>
                      <para>Considerations</para>
                    </TD>
                  </tr>
                </thead>
                <tbody>
                  <tr>
                    <TD>
                      <para>
                        <externalLink>
                          <linkText>Virtual Machine Live Migration</linkText>
                          <linkUri>http://technet.microsoft.com/library/hh831435.aspx</linkUri>
                        </externalLink> at the host level</para>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>If a host needs to be taken down for planned maintenance, the running virtual machines can be migrated to an operable host with no downtime to the virtual machines. For more information about host considerations, see <link xlink:href="0a72c21e-9430-4b2c-a53b-87f23cf85c00#BKMK_Step4Task5">Step 4, Task 5: Define server virtualization host availability strategy</link> below.</para>
                        </listItem>
                        <listItem>
                          <para>If the virtual machines are not stored on storage that is accessible by both hosts, you need to move the virtual machine storage during a live migration.</para>
                        </listItem>
                        <listItem>
                          <para>If a host fails unexpectedly, all virtual machines running on the host stop running. You need to start the virtual machines by running the same workload on another host.</para>
                        </listItem>
                      </list>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>Load-balanced clusters (by using <externalLink><linkText>Windows Network Load Balancing</linkText><linkUri>http://technet.microsoft.com/library/hh831698.aspx</linkUri></externalLink>)</para>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Requires that the virtual machine administrator have at least two virtual machines running an identical workload hosted on different hosts. </para>
                        </listItem>
                        <listItem>
                          <para>Network Load Balancing (NLB) is configured within the virtual machines by the virtual machine administrator.</para>
                        </listItem>
                        <listItem>
                          <para>NLB requires that static IP addresses are assigned to the network adapters. DHCP address assignment is not supported.</para>
                        </listItem>
                        <listItem>
                          <para>The virtual machine administrator needs to work with the fabric administrator to get IP addresses to use for the NLB virtual IP address and to create the required DNS entry.</para>
                        </listItem>
                        <listItem>
                          <para>Enable MAC spoofing for the virtual network that is used by NLB in the guests. This can be done from the Network Adapter settings on each virtual machine that is participating in a NLB cluster as a node. You can create NLB clusters, add nodes, and update NLB cluster configurations without rebooting the virtual machines.</para>
                        </listItem>
                        <listItem>
                          <para>All of the virtual machines that are participating in the NLB cluster must be on the same subnet. </para>
                        </listItem>
                        <listItem>
                          <para>To ensure availability of the workload (even in the case of host failure), the virtual machine fabric administrator needs to ensure that the virtual machines are running on different hosts.</para>
                        </listItem>
                      </list>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>Load-balanced clusters (by using a hardware load balancer)</para>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Must provide this capability at the fabric level, and fabric administrators must configure load-balanced clusters for virtual machines that require it. Or they can enable virtual machine administrators to configure it through the management portal for the hardware load balancer. </para>
                        </listItem>
                        <listItem>
                          <para>Requires that the virtual machine administrator have at least two virtual machines running an identical workload hosted on the fabric.</para>
                        </listItem>
                        <listItem>
                          <para>Review the hardware vendor’s product documentation for additional information.</para>
                        </listItem>
                      </list>
                    </TD>
                  </tr>
                </tbody>
              </table>
              <para/>
            </content>
          </section>
          <section address="BKMK_Stateful">
            <title>Stateful</title>
            <content>
              <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
                <thead>
                  <tr>
                    <TD>
                      <para>Option</para>
                    </TD>
                    <TD>
                      <para>Considerations</para>
                    </TD>
                  </tr>
                </thead>
                <tbody>
                  <tr>
                    <TD>
                      <para>
                        <externalLink>
                          <linkText>Hyper-V Cluster</linkText>
                          <linkUri>http://technet.microsoft.com/library/dn743844.aspx</linkUri>
                        </externalLink>
                      </para>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Requires configuration of a failover cluster. </para>
                        </listItem>
                        <listItem>
                          <para>Requires shared storage between all of the nodes in the cluster for the CSV files. This can be SAN storage or an SMB 3.0 file share. </para>
                        </listItem>
                        <listItem>
                          <para>When the cluster detects an issue with a host or Hyper-V detects an issue with the virtual machine networking or storage, the virtual machine can be moved to another host. The virtual machine continues to run during the move.</para>
                        </listItem>
                        <listItem>
                          <para>If there is a catastrophic failure of a host, the virtual machines that were running on that host can be started on other nodes in the cluster. Critical virtual machines can be configured to automatically start. This limits the amount of downtime if there is a catastrophic host failure.</para>
                        </listItem>
                        <listItem>
                          <para>Patch hosts without impacting running virtual machines with Cluster-Aware Updating. </para>
                        </listItem>
                        <listItem>
                          <para>Configure virtual machine anti-affinity to avoid running virtual machines on the same node. For example, if you are running two web servers that provide front-end services for a back-end application, you do not want both web servers running on the same node. </para>
                        </listItem>
                        <listItem>
                          <para>A node can be placed into maintenance mode and the failover cluster service will move the running virtual machines to another node in the cluster. When there are no running virtual machines on the node, the required maintenance can be performed. </para>
                          <para>The failover cluster will not move virtual machines to a node in maintenance mode. Before putting a node in maintenance mode, ensure that there is enough capacity on the other nodes in the Hyper-V cluster to run the existing virtual machines and still maintain the SLAs for your customers.</para>
                        </listItem>
                      </list>
                    </TD>
                  </tr>
                </tbody>
              </table>
              <para/>
            </content>
          </section>
          <section address="BKMK_SharedStateful">
            <title>Shared stateful</title>
            <content>
              <para>When running cluster-aware workloads, you can provide an additional layer of availability by enabling virtual machine guest clustering. Guest clustering supports high availability for workloads within the virtual machine. Guest clustering provides protection to the workload that is running in the virtual machines, even if a host fails where the virtual machine is running. Because the workload was protected by Failover Clustering, the virtual machine on the other node can take over automatically.</para>
              <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
                <thead>
                  <tr>
                    <TD>
                      <para>Option</para>
                    </TD>
                    <TD>
                      <para>Considerations</para>
                    </TD>
                  </tr>
                </thead>
                <tbody>
                  <tr>
                    <TD>
                      <para>
                        <externalLink>
                          <linkText>Virtual Machine Guest Clustering</linkText>
                          <linkUri>http://technet.microsoft.com/library/dn440540.aspx</linkUri>
                        </externalLink>
                      </para>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Requires shared storage that is accessible by two or more virtual machines at the same time. Supported connection types include:</para>
                          <list class="bullet">
                            <listItem>
                              <para>iSCSI</para>
                            </listItem>
                            <listItem>
                              <para>Virtual Fibre Channel</para>
                            </listItem>
                            <listItem>
                              <para>Shared VHDX</para>
                            </listItem>
                          </list>
                        </listItem>
                        <listItem>
                          <para>Configure virtual machine anti-affinity to avoid both virtual machines from running on the same cluster node. </para>
                        </listItem>
                        <listItem>
                          <para>Virtual machine guest clustering is not supported by Azure.</para>
                        </listItem>
                        <listItem>
                          <para>The following features are not compatible with shared VHDX:</para>
                          <list class="bullet">
                            <listItem>
                              <para>Hyper-V Replica</para>
                            </listItem>
                            <listItem>
                              <para>Resizing the virtual hard disk while any of the configured virtual machines are running</para>
                            </listItem>
                            <listItem>
                              <para>Live storage migration</para>
                            </listItem>
                            <listItem>
                              <para>Host-level VSS backups. Guest-level backups should be performed by using the same methods that you would use for a cluster running on physical servers. </para>
                            </listItem>
                            <listItem>
                              <para>Virtual machine checkpoints</para>
                            </listItem>
                            <listItem>
                              <para>Storage QoS</para>
                            </listItem>
                          </list>
                        </listItem>
                      </list>
                    </TD>
                  </tr>
                </tbody>
              </table>
              <para/>
              <para>
                <embeddedLabel>Additional information:</embeddedLabel>
              </para>
              <para>
                <externalLink>
                  <linkText>Deploy a Guest Cluster Using a Shared Virtual Hard Disk</linkText>
                  <linkUri>http://technet.microsoft.com/library/dn265980.aspx</linkUri>
                </externalLink>
              </para>
              <para>
                <externalLink>
                  <linkText>Using Guest Clustering for High Availability</linkText>
                  <linkUri>http://technet.microsoft.com/library/dn440540.aspx</linkUri>
                </externalLink>
              </para>
            </content>
          </section>
          <section>
            <title>Disaster Recovery</title>
            <content>
              <para>If there is a disaster, how quickly can you get the required workloads up and running so they can service clients? In some cases, the allotted time can be only a few minutes. </para>
              <para>Replication of data from your main datacenters to your disaster recovery centers is required to ensure that the most up-to-date data can be replicated with an acceptable loss of data due to delays. By running workloads in virtual machines, you can replicate the virtual hard disks and the virtual machine configuration files from your primary site to a replica site. </para>
              <para>The following table compares disaster recovery options.</para>
              <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
                <thead>
                  <tr>
                    <TD>
                      <para>Option</para>
                    </TD>
                    <TD>
                      <para>Considerations</para>
                    </TD>
                  </tr>
                </thead>
                <tbody>
                  <tr>
                    <TD>
                      <para>Hyper-V Replica</para>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Inexpensive, and there is no need to duplicate host and storage hardware at disaster recovery sites.</para>
                        </listItem>
                        <listItem>
                          <para>Use the same management tools to manage replication as to manage the virtual machines.</para>
                        </listItem>
                        <listItem>
                          <para>Configurable replication intervals to meet your data loss requirements.</para>
                        </listItem>
                        <listItem>
                          <para>Configure different IP addresses to be used at the replica site.</para>
                        </listItem>
                        <listItem>
                          <para>Minimal impact on network infrastructure.</para>
                        </listItem>
                        <listItem>
                          <para>Not supported for virtual machines configured with physical disks (also known as pass-through disks), virtual Fibre Channel storage, or shared virtual hard disks.</para>
                        </listItem>
                        <listItem>
                          <para>Hyper-V Replica should not be used as a replacement for data backup storage and data retrieval. </para>
                        </listItem>
                        <listItem>
                          <para>Additional storage will be required at the replica site if additional recovery points are configured.</para>
                        </listItem>
                        <listItem>
                          <para>Replication interval rate will determine the amount of data loss.</para>
                        </listItem>
                        <listItem>
                          <para>Additional storage is required at the replica site when a virtual machine with a large amount of changes is configured with a short replication interval.</para>
                        </listItem>
                      </list>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>Backup</para>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Back up the complete virtual machine by using a Hyper-V supported backup solution, such as System Center Data Protection Manager.</para>
                        </listItem>
                        <listItem>
                          <para>Data loss will be determined by how old the last backup is.</para>
                        </listItem>
                        <listItem>
                          <para>Virtual machines configured with a shared VHDX file cannot be backed up at the host level. Install a backup agent in the virtual machine and back up the data from within the virtual machine.</para>
                        </listItem>
                      </list>
                    </TD>
                  </tr>
                </tbody>
              </table>
              <para/>
              <para>
                <embeddedLabel>Notes:</embeddedLabel> </para>
              <list class="bullet">
                <listItem>
                  <para>To centrally manage and automate replication when running System Center 2012 R2 - Virtual Machine Manager you need to use Microsoft Azure Site Recovery.</para>
                </listItem>
                <listItem>
                  <para>To replicate virtual machines to Azure by using Microsoft Azure Site Recovery. Replicating a virtual machine to Azure is currently in preview mode.</para>
                </listItem>
              </list>
              <para>
                <embeddedLabel>Additional information:</embeddedLabel>
              </para>
              <para>
                <externalLink>
                  <linkText>Microsoft Azure Site Recovery</linkText>
                  <linkUri>http://azure.microsoft.com/services/recovery-manager/</linkUri>
                </externalLink>
              </para>
              <para>
                <embeddedLabel>Important:</embeddedLabel> </para>
              <list class="bullet">
                <listItem>
                  <para>Use the <externalLink><linkText>Hyper-V Replica Capacity Planner</linkText><linkUri>http://www.microsoft.com/download/details.aspx?id=39057</linkUri></externalLink> to understand the impact Hyper-V Replica will have on your network infrastructure; processor utilization on the primary, replica, and extended replica servers; memory usage on the primary and replica servers; and disk IOPS on the primary, replica, and extended replica servers that are based on your existing virtual machines. </para>
                </listItem>
                <listItem>
                  <para>Your workload might have a built-in disaster recovery solution, such as <externalLink><linkText>AlwaysOn Availability Groups in SQL Server</linkText><linkUri>http://technet.microsoft.com/library/hh510230.aspx</linkUri></externalLink>. Consult with the workload documentation to confirm if Hyper-V Replica is supported by the workload.</para>
                </listItem>
              </list>
              <para>
                <embeddedLabel>Additional information:</embeddedLabel>
              </para>
              <para>
                <externalLink>
                  <linkText>Hyper-V Replica</linkText>
                  <linkUri>http://technet.microsoft.com/library/jj134172.aspx</linkUri>
                </externalLink>
              </para>
              <para>
                <externalLink>
                  <linkText>System Center Data Protection Manager</linkText>
                  <linkUri>http://technet.microsoft.com/library/hh758173.aspx</linkUri>
                </externalLink>
              </para>
            </content>
          </section>
        </sections>
      </section>
      <section address="BKMK_Step2Task5">
        <title>Task 5: Define virtual machine types</title>
        <content>
          <para>To support the workloads in your environment, you might create virtual machines with unique resource requirements to meet the needs of every workload. Alternatively, you might take a similar approach to public providers of virtual machine hosting services (also referred to as Infrastructure-as-a-Service (IaaS).</para>
          <para>See <externalLink><linkText>Virtual Machine and Cloud Service Sizes for Azure</linkText><linkUri>http://msdn.microsoft.com/library/windowsazure/dn197896.aspx</linkUri></externalLink> for a description of the virtual machine configurations offered by Microsoft Azure Infrastructure Services. As of this writing, the service supported 13 virtual machine configurations, each with different combinations of space for processor, memory, storage, and IOP. </para>
          <para>
            <embeddedLabel>
              <externalLink>
                <linkText>Design decision</linkText>
                <linkUri>http://aka.ms/P0anp3</linkUri>
              </externalLink>
            </embeddedLabel> - The decisions you make in all tasks of this step can be entered in the Virtual machine configs. worksheets.</para>
        </content>
      </section>
    </sections>
  </section>
  <section address="BKMK_Step3">
    <title>Step 3: Plan for server virtualization host groups</title>
    <content>
      <para>Before you define individual server hosts, you may want to first define host groups. Host groups are simply a named collection of servers that are grouped together to meet the common goals that are outlined in the remaining tasks of this step.</para>
    </content>
    <sections>
      <section>
        <title>Task 1: Define physical locations</title>
        <content>
          <para>You’ll likely group and manage hardware resources by physical location, so you’ll want to first define the locations that will contain fabric resources within your organization.</para>
        </content>
      </section>
      <section>
        <title>Task 2: Define host group types</title>
        <content>
          <para>You may create host groups for any number of reasons, such as to host workloads with specific:</para>
          <list class="bullet">
            <listItem>
              <para>Workload characterizations</para>
            </listItem>
            <listItem>
              <para>Resource requirements</para>
            </listItem>
            <listItem>
              <para>Service quality requirements</para>
            </listItem>
          </list>
          <para>The following image illustrates an organization that has created five host groups in two locations.</para>
          <mediaLink>
            <image xlink:href="17c0b7f6-4820-410e-8f4f-0ce4cf0e8d4c"/>
          </mediaLink>
          <para>
            <embeddedLabel>Figure  SEQ Figure \* ARABIC 2:</embeddedLabel> <externalLink><linkText>Host group example</linkText><linkUri>http://aka.ms/Tdxs0r</linkUri></externalLink></para>
          <para>The organization created the host groups for the reasons outlined in the following table.</para>
          <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
            <thead>
              <tr>
                <TD>
                  <para>Host group</para>
                </TD>
                <TD>
                  <para>Reasons for creating it</para>
                </TD>
              </tr>
            </thead>
            <tbody>
              <tr>
                <TD>
                  <para>Stateless and stateful workload</para>
                </TD>
                <TD>
                  <list class="bullet">
                    <listItem>
                      <para>These workload characterizations are the most common in this organization, so they have this type of host group in both locations.</para>
                    </listItem>
                    <listItem>
                      <para>These workloads have similar performance and service-level requirements.</para>
                    </listItem>
                  </list>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>Accounting department stateful and stateless workloads</para>
                </TD>
                <TD>
                  <para>Though the hardware configuration of the servers in this host group are the same as other stateless and stateful workload host groups in their environment, the Accounting department has applications that have higher security requirements than other departments in the organization. As a result, a dedicated host group was created for them so it could be secured differently than the other host groups in the fabric.</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>Shared stateful workloads</para>
                </TD>
                <TD>
                  <para>The workloads hosted by this host group require shared storage because they rely on Failover Clustering in Windows Server to maintain their availability. These workloads are hosted by a dedicated host group because the configuration of these virtual machines is different than the other virtual machines in the organization.</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>High I/O stateful workloads</para>
                </TD>
                <TD>
                  <para>All the hosts in this host group are connected to higher speed networks than the hosts in the other host groups.</para>
                </TD>
              </tr>
            </tbody>
          </table>
          <para/>
          <para>Though the organization could have spanned locations with their host groups, they chose to keep all members of each host group within the same location to ease their management. As you can see from this example, host groups can be created for a variety of reasons, and those reasons will vary across organizations. The more types of host groups you create in your organization, the more complex the environment will be to manage, which ultimately adds to the cost of hosting virtual machines. </para>
          <para>
            <embeddedLabel>Tip:</embeddedLabel> The more standardized the server hardware is within a host group, the easier it will be to scale and maintain the host group over time. If you determine that you want to standardize the hardware within a host group, you can add the standardized configuration data to the Host groups worksheet in <externalLink><linkText>Virtualization Fabric Design Considerations Worksheets</linkText><linkUri>http://aka.ms/P0anp3</linkUri></externalLink>. For more information about physical hardware considerations, see <link xlink:href="0a72c21e-9430-4b2c-a53b-87f23cf85c00#BKMK_Step4">Step 4: Plan for server virtualization hosts</link>.</para>
          <para>Consider that currently, most public cloud providers that host virtual machines:</para>
          <list class="bullet">
            <listItem>
              <para>Only host virtual machines that don’t require shared state. </para>
            </listItem>
            <listItem>
              <para>Often only have one set of service quality metrics that they provide to all customers.</para>
            </listItem>
            <listItem>
              <para>Do not dedicate specific hardware to specific customers.</para>
            </listItem>
          </list>
          <para>We recommend that you start with one host group type that contains identical hardware, and only add additional host group types because the benefit of doing so outweighs the cost.</para>
        </content>
      </section>
      <section>
        <title>Task 3: Determine whether to cluster host group members</title>
        <content>
          <para>In the past, Failover Clustering in Windows Server was only used to increase server availability, but it has grown to provide significantly more functionality. Consider the information in the following table to help you decide whether you’ll want to cluster your host group members.</para>
          <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
            <thead>
              <tr>
                <TD>
                  <para>Option</para>
                </TD>
                <TD>
                  <para>Advantages</para>
                </TD>
                <TD>
                  <para>Disadvantages</para>
                </TD>
              </tr>
            </thead>
            <tbody>
              <tr>
                <TD>
                  <para>Host group members are part of a failover cluster</para>
                </TD>
                <TD>
                  <list class="bullet">
                    <listItem>
                      <para>If any host fails, the virtual machines it’s hosting automatically restart on surviving nodes.</para>
                    </listItem>
                    <listItem>
                      <para>Virtual machines can be moved to another node in the cluster when the node it is currently running on detects an issue with the node or in the virtual machine.</para>
                    </listItem>
                    <listItem>
                      <para>Use Cluster-Aware Updating to easily update nodes in the cluster without impacting running virtual machines.</para>
                    </listItem>
                  </list>
                </TD>
                <TD>
                  <list class="bullet">
                    <listItem>
                      <para>Hosts require specific configuration to be cluster members.</para>
                    </listItem>
                    <listItem>
                      <para>Hosts must be members of an Active Directory domain. </para>
                    </listItem>
                    <listItem>
                      <para>Failover Clustering requires additional networking and storage requirements.</para>
                    </listItem>
                  </list>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>Host group members are not part of a failover cluster</para>
                </TD>
                <TD>
                  <list class="bullet">
                    <listItem>
                      <para>Hosts do not require a specific cluster configuration.</para>
                    </listItem>
                    <listItem>
                      <para>Hosts do not have to be members of an Active Directory domain. </para>
                    </listItem>
                    <listItem>
                      <para>Additional networking and storage are not required.</para>
                    </listItem>
                  </list>
                </TD>
                <TD>
                  <para>Virtual machines running on a host that fails must be manually (or you can use some form of automation) moved to a surviving host and restarted.</para>
                </TD>
              </tr>
            </tbody>
          </table>
          <para/>
          <para>
            <embeddedLabel>
              <externalLink>
                <linkText>Design decision</linkText>
                <linkUri>http://aka.ms/P0anp3</linkUri>
              </externalLink>
            </embeddedLabel> - The decisions you make in all tasks of this step can be entered in the Settings worksheet.</para>
        </content>
      </section>
    </sections>
  </section>
  <section address="BKMK_Step4">
    <title>Step 4: Plan for server virtualization hosts</title>
    <content>
      <para>In this step, you’ll define the types of hosts you’ll need to host the virtual machines you plan to run on your virtualization fabric. You will want limit the number of host configurations, in some cases to a single configuration, to ease procurement and support costs. Additionally, purchasing the wrong equipment will drive up the deployment costs. </para>
      <para>
        <embeddedLabel>Cloud Platform System</embeddedLabel>
      </para>
      <para>Microsoft brings its experience running some of the largest datacenters and cloud services into a factory-integrated and fully validated converged system. Cloud Platform System (CPS) combines Microsoft’s proven software stack of <token>winblue_server_2</token>, <token>sc2012r2_1</token>, and <token>katal_2</token>, with Dell’s cloud server, storage and networking hardware. As a scalable building block for your cloud, CPS shortens the time to value and enables a consistent cloud experience.</para>
      <para>CPS provides a self-service, multi-tenant cloud environment for Platform-as-a-Service, Windows and Linux virtual machines, and includes optimized deployment packs for Microsoft applications like SQL Server, SharePoint, and Exchange. The factory integration decreases risk and complexity while accelerating deployment time from months to days. The simplified support process and automation of routine infrastructure tasks also frees up IT resources to focus on innovation.</para>
      <para>For additional information, see the <externalLink><linkText>Cloud Platform System</linkText><linkUri>http://www.microsoft.com/server-cloud/products/cloud-platform-system/</linkUri></externalLink> site.</para>
      <para>
        <embeddedLabel>Fast Track</embeddedLabel>
      </para>
      <para>Rather than designing your hardware (and software) configuration, you can purchase preconfigured hardware configurations from a variety of hardware partners through the Microsoft Private Cloud Fast Track program. </para>
      <para>The Fast Track program is a joint effort between Microsoft and its hardware partners to deliver validated, preconfigured solutions that reduce the complexity and risk of implementing a virtualization fabric and the tools to manage it. </para>
      <para>The Fast Track program provides flexibility of solutions and customer choice across hardware vendors’ technologies. It uses the core capabilities of the Windows Server operating system, Hyper-V technology, and Microsoft System Center to deliver the building blocks of a private cloud infrastructure as a service offering. </para>
      <para>
        <embeddedLabel>Additional information:</embeddedLabel>
      </para>
      <para>
        <externalLink>
          <linkText>Microsoft Private Cloud Fast Track site</linkText>
          <linkUri>http://www.microsoft.com/server-cloud/fast-track.aspx</linkUri>
        </externalLink>
      </para>
      <para/>
    </content>
    <sections>
      <section>
        <title>Task 1: Define compute configuration</title>
        <content>
          <para>In this task, you’ll determine the amount of memory, number of processors, and the version of Windows Server that are required for each host. The number of virtual machines to run on a host will be determined by the hardware components discussed in this section. </para>
          <para>
            <embeddedLabel>Note:</embeddedLabel> To ensure that your solution is fully supported, all hardware that you purchase must carry the Certified for Windows Server logo for the version of Windows Server you are running. </para>
          <para>The Certified for Windows Server logo demonstrates that a server system meets Microsoft’s highest technical bar for security, reliability and manageability. With other certified devices and drivers, it can support the roles, features, and interfaces for Cloud and Enterprise workloads and for business critical applications. </para>
          <para>For the latest list of Certified for Windows Server hardware, see the <externalLink><linkText>Windows Server Catalog</linkText><linkUri>http://www.windowsservercatalog.com/</linkUri></externalLink>.</para>
        </content>
        <sections>
          <section>
            <title>Task 1a: Define processor</title>
            <content>
              <para>Hyper-V presents the logical processors to each active virtual machine as one or more virtual processors. You can achieve additional run-time efficiency by using processors that support Second Level Address Translation (SLAT) technologies such as Extended Page Tables (EPTs) or Nested Page Tables (NPTs). Hyper-V in Windows Server 2012 R2 supports a maximum of 320 logical processors. </para>
              <para>
                <embeddedLabel>Considerations:</embeddedLabel>
              </para>
              <list class="bullet">
                <listItem>
                  <para>Workloads that are not processor intensive should be configured to use one virtual processor. Monitor host processor utilization over time to ensure that you’ve allocated processors for maximum effectiveness.</para>
                </listItem>
                <listItem>
                  <para>Workloads that are CPU intensive should be assigned two or more virtual processors. You can assign a maximum of 64 virtual processors to a virtual machine. The number of virtual processors recognized by the virtual machine is dependent on the guest operating system. For example, Windows Server 2008 with Service Pack 2 recognizes only four virtual processors.</para>
                </listItem>
              </list>
              <para>
                <embeddedLabel>Additional information:</embeddedLabel>
              </para>
              <para>
                <externalLink>
                  <linkText>Hyper-V Overview</linkText>
                  <linkUri>http://technet.microsoft.com/library/hh831531.aspx</linkUri>
                </externalLink>
              </para>
              <para>
                <externalLink>
                  <linkText>Performance Tuning for Hyper-V Servers</linkText>
                  <linkUri>http://msdn.microsoft.com/library/windows/hardware/dn567657</linkUri>
                </externalLink>
              </para>
            </content>
          </section>
          <section>
            <title>Task 1b: Define memory</title>
            <content>
              <para>The physical server requires sufficient memory for the host and running virtual machines. The host requires memory to efficiently perform I/O on behalf of the virtual machines and operations such as a virtual machine checkpoint. Hyper-V ensures that sufficient memory is available to the host, and it allows remaining memory to be assigned to the virtual machines. Virtual machines should be sized based on the needs of the expected load for each virtual machine.</para>
              <para>The hypervisor virtualizes the guest physical memory to isolate virtual machines from each other and to provide a contiguous, zero-based memory space for each guest operating system, the same as on non-virtualized systems. To ensure that you get maximum performance, use SLAT-based hardware to minimize the performance cost of memory virtualization.</para>
              <para>Size your virtual machine memory as you typically do for server applications on a physical computer. The amount of memory assigned to the virtual machine should allow the virtual machine to reasonably handle the expected load at ordinary and peak times because insufficient memory can significantly increase response times and CPU or I/O usage.</para>
              <para>Memory that has been allocated for a virtual machine reduces the amount of memory that is available to other virtual machines. If there is not enough available memory on the host, the virtual machine will not start. </para>
              <para>Dynamic Memory enables you to attain higher consolidation numbers with improved reliability for restart operations. This can lead to lower costs, especially in environments that have many idle or low-load virtual machines, such as pooled VDI environments. Dynamic Memory run-time configuration changes can reduce downtime and provide increased agility to respond to requirement changes. </para>
              <para>For more information about Dynamic Memory, see <link xlink:href="0a72c21e-9430-4b2c-a53b-87f23cf85c00#BKMK_Step2Task1b">Step 2, Task 1b: Define memory</link>, which discusses how to determine memory for a virtual machine. </para>
              <para>
                <embeddedLabel>Additional information:</embeddedLabel>
              </para>
              <para>
                <externalLink>
                  <linkText>Dynamic Memory Overview</linkText>
                  <linkUri>http://technet.microsoft.com/library/hh831766.aspx</linkUri>
                </externalLink>
              </para>
              <para>
                <externalLink>
                  <linkText>Virtual NUMA Overview</linkText>
                  <linkUri>http://technet.microsoft.com/library/dn282282.aspx</linkUri>
                </externalLink>
              </para>
            </content>
          </section>
          <section>
            <title>Task 1c: Define Windows Server operating system edition</title>
            <content>
              <para>The feature sets in Windows Server Standard and Windows Server Datacenter are exactly the same. Windows Server Datacenter provides an unlimited number of virtual machines. With Windows Server Standard, you are limited to two virtual machines.</para>
              <para>In Windows Server 2012 R2, the Automatic Virtual Machine Activation (AVMA) feature was added. AVMA lets you install virtual machines on a properly activated server without having to manage product keys for each virtual machine, even in disconnected environments. </para>
              <para>AVMA requires that the guest operating systems are running Windows Server 2012 R2 Datacenter, Windows Server 2012 R2 Standard, or Windows Server 2012 R2 Essentials. The following table compares the editions.</para>
              <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
                <thead>
                  <tr>
                    <TD>
                      <para>Edition</para>
                    </TD>
                    <TD>
                      <para>Advantages</para>
                    </TD>
                    <TD>
                      <para>Disadvantages</para>
                    </TD>
                  </tr>
                </thead>
                <tbody>
                  <tr>
                    <TD>
                      <para>Standard</para>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Includes all Windows Server features</para>
                        </listItem>
                        <listItem>
                          <para>Acceptable for non-virtualized or lightly virtualized environments</para>
                        </listItem>
                      </list>
                    </TD>
                    <TD>
                      <para>Limited to two virtual machines</para>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>Datacenter</para>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Includes all Windows Server features</para>
                        </listItem>
                        <listItem>
                          <para>Allows unlimited virtual machines</para>
                        </listItem>
                        <listItem>
                          <para>Acceptable for highly-virtualized private cloud environments</para>
                        </listItem>
                      </list>
                    </TD>
                    <TD>
                      <para>More expensive</para>
                    </TD>
                  </tr>
                </tbody>
              </table>
              <para/>
              <para>Hyper-V can be installed on a Server Core installation option of Windows Server. A Server Core installation reduces the space required on the disk, the potential attack surface, and especially the servicing requirements. A Server Core installation is managed by using the command line, Windows PowerShell, or by remote administration. </para>
              <para>It is important to review the licensing terms of any software you are planning to use. </para>
              <para>
                <embeddedLabel>
                  <placeholder>Microsoft Hyper-V Server</placeholder>
                </embeddedLabel>
              </para>
              <para>Microsoft Hyper-V Server provides a simple and reliable virtualization solution to help organizations improve their server utilization and reduce costs. It is a stand-alone product that contains only the Windows hypervisor, a Windows Server driver model, and virtualization components. </para>
              <para>Hyper-V Server can fit into customers’ existing IT environments and leverage their existing provisioning, management processes, and support tools. It supports the same hardware compatibility list as the corresponding editions of Windows Server, and it integrates fully with Microsoft System Center and Windows technologies such as Windows Update, Active Directory, and Failover Clustering. </para>
              <para>Hyper-V Server is a free download, and its installation is already-activated. However, every operating system that is running on a hosted virtual machine requires a proper license. </para>
              <para>
                <embeddedLabel>Additional information:</embeddedLabel>
              </para>
              <para>
                <externalLink>
                  <linkText>Automatic Virtual Machine Activation</linkText>
                  <linkUri>http://technet.microsoft.com/library/dn303421.aspx</linkUri>
                </externalLink>
              </para>
              <para>
                <externalLink>
                  <linkText>Microsoft Hyper-V Server</linkText>
                  <linkUri>http://technet.microsoft.com/library/hh833684.aspx</linkUri>
                </externalLink>
              </para>
              <para>
                <externalLink>
                  <linkText>Manage Hyper-V Server Remotely</linkText>
                  <linkUri>http://technet.microsoft.com/library/jj647785(v=ws.11)</linkUri>
                </externalLink>
              </para>
            </content>
          </section>
        </sections>
      </section>
      <section>
        <title>Task 2: Define network configuration</title>
        <content>
          <para>In Step 2, Task 2 above, we discussed the design considerations for the virtual machine networking. Now we are going to discuss the networking consideration for the host. There are several types of network traffic that you must consider and plan for when you deploy Hyper-V. You should design your network configuration with the following goals in mind:</para>
          <list class="bullet">
            <listItem>
              <para>To ensure network QoS</para>
            </listItem>
            <listItem>
              <para>To provide network redundancy</para>
            </listItem>
            <listItem>
              <para>To isolate traffic to defined networks</para>
            </listItem>
          </list>
        </content>
        <sections>
          <section>
            <title>Task 2a: Define network traffic types</title>
            <content>
              <para>When you deploy a Hyper-V cluster, you must plan for several types of network traffic. The following table summarizes the traffic types. </para>
              <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
                <thead>
                  <tr>
                    <TD>
                      <para>Traffic type</para>
                    </TD>
                    <TD>
                      <para>Description</para>
                    </TD>
                  </tr>
                </thead>
                <tbody>
                  <tr>
                    <TD>
                      <para>Management</para>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Provides connectivity between the server that is running Hyper-V and basic infrastructure functionality</para>
                        </listItem>
                        <listItem>
                          <para>Used to manage the Hyper-V host operating system and virtual machines</para>
                        </listItem>
                      </list>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>Cluster and CSVs</para>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Used for internode cluster communication such as the cluster heartbeat and Cluster Shared Volumes (CSV) redirection</para>
                        </listItem>
                        <listItem>
                          <para>Only when Hyper-V has been deployed using Failover Clustering</para>
                        </listItem>
                      </list>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>Live migration</para>
                    </TD>
                    <TD>
                      <para>Used for virtual machine live migration and shared nothing live migration</para>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>Storage</para>
                    </TD>
                    <TD>
                      <para>Used for SMB traffic or for iSCSI traffic</para>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>Replica</para>
                    </TD>
                    <TD>
                      <para>Used for virtual machine replication traffic through the Hyper-V Replica feature</para>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>Virtual machine (tenant) traffic</para>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Used for virtual machine connectivity</para>
                        </listItem>
                        <listItem>
                          <para>Typically requires external network connectivity to service client requests</para>
                        </listItem>
                      </list>
                      <para>
                        <embeddedLabel>Note:</embeddedLabel> See <link xlink:href="0a72c21e-9430-4b2c-a53b-87f23cf85c00#BKMK_Step2">Step 2: Plan for virtual machine configuration</link> for a list of virtual machine traffic types.</para>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>Backup</para>
                    </TD>
                    <TD>
                      <para>Used to back up virtual hard disk files</para>
                    </TD>
                  </tr>
                </tbody>
              </table>
              <para/>
            </content>
          </section>
          <section>
            <title>Task 2b: Define network traffic performance options</title>
            <content>
              <para>Each network traffic type will have maximum and minimum bandwidth requirements and minimum latency requirements. Following are the strategies that can be used to meet different network performance requirements. </para>
            </content>
            <sections>
              <section>
                <title>Policy-based QoS</title>
                <content>
                  <para>When you deploy a Hyper-V cluster, you need a minimum of six traffic patterns or networks. Each network requires network redundancy. To start, you are talking about 12 network adapters in the host.  It is possible to install multiple quad network adapters, but at some point you are going to run out of slots in your host. </para>
                  <para>Networking equipment is getting faster. Not so long ago, 1 GB network adapters were the top-of-the-line. 10 GB adapters in servers are becoming more common, and prices to support 10 GB infrastructures are becoming more reasonable. </para>
                  <para>Installing two 10 GB teamed network adapters provides more bandwidth than two quad 1 GB adapters, requires fewer switch ports, and simplifies your cabling needs. As you converge more of your network traffic types on the teamed 10 GB network adapters, policy-based QoS allows you to manage the network traffic to properly meet the need of your virtualization infrastructure. </para>
                  <para>Policy-based QoS enables you to specify network bandwidth control, based on application type, users, and computers. QoS policies allow you meet the service requirements of a workload or an application by measuring network bandwidth, detecting changing network conditions (such as congestion or availability of bandwidth), and prioritizing (or throttling) network traffic. </para>
                  <para>In addition to the ability to enforce maximum bandwidth, QoS policies in Windows Server 2012 R2 provide a new bandwidth management feature: minimum bandwidth. Unlike maximum bandwidth, which is a bandwidth cap, minimum bandwidth is a bandwidth floor, and it assigns a certain amount of bandwidth to a given type of traffic. You can simultaneously implement minimum and maximum bandwidth limits.</para>
                  <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
                    <thead>
                      <tr>
                        <TD>
                          <para>Advantages</para>
                        </TD>
                        <TD>
                          <para>Disadvantages</para>
                        </TD>
                      </tr>
                    </thead>
                    <tbody>
                      <tr>
                        <TD>
                          <list class="bullet">
                            <listItem>
                              <para>Managed by Group Policy </para>
                            </listItem>
                            <listItem>
                              <para>Easily applied to VLANs to provide proper bandwidth settings when multiple VLANs are running on the network adapter or using NIC Teaming</para>
                            </listItem>
                            <listItem>
                              <para>Policy-based QoS can be applied to IPsec traffic</para>
                            </listItem>
                          </list>
                        </TD>
                        <TD>
                          <list class="bullet">
                            <listItem>
                              <para>Does not provide bandwidth management to traffic that is using a virtual switch</para>
                            </listItem>
                            <listItem>
                              <para>Hyper-V hosts must be domain joined</para>
                            </listItem>
                            <listItem>
                              <para>Software-based QoS policies and hardware-based QoS policies (DCB) should not be used at the same time</para>
                            </listItem>
                          </list>
                        </TD>
                      </tr>
                    </tbody>
                  </table>
                  <para>
                    <embeddedLabel>Additional information:</embeddedLabel>
                  </para>
                  <para>
                    <externalLink>
                      <linkText>Quality of Server (QoS) Overview</linkText>
                      <linkUri>http://technet.microsoft.com/library/hh831679.aspx</linkUri>
                    </externalLink>
                  </para>
                  <para>
                    <externalLink>
                      <linkText>Policy-based Quality of Service</linkText>
                      <linkUri>http://technet.microsoft.com/library/jj159288.aspx</linkUri>
                    </externalLink>
                  </para>
                </content>
              </section>
              <section>
                <title>Data Center Bridging</title>
                <content>
                  <para>Data Center Bridging (DCB), provides hardware-based bandwidth allocation to a specific type of traffic and enhances Ethernet transport reliability with the use of priority-based flow control. DCB is recommended when using FCoE and iSCSI. </para>
                  <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
                    <thead>
                      <tr>
                        <TD>
                          <para>Advantages</para>
                        </TD>
                        <TD>
                          <para>Disadvantages</para>
                        </TD>
                      </tr>
                    </thead>
                    <tbody>
                      <tr>
                        <TD>
                          <list class="bullet">
                            <listItem>
                              <para>Support for Microsoft iSCSI</para>
                            </listItem>
                            <listItem>
                              <para>Support for FCoE</para>
                            </listItem>
                          </list>
                        </TD>
                        <TD>
                          <list class="bullet">
                            <listItem>
                              <para>Hardware investments required, including:</para>
                              <list class="bullet">
                                <listItem>
                                  <para>DCB-capable Ethernet adapters</para>
                                </listItem>
                                <listItem>
                                  <para>DCB-capable hardware switches</para>
                                </listItem>
                              </list>
                            </listItem>
                            <listItem>
                              <para>Complex to deploy and manage</para>
                            </listItem>
                            <listItem>
                              <para>Does not provide bandwidth management for virtual switch traffic</para>
                            </listItem>
                            <listItem>
                              <para>Software-based QoS policies and DCB policies  should not be used at the same time</para>
                            </listItem>
                          </list>
                        </TD>
                      </tr>
                    </tbody>
                  </table>
                  <para/>
                  <para>
                    <embeddedLabel>Additional information:</embeddedLabel>
                  </para>
                  <para>
                    <externalLink>
                      <linkText>Data Center Bridging (DCB) Overview</linkText>
                      <linkUri>http://technet.microsoft.com/library/hh849179.aspx</linkUri>
                    </externalLink>
                  </para>
                </content>
              </section>
              <section>
                <title>SMB Direct</title>
                <content>
                  <para>
                    <externalLink>
                      <linkText>SMB Direct</linkText>
                      <linkUri>http://technet.microsoft.com/library/jj134210.aspx</linkUri>
                    </externalLink> (SMB over remote direct memory access or RDMA) is a storage protocol in Windows Server 2012 R2. It enables direct memory-to-memory data transfers between the server and storage. It requires minimal CPU usage, and it uses standard RDMA-capable network adapters. This provides extremely fast responses to network requests, and as a result, this makes remote file storage response times on par with directly attached block storage. </para>
                  <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
                    <thead>
                      <tr>
                        <TD>
                          <para>Advantages</para>
                        </TD>
                        <TD>
                          <para>Disadvantages</para>
                        </TD>
                      </tr>
                    </thead>
                    <tbody>
                      <tr>
                        <TD>
                          <list class="bullet">
                            <listItem>
                              <para>Increased throughput: Leverages the full throughput of high speed networks where the network adapters coordinate the transfer of large amounts of data at line speed</para>
                            </listItem>
                            <listItem>
                              <para>Low latency: Provides extremely fast responses to network requests, and as a result, makes remote file storage seem like it is directly attached block storage</para>
                            </listItem>
                            <listItem>
                              <para>Low CPU utilization: Uses fewer CPU cycles when transferring data over the network, which frees up more CPU cycles for the virtual machines</para>
                            </listItem>
                            <listItem>
                              <para>Live migration can be configured to use SMB Direct for faster live migrations. </para>
                            </listItem>
                            <listItem>
                              <para>Enabled by default on the host</para>
                            </listItem>
                            <listItem>
                              <para>The SMB client automatically detects and uses multiple network connections if an appropriate configuration is identified</para>
                            </listItem>
                            <listItem>
                              <para>Configure SMB bandwidth management to set limits for live migration, virtual machines, and default storage traffic</para>
                            </listItem>
                            <listItem>
                              <para>SMB Multichannel does not require RDMA-supported adapters</para>
                            </listItem>
                          </list>
                        </TD>
                        <TD>
                          <list class="bullet">
                            <listItem>
                              <para>RDMA-enabled network adapters are not compatible with NIC Teaming</para>
                            </listItem>
                            <listItem>
                              <para>Requires two or more RDMA network adapters to be deployed in each host to provide high availability</para>
                            </listItem>
                            <listItem>
                              <para>Currently limited to the following types of network adapters:</para>
                              <list class="bullet">
                                <listItem>
                                  <para>iWARP</para>
                                </listItem>
                                <listItem>
                                  <para>Infiniband</para>
                                </listItem>
                                <listItem>
                                  <para>RoCE</para>
                                </listItem>
                              </list>
                            </listItem>
                            <listItem>
                              <para>RDMA with RoCE requires DCB for flow control.</para>
                            </listItem>
                          </list>
                        </TD>
                      </tr>
                    </tbody>
                  </table>
                </content>
              </section>
              <section>
                <title>Receive Segment Coalescing</title>
                <content>
                  <para>
                    <externalLink>
                      <linkText>Receive segment coalescing (RSC)</linkText>
                      <linkUri>http://technet.microsoft.com/library/hh997024.aspx</linkUri>
                    </externalLink> reduces CPU utilization for inbound network processing by offloading tasks from the CPU to an RSC-capable network adapter.</para>
                  <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
                    <thead>
                      <tr>
                        <TD>
                          <para>Advantages</para>
                        </TD>
                        <TD>
                          <para>Disadvantages</para>
                        </TD>
                      </tr>
                    </thead>
                    <tbody>
                      <tr>
                        <TD>
                          <list class="bullet">
                            <listItem>
                              <para>Improves the scalability of the servers by reducing the overhead for processing a large amount of inbound network traffic</para>
                            </listItem>
                            <listItem>
                              <para>Minimizes the CPU cycles that are spent for network storage and live migrations</para>
                            </listItem>
                          </list>
                        </TD>
                        <TD>
                          <list class="bullet">
                            <listItem>
                              <para>Requires a RSC-capable network adapter</para>
                            </listItem>
                            <listItem>
                              <para>Does not provide significant improvement for send-intensive workloads</para>
                            </listItem>
                            <listItem>
                              <para>Not compatible with IPsec encrypted traffic</para>
                            </listItem>
                            <listItem>
                              <para>Applies to the host traffic. To apply RSC to virtual machine traffic, the virtual machine must be running Windows Server 2012 R2 and configured with a SR-IOV network adapter.</para>
                            </listItem>
                            <listItem>
                              <para>Not enabled by default on servers upgraded to Windows Server 2012 R2</para>
                            </listItem>
                          </list>
                        </TD>
                      </tr>
                    </tbody>
                  </table>
                </content>
              </section>
              <section>
                <title>Receive Side Scaling</title>
                <content>
                  <para>
                    <externalLink>
                      <linkText>Receive-side scaling (RSS)</linkText>
                      <linkUri>http://technet.microsoft.com/library/hh997036.aspx</linkUri>
                    </externalLink> enables network adapters to distribute the kernel-mode network processing load across multiple processor cores in multiple core computers. The distribution of this processing makes it possible to support higher network traffic loads than would be possible if only a single core is used. RSS achieves this by spreading the network processing load across many processors and actively load balancing traffic that is terminated by the Transmission Control Protocol (TCP).</para>
                  <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
                    <thead>
                      <tr>
                        <TD>
                          <para>Advantages</para>
                        </TD>
                        <TD>
                          <para>Disadvantages</para>
                        </TD>
                      </tr>
                    </thead>
                    <tbody>
                      <tr>
                        <TD>
                          <list class="bullet">
                            <listItem>
                              <para>Spreads monitoring interruptions over multiple processors, so a single processor is not required to handle all I/O interruptions, which were common with earlier versions of Windows Server.</para>
                            </listItem>
                            <listItem>
                              <para>Works with NIC Teaming</para>
                            </listItem>
                            <listItem>
                              <para>Works with User Datagram Protocol (UDP) traffic</para>
                            </listItem>
                          </list>
                        </TD>
                        <TD>
                          <list class="bullet">
                            <listItem>
                              <para>Requires a RSS-capable network adapter</para>
                            </listItem>
                            <listItem>
                              <para>Disabled if the virtual network adapter is bound to a virtual switch. VMQ is used instead of RSS for network adapters bound to a virtual switch.</para>
                            </listItem>
                          </list>
                        </TD>
                      </tr>
                    </tbody>
                  </table>
                </content>
              </section>
              <section>
                <title>SR-IOV</title>
                <content>
                  <para>Hyper-V supports <externalLink><linkText>SR-IOV</linkText><linkUri>http://technet.microsoft.com/library/hh831410.aspx#BKMK_SR</linkUri></externalLink>-capable network devices and allows the direct assignment of an SR-IOV virtual function of a physical network adapter to a virtual machine. This increases network throughput, reduces network latency, and reduces the host CPU overhead that is required for processing network traffic. </para>
                  <para>For additional information about SR-IOV, see <link xlink:href="0a72c21e-9430-4b2c-a53b-87f23cf85c00#BKMK_Step2Task2b">Step 2, Task 2b: Define network traffic performance options</link> above.</para>
                </content>
              </section>
            </sections>
          </section>
          <section>
            <title>Task 2c: Define network traffic high availability and bandwidth aggregation strategy</title>
            <content>
              <para>NIC Teaming, also known as load balancing and failover (LBFO), allows multiple network adapters to be placed into a team for the purposes of bandwidth aggregation and traffic failover. This helps maintain connectivity in the event of a network component failure.</para>
              <para>This feature has been available from network adapter vendors. Introduced in Windows Server 2012, NIC Teaming is included as a feature in the Windows Server operating system.</para>
              <para>NIC Teaming is compatible with all networking capabilities in Windows Server 2012 R2 with three exceptions:</para>
              <list class="bullet">
                <listItem>
                  <para>SR-IOV</para>
                </listItem>
                <listItem>
                  <para>RDMA</para>
                </listItem>
                <listItem>
                  <para>802.1X authentication</para>
                </listItem>
              </list>
              <para>From a scalability perspective, in Windows Server 2012 R2, a minimum of 1 and a maximum of 32 network adapters can be added to a single team. An unlimited number of teams can be created on a single host.</para>
              <para>
                <embeddedLabel>Additional information:</embeddedLabel>
              </para>
              <para>
                <externalLink>
                  <linkText>NIC Teaming Overview</linkText>
                  <linkUri>http://technet.microsoft.com/library/hh831648.aspx</linkUri>
                </externalLink>
              </para>
              <para>
                <externalLink>
                  <linkText>Microsoft Virtual Academy: NIC Teaming in Windows Server 2012</linkText>
                  <linkUri>http://technet.microsoft.com/video/microsoft-virtual-academy-nic-teaming-in-windows-server-2012.aspx</linkUri>
                </externalLink>
              </para>
              <para>
                <externalLink>
                  <linkText>NIC Teaming (NetLBFO) Cmdlets in Windows PowerShell</linkText>
                  <linkUri>http://technet.microsoft.com/library/jj130849.aspx</linkUri>
                </externalLink>
              </para>
              <para>
                <externalLink>
                  <linkText>Windows Server 2012 R2 NIC Teaming (LBFO) Deployment and Management</linkText>
                  <linkUri>http://www.microsoft.com/download/details.aspx?id=40319</linkUri>
                </externalLink>
              </para>
              <para>
                <externalLink>
                  <linkText>Converged Data Center with File Server Storage</linkText>
                  <linkUri>http://technet.microsoft.com/library/hh831738.aspx</linkUri>
                </externalLink>
              </para>
            </content>
          </section>
          <section>
            <title>Task 2d: Define network traffic isolation and security strategy</title>
            <content>
              <para>Each network traffic type may have different security requirements for functions such as isolation and encryption. The following table lists the strategies that can be used to meet various security requirements.</para>
              <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
                <thead>
                  <tr>
                    <TD>
                      <para>Strategy</para>
                    </TD>
                    <TD>
                      <para>Advantages</para>
                    </TD>
                    <TD>
                      <para>Disadvantages</para>
                    </TD>
                  </tr>
                </thead>
                <tbody>
                  <tr>
                    <TD>
                      <para>Encryption (IPsec)</para>
                    </TD>
                    <TD>
                      <para>Traffic is secured while traversing the wire</para>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Performance impact to encrypt and decrypt traffic</para>
                        </listItem>
                        <listItem>
                          <para>Complex to configure, manage, and troubleshoot</para>
                        </listItem>
                        <listItem>
                          <para>Incorrect IPsec configuration changes can cause network disruptions or traffic to not be properly encrypted</para>
                        </listItem>
                      </list>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>Separate physical networks</para>
                    </TD>
                    <TD>
                      <para>Network is physically separated</para>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Requires additional network adapters to be installed in the host</para>
                        </listItem>
                        <listItem>
                          <para>If network requires high availability, two or more network adapters are required for each network.</para>
                        </listItem>
                      </list>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>Virtual local area network (VLAN)</para>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Isolates traffic by using an assigned VLAN ID </para>
                        </listItem>
                        <listItem>
                          <para>Support for VLAN Trunking Protocol</para>
                        </listItem>
                        <listItem>
                          <para>Support for private VLANs</para>
                        </listItem>
                        <listItem>
                          <para>Already used by many enterprise customers</para>
                        </listItem>
                      </list>
                    </TD>
                    <TD>
                      <list class="bullet">
                        <listItem>
                          <para>Limited to 4094 VLANs, and most switches support only 1000 VLANs </para>
                        </listItem>
                        <listItem>
                          <para>Requires additional configuration and management of networking equipment</para>
                        </listItem>
                        <listItem>
                          <para>VLANs cannot span multiple Ethernet subnets, which limits the number of nodes in a single VLAN and restricts the placement of virtual machines, based on physical location.</para>
                        </listItem>
                      </list>
                    </TD>
                  </tr>
                </tbody>
              </table>
              <para/>
            </content>
          </section>
          <section>
            <title>Task 2e: Define virtual network adapters</title>
            <content>
              <para>With an understanding of the types of traffic required by the virtualization server hosts, and the performance, availability, and security strategies for the traffic, you can determine how many physical network adapters are required for each host and the types of network traffic that will be transmitted over each adapter.</para>
            </content>
          </section>
          <section>
            <title>Task 2f: Define virtual switches</title>
            <content>
              <para>To connect a virtual machine to a network, you need to connect the network adapter to a Hyper-V virtual switch. </para>
              <para>There are three types of virtual switches that can be created in Hyper-V:</para>
              <list class="bullet">
                <listItem>
                  <para>
                    <embeddedLabel>External virtual switch</embeddedLabel> </para>
                  <para>Use an external virtual switch when you want to provide virtual machines with access to a physical network to communicate with externally located servers and clients. This type of virtual switch also allows virtual machines on the same host to communicate with each other. This type of network may also be available for use by the host operating system, depending on how you configure the networking.</para>
                  <para>
                    <embeddedLabel>Important:</embeddedLabel> A physical network adapter can only be bound to one virtual switch at a time. </para>
                </listItem>
                <listItem>
                  <para>
                    <embeddedLabel>Internal virtual switch</embeddedLabel>
                  </para>
                  <para>Use an internal virtual switch when you want to allow communication between virtual machines on the same host and between virtual machines and the host operating system. This type of virtual switch is commonly used to build a test environment in which you need to connect to the virtual machines from the host operating system. An internal virtual switch is not bound to a physical network adapter. As a result, an internal virtual network is isolated from external network traffic.</para>
                </listItem>
                <listItem>
                  <para>
                    <embeddedLabel>Private virtual switch</embeddedLabel>
                  </para>
                  <para>Use a private virtual switch when you want to allow communication only between virtual machines on the same host. A private virtual switch is not bound to a physical network adapter. A private virtual switch is isolated from all external network traffic on the virtualization server, and from any network traffic between the host operating system and the external network. This type of network is useful when you need to create an isolated networking environment, such as an isolated test domain. </para>
                  <para>
                    <embeddedLabel>Note:</embeddedLabel> Private and internal virtual switches do not benefit from hardware acceleration features that are available to a virtual machine that is connected to an external virtual switch</para>
                </listItem>
              </list>
              <para>
                <embeddedLabel>
                  <externalLink>
                    <linkText>Design decision</linkText>
                    <linkUri>http://aka.ms/P0anp3</linkUri>
                  </externalLink>
                </embeddedLabel> - The decisions you make in all the tasks of this step can be entered in the Virtualization hosts worksheets.</para>
              <para>
                <embeddedLabel>Tip:</embeddedLabel> The name of virtual switches on different hosts that connect to the same network should have the same name. This eliminates confusion about which virtual switch a virtual machine should be connected to and it simplifies moving a virtual machine from one host to another. The <system>Move-VM</system> Windows PowerShell cmdlet will fail if the same virtual switch name is not found on the destination host.</para>
            </content>
          </section>
        </sections>
      </section>
      <section>
        <title>Task 3: Define storage configuration</title>
        <content>
          <para>In addition to the storage required for the host operating system, each host requires access to storage where the virtual machine configuration files and virtual hard disks are stored. This task will focus on the virtual machine storage.</para>
        </content>
        <sections>
          <section>
            <title>Task 3a: Define data types</title>
            <content>
              <para>The following are the sample data types you need to consider for your storage requirements. </para>
              <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
                <thead>
                  <tr>
                    <TD>
                      <para>Data type</para>
                    </TD>
                    <TD>
                      <para>Storage location of data type</para>
                    </TD>
                  </tr>
                </thead>
                <tbody>
                  <tr>
                    <TD>
                      <para>Host operating system files</para>
                    </TD>
                    <TD>
                      <para>Typically on a local hard drive</para>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>Host page file and crash dumps in Windows</para>
                    </TD>
                    <TD>
                      <para>Typically on a local hard drive</para>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>Failover cluster shared state</para>
                    </TD>
                    <TD>
                      <para>Shared network storage or cluster shared volume</para>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>Virtual hard disk files and virtual machine configuration file</para>
                    </TD>
                    <TD>
                      <para>Typically on shared network storage or cluster shared volume</para>
                    </TD>
                  </tr>
                </tbody>
              </table>
              <para/>
              <para>The remainder of this step is focused on the storage required for the virtual machines. </para>
            </content>
          </section>
          <section address="BKMK_Step4Task3b">
            <title>Task 3b: Storage options</title>
            <content>
              <para>The following options are available for storing the virtual machine configuration files and virtual hard disks.</para>
            </content>
            <sections>
              <section>
                <title>Option1: Direct-attached storage</title>
                <content>
                  <para>Direct-attached storage refers to a computer storage system that is directly attached to your server, instead of being attached directly to a network. Direct-attached storage is not limited to only internal storage. It can also use an external disk enclosure that contains hard disk drives, including just-a-bunch-of-disks (JBOD) enclosures and enclosures that are connected through SAS or another disk controller.</para>
                  <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
                    <thead>
                      <tr>
                        <TD>
                          <para>Advantages</para>
                        </TD>
                        <TD>
                          <para>Disadvantages</para>
                        </TD>
                      </tr>
                    </thead>
                    <tbody>
                      <tr>
                        <TD>
                          <list class="bullet">
                            <listItem>
                              <para>Does not require a storage network</para>
                            </listItem>
                            <listItem>
                              <para>Fast disk I/O, so there is no need for storage requests to travel over a network</para>
                            </listItem>
                            <listItem>
                              <para>Can be internal storage or an external disk enclosure, including JBODs</para>
                            </listItem>
                            <listItem>
                              <para>You can use JBOD with the <externalLink><linkText>Storage Spaces</linkText><linkUri>http://technet.microsoft.com/library/hh831739.aspx</linkUri></externalLink> technology to combine all of your physical disks into a storage pool, and then create one or more virtual disks (called Storage Spaces) out of the free space in the pool.</para>
                            </listItem>
                            <listItem>
                              <para>JBOD are typically less expensive and often more flexible and easier to manage than RAID enclosures because they use the Windows or Windows Server operating systems to manage the storage instead of using dedicated RAID adapters.</para>
                            </listItem>
                          </list>
                        </TD>
                        <TD>
                          <list class="bullet">
                            <listItem>
                              <para>Limited in the number of servers that can be attached to the external disk enclosure</para>
                            </listItem>
                            <listItem>
                              <para>Only external shared storage, such as shared SAS with Storage Spaces, provides support for Failover Clustering </para>
                            </listItem>
                          </list>
                        </TD>
                      </tr>
                    </tbody>
                  </table>
                </content>
              </section>
              <section>
                <title>Option 2: Network-attached storage</title>
                <content>
                  <para>Network-attached storage devices connect storage to a network where they are accessed through file shares. Unlike direct-attached storage, they are not directly attached to the computer.</para>
                  <para>Network-attached storage devices support Ethernet connections, and they typically allow an administrator to manage disk space, set disk quotas, provide security, and use checkpoint technologies. Network-attached storage devices support multiple protocols. These include network-attached file systems, Common Internet File Systems (CIFS), and Server Message Block (SMB).</para>
                  <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
                    <thead>
                      <tr>
                        <TD>
                          <para>Advantages</para>
                        </TD>
                        <TD>
                          <para>Disadvantages</para>
                        </TD>
                      </tr>
                    </thead>
                    <tbody>
                      <tr>
                        <TD>
                          <list class="bullet">
                            <listItem>
                              <para>Simpler to set up than SAN storage, requiring less dedicated storage hardware</para>
                            </listItem>
                            <listItem>
                              <para>Plug and play </para>
                            </listItem>
                            <listItem>
                              <para>Can use existing Ethernet network</para>
                            </listItem>
                          </list>
                        </TD>
                        <TD>
                          <list class="bullet">
                            <listItem>
                              <para>Network attached storage device must support SMB 3.0—CIFS is not supported</para>
                            </listItem>
                            <listItem>
                              <para>Not directly attached to the host servers that are accessing the storage</para>
                            </listItem>
                            <listItem>
                              <para>Slower than other options</para>
                            </listItem>
                            <listItem>
                              <para>Typically require a dedicated network for optimal performance</para>
                            </listItem>
                            <listItem>
                              <para>Limited management and functionality</para>
                            </listItem>
                            <listItem>
                              <para>Hyper-V supports network-attached storage devices that support SMB 3.0, SMB 2.0, and CIFS are not supported</para>
                            </listItem>
                            <listItem>
                              <para>May or may not support RDMA</para>
                            </listItem>
                          </list>
                        </TD>
                      </tr>
                    </tbody>
                  </table>
                </content>
              </section>
              <section>
                <title>Option 3: Storage area network</title>
                <content>
                  <para>A storage area network (SAN) is a dedicated network that allows you to share storage. A SAN consists of a storage device, the interconnecting network infrastructure (switches, host bus adapters, and cabling), and servers that are connected to this network. SAN devices provide continuous and fast access to large amounts of data. The communication and data transfer mechanism for a given deployment is commonly known as a storage fabric.</para>
                  <para>A SAN uses a separate network, and it is generally not accessible by other devices through the local area network. A SAN can be managed by using Storage Management Initiative Specification (SMI-S), Simple Network Management Protocol (SNMP), or a proprietary management protocol. </para>
                  <para>A SAN does not provide file abstraction, only block-level operations. The most common SAN protocols used are iSCSI, Fiber Channel, and Fiber Channel over Ethernet (FCoE). An SMI-S or a proprietary management protocol can deliver additional capabilities, such as disk zoning, disk mapping, LUN masking, and fault management.</para>
                  <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
                    <thead>
                      <tr>
                        <TD>
                          <para>Advantages</para>
                        </TD>
                        <TD>
                          <para>Disadvantages</para>
                        </TD>
                      </tr>
                    </thead>
                    <tbody>
                      <tr>
                        <TD>
                          <list class="bullet">
                            <listItem>
                              <para>SAN uses a separate network, so there is limited impact on the data network</para>
                            </listItem>
                            <listItem>
                              <para>Provides continuous and fast access to large amounts of data</para>
                            </listItem>
                            <listItem>
                              <para>Typically provides additional features such as data protection and replication</para>
                            </listItem>
                            <listItem>
                              <para>Can be shared amongst various teams</para>
                            </listItem>
                            <listItem>
                              <para>Support for Virtual Fibre Channel for direct access to storage LUNs</para>
                            </listItem>
                            <listItem>
                              <para>Support for guest clustering</para>
                            </listItem>
                            <listItem>
                              <para>Virtual machines that need access to data volumes greater than 64 TB can use virtual Fibre Channel for direct LUN access</para>
                            </listItem>
                          </list>
                        </TD>
                        <TD>
                          <list class="bullet">
                            <listItem>
                              <para>Expensive</para>
                            </listItem>
                            <listItem>
                              <para>Requires specialized skills to deploy, manage, and maintain</para>
                            </listItem>
                            <listItem>
                              <para>HBA or FCoE network adapters need to be installed in each host.</para>
                            </listItem>
                            <listItem>
                              <para>Migrating a Hyper-V cluster requires additional planning and limited downtime.</para>
                            </listItem>
                            <listItem>
                              <para>To provide bandwidth management for FCoE traffic, a hardware QoS policy that uses datacenter bridging is required.</para>
                            </listItem>
                            <listItem>
                              <para>FCoE traffic is not routable.</para>
                            </listItem>
                          </list>
                        </TD>
                      </tr>
                    </tbody>
                  </table>
                </content>
              </section>
              <section>
                <title>Option 4: Server Message Block 3.0 file shares</title>
                <content>
                  <para>Hyper-V can store virtual machine files, such as configuration files, virtual hard disk files, and checkpoints, in file shares that use the Server Message Block (SMB) 3.0 protocol. The file shares will typically be on a scale-out file server to provide redundancy. When running a scale-out file server, if one nod is down, the file shares are still available from the other nodes in the scale-out file server.</para>
                  <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
                    <thead>
                      <tr>
                        <TD>
                          <para>Advantages</para>
                        </TD>
                        <TD>
                          <para>Disadvantages</para>
                        </TD>
                      </tr>
                    </thead>
                    <tbody>
                      <tr>
                        <TD>
                          <list class="bullet">
                            <listItem>
                              <para>Option to use existing networks and protocols</para>
                            </listItem>
                            <listItem>
                              <para>SMB Multichannel provides an aggregation of network bandwidth and fault tolerance when multiple paths are available between the server running Hyper-V and the SMB 3.0 file share. </para>
                            </listItem>
                            <listItem>
                              <para>You can use JBOD with the <externalLink><linkText>Storage Spaces</linkText><linkUri>http://technet.microsoft.com/library/hh831739.aspx</linkUri></externalLink> technology to combine all of your physical disks into a storage pool, and then create one or more virtual disks (called Storage Spaces) out of the free space in the pool.</para>
                            </listItem>
                            <listItem>
                              <para>SMB Multichannel can be used for virtual machine migrations.</para>
                            </listItem>
                            <listItem>
                              <para>Less expensive than SAN deployments</para>
                            </listItem>
                            <listItem>
                              <para>Flexible storage configurations on the file server running Windows Server</para>
                            </listItem>
                            <listItem>
                              <para>Separate Hyper-V services from storage services, which enables you to scale each service as needed</para>
                            </listItem>
                            <listItem>
                              <para>Provides flexibility when upgrading to the next version when running a Hyper-V cluster. You can upgrade the servers running Hyper-V or the scale-out file servers in any order without downtime. You need enough capacity in the cluster to remove one or two nodes to perform the upgrade.</para>
                            </listItem>
                            <listItem>
                              <para>Scale-out file server provides support for shared VHDX</para>
                            </listItem>
                            <listItem>
                              <para>SMB bandwidth management allows you to set limits for live migration, virtual hard disk, and default storage traffic.</para>
                            </listItem>
                            <listItem>
                              <para>Support for SMB traffic encryption with minimal impact on performance</para>
                            </listItem>
                            <listItem>
                              <para>Save disk space with data deduplication for VDI deployments</para>
                            </listItem>
                            <listItem>
                              <para>Does not require specialized skills to deploy, manage, and maintain</para>
                            </listItem>
                          </list>
                        </TD>
                        <TD>
                          <list class="bullet">
                            <listItem>
                              <para>I/O performance is not as fast as in SAN deployments.</para>
                            </listItem>
                            <listItem>
                              <para>Data Deduplication is not supported on running virtual machine files, except for VDI deployments.</para>
                            </listItem>
                          </list>
                        </TD>
                      </tr>
                    </tbody>
                  </table>
                  <para>
                    <embeddedLabel>SMB Direct</embeddedLabel>
                  </para>
                  <para>SMB Direct works as part of the SMB file shares. SMB Direct requires network adapters and switches that support RDMA to provide full speed with low latency storage access. SMB Direct enables remote file servers to resemble local and direct-attached storage. In addition to the benefits of SMB, SMB Direct has the following advantages and disadvantages.</para>
                  <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
                    <thead>
                      <tr>
                        <TD>
                          <para>Advantages</para>
                        </TD>
                        <TD>
                          <para>Disadvantages</para>
                        </TD>
                      </tr>
                    </thead>
                    <tbody>
                      <tr>
                        <TD>
                          <list class="bullet">
                            <listItem>
                              <para>Functions at full speed with low latency, while using very little CPU</para>
                            </listItem>
                            <listItem>
                              <para>Enables a scale-out file server to deliver storage performance and resiliency similar to a traditional SAN by using Microsoft storage solutions and inexpensive shared direct-attached storage</para>
                            </listItem>
                            <listItem>
                              <para>Provides the fastest option for live migrations and storage migrations</para>
                            </listItem>
                          </list>
                        </TD>
                        <TD>
                          <list class="bullet">
                            <listItem>
                              <para>Not supported with NIC Teaming</para>
                            </listItem>
                            <listItem>
                              <para>Two or more RDMA-enabled network adapters are required for redundant connections to the storage.</para>
                            </listItem>
                          </list>
                        </TD>
                      </tr>
                    </tbody>
                  </table>
                  <para/>
                  <mediaLink>
                    <image xlink:href="a95461e5-38b4-41b8-a3ea-95436776578d"/>
                  </mediaLink>
                  <para>
                    <embeddedLabel>Figure  SEQ Figure \* ARABIC 3:</embeddedLabel> <externalLink><linkText>Sample scale-out file server that uses converged networking with RDMA</linkText><linkUri>http://aka.ms/Tdxs0r</linkUri></externalLink></para>
                  <para>
                    <embeddedLabel>Additional information:</embeddedLabel>
                  </para>
                  <para>
                    <externalLink>
                      <linkText>Provide cost-effective storage for Hyper-V workloads by using Windows Server</linkText>
                      <linkUri>http://technet.microsoft.com/library/dn554251.aspx</linkUri>
                    </externalLink>
                  </para>
                  <para>
                    <externalLink>
                      <linkText>Converged Data Center with File Server Storage</linkText>
                      <linkUri>http://technet.microsoft.com/library/hh831738.aspx</linkUri>
                    </externalLink>
                  </para>
                  <para>
                    <externalLink>
                      <linkText>Deploy Hyper-V over SMB</linkText>
                      <linkUri>http://technet.microsoft.com/library/jj134187.aspx</linkUri>
                    </externalLink>
                  </para>
                  <para>
                    <externalLink>
                      <linkText>Achieving over 1-Million IOPS from Hyper-V VMs in a Scale-Out File Server Cluster Using Windows Server 2012 R2</linkText>
                      <linkUri>http://www.microsoft.com/download/details.aspx?id=42960</linkUri>
                    </externalLink>
                  </para>
                </content>
              </section>
            </sections>
          </section>
          <section>
            <title>Task 3c: Define physical drive architecture types</title>
            <content>
              <para>The type of physical drive architecture that you select for your storage will impact the performance of your storage solution. For additional information about disk types, see Section 7.1 of <externalLink><linkText>Infrastructure-as-a-Service Product Line Architecture</linkText><linkUri>http://aka.ms/iaasfabricarchitecture</linkUri></externalLink>.</para>
            </content>
          </section>
          <section>
            <title>Task 3d: Define storage networking type</title>
            <content>
              <para>The storage controller or storage networking controller types that you use are determined by the storage option that you select for each host group. For more information, see <link xlink:href="0a72c21e-9430-4b2c-a53b-87f23cf85c00#BKMK_Step4Task3b">Step 4, Task 3b: Storage options</link>.</para>
            </content>
          </section>
          <section>
            <title>Task 3e: Determine which storage type to use for each data type</title>
            <content>
              <para>With an understanding of your data types, you can now determine which storage option, storage controller, storage networking controller, and physical disk architectures best meet your requirements. </para>
              <para>
                <embeddedLabel>
                  <externalLink>
                    <linkText>Design decision</linkText>
                    <linkUri>http://aka.ms/P0anp3</linkUri>
                  </externalLink>
                </embeddedLabel> - The decisions you make in this task can be entered in the Virtualization hosts worksheet.</para>
              <para>
                <embeddedLabel>Additional information:</embeddedLabel>
              </para>
              <para>
                <externalLink>
                  <linkText>Networking configurations for Hyper-V over SMB in Windows Server 2012 and Windows Server 2012 R2</linkText>
                  <linkUri>http://blogs.technet.com/b/josebda/archive/2013/10/09/networking-configurations-for-hyper-v-over-smb-in-windows-server-2012-and-windows-server-2012-r2.aspx</linkUri>
                </externalLink>
              </para>
              <para>
                <externalLink>
                  <linkText>Windows Server 2012 Hyper-V Component Architecture Poster and Companion References</linkText>
                  <linkUri>http://www.microsoft.com/download/details.aspx?id=29189</linkUri>
                </externalLink>
              </para>
              <para>
                <externalLink>
                  <linkText>Storage Technologies Overview</linkText>
                  <linkUri>http://technet.microsoft.com/library/dn610883.aspx</linkUri>
                </externalLink>
              </para>
            </content>
          </section>
        </sections>
      </section>
      <section>
        <title>Task 4: Define server virtualization host scale units</title>
        <content>
          <para>Purchasing individual servers requires procurement, installation, and configuration for each server. Scale units enable you to purchase collections of servers (that typically contain identical hardware).They are preconfigured, which enables you to add capacity to the datacenter by adding scale units, rather than by adding individual servers. </para>
          <para>The following image illustrates a scale unit that could have been purchased preconfigured from any number of hardware vendors. It includes a rack, an uninterruptable power supply (UPS), a pair of redundant network switches for the servers contained within the rack, and ten servers.</para>
          <mediaLink>
            <image xlink:href="ec85ecd1-c134-4231-9da2-86b598dac8cc"/>
          </mediaLink>
          <para>
            <embeddedLabel>Figure  SEQ Figure \* ARABIC 4:</embeddedLabel> <externalLink><linkText>Example of a virtualization server host scale unit</linkText><linkUri>http://aka.ms/Tdxs0r</linkUri></externalLink></para>
          <para>The scale unit comes preconfigured and pre-cabled to the UPS and network switches. The unit simply needs to be added to a datacenter, plugged into electrical power, and connected to the network and storage. Then it is ready to be used. If the individual components were not purchased as a scale unit, the purchaser would need to rack and wire all of the components. </para>
          <para>
            <embeddedLabel>
              <externalLink>
                <linkText>Design decision</linkText>
                <linkUri>http://aka.ms/P0anp3</linkUri>
              </externalLink>
            </embeddedLabel> - If you decide to use server virtualization host scale units, you can define the hardware for your virtualization host scale units in the Host scale units worksheet.</para>
          <para>
            <embeddedLabel>Tip:</embeddedLabel> You can purchase preconfigured scale units from a variety of Microsoft hardware partners through the <externalLink><linkText>Microsoft Private Cloud Fast Track</linkText><linkUri>http://www.microsoft.com/server-cloud/fast-track.aspx#fbid=Y72PESH8nsL</linkUri></externalLink> program. </para>
        </content>
      </section>
      <section address="BKMK_Step4Task5">
        <title>Task 5: Define server virtualization host availability strategy</title>
        <content>
          <para>Virtualization server hosts may become unavailable for planned reasons (such as maintenance) or unplanned reasons. Following are some strategies that can be used for both. </para>
          <para>
            <embeddedLabel>Planned</embeddedLabel>
          </para>
          <para>You can use live migration to move the virtual machines from one host to another host. This requires no downtime for virtual machines.</para>
          <para>
            <embeddedLabel>Unplanned</embeddedLabel>
          </para>
          <para>This scenario depends on the workload characterization types that the host is hosting. </para>
          <list class="bullet">
            <listItem>
              <para>For shared stateful workloads, use Failover Clustering within the virtual machines.</para>
            </listItem>
            <listItem>
              <para>For stateful workloads, run as a high availability virtual machine on a Hyper-V cluster.</para>
            </listItem>
            <listItem>
              <para>For stateless workloads, start new instances manually or through some automated means.</para>
            </listItem>
          </list>
          <para>If you are using Failover Clustering in Windows Server with Hyper-V, consider whether to use the features listed in the following table. For additional information about each feature, click the hyperlink.</para>
          <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
            <thead>
              <tr>
                <TD>
                  <para>Functionality</para>
                </TD>
                <TD>
                  <para>Considerations</para>
                </TD>
              </tr>
            </thead>
            <tbody>
              <tr>
                <TD>
                  <para>
                    <externalLink>
                      <linkText>Hyper-V application monitoring</linkText>
                      <linkUri>http://technet.microsoft.com/library/dn282278.aspx#bkmk_clustering</linkUri>
                    </externalLink>
                  </para>
                </TD>
                <TD>
                  <para>Monitor a virtual machine for failures in networking and storage that are not monitored by the Failover Clustering service.</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>
                    <externalLink>
                      <linkText>Virtual machine priority settings</linkText>
                      <linkUri>http://technet.microsoft.com/library/dn265972.aspx</linkUri>
                    </externalLink>
                  </para>
                </TD>
                <TD>
                  <list class="bullet">
                    <listItem>
                      <para>Set the virtual machine priority, based on the workload. You can assign the following priority settings to high availability virtual machines (also known as clustered virtual machines):</para>
                      <list class="bullet">
                        <listItem>
                          <para>High</para>
                        </listItem>
                        <listItem>
                          <para>Medium (default)</para>
                        </listItem>
                        <listItem>
                          <para>Low</para>
                        </listItem>
                        <listItem>
                          <para>No Auto Start</para>
                        </listItem>
                      </list>
                    </listItem>
                    <listItem>
                      <para>Clustered roles with higher priority are started and are placed on nodes before those with lower priority.</para>
                    </listItem>
                    <listItem>
                      <para>If a No Auto Start priority is assigned, the role does not come online automatically after it fails, which keeps resources available so other roles can start.</para>
                    </listItem>
                  </list>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>Virtual machine anti-affinity</para>
                </TD>
                <TD>
                  <para>Set anti-affinity for virtual machines that you do not want to run on the same node in a Hyper-V cluster. This could be for virtual machines that provide redundant service or are part of guest virtual machine cluster. </para>
                  <para>
                    <embeddedLabel>Note:</embeddedLabel> Anti-affinity settings are configured by using Windows PowerShell.</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>
                    <externalLink>
                      <linkText>Automated node draining</linkText>
                      <linkUri>http://technet.microsoft.com/library/dn265972.aspx</linkUri>
                    </externalLink>
                  </para>
                </TD>
                <TD>
                  <list class="bullet">
                    <listItem>
                      <para>The cluster automatically drains a node (moves the clustered roles that are running on the node to another node) before putting the node into maintenance mode or making other changes on the node.</para>
                    </listItem>
                    <listItem>
                      <para>Roles fail back to the original node after maintenance operations.</para>
                    </listItem>
                    <listItem>
                      <para>Administrators can drain a node with a single action in Failover Cluster Manager or by using the Windows PowerShell cmdlet, <system>Suspend-ClusterNode</system>. The target node for the moved clustered roles can be specified.</para>
                    </listItem>
                    <listItem>
                      <para>Cluster-Aware Updating uses node draining in the automated process to apply software updates to cluster nodes.</para>
                    </listItem>
                  </list>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>
                    <externalLink>
                      <linkText>Cluster-Aware Updating</linkText>
                      <linkUri>http://technet.microsoft.com/library/hh831694.aspx</linkUri>
                    </externalLink>
                  </para>
                </TD>
                <TD>
                  <list class="bullet">
                    <listItem>
                      <para>Cluster-Aware Updating enables you to update nodes in a cluster without impacting the virtual machines running in your cluster.</para>
                    </listItem>
                    <listItem>
                      <para>A sufficient number of cluster nodes must remain available during the update process to handle the load of the running virtual machines.</para>
                    </listItem>
                  </list>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>
                    <externalLink>
                      <linkText>Preemption of virtual machines based on priority</linkText>
                      <linkUri>http://technet.microsoft.com/library/dn265972.aspx</linkUri>
                    </externalLink>
                  </para>
                </TD>
                <TD>
                  <para>Another reason to set virtual machine priority is that the cluster service can take offline a lower priority virtual machine when a high-priority virtual machine does not have the necessary memory and other resources to start.</para>
                  <list class="bullet">
                    <listItem>
                      <para>Preemption starts with the lowest priority virtual machine and continues to higher priority virtual machines.</para>
                    </listItem>
                    <listItem>
                      <para>Virtual machines that are preempted are later restarted in priority order.</para>
                    </listItem>
                  </list>
                </TD>
              </tr>
            </tbody>
          </table>
          <para/>
          <para>
            <embeddedLabel>Note:</embeddedLabel> Hyper-V clusters can have a maximum of 64 nodes and 8,000 virtual machines.</para>
        </content>
      </section>
    </sections>
  </section>
  <section address="BKMK_Step5">
    <title>Step 5: Plan for virtualization fabric architecture concepts</title>
    <content>
      <para>This step requires defining logical concepts to which the fabric architecture will align.</para>
    </content>
    <sections>
      <section>
        <title>Task 1: Define maintenance domains</title>
        <content>
          <para>Maintenance domains are logical collections of servers that are serviced together. Servicing may include hardware or software upgrades or configuration changes. Maintenance domains typically span host groups of each type or within each location, though they don’t have to. The purpose is to prevent server maintenance from adversely impacting any consumers’ workloads.</para>
          <para>
            <embeddedLabel>Note:</embeddedLabel> This concept applies to physical network and storage components.</para>
        </content>
      </section>
      <section>
        <title>Task 2: Define physical fault domains</title>
        <content>
          <para>Groups of virtualization server hosts often fail together as the result of a failed shared infrastructure component, such as a network switch or uninterruptable power supply (UPS). Physical fault domains help support resiliency within the virtualization fabric. It is important to understand how a fault domain impacts each of the host groups you defined for your fabric.</para>
          <para>
            <embeddedLabel>Note:</embeddedLabel> This concept applies to physical network and storage components. </para>
          <para>Consider the example in the following image, which overlays maintenance and physical fault domains over a collection of host groups within a datacenter.</para>
          <mediaLink>
            <image xlink:href="a4c48af3-a273-4d8b-a7f1-3db78fb97a2d"/>
          </mediaLink>
          <para>
            <embeddedLabel>Figure  SEQ Figure \* ARABIC 5:</embeddedLabel> <externalLink><linkText>Example of a maintenance and physical fault domain definition</linkText><linkUri>http://aka.ms/Tdxs0r</linkUri></externalLink></para>
          <para>In this example, each rack of servers is defined as a separate, numbered physical fault domain. This is because each rack contains a network switch at the top and a UPS at the bottom. All servers within the rack rely on these two components, and if either fails, all servers in the rack effectively fail. </para>
          <para>Because all servers within a rack are also members of unique host groups, this design would mean that there is no mitigation in the event of a failure of any of the physical fault domains. To mitigate the issues, you could add physical fault domains of each host group type. In smaller scale environments, you could potentially add redundant switch and power supplies in each rack, or use Failover Clustering for virtualization server hosts across physical fault domains.</para>
          <para>In Figure 5, each of the colored, dashed-line boxes defines a maintenance domain (they are labeled MD 1 through 5). Note how each of the servers in the load-balanced cluster of virtual machines is hosted on a server virtualization host that is contained within a separate maintenance domain and a separate physical fault domain. </para>
          <para>This enables the fabric administrator to take down all virtualization server hosts within a maintenance domain without significantly impacting applications that have multiple servers spread across maintenance domains. It also means that the application running on the load-balanced cluster is not completely unavailable if a physical fault domain fails.</para>
          <para>
            <embeddedLabel>
              <externalLink>
                <linkText>Design decision</linkText>
                <linkUri>http://aka.ms/P0anp3</linkUri>
              </externalLink>
            </embeddedLabel> - The decisions you make for Tasks 1 and 2 can be entered in the Settings worksheet.</para>
        </content>
      </section>
      <section>
        <title>Task 3: Define reserve capacity</title>
        <content>
          <para>The failure of individual servers in the fabric is inevitable. The fabric design needs to accommodate individual server failure, just as it accommodates failures of collections of servers in fault and maintenance domains. The following illustration is the same as Figure 5, but it uses red to identify three failed servers.</para>
          <mediaLink>
            <image xlink:href="af8534fc-5ad4-4ff6-b73c-eac2d74bb556"/>
          </mediaLink>
          <para>
            <embeddedLabel>Figure  SEQ Figure \* ARABIC 6:</embeddedLabel> <externalLink><linkText>Failed servers</linkText><linkUri>http://aka.ms/Tdxs0r</linkUri></externalLink></para>
          <para>In Figure 6, server virtualization hosts have failed in the following host groups, maintenance domains, and physical fault domains.</para>
          <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
            <thead>
              <tr>
                <TD>
                  <para>Host group</para>
                </TD>
                <TD>
                  <para>Physical fault domain</para>
                </TD>
                <TD>
                  <para>Maintenance domain</para>
                </TD>
              </tr>
            </thead>
            <tbody>
              <tr>
                <TD>
                  <para>2</para>
                </TD>
                <TD>
                  <para>2</para>
                </TD>
                <TD>
                  <para>3</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>3</para>
                </TD>
                <TD>
                  <para>3</para>
                </TD>
                <TD>
                  <para>2</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>4</para>
                </TD>
                <TD>
                  <para>4</para>
                </TD>
                <TD>
                  <para>2</para>
                </TD>
              </tr>
            </tbody>
          </table>
          <para/>
          <para>The application running on the load-balanced cluster is still available, even though the host in Physical fault domain 2 has failed, but the application will operate at a third less capacity. </para>
          <para>Consider what would happen if the server virtualization host that hosted one of the virtual machines in Physical fault domain 3 also failed, or if Maintenance domain 2 was taken down for maintenance. In these cases, the capacity for the application would decrease by 2/3. </para>
          <para>You may decide that’s unacceptable for your virtualization fabric. To mitigate the impact of failed servers, you can ensure that each of your physical fault domains and maintenance domains have enough reserve capacity so that capacity will never drop below the acceptable level that you define.</para>
          <para>For more information about calculating reserve capacity, see <externalLink><linkText>Reserve Capacity</linkText><linkUri>http://blogs.technet.com/b/cloudsolutions/archive/2013/08/15/cloud-services-foundation-reference-architecture-principles-concepts-and-patterns.aspx#Reserve_Capacity</linkUri></externalLink> in Cloud Services Foundation Reference Architecture – Principles, Concepts, and Patterns.</para>
        </content>
      </section>
    </sections>
  </section>
  <section address="BKMK_Step6">
    <title>Step 6: Plan for initial capability characteristics</title>
    <content>
      <para>After completing all of the tasks in this document, you will be able to determine the initial costs to host virtual machines and storage on the fabric, in addition to the initial service quality levels that the fabric can meet. You won’t be able to finalize either of these tasks, however, until you implement your fabric management tools and human resources, which are discussed in the Next Steps section of this document.</para>
    </content>
    <sections>
      <section>
        <title>Task 1: Define initial SLA metrics for storage and virtual machines</title>
        <content>
          <para>As a fabric administrator, you’ll probably define a service level agreement (SLA) that details the service quality metrics that the fabric will meet. Your virtual machine administrators will need to know this to plan how they’ll use the fabric. </para>
          <para>At a minimum, this will likely include an availability metric, but it may also include other metrics. To get an idea of a baseline for virtualization fabric SLA metrics, you can review those offered by public cloud providers such as Microsoft Azure. For virtual machine hosting, that SLA guarantees that when a customer deploy two or more instances of a virtual machine running the same workload, and deploys those instances in different fault and upgrade domains (referred to as “maintenance domains” in this document), at least one of those virtual machines will be available 99.95% of the time. </para>
          <para>For a full description of the Azure SLA, please see <externalLink><linkText>Service Level Agreements</linkText><linkUri>http://azure.microsoft.com/support/legal/sla/</linkUri></externalLink>. Optimally, your virtualization fabric will meet or exceed those of public cloud providers. </para>
        </content>
      </section>
      <section>
        <title>Task 2: Define initial costs to host storage and virtual machines</title>
        <content>
          <para>With your fabric designed, you’ll also be able to calculate:</para>
          <list class="bullet">
            <listItem>
              <para>The hardware, space, power, and cooling costs of the fabric</para>
            </listItem>
            <listItem>
              <para>The hosting capacity of the fabric</para>
            </listItem>
          </list>
          <para>This information, combined with your other costs, such as the cost of your fabric management tools and human resources, will enable you to determine your final costs to host virtual machines and storage.</para>
          <para>To get an idea of the baseline costs for virtual machines and storage, you can review the hosting costs of public cloud providers such as Microsoft Azure. For more information, see <externalLink><linkText>Virtual Machine Pricing Details</linkText><linkUri>http://azure.microsoft.com/pricing/details/virtual-machines/</linkUri></externalLink>.</para>
          <para>Although not always the case, you will typically find that your hosting costs are higher than those of public providers because your fabric will be much smaller than the fabrics of large public providers who are able to attain volume discounts on hardware, datacenter space, and power.</para>
        </content>
      </section>
    </sections>
  </section>
  <section>
    <title>Next steps</title>
    <content>
      <para>After you complete all the tasks in this document, you’ll have a fabric design that meets your organization’s requirements. You’ll also have an initial service characteristic definition that includes the costs and service-level metrics. You won’t be able to determine your final service-level metrics and costs until you determine the human resources costs and the management tools and processes that you’ll use for your fabric. </para>
      <para>Microsoft System Center 2012 provides a comprehensive set of functionality to enable you to provision, monitor, and maintain your virtualization fabric. You can learn more about how to use System Center for fabric management by reading the following resources:</para>
      <para>
        <externalLink>
          <linkText>System Center Technical Documentation Library</linkText>
          <linkUri>http://technet.microsoft.com/library/cc507089.aspx</linkUri>
        </externalLink>
      </para>
      <para>
        <externalLink>
          <linkText>Fabric Management Architecture Guide</linkText>
          <linkUri>http://aka.ms/iaasfabricmanagement</linkUri>
        </externalLink>
      </para>
    </content>
  </section>
  <relatedTopics/>
</developerConceptualDocument>
