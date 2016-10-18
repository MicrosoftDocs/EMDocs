---
# required metadata

title: Microsoft responsibilities
description: Microsoft's responsibilities when customers are using the FastTrack Center Benefit
keywords:
author: staciebarker
manager: angrobe
ms.date: 10/02/2016
ms.topic: article
ms.prod:
ms.service:
ms.technology:
ms.assetid: c8fd871e-f1bc-43ec-a5f3-ad025df9b026

# optional metadata

ROBOTS: noindex
#audience:
#ms.devlang:
ms.reviewer:
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Microsoft responsibilities

Microsoft has the following responsibilities during onboarding.

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

-   For a multiple-forest environment:

    -   Install Azure Active Directory Connect synchronization, set up for multiple forest scenarios. Note that password hash sync and password writeback support multiple forest.  However, other writeback scenarios are not supported.

    -   Configure synchronization between on-premises Active Directory forests and Microsoft Azure Active Directory Premium directory (Azure Active Directory).

        > [!NOTE]
        > Development and implementation for custom rules extensions are out of scope.

-   For a single forest when the target is federated identities: Installing and configuring Active Directory Federation Services (AD FS) for local domain authentication with Microsoft Azure Active Directory Premium in a single-site, fault-tolerant configuration, if required.

    > [!NOTE]
    > For all multiple forest configurations, AD FS deployments are out of scope.

-   Testing single sign-on (SSO) functionality, if deployed.

### Enable phase - Azure Active Directory Premium--with Azure Active Directory Connect and Active Directory Federation Services (AD FS)

Provide guidance about setting up:

-   User provisioning, including licensing.

-   Azure Active Directory Connect directory synchronization (with password writeback and password hash sync).

  - Self-Service Password Reset (SSPR).

  - Azure Multi-Factor Authentication (MFA).

  - One Software as a Service (SaaS) application integration with Single Sign On (SSO) from the [Azure Active Directory Marketplace](https://azure.microsoft.com/marketplace/active-directory/).

  - Customized logon screen, including logo, text and images.

  - Self-Service & Dynamic Groups (Groups).

  - Azure Active Directory Application Proxy.

  - Azure Active Directory Connect Health.

  - Identity Protection.

  - Privileged Identity Management.

  - Usage and security reports to administrators.

  - Administrative notifications and alerts.

### Enable phase - Microsoft Intune
Provide guidance with:

-   Licensing your end users. When needed, we’ll also provide assistance on how to activate volume licenses for your Microsoft cloud service tenant.

-   Configuring identities to be used by Microsoft Intune, by either leveraging your on-premise Active Directory or cloud identities.

-   Adding users to your Microsoft Intune subscription, defining IT Admin roles, and creating user and device groups.

-   Based on your management needs, configuring your Mobile Device Management authority:

    -   Set Microsoft Intune as your MDM authority when Microsoft Intune is your only MDM solution or is in conjunction with Mobile Device Management for Office 365.

    -   If you have an existing implementation of System Center Configuration Manager and you want to expand its management capabilities with Microsoft Intune, set Configuration Manager as your MDM authority.

        > [!NOTE]
        > If you only want to leverage Mobile Application Management over your end-users' owned devices, shared devices, or kiosk-type devices, setting up an MDM authority is not required.

-   If Mobile Device Management is in your scope, we’ll provide guidance with:

    -   Configuring tests groups to be used to validate MDM management policies.

    -   Configuring MDM management policies and services such as:

        -   Application deployment for each supported platform through web links or deep links.

        -   Conditional access policies.

        -   Deployment of e-mail profiles.

        -   Setting up the Microsoft Intune Exchange Connector, when applicable.

    -   Enrolling devices of each supported platform to your Microsoft Intune or Configuration Manager with Microsoft Intune service.

    -   Using hardware and software inventory reports.

-   If Mobile Application Management (MAM) is in your scope, or if you want to complement your existing third-party MDM solution with MAM policies, we’ll provide guidance with:

    -   Configuring MAM policies for each supported platform.

    -   Configuring conditional access policies for managed apps.

    -   Targeting the appropriate user groups with the above MAM policies.

    -   Using managed-applications usage reports.

-   If PC management is in your scope, we’ll provide guidance with:

    -   Installing the Intune client software, when needed.

    -   Using the software and hardware reports available in Intune.

**Want to learn more?**

[Enterprise Mobility + Security](https://www.microsoft.com/en-us/cloud-platform/enterprise-mobility)