---
# required metadata

title: Understand the MDM lifecycle
description: This article provides guidance on how the Microsoft Mobile device management solution lifecycle works, so customers can better plan and design their mobile device management solutions using Microsoft Enterprise Mobility + Security.
keywords:
author: andredm7
ms.author: andredm
manager: swadhwa
ms.date: 10/3/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 901b52bf-2340-4847-aaff-c94fec9ee925

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer:
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom: microsoft-intune

---

# Understand the MDM lifecycle

>[!NOTE]
>This topic is part of a larger design considerations guide. If you'd like to start at the beginning of the guide, check out the [main topic](mdm-design-considerations-guide.md). To get a downloadable copy of this entire guide, visit the [TechNet Gallery](https://gallery.technet.microsoft.com/Mobile-Device-Management-7d401582).

Understanding the different areas of managing mobile devices is important when designing your mobile device management solution. The figure below outlines the overall mobile device management lifecycle stages. Each stage has unique requirements and questions for you to consider when planning your solution. We’ll start with the enrollment stage in this section, and the other stages will be covered in more detail throughout this guide.

![Mobile device management lifecycle stages](./media/MDM_Figure_03.png)

**Mobile device management lifecycle stages**

## Device enrollment and configuration
Mobile device management starts with the initial enrollment and configuration of devices into your mobile device management solution. Simplicity, ease of registration, and enrollment are the key factors for success in the mobile device management lifecycle. If initial device enrollment is difficult or overly confusing, both you and your users may be reluctant to go ahead with a mobile device management solution, which means you couldn’t leverage the features, benefits, and protections that the mobile device management solution can deliver.

Mobile device enrollment in mobile device management solutions are typically initiated in two ways:

- Administrator-managed enrollment
- User/owner self-enrollment

Administrator-managed enrollment offers a centrally managed enrollment experience, and typically is centered on bulk enrollment of multiple devices using a single directory account. This is useful if you need to enroll many company-owned devices into your mobile device management solution.

With self-enrollment, the device user/owner enrolls their device in the mobile device management solution. This is typically used in “bring your own device” (BYOD) scenarios, although it can also be used in scenarios where the company owns the device. This type of enrollment typically uses a “push-based” enrollment model, where devices are automatically triggered to enroll in the mobile device management solution when the user tries to connect to the corporate network or network resource from the device. Users can sometimes also elect to enroll their devices before connecting to an organization’s network or resources.

Enrolling and configuring mobile devices includes the following:

- Deploying, accessing, and managing internal and external applications and services
- Enforcing device security and access configurations
- Protecting devices from security threats

In most cases, when a mobile device is enrolled in a mobile device management solution, the device is automatically assigned policies and permissions that you have associated with the device user’s directory account and/or the group the device itself is associated with in directory services. Depending on the mobile device management solution, most of the configuring and provisioning of device policies and permissions is done before device enrollment. Then policy and compliance settings take effect as soon as the devices enroll, avoiding gaps between enrollment and compliance.

## Device enrollment and configuration planning questions

To plan for MDM lifecycle management, answer the following planning questions about device enrollment and configuration:

- Will mobile devices be enrolled by you, by users, or both?
- Do you need to ability to bulk-enroll mobile devices?
- What is the maximum number of devices you’ll need to bulk-enroll?
- Do the mobile operating system platforms in your organization require different bulk enrollment requirements and resources?
- How many devices will each user typically use and need to enroll?
- Does the mobile device management solution have a per-user device enrollment limit?
- What are the requirements (connectivity, application, management agent, company portal, support) for users to self-enroll devices?
-  Is this different from the requirements for administrator-managed enrollment?
-  What are the enrollment requirements for each device operating system you need to support?
-  Do the mobile device operating systems in your organization require special or unique enrollment requirements?
-  Does the mobile device management solution support both connected and over-the-air enrollments?
-  What are the hardware requirements (if any) for supporting device enrollments?
-  What are the network connectivity and network security requirements for supporting device enrollments?
-  Do you need specific device compliance policies applied to devices upon initial enrollment?
-  Do you need specific device security policies applied to devices upon initial enrollment?
-  Do you need the ability to configure or set a maximum or minimum time limit for provisioning device policies after initial enrollment?
-  Do you require special provisioning policies to be automatically triggered in the event of enrollment failures?

##Device management
How mobile devices are managed, both from your perspective and the device user’s perspective, is a key component of a mobile device management solution.

For example, you may want to integrate the way mobile devices are managed with how non-mobile devices (servers, desktops, other networked devices) are managed. Depending on the organization, non-mobile device management solutions may have been in place long before mobile devices were introduced to the organization. This may have been at considerable cost and may include long-term investments in these management solutions.

Thoroughly understanding how your organization can integrate mobile device management solutions with existing non-mobile device management solutions is likely one of the most important activities to complete when designing a mobile device management solution that meets the needs of your organization.

