---
title: Provide data protection in small and midsize businesses
ms.custom: na
ms.prod: windows-server-2012-r2-essentials
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 416847db-659f-495e-9893-0855378ab4f2
---
# Provide data protection in small and midsize businesses
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://clixdevr3.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>
      <embeddedLabel>How can this guide help you?</embeddedLabel> This solution guide describes how you can protect your small to midsize business against data loss (such as through hardware theft or a natural disaster) and unauthorized access, so that you can save time and money.</para>
    <para>This guide describes a tested, prescriptive design and implementation solution that can help you protect your business data by backing it up on-premises and in the cloud, by centralizing data storage, and by restricting data access permissions.</para>
    <para>
      <legacyBold>In this solution guide:</legacyBold>
    </para>
    <list class="bullet">
      <listItem>
        <para>
          <link xlink:href="416847db-659f-495e-9893-0855378ab4f2#BKMK_ProblemH1">Scenario, problem statement, and goals</link>
        </para>
      </listItem>
      <listItem>
        <para>
          <link xlink:href="416847db-659f-495e-9893-0855378ab4f2#BKMK_Strategy">What is the recommended design for this solution?</link>
        </para>
      </listItem>
      <listItem>
        <para>
          <link xlink:href="416847db-659f-495e-9893-0855378ab4f2#BKMK_DesignDetails">Why are we recommending this design?</link>
        </para>
      </listItem>
      <listItem>
        <para>
          <link xlink:href="416847db-659f-495e-9893-0855378ab4f2#BKMK_Solution">What are the steps to implement this solution?</link>
        </para>
      </listItem>
    </list>
    <para>The following diagram illustrates the problem and scenario that this solution guide addresses.</para>
    <para> <legacyBold>Problems associated with data storage, access, and protection</legacyBold></para>
    <mediaLink>
      <image xlink:href="45bc2dd3-93b8-46b3-85ce-9923f39cbf51" />
    </mediaLink>
    <para />
  </introduction>
  <section address="BKMK_ProblemH1">
    <title>Scenario, problem statement, and goals</title>
    <content>
      <para>This section describes the scenario, problem, and goals for an example organization. </para>
    </content>
    <sections>
      <section>
        <title address="BKMK_Scenario">Scenario</title>
        <content>
          <para>The organization is a small to midsize business with up to 100 users and 200 devices, and it is looking for a way to secure its company data. Currently, each user is saving data on their local computers, and data is shared through print copies and emails or by creating local shared resources.</para>
          <para>Data backups are created inconsistently, depending on a user’s individual backup schedules. Some users are working on laptop devices, and as a result, critical data is leaving office premises. When a computer’s hardware fails, a lot of the company’s critical data is lost permanently due to lack of backups, and tremendous time is spent re-creating a new desktop with all its files and line-of-business applications installed.</para>
        </content>
      </section>
      <section address="BKMK_Problem">
        <title>Problem statement</title>
        <content>
          <para>The organization wants to address the following problems:</para>
          <list class="bullet">
            <listItem>
              <para> Files with business critical data are being exposed to unintended users.</para>
            </listItem>
            <listItem>
              <para>Expanding storage capacity on existing computers in the network involves large administrative and cost overheads.</para>
            </listItem>
            <listItem>
              <para>Network users are saving company’s data on multiple devices (for example, on a PC when at work, and on their laptop when remote). This is leading to multiple file versions that are hard to track and locate.</para>
            </listItem>
            <listItem>
              <para>Not all users are backing up their computers and data consistently. As a result, if a computer crashes, sometime there is no backup from which to restore the computer and data. </para>
            </listItem>
            <listItem>
              <para>The company’s backup data is at risk because it resides in a single location.</para>
            </listItem>
          </list>
        </content>
      </section>
      <section address="BKMK_Goals">
        <title>Organizational goals</title>
        <content>
          <para>Your organization is looking for a solution that allows it to:</para>
          <list class="bullet">
            <listItem>
              <para>Store the company’s data on-premises in a single centralized location so that all its network users can easily access it and so your administrator can more easily apply access restrictions on the data.</para>
            </listItem>
            <listItem>
              <para>Easily expand the storage capacity of the server as the organization grows in size.</para>
            </listItem>
            <listItem>
              <para>Restrict permissions to shared folders so that only select users can access the data.</para>
            </listItem>
            <listItem>
              <para>Define a backup schedule so that backups happen automatically instead of manually.</para>
            </listItem>
            <listItem>
              <para>Completely restore servers and client computers from backups in the event of hardware failure. </para>
            </listItem>
            <listItem>
              <para>Create backups on-site and online to provide an additional layer of data protection. </para>
            </listItem>
          </list>
        </content>
      </section>
    </sections>
  </section>
  <section address="BKMK_Strategy">
    <title>What is the recommended design for this solution?</title>
    <content>
      <para>The following diagram illustrates how to store, protect, and securely access data from a server running <token>wseblue_2</token> or the Standard and Datacenter editions of <token>winblue_server_2</token> with the <token>wseblue_experience</token> role installed (referred to as <token>wseblue_experience</token> in the remainder of the document).</para>
      <para>
        <legacyBold>Solution design for protecting, centralizing, and providing secure access to data</legacyBold>
      </para>
      <mediaLink>
        <image xlink:href="13e92372-b2fb-48ac-a207-96f4009f89f8" />
      </mediaLink>
      <para />
      <para>
        <token>wseblue_2</token> (appropriate for use for up to 25 users and 50 devices) or <token>wseblue_experience</token> (appropriate for use for up to 100 users and 200 devices) provide a solution for small to midsize business partners and owners to protect their data by centralizing data storage, restricting access to data, and backing up data on-premises and in the cloud.</para>
      <para>The following table lists the technologies that are included in <token>wseblue_2</token> and <token>wseblue_experience</token> that are part of this solution design and describes the reason for the design choice.</para>
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
              <para>Windows Server Essentials Dashboard</para>
            </TD>
            <TD>
              <para>Use the Dashboard to perform all administrative tasks in your network, such as creating user accounts, granting access permissions, setting up server and client backups, creating storage spaces and server folders, and integrating with <token>sbs8_mob_1</token>.</para>
              <para>For information, see <legacyLink xlink:href="f70a79de-9c56-4496-89b5-20a1bff2293e">Overview of the Dashboard in Windows Server Essentials [fwlink_SBS8_Admin]</legacyLink>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Storage Spaces</para>
            </TD>
            <TD>
              <para>Use Storage Spaces for storing your company’s data. With Storage Spaces, you can expand storage as your organization grows, ensure that you are providing high availability for your data, and provide a cost effective solution. You do not need to spend money on hardware upfront, and you can scale up based on your business needs.</para>
              <para>For more information about Storage Spaces, see the <legacyLink xlink:href="1836682e-c7bb-4dd5-a2b5-6ff032693574#BKMK_5">Storage Spaces Overview</legacyLink> and <externalLink><linkText>Storage Spaces Frequently Asked Questions</linkText><linkUri>http://social.technet.microsoft.com/wiki/contents/articles/11382.storage-spaces-frequently-asked-questions-faq.aspx</linkUri></externalLink>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Server Folders</para>
            </TD>
            <TD>
              <para>Store and share your organization’s files and folders in server folders that you create on your server rather than sharing them from individual user's PCs. This enables you to consolidate your data in one central location that all network users can access. When you store your data in server folders, you can protect it against total server failure by using Windows Server Backup and <token>sbs8_mob_2</token>.</para>
              <para>For more information, see <legacyLink xlink:href="090cf1b8-7b9b-48b9-ae85-b98477b8d7cc">Manage Server Folders in Windows Server Essentials [A_Web_Admin_H2]</legacyLink>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>User management</para>
            </TD>
            <TD>
              <para>Create user accounts and user groups to control access to your company’s data and devices. When you create a user group, you can provide the same access level to network resources for all members.</para>
              <para>For more information, see <legacyLink xlink:href="0d115697-532b-48c2-a659-9f889e235326">Manage User Accounts in Windows Server Essentials [H2]</legacyLink>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Device management</para>
            </TD>
            <TD>
              <para>Join your client computers to the network so that you can easily manage all the client computers in the network through the Windows Server Essentials Dashboard.</para>
              <para>For more information about computer management-related tasks, see <legacyLink xlink:href="f5fe1088-ebe7-4799-a47d-075b0048dea1">Manage Devices in Windows Server Essentials [H2]</legacyLink>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Group Policy settings</para>
            </TD>
            <TD>
              <para>Protect client computers from network attacks and keep the software and operating system on your computers up-to-date by implementing Windows Server Essentials Group Policy settings. For more information , see <legacyLink xlink:href="f5fe1088-ebe7-4799-a47d-075b0048dea1#BKMK_5">Configure Group Policy settings for folder redirection and security</legacyLink>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Windows Server Backup</para>
            </TD>
            <TD>
              <para>Use Windows Server Backup to back up the files and folders that are stored on your server. From the backup files, you can restore files and folders on your server or perform a full system restore of your server. </para>
              <para>For more information, see <legacyLink xlink:href="0302d070-c58a-40f2-b56d-7e7842813d02">Manage Server Backup in Windows Server Essentials [SBS8_SrvrBackUp]</legacyLink>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Client Computer Backup</para>
            </TD>
            <TD>
              <para>Use Client Computer Backup to back up all the clients in your network. The data that is located on the clients is backed up on a server that is running <token>wseblue_2</token> or <token>wseblue_experience</token>. From the backup files, you can restore files and folders on the clients, or perform a full system restore of a client in the network.</para>
              <para>For more information, see <legacyLink xlink:href="1b4776e8-9504-4b98-ae80-11da797d9819">Manage Client Computer Backup in Windows Server Essentials [SBS8_Backup]</legacyLink>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>File History</para>
            </TD>
            <TD>
              <para>File History provides a supplemental mechanism for client computer backups. File History backups are stored in the File History folder, which is located on a server that is running <token>wseblue_2</token> or <token>wseblue_experience</token>. From the File History backups, network users can restore versions of files from a specific point-in-time. In addition, network users can restore the files without asking for help from the administrator.</para>
              <para>For more information, see <externalLink><linkText>Managing File History in Windows Server Essentials</linkText><linkUri>http://blogs.technet.com/b/sbs/archive/2012/12/17/managing-file-history-in-windows-server-2012-essentials.aspx</linkUri></externalLink>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <token>sbs8_mob_2</token>
              </para>
            </TD>
            <TD>
              <para>Integrate your server running <token>wseblue_experience</token> with <token>sbs8_mob_2</token> to back up files or folders that are located on your server. You can back up your business critical data on-premises and by using <token>sbs8_mob_2</token> to provide dual protection for your company’s data. </para>
              <para>For more information, see <legacyLink xlink:href="95a9f593-fad7-4335-bd4d-c7bb8c033efb">Manage Online Backup in Windows Server Essentials [fwlink_SBS8_Admin]</legacyLink>.</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section address="BKMK_DesignDetails">
    <title>Why are we recommending this design?</title>
    <content>
      <para>This section explains the details of the design considerations and the decisions that were made that led to the final solution design. It also provides the recommended configuration or usage of each feature that is used this solution.</para>
    </content>
    <sections>
      <section address="BKMK_Dashboard" DoNotNumber="false">
        <title>Windows Server Essentials Dashboard</title>
        <content>
          <para>The Windows Server Essentials Dashboard in <token>wseblue_2</token> and <token>wseblue_experience</token> helps you quickly access key information and the management features of your server instead of using multiple native Windows Server Administration tools. By using the Dashboard, you can create and manage user accounts, manage devices and backups, and manage access and settings for server folders. </para>
          <para>
            <embeddedLabel>Recommendation:</embeddedLabel> Use the Windows Server Essentials Dashboard to perform a majority of administrative tasks in your network. You can run tasks and wizards from the Dashboard to optimally configure the features that are included in your server. </para>
        </content>
      </section>
      <section address="BKMK_StorageSpaces" DoNotNumber="false">
        <title>Storage Spaces</title>
        <content>
          <para>Options for providing high availability and resilient storage for your company’s data include using the built-in RAID controller that comes with common server hardware. This storage option will provide the storage availability and resiliency you need, but it can be relatively complex and costly. </para>
          <para>In contrast, you can use the Storage Spaces feature to create low-cost, resilient, and dynamically expandable data volumes to store your business data, rather than storing it on standard hard drives. Storage Spaces are virtual hard disk drives (VHDs) that appear on the <ui>Hard Drives</ui> tab of the Dashboard. Storage Spaces helps you save files to two or more drives so that your files remain safe even when a drive fails. With Storage Spaces, you can virtualize your server’s storage by grouping industry standard hard drives into storage pools, and then create VHDs (called storage spaces) from the available capacity in the storage pools. You can use these storage spaces to store your company’s data in one central location instead of all users saving data on their PCs.</para>
          <para>
            <embeddedLabel>Recommendation:</embeddedLabel> For small businesses with fewer than 10 users, use at least three SAS or SATA drives—one drive to be used to back up the operating system, and the other two to be used for storage spaces. We recommend that you create a storage space by using at least two drives with mirrored resiliency. </para>
          <para>For small businesses with more than 10 users, or midsize businesses with up to 100 users, configure at least three SAS drives with Storage Spaces—one drive to be used to back up the operating system, and the other two to be used for storage spaces. We also recommend providing a server chassis that supports adding more drives for expansion. </para>
        </content>
      </section>
      <section address="BKMK_ServerFolders" DoNotNumber="false">
        <title>Server Folders</title>
        <content>
          <para>By using server folders, you can store files that are located on client computers to a central location instead of users storing files on their PCs. </para>
          <para>Storing files in server folders ensures that your files are easy to back up and easy to access. They are located in a place that is always accessible from every client. Files are secure because accessing them requires using authenticated network credentials.</para>
          <para>
            <embeddedLabel>Recommendation:</embeddedLabel> Create server folders on a Storage Space drive and create separate server folders for departments or projects. For example, if you have an accounting department, you can create a folder called “Accounting.” Creating the server folder on a Storage Space drive increases data availability (due to mirroring). We also recommend that you set a quota for your server folders so that you are alerted when a server folder is about to reach its capacity. When you are alerted, you can delete files in the server folder to increase available space for storage, or you can add more space to the server folder and adjust its quota settings.</para>
        </content>
      </section>
      <section address="BKMK_UsersGroups" DoNotNumber="false">
        <title>Users and groups management</title>
        <content>
          <para>User and user group accounts help you specify permissions that allow users to access your company data. This protects your company data from unintended user access. You can easily manage access to your network resources by creating user accounts for all your network users from the <ui>Users</ui> tab of the Windows Server Essentials Dashboard. </para>
          <para>In addition, you can create user group accounts, and make the user accounts as its members. All members of a user group account share the same security access level to server resources. Group membership simplifies resource management because you can specify permissions for a group of users on one UI page. This is in contrast to opening property pages for each user in the network to assign relevant folder permissions. </para>
          <para>
            <embeddedLabel>Recommendation:</embeddedLabel> Create user accounts that include members of various user groups, based on the departments that exist in your company or the various projects that people work on within your company. When you create a user group, you can assign a set of permissions to the group that will be applicable to all its members. For example, if you have group of users who are working in Department A, you can create a user group account called “Department A User Group,” and then add the relevant user accounts to this group. Next, you can assign permissions for the “Department A User Group” to access the server folder named “Accounting.”</para>
        </content>
      </section>
      <section address="BKMK_Devices" DoNotNumber="false">
        <title>Device management</title>
        <content>
          <para>To enable users to access server folders from computers in the network, you must connect the users’ computers to the server. Connecting computers to the server provides the following advantages:</para>
          <list class="bullet">
            <listItem>
              <para>Enables network users to securely access data that is stored on the server by using their user accounts.</para>
            </listItem>
            <listItem>
              <para>Enables you to manage client computers from the Dashboard.</para>
            </listItem>
            <listItem>
              <para>Protects client computers in the network by using Group Policy.</para>
            </listItem>
            <listItem>
              <para>Backs up data on client computers regularly.</para>
            </listItem>
            <listItem>
              <para>Monitors the health of the client computers.</para>
            </listItem>
          </list>
          <para>
            <embeddedLabel>Recommendation:</embeddedLabel> Connect all the computers (local or remote) that you want to administer to the server so that you can manage them from the <ui>Devices</ui> tab of the Windows Server Essentials Dashboard instead of using the native server tool, <ui>Active Directory Users and Computers</ui>. </para>
        </content>
      </section>
      <section address="BKMK_GroupPolicy" DoNotNumber="false">
        <title>Group Policy settings in Windows Server Essentials</title>
        <content>
          <para>Using  the Implement Group Policy Wizard in <token>wseblue_2</token> or <token>wseblue_experience</token> keeps your data centralized by turning on <externalLink><linkText>Folder Redirection</linkText><linkUri>http://technet.microsoft.com/library/cc732275.aspx</linkUri></externalLink>. In addition, it helps keep your network secure by enforcing that <externalLink><linkText>Windows Update</linkText><linkUri>http://windows.microsoft.com/windows/help/windows-update</linkUri></externalLink>, <externalLink><linkText>Windows Defender</linkText><linkUri>http://www.microsoft.com/security/pc-security/windows-defender.aspx</linkUri></externalLink>, and the <externalLink><linkText>Windows Firewall</linkText><linkUri>http://windows.microsoft.com/windows7/products/features/windows-firewall</linkUri></externalLink> remain turned on for all the client computers in the network. This eliminates relying on end users to turn on these settings on their PCs. </para>
          <para>
            <embeddedLabel>Recommendation:</embeddedLabel> We recommend that you do not turn off the Group Policy settings in Windows Server Essentials.</para>
        </content>
      </section>
      <section address="BKMK_ServerBackup" DoNotNumber="false">
        <title>Windows Server Backup</title>
        <content>
          <para>You can use Windows Server Backup to back up all volumes on your server, selected volumes, the system state, or specific files or folders. You can also create a backup that you can use for bare metal recovery. Instead of using native server tools, you can easily create and administer your backups from the <ui>Devices</ui> tab on the Windows Server Essentials Dashboard. For more information, see <externalLink><linkText>Manage server backup in Windows Server Essentials</linkText><linkUri>http://technet.microsoft.com/library/jj713501.aspx</linkUri></externalLink>.</para>
          <alert class="note">
            <para>Only servers running <token>wseblue_2</token> or <token>wseblue_experience</token> are automatically backed up. Other servers running the Window Server operating system can also be joined to these servers. They will be displayed on and can be monitored from the Dashboard, but automatic and centralized backups for these servers are not supported.</para>
          </alert>
          <para>
            <embeddedLabel>Recommendation:</embeddedLabel> Use removable storage devices for your backups. For cost effectiveness and high-performance, we recommend using a USB 3.0 device rather than an IEEE 1394 interface (also known as FireWire). You should use at least two removable storage devices, and ensure that they have a large enough capacity to store the server backups. Using multiple removable storage devices also provides a backup rotation.</para>
        </content>
      </section>
      <section address="BKMK_ClientBackup" DoNotNumber="false">
        <title>Client computer backups</title>
        <content>
          <para>By default, all computers that are connected to a server running <token>wseblue_2</token> or <token>wseblue_experience</token> will have their entire system and data backed up instead of relying on end users to back up their computers, or using non-Microsoft backup tools. These computer backups are stored in the <ui>Client Computer Backups</ui> server folder on a server that is running <token>wseblue_2</token> or <token>wseblue_experience</token>. This feature enables the recovery of individual files and folders, and a bare metal recovery of an entire client computer to a previous state. However, only the domain administrator can recover the data, and this feature does not scale beyond 75 client computers. For more information, see <externalLink><linkText>Manage client computer backup in Windows Server Essentials</linkText><linkUri>http://technet.microsoft.com/library/jj713516.aspx</linkUri></externalLink>.</para>
          <para>
            <embeddedLabel>Recommendation:</embeddedLabel> To conserve resources, you should only back up critical client computers and the most important data as your organization grows.</para>
        </content>
      </section>
      <section address="BKMK_FIleHistory" DoNotNumber="false">
        <title>File History backups</title>
        <content>
          <para>File History is a supplemental mechanism to use for client computer backups. The File History backups are stored in the <ui>File History</ui> server folder, which is located on a server that is running <token>wseblue_2</token> or <token>wseblue_experience</token>. From the File History backups, network users can restore versions of files from a specific point-in-time. In addition, network users can restore the files without asking for help from the administrator.</para>
          <para>
            <embeddedLabel>Recommendation:</embeddedLabel> By default, all users with connected clients running Windows 8.1 or Windows 8 will have their profile data backed up to the server running Windows Server Essentials. We recommend that you change the settings for File History backups (such as backup retention) per your company’s needs. For example, if your users save large data files on their computers, you may want to reduce the frequency of File History backups and the backup retention time.</para>
        </content>
      </section>
      <section address="BKMK_AzureBackup" DoNotNumber="false">
        <title>Azure Backup</title>
        <content>
          <para>
            <token>sbs8_mob_2</token> is an online backup service that is provided by Microsoft. You can use it to back up files and folders that are critical to your organization. For more information, see <externalLink><linkText>Manage Online Backup in Windows Server Essentials</linkText><linkUri>http://technet.microsoft.com/library/jj593190.aspx</linkUri></externalLink>. </para>
          <para>
            <token>sbs8_mob_2</token> encrypts, backups before transmission and stores the encrypted data in <token>azure_2</token>. These backups are safely stored offsite from your company’s location, and they are protected by reliable <token>azure_2</token> Storage. Online backup storage provides an additional layer of data protection with the on-premises backups, without having to maintain and invest in additional hardware. However <token>sbs8_mob_2</token> does not create a backup of your system’s state, so it cannot be used to perform a complete bare metal recovery.</para>
          <para>
            <embeddedLabel>Recommendation:</embeddedLabel> Protect the critical data for your organization by using <token>sbs8_mob_2</token>. In addition, use bandwidth throttling to reduce Internet traffic during working hours. For more information, see <externalLink><linkText>article 238145</linkText><linkUri>http://support.microsoft.com/kb/238145</linkUri></externalLink> in the Microsoft Knowledge Base.</para>
        </content>
      </section>
    </sections>
  </section>
  <section address="BKMK_Solution">
    <title>What are the steps to implement this solution?</title>
    <content>
      <para>You can follow the steps in this section to implement this solution. Make sure to verify the correct deployment of each step before proceeding to the next step.</para>
      <alert class="note">
        <para>The following steps make the assumption that there is already a server in the network that is running <token>wseblue_2</token> or <token>wseblue_experience</token>. For information about installing <token>wseblue_2</token> or the <token>wseblue_experience</token> role, see <legacyLink xlink:href="48ea6cd4-3955-4aaf-9236-2515a6c3e730">Install and Configure Windows Server 2012 R2 Essentials or Windows Server Essentials Experience [WSE_Blue]</legacyLink>.</para>
      </alert>
      <list class="ordered">
        <listItem>
          <para>
            <embeddedLabel>Create a storage space on the server.</embeddedLabel> </para>
          <para>To create a storage space, follow the instructions in <legacyLink xlink:href="1836682e-c7bb-4dd5-a2b5-6ff032693574#BKMK_6">Create a storage space</legacyLink>.</para>
          <para>You can also create a new two-way mirrored storage space by using the <externalLink><linkText>New-WssStorageSpace</linkText><linkUri>http://technet.microsoft.com/library/dn363546.aspx</linkUri></externalLink> Windows PowerShell cmdlet.</para>
          <para>After you create the storage space, verify that it is listed on the <ui>Hard Drives</ui> tab of the Dashboard. </para>
        </listItem>
        <listItem>
          <para>
            <embeddedLabel>Create server folders for various departments or data types as needed.</embeddedLabel>
          </para>
          <para>To create server folders, follow the instructions in <legacyLink xlink:href="090cf1b8-7b9b-48b9-ae85-b98477b8d7cc#BKMK_5">Add or move a server folder</legacyLink>.</para>
          <alert class="note">
            <para>If your organization has shared folders that are already being used, also move the data that is stored on various devices to the server folders that you create in this step.</para>
          </alert>
          <para>When you create a new server folder using the Add Folder Wizard, on the <ui>Type a name and description for the folder</ui> page, in the <ui>Location</ui> field, store the folder in its default location, which is the storage space that you created in Step 1, to ensure high availability for the data. Verify that all the server folders you created are listed on the <ui>Storage</ui> tab of the Dashboard.</para>
          <para>You can also add a server folder by using the <command>Add-WssFolder</command> Windows PowerShell cmdlet. For more information, see <externalLink><linkText>Add-WssFolder</linkText><linkUri>http://technet.microsoft.com/library/dn155961.aspx</linkUri></externalLink>.</para>
        </listItem>
        <listItem>
          <para>
            <embeddedLabel>Create user groups and user accounts</embeddedLabel>.</para>
          <para>Create user accounts for all the users in the network, and then create user groups based on the various departments and projects in your organization. Next, add the user accounts to the relevant user groups based on the departments or projects that the users are associated with. For step-by-step instructions to create user accounts, see <legacyLink xlink:href="0d115697-532b-48c2-a659-9f889e235326#BKMK_Manage1">Add a user account</legacyLink>. For more information about user groups, see <legacyLink xlink:href="0d115697-532b-48c2-a659-9f889e235326">Manage User Accounts in Windows Server Essentials [H2]</legacyLink>.</para>
          <para>You can also add a user account and user group by using the  <command>Add-WssUser</command> and <command>Add-WssUserGroup</command> Windows PowerShell cmdlets respectively. For more information, see <externalLink><linkText>Add-WssUser</linkText><linkUri>http://technet.microsoft.com/library/dn155951.aspx</linkUri></externalLink> and <externalLink><linkText>Add-WssUserGroup</linkText><linkUri>http://technet.microsoft.com/library/dn390998.aspx</linkUri></externalLink>.</para>
          <para>Verify that all the user accounts and user groups are listed on the <ui>Users</ui> and <ui>User Groups</ui> tabs of the Dashboard. </para>
        </listItem>
        <listItem>
          <para>
            <embeddedLabel>Assign user access permissions for the server folders</embeddedLabel>.</para>
          <para>To assign permissions to user accounts so that users can access the server folders, follow instructions in <legacyLink xlink:href="090cf1b8-7b9b-48b9-ae85-b98477b8d7cc#BKMK_1">Manage access to server folders</legacyLink>.</para>
          <para>After you have granted user access permissions, you can view or modify permissions to network resources for any user account by viewing the user account’s properties from the Dashboard. For more information, see <legacyLink xlink:href="0d115697-532b-48c2-a659-9f889e235326">Manage User Accounts in Windows Server Essentials [H2]</legacyLink>.</para>
        </listItem>
        <listItem>
          <para>
            <embeddedLabel>Connect all the client computers in the network to the server.</embeddedLabel>
          </para>
          <para>All clients need to be connected to a server that is running <token>wseblue_2</token> or <token>wseblue_experience</token>. Before you connect a client to a server that is running Windows Server Essentials, review the following:</para>
          <list class="nobullet">
            <listItem>
              <para>
                <legacyLink xlink:href="149a5d34-43b7-4b9e-99e7-9f2294ab9ddb#BKMK_4">Supported operating systems for client computers</legacyLink>
              </para>
            </listItem>
            <listItem>
              <para>
                <legacyLink xlink:href="149a5d34-43b7-4b9e-99e7-9f2294ab9ddb#BKMK_2">Prerequisites for connecting a computer to the server</legacyLink>
              </para>
            </listItem>
          </list>
          <para>Run the Connect Computer to the Server Wizard on all computers in your network, whether they are local or remote. For step-by-step instructions to connect client computers to a server running <token>wseblue_experience</token>, see <legacyLink xlink:href="149a5d34-43b7-4b9e-99e7-9f2294ab9ddb#BKMK_9">Connect computers to the server</legacyLink>.</para>
          <para>After you have connected a client computer to the server, verify that the computer’s name is listed on the <ui>Devices</ui> tab of the Dashboard. You can manage all computers that are connected to the server through the administrative tasks that are listed in the task pane of the Dashboard. For more information, see <legacyLink xlink:href="f5fe1088-ebe7-4799-a47d-075b0048dea1#BKMK_1">Manage devices by using the Dashboard</legacyLink>.</para>
        </listItem>
        <listItem>
          <para>
            <embeddedLabel>Implement Group Policy settings.</embeddedLabel>
          </para>
          <para>To implement Group Policy settings in Windows Server Essentials, turn on settings for Folder Redirection, Windows Defender, Windows Firewall, and Windows Update as discussed in <legacyLink xlink:href="f5fe1088-ebe7-4799-a47d-075b0048dea1#BKMK_5">Configure Group Policy settings for folder redirection and security</legacyLink>.</para>
        </listItem>
        <listItem>
          <para>
            <embeddedLabel>Set up Windows Server Backup.</embeddedLabel>
          </para>
          <para>To set up a backup for your server, follow instructions in <legacyLink xlink:href="441c2d6c-435a-42cb-90f2-6d680d279d34">Set up or customize server backup [SBS8_SrvrBackUp]</legacyLink>.</para>
          <para>After you set up the backup for your server, the <ui>Customize backup for the server</ui> task appears on the <ui>Devices</ui> tab of the Dashboard when you select your server from the list of devices. You can change the server backup settings with this task.</para>
        </listItem>
        <listItem>
          <para>
            <embeddedLabel>Set up the client computer backup.</embeddedLabel>
          </para>
          <para>By default, client backups are automatically configured when you connect a client computer to a server that is running <token>wseblue_2</token> or <token>wseblue_experience</token>. A backup is performed on a daily basis for every computer that is configured.</para>
          <para>As the number of computers increase in your organization, we recommend that you back up only computers that contain critical company data. For more client computer backup-related tasks, see <legacyLink xlink:href="1b4776e8-9504-4b98-ae80-11da797d9819">Manage Client Computer Backup in Windows Server Essentials [SBS8_Backup]</legacyLink>.</para>
        </listItem>
        <listItem>
          <para>
            <embeddedLabel>Set up File History backup settings</embeddedLabel>.</para>
          <para>For all client computers that are running Windows 8.1 or Windows 8 and are connected to Windows Server Essentials, File History is automatically turned on. By default, the data on the Desktop and in the <ui>Documents</ui> folder is backed up on an hourly basis. The backup is stored on the server for a year. You can configure the File History backup setting for each computer by using the <embeddedLabel>Change the File History setting</embeddedLabel> task, which you can access from the <ui>Users</ui> tab on the Dashboard. For more information, see <externalLink><linkText>Managing File History in Windows Server 2012 Essentials</linkText><linkUri>http://blogs.technet.com/b/sbs/archive/2012/12/17/managing-file-history-in-windows-server-2012-essentials.aspx</linkUri></externalLink>.</para>
        </listItem>
        <listItem>
          <para>
            <embeddedLabel>Set up your server for online backup with <token>sbs8_mob_2</token></embeddedLabel>. </para>
          <para>To set up your server for online backup by using <token>sbs8_mob_2</token>, use the following steps:</para>
          <list class="ordered">
            <listItem>
              <para>
                <legacyLink xlink:href="95a9f593-fad7-4335-bd4d-c7bb8c033efb#BKMK_16">Sign up for Azure Backup Service</legacyLink>
              </para>
            </listItem>
            <listItem>
              <para>
                <legacyLink xlink:href="95a9f593-fad7-4335-bd4d-c7bb8c033efb#BKMK_1">Upload a certificate to the Azure Backup vault</legacyLink>
              </para>
            </listItem>
            <listItem>
              <para>
                <legacyLink xlink:href="95a9f593-fad7-4335-bd4d-c7bb8c033efb#BKMK_5">Register this server for backup</legacyLink>
              </para>
            </listItem>
            <listItem>
              <para>
                <legacyLink xlink:href="95a9f593-fad7-4335-bd4d-c7bb8c033efb#BKMK_2">Configure online backup</legacyLink>
              </para>
            </listItem>
          </list>
          <alert class="note">
            <para>Before you begin to integrate your server with <token>sbs8_mob_2</token>, ensure that you turn off the enhanced Internet security settings on your server by using Server Manager.</para>
          </alert>
          <para>After you have completed the integration of your server with <token>sbs8_mob_2</token>, verify that the <ui>Online Backup</ui> tab has been added to the Dashboard. From this tab, you can configure online backup settings to perform regularly scheduled backups. To initiate an online backup, click <ui>Start backup now</ui> on the <ui>Online Backup</ui> tab of the Dashboard, and then verify that the server backup was created.</para>
        </listItem>
      </list>
      <para>After you complete Steps 1 through 10, all your organization’s goals as listed in this document are met as follows:</para>
      <list class="bullet">
        <listItem>
          <para>Your organization’s data is now stored in a central location on a server running <token>wseblue_2</token> or <token>wseblue_experience</token> so that all network users can easily access it.</para>
        </listItem>
        <listItem>
          <para>You have created a storage space to use as your destination for creating server folders, which allows you to easily expand the storage capacity of your server.</para>
        </listItem>
        <listItem>
          <para>You have set access permissions for user accounts in your network, so only selected users can access server folders and the data in them as needed.</para>
        </listItem>
        <listItem>
          <para>You have defined a schedule for creating backups by using Windows Server Backup, which solves the problem of inconsistent manual backups.</para>
        </listItem>
        <listItem>
          <para>In the event of hardware failure, you can restore a client computer or server from its backup. </para>
        </listItem>
        <listItem>
          <para>If the on-site backups are unavailable, you can restore your files and folders from your online backups stored in <token>azure_2</token>.</para>
        </listItem>
      </list>
    </content>
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
              <para>Product evaluation/Get started</para>
            </TD>
            <TD>
              <para>
                <externalLink>
                  <linkText>Windows Server 2012 R2 Essentials Evaluation</linkText>
                  <linkUri>http://technet.microsoft.com/evalcenter/dn205288.aspx?wt.mc_id=TEC_144_1_7</linkUri>
                </externalLink>
              </para>
              <para>
                <externalLink>
                  <linkText>Windows Server 2012 R2 Datacenter Evaluation</linkText>
                  <linkUri>http://technet.microsoft.com/evalcenter/dn205286.aspx</linkUri>
                </externalLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Deployment</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="48ea6cd4-3955-4aaf-9236-2515a6c3e730">Install and Configure Windows Server 2012 R2 Essentials or Windows Server Essentials Experience [WSE_Blue]</legacyLink>
              </para>
              <para>
                <legacyLink xlink:href="958ecbde-ba6f-4789-88da-58542b8b1faf">Windows Server Essentials Experience Overview [fwlink_blue]</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Operations</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="4f1902f1-a0e0-49a6-afa7-3c4b61a11b48">Manage Windows Server Essentials [H2]</legacyLink>
              </para>
              <para>
                <link xlink:href="74731157-645e-4ddc-953a-c76218c815fe">Secure remote access in small and midsize businesses</link>
              </para>
              <para>
                <link xlink:href="9e87affa-0edf-414d-9ddf-85195ad5f330">Improve collaboration in small and midsize businesses</link>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Support</para>
            </TD>
            <TD>
              <para>
                <externalLink>
                  <linkText>Windows Server 2012 Essentials Forum</linkText>
                  <linkUri>http://social.technet.microsoft.com/Forums/windowsserver/home?forum=winserveressentials</linkUri>
                </externalLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Reference</para>
            </TD>
            <TD>
              <para>
                <externalLink>
                  <linkText>Windows Server Essentials Cmdlets in Windows PowerShell</linkText>
                  <linkUri>http://technet.microsoft.com/library/dn205088.aspx</linkUri>
                </externalLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Community resources</para>
            </TD>
            <TD>
              <para>
                <externalLink>
                  <linkText>The Windows Server Essentials and Small Business Server Blog</linkText>
                  <linkUri>http://blogs.technet.com/b/sbs/</linkUri>
                </externalLink>
              </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics />
</developerConceptualDocument>