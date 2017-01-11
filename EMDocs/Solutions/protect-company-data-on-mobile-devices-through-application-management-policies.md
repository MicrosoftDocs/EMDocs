---
# required metadata

title: Protect Company Data using MAM with MDM
description: Create and deploy apps with mobile app management (MAM) policies to best protect your company data.
keywords:
author: craigcaseyMSFT
ms.author: v-craic
manager: swadhwa
ms.date: 01/10/2017
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 6c7088a9-ca88-4ff2-97a6-f842691fd3c7

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer:
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Protect company data on mobile devices through app management policies
Protecting your company's data is vitally important, and is an increasingly challenging task as more employees are using their mobile devices to access company resources, including email and email attachments. As an IT administrator, you want to make sure that company data is protected even when those mobile devices are not within the company’s physical location.

This guide will focus on enablement of managed applications as it applies to two Intune MDM deployments:

- As a cloud management solution using Intune
- As an integrated service with Configuration Manager

This allows you to create and deploy apps with mobile app management (MAM) policies to best protect your company data.

This document focusses on creation of these MAM based policies when the end-user device is enrolled in Intune for MDM. See [Protect line of business apps and data on devices not enrolled in Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/protect-line-of-business-apps-and-data-on-devices-not-enrolled-in-microsoft-intune) for information about configuring these MAM policies when the device itself is not enrolled in Intune for MDM.

> [!TIP]
> Downloadable a copy of this entire topic from the [TechNet Gallery](https://gallery.technet.microsoft.com/Protect-Company-Data-on-d972f4f4/file/154240/1/Protect%20Company%20Data%20on%20Mobile%20Devices%20through%20Application%20Management%20Policies.pdf).

## Introduction
Managed apps are apps that have MAM policies applied to them that make them compliant with your company’s security requirements. You have two options for managing mobile apps:
- **The default capability**, such as Apple Managed Open In, which protects corporate data by controlling the apps that are allowed to open certain documents and email attachments
- **The Intune App SDK**, which lets you limit the functionality and restrict sharing of data for any apps that have the Intune App SDK enabled. Some of the main features of the Intune App SDK is that it allows you to:
  - Manage the save-as function
  - Prevent cut, copy, paste
  - Require authentication when an app is accessed
  - Wipe corporate data from an Intune-managed app

  See [Intune App SDK Overview](https://docs.microsoft.com/intune/develop/intune-app-sdk) for a description of all SDK features.

## Before you begin
- **Learn about deploying apps using Microsoft Intune:**  [Learn the basics](https://docs.microsoft.com/intune/understand-explore/get-started-with-a-30-day-trial-of-microsoft-intune) about Intune app deployment.

- **Evaluate your desired implementation:** With all of the different design and configuration options for managing mobile devices, it’s difficult to determine which combination will best meet the needs of your company. The [Mobile Device Management Design Considerations Guide](https://docs.microsoft.com/enterprise-mobility/Solutions/mdm-design-considerations-guide) helps you understand mobile device management design requirements and details a series of steps and tasks that you can follow to design a solution that best fits the business and technology needs for your company.
- **Understand the high level end-user experience:** After the solution is implemented, you will be able to protect data on devices whether or not your company manages them. By simply implementing app-level policies, you can restrict access to company resources and keep data within the purview of your IT department.

   > [!NOTE]
   > The end-user experience of this solution is described in more details in the [End-user Experience](end-user-experience-mam.md) article.

- **Understand the app lifecycle:** Just like with the management of your devices, apps have a lifecycle that takes you from preparation, to deployment, monitoring, updating, and retiring. Intune can help you at all stages of this lifecycle. For detailed information about the app lifecycle, see [Overview of the app lifecycle](https://docs.microsoft.com/intune/deploy-use/overview-of-app-lifecycle-in-microsoft-intune).
- **Learn about the Microsoft apps you can use with MAM policies:** The [Microsoft Intune application partner’s](https://www.microsoft.com/en-us/cloud-platform/microsoft-intune-partners) page contains the latest information about apps from Microsoft and other companies that you can use with mobile app management policies.

  You can use the Microsoft Intune App Wrapping Tool to modify the behavior of your in-house apps to let you configure features of the app without modifying the code of the app itself. See the following topics for more specific information:
 - [Prepare iOS apps for mobile application management with the Microsoft Intune App Wrapping Tool](https://docs.microsoft.com/intune/deploy-use/prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool)
 - [Prepare Android apps for mobile application management with the Intune App Wrapping Tool](https://docs.microsoft.com/intune/deploy-use/prepare-android-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool)

- **Understand how policy conflicts are resolved:** When there is a mobile app management policy conflict on the first deployment to the user or device, the specific setting value in conflict will be removed from the policy deployed to the app, and the app will use a built-in conflict value (**most restrictive** is the default).

  When there is a mobile app management policy conflict on later deployments to the app or user, the specific setting value in conflict will not be updated on the mobile app management policy deployed to the app, and the app will use the existing value for that setting.

  In cases where the device or user receives two conflicting policies, the following behavior applies:
  - If a policy has already been deployed to the device, the existing policy settings are not overwritten.
  - If no policy has already been deployed to the device, and two conflicting settings are deployed, the default setting built into the device is used.

## Where to go from here
Now that you are familiar with the overall process for MAM, you are ready to [use mobile app management policies in Intune](mam-intune.md) or [use mobile app management policies in Configuration Manager](mam-configmgr.md). Or you can read about the [end-user experience of MAM policies](end-user-experience-mam.md).
