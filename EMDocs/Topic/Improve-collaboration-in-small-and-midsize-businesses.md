---
title: Improve collaboration in small and midsize businesses
ms.custom: na
ms.prod: windows-server-2012-r2-essentials
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9e87affa-0edf-414d-9ddf-85195ad5f330
---
# Improve collaboration in small and midsize businesses
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://clixdevr3.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>
      <embeddedLabel>How can this guide help you?</embeddedLabel> This solution guide describes how you can enable your employees and external partners to securely access secured data in your small or midsized business.</para>
    <para>This guide describes a prescriptive, tested design and implementation solution that can help you enable collaboration between employees and external business partners and vendors in a more secured way by allowing them to securely access shared data.</para>
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
          <link xlink:href="416847db-659f-495e-9893-0855378ab4f2#BKMK_Strategy">Recommended planning and design approach for this solution</link>
        </para>
      </listItem>
      <listItem>
        <para>
          <link xlink:href="416847db-659f-495e-9893-0855378ab4f2#BKMK_Solution">High-level steps to implement this solution</link>
        </para>
      </listItem>
    </list>
    <para>The following diagram illustrates the problem and scenario that this solution guide addresses.</para>
    <para> <legacyBold>Problems associated with collaboration between employees and vendors or partners</legacyBold></para>
    <para> </para>
    <mediaLink>
      <image xlink:href="66729432-ff2a-4b70-b2f0-57b8211daf0b" />
    </mediaLink>
    <para> </para>
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
          <para>An organization is a small to midsize business and the business administrator is looking for a way that employees can collaborate with partners and vendors. The employees currently use Microsoft Office applications—such as Word, Excel, and PowerPoint—on their local computers. The employees save documents on local computers and share them with business vendors and partners through print copies and emails, or by creating local shared resources.</para>
        </content>
      </section>
      <section address="BKMK_Problem">
        <title>Problem statement</title>
        <content>
          <para>Currently, the organization does not have a secure way of sharing documents with its vendors and partners. The overall problem to solve is:</para>
          <para>
            <embeddedLabel>As a small or midsize business administrator, how can the business administrator improve secure collaboration between employees and partners or vendors?</embeddedLabel>
          </para>
          <para>Some aspects of this problem are:</para>
          <list class="bullet">
            <listItem>
              <para>Documents are not shared between employees and vendors or partners in a secure manner.</para>
            </listItem>
            <listItem>
              <para>The risk exists that business-critical data could be displayed inadvertently to users who should not be seeing the data.</para>
            </listItem>
            <listItem>
              <para>It is difficult to track multiple file versions that result from employees and vendors saving company data on multiple devices (for example, on a user’s computer at work and a vendor’s computer offsite).</para>
            </listItem>
            <listItem>
              <para>User management and file management are not centralized for documents.</para>
            </listItem>
          </list>
        </content>
      </section>
      <section address="BKMK_Goals">
        <title>Organization goals</title>
        <content>
          <para>The organization’s goals for improved collaboration are:</para>
          <list class="bullet">
            <listItem>
              <para>Store data in the cloud and/or on-premises so that employees and vendors can easily access the data for collaboration when they want and from where they want.</para>
            </listItem>
            <listItem>
              <para>Provide specific employees, partners, and vendors access to documents to prevent losing control of the information.</para>
            </listItem>
            <listItem>
              <para>Eliminate version conflicts that arise because multiple file versions are created when employees and vendors work on local copies.</para>
            </listItem>
            <listItem>
              <para>Integrate and centralize the administration of collaboration-related cloud services and on-premises applications, such as Microsoft Outlook, Word, Excel, and PowerPoint.</para>
            </listItem>
            <listItem>
              <para>Increase productivity by enabling employees to collaborate with vendors and partners by using a broad range of cloud-based services.</para>
            </listItem>
            <listItem>
              <para>Centralize the management of permissions to documents stored on-premises and in the cloud.</para>
            </listItem>
          </list>
        </content>
      </section>
    </sections>
  </section>
  <section address="BKMK_Strategy">
    <title>What is the recommended planning and design approach for this solution?</title>
    <content>
      <para>The following diagram illustrates how to store, protect, and securely access data from a server running <token>wseblue_2</token> or <token>winblue_server_2</token> with the <token>wseblue_experience</token> role installed (referred to as <token>wseblue_experience</token> in the rest of the document).</para>
      <para>
        <legacyBold>Solution design for collaboration between employees and vendors or partners</legacyBold>
      </para>
      <para> </para>
      <mediaLink>
        <image xlink:href="d758f878-a47c-40ea-a50e-ea9f0ffc7b2a" />
      </mediaLink>
      <para> </para>
      <para>
        <token>wseblue_2</token> (appropriate for use for up to 25 users and 50 devices) and the Standard and Datacenter editions of <token>winblue_server_2</token> with the <token>wseblue_experience</token> role installed provide a solution for small to midsize business partners and owners that enables employees to easily collaborate with partners and vendors.</para>
      <para>The following table lists the technologies that are included in <token>wseblue_2</token> and <token>wseblue_experience</token> that are part of this solution design, and it describes the reason for the design choices.</para>
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
              <para>Use the Dashboard to perform all administrative tasks in your network, such as creating user accounts, granting access permissions, setting up server and client backups, creating Storage Spaces and server folders, and integrating with Microsoft Azure Backup.</para>
              <para>For more information, see <legacyLink xlink:href="f70a79de-9c56-4496-89b5-20a1bff2293e">Overview of the Dashboard in Windows Server Essentials [fwlink_SBS8_Admin]</legacyLink>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Storage Spaces</para>
            </TD>
            <TD>
              <para>Use Storage Spaces for storing your company’s data. With Storage Spaces, you can expand storage as your organization grows, ensure that you are providing high availability for your data, and provide a cost-effective solution. You do not need to spend upfront money on hardware, and you can scale up based on your business needs.</para>
              <para>For more information, see the <legacyLink xlink:href="1836682e-c7bb-4dd5-a2b5-6ff032693574#BKMK_5">Storage Spaces Overview</legacyLink> and <externalLink><linkText>Storage Spaces Frequently Asked Questions</linkText><linkUri>http://social.technet.microsoft.com/wiki/contents/articles/11382.storage-spaces-frequently-asked-questions-faq.aspx</linkUri></externalLink>.</para>
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
              <para>Create user accounts for your employees and your vendors and partners who you collaborate with. Create a user group for each project that requires your employees to collaborate with external partners, and then add the appropriate employee and partner user accounts to the user group. When you create a user group, you can provide the same access level to network resources for all members.</para>
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
              <para>Group Policy settings</para>
            </TD>
            <TD>
              <para>Protect client computers from network attacks and keep the software and operating system on your computers up to date by implementing Windows Server Essentials Group Policy settings, which include settings for Windows Defender, Windows Firewall, and Windows Update. </para>
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
          <tr>
            <TD>
              <para>Office 365</para>
            </TD>
            <TD>
              <para>Integrate your server running Windows Server Essentials with Microsoft Office 365 so that you can use the Dashboard to manage your Office 365 services and resources with your on-premises resources, instead of managing them in two places.</para>
              <para>For more information, see <legacyLink xlink:href="3f8485e4-e10f-4f38-8a5e-d5227abd0d84">Manage Office 365 in Windows Server Essentials [WSE_O365_Integrate]</legacyLink>.</para>
              <alert class="note">
                <para>You do not need to subscribe to Office 365 in advance. You will be able to buy a subscription or sign up for a free trial when you integrate Office 365. </para>
                <para>If you would like to see plans and pricing for Office 365, see <externalLink><linkText>Compare Office 365 for business plans</linkText><linkUri>http://office.microsoft.com/compare-office-365-for-business-plans-FX102918419.aspx?CR_CC=200061904&amp;WT.srch=1&amp;WT.mc_ID=PS_bing_O365Comm_subscribe%20to%20office%20365_Text</linkUri></externalLink>.</para>
              </alert>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Microsoft online accounts management</para>
            </TD>
            <TD>
              <para>Create online accounts for all the employees in the network who need to collaborate with vendors and partners. Employees can sign in to the Office 365 portal by using these online accounts. When you complete the integration of Windows Server Essentials with Office 365, employees will be able to sign in to the Office 365 portal by using their network credentials. </para>
              <para>For more information, see <legacyLink xlink:href="c09f4cf6-4d12-49fe-9ae4-e6cb14027b9d">Manage Online Accounts for Windows Server Essentials Users [WSE_O365_Integrate]</legacyLink>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SharePoint Online</para>
            </TD>
            <TD>
              <para>All Office 365 subscription plans for businesses let you create team sites and libraries in SharePoint Online. SharePoint Online enables you to collaborate with your partners and vendors. With SharePoint Online, you can access documents and other information from anywhere, such as at the office, from home, or from a mobile device. After you integrate your server running <token>wseblue_2</token> or <token>wseblue_experience</token> with Microsoft Office 365, you can manage SharePoint libraries and set up access permissions from the Dashboard, without visiting the Office 365 portal. </para>
              <para>For more information about managing SharePoint Online in Windows Server Essentials, see <legacyLink xlink:href="f5fe1088-ebe7-4799-a47d-075b0048dea1">Manage Devices in Windows Server Essentials [H2]</legacyLink>. </para>
              <para>For an overview of SharePoint Online, see <externalLink><linkText>SharePoint Online</linkText><linkUri>http://office.microsoft.com/sharepoint/sharepoint-2013-overview-collaboration-software-features-FX103789323.aspx</linkUri></externalLink>.</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para> </para>
      <para>
        <token>wseblue_2</token> and <token>wseblue_experience</token> include the following features and technologies that can help a small or midsize Microsoft business partner or an administrator achieve the business goals that are listed earlier in this solution guide.</para>
      <para>Consider the following features and technologies when you are planning for this solution. We have included design recommendations for you for each feature or technology.</para>
    </content>
  </section>
  <section>
    <title>Why are we recommending this design?</title>
    <content>
      <para>This section explains the details of the design considerations and the decisions that were made that led to the final solution design. This section also provides the recommended configuration or usage of each feature that is used in this solution.</para>
    </content>
    <sections>
      <section>
        <title>Windows Server Essentials Dashboard</title>
        <content>
          <para>The Windows Server Essentials Dashboard in <token>wseblue_2</token> and <token>wseblue_experience</token> helps you quickly access key information and the management features on your server. By using the Dashboard, you can create and manage user accounts, manage devices and backups, manage access and settings for server folders and hard drives, view server alerts and take action on them, integrate with Microsoft Online Services, and install non-Microsoft add-ins that integrate with online services.</para>
          <para>
            <embeddedLabel>Recommendation:</embeddedLabel> Use the Windows Server Essentials Dashboard to perform a majority of administrative tasks for your network. You can run tasks and wizards from the Dashboard to optimally configure the features that are included in your server. By using the Dashboard, you can also configure remote access permissions to network resources, such as shared folders, client computers, or a virtual private network (VPN), on a per-user basis.</para>
        </content>
      </section>
      <section>
        <title>Storage Spaces</title>
        <content>
          <para>You can use the Storage Spaces feature to create flexible, low-cost, resilient, and dynamically expandable data volumes. With Storage Spaces, you can virtualize your server’s storage by grouping industry standard hard disks into storage pools, and then create virtual disks (called storage spaces) from the available capacity in the storage pools. You can use these storage spaces to store your company data in one central location. </para>
          <para>
            <embeddedLabel>Recommendation:</embeddedLabel> For small businesses with fewer than 10 employees, use at least three SAS or SATA hard disks—one hard disk to be used for the operating system, and other two to be used for storage spaces. We recommend that you create a storage space by using at least two hard drives with mirrored resiliency. </para>
          <para>For small businesses with more than 10 employees, or midsize businesses with up to 100 employees, configure at least three SAS hard disks with Storage Spaces—one hard disk to be used for the operating system, and other two to be used for storage spaces. We also recommend providing a server chassis that supports adding more drives for expansion. </para>
        </content>
      </section>
      <section>
        <title>Server Folders</title>
        <content>
          <para>By using the Server Folders feature, you can store files that are located on client computers at a central location. Storing files in server folders ensures that files are always accessible from every client in a secure manner by using authenticated network credentials.</para>
          <para>
            <embeddedLabel>Recommendation:</embeddedLabel> Create server folders on a storage space drive and create separate server folders for departments or projects. For example, if you have an accounting department, you can create a server folder called “Accounting.” Creating the server folder on a storage space disk increases data availability (because of mirroring). </para>
          <para>We also recommend that you set a quota for your server folders so that you are alerted when a server folder is about to reach its capacity. When you are alerted, you can delete files in the server folder to increase available space for storage, or you can add more space to the server folder and adjust its quota settings. You can also configure which server folders are available remotely, and you can assign remote access permissions to user accounts that can access server folders from off-premises.</para>
        </content>
      </section>
      <section>
        <title>User and group management</title>
        <content>
          <para>You can easily manage access to your network resources by creating user accounts for all your employees from the <ui>Users</ui> tab of the Windows Server Essentials Dashboard. In addition, you can create user group accounts, and then add the user accounts as members. All members of a user group account share the same security access level to server resources.</para>
          <para>
            <embeddedLabel>Recommendation:</embeddedLabel> Create user accounts for all the employees in the network, and for all the vendors and partners who you want to collaborate with by using Office 365. Next, create user groups based on the projects that require collaboration or need access to Server Folders. For example, for all employees working in the Accounting department, you can create a user group named “Accounting,” and then add all relevant user accounts to the user group. For a collaboration project that requires vendors and employees to work together, create a user group named “Vendor A.” Next, add the user accounts of the employees and vendors who will be collaborating on this project to the user group called “Project A.” You can later assign access permissions to the Vendor A group for SharePoint libraries.</para>
        </content>
      </section>
      <section>
        <title>Device management</title>
        <content>
          <para>You can manage all the devices in your network from the <ui>Devices</ui> tab of the Windows Server Essentials Dashboard after you connect all the computers in your network to a server running <token>wseblue_2</token> or <token>wseblue_experience</token>. To enable employees to access server folders from computers in the network, you must connect the employees’ computers to the server. </para>
          <para>To do so, run the Connect Computer to the Server Wizard on all the computers that need to access files and folders that are located on the server running <token>wseblue_2</token> or <token>wseblue_experience</token>. When you run the wizard on a computer, it installs the Connector software and joins the computer to the server. This provides the following advantages:</para>
          <list class="bullet">
            <listItem>
              <para>Enables employees to securely access data that is stored on the server by using their user accounts.</para>
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
            <embeddedLabel>Recommendation:</embeddedLabel> Run the Connect Computer to the Server Wizard on all client computers in the network, whether a computer is used remotely or locally.</para>
        </content>
      </section>
      <section>
        <title>Group Policy settings in Windows Server Essentials</title>
        <content>
          <para>When implemented, Windows Server Essentials Group Policy in <token>wseblue_2</token> and <token>wseblue_experience</token> helps keep your network secure by enforcing that Windows Update, Windows Defender, and the network firewall remain turned on for all client computers in the network. </para>
          <para>
            <embeddedLabel>Recommendation:</embeddedLabel> Turn on Windows Update, Windows Defender, and Windows Firewall settings in Windows Server Essentials Group Policy.</para>
        </content>
      </section>
      <section>
        <title>Office 365</title>
        <content>
          <alert class="important">
            <para>Office 365 integration is only supported in a single domain controller environment. In addition, the Integrate with Microsoft Office 365 Wizard must run on a domain controller.</para>
          </alert>
          <para>After you run the Integrate with Microsoft Office 365 Wizard, you can accomplish the following tasks from the Dashboard:</para>
          <list class="bullet">
            <listItem>
              <para>Manage your Office 365 services and resources.</para>
            </listItem>
            <listItem>
              <para>Manage the online accounts that give your employees access to Office 365 and your user accounts.</para>
            </listItem>
            <listItem>
              <para>Manage your subscription and Office 365 integration from the Dashboard.</para>
            </listItem>
            <listItem>
              <para>Create and manage your SharePoint Online libraries.</para>
            </listItem>
            <listItem>
              <para>Change permissions for a SharePoint Online team site.</para>
            </listItem>
            <listItem>
              <para>If you subscribe to Exchange Online, you can manage the mobile devices that your employees use to connect to your company email server.</para>
            </listItem>
          </list>
          <para>For more information about Office 365 integration, see <legacyLink xlink:href="3f8485e4-e10f-4f38-8a5e-d5227abd0d84">Manage Office 365 in Windows Server Essentials [WSE_O365_Integrate]</legacyLink>.</para>
        </content>
      </section>
      <section>
        <title>SharePoint Online</title>
        <content>
          <para>With any Office 365 business plan, you can create team sites and libraries in SharePoint Online. Office 365 integration adds a <ui>SharePoint Libraries</ui> tab for managing your SharePoint Online resources to the <ui>Storage</ui> tab on the Dashboard. Run the Integrate with Microsoft Office 365 Wizard to manage your SharePoint Online libraries and team site permissions from the Dashboard. For more information, see <legacyLink xlink:href="282f3634-6de6-4691-803c-df6c3c16660d">Manage SharePoint Online in Windows Server Essentials [WSE_O365_Integrate]</legacyLink>.</para>
          <para>After Office 365 is integrated with a server running <token>wseblue_2</token> or <token>wseblue_experience</token>, employees and vendors can also access the team’s SharePoint Online libraries from their mobile devices or Windows phones by using the My Server 2012 R2 app. For more information, see <legacyLink xlink:href="4e40b57f-6917-43ef-92e0-030baa9d2b99">Use the My Server App to Connect to Windows Server Essentials  [SBS8]</legacyLink>.</para>
        </content>
      </section>
      <section>
        <title>Microsoft online accounts</title>
        <content>
          <para>After you complete the Office 365 integration, you can create Microsoft online accounts for any of your employees by using the Dashboard. When you use the Dashboard to assign a Microsoft online account to a user account, the user account password is automatically synchronized with the employees’ online account. This means that a user only needs a single password to access resources on the server and resources in Office 365. </para>
          <para>Furthermore, you can use the same name for the user account and the user’s online ID. Password synchronization occurs immediately and automatically when a user changes the password for their user account from a domain-joined computer or by using Remote Web Access.</para>
          <para>
            <embeddedLabel>Recommendation</embeddedLabel> Create Microsoft online accounts for all the employees who need to work on collaboration projects with the partners and vendors.</para>
        </content>
      </section>
    </sections>
  </section>
  <section address="BKMK_Solution">
    <title>What are the high-level steps to implement this solution?</title>
    <content>
      <para>You can use the steps in this section to implement the solutions. Make sure to verify the correct deployment of each step before proceeding to the next step.</para>
      <alert class="note">
        <para>To follow these steps, it is assumed that there is already a server in the network that is running <token>wseblue_2</token> or <token>wseblue_experience</token>. For information about installing <token>wseblue_2</token> or the <token>wseblue_experience</token> role, see <legacyLink xlink:href="48ea6cd4-3955-4aaf-9236-2515a6c3e730">Install and Configure Windows Server 2012 R2 Essentials or Windows Server Essentials Experience [WSE_Blue]</legacyLink>.</para>
      </alert>
      <list class="ordered">
        <listItem>
          <para>
            <embeddedLabel>Set up a domain name from Anywhere Access.</embeddedLabel>
          </para>
          <para>To set up a domain name, follow instructions in <legacyLink xlink:href="f3ea40fa-b6ba-4d66-b754-221ca6271387#BKMK_SetUpName">Manage Remote Web Access</legacyLink>. If you do not have an existing domain name, get a professional domain name (for example, contoso.com) by using the Set Up Your Domain Name Wizard.</para>
        </listItem>
        <listItem>
          <para>
            <embeddedLabel>Turn on Anywhere Access.</embeddedLabel>
          </para>
          <para>To turn on Remote Web Access and a VPN, run the Set Up Anywhere Access Wizard from the <ui>Anywhere Access</ui> tab on the <ui>Settings</ui> page of the Dashboard. To turn on Remote Web Access, follow instructions in <legacyLink xlink:href="f3ea40fa-b6ba-4d66-b754-221ca6271387#BKMK_TurnOnRWA">Manage Remote Web Access</legacyLink>. To turn on a VPN, follow instructions in <legacyLink xlink:href="cc2b264a-b9a8-4114-9f7b-8604f77096e5">Manage VPN in Windows Server Essentials [blue]</legacyLink>.</para>
        </listItem>
        <listItem>
          <para>
            <embeddedLabel>Create a storage space on the server.</embeddedLabel> </para>
          <para>To create a storage space, follow the instructions in <legacyLink xlink:href="1836682e-c7bb-4dd5-a2b5-6ff032693574#BKMK_6">Create a storage space</legacyLink>.</para>
          <para>After you create the storage space, verify that it is listed on the <ui>Hard Drives</ui> tab of the Dashboard. </para>
        </listItem>
        <listItem>
          <para>
            <embeddedLabel>Create server folders for documents that are sensitive and need to be stored on-premises.</embeddedLabel>
          </para>
          <para>To create server folders, follow the instructions in <legacyLink xlink:href="090cf1b8-7b9b-48b9-ae85-b98477b8d7cc#BKMK_5">Add or move a server folder</legacyLink>. For example, to store your company’s accounting files, you can create a server folder named “Accounting.”</para>
          <alert class="note">
            <para>If your organization has shared folders that are already being used, also move the data that is stored on various devices to the server folders that you create in this step.</para>
          </alert>
          <para>After you create Storage Spaces, the default location of the server folder is on a hard drive. Verify that all the server folders that you have created are listed on the <ui>Server Folders</ui> tab of the Dashboard. We recommend that you always add server folders to a Storage Spaces hard drive. </para>
        </listItem>
        <listItem>
          <para>
            <embeddedLabel>Create user accounts and user groups, and assign access permissions to network resources.</embeddedLabel>
          </para>
          <para>For step-by-step instructions to create user accounts, see <legacyLink xlink:href="0d115697-532b-48c2-a659-9f889e235326#BKMK_Manage1">Add a user account</legacyLink>. For more information about user groups, see <legacyLink xlink:href="0d115697-532b-48c2-a659-9f889e235326">Manage User Accounts in Windows Server Essentials [H2]</legacyLink>.</para>
          <para>Verify that all the user accounts and user groups that you have created are listed on the <ui>Users</ui> and the <ui>User Groups</ui> tab respectively on the Dashboard. </para>
        </listItem>
        <listItem>
          <para>
            <embeddedLabel>Assign user access permissions to server folders.</embeddedLabel>
          </para>
          <para>To assign permissions to user accounts so that employees can access the server folders, follow the instructions in <legacyLink xlink:href="090cf1b8-7b9b-48b9-ae85-b98477b8d7cc#BKMK_1">Manage access to server folders</legacyLink>.</para>
          <para>After you have granted user access permissions, you can view or modify permissions to network resources for any user account by viewing the user account properties from the Dashboard. For more information, see <legacyLink xlink:href="0d115697-532b-48c2-a659-9f889e235326">Manage User Accounts in Windows Server Essentials [H2]</legacyLink>.</para>
        </listItem>
        <listItem>
          <para>
            <embeddedLabel>Connect all client computers in the network to the server that is running Windows Server 2012 R2 Essentials or Windows Server 2012 R2 with the Windows Server Essentials Experience role installed.</embeddedLabel>
          </para>
          <para>Before you connect a client computer to the server that is running Windows Server Essentials, review the following topics:</para>
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
          <para>Next, run the Connect Computer to the Server Wizard on all the computers in your network, whether they are local or remote. For step-by-step instructions to connect client computers to a server running <token>wseblue_experience</token>, see <legacyLink xlink:href="149a5d34-43b7-4b9e-99e7-9f2294ab9ddb#BKMK_9">Connect computers to the server</legacyLink>.</para>
          <para>After you have connected a client computer to the server, verify that the computer’s name is listed on the <ui>Devices</ui> tab of the Dashboard. You can manage all computers that are connected to the server through the administrative tasks that are listed in the task pane of the Dashboard. For more information about using the Dashboard to manage computers, see <legacyLink xlink:href="f5fe1088-ebe7-4799-a47d-075b0048dea1#BKMK_1">Manage devices by using the Dashboard</legacyLink>.</para>
        </listItem>
        <listItem>
          <para>
            <embeddedLabel>Implement Windows Server Essentials Group Policy.</embeddedLabel>
          </para>
          <para>To implement Windows Server Essentials Group Policy, turn on Group Policy settings for Folder Redirection, Windows Defender, Windows Firewall, and Windows Update as discussed in <legacyLink xlink:href="f5fe1088-ebe7-4799-a47d-075b0048dea1#BKMK_5">Configure Group Policy settings for folder redirection and security</legacyLink>.</para>
        </listItem>
        <listItem>
          <para>
            <embeddedLabel>Integrate Windows Server Essentials with Office 365.</embeddedLabel>
          </para>
          <para>To integrate Windows Server Essentials with Office 365, see the “Set up Office 365 integration” section in <legacyLink xlink:href="3f8485e4-e10f-4f38-8a5e-d5227abd0d84">Manage Office 365 in Windows Server Essentials [WSE_O365_Integrate]</legacyLink>. </para>
          <alert class="note">
            <para>During the Integrate with Microsoft Office 365 Wizard, you are given the option to create a new Microsoft online account (if you do not have one) or use an existing online account. In addition, if you don’t have a subscription to Office 365, the wizard allows you to subscribe to Office 365 or sign up for a trial subscription.</para>
          </alert>
        </listItem>
        <listItem>
          <para>
            <embeddedLabel>Link your organization’s Internet domain name to Office 365.</embeddedLabel>
          </para>
          <para>To use your own Internet domain in email addressed to your organization and the URLs for your SharePoint Online resources, follow the steps in the “Link your organization’s Internet domain name to Office 365” section of <legacyLink xlink:href="3f8485e4-e10f-4f38-8a5e-d5227abd0d84">Manage Office 365 in Windows Server Essentials [WSE_O365_Integrate]</legacyLink>.</para>
        </listItem>
        <listItem>
          <para>
            <embeddedLabel>Create Microsoft online accounts for your employees.</embeddedLabel>
          </para>
          <para>To create Microsoft online accounts, see the “Create online accounts” section in <legacyLink xlink:href="c09f4cf6-4d12-49fe-9ae4-e6cb14027b9d">Manage Online Accounts for Windows Server Essentials Users [WSE_O365_Integrate]</legacyLink>.</para>
        </listItem>
        <listItem>
          <para>
            <embeddedLabel>Notify employees that they need to sign in to the server and change their password.</embeddedLabel>
          </para>
          <para>For the Office 365 user account passwords and the network user passwords to be synchronized, you must notify your employees to change their passwords when they log on to their network computer. After the password is changed, employees can use the same credentials to sign in to the Windows Server Essentials network or the Office 365 portal.</para>
        </listItem>
        <listItem>
          <para>
            <embeddedLabel>Create SharePoint Online libraries and set access permissions from dashboard.</embeddedLabel>
          </para>
          <para>To create SharePoint Online libraries and set their access permissions using the Windows Server Essentials dashboard, see <legacyLink xlink:href="282f3634-6de6-4691-803c-df6c3c16660d#BKMK_AddSharePointLibrary">Manage SharePoint Online</legacyLink>.</para>
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
              <para>
                <externalLink>
                  <linkText>Windows Server 2012 Essentials: Router Setup</linkText>
                  <linkUri>http://social.technet.microsoft.com/wiki/contents/articles/14153.windows-server-2012-essentials-router-setup.aspx</linkUri>
                </externalLink>
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
                <link xlink:href="416847db-659f-495e-9893-0855378ab4f2">Provide data protection in small and midsize businesses</link>
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
                  <linkText>Windows Server Essentials Library</linkText>
                  <linkUri>http://technet.microsoft.com/sbs/jj159331</linkUri>
                </externalLink>
              </para>
              <para>
                <externalLink>
                  <linkText>Office 365 for business</linkText>
                  <linkUri>http://office.microsoft.com/business/?WT%2Eintid1=ODC%5FENUS%5FFX101785584%5FXT104029222</linkUri>
                </externalLink>
              </para>
              <para>
                <externalLink>
                  <linkText>SharePoint Online Planning Guide for Office 365 Small Business</linkText>
                  <linkUri>http://office.microsoft.com/office365-sharepoint-online-small-business-help/sharepoint-online-planning-guide-for-office-365-small-business-HA101988914.aspx</linkUri>
                </externalLink>
              </para>
              <para>
                <externalLink>
                  <linkText>SharePoint Online Planning Guide for Office 365 Enterprise and Midsize</linkText>
                  <linkUri>http://office.microsoft.com/office365-sharepoint-online-enterprise-help/sharepoint-online-planning-guide-for-office-365-enterprise-and-midsize-HA101988931.aspx</linkUri>
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