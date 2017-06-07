---
# required metadata

title: Enable BYOD with Intune | Microsoft Docs
description:
keywords:
author: jeffgilb
manager: angrobe
ms.date: 6/7/2017
ms.topic: solution
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 6d31eebe-81d2-4c6b-bfec-fbd536096dda

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: vlpetros
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---
# Enable BYOD with Intune
Supporting digital transformation brings new challenges for IT as they strive to protect company data while enabling employees to stay productive in today’s increasingly complex mobile landscape. As organizations continue to move to the cloud, employees expect to be productive on the go with an experience that matches their consumer experiences across many devices.

![Choices in a complex device landscape](..\Solutions\media\enable-byod\management-choices-with-intune.png)

> <sup>You can download this infographic at https://gallery.technet.microsoft.com/Infographic-Management-3644ae41.</sup>

Some of those devices are company-managed and might be dedicated to a specific user or one device might be shared between multiple employees. You will also have devices that are employee-managed. These personal devices could be their iPhone or PC that they use for work every day or a companion device that they are using to get online from time to time, like their daughter’s iPad or a family computer.

In addition to devices, the place where people get their work done is also changing. People no longer work exclusively in a traditional office or workplace. The modern workforce now works from home, in cafes, at customer sites, on the road, and even in the air. Because of this, Bring Your Own Device (BYOD) programs have become commonplace in the modern workplace. It’s up to IT to somehow cash in on the benefits and opportunities to increase employee satisfaction and reduce costs while also keeping control of company data.

Successful BYOD programs gain tighter control and increased security without having to impose complex processes or change the way people work. A great experience for end users means they have a higher likelihood of using the protected solutions that you provide and less likely to create workarounds that are completely off your radar to get work done.

## How can Enterprise Mobility + Security (EMS) help you?

With EMS you can provide capabilities and experiences to create a productive workplace that embraces diverse workstyles, anywhere. Whether your employees are using iOS, MacOS, Android, or Windows devices, Microsoft Intune, part of EMS, can help you deliver productivity to your people across devices while also keeping your company data secure. Intune provides MAM and MDM capabilities that allow you to protect corporate data with or without device management. In addition to comprehensive mobile device and app lifecycle management, Intune integrates directly with Office 365 and Office mobile apps.

### Recommended solution

Using Intune you can easily provide employees access to company applications, data, and resources from virtually anywhere on any device, while helping to keep corporate information safe and secure at the same time. Direct integration with Office 365 enables amazing end user experiences and provides the most comprehensive data loss prevention capabilities for Office mobile apps and access control to Office 365. When a device is lost, stolen, or simply just not needed for work anymore, Intune allows you to selectively wipe only company data from BYOD devices.

Here's a short video to hear from real IT Pros and real users on their needs and challenges balancing productivity and protection in a mobile-first, cloud-first world:
<iframe width="675" height="480" src="https://www.youtube.com/embed/pgAmKnluwVw" frameborder="0" allowfullscreen></iframe>

### How to implement this solution

The rest of this solution is divided into the following sections that show you how to:

-   **Enroll devices and check for compliance**. This section describes how to enable users to enroll devices (iOS, MacOS, Android, Android for Work, and Windows) into management with Intune and deploy policies to them and ensure they are compliant with basic security requirements.

-   **Provide access to company resources**. This section shows you how IT can enable users to easily, and securely, access company resources by deploying access profiles to managed devices, and how to manage volume-purchased app deployments with Intune.  

-   **Protect company data**. This section helps you learn how to provide conditional access to company resources, prevent data loss, and remove company apps and data from devices when they are no longer needed for work or have been lost or stolen.

## **Enroll devices and check for compliance**

This section describes how to enable users to enroll devices into management with Intune and ensure their devices are compliant with basic security requirements.

### Enable users to enroll their personal devices into management

