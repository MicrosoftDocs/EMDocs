---
title: Mobile device management for Configuration Manager 2007 customers planning to migrate to System Center 2012 R2 Configuration Manager
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b4b50cd8-591c-47c1-81ff-3e8ae61595f5
author: Jeffgilb
---
# Mobile device management for Configuration Manager 2007 customers planning to migrate to System Center 2012 R2 Configuration Manager
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>
      <legacyBold>How can this guide help you?</legacyBold> This guide provides a prescriptive, tested design that you can use to understand the design and implementation steps that we recommend to enable mobile device management for iOS, Android, <token>winphone8_client_1</token>, <token>win8RT_client_1</token>, and <token>winblue_client_2</token> devices when you have an existing <token>sccmshortname</token> hierarchy and plan to migrate to <token>sccm2012r2_1</token>. </para>
    <para>While you plan to migrate to <token>sccm2012r2_1</token>, you need a solution that allows you to manage the devices in your organization. This solution guide describes how you can run a <token>sccm2012r2_1</token> stand-alone primary site server alongside your <token>sccmshortname</token> environment to enable mobile device management.</para>
    <para>The following diagram illustrates the problem and scenario that this solution guide is addressing.</para>
    <para>
      <legacyBold>
        <legacyItalic>Configuration Manager and mobile device management</legacyItalic>
      </legacyBold>
    </para>
    <mediaLink>
      <image xlink:href="7440bcb4-bfd8-400c-aacc-2d880b418f30" />
    </mediaLink>
    <para />
    <para>
      <legacyBold>In this solution guide:</legacyBold>
    </para>
    <list class="bullet">
      <listItem>
        <para>
          <link xlink:href="b4b50cd8-591c-47c1-81ff-3e8ae61595f5#BKMKScenario">Scenario, problem statement, and goals</link>
        </para>
      </listItem>
      <listItem>
        <para>
          <link xlink:href="b4b50cd8-591c-47c1-81ff-3e8ae61595f5#BKMKStrategy">Recommended planning and design approach for this solution</link>
        </para>
      </listItem>
      <listItem>
        <para>
          <link xlink:href="b4b50cd8-591c-47c1-81ff-3e8ae61595f5#BKMKImplentationSteps">High-level steps to implement this solution</link>
        </para>
      </listItem>
    </list>
  </introduction>
  <section address="BKMKScenario">
    <title>Scenario, problem statement, and goals</title>
    <content>
      <para>This section describes the scenario, current problem, and goals that you might have.</para>
      <para>
        <legacyBold>Scenario</legacyBold>
      </para>
      <para>There’s a growing demand from your company’s employees for the ability to access company data from their personal devices. You want to meet this demand by providing the employees with the flexibility to use their own devices over the internet from any location to accomplish work related tasks.</para>
      <para>Your organization is a large enterprise consisting of more than 5,000 users who bring their personal devices to the workplace. Your infrastructure supports the management of computers for users that are on premises and who remotely connect to the corporate network by using VPN. Currently, you manage these computers using <token>sccmshortname</token> and are not ready to do a full deployment of <token>sccm2012r2_1</token>.</para>
      <para>In summary, the current technologies used by your organization:</para>
      <list class="bullet">
        <listItem>
          <para>A domain and directory service, specifically, Active Directory. </para>
        </listItem>
        <listItem>
          <para>PC management software, specifically, System Center <token>sccmshortname</token>. </para>
        </listItem>
        <listItem>
          <para>PCs that are joined to the domain and managed by <token>sccmshortname</token>.</para>
        </listItem>
        <listItem>
          <para>Personal mobile devices owned by employees, as well as personal PCs not joined to the domain.</para>
        </listItem>
      </list>
      <para>
        <legacyBold>Problem statement</legacyBold>
      </para>
      <para>Today you use <token>sccmshortname</token> to manage devices in your organization but this solution does not manage iOS, Android, <token>winphone8_client_1</token>, <token>win8RT_client_1</token>, and personally-owned <token>winblue_client_2</token> devices. However, the latest version of Configuration Manager and Windows Intune does provide support for these devices. Because you are planning to migrate to System Center 2012 R2 Configuration Manager, you want to use it as your mobile device management solution to avoid the cost and effort of integrating a third-party solution. You would like to implement <token>sccm2012r2_1</token> as a management solution even though you are neither ready to fully deploy this version nor migrate your full infrastructure from <token>sccmshortname</token>.</para>
      <para>
        <legacyBold>Organization goals</legacyBold>
      </para>
      <list class="bullet">
        <listItem>
          <para>You can manage today’s mobile devices, specifically, Windows Phone 8, Windows RT, iOS, Android, and personally-owned Windows 8.1 devices. Managing devices can mean security and compliance settings, gathering software and hardware inventory, or deploying mobile apps.</para>
        </listItem>
        <listItem>
          <para>You can protect company data with the ability to wipe company data from mobile devices over the internet. </para>
        </listItem>
        <listItem>
          <para>You can scale up to managing 100,000 mobile devices.</para>
        </listItem>
        <listItem>
          <para>You want a solution that you are familiar with and with minimal learning curve.</para>
        </listItem>
        <listItem>
          <para>You can implement a solution that is compatible with your current environment and can be leveraged for future use.</para>
        </listItem>
      </list>
    </content>
  </section>
  <section address="BKMKStrategy">
    <title>What is the recommended design for this solution?</title>
    <content>
      <para>In an environment where you are managing on-premises devices using <token>sccmshortname</token>, you want to be able to manage mobile devices as well. Your main constraint is that you are not ready to migrate to the latest version of <token>cmshort</token> but you want to use its mobile device management capabilities. Since you are planning to migrate to the latest version of <token>cmshort</token>, you would like the interim solution for mobile device management to be relevant after migration.</para>
      <para>
        <token>sccm2012r2_1</token> works with Windows Intune to manage mobile devices. Through the <token>cmshort</token> console, you can manage mobile devices much like you would manage other devices. The main difference with the mobile devices as compared to computers in your domain is that they are managed over the internet. The <token>cmshort</token> console interfaces with the Windows Intune service which does the actual management of the mobile devices over the internet. When you use <token>sccm2012r2_1</token> with Windows Intune for mobile device management, you can:</para>
      <list class="bullet">
        <listItem>
          <para>Protect your company data with security settings and the ability to wipe company data from retired devices. You can use compliance settings to enforce security policy on mobile device users. These settings can include attributes such as password, camera, system, and security settings. You can also run reports to identify rooted Android devices and modified iOS devices.</para>
        </listItem>
        <listItem>
          <para>Manage devices through compliance settings. Compliance settings can include anything from roaming, store, or device settings. For a full list of settings, see <externalLink><linkText>Compliance Settings for Mobile Devices in Configuration Manager</linkText><linkUri>http://technet.microsoft.com/library/dn376523.aspx</linkUri></externalLink>. </para>
        </listItem>
        <listItem>
          <para>Collect hardware and software inventory. You can run reports to view hardware inventory that describes the types of devices that are enrolled and software inventory can report on what apps are installed on the devices.</para>
        </listItem>
        <listItem>
          <para>Manage apps either by sideloading apps to mobile devices or by deploying links to apps available in device stores such as Windows Store, Windows Phone store, App Store and Google Play.</para>
        </listItem>
        <listItem>
          <para>Create a consistent experience for accessing company data using the company portal. The company portal is an interface where users can view company data and install apps.</para>
        </listItem>
      </list>
      <para>In this solution, mobile device management will be enabled by a <token>sccm2012r2_1</token> stand-alone primary site and a Windows Intune connector. Windows Intune is a cloud service so, to let users enroll their devices, you need to synchronize your domain user accounts to Windows Azure. This will allow you to manage which users can access company resources with their mobile devices. Once users can access company resources over the internet with their mobile devices, you can use Active Directory Federation Service (AD FS) to enable a single sign-on experience.</para>
      <para address="BKMK_PSstep2">The following diagram shows how the components of a <token>sccm2012r2_1</token> stand-alone primary site server communicate side-by-side with a <token>sccmshortname</token> environment. The AD FS portion of the diagram is optional.</para>
      <para>
        <legacyBold>
          <legacyItalic>
            <token>sccm2012r2_1</token> stand-alone primary server runs side-by-side with a <token>sccmshortname</token> environment.</legacyItalic>
        </legacyBold>
      </para>
      <mediaLink>
        <image xlink:href="72e7ef4b-2b01-4bc2-b53d-23089c6cdb26" />
      </mediaLink>
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
                <token>sccm2012r2_1</token>
              </para>
            </TD>
            <TD>
              <para>Manages mobile devices by using the Windows Intune service.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Windows Intune </para>
            </TD>
            <TD>
              <para>Manages mobile devices over the internet.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Windows Azure Active Directory</para>
            </TD>
            <TD>
              <para>Provisions users in the cloud.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Directory synchronization</para>
            </TD>
            <TD>
              <para>Synchronizes on-premises Active Directory users with Windows Azure Active Directory.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Active Directory Federation Services (AD FS) </para>
            </TD>
            <TD>
              <para>Enables a single sign-on experience.</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>
        <legacyBold>
          <token>sccm2012r2_1</token> and the Windows Intune Connector</legacyBold>
      </para>
      <para>You will be running <token>sccm2012r2_1</token> side-by-side with <token>sccmshortname</token>. The <token>sccm2012r2_1</token> site will only be used for mobile device management until you migrate your entire Configuration Manager environment to System Center 2012. Because you can install the <token>sccm2012r2_1</token> console on the same computer where you install a <token>sccmshortname</token> console, you can manage devices from a single computer.</para>
      <para>When you run both products side-by-side, you must take some precautions to prevent devices that should be managed by <token>sccmshortname</token> from discovering your <token>sccm2012r2_1</token> deployment. For example, you should make sure that the two products do not configure boundaries for site assignment where those boundaries include the same network locations. This is referred to as overlapping boundaries. Fortunately, overlapping boundaries are easy to avoid because they are not configured by default and you do not need to configure any boundaries for <token>sccm2012r2_1</token> to enable management of mobile devices when you use Windows Intune.</para>
      <para>You will install a Windows Intune Connector site system role to the <token>sccm2012r2_1</token> site, which connects you to the Windows Intune service.</para>
      <para>
        <legacyBold>Windows Azure Active Directory and directory synchronization (DirSync)</legacyBold>
      </para>
      <para>Windows Intune uses Windows Azure Active Directory to store user accounts. You will need to sync your Active Directory users to the Windows Azure Active Directory. Directory synchronization is intended as an ongoing relationship between your on-premises environment and cloud. After you have activated directory synchronization, you can edit synchronized objects in your on-premises environment and these edits will synchronize with your Windows Intune subscription. </para>
      <para>
        <legacyBold>Options for user authentication</legacyBold>
      </para>
      <para>Once you’ve populated Windows Azure AD with your user accounts, you have a few options as to how to authenticate users. Your options are AD FS, Password Synchronization, or neither.</para>
      <para>AD FS provides a true single sign-on experience working together with Active Directory authentication protocols. AD FS is the more secure solution because it never shares password information with the cloud service, Windows Azure AD. Your on-premises Active Directory and AD FS interact with the Windows Azure AD identity platform to provide access to one or more Microsoft cloud services. When you set up single sign-on, you establish a federated trust between your domain and the Windows Azure AD authentication system. This allows your users to seamlessly access the Microsoft cloud services without needing to sign in with different credentials.</para>
      <para>With AD FS you will need at least one federation server or server farm and a federation proxy server. The federation server authenticates clients, while the federation server proxy provides a layer of security and redirects client authentication requests coming from outside your corporate network to your federation servers. As a Windows Intune customer, deploying a federation server proxy to your existing AD FS infrastructure is necessary to enable mobile device users to authenticate from the internet. </para>
      <para>Password Sync is a lightweight option that provides users with an experience that is similar to single sign-on and very easy to deploy. While not a true single sign-on capability, Password Sync is a selectable option within DirSync that allows DirSync to store a hash of the password in Windows Azure AD. Users can authenticate with cloud services and on-premises services by using the same user name and password for both. </para>
      <para>If you choose not to implement AD FS or Password Sync, users will have to manually update the passwords to keep them in sync or simply remember more than one password, depending on whether they are accessing cloud or on-premises services. This approach is not recommended, as it requires additional administrative overhead to manage initial and ongoing password changes, and results in a less friendly user experience.</para>
      <para>
        <legacyBold>Company Portal</legacyBold>
      </para>
      <para>The company portal is an easy way for users to access all their corporate apps from one place. You can populate the company portal with internal line-of-business applications, as well as with links to apps available in the public application stores (Microsoft Windows Store, Windows Phone Store, Apple App Store, and Google Play). From within the company portal, users can manage their devices and perform various actions, such as wiping a lost or replaced device.</para>
      <para>Users enroll through the company portal on their mobile device. During enrollment the mobile device communicates with the federation proxy which authenticates the user for enrollment.</para>
      <para>
        <legacyBold>Migration</legacyBold>
      </para>
      <para>When you are ready to migrate your <token>sccmshortname</token> infrastructure to <token>sccm2012r2_1</token>, you can use your existing stand-alone primary site as the starting point. <token>sccm2012r2_1</token> supports migrating data and clients from your <token>sccmshortname</token> infrastructure to <token>sccm2012r2_1</token>. Then, after your data and clients have migrated, you can decommission your <token>sccmshortname</token> sites and infrastructure. </para>
      <para>When your <token>sccmshortname</token> infrastructure includes more devices than you can manage with a single <token>sccm2012r2_1</token> stand-alone primary site, you can use the option to expand that stand-alone primary site into a larger hierarchy that includes a central administration site and additional primary sites. This option enables you to maintain your current primary site to manage your mobile devices, while adding more primary sites to your hierarchy, which increases the total capacity of devices the hierarchy can support.</para>
    </content>
  </section>
  <section address="BKMKImplentationSteps">
    <title>What are the high-level steps to implement this solution?</title>
    <content>
      <para>You can use the steps in this section to implement the solution. Make sure to verify the correct deployment of each step before proceeding to the next step.</para>
      <list class="ordered">
        <listItem>
          <para>
            <legacyBold>Get a Windows Intune subscription.</legacyBold> </para>
          <para>Before you can install the Windows Intune connector, you need to create a Windows Intune subscription. You can sign up for an account at <externalLink><linkText>Windows Intune</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkID=271123</linkUri></externalLink>.</para>
        </listItem>
        <listItem>
          <para>
            <legacyBold>Configure your public domain.</legacyBold>
          </para>
          <list class="ordered">
            <listItem>
              <para>To use the Windows Intune service you also need a public organization domain name that is verifiable through services like GoDaddy. Add and verify your public domain in the Windows Intune account portal at <externalLink><linkText>https://account.manage.microsoft.com</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkID=329938</linkUri></externalLink> under the <ui>Domains</ui> node.  </para>
            </listItem>
            <listItem>
              <para>Ensure the public domain has been added as an alternate UPN suffix in on-premises Active Directory. Users must have the same public domain User Principal Name (UPN) in the cloud and the on-premises Active Directory to enroll mobile devices. You must verify that your users have a public domain UPN before you configure directory synchronization and AD FS.  If you skip this step, you may end up with users automatically getting “onmicrosoft.com” appended to their cloud UPN which will result in a mismatch with on-premises Active Directory user names. For information on how to change the UPN, see <externalLink><linkText>Add User Principal Name Suffixes</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkID=271122</linkUri></externalLink> in the Active Directory documentation library. </para>
            </listItem>
            <listItem>
              <para>Add a CNAME record in DNS pointing <ui>enterpriseenrollment.&lt;publicdomain&gt;</ui> to <ui>manage.microsoft.com</ui>. The CNAME record is used later as part of the enrollment process. </para>
            </listItem>
          </list>
          <para>
            <legacyBold>Verification steps</legacyBold>: </para>
          <list class="bullet">
            <listItem>
              <para>Check the <ui>Domains</ui> page of the Windows Intune Account Portal to make sure the public domain is listed and verified.</para>
            </listItem>
            <listItem>
              <para>Look at the properties of a user account in on-prem Active Directory to ensure the UPN is listed with the public domain name.</para>
            </listItem>
            <listItem>
              <para>Ping <ui>enterpriseenrollment.&lt;publicdomain&gt;</ui> and ensure it is resolving to the IP address of manage.microsoft.com. The CNAME record is used as part of the enrollment process.</para>
            </listItem>
          </list>
        </listItem>
        <listItem>
          <para>
            <legacyBold>Configure User Authentication.</legacyBold>
          </para>
          <para>You can configure AD FS from your Windows Intune Account portal at <externalLink><linkText>https://account.manage.microsoft.com</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkID=329938</linkUri></externalLink>. In the <ui>User</ui> node of the portal, click <ui>Single sign-on: Set up</ui> and then follow the steps to <ui>Set up and manage single sign-on</ui>. For more information, see <externalLink><linkText>Checklist: Use AD FS to implement and manage single sign-on</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkID=329978</linkUri></externalLink> in the Active Directory documentation library, this article fully details the requirements needed, the planning and deployment process, as well as how to verify that AD FS has been deployed and configured correctly.</para>
          <para>Alternatively, you can consider implementing Password Synchronization depending on your security considerations. Password Synchronization is a feature of the Windows Azure Active Directory Synchronization tool that synchronizes user passwords from your on-premises Active Directory to Windows Azure Active Directory. You can implement Password Sync as part of configuring directory synchronization. To understand the security considerations and whether this is the right decision for your organization, see <externalLink><linkText>Implement Password Synchronization</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkID=330001</linkUri></externalLink>.</para>
        </listItem>
        <listItem>
          <para>
            <legacyBold>Provision users by configuring directory synchronization.</legacyBold>
          </para>
          <para>In the <ui>Users</ui> node of the Windows Intune Account portal at <externalLink><linkText>https://account.manage.microsoft.com</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkID=329938</linkUri></externalLink>, click <ui>Active Directory synchronization: Setup</ui>, and then follow the steps outlined in <ui>Set up and manage Active Directory synchronization</ui>. For more information, see <externalLink><linkText>Configure directory synchronization</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkID=271120</linkUri></externalLink> in the Active Directory documentation library. You can install DirSync on any computer as long as it is not a domain controller.</para>
          <para>
            <legacyBold>Verification steps</legacyBold>: Check in the Windows Intune Account portal at <externalLink><linkText>https://account.manage.microsoft.com</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkID=329938</linkUri></externalLink>to view user <?Comment DS: Note:Besides checking that the User accounts have been populated, you don’t actually use the Windows Intune portal for any management tasks. Management tasks will be performed in the Configuration Manager console. 2013-10-29T11:40:00Z  Id='1?>accounts<?CommentEnd Id='1'
    ?>.  </para>
        </listItem>
        <listItem>
          <para>
            <legacyBold>Plan your stand-alone primary site server.</legacyBold>
          </para>
          <para>Identify a server that meets both the software and hardware prerequisites to host a Configuration Manager primary site. By default, when you install a primary site for Configuration Manager, the management point and distribution point site system roles are also installed. Because you will only manage mobile devices for this scenario, the management point and distribution point are not used. However, their presence does not affect the performance of your site. Therefore, we recommend to leaving these site system roles installed. </para>
          <para>For hardware sizing information for the primary site, see <externalLink><linkText>Planning for Hardware Configurations for Configuration Manager</linkText><linkUri>http://technet.microsoft.com/library/hh846235.aspx</linkUri></externalLink>. The details provided for a stand-alone primary site will give you the basics for running a primary site that can support the Windows Intune connector and up to 100,000 mobile devices.</para>
          <para>For information on required software and supported operating systems for hosting a Configuration Manager site, see <externalLink><linkText>Site System Requirements</linkText><linkUri>http://technet.microsoft.com/library/gg682077.aspx</linkUri></externalLink>. Specifically, review the applicable section for the prerequisites that apply to the operating system you use to host the stand-alone primary site. The site system roles installed by default are the site server, database server, SMS Provider server, management point, and distribution point.</para>
        </listItem>
        <listItem>
          <para>
            <legacyBold>Deploy a stand-alone primary site server.</legacyBold>
          </para>
          <para>Install and configure a <token>sccm2012r2_1</token> stand-alone primary site which will allow you to manage mobile devices. For information, see the <externalLink><linkText>Install a Primary Site Server</linkText><linkUri>http://technet.microsoft.com/library/gg712320.aspx</linkUri></externalLink>.</para>
          <para>After the site installation completes, confirm or set the following common configurations for Configuration Manager primary sites:</para>
          <list class="bullet">
            <listItem>
              <para>Do not configure site boundaries. By default, no site boundaries are created for a new site.  Site boundaries are used by new Configuration Manager clients to identify a site to join, and to locate content that you deploy. For this scenario, neither activity applies.  </para>
            </listItem>
            <listItem>
              <para>Configure and run Active Directory User Discovery on your domain to discover users for future enrollment.</para>
            </listItem>
            <listItem>
              <para>Ensure that Client Push Installation is not enabled. This is only used when you are ready to install the Configuration Manager client on Windows devices, and is not used to manage mobile devices. </para>
            </listItem>
          </list>
        </listItem>
        <listItem>
          <para>
            <legacyBold>Configure the Windows Intune subscription and install the Windows Intune Connector site system role on your stand-alone primary site server.</legacyBold>
          </para>
          <para>Before you can use Configuration Manager to manage mobile devices, you must configure your Windows Intune subscription and install the Windows Intune connector site system role on the stand-alone primary site server. For more information, see <externalLink><linkText>How to Manage Mobile Devices by Using Configuration Manager and Windows Intune</linkText><linkUri>http://technet.microsoft.com/library/jj884158.aspx</linkUri></externalLink>. </para>
          <para>
            <legacyBold>Verification steps</legacyBold>:</para>
          <list class="bullet">
            <listItem>
              <para>On the primary site server computer, review the <ui>Sitecomp.log</ui> to verify that the Windows Intune connector site system role installed successfully.</para>
            </listItem>
            <listItem>
              <para>On the computer where you install the Windows Intune connector, review the <ui>Cloudusersync.log</ui> to verify that users from your domain have successfully synchronized to the Windows Intune. The log file will confirm that the UPN names are consistent between Windows Azure AD and on-premises AD. If any users fail to sync, it’s most likely due to UPN mismatches.</para>
            </listItem>
            <listItem>
              <para>On the primary site server computer, review the <ui>Certmgr.log</ui> to confirm that the computer where you installed the Windows Intune connector shares the connector certificate. The certificate is shared after the installation of the Windows Intune connector site system role is complete. </para>
            </listItem>
            <listItem>
              <para>On the computer where you install the Windows Intune connector, review the <ui>Dmpuploader.log</ui> to verify that the connector site system role can upload policy and configuration changes to the Windows Intune service.</para>
            </listItem>
            <listItem>
              <para>On the computer where you install the Windows Intune connector, review the <legacyBold>Dmpdownloader.log</legacyBold> to verify that the Windows Intune connector is able to download messages from Windows Intune. This log might only show a ping at the beginning of the download process and it might take some time before entries related to downloads are logged.</para>
            </listItem>
          </list>
        </listItem>
        <listItem>
          <para>
            <legacyBold>Install the <token>sccm2012r2_1</token> console.</legacyBold>
          </para>
          <para>By default, when you install a primary site, the Configuration Manager console also installs on the primary site server computer. After the site installs, you can install additional <token>sccm2012r2_1</token> consoles on additional computers to manage the site. Installing a console from both <token>sccmshortname</token>and <token>sccm2012r2_1</token> on the same computer is supported. This side-by-side installation allows you to use a single computer to manage both your existing <token>sccmshortname</token> infrastructure, and the mobile devices you manage using Windows Intune with <token>sccm2012r2_1</token>.  However, you cannot use the management console from <token>sccm2012r2_1</token> to manage your <token>sccmshortname</token> site, and vice versa. For more information, see <externalLink><linkText>Install a Configuration Manager Console</linkText><linkUri>http://technet.microsoft.com/library/gg712320.aspx</linkUri></externalLink>.</para>
        </listItem>
        <listItem>
          <para>
            <legacyBold>Enroll mobile devices.</legacyBold>
          </para>
          <para>For information on how to enroll mobile devices, see <externalLink><linkText>Mobile Device Enrollment</linkText><linkUri>http://technet.microsoft.com/library/jj884158.aspx</linkUri></externalLink>.</para>
        </listItem>
        <listItem>
          <para>
            <legacyBold>Manage mobile devices.</legacyBold>
          </para>
          <para>After you install and make the basic configurations for your stand-alone primary site, you can begin to configure management of mobile devices. The following are typical actions you might configure:</para>
          <list class="bullet">
            <listItem>
              <para>To apply compliance setting to mobile devices, see <externalLink><linkText>Compliance Settings for Mobile Devices in Configuration Manager</linkText><linkUri>http://technet.microsoft.com/library/dn376523.aspx</linkUri></externalLink>.</para>
            </listItem>
            <listItem>
              <para>To create and deploy applications to mobile devices, see <externalLink><linkText>How to Create and Deploy Applications for Mobile Devices in Configuration Manager</linkText><linkUri>http://technet.microsoft.com/library/dn469410.aspx</linkUri></externalLink>.</para>
            </listItem>
            <listItem>
              <para>To configure Hardware Inventory, see <externalLink><linkText>How to Configure Hardware Inventory for Mobile Devices Enrolled by Windows Intune and Configuration Manager</linkText><linkUri>http://technet.microsoft.com/library/dn469411.aspx</linkUri></externalLink>.</para>
            </listItem>
            <listItem>
              <para>To configure Software Inventory, see <externalLink><linkText>Introduction to Software Inventory in Configuration Manager</linkText><linkUri>http://technet.microsoft.com/library/gg682049.aspx</linkUri></externalLink>.</para>
            </listItem>
            <listItem>
              <para>To wipe content from mobile devices, see <externalLink><linkText>Wiping Company Content from Mobile Devices</linkText><linkUri>http://technet.microsoft.com/library/jj884158.aspx</linkUri></externalLink>.</para>
            </listItem>
          </list>
        </listItem>
        <listItem>
          <para>
            <legacyBold>Migrate to <token>sccm2012r2_1</token>.</legacyBold> </para>
          <para>For information on migrating to System Center 2012 R2 Configuration Manager, see <externalLink><linkText>Migrating Hierarchies in System Center 2012 Configuration Manager</linkText><linkUri>http://technet.microsoft.com/library/gg682006.aspx</linkUri></externalLink>.</para>
          <para>If you will be managing more than 100,000 devices, you will need to expand your stand-alone primary site into a hierarchy.  For more information, see <externalLink><linkText>Planning to Expand a Stand-Alone Primary Site</linkText><linkUri>http://technet.microsoft.com/library/gg712681.aspx</linkUri></externalLink>.</para>
        </listItem>
      </list>
    </content>
  </section>
  <relatedTopics />
</developerConceptualDocument>