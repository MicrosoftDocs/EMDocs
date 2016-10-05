---
# required metadata

title: Specify your access requirements
description:
keywords:
author: YuriDio
manager: swadhwa
ms.date: 10/3/2016
ms.topic: solution
ms.prod:
ms.service: 
ms.technology:
ms.assetid: 1cdc3cdf-cb71-46d5-99fd-05ec96771b81

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: 
ms.suite: ems
#ms.tgt_pltfrm:
ms.custom: microsoft-intune

---

# Specify your access requirements

>[!NOTE]
>This topic is part of a larger design considerations guide. If you'd like to start at the beginning of the guide, check out the [main topic](mdm-design-considerations-guide.md). To get a downloadable copy of this entire guide, visit the [TechNet Gallery](https://gallery.technet.microsoft.com/Mobile-Device-Management-7d401582).

A mobile device that can’t use apps or access company data that is needed to perform work isn’t useful for your employees. So it’s critical to understand how the data will travel from the source location (on-premises or cloud) to the mobile device. 

The data will travel to and from mobile devices, and the considerations that should be in place for each path. Many companies that have security policies in place haven’t considered how mobile devices can increase the likelihood that corporate data might be leaked. So review your current company policies to ensure that the requirements you develop for authentication, authorization, and access control are aligned with your business requirements.
 
Answer the following questions to help determine the access requirements for mobile devices:

- Authentication and authorization: As part of the strategy to allow your users to access to company data from mobile devices, you must identify which users are eligible for access. Some companies decide to initially allow data access for just a portion of their users, and then grant access to other employees as they request it, based on business need. To restrict access, your solution must authenticate (identify that the user is who they claim to be) and authorize (evaluate if the user should have access to the data that they are requesting) according to your company’s policy. 

When designing your MDM solution, consider the following:

- Does your organization have a current directory service that is used for authentication and authorization?
	- If yes, does the MDM solution integrate with your directory service to authenticate and authorize access to resources?
	- Does your organization need to have centralized authentication, or can it be hybrid?
	- Does your organization plan to have multi-factor authentication for mobile users?
	- Does your organization use an on-premises Public Key Infrastructure (PKI) to issue certificates?
		- If yes, does the MDM solution have the capability to perform authentication using digital certificates?
			- If yes, does the MDM solution have the capability to integrate with an existing on-premises PKI?
- Does your organization need to use the current directory services to authenticate users accessing third party apps?
	- If yes, does the MDM solution allow users to use single sign-on (SSO) to authenticate against third party apps?


**Access Control**: Once a user is authenticated and authorized, requests for access to a resource must be validated with the level of access for the user. The requested resource can be data or an app. When designing your solution, consider the following:

- Does your company need to have different level of control for you to manage the mobile devices and the MDM solution?
	- If yes, does the MDM solution support Role Based Access Control (RBAC)?
- Does your company need to have different levels of access according to the user’s location?
	- If yes, does the MDM solution allow you to create access control restrictions according to the user’s location?
- Does your company need to control access to apps?
	- If yes, does the MDM solution allow you to control access to apps installed at the mobile device?
- Does your company need to control access according to a set of conditions?
	- If yes, does the MDM solution allow you to have conditional access control?
	- If yes, does the MDM solution allow you to enable/disable application’s feature according to the user’s identity?
	- If yes, does the MDM solution allow you to manage device attestation?

Read the [Secure access to company resources from any location on any device](https://technet.microsoft.com/library/dn550982) to better understand how to leverage built in Windows Server 2012 R2 capabilities in conjunction with ConfigMgr to provide access to your company resources. 
