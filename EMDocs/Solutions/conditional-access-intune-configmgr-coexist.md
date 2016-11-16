---
# required metadata

title: Conditional access in Exchange with Intune and Configuration Manager
description: Use a coexistence of Exchange on-premises and Exchange Online along with Configuration Manager and Intune to manage email access and protect email data on mobile devices.
keywords:
author: craigcaseyMSFT
ms.author: v-craic
manager: swadhwa
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 5ccd033f-bc31-4fae-b6bf-9e1c2722627f

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer:
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Deploy Exchange Online and on-premises with Microsoft Intune and Configuration Manager
Now that you've read through the [architecture guidance for protecting company email and documents](architecture-guidance-for-protecting-company-email-and-documents.md), you are ready to proceed with deploying a solution.

An environment in which Exchange on-premises and Exchange Online are both used to manage email profiles offers companies the ability to extend the feature-rich experience and administrative control they have with their existing on-premises Microsoft Exchange organization to the cloud. This "hybrid" type of deployment provides the seamless look and feel of a single Exchange organization between an on-premises Exchange Server 2013 organization and Exchange Online in Microsoft Office 365. In addition, this type of deployment can serve as an intermediate step to moving completely to an Exchange Online organization.

If you are already using Configuration Manager along with a coexistence of Exchange on-premises and Exchange Online, you can incorporate Intune to manage email access and protect email data on mobile devices. You can implement this solution by following the instructions above for implementing each solution separately.

## Prerequisites
To configure a coexistence type of environment that implements both Exchange on-premises and Exchange Online, your existing Exchange organization must meet certain requirements. If you don't meet these requirements, you won't be able to complete the steps necessary to configure a hybrid deployment between your on-premises Exchange organization and the Exchange Online organization in Microsoft Office 365.

See [Hybrid deployment prerequisites](https://technet.microsoft.com/library/hh534377.aspx) to review the requirements for creating and configuring this type of environment.

## Deployment Steps
To deploy a coexistence solution, follow the steps above for deploying both the [Exchange Server on-premises](conditional-access-intune-configmgr-exchange.md) and [Exchange Online](conditional-access-intune-configmgr-exchange-online.md) solutions.

## Where to go from here
After you have deployed a solution for protecting corporate email and email data on mobile devices, you can learn more about the [end-user experience of conditional access](end-user-experience-conditional-access.md). This will help prepare you for issues that might arise when end users enroll their specific devices.
