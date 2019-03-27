---
# required metadata

title: Microsoft Threat Protection Trial Guide
description: Learn how you can start a free trial of Microsoft Threat Protection for 30 days and up to 250 users.
keywords:
author: dougeby
ms.author: dougeby
manager: mtillman
ms.date: 02/26/2019
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.service:
ms.technology:
ms.assetid: dfe45038-7567-46d1-ab9a-d455af2588ac

# optional metadata

ROBOTS: NOINDEX,NOFOLLOW
#audience:
#ms.devlang:
#ms.reviewer: [ALIAS]
#ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Deploying Microsoft Threat Protection Services
Microsoft Threat Protection (MTP) is a comprehensive, integrated, and intelligent solution securing the modern workplace across identities, endpoints, user data, cloud apps, and infrastructure.  The solution is built on and powered by the Microsoft Intelligent Security Graph, harnessing signals from the threat landscape, providing intelligent analysis, actionable insights, and ultimately, best in breed security for the modern workplace.  This guide will help you set up the following services that are part of Microsoft Threat Protection.

- **Azure Active Directory** enhances security, simplifies access, and sets smart policies with a single identity platform.

- **Office 365 Exchange Online Protection (EOP)** is a cloud-based email filtering service that helps protect your organization against spam and malware and includes features to safeguard your organization from messaging-policy violations. EOP simplifies your messaging environment and eases the management burden of on-premises systems.

- **Office 365 Advanced Threat Protection (ATP)** protects your organization from malicious attacks by scanning email attachments, URLs within email messages and documents, identifying and blocking malicious files, checking for unauthorized spoofing, and detecting user and domain impersonation attempts.

- **Microsoft Cloud App Security (CAS)** provides enterprise-grade security for your cloud apps and secures on-premises systems related to those cloud applications. Comprehensive controls offer deeper visibility and enhanced protection against cloud security and compliance issues.

- **Windows Defender Advanced Threat Protection (Windows Defender ATP)** is a unified platform for preventive protection, post-breach detection, and automated response, employing intelligent endpoint protection. The Windows Defender Security Center dashboard provides insight into virus, attack and device health activities and performance.

- **Azure Advance Threat Protection (Azure ATP)** is a cloud service that helps protect your enterprise hybrid environments from multiple types of advanced cyber-attacks and insider threats by leveraging multiple data sources and a proprietary network parsing engine to capture network traffic for authentication, authorization and information gathering.

- **Azure Security Center (ASC)** provides unified security management and advanced threat protection across hybrid cloud workloads. With Azure Security Center, you can apply custom security policies across all workloads, limit exposure to threats, and immediately detect and respond to attacks.

