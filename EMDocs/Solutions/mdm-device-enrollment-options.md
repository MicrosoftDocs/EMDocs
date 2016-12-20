---
# required metadata

title: Device enrollment options
description: This article provides guidance on the device enrollment options when planning and designing a Microsoft Mobile Device Management solution using Enterprise Mobility + Security.
keywords:
author: andredm7
ms.author: andredm
manager: swadhwa
ms.date: 10/3/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 54082b94-1d21-44d5-9fba-af6e04397def

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer:
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom: microsoft-intune

---


# Device enrollment options

>[!NOTE]
>This topic is part of a larger design considerations guide. If you'd like to start at the beginning of the guide, check out the [main topic](mdm-design-considerations-guide.md). To get a downloadable copy of this entire guide, visit the [TechNet Gallery](https://gallery.technet.microsoft.com/Mobile-Device-Management-7d401582).

Enrolling devices in Microsoft Intune, whether standalone or when connected to System Center 2012 R2 Configuration Manager (ConfigMgr), requires that you prepare the service for the devices. Enrolling mobile devices in MDM for Office 365 also requires that you activate MDM, configure basic settings, and include each user in a [security policy](https://technet.microsoft.com/library/ms.o365.cc.newdevicepolicy.aspx) respond to an enrollment message the next time they sign in to Office 365 on their mobile device. They must complete the enrollment and activation steps on each mobile device they will use to access Office 365 email and documents.

Intune standalone needs to be configured to define the Mobile Device Management Authority solution, which can be either Intune or an on-premises ConfigMgr infrastructure. This simply means “which management platform do you want to use to manage Intune-enrolled devices – Intune *or* ConfigMgr?” It’s *very important* to understand the [impact of choosing the best option](/Intune/deploy-use/enroll-devices-in-microsoft-intune) for your organization, as the management solution cannot be easily changed once chosen. If you need to change this configuration later, you’ll have to contact Microsoft Support for assistance. For Office 365 tenants, you can more easily designate and change the MDM authority between MDM for Office 365 and Intune. You can easily switch the user-level management authority by changing the license assignment for a user.

For most organizations that are already using ConfigMgr to manage PCs, servers, and other devices, connect the on-premises solution with Intune and managing devices with ConfigMgr is usually the best choice. To assign the mobile device management authority to ConfigMgr, you need to create an [Intune subscription](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0) and select the option to allow ConfigMgr to manage the Intune subscription and Intune-enrolled devices. The Intune subscription can also be created [from within the ConfigMgr console](https://technet.microsoft.com/library/jj884158.aspx).

Additionally, before you can enroll certain types of mobile devices running different types of mobile operating systems, you’ll need to prepare the Intune service or MDM for Office 365 with specific configuration requirements. For example, if you plan to enroll Apple iOS-based devices, you’ll need to **[configure Intune with an Apple Push Notification (APN) service certificate](https://technet.microsoft.com/library/dn408185.aspx)** prior to enrolling iOS-based devices. If this isn’t configured, Intune can’t communicate with the APN service and iOS-based devices. Mobile devices running **[Android](https://technet.microsoft.com/library/dn764960.aspx)** or **[Windows Phone](https://technet.microsoft.com/library/dn764959.aspx)** operating systems have separate enrollment requirements

Your answers to the questions in Step 1 will help you decide how you want devices to be enrolled in your mobile device management solution. The table below compares the advantages and disadvantages of each enrollment scenario:

| Area  | Administrators enroll devices | Users self-enroll devices |
| ------------- | ------------- | ------------ |
| Costs | Support/help desk costs may decrease since experienced administrators are performing the device enrollments. | Potential increase in support costs or help desk calls, less-experienced users may need personal help with enrollment |
| Convenience  | Each device is enrolled without any user interaction, reducing device enrollment errors. Users may have to arrange times with you to drop off and pick up mobile devices, requiring device enrollment scheduling and tracking.| Quicker device enrollment than a centralized enrollment process in most cases. May be more convenient and flexible for device owners/users. |
| Administration | Easier to support more complex, automated, bulk, or highly customized device enrollment. Administrators closely control the enrollment of all devices, effectively pre-screening any device or user at the beginning of the enrollment process. | Offloads relatively simple administration tasks to your users, saving time, scheduling, tracking, and administration overhead. |
| Security | If supporting a BYOD strategy, increased likelihood that administrators may see or expose sensitive user personal information if appropriate security controls are not in place. | Modern mobile device users may feel that this centralization is cumbersome and inconvenient, leading to user-defined workarounds that may compromise enrollment security and compliance processes |

Your organization might want to allow both of these enrollment scenarios, taking a flexible approach to permit different methods for different departments or situations. If so, your mobile device management solution must be able to support both scenarios.
