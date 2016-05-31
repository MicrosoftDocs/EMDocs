---
# required metadata

title: Gather monitoring requirements
description:
keywords:
author: andredm7
manager: swadhwa
ms.date: 05/31/2016
ms.topic: article
ms.prod:
ms.service:
ms.technology:
ms.assetid: ac136523-8089-409b-b74d-2d4c0ce399d4

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: 
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Gather monitoring requirements

>[!NOTE]
>This topic is part of a larger design considerations guide. If you'd like to start at the beginning of the guide, check out the [main topic](mdm-design-considerations-guide.md). To get a downloadable copy of this entire guide, visit the [TechNet Gallery](https://gallery.technet.microsoft.com/Mobile-Device-Management-7d401582).

Monitoring and capturing status and event information for mobile devices is vital to ensuring that users and devices are in compliance with your corporate policies and security strategy. This is especially important for organizations that must comply with governmental regulatory requirements and industry compliance guidelines.

Reporting can also provide valuable information about software, hardware, and software licenses in your organization to assist with inventory management. 

Be aware of the importance of user privacy when you’re establishing monitoring and reporting guidelines, especially when users can enroll personally-owned devices in your organization’s mobile device management solution. Your organization should not be able to capture, monitor, report, or share any personal activity or information.

In general, mobile device management solutions divide monitoring into two general areas:

- **Logging:** Capturing and storing mobile device and mobile device application status and information.
- **Reporting:** Displaying reports or notifications, including standard and customizable reports that can be created on-demand, and automatic summary and dashboard status reports.

## Monitoring planning questions

Answer the following planning questions about device monitoring:

- What types of regular reports for mobile devices will you need?
 - Device inventory?
 - Device usage?
 - Device access?
 - Device applications?
- Will reports need to be shared?
 - Between IT roles?
 - Outside of the IT organization?
 - Accessed remotely (outside of the corporate network)?
- What types of issues or problems with devices will you need to identify?
- What types of events captured in monitoring will need to be acted upon? In what time frame?
- Will you need customized, on-demand reports?
- When a device is de-enrolled, should specific inventory and reporting events be captured?
- After a device is de-enrolled, should legacy inventory and reporting events be archived/maintained?
 
>[!TIP]
>Make sure to take notes of each answer and understand the rationale behind the answer. Later tasks will go over the options available and advantages/disadvantages of each option.  Answering these questions will help you select the option that best suits your business needs.
