---
# required metadata

title: Source environment expectations
description: Source environment requirements for using the FastTrack Center Benefit for EMS
keywords:
author: andredm7
ms.author: andredm
manager:
ms.date: 03/21/2018
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 9048f3e5-cc28-4744-bb5e-36f974abb261

# optional metadata

#ROBOTS: noindex
#audience:
#ms.devlang:
ms.reviewer:
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom: active-directory, ad-health-connect, multi-factor-authentication, microsoft-intune

---

# Source Environment Expectations

When you use the [FastTrack Center Benefit for Enterprise Mobility + Security (EMS)](fasttrack-center-benefit-for-enterprise-mobility-suite-ems.md) to get Microsoft Azure Active Directory Premium and Microsoft Intune ready for use, your environment needs to meet the expectations described in the following sections.

You may already have on-premises Active Directory in your organization that you want to integrate with EMS or any of its individual services for leveraging rich identity management from a single console. The FastTrack Center Benefit for EMS includes helping you integrate Azure Active Directory with your existing on-premises Active Directory environment.

The following table shows expectations for your existing source environment for onboarding.

|Activity|Source environment expectation|
|------------|----------------------------------|
|Core onboarding|Active Directory forests with the functional forest level set to Windows Server 2008 or above, with the following forest configuration:<br /><br />-   Single Active Directory forest<br />-   Multiple Active Directory forests </br></br>**Note**: For all multiple forests configurations, Active Directory Federation Services (AD FS) deployment is out of scope for the FastTrack Center Benefit.|
|Azure AD Premium onboarding|The on-premises Active Directory and its environment have been prepared for Azure AD Premium, which includes remediation of identified issues that prevent integration with Azure AD and Azure AD Premium features.|
|Intune, cloud only or integrated with System Center Configuration Manager, onboarding|For device management with Configuration Manager 2012 R2 or later, connected with Intune, IT admins need to follow the [Administrator Checklist: Configuring Configuration Manager to Manage Mobile Devices by Using Microsoft Intune](https://technet.microsoft.com/library/jj943763.aspx).</br></br> **Note**: The service benefit doesn't include assistance for setting up or upgrading Configuration Manager to the minimum requirements needed for Microsoft Intune integration with Configuration Manager.</br></br>For WiFi and VPN profile deployment, IT admins need to have existing Certificate Authority, WiFi and VPN infrastructures already working in their production environments.</br></br> **Note**: The service benefit doesn’t include assistance for setting up or configuring Certificate Authorities, WiFi or VPN infrastructures. |

> [!NOTE]
> **Want to learn more?**
> [Enterprise Mobility + Security](https://www.microsoft.com/cloud-platform/enterprise-mobility)

## Next steps

[FastTrack Center benefit for EMS Onboarding and migration phases](fasttrack-center-benefit-process-for-ems-phases.md)
