---
title: Secure remote access in small and midsize businesses
ms.custom: na
ms.prod: windows-server-2012-r2-essentials
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 74731157-645e-4ddc-953a-c76218c815fe
---
# Secure remote access in small and midsize businesses
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://clixdevr3.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>
      <embeddedLabel>How can this guide help you?</embeddedLabel> This guide explains how you can enable users to easily and securely access company data through a variety of Internet-connected devices from any location.</para>
    <para>This guide describes a prescriptive, tested design and implementation solution that can help you provide secure remote access to your network users, by centralizing data storage, configuring your network for remote access, and restricting data access permissions.</para>
    <para>
      <legacyBold>In this solution guide:</legacyBold>
    </para>
    <list class="bullet">
      <listItem>
        <para>
          <link xlink:href="74731157-645e-4ddc-953a-c76218c815fe#BKMK_ProblemH1">Scenario, problem statement, and goals</link>
        </para>
      </listItem>
      <listItem>
        <para>
          <link xlink:href="74731157-645e-4ddc-953a-c76218c815fe#BKMK_Strategy">What is the recommended design for this solution?</link>
        </para>
      </listItem>
      <listItem>
        <para>
          <link xlink:href="74731157-645e-4ddc-953a-c76218c815fe#BKMK_DesignDetails">Why are we recommending this design?</link>
        </para>
      </listItem>
      <listItem>
        <para>
          <link xlink:href="74731157-645e-4ddc-953a-c76218c815fe#BKMK_Solution">What are the steps to implement this solution?</link>
        </para>
      </listItem>
    </list>
    <para>The following diagram illustrates the problem and scenario that this solution guide addresses.</para>
    <para> <legacyBold>Problems associated with remote data access</legacyBold></para>
    <mediaLink>
      <image xlink:href="77b0e908-e808-4285-a12f-7f8c747cced3" />
    </mediaLink>
  </introduction>
  <section address="BKMK_ProblemH1">
    <title>Scenario, problem statement, and goals</title>
    <content>
      <para>This section describes the scenario, problem, and goals for an example organization. </para>
    </content>
    <sections>
      <section>
        <title address="BKMK_Scenario">Scenario</title>
        <content>
          <para>The organization is small to midsize with up to 100 users and 200 devices, and it is looking for a way for users to securely access company data when they are off-premises and using a wide range of Internet-connected devices. The users do not have consistent access to company resources onsite and offsite. Files are not accessible after a network user steps outside the office. As a result, network users are saving company data on their mobile devices or sending it through email. They use a PC to email data from work, and they can email data to the office from their laptops when they are working remotely. Sometimes after work hours, users need to work on files or access data from a variety of devices, such as tablets, pads, or laptops; however, users are unable to use their line-of-business applications when they are offsite.</para>
        </content>
      </section>
      <section address="BKMK_Problem">
        <title>Problem statement</title>
        <content>
          <para>The organization wants to address the following problems:</para>
          <list class="bullet">
            <listItem>
              <para>Users do not have a secure way to access company data and line-of-business applications outside the office network.</para>
            </listItem>
            <listItem>
              <para>Users do not have a secure way to access network resources on mobile devices.</para>
            </listItem>
            <listItem>
              <para>Users are saving company’s data on multiple devices (for example, on a PC when at work, and on their laptop when remote). This is leading to multiple file versions that are hard to track and locate.</para>
            </listItem>
            <listItem>
              <para>Financial loss occurs when users are unable to work because they do not have the line-of-business applications installed on their personal network-connected devices.</para>
            </listItem>
          </list>
        </content>
      </section>
      <section address="BKMK_Goals">
        <title>Organizational goals</title>
        <content>
          <para>Your organization is looking for a solution that allows you to:</para>
          <list class="bullet">
            <listItem>
              <para>Provide secure access to company data and resources for users outside the office network.</para>
            </listItem>
            <listItem>
              <para>Enable users to access network resources on mobile devices.</para>
            </listItem>
            <listItem>
              <para>Eliminate version conflicts that arise because multiple file versions are created when users work on local copies when they are outside the network. </para>
            </listItem>
            <listItem>
              <para>Prevent financial loss caused by lack of access to line-of-business applications outside the office.</para>
            </listItem>
          </list>
        </content>
      </section>
    </sections>
  </section>
  <section address="BKMK_Strategy">
    <title>What is the recommended design for this solution?</title>
    <content>
      <para>The following diagram illustrates how to store, protect, and remotely access company data from a server running <token>wseblue_2</token> or the Standard and Datacenter editions of <token>winblue_server_2</token> with the <token>wseblue_experience</token> role installed (referred to as <token>wseblue_experience</token> in the rest of the document).</para>
      <para> </para>
      <para>
        <legacyBold>Solution design for providing secure access to data when users are outside the network</legacyBold>
      </para>
      <mediaLink>
        <image xlink:href="545a6ca9-b839-4566-bd2d-9027b80d8a2f" />
      </mediaLink>
      <para>
        <token>wseblue_2</token> (appropriate for use for up to 25 users and 50 devices) and the Standard and Datacenter editions of <token>winblue_server_2</token> with the <token>wseblue_experience</token> role installed (appropriate for use for up to 100 users and 200 devices) provide a solution for small to midsize business to enable users to easily and securely access company data through a variety of Internet-connected devices.</para>
      <para>The following table lists the technologies that are included in <token>wseblue_2</token> and <token>wseblue_experience</token> that are part of this solution design, and it describes the reason for the design choice.</para>
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
              <para>Use the Dashboard to perform all administrative tasks in your network, such as creating user accounts, granting access permissions, creating storages spaces and server folders, and setting up an Internet domain name.</para>
              <para>For information about the Dashboard, see <legacyLink xlink:href="f70a79de-9c56-4496-89b5-20a1bff2293e">Overview of the Dashboard in Windows Server Essentials [fwlink_SBS8_Admin]</legacyLink>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Remote Web Access</para>
            </TD>
            <TD>
              <para>Use the Remote Web Access portal to provide access to data and other network resources for users who are working outside your company network. With My Server app, users can securely access network resources using their network credentials. They are able to access resources from a wide range of Internet-connected devices. In addition, offsite users can connect to a computer that is on-premises by using a Remote Desktop session through Remote Web Access.</para>
              <para>For more information about configuring and using Remote Web Access, see <legacyLink xlink:href="f3ea40fa-b6ba-4d66-b754-221ca6271387">Manage Remote Web Access in Windows Server Essentials [A_Web_Admin_H2]</legacyLink> and  <legacyLink xlink:href="47ea21a0-5e05-4b4b-8fa4-338c82601276">Use Remote Web Access in Windows Server Essentials [A_Web_Client_H2]</legacyLink>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Virtual private network</para>
            </TD>
            <TD>
              <para>Use a virtual private network (VPN) to provide users with remote access to company data and other network resources or to connect to a computer that is on-premises by using a Remote Desktop session. With VPN, users can securely access network resources using their network credentials.</para>
              <para>For more information about a VPN, see <legacyLink xlink:href="cc2b264a-b9a8-4114-9f7b-8604f77096e5">Manage VPN in Windows Server Essentials [blue]</legacyLink>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>My Server app </para>
            </TD>
            <TD>
              <para>Use the My Server app with a device that is running the Windows 8.1, Windows 8, or Windows RT operating system, or a Windows Phone 8, to provide access to documents and media on your server. With My Server app, users can securely access network resources using their network credentials.</para>
              <para>For more information about the My Server app, see <legacyLink xlink:href="4e40b57f-6917-43ef-92e0-030baa9d2b99">Use the My Server App to Connect to Windows Server Essentials  [SBS8]</legacyLink>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Storage Spaces</para>
            </TD>
            <TD>
              <para>Use Storage Spaces to store your company data. With Storage Spaces, you can expand storage as your organization grows, ensure that your data has high availability, and make sure that your solution is cost effective. You do not need to spend money upfront on hardware, and you can scale up based on your business needs.</para>
              <para>For more information about Storage Spaces, see the <legacyLink xlink:href="1836682e-c7bb-4dd5-a2b5-6ff032693574#BKMK_5">Storage Spaces Overview</legacyLink> and <externalLink><linkText>Storage Spaces Frequently Asked Questions</linkText><linkUri>http://social.technet.microsoft.com/wiki/contents/articles/11382.storage-spaces-frequently-asked-questions-faq.aspx</linkUri></externalLink>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Server Folders</para>
            </TD>
            <TD>
              <para>Store your organization’s files and folders in the server folders that you create on your server. This enables you to consolidate your data in one central location that all network users can access. When you store your data in server folders, you can protect it against total server failure by using Windows Server Backup and Windows Azure Backup.</para>
              <para>For more information about server folders, see <legacyLink xlink:href="090cf1b8-7b9b-48b9-ae85-b98477b8d7cc">Manage Server Folders in Windows Server Essentials [A_Web_Admin_H2]</legacyLink>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>User management</para>
            </TD>
            <TD>
              <para>Create user accounts and user groups to control access to your company’s data and devices. When you create user groups, you can provide the same access level to network resources for all members.</para>
              <para>For more information, see <legacyLink xlink:href="0d115697-532b-48c2-a659-9f889e235326">Manage User Accounts in Windows Server Essentials [H2]</legacyLink>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Device management</para>
            </TD>
            <TD>
              <para>Join client computers to the network so that you can easily manage all the computers in the network through the Windows Server Essentials Dashboard.</para>
              <para>For information about all computer management-related tasks, see <legacyLink xlink:href="f5fe1088-ebe7-4799-a47d-075b0048dea1">Manage Devices in Windows Server Essentials [H2]</legacyLink>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Windows Server Essentials Group Policy</para>
            </TD>
            <TD>
              <para>Protect client computers from network attacks and keep the software and operating system on your computers up to date by implementing Windows Server Essentials Group Policy settings. </para>
              <list class="bullet">
                <listItem>
                  <para>For more information about Group Policy settings in Windows Server Essentials, see <legacyLink xlink:href="f5fe1088-ebe7-4799-a47d-075b0048dea1#BKMK_5">Configure Group Policy settings for folder redirection and security</legacyLink>.</para>
                </listItem>
                <listItem>
                  <para>For more information about Windows Defender, see <externalLink><linkText>What is Windows Defender?</linkText><linkUri>http://www.microsoft.com/security/pc-security/windows-defender.aspx</linkUri></externalLink></para>
                </listItem>
                <listItem>
                  <para>For more information about Windows Firewall, see <externalLink><linkText>Windows Firewall</linkText><linkUri>http://windows.microsoft.com/windows7/products/features/windows-firewall</linkUri></externalLink>.</para>
                </listItem>
                <listItem>
                  <para>For more information about Windows Update, see <externalLink><linkText>Windows Update</linkText><linkUri>http://windows.microsoft.com/windows/help/windows-update</linkUri></externalLink>.</para>
                </listItem>
                <listItem>
                  <para>For more information about folder redirection, see <externalLink><linkText>Folder Redirection Overview</linkText><linkUri>http://technet.microsoft.com/library/cc732275.aspx</linkUri></externalLink>.</para>
                </listItem>
              </list>
            </TD>
          </tr>
        </tbody>
      </table>
      <para> </para>
    </content>
  </section>
  <section address="BKMK_DesignDetails">
    <title>Why are we recommending this design?</title>
    <content>
      <para>This section explains the details of the design considerations and the decisions that were made that led to the final solution design. It also provides the recommended configuration or usage of each feature that is used in this solution.</para>
    </content>
    <sections>
      <section address="BKMK_Dashboard">
        <title>Windows Server Essentials Dashboard</title>
        <content>
          <para>The Windows Server Essentials Dashboard in <token>wseblue_2</token> and <token>wseblue_experience</token> helps you quickly access key information and the management features of your server instead of using multiple native Windows Server Administration tools. For example, by using the Dashboard, you can create and manage user accounts and manage data in server folders. </para>
          <para>
            <embeddedLabel>Recommendation:</embeddedLabel> Use the Windows Server Essentials Dashboard to perform a majority of administrative tasks for your network. You can run tasks and wizards from the Dashboard to optimally configure the features in your server. By using the Dashboard, you can also configure remote access permissions to network resources (such as shared folders, client computers, and the VPN) on a per-user basis.</para>
        </content>
      </section>
      <section address="BKMK_StorageSpaces" DoNotNumber="false">
        <title>Storage Spaces</title>
        <content>
          <para>Options for providing high availability and resilient storage for your company’s data include using the built-in RAID controller that comes with common server hardware. With this storage option, you could provide the storage availability and resiliency you need, but it can be relatively complex and costly. </para>
          <para>In contrast, you can use the Storage Spaces feature to create low-cost, resilient, and dynamically expandable data volumes to store your business data, rather than storing it on standard hard drives. Storage Spaces include virtual hard disk drives (VHDs) that appear on the <ui>Hard Drives</ui> tab of the Dashboard. </para>
          <para>Storage Spaces helps you save files to two or more drives so that your files remain safe if a drive fails. With Storage Spaces, you can virtualize your server’s storage by grouping industry standard hard drives into storage pools, and then create VHDs (called storage spaces) from the available capacity in the storage pools. You can use these storage spaces to store your company’s data in one central location, instead of all users saving data on their PCs.</para>
          <para>
            <embeddedLabel>Recommendation:</embeddedLabel> For small businesses with fewer than 10 users, use at least three SAS or SATA drives—one drive to be used to back up the operating system, and the other two to be used for storage spaces. We recommend that you create a storage space by using at least two drives with mirrored resiliency. </para>
          <para>For small businesses with more than 10 users or midsize businesses with up to 100 users, configure at least three SAS drives with Storage Spaces—one drive to be used to back up the operating system, and the other two to be used for storage spaces. We also recommend providing a server chassis that supports adding more drives for expansion. </para>
        </content>
      </section>
      <section address="BKMK_ServerFolders" DoNotNumber="false">
        <title>Server Folders</title>
        <content>
          <para>By using server folders, you can store files that are located on client computers in a central location instead of users storing files on their PCs. </para>
          <para>Storing files in server folders ensures that your files are easy to back up and easy to access. They are located in a place that is accessible from every client. Files are secure because accessing them requires using authenticated network credentials.</para>
          <para>
            <embeddedLabel>Recommendation:</embeddedLabel> Create server folders on a Storage Space drive and create separate server folders for departments or projects. For example, if you have an accounting department, you can create a folder called “Accounting.” Creating the server folder on a Storage Space drive increases data availability (because of mirroring). </para>
          <para>We also recommend that you set a quota for your server folders so that you are alerted when a server folder is about to reach its capacity. When you are alerted, you can delete files in the server folder to increase available space for storage, or you can add more space to the server folder and adjust its quota settings.</para>
        </content>
      </section>
      <section address="BKMK_UsersGroups">
        <title>Users and groups management</title>
        <content>
          <para>User accounts and user group accounts help you specify permissions that allow users to access your company data. This protects your company data from unintended user access. You can easily manage access to your network resources by creating user accounts for all your network users from the <ui>Users</ui> tab of the Windows Server Essentials Dashboard. </para>
          <para>In addition, you can create user group accounts and add the user accounts as members. All members of a user group account share the same security access level to server resources. Group membership simplifies resource management because you can specify permissions for a group of users on one page. This is in contrast to opening property pages for each user in the network to assign relevant folder permissions. </para>
          <para>
            <embeddedLabel>Recommendation:</embeddedLabel> Create user accounts that include members of various user groups, based on the departments that exist in your company or the various projects that people work on within your company. When you create user groups, you can assign a set of permissions to the user groups that will be applicable to all its members. For example, if you have group of users who are working in Accounting Department A, you can create a user group account called “Department A User Group,” and then add the relevant user accounts to this group. Next, you can assign the “Department A User Group” permissions to access the server folder named “Accounting.” </para>
          <para>For each user account in your network, you can configure remote access permissions, depending on the method that is used for remote access (such as Remote Web Access or a VPN). You can also configure access to network resources (such as server folders and client computers). For example, you can create user groups for “VPN Users” and “RWA Users,” configure remote access permissions for these groups, and then add the user accounts that you want to have remote access privileges to these groups.</para>
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
              <para>Protects client computers in the network by using Group Policy settings.</para>
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
          <para>You can use the Implement Group Policy Wizard in <token>wseblue_2</token> or <token>wseblue_experience</token> to centralize your data by turning on <externalLink><linkText>Folder Redirection</linkText><linkUri>http://technet.microsoft.com/library/cc732275.aspx</linkUri></externalLink>. In addition, use this wizard to help keep your network secure by enforcing that <externalLink><linkText>Windows Update</linkText><linkUri>http://windows.microsoft.com/windows/help/windows-update</linkUri></externalLink>, <externalLink><linkText>Windows Defender</linkText><linkUri>http://www.microsoft.com/security/pc-security/windows-defender.aspx</linkUri></externalLink>, and the <externalLink><linkText>Windows Firewall</linkText><linkUri>http://windows.microsoft.com/windows7/products/features/windows-firewall</linkUri></externalLink> remain turned on for all the client computers in the network. This eliminates relying on end users to turn on these settings on their PCs. </para>
          <para>
            <embeddedLabel>Recommendation:</embeddedLabel> We recommend that you do not turn off the Group Policy settings in Windows Server Essentials.</para>
        </content>
      </section>
      <section>
        <title>Anywhere Access</title>
        <content>
          <para>When you configure the Anywhere Access functionalities (Remote Web Access and the VPN), you enable network users to access server resources from any location that has an Internet connection, at any time, and on almost any device. </para>
          <para>
            <embeddedLabel>Recommendation:</embeddedLabel> Run the Set Up Anywhere Access Wizard to set up Remote Web Access and a virtual private network. Fix the issues that are reported by the wizard when it completes.</para>
        </content>
        <sections>
          <section>
            <title>Remote Web Access</title>
            <content>
              <para>Remote Web Access provides a streamlined, touch-friendly browser experience for accessing applications and data from virtually anywhere that you have an Internet connection and by using almost any device.</para>
              <para>
                <embeddedLabel>Recommendation:</embeddedLabel> Configure the permissions of users and user groups for Remote Web Access so that remote users can securely access data from off-premises locations.</para>
            </content>
          </section>
          <section>
            <title>Virtual private network</title>
            <content>
              <para>Virtual private network (VPN) connections enable users who are working at home or on the road to access a server on a private network by using the infrastructure that is provided by a public network, such as the Internet.</para>
              <para>
                <embeddedLabel>Recommendation:</embeddedLabel> Configure the permissions of users and user groups for the VPN so that remote users can connect to your server through a secure VPN connection.</para>
            </content>
          </section>
        </sections>
      </section>
      <section>
        <title>My Server 2012 R2 app</title>
        <content>
          <para>The My Server app lets you connect to resources and perform light administrative tasks on your Windows Server Essentials server from a device that is running the Windows 8.1, Windows 8, or Windows RT operating system. In My Server, you can manage users, devices, and alerts, and work with shared files on the server. When you are offline, you can continue to work with files that you recently accessed in My Server, and your offline changes are automatically synchronized with the server the next time you connect.</para>
          <para>
            <embeddedLabel>Recommendation:</embeddedLabel> Install the My Server app on any device that is running the Windows 8.1, Windows 8, or Windows RT operating system, and use My Server to access documents on your server.</para>
        </content>
      </section>
    </sections>
  </section>
  <section address="BKMK_Solution">
    <title>What are the high-level steps to implement this solution?</title>
    <content>
      <para>You can follow the steps in this section to implement this solution. Make sure to verify the correct deployment of each step before proceeding to the next step.</para>
      <alert class="note">
        <para>The following steps make the assumption that there is already a server in the network that is running <token>wseblue_2</token> or <token>wseblue_experience</token>. For information about installing <token>wseblue_2</token> or the <token>wseblue_experience</token> role, see <legacyLink xlink:href="48ea6cd4-3955-4aaf-9236-2515a6c3e730">Install and Configure Windows Server 2012 R2 Essentials or Windows Server Essentials Experience [WSE_Blue]</legacyLink>.</para>
      </alert>
      <list class="ordered">
        <listItem>
          <para>
            <embeddedLabel>Turn on Anywhere Access.</embeddedLabel>
          </para>
          <para>With Anywhere Access, you can manage Remote Web Access and VPN functionalities. To turn on Remote Web Access and a VPN, run the Set Up Anywhere Access Wizard from the <ui>Anywhere Access</ui> tab on the <ui>Settings</ui> page of the Dashboard. To turn on Remote Web Access, follow the instructions in <legacyLink xlink:href="f3ea40fa-b6ba-4d66-b754-221ca6271387#BKMK_TurnOnRWA">Manage Remote Web Access</legacyLink>. To turn on a VPN, follow the instructions in <legacyLink xlink:href="cc2b264a-b9a8-4114-9f7b-8604f77096e5">Manage VPN in Windows Server Essentials [blue]</legacyLink>.</para>
        </listItem>
        <listItem>
          <para>
            <embeddedLabel>Set up a domain name.</embeddedLabel>
          </para>
          <para>To set up a domain name, run the Set Up Your Domain Name Wizard and follow the instructions in <legacyLink xlink:href="f3ea40fa-b6ba-4d66-b754-221ca6271387#BKMK_SetUpName">Manage Remote Web Access</legacyLink>. If you do not have an existing domain name, you can get a free Microsoft personalized domain name (for example, <placeholder>yourhostname</placeholder>.remotewebaccess.com) during the Set Up Your Domain Name Wizard.</para>
        </listItem>
        <listItem>
          <para>
            <embeddedLabel>Create a storage space on the server.</embeddedLabel> </para>
          <para>To create a storage space, follow the instructions in the Create a storage space section of the <legacyLink xlink:href="1836682e-c7bb-4dd5-a2b5-6ff032693574#BKMK_6">Manage Server Storage in Windows Server Essentials</legacyLink>.</para>
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
          <para>When you create a new server folder by using the Add Folder Wizard, on the <ui>Type a name and description for the folder</ui> page, in the <ui>Location</ui> field, store the folder in its default location, which is the storage space that you created in Step 1, to ensure high availability for the data. Verify that all the server folders you created are listed on the <ui>Storage</ui> tab of the Dashboard.</para>
          <para>You can also add a server folder by using the <system>Add-WssFolder</system> Windows PowerShell cmdlet. For more information, see <externalLink><linkText>Add-WssFolder</linkText><linkUri>http://technet.microsoft.com/library/dn155961.aspx</linkUri></externalLink>.</para>
        </listItem>
        <listItem>
          <para>
            <embeddedLabel>Create user accounts and user groups</embeddedLabel>.</para>
          <para>Create user accounts for all the users in the network, and then create user groups that are based on the departments and projects in your organization. You can also create user groups according to the method of remote access, such as users who access data through the VPN, or users who access data through Remote Web Access. </para>
          <para>Next, add the user accounts to the relevant user groups, based on the departments, projects, or remote access methods that the users are associated with. For step-by-step instructions to create user accounts, see <legacyLink xlink:href="0d115697-532b-48c2-a659-9f889e235326#BKMK_Manage1">Add a user account</legacyLink>. For more information about user groups, see <legacyLink xlink:href="0d115697-532b-48c2-a659-9f889e235326">Manage User Accounts in Windows Server Essentials [H2]</legacyLink>.</para>
          <para>Verify that all the user accounts and user groups are listed on the <ui>Users</ui> and <ui>User Groups</ui> tabs of the Dashboard. </para>
        </listItem>
        <listItem>
          <para>
            <embeddedLabel>Assign user access permissions for the server folders</embeddedLabel>.</para>
          <para>To assign permissions to user accounts so that users can access the server folders, follow instructions in <legacyLink xlink:href="090cf1b8-7b9b-48b9-ae85-b98477b8d7cc#BKMK_1">Manage access to server folders</legacyLink>.</para>
          <para>After you have granted user access permissions, you can verify, view or modify permissions to network resources for any user account by viewing the user account’s properties from the Dashboard. For more information, see <legacyLink xlink:href="0d115697-532b-48c2-a659-9f889e235326">Manage User Accounts in Windows Server Essentials [H2]</legacyLink>.</para>
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
            <embeddedLabel>Configure remote access permissions for user accounts and network devices.</embeddedLabel>
          </para>
          <para>Assign remote access permissions to the user accounts and the network devices that users can use to connect remotely. This connection can be through a VPN connection or through a Remote Desktop session by using Remote Web Access. For step-by-step instructions, see the following sections in <legacyLink xlink:href="0d115697-532b-48c2-a659-9f889e235326">Manage User Accounts in Windows Server Essentials [H2]</legacyLink>:</para>
          <list class="bullet">
            <listItem>
              <para>Give user accounts Remote Desktop permissions</para>
            </listItem>
            <listItem>
              <para>Allow users to establish a Remote Desktop session to their computer</para>
            </listItem>
            <listItem>
              <para>Change remote access permissions for a user account</para>
            </listItem>
            <listItem>
              <para>Change virtual network permissions for a user account</para>
            </listItem>
          </list>
        </listItem>
        <listItem>
          <para>
            <embeddedLabel>Implement Group Policy settings.</embeddedLabel>
          </para>
          <para>To implement Group Policy settings in Windows Server Essentials, turn on settings for Folder Redirection, Windows Defender, Windows Firewall, and Windows Update as discussed in <legacyLink xlink:href="f5fe1088-ebe7-4799-a47d-075b0048dea1#BKMK_5">Configure Group Policy settings for folder redirection and security</legacyLink>.</para>
          <para>After the Group Policy settings has been implemented, verify that the task <ui>Configure group policy settings</ui> appears on the <ui>Devices</ui> tab. </para>
        </listItem>
        <listItem>
          <para>
            <embeddedLabel>Install the My Server 2012 R2 app.</embeddedLabel>
          </para>
          <para>Install the My Server 2012 R2 app on your Windows Phone and devices running Windows 8.1 and Windows 8. You can install the My Server 2012 R2 app for devices running Windows from the <externalLink><linkText>Windows Store</linkText><linkUri>http://apps.microsoft.com/windows/app/my-server-2012-r2/67e86695-bda3-4f32-96c4-2e20e56f1cf3</linkUri></externalLink>. For information about using this app, see <legacyLink xlink:href="4e40b57f-6917-43ef-92e0-030baa9d2b99">Use the My Server App to Connect to Windows Server Essentials  [SBS8]</legacyLink>.</para>
          <para>You can install the My Server 2012 R2 app on your Windows Phone from the <externalLink><linkText>Windows Phone Store</linkText><linkUri>http://www.windowsphone.com/store/app/my-server-2012-r2/44f596b5-0477-4096-b96e-ddd6ef64ad6b</linkUri></externalLink>. Verify that the My Server app is installed on your device. For information about the My Server 2012 R2 phone app, see the blog post <externalLink><linkText>My Server 2012 R2 Windows and Windows Phone apps</linkText><linkUri>http://blogs.technet.com/b/sbs/archive/2013/11/19/my-server-2012-r2-windows-and-windows-phone-apps.aspx</linkUri></externalLink>.</para>
          <para>To successfully use the My Server 2012 R2 app for Windows Phone and devices running Windows 8.1 or Windows 8 in Windows Server Essentials, you must first install the server certificate on your device. The certificate enables you to connect your device to your server running Windows Server Essentials from your local network. For step-by-step instructions to install the server certificate, see the “How to connect to my server from my local network” section in <legacyLink xlink:href="4e40b57f-6917-43ef-92e0-030baa9d2b99">Use the My Server App to Connect to Windows Server Essentials  [SBS8]</legacyLink>.</para>
        </listItem>
      </list>
      <para>After you complete the previous steps, the goals for your organization as listed in this document are met as follows:</para>
      <list class="bullet">
        <listItem>
          <para>Network users can use Remote Web Access or a VPN from outside the office network to securely access company data and resources.</para>
        </listItem>
        <listItem>
          <para>Users are able to access network resources from a wide range of mobile devices by using Remote Web Access, a VPN, or the My Server 2012 R2 app.</para>
        </listItem>
        <listItem>
          <para>Users can work from outside the network so that they no longer need to use local copies when they are working off-premises. Version conflicts that arise from multiple file versions are eliminated. </para>
        </listItem>
        <listItem>
          <para>Business loss is prevented because network users can access their line-of-business applications outside of work hours by using a VPN or by using Remote Web Access to create a Remote Desktop session with their on-site client computers. </para>
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
                  <linkText>Windows Server 2012 R2 Essentials Evaluation</linkText>
                  <linkUri>http://technet.microsoft.com/evalcenter/dn205288.aspx?wt.mc_id=TEC_144_1_7</linkUri>
                </externalLink>
              </para>
              <para>
                <externalLink>
                  <linkText>Windows Server 2012 R2 Datacenter Evaluation</linkText>
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
                  <linkText>Windows Server 2012 Essentials Forum</linkText>
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