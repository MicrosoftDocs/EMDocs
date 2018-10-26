---
# required metadata

title: Source environment expectations
description: Source environment requirements for using the FastTrack Center Benefit for EMS
keywords:
author: andredm7
ms.author: andredm
manager:
ms.date: 08/13/2018
ms.topic: article
ms.prod:
ms.service: microsoft-intune
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

The following table shows expectations for your existing source environment for on-boarding.

|Activity|Source environment expectation|
|------------|----------------------------------|
|Core on boarding|Active Directory forests with the functional forest level set to Windows Server 2008 or above, with the following forest configuration:<br /><br />-   Single Active Directory forest<br />-   Multiple Active Directory forests </br></br>**Note**: For all multiple forests configurations, Active Directory Federation Services (AD FS) deployment is out of scope for the FastTrack Center Benefit.|
|Azure AD Premium on-boarding|The on-premises Active Directory and its environment have been prepared for Azure AD Premium, which includes remediation of identified issues that prevent integration with Azure AD and Azure AD Premium features.|
|Intune on-boarding| IT admins need to have existing Certificate Authority, WiFi, and VPN infrastructures already working in their production environments when planning on deploying WiFi and VPN profiles with Intune.<br /><br /> **Note**: The service benefit doesn’t include assistance for setting up or configuring Certificate Authorities, WiFi, VPN infrastructures, or Apple MDM push certificates for  |
|Co-management|With Co-management IT admins are responsible for preparing the on-premises environment, which might include remediation of issues that prevent you from concurrently manage Windows 10 devices using both Configuration Manager and Intune.<br /><br />**Note**: The FastTrack service benefit doesn't include assistance for setting up or upgrading Configuration Manager site server and/or Configuration Manager client to the minimum requirements needed to support Co-management with Windows 10 devices. |
|Intune integrated with Windows Defender Advanced Threat Protection (Windows Defender ATP)|Your Windows Defender ATP subscription has been activated and configured based on your company security requirements.<br /><br />**Note**: The FastTrack service benefit provides assistance on integrating Intune with Windows Defender ATP, and creating device compliance policies based on its Windows 10 risk level assessment. The FastTrack service benefit does not provide assistance on purchasing, licensing, activating, or using Windows Defender ATP and its Security Center console. |
|Windows Autopilot|IT admins are responsible for registering their devices to their organization by either having the hardware vendor upload their hardware IDs on their behalf or by uploading it themselves into the Windows Autopilot service.

> [!NOTE]
> **Want to learn more?**
> [Enterprise Mobility + Security](https://www.microsoft.com/cloud-platform/enterprise-mobility)

## Next steps

[FastTrack Center benefit for EMS Onboarding and migration phases](fasttrack-center-benefit-process-for-ems-phases.md)
