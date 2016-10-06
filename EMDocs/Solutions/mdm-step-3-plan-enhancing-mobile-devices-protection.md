---
# required metadata

title: Plan for enhancing mobile devices protection
description:
keywords:
author: YuriDio
manager: swadhwa
ms.date: 10/3/2016
ms.topic: solution
ms.prod:
ms.service: 
ms.technology:
ms.assetid: a4504456-a241-4380-ab92-3bc14c91347c

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: 
ms.suite: ems
#ms.tgt_pltfrm:
ms.custom: microsoft-intune

---

# Plan for enhancing mobile devices protection

>[!NOTE]
>This topic is part of a larger design considerations guide. If you'd like to start at the beginning of the guide, check out the [main topic](mdm-design-considerations-guide.md). To get a downloadable copy of this entire guide, visit the [TechNet Gallery](https://gallery.technet.microsoft.com/Mobile-Device-Management-7d401582).

While on-premises and remote users can be more productive by accessing company resources on their mobile devices, letting them to do also increases security threats that you’ll need to mitigate in order to help protect your company’s data and maintain user privacy. Your company might have specific requirements about how to balance these needs. Compliance rules can vary depending on the industry in which your company operates, for example, which may lead to different design decisions.
 
However, there are some general aspects of security in mobile device management to explore and conform to, regardless of the industry. These are shown in the figure below.

![Core security capabilities for the MDM platform](./media/MDM_Figure_08.png)

## Security capabilities in a MDM solution

This diagram shows the core security capabilities required in any MDM solution. The key areas to consider are the following:

1. Considerations for data protection at the mobile device level:
	- Data encryption
	- Data classification
	- Client privacy
	- Containerization
	- Policy enforcement
	- Compliance policies
	- Hardening
2. Considerations for data protection while in transit:
	- Data encryption
	- Authentication
	- Authorization
3. Considerations for data protection while at rest in your on-premises organization:
	- Data encryption
	- Authentication
	- Authorization
4. Considerations for data protection while at rest in the cloud:
	- Data encryption
	- Authentication
	- Authorization

The tasks described in the sections that follow can help you understand how your specific security needs will influence your decision about the best MDM solution for your business requirements.

## About this step

There are 12 steps in this section of the guide. Total time to read through the sections is about 36 minutes, or you can jump to a specific section.

- [Gather data protection requirements](mdm-gather-data-protection-requirements.md)
- [Specify privacy requirements](mdm-specify-privacy-requirements.md)
- [Specify access requirements](mdm-specify-your-access-requirements.md)
- [Develop incident response requirements](mdm-develop-incident-response-requirements.md)
- [Plan for data encryption](mdm-data-encryption.md)
- [Plan for data segregation](mdm-data-segregation.md)
- [Hardening mobile devices](mdm-hardening-mobile-devices.md)
- [Client privacy](mdm-client-privacy.md)
- [Data classification](mdm-data-classification.md)
- [Authentication and authorization](mdm-authentication-authorization.md)
- [Access control to resources](mdm-access-control-resources.md)


