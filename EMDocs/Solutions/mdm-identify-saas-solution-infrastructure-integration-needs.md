---
title: Identify SaaS solution infrastructure integration needs
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
# Identify SaaS solution infrastructure integration needs

>[!NOTE]
>This topic is part of a larger design considerations guide. If you'd like to start at the beginning of the guide, check out the [main topic](mdm-design-considerations-guide.md). To get a downloadable copy of this entire guide, visit the [TechNet Gallery](https://gallery.technet.microsoft.com/Mobile-Device-Management-7d401582).

One of the primary decisions that need to be made when considering managing mobile devices with a SaaS solution are:

- How will your existing user and device on-premises directory accounts integrate with the SaaS solution?
- Do you need to integrate the SaaS solution with existing on-premises client management platforms?

The decisions you make in these two areas will significantly impact the overall deployment, administration, and end-user experiences for your mobile device management solution.

## Identity and directory connectivity

Connecting and synchronizing your on-premises user and device account directory with the SaaS solution is really the glue that truly connects users, mobile devices, mobile applications, and mobile device management. Knowing who a user is (identity) and associating the identity to specific mobile devices is critical in managing access to company resources and data from the mobile device. In many ways, maximizing how these areas are connected to the SaaS solution determines the overall value to both you and your mobile device users.  Ubiquitous connectivity means that people and devices can use devices and applications anywhere, and it’s essential that user identity management keeps pace with the demands of this connectivity. It can’t be stressed enough that how you manage identity and user authentication is critical to the success of your mobile device management solution.

Synchronizing on-premises directory services to the SaaS solution is another key area to consider when defining your mobile device management strategy. Most organizations prefer to maintain an on-premises user and device directory infrastructure, but need to extend these accounts to a variety of cloud-based services. This may include only a SaaS-based mobile device management solution, but in most scenarios organizations need to integrate user and device accounts into several different types of cloud-based services. This may include cloud-based applications, data, or 3rd party web services. Keeping your user and device directory accounts synchronized is the cornerstone of a well-designed identity management solution. Once you integrate your on-premises directory with cloud directory, you can also enable single sign-on (SSO) to allow users to sign into all services using their on-premises credentials. Both <token>Intune</token> and Office 365 can take advantage of this integration to enable SSO with SaaS apps that the organization might want to use.

### Identity and directory connectivity questions

As part of SaaS management lifecycle planning, you’ll want to answer the following planning questions about identity management and directory connectivity:

- Does the SaaS solution support integrated user authentication services? If so, does it support the type of directory services you’re using in your on-premises infrastructure?
- Do you need to support user and mobile device authentication for on-premises and/or internal applications or services?
- Does the SaaS solution support user and mobile device authentication for 3rd party or other external SaaS-based applications or services?
- How does the SaaS solution manage identity-related threats and abnormalities?
- Does the SaaS solution support implementing and managing multi-factor authentication (MFA)?
- What types of directory services objects do you need to extend to the SaaS solution? Does the SaaS solution have any restrictions for certain object types?
- What on-premises requirements are needed to extend your directory services to the SaaS solution?
- Once connected to the SaaS solution, how are user and mobile device directory objects replicated or synchronized with the cloud service? Are synchronization settings customizable or fixed?
- Are all directory object attributes synchronized with the SaaS solution? Do you need to synchronize custom directory object attributes?
- Are on-premises directory services hosted in a single location or logical grouping? If not, does the SaaS solution support synchronizing multiple directory services from multiple locations and logical groupings?

## Connecting with existing client management platforms

Most organizations have an existing on-premises client management platform to manage desktop computers and servers. How you integrate the management of mobile devices into this system is likely to have a substantial impact on IT infrastructure costs, device management administration processes, device inventory and reporting support, and overall integration with other business-critical applications and services. By connecting these two platforms, organizations are able to leverage the economies of scale of a single, unified management platform.

### Connecting existing client management platforms questions

As part of SaaS management lifecycle planning, you’ll want to answer the following planning questions about connecting the SaaS solution with existing client management platforms:

- Does your on-premises client management platform support integration with SaaS solution? If so, are there:
 - Limitations on the type of SaaS solution?
 - Limitations on the types of supported devices?
- What are the requirements to connect your on-premises client management platform to the SaaS solution? Specifically, are there:
 - Physical server or device requirements?
 - Directory services or directory schema requirements?
 - Domain Name Services (DNS) requirements?
 - Identity requirements?
 - Client management platform upgrades or configuration requirements?
 - Network connectivity and/or network security configuration requirements?
- Can existing client or device configuration information (policies, profiles, and settings) be shared or leveraged in the SaaS solution? Will this information have to be recreated?
- After the two platforms are connected, how are clients managed? Are different types of clients managed in a unified administration system or are they managed separately?
- How are updates and changes in the SaaS solution integrated with the on-premises client management platform? Is this an automatic or manual configuration process?

>[!NOTE]
>Make sure to take notes of each answer and understand the rationale behind the answer. Later tasks will go over the options available and advantages/disadvantages of each option.  Answering these questions will help you select the option that best suits your business needs.