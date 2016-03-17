---
title: Application management options
ms.custom: na
ms.reviewer: na
ms.service: multiple
ms.suite: na
ms.technology: na 
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid:  
author: robmazz
---
# Enterprise Mobility FastTrack Program

>[!NOTE]
>This topic is part of a larger design considerations guide. If you'd like to start at the beginning of the guide, check out the [main topic](mdm-design-considerations-guide.md). To get a downloadable copy of this entire guide, visit the [TechNet Gallery](https://gallery.technet.microsoft.com/Mobile-Device-Management-7d401582).

Mobile application management (MAM) policies help prevent your company data from being leaked to consumer apps or services on mobile devices. Typically, these policies would only be enforced on device enrolled in a mobile device management solution. Intune has now expanded its MAM capabilities to include devices managed by other mobile device management solutions and devices that aren’t enrolled in any device management system.

As shown in the figure below, if you already have an MDM solution in place, Intune MAM can help you manage and secure Office applications and Office 365 data without needing to un-enroll employee devices and re-enroll them in Intune MDM in a coexistence or migration scenario:

Intune MAM features are not a replacement for entire MDM solutions. The MDM protocol is required for comprehensive device management scenarios like VPN, Wi-Fi, certificate management, application deployment, and configuring device level security settings.

For hybrid deployments with ConfigMgr and Intune, mobile app management policies can be used to protect apps on devices that are not managed by Intune. Using this new capability, you can apply mobile app management policies for apps connecting to Office 365 services. This is not supported for apps connecting to on-premises Exchange or SharePoint. To use this capability, you must use the Azure preview portal.

Depending on how you answered the questions in Task 1, you should be able to determine how you want applications to be managed in the mobile device management solution. The tableable 8 below shows the advantages and disadvantages of each app management option.

