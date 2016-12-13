---
# required metadata

title: Specify your mobile device management location requirements
description: This article provides a series of common requirements regarding device location in a mobile device management scenario.
keywords:
author: YuriDio
ms.author: yurid
manager: swadhwa
ms.date: 11/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: c8824726-082e-417a-8522-183a69328ae4

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer:
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom: microsoft-intune

---

# Specify your mobile device management location requirements

>[!NOTE]
>This topic is part of a larger design considerations guide. If you'd like to start at the beginning of the guide, check out the [main topic](mdm-design-considerations-guide.md). To get a downloadable copy of this entire guide, visit the [TechNet Gallery](https://gallery.technet.microsoft.com/Mobile-Device-Management-7d401582).

Location requirements are one of the many factors that you should take in consideration when designing your mobile device management strategy. Location is important from the mobile device management solution perspective as well as from the device itself. Answer the following questions:

- Track users: For some kinds of mobile device control, you might need to implement policies that can restrict access to company resources based on a user’s location.
	- Does the company need to implement mechanisms to cover geo-fencing, or the ability to enforce policies based on the geographic location of the device?
	- Does the company need to keep track of where the user was geographically located when they accessed a company resource?
- Administration model: Depending on the mobile device management solution that you deploy, administration can be distributed in different sites (locations) or centralized in a single location. A central administration site is suitable for large-scale deployments and provides a central point of administration and the flexibility to support devices that are distributed across a global network infrastructure. A primary site is suitable for smaller deployments, though it has fewer options to accommodate future growth. Determine if MDM control should be centralized or distributed.
	- Does your company need a centralized administration model?
	- Does the device management solution need to be located on-premises?
		- If not, can it be located in the cloud?
		- If not, can it be hybrid?
	- Does your company need a decentralized model where different locations should have autonomy over the device management administration?

>[!TIP]
> Make sure to take notes of each answer and understand the rationale behind the answer. Next section will go over the available options and advantages/disadvantages of each option.  By having answered these questions, you’ll be able to select which solution best suits your business needs.
