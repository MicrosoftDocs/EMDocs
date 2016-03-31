---
title: Use conditional access in Exchange Online and on-premises with Microsoft Intune and Configuration Manager
ms.custom: na
ms.reviewer: na
ms.service: microsoft-intune
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5ccd033f-bc31-4fae-b6bf-9e1c2722627f
author: karthikaraman
---
# Deploy Exchange Online and on-premises with Microsoft Intune and Configuration Manager
An environment in which Exchange on-premises and Exchange Online are both used to manage email profiles offers companies the ability to extend the feature-rich experience and administrative control they have with their existing on-premises Microsoft Exchange organization to the cloud. This "hybrid" type of deployment provides the seamless look and feel of a single Exchange organization between an on-premises Exchange Server 2013 organization and Exchange Online in Microsoft Office 365. In addition, this type of deployment can serve as an intermediate step to moving completely to an Exchange Online organization.

If you are already using Configuration Manager along with a coexistence of Exchange on-premises and Exchange Online, you can incorporate Intune to manage email access and protect email data on mobile devices. You can implement this solution by following the instructions above for implementing each solution separately.

## Prerequisites
To configure a coexistence type of environment that implements both Exchange on-premises and Exchange Online, your existing Exchange organization must meet certain requirements. If you don't meet these requirements, you won't be able to complete the steps necessary to configure a hybrid deployment between your on-premises Exchange organization and the Exchange Online organization in Microsoft Office 365.

See [Hybrid deployment prerequisites](https://technet.microsoft.com/en-us/library/hh534377.aspx) to review the requirements for creating and configuring this type of environment.

## Deployment Steps
To deploy a coexistence solution, follow the steps above for deploying both the [Exchange Server on-premises](../Topic/conditional-access-intune-configmgr-exchange.md) and [Exchange Online](../Topic/conditional-access-intune-configmgr-exchange-online.md) solutions.

## Where to go from here
[End-user experience of conditional access](../Topic/end-user-experience-of-conditional-access.md)
