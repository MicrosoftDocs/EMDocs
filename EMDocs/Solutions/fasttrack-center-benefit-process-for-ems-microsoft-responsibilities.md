---
# required metadata

title: Microsoft responsibilities
description: Microsoft's responsibilities when customers are using the FastTrack Center Benefit
keywords:
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 11/07/2016
ms.topic: article
ms.prod:
ms.service: ems
ms.technology:
ms.assetid: c8fd871e-f1bc-43ec-a5f3-ad025df9b026

# optional metadata

ROBOTS: noindex
#audience:
#ms.devlang:
ms.reviewer:
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom: active-directory, ad-health-connect, multi-factor-authentication, microsoft-intune

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

-   Assist with running tools to identify and remediate issues and with interpreting the results.

## Enable phase
Provide guidance about:

-   Activating your Microsoft online service tenant.

-   Configuring TCP/IP protocols and firewall ports.

-   Configuring DNS for eligible services.

-   Validating connectivity to Microsoft online services.

-   For a single-forest environment:

    -   Installing a directory synchronization server between your Active Directory Domain Services (AD DS) and the eligible Microsoft online services (if required).

    -   Configuring password synchronization (password hash) to Microsoft Intune (Azure Active Directory) with the Azure Active Directory Connect tool.

        > [!NOTE]
        > Development and implementation for custom rules extensions are out of scope.

-   For a single forest when the target is federated identities: Installing and configuring Active Directory Federation Services (AD FS) for local domain authentication with Intune in a single-site, fault-tolerant configuration, if required.

    > [!NOTE]
    > For all multiple forest configurations, AD FS deployments are out of scope.

-   Testing single sign-on (SSO) functionality, if deployed.

### Enable phase - Microsoft Azure Active Directory Premium

Provide guidance about:

-   Activating your Azure AD Premium tenant.

-   Configuring firewall ports.

-   Configuring DNS for eligible services.

-   Validating connectivity to Azure AD Premium services.

-   For a single-forest environment:

    -   Installing a directory synchronization between your Active Directory Domain Services (AD DS) and Azure AD Connect, if required.

    -   Configuring password synchronization with the Azure AD Connect tool.

-   For a multiple-forest environment:

    -   Installing Azure AD Connect synchronization, set up for multiple forest scenarios.

		> [!NOTE]
        > Password hash sync and password writeback support multiple forests. However, other writeback scenarios aren't supported.

    -   Configuring synchronization between on-premises Active Directory forests and Microsoft Azure Active Directory Premium directory (Azure Active Directory).

        > [!NOTE]
        > Development and implementation for custom rules extensions are out of scope.

-   For a single forest when the target is federated identities:

    -   Installing and configuring AD FS for local domain authentication with Azure AD Premium in a single-site, fault-tolerant configuration (if required).

    > [!NOTE]
    > For all multiple forest configurations, AD FS deployments are out of scope.

-   Testing SSO functionality (if deployed).

### Enable phase - Azure AD Premium--with Azure AD Connect and AD FS

Provide guidance about setting up:

-   User provisioning, including licensing.

-   Azure AD Connect directory synchronization (with password writeback and password hash sync).

  - Self Service Password Reset (SSPR).

  - Azure Multi-Factor Authentication.

  - One Software as a Service (SaaS) application integration with SSO from the [Azure Active Directory Marketplace](https://azure.microsoft.com/marketplace/active-directory/).

  - Customized logon screen, including logo, text and images.

  - Self-Service and Dynamic Groups (Groups).

  - Azure Active Directory Application Proxy.

  - Azure AD Connect Health.

  - Identity Protection.

  - Privileged Identity Management.

  - Usage and security reports to administrators.

  - Administrative notifications and alerts.

### Enable phase - Intune
Provide guidance about:

-   Licensing your end users.

-   Configuring identities to be used by Intune, by either leveraging your on-premises Active Directory or cloud identities.

-   Adding users to your Intune subscription, defining IT admin roles, and creating user and device groups.

-   Configuring your Mobile Device Management MDM) authority, based on your management needs, including:

    -   Setting Intune as your MDM authority when Intune is your only MDM solution or is in conjunction with Mobile Device Management for Office 365.

    -   Setting System Center Configuration Manager as your MDM authority if you have an existing implementation of Configuration Manager and you want to expand its management capabilities with Intune.

        > [!NOTE]
        > If you only want to leverage MDM over your end-users' owned devices, shared devices, or kiosk-type devices, setting up an MDM authority is not required.

    -   Configuring tests groups to be used to validate MDM management policies.

    -   Configuring MDM management policies and services like:

        -   Application deployment for each supported platform through web links or deep links.

        -   Conditional access policies.

        -   Deployment of e-mail, wireless networks, and VPN profiles if you have an existing certificate authority, Wi-Fi or VPN infrastructure in your organization.

        -   Setting up the Microsoft Intune Exchange Connector (when applicable).

    -   Enrolling devices of each supported platform to your Intune or Configuration Manager with Microsoft Intune service.

    -   Using hardware and software inventory reports.

    -   Configuring MAM policies for each supported platform.

    -   Configuring conditional access policies for managed apps.

    -   Targeting the appropriate user groups with the above MAM policies.

    -   Using managed-applications usage reports.

    -   Installing the Intune client software (when needed).

    -   Using the software and hardware reports available in Intune.

**Want to learn more?**

[Enterprise Mobility + Security](https://www.microsoft.com/en-us/cloud-platform/enterprise-mobility)
