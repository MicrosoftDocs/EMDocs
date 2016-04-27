---
title: FastTrack Center Benefit Process for Enterprise Mobility Suite - Microsoft's responsibilities
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 
robots: noindex
---
# FastTrack Center Benefit Process for Enterprise Mobility Suite - Microsoft's responsibilities
The following sections describe what you can expect of Microsoft when your organization is using the [FastTrack Center Benefit for Enterprise Mobility Suite (EMS)](fasttrack-center-benefit-for-enterprise-mobility-suite-ems.md) to get Azure Active Directory Premium, Microsoft Intune and/or Azure Rights Management ready for use.

To read about the other parts of the FastTrack onboarding process, see [FastTrack Center Benefit Process for Enterprise Mobility Suite (EMS)](fasttrack-center-benefit-process-for-enterprise-mobility-suite-ems.md).


## General

-   Provide remote support assistance to you for the required configuration activities as listed in the detailed phase descriptions.

-   Provide available documentation and software tools, admin consoles, and scripts to help you reduce or eliminate configuration tasks.

## Initiate phase

-   Contact you within 30 days of the purchase of eligible licenses for a new tenant.

-   Work with you to begin onboarding.

-   Define which eligible services you want to onboard.

## Assess phase

-   Provide an administrative overview.

-   Provide guidance about:

    -   DNS, network, and infrastructure needs.

    -   Client needs (Internet browser, client operating system, and services' needs).

    -   User identity and provisioning.

    -   Enabling eligible services that have been purchased and defined to be part of the onboarding.

-   Establish the timeline for remediation activities.

-   Provide a remediation checklist.

## Remediate phase

-   Hold conference calls with you according to the agreed-upon schedule to review the progress of the remediation activities.

-   Assist with running tools to identify and remediate issues, and with interpreting the results.

## Enable phase
Provide guidance about:

-   Activating your Microsoft online service tenant.

-   Configuring TCP/IP protocols and firewall ports.

-   Configuring DNS for eligible services.

-   Validating connectivity to Microsoft online services.

-   For a single-forest environment:

    -   Installing a directory synchronization server between your Active Directory Domain Services (AD DS) and the eligible Microsoft online service(s), if required.

    -   Configuring password synchronization (password hash) to Microsoft Intune (Azure Active Directory) with the Azure Active Directory Connect tool.

        > [!NOTE]
        > Development and implementation for custom rules extensions are out of scope.

-   For a single forest when the target is federated identities: Installing and configuring Active Directory Federation Services (AD FS) for local domain authentication with Microsoft Intune in a single-site, fault-tolerant configuration, if required.

    > [!NOTE]
    > For all multiple forest configurations, AD FS deployments are out of scope.

-   Testing single sign-on (SSO) functionality if deployed.

### Enable phase - Azure Active Directory Premium

Provide guidance about:

-   Activating your Microsoft Azure Active Directory Premium tenant.

-   Configuring firewall ports.

-   Configuring DNS for eligible services.

-   Validating connectivity to Microsoft Azure Active Directory Premium services.

-   For a single-forest environment:

    -   Installing a directory synchronization between your Active Directory Domain Services (AD DS) and Azure Active Directory Connect, if required.

    -   Configuring password synchronization with the Azure Active Directory Connect tool.

-   For a multiple forest environment:

    -   Install Azure Active Directory Connect synchronization, set up for multiple forest scenarios. Note that password hash sync and password writeback support multiple forest.  However, other writeback scenarios are not supported.

    -   Configure synchronization between on-premises Active Directory forests and Microsoft Azure Active Directory Premium directory (Azure Active Directory).

        > [!NOTE] Development and implementation for custom rules extensions are out of scope.

-   For a single forest when the target is federated identities: Installing and configuring Active Directory Federation Services (AD FS) for local domain authentication with Microsoft Azure AD Premium in a single-site, fault-tolerant configuration, if required.

    > [!NOTE] For all multiple forest configurations, AD FS deployments are out of scope.

-   Testing single sign-on (SSO) functionality, if deployed.

### Enable phase - Azure Active Directory Premium--with Azure Active Directory Connect and Active Directory Federation Services (AD FS)

Provide guidance about setting up:

-   User provisioning, including licensing.

-   Azure Active Directory Connect directory synchronization (with password writeback and password hash sync).

-   Active Directory Federation Services (AD FS).

- Self-Service Password Reset (SSPR).

- Azure Multi-Factor Authentication (MFA).

- One integrated application, which can include Single Sign-On for SaaS applications.

- Usage and security reports to administrators.

- Self Service Group Management (SSGM).

- Application proxy.

- Administrator notifications.

- Customized logon screen, including logo, text and images.
 
### Enable phase - Microsoft Intune
Provide guidance with:

-   Licensing your end users. When needed, we’ll also provide assistance on how to activate volume licenses for your Microsoft cloud service tenant.

-   Configuring identities to be used by Microsoft Intune, by either leveraging your on-premise Active Directory or cloud identities.

-   Adding users to your Microsoft Intune subscription, defining IT Admin roles, and creating user and device groups.

-   Based on your management needs, configuring your Mobile Device Management authority:

    -   Set Microsoft Intune as your MDM authority when Microsoft Intune is your only MDM solution or is in conjunction with Mobile Device Management for Office 365.

    -   If you have an existing implementation of System Center Configuration Manager and you are looking to expand its management capabilities with Microsoft Intune, set Configuration Manager as your MDM authority.

        > [!NOTE] If you are only looking to leverage Mobile Application Management over your end-users' owned devices, shared, or kiosk-type devices, setting up an MDM authority is not required.

-   If Mobile Device Management is in your scope, we’ll provide guidance with:

    -   Configuring tests groups to be used to validate MDM management policies.

    -   Configuring MDM management policies and services such as:

        -   Application deployment for each supported platform through web links or deep links.

        -   Conditional access policies.

        -   Deployment of e-mail profiles.

        -   Setting up the Microsoft Intune Exchange Connector, when applicable.

    -   Enrolling up to two test devices of each supported platform to your Microsoft Intune or Configuration Manager with Microsoft Intune service.

    -   Using hardware and software inventory reports.

-   If Mobile Application Management (MAM) is in your scope, or if you are looking to complement your existing third-party MDM solution with MAM policies, we’ll provide guidance with:

    -   Configuring MAM policies for each supported platform.

    -   Configuring conditional access policies for managed apps.

    -   Targeting the appropriate user groups with the above MAM policies.

    -   Using managed-applications usage reports.

-   If PC management is in your scope, we’ll provide guidance with:

    -   When needed, installing the Intune client software.

    -   Using the software and hardware reports available in Intune.

### Enable phase - Azure Right Management Premium

Provide guidance about:

-   Activating your Azure RMS tenant.

-   Adding additional information security administrators to manage templates.

-   Assigning a super user account to Azure RMS.

-   Licensing two pilot users for Azure RMS.

-   Configuring two test distribution groups to validate policies.

-   Configuring one custom Azure RMS template for your directory.

-   Providing guidance in setting up SharePoint Online and Exchange Online integration with Azure RMS, including:

    -   Configuring and validating Exchange Online integration with Azure RMS.

    -   Setting up one test mail flow rule to encrypt sensitive messages sent to recipients outside your organization.

    -   Configuring and validating SharePoint Online protection of one test Library to be protected with Azure RMS.

-   Configuring one server on-premises with the RMS Connector, when applicable:

    -   Configuring and validating Exchange 2013/2010 on-premises integration with Azure RMS.

    -   Setting up one test mail flow rule to encrypt sensitive messages sent to recipients outside your organization using the Connector.

    -   Configuring and Validating SharePoint 2013/2010 on-premises protection of one test Library to be protected with Azure RMS.

-   Setting up RMS Sharing Application for Windows and non-Windows devices.

Read about the next part of the FastTrack onboarding process: [Customer responsibilities](fasttrack-center-benefit-process-for-ems-your-responsibilities.md)

### Want to learn more?
See [Enterprise Mobility Suite](https://www.microsoft.com/en-us/server-cloud/enterprise-mobility/overview.aspx).

