---
# required metadata

title: End-user experience of conditional access
description:
keywords:
author: craigcaseyMSFT
manager: swadhwa
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service:
ms.technology:
ms.assetid: 3e186dd2-e17c-40d8-b160-48038b2c6593

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: 
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# End-user experience of conditional access
When the user attempts to access email on the device for the first time, or sync subsequently, the device enrollment and compliance status is checked. The process of enrolling or fixing compliance issues is a guided experience. The end-user is shown the necessary steps to enroll their device and make it compliant without needing to call your IT help desk:

-   **If the device is not enrolled**, the sign-in page will show access denied and will prompt for enrollment. On enrollment, the device is automatically registered in Azure Active Directory. Intune checks the device for compliance and provides remediation steps to resolve any non-compliance issues. Once the device is compliant, Intune sets the device compliance status with Azure Active Directory.

-   **If the device is enrolled but is not in compliance**, a link with steps to remediate the issues is sent to the device. When the end-user corrects the issue (for example, set password, encryption), Intune which manages the compliance policies updates the compliance status of the device in Azure AD.

Once the device is evaluated as enrolled and compliant, the email sync should happen within a few minutes.

## Android

[This topic](../Solutions/end-user-experience-conditional-access-android.md) describes the enrollment experience after conditional access is enabled and an end user first tries to access email on their Android mobile device.

## iOS

[This topic](../Solutions/end-user-experience-conditional-access-ios.md) describes the end-user experience when an end user first tries to access email on their iOS mobile device after conditional access is enabled.

## Windows Phone

[This topic](../Solutions/end-user-experience-conditional-access-winphone.md) describes the end-user experience after conditional access is enabled and an end user tries to access email on their Windows Phone.
