---
# required metadata

title: Develop SaaS mobile device management strategy
description:
keywords:
author: andredm7
manager: swadhwa
ms.date: 10/3/2016
ms.topic: solution
ms.prod:
ms.service: 
ms.technology:
ms.assetid: b3cefcc5-b045-48f9-91f5-6d282a4428f3

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: 
ms.suite: ems
#ms.tgt_pltfrm:
ms.custom: microsoft-intune

---

# Develop SaaS mobile device management strategy

>[!NOTE]
>This topic is part of a larger design considerations guide. If you'd like to start at the beginning of the guide, check out the [main topic](mdm-design-considerations-guide.md). To get a downloadable copy of this entire guide, visit the [TechNet Gallery](https://gallery.technet.microsoft.com/Mobile-Device-Management-7d401582).

## Identify your SaaS solution requirements

Depending on how you answered the questions in Task 1, you should be able to determine what the SaaS solution needs to support in your mobile device management solution. Table 20 below will help you understand the advantages and disadvantages of each SaaS solution scenario:

## Intune (standalone)

**Advantages**

- Offered as a multi-tenant, public cloud architecture
- Scales to support up to 50,000 mobile devices
- Doesn’t require any additional investments in on-premises infrastructure, hardware or software
- Updates and feature improvements are made on a daily basis. Major feature and functionality enhancements made on a monthly basis
- Services can be assigned to datacenters in specific geographic locations
- Datacenter fail-overs can be restricted to specific geographic locations
- Certified and compliant with the most industry and governmental standards Service Level Agreement (SLA) is financially-backed, if the service or features aren’t available, monthly charges are waived

**Disadvantages**

- Private cloud instances aren’t supported
- If you need to support more than 50,000 mobile devices, you’ll need to connect Intune to ConfigMgr to manage the additional devices

## MDM for Office 365

**Advantages**

- Tightly integrated with Office 365 commercial tenants, providing a single management console for mobile devices and Office 365 tenant services (Exchange Online, SharePoint Online, and Skype for Business Online).
- Offered in Office 365 multi-tenant (public) or private (dedicated) platform types
- No additional user or device licensing costs, included by default in Office 365 commercial (Business, Enterprise, Education, and Government) plans

**Disadvantages**

- Doesn’t support managing non-mobile operating system
- Additional management interface for provisioning mobile devices (only) if using an on-premises management platform for non-mobile devices.

## Hybrid (Intune with ConfigMgr)

**Advantages**

- All the advantages of Intune standalone, plus the following:Native integration between Intune (cloud-based device management service) with ConfigMgr (on-premises device management platform)
- Supports advanced device provisioning options for mobile devices via Intune connectivity
- New Intune service features and functionality extended to the on-premises ConfigMgr infrastructure via platform extensions, either automatically or customized.

**Disadvantages**

- Requires additional configuration requirements to connect Intune with the on-premises ConfigMgr infrastructure.
- For organizations that don’t have a current ConfigMgr infrastructure configured, it will need to be planned, installed and configured prior to integrating with Intune.

Make sure to read the article **[Help protect your data with remote wipe, remote lock, or passcode reset using Microsoft Intune](https://technet.microsoft.com/library/jj676679.aspx)** to understand what data is removed and the effect on data that remains on the device after a selective wipe per platform. If you have a hybrid environment, consult the article [How to remote wipe mobile devices using Configuration Manager](https://technet.microsoft.com/library/dn956981.aspx) to understand how ConfigMgr can be used to accomplish this task.

For more details about SaaS solution functionality and requirements, make sure to review the **[service description for Microsoft Intune](https://technet.microsoft.com/library/dn600286.aspx)** topic to understand the differences in SaaS support in [MDM for Office 365](https://technet.microsoft.com/library/faa7d8e5-645d-4d59-839c-c8d4c1869e4a(v=technet.10).aspx) and in a [hybrid](https://technet.microsoft.com/library/jj884158.aspx) Intune and ConfigMgr infrastructure.
