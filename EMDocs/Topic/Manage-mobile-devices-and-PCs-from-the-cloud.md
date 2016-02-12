---
title: Manage mobile devices and PCs from the cloud
ms.custom: na
ms.reviewer: na
ms.service: microsoft-Intune
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bbc3eece-adc2-446a-89a3-55ae59e24d7c
author: Jeffgilb
---
# Manage mobile devices and PCs from the cloud
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://clixdevr3.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>
      <embeddedLabel>How can this guide help you?</embeddedLabel> As a small business IT professional, you can use this solution guide to understand the solution design and implementation steps that we recommend to manage mobile devices and computers via the cloud and let people in your company use the devices they choose to access applications and data. </para>
    <para>This solution guide describes how a small business with no local servers can extend their current infrastructure to the cloud to support mobile device management and the "<externalLink><linkText>bring your own device (BYOD)</linkText><linkUri>http://technet.microsoft.com/library/dn646978.aspx</linkUri></externalLink>" demand to use personal mobile devices and computers at work to access company resources. In addition to managing mobile devices and computers via the cloud, this solution also describes how you can let people in the company use the devices they choose to access applications and data while, at the same time, enforcing company policies on those devices.</para>
    <para>
      <embeddedLabel>In this solution guide:</embeddedLabel>
    </para>
    <list class="bullet">
      <listItem>
        <para>Scenario, problem statement, and goals</para>
      </listItem>
      <listItem>
        <para>Recommended design for this solution</para>
      </listItem>
      <listItem>
        <para>Steps to implement this solution</para>
      </listItem>
    </list>
    <para>The following diagram illustrates the problem that this solution guide is addressing.</para>
    <para>
      <embeddedLabel>Users accessing company data and applications by using unmanaged mobile devices and computers.</embeddedLabel>
    </para>
    <mediaLink>
      <image xlink:href="789f3b22-31c7-435d-b100-42d32fdf3f62" />
    </mediaLink>
    <para />
  </introduction>
  <section>
    <title>Scenario, problem statement, and goals</title>
    <content>
      <para>This section describes the scenario, current problem, and goals you might have. After reviewing this solution to the problem of users accessing company applications and data from unmanaged mobile devices and computers, you can decide whether it meets your needs, or if you need to adjust it for your particular business environment.</para>
    </content>
    <sections>
      <sectionSimple>
        <para>
          <embeddedLabel>Scenario</embeddedLabel>
        </para>
        <para>In this solution, a small business is looking for a cloud-only solution to manage mobile devices and computers. This solution is best for small businesses because they typically: </para>
        <list class="bullet">
          <listItem>
            <para>Have very small IT support teams.</para>
          </listItem>
          <listItem>
            <para>Rely on free, web-based email for employee communications.</para>
          </listItem>
          <listItem>
            <para>Have no on-premises servers.</para>
          </listItem>
          <listItem>
            <para>Do not use management software for mobile devices or computers.</para>
          </listItem>
        </list>
      </sectionSimple>
      <sectionSimple>
        <para>
          <embeddedLabel>Problem statement</embeddedLabel>
        </para>
        <para>The overall problem to solve is:</para>
        <para>
          <embeddedLabel>Without on-premise servers, small businesses can struggle to manage mobile devices and PCs and protect company data</embeddedLabel>. Small business employees are mobile and expect to be able to consistently and easily access the applications they need to get their jobs done. Additionally, they need to get their work done wherever they might be on whatever device they might be using. </para>
      </sectionSimple>
      <sectionSimple>
        <para>
          <embeddedLabel>Goals</embeddedLabel>
        </para>
        <para>Based on the scenario and problem statement, a management solution for mobile devices and PCs is needed that meets the following goals:</para>
        <list class="bullet">
          <listItem>
            <para>Effectively manages employees’ mobile devices and computers from a single administration console regardless of whether or not they are company-owned or employee-owned. Managing mobile devices and computers includes setting security and compliance settings, gathering and maintaining a software and hardware inventory, and deploying software. </para>
          </listItem>
          <listItem>
            <para>Helps prevent malware infections and potentially unwanted software from infecting computers that connect to company assets. </para>
          </listItem>
          <listItem>
            <para>Helps protect company data by erasing company data stored on mobile devices when they are lost, stolen, or retired from use.</para>
          </listItem>
          <listItem>
            <para>Provides a company portal to enable employees to enroll their own devices, access licensed applications, and contact support.</para>
          </listItem>
          <listItem>
            <para>Eliminates the need for on-premises servers.</para>
          </listItem>
        </list>
      </sectionSimple>
    </sections>
  </section>
  <section>
    <title>What is the recommended design for this solution?</title>
    <content>
      <para>The solution we recommend for companies such as the ones described earlier is to use <token>wit_2</token> to manage both company owned and employee owned mobile devices and PCs. Administrators can simply and easily meet their basic mobile device and PC management needs using the <token>wit_2</token> admin portal and deploy applications or provide end user self-service using the <token>wit_2</token> company portal.</para>
      <para>Watch this demo video to learn how easy it is to get started with a free trial of <token>wit_2</token> and manage your first device:</para>
      <mediaLink>
        <image xlink:href="44449e46-f5c6-440d-9dfc-4ebede07b685" />
        <video player="sp_generic_640X360" videotype="single" videoid="a10cccb3-3a88-4b80-9b93-8896c8541dba" />
      </mediaLink>
      <para />
    </content>
    <sections>
      <section>
        <title>Why are we recommending this design?</title>
        <content>
          <para>
            <token>wit_2</token> is a cloud-based management solution for computers and mobile devices that requires no on-premises hardware and it does not matter if those computers and mobile devices are employee-owned or company owned. Using <token>wit_2</token>, you can secure your company's information assets and manage user access to company resources and licensed software that they can install themselves using the company portal. </para>
          <alert class="note">
            <para>This solution describes how to use <token>wit_2</token> in the simplest scenario supported for a stand-alone, cloud-only configuration with no local servers. However, <token>wit_2</token> can also be <externalLink><linkText>used in conjunction with System Center 2012 Configuration Manager</linkText><linkUri>http://technet.microsoft.com/library/dn646980.aspx</linkUri></externalLink> or in addition to <token>sccmshortname</token> to provide unified device management for both on-premises and mobile device management needs.</para>
          </alert>
          <para>The following diagram illustrates how to use <token>wit_2</token> to manage mobile devices and computers without an on-premises infrastructure.</para>
          <para>
            <embeddedLabel>Using <token>wit_2</token> to manage mobile devices and PCs</embeddedLabel>
          </para>
          <mediaLink>
            <image xlink:href="536c1227-ff30-4981-9a02-6d7afda93aee" />
          </mediaLink>
          <para />
          <para>The following table lists the elements that are part of this solution design and describes why they’re included in the design. There is also <externalLink><linkText>additional planning information</linkText><linkUri>http://technet.microsoft.com/library/dn646966.aspx</linkUri></externalLink> for implementing <token>wit_2</token> in the Documentation Library for <token>wit_2</token> on TechNet.</para>
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
                    <token>wit_2</token>
                  </para>
                </TD>
                <TD>
                  <list class="bullet">
                    <listItem>
                      <para>
                        <token>wit_2</token> is a cloud-based management solution.</para>
                    </listItem>
                    <listItem>
                      <para>It lets you manage Windows computers and mobile devices including iOS, Android, Windows RT and Windows Phone devices.</para>
                    </listItem>
                    <listItem>
                      <para>It helps you to manage and secure your company's information assets.</para>
                    </listItem>
                  </list>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>Users</para>
                </TD>
                <TD>
                  <list class="bullet">
                    <listItem>
                      <para>You can easily manage license usage and access to resources by <externalLink><linkText>creating Microsoft Intune users</linkText><linkUri>http://technet.microsoft.com/library/dn646983.aspx#BKMK_AddUsers</linkUri></externalLink>.</para>
                    </listItem>
                    <listItem>
                      <para>You can also <externalLink><linkText>assign administrative rights</linkText><linkUri>http://technet.microsoft.com/library/dn646983.aspx#BKMK_AssignAdmins</linkUri></externalLink> to users in the Microsoft Intune administration console.</para>
                    </listItem>
                    <listItem>
                      <para>Users can enroll their mobile devices and computers to enable them to work from anywhere on their devices to access company applications and data more securely.</para>
                    </listItem>
                  </list>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>All devices</para>
                </TD>
                <TD>
                  <list class="bullet">
                    <listItem>
                      <para>The web-based <token>wit_2</token> administration console provides simplified management of computers in your company, including computers running <token>nextref_client_7</token> and <token>win8_client_ent_2</token>. </para>
                    </listItem>
                    <listItem>
                      <para>Not all computers running Windows operating systems, such as the Windows XP Home Edition operating systems, are supported for <token>wit_2</token> management. You should review the <externalLink><linkText>computer requirements</linkText><linkUri>http://technet.microsoft.com/library/dn646950.aspx#BKMK_DeviceReqs</linkUri></externalLink> for more information to help you plan for managing Windows-based computers with <token>wit_2</token>. </para>
                    </listItem>
                    <listItem>
                      <para>Company-owned or employee-owned mobile devices including <token>winrt_2</token>, Windows Phone 8, <?Comment SE(L: Incorrect: &quot;Apple iOS&quot;, use iOS.https://microsoft.sharepoint.com/teams/sc-style/Lists/System%20Center%20All%20Up%20Terminology%20%20Style%20List/Windows%20Intune.aspx 2015-04-07T17:29:00Z?>iOS, and Android devices can also be managed by <token>wit_2</token>.</para>
                    </listItem>
                    <listItem>
                      <para>
                        <token>wit_2</token> direct management of mobile devices has different requirements and capabilities than managing Windows-based computers. You should review the <externalLink><linkText>mobile device requirements</linkText><linkUri>http://technet.microsoft.com/library/dn646950.aspx#BKMK_DeviceReqs</linkUri></externalLink> for more information to help you plan for managing mobile devices with <token>wit_2</token>.</para>
                    </listItem>
                  </list>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>Apps and data</para>
                </TD>
                <TD>
                  <list class="bullet">
                    <listItem>
                      <para>Using <token>wit_2</token>, you can <externalLink><linkText>publish software</linkText><linkUri>http://technet.microsoft.com/library/2b770f4f-6d36-41e4-b535-514b46e29aaa#BKMK_BeforeYouDeploy</linkUri></externalLink> to the Microsoft Intune Company Portal. Users can then access and install the software on their managed computers and devices. </para>
                    </listItem>
                    <listItem>
                      <para>There are <externalLink><linkText>several, device-specific requirements</linkText><linkUri>http://technet.microsoft.com/library/dn408185.aspx</linkUri></externalLink> that must be planned for, and <?Comment SE(L: Voice word list: use &quot;set up&quot; for &quot;configure&quot;. 2015-04-07T17:29:00Z  Id='571?>set up <?CommentEnd Id='571'
    ?>correctly, before you can deploy software to mobile device. These requirements can include <?Comment SE(L: Or, replace with &quot;tasks&quot;. 2015-04-07T17:29:00Z  Id='572?>things to do<?CommentEnd Id='572'
    ?> such as obtaining sideloading keys for <token>winrt_2</token> devices, code-signing certificates, and deploying the Company Portal application when necessary.</para>
                    </listItem>
                    <listItem>
                      <para>In addition to deploying software, you can set up and deploy policies for the Microsoft Intune Agent settings on computers, manage mobile device policies, and collect hardware and software computer inventory. You can see the data collected during your evaluation period by <externalLink><linkText>reviewing the reports available</linkText><linkUri>http://technet.microsoft.com/library/dn646979.aspx</linkUri></externalLink> in the <ui>Reports</ui> workspace of the <token>wit_2</token>administration console.</para>
                    </listItem>
                  </list>
                </TD>
              </tr>
            </tbody>
          </table>
        </content>
      </section>
    </sections>
  </section>
  <section>
    <title>What are the steps to implement this solution?</title>
    <content>
      <para>Use the steps in this section to implement the solution. Make sure to verify the correct deployment of each step before proceeding to the next step.</para>
      <alert class="note">
        <para>If you want to print or export a customized set of solution topics, see <externalLink><linkText>Print/Export Multiple Topics – Help</linkText><linkUri>http://technet.microsoft.com/en-US/library/export/help/?returnUrl=%2fen-US%2flibrary%2fff630950.aspx</linkUri></externalLink>.</para>
      </alert>
      <alert class="important">
        <para>In the implementation steps for this solution, it is assumed that you are not already using Active Directory for identity management or Microsoft Online Services such as Microsoft Office 365. If you have one of those technologies, the following steps help you evaluate <token>wit_2</token> in a cloud-only configuration, but these steps might not all be applicable or lead to the best solution for your organization in production.</para>
      </alert>
      <list class="ordered">
        <listItem>
          <para>
            <embeddedLabel>Sign up for a free, 30-day trial of Microsoft Intune.</embeddedLabel> You can sign up for a <externalLink><linkText>free, 30-day trial of Microsoft Intune</linkText><linkUri>https://account.manage.microsoft.com/Signup/MainSignUp.aspx?OfferId=D585216E-936C-7E18-3AE2-0AA7445F8F80&amp;ali=1</linkUri></externalLink> to manage up to 25 computers and mobile devices.</para>
          <alert class="warning">
            <para>If your company already has a Microsoft Online Services <?Comment JJG: New account guidance issued to replace organizational account 2014-10-06T13:35:00Z  Id='611?>work or school <?CommentEnd Id='611'
    ?>account<?Comment SE(L: &quot;organizationalaccount&quot; replaces &quot;organization ID&quot; and &quot;OrgID&quot;.https://microsoft.sharepoint.com/teams/sc-style/Lists/System%20Center%20All%20Up%20Terminology%20%20Style%20List/Windows%20Intune.aspx 2014-10-06T13:35:00Z  Id='613?>, <?CommentEnd Id='613'
    ?>and you might possibly continue with this <token>wit_2</token> subscription in production after the trial period ends, it is essential that you click the <ui>Sign in</ui> option on that <ui>Sign in</ui> page and authenticate yourself by using the Global Administrator account for your company. This action ensures that your <token>wit_2</token> trial links to your existing Microsoft Online Services account.</para>
          </alert>
          <para>
            <embeddedLabel>Verification steps:</embeddedLabel> Review the confirmation email from the Microsoft Online Services Team to ensure that all the information is correct and ensure that you can log in to the <externalLink><linkText>Microsoft Intune account portal</linkText><linkUri>https://account.manage.microsoft.com/</linkUri></externalLink> with the User ID that is included in the email.</para>
          <para />
        </listItem>
        <listItem>
          <para>
            <embeddedLabel>Familiarize yourself with the various Microsoft Intune portals, workspaces, and tasks.</embeddedLabel> There are <externalLink><linkText>three Microsoft Intune portals</linkText><linkUri>http://technet.microsoft.com/library/dn646966.aspx#BKMK_AdminWebsites</linkUri></externalLink> that you should be aware of: two administration management portals that you can use to access the various features of your <token>wit_2</token> service, and one company portal that your <?Comment SE(L: To stay within the small business scenario, you might want to use &quot;employees&quot;. 2014-10-06T13:35:00Z  Id='620?>end users<?CommentEnd Id='620'
    ?> use to connect to <token>wit_2</token> services.</para>
          <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
            <thead>
              <tr>
                <TD>
                  <para>Microsoft Intune portal</para>
                </TD>
                <TD>
                  <para>Verification step</para>
                </TD>
              </tr>
            </thead>
            <tbody>
              <tr>
                <TD>
                  <para>
                    <embeddedLabel>Microsoft Intune account portal</embeddedLabel>. Using the <token>wit_2</token> account portal, administrators can manage users, groups, and domains for all Microsoft Online Services, including <token>wit_2</token> and Office 365. You can use the account portal to check the status of your subscriptions, add new subscriptions, add new domain names, and activate new user accounts. It is also where you can set up and configure the link to your on-premises Active Directory Domain Services (AD DS) instance if you have one.</para>
                </TD>
                <TD>
                  <para>Ensure that you can log in to the <externalLink target="_blank"><linkText>Microsoft Intune account portal</linkText><linkUri>https://account.manage.microsoft.com</linkUri></externalLink> with your tenant administrator credentials.</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>
                    <embeddedLabel>Microsoft Intune administration console</embeddedLabel>. The Microsoft Intune administration console is a web-based console that helps you to quickly access key information and <token>wit_2</token> management features. Here you can manage user and device groups, configure policy settings, view alerts and take action on them, review reports, and perform other service administrative tasks.</para>
                </TD>
                <TD>
                  <para>Ensure that you can log in to the <externalLink target="_blank"><linkText>Microsoft Intune administration console</linkText><linkUri>https://admin.manage.microsoft.com</linkUri></externalLink> with your tenant administrator credentials.</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>
                    <embeddedLabel>Microsoft Intune Company Portal</embeddedLabel>. To self-enroll a computer, the user must first access the <token>wit_2</token> company portal and log in by using their <token>wit_2</token> user ID. As an administrator, you configure Company Portal settings such as the company name, support contact information, and privacy statement links from within the <ui>Administration</ui> workspace of the administration console. </para>
                  <para>Don’t forget that you need to send instructions to users explaining what to expect when they go to the Company Portal. Make sure to include their user ID and temporary password, steps for connecting their computers and mobile devices to <token>wit_2</token>, and information about how to browse and install apps, and how to contact IT for help.</para>
                </TD>
                <TD>
                  <para>Ensure that you can log in to the <externalLink target="_blank"><linkText>Microsoft Intune Company Portal</linkText><linkUri>https://portal.manage.microsoft.com/</linkUri></externalLink> website with your tenant administrator credentials.</para>
                </TD>
              </tr>
            </tbody>
          </table>
          <para />
        </listItem>
        <listItem>
          <para>
            <embeddedLabel>Add Microsoft Intune users and administrators</embeddedLabel>. </para>
          <para>A tenant administrator can use the account portal to <externalLink><linkText>assign subscription licenses to users</linkText><linkUri>http://technet.microsoft.com/library/dn646983.aspx</linkUri></externalLink> by adding them to the <token>wit_2</token> Users Group.  Adding users to the <token>wit_2</token> Users Group maintained in the account portal is also how you get those users to show up in the <token>wit_2</token>administration console.  </para>
          <para>Administrator accounts for your <token>wit_2</token> service are not created in the account portal the way regular user accounts are. Instead, you have the option to <externalLink><linkText>assign administrative rights</linkText><linkUri>http://technet.microsoft.com/library/dn646983.aspx</linkUri></externalLink> to existing users. You do this by assigning either read-only access or full access administrative rights to users from within the administrator console in the <ui>Administration</ui> workspace under <?Comment SE(L: Is this sentence capped in the console? Please check. 2014-10-06T13:35:00Z  Id='639?>administration management<?CommentEnd Id='639'
    ?>. Service administrators that are assigned read-only access cannot modify <token>wit_2</token> settings, but they can view data and run reports. Service administrators with full access have all possible administrative rights.  </para>
          <para>You can view tenant administrator information by using the <token>wit_2</token> administration console, but you cannot create them there. By default, the subscription owner becomes a tenant administrator for your <token>wit_2</token> service and has full access to both the <token>wit_2</token> account portal and the <token>wit_2</token>administration console. We recommend that you create a least one extra tenant administrator account by using the account portal to help delegate tasks and ensure you don’t get locked out of your <token>wit_2</token> service administrator account if you forget your password.
</para>
          <para>
            <embeddedLabel>Verification steps:</embeddedLabel>
          </para>
          <list class="bullet">
            <listItem>
              <para>Ensure that user accounts appear in the All Users group within the <token>wit_2</token> administration console after adding them to the <token>wit_2</token> group in the account portal.</para>
            </listItem>
            <listItem>
              <para>Log out of the administration console, and then ensure that you can log back in to it with the newly assigned service administrator’s credentials.</para>
            </listItem>
          </list>
          <para />
        </listItem>
        <listItem>
          <para>
            <embeddedLabel>Create groups to organize users and devices</embeddedLabel>. In <token>wit_2</token>, <externalLink><linkText>groups are used to help you manage users, mobile devices, computers, and software deployments</linkText><linkUri>http://technet.microsoft.com/library/dn646990.aspx</linkUri></externalLink>. <token>wit_2</token> uses two types of groups that you can create in the <token>wit_2</token> administrator console:</para>
          <list class="bullet">
            <listItem>
              <para>
                <embeddedLabel>User Groups</embeddedLabel>. User Groups are used to make licensed software available to users and target mobile device security policies.</para>
            </listItem>
            <listItem>
              <para>
                <embeddedLabel>Device Groups</embeddedLabel>. Device Groups are used to deploy software and updates, and configure Microsoft Intune Agent Settings and Windows Firewall Settings policies.</para>
            </listItem>
          </list>
          <para>
            <embeddedLabel>Verification steps:</embeddedLabel> As new groups are created, you should see them displayed in the <token>wit_2</token>administration console.</para>
          <para />
        </listItem>
        <listItem>
          <para>
            <embeddedLabel>Set policies for mobile devices and computers</embeddedLabel>. <token>wit_2</token> policies let you configure settings that help secure mobile devices, deploy computer updates, protect against malware, maintain firewall settings, and enhance the end-user experience. </para>
          <para>You can configure and deploy <token>wit_2</token> policies to groups to manage settings for the <externalLink><linkText>Microsoft Intune client on computers</linkText><linkUri>http://technet.microsoft.com/library/dn646989.aspx</linkUri></externalLink> and <externalLink><linkText>mobile device</linkText><linkUri>http://technet.microsoft.com/library/dn646984.aspx</linkUri></externalLink> policy-based settings. After you add and deploy a new policy, all users or devices in the group to which you applied the policy inherit the settings as their baseline policy. You can always review and, if required, edit the details of these policies later from the <ui>Policy</ui> workspace.</para>
          <para>
            <embeddedLabel>Verification steps:</embeddedLabel> As new polices are added, you should see them displayed in the <token>wit_2</token> administration console.</para>
          <para />
        </listItem>
        <listItem>
          <para>
            <embeddedLabel>Install the Microsoft Intune client on computers</embeddedLabel>. The <token>wit_2</token> client is used to <externalLink><linkText>manage computers</linkText><linkUri>http://technet.microsoft.com/library/dn646975.aspx</linkUri></externalLink> and can be installed on both domain-joined computers in any domain and non-domain-joined computers. After the <token>wit_2</token> is installed on a <externalLink><linkText>supported computer operating system</linkText><linkUri>http://technet.microsoft.com/library/dn646950.aspx#BKMK_DeviceReqs</linkUri></externalLink>, the <token>wit_2</token> client provides application management, Endpoint Protection, hardware and software inventory, remote control through remote assistance requests, software updates, and compliance settings reporting.</para>
          <para>You can enroll computers in <token>wit_2</token> without an on-premises infrastructure in one of the following ways:</para>
          <list class="bullet">
            <listItem>
              <para>You can <externalLink><linkText>manually deploy the Microsoft Intune client software</linkText><linkUri>http://technet.microsoft.com/library/dn646969.aspx#BKMK_Manual </linkUri></externalLink>. In this type of deployment, an administrator downloads the <token>wit_2</token> client software and manually installs it on each PC. To download the <token>wit_2</token> client software, open the <token>wit_2</token> administration console and, in the Client Software Download area, download the client software package. After the client software is installed, <token>wit_2</token> automatically installs additional software as necessary to manage the computer.</para>
            </listItem>
            <listItem>
              <para>
                <externalLink>
                  <linkText>End-users can self-enroll each of their computers</linkText>
                  <linkUri>http://technet.microsoft.com/library/dn646969.aspx#BKMK_Allow</linkUri>
                </externalLink> through the <token>wit_2</token> Company Portal. Each enrolled computer is then automatically linked to the user account that was used to install the <token>wit_2</token> client software. 
</para>
            </listItem>
            <listItem>
              <para>You can deploy the <token>wit_2</token> client software to computers as <externalLink><linkText>part of an operating system deployment</linkText><linkUri>http://technet.microsoft.com/library/dn646969.aspx#BKMK_Image</linkUri></externalLink>.</para>
            </listItem>
          </list>
          <para>
            <externalLink>
              <linkText>Microsoft Intune Endpoint Protection</linkText>
              <linkUri>http://technet.microsoft.com/library/dn646970.aspx</linkUri>
            </externalLink> is installed by default during <token>wit_2</token> client installation on computers. Endpoint Protection helps enhance the security of computers in your organization by providing real-time protection against potential threats, keeping malicious software definitions up-to-date, and automatically running scheduled scans. For added security, you can also use <token>wit_2</token> policies to <externalLink><linkText>manage Windows Firewall settings</linkText><linkUri>http://technet.microsoft.com/library/dn646970.aspx</linkUri></externalLink> on managed computers. 
</para>
          <para>
            <embeddedLabel>Verification steps:</embeddedLabel> </para>
          <list class="bullet">
            <listItem>
              <para>Ensure that you can see the <token>wit_2</token> client icon in the taskbar at the bottom of the Windows desktop and that you get the <ui>Tech Support</ui> and <ui>Company Portal</ui> options when you click them.  </para>
              <list class="bullet">
                <listItem>
                  <para>The <embeddedLabel>Tech Support</embeddedLabel> option should open the Microsoft Intune Center. From there, you can see the tech support contact information and other options such as checking for available applications or software updates and scanning your computer for malware by using Endpoint Protection. </para>
                </listItem>
                <listItem>
                  <para>The <embeddedLabel>Company Portal</embeddedLabel> option should open a web browser and display a <token>wit_2</token> <ui>log in</ui> page. After logging in with your work or school account, you should see your company portal website with options for contacting IT, adding a device, and all applications available for your device.  </para>
                </listItem>
              </list>
            </listItem>
          </list>
          <para />
        </listItem>
        <listItem>
          <para>
            <embeddedLabel>Prepare for mobile device management</embeddedLabel>. Before you can enroll mobile devices, you must prepare the <token>wit_2</token> service by selecting the appropriate mobile device management authority setting on the <ui>Mobile Device Management</ui> page of the <ui>Administration</ui> workspace. The mobile device management authority setting determines whether you manage mobile devices with <token>wit_2</token> or System Center Configuration Manager with <token>wit_2</token> integration. In this solution, <token>wit_2</token> is used without System Center Configuration Manager integration so the setting should be set to <token>wit_2</token>.</para>
          <alert class="important">
            <para>Consider carefully whether you want to manage mobile devices by using <token>wit_2</token> only or System Center Configuration Manager with <token>wit_2</token> integration. After you set the mobile device management authority to either of these options, it cannot be changed again.</para>
          </alert>
          <para>In addition to setting the mobile device management authority, there might be other tasks necessary to <externalLink><linkText>prepare to manage mobile devices</linkText><linkUri>http://technet.microsoft.com/library/dn408185.aspx</linkUri></externalLink> in use by your company. For example, <token>winrt_2</token> and Windows Phone devices require access to an enrollment server during the enrollment process, and you need an Apple Push Notification service (APNs) certificate to manage iOS devices.</para>
          <para>
            <embeddedLabel>Verification steps:</embeddedLabel> Ensure that the mobile device management authority is set to <embeddedLabel>Microsoft Intune</embeddedLabel> and that you have completed any additional tasks required to support the types of mobile devices you plan to support before you continue.</para>
          <para />
        </listItem>
        <listItem>
          <para>
            <embeddedLabel>Enroll mobile devices</embeddedLabel>. You do not need to install <token>wit_2</token> client software on <externalLink><linkText>supported mobile devices</linkText><linkUri>http://technet.microsoft.com/library/dn408185.aspx</linkUri></externalLink>. Instead, they are enrolled in the <token>wit_2</token> service by using the company portal or the Company Apps Windows Phone setting. </para>
          <para>After enrolling a mobile device in <token>wit_2</token>, device management capabilities are provided for application management, hardware and software inventory of managed applications, and compliance settings reporting. You can help protect company data by deploying security policies to user groups to help secure company data and by using the <externalLink><linkText>Microsoft Intune remote wipe</linkText><linkUri>http://technet.microsoft.com/library/jj676679.aspx</linkUri></externalLink> feature to delete company data stored on mobile devices when they are lost, stolen, or retired from use.</para>
          <para>
            <embeddedLabel>Verification steps:</embeddedLabel> </para>
          <list class="bullet">
            <listItem>
              <para>Ensure that the Company Portal app has been successfully installed on the mobile device. If it has not been installed, you need to distribute it manually. </para>
            </listItem>
            <listItem>
              <para>After logging in with your work or school account, you should see all apps that have been made available, and the devices that have been linked, to the user account you are logged in as. </para>
            </listItem>
          </list>
          <para />
        </listItem>
        <listItem>
          <para>
            <embeddedLabel>Deploy applications to mobile devices and computers</embeddedLabel>. You can perform two types of software installations by using <token>wit_2</token>: <embeddedLabel>required <?Comment SE(L: Global comment: If this is part of the UI, you have to use it as such, but if you emphasized it just to make it stand out, use &quot;required installation&quot; and &quot;available installation&quot;. Install is not a noun. 2014-10-06T13:35:00Z  Id='660?><?Comment JJG: This is an example of using voice to bold important things that aren’t UI elements. 2014-10-06T13:35:00Z  Id='661?>install<?CommentEnd Id='660'
    ?><?CommentEnd Id='661'
    ?></embeddedLabel>, which automatically installs or pushes the software to managed computers, or an <embeddedLabel>available install</embeddedLabel> which deploys the software, or a link to the software, to the <token>wit_2</token> Company Portal so that users can choose whether to install it on their computers or on their mobile devices. </para>
          <list class="bullet">
            <listItem>
              <para>Before using <token>wit_2</token> to deploy software, you should make sure that you have the appropriate licenses to publish, distribute, and use the software. The <ui>Licenses</ui> workspace lets you <externalLink><linkText>add and manage license agreement information</linkText><linkUri>http://technet.microsoft.com/library/dn646985.aspx</linkUri></externalLink> for software that was purchased through Microsoft Volume Licensing agreements, and for Microsoft or non-Microsoft software that was purchased by other means. You can then create license reports that display managed license usage information throughout your company to stay informed of license usage activity.</para>
            </listItem>
            <listItem>
              <para>Users must be linked to their computer before you can deploy software to them by using <token>wit_2</token>. However, if a user is not already automatically linked to a computer, you can use the administration console to link them. You can link a user to multiple computers, but each computer can be linked to only one user. Mobile device users are automatically linked to their devices during enrollment, and users are also automatically linked to any computers that they add to <token>wit_2</token> by using the company portal.</para>
            </listItem>
            <listItem>
              <para>After you have ensured license compliance, and users are linked to devices, you can start the <token>wit_2</token> Software Publisher from the <ui>Software</ui> workspace in the <token>wit_2</token> administration console to publish and <externalLink><linkText>deploy software to mobile devices and computers</linkText><linkUri>http://technet.microsoft.com/library/2b770f4f-6d36-41e4-b535-514b46e29aaa#BKMK_BeforeYouDeploy</linkUri></externalLink>. There are two ways to deploy published applications with the software publisher: external links and software installer packages. </para>
              <list class="bullet">
                <listItem>
                  <para>
                    <embeddedLabel>External link:</embeddedLabel> To use external links, you simply provide a link to the web address of an application in an online app store. The link that you provide is then be made available to users in the company portal. The link lets users obtain the software from the online app store or be redirected to a web-based application that runs on the device’s web browser.</para>
                </listItem>
                <listItem>
                  <para>
                    <embeddedLabel>Software installer:</embeddedLabel> You can also use the Microsoft Intune Software Publisher to upload a signed application package directly to the <token>wit_2</token> service for users to access from the company portal. Using the software publisher, you can publish any of the following installer types: Windows Installer (.exe and .msi files), app packages for Android (.apk file type), app packages for iOS (.ipa file type), Windows Phone app packages (.xap file type), and Windows app packages (.appx file type). </para>
                  <alert class="tip">
                    <para>To make the process of deploying software to Windows Phone 8 devices easier during your trial evaluation period, you can use the <externalLink><linkText>support tool for Microsoft Intune trial management of Window Phone 8</linkText><linkUri>http://www.microsoft.com/en-us/download/details.aspx?id=39079</linkUri></externalLink>, which provides the necessary enrollment token and example applications for you to deploy during the trial evaluation period. The sample Company Portal app only works with trial accounts, but additional help for deploying applications to Windows Phone 8 devices in production is available by <externalLink><linkText>downloading the Windows Phone 8 walkthrough guide</linkText><linkUri>http://download.microsoft.com/download/5/E/9/5E9F371B-65A3-4821-8A82-C4A68E81C120/Windows_Intune_Windows_Phone_8_Walkthrough.pdf</linkUri></externalLink>.</para>
                  </alert>
                </listItem>
              </list>
            </listItem>
          </list>
          <para>
            <embeddedLabel>Verification steps:</embeddedLabel> Ensure that a published application is available from the company portal when logged in with a user account that is associated with a software deployment. </para>
          <para />
        </listItem>
        <listItem>
          <para>
            <embeddedLabel>Manage software update approvals</embeddedLabel>. You can <externalLink><linkText>approve and deploy Microsoft and non-Microsoft updates to Microsoft Intune clients</linkText><linkUri>http://technet.microsoft.com/library/dn646968.aspx</linkUri></externalLink> from the <ui>Updates</ui> workspace in the <token>wit_2</token>administration console. If you want to closely manage individual update approvals, then you can use the <ui>Approve</ui> or <ui>Decline</ui> options for each update in the <ui>Updates</ui> workspace. You can also automatically approve updates by using <token>wit_2</token> auto-approval rules.
</para>
          <para>
            <embeddedLabel>Verification steps:</embeddedLabel> As new updates are approved, you should see <embeddedLabel>Yes</embeddedLabel> displayed in the approved column for them in the <ui>Updates</ui> workspace in the administration console.</para>
          <para />
        </listItem>
        <listItem>
          <para>
            <embeddedLabel>Configure alerts and notifications</embeddedLabel>. <token>wit_2</token> alerts are used to monitor system and software performance or notify administrators when an action is required. You can <externalLink><linkText>configure</linkText><linkUri>http://technet.microsoft.com/library/dn646958.aspx</linkUri></externalLink> and <externalLink><linkText>monitor</linkText><linkUri>http://technet.microsoft.com/library/dn646973.aspx</linkUri></externalLink> alerts from the <ui>Alerts</ui> workspace or by having the service send the alerts directly to specific service administrator email addresses.</para>
          <para>
            <embeddedLabel>Verification steps:</embeddedLabel> As alerts are generated, you should see them displayed in the <ui>Alerts</ui> workspace in the <token>wit_2</token> administration console. If notification rules have been configured, specified alert recipients should receive alert notifications.</para>
          <para />
        </listItem>
        <listItem>
          <para>
            <embeddedLabel>Create reports to review organizational data</embeddedLabel>. <externalLink><linkText>Microsoft Intune reports</linkText><linkUri>http://technet.microsoft.com/library/dn646977.aspx</linkUri></externalLink> provide information about the status of software updates, detected software, computer inventory, mobile device inventory, license purchase, and license installation reports for managed mobile devices and computers. </para>
          <para>Reports can help you answer a range of questions, such as how many computers have a particular application or update installed, information about the computer hardware and mobile devices in use, and even software license purchase and usage activities. <token>wit_2</token> provides a set of built-in report templates that can be used as-is, or you can create custom reports based on views within the <token>wit_2</token> workloads.</para>
          <para>
            <embeddedLabel>Verification steps:</embeddedLabel> Ensure that expected information is returned when you view a report in the <ui>Reports</ui> workspace of the <token>wit_2</token> administration console. If you create a new report, it should be available from the <embeddedLabel>Load</embeddedLabel> <?Comment SE(L: Microsoft style,http://mstp/html/542f639a-975e-4f47-9574-b16a2095bbcc.htm 2014-10-06T13:35:00Z?>list on the <ui>Report</ui> page that you created it on. </para>
          <para />
        </listItem>
      </list>
      <para>
        <embeddedLabel>Cloud-only implementation complete</embeddedLabel>. After completing the implementation steps, all of the goals as listed in this solution are met as follows:</para>
      <list class="bullet">
        <listItem>
          <para>Mobile devices and computers can effectively be managed from the cloud-based <token>wit_2</token> administration console to configure security and compliance settings, software and hardware inventory, and software deployment. </para>
        </listItem>
        <listItem>
          <para>
            <token>wit_2</token> client computers are protected from malware infections and unwanted software installations by <token>wit_2</token> Endpoint Protection.</para>
        </listItem>
        <listItem>
          <para>
            <token>wit_2</token> remote wipe functionality can protect company data by wiping company data stored on mobile devices when they are lost, stolen, or retired from use.</para>
        </listItem>
        <listItem>
          <para>Employees can access the company portal to provide self-service functions such as enrolling their own devices, accessing applications, and contacting IT.</para>
        </listItem>
        <listItem>
          <para>Because this is a cloud-only management solution without the need for on-premises hardware, server and site system role management are eliminated. </para>
        </listItem>
      </list>
      <para>
        <embeddedLabel>Do you need additional, step-by-step evaluation information?</embeddedLabel> If so, you should review the <externalLink><linkText>Microsoft Intune Evaluation Guide</linkText><linkUri>http://technet.microsoft.com/library/dn646952.aspx</linkUri></externalLink> in the <externalLink><linkText>Documentation Library for Microsoft Intune</linkText><linkUri>http://technet.microsoft.com/library/jj676587.aspx</linkUri></externalLink>. That guide is designed to help you evaluate the main features of <token>wit_2</token> by providing step-by-step instructions for you to set up your new <token>wit_2</token> evaluation environment. </para>
      <para>
        <embeddedLabel>Buy a subscription to Microsoft Intune</embeddedLabel>. After evaluating <token>wit_2</token>, you should be ready to <externalLink><linkText>move from Microsoft Intune free trial</linkText><linkUri>http://technet.microsoft.com/library/dn646949.aspx</linkUri></externalLink> to buy a subscription to continue providing mobile device and PC management services to your organization. </para>
      <para>You can easily convert your free trial subscription to a paid, full subscription on the <ui>Admin</ui> page of the account portal. The full subscription lets you continue using the <token>wit_2</token> service without any interruption or loss of data. Alternatively, you can let your initial trial <token>wit_2</token> subscription expire so that you can start a new trial subscription configured to match your production needs in preparation for purchasing a full subscription to <token>wit_2</token>.</para>
      <para>
        <embeddedLabel>Get technical help for Microsoft Intune</embeddedLabel>. You can review the <externalLink><linkText>Microsoft Intune Knowledge Base</linkText><linkUri>http://support.microsoft.com/search/default.aspx?mode=a&amp;query=kb+%22windows+intune%22&amp;spid=global&amp;catalog=lcid%3D1033&amp;1033comm=1&amp;ast=25&amp;ast=28&amp;ast=30&amp;ast=31&amp;res=10</linkUri></externalLink> for known issues. Additionally, you can get phone support and email support for both non-technical issues, such as billing or subscription issues, or technical questions about the <token>wit_2</token> cloud-based service by contacting <externalLink><linkText>Microsoft Intune Support</linkText><linkUri>https://support.microsoftonline.com/default.aspx?productkey=intunesupp&amp;wa=wsignin1.0</linkUri></externalLink>. </para>
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
              <para>Planning and design</para>
            </TD>
            <TD>
              <para>
                <externalLink>
                  <linkText>Documentation Library for Microsoft Intune</linkText>
                  <linkUri>http://technet.microsoft.com/library/jj676587.aspx</linkUri>
                </externalLink>
              </para>
              <para>
                <externalLink>
                  <linkText>Microsoft Intune Evaluation Guide</linkText>
                  <linkUri>http://technet.microsoft.com/library/dn646952.aspx</linkUri>
                </externalLink>
              </para>
              <para>
                <externalLink>
                  <linkText>Microsoft Intune Showcase videos</linkText>
                  <linkUri>http://www.microsoft.com/en-us/showcase/channelDetails.aspx?channelid=windowsintune</linkUri>
                </externalLink>
              </para>
              <para>
                <externalLink>
                  <linkText>Microsoft Intune Trust Center</linkText>
                  <linkUri>http://www.microsoft.com/en-us/WindowsIntuneTrust/</linkUri>
                </externalLink>
              </para>
              <para>
                <externalLink>
                  <linkText>Microsoft Intune Privacy and Data Protection Overview white paper</linkText>
                  <linkUri>http://download.microsoft.com/download/C/C/8/CC8065C4-829F-4635-B731-1D39287444C0/Windows_Intune_Privacy_and_Data_Protection_Overview.pdf</linkUri>
                </externalLink>
              </para>
              <para>
                <externalLink>
                  <linkText>Microsoft Intune Purchasing and Support Guide</linkText>
                  <linkUri>http://download.microsoft.com/download/C/8/A/C8ACC872-EC51-4915-B408-836849F53F3F/Dec-2012_Windows_Intune_Purchase_Guide.pdf</linkUri>
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
                  <linkText>Microsoft Intune forums</linkText>
                  <linkUri>http://go.microsoft.com/fwlink/?LinkId=232998</linkUri>
                </externalLink>
              </para>
              <para>
                <externalLink>
                  <linkText>Microsoft Intune Wiki</linkText>
                  <linkUri>http://go.microsoft.com/fwlink/?LinkID=244347</linkUri>
                </externalLink>
              </para>
              <para>
                <externalLink>
                  <linkText>Microsoft Intune Team Blog</linkText>
                  <linkUri>http://go.microsoft.com/fwlink/?LinkId=273882</linkUri>
                </externalLink>
              </para>
              <para>
                <externalLink>
                  <linkText>Microsoft Intune Twitter Feed</linkText>
                  <linkUri>http://go.microsoft.com/fwlink/?LinkId=273880</linkUri>
                </externalLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Microsoft Virtual Academy Training</para>
            </TD>
            <TD>
              <para>
                <externalLink>
                  <linkText>Microsoft Intune for IT Professionals Jump Start</linkText>
                  <linkUri>http://www.microsoftvirtualacademy.com/training-courses/windows-intune-for-it-professionals-jump-start</linkUri>
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
                <externalLink>
                  <linkText>Manage mobile devices and computers  by migrating to Configuration Manager with Microsoft Intune</linkText>
                  <linkUri>http://technet.microsoft.com/en-us/library/dn582037.aspx</linkUri>
                </externalLink>
              </para>
              <para>
                <externalLink>
                  <linkText>Mobile device management for Configuration Manager 2007 customers planning to migrate to System Center 2012 R2 Configuration Manager</linkText>
                  <linkUri>http://technet.microsoft.com/en-us/library/dn508400.aspx</linkUri>
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