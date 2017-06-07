---
# required metadata

title: Manage company owned devices with Intune | Microsoft Docs
description:
keywords:
author: jeffgilb
manager: angrobe
ms.date: 6/7/2017
ms.topic: solution
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: e9e695ec-5608-43bb-bbfb-808b869b1567

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: vlpetros
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Manage company owned devices with Intune

There are many options available to meet employee mobility experience expectations in the modern workplace, including bring your own device (BYOD) programs. However, many organizations want to have more control over which devices are used to access company data. In these scenarios, businesses can implement choose your own device (CYOD) strategies where IT provides managed, mobile devices to employees.

For CYOD strategies to be successful, companies must be able to offer a select variety of devices that users can choose from. This is especially true if the organization is implementing CYOD as an alternative to BYOD because if users do not like the device you issue them, they will find a way to use their own, unmanaged devices. With CYOD, IT can enroll only specific device types into management, reduce support costs, and help protect company data starting from the minute a device is issued to an employee.  Employees get the mobile device options they’ve grown accustomed to in their personal lives without needing to take any additional steps or call the help desk to get their devices managed and company data access configured.  

## How can Enterprise Mobility + Security help you?

You can enroll organization-owned or corporate-owned devices to manage with Microsoft Intune in a variety of ways, depending on the type of device, how the device was purchased, and the needs of the organization. You also can install the Company Portal app to enroll and manage corporate-owned devices, just like [in a BYOD scenario](https://docs.microsoft.com/enterprise-mobility-security/solutions/enable-byod). Corporate-owned iOS devices can be  enrolled directly into management by Intune through the configuration tools provided by Apple. All device types can be enrolled by an admin or manager using the device enrollment manager. Devices with an IMEI number can also be identified and tagged as company-owned to enable COD scenarios.

With EMS you can provide capabilities and experiences to create a productive workplace that embraces diverse workstyles, anywhere. Whether your employees are using iOS, MacOS, Android, or Windows devices, Intune can help you deliver productivity to your people across devices while also keeping your company data secure. In addition to comprehensive mobile device and app lifecycle management, Intune integrates directly with Office 365 and Office mobile apps to allow you to easily protect corporate data.

### Recommended solution

Using Intune you can easily provide employees access to company applications, data, and resources from virtually anywhere on any device, while helping to keep corporate information safe and secure at the same time. Direct integration with Office 365 enables amazing end user experiences and provides the most comprehensive data loss prevention capabilities for Office mobile apps and access control to Office 365. When a device is lost, stolen, or just simply just not needed for work anymore, Intune allows you to selectively wipe only company data from managed devices.

>[!Note]
>Intune recognizes devices as *corporate* owned when any of the methods described in this solution are used to enroll a device. When a device is recognized as corporate by the Intune service, you see **Corporate** in the Ownership column for that device record in the administrator console.

![Choices in a complex device landscape](..\Solutions\media\enable-byod\management-choices-with-intune.png)

> <sup>You can download this infographic at https://gallery.technet.microsoft.com/Infographic-Management-3644ae41.</sup>

### How to implement this solution
The rest of this solution is divided into the following sections that show you how to:
- **Enroll corporate-owned iOS devices**. This section describes how to use the Apple Configurator (on a Mac device) and Apple DEP integration to enroll corporate-owned devices.
- **Enroll corporate-owned Windows 10 devices**. In this section, how to automatically enroll Windows 10 devices into management when they are joined to your company's Azure Active Directory is described.
- **Enroll devices using a device enrollment manager (DEM) account**. Learn how DEM accounts enable a single person from IT to enroll more than the default number of devices into management.
- **Tag corporate-owned devices with international mobile equipment identity (IMEI) numbers**. This section describes another option to begin managing corporate-owned devices at enrollment by importing IMEI numbers that identify corporate-owned devices.
- **Make sure that managed devices comply with basic security requirements**. This section describes how to make sure that devices used to access company apps and data comply with basic security requirements.
- **Provide access to company resources**. This section shows you how IT can enable users to easily, and securely, access company resources by deploying access profiles to managed devices, and how to manage volume-purchased app deployments with Intune.
- **Protect company data**. This section helps you learn how to provide conditional access to company resources, prevent data loss, and remove company apps and data from devices when they are no longer needed for work or have been lost or stolen.

## Enroll corporate-owned iOS devices
If you offer users iOS devices to choose from as part of your CYOD strategy, you can preconfigure enrollment so that the device is managed with Intune from the first time the user turns it on. Intune supports enrollment via the [Apple Device Enrollment Program (DEP)](https://docs.microsoft.com/intune/deploy-use/ios-device-enrollment-program-in-microsoft-intune), or by using the Apple Configurator tool on a Mac computer for [Setup Assistant](https://docs.microsoft.com/intune/deploy-use/ios-setup-assistant-enrollment-in-microsoft-intune) or  [direct](https://docs.microsoft.com/intune/deploy-use/ios-direct-enrollment-in-microsoft-intune) enrollment. You can also deploy an enrollment profile *over the air* to iOS devices purchased through DEP.

### Setup Assistant enrollment
When you use the [Setup Assistant enrollment option for iOS devices](https://docs.microsoft.com/intune/deploy-use/ios-setup-assistant-enrollment-in-microsoft-intune), the device is reset to factory defaults and prepared for final setup by the device's new user. This method requires the admin to connect the iOS device through USB to a Mac computer running [Apple Configurator](http://go.microsoft.com/fwlink/?LinkId=518017) to preconfigure the enrollment. Devices are then delivered to their users, who run the Setup Assistant process. This process configures the device with their work or school credentials and completes the enrollment process.

### Direct enrollment
[Direct enrollment for iOS devices](https://docs.microsoft.com/intune/deploy-use/ios-direct-enrollment-in-microsoft-intune) creates an Apple Configurator–compliant file for use during device preparation. The enrolled device isn’t factory reset, but it has no user affiliation. This method requires the admin to connect the iOS device through USB to a Mac computer running [Apple Configurator](http://go.microsoft.com/fwlink/?LinkId=518017) to enroll the device.

### DEP enrollment
Microsoft Intune can deploy an enrollment profile that enrolls iOS devices that were bought through the [Device Enrollment Program (DEP)](https://docs.microsoft.com/intune/deploy-use/ios-device-enrollment-program-in-microsoft-intune) *over the air*. The enrollment package can include setup assistant options for the device so when a user runs Setup Assistant on the device, the device is enrolled in Intune to provide *day 0* management.

>[!Important]

>[Devices enrolled through DEP](https://docs.microsoft.com/intune/deploy-use/ios-device-enrollment-program-in-microsoft-intune) cannot be unenrolled by users.

## Enroll corporate-owned Windows 10 devices
You can make enrolling Windows devices into management seamless for your users by enabling the automatic enrollment feature in your Azure AD (Premium). When you do that, devices will automatically be enrolled into management with Intune when a user adds a work or school account to register their company owned device when it joins your organization’s Azure AD.

[Windows 10 Azure Active Directory Join (Azure AD Join)](https://docs.microsoft.com/azure/active-directory/active-directory-azureadjoin-overview) makes it easy for users to connect to your enterprise cloud through Azure AD. From there, they can access to organizational apps and resources from their Windows devices. Automatic device enrollment integration means that those devices are also automatically managed by Microsoft Intune.

>[!Tip]

>To enable auto-MDM enrollment in your Azure AD Premium directory from the [Microsoft Azure portal](https://portal.azure.com), go to **Azure Active Directory** > **Mobility (MDM and MAM)** > **Microsoft Intune**.

Azure AD Join is intended for enterprises that are cloud-first/cloud-only. These organizations are typically small and medium-sized businesses that do not have an on-premises Windows Server Active Directory Domain Services (AD DS) infrastructure. That said, Azure AD Join can and will also be used by large organizations on devices that are incapable of doing a traditional domain join (mobile devices, for example) or for users who primarily need to access Office 365 or other Azure AD SaaS apps. When device management is done with Intune, IT administrators can manage Azure AD-joined devices alongside AD DS domain-joined devices in the Configuration Manager management console through [hybrid MDM](https://docs.microsoft.com/sccm/mdm/understand/choose-between-standalone-intune-and-hybrid-mobile-device-management#what-is-hybrid-mdm-with-configuration-manager).
When a user adds a work or school account on a Windows 10 device, the device is automatically tagged as "corporate-owned."

## Enroll devices with a device enrollment manager (DEM) account
A single Intune [device enrollment manager (DEM) account](https://docs.microsoft.com/intune/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune) can be used to enroll large numbers of mobile devices for your organization. After you create a DEM account, it can be used to enroll up to 1,000 devices.

You can use a DEM account to enroll only devices that aren't used by a single, specific user. Those types of devices are good for point-of-sale or utility apps, for example, but not for users who need to access email or company resources.
- Users can't use Apple Volume Purchase Program (VPP) apps because of per-user Apple ID requirements for app management.
- If you use DEM to enroll iOS devices, you can't use the Apple Configurator or Apple Device Enrollment Program (DEP) to enroll devices.

## Tag corporate-owned devices with international mobile equipment identity (IMEI) numbers
Microsoft Intune lets admins [import international mobile equipment identity (IMEI) numbers](https://docs.microsoft.com/intune/deploy-use/specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers) for mobile device platforms by using IMEI numbers to help identify corporate-owned mobile devices.

You can import up to 5,000 IMEI numbers using a specially formatted .CSV file or manually input up to 15 device IMEI numbers at a time from within the Intune administration console. When a device that has IMEI number enrolls in Intune, usually when a user installs the Company Portal app and completes the enrollment process, the device will be tagged as corporate-owned and appear as enrolled in the IMEI Devices group.

## Make sure that managed devices comply with basic security requirements
Whether enrolling an iOS, Android, or Windows 10 device, IT needs to make sure that devices used to access company apps and data comply with basic security requirements. These rules might include using a PIN to access devices and encrypting data stored on devices. A set of such rules is called a [compliance policy](https://docs.microsoft.com/intune/deploy-use/introduction-to-device-compliance-policies-in-microsoft-intune).

When you [create and deploy a compliance policy](https://docs.microsoft.com/intune/deploy-use/create-a-device-compliance-policy-in-microsoft-intune) to a user, all the devices they have managed by Intune will be checked to see if they comply with basic security requirements you’ve defined as part of your CYOD or BYOD policy. After a device has been evaluated for policy compliance, it will report its status back to the Intune service. In some cases, users might be prompted to remediate non-compliant settings, such as using a PIN or device encryption, but other times the company portal app will only notify the user about any compliance problems found.

## Provide access to company resources

This section shows you how IT can enable users to easily, and securely, access company resources by deploying access profiles to managed devices, and managing volume-purchased apps.

### Provide access to company data
The first thing most employees want on their mobile device is access to company email and documents. And they expect to set it up without going through complex steps or calling the help desk. Microsoft Intune makes it easy for you to [create and deploy email settings](https://docs.microsoft.com/intune/deploy-use/configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune) for native email apps that are pre-installed on mobile devices used by your organization.

> [!NOTE]
> Intune supports Android for Work email profile configuration for the Gmail and Nine Work email apps found in the Google Play store.

In addition to email, EMS also helps you control access and protect on-premises company data being accessed from outside traditional corporate security boundaries. Microsoft Intune [Wi-Fi](https://docs.microsoft.com/intune/deploy-use/wi-fi-connections-in-microsoft-intune), [VPN](https://docs.microsoft.com/intune/deploy-use/vpn-connections-in-microsoft-intune#create-a-vpn-profile), and email profiles work together to help your users gain access to the files and resources that they need to do their work wherever they are. Your company's web applications and services hosted on-premises can also be securely accessed and protected using the Azure Active Directory Application Proxy and conditional access.

### Add apps for enrolled devices
It's easy to add apps for enrolled devices with Intune, but before you can deploy or manage an app, you must [add it to Intune](https://docs.microsoft.com/intune/deploy-use/add-apps-for-mobile-devices-in-microsoft-intune) using the Intune Software Publisher. You use the Intune Software Publisher to configure the properties of the app and, where applicable, upload it to your cloud storage space.

With Intune, you can [deploy or manage the following types of apps](https://docs.microsoft.com/intune/deploy-use/add-apps) to enrolled devices:
- **Software installer**. These kinds of apps include Windows software installer (.exe, or .msi), App Package for Android (.apk), App Package for iOS (.ipa), Windows Phone app package (.xap, .appx, and .appxbundle), Windows app package (.appx, .appxbundle), and Windows Installer through MDM (.msi) files. All software installer app types are uploaded to your [cloud storage space](https://docs.microsoft.com/intune/deploy-use/add-apps#cloud-storage-space).
- **External link**. This type of app deployment provides an external link (URL) that lets users download an app from an app store or a link to a web-based app that runs from the web browser. Apps based on external links are not stored in your Intune cloud storage space.
- **Managed iOS app from the app store**. You can use managed iOS apps to manage and deploy iOS apps that are free of charge from the app store. You can also use managed iOS apps to associate mobile application management policies with compatible apps and review their status in the administrator console. Managed iOS apps are not stored in your Intune cloud storage space.

### Manage volume-purchased apps
You can easily [deliver store apps to managed devices](https://docs.microsoft.com/intune/deploy-use/deploy-apps-in-microsoft-intune), and even target apps to unmanaged devices using the company portal website, but Intune also allows you to manage and deploy apps that you purchased in volume from the iOS app store and the Windows Store for Business. This helps you reduce the administrative overhead of tracking volume-purchased apps.

> [!TIP]
> You can easily [configure Single Sign On (SSO) with Azure AD Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) to enable users to sign into apps with the domain user name and password they use on-premises. In addition, you can [provide internet-based access to web apps hosted on-premises](https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started) using the Azure Active Directory Application Proxy.

With Intune it is easy to import the volume license information from either app store, track how many licenses you have used, and prevent your users from installing more copies of the app than you own.

-   [Manage volume-purchased apps for iOS devices](https://docs.microsoft.com/intune/deploy-use/manage-ios-apps-you-purchased-through-a-volume-purchase-program-with-microsoft-intune). You purchase multiple licenses for iOS apps through the [Apple Volume Purchase Program for Business](http://www.apple.com/business/vpp/). This involves setting up an Apple VPP account from the Apple website and uploading the Apple VPP token to Intune. You can then synchronize your volume purchase information with Intune and track your volume-purchased app use.

-   [Windows Store for Business](https://docs.microsoft.com/intune/deploy-use/manage-apps-you-purchased-from-the-windows-store-for-business-with-microsoft-intune). The [Windows Store for Business](https://www.microsoft.com/business-store) gives you a place to find and purchase apps for your organization, individually, or in volume. By connecting the store to Microsoft Intune, you can manage volume-purchased apps from the Intune portal.

## Protect company data

Intune protects company data through multiple technology layers. At the identity layer, conditional access protects access to services by only allowing access from managed and compliant devices. At the client application layer, app protection policies protect against data loss by preventing data from moving to nonprotected apps or storage locations—and by wiping data when a device is lost or stolen.

### Enforce conditional access to company resources

You can use compliance policies in combination with [conditional access policies](https://docs.microsoft.com/intune/deploy-use/restrict-access-to-email-and-o365-services-with-microsoft-intune) to check if devices comply with basic security requirements that your BYOD policy requires. If a device is not compliant with policy, conditional access rules are enforced and access is denied until the device is configured to meet policy requirements. This ensures that only managed and compliant devices can access company data from services like Exchange ([Exchange On-premises](https://docs.microsoft.com/intune/deploy-use/restrict-access-to-exchange-onpremises-with-microsoft-intune) or [Exchange Online](https://docs.microsoft.com/intune/deploy-use/restrict-access-to-exchange-online-with-microsoft-intune)), SharePoint Online, Skype for Business Online, and others.

> [!IMPORTANT]
> Conditional access policies will not work if there is no compliance policy in place to validate compliance.

### Prevent data loss of company data with application protection policies

Intune’s application protection policies give you the versatility to manage how your data is accessed with or without device enrollment. The ability to protect company data with or without device enrollment give you the ability to enable data protection scenarios so that company data can be accessed securely even when a user is reluctant to enroll their device into management.

You can use [Intune app protection policies](https://docs.microsoft.com/intune/deploy-use/create-and-deploy-mobile-app-management-policies-with-microsoft-intune) to help protect company data that is accessed by your users' iOS and Android devices. By implementing these app-level policies, you are able to control how company data is used and shared by employees even if the device itself isn’t managed by Intune.

Use [Windows Information Protection (WIP) policies](https://docs.microsoft.com/intune/deploy-use/microsoft-intune-policy-reference#windows-configuration-policies) to do the same for managed Windows 10 devices. These policies work without interfering with the employee experience or requiring changes to your network environment or other apps.

### Wipe company data while leaving personal data intact

When a device is no longer needed for work, is being repurposed, or maybe has just gone missing, you need to be able to remove company apps and data from it. To do this you can leverage Intune's selective wipe and full wipe capabilities. Your users can also remotely wipe their own personally owned devices they've enrolled into management from the Intune Company Portal.

Rather than doing a [full wipe](https://docs.microsoft.com/intune/deploy-use/use-remote-wipe-to-help-protect-data-using-microsoft-intune#full-wipe) that restores a device to its factory default settings and removes user data and settings, you can use [selective wipe](https://docs.microsoft.com/intune/deploy-use/use-remote-wipe-to-help-protect-data-using-microsoft-intune#selective-wipe) functionality to only remove company data from the device while leaving users’ personal data intact.

Once initiated, the device will immediately begin the selective wipe process to be removed from management. When the process is complete, all company data is deleted and the device name will be removed from the Intune administrator console completing the device management lifecycle.

### Learn more
[Start using Enterprise Mobility + Security](https://docs.microsoft.com/enterprise-mobility/solutions/ems-get-started)

[Microsoft Enterprise Mobility](https://www.microsoft.com/en-us/cloud-platform/enterprise-mobility)