Enrolling devices and PCs into management with Intune ensures all the policies and access profiles you’ve configured for managed devices can be applied. Before you can enroll devices, you will first need to [prepare the Intune service](https://docs.microsoft.com/intune/deploy-use/get-ready-to-enroll-devices-in-microsoft-intune) itself by assigning licenses to users, setting the mobile device management authority, and satisfy the various enrollment requirements for the different device types that you want to manage. While you are at it, you should probably also [customize the company portal](https://docs.microsoft.com/intune/deploy-use/get-ready-to-enroll-devices-in-microsoft-intune#configure-the-intune-company-portal) with support information and company-specific branding to provide a trusted enrollment and support experience for your users.

After preparing the Intune service, the process to enroll devices into management is straightforward, but differs slightly for the various device types:

-   **iOS and Mac devices**. You'll need to get an Apple Push Notification service (APNs) certificate to enroll iPads, iPhones, or MacOS devices. After you've [uploaded your APNs certificate to Intune](https://docs.microsoft.com/en-us/intune/deploy-use/set-up-ios-and-mac-management-with-microsoft-intune), users can [enroll iOS devices](https://docs.microsoft.com/intune/enduser/enroll-your-device-in-intune-ios) using the Company Portal app and use the Company Portal website to [enroll MacOS devices](https://docs.microsoft.com/intune/enduser/enroll-your-device-in-intune-mac-os-x).

-   **Android devices**. There's nothing you need to do to get the Intune service ready to enroll Android devices. Users can just [enroll their Android devices](https://docs.microsoft.com/intune/deploy-use/set-up-android-management-with-microsoft-intune) into management using the Company Portal app available from Google Play.

-   **Android for Work**. To [set up Android for Work](https://docs.microsoft.com/intune/deploy-use/set-up-android-for-work) for Android 5.0 Lollipop and later devices that support work profiles to be managed by Intune, your organization needs to sign up for Android for Work with Google and then configure Android for Work settings in the ADMIN node of the Intune administration console.

-   **Windows Phones and PCs**. You should [set a DNS alias for the enrollment server](https://docs.microsoft.com/intune/deploy-use/set-up-windows-phone-management-with-microsoft-intune) to make enrolling Windows devices easier. Otherwise, you can [enroll Windows devices](https://docs.microsoft.com/intune/enduser/enroll-your-w10-phone-or-w10-pc-windows) by adding a work or school account.

> [!TIP]
> You can make enrolling Windows devices even easier for your users by [enabling the automatic enrollment](https://docs.microsoft.com/intune/deploy-use/set-up-windows-device-management-with-microsoft-intune#azure-active-directory-enrollment) feature in your Azure AD (Premium). When you do that, devices will automatically be enrolled into management with Intune when a user adds a work or school account to register their personal device or a company owned device joins your organization’s Azure AD.

### Make sure that managed devices comply with basic security requirements

After users enroll their devices into management, IT needs to make sure that devices used to access company apps and data comply with basic security requirements. These rules might include using a PIN to access devices and encrypting data stored on devices. A set of such rules is called a [compliance policy](https://docs.microsoft.com/intune/deploy-use/introduction-to-device-compliance-policies-in-microsoft-intune).

When you [create and deploy a compliance policy](https://docs.microsoft.com/intune/deploy-use/create-a-device-compliance-policy-in-microsoft-intune) to a user, all the devices they have managed by Intune will be checked to see if they comply with basic security requirements you’ve defined as part of your BYOD policy. After a device has been evaluated for policy compliance, it will report its status back to the Intune service. In some cases, users might be prompted to remediate non-compliant settings, such as using a PIN or device encryption, but other times the company portal app will only notify the user about any compliance problems found.

## Provide access to company resources

This section shows you how IT can enable users to easily, and securely, access company resources by deploying access profiles to managed devices, and managing volume-purchased apps.

### Provide access to company data
The first thing most employees want on their mobile device is access to company email and documents. And they expect to set it up without going through complex steps or calling the help desk. Microsoft Intune makes it easy for you to [create and deploy email settings](https://docs.microsoft.com/intune/deploy-use/configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune) for native email apps that are pre-installed on mobile devices used by your organization.

> [!NOTE]
> Intune supports Android for Work email profile configuration for the Gmail and Nine Work email apps found in the Google Play store.

In addition to email, EMS also helps you control access and protect on-premises company data being accessed from outside traditional corporate security boundaries. Microsoft Intune [Wi-Fi](https://docs.microsoft.com/intune/deploy-use/wi-fi-connections-in-microsoft-intune), [VPN](https://docs.microsoft.com/intune/deploy-use/vpn-connections-in-microsoft-intune#create-a-vpn-profile), and email profiles work together to help your users gain access to the files and resources that they need to do their work wherever they are. Your company's web applications and services hosted on-premises can also be securely accessed and protected using the Azure Active Directory Application Proxy and conditional access.

### Manage volume-purchased apps
You can easily [deliver store apps to managed devices](https://docs.microsoft.com/intune/deploy-use/deploy-apps-in-microsoft-intune), and even target apps to unmanaged devices using the company portal website, but Intune also allows you to manage and deploy apps that you purchased in volume from the iOS app store and the Windows Store for Business. This helps you reduce the administrative overhead of tracking volume-purchased apps.

> [!TIP]
> You can easily [configure Single Sign On (SSO) with Azure AD Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) to enable users to sign into apps with the domain user name and password they use on-premises. In addition, you can [provide internet-based access to web apps hosted on-premises](https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started) using the Azure Active Directory Application Proxy.

With Intune it is easy to import the volume license information from either app store, track how many licenses you have used, and prevent your users from installing more copies of the app than you own.

-   [Manage volume-purchased apps for iOS devices](https://docs.microsoft.com/intune/deploy-use/manage-ios-apps-you-purchased-through-a-volume-purchase-program-with-microsoft-intune). You purchase multiple licenses for iOS apps through the [Apple Volume Purchase Program for Business](http://www.apple.com/business/vpp/). This involves setting up an Apple VPP account from the Apple website and uploading the Apple VPP token to Intune. You can then synchronize your volume purchase information with Intune and track your volume-purchased app use.

-   [Windows Store for Business](https://docs.microsoft.com/intune/deploy-use/manage-apps-you-purchased-from-the-windows-store-for-business-with-microsoft-intune). The [Windows Store for Business](https://www.microsoft.com/business-store) gives you a place to find and purchase apps for your organization, individually, or in volume. By connecting the store to Microsoft Intune, you can manage volume-purchased apps from the Intune portal.

## Protect company data

Intune protects company data through multiple technology layers. At the identity layer, conditional access protects access to services by only allowing access from managed and compliant devices. At the client application layer, mobile application management (MAM) protects data loss by preventing data from moving to nonprotected apps or storage locations—and by wiping data when a device is lost or stolen.

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
