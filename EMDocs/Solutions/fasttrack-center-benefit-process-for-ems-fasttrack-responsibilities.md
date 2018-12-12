---
# required metadata

title: FastTrack responsibilities
description: FastTrack's responsibilities when customers are using the FastTrack Center Benefit for EMS
keywords:
author: andredm7
ms.author: andredm
manager:
ms.date: 12/4/2018
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.assetid: c8fd871e-f1bc-43ec-a5f3-ad025df9b026

# optional metadata

#ROBOTS: noindex
#audience:
#ms.devlang:
ms.reviewer:
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom: active-directory, ad-health-connect, multi-factor-authentication, microsoft-intune

---

# FastTrack responsibilities

FastTrack has the following responsibilities during onboarding.

## General

-   Provide remote support assistance to you for the required configuration activities as listed in the detailed phase descriptions.

-   Provide available documentation, software tools and admin consoles to help you reduce or eliminate configuration tasks.

## Initiate phase

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

-   Provide a remediation checklist for both Intune and Azure AD Premium.

## Remediate phase

-   Hold conference calls with you according to the agreed-upon schedule to review the progress of the remediation activities, for example, guide you through installation pre-requisites prior onboarding a Microsoft cloud service.

## Enable phase
Provide guidance about:

-   Activating your Microsoft online service tenant or subscription.

-   Configuring TCP/IP protocols and firewall ports.

-   Configuring DNS for eligible services.

-   Validating connectivity to Microsoft online services.

-   For a single-forest environment:

    -   Installing a directory synchronization server between your Active Directory Domain Services (AD DS) and the eligible Microsoft online services (only guidance if required).

    -   Configuring managed authentication (Password Hash Sync or Pass-through Authentication) with the Azure Active Directory Connect tool. (only guidance if required).

        > [!NOTE]
        > Development and implementation for custom rules extensions are out of scope.

-   For a single forest when the target is federated identities: Installing and configuring Active Directory Federation Services (AD FS) for local domain authentication with Intune in a single-site, fault-tolerant configuration, if required.

    > [!NOTE]
    > For all multiple forest configurations, AD FS deployments are out of scope.

-   Testing single sign-on (SSO) functionality, if deployed.

### Enable phase - Microsoft Azure Active Directory Premium

Provide guidance about:

- Activating your Azure AD Premium tenant.

- Configuring firewall ports.

- Configuring DNS for eligible services.

- Validating connectivity to Azure AD Premium services.

- For a single-forest environment:

  -   Installing a directory synchronization between your Active Directory Domain Services (AD DS) and Azure AD Connect, if required.

  -   Configuring an authentication method (Password Hash Sync or Pass-Through Authentication) with the Azure AD Connect tool.

- For a multiple-forest environment:

  -   Installing Azure AD Connect synchronization, set up for multiple forest scenarios.
