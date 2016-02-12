---
title: Manage identities for single-forest hybrid environments using on-premises authentication
ms.custom: na
ms.prod: windows-server-2012-r2
ms.reviewer: na
ms.suite: na
ms.technology: 
  - active-directory-federation-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d71ba67e-3862-48c1-b522-7667416dae1c
---
# Manage identities for single-forest hybrid environments using on-premises authentication
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://clixdevr3.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction />
  <section address="BKMKStrategy" DoNotNumber="false">
    <title>How can this guide help you?</title>
    <content>
      <para>Corporate users want to be able to use applications that reside in the cloud from anywhere and any device, but they cannot because they do not have a way to authenticate. Corporate IT wants to be able to allow users the ability to authenticate to these cloud applications, and it also wants the ability in real time to control who can access these applications.</para>
      <para>This guide provides a prescriptive, tested design about how to integrate an on-premises directory with a cloud directory so that users can easily access applications that reside in the cloud from anywhere and any device. This is accomplished using on-premises authentication. For an example of using cloud authentication, see <externalLink><linkText>Manage identities for single-forest hybrid environments using cloud authentication</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkID=389810</linkUri></externalLink>.</para>
      <para />
      <mediaLink>
        <image xlink:href="090d1b6a-39ed-44bf-aa55-b63c884515e6" />
      </mediaLink>
      <para />
      <para>
        <ui>In this solution guide:</ui>
      </para>
      <list class="nobullet">
        <listItem>
          <para>
            <link xlink:href="d71ba67e-3862-48c1-b522-7667416dae1c#BKMKscenarioproblemgoals">Scenario, problem statement, and goals</link>
          </para>
        </listItem>
        <listItem>
          <para>
            <link xlink:href="d71ba67e-3862-48c1-b522-7667416dae1c#BKMKRecommnedations">What is the recommended planning and design approach for this solution?</link>
          </para>
        </listItem>
        <listItem>
          <para>
            <link xlink:href="d71ba67e-3862-48c1-b522-7667416dae1c#whyrecommenddesign">Why are we recommending this design?</link>
          </para>
        </listItem>
        <listItem>
          <para>
            <link xlink:href="d71ba67e-3862-48c1-b522-7667416dae1c#BKMKhighlevelsteps">What are the high-level steps to implement this solution?</link>
          </para>
        </listItem>
      </list>
    </content>
  </section>
  <section address="BKMKscenarioproblemgoals">
    <title>Scenario, problem statement, and goals</title>
    <content>
      <para>This section describes the scenario, problem statement, and goals for an example organization.</para>
    </content>
    <sections>
      <section>
        <title>Scenario</title>
        <content>
          <para>Your organization is a large-sized corporation with offices all over the world, including in North and South America, Europe, and Asia. The research and development (R&amp;D) teams work primarily in North America and Europe. They develop the formulas that will be used by the manufacturing centers that are located primarily in Asia.</para>
          <para>The R&amp;D teams work closely together when developing new formulas or improving upon existing ones. This is done by running similar, standardized tests in facilities in North America and Europe, and then sharing the results. The results are then made final and new formulas are developed. These formulas are considered trade secrets and are patented. After this process is completed, the formulas are sent to the manufacturing facilities to begin production.</para>
          <para>Currently, if a member of the R&amp;D team wants to share results with counterparts in another part of the company or wants to send a formula to one of the plants in Asia, the team uses the Encrypting File System (EFS) to encrypt and email the files. The person on the other end then decrypts the files.</para>
          <para>Your organization has several issues with the current process:</para>
          <list class="bullet">
            <listItem>
              <para>
                <legacyBold>Privacy:</legacyBold> Data is transferred via email, and although it is encrypted, it is still susceptible to hacking over the Internet. Also, many employees are accessing email from their own devices and there is no guarantee that those devices are secure.</para>
            </listItem>
            <listItem>
              <para>
                <legacyBold>Integrity:</legacyBold> The EFS Certificate used to encrypt files must be exported and sent to the destination. Users are using email to send those certificates, which could violate the integrity of the certificate.</para>
            </listItem>
            <listItem>
              <para>
                <legacyBold>Confidentiality:</legacyBold> The same certificate is often used for encrypting the test results and the formulas. Employees at the manufacturing plants will have the ability to decrypt these results, if they get a copy of them by mistake.</para>
            </listItem>
          </list>
          <para>In order to address these concerns, your organization has decided it would like to set up Office 365 SharePoint in the cloud and use this as its portal for sharing test results and formulas. However, your organization wants to use its on-premises Active Directory as the authentication provider and does not want to use cloud authentication.</para>
        </content>
      </section>
      <section>
        <title>Problem statement</title>
        <content>
          <para>Your organization currently has an authentication provider, the on-premises Active Directory, but this provider is currently unable to authenticate employees to the new Office 365 SharePoint sites that will be hosted in Azure.</para>
          <para>The overall problem your organization wants to solve is:</para>
          <para>
            <legacyBold>As a system architect or IT administrator, how can you provide users with a common identity when accessing resources that are on-premises and cloud-based? And how can you manage these identities and keep the information synchronized across several environments without using excessive IT resources?</legacyBold>
          </para>
          <para>Providing access to your organization’s SharePoint sites will require the ability to authenticate the employees with an authentication provider, the on-premises instance of Active Directory. Also, your organization wants to restrict access to just the R&amp;D and manufacturing employees who require access to the sites. They are currently the only ones who will need to access the sites.</para>
          <para>Having looked into the options, you have determined that you can leverage your existing instance of Active Directory Federation Services (AD FS) to use on-premises authentication with Azure. Your organization set up AD FS several years ago. This will save time and money because the IT staff is already familiar with using AD FS.</para>
          <para>Management has authorized the purchase of Office 365 and Azure subscriptions. It is now up to the Active Directory administrators to set up their instance of Azure AD and federate it with the on-premises Active Directory.</para>
          <para>The Active Directory administrators need to be able to leverage the on-premises Active Directory to populate the instance of Azure AD. The Active Directory administrators must be able to do this quickly. Next, the Active Directory administrators need to federate the on-premises instance of Active Directory with Azure AD. Also, your organization wants employees who will be accessing the SharePoint sites to have a true single sign-on experience and only be able to access the sites when logged on to the corporate network. Your organization does not want these sites to be accessed from external computers or devices. Your organization would like the ability to quickly disable a user in the event of a separation so that the user cannot access the SharePoint site after their account has been disabled. Finally, your organization would like to be able to customize the sign-in page so that users know they are logging in to a corporate site.</para>
        </content>
      </section>
      <section>
        <title>Organizational goals</title>
        <content>
          <para>Your organization’s goals for its hybrid identity solution are:</para>
          <list class="bullet">
            <listItem>
              <para>Ability to manage identities in the on-premises directory with identities in the cloud.</para>
            </listItem>
            <listItem>
              <para>Ability to quickly set up synchronization with the on-premises single-forest directory.</para>
            </listItem>
            <listItem>
              <para>Ability to provide on-premises authentication directory.</para>
            </listItem>
            <listItem>
              <para>Ability to control who and what gets synchronized to the cloud.</para>
            </listItem>
            <listItem>
              <para>Ability to offer single sign-on (SSO). Alerts are received if either synchronization or SSO is down.</para>
            </listItem>
            <listItem>
              <para>Ability to restrict access to only R&amp;D and manufacturing users who are signing in from a secure, on-premises location.</para>
            </listItem>
            <listItem>
              <para>Ability to prevent real-time user access to cloud resources in the event of a separation. </para>
            </listItem>
            <listItem>
              <para>Ability to quickly get on-premises identity systems cleaned up and well managed so that they can be the source for the cloud.</para>
            </listItem>
            <listItem>
              <para>Ability to customize the sign-in page so that it presents a corporate identity.</para>
            </listItem>
          </list>
        </content>
      </section>
    </sections>
  </section>
  <section address="BKMKRecommnedations">
    <title>What is the recommended planning and design approach for this solution?</title>
    <content>
      <para>This section describes the solution design that addresses the problem described in the previous section and provides high-level planning considerations for this design.</para>
      <para>By using Azure AD, your organization is able to integrate the on-premises instance of Active Directory with the Azure AD instance. This instance will then be used to re-direct users to the AD FS sign-in page where they will be issued a token that is then presented to Azure AD and authentication granted.</para>
      <para />
      <mediaLink>
        <image xlink:href="90563daf-87c7-40ff-9720-9c3c5ead5799" />
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
              <para>Azure Active Directory Sync tool</para>
            </TD>
            <TD>
              <para>Is used to synchronize on-premises directory objects with Azure AD. For an overview of this technology, see <externalLink><linkText>Directory synchronization roadmap</linkText><linkUri>http://technet.microsoft.com/library/hh967642.aspx</linkUri></externalLink>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Active Directory Federation Services</para>
            </TD>
            <TD>
              <para>A feature of Windows Server 2012 R2 that is a security token service (STS) that uses Active Directory as its identity store. The STS in <?Comment CL: Do we mean AD FS here? 2014-01-09T10:50:00Z  Id='36?>AD FS <?CommentEnd Id='36'
    ?>can issue security tokens to the caller using various protocols, including OAuth, WS-Trust, WS-Federation, and Security Assertion Markup Language (SAML) 2.0.  For an overview of this technology, see <externalLink><linkText>Active Directory Federation Services Overview</linkText><linkUri>http://technet.microsoft.com/library/hh831502.aspx</linkUri></externalLink>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>IdFix DirSync Error Remediation Tool</para>
            </TD>
            <TD>
              <para>Provides customers with the ability to identify and remediate the majority of object synchronization errors in their Active Directory forests. For an overview of this technology, see <externalLink><linkText>IdFix DirSync Error Remediation Tool</linkText><linkUri>http://www.microsoft.com/download/details.aspx?id=36832</linkUri></externalLink>.</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <?Comment CL: The first and third paragraphs correspond to the table just above them. The second paragraph is not mentioned in the table—why is it mentioned here? Also, these paragraphs’ order should match the order in which the subjects appear in the table. 2014-01-09T11:35:00Z  Id='39?>
      <para>AD FS is a feature of Windows Server 2012 R2 that allows federation between your on-premises Active Directory and Azure AD. This feature enables users to log in to their Azure AD services (such as Office 365, Intune, and CRM Online) by using an SSO experience. This will provide your users with the ability to have SSO that uses your on-premises Active Directory instance as the authentication provider.</para>
      <para>The IdFix DirSync Error Remediation Tool can be used to perform discovery and remediation of identity objects and their attributes in an on-premises Active Directory environment in preparation for migration. This will allow you to quickly identify any issues that may occur with synchronization before you start synchronizing. Using this information, you can make changes to your environment so that you can avoid these errors.<?CommentEnd Id='39'
    ?></para>
    </content>
  </section>
  <section address="whyrecommenddesign">
    <title>Why are we recommending this design?</title>
    <content>
      <para>This design is recommended because it addresses the design goals of your organization. That is, there are two ways to provide authentication to Azure based resources: through cloud authentication or on-premises authentication using an STS. </para>
      <para>One of your organization’s main concerns is that they have the ability in real time to stop a user who may have been separated from the corporation from accessing the cloud-based resources. There is up to a three-hour lag associated with using the Azure Active Directory Synchronization Tool and cloud authentication. That is, if you disable a user account on-premises, it may take up to three hours for that change to appear in Azure. This is not the case if the user must come back to the on-premises environment and authenticate. If a user account is disabled on-premises, that user will not be able to receive a token and will not be authorized to access the cloud resources.</para>
      <para>Your organization wants the ability to provide SSO. This can be accomplished only by federating your on-premises instance of Active Directory with Azure AD.</para>
      <para>The ability to customize the sign-in page is available only by using AD FS and AD FS customization.</para>
    </content>
  </section>
  <section address="BKMKhighlevelsteps">
    <title>What are the high-level steps to implement this solution?</title>
    <content>
      <para>You can use the steps in this section to implement the solution. Make sure to verify the correct deployment of each step before proceeding to the next step.</para>
      <list class="ordered">
        <listItem>
          <para>
            <legacyBold>Prepare for single sign-on (SSO)</legacyBold>
          </para>
          <para>To prepare, you must make sure your environment meets the requirements for SSO and verify that your Active Directory and Azure AD tenant are set up in a way that is compatible with SSO requirements. For more information, see <externalLink><linkText>Prepare for single sign-on</linkText><linkUri>http://technet.microsoft.com/en-us/library/jj151786.aspx</linkUri></externalLink>.</para>
        </listItem>
        <listItem>
          <para>
            <legacyBold>Set up your on-premises security token service—AD FS</legacyBold>
          </para>
          <para>After you have prepared your environment for SSO, you will need to set up a new on-premises AD FS infrastructure to provide your local and remote Active Directory users with SSO access to the cloud service. If you currently have AD FS in your production environment, you can use it for SSO deployment rather than setting up a new infrastructure as long as it is supported by Azure AD. For more information about how to get started with setting up an AD FS STS, follow the steps provided in <externalLink><linkText>Checklist: Use AD FS to implement and manage single sign-on.</linkText><linkUri>http://technet.microsoft.com/en-us/library/jj205462.aspx</linkUri></externalLink></para>
        </listItem>
        <listItem>
          <para>
            <legacyBold>Install Windows PowerShell for single sign-on with AD FS</legacyBold>
          </para>
          <para>The Azure AD Module for Windows PowerShell is a download for managing your organization’s data in Azure AD. This module installs a set of cmdlets in Windows PowerShell that you run to set up SSO access to Azure AD and in turn to all of the cloud services to which you are subscribed. For more information, see <externalLink><linkText>Install Windows PowerShell for single sign-on with AD FS</linkText><linkUri>http://technet.microsoft.com/library/jj151814.aspx</linkUri></externalLink>.</para>
        </listItem>
        <listItem>
          <para>
            <legacyBold>Set up a trust between AD FS and Azure AD</legacyBold>
          </para>
          <para>You need to establish a trust between Azure AD and your on-premises Active Directory. Each domain that you want to federate must either be added as a single sign-on domain or converted to be a single sign-on domain from a standard domain. Adding or converting a domain sets up a trust between AD FS and Azure AD. For more information, see <externalLink><linkText>Set up a trust between AD FS and Azure AD</linkText><linkUri>http://technet.microsoft.com/library/jj205461.aspx</linkUri></externalLink>.</para>
        </listItem>
        <listItem>
          <para>
            <legacyBold>Prepare for directory synchronization</legacyBold>
          </para>
          <para>Verify system requirements, create the right permissions, and allow for performance considerations. For more information, see <externalLink><linkText>Prepare for directory synchronization</linkText><linkUri>http://technet.microsoft.com/library/jj151831.aspx</linkUri></externalLink>.
After you complete this step, verify you have a completed worksheet showing your selected solution design options.</para>
        </listItem>
        <listItem>
          <para>
            <legacyBold>Activate directory synchronization</legacyBold>
          </para>
          <para>Activate directory synchronization for your company. For more information, see <externalLink><linkText>Activate directory synchronization</linkText><linkUri>http://technet.microsoft.com/library/dn144766.aspx</linkUri></externalLink>. 
After you complete this step, verify you have the features configured.</para>
        </listItem>
        <listItem>
          <para>
            <legacyBold>Set up your directory synchronization computer</legacyBold>
          </para>
          <para>Install the Azure AD Synchronization Tool. If you’ve already done so, learn how to upgrade, uninstall, or move it to another computer. For more information, see <externalLink><linkText>Set up your directory sync computer</linkText><linkUri>http://technet.microsoft.com/library/dn144767.aspx</linkUri></externalLink>. After you complete this step, verify you have the features configured.</para>
        </listItem>
        <listItem>
          <para>
            <legacyBold>Synchronize your directories</legacyBold>
          </para>
          <para>Perform an initial sync and verify that the data synchronized successfully. You will also learn how to configure the Azure AD Synchronization Tool to set up recurring synchronization and how to force directory synchronization. For more information, see <externalLink><linkText>Use the Configuration Wizard to sync your directories</linkText><linkUri>http://technet.microsoft.com/library/dn144765.aspx</linkUri></externalLink>. After you complete this step, verify you have the features configured.</para>
        </listItem>
        <listItem>
          <para>
            <legacyBold>Activate synced users</legacyBold>
          </para>
          <para>Activate the users in the Office 365 portal before they can use the services to which you have subscribed. This involves assigning them a license to use Office 365. You can do this individually or in bulk. For more information, see <externalLink><linkText>Activate synced users</linkText><linkUri>http://technet.microsoft.com/library/hh967617.aspx</linkUri></externalLink>. After you complete this step, verify you have the features configured. Note that this is an optional step and is required only if you are using Office 365.  </para>
        </listItem>
        <?Comment CL: This is the only step without a link. Should it have one? 2014-01-09T10:53:00Z  Id='59?>
        <listItem>
          <para>
            <legacyBold>Verify the solution.</legacyBold>
          </para>
          <para>After the users have been synchronized, test logging in to http://myapps.microsoft.com. You should be redirected to the AD FS sign-in page. After you have signed in and AD FS has authenticated the user, the user will be redirected back to http://myapps.microsoft.com. If you have Office 365 applications, you will see them here. A regular user can log in here without needing an Azure subscription.<?CommentEnd Id='59'
    ?></para>
        </listItem>
      </list>
    </content>
  </section>
  <section>
    <title>See Also</title>
    <content>
      <para />
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <tbody>
          <tr>
            <TD>
              <para>
                <legacyBold>Content type</legacyBold>
              </para>
            </TD>
            <TD>
              <para>
                <legacyBold>References</legacyBold>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Product evaluation/ Getting started</para>
            </TD>
            <TD>
              <para>
                <?Comment CL: This link is pointing to a placeholder URL as of 010914. 2014-01-09T10:53:00Z  Id='74?>
                <externalLink>
                  <linkText>Test Lab Guide: Creating an Azure AD and Windows Server AD Environment Using DirSync with Password Sync</linkText>
                  <linkUri>http://go.microsoft.com/fwlink/?LinkId=389808</linkUri>
                </externalLink>
                <?CommentEnd Id='74'
    ?> </para>
              <para>
                <?Comment CL: This link is pointing to a placeholder URL as of 010914. 2014-01-09T10:54:00Z  Id='75?>
                <externalLink>
                  <linkText>Test Lab Guide: Creating an Azure AD and Windows Server AD Environment with Federation (SSO)</linkText>
                  <linkUri>http://go.microsoft.com/fwlink/?LinkId=389809</linkUri>
                </externalLink>
                <?CommentEnd Id='75'
    ?>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Planning and design</para>
            </TD>
            <TD>
              <para>
                <externalLink>
                  <linkText>AD FS Design Guide in Windows Server 2012</linkText>
                  <linkUri>http://technet.microsoft.com/en-us/library/dd807036.aspx</linkUri>
                </externalLink>
              </para>
              <para>
                <externalLink>
                  <linkText>Directory integration</linkText>
                  <linkUri>http://technet.microsoft.com/library/jj573653.aspx</linkUri>
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
                <externalLink>
                  <linkText>Windows Server 2012 R2 AD FS Deployment Guide</linkText>
                  <linkUri>http://technet.microsoft.com/library/dn486820.aspx</linkUri>
                </externalLink>
              </para>
              <para>
                <externalLink>
                  <linkText>Directory synchronization roadmap</linkText>
                  <linkUri>http://technet.microsoft.com/library/hh967642.aspx</linkUri>
                </externalLink>
              </para>
              <para>
                <externalLink>
                  <linkText>Single sign-on roadmap</linkText>
                  <linkUri>http://technet.microsoft.com/library/hh967643.aspx</linkUri>
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
                <externalLink>
                  <linkText>AD FS Operations</linkText>
                  <linkUri>http://technet.microsoft.com/library/dn448847.aspx</linkUri>
                </externalLink>
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
                  <linkText>Troubleshoot directory synchronization</linkText>
                  <linkUri>http://technet.microsoft.com/library/jj151787.aspx</linkUri>
                </externalLink>
              </para>
              <para>
                <externalLink>
                  <linkText>Forefront Identity Manager Forum</linkText>
                  <linkUri>http://social.technet.microsoft.com/Forums/home?forum=ilm2</linkUri>
                </externalLink>
              </para>
              <para>
                <externalLink>
                  <linkText>Azure Forums</linkText>
                  <linkUri>http://social.msdn.microsoft.com/Forums/windowsazure/home?category=windowsazureplatform%2Cazuremarketplace%2Cwindowsazureplatformctp</linkUri>
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
                  <linkText>Checklist: Use AD FS to implement and manage single sign-on</linkText>
                  <linkUri>http://technet.microsoft.com/en-us/library/jj205462.aspx</linkUri>
                </externalLink>
              </para>
              <para>
                <externalLink>
                  <linkText>Determine which directory integration scenario to use</linkText>
                  <linkUri>http://technet.microsoft.com/library/jj573649.aspx</linkUri>
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
                  <linkText>Cloud Identity</linkText>
                  <linkUri>http://www.cloudidentity.com/blog/</linkUri>
                </externalLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Related solutions</para>
            </TD>
            <TD>
              <para>
                <?Comment CL: This link goes to a “Content not found” page. 2014-01-09T10:56:00Z  Id='76?>
                <externalLink>
                  <linkText>Streamlined management for mobile devices and computers in a hybrid environment</linkText>
                  <linkUri>http://technet.microsoft.com/library/dn582037.aspx</linkUri>
                </externalLink>
                <?CommentEnd Id='76'
    ?>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Related technologies</para>
            </TD>
            <TD>
              <para>
                <externalLink>
                  <linkText>Azure</linkText>
                  <linkUri>http://www.windowsazure.com/</linkUri>
                </externalLink>
              </para>
              <para>
                <externalLink>
                  <linkText>Forefront Identity Manager 2010 R2</linkText>
                  <linkUri>http://www.microsoft.com/server-cloud/products/forefront-identity-manager/default.aspx</linkUri>
                </externalLink>
              </para>
              <para>
                <externalLink>
                  <linkText>Active Directory Federation Services</linkText>
                  <linkUri>http://technet.microsoft.com/library/cc772128(v=WS.10).aspx</linkUri>
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