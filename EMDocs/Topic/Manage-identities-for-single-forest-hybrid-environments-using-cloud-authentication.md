---
title: Manage identities for single-forest hybrid environments using cloud authentication
ms.custom: na
ms.reviewer: na
ms.service: active-directory
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a480f7a7-0904-4212-a09a-1381db57ef94
---
# Manage identities for single-forest hybrid environments using cloud authentication
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://clixdevr3.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction />
  <section address="BKMKStrategy">
    <title>How can this guide help you?</title>
    <content>
      <para>Corporate users want to be able to use applications that reside in the cloud from anywhere and any device, but they cannot because they do not have a way to authenticate.</para>
      <para>This guide provides a prescriptive, tested design about how to integrate an on-premises directory with a cloud directory so that users can easily access applications that reside in the cloud from anywhere and any device. This access is accomplished using cloud authentication. For an example of using on-premises authentication, see <externalLink><linkText>Manage identities for single-forest hybrid environments using on-premises authentication</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkID=389811</linkUri></externalLink>.</para>
      <para />
      <?Comment CL: “3rdParty” should be “Third-Party”; also, “…becausethecannot…” should be “…because they cannot…” 2014-09-05T14:15:00Z  Id='0?>
      <mediaLink>
        <image xlink:href="02d01d12-ba29-49c7-bb38-be512ba55159" />
        <?CommentEnd Id='0'
    ?>
      </mediaLink>
      <para />
      <para>
        <ui>In this solution guide:</ui>
      </para>
      <list class="nobullet">
        <listItem>
          <para>
            <link xlink:href="a480f7a7-0904-4212-a09a-1381db57ef94#scenarioproblemgoals">Scenario, problem statement, and goals</link>
          </para>
        </listItem>
        <listItem>
          <para>
            <link xlink:href="a480f7a7-0904-4212-a09a-1381db57ef94#Recommnedations">What is the recommended planning and design approach for this solution?</link>
          </para>
        </listItem>
        <listItem>
          <para>
            <link xlink:href="a480f7a7-0904-4212-a09a-1381db57ef94#whyrecommend">Why are we recommending this design?</link>
          </para>
        </listItem>
        <listItem>
          <para>
            <link xlink:href="a480f7a7-0904-4212-a09a-1381db57ef94#highlevelsteps">What are the high-level steps to implement this solution?</link>
          </para>
        </listItem>
      </list>
    </content>
  </section>
  <section address="scenarioproblemgoals">
    <title>Scenario, problem statement, and goals</title>
    <content>
      <para>This section describes the scenario, problem statement, and organizational goals that are useful as examples for this guide.</para>
    </content>
    <sections>
      <section>
        <title>Scenario</title>
        <content>
          <para>Your organization is a medium-sized corporation. Your organization’s sales staff works all over. When they make a sale, they are required to access a computer that is joined to the corporate network, either from a hub location or via VPN, and enter that sale in a custom application that runs on the corporate network.</para>
          <para> Because these sales are not always recorded in real time, it has made inventories difficult to manage. This has led to back orders and delays. Also, the sales staff has been complaining that they often do not have the ability to access the corporate network when they are at a customer’s place of business, and they would like to be able to enter the information via their tablets or smartphones.</para>
          <para> Your organization’s developers have recently developed a new customer relations management application that will make it easier for field sales agents to submit orders from any device that has Internet access.</para>
          <para>Your organization has decided to host this application in the cloud. This will allow the sales force to quickly enter a sale from their tablet or smartphone at the time of the sale without having to connect to the corporate network first. Your organization anticipates that this will greatly improve inventory management.</para>
        </content>
      </section>
      <section>
        <title>Problem statement</title>
        <content>
          <para>Your organization has determined that the new application will be hosted in Microsoft Azure. However, your organization currently does not have an authentication provider that will be able to authenticate the sales staff to the new application that will be hosted in Azure.</para>
          <para>The overall problem you want to solve is:</para>
          <para>
            <legacyBold>As a system architect or IT administrator, how can you provide users with a common identity when accessing resources that are on-premises and cloud-based? How can you manage these identities and keep the information synchronized across several environments without using excessive IT resources?</legacyBold>
          </para>
          <para>Providing access to this application will require the ability to authenticate the sales personnel with an authentication provider. Your organization wants to restrict access to the CRM application to the sales staff because they are currently the only employees who will need to access it.</para>
          <para>Your organization has looked at the options and agrees to allow cloud authentication against an instance of Azure AD. Your organization has determined this will be less expensive and easier to set up because currently they do not have any instances of Active Directory Federation Services (AD FS) on-premises. Also, because they have sales staff all over the world, the cloud authentication will provide a better experience, especially in areas of lower bandwidth. Your organization is concerned with the resources required to manage these identities—there is only one Active Directory administrator, and the administrator needs to be able to get this solution up and running quickly.</para>
          <para>Your organization’s developers have added the code to make this happen. It is now up to the Active Directory administrator to get his instance of Azure AD set up. The Active Directory administrator needs to be able to leverage the on-premises Active Directory to populate its instance of Azure AD. The Active Directory administrator must be able to do this quickly. He does not have time to clean up his current Active Directory environment or to recreate every user account in Azure. Also, your organization wants the sales staff to be able to use the same password they use when logging on to the corporate network. Your organization does not want the sales staff to have to remember multiple passwords.</para>
        </content>
      </section>
      <section>
        <title>Organizational goals</title>
        <content>
          <para>Your organization’s goals for its hybrid identity solution are:</para>
          <list class="bullet">
            <listItem>
              <?Comment CL: This bullet is unclear. What does it mean to manage identities with identities? 2014-09-05T14:17:00Z  Id='1?>
              <para>Ability to manage identities in the on-premises directory and in the cloud.<?CommentEnd Id='1'
    ?></para>
            </listItem>
            <listItem>
              <para>Ability to quickly set up synchronization with the on-premises single-forest directory.</para>
            </listItem>
            <listItem>
              <para>Ability to provide a cloud authentication provider.</para>
            </listItem>
            <listItem>
              <para>Ability to quickly set up synchronization with its on-premises directory.</para>
            </listItem>
            <listItem>
              <para>Ability to control who and what gets synchronized to the cloud.</para>
            </listItem>
            <listItem>
              <para>Ability to provide a secure sign-in experience no different than the one it has today.</para>
            </listItem>
            <listItem>
              <para>Ability to quickly get on-premises identity systems cleaned up and well managed so that they can be the source for the cloud.</para>
            </listItem>
          </list>
        </content>
      </section>
    </sections>
  </section>
  <section address="Recommnedations">
    <title>What is the recommended planning and design approach for this solution?</title>
    <content>
      <para>This section describes the solution design that addresses the problem described in the previous section and provides high-level planning considerations for this design.</para>
      <para>By using Azure AD, your organization is able to integrate the on-premises instance of Active Directory with the Azure AD instance. This instance will then be used to provide cloud authentication, as the following diagram shows. </para>
      <para />
      <?Comment CL: “3rdParty” should be “Third-Party” 2014-09-05T14:18:00Z  Id='2?>
      <mediaLink>
        <image xlink:href="410cb228-df2b-4701-9dd5-e642378b008b" />
        <?CommentEnd Id='2'
    ?>
      </mediaLink>
      <para />
      <para>The following table lists the elements that are part of this solution design and describes the reasons for each design choice.</para>
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
              <para>Password Sync</para>
            </TD>
            <TD>
              <para>A feature of the Azure Active Directory Sync tool that synchronizes user passwords from your on-premises Active Directory to Azure AD. For an overview of this technology, see <externalLink><linkText>Implement Password Synchronization</linkText><linkUri>http://technet.microsoft.com/library/dn246918.aspx</linkUri></externalLink>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>IdFix DirSync Error Remediation Tool</para>
            </TD>
            <TD>
              <para>Provides customers the ability to identify and remediate the majority of object synchronization errors in their Active Directory forests. For an overview of this technology, see <externalLink><linkText>IdFix DirSync Error Remediation Tool</linkText><linkUri>http://www.microsoft.com/download/details.aspx?id=36832</linkUri></externalLink>.</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>Password Sync is a feature of the Azure Active Directory Sync tool that synchronizes user passwords from your on-premises Active Directory to Azure AD. This feature enables your users to log in to their Azure AD services (such as Office 365, Intune, and CRM Online) using the same password they use to log in to your on-premises network. This will provide your users with the ability to have a secure sign-on that is the same as if they were signing in to the corporate network.</para>
      <para>The IdFix DirSync Error Remediation Tool can be used to perform discovery and remediation of identity objects and their attributes in an on-premises Active Directory environment in preparation for migration. This will allow you to quickly identify any issues that may occur with synchronization before you start synchronizing. Using this information, you can make changes to your environment so that you can avoid these errors.</para>
    </content>
  </section>
  <section address="whyrecommend">
    <title>Why are we recommending this design?</title>
    <content>
      <para>This design is recommended because it addresses the design goals of your organization. That is, there are two ways to provide authentication to Azure based resources: through cloud authentication or via on-premises authentication using a security token service<?Comment CL: What is an STS?This is the first time it’s mentioned in this topic. 2014-09-05T14:19:00Z  Id='3?>STS<?CommentEnd Id='3'
    ?>. </para>
      <para>Your organization’s first design goal is to have the ability to quickly set up synchronization with its on-premises instance of Active Directory. This design represents the quickest way to synchronize your on-premises Active Directory with Azure AD. </para>
      <para>Second, your organization wanted the ability to provide a secure sign-in experience no different than the one it has today. By using this design, users will sign in with the same user name and password they use today and the experience will be no different.</para>
    </content>
  </section>
  <section address="highlevelsteps">
    <title>What are the high-level steps to implement this solution?</title>
    <content>
      <para>You can use the steps in this section to implement the solution. Make sure to verify the correct deployment of each step before proceeding to the next step.</para>
      <list class="ordered">
        <listItem>
          <para>
            <legacyBold>Prepare for directory synchronization.</legacyBold>
          </para>
          <para>Verify system requirements, create the right permissions, and allow for performance considerations. For more information, see <externalLink><linkText>Prepare for directory synchronization</linkText><linkUri>http://technet.microsoft.com/library/jj151831.aspx</linkUri></externalLink>.
