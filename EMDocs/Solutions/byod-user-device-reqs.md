---
# required metadata

title: User and devices requirements
description: This article provides a set of common requirements to be adopted by users and their devices in a Bring Your Own Device scenario.
keywords:
author: YuriDio
ms.author: yurid
manager: swadhwa
ms.date: 02/21/2017
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: a6319952-e9cd-4308-b9b9-b2e6005e6506

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer:
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom: microsoft-intune

---

# User and device requirements

Before enabling users to access company resources from their devices, answer the questions in the sections that follow by working with the consumers of these resources in your environment and with your IT department. Figure below shows the interactions between users and devices, with the ultimate goal of accessing and consuming data. Note that the diagram does not address geographical location. Although geographical location is an important consideration (and it will be covered later in this guide), the intent of this figure is to illustrate the core components of users and devices. Design considerations must be made to enable this communication to occur.

![Users, Devices and Data](./media/BYOD_Figure2.png)

The outcome of this process is a clear definition of the functionality to be provided. The section below contains questions about users and devices that you will need to answer in order to formulate the requirements for your solution design.

## Questions to ask

User and device requirements are categorized in three areas:

- Profile
- Device
- Network

### Profile

- What are the types of user profiles that you have in your enterprise (such as remote workers, occasional travelers, and full-time home-office workers)?
- Do all users have the same requirements to perform their jobs?
- Do you have a matrix that establishes users’ needs according to jobs/roles?


### Devices

- What are the types of devices that users will bring (such as smartphones, tablets, and laptops)?
- Do you plan to provide remote wipe capability to all types of devices?
- Do you plan to manage users’ devices?
- Do you have any scenario in which it is not necessary to manage the device, but you will need to track who owns the device anyway?
- Do you plan to authenticate devices according to the users who brought the devices to the company?
- Does your company follow any compliance requirements that must be applied to all devices that will potentially have access to your company’s data?
- Does your company have a policy in place to deal with stolen devices?

### Network

- Does your company have any resources in the cloud that will be accessible via the Internet from users’ devices?
- Does your company have policy restrictions for users accessing the company’s data from different geographical locations?
- Do you plan to provide network encryption to allow users to access company resources from their devices?
	- If so, does the current list of supported devices support the encryption protocol that will be used?
- Do you have network segmentation in place?
	- If so, will you have all users’ devices connected to a separate network to isolate them from the production network?
- For home-office workers, How are the users to be connected in your network? wired, wireless or both?
	- If wireless, how do you intend to handle the devices' Authentication, Authorization and Accounting (AAA) so that no unregistered/unauthorized devices will be able to use network resources without proper clearance?

### Technical Support
- Are your network/security team ready to accommodate a regular device compliance audits?
- Do you have change management policies and procedures in place to support BYOD implementation?