## Exercise 1: Prepare your environment
> [!NOTE]
> Perform these steps in a browser instance of [Jump Host 01](https://labondemand.com/LabProfile/EditInstructions/45973).

Before setting up Microsoft 365 Threat Protection technology, it's important to know about your environment and what licenses are in place so that installation and configuration are successful. The following components are included in your lab environment:

- A Microsoft 365 tenant (see tenant global admin user credentials at the top of the **Resources** page)
- Virtual machines:
  - Windows 10 client PC (**Jump Host 01** under **Resources**)
  - Windows Server running domain controller (**DC01** under **Resources**)
- An Azure Subscription. For guidelines on how to obtain a temporary Azure Subscription using an Azure Pass, see [Exercise 7: Set up Azure Security Center](#exercise-7-set-up-azure-security-center).

### Microsoft 365 Tenant
For this lab, a Microsoft 365 tenant is supplied to you and includes appropriate trial subscriptions. To verify your tenant is equipped with these licenses, use the following procedure:

1. If necessary, switch to the Windows 10 client machine, [Jump Host 01](https://labondemand.com/LabProfile/EditInstructions/45973).
2. Launch a new browser instance, then navigate to the [Office 365 management portal](https://portal.office.com).
3. Sign in with global admin user credentials. For your lab tenant user credentials, see the **Resources** tab.
4. Dismiss any pop-up windows, and then click **Admin** to go to Microsoft 365 admin center.
5. In the navigation, go to **Billing**, and then **Subscriptions**.
6. Review the list of current licenses, including Office 365 Enterprise E5, EMS Enterprise E5, and Windows 10 E5.

> [!IMPORTANT]
> Your Microsoft 365 tenant is a temporary learning environment only and will be automatically deleted after the allotted time period, unless converted to a paid subscription.

In the real-world environment, you must have a subscription to Microsoft Azure, and be assigned the role of Subscription Owner, Subscription Contributor, or Security Administrator.

### Azure Subscription
An Azure Subscription is required for upgrading Azure Security Center (ASC) from Free Tier to Standard Tier. Free Tier provides threat monitoring protection for Azure resources only, while the Standard Tier extends this capability to on-premises and non-Azure cloud resources. The Standard Tier upgrade is free for the first 60 days in all tenants.

> [!NOTE] 
For guidelines to acquiring a temporary Azure Subscription using an Azure Pass for this lab, see [Exercise 7: Set up Azure Security Center](#exercise-7-set-up-azure-security-center).

## Exercise 2: Set up and configure Exchange Online Protection

### Introduction
Microsoft Exchange Online Protection (EOP) is a cloud-based email filtering service that helps protect your organization against spam and malware, and includes features to safeguard your organization from messaging-policy violations. EOP can simplify the management of your messaging environment and alleviate many of the burdens that come with maintaining on-premises hardware and software.    
You can use EOP for messaging protection in a standalone environment, as part of Microsoft Exchange Online, and in a hybrid deployment.

### Prerequisites
You must have the following prerequisites for a successful set up:
- You have Office 365 and your subscription includes Exchange Online. (For the premium Office Advanced Threat Protection topics, an Office ATP license is required either through Office 365 E5 or as a standalone service.)
- You have Exchange Online Protection Admin permission for advanced protection policy definition and have added your domain.

### Add recipients and enable Directory-Based Edge Blocking
The Directory Based Edge Blocking (DBEB) feature in Exchange Online and Exchange Online Protection (EOP) lets you reject messages for invalid recipients at the service network perimeter. DBEB lets admins add mail-enabled recipients to Office 365 and block all messages sent to email addresses that aren't present in Office 365.

To ensure your accepted domain is set to Internal relay, use the following procedure:
1. In the Windows 10 client machine, [Jump Host 01](https://labondemand.com/LabProfile/EditInstructions/45973), ensure you're in the **Microsoft 365 admin center** page.
2. At the bottom of the left navigation, expand **Admin centers** menu, then select **Exchange** to go to the **Exchange admin center (EAC)**. 
3. In the EAC, go to **Mail flow** > **Accepted domains**.
4. Select the domain and click **Edit**.
5. Ensure that the domain type is set to **Internal relay**. If it's set to **Authoritative**, change it to **Internal relay** and click **Save**.

To add valid users to Office 365, use one of the following:
- **Directory synchronization** 
  Add valid users to Office 365 by synchronizing from your on-premises Active Directory environment to Azure Active Directory in the cloud.
- **Add users via remote Windows PowerShell**
  Adding and managing mail users by running remote Windows PowerShell is useful for adding multiple records and creating scripts.
- **Add users directly in the Exchange admin center (EAC)**
  Adding and managing mail users directly in the EAC is useful for adding one user at a time.

To set your accepted domain to Authoritative, use the following procedure:
1. In the EAC, go to **Mail flow** > **Accepted domains**.
2. Select the domain and click **Edit**.
3. Set the domain type to **Authoritative**.
4. Click **Save**, and confirm enablement of Directory Based Edge Blocking.

### Use the EAC to set up mail flow
Connectors are created in the Exchange admin center (EAC) to enable mail flow between EOP and your on-premises mail servers.
1. The **email server is set up** and capable of sending and receiving mail to and from the Internet.
2. On-premises email server has **Transport Layer Security (TLS) enabled**, with a valid certification authority-signed (CA-signed) certificate.
3. The default certificate for the **Receive connector is updated** to securely receive email between Office 365 and your email server via Edge Transport Server or Client Access Server using the *TlsCertificateName* parameter on the Set-ReceiveConnector cmdlet in the Exchange Management Shell.
4. The **name or IP address of your external-facing email** server has been noted. If you're using Exchange, this will be the Fully Qualified Domain Name (FQDN) of your Edge Transport server or CAS that will receive email from Office 365.
5. **Port 25 on the firewall is open** for Office 365 to connect to email servers, ensuring connections are accepted from all IP addresses.
6. The connector is created via the Exchange admin center.

### Define Spam Routing
Detected spam can be automatically routed via a custom spam-filter policy, defining high confidence spam and sending to the appropriate folder.
1. In the Exchange admin center (EAC), navigate to **Protection** > **Spam filter**.
   You can edit the default policy or add a new policy on the general page.
2. Double-click the default policy in order to edit this company-wide policy.
3. Click the **+ New** icon to create a new custom spam-filter policy that can be applied to users, groups, and domains in your organization. You can also edit existing custom policies by double-clicking them.
4. On the **spam and bulk email actions** page, under **Spam** and **High confidence spam**, keep the default **Move messages to Junk Email** folder selection.
   You can also do the following:
   - **Delete message** deletes the entire message, including all attachments.
   - **Quarantine message** sends the message to quarantine instead of the intended recipients. The **Retain spam for (days)** allows you to specify the number of days of quarantine. (It will automatically be deleted after the time elapses. The default value is 15 days which is the maximum value, and the minimum value is 1 day.)
   - **Add X-header** sends the message to the specified recipients, but adds X-header text to the message header in order to identify the message as spam. Using this text as an identifier, you can also create inbox rules or use a downstream device to act on the message. The default X-header text is **This message appears to be spam**.
   - **Prepend subject line with text** sends the message to the intended recipients but prepends the subject line with the text that you specify in the **Prefix subject line with this text** input box. Using this text as an identifier, you can optionally create rules to filter or route the messages as necessary.
   - **Redirect message to email address** sends the message to a designated email address instead of the intended recipients. Specify the **redirect** address in the **Redirect to this email address** input box.
5. Under **Bulk email**, select a threshold to treat bulk email as spam. Level 1 indicates most bulk email as spam and level 9 allows the most bulk email to be delivered. The service then performs the configured action, such as sending the message to the recipient's **Junk Email** folder.

### Migrate Spam Block and Allow Lists
Known suspicious senders and domains can be listed and blocked, while trusted senders remain on an Allow list to ensure appropriate and undisrupted receipt of information.

On the Block Lists page, you can specify entries such as senders or domains to be marked as spam. The service then applies the configured high confidence spam action to email that matches these entries.
- Add unwanted senders to the Sender block list. Click **Add +** . In the selection dialog box, add the sender addresses to block, separating multiple entries using a semi-colon or a new line. Click **Ok** to return to the **Block Lists** page.
- Add unwanted domains to the Domain block list. Click **Add +**. In the selection dialog box, add the domains you want to block, separating multiple entries using a semi-colon or a new line. Click **Ok** to return to the **Block Lists** page.

On the Allow Lists page, specify entries such as senders or domains to be delivered to the inbox. Email from these entries is not processed by the spam filter.
- Add trusted senders to the Sender allow list. Click **Add +**. In the selection dialog box, add the sender addresses you wish to allow, separating multiple entries using a semi-colon or a new line. Click **Ok** to return to the **Allow Lists** page.
- Add trusted domains to the Domain allow list. Click **Add +**. In the selection dialog box, add the domains you wish to allow, separating multiple entries using a semi-colon or a new line. Click **Ok** to return to the **Allow Lists** page.

### Create Bypass Rule for Spam
Spam can easily be detected and contained via email flow bypass rules.
1. In the EAC, navigate to **Mail flow** > **Rules**. Choose **Add +** and choose **Bypass spam filtering**.
2. Give the rule a name. Under **Apply this rule if**, choose **The sender** and select one of the following conditions:
   - To specify a domain, choose **domain is**. In the **Specify domain** dialog box, enter the domain of the sender to designate as safe, such as contoso.com. **Add +** to move it to the list of phrases. Repeat this step to add domains, and click Ok to confirm.
   - To specify a user, choose is this person. In the Select members dialog box, add the user from the list or type the user and click Check names. Repeat this step to add users and click **Ok** to confirm.
3. Select the **Stop processing more rules** check box to ensure that no other rule can reverse the bypass action.
4. For the **Match sender address in message** option, select **Header or envelope**.
5. You may make selections to audit the rule, test the rule, activate the rule during a specific time period, and others.
6. Choose **Save** to save the rule.

After you create and enforce the rule, spam filtering is bypassed for the domain or user you specified.

### Create a Transport Rule
Use the Exchange admin center to create a transport rule that blocks messages sent from a domain or user.
1. In the EAC, navigate to **Mail flow** > **Rules**. Choose **Add +** and choose **Create a new rule**.
2. Give the rule a name and then click **More options**.
3. Under **Apply this rule if**, choose **The sender** and select one of the following conditions:
   - To specify a domain, choose domain is. In the Specify domain dialog box, enter the sender domain from which you want to block messages, such as contoso.com. Click Add  to move it to the list of phrases. Repeat this step to add domains, and click Ok to confirm.
   - To specify a user, choose is this person. In the Select members dialog box, add the user from the list or type the user and click Check names. Repeat this step to add users, and click Ok to confirm.
 4. Under **Do the following**, choose **Block the message** and click one of the other options such as **Delete the message without notifying anyone**.
 5. Click **More options**, and then for the **Match sender address in message** option, select **Header or envelope**.
 6. Choose **Save** to save the rule.

After you create and enforce the rule, any messages sent from the domain or user you specify will be blocked.

### Mark Visual Basic or JavaScript as Spam
Protect your organization by filtering Visual Basic and JavaScript-based spam.
1. Go to **Spam filter settings** > **advanced options** > **Mark as Spam**.
2. Toggle on **JavaScript** or **VBScript in HTML**.
3. Click **Save**.

### Deploy Office 365 Report Message Add-in
Choose how messages are sent to Microsoft when they're reported as junk or phishing attempts. 
1. Choose **Options** from the **Report Message** button on the ribbon.
2. Select one of the following options:
   - Always send a copy of the message to Microsoft
   - Never send a copy of the message to Microsoft
   - Ask before sending a copy of the message to Microsoft
3. Make selection and click **Save**.

## Exercise 3: Set up and configure Office 365 Advanced Threat Protection

### Introduction
Office 365 Advanced Threat Protection protects mailboxes, files, online storage, and applications against new and sophisticated attacks in real time. It offers holistic protection in Microsoft Teams, Word, Excel, PowerPoint, Visio, SharePoint Online, and OneDrive for Business. By protecting against unsafe attachments and expanding protection against malicious links, it complements the security features of Exchange Online Protection to provide better zero-day protection.

### Prerequisites
Successfully set up Exchange Online Protection. The following steps for setting up Office 365 Advanced Threat Protection are to be performed on a Windows client. You must have the following prerequisites for a successful set up:
- Your organization has Office 365 Advanced Threat Protection. Office 365 Enterprise E5, Office 365 Education A5, or Microsoft 365 Business include Advanced Threat Office 365 Exchange Online Protection is set up and successfully configured.
- You have necessary permissions assigned in the Office 365 Security & Compliance Center.

### Setting Up Office 365 Advanced Threat Protection

#### Configure ATP for entire organization
Office 365 Advanced Threat Protection (ATP) protects your organization from malicious attacks by scanning email, attachments, URLs, document libraries, while monitoring suspicious activity like user impersonations, spoofing and phishing attempts. You can configure security policies for an entire organization meeting security and compliance requirements.
1. In the Windows 10 client machine, [Jump Host 01](https://labondemand.com/LabProfile/EditInstructions/45973), navigate to the [Security & Compliance admin page](https://protection.office.com/).
2. In the left navigation, under **Threat management**, choose **Policy** > **Safe Links**.
3. In the **Policies that apply to the entire organization** section, select **Default**, and then choose **Edit** (the Edit button resembles a pencil).
4. In the **Block the following URLs** section, specify one or more URLs that you want to prevent people in your organization from visiting.
5. In the **Settings that apply to content except email** section, select all the options you want to use.
6. Choose **Save**.

#### Configure ATP for Email Notifications and Exclusions
ATP can send email notifications when it detects a suspicious activity or a health alert, communicating the type of risk and actions taken.
1. In the ATP workspace portal, select the settings option on the toolbar and select **Configuration**.
2. Click **Notifications**.
3. Under **Mail notifications**, specify which notifications should be sent via email - they can be sent for new alerts (suspicious activities) and new health issues.
4. Click **Save**.
5. In Configuration page go to **Configuration**, click **Exclusions** and select the suspicious activity. To add an entity from the **Exclusions** configuration, enter the entity name and then click the plus, and then click **Save** at the bottom of the page. To remove an entity from the **Exclusions** configuration, click the minus next to the entity name and then click **Save** at the bottom of the page.

ATP can be easily configured in much the same way for blocking password protected and encrypted files, multimedia and scripts.

#### Enable ATP Anti-phishing
ATP anti-phishing applies a set of machine learning models together with impersonation detection algorithms to incoming messages to provide protection for commodity and spear phishing attacks. To set up ATP anti-phishing policies in Office 365, use the following procedure:
1. In the **Office 365 Security & Compliance** admin page, in the left navigation pane, under **Threat management**, choose **Policy**.
2. On the **Policy** page, choose **ATP anti-phishing**.
3. On the **Anti-phishing** page, add a new policy select **+ Create**. You can edit an existing policy as well. The wizard guides you through the anti-phishing policy definition.
4. Specify the name, description, and settings for your policy.
5. Once you have reviewed your settings, choose **Create this policy**.

ATP can be easily configured in much the same way for applying company domain, C-level name protection, and outside account policies.

#### Enable ATP SafeLinks, SafeAttachments and Blocked URL Lists
ATP keeps email safe by scanning mailed links and attachments, and monitoring blocked URLs.

##### Set up ATP SafeLinks policies in Office 365: 
1. Sign in to the [Office 365 Security & Compliance Center](https://protection.office.com).
2. In the left navigation, under Threat management, choose **Policy** > **Safe Links**.
3. In the **Policies that apply to the entire organization** section, select **Default**, and then choose **Edit** (the Edit button resembles a pencil).
4. In the **Block the following URLs** section, specify one or more URLs that you want to prevent people in your organization from visiting.
5. In the **Settings that apply to content except email** section, select all the options you want to use.
6. Choose **Save**.

##### Set up a custom URL block list: 
1. Sign in to the [Office 365 Security & Compliance Center](https://protection.office.com).
2. In the left navigation, under **Threat management**, choose **Policy** > **Safe Links**.
3. In the **Policies that apply to the entire organization** section, select **Default**, and then choose **Edit** (the Edit button resembles a pencil).
4. Select the **Enter a valid URL** box, type a URL, and then choose the plus sign (+).
   - You can specify a domain-only URL (like contoso.com or tailspintoys.com). This will block clicks on any URL that contains the domain.
   - Do not include a forward slash (/) at the end of the URL. For example, instead of entering http://www.contoso.com/, enter http://www.contoso.com.
   - You can include up to three wildcard asterisks (*) per URL.

##### Add a policy for specific email recipients:
1. Sign in to the [Office 365 Security & Compliance Center](https://protection.office.com).
2. In the left navigation, under **Threat management**, choose **Policy**.
3. Choose **Safe Links**.
4. In the **Policies that apply to specific recipients** section, choose **New** (the New button resembles a plus sign (+).
5. Specify the name, description, and settings for your policy.
6. Choose **Save**.

##### Set up ATP SafeAttachments policies in Office 365:
1. Sign in to the [Office 365 Security & Compliance Center](https://protection.office.com).
2. In the left navigation pane, under **Threat management**, choose **Policy** > **Safe Attachments**.
3. If you see **Turn on ATP for SharePoint, OneDrive, and Microsoft Teams**, select this option to enable [Office 365 Advanced Threat Protection for SharePoint, OneDrive, and Microsoft Teams](https://support.office.com/article/office-365-atp-for-sharepoint-onedrive-and-microsoft-teams-26261670-db33-4c53-b125-af0662c34607) for your Office 365 environment.
4. Choose **New** (the New button resembles a plus sign (+) to start creating your policy.
5. Specify the name, description, and settings for the policy.
6. Choose **Save**.

#### Enable SharePoint/OneDrive/Teams Scanning
ATP can detect and block files that are identified as malicious in SharePoint, Teams and OneDrive document libraries. 
1. Sign in to the [Office 365 Security & Compliance Center](https://protection.office.com).
2. In the left navigation pane, under **Threat management**, choose **Policy** > **Safe Attachments**.
3. Select **Turn on ATP for SharePoint, OneDrive, and Microsoft Teams**.
4. Click **Save**.
5. Review and edit your organization's Safe Attachments policies and Safe Links policies.
6. As a global administrator or a SharePoint Online administrator, you can run the Set-SPOTenant cmdlet with the **DisallowInfectedFileDownload** parameter set to **true**. Office 365 datacenters will be updated over time.

#### Enable Bypass Rules For SafeLinks/SafeAttachments
False clicks or attachment can be avoided by setting up bypass rules for mail flow. 

##### SafeLinks bypass rule set up
1. Log in to the Office 365 admin center and navigate to the [Exchange admin center](https://outlook.office365.com/ecp).
2. Select **Mail Flow**.
3. Click  **+** and select **Create a new rule**.
4. Click **more options…** at the bottom of the dialog box to show all fields required to complete the rule.
5. Enter a value for the name, select which messages the rule will apply to (such as applying to a certain sender, IP address range, or domain), and then under **Do the following**, select **Modify the message properties | Set the message header to this value**.
6. Enter **X-MS-Exchange-Organization-SkipSafeLinksProcessing** as the header name, then set the value to **1**.
7. Click **Save** to finish the rule.

##### SafeAttachment bypass rule set up
1. Log in to the Office 365 admin center and navigate to the [Exchange admin center](https://outlook.office365.com/ecp).
2. Select **Mail Flow**.
3. Click **+** and select **Create a new rule**.
4. Click **more options…** at the bottom of the dialog box to show all fields required to complete the rule.
5. Enter a value for the name, select which messages the rule will apply to (such as applying to a certain sender, IP address range, or domain), and then under **Do the following**, select **Modify the message properties | Set the message header to this value**.
6. Enter **X-MS-Exchange-Organization-SkipSafeAttachmentProcessing** as the header name, then set the value to **1**.
7. Click **Save** to finish the rule.

## Exercise 4: Set up and configure Microsoft Cloud App Security

### Introduction
Cloud App Security is a critical component of Microsoft Cloud Security and helps your organization optimize and protect cloud applications while providing simple and secure management tools for organizations of every size and industry.

The Cloud App Security framework consists of 3 parts:
- **Cloud Discovery** gives visibility to all cloud use in your organization, including Shadow IT reporting and control and risk assessment.
- **Data Protection** monitors and controls your data in the cloud by detecting anomalies, enforcing DLP policies, investigating and sending alerts.
- **Threat Protection** detects anomalous use and security incidents by using behavioral analytics and advanced investigation tools.

### Prerequisites
The following steps for setting up Microsoft Cloud App Security are to be performed on a Windows client.
The following is required for successful set up:
Access to a tenant with license for Cloud App Security. Cloud App Security is available with one of the following subscriptions:
- Standalone Cloud App Security subscription
- Microsoft Enterprise + Security (EMS) E5 subscription
- Microsoft 365 Enterprise E5 (which includes EMS E5 subscription)

An Office 365 subscription is required to connect CAS with Office 365 online apps such as SharePoint and OneDrive.

### Setting Up Microsoft Cloud App Security

#### Setup Cloud Discovery
Shadow IT visibility is critical. After your logs are analyzed, you can easily discover which cloud apps are being used, by which people, and on which devices.

1. Navigate to the [Microsoft Cloud App Security portal](https://portal.cloudappsecurity.com), and then sign in with tenant admin username and password, if necessary.
2. Click the settings cog and select **Cloud Discovery settings**. Choose **Automatic log upload**.
3. On the **Data sources** tab, add your sources.
4. On the **Log collectors** tab, configure the log collector.
5. Go to Discover > Snapshot report and follow the steps shown.

#### Connect Apps - Set Visibility, Protection and Governance Actions
App connectors leverage the APIs of app providers to enable greater visibility and control by Microsoft Cloud App Security across all apps in use.
1. In the [Microsoft Cloud App Security portal](https://portal.cloudappsecurity.com), click the settings cog and select **App connectors**.
2. On **Connected apps** page, click **+** (the plus button) and select **Office 365**.
3. In the Office 365 pop-up, click **Connect Office 365**.
4. Click **Test new** to validate connectivity with Office 365.
5. After Office 365 is displayed as successfully connected, click **Close**.

#### Create and Configure Policies
Policies help you monitor trends, see security threats, and generate customized reports and alerts. With policies, you can create governance actions, and set data loss prevention and file-sharing controls.
1. Go to **Control** > **Templates**.
2. Select a policy template from the list, and then choose **+** (Create policy).
3. Customize the policy (select filters, actions, and other settings), and then choose **Create**.
4. On the **Policies** tab, choose the policy to see the relevant matches (activities, files, alerts). **Tip**: To cover all your cloud environment security scenarios, create a policy for each risk category.

##### Create a new policy based on investigation results
When drilling down for specific information while investigating the **Activity log**, **Files** or **Accounts**, you can create a new policy based on the results of your investigation.
1. In the console, click **Investigate** followed by **Activity log**, **Files**, or **Accounts**.
2. Use the filters at the top of the page to limit the search results to the suspicious area. In the Activity log page, click **Activity** and select **Admin logon**.
3. Under **IP address**, select **Category** and set the value to not include IP address categories you've created for your recognized domains, such as your admin, corporate, and VPN IP addresses.
4. In the upper right corner of the console click **New policy from search**.
5. A create policy page opens containing the filters you used in your investigation. Modify the template as needed for your custom policy. Every property and field of this new investigation-based policy can be modified according to your needs.

#### Create a Cloud App Security access policy
Microsoft Cloud App Security access policies enable real-time monitoring and control over access to cloud apps based on user, location, device and app. You can create access policies for any device, including devices that are not domain joined and not managed by Windows Intune by rolling out client certificates to managed devices or by leveraging existing certificates, such as third-party MDM certificates.
1. In the Microsoft Cloud App Security portal, select **Control** followed by **Policies**.
2. On the **Policies** page, click **Create policy** and select **Access policy**.
3. In the **Access policy** window, assign a name for your policy, such as **Block access from unmanaged devices**.
4. Under **Activity source** in the **Activities matching all of the following** section, select additional activity filters to apply to the policy. These can include the following options:
   - **Device tags**: Use this filter to identify unmanaged devices.
   - **Location**: Use this filter to identify unknown (and therefore risky) locations.
   - **IP address**: Use this filter to filter per IP addresses or use previously assigned IP address tags.
   - **User agent tag**: Use this filter to enable the heuristic to identify mobile and desktop apps. This filter can be set to equals or does not equal Native client and should be tested against your mobile and desktop apps for each cloud app.
5. Under **Actions**, select one of the following:
   - **Allow**: Set this action to explicitly allow access according to the policy filters you set.
   - **Block**: Set this action to explicitly block access according to the policy filters you set.
6. Create an alert for each matching event with the policy's severity, set an alert limit, and select whether you want the alert as an email, a text message, or both.

## Exercise 5: Set up and configure Windows Defender Advanced Threat Protection

### Introduction
Windows Defender Advanced Threat Protection (Windows Defender ATP) is a platform designed to help enterprise networks prevent, detect, investigate, and respond to advanced threats.

Windows Defender Security Center gives enterprise security operations teams a central point of visibility to seamlessly secure networks. To help you maximize the effectiveness of the security platform, you can configure individual capabilities that surface in Windows Defender Security Center.

### Prerequisites
> [!Important]
> Set up Microsoft Cloud App Security before you go any further.

The following is required for successful set up:
- You have Windows Defender ATP subscription in your tenant.
- Any of the following Microsoft Volume licensing subscription offers includes Windows Defender ATP:
   - Windows 10 Enterprise E5
   - Windows 10 Education E5
   - Microsoft 365 E5 (which includes Windows 10 Enterprise E5)
- You have at least one client PC running Windows, preferably Windows 10 version 1803 or later to onboard to Windows Defender ATP.

### Setting Up Windows Defender ATP
Perform the following steps on the Windows 10 client PC, [Jump Host 01](https://labondemand.com/LabProfile/EditInstructions/45973).

#### Activate Windows Defender Security Center for the first time
1. Navigate to the [Windows Defender Security Center portal](https://securitycenter.windows.com). Sign in with your tenant global admin credentials, if necessary.
2. Since you're accessing Windows Defender Security Center for the first time, you'll be prompted to onboard your organization onto the Windows Defender ATP service. Click **Next** to begin the setup wizard.
3. On Step 3 of the wizard, select an appropriate data storage location for your tenant, e.g. US. Data collected by Windows Defender ATP service from your organization's end points is stored in a secure storage facility hosted in the Azure data center of your choice.
4. Click **Next**, then set the data retention policy in days (e.g. 180 days). Microsoft will store your data from your organization for up to 180 days.
5. Click **Next** until you reach **Step 4**.

#### Onboarding your Windows 10 endpoint to Windows Defender ATP
You're now ready to onboard your first endpoint/PC to Windows Defender ATP. In this exercise, you will onboard the Windows 10 client VM, which also serves as your jump host, to your tenant's Windows Defender ATP service.
1. Ensure you're on Step 4 of the Windows Defender ATP setup wizard. If you closed the browser or navigated away, return to the page by navigating to https://securitycenter.windows.com.
2. Set the **Deployment method** drop-down to **Local Script**, then click **Download package**.
3. Save the file (**WindowsDefenderATPOnboardingPackage.zip**) locally on the computer.
4. Extract the contents of the downloaded configuration package to a location on the endpoint you want to onboard (for example, the desktop). You should have a file named **WindowsDefenderATPOnboardingScript.cmd**.
5. Open an elevated command-line prompt on the endpoint and run the script:
   1. Go to Start and type **cmd**.
   2. Right-click the command prompt and select **Run as administrator**.
   3. Type the location of the script file. If you copied the file to the desktop, for example, type: **C:\<USER>\Desktop\WindowsDefenderATPOnboardingScript.cmd**, and then press **Enter**.
   5. At the prompt, press **Y**, and then press **Enter** to confirm.

#### Run a Detection Test on a newly onboarded computer
Run the following PowerShell script on a newly onboarded computer to verify that it is properly reporting to the Windows Defender ATP service.
1. Open an elevated command-line prompt on the computer and run the script: 
   1. Go to Start and type **cmd**.
   2. Right-click **Command Prompt** and select **Run as administrator**.
2. At the prompt, copy and run the following command:
   ```
   powershell.exe -NoExit -ExecutionPolicy Bypass -WindowStyle Hidden (New-Object System.Net.WebClient).DownloadFile('http://127.0.0.1/1.exe', 'C:\test-WDATP-test\invoice.exe');Start-Process 'C:\test-WDATP-test\invoice.exe'
   ```
   The Command Prompt window will close automatically.
3. When detected, the test will be marked as completed and a new alert will appear in the portal for the onboarded computer in approximately 2-10 minutes.

#### Enabling WD Antivirus Protection and WD Exploit Guard
Use PowerShell cmdlets to enable Windows Defender features:
1. Open an elevated command-line prompt on the computer and run the script: 
   1. Go to Start and type **cmd**.
   2. Right-click **Command Prompt** and select **Run as administrator**.
2. At the prompt, copy and run the following command:
   ```
   powershell.exe -NoExit -ExecutionPolicy Bypass -WindowStyle Hidden (New-Object System.Net.WebClient).DownloadFile('http://127.0.0.1/1.exe', 'C:\test-WDATP-test\invoice.exe');Start-Process 'C:\test-WDATP-test\invoice.exe'
   ```

You can check the status of all settings before you begin or during evaluation by running the **Get-MpPreference** PowerShell cmdlet.

Windows Defender AV will indicate a detection through standard Windows notifications. You can also review detections in the Windows Defender AV app. The Windows event log also records detection and engine events.

##### Cloud protection features 
- Enable the Windows Defender Cloud for near-instant protection and increased protection:</br>
  ```Set-MpPreference -MAPSReporting Advanced```
- Submit samples to increase group protection:</br>
  ```Set-MpPreference -SubmitSamplesConsent Always```
- Use the cloud to block new malware within seconds:</br>
  ```Set-MpPreference -DisableBlockAtFirstSeen 0```
- Scan all downloaded files and attachments:</br>
  ```Set-MpPreference -DisableIOAVProtection 0```
- Set cloud block level to 'High':</br>
  ```Set-MpPreference -CloudBlockLevel High```
- Set cloud block timeout to 1 minute:</br>
  ```Set-MpPreference -CloudExtendedTimeout 50```

##### Always-on protection (real-time scanning) 
Windows Defender AV scans files as soon as they are seen by Windows and will monitor running processes for known or suspected malicious behaviors. If the antivirus engine discovers malicious modification, it will immediately block the process or file from running.

- Constantly monitor files and processes for known malware modifications:</br>
  ```Set-MpPreference -DisableRealtimeMonitoring 0```
- Constantly monitor for known malware behaviors in running programs:</br>
  ```Set-MpPreference -DisableBehaviorMonitoring 0```
- Scan scripts as soon as they are seen or run:</br>
  ```Set-MpPreference -DisableScriptScanning 0```
- Scan removable drives as soon as they are inserted or mounted:</br>
  ```Set-MpPreference -DisableRemovableDriveScanning 0```
##### Potentially Unwanted Application protection
- Prevent grayware, adware, and other potentially unwanted apps from installing:</br>
  ```Set-MpPreference -PUAProtection Enabled```

##### Email and archive scanning
You can set Windows Defender Antivirus to automatically scan certain types of email files and archive files (such as .zip files) when they are seen by Windows.
- Scan email files and archives:</br>
  ```Set-MpPreference -DisableArchiveScanning 0 Set-MpPreference -DisableEmailScanning 0```

##### Manage product and protection updates
Adjust the frequency of updates by setting the following options and ensuring that your updates are managed either in System Center Configuration Manager, with Group Policy, or in Intune.
- Update signatures every day:</br>
  ```Set-MpPreference -SignatureUpdateInterval 8```
- Check to update signatures before running a scheduled scan:</br>
  ```Set-MpPreference -CheckForSignaturesBeforeRunningScan 1```

##### Advanced threat and exploit mitigation and prevention Controlled folder access 
- Prevent malicious and suspicious apps (such as ransomware) from making changes to protected folders with Controlled folder access:</br>
  ```Set-MpPreference -EnableControlledFolderAccess Enabled```
- Block connections to known bad IP addresses and other network connections with Network protection:</br>
  ```Set-MpPreference -EnableNetworkProtection Enabled```
- Apply a standard set of mitigations with Exploit protection:</br>
  ```Invoke-WebRequest https://demo.wd.microsoft.com/Content/ProcessMitigation.xml -OutFile ProcessMitigation.xml``` </br>
  ```Set-ProcessMitigation -PolicyFilePath ProcessMitigation.xml```
- Ensure notifications allow you to boot the PC into a specialized malware removal environment:</br>
  ```Set-MpPreference -UILockdown 0```

## Exercise 6: Set up and configure Azure Advanced Threat Protection

### Introduction
Azure Advanced Threat Protection (ATP) is a cloud service that helps protect your enterprise hybrid environments from multiple types of advanced targeted cyber-attacks and insider threats, utilizing technology that detects multiple suspicious activities and focuses on distinct phases of the cyber-attack kill chain. Azure ATP searches for three main types of attacks: Malicious attacks, abnormal behavior, and security issues and risks.

Azure ATP takes information from multiple data-sources such as logs and events in your network to learn the behavior of users and other entities in the organization and build a behavioral profile about them. Azure ATP can receive events and logs from:
- SIEM Integration
- Windows Event Forwarding (WEF)
- Directly from the Windows Event Collector (for the sensor)
- RADIUS Accounting from VPNs

### Prerequisites
- Administrative access to the Azure portal
- Access to on-premises domain controller
- Completion of Lab Exercise #5 (Set up and configure Windows Defender ATP) if you want to configure Azure ATP integration with Windows Defender ATP.

### Setting Up Azure Advanced Threat Protection
An Azure ATP workspace is required to set up Azure ATP for your tenant. Configuring Azure ATP is a multi-phased process requiring configuration for both on-premises components (i.e. domain controller) and cloud components (i.e. Azure ATP workspace).

> [!Important]
> Perform these steps in the domain controller VM, [DC01](https://labondemand.com/LabProfile/EditInstructions/45973)

### Configure Azure AD Sync with domain controller
Azure AD Sync allows you to join your on-premises Active Directory with your Azure Active Directory. Perform the following steps on your on-premises domain controller:
1. Sign in to the domain controller server with local user credentials (provided in the Resources tab). 
2. In a new browser window, browse to the [Azure management portal](https://portal.azure.com).
3. In the left navigation menu, select **Azure Active Directory**.
4. Under **Manage**, click **Azure AD Connect**.
5. Click **Download Azure AD Connect**.
6. Navigate to and double-click **AzureADConnect.msi**, and then downloaded locally.
7. On the Welcome screen, select the box agreeing to the licensing terms, then click **Continue**.
8. On the Express settings screen, click **Use express settings**.
9. On the **Connect to Azure AD** screen, enter the username and password of the M365 tenant global admin user. These credentials are available in the **Resources** tab.
10. Click **Next**.
11. On the Connect to AD DS screen, enter the credentials for the local domain controller admin user (the domain value can be in either NetBIOS or FQDN format): ```user name: contoso\administrator++ and password: +++pass@word1*```.
12. Click **Next**.
13. The **Azure AD sign-in configuration** page shows which Azure AD user authentication domains have been properly verified.
   If a domain is marked with **Not Added* or **Not Verified**, confirm that they are domains you won't be using to authenticate users in Azure AD. Ensure that the domains you do want to use for user authentication have been verified in Azure AD.

   **Tip**: If you have to make changes to your domains, you can leave this wizard open, make the necessary changes, then come back to this wizard and click the Refresh button in the lower right.
14. On the **Ready to configure** screen, click **Install**.
15. Ensure that the **Start the synchronization process as soon as configuration completes** checkbox is checked. This will immediately trigger a full synchronization to Azure AD of all users, groups, and contacts.
16. Ensure that the Exchange hybrid deployment checkbox is unchecked. This lab doesn't use Exchange in a hybrid scenario so this checkbox is unnecessary.
17. When the installation completes, click **Exit**.

### Create an Azure ATP Workspace
Azure ATP Workspace enables you to manage various Azure ATP functionality.
1. On the domain controller PC, browse to the [Azure ATP workspace portal](https://portal.atp.azure.com). If necessary, sign in with your M365 admin user account.
2. Click **Create Workspace**.
3. In the **Create New Workspace** dialog, name your workspace (e.g. "ContosoLab123" -- this name must be universally unique across all Azure ATP workspaces).
4. Decide whether it's your primary workspace or not. Since this is your first workspace, leave this option to **On**.
5. Select a **Geolocation** for your data center (e.g. North America).
6. Click **Create**.
7. In the **Welcome to Azure ATP workspace** page, click on the link, provide a user name and password to connect to your Active Directory forest.
8. Enter the local AD administrator user credentials in the Directory services page as follows:
   **Username**: administrator
   **Password**: pass@word1
   **Domain**: DC01.contoso.lab (this is the FQDN name of the local AD)
9. Click **Save**.

### Integrate Azure ATP with Windows Defender ATP
1. Navigate to the [Windows Defender admin center page](https://securitycenter.windows.com).
2. Click **Settings**, and then click **Advanced features**.
3. Turn on **Azure ATP integration**, and then click **Save Preferences**.
4. Return to the [Azure ATP admin page](https://portal.atp.azure.com).
5. Click the Manage Azure ATP user roles link to directly access the Azure Active Directory admin center to manage role groups.
6. Back on the Azure ATP management page, click the **name of the new workspace** to access the Azure ATP portal for that workspace.</br>
   Only the Primary workspace can be edited. To make changes to other workspaces, you can delete them and add them again. If you want to delete the primary workspace, you must first turn off integrations and set the workspace to be not Primary before it is able to be deleted.
   > [!NOTE]
   > To edit a Primary workspace, you must first turn off existing integrations in the workspace.</br>Deleted workspaces do not appear in the UI.

### Install Azure ATP Sensor on DC
Sensors are required to enable Azure ATP to learn the behavior of users and organizations to build robust profiles.
1. On the next page, **Download sensor setup**, click **Download**.
2. Save the package locally to the domain controller.
3. Copy the access key from the Azure ATP portal. The access key is required for the Azure ATP sensor to connect to your Azure ATP workspace and is a one-time-password for sensor deployment.
4. Click **Regenerate** to regenerate the new access key. The key is only used for initial registration of the sensor.
5. Copy the package to the dedicated server or domain controller onto which you are installing the Azure ATP sensor and verify the machine has connectivity to the US Azure ATP cloud service endpoint.
6. Run **Azure ATP sensor setup.exe** and follow the setup wizard.
7. On the Welcome page, select your language and click **Next**. The installation wizard automatically checks if the server is a domain controller or a dedicated server. Click **Next**.
8. Under **Configure the sensor**, enter the installation path and the access key that you copied from the previous step, based on your environment, and click **Install**.
9. Click **Launch** to open your browser and log in as admin to the Azure ATP workspace portal.
10. Go to **Configure** > **System** and select sensor.
11. Enter the description, domain controllers, capture network adapters, the domain synchronizer candidate, and then click **Save**.

### Configure detection exclusions and honeytoken accounts
Azure ATP enables the exclusion of specific IP addresses or users from a number of detections, and enables the configuration of honeytoken accounts, which are used as traps for malicious actors.
1. From the Azure ATP workspace portal, click the settings icon and select **Configuration**.
2. Under **Detection**, click **Entity tags**.
3. Under **Honeytoken accounts**, enter the Honeytoken account name and click the + sign. The Honeytoken accounts field is searchable and automatically displays entities in your network. Click **Save**.
4. Click **Exclusions** and enter a user account or IP address to be excluded from the detection for each type of threat.
 Click the plus sign (+). The **Add entity** (user or computer) field is searchable and will autofill with entities in your network. Click **Save**.

## Exercise 7: Set up Azure Security Center

### Introduction
Azure Security Center (ASC) provides unified security management and advanced threat protection across hybrid cloud workloads. It collects data from your Azure VMs and non-Azure computers to monitor for security vulnerabilities and threats. Data is collected using the Microsoft Monitoring Agent. The agent reads various security-related configurations and event logs from the onboarded machines and copies the data to ASC workspace for analysis.

### Prerequisites
For managing only Azure-based resources, the free tier of Azure Security Center is available to all organizations for no charge. Anyone with security administrator or higher level of directory access can administer Azure Security Center in free tier using the Azure Management Portal.
For managing non-Azure workloads (i.e. hybrid infrastructure and/or resources in third-party cloud services such as AWS), the following items are required:  

- Upgrade to Standard Tier
- Azure Subscription associated with the tenant
- Administrative user access to the Azure Subscription
- Completion of [Exercise 6: Set up and configure Azure Advanced Threat Protection](#exercise-6-set-up-and-configure-azure-advanced-threat-protection)

For this lab, we assume you have a hybrid infrastructure to manage. We assume the Windows Server-based domain controller PC is running on-premises and will be managed by ASC.

### Setting Up Azure Security Center
To leverage the full capabilities of Azure Security Center, you'll need to upgrade ASC from Free Tier to Standard Tier. This upgrade will require an Azure Subscription that is associated with your tenant/environment. You must have administrative access to the Azure Subscription.

#### Create an Azure Subscription from Azure Pass
An Azure Pass promo code is provided for you to use for the purpose of this lab. The code can be found in the Resources tab. Follow these steps to redeem your Azure Azure pass for an Azure subscription.
1. On the Windows 10 client PC, navigate to the [Microsoft Azure Pass](https://www.microsoftazurepass.com) page. Ensure that you are signed in as your tenant's global admin user.
2. Click **Confirm Microsoft Account**.
3. Copy and paste the Azure Pass promo code in the **Enter Promo Code** textbox, and then click **Claim Promo Code**.
4. In the next page, review your free Azure Subscription details, then click **Activate**.
5. In the **About you** page, update your personal information (optional), and then click **Next**.
6. Agree to the terms and conditions, and then click **Sign up**. When the signup process is complete, you'll be redirected to the Azure management portal automatically.

#### Create a Security Center workspace in your tenant
The first step in setting up Azure Security Center is creating a workspace.
1. Go to the [Azure Management Portal page](https://portal.azure.com) and sign in as the tenant global admin user.
2. In the left navigation pane, click **Security Center**.
3. In the **Getting started** page, click **Start trial** to begin. By doing this, you have upgraded your tenant's ASC service from Free Tier to Standard Tier.
4. Click **Install agents**. This will enable the Microsoft Monitoring Agent to be automatically installed on all VMs hosted in the Azure Subscription associated with this ASC workspace.

#### Define Security Policies and respond to alerts
ASC automatically creates a default security policy for each of your Azure subscriptions. Security policies are comprised of recommendations that you can turn on or turn off according to the security requirements of that subscription. To make changes to the default security policy, you need to be an owner, contributor, or security administrator of the subscription.
1. At the Security Center main menu, select **Security policy**.
2. Select the Azure Subscription you want to use.
3. For each security configuration you want to monitor, select **On**. Security Center will continuously assess the configuration of your environment and when vulnerability exists, Security Center will generate a security recommendation. Select **Off** if the security configuration is not recommended or not relevant. After selecting the policies that are applicable to your environment, click **Save**.
4. Return to the **Security Center - Overview** page.
5. On the overview dashboard, review VM and computer security recommendations by selecting **Overview** > **Compute & apps**.
6. On Security Center dashboard, review networking by selecting **Overview** > **Networking**.
7. On Security Center dashboard, review data and storage by selecting **Overview** > **Data & storage**.
8. On Security Center dashboard, review identity and access by selecting **Overview** > **Identity & Access**.
9. On Security Center dashboard, click Security alerts tile to see alert details. Click **Filter** on the **Security Alerts**. The filter opens and you select the date, state, and severity values you wish to see. Select a security alert to learn more about the event(s) that triggered the alert and what, if any, steps you need to take to remediate an attack.
Azure Security Center continues to monitor all critical workloads, making security recommendations for associated computers, VMs, data, and identities.

#### Onboard On-Premises Computers to Azure Security Center
In addition to Azure-hosted virtual machines, you can also monitor on-premises computers. This is done through a service application running on the computers, called Microsoft Monitoring Agent. In this exercise, you'll onboard your lab's domain controller PC to your tenant's Azure Security Center workspace that you created earlier.

*Perform these steps in the Domain Controller PC.*

1. Log in to the [Azure Portal](https://portal.azure.com) as tenant global admin user.
2. In the Azure portal left navigation, select **Security Center**.
3. Under **Resource Security Hygiene**, select **Compute & apps**.
4. Click the **+ Add Computers** link at the top of the blade.
5. A Log Analytics workspace (also known as an OMS Workspace) is required to onboard non-Azure computers to Security Center. If you already have a Log Analytics workspace created in your subscription, you will see it listed here. Otherwise, you'll have to create one to proceed. To create a new Log Analytics workspace, click **add a new workspace** link.
6. Click **OMS Workspace**, and then fill in the log analytics workspace creation form. The OMS workspace name has to be globally unique across Azure.
7. Click **OK** to finish creating the workspace.
8. Back in the **Add new non-Azure computers** blade, click **+ Add Computers** next to the newly created workspace.
9. In the **Direct Agent** blade, select the **Download Windows Agent (64 bit)** link to download the setup file.
10. Click **Run** to open the Microsoft Monitoring Agent Windows Agent Setup wizard.
11. On the Welcome page, click **Next**.
12. On the License Terms page, read the license, and then select **I Agree**.
13. On the Destination Folder page, change or keep the default installation folder, and then select **Next**.
14. On the Agent Setup Options page, choose **Connect the agent to Azure Log Analytics (OMS)**, then select **Next**.
15. Copy/paste the **Workspace ID** and **Primary Key** values from the **Direct Agent** blade in Security Center to the setup form, and then select **Next**.
16. On the Ready to Install page, review your choices and then select **Install**.
17. On the Configuration completed successfully page, select **Finish**.

When complete, the Microsoft Monitoring Agent can be found in the onboarded computer's Control Panel. The log analytics service will start collecting data from the computer immediately.

#### View data collected in Log Analytics
Now that you have enabled data collection, lets run a simple log search example to see some data from the onboarded computer.
1. In the Azure Management Portal left navigation, click **All services**, type **log**, and then select **Log Analytics**.
2. Select the Log Analytics workspace name.
3. Under **General**, select **Logs** to load a new query page.
4. In the **Type your query here…** text box, type **Perf** (without any punctuation or carriage return), and then click **Run**.
5. From the list of results, click **>** to expand an item and see details.
6. Note the computer name.

Now that you are collecting operational and performance data from both cloud and on-premises computers, you can easily begin exploring, analyzing, and taking action on data and security related issues in your organization.
