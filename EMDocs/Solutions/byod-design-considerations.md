---
# required metadata

title: Design considerations | Enetrprise Mobility Suite
description:
keywords:
author: YuriDio
manager: swadhwa
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service:
ms.technology:
ms.assetid: 639dfd46-33ea-4cfd-918d-f3d8e57645ed

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: 
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Design considerations

With an understanding of the requirements detailed in Envisioning the BYOD Infrastructure Solution in this document, you can select appropriate products and technologies to implement the requirements for your BYOD infrastructure design. The following table lists Microsoft products, technologies, and services that can be used to implement a BYOD infrastructure solution.

Microsoft products, technologies, and services for a BYOD infrastructure solution that will be mentioned in this guide are:

## User and device

- Windows Server 2012 R2
- Windows 10
- Workplace Join
- Device Registration Service
- Device Enrollment
- Wi-Fi profile
- Company Portal
- HTTPS protocol

## Data access and protection

- Windows Server 2012 R2
- Active Directory Domain Services (AD DS)
- Azure Active Directory (Azure AD)
- Azure Multi-Factor Authentication (Azure MFA)
- Active Directory Federation Services (AD FS)
- Dynamic Access Control
- Microsoft Rights Management service
- Azure Rights Management 
- SMB Encryption
- Single signSign-onOn (SS)
- Work Folders
- Web Application Proxy (WAP)

## Management

- Microsoft Intune
- Device Management Policies
- Unified Management Infrastructure
- Selective Wipe
- Software Distribution
- Distribution Point Usage Reports and Management
- System Center 2012 R2 Configuration Manager

## Apps

- Web Application Proxy
- Automatic Trigger VPN
- RemoteApp
- Session Shadow
- Quick Reconnect
- Deduplication Storage
- Security Development Lifecycle (SDL)
- Active Directory Federations Services (AD FS)
- HTTPS protocol

The sections that follow outline the design process, but as mentioned in Envisioning the BYOD Infrastructure Solution in this document, the design and requirements definition process is iterative until it has been completed.
The remainder of the document addresses design considerations and the products, technologies, and services listed in the preceding table. When multiple Microsoft products, technologies, and services can be used to address different design considerations, the tradeoffs among them are discussed.

The infrastructure design to support BYOD brings together the answers to the questions that were presented previously in this article and the technology capabilities and options that are made available to you. The design that is discussed in this document uses Microsoft-based technology. However, the design options and considerations can be applied to any infrastructure used to embrace the BYOD model.


