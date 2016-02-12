---
title: Streamlined management for mobile devices and computers in a hybrid environment
ms.custom: na
ms.prod: system-center-2012-r2
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configuration-manager
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 07cad07f-e499-4b96-9ae0-96aca1373748
author: Jeffgilb
---
# Streamlined management for mobile devices and computers in a hybrid environment
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://clixdevr3.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>
      <embeddedLabel>Who is this guide intended for?</embeddedLabel>: Companies who need to manage mobile devices and PCs that are on-premises and remote by utilizing their existing <token>cmshort</token> infrastructure to support the employee demand to use these devices to access corporate resources.</para>
    <para>
      <embeddedLabel>How can this guide help you?</embeddedLabel> This guide provides a prescriptive, tested design that explains how to:</para>
    <list class="bullet">
      <listItem>
        <para>Upgrade your existing on-premises <token>cmshort</token> infrastructure and extend it to the cloud to let your users work remotely from the device of their choice.</para>
      </listItem>
      <listItem>
        <para>Unify PC and mobile device management into a single infrastructure.</para>
      </listItem>
      <listItem>
        <para>Maintain corporate compliance for all devices.</para>
      </listItem>
      <listItem>
        <para>Protect corporate data.</para>
      </listItem>
    </list>
    <para>In this solution:</para>
    <list class="bullet">
      <listItem>
        <para>
          <link xlink:href="07cad07f-e499-4b96-9ae0-96aca1373748#BKMK_ScenProbGoals">Scenario, Problem Statement, and Goals</link>
        </para>
        <list class="bullet">
          <listItem>
            <para>
              <link xlink:href="07cad07f-e499-4b96-9ae0-96aca1373748#BKMK_Scenario">Scenario</link>
            </para>
          </listItem>
          <listItem>
            <para>
              <link xlink:href="07cad07f-e499-4b96-9ae0-96aca1373748#BKMK_Problem">Problem Statement</link>
            </para>
          </listItem>
          <listItem>
            <para>
              <link xlink:href="07cad07f-e499-4b96-9ae0-96aca1373748#BKMK_Goals">Organizational Goals</link>
            </para>
          </listItem>
        </list>
      </listItem>
      <listItem>
        <para>
          <link xlink:href="07cad07f-e499-4b96-9ae0-96aca1373748#BKMK_Design">What is the Recommended Design for this Solution?</link>
        </para>
        <list class="bullet">
          <listItem>
            <para>
              <link xlink:href="07cad07f-e499-4b96-9ae0-96aca1373748#BKMK_PlanConfigMgr">Install System Center 2012 R2 Configuration Manager and migrate data</link>
            </para>
          </listItem>
          <listItem>
            <para>
              <link xlink:href="07cad07f-e499-4b96-9ae0-96aca1373748#BKMK_PlanSubscribe">Subscribe to Windows Intune</link>
            </para>
          </listItem>
          <listItem>
            <para>
              <link xlink:href="07cad07f-e499-4b96-9ae0-96aca1373748#BKMK_PlanIdentity">Manage identify and access with Windows Azure AD and directory synchronization</link>
            </para>
          </listItem>
          <listItem>
            <para>
              <link xlink:href="07cad07f-e499-4b96-9ae0-96aca1373748#BKMK_PlanPasswordSync">Provide secure easy access for users with Password Sync</link>
            </para>
          </listItem>
          <listItem>
            <para>
              <link xlink:href="07cad07f-e499-4b96-9ae0-96aca1373748#BKMK_PlanPhasedUpgrade">Plan a phased platform upgrade</link>
            </para>
          </listItem>
        </list>
      </listItem>
      <listItem>
        <para>
          <link xlink:href="07cad07f-e499-4b96-9ae0-96aca1373748#BKMK_Implementation">Implementation steps</link>
        </para>
      </listItem>
    </list>
    <para>The following diagram illustrates the problem that this solution guide is addressing.</para>
    <mediaLink>
      <image xlink:href="258989c5-9d58-42d7-97f5-da0b3ec647bc" />
    </mediaLink>
    <para> </para>
    <para>
      <legacyItalic>
        <embeddedLabel>Diagram 1: High-level overview of the problem.</embeddedLabel>
      </legacyItalic>
    </para>
  </introduction>
  <section expanded="true" address="BKMK_ScenProbGoals">
    <title>Scenario, Problem Statement, and Goals</title>
    <content>
      <para>This section describes the scenario, problem, and goals for an example organization.</para>
    </content>
    <sections>
      <section address="BKMK_Scenario">
        <title>Scenario</title>
        <content>
          <para>This solution uses an example company that employs more than 5,000 people who bring their Windows Phone 8, Windows RT, iOS, and Android personal devices to work. Currently, they have no way to access company resources from these devices. </para>
          <para>The company uses <token>sccmlongname</token> SP2 to manage PCs for users who are on-premises and who remotely connect to the corporate network by VPN. The company can’t manage mobile devices.</para>
          <para>The infrastructure of the company’s environment contains:</para>
          <list class="bullet">
            <listItem>
              <para>Windows Server 2008 R2</para>
            </listItem>
            <listItem>
              <para>Windows Server 2008 R2 Active Directory</para>
            </listItem>
            <listItem>
              <para>
                <token>sccmshortname</token> SP2</para>
            </listItem>
            <listItem>
              <para>PCs that are joined to the domain and managed by <token>cmshort</token></para>
            </listItem>
          </list>
          <para>The following diagram illustrates the current environment for the company.</para>
          <mediaLink>
            <image xlink:href="2536f42f-dd53-4f28-859f-b1553037bced" />
          </mediaLink>
          <para />
          <para>
            <embeddedLabel>Diagram 2: High-level overview of the current environment</embeddedLabel>
          </para>
        </content>
      </section>
      <section address="BKMK_Problem">
        <title>Problem Statement</title>
        <content>
          <para>The current device management infrastructure does not support the example company’s growing needs: </para>
          <list class="bullet">
            <listItem>
              <para>They manage PCs in their current environment, but can’t manage mobile devices. </para>
            </listItem>
            <listItem>
              <para>They provide some employees with corporate-owned mobile devices. Other employees want to use their personal devices at work.</para>
            </listItem>
          </list>
          <para>The company is also concerned about the resources required to manage all these devices. It is expensive to support many PCs, devices, and applications, and device management can tie up IT 24/7. </para>
          <para>The company needs to manage risk and make sure all devices, both corporate and personal, comply with security guidelines.</para>
          <list class="bullet">
            <listItem>
              <para>Device management is a security risk to corporate assets and information. As soon as employees work on a device that IT doesn’t manage (or even know about), it becomes very difficult to retain control of sensitive corporate information. </para>
            </listItem>
            <listItem>
              <para>IT can’t do anything if the device is sold, lost, or stolen.</para>
            </listItem>
          </list>
        </content>
      </section>
      <section address="BKMK_Goals">
        <title>Organizational Goals</title>
        <content>
          <para>The example company is looking for a solution that allows them to do the following: </para>
          <list class="bullet">
            <listItem>
              <para>Use their existing <token>cmshort</token> infrastructure. IT has invested a lot of resources into their current infrastructure and doesn’t want to start over.</para>
            </listItem>
            <listItem>
              <para>Let employees use personal devices as well as company devices to access corporate applications and data. These include PCs and mobile devices.</para>
            </listItem>
            <listItem>
              <para>Manage PCs and personal devices from a single administrator console. Managing devices includes setting security and compliance settings, gathering software and hardware inventory, or deploying software.</para>
            </listItem>
            <listItem>
              <para>Deploy applications or web links based on device type, and whether the device is personal or owned by the company. </para>
            </listItem>
            <listItem>
              <para>Protect the company by wiping corporate data stored on the mobile device when it is lost, stolen, or retired from use.</para>
            </listItem>
          </list>
          <para />
        </content>
      </section>
    </sections>
  </section>
  <section expanded="true" address="BKMK_Design">
    <title>What is the Recommended Design for this Solution?</title>
    <content>
      <para>To solve their business problem and meet their organization goals, the company needs to:</para>
      <list class="bullet">
        <listItem>
          <para>Install a new <token>sccm2012r2_1</token> stand-alone primary site at their headquarters and install distribution points at remote locations.</para>
        </listItem>
        <listItem>
          <para>Migrate objects and distribution points from their existing <token>cmshort</token> 2007 SP2 infrastructure to <token>sccm2012r2_1</token>.</para>
        </listItem>
        <listItem>
          <para>Subscribe to Windows Intune and configure the Windows Intune connector in <token>cmshort</token> to integrate with Windows Intune.</para>
        </listItem>
        <listItem>
          <para>Synchronize their domain user accounts to Windows Azure, since Windows Intune is a cloud service. This allows them to manage the users who can access company resources from their mobile devices. </para>
        </listItem>
        <listItem>
          <para>Use Password Sync to allow users to use their on-premises domain user name and password for cloud services. </para>
        </listItem>
      </list>
      <para>The following diagram illustrates how the elements in this solution communicate with each other.</para>
      <mediaLink>
        <image xlink:href="04f7f970-9605-46c2-abc0-7d132c91f21f" />
      </mediaLink>
      <para>
        <legacyItalic>
          <embeddedLabel>Diagram 3: High-level overview of the solution</embeddedLabel>
        </legacyItalic>
      </para>
      <para> </para>
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
              <para>Provides secure and scalable software deployment, compliance settings management, and comprehensive asset management of servers, desktops, laptops, and mobile devices (when Windows Intune is integrated).</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Windows Intune </para>
            </TD>
            <TD>
              <para>Manages mobile devices over the internet. When integrated with <token>sccm2012r2_1</token>, you can manage both PCs and mobile devices from the <token>cmshort</token> console. </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Windows Azure Active Directory (AD)</para>
            </TD>
            <TD>
              <para>A service that provides identity and access capabilities for on-premises and cloud applications.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Windows Azure directory synchronization (DirSync)</para>
            </TD>
            <TD>
              <para>Synchronizes on-premises AD users with Windows Azure AD.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Password Sync</para>
              <para />
            </TD>
            <TD>
              <para>Allows users to use the same user name and password for on-premises and cloud services.</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
    <sections>
      <section address="BKMK_PlanConfigMgr" expanded="true">
        <title>Install System Center 2012 R2 Configuration Manager and migrate objects</title>
        <content>
          <para>
            <token>sccm2012r2_1</token> can extend the company’s ability to manage PCs on-premises to the cloud by integrating Windows Intune. And, by using <token>cmshort</token> with Windows Intune, the company can manage both their on-premises PCs and mobile devices from a single console. They also want to reduce IT overhead. </para>
          <para>So, the company will install a <token>sccm2012r2_1</token> stand-alone primary site located at their headquarters and distribution points at remote locations.</para>
          <para>Then, they will migrate objects from their <token>sccmshortname</token> SP2 environment to <token>sccm2012r2_1</token>.</para>
          <para>The company chose to migrate for the following reasons:</para>
          <list class="bullet">
            <listItem>
              <para>
                <embeddedLabel>Integrated solution</embeddedLabel>: The company wants an integrated solution that lets them manage both PCs and mobile devices from a single console. <token>sccm2012r2_1</token> with Windows Intune provides this integrated solution.</para>
            </listItem>
            <listItem>
              <para>
                <embeddedLabel>Simplified hierarchy</embeddedLabel>: With <token>sccm2012r2_1</token>, they determined that they no longer need a secondary site at each remote location as shown in the following diagrams.</para>
              <para> </para>
              <mediaLink>
                <image xlink:href="07c8f3e8-732e-4528-8d76-e0f3d039d023" />
              </mediaLink>
              <para> </para>
              <para>
                <legacyItalic>
                  <embeddedLabel>Diagram 3: Existing hierarchy, <token>sccmshortname</token></embeddedLabel>
                </legacyItalic>
              </para>
              <para> </para>
              <para> </para>
              <mediaLink>
                <image xlink:href="d7ac1e5d-c3ae-4365-ba75-6e03b6b59bd7" />
              </mediaLink>
              <para> </para>
              <para>
                <legacyItalic>
                  <embeddedLabel>Diagram 4: New hierarchy, <token>sccm2012r2_1</token></embeddedLabel>
                </legacyItalic>
              </para>
              <para> </para>
              <para> </para>
              <para>Key drivers for the simplified hierarchy:</para>
              <list class="bullet">
                <listItem>
                  <para>Role-based administration: In <token>sccm2012r2_1</token>, role-based administration lets the company design and implement administrative security for the <token>sccm2012r2_1</token> hierarchy by using any or all of the following:</para>
                  <list class="bullet">
                    <listItem>
                      <para>Security roles</para>
                    </listItem>
                    <listItem>
                      <para>Collections</para>
                    </listItem>
                    <listItem>
                      <para>Security scopes</para>
                    </listItem>
                  </list>
                  <para>These settings combine to define an administrative scope for an administrative user. The administrative scope controls the objects that an administrative user can view in the <token>cmshort</token> console and the permissions that user has on those objects. See <externalLink><linkText>Planning for Role-Based Administration</linkText><linkUri>http://technet.microsoft.com/en-us/library/gg712284.aspx#BKMK_PlanningForRBA</linkUri></externalLink>.</para>
                </listItem>
                <listItem>
                  <para>Content management: In <token>sccm2012r2_1</token>, the company can configure the network bandwidth used to transfer content to distribution points and prestage content on distribution points at remote locations. See <externalLink><linkText>Network Bandwidth Considerations for Distribution Points</linkText><linkUri>http://technet.microsoft.com/library/gg712321.aspx#BKMK_DistributionPointBandwidth</linkUri></externalLink>.</para>
                </listItem>
              </list>
              <para />
            </listItem>
            <listItem>
              <para>
                <embeddedLabel>Migrated objects</embeddedLabel>: The company can use migration tools to migrate objects from <token>sccmshortname</token> SP2 to the <token>sccm2012r2_1</token> hierarchy. The company’s IT has invested a significant amount of time creating <token>cmshort</token> objects, such as collections, task sequences, configuration items, and so on. By using migration, they will continue to benefit from this investment.</para>
            </listItem>
            <listItem>
              <para>
                <embeddedLabel>Latest features</embeddedLabel>: The company is also interested in new features in <token>sccm2012r2_1</token> that are not directly related to this solution. See <externalLink><linkText>What’s New in System Center 2012 R2 Configuration Manager</linkText><linkUri>http://technet.microsoft.com/library/dn236351.aspx</linkUri></externalLink>.</para>
            </listItem>
          </list>
        </content>
      </section>
      <section address="BKMK_PlanSubscribe" expanded="true">
        <title>Subscribe to Windows Intune</title>
        <content>
          <para>The Windows Intune service provides cloud-based management of mobile devices. The company will subscribe to Windows Intune, and then integrate Windows Intune with <token>sccm2012r2_1</token> to manage both PCs and mobile devices from the <token>cmshort</token> console. </para>
          <para>A subscription to Windows Intune supports the company’s goal for <embeddedLabel>an integrated solution</embeddedLabel> to manage both PCs and mobile devices. </para>
          <para>The company considered third-party mobile device management solutions. None of these solutions provide the integrated experience they want. Nor do they want to switch products and incur training and implementation costs.</para>
          <para>As an additional benefit, the company can use the user account from their Windows Intune subscription when they subscribe to Microsoft Office 365 a few months later. </para>
          <alert class="tip">
            <para>If your company is already using Microsoft Online Services for services such as Microsoft Office 365, use the same user account when you subscribe to Windows Intune. This allows you to use the same group of users across all the services in your organization’s Windows Azure AD <externalLink><linkText>tenant</linkText><linkUri>http://technet.microsoft.com/library/jj573650.aspx</linkUri></externalLink>. If you do not select the option to sign-in using your existing user, a new Windows Azure AD tenant is created for you. You will then need to add users to the new tenant.</para>
          </alert>
        </content>
      </section>
      <section address="BKMK_PlanIdentity" expanded="true">
        <title>Manage identity and access with Windows Azure AD and directory synchronization</title>
        <content>
          <para>Windows Intune uses Windows Azure AD to store user accounts. Microsoft cloud services, such as Windows Intune and Office 365, rely on the identity management capabilities provided by Windows Azure AD. </para>
          <para>The company will use Windows Azure directory synchronization (DirSync) to synchronize on-premises Windows Server AD users with Windows Azure AD. Directory synchronization is intended as an ongoing relationship between on-premises AD and cloud-based Windows Azure AD. The company chose DirSync to:</para>
          <list class="bullet">
            <listItem>
              <para>
                <embeddedLabel>Reduce administration costs</embeddedLabel>: Without DirSync, the company would have had to manually add their user and group accounts to Windows Azure AD. DirSync synchronizes the user accounts from on-premises Windows Server AD to Windows Azure AD. After you activate directory synchronization, you can edit synchronized objects in your on-premises environment and these edits will synchronize with your Windows Intune subscription, which reduces administrative costs. </para>
            </listItem>
            <listItem>
              <para>
                <embeddedLabel>Improve productivity</embeddedLabel>: By automating the process of synchronizing user and group accounts, the company can significantly reduce the amount of time it takes to make cloud-based services accessible for their employees.</para>
            </listItem>
          </list>
        </content>
        <sections>
          <section>
            <title>Planning and design considerations for directory synchronization</title>
            <content>
              <para>When planning for directory synchronization, the company considered hardware requirements, administrator permissions, performance considerations, and so on. These requirements are documented in <externalLink><linkText>Prepare for directory synchronization</linkText><linkUri>http://technet.microsoft.com/library/jj151831.aspx</linkUri></externalLink>. </para>
            </content>
          </section>
        </sections>
      </section>
      <section address="BKMK_PlanPasswordSync" expanded="true">
        <title>Provide secure easy access for users with Password Sync</title>
        <content>
          <para>User authentication must be configured or the company’s employees will have to use a different user name and separate passwords to access cloud and on-premises services. The company decided that they must have user authentication to avoid additional administrative overhead to manage initial and ongoing password changes and to provide a better user experience. The decided to use Password Sync for user authentication.  </para>
          <para>The company considered the following authentication methods for employee access to cloud and on-premises resources with the same credentials:</para>
          <list class="bullet">
            <listItem>
              <para>
                <embeddedLabel>Password Sync</embeddedLabel> is a lightweight option that provides users with an experience that is similar to single sign-on and very easy to deploy. Password Sync is an option that you can select within DirSync that allows DirSync to store a hash of the password in Windows Azure AD. When password sync is enabled on your directory sync computer, your users will be able to sign into Microsoft cloud services, such as Office 365, Dynamics CRM, and Windows Intune, using the same password as they use when logging into your on-premises network. When your users change their passwords in your corporate network, those changes are synchronized to the cloud. </para>
              <para>However, Password Sync does not provide a Single Sign-On (SSO) solution that you get when using AD FS. Users will need to re-enter their credentials each time they access a cloud service. See: </para>
              <list class="bullet">
                <listItem>
                  <para>
                    <externalLink>
                      <linkText>Directory Sync with Password Sync Scenario</linkText>
                      <linkUri>http://technet.microsoft.com/library/dn441214.aspx</linkUri>
                    </externalLink>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <externalLink>
                      <linkText>Implement Password Synchronization</linkText>
                      <linkUri>http://technet.microsoft.com/library/dn246918.aspx</linkUri>
                    </externalLink>
                  </para>
                </listItem>
              </list>
            </listItem>
            <listItem>
              <para>
                <embeddedLabel>Active Directory Federation Services (AD FS)</embeddedLabel> provides a true single sign-on (SSO) experience working together with Active Directory authentication protocols. The on-premises Active Directory and AD FS interact with the Windows Azure AD identity platform to provide access to one or more Microsoft cloud services. When SSO is configured, a federated trust is created between the domain and the Windows Azure AD authentication system. Users can authenticate with cloud services and on-premises services by using the same user name and password for both. After a user is authenticated, they are not prompted again for credentials when they access a cloud service. </para>
            </listItem>
          </list>
          <para>The company decided to use Password Sync for user authentication for a couple of reasons. Password Sync is very easy to configure in DirSync, which they already plan to use to synchronize their on-premises user accounts. They also plan to upgrade their domain controllers to Windows Server 2012 R2 within the next six months. AD FS is a site role in Windows Server 2012 R2 and has a lot of new features. The company plans to implement AD FS when they upgrade their domain controllers. For more information about implementing AD FS in Windows Server 2012 R2, see:</para>
          <list class="bullet">
            <listItem>
              <?Comment DE: Updatefwlinkwhen the URL is live. 2015-03-20T15:37:00Z  Id='1?>
              <para>
                <externalLink>
                  <linkText>Secure access to company resources from any location on any device</linkText>
                  <linkUri>Http://technet.microsoft.com/library/dn550982.aspx</linkUri>
                </externalLink>
                <?CommentEnd Id='1'
    ?>
              </para>
            </listItem>
            <listItem>
              <para>
                <externalLink>
                  <linkText>Active Directory Federation Services Overview</linkText>
                  <linkUri>http://technet.microsoft.com/library/hh831502.aspx</linkUri>
                </externalLink>
              </para>
            </listItem>
          </list>
          <para>The company decided to use Password Sync for user authentication. However, you might decide to implement AD FS for SSO in your environment. See:</para>
          <list class="bullet">
            <listItem>
              <para>AD FS design considerations: <externalLink><linkText>AD FS 2.0 Design Guide</linkText><linkUri>http://technet.microsoft.com/library/dd807036(v=ws.10).aspx</linkUri></externalLink></para>
            </listItem>
            <listItem>
              <para>Using AD FS for SSO: <externalLink><linkText>Checklist: Use AD FS to implement and manage single sign-on</linkText><linkUri>http://technet.microsoft.com/library/jj205462.aspx</linkUri></externalLink></para>
            </listItem>
          </list>
        </content>
      </section>
      <section address="BKMK_PlanPhasedUpgrade" expanded="true">
        <title>Plan a phased platform upgrade</title>
        <content>
          <para>The company decided not to upgrade their on-premises AD as part of this solution, but plans to upgrade in the next 6 months. </para>
          <para>The company’s IT proposed that their on-premises AD be upgraded as part of the solution. In Windows Server 2012 R2, AD has been enhanced with the following functionality:</para>
          <list class="bullet">
            <listItem>
              <para>
                <embeddedLabel>Device registration</embeddedLabel>. IT administrators can allow a device to be registered, which associates the device with the company’s Active Directory. This association can be used as a seamless second factor authentication. </para>
            </listItem>
            <listItem>
              <para>
                <embeddedLabel>Single sign-on</embeddedLabel> (SSO) from devices that are associated with the company’s Active Directory. </para>
            </listItem>
            <listItem>
              <para>
                <embeddedLabel>Web Application Proxy</embeddedLabel>, which allows users to connect to applications and services from anywhere. </para>
            </listItem>
            <listItem>
              <para>
                <embeddedLabel>Multi-Factor Access Control and Multi-Factor Authentication (MFA)</embeddedLabel>, which manage the risk of users working from anywhere and accessing protected data from their devices.</para>
            </listItem>
            <listItem>
              <para>
                <embeddedLabel>Work folders</embeddedLabel>, which provide users a location to store and access work files on PCs and devices.</para>
            </listItem>
          </list>
          <para>See <externalLink><linkText>Active Directory Services</linkText><linkUri>http://technet.microsoft.com/library/dd578336(v=ws.10).aspx</linkUri></externalLink>.</para>
          <para>While the company’s management team agreed that the new features were valuable, they couldn’t approve the resources to upgrade AD as part of this solution. The management team wants to upgrade their on-premises AD in the next six months. </para>
          <para>When you are ready to upgrade your on-premises AD and implement AD FS, see <externalLink><linkText>Secure access to company resources from any location on any device</linkText><linkUri>Http://technet.microsoft.com/library/dn550982.aspx</linkUri></externalLink>.</para>
        </content>
      </section>
    </sections>
  </section>
  <section address="BKMK_Implementation" expanded="true">
    <title>Implementation steps</title>
    <content>
      <para>This section provides the steps that the company took to implement the solution. If you follow these steps, make sure to verify the correct deployment of each step before proceeding to the next step.</para>
      <list class="ordered">
        <listItem>
          <para>
            <embeddedLabel>Subscribe to Windows Intune.</embeddedLabel> </para>
          <para>Create a Windows Intune subscription on the <externalLink><linkText>Windows Intune</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkID=271123</linkUri></externalLink> web site.</para>
          <list class="bullet">
            <listItem>
              <para>If you already have a user account for another cloud service, such as Office 365, you can click <ui>Sign in</ui> to enter the account credentials. This allows you to share the same group of users across all the services in your organization’s Windows Azure AD tenant.</para>
            </listItem>
          </list>
          <para>
            <embeddedLabel>Verification steps:</embeddedLabel> After you complete the sign-up process, an email is sent to the email address that you provided. Click the link that is included in that email or go to the Windows Intune account portal at <placeholder>https://account.manage.microsoft.com</placeholder> and verify that you can sign in.</para>
        </listItem>
        <listItem>
          <para>
            <embeddedLabel>Configure your public domain.</embeddedLabel>
          </para>
          <list class="ordered">
            <listItem>
              <para>
                <embeddedLabel>Get a public domain</embeddedLabel>. To use the Windows Intune service you also need a public organization domain name that is verifiable through a domain name registration service. Add and verify your public domain in the Windows Intune account portal at <externalLink><linkText>https://account.manage.microsoft.com</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkID=329938</linkUri></externalLink> under the <ui>Domains</ui> node.</para>
            </listItem>
            <listItem>
              <para>
                <embeddedLabel>Ensure the public domain has been added as an alternate UPN suffix in on-premises Active Directory</embeddedLabel>. Users must have the same public domain User Principal Name (UPN) in the cloud and the on-premises Active Directory to enroll mobile devices. You must verify that your users have a public domain UPN before you configure directory synchronization. If you skip this step, users may get “onmicrosoft.com” appended to their cloud UPN, which will cause a mismatch with on-premises Active Directory user names. See <externalLink><linkText>Add User Principal Name Suffixes</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkID=271122</linkUri></externalLink>. </para>
            </listItem>
            <listItem>
              <para>
                <embeddedLabel>Add a CNAME record in DNS</embeddedLabel> that points <ui>enterpriseenrollment.&lt;publicdomain&gt;</ui> to <ui>manage.microsoft.com</ui>. The CNAME record is used later as part of the enrollment process. See <externalLink><linkText>Add an Alias (CNAME) Resource Record to a Zone</linkText><linkUri>http://technet.microsoft.com/library/cc772053.aspx</linkUri></externalLink>.</para>
            </listItem>
          </list>
          <para>
            <legacyBold>Verification steps:</legacyBold> </para>
          <list class="bullet">
            <listItem>
              <para>Check the <ui>Domains</ui> page of the <externalLink><linkText>Windows Intune account portal</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkID=329938</linkUri></externalLink> to make sure the public domain is listed and verified.</para>
            </listItem>
            <listItem>
              <para>Look at the properties of a user account in your on-premises Active Directory to ensure the UPN is listed with the public domain name.</para>
            </listItem>
          </list>
        </listItem>
        <listItem>
          <para>
            <legacyBold>Provide secure easy access for users by using DirSync with Password Sync.</legacyBold>
          </para>
          <para>You can configure Password Sync from your Windows Intune Account portal at <externalLink><linkText>https://account.manage.microsoft.com</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkID=329938</linkUri></externalLink>. In the <ui>Users</ui> node of the portal, click <ui>Active Directory synchronization: Set up</ui>, and then follow the steps outlined in <ui>Set up and manage Active Directory synchronization</ui>. You enable Password Sync when running the Directory Sync tool Configuration Wizard by selecting <ui>Enable Password Synchronization</ui>. </para>
          <para>See: </para>
          <list class="bullet">
            <listItem>
              <para>
                <externalLink>
                  <linkText>Directory synchronization roadmap</linkText>
                  <linkUri>http://technet.microsoft.com/library/hh967642.aspx</linkUri>
                </externalLink>
              </para>
            </listItem>
            <listItem>
              <para>
                <externalLink>
                  <linkText>Implement Password Synchronization</linkText>
                  <linkUri>http://technet.microsoft.com/en-us/library/dn246918.aspx</linkUri>
                </externalLink>
              </para>
            </listItem>
          </list>
          <para>
            <legacyBold>Verification steps</legacyBold>: Check in the Windows Intune Account portal at <externalLink><linkText>https://account.manage.microsoft.com</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkID=329938</linkUri></externalLink> to view user accounts.  </para>
        </listItem>
        <listItem>
          <para>
            <legacyBold>Install your <token>sccm2012r2_1</token> site or hierarchy.</legacyBold>
          </para>
          <para>After planning for their <token>sccm2012r2_1</token> hierarchy, the company decided they will install a stand-alone primary site at their headquarters and install distribution points at their remote locations. You might determine that your hierarchy requires a different configuration. Use the following steps to install your <token>sccm2012r2_1</token> site or hierarchy:</para>
          <list class="ordered">
            <listItem>
              <para>Identify a server that meets both the software and hardware prerequisites to host a <token>cmshort</token> primary site. See <externalLink><linkText>Planning for Hardware Configurations for Configuration Manager</linkText><linkUri>http://technet.microsoft.com/library/hh846235.aspx</linkUri></externalLink>.</para>
            </listItem>
            <listItem>
              <para>Review the required software and supported operating systems for hosting a <token>cmshort</token> site. See <externalLink><linkText>Site System Requirements</linkText><linkUri>http://technet.microsoft.com/library/gg682077.aspx#BKMK_SupConfigSiteSystemReq</linkUri></externalLink>.</para>
            </listItem>
            <listItem>
              <para>Configure your Windows environment to support <token>sccm2012r2_1</token>. See <externalLink><linkText>Prepare the Windows Environment for Configuration Manager</linkText><linkUri>http://technet.microsoft.com/library/gg712264.aspx</linkUri></externalLink>.</para>
            </listItem>
            <listItem>
              <para>Install a <token>sccm2012r2_1</token> site. See <externalLink><linkText>Install Sites and Create a Hierarchy for Configuration Manager</linkText><linkUri>http://technet.microsoft.com/library/gg712320.aspx</linkUri></externalLink>. For this solution, the company will install a stand-alone primary site and will skip steps to install a central administration site or secondary site. As you go through the topic, choose sites appropriate for your environment. </para>
            </listItem>
            <listItem>
              <para>Install a distribution point at remote locations. The example company has determined that they can use a distribution point at each of their remote locations instead of using a secondary site at each location. For details about installing and configuring a distribution point, see <externalLink><linkText>Configuring Content Management in Configuration Manager</linkText><linkUri>http://technet.microsoft.com/library/gg682115.aspx</linkUri></externalLink>.</para>
            </listItem>
          </list>
          <para>
            <embeddedLabel>Verification steps</embeddedLabel>
          </para>
          <para>On the primary site server computer, monitor progress in the Setup wizard. The <token>cmshort</token> Setup wizard displays the result of each site installation task. After all installation tasks are complete, you can close the wizard. However, after the site installation is complete, the Setup wizard continues to display information about ongoing configurations for the site, which you can monitor if you do not close the wizard. Closing the Setup wizard does not affect these ongoing configurations, which continue to run in the background after the wizard is closed. Review the <embeddedLabel>ConfigMgrSetup.log</embeddedLabel> to <?Comment DE: Need specific line to look for in the log file. 2015-03-20T15:37:00Z  Id='2?>verify that the site installed successfully<?CommentEnd Id='2'
    ?>.</para>
        </listItem>
        <listItem>
          <para>
            <embeddedLabel>Configure management features and functions.</embeddedLabel>
          </para>
          <para>After you install your site or hierarchy, configure the site to support the management features and functions of <token>sccm2012r2_1</token> you want to use. You must configure Active Directory User Discovery before you configure the Windows Intune subscription or install the Windows Intune Connector site system role in step 8. See: </para>
          <list class="ordered">
            <listItem>
              <para>
                <externalLink>
                  <linkText>Configure Sites and the Hierarchy in Configuration Manager</linkText>
                  <linkUri>http://technet.microsoft.com/library/gg712682.aspx</linkUri>
                </externalLink>
              </para>
            </listItem>
            <listItem>
              <para>
                <externalLink>
                  <linkText>Configure Active Directory Discovery for Computers, Users, or Groups</linkText>
                  <linkUri>http://technet.microsoft.com/library/hh427340.aspx</linkUri>
                </externalLink>
              </para>
            </listItem>
          </list>
        </listItem>
        <listItem>
          <para>
            <legacyBold>Migrate to <token>sccm2012r2_1</token>.</legacyBold> </para>
          <para>When you migrate objects from your <token>sccmshortname</token> source hierarchy, you access data from the site databases that you identify in the source infrastructure and then copy that data to the <token>sccm2012r2_1</token> hierarchy. Migration does not change the data in the source hierarchy. It discovers the data and stores a copy in the database of the destination hierarchy. See <externalLink><linkText>Migrating Hierarchies in System Center 2012 Configuration Manager</linkText><linkUri>http://technet.microsoft.com/library/gg682006.aspx</linkUri></externalLink>.</para>
          <para>To migrate your <token>sccmshortname</token> data to <token>sccm2012r2_1</token>:</para>
          <list class="ordered">
            <listItem>
              <para>
                <embeddedLabel>Specify your <token>sccmshortname</token> SP2 hierarchy as the source hierarchy for migration</embeddedLabel>. By default, the top-level site of that hierarchy becomes a source site of the source hierarchy. After data is gathered from the initial source site, you can then configure additional source sites for migration. </para>
              <para>
                <token>cmshort</token> starts to gather data from the source site immediately after you specify a source hierarchy, configure credentials for each additional source site in a source hierarchy, or share the distribution points for a source site. By default, the data gathering process repeats every four hours so that <token>cmshort</token> can identify changes to data in the source hierarchy that you might want to migrate. Data gathering is also necessary to share distribution points from the source hierarchy to the destination hierarchy. See <externalLink><linkText>Configuring Source Hierarchies and Source Sites for Migration to System Center 2012 Configuration Manager</linkText><linkUri>http://technet.microsoft.com/library/gg712307.aspx</linkUri></externalLink>.</para>
            </listItem>
            <listItem>
              <para>
                <embeddedLabel>Create migration jobs to migrate data between the source and destination hierarchy</embeddedLabel>. Use migration jobs to configure the specific data that you want to migrate to your <token>sccm2012r2_1</token> environment. Migration jobs identify the objects that you plan to migrate, and they run at the top-level site in your hierarchy. See <externalLink><linkText>Create and Edit Migration Jobs for System Center 2012 Configuration Manager</linkText><linkUri>http://technet.microsoft.com/library/gg682026.aspx#Create_Edit_migration_Jobs</linkUri></externalLink>. </para>
            </listItem>
            <listItem>
              <para>
                <embeddedLabel>Monitor migration jobs</embeddedLabel>. Monitor the progress of migration jobs in the <token>sccm2012r2_1</token> console. See <externalLink><linkText>Monitor Migration Activity in the Migration Workspace</linkText><linkUri>http://technet.microsoft.com/library/gg682026.aspx#Monitor_MIgration</linkUri></externalLink>. </para>
            </listItem>
            <listItem>
              <para>
                <embeddedLabel>Upgrade shared distribution points</embeddedLabel>. You can upgrade a supported distribution point that is shared from your <token>sccmshortname</token> source site to be a distribution point in the destination hierarchy. See <externalLink><linkText>Upgrade or Reassign a Shared Distribution Point in System Center 2012 Configuration Manager</linkText><linkUri>http://technet.microsoft.com/library/gg682026.aspx#BKMK_ProcUpgrdSS</linkUri></externalLink>.</para>
            </listItem>
            <listItem>
              <para>
                <embeddedLabel>Migrate <token>sccmshortname</token> clients to <token>sccm2012r2_1</token></embeddedLabel>. After you migrate data for clients between hierarchies but before you complete migration, plan to migrate clients to the destination hierarchy. To migrate clients between hierarchies, install the <token>cmshort</token> client software from the destination hierarchy. The <token>cmshort</token> client is uninstalled, and the <token>sccm2012r2_1</token> client is installed and assigned to the primary site. See <externalLink><linkText>Planning a Client Migration Strategy in System Center 2012 Configuration Manager</linkText><linkUri>http://technet.microsoft.com/library/gg712283.aspx</linkUri></externalLink>.</para>
            </listItem>
            <listItem>
              <para>
                <embeddedLabel>Complete the migration process</embeddedLabel>: When your <token>sccmshortname</token> hierarchy no longer contains data that you want to migrate to your destination hierarchy, you can complete the migration process. To do so: </para>
              <list class="ordered">
                <listItem>
                  <para>Make sure that you have successfully migrated all of the resources from the source hierarchy that you require in the destination hierarchy. This can include data and clients.</para>
                </listItem>
                <listItem>
                  <para>Stop gathering data from each source site in your <token>sccmshortname</token> hierarchy. To do so, run the <embeddedLabel>Stop Gathering Data</embeddedLabel> action on the bottom tier source sites, and then repeat the process at each parent site. The top-level site of the source hierarchy must be the last site on which you stop gathering data. <embeddedLabel>You must stop data gathering at each child site before performing this action on a parent site.</embeddedLabel> After you stop gathering data, you can no longer share distribution points between the source and destination hierarchies. </para>
                </listItem>
                <listItem>
                  <para>Clean up migration data. To do so, use the <embeddedLabel>Clean Up Migration Data</embeddedLabel> action. This optional action removes data about the current source hierarchy from the database of the destination hierarchy. Until you clean up migration data, each migration job that has run or that is scheduled to run remains accessible in the <token>cmshort</token> console. When you clean up migration data, most data about the migration is removed from the database of the destination hierarchy. See <externalLink><linkText>Complete Migration in System Center 2012 Configuration Manager</linkText><linkUri>http://technet.microsoft.com/library/gg682026.aspx#Complete_Migration</linkUri></externalLink>.</para>
                </listItem>
              </list>
              <para>
                <embeddedLabel>Verification steps:</embeddedLabel> Migration is comprised of several distinct actions or phases, and extends over a period of time until you decide to complete the migration process. Therefore, there is no single verification step or process you can review to confirm that migration is complete. Instead, you can verify results as they display in the <token>sccm2012r2_1</token> console when actions for each phase run or complete. </para>
            </listItem>
            <listItem>
              <para>
                <embeddedLabel>Decommission your <token>sccmshortname</token> hierarchy:</embeddedLabel> After you complete migration from a source hierarchy and that hierarchy no longer contains resources that you manage, you can decommission the sites in the source hierarchy and remove the related infrastructure from your environment. See <externalLink><linkText>Configuration Manager Tasks for Decommissioning Sites and Hierarchies</linkText><linkUri>http://technet.microsoft.com/library/bb681023.aspx</linkUri></externalLink>.</para>
            </listItem>
          </list>
        </listItem>
        <listItem>
          <para>
            <embeddedLabel>Get certificates or keys for mobile devices</embeddedLabel>
          </para>
          <para>The company must have certificates or sideloading keys before they can enroll mobile devices. The types of mobile devices that you have in your environment will determine what certificates or sideloading keys you will need. See <externalLink><linkText>Obtain Certificates or Keys to Meet Prerequisites per Platform</linkText><linkUri>http://technet.microsoft.com/library/jj884158.aspx#bkmk_certs</linkUri></externalLink>.</para>
        </listItem>
        <listItem>
          <para>
            <embeddedLabel>Configure the Windows Intune subscription and install the Windows Intune Connector site system role on the top-level site.</embeddedLabel> </para>
          <para>Before the company can use <token>cmshort</token> to manage mobile devices, they must configure their Windows Intune subscription and install the Windows Intune connector site system role on their top-level site server. They will configure their stand-alone primary site. If you have a more complex hierarchy, configure your central administration site. </para>
          <list class="ordered">
            <listItem>
              <para>
                <embeddedLabel>Configure your Windows Intune subscription</embeddedLabel>. See <externalLink><linkText>Configuring the Windows Intune Subscription</linkText><linkUri>http://technet.microsoft.com/library/jj884158.aspx#bkmk_witsub</linkUri></externalLink>.</para>
            </listItem>
            <listItem>
              <para>
                <embeddedLabel>Install the Windows Intune connector</embeddedLabel>. See <externalLink><linkText>The Windows Connector Site System Role</linkText><linkUri>http://technet.microsoft.com/library/jj884158.aspx#bkmk_WITconn</linkUri></externalLink>.</para>
            </listItem>
          </list>
          <para />
          <para>
            <legacyBold>Verification steps:</legacyBold> </para>
          <list class="bullet">
            <listItem>
              <para>On the primary site server computer, review the <ui>sitecomp.log</ui> to verify that the Windows Intune connector site system role installed successfully.</para>
            </listItem>
            <listItem>
              <para>On the computer where you install the Windows Intune connector, review the <ui>cloudusersync.log</ui> to verify that users from your domain have successfully synchronized to Windows Intune. </para>
            </listItem>
            <listItem>
              <para>On the primary site server computer, review the <ui>CertMgr.log</ui> to confirm that the computer where you installed the Windows Intune connector shares the connector certificate. The certificate is shared after the installation of the Windows Intune connector site system role is complete. </para>
            </listItem>
            <listItem>
              <para>On the computer where you install the Windows Intune connector, review the <ui>dmpuploader.log</ui> to verify that the connector site system role can upload policy and configuration changes to the Windows Intune service.</para>
            </listItem>
            <listItem>
              <para>On the computer where you install the Windows Intune connector, review the <ui>dmpdownloader.log</ui> to verify that the Windows Intune connector is able to download messages from Windows Intune. This log might only show a ping at the beginning of the download process and it might take some time before entries related to downloads are logged.</para>
            </listItem>
          </list>
        </listItem>
        <listItem>
          <para>
            <legacyBold>Enroll mobile devices.</legacyBold>
          </para>
          <para>Enrollment establishes a relationship between the user, the mobile device, and the Windows Intune service. Users enroll their own mobile devices. Android devices are not enrolled, but can be managed by using the Exchange Server connector. See <externalLink><linkText>Mobile Device Enrollment</linkText><linkUri>http://technet.microsoft.com/library/jj884158.aspx#bkmk_enroll</linkUri></externalLink>.</para>
        </listItem>
        <listItem>
          <para>
            <legacyBold>Install the <token>sccm2012r2_1</token> console.</legacyBold>
          </para>
          <para>By default, when you install a primary site, the <token>cmshort</token> console also installs on the primary site server computer. After the site installs, you can install additional <token>sccm2012r2_1</token> consoles on computers to manage the site. See <externalLink><linkText>Install a Configuration Manager Console</linkText><linkUri>http://technet.microsoft.com/library/gg712320.aspx#BKMK_InstallConsole</linkUri></externalLink>.</para>
        </listItem>
        <listItem>
          <para>
            <legacyBold>Manage your PCs and mobile devices.</legacyBold>
          </para>
          <para>After you install and make the basic configurations for your site, you can begin to configure management of your PCs and mobile devices. The following are typical features or functionality that you might configure:</para>
          <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
            <thead>
              <tr>
                <TD>
                  <para>Feature</para>
                </TD>
                <TD>
                  <para>Details</para>
                </TD>
              </tr>
            </thead>
            <tbody>
              <tr>
                <TD>
                  <para>
                    <externalLink>
                      <linkText>Hardware inventory</linkText>
                      <linkUri>http://technet.microsoft.com/library/gg682078.aspx</linkUri>
                    </externalLink>
                  </para>
                </TD>
                <TD>
                  <para>Use hardware inventory to collect information about the hardware configuration of client devices in your organization.</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>
                    <externalLink>
                      <linkText>Software inventory</linkText>
                      <linkUri>http://technet.microsoft.com/library/gg682204.aspx</linkUri>
                    </externalLink>
                  </para>
                </TD>
                <TD>
                  <para>Use software inventory to collect information about files that are contained on client devices in your organization. Additionally, software inventory can collect files from client devices and store these on the site server.</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>
                    <externalLink>
                      <linkText>Asset Intelligence</linkText>
                      <linkUri>http://technet.microsoft.com/library/gg712322.aspx</linkUri>
                    </externalLink>
                  </para>
                </TD>
                <TD>
                  <para>Use Asset Intelligence to inventory and manage software license usage throughout your enterprise and improve the breadth of information that is collected about hardware and software.</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>
                    <externalLink>
                      <linkText>Compliance settings</linkText>
                      <linkUri>http://technet.microsoft.com/library/gg682002.aspx</linkUri>
                    </externalLink>
                  </para>
                </TD>
                <TD>
                  <para>Use compliance settings to manage the configuration and compliance of servers, laptops, desktop computers, and mobile devices in your organization.</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>
                    <externalLink>
                      <linkText>Company resource access</linkText>
                      <linkUri>http://technet.microsoft.com/library/dn248972.aspx</linkUri>
                    </externalLink>
                  </para>
                </TD>
                <TD>
                  <para>Use company resource access to provide users in your organization access to data and applications from remote locations by configuring the following: </para>
                  <list class="bullet">
                    <listItem>
                      <para>Certificate profiles</para>
                    </listItem>
                    <listItem>
                      <para>VPN profiles</para>
                    </listItem>
                    <listItem>
                      <para>Wi-Fi profiles</para>
                    </listItem>
                  </list>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>
                    <externalLink>
                      <linkText>Remote connection profiles</linkText>
                      <linkUri>http://technet.microsoft.com/library/dn261201.aspx</linkUri>
                    </externalLink>
                  </para>
                </TD>
                <TD>
                  <para>Use remote connection profiles to allow your users to remotely connect to work computers when they are not connected to the domain or if their personal computers are connected over the Internet.</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>
                    <externalLink>
                      <linkText>Application management</linkText>
                      <linkUri>http://technet.microsoft.com/library/gg699373.aspx</linkUri>
                    </externalLink>
                  </para>
                </TD>
                <TD>
                  <para>Use application management to manage applications in your enterprise for both <token>cmshort</token> administrative users and client device users.</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>
                    <externalLink>
                      <linkText>Software updates</linkText>
                      <linkUri>http://technet.microsoft.com/library/gg712304.aspx</linkUri>
                    </externalLink>
                  </para>
                </TD>
                <TD>
                  <para>Use software updates to monitor compliance and deploy software updates to computers in your enterprise.</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>
                    <externalLink>
                      <linkText>Manage mobile devices</linkText>
                      <linkUri>http://technet.microsoft.com/library/jj884158.aspx</linkUri>
                    </externalLink>
                  </para>
                </TD>
                <TD>
                  <para>Use this walkthrough for the steps to let you manage Windows Phone 8, Windows RT, iOS, and Android devices by using the Windows Intune service over the Internet.</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>
                    <externalLink>
                      <linkText>Wiping company content from mobile devices</linkText>
                      <linkUri>http://technet.microsoft.com/library/jj884158.aspx#bkmk_dev</linkUri>
                    </externalLink>
                  </para>
                </TD>
                <TD>
                  <para>You can do a full wipe on Windows Phone 8, iOS, and Android devices to restore the device to factory settings. Or, you can do a selective wipe that only removes company content. </para>
                </TD>
              </tr>
            </tbody>
          </table>
        </listItem>
      </list>
    </content>
  </section>
  <section>
    <title>See also</title>
    <content>
      <para />
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Content type</para>
            </TD>
            <TD>
              <para>Reference</para>
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
                      <linkText>Getting Started with System Center 2012 Configuration Manager</linkText>
                      <linkUri>http://technet.microsoft.com/library/gg682144.aspx</linkUri>
                    </externalLink>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <externalLink>
                      <linkText>Download the evaluation for System Center 2012 R2 Configuration Manager and Endpoint Protection</linkText>
                      <linkUri>http://technet.microsoft.com/evalcenter/dn205297.aspx</linkUri>
                    </externalLink>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <externalLink>
                      <linkText>Configuration Manager TechCenter</linkText>
                      <linkUri>http://technet.microsoft.com/systemcenter/hh285244</linkUri>
                    </externalLink>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <externalLink>
                      <linkText>Evaluate Windows Intune</linkText>
                      <linkUri>http://www.microsoft.com/windowsintune</linkUri>
                    </externalLink>
                  </para>
                </listItem>
              </list>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Reference</para>
            </TD>
            <TD>
              <list class="bullet">
                <listItem>
                  <para>
                    <externalLink>
                      <linkText>Manage mobile devices</linkText>
                      <linkUri>http://technet.microsoft.com/library/jj884158.aspx</linkUri>
                    </externalLink>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <externalLink>
                      <linkText>Bring Your Own Device (BYOD) Design Considerations Guide</linkText>
                      <linkUri>http://technet.microsoft.com/library/dn656905.aspx</linkUri>
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
                    <externalLink>
                      <linkText>Mobile Device Management for Configuration Manager 2007 Customers Planning to Migrate to System Center 2012 R2 Configuration Manager</linkText>
                      <linkUri>http://technet.microsoft.com/library/dn508400.aspx</linkUri>
                    </externalLink>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <externalLink>
                      <linkText>Secure access to company resources from any location on any device</linkText>
                      <linkUri>Http://technet.microsoft.com/library/dn550982.aspx</linkUri>
                    </externalLink>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <externalLink>
                      <linkText>Use DirSync with Password Sync to manage identities and synchronize information in hybrid environments</linkText>
                      <linkUri>http://technet.microsoft.com/library/dn550986.aspx</linkUri>
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
                      <linkText>System Center 2012 R2 Configuration Manager TechNet forums</linkText>
                      <linkUri>http://social.technet.microsoft.com/Forums/en-us/category/systemcenter2012configurationmanager</linkUri>
                    </externalLink>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <externalLink>
                      <linkText>Windows Intune forum</linkText>
                      <linkUri>http://social.technet.microsoft.com/Forums/en-US/home?category=windowsintune</linkUri>
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