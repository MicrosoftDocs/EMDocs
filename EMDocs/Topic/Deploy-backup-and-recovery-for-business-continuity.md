---
title: Deploy backup and recovery for business continuity
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5a75a516-32cd-4757-bef1-280dd95f7d7c
---
# Deploy backup and recovery for business continuity
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Your business continuity strategy defines how you keep corporate data available—and business workloads up and running—during both planned downtime and unplanned outages. This guide provides a backup and recovery solution.</para>
    <para>
      <legacyBold>How can this guide help you?</legacyBold> This guide helps individuals and teams who are evaluating, designing, and deploying a backup and recovery solution. As an IT administrator or team in a medium-to-large business, you can use this guide to understand the recommend steps for deploying a backup and recovery solution. </para>
    <para>
      <legacyBold>In this solution guide:</legacyBold>
    </para>
    <list class="bullet">
      <listItem>
        <para>
          <link xlink:href="5a75a516-32cd-4757-bef1-280dd95f7d7c#BKMKScenario">Scenario, problem statement, and goals</link>
        </para>
      </listItem>
      <listItem>
        <para>
          <link xlink:href="5a75a516-32cd-4757-bef1-280dd95f7d7c#BKMKStrategy">What is the recommended design for this solution?</link>
        </para>
      </listItem>
      <listItem>
        <para>
          <link xlink:href="5a75a516-32cd-4757-bef1-280dd95f7d7c#BKMKWhy">Why are we recommending this design?</link>
        </para>
      </listItem>
      <listItem>
        <para>
          <link xlink:href="5a75a516-32cd-4757-bef1-280dd95f7d7c#BKMKImplentationSteps">What are the steps to implement this solution?</link>
        </para>
      </listItem>
    </list>
    <para>The following diagram illustrates the problem that this solution guide is addressing. </para>
    <mediaLink>
      <image xlink:href="37f059e0-03df-41f4-8055-b9681df45526" />
    </mediaLink>
  </introduction>
  <section address="BKMKScenario">
    <title>Scenario, problem statement, and goals</title>
    <content>
      <para>This section uses an example to describe the scenario, current problem, and goals that you might have. </para>
      <para>
        <legacyBold>Scenario</legacyBold>
      </para>
      <para>You’re an expanding, medium-size organization whose business is built around a number of Microsoft technologies:</para>
      <list class="bullet">
        <listItem>
          <para>You have two Windows Server file servers that contain business data that ranges from critical to important.</para>
        </listItem>
        <listItem>
          <para>You run a couple of virtualized internal applications on a Hyper-V host server.</para>
        </listItem>
        <listItem>
          <para>You use an Exchange server for email, a SharePoint server for information sharing, and a server running SQL Server as a backend database for your application data.</para>
        </listItem>
        <listItem>
          <para>Most of your employee desktop computers run Windows 7, 8, or 8.1. Employees are supposed to save business critical files to your network file servers or to a SharePoint site for collaboration purposes, but files are often left on local desktop computers.</para>
        </listItem>
        <listItem>
          <para>You have a storage area network (SAN)/unified storage device from a non-Microsoft vendor.</para>
        </listItem>
      </list>
      <para>
        <legacyBold>Problem statement</legacyBold>
      </para>
      <para>The overall problem you want to solve is:</para>
      <para>
        <embeddedLabel>How do I get my business data backed up and stored, and how do I recover that data within a reasonable amount of time when an unexpected incident or disaster occurs?</embeddedLabel>
      </para>
      <para>In answering this question, you have a number of issues associated with your current environment:</para>
      <list class="bullet">
        <listItem>
          <para>Your backup strategy has grown piecemeal over the years, and the processes aren’t well-known.</para>
        </listItem>
        <listItem>
          <para>Your current backup assumes all corporate data is of the same importance, although it isn’t.</para>
        </listItem>
        <listItem>
          <para>Recovery was slow the last time you had an unexpected outage, and some critical data was lost.</para>
        </listItem>
        <listItem>
          <para>You back up data only to an on-premises SAN disk. You’re concerned what might happen if a disaster occurs in the building.</para>
        </listItem>
        <listItem>
          <para>Your current backup solution is complex to manage, there are scheduling limitations, and only some types of backups can be performed. In particular, your current solution isn’t optimized for backing up the Microsoft workloads around which your organization revolves.</para>
        </listItem>
        <listItem>
          <para>Your storage needs are growing. There are currently 20 terabytes (TB) of data in the organization, and this number is growing at around 20 percent per year.</para>
        </listItem>
      </list>
      <para>
        <legacyBold>Organization goals</legacyBold>
      </para>
      <para>After analyzing the problem and issues, you’ve identified these goals and requirements:</para>
      <list class="bullet">
        <listItem>
          <para>
            <embeddedLabel>Provide optimal and flexible backup</embeddedLabel>—You need to back up different types of data with differing levels of detail, for example, applications, workloads, computers and servers, volumes, folders, and files. The solution should be optimized for backup of Microsoft workloads.</para>
        </listItem>
        <listItem>
          <para>
            <embeddedLabel>Provide resilient backup</embeddedLabel>—Workloads must remain up and running during backup, so that normal operations aren’t disrupted. </para>
        </listItem>
        <listItem>
          <para>
            <embeddedLabel>Provide scalable storage</embeddedLabel>—You need scalable storage to accommodate your growing needs. </para>
        </listItem>
        <listItem>
          <para>
            <embeddedLabel>Provide offsite storage</embeddedLabel>—Offsite storage is important in case of onsite disaster.</para>
        </listItem>
        <listItem>
          <para>
            <embeddedLabel>Define data RPOs</embeddedLabel>—The solution should reflect that not all data is equal, and it should allow for variations in recovery point objectives (RPOs) for different data types. An RPO defines the maximum period that’s acceptable for data to be unavailable when an outage occurs, so it’ll be shorter for more critical data.</para>
        </listItem>
        <listItem>
          <para>
            <embeddedLabel>Ensure ease of management and self-service</embeddedLabel>—Backup should be initiated, managed, and monitored easily. Users need to be able to initiate backup and recovery from their computers. </para>
        </listItem>
        <listItem>
          <para>
            <embeddedLabel>Provide backup initiation</embeddedLabel>—You need to be able to run both scheduled and on-demand backups.</para>
        </listItem>
        <listItem>
          <para>
            <embeddedLabel>Ensure simple data recovery</embeddedLabel>—It should be easy to recover data manually and automatically. You’ll need to be able to restore data at different levels and to the original or alternate location. </para>
        </listItem>
        <listItem>
          <para>
            <embeddedLabel>Provide simple costing</embeddedLabel>—Costing should be easy to figure out.</para>
        </listItem>
      </list>
    </content>
  </section>
  <section address="BKMKStrategy">
    <title>What is the recommended design for this solution?</title>
    <content>
      <para>The following diagram illustrates the backup and recovery design, which focuses on Microsoft System Center 2012 R2 Data Protection Manager (DPM) and Microsoft Azure.</para>
      <mediaLink>
        <image xlink:href="3b5f631a-7eff-4360-9d53-93f9dcbb155a" />
      </mediaLink>
      <para />
      <para>The following table lists the design elements. </para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Technology</para>
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
                <externalLink>
                  <linkText>System Center 2012 DPM</linkText>
                  <linkUri>http://go.microsoft.com/fwlink/?LinkId=391357</linkUri>
                </externalLink>
              </para>
            </TD>
            <TD>
              <para>System Center DPM (DPM) provides simple and centralized backup of Microsoft workloads, and servers and clients running Microsoft operating systems.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <externalLink>
                  <linkText>Azure Backup</linkText>
                  <linkUri>http://go.microsoft.com/fwlink/?LinkId=391358</linkUri>
                </externalLink>
              </para>
            </TD>
            <TD>
              <para>Azure Backup enhances DPM backup options. In addition to backing up data to disk for short-term storage, you can back up data to the Azure cloud for off-premises online storage. </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section address="BKMKWhy">
    <title address="BKMKwhy">Why are we recommending this design?</title>
    <content>
      <para>Let’s see how these technologies align to your organizational goals and solve the problem and issues you identified.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Goal</para>
            </TD>
            <TD>
              <para>Alignment</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>
                <embeddedLabel>Provide optimal and flexible backup</embeddedLabel>
              </para>
            </TD>
            <TD>
              <para>DPM provides tailored backup and recovery for Microsoft workloads, including:</para>
              <list class="bullet">
                <listItem>
                  <para>Microsoft workloads: File Server, Exchange. SharePoint, Windows, Hyper-V.</para>
                </listItem>
                <listItem>
                  <para>File data— full server (all volumes), volumes, shares, folders.</para>
                </listItem>
                <listItem>
                  <para>SQL Server—database backup.</para>
                </listItem>
                <listItem>
                  <para>Exchange server—stand-alone server, databases in a database availability group (DAG).</para>
                </listItem>
                <listItem>
                  <para>SharePoint—farm, SharePoint search, front-end Web server content.</para>
                </listItem>
                <listItem>
                  <para>Hyper-V—Hyper-V computers, cluster-shared volumes (CSVs).</para>
                </listItem>
                <listItem>
                  <para>Client computers—file data.</para>
                </listItem>
                <listItem>
                  <para>Servers—System state or full backup for bare metal recovery.</para>
                </listItem>
              </list>
              <para>For more information, see <externalLink><linkText>DPM protection support matrix</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=391359</linkUri></externalLink>.</para>
              <para>Backed up data can be stored on tape or disk, and in the Microsoft Azure cloud.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <embeddedLabel>Provide resilient backup</embeddedLabel>
              </para>
            </TD>
            <TD>
              <para>DPM uses the Volume Shadow Copy Service (VSS) to back up without disrupting normal operations.</para>
              <para>DPM synchronization is asynchronous, so that it doesn’t block disk I/O on the protected sources. Data changes are stored in the agent synchronization log and then replicated across the network to the DPM server, where they are stored in the transfer log. VSS creates consistent point-in-time shadow copies of the copied data. After the synchronization is complete, VSS creates replicas that can be recovered as required. </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <embeddedLabel>Provide scalable backup and storage</embeddedLabel>
              </para>
            </TD>
            <TD>
              <para>DPM provides the following data volumes:</para>
              <list class="bullet">
                <listItem>
                  <para>For 64-bit computers, you can back up approximately 600 volumes (300 replica volumes and 300 recovery volumes) with a DPM server.</para>
                </listItem>
                <listItem>
                  <para>Volume capacity within this limitation depends on DPM limitations, the data you’re protecting, and storage space. For more information about DPM limitations, see <externalLink><linkText>Preparing your environment for System Center 2012 R2 DPM </linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=507399</linkUri></externalLink>.</para>
                </listItem>
                <listItem>
                  <para>To help scale backups from DPM in System Center 2012 R2 Update 3 onwards, you can define backup windows for virtual machine backup. These windows specify when the backup should start and finish. For more information, see <externalLink><linkText>Configure backup windows for virtual machines</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=472535</linkUri></externalLink>.</para>
                </listItem>
              </list>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <embeddedLabel>Provide offsite storage to tape</embeddedLabel>
              </para>
            </TD>
            <TD>
              <para>For long-term storage, you can back up data to tape. For more information, see <externalLink><linkText>Data Storage</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=391360</linkUri></externalLink>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <embeddedLabel>Provide offsite storage to Azure</embeddedLabel>
              </para>
            </TD>
            <TD>
              <para>In addition to backing up data to disk for short-term storage, you can back up data to Microsoft Azure for offsite storage: </para>
              <list class="bullet">
                <listItem>
                  <para>You can back up data to Azure for files and folders, SQL Server, and Hyper-V. Other workloads aren’t supported.</para>
                </listItem>
                <listItem>
                  <para>Azure Backup supports 850 gigabytes (GB) per volume per backup. You can work around this limitation by using multiple volumes.</para>
                </listItem>
                <listItem>
                  <para>You can schedule a maximum of two backups a day. The maximum retention period is 120 days at once a day. If you schedule two backups a day, the maximum retention period is 60 days.</para>
                </listItem>
              </list>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <embeddedLabel>Define data RPOs</embeddedLabel>
              </para>
            </TD>
            <TD>
              <para>DPM organizes resources that you want to protect into protection groups. You can organize your protection groups by workload or by data importance. For example, you can create a protection group that contains multiple volumes that include critical business data, and another group with volumes containing less important end-user data. In case of unexpected outages, you can restore data from protection groups in accordance with the importance of data and the required RPO.</para>
              <para>You can restore data from disk, tape, and Azure. Obviously, recovery from tape will be slower, aligning to a longer RPO. Disk and online backup can be restored more quickly for a shorter RPO. </para>
              <para />
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <embeddedLabel>Ensure ease of management and self service</embeddedLabel>
              </para>
            </TD>
            <TD>
              <para>You can centrally back up and restore all your data (from tape, disk, and Azure) in the DPM console, using simple wizards.</para>
              <para>DPM provides self-service support:</para>
              <list class="bullet">
                <listItem>
                  <para>Non-DPM administrators can use the DPM Self-Service Recovery Tool to recover SQL Server databases that are backed up by DPM. For more information, see <externalLink><linkText>Recover SQL Server databases using self-service recovery</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=391361</linkUri></externalLink>.</para>
                </listItem>
                <listItem>
                  <para>Users can back up and retrieve their own data using the end user recovery option, which installs the DPM Client on the user’s desktop. For more information, see <externalLink><linkText>Configure end-user recovery and recover file data</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=391362</linkUri></externalLink>.</para>
                </listItem>
              </list>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <embeddedLabel>Provide backup initiation</embeddedLabel>
              </para>
            </TD>
            <TD>
              <para>You can run scheduled and on-demand backups in DPM:</para>
              <para>You can schedule some options in DPM:</para>
              <list class="bullet">
                <listItem>
                  <para>On-demand—You can run an on-demand backup for a specific resource in a DPM protection group.</para>
                </listItem>
                <listItem>
                  <para>Scheduled—You can set up scheduled backups with a number of options, including how often source and replica data should be synchronized, and when backups should run. For details, see <externalLink><linkText>Configure and run backups</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=472534</linkUri></externalLink>.</para>
                </listItem>
              </list>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <embeddedLabel>Ensure simple data recovery</embeddedLabel>
              </para>
            </TD>
            <TD>
              <para>DPM provides a Recovery Wizard to recover:</para>
              <list class="bullet">
                <listItem>
                  <para>Servers and client computers—File data can be recovered at the volume, share, folder, or file level. On protected client computers with end-user recovery enabled, users can recover their own files.</para>
                </listItem>
                <listItem>
                  <para>Exchange—mailboxes and mailboxes under a DAG.</para>
                </listItem>
                <listItem>
                  <para>SharePoint—farm, database, Web application, file or list item, SharePoint search, SharePoint Front-End Web server.</para>
                </listItem>
                <listItem>
                  <para>SQL Server—database.</para>
                </listItem>
                <listItem>
                  <para>Hyper-V—item-level recovery of files, folders, volumes, and virtual hard drives.</para>
                </listItem>
                <listItem>
                  <para>If you back up to Azure, you can recover DPM directly from the DPM console, to the same location or an alternate location.</para>
                </listItem>
              </list>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <embeddedLabel>Provide simple costing</embeddedLabel>
              </para>
            </TD>
            <TD>
              <para>DPM costs are in accordance with System Center licensing. See <externalLink><linkText>System Center 2012 R2</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=391363</linkUri></externalLink>.</para>
              <para>To back up to Azure, you pay for data stored, not data transferred to computer resources. The first 5 GB per month is free. See <externalLink><linkText>Backup Pricing Details</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=391364</linkUri></externalLink>.</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section address="BKMKImplentationSteps">
    <title>What are the steps to implement this solution?</title>
    <content>
      <para>Use the steps in this section to implement the solution. Verify each step before proceeding to the next. </para>
      <alert class="note">
        <para>If you want to print or export a customized set of solution topics, see <externalLink><linkText>Print/Export Multiple Topics – Help</linkText><linkUri>http://technet.microsoft.com/library/export/help/?returnUrl=%2fen-US%2flibrary%2fff630950.aspx</linkUri></externalLink>.</para>
      </alert>
      <list class="ordered">
        <listItem>
          <para>
            <link xlink:href="#BKMK_Deploy">Set up and deploy DPM</link>
          </para>
        </listItem>
        <listItem>
          <para>
            <link xlink:href="#BKMK_Storage">Set up storage for backed up data</link>
          </para>
        </listItem>
        <listItem>
          <para>
            <link xlink:href="#BKMK_Protect">Set up protection</link>
          </para>
        </listItem>
        <listItem>
          <para>
            <link xlink:href="#BKMK_Self">Set up self-service</link>
          </para>
        </listItem>
        <listItem>
          <para>
            <link xlink:href="#BKMK_Verify">Validate your backups</link>
          </para>
        </listItem>
      </list>
    </content>
    <sections>
      <section address="BKMK_Deploy">
        <title>Set up and deploy DPM</title>
        <content>
          <list class="bullet">
            <listItem>
              <para>
                <embeddedLabel>Download System Center 2012 R2</embeddedLabel> </para>
              <para>You can download a trial version of DPM before you acquire the full version. For more information, see <externalLink><linkText>Download the Evaluation: System Center 2012 R2</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=391365</linkUri></externalLink> from the TechNet Evaluation Center.</para>
            </listItem>
            <listItem>
              <para>
                <embeddedLabel>Learn about DPM</embeddedLabel> </para>
              <para>Before you set up DPM, read about system requirements, supported deployments, and DPM features. For more information, see <externalLink><linkText>Get started with DPM</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=391366</linkUri></externalLink> in the TechNet library.</para>
            </listItem>
            <listItem>
              <para>
                <embeddedLabel>Install DPM</embeddedLabel>
              </para>
              <para>After ensuring that all prerequisites are in place, install DPM. For more information, see <externalLink><linkText>Installing and Upgrading System Center 2012 - DPM</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=391367</linkUri></externalLink> in the TechNet library.</para>
            </listItem>
          </list>
        </content>
      </section>
      <section address="BKMK_Storage">
        <title>Set up storage for backed up data</title>
        <content>
          <list class="bullet">
            <listItem>
              <para>
                <embeddedLabel>Configure disk storage</embeddedLabel>—You’ll need to add a disk to the DPM backup storage pool to store replicas and recovery points. This disk shouldn’t have any volumes defined. For instructions, see <externalLink><linkText>Configure disk storage</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=391370</linkUri></externalLink>.</para>
            </listItem>
            <listItem>
              <para>
                <embeddedLabel>Set up Azure Backup</embeddedLabel>—For instructions, see the following topics: <externalLink><linkText>Prerequisites for Backup to Azure</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=391371</linkUri></externalLink>, <externalLink><linkText>Configuring backup vaults for Azure Backup</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=391372</linkUri></externalLink>, and <externalLink><linkText>Registering DPM servers</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=391373</linkUri></externalLink>.</para>
            </listItem>
            <listItem>
              <para>
                <embeddedLabel>Set up tape storage</embeddedLabel>—You’ll need to physically attach a tape library or stand-alone tape drive to the DPM server, and add it to the DPM library. For instructions, see <externalLink><linkText>Configure tape storage</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=391374</linkUri></externalLink>. </para>
            </listItem>
          </list>
        </content>
      </section>
      <section address="BKMK_Protect">
        <title>Set up protection</title>
        <content>
          <list class="bullet">
            <listItem>
              <para>A general walkthrough for setting up client protection is available on <externalLink><linkText>Kevin Holman’s System Center Blog</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=391368</linkUri></externalLink>. </para>
            </listItem>
            <listItem>
              <para>
                <externalLink>
                  <linkText>Install and configure the DPM protect agent</linkText>
                  <linkUri>http://go.microsoft.com/fwlink/?LinkId=391369</linkUri>
                </externalLink>—Install the agent on each computer or server you want to protect.</para>
            </listItem>
            <listItem>
              <para>
                <externalLink>
                  <linkText>Configure protection groups</linkText>
                  <linkUri>http://go.microsoft.com/fwlink/?LinkId=391376</linkUri>
                </externalLink>—Gather and organize the servers and computers you want to protect into protection groups. When you create a protection group, you set up short-term and long-term backup options, schedule backups, and set up initial replication for the data. </para>
              <para>For this solution, set up protection groups as follows:</para>
              <list class="bullet">
                <listItem>
                  <para>
                    <externalLink>
                      <linkText>Client computers</linkText>
                      <linkUri>http://go.microsoft.com/fwlink/?LinkId=391377</linkUri>
                    </externalLink> and <externalLink><linkText>File servers</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=391378</linkUri></externalLink>—When you set up protection groups for client computers and file servers, you’ll select the computers or server and the file data you want to protect. You can also specify whether you want to allow users to specify other files to back up and recover. The users won’t be able to select any files you explicitly exclude. You’ll select disk and Azure for short-term storage, and tape for long-term storage.</para>
                </listItem>
                <listItem>
                  <para>
                    <externalLink>
                      <linkText>SQL Server</linkText>
                      <linkUri>http://go.microsoft.com/fwlink/?LinkId=391379</linkUri>
                    </externalLink>—When you set up a protection group, you’ll select the server running SQL Server that has the DPM agent installed, and you’ll specify which SQL Server databases on that server should be protected. You’ll select the options to perform short-term protection with disk and Azure Backup, and long-term protection with tape. </para>
                </listItem>
                <listItem>
                  <para>
                    <externalLink>
                      <linkText>Exchange</linkText>
                      <linkUri>http://go.microsoft.com/fwlink/?LinkId=391380</linkUri>
                    </externalLink>—Before protecting Exchange, you’ll need to copy the <system>ese</system> and <system>eseutil</system> files (usually located at C:\Program Files\Microsoft\Exchange Server\V14\Bin) to the DPM server. The versions of these files must be the same on the server you’re protecting, and on the DPM server. When you configure the protection group, you’ll select the Exchange mailbox databases you want to protect. You’ll configure short-term protection with disk only, and long-term protection with tape. Then, the wizard runs an integrity check for the Exchange databases. This offloads backup consistency checking from the Exchange server to the DPM server, eliminating the impact of running <system>eseutil</system> on the Exchange server during backup. There’s a useful full walkthrough of this deployment at <externalLink><linkText>MSExchange.org</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=391381</linkUri></externalLink>.</para>
                </listItem>
                <listItem>
                  <para>
                    <externalLink>
                      <linkText>SharePoint</linkText>
                      <linkUri>http://go.microsoft.com/fwlink/?LinkId=391382</linkUri>
                    </externalLink>—Before you configure a protection group, be sure the DPM protection agent is running on at least one Front End server in the farm, and on all SQL servers that host databases for the SharePoint Farm. In addition, you’ll need to run <system>ConfigureSharepoint.exe –EnableSharepointProtection</system> from an elevated Windows PowerShell command line with an account that has full access to SharePoint. This configures SharePoint permissions and VSS writer for DPM. When you configure the protection group, you’ll select a farm database from the SharePoint Front End server. When you configure the protection group, you’ll select the options to perform short-term protection with disk only, and long-term protection with tape.</para>
                </listItem>
                <listItem>
                  <para>
                    <externalLink>
                      <linkText>Hyper-V</linkText>
                      <linkUri>http://go.microsoft.com/fwlink/?LinkId=391383</linkUri>
                    </externalLink>—When you configure a protection group for Hyper-V, you select the virtual machines on the Hyper-V host or cluster that you want to protect. You can select the options to perform backups online (with no interruption to a working virtual machine), or offline (which pauses the virtual machine, takes a snapshot, and then backs it up). You’ll select the options to do short-term storage with disk and online with Azure Backup, and long-term storage with tape.</para>
                </listItem>
              </list>
            </listItem>
            <listItem>
              <para>When you set up data storage options for the protection group, use these settings.</para>
              <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
                <thead>
                  <tr>
                    <TD>
                      <para>Backup medium</para>
                    </TD>
                    <TD>
                      <para>Description</para>
                    </TD>
                    <TD>
                      <para>Characteristic</para>
                    </TD>
                    <TD>
                      <para>Scenario recommendation</para>
                    </TD>
                  </tr>
                </thead>
                <tbody>
                  <tr>
                    <TD>
                      <para>Disk-to-disk-to-tape backup (D2D2T)</para>
                    </TD>
                    <TD>
                      <para>Backup data to disk in the short term and tape in the long term</para>
                    </TD>
                    <TD>
                      <para>Backing up data to disk for short-term storage and tape for long-term storage provides more flexibility than disk-to-tape backup only, because in the short term you’ll back up your data to disk and in the long term to tape. It’s useful for:</para>
                      <list class="bullet">
                        <listItem>
                          <para>Critical and important data with some loss tolerance. Using this method, there is a time period in which data is stored on disk and probably onsite. If disaster occurs before your data is moved to tapes offsite, data loss can occur.</para>
                        </listItem>
                        <listItem>
                          <para>Data that has a short RPO in the short term and a longer RPO as time goes on. For example, you might be working on a particular project, and file data for that project is critical, with a short RPO for the next three months. However, after that period the RPO for that data gets longer.</para>
                        </listItem>
                      </list>
                    </TD>
                    <TD>
                      <para>Use to back up:</para>
                      <list class="bullet">
                        <listItem>
                          <para>Exchange servers</para>
                        </listItem>
                        <listItem>
                          <para>SharePoint servers</para>
                        </listItem>
                        <listItem>
                          <para>For these scenarios, only disk is available for short-term storage. Azure Backup isn’t supported.</para>
                        </listItem>
                      </list>
                      <para>You’ll need to purchase a tape library or stand-alone tape drive that must be physically attached to the DPM server. The tape library can be direct SCSI-attached or SAN.</para>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>Disk-to-tape backup (D2T) + Azure Backup</para>
                    </TD>
                    <TD>
                      <para>Back up data to disk and Azure in the short term and to tape in the long term</para>
                    </TD>
                    <TD>
                      <para>Backing up to both disk and Azure for short-term storage works around some of the disadvantages of the disk-to-disk-to-tape method alone. It’s useful for: </para>
                      <list class="bullet">
                        <listItem>
                          <para>Business-critical data that has a low loss tolerance in the short term and needs to be stored off premises.</para>
                        </listItem>
                        <listItem>
                          <para>Short-term data is available both on disk and in the cloud.</para>
                        </listItem>
                      </list>
                    </TD>
                    <TD>
                      <para>Use to back up:</para>
                      <list class="bullet">
                        <listItem>
                          <para>SQL Server data</para>
                        </listItem>
                        <listItem>
                          <para>Hyper-V data</para>
                        </listItem>
                        <listItem>
                          <para>Server and client computer file data</para>
                        </listItem>
                      </list>
                    </TD>
                  </tr>
                </tbody>
              </table>
            </listItem>
          </list>
        </content>
      </section>
      <section address="BKMK_Self">
        <title>Set up self-service</title>
        <content>
          <para>You can specify that end users can independently recover file data by retrieving recovery points of their files. Enabling end-user recovery involves configuring Active Directory Domain Services (AD DS) to support end-user recovery, enabling the end-user recovery feature on the DPM server, and installing the shadow copy client software on the client computers. For more information, see <externalLink><linkText>Configure end-user recovery and recover file data</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=391385</linkUri></externalLink>.</para>
          <para>You can also enable user recovery for SQL Server databases that are backed up by the DPM server, using the Self-Service Recovery Tool (SSRT). For more information, see <externalLink><linkText>Recover SQL Server databases using self-service recovery</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=391386</linkUri></externalLink>.</para>
        </content>
      </section>
      <section address="BKMK_Verify">
        <title>Validate your backups</title>
        <content>
          <para>Verify that backups are working as expected. When you configure your workload backups with DPM protection groups, DPM immediately performs the initial replication (full backup) of the data. In the DPM console, the Protection Groups will show this initial replication as progress, and they will show an <ui>OK</ui> status when the replication succeeds. In addition, you can view the monitoring jobs and alerts in the console. You can monitor backups to Azure in the Azure portal. For more information, see <externalLink><linkText>Manage and monitor backup vaults in Azure Backup</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=391384</linkUri></externalLink>.</para>
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
              <para>MSDN forum</para>
            </TD>
            <TD>
              <list class="bullet">
                <listItem>
                  <para>
                    <externalLink>
                      <linkText>Azure Backup</linkText>
                      <linkUri>http://go.microsoft.com/fwlink/?LinkId=391387</linkUri>
                    </externalLink>
                  </para>
                </listItem>
              </list>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>TechNet forum</para>
            </TD>
            <TD>
              <list class="bullet">
                <listItem>
                  <para>
                    <externalLink>
                      <linkText>DPM</linkText>
                      <linkUri>http://go.microsoft.com/fwlink/?LinkId=391388</linkUri>
                    </externalLink>
                  </para>
                </listItem>
              </list>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Blog</para>
            </TD>
            <TD>
              <list class="bullet">
                <listItem>
                  <para>
                    <externalLink>
                      <linkText>System Center: DPM</linkText>
                      <linkUri>http://go.microsoft.com/fwlink/?LinkId=391389</linkUri>
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