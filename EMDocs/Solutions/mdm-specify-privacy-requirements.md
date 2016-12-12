---
# required metadata

title: Specify your privacy requirements
description: This article provides a set of common privacy requirements that should be used in a mobile device management scenario.
keywords:
author: YuriDio
ms.author: yurid
manager: swadhwa
ms.date: 11/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: d02d3ec2-706a-4e03-977c-b7c06cbd4ebd

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer:
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom: microsoft-intune

---

# Specify your privacy requirements

>[!NOTE]
>This topic is part of a larger design considerations guide. If you'd like to start at the beginning of the guide, check out the [main topic](mdm-design-considerations-guide.md). To get a downloadable copy of this entire guide, visit the [TechNet Gallery](https://gallery.technet.microsoft.com/Mobile-Device-Management-7d401582).


In the previous step, you defined device management tasks, including device management and content distribution management. In this task, the goal is to define the privacy requirements for company content that will reside on the mobile device.

>[!TIP]
> Read the solution Streamlined management for mobile devices and computers in a hybrid environment for more information about content distribution for mobile devices.

An organization’s privacy and compliance requirements will vary according to the industry, applicable regulations, and type of business. For example, you may want your MDM solution to allow you to perform basic hardware inventories, software inventories, file collections, and software distribution on mobile devices. Hardware inventory and software distribution are usually supported by default.

Keep in mind that privacy concerns that apply to your client computers for inventory and software distribution also apply to mobile devices.

Before choosing a mobile device management solution, consider your unique privacy requirements. For example, consider the following:

- Client Privacy: Allowing users to use their mobile devices to connect to and use company resources also means that they must understand your organization’s privacy policy and how this will affect their privacy.
	- Are you required to provide users with your company privacy policy, and what should it include?
		- If yes, does the MDM solution include the ability to easily provide a privacy policy to users?
	- Does the MDM solution store user’s mobile device information or data in the cloud?
		- If yes, how is user’s privacy maintained in the cloud?
- Who has access to their data?
- How is their data kept private?
- Data Classification and compliance: It’s important to define what constitutes company data, and how it will be protected. Having policies and mechanisms in place to classify data should be part of the plan to ensure privacy when managing mobile devices.
	- Can you identify or classify company documents or data that will reside on the mobile device?
		- If yes, what type of data or document rights or permissions are supported?
	- Will this classification travel with the data or document, regardless of the mobile device that the user is using?
	- What type of data or documents can (or can’t) be classified?
	- Will compliance requirements affect how you choose your mobile device management platform?
		- If yes, ensure that you enumerate these requirements prior to select your mobile device management platform.

Read the [Microsoft Online Services Privacy Statement](http://www.microsoft.com/server-cloud/products/intune-trust-center/privacy.aspx) to better understand how Microsoft Cloud services, including Intune will maintain user’s privacy.
