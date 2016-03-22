---
title: Authentication and authorization
ms.custom: na
ms.reviewer: na
ms.service: multiple
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5dffb570-dd1a-4beb-aa1e-7c0b51393704
author: YuriDio
---
# Authentication and authorization

>[!NOTE]
>This topic is part of a larger design considerations guide. If you'd like to start at the beginning of the guide, check out the [main topic](mdm-design-considerations-guide.md). To get a downloadable copy of this entire guide, visit the [TechNet Gallery](https://gallery.technet.microsoft.com/Mobile-Device-Management-7d401582).

Before you can properly protect your company data, you must identify who your users are, and then you can verify that they’re authorized to access the resource that they’re requesting. Organizations that already have on-premises Active Directory services should leverage it to authenticate and authorize mobile users. All Microsoft mobile device management solutions can use an existing Active Directory infrastructure to do this. 

Another decision point for authentication and authorization is where the directory services will be located. While most organizations have on-premises Active Directory services, some organizations might be considering extending their on-premises directory services with a cloud-based directory service such as [Azure AD](http://azure.microsoft.com/documentation/articles/active-directory-whatis/). 

ConfigMgr lets you integrate with [Microsoft Passport for Work](https://technet.microsoft.com/library/mt488797.aspx) which is an alternative sign-in method that uses Active Directory, or an Azure Active Directory account to replace a password, smart card, or virtual smart card on devices running Windows 10.For a hybrid scenario, integrating both directories is a good alternative to leverage Azure AD capabilities, such as the following:

- **Self-service group management**: Allows users to create groups, request access to other groups, delegate group ownership so others can approve requests, and maintain their group memberships.
- **Enterprise SLA of 99.9%**:  Microsoft guarantees at least 99.9% availability of the Azure Active Directory Premium service.
- **Password reset with write-back**: Self-service password reset can be written back to on-premises directories.

Read more about the different options and capabilities at [Azure Active Directory](https://msdn.microsoft.com/library/azure/dn532272.aspx).
Requiring two types of authentication (multi-factor authentication, or MFA) is another strategy to consider including when planning a mobile device management solution. Intune can [integrate directory services with multi-factor authentication (MFA)](https://technet.microsoft.com/library/dn889751.aspx), which adds another layer of security for the authentication process. 

If your organization has an on-premises IT infrastructure that includes an Active Directory domain with Active Directory Federation Services (AD FS), you can configure MFA on your federation server and then enable MFA for enrollment in Intune. If you configure MFA on your federation server, but you don’t enable MFA for enrollment in Intune, users will need to use MFA each time that they access corporate resources from any device. 

You can also use Azure AD MFA to require MFA each time that users access your corporate resources, enabled on a per-user basis. Azure AD MFA is a cloud service that doesn’t require any on-premises IT infrastructure.

Use the table below as a reference to assist you choosing the MDM option that best fits your organization’s authentication and authorization requirements.

| **MDM option**                 | **Advantages**                                                                           | **Disadvantages**                                                                   |
|--------------------------------|------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|
| **Intune (standalone)**            | Can use on-premises directory services, such as Active Directory for authentication      | Azure AD cloud service is not included when you purchase an Intune subscription     |
|                                | Can use cloud-based directory services, such as Azure AD for authentication              |                                                                                     |
|                                | Can integrate with multi-factor authentication                                           |                                                                                     |
| **MDM for Office 365**             | Can use on-premises directory, such as Active Directory for authentication               | Azure AD cloud service is not included when you purchase an Office 365 subscription |
|                                | Can use cloud based directory, such as Azure AD for authentication                       |                                                                                     |
|                                | Can integrate with multi-factor authentication                                           |                                                                                     |
|                                | Can leverage Compliance Center to use Role Based Access Control (RBAC) permissions model |                                                                                     |
| **Hybrid (Intune with ConfigMgr)** | Can use on-premises directory, such as Active Directory for authentication               | Azure AD cloud service is not included when you purchase an Intune subscription     |
|                                | Can use cloud based directory, such as Azure AD for authentication                       |                                                                                     |
|                                | Can integrate with multi-factor authentication                                           |                                                                                     |
| **Enterprise Mobility Suite**      | Leverages Azure AD Premium to provide access control                                     | Not available for customers that are not adopting a cloud-based solution            |
|                                | Azure AD Premium license is already included with EMS                                    |                                                                                     |
|                                | Does not required on-premises directory services                                         |                                                                                     |
|                                | Can synchronize with on-premises Active Directory services                               |                                                                                     |
|                                | MFA is natively available with EMS                                                       |                                                                                     |

