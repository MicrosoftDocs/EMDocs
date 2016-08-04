---
# required metadata

title: Using Mobile App Management Policies in Intune
description: Create and deploy an app in Intune with a mobile app management policy.
keywords:
author: craigcaseyMSFT
manager: swadhwa
ms.date: 05/12/2016
ms.topic: article
ms.prod:
ms.service:
ms.technology:
ms.assetid: 6d7c4104-b85f-407e-8832-0e6bbac934f5

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer:
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Use Mobile App Management Policies in Intune
One of the primary reasons many companies use Microsoft Intune is to deploy apps that users need to get their work done. Before you deploy apps, you'll need to [get your devices managed](https://docs.microsoft.com/intune/deploy-use/enroll-devices-in-microsoft-intune).

For example, if your company uses Microsoft Word, there are versions available for Windows, iOS, Android and more. The challenge you, as an IT admin, face is to manage the multitude of apps available, on many different device and computer platforms, with the aim of allowing users to do their work while still ensuring the security of your company data.

If you are using Intune with Configuration Manager, see [How to Control Apps Using Mobile Application Management Policies in Configuration Manager](https://technet.microsoft.com/library/mt131414.aspx?f=255&MSPPError=-2147217396).

Mobile app management (MAM) policies support:
- Devices that run Android 4 and later.
- Devices that run iOS 7 and later.

> [!NOTE]
> MAM policies support devices that are enrolled with Intune. For information about how to create app management policies for devices that are not managed by Intune, see [Protect app data using mobile app management policies with Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune).

Unlike other Intune policies, you do not deploy a MAM policy directly. Instead, you associate the policy with the app that you want to restrict. When the app is deployed and installed on devices, the settings you specify will take effect.

To apply restrictions to an app, the app must incorporate the Microsoft Intune App Software Development Kit (SDK). There are two methods of obtaining this type of app:

- **Use a policy managed app** – Has the App SDK built-in. To add this type of app, you specify a link to the app from an app store such as the iTunes store or Google Play. No further processing is required for this type of app. To see the full list of supported Microsoft apps, go to Microsoft Intune mobile application gallery on the [Microsoft Intune application partners](https://www.microsoft.com/en-us/cloud-platform/microsoft-intune-partners) page. Click the app to see the supported scenarios, platforms and whether or not the app supports multi-identity.
- **Use a ‘wrapped’ app** - Apps that are repackaged to include the App SDK by using the Microsoft Intune App Wrapping Tool. This tool is typically used to process company apps that were created in-house. It cannot be used to process apps that were downloaded from the app store. See:
  - [Prepare iOS apps for mobile application management with the Microsoft Intune App Wrapping Tool](https://docs.microsoft.com/intune/deploy-use/prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool)
  - [Prepare Android apps for mobile application management with the Intune App Wrapping Tool](https://docs.microsoft.com/intune/deploy-use/prepare-android-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool)

Some managed apps, like the Outlook app for iOS and Android, support **multi-identity**. This means that Intune only applies management settings to corporate accounts or data in the app.

For example, using the Outlook app:
- If the user configures a corporate, and a personal email account, Intune only applies management settings to the corporate account and does not manage the personal account.
- If the device is retired, or unenrolled, only the corporate Outlook data is removed from the device.
- The corporate account used must be the same account that was used to enroll the device with Intune.

Word, Excel, and PowerPoint all support multi-identity as well, except the policy restrictions only apply when managing and editing corporate-identifiable data from a service such as OneDrive or SharePoint.

## Create and deploy an app in Intune with a mobile app management policy

- Step 1: Get the link to a policy managed app, or create a wrapped app.
- Step 2: Publish the app to your cloud storage space.
- Step 3: Create a mobile app management policy.
- Step 4: Deploy the app, selecting the option to associate the app with a mobile a app management policy.
- Step 5: Monitor the app deployment.

### Step 1: Obtain the link to a policy managed app, or create a wrapped app
- **To obtain a link to a policy managed app** - From the app store, find, and note the URL of the policy managed app you want to deploy.
For example, the URL of the Microsoft Word for iPad app is [https://itunes.apple.com/us/app/microsoft-word-for-ipad/id586447913?mt=8](https://itunes.apple.com/us/app/microsoft-word-for-ipad/id586447913?mt=8)
- **To create a wrapped app** - Use the information in the topics [Prepare iOS apps for mobile application management with the Microsoft Intune App Wrapping Tool](https://docs.microsoft.com/intune/deploy-use/prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool) and [Prepare Android apps for mobile application management with the Intune App Wrapping Tool](https://docs.microsoft.com/intune/deploy-use/prepare-android-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool) to create a wrapped app. The tool creates a processed app that you will use when you publish the app to your cloud storage space.

### Step 2: Upload the app to your cloud storage space
When you publish a managed app, the procedures differ depending on whether you are publishing a policy managed app, or an app that was processed using the Microsoft Intune App Wrapping Tool for iOS.

See [Add apps for mobile devices in Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/add-apps-for-mobile-devices-in-microsoft-intune#add-the-app) for the complete steps required to upload an app to your cloud storage space.

### Step 3: Create a mobile app management policy
The Azure portal is the recommended admin console for creating MAM policies. Azure portal supports the following MAM scenarios:
- Devices enrolled in Intune
- Devices managed by a third-party MDM solution
- Devices that are not managed by any MDM solution (BYOD).

See [Create and deploy mobile app management policies with Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/create-and-deploy-mobile-app-management-policies-with-microsoft-intune) for more information about using the Azure portal to create a MAM policy.

If you are currently using the Intune admin console to manage your devices, you can create a MAM policy that supports apps for devices enrolled in Intune by using the [Intune admin console](https://docs.microsoft.com/intune/deploy-use/configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console#-step-3-create-a-mobile-application-management-policy).


### Step 4: Deploy the app, selecting the option to associate the app with a mobile application management policy
If you are using the Azure portal, [deploy the MAM policy to users](https://docs.microsoft.com/intune/deploy-use/create-and-deploy-mobile-app-management-policies-with-microsoft-intune#deploy-a-policy-to-users).

If you are using the Intune portal, you [deploy the app](https://docs.microsoft.com/intune/deploy-use/deploy-apps-in-microsoft-intune#deploy-an-app), ensuring that you select the mobile app management policy on the Mobile App Management page to associate the policy with the app.

If the device is unenrolled from Intune, polices are not removed from the apps; any apps that had policies applied will retain the policy settings even after the app is uninstalled and reinstalled.

#### What to do when an app is already deployed on devices

There might be situations where you deploy an app and one of the targeted users or devices already has an unmanaged version of the app installed, for example, the user installed Microsoft Word from the app store.

In this case, you must ask the user to manually uninstall the unmanaged version so that the managed version you configured can be installed.

However, for devices that run iOS 9 and later, Intune will automatically ask the user for permission to take over management of the existing app. If they agree, then the app will become managed by Intune and any MAM policies you associated with the app will also be applied.


### Step 5: Monitor the app deployment with MAM policy
Use the following procedures to monitor deployment of the app through the Intune console and resolve any policy conflicts.

1. In the [Microsoft Intune administration console](https://manage.microsoft.com/), click **Groups**.
2. Perform one of the following steps:
  -  Click **All Users**, then double-click on the user whose devices you want to examine. On the User Properties page, click **Devices**, then double-click the device you want to examine.
  -  Click **All Devices > All Mobile Devices**. On the Device Group Properties page, click **Devices**, then double-click the device you want to examine.
3. From the Mobile Device Properties page, click **Policy** to see a list of the MAM policies that have been deployed to the device.
4. Select the MAM policy whose status you want to view. You can view details of the policy in the bottom pane and expand its node to display its settings.
5.	Under the Status column of each of the MAM policies, Conforms, Conforms (Pending), or Error will be displayed. If the selected policy has one or more settings in conflict, Error will be displayed in this field.
6.	Once you have identified a conflict, you can revise conflicting policy settings to use the same setting, or deploy only one policy to the app and user.

> [!NOTE]
> You can learn more general information about monitoring apps through the [Azure portal](https://docs.microsoft.com/intune/deploy-use/monitor-mobile-app-management-policies-with-microsoft-intune) or by using the [Intune console](https://docs.microsoft.com/intune/deploy-use/monitor-apps-in-microsoft-intune).

## Where to go from here

After you have created and deployed an app associated with a MAM policy, you can learn more about the [end-user experience of MAM](end-user-experience-mam.md). This will help prepare you for any issues that might arise.
