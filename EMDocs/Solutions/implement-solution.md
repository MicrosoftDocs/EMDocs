---
# required metadata

title: Implementing a solution for protecting company email and attachments
description:
keywords:
author: karthikaraman
manager: swadhwa
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service:
ms.technology:
ms.assetid: fc9c7d79-d2ca-4cb2-8456-c7a88cbbf6fd

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: 
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Implementing your solution for protecting email and attachments
This article helps you prepare for and then implement a solution for protecting company email content and attachments.

## What you should consider when planning your implementation:

-   **Device platform support**: You must also consider if you want to allow email access on platforms that are not supported by Intune. Intune mobile device management supports the following operating systems:

    -   Apple iOS 7.1 and later (previously enrolled iOS 6.0 and 7.0 devices remain enrolled but new devices cannot enroll)

    -   Google Android 2.3.4 and later (includes Samsung KNOX)

    -   Windows Phone 8.0 and later

    -   Windows RT and later

    -   Windows 8.1 computers and later

-   **Type of email apps**: The EMS solution currently supports clients that use EAS protocol, and Outlook apps (previously Accompli on iOS and Android).

-   **Policies**: The EMS solution and its components have several policies through which security and access is managed. Determine what policies your IT admin needs to configure. The three key policies to be used for research and plan when securing access to email and email data are:

    -   **Device Compliance Policies**: Determine what compliance means for your company. Intune includes several rules that you can set, but all of those rules may or may not apply to your company. You can change policies anytime, but it is good practice to
        determine a basic set of policies for you company. Compliance policies are targeted at Intune user groups and device groups.

    -   **Conditional Access Policies**: Conditional access policies are targeted at Azure AD Security Groups. Determine which users will be targeted by the policies and if there are users who need to be exempt. Conditional Access is supported by both the cloud based solution and the hybrid implementation.

    -   **Mobile Application Management**: Determine what apps should be managed and the MAM policies you need to apply to these apps.

-   **Device management considerations**: Select the device management option that best meets the requirements for your organization before you implement the solution. There are two options:

    -   Unify System Center Configuration Manager with Microsoft Intune to manage all devices through a single console. This is called the *Hybrid implementation*. Advantages of this approach:

        -   Single management console with rich rights-management controls to manage both on-premises PCs as well as mobile devices

        -   Rich targeting and deployment capabilities

        -   High scale for very large enterprises

    -   Manage the mobile devices through Microsoft Intune separately from the on-premises devices using System Center Configuration Manager. This is called *Intune Stand-alone implementation*. Advantages of this approach:

        -   Simple web-based console tailored specifically for mobile device management

        -   Rapid access to the latest features

    While migration is always possible, we strongly recommend that you make this decision before implementing it, since it will influence a lot of the decisions you will make in the roll out process.

-   **Your Exchange environment**:

    -   Deployment of Exchange connectors and how they connect when network load balancers are implemented.

    -   Exchange Online – is it multi-tenant or dedicated? If it is dedicated, find out which architecture your tenant is on. This will determine whether Azure AD-based conditional access can be used, or if an on-premises connector is required.

-   **Azure AD synchronization and Active Directory Federated Services (ADFS), or another third-party federated service**:

    -   Conditional Access is designed to work for customers who have federated their identity service to ADFS. Client access rules will generally still apply, however it is recommended that full testing be conducted. Requirements for directory synchronization and ADFS are no different than for Office 365.

    -   Third-party federation services like Ping should also work. Testing before implementation is recommended.

## On-premises implementation
If you have an existing implementation of System Center Configuration Manager, Active Directory and/or Exchange Server you can extend the existing infrastructure by integrating with Intune, Azure AD and Office 365. Using this hybrid implementation, you can provide a consistent management experience across devices on-premises and in the cloud. Intune and Configuration Manager offer a similar set of capabilities to allow restricted email access based on the device state.

For Exchange Online Dedicated implementations, whether you can take advantage of the cloud based solution described previously, or the hybrid implementation depends on what your current implementation looks like. Talk to your account team to determine what your implementation will involve.

## Operations and Incidence Response
Once you have implemented the solution, you need to manage the environment and identify potential security risks. Both Intune and Azure AD have monitoring and reporting capabilities that can help in monitoring and responding quickly in case of a security incident.

Here are some of the reporting capabilities:

-   Intune reports and alerts help you monitor the status and health of devices managed by Intune.

-   Azure AD has auditing and activity logging. You can monitor things like password changes and user management. Azure Active Directory premium includes advanced anomaly security reports and alerts. These alerts are based on detailed machine learning based reports showing sign in activity, inconsistent access patterns, and potential threat areas.

## Where to go from here
For step-by-step instructions on how to deploy a solution for protecting company email content and attachments, see one of these topics, depending on your specific environment:

- [Use conditional access with Microsoft Intune](../Solutions/conditional-access-intune.md)
- [Use conditional access with Microsoft Intune and Configuration Manager](../Solutions/conditional-access-intune-configmgr.md)
