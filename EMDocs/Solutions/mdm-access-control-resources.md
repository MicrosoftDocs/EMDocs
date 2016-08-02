---
# required metadata

title: Access control to resources
description:
keywords:
author: YuriDio
manager: swadhwa
ms.date: 8/1/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 5967876b-3c08-4498-a0a6-0225b562d35f

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: 
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Access control to resources

>[!NOTE]
>This topic is part of a larger design considerations guide. If you'd like to start at the beginning of the guide, check out the [main topic](mdm-design-considerations-guide.md). To get a downloadable copy of this entire guide, visit the [TechNet Gallery](https://gallery.technet.microsoft.com/Mobile-Device-Management-7d401582).

Organizations that already use Active Directory to authenticate and authorize users already manage access control to specific resources, by using groups in Active Directory to segment and control access to resources.  

To manage control to specific resources, you first authenticate and authorize access for the user, and then validate the type of control the user has on the target resource. In the figure below, this is shown for user Bob accessing a folder.

![Authentication flow](./media/MDM_Figure_13.png)

## Basic authentication and authorization flow

The traditional Access Control List (ACL) is very limited and doesn’t take into consideration other aspects of the user’s state, such as where he is located when trying to access this resource. If your organization needs to include more variables before granting access to a resource, you can use [Dynamic Access Control](https://technet.microsoft.com/library/dn408191.aspx), which is natively available in Windows Server 2012. Windows 10 supports health attestation, which helps IT to control the health state of the device prior to provide access to the data. Remote health attestation service performs a series of checks on the measurements. It validates security related data points, including boot state (Secure Boot, Debug Mode, and so on), and the state of components that manage security (BitLocker, Device Guard, and so on). It then conveys the health state of the device by sending a health encrypted blob back to the device. Read [Control the health of Windows 10-based devices](https://technet.microsoft.com/library/mt592023.aspx) for more information.

Intune administrators can view the status of Windows 10 Device Health Attestation in the [Intune Admin console](/intune/deploy-use/introduction-to-device-compliance-policies-in-microsoft-intune). Device health attestation lets the administrator ensure that client computers have trustworthy BIOS, TPM, and boot software configurations. To support device health attestation, client devices must be running Windows 10 with TPM 2 enabled. 

With many companies acting as a cloud provider themselves by using technologies that allow them to have a private cloud, another option is to use Role Based Access Control (RBAC). [Azure AD allows IT to use RBAC](http://azure.microsoft.com/documentation/articles/role-based-access-control-configure/) to control access to resources. And since Azure AD can be integrated with your Active Directory on-premises, you can use them together to determine how users access resources.

A resource can also be an app, which means that to implement access control to resources, your MDM solution must also be able to control how apps are installed and accessed. [Mobile application management policies in Intune](/intune/deploy-use/configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console) let you modify the functionality of apps that you deploy to help make sure that they comply with your company compliance and security policies. 

Use the table below as a reference to assist you choosing the MDM option that best fits your organization’s access control requirements.

## Intune (standalone)

**Advantages**

- Access control (installation and management) for apps
- Conditional access with health attestation service

**Disadvantages**

- Lack of integration with current on-premises MDM platform will introduce an additional management interface for you to use
- Some policies may not be available for some mobile platforms
 
## MDM for Office 365

**Advantages**

- Access control to email, Office Mobile, Office apps, and OneDrive for Business

**Disadvantages**

- Only allows a small subset of access control to resources
- Lack of integration with current on-premises MDM platform will introduce an additional management interface for you to use
- Some policies may not be available for some mobile platforms

## Hybrid (Intune with ConfigMgr)

**Advantages**

- Access control (installation and management) for apps
- Conditional access with health attestation service

**Disadvantages**

- Azure AD cloud service is not included when you purchase Intune subscription

## Enterprise Mobility Suite

**Advantages**

- Access control (installation and management) for apps
- Leverages Azure AD Premium to provide RBAC based access control
- Conditional access with health attestation service

**Disadvantages**

- If the organization does not have a current on-premises ConfigMgr infrastructure, it will require to plan, install and configure this platform prior to the integration