- For single- and multiple-forest environments:
  - Configuring Azure Active Directory Pass-through Authentication, if required.
  - Configuring Azure Active Directory Seamless Single Sign-On (SSO), if required.
    > [!NOTE]
    > Azure Active Directory Pass-through Authentication for multiple-forest environments is supported if there are forest trusts between your Active Directory forests and if name suffix routing is correctly configured. Additional agents can be installed on multiple on-premises servers to provide high availability for sign-in requests.

  - For more information, see [Azure Active Directory Pass-through Authentication: Quick start](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-pass-through-authentication-quick-start#step-1-check-prerequisites) and [Azure Active Directory Seamless Single Sign-On: Quick start](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-sso-quick-start#step-1-check-prerequisites).
  - For more information about pass-through authentication limits, see [Azure Active Directory Pass-through Authentication: Current limitations](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-pass-through-authentication-current-limitations).
  - For more information about Seamless SSO issues, see [Troubleshoot Azure Active Directory Seamless Single Sign-On](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-troubleshoot-sso).

      > [!NOTE]
      > Password hash sync and password writeback support multiple forests. However, other writeback scenarios aren't supported.

  - Configuring synchronization between on-premises Active Directory forests and Microsoft Azure Active Directory Premium directory (Azure Active Directory).

    > [!NOTE]
    > Development and implementation for custom rules extensions are out of scope.

- For a single forest when the target is federated identities:

  -   Installing and configuring AD FS for local domain authentication with Azure AD Premium in a single-site, fault-tolerant configuration (if required).

  > [!NOTE]
  > For all multiple forest configurations, AD FS deployments are out of scope.

- Testing SSO functionality (if deployed).

### Enable phase - Azure AD Premium--with Azure AD Connect and AD FS

Provide guidance about setting up:

- User provisioning, including licensing.

- Azure AD Connect directory synchronization (with password writeback and password hash sync).

  - Azure Active Directory Self Service Password Reset (SSPR).

  - Azure Multi-Factor Authentication.

  - Up to three (3) or more Software as a Service (SaaS) application integrations with Single Sign-On (SSO) from the [Azure Active Directory Marketplace](https://azure.microsoft.com/marketplace/active-directory/).

  - Automatic user provisioning for pre-integrated SaaS applications as listed in the [App integration tutorial list](https://docs.microsoft.com/en-us/azure/active-directory/saas-apps/tutorial-list), limited to outbound provisioning only.

  - Customized logon screen, including logo, text, and images.

  - Self-Service and Dynamic Groups (Groups).

  - Azure Active Directory Application Proxy.

  - Azure Active Directory Connect Health.

  - Azure Active Directory Conditional Access.

  - Azure Active Directory Terms of Use.

  - Azure Active Directory Identity Protection.

  - Azure Active Directory Privileged Identity Management.

  - Azure Active Directory Access Reviews.

### Enable phase - Intune

> [!IMPORTANT]
> FastTrack does not support Windows 10 classic PC management with Intune. FastTrack only supports Windows 10 management through Intune mobile device management (MDM).

Provide **guidance** on:

-   Configuring identities to be used by Intune, by either leveraging your on-premises Active Directory or cloud identities (Azure Active Directory).

-   Licensing your end users.

-   Adding users to your Intune subscription, defining IT admin roles, and creating user and device groups.

-   Configuring your Mobile Device Management MDM) authority, based on your management needs, including:

    -   Setting Intune as your MDM authority.

    -   Configuring tests groups to be used to validate MDM management policies.

    -   Navigating the Intune admin portal to locate information on users and devices.

    -   Setting up Intune roles (Help desk operator, admins, etc.)

    -   Configuring MDM management policies and services like:

        -   App deployment for each supported platform through web links, MSI and/or deep links.

        -   Deploying Office ProPlus onto Windows 10 devices.

        -   Volume purchase programs for app deployment, including Apple's VPP, Windows Store for Business, and Google's Play for Work Store.

        -   Deployment of e-mail, wireless networks, and VPN profiles if you have an existing certificate authority, Wi-Fi or VPN infrastructure in your organization.

        -   Setting up the Microsoft Intune Exchange Connector (when applicable).

        -   Device configuration profiles for supported device platforms.

    -   Setting up conditional access policies.

    -   Configuring and deploying Intune app protection policies for each supported platform.

    -   Preparing line-of-business (LOB) apps for Intune app protection policies, with guidance on available options.

    -   Enrolling devices of each supported platform to your Intune or Configuration Manager with Microsoft Intune service.

    -   Connecting to Intune Data Warehouse.

    -   Integrating Intune with:
	    -   Team Viewer for remote assistance (Team Viewer subscription is required).

	    -   Mobile Threat Defense partner solutions (Mobile Threat Defense partner solution subscription is required).

	    -   Telecom expense management solutions (Telecom expense management solution subscription is required).

	    -   Windows Defender Advanced Threat Protection (Windows E5 or Microsoft 365 E5 licenses are required).

    -   Configuring Software updates for applicable supported platforms.

    -   Resources for user adoption planning.

- Setting up Windows Autopilot:

	- Configure and setup Microsoft Intune for Windows Autopilot.

	- Configure Azure AD dynamic groups

	- Add your Company branding into Azure AD.

	- Create and assign devices to Windows Autopilot profiles (e.g a Windows Autopilot profile that restricts Local Administrator account creation).

	- Customize the Out-of-box-experience (OOBE) to comply with organization's requirements.

	- Configuring MDM Auto-enrollment in Azure AD and Intune.

    > [!NOTE]
    > Setting up Windows Autopilot outside Intune is out of scope for the FastTrack benefit.

### Enable phase - Co-management

Provide guidance about:

-   Licensing your end users.

-   Adding users to your Intune subscription, defining IT admin roles, and creating user and device groups (if Intune is not installed).

-   Setting up Azure Active Directory for MDM auto-enrollment.

-   Set up hybrid Azure Active Directory Join.

-   Set up Cloud Management Gateway.

-   Adding users to your Intune subscription, defining IT admin roles, and creating user and device groups.

-   Prepare Intune (if Intune is not installed):

	-   Configuring your Mobile Device Management MDM) authority, based on your management needs, including:

    -   Setting Intune as your MDM authority.

    -   Configuring tests groups to be used to validate MDM management policies.

    -   Navigating the Intune admin portal to locate information on users and devices.

    -   Setting up Intune roles (Help desk operator, admins, etc.)

    -   Configuring and deploying Intune app protection policies for each supported platform.

    -   Enrolling Windows 10 devices to your Intune.

- Enable Co-Management in the Configuration Manager console.

- Switch workloads to Intune.

- Monitor the Co-management activity in your environment.

> [!NOTE]
> **Want to learn more?** see [Enterprise Mobility + Security](https://www.microsoft.com/cloud-platform/enterprise-mobility).

## Next steps

[FastTrack benefit for EMS - Your responsibilities](fasttrack-center-benefit-process-for-ems-your-responsibilities.md)
