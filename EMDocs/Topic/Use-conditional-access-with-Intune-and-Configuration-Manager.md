---
title: Use conditional access with Intune and Configuration Manager
ms.custom: na
ms.reviewer: na
ms.service: microsoft-intune
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5b021c5a-b7a4-4ea5-957d-d6f2cdc1812c
author: karthikaraman
---
# Use conditional access with Intune and Configuration Manager
In this solution, you are already using System Center Configuration Manager and Microsoft Exchange Server – with on-premises, Exchange Online, or a hybrid deployment of both – in your company to manage email access. This solution combines your existing Configuration Manager environment with Intune to safely manage email access on all types of devices, regardless of their location.

> [!TIP]
> Get a downloadable copy of this entire topic at the [TechNet Gallery](https://gallery.technet.microsoft.com/Deploying-Enterprise-16499404).

## <a name="ExchangeOnPrem"></a>Exchange Server on-premises
If you are already using System Center Configuration Manager and Exchange in your on-premises infrastructure, you can incorporate Intune to manage email access and protect email data on mobile devices. The high-level process for implementing this solution is as follows:

-   Configure the On-Premises Intune Exchange Connector through the Configuration Manager console, which will let Configuration Manager communicate with the Exchange Server that hosts the mobile devices’ mailboxes.

-   Run a full synchronization of the Exchange Server Connector to discover users and to inventory all of the mobile device Exchange ActiveSync IDs (EASIDs) that are connecting to Exchange Server on-premises.

-   Create user collections for groups of users that will either be targeted or exempted from the conditional access policy. Then create the compliance policies that define the rules and settings that a device must comply with in order to be considered compliant by conditional access polices.

-   Begin enforcing conditional access.

### Conditional access control flow for Exchange Server on-premises
This diagram shows the control flow for clients attempting to access email in Exchange on-premises.

![](../Image/Hybrid_on-prem_CA_architecture.png)

-   Microsoft Intune: Manages the compliance and conditional access policies for the device

-   Microsoft Azure Active Directory: Authenticates user and provides device compliance status

-   Configuration Manager: Manages device enrollment and provides reporting

-   Exchange on-premises: Enforces access to email based on the device state

### Prerequisites
Before you proceed, make sure your environment includes these requirements for implementing this solution.

> [!NOTE]
> If you have already configured Configuration Manager to manage mobile devices through the Intune service, you can proceed to the [Deployment Steps](#DeploySteps).

-   Verify that you meet the [hardware requirements for the on-premises connector](https://technet.microsoft.com/en-us/library/dn646950.aspx#BKMK_ExchanceConnectorReqs).

-   Verify that you are running System Center 2012 R2 Configuration Manager SP1 with cumulative update 1 or later.

-   Ensure that the [Exchange Web Services (EWS) endpoint ](https://technet.microsoft.com/library/hh529912(v=exchg.150).aspx)is configured properly for discovery. If necessary, contact your Configuration Manager Support team for a tool that can help identify EWS connection issues. EWS lets developers interact with Exchange mailboxes and contents by using standard HTTP.

-   Install and assign Exchange services to a [valid digital certificate ](https://technet.microsoft.com/library/dd351044(v=exchg.150).aspx) purchased from a trusted public certificate authority.

-   Configure an account (local or domain admin) with permissions to run the following Exchange Server cmdlets:

    **Clear-ActiveSyncDevice**

    **Get-ActiveSyncDevice**

    **Get-ActiveSyncDeviceAccessRule**

    **Get-ActiveSyncDeviceStatistics**

    **Get-ActiveSyncMailboxPolicy**

    **Get-ActiveSyncOrganizationSettings**

    **Get-ExchangeServer**

    **Get-Recipient**

    **Set-ADServerSettings**

    **Set-ActiveSyncDeviceAccessRule**

    **Set-ActiveSyncMailboxPolicy**

    **Set-CASMailbox**

    **New-ActiveSyncDeviceAccessRule**

    **New-ActiveSyncMailboxPolicy**

    **Remove-ActiveSyncDevice**

> [!IMPORTANT]
> If you try to install or use the Exchange Server connector without the required cmdlets, you will see an error logged with the message Invoking cmdlet &lt;cmdlet&gt; failed in the EasDisc.log file on the site server computer.

### <a name="DeploySteps"></a>Deployment Steps
Follow these steps to deploy the Exchange on-premises solution:

#### Step 1: Ensure that Intune Connector role is installed.
Make sure that the Intune Connector role is installed so that Configuration Manager can interact with Intune. See [Manage Mobile Devices with Configuration Manager and Intune](https://technet.microsoft.com/en-us/library/JJ884158.aspx) for more information.

#### Step 2: Install and configure an Exchange Server connector.
Configuration Manager supports only one connector in an Exchange organization.

> [!IMPORTANT]
> Before you install the Exchange Server connector, confirm that Configuration Manager supports the version of Microsoft Exchange that you are using. For more information, see [Supported Configurations for Configuration Manager](https://technet.microsoft.com/en-us/library/gg682077.aspx).

Follow the steps at [How to Manage Mobile Devices by Using Configuration Manager and Exchange](https://technet.microsoft.com/en-us/library/gg682001.aspx) to install and configure the Exchange Server connector.

#### Step 3: Run a full synchronization to discover users.

1.  In the Configuration Manager console, click **Administration**, expand **Hierarchy Configuration**, and then select **Exchange Server Connectors**.

2.  Select the Exchange Server Connector that you installed in Step 2.

3.  Click **Synchronize Now**.

    ![](../Image/HybridOnpremRunFullSync.png)

This full synchronization can take several hours to complete, depending on the number of devices. A full synchronization will run once every 24 hours by default. A delta synchronization discovers device connections since the previous full synchronization and occurs per the interval you set during installation of the Exchange Server Connector. This ensures that new users and new Exchange users are discovered quickly so that conditional access can be applied.

Using the Configuration Manager Trace Log Tool, you can open the EasDisc.log file (located in the **Microsoft Configuration Manager/Logs** folder where you installed Configuration Manager) to verify that the connector is running and querying for device connections. After full sync completes, it will inventory all of the mobile device Exchange ActiveSync IDs (EASIDs) that are connecting to Exchange On-premises.

#### Step 4: Create user collections.
Determine the Intune user groups for whom the conditional access policy will be targeted. Then, create user collections for groups of users that will either be targeted or exempted from the conditional access policy. You will specify these groups when you enforce conditional access later on.

Follow the steps at [How to Create Collections in Configuration Manager](https://technet.microsoft.com/en-us/library/gg712295.aspx) to create user collections.

#### <a name="Step_5"></a>Step 5: Create compliance policies and deploy to users.
Compliance policies define the rules and settings that a device must comply with in order to be considered compliant by conditional access polices. Follow the steps at [Compliance Policies in Configuration Manager](https://technet.microsoft.com/en-us/library/mt131417.aspx) to create compliance policies.

> [!NOTE]
> If you want the ability to remove all corporate email from an iOS device after it is no longer part of your company, you must create and deploy an email profile and then set the compliance policy that specifies that email profiles are managed by Intune. You must deploy the email profile to the same set of users that you target with this compliance policy.
> 
> ![](../Image/HybridOnpremExchSrvrWizard6.PNG)
> 
> If you specify this compliance policy, a user who has already set up their email account must manually remove it and then Intune will add it back in through the registration process described in [End-user experience of conditional access](../Topic/End-user-experience-of-conditional-access.md).

After the compliance policy is created, select the compliance policy name in the list and click **Deploy**.

#### Step 6: Configure conditional access policy.
First, decide how and when you want to enforce conditional access and which employees will be affected. Then, follow the steps at [Conditional Access for Exchange Email in Configuration Manager](https://technet.microsoft.com/en-us/library/mt131421.aspx) to configure the conditional access policy for Exchange on-premises.

#### Step 7: Monitor enrollments and enforce conditional access.
If you already have a significant number of users enrolled in Intune and compliant, you can start enforcing conditional access by rolling it out to about 500 users per day. This will take about 4 to 5 months for 70,000 users and lets you sort out any issues that might arise without restricting email access to too many users at the same time.

If you don’t have a large number of users already enrolled in Intune, conditional access provides them with a guided experience for enrollment, as described in [End-user experience of conditional access](../Topic/End-user-experience-of-conditional-access.md).

### Verification Steps
Using the Configuration Manager Trace Log Tool, open the EasDisc.log file (located in the Microsoft Configuration Manager/Logs folder where you installed Configuration Manager). Search the log file for “Exchange Connector” to find information about whether the Exchange Connector is running and how many devices are connected.

![](../Image/HybridOnpremEasDiscLogSample.PNG)

The Configuration Manager Trace Log Tool is included in the [System Center 2012 R2 Configuration Manager Toolkit](http://www.microsoft.com/en-us/download/details.aspx?id=36213).

### Reporting
You can use the Configuration Manager console to view specific information about devices that have been discovered by the Exchange Connector. For devices on which conditional access is enforced, you can view the current status of each device, the last time the device was connected with the Exchange server, and so on.

In the Configuration Manager console, click **Assets and Compliance** and then click **Devices**. You can view the current status of each device (Blocked or Allowed) in the **Exchange Access State** column. Add this column if not already shown by right-clicking in the column title bar area. You can also view the last successful synchronization time for each device as reported by Exchange by adding the **Last Success Sync Time To Exchange Server** column.

![](../Image/HybridOnpremVerifyDevicesState.png)

If you are running SQL Server Reporting Services (SSRS), you can view a conditional access report that shows the compliance state of devices, whether there is an Exchange connector installed and running, and the EAS Access state. It will also provide information about Active Directory registration, EAS activation, as well as the device owner.

![](../Image/HybridReports_CA.png)

To view SSRS reports, you must have a reporting role installed on the primary server:

1.  In Configuration Manager, click **Administration**, click **Hierarchy configuration**, click **Site Configuration**, and then click **Servers and Site System Roles**.

2.  Select a server and click **Add Site System Role** to open the Add Site System Role wizard.

3.  On the System Role Selection page, select the **Reporting services point** checkbox. The reporting services point displays reports related to client management.

4.  Click **Next**.

The following shows the deployment status of the configuration policy:

![](../Image/HybridReportsDeploymentStatus.png)

#### Latency
A device is blocked as soon as it is discovered by the Exchange connector. The latency of blocking depends on the configured intervals for Full synchronization and delta synchronization and the time in between these intervals when the device connects to the Exchange server. By default, a Full synchronization occurs every 24 hours while a delta synchronization occurs every 240 minutes. During this latency period, a device might be considered compliant.

## <a name="ExchangeOnline"></a>Exchange Online
If you are already using System Center Configuration Manager and Exchange Online, you can incorporate Intune to manage email access and protect email data on mobile devices. The high-level process for implementing this solution is as follows:

-   Create the compliance policies that define the rules and settings that a device must comply with in order to be considered compliant by conditional access polices.

-   Begin enforcing conditional access.

-   Optionally, configure the Exchange Server connector for Exchange Online
    This connector is required for reporting purposes only. It is not required to enable conditional access.

### Conditional access control flow for Exchange Online
This diagram shows the control flow for clients attempting to access email in Exchange Online. A and B might be performed prior to enforcing conditional access.

![](../Image/Hybrid_Exchange-Online_CA_architecture.png)

-   Microsoft Intune: Manages the compliance and conditional access policies for the device

-   Microsoft Azure Active Directory: Authenticates user and provides device compliance status

-   Configuration Manager: Manages device enrollment and provides reporting, if enabled

-   Exchange Online: Enforces access to email based on the device state

### Prerequisites
Before you proceed, make sure your environment includes these requirements for implementing this solution.

-   Install and assign Exchange services to a [valid digital certificate ](https://technet.microsoft.com/library/dd351044(v=exchg.150).aspx) purchased from a trusted public certificate authority.

-   Verify that you are running System Center 2012 R2 Configuration Manager SP1 with cumulative update 1 or later.

-   Configure an account (local or domain admin) with permissions to run the following Exchange Server cmdlets:

    **Clear-ActiveSyncDevice**

    **Get-ActiveSyncDevice**

    **Get-ActiveSyncDeviceAccessRule**

    **Get-ActiveSyncDeviceStatistics**

    **Get-ActiveSyncMailboxPolicy**

    **Get-ActiveSyncOrganizationSettings**

    **Get-ExchangeServer**

    **Get-Recipient**

    **Set-ADServerSettings**

    **Set-ActiveSyncDeviceAccessRule**

    **Set-ActiveSyncMailboxPolicy**

    **Set-CASMailbox**

    **New-ActiveSyncDeviceAccessRule**

    **New-ActiveSyncMailboxPolicy**

    **Remove-ActiveSyncDevice**

### Deployment Steps
Follow these steps to deploy the Exchange Online solution:

#### Step 1: Create compliance policies and deploy to users.
Compliance policies define the rules and settings that a device must comply with in order to be considered compliant by conditional access polices. Follow the steps at [Compliance Policies in Configuration Manager](https://technet.microsoft.com/en-us/library/mt131417.aspx)to create compliance policies.

> [!NOTE]
> If you want the ability to remove all corporate email from an iOS device after it is no longer part of your company, you must create and deploy an email profile and then set the compliance policy that specifies that email profiles are managed by Intune. You must deploy the email profile to the same set of users that you target with this compliance policy.
> 
> ![](../Image/HybridOnpremExchSrvrWizard6.PNG)
> 
> If you specify this compliance policy, a user who has already set up their email account must manually remove it and then Intune will add it back in through the registration process described in [End-user experience of conditional access](../Topic/End-user-experience-of-conditional-access.md).

After the compliance policy is created, select the compliance policy name in the list and click **Deploy**.

#### Step 2: Configure conditional access policy.
First, decide how and when you want to enforce conditional access and which employees will be affected. Then, follow the steps at [Conditional Access for Exchange Email in Configuration Manager](https://technet.microsoft.com/en-us/library/mt131421.aspx) to enable the conditional access policy for Exchange Online.

> [!NOTE]
> Conditional access policy must be configured in the Intune console. These steps begin by accessing the Intune console through Configuration Manager. If prompted, log in using the same credentials that were used to set up the connector between Configuration Manager and Intune.

#### Step 3: (*Optional*) Install and configure an Exchange Server connector.
Configuration Manager supports only one connector in an Exchange organization.

> [!IMPORTANT]
> Before you install the Exchange Server connector, confirm that Configuration Manager supports the version of Microsoft Exchange that you are using. For more information, see [Supported Configurations for Configuration Manager](https://technet.microsoft.com/en-us/library/gg682077.aspx).

Follow the steps at [How to Manage Mobile Devices by Using Configuration Manager and Exchange](https://technet.microsoft.com/en-us/library/gg682001.aspx) to install and configure the Exchange Server connector.

### Verification Steps
If you configured the optional Exchange Server connector for this solution, you can use the Configuration Manager Trace Log Tool to open the EasDisc.log file (located in the Microsoft Configuration Manager/Logs folder where you installed Configuration Manager). Search the log file for “Exchange Connector” to find information about whether the Exchange Connector is running and how many devices are connected.

![](../Image/HybridOnpremEasDiscLogSample.PNG)

The Configuration Manager Trace Log Tool is included in the [System Center 2012 R2 Configuration Manager Toolkit](http://www.microsoft.com/en-us/download/details.aspx?id=36213).

### Reporting
If you configured the optional Exchange Server connector, you can use the Configuration Manager console to view specific information about devices that have been discovered by the Exchange Connector. For devices on which conditional access is enforced, you can view the current status of each device, the last time the device was connected with the Exchange server, and so on.

In the Configuration Manager console, click **Assets and Compliance** and then click **Devices**. You can view the current status of each device (Quarantined or Allowed) in the **Exchange Access State** column. Add this column if not already shown by right-clicking in the column title bar area. You can also view the last successful synchronization time for each device as reported by Exchange by adding the **Last Success Sync Time To Exchange Server** column.

![](../Image/HybridOnpremVerifyDevicesState.png)

If you are running SQL Server Reporting Services (SSRS), you can view a conditional access report that shows the compliance state of devices, whether there is an Exchange connector installed and running, and the EAS Access state. It will also provide information about Active Directory registration, EAS activation, as well as the device owner.

![](../Image/HybridReports_CA.png)

To view SSRS reports, you must have a reporting role installed on the primary server:

1.  In Configuration Manager, click **Administration &gt; Hierarchy configuration &gt; Site Configuration &gt; Servers and Site System Roles**.

2.  Select a server and click **Add Site System Role** to open the Add Site System Role wizard.

3.  On the System Role Selection page, select the **Reporting services point** checkbox. The reporting services point displays reports related to client management.

4.  Click **Next**.

The following shows the deployment status of the configuration policy:

![](../Image/HybridReportsDeploymentStatus.png)

#### Latency
Devices that use modern authentication have conditional access applied immediately. For devices connecting through the EAS protocol, there can be a lag time of up to six hours before conditional access is enforced, based on the default setting. During that time, a device might be considered compliant.

## Coexistence of Exchange Server on-premises and Exchange Online
An environment in which Exchange on-premises and Exchange Online are both used to manage email profiles offers companies the ability to extend the feature-rich experience and administrative control they have with their existing on-premises Microsoft Exchange organization to the cloud. This "hybrid" type of deployment provides the seamless look and feel of a single Exchange organization between an on-premises Exchange Server 2013 organization and Exchange Online in Microsoft Office 365. In addition, this type of deployment can serve as an intermediate step to moving completely to an Exchange Online organization.

If you are already using Configuration Manager along with a coexistence of Exchange on-premises and Exchange Online, you can incorporate Intune to manage email access and protect email data on mobile devices. You can implement this solution by following the instructions above for implementing each solution separately.

### Prerequisites
To configure a coexistence type of environment that implements both Exchange on-premises and Exchange Online, your existing Exchange organization must meet certain requirements. If you don't meet these requirements, you won't be able to complete the steps necessary to configure a hybrid deployment between your on-premises Exchange organization and the Exchange Online organization in Microsoft Office 365.

See [Hybrid deployment prerequisites](https://technet.microsoft.com/en-us/library/hh534377.aspx) to review the requirements for creating and configuring this type of environment.

### Deployment Steps
To deploy a coexistence solution, follow the steps above for deploying both the [Exchange Server on-premises](#ExchangeOnPrem) and [Exchange Online](#ExchangeOnline) solutions.

## See Also
[Learn how to deploy a solution for protecting company email and documents](../Topic/Learn-how-to-deploy-a-solution-for-protecting-company-email-and-documents.md)
[End-user experience of conditional access](../Topic/End-user-experience-of-conditional-access.md)