Mobile device management typically involves several administrative areas:

- **Device security and configuration:** Mobile device security includes a wide range of settings that you can deploy to managed devices in your organization. Settings can include specifying the timing, expiration, and required characteristics for device passcode access, device encryption, and erasing data from lost or stolen devices. More details about security and configuration are in  the [Step 3 - Plan for securing mobile devices](mdm-step-3-plan-enhancing-mobile-devices-protection.md) topic.
- **Application management:** This area includes managing application deployment, installation, updating and managing status, and application removal. You can also manage restrictions on certain non-compliant applications, which can be central to an overall compliance and security strategy. There may also be application management scenarios where you need to manage applications on mobile devices, but don’t want to enroll the devices into the mobile device management platform.
- **Company resource access:** MDM can also help manage access to on-premises network resources, such as email servers, Wi-Fi networks, and VPN-enabled resources. This serves a dual purpose of helping to insure security compliance and making it easier for mobile device users to access company resources according to company policy. If accessing organization resources is overly complex or difficult for mobile device users, they may opt to use non-approved company resources to store company data because it’s easier.
- **Inventory and reporting:** When you manage mobile devices, you’ll want to record and analyze mobile device and platform events to track compliance with the management policies in your organization. Detailed reporting can also provide you with real-time statistics and data so that you can make faster, better decisions based on the status of mobile devices and mobile device users. More details about inventory and reporting is included in a later section.

### Device management planning questions
For now, focus only in the key administration aspects as you are still defining the requirements. You can refine these requirements as you iterate on your plan and better understand the overall needs of your organization.</para><para>Answer the following planning questions about device management:

- Do you need specific management policies applied to groups of users, groups of devices, and/or groups of device operating systems?
- Do you need specific management policies for different types of devices? For example, separate policies for user-owned or company-owned devices, or mobile devices and non-mobile devices?
- Do you need to separate device management rights and permissions among several IT roles or positions? If so:
 - What separation of permission levels is required?
 - Do the permission levels supported by the solution need to be customizable?
 - Do the permissions need to be integrated into your existing account directory services?
- Do you need the ability to both manually and automatically deploy the mobile device management solution agents or software?
- Do you need the ability to manage applications on mobile devices, but don’t need to enroll the device into a mobile device management platform (either new or existing)?
- Do you want to integrate managing mobile devices with an existing non-mobile device management solution? If so:
 - Do you want to manage all devices from a unified management console or portal?
 - What are the integration requirements for your existing non-mobile device management solution?
 - How does your existing non-mobile device management solution support required management roles and permissions?
 - Are there hardware or networking requirements to connect management services between the mobile device management and the non-mobile device management solutions?
 - Do both solutions have separate or integration inventory and reporting systems?
- Does the mobile device management solution have a company portal for users to install their apps?
- Does the mobile device management solution meet your company’s scalability requirements?
- Does the mobile device management solution support remote administration?
- Does the mobile device management solution support automation?

## App management

Some cases, you may not want to enroll a mobile device into a device management system but still need to manage applications on the device to prevent company data from being leaked to other consumer apps or services on the device. This could apply to employees using personal devices to access company resources in a BYOD scenario, or even in scenarios where you need to manage mobile devices on one device management platform and manage applications on another device management platform.

### App management planning questions

To plan for app management considerations, answer the following planning questions:

- Does company data need to be isolated from consumer data within apps on mobile devices?
- Do you need to prevent data from being shared via cut/copy/paste across company and personal apps on mobile devices?
- Do you need to prevent apps from backing up or saving data to other apps or services?
- Do you need to enable per-App data loss prevention policies?
- Do you need to restrict web content displayed in a managed browser?

##Device retirement/unenrollment

When users leave your organization or mobile devices are retired or replaced, you need to make sure that corporate data isn’t lost or compromised. Typically, mobile device management solutions support both IT-managed and user-managed device resets and unenrollment. With most mobile devices, unenrollment starts with resetting the device to factory defaults or performing a selective wipe of all corporate data and applications. Then the device enrollment connection to the management solution is removed. However, the process varies between mobile device manufacturers and device operating system platforms.

### Device retirement/unenrollment planning questions

Answer the following planning questions about device retirement and unenrollment:

- Do you need the ability for both IT and users to unenroll mobile devices?
- If a device is selectively wiped, should it be automatically unenrolled from the mobile device management solution?
- If mobile device users can unenroll their mobile devices, how will the removal of corporate data and applications be verified?
 - Is this different for devices that are selectively wiped and devices that are reset to the factory default setting?

>[!TIP]
>Make sure to take notes of each answer and understand the rationale behind the answer. Later tasks will go over the options available and advantages/disadvantages of each option.  Answering these questions will help you select the option that best suits your business needs.
