---
# required metadata

title: Using Mobile Application Management policies in Configuration Manager
description:
keywords:
author: craigcaseyMSFT
manager: swadhwa
ms.date: 05/12/2016
ms.topic: article
ms.prod:
ms.service:
ms.technology:
ms.assetid: 74288276-84d3-4d24-8307-7875491be9c9

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer:
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Use Mobile Application Management policies in Configuration Manager
Beginning with System Center 2012 Configuration Manager SP2, app management policies let you modify the functionality of apps that you deploy to help bring them into line with your company compliance and security policies. For example, you can restrict cut, copy and paste operations within a restricted app, or configure an app to open all web links inside a managed browser. App management policies support:

- Devices that run Android 4 and later.
- Devices that run iOS 7 and later.

> [!TIP]
> In addition to managed devices, mobile app management policies can be used to protect apps on devices that are not managed by Intune. Using this new capability, you can apply mobile app management policies for apps connecting to Office 365 services. This is not supported for apps connecting to on-premises Exchange or SharePoint.
To use this new capability, you must use the Azure portal. The following topics can help you get started:
- [Get ready to configure mobile app management policies with Microsoft Intune](https://docs.microsoft.com/en-us/intune/deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune)
- [Create and deploy mobile app management policies with Microsoft Intune](https://docs.microsoft.com/en-us/intune/deploy-use/create-and-deploy-mobile-app-management-policies-with-microsoft-intune)

Unlike configuration items and baselines in Configuration Manager, you do not deploy an application management policy directly. Instead, you associate the policy with the app deployment type (DT) that you want to restrict. When the app DT is deployed and installed on devices, the settings you specify will take effect.

To apply restrictions to an app, the app must incorporate the Microsoft Intune App Software Development Kit (SDK). There are two methods of obtaining this type of app:

- **Use a policy managed app** (Android and iOS): Has the App SDK built-in. To add this type of app, you specify a link to the app from an app store such as the iTunes store or Google Play. No further processing is required for this type of app. For a list of the policy managed apps that are available for iOS and Android devices, see [Microsoft Intune mobile application gallery](https://www.microsoft.com/en-us/cloud-platform/microsoft-intune-partners).
- **Use a ‘wrapped’ app ** (Android and iOS): Apps that are repackaged to include the App SDK by using the Microsoft Intune App Wrapping Tool. This tool is typically used to process company apps that were created in-house. It cannot be used to process apps that were downloaded from the app store. See [Prepare iOS apps for mobile application management with the Microsoft Intune App Wrapping Tool](https://docs.microsoft.com/en-us/intune/deploy-use/prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool) and [Prepare Android apps for mobile application management with the Microsoft Intune App Wrapping Tool](https://docs.microsoft.com/en-us/intune/deploy-use/prepare-android-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool).

## Create and deploy an app with a mobile application management policy

- Step 1: Get the link to a policy managed app, or create a wrapped app.
- Step 2: Create a Configuration Manager application that contains an app.
- Step 3: Create a mobile application management policy.
- Step 4: Associate the application management policy with a deployment type.
- Step 5: Monitor the app deployment.

### Step 1: Obtain the link to a policy managed app, or create a wrapped app.
- **To obtain a link to a policy managed app** - From the app store, find, and note the URL of the policy managed app you want to deploy.
For example, the URL of the Microsoft Word for iPad app is [https://itunes.apple.com/us/app/microsoft-word-for-ipad/id586447913?mt=8](https://itunes.apple.com/us/app/microsoft-word-for-ipad/id586447913?mt=8)
- **To create a wrapped app** - Use the information in the topics [Prepare iOS apps for mobile application management with the Microsoft Intune App Wrapping Tool](https://docs.microsoft.com/en-us/intune/deploy-use/prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool) and [Prepare Android apps for mobile application management with the Intune App Wrapping Tool](https://docs.microsoft.com/en-us/intune/deploy-use/prepare-android-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool) to create a wrapped app. The tool creates a processed app and an associated manifest file. You will use these files when you create a Configuration Manager application containing the app.

### Step 2: Create a Configuration Manager application that contains an app.
The procedure to create the Configuration Manager application differs depending on whether you are using a policy managed app (external link), or an app that was created by using the Microsoft Intune App Wrapping Tool for iOS (App package for iOS).

See [How to Control Apps Using Mobile Application Management Policies in Configuration Manager](https://technet.microsoft.com/en-us/library/mt131414.aspx?f=255&MSPPError=-2147217396#BKMK_Step2) for the complete steps required to create a Configuration Manager application that contains an app.

After you have created the application, it is displayed in the **Applications** node of the **Software Library** workspace.

### Step 3: Create a mobile application management policy.
Next, you will [create an application management policy](https://technet.microsoft.com/en-us/library/mt131414.aspx?f=255&MSPPError=-2147217396#bkmk_step3) that you will associate with the application. You can create a general or managed browser policy.

After you have created the new policy, it is displayed in the **Application Management Policies** node of the **Software Library** workspace.

### Step 4: Associate the application management policy with a deployment type.
When a deployment type is created for an app that requires an application management policy, Configuration Manager will recognize that an app management policy must be linked to this deployment type when the associated app gets deployed and prompt you to associate an app management policy. For the Managed Browser, you will be required to associate both a General and Managed Browser policy. For more information, see [How to Create and Deploy Applications for Mobile Devices in Configuration Manager](https://technet.microsoft.com/en-us/library/dn469410.aspx).

> [!TIP]
> For devices that run operating systems earlier than iOS 7.1, associated policies will not be removed when the app is uninstalled.

> If the device is unenrolled from Configuration Manager, polices are not removed from the apps. Apps that had policies applied will retain the policy settings even after the app is uninstalled and reinstalled.


### Step 5: Monitor the app deployment.
Once you have created and deployed an app associated with a mobile application management policy, you can [monitor the app and resolve any policy conflicts](https://technet.microsoft.com/en-us/library/mt131414.aspx?f=255&MSPPError=-2147217396#BKMK_Step5).

For general information about monitoring applications, see [How to Monitor Applications in Configuration Manager](https://technet.microsoft.com/en-us/library/gg682201.aspx).

## Where to go from here

After you have created and deployed an app associated with a MAM policy, you can learn more about the [end-user experience of MAM](end-user-experience-mam.md). This will help prepare you for any issues that might arise.
