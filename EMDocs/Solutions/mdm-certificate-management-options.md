---
# required metadata

title: Certificate management options
description: Provide decision points on how to plan and design a certificate infrastructure to support certificate provisioning with Intune standalone and hybrid.
keywords:
author: andredm7
manager: swadhwa
ms.date: 10/3/2016
ms.topic: solution
ms.prod:
ms.service: 
ms.technology:
ms.assetid: c3d350b5-4437-4f3d-907f-57ce6a819a74

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: 
ms.suite: ems
#ms.tgt_pltfrm:
ms.custom: microsoft-intune

---

# Certificate management options

>[!NOTE]
>This topic is part of a larger design considerations guide. If you'd like to start at the beginning of the guide, check out the [main topic](mdm-design-considerations-guide.md). To get a downloadable copy of this entire guide, visit the [TechNet Gallery](https://gallery.technet.microsoft.com/Mobile-Device-Management-7d401582).

Using digital certificate management and certificate profiles is supported both by [Intune](/Intune/deploy-use/secure-resource-access-with-certificate-profiles) standalone and [hybrid](https://technet.microsoft.com/library/dn261202.aspx) deployment scenarios. These features allow you to deploy trusted root certificates to mobile devices, as well as Simple Certificate Enrollment Protocol (SCEP) based profiles that instruct mobile devices to get additional certificates from a NDES server in your organization.

Since SCEP is natively supported by iOS, Windows 10 and 8.1, and Windows Phone 10 and 8.1, and is also supported through the Microsoft Intune Company Portal app for Android, using this enrollment protocol has the advantage of having the private key generated directly on the mobile device. The private key is never generated, cached, or stored by either ConfigMgr or by Intune - which helps to keep the mobile device secure.

The figure below shows how Intune and ConfigMgr use the NDES to provide secure certificate provisioning to mobile devices using SCEP:

![Secure certificate provisioning](./media/MDM_Figure_07.png)

**Secure certificate provisioning**

1. A policy that includes the properties of the certificate for SCEP enrollment is created on the Intune service.
2. Intune converts the policy to a platform mobile device management protocol (like OMA-DM for Windows 10 and Windows 8.1) and sends it to the device
3. The mobile device receives the policy and initiates an enrollment request from NDES
4. NDES forwards the request to ConfigMgr
5. ConfigMgr compares the request attributes of the SCEP request for an authentication match and sends confirmation back to NDES.
6. NDES sends a certificate issuance request to the CA and it sends the certificate to the NDES role.
7. NDES role sends the certificate to the device.

Depending on how you answered the questions in Task 3, you should be able to determine how you want certificates managed in the mobile device management solution. Currently, MDM for Office 365 doesn’t support managing certificate profiles for mobile devices. 

The lists below will help you understand the advantages and disadvantages of the certificate profile management for Intune and the hybrid Intune with ConfigMgr deployment scenario:

## Intune (standalone)

**Advantages**

- Supports certificate profiles on all major mobile device operating systems (Android, iOS, Windows 10, Windows 8.x, and Windows Phone)
- Platform supports the Simple Certificate Enrollment Protocol (SCEP)
- Certificate profiles can automatically configure mobile devices so that company resources can be accessed without having to install certificates manually or use a non-approved security process
- Certificates can be automatically revoked when the device is retired from management, selectively wiped, or block from the management hierarchy

**Disadvantages**

- To use certificate profiles, some existing on-premises infrastructure must be in place. You must integrate the following on-premises infrastructure with Intune:
 - A server that runs the Network Device Enrollment Service
 - An Enterprise Certification Authority
 - The Intune NDES Connector, which installs on the server that runs NDES

## MDM for Office 365

- Support for certificate profiles aren't supported in MDM for Office 365.

## Hybrid (Intune with ConfigMgr)

**Advantages**

- All the advantages of Intune standalone, plus the following:
 - Also supports managing certificates for non-mobile devices

**Disadvantages**

- To use certificate profiles, some existing on-premises infrastructure must be in place. 
- You must integrate the following on-premises infrastructure with Intune:
 - A server that runs the Network Device Enrollment Service
 - An Enterprise Certification Authority
 - The Intune NDES Connector, which installs on the server that runs NDES

For more details about mobile device certificate management options, read how to [enable certificate profiles](/Intune/deploy-use/secure-resource-access-with-certificate-profiles) in Intune and compare these requirements and procedures to [enabling certificate profiles](https://technet.microsoft.com/library/dn261202.aspx) in System Center 2012 R2 Configuration Manager.
