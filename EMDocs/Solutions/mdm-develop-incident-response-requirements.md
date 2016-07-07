---
# required metadata

title: Develop your incident response requirements
description:
keywords:
author: YuriDio
manager: swadhwa
ms.date: 07/07/2016
ms.topic: article
ms.prod:
ms.service:
ms.technology:
ms.assetid: 6f9fd9b3-492b-48e1-871c-e5abefe1293a

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: 
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Develop your incident response requirements

>[!NOTE]
>This topic is part of a larger design considerations guide. If you'd like to start at the beginning of the guide, check out the [main topic](mdm-design-considerations-guide.md). To get a downloadable copy of this entire guide, visit the [TechNet Gallery](https://gallery.technet.microsoft.com/Mobile-Device-Management-7d401582).

While many organizations already have an incident response (IR) plan in place, you should check to make sure the plan includes mobile devices and what steps should be taken if an incident is reported on those devices. If your company is just now adding a mobility solution, it’s likely the current IR plan doesn’t cover mobile devices. 
If your organization doesn’t have an IR plan, it is important to work closely with your security team to understand the requirements as you develop one, so you’ll know the right questions to ask when you’re choosing the best MDM solution for your needs. 
 
>[!TIP] 
> Read [Responding to IT Security Incidents](https://technet.microsoft.com/library/cc700825.aspx) to better understand the minimum requirements for an IR plan.

When designing your MDM solution, make sure you ask the following questions so you can make sure mobile devices can be managed if there’s an incident.

- Does your organization have an existing Incident Response Plan?
	- If yes, does it include processes and procedures for handling compromised mobile devices?
- Does the incident response policy cover scenarios where an end user reports that they’ve lost their mobile device?
	- Is it permissible to erase the entire device to avoid data leakage? 
		- If it is, does your company have backup policy in place for data that resides on mobile devices?
- Does your organization have different procedures for company-owned devices and personally-owned devices in case they are lost?
	- If yes, what are those procedures?
	- Will those procedures affect the selection of the MDM solution?
- If a user loses their personally-owned mobile device but they don’t authorize your company to erase the entire device, does the MDM solution allow selective device wipes?
- When a mobile device is compromised and you need to prevent that device from spreading malicious apps to the corporate network, does the MDM solution allow you to enforce policies that can rapidly contain the compromised device?
- Does the MDM solution allow you to plan for potential attacks so you can take proactive actions to address problems?
- Does the MDM solution allow you to identify when a file is infected with malware, by using a management console?

