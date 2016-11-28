---
# required metadata

title: Device provisioning options
description: This article provides guidance on the device provisioning options when planning and designing a Microsoft Mobile Device Management solution using Enterprise Mobility + Security.
keywords:
author: andredm7
ms.author: andredm
manager: swadhwa
ms.date: 10/3/2016
ms.topic: solution
ms.prod:
ms.service: 
ms.technology:
ms.assetid: 991cd722-089c-4e8c-80b9-b82e405cc891

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: 
ms.suite: ems
#ms.tgt_pltfrm:
ms.custom: microsoft-intune

---

# Device provisioning options

>[!NOTE]
>This topic is part of a larger design considerations guide. If you'd like to start at the beginning of the guide, check out the [main topic](mdm-design-considerations-guide.md). To get a downloadable copy of this entire guide, visit the [TechNet Gallery](https://gallery.technet.microsoft.com/Mobile-Device-Management-7d401582).

When a user can use and enroll their own device, this increases the requirements for both the user and IT, and impacts several areas. For example, teh figure below shows an overview of the enrollment process for an organization using both Intune and ConfigMgr. This example outlines the certificate, web application, and synchronization considerations that you’ll need to consider when planning your solution:

![Overview of the enrollment process for mobile devices using hybrid Intune and ConfigMgr](./media/MDM_Figure_04.png)

**Overview of the enrollment process for mobile devices using hybrid Intune and ConfigMgr**

1. With <token>Windows Server 2012 R2, a new concept known as device registration was introduced.  Users can register their devices for single sign-on and access to corporate data using Workplace Join.  As part of this registration process, a certificate is installed on the device. In return for registering their device and making in known to the device management solution, the user gains access to corporate resources that were previously not available outside of their domain-joined PC.
2. Users can enroll devices which configure the device for management with Intune [using the Company Portal](/Intune/deploy-use/enroll-devices-in-microsoft-intune), and then leverage the Microsoft Intune Company Portal for easy access to corporate applications, data and to be able to manage their own devices, performing tasks such as remote wiping them in the event they are lost, stolen or replaced.
3. You can publish access to corporate resources with the built in capability available in Windows Server 2012 R2 called [Web Application Proxy](https://technet.microsoft.com/library/dn584107.aspx) based on device awareness (i.e. is it registered) and the users identity. If you’re using the Enterprise Mobility + Security, you can also publish applications using the Azure AD Application Proxy. Multi-factor authentication can be used through [Azure Active Authentication](https://azure.microsoft.com/documentation/articles/multi-factor-authentication-get-started-cloud/).
4. In order to provide administrators with a unified view of their entire environment, the data from Intune is synchronized with ConfigMgr which provides unified management across both on-premises and in the cloud.
5. As part of the enrollment process, a new device object is created in Active Directory.  This device object establishes a link between the user and their device, making it known to the device management solution, and allowing the device to be authenticated, effectively a seamless two-factor authentication.

Depending on how you answered the questions in Step 1, you should be able to determine how you want devices to be managed in the mobile device management solution. The lists below show the advantages and disadvantages of each provisioning option.

## Intune (standalone)

**Advantages**

- Supports enrolling and provisioning all major mobile device operating systems (Android, iOS, Windows 10, Windows 8.x, and Windows Phone)
- A cloud-based service, mobile devices can be enrolled from any location with Internet access
- Devices may be enrolled via a centralized, customizable Company Portal
- Advanced device provisioning options for mobile devices

**Disadvantages**

- Additional management interface for provisioning mobile devices (only) if using an on-premises management platform for non-mobile devices
- Separate device compliance and security policies for the cloud-based service and the on-premises management platform 

## MDM for Office 365

**Advantages**

- Integrated with Office 365 tenants, providing a single management console for mobile devices and Office 365 tenant services (Exchange Online, SharePoint Online, and Skype for Business)
- Supports enrolling and provisioning all major mobile device operating systems (Android, iOS, Windows 10, Windows 8.1, and Windows Phone)
- Basic device provisioning options for mobile devices

**Disadvantages**

- Additional management interface for provisioning mobile devices (only) if using an on-premises management platform for non-mobile devices
- Separate device compliance and security policies for the cloud-based service and the on-premises management platform
- Less advanced device provisioning options

## Hybrid (Intune with ConfigMgr)

**Advantages**

- Native integration between Intune (cloud-based device management service) with System Center 2012 Configuration Manager and System Center 2012 R2 Configuration Manager (on-premises device management platforms)
- Supports enrolling and provisioning all major mobile device operating systems (Android, iOS, and Windows Phone), and includes provisioning for all major non-mobile device operating systems
- Supports advanced device provisioning options for mobile devices via Intune connectivity

**Disadvantages**

- For organizations that don’t have a current ConfigMgr infrastructure configured, it will need to be planned, installed and configured prior to integrating with Intune
- Requires additional configuration to connect Intune with the on-premises ConfigMgr infrastructure

For more details about mobile device enrollment and provisioning options, make sure to review how to [enable mobile device enrollments](/Intune/deploy-use/enroll-devices-in-microsoft-intune) in Intune and compare these requirements and procedures to [enable mobile device enrollments](https://technet.microsoft.com/library/jj884158.aspx) in ConfigMgr and MDM for Office 365.
