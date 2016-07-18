---
# required metadata

title: End-user experience of MAM
description: End-user experience of mobile app management policies.
keywords:
author: craigcaseyMSFT
manager: swadhwa
ms.date: 05/12/2016
ms.topic: article
ms.prod:
ms.service:
ms.technology:
ms.assetid: bbc9f6ea-fc92-468d-bb5b-60c67949ca28

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer:
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# End-user experience of mobile app management policies
MAM polices are applied only when apps are used in the work context. Read the following example scenarios to help you educate your users so that they understand how managed apps work.

This section provides examples of the following end-user experiences:

- Scenario: Accessing OneDrive on an iOS device
- Scenario: Accessing OneDrive on an Android device

For information on other specific end-user experiences, see the following articles:

- [Using apps with multi-identity support](https://docs.microsoft.com/en-us/intune/deploy-use/end-user-experience-for-mam-enabled-apps-with-microsoft-intune#using-apps-with-multi-identity-support)
- [Managing user accounts](https://docs.microsoft.com/en-us/intune/deploy-use/end-user-experience-for-mam-enabled-apps-with-microsoft-intune#managing-user-accounts)
- [Viewing media files with the Rights Management sharing app](https://docs.microsoft.com/en-us/intune/deploy-use/end-user-experience-for-mam-enabled-apps-with-microsoft-intune#viewing-media-files-with-the-rights-management-sharing-app)

## Scenario: Accessing OneDrive on an iOS device

1. The user launches the **OneDrive** app to open the sign in page.
> [!NOTE]
> On a personal device, typically the end user would download the app. If the device is managed by a MDM solution, you can deploy the app to the device.

2. The user types their work account user name and is redirected to the **O365 authentication** page to enter work credentials.

  After the credentials are successfully authenticated by Azure AD, the MAM polices are applied.
3. The user is prompted to set a **PIN** for the app (if you configured the policy for this).

4.	Once the PIN is set and confirmed, the user can access the files on their **OneDrive for Business**.
> [!NOTE]
> When you change a deployed policy, the changes will be applied next time the app is opened.

## Scenario: Accessing OneDrive on an Android device
1. The user launches the **OneDrive** app to open the sign in page.
> [!NOTE]
> On a personal device, typically the end user would download the app. If the device is managed by a MDM solution, you can deploy the app to the device.

2.	The user types their work account user name and is redirected to the **O365 authentication** page to enter work credentials.

  After the credentials are successfully authenticated by Azure AD, the MAM polices are applied.

3.	The **OneDrive** app launches automatically and the user is prompted to set a **PIN**, provided the policy settings are set to require a **PIN** to access the **OneDrive** app.

4.	Once the PIN is set and confirmed, the user can continue using **OneDrive**, which is now managed by app policies.

## Where to go from here
There are other end-user experiences you can read more about, including [Using apps with multi-identity support](https://docs.microsoft.com/en-us/intune/deploy-use/end-user-experience-for-mam-enabled-apps-with-microsoft-intune#using-apps-with-multi-identity-support), [Managing user accounts](https://docs.microsoft.com/en-us/intune/deploy-use/end-user-experience-for-mam-enabled-apps-with-microsoft-intune#managing-user-accounts), and [Viewing media files with the Rights Management sharing app](https://docs.microsoft.com/en-us/intune/deploy-use/end-user-experience-for-mam-enabled-apps-with-microsoft-intune#viewing-media-files-with-the-rights-management-sharing-app).
