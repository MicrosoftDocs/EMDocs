---
title: Extend Device Management to the Cloud
ms.custom: na
ms.prod: system-center-2012-r2
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configuration-manager
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2b84908d-2694-4558-bbc0-bc02e252d055
author: Jeffgilb
---
# Extend Device Management to the Cloud
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://clixdevr3.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>
      <embeddedLabel>How can this guide help you?</embeddedLabel> As the bring your own device (BYOD) trend continues to grow, and supporting it becomes a business reality, enterprises must find a way to manage both company-owned and employee-owned mobile devices and PCs that can now be used either on-premises or remotely. As an enterprise-level IT Professional you can use this solution guide to understand how to leverage investments in your existing <token>sccm2012r2_1</token> infrastructure to support the employee demand to use these devices to access corporate resources.</para>
    <para>This solution guide describes the implementation steps for the tested design that we recommend to unify PC and mobile device management into a single infrastructure by integrating <token>wit_2</token> with your existing <token>cmshort</token> environment.  By extending device management to the cloud you can help maintain corporate compliance, protect company data, and enable users to work from anywhere and on the device of their choice. </para>
    <para />
    <para>
      <embeddedLabel>In this solution guide:</embeddedLabel>
    </para>
    <list class="bullet">
      <listItem>
        <para>
          <legacyLink xlink:href="28efb45b-692c-46f5-9a36-aef89ef1e4a6#BKMK_Scenario">Scenario, problem statement, and goals</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="28efb45b-692c-46f5-9a36-aef89ef1e4a6#BKMK_Recommendation">What is the recommended design for this solution?</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <link xlink:href="07cad07f-e499-4b96-9ae0-96aca1373748#BKMK_WhyRecommended">Why are we recommending this design?</link>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="28efb45b-692c-46f5-9a36-aef89ef1e4a6#BKMK_ImplementationSteps">What are the steps to implement this solution?</legacyLink>
        </para>
      </listItem>
    </list>
  </introduction>
  <section address="BKMK_Scenario">
    <title>Scenario, problem statement, and goals</title>
    <content>
      <para>This section describes the scenario, current problem, and business goals you might have. After reviewing this solution to the growing problem of supporting BYOD while empowering users to work virtually anywhere on almost any device, you can decide whether it meets your needs, or if you need to adjust it for your particular business environment.</para>
      <para>The following diagram illustrates the problem that this solution guide is addressing.</para>
      <para>
        <embeddedLabel>Users cannot access corporate resources from mobile devices.</embeddedLabel>
      </para>
      <mediaLink>
        <image xlink:href="5f549792-dd46-407b-a76d-175d8dcd47b5" />
      </mediaLink>
      <para />
    </content>
    <sections>
      <sectionSimple>
        <para>
          <embeddedLabel>Scenario</embeddedLabel>
        </para>
        <para>Enterprise businesses need to find a way to support growing BYOD requirements and enable their users to easily and securely access corporate resources from the device of their choice—either corporate owned or personal.  </para>
        <para>In this solution, it is assumed that enterprises are already using <token>sccm2012r2_1</token> to manage PCs for users who are on-premises and who remotely connect to the corporate network by VPN. However, these companies cannot manage mobile devices. In addition to <token>cmshort</token>, the on-premises infrastructure of these company environments contains: </para>
        <list class="bullet">
          <listItem>
            <para>
              <token>winblue_server_2</token>
            </para>
          </listItem>
          <listItem>
            <para>
              <token>winblue_server_2</token> Active Directory</para>
          </listItem>
          <listItem>
            <para>PCs that are joined to the domain and managed by <token>sccm2012r2_1</token></para>
          </listItem>
        </list>
        <para>In addition, these companies do not currently make use of the available Microsoft Cloud technology services for identity, productivity, or device and data management.  </para>
      </sectionSimple>
      <sectionSimple>
        <para>
          <embeddedLabel>Problem statement</embeddedLabel>
        </para>
        <para>The overall problem to solve is: <embeddedLabel>the current device management infrastructure does not support the company’s growing BYOD needs.</embeddedLabel></para>
        <para>Companies such as these can easily manage on-premises PCs in their current environment using <token>cmshort</token>, but they can’t manage mobile devices—whether they provide corporate-owned mobile devices or employees bring their personal devices to work. Because they know it can be expensive to support many mobile devices and applications in addition to company PCs, these businesses are also concerned about the resources required to manage all these devices.</para>
        <para>However, as soon as employees start working on a device that IT doesn’t manage (or even know about), it becomes very difficult to retain control of sensitive corporate information and nothing can be done if the device is sold, lost, or stolen. Because of this, the costs of managing mobile devices and applications is outweighed by the need to manage security risks to corporate assets and information by ensuring that all devices, both corporate and personal, comply with company security and acceptable use policies. </para>
      </sectionSimple>
      <sectionSimple>
        <para>
          <embeddedLabel>Goals</embeddedLabel>
        </para>
        <para>Based on the scenario and problem statement, an enterprise level solution for supporting BYOD is needed that meets the following business requirements:</para>
        <list class="bullet">
          <listItem>
            <para>Leverages and extends the existing on-premises Active Directory and <token>cmshort</token> infrastructure. IT teams have usually invested a lot of resources into their current environment and they don’t want to start over.</para>
          </listItem>
          <listItem>
            <para>Let employees use personal, as well as company owned, PCs and devices to access corporate applications and data.</para>
          </listItem>
          <listItem>
            <para>Manage PCs and mobile devices from a single administrator console.</para>
          </listItem>
          <listItem>
            <para>Deploy applications based on device type or whether the device is personal or owned by the company.</para>
          </listItem>
          <listItem>
            <para>Protect the company by wiping corporate data stored on mobile devices when they are lost, stolen, or retired from use.</para>
          </listItem>
        </list>
      </sectionSimple>
    </sections>
  </section>
  <section address="BKMK_Recommendation">
    <title>What is the recommended design for this solution?</title>
    <content>
      <para>To solve their current business problems and fully embrace the BYOD trend, enterprises should extend their device management infrastructure to support growing BYOD needs as follows:</para>
      <list class="bullet">
        <listItem>
          <para>Synchronize their on-premises Active Directory domain user accounts to Microsoft Azure Active Directory using Azure Active Directory Connect. Doing this makes corporate identities available in the cloud to authenticate and authorize users on the devices and apps they are using, wherever they are. </para>
        </listItem>
        <listItem>
          <para>Synchronize user passwords using Azure Active Directory Connect to allow users to use the same on-premises domain user name and password for cloud services authenticated by Azure Active Directory. This is the simplest way to enable same-sign-on for their users without implementing Active Directory Federation Services on-premises.</para>
          <alert class="important">
            <para>When you synchronize passwords you don’t actually send user passwords to Azure Active Directory. Instead, you will be synchronizing a non-reversible hash of the passwords that is used to authenticate users to services and applications. If you do not enable password sync you will need to implement AD FS to support on-premises user account authentication. </para>
          </alert>
        </listItem>
        <listItem>
          <para>Subscribe to <token>wit_2</token> and configure the <token>wit_2</token> connector in Configuration Manager to integrate with the <token>wit_2</token> service. This also includes preparing their environments to meet mobile device enrollment prerequisites.</para>
        </listItem>
        <listItem>
          <para>Empower users to enroll their mobile devices into management and gain access to company resources in a secure and efficient manner.</para>
        </listItem>
      </list>
      <para>You can learn how Microsoft IT defined a people centric approach to enable the consumerization of IT by providing unified device management solution using <token>cmshort</token> and <token>wit_2</token> in this short video:</para>
      <mediaLink>
        <image xlink:href="674e014c-91c2-470c-8adf-cf1726029567" />
        <video videotype="single" videoid="4f62f141-8738-4bf3-8edf-b5dbb9b7b01c" player="sp_generic_640X360" />
      </mediaLink>
      <para />
    </content>
    <sections>
      <section address="BKMK_WhyRecommended">
        <title>Why are we recommending this design?</title>
        <content>
          <para>You can extend your device management to the cloud by integrating <token>sccm2012r2_1</token> and <token>wit_2</token> to manage corporate-connected Windows PCs, Macs, and Unix/Linux Servers on-premises along with cloud-based mobile devices running Windows, Windows Phone, Apple iOS, and Android to create a complete, comprehensive management solution using a single administrative console, infrastructure, and reporting system.</para>
          <para>In this solution it is recommended to leverage the <token>wit_2</token> service to manage mobile devices and non-domain joined computers while <token>cmshort</token> is used to manage domain-joined or on-premises computers and servers. Device management tasks are managed from the <token>cmshort</token> console and then communicated to the <token>wit_2</token> service, which actually performs the device management functions relayed to it by the <token>wit_2</token> connector site system role. This provides you with a single management experience that spans across all of the mobile devices and computers used by your enterprise.  </para>
          <para>Even if you have previously evaluated or used <token>wit_2</token> stand-alone, this solution would still be applicable to you if you have over 50,000 devices to manage (or plan to scale-up). Integrating <token>wit_2</token> with <token>cmshort</token> can manage larger numbers of mobile devices and computers than <token>wit_2</token> stand-alone.</para>
          <alert class="note">
            <para>For more information to help choose which configuration is best for you, you can review the <externalLink><linkText>detailed comparison of capabilities</linkText><linkUri>https://technet.microsoft.com/library/dn646980.aspx</linkUri></externalLink> available for using <token>wit_2</token> standalone, <token>cmshort</token> standalone, or <token>cmshort</token> with <token>wit_2</token> integration (this solution). </para>
          </alert>
          <para>The following diagram illustrates how the elements in this solution communicate with each other.</para>
          <mediaLink>
            <image xlink:href="bb73c7ba-9476-4058-aead-dc53e381c37d">
              <externalLink>
                <linkText />
                <linkUri>http://content1.catalog.video.msn.com/e2/ds/dee37556-2d42-43dd-aee5-7a561f57aec0.mp4</linkUri>
              </externalLink>
            </image>
          </mediaLink>
          <para>2D     3D     <externalLink><linkText>Video</linkText><linkUri>http://content1.catalog.video.msn.com/e2/ds/dee37556-2d42-43dd-aee5-7a561f57aec0.mp4</linkUri></externalLink></para>
          <para />
          <para>The following table lists the elements that are part of this solution design and describes why they’re included in the design. The elements are listed in the order that they are addressed in this solution to provide a step-wise implementation of unifying device management by integrating <token>wit_2</token> with <token>cmshort</token>. </para>
          <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
            <thead>
              <tr>
                <TD>
                  <para>
                    <embeddedLabel>Solution design element</embeddedLabel>
                  </para>
                </TD>
                <TD>
                  <para>
                    <embeddedLabel>Why is it included in this solution?</embeddedLabel>
                  </para>
                </TD>
              </tr>
            </thead>
            <tbody>
              <tr>
                <TD>
                  <para>
                    <embeddedLabel>Domain name server</embeddedLabel>
                  </para>
                </TD>
                <TD>
                  <para>This solution design element represents the publicly accessible domain name server that hosts the DNS zone file for your public domain name. You will need to modify the DNS zone file to verify your company’s public domain name with Microsoft Azure AD.</para>
                  <alert class="note">
                    <para>Later, you will also need to add a CNAME for your custom domain to point to <placeholder>manage.microsoft.com</placeholder> if you want to enable name resolution for Windows devices to find the enrollment server during the <token>wit_2</token> device enrollment process. </para>
                  </alert>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>
                    <embeddedLabel>On-premises Active Directory</embeddedLabel>
                  </para>
                </TD>
                <TD>
                  <para>The user objects to be synchronized with Azure AD and enabled for device enrollment will come from the on-premises AD.</para>
                  <para>You will also need to add a user principle name (UPN) matching your company’s public domain name to Active Directory Domains and Trusts in the on-premises Active Directory. </para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>
                    <embeddedLabel>Cloud Users OU</embeddedLabel>
                  </para>
                </TD>
                <TD>
                  <para>The custom cloud users organizational unit is created as part of this solution. It is used to group on-premises Active Directory users into a single organizational unit in preparation for synchronizing account information to Azure Active Directory. </para>
                  <para>Before you synchronize these accounts, the UPN properties for each user account should be modified to use the public domain name previously added to Active Directory Domains and Trusts.</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>
                    <embeddedLabel>Synchronization Server</embeddedLabel>
                  </para>
                </TD>
                <TD>
                  <para>The <token>winblue_server_2</token> server that runs the Active Directory synchronization service to provide identity and access capabilities for on-premises and cloud applications.</para>
                  <para>In this solution <externalLink><linkText>Azure AD Connect</linkText><linkUri>http://connect.microsoft.com/site1164/Downloads/DownloadDetails.aspx?DownloadID=53949</linkUri></externalLink> is installed on the synchronization server to provide a guided experience for integrating one or more Active Directory forests with Microsoft Azure Active Directory.</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>
                    <embeddedLabel>Azure AD</embeddedLabel>
                  </para>
                </TD>
                <TD>
                  <para>Similar to Windows Server Active Directory on-premises, Azure AD lets you centrally control access to applications and resources by providing a cloud-based identity and access management solution. With Azure AD, and directory synchronization, your users don’t need to remember a separate user name or password.</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>
                    <embeddedLabel>Synchronized Users</embeddedLabel> </para>
                </TD>
                <TD>
                  <para>On-premises users that you want to enable for device management are synchronized to Azure AD.</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>
                    <embeddedLabel>
                      <token>wit_2</token> Account Portal</embeddedLabel>
                  </para>
                </TD>
                <TD>
                  <para>The <token>wit_2</token> account portal is used by administrators to manage users, groups, and domains for Microsoft Online Services, including <token>wit_2</token> and Office 365. You can use the account portal to check the status of your subscriptions, add new subscriptions, add new domain names, and activate new user accounts. It is also where you can set up and configure the link to your on-premises Active Directory Domain.</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>
                    <embeddedLabel>Configuration Manager Primary Site Server</embeddedLabel>
                  </para>
                </TD>
                <TD>
                  <para>Provides secure and scalable software deployment, compliance settings management, and comprehensive asset management of servers, desktops, laptops, and mobile devices when <token>wit_2</token> is integrated.</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>
                    <embeddedLabel>Configuration Manager Cloud Users Collection</embeddedLabel>
                  </para>
                </TD>
                <TD>
                  <para>The custom cloud users <token>cmshort</token> collection is created as part of this solution. It is used to group on-premises Active Directory users into a collection in preparation for mobile device management enrollment.</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>
                    <embeddedLabel>
                      <token>wit_2</token> Subscription</embeddedLabel>
                  </para>
                </TD>
                <TD>
                  <para>
                    <token>wit_2</token>’s subscription-based, per-user licensing provides an easy and predictable way to automatically access the latest mobile device management features.</para>
                  <para>You will need to obtain or use a pre-existing <token>wit_2</token> subscription in order to integrate it into <token>cmshort</token>.</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>
                    <embeddedLabel>
                      <token>wit_2</token> Connector <token>cmshort</token> Site System Role Server</embeddedLabel>
                  </para>
                </TD>
                <TD>
                  <para>The Intune connector sends settings and software deployment information to the Intune service and retrieves status and inventory messages from mobile devices to add to the <token>cmshort</token> site database.</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>
                    <embeddedLabel>
                      <token>wit_2</token> Company Portal</embeddedLabel>
                  </para>
                </TD>
                <TD>
                  <para>Users must sign in to the Microsoft Intune Company Portal (website or app) to self-enroll their device and access managed apps. Administrators can configure Company Portal settings such as the company name, support contact information, and privacy statement links from within the <token>cmshort</token> administration console.</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>
                    <embeddedLabel>
                      <token>wit_2</token> Management Service</embeddedLabel>
                  </para>
                </TD>
                <TD>
                  <para>Microsoft Intune helps organizations provide their employees with access to corporate applications, data, and resources from anywhere on almost any device, while helping to keep corporate information secure.</para>
                </TD>
              </tr>
            </tbody>
          </table>
          <para />
        </content>
      </section>
    </sections>
  </section>
  <section address="BKMK_ImplementationSteps">
    <title>What are the steps to implement this solution?</title>
    <content>
      <para>Follow these steps to implement device management using Configuration Manager with Microsoft Intune integration. Make sure to verify the correct deployment of each step before proceeding to the next step.</para>
      <alert class="note">
        <para>If you want to print or export a customized set of solution topics, see <externalLink><linkText>Print/Export Multiple Topics – Help</linkText><linkUri>http://technet.microsoft.com/en-US/library/export/help/?returnUrl=%2fen-US%2flibrary%2fff630950.aspx</linkUri></externalLink>.</para>
      </alert>
      <list class="ordered">
        <listItem>
          <para>
            <embeddedLabel>Get a Microsoft Intune subscription</embeddedLabel> that will be used.</para>
          <para />
          <para>
            <embeddedLabel>Verification steps:</embeddedLabel>.</para>
          <para />
        </listItem>
        <listItem>
          <para>
            <embeddedLabel>
              <?Comment JJG: https://technet.microsoft.com/en-us/library/hh969247.aspx 2015-03-20T15:36:00Z  Id='2?>Add and verify your public domain to Azure<?CommentEnd Id='2'
    ?></embeddedLabel> that will be used. Go to manage your account from the Intune Admin Portal and then select Domains under Management. Select Add a domain.  Note: You can only add domain names that you own. If you don't already own a domain name, you can purchase one from a domain registrar, and then return to add it to Microsoft Online Services.  After you create the TXT record and sign out of the website, return to Microsoft Online Services to verify the domain.