After you complete this step, verify you have a completed worksheet showing your selected solution design options.</para>
        </listItem>
        <listItem>
          <para>
            <legacyBold>Activate directory synchronization.</legacyBold>
          </para>
          <para>Activate directory synchronization for your company. For more information, see <externalLink><linkText>Activate directory synchronization</linkText><linkUri>http://technet.microsoft.com/library/dn144766.aspx</linkUri></externalLink>. 
After you complete this step, verify you have the features configured.</para>
        </listItem>
        <listItem>
          <para>
            <legacyBold>Set up your directory synchronization computer.</legacyBold>
          </para>
          <para>Install the Windows Azure AD Synchronization Tool. If you’ve already done so, learn how to upgrade, uninstall, or move it to another computer. For more information, see <externalLink><linkText>Set up your directory sync computer</linkText><linkUri>http://technet.microsoft.com/library/dn144767.aspx</linkUri></externalLink>. After you complete this step, verify you have the features configured.</para>
        </listItem>
        <listItem>
          <para>
            <legacyBold>Synchronize your directories.</legacyBold>
          </para>
          <para>Perform an initial sync and verify that the data synchronized successfully. You will also learn how to configure the Azure AD Synchronization Tool to set up recurring synchronization and how to force directory synchronization. For more information, see <externalLink><linkText>Use the Configuration Wizard to sync your directories</linkText><linkUri>http://technet.microsoft.com/library/dn144765.aspx</linkUri></externalLink>. After you complete this step, verify you have the features configured.</para>
        </listItem>
        <listItem>
          <para>
            <legacyBold>Activate synced users.</legacyBold>
          </para>
          <para>Activate the users in the Office 365 portal before they can use the services to which you have subscribed. This involves assigning them a license to use Office 365. You can do this individually or in bulk. For more information, see <externalLink><linkText>Activate synced users</linkText><linkUri>http://technet.microsoft.com/library/hh967617.aspx</linkUri></externalLink>. After you complete this step, verify you have the features configured. Note that this is an optional step and is required only if you are using Office 365.  </para>
        </listItem>
        <?Comment CL: This is the only step in this section with a link to click. Should it have one? 2014-01-09T12:13:00Z  Id='4?>
        <listItem>
          <para>
            <legacyBold>Verify the solution.</legacyBold>
          </para>
          <para>After the users have been synchronized, test logging in to <externalLink><linkText>http://myapps.microsoft.com</linkText><linkUri>http://myapps.microsoft.com</linkUri></externalLink>. If you have Office 365 applications, you will see them here. A regular user can log in here without needing an Azure subscription.<?CommentEnd Id='4'
    ?></para>
        </listItem>
      </list>
    </content>
  </section>
  <section>
    <title>See also</title>
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
              <para>Product evaluation/Getting started</para>
            </TD>
            <TD>
              <?Comment CL: Both of these links point to a placeholder as of 010914. 2014-01-09T12:04:00Z  Id='5?>
              <para>
                <externalLink>
                  <linkText>Test Lab Guide: Creating a Windows Azure AD and Windows Server AD Environment using DirSync with Password Sync</linkText>
                  <linkUri>http://go.microsoft.com/fwlink/?LinkId=389808</linkUri>
                </externalLink>
              </para>
              <para>
                <externalLink>
                  <linkText>Test Lab Guide: Creating a Windows Azure AD and Windows Server AD Environment with Federation (SSO)</linkText>
                  <linkUri>http://go.microsoft.com/fwlink/?LinkId=389809</linkUri>
                </externalLink>
                <?CommentEnd Id='5'
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
                  <linkText>AD FS Design Guide in Windows Server 2012</linkText>
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
                  <linkText>Windows Server 2012 R2 AD FS Deployment Guide</linkText>
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
                  <linkText>AD FS Operations</linkText>
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
                  <linkText>Windows Azure Forums</linkText>
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
                  <linkText>Checklist: Use AD FS to implement and manage single sign-on</linkText>
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
                <?Comment CL: This link goes to a “Content not found” page. 2014-01-09T12:10:00Z  Id='7?>
                <externalLink>
                  <linkText>Manage mobile devices and PCs by migrating to Configuration Manager with Windows Intune</linkText>
                  <linkUri>http://technet.microsoft.com/library/dn582037.aspx</linkUri>
                </externalLink>
                <?CommentEnd Id='7'
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