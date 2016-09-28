---
# required metadata

title: Source Environment Expectations
description:
keywords:
author: staciebarker
manager: angrobe
ms.date: 10/02/2016
ms.topic: article
ms.prod:
ms.service:
ms.technology:
ms.assetid: 9048f3e5-cc28-4744-bb5e-36f974abb261

# optional metadata

ROBOTS: noindex
#audience:
#ms.devlang:
ms.reviewer:
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


# Source Environment Expectations
When you use the [FastTrack Center Benefit for Enterprise Mobility + Security (EMS)](fasttrack-center-benefit-for-enterprise-mobility-suite-ems.md) to get Azure Active Directory Premium and/or Microsoft Intune ready for use, your environment needs to meet the expectations described in the following sections.

You may already have Microsoft Active Directory on-premise in your current environment that you want to integrate with EMS or any of its individual services for leveraging rich identity management from a single console. The FastTrack Center benefit includes helping you integrate Microsoft Azure Active Directory with your existing on-premises implementation. If integration is required, your source environment must be at a minimum level for that application.

The following table shows expectations for your existing source environment for onboarding.

|Activity|Source environment expectation|
|------------|----------------------------------|
|Core onboarding|Active Directory forests with the functional forest level set to Windows Server 2008 or above, with the following forest configuration:<br /><br />-   Single Active Directory forest<br />-   Multiple Active Directory forests </br></br>**Note**: For all multiple forests configurations, AD FS deployment is out of scope for the FastTrack Center Benefit.|
|Microsoft Azure Active Directory Premium onboarding|On-premises Active Directory and environment have been prepared for Azure Active Directory Premium, which includes remediation of identified issues that would prevent integration with Azure Active Directory and Azure Active Directory Premium features.|
|Microsoft Intune, cloud only or integrated with System Center Configuration Manager, onboarding|For device management with System Center Configuration Manager 2012 R2 or later version connected with Microsoft Intune, IT administrators need to follow the [Administrator Checklist: Configuring Configuration Manager to Manage Mobile Devices by Using Microsoft Intune](https://technet.microsoft.com/library/jj943763.aspx).</br></br> **Note**: The service benefit does not include assistance for setting up or upgrading System Center Configuration Manager to the minimum requirements needed for Microsoft Intune integrated with System Center Configuration Manager.|

**Want to learn more?**

[Enterprise Mobility + Security](https://www.microsoft.com/en-us/cloud-platform/enterprise-mobility)
