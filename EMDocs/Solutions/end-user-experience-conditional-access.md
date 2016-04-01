---
title: End-user experience of conditional access
ms.custom: na
ms.reviewer: na
ms.service: microsoft-intune
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3e186dd2-e17c-40d8-b160-48038b2c6593
author: karthikaraman
---
# End-user experience of conditional access
When the user attempts to access email on the device for the first time, or sync subsequently, the device enrollment and compliance status is checked. The process of enrolling or fixing compliance issues is a guided experience. The end-user is shown the necessary steps to enroll their device and make it compliant without needing to call your IT help desk:

-   **If the device is not enrolled**, the sign-in page will show access denied and will prompt for enrollment. On enrollment, the device is automatically registered in Azure Active Directory. Intune checks the device for compliance and provides remediation steps to resolve any non-compliance issues. Once the device is compliant, Intune sets the device compliance status with Azure Active Directory.

-   **If the device is enrolled but is not in compliance**, a link with steps to remediate the issues is sent to the device. When the end-user corrects the issue (for example, set password, encryption), Intune which manages the compliance policies updates the compliance status of the device in Azure AD.

Once the device is evaluated as enrolled and compliant, the email sync should happen within a few minutes.

This section describes the end-user experience after conditional access is enabled and an end user tries to access email on their mobile device. Choose a device to see the specific end-user experience for that device:

-   [Windows Phone](../Topic/end-user-experience-conditional-access-winphone.md)
-   [iOS](../Topic/end-user-experience-conditional-access-ios.md)
-   [Android](../Topic/end-user-experience-conditional-access-android.md)
