---
title: Specify your mobile device management location requirements
ms.custom: na
ms.reviewer: na
ms.service: multiple
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 32ef7e4e-41b6-4e40-b9d9-6d2bfb464a99
author: YuriDio
---
# Specify your mobile device management location requirements

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

>[!NOTE] Make sure to take notes of each answer and understand the rationale behind the answer. Next section will go over the available options and advantages/disadvantages of each option.  By having answered these questions, you’ll be able to select which solution best suits your business needs.

>[Note!]
>This topic is part of a larger design considerations guide. If you'd like to start at the beginning of the guide, check out the [main topic](mdm-design-considerations-guide.md). To get a downloadable copy of this entire guide, visit the [TechNet Gallery](https://gallery.technet.microsoft.com/Mobile-Device-Management-7d401582).