</para>
          <para>Next, you’ll need to go through the process to verify the name with Azure.  The preferred method is a txt file. </para>
          <alert class="note">
            <para>Typically it takes about 15 minutes for your changes to take effect. But it can take up to 72 hours for the DNS record that you created to propagate through the DNS system.</para>
          </alert>
          <para>
            <embeddedLabel>Verification steps:</embeddedLabel> Log into the account portal, go to Management, Domains. Select the domain name and “Click to verify domain”. At the bottom of the page, click Verify. “emsdemos.net has been added to your account You can now use this domain to add users. Next step: configure domain

To configure your domain to work with Microsoft Online Services, click Configure DNS records below. To return to this step at a later time, click Close.  Learn more Next step: Configure DNS and set up your website 

To create your website, and to learn about the DNS record you'll need to configure to route traffic to your website, go to the SharePoint Online Administration Center. 

Creating public-facing websites 

SharePoint Online Administration CenterSharePoint Online Administration Center 
”</para>
          <para />
        </listItem>
        <listItem>
          <para>
            <embeddedLabel>Add UPN to AD Domains and Trusts</embeddedLabel>.</para>
          <para>
            <?Comment JJG: fromhybrid lab guide 2015-03-20T15:36:00Z  Id='3?>The first step in integrating Configuration Manager and Intune is to configure alternate user principle name (UPN) suffixes in Active Directory Domain Services (AD DS). Alternate UPN suffixes can allow users to log in to Windows by using your Intune subscription’s domain name (e.g., contoso.onmicrosoft.com). You add alternate UPN suffixes in AD DS by using the Active Directory Domains and Trusts Microsoft Management Console (MMC) snap-in.<?CommentEnd Id='3'
    ?></para>
          <para>
            <embeddedLabel>Verification steps:</embeddedLabel>.</para>
          <para />
        </listItem>
        <listItem>
          <para>
            <embeddedLabel>Create an organizational unit of users to sync with Azure AD</embeddedLabel>.</para>
          <para />
          <para>
            <embeddedLabel>Verification steps:</embeddedLabel>.</para>
          <para />
        </listItem>
        <listItem>
          <para>
            <embeddedLabel>Update users’ UPN settings</embeddedLabel>. The easiest way to do this is to highlight all of them, right-click properties, and bulk update the UPN suffix setting on the Account tab. If you have properly added the UPN to your domain, it should be available via the drop-down box. .</para>
          <para />
          <para>
            <embeddedLabel>Verification steps:</embeddedLabel> Check the UPN setting on a user property’s Account tab.</para>
          <para />
        </listItem>
        <listItem>
          <para>
            <embeddedLabel>Install Azure AD Connect and perform a custom synchronization</embeddedLabel>. This option will install the Azure Active Directory Sync tool on the local server computer, configure synchronization of identities in the current AD forest, configure password synchronization from on-premise to AD to AAD, and start an initial synchronization. </para>
          <para>The Azure AD Connect wizard is the single tool and guided experience for connecting your on premises identity infrastructure to the cloud.  Choose your topology and needs (single or multiple directories, password sync or federation), and the wizard will deploy and configure all components required to get your connection up and running including sync services, AD FS, and the Azure AD PowerShell module.</para>
          <para>Azure AD Connect encompasses functionality that was previously released as Dirsync and AAD Sync.  These tools will no longer be released individually.  All future improvements will be included in updates to Azure AD Connect, so that you always know where to get the most current functionality.</para>
          <para>The Azure AD Connect wizard is a single wizard that performs all of the steps you would otherwise have to do manually for connecting Active Directory and local directories to Azure Active Directory:</para>
          <list class="bullet">
            <listItem>
              <para>Downloads and installs pre-requisites like the .NET Framework, Azure Active Directory Powershell Module and Microsoft Online Services Sign-In Assistant</para>
            </listItem>
            <listItem>
              <para>Downloads, installs and configures Dirsync (and in the future, AAD Sync), and enables it in your Azure tenant</para>
            </listItem>
            <listItem>
              <para>Configures either password sync or AD FS, depending on which sign-on option you prefer, and including any required configuration in Azure</para>
            </listItem>
            <listItem>
              <para>Checks to make sure it's all working!</para>
            </listItem>
          </list>
          <alert class="note">
            <para>Select the default option to include a starting an initial synchronization. You’ll need to customize the install to target a specific OU like we want to do.</para>
          </alert>
          <para>Select customize and password sync. Use an enterprise admin credentials and select password write-back on the next page.  At the end, uncheck the “Start the synchronization process as soon as the initial configuration completes”.</para>
          <para>
            <?Comment JJG: hybridlab content 2015-03-20T15:36:00Z  Id='4?>The next step in integrating Configuration Manager and Intune is to configure synchronization between the on-premises AD DS domain and Intune (i.e., Azure AD). Doing so allows users to sign in to Intune with their existing credentials. You configure AD DS synchronization by using Azure AD Connect.<?CommentEnd Id='4'
    ?></para>
          <alert class="note">
            <para>
              <?Comment JJG: hybridlab content 2015-03-20T15:36:00Z  Id='5?>The wizard determines whether the required prerequisites are installed. If any are missing, the wizard automatically downloads and installs them.<?CommentEnd Id='5'
    ?></para>
          </alert>
          <para />
          <para>
            <embeddedLabel>Verification steps:</embeddedLabel> Validate users have sync’d by...</para>
          <para>
            <?Comment JJG: hybridlab content 2015-03-20T15:36:00Z  Id='6?>The on-premises users are synchronized with Azure AD. Now, verify that synchronization is complete. You do this by signing in to Azure AD and visually verifying that the user accounts have been synchronized.<?CommentEnd Id='6'
    ?> Accounts synchronized from the on-premises AD DS domain have the value Local Active Directory in the SOURCED FROM column.</para>
          <para />
        </listItem>
        <listItem>
          <para>
            <embeddedLabel>
              <?Comment JJG: https://msdn.microsoft.com/en-us/library/azure/jj710171.aspx 2015-03-20T15:36:00Z  Id='7?>Filter users to sync<?CommentEnd Id='7'
    ?></embeddedLabel>. On the synchronization computer that you ran the Azure AD Connect Wizard on, launch the Synchronization Service Manager from the Start menu and then select Connectors. 2. With the on-premises AD name highlighted, select Properties from the Action menu. 3. In the connector Properties’ dialog box, select the Configure Directory Partitions option in the Connector Designer area and then click Containers to configure connection options. 4. After successfully authenticating using your on-premises credentials, you will see the Select Containers dialog box. From here you can clear all of the represented OUs except for the Cloud Service Users OU, as shown in Figure 4-11. 5. Click OK to close the properties dialog boxes and then use the Run options for the on-premises AD Connector to run the Full Import and Delta Synchronization actions </para>
          <para>Azure AD Sync’s job is to make sense of the objects in your on-premises AD DS and deliver them into Azure AD. Azure AD Sync takes the information stored in objects in your AD DS forests and projects them into a construct (actually a SQL Server DB) called the Metaverse. Azure AD Sync does this based on synchronization rules, both inbound and outbound in Connector Spaces.We are getting into the internal workings, but it’s important to understand what’s happening for a less “off the peg” scenario. Really, it’s all about matching and provisioning.When Azure AD Sync finds and object, it takes a look at what it already knows in the metaverse to see if the new object in the connector space matches anything already there. If it does, it will, based on some attributes, join the objects. If not it will either provision or disregard the object.</para>
          <para>
            <?Comment JJG: orfilter by a global security group instead? 2015-03-20T15:36:00Z  Id='8?>Windows_Intune_Users AD DS global security group<?CommentEnd Id='8'
    ?></para>
          <para>Go enable the “Azure AD Sync Scheduler” scheduled task and run it. </para>
          <para />
          <para>
            <embeddedLabel>Verification steps:</embeddedLabel> Go look in your account portal for users.</para>
          <para />
        </listItem>
        <?Comment JJG: doI need this? 2015-03-20T15:36:00Z  Id='9?>
        <listItem>
          <para>
            <embeddedLabel>Assign Microsoft Intune licenses to users</embeddedLabel> by editing the user account properties and adding them to the Microsoft Intune group.</para>
          <para>You must assign an Intune license to users who you want to enroll in Intune. You must activate their accounts in the Intune Account Portal to assign a license to them.</para>
          <para>Sign in to the Intune Account Portal by using your organizational account. Select the Licenses option under Subscriptions and then click the Assign now option to the right of Microsoft Intune.  Simply select the check box next to the synchronized users that you would like to activate and assign licenses for Microsoft Intune. After you select the users, use the Activate synced users option at the bottom of the portal page. It’s best to do this by geographical region if you can because you’ll need that information as part of activating them because services available vary by location. </para>
          <para>The results (user names and temporary passwords for users who have them) will be displayed on the next page. You can also send the results in email to yourself or someone else; enter the email addresses of up to five recipients separated by semicolons.  Ensure the Send email option is selected, verify the email address to send account information to, and then click Activate. </para>
          <alert class="note">
            <para>Now you should also configure Intune admins and other logins so you don’t have to log in with admin@____.onmicrosoft.com anymore (billing, global, password, service support, or user management administrator).</para>
          </alert>
          <para>
            <embeddedLabel>Verification steps:</embeddedLabel>. The activated user information is displayed on the Results page of the Activate Synced users wizard pages. Make sure that users are added to the Microsoft Intune security group. Back in the Intune admin console, the users should now all appear in the ungrouped users group.</para>
          <para>
            <?CommentEnd Id='9'
    ?>
          </para>
        </listItem>
        <listItem>
          <para>
            <embeddedLabel>Create a user collection for device enrollment</embeddedLabel>.</para>
          <para>
            <?Comment JJG: Hybrid lab content 2015-03-20T15:36:00Z  Id='10?>The next step in integrating Configuration Manager and Intune is to create a collection of users you will manage through Intune. This user collection identifies those who can enroll devices in Intune for subsequent management by Configuration Manager.<?CommentEnd Id='10'
    ?></para>
          <para>
            <embeddedLabel>Verification steps:</embeddedLabel> Go to the User Collections list in the Assets and Compliance workspace to see the Windows Intune Users user collection.</para>
          <para />
        </listItem>
        <listItem>
          <para>
            <embeddedLabel>Add Intune subscription</embeddedLabel>.</para>
          <?Comment JJG: Hybrid lab content 2015-03-20T15:36:00Z  Id='11?>
          <para>Integrating Configuration Manager and Intune is easy. The Create Windows Intune Subscription Wizard walks you through the process of collecting all the information necessary to integrate Configuration Manager and Intune.</para>
          <para>Setting an MDM authority specifies which configuration you use to manage mobile devices. In this lab, you are using Configuration Manager to manage mobile devices, so you will configure it as the MDM authority. If you were using Intune alone, you would use the Intune Admin Console to set Intune as the MDM authority. In either case, after you have configured this setting, you cannot change it later. When you set Configuration Manager as the MDM authority, you can no longer use the Intune Admin Console to manage the Intune subscription.</para>
          <para>On the General page, specify the user collection whose members can enroll their devices in MDM, provide company details, and then select the NYC site code.<?CommentEnd Id='11'
    ?></para>
          <para />
          <para>
            <embeddedLabel>Verification steps:</embeddedLabel> Configuration Manager–Intune integration is configured. You can verify it by checking that the MDM authority in Intune is set to Configuration Manager. You do that in the ADMIN workspace of the Intune Admin Console..</para>
          <para />
        </listItem>
        <listItem>
          <para>
            <embeddedLabel>Add intune connector</embeddedLabel>. Now, you need to add the Windows Intune Connector site system role to the Configuration Manager environment. You do that by using the Add Site System Roles Wizard, which collects all the information necessary to add the Windows Intune Connector site system role.</para>
          <alert class="note">
            <para>The Windows Intune connector site system role may only be installed on a central administration site or stand-alone primary site.</para>
          </alert>
          <para>dmpuploader.log and dmpdownloader.log https://technet.microsoft.com/en-us/library/hh427342.aspx#BKMK_WITLog </para>
          <para>
            <embeddedLabel>Verification steps:</embeddedLabel>.</para>
          <para />
        </listItem>
        <?Comment JJG: At this point you have completed the integration. Go to core docs for configuring MDMprereqsand enrolling devices into management. 2015-03-20T15:36:00Z  Id='12?>
        <listItem>
          <para>
            <embeddedLabel>Enable all extensions</embeddedLabel> it might take some time before any extensions for Microsoft Intune to appear in the Configuration manager console. Close and re-open the console to see them.</para>
          <para />
          <para>
            <embeddedLabel>Verification steps:</embeddedLabel> <placeholder>_____</placeholder>.</para>
          <para>
            <?CommentEnd Id='12'
    ?>
          </para>
        </listItem>
        <?Comment JJG: Do I need to talk about Cloud DPs here? 2015-03-20T15:36:00Z?>
      </list>
      <para>
        <embeddedLabel>Implementation complete</embeddedLabel>. After completing the implementation steps, all of the goals as listed in this solution are met as follows:</para>
      <list class="bullet">
        <listItem>
          <para>By integrating <token>wit_2</token> with the existing on-premises <token>cmshort</token> infrastructure, device management is extended to the cloud by building upon previous on-premises IT investments.</para>
        </listItem>
        <listItem>
          <para>Employees can use managed mobile devices of their choice, whether personal devices or company devices, to access corporate applications and data. These include PCs and mobile devices.</para>
        </listItem>
        <listItem>
          <para>IT can now manage PCs and mobile devices from a single administrator console. Managing devices includes setting security and compliance settings, gathering software and hardware inventory, and deploying software.</para>
        </listItem>
        <listItem>
          <para>IT can now deploy applications or web links based to managed mobile devices whether they are employee personal devices or devices owned by the company.</para>
        </listItem>
        <listItem>
          <para>IT can protect company data by wiping corporate data stored on the mobile device when it is lost, stolen, or retired from use.</para>
        </listItem>
      </list>
    </content>
  </section>
  <section>
    <title>See Also</title>
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
              <para>Learn more about Configuration Manager</para>
            </TD>
            <TD>
              <para>
                <externalLink>
                  <linkText>Introduction to Microsoft System Center 2012 R2 Configuration Manager TechNet Virtual Lab</linkText>
                  <linkUri>https://technet.microsoft.com/en-us/virtuallabs/bb467605.aspx</linkUri>
                </externalLink>
              </para>
              <para>
                <externalLink>
                  <linkText>TechNet Virtual Lab: Device Management with Microsoft System Center 2012 Configuration Manager</linkText>
                  <linkUri>https://vlabs.holsystems.com/vlabs/technet?eng=VLabs&amp;auth=external&amp;src=vlabs&amp;altadd=true&amp;labid=13538</linkUri>
                </externalLink>
              </para>
              <para>
                <externalLink>
                  <linkText>Manage Mobile Devices with Configuration Manager and Microsoft Intune</linkText>
                  <linkUri>https://technet.microsoft.com/en-us/library/jj884158.aspx</linkUri>
                </externalLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Learn about <token>wit_2</token></para>
            </TD>
            <TD>
              <para />
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Learn more about integrating <token>wit_2</token> and Configuration Manager</para>
            </TD>
            <TD>
              <para>
                <externalLink>
                  <linkText>Choose between using Microsoft Intune standalone and using it with Configuration Manager</linkText>
                  <linkUri>http://technet.microsoft.com/en-us/library/dn600286.aspx</linkUri>
                </externalLink> </para>
              <para>
                <externalLink>
                  <linkText>Manage Mobile Devices with Configuration Manager and Microsoft Intune</linkText>
                  <linkUri>https://technet.microsoft.com/en-us/library/jj884158.aspx</linkUri>
                </externalLink>
              </para>
              <para>
                <externalLink>
                  <linkText>Information shared between Microsoft Intune and System Center 2012 R2 Configuration Manager</linkText>
                  <linkUri>https://technet.microsoft.com/en-us/library/dn823755.aspx</linkUri>
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