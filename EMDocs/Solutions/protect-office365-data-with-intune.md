---
# required metadata

title: Protect Office 365 company data with Microsoft Intune | Microsoft Docs
description: Together, EMS and Office 365 offer a complete managed mobile productivity solution that equips your users with the gold standard of productivity and your IT staff with deeply integrated data controls.
keywords:
author: jeffgilb
manager: swadhwa
ms.date: 1/18/2017
ms.topic: solution
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: cc0d2e1f-9c34-4dcb-ac1f-2f355e9ebb7e

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: vlpetros
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Protect Office 365 company data with Intune
The first thing most employees want on their mobile device is access to company email and documents. And they expect to set it up without going through complex steps or calling the help desk. IT on the other hand wants to keep corporate data secure wherever it is without the headache of maintaining a large, on-premises infrastructure. With Enterprise Mobility + Security (EMS) you'll be able to keep your employees productive with their favorite apps and devices—and your company data protected. Keep reading to see how.

## How can Enterprise Mobility + Security (EMS) help you?
EMS is the only solution that is designed to natively protect Microsoft Office email, files, and apps on all of the devices your users bring to work. Behind the scenes EMS makes it easy to deliver secure email to employees on the go by working to provide four layers of protection across identities, devices, apps, and data. With EMS, your employees will get secure and seamless access to corporate email and documents as well as familiar email and productivity experiences with Office Mobile apps such as Outlook, Word, Excel, PowerPoint, and OneDrive.

Office 365 is designed for employees who want the flexibility to take their work with them, wherever they go, without sacrificing the user experience. Together, EMS and Office 365 offer a complete managed mobile productivity solution that equips your users with the gold standard of productivity and your IT staff with deeply integrated data controls.

### Recommended solution
Using Intune you can easily provide employees access to company applications, data, and resources from virtually anywhere on any device, while helping to keep corporate information safe and secure at the same time. In addition to just being easier, Intune is also a more modern and cost effective way to protect company data than most traditional on-premises solutions. With Intune securing Office 365 data, there’s no need to install and maintain any on-premises infrastructure or open your company firewall to route traffic through it.

Here's a short video to give you a quick introduction to how Intune and Office 365 work together to provide a seamless experience for employees to access your company data securely from iOS, Android, and Windows devices:

<iframe width="675" height="480" src="https://www.youtube.com/embed/To9zfl6-Z6Y" frameborder="0" allowfullscreen></iframe>

### How to implement this solution
The rest of this solution is divided into the following sections that show you how to protect Office 365 company data with Intune:
- **Enroll mobile devices and Windows PCs into management**. This section describes how to enroll devices  (iOS, Android, Android for Work, and Windows PCs) into management with Intune so that you deploy policies to them that protect Office 365 company data.
- **Secure access to Office 365 services**. In this section you can learn about Intune compliance policies and how to manage conditional access to the Exchange Online and SharePoint online Office 365 services.
- **Protect company data**. This section shows you how to use app protection policies for Android and iOS devices, and also how to leverage Windows Information Protection (WIP) policies to safeguard company app data on Windows 10 PCs managed as devices by Intune.
- **Selectively wipe company data**. This section helps you learn how to remove company apps and data from devices when they are no longer needed for work or have been lost or stolen.


## Enroll mobile devices and Windows PCs into management
Enrolling devices and PCs into management with Intune ensures all the policies and access profiles you’ve configured for managed devices are applied. Before you can enroll devices, you will first need to [prepare the Intune service](https://docs.microsoft.com/intune/deploy-use/get-ready-to-enroll-devices-in-microsoft-intune) itself by assigning licenses to users, setting the mobile device management authority, and satisfy the various enrollment requirements for the different device types that you want to manage. While you are at it, you should probably also [customize the company portal](https://docs.microsoft.com/intune/deploy-use/get-ready-to-enroll-devices-in-microsoft-intune#configure-the-intune-company-portal) with support information and company-specific branding to provide a trusted enrollment and support experience for your users.

After preparing the Intune service, the process to enroll devices into management is pretty straightforward, but slightly different for the various device types:
- **iOS and Mac devices**. You'll need to get an Apple Push Notification service (APNs) certificate to enroll iPads, iPhones, or Mac OS X devices. After you've [uploaded your APNs certificate to Intune](https://docs.microsoft.com/en-us/intune/deploy-use/set-up-ios-and-mac-management-with-microsoft-intune), you can [enroll iOS devices](https://docs.microsoft.com/intune/enduser/enroll-your-device-in-intune-ios) using the Company Portal app and use the Company Portal website to [enroll Mac OS X devices](https://docs.microsoft.com/intune/enduser/enroll-your-device-in-intune-mac-os-x).
- **Android devices**. There's nothing you need to do to get the Intune service ready to enroll Android devices. Users can just [enroll their Android devices](https://docs.microsoft.com/intune/deploy-use/set-up-android-management-with-microsoft-intune) into management using the Company Portal app available from Google Play.
-   **Android for Work**. To [set up Android for Work](https://docs.microsoft.com/intune/deploy-use/set-up-android-for-work) for Android 5.0 Lollipop and later devices that support work profiles to be managed by Intune, your organization needs to sign up for Android for Work with Google and then configure Android for Work settings in the ADMIN node of the Intune administration console.
- **Windows Phones and PCs**. You should [set a DNS alias for the enrollment server](https://docs.microsoft.com/en-us/intune/deploy-use/set-up-windows-phone-management-with-microsoft-intune) to make enrolling Windows devices easier. Otherwise, you can [enroll Windows devices](https://docs.microsoft.com/intune/enduser/enroll-your-w10-phone-or-w10-pc-windows) by adding a work or school account.

> [!TIP]
> You can make enrolling Windows devices even easier for your users by [enabling the automatic enrollment](https://docs.microsoft.com/intune/deploy-use/set-up-windows-device-management-with-microsoft-intune#azure-active-directory-enrollment) feature in your Azure AD (Premium). When you do that, devices will automatically be enrolled into management with Intune when a user adds a work or school account to register their personal device or a company owned device joins your organization’s Azure AD.

## Secure access to Office 365 services
Your users expect to get access to all of their company email and files when using Office 365 mobile apps, but you also need to be sure that only trusted devices are connecting to company resources. To help accomplish this, you can use Intune conditional access policies to make sure that employees access Office 365 cloud services only from managed and policy compliant devices.

For conditional access policies to work you first have to define an [Intune device compliance policy](https://docs.microsoft.com/intune/deploy-use/introduction-to-device-compliance-policies-in-microsoft-intune). These kinds of Intune policies check devices, both when first being enrolled and periodically afterwards, to ensure devices settings are configured the way you want them to be. This makes it easy for you to be sure only devices that meet your security requirements can access company resource. Just define for yourself what makes a device compliant (e.g. require password to unlock, allow or deny simple passwords, minimum password length, not jailbroken, etc.) by creating an Intune device compliance policy and then deploy it to users.

> [!IMPORTANT]
> Conditional access policies will not work if there is no compliance policy in place to validate compliance.

[Conditional access policies](https://docs.microsoft.com/intune/deploy-use/restrict-access-to-email-and-o365-services-with-microsoft-intune) can be used to secure access to Office 365 services such as Dynamics CRM Online<sup>1</sup>, Exchange Online<sup>2</sup>, SharePoint Online<sup>2</sup>, and Skype for Business Online<sup>1</sup>. Conditional access policies will be configured for Exchange Online and SharePoint Online in the following examples.  

> <sup>1</sup> iOS and Android only.

> <sup>2</sup> iOS, Android, and Windows devices.

### Secure access to Exchange Online
With Intune, your company’s Exchange Online email is protected according to the conditional access and compliance policies that you set. For example, you can [restrict access to Exchange Online](https://docs.microsoft.com/intune/deploy-use/restrict-access-to-exchange-online-with-microsoft-intune) email to devices that don’t use a strong password, are not jailbroken, and are not encrypted.

Here's what happens when a user tries to check their email using a device that is not managed by Intune when you have configured conditional access policies to get to Exchange Online:
1. The user tries to read their Exchange online company email using the native email app on their unmanaged Android device. Access to email is denied because the device is not being managed by Intune and so is not compliant with your compliance policy.
2. The only email the user sees is from the Intune service telling them that their device is not compliant with company policies and that they need to enroll it before getting access to their email.
3. After the device is enrolled, and evaluated as compliant with company policies, full access to company email is restored.

![Images showing how conditional access works for Exchange Online](..\Solutions\media\protect-office365-data-with-intune\protect-office365-data-with-intune-fig1.png)

### Secure access to SharePoint Online
Intune can also easily [secure access to SharePoint Online](https://docs.microsoft.com/intune/deploy-use/restrict-access-to-sharepoint-online-with-microsoft-intune) files using conditional access. Just like protecting access to email, you'll need to set up two policies that must be satisfied to enabled access: a device compliance policy to make sure company policies are being followed on the device and a conditional access policy that sets conditions that must be meet to access the service.

When a user attempts to use an unmanaged device to connect to the SharePoint online service protected by Intune conditional access policies this happens:
1.	The user is denied access to SharePoint Online resources and instead gets a message to beef up security and links to enroll their device into Intune management.
2.	Following the links provided by the access denied message, the user enrolls their device.
3.	After the device is enrolled, and evaluated as compliant with company policies, full access to company SharePoint Online data is restored.

![Images showing how conditional access works for SharePoint Online](..\Solutions\media\protect-office365-data-with-intune\protect-office365-data-with-intune-fig2.png)

## Protect company data
You probably already know that most employees use their mobile devices for both personal and work reasons. Especially now with the increase of employee-owned devices now being used for work, there’s an increasing risk of accidental data leaks through apps and services, like email, social media, and the public cloud which are outside of your control. For example, when an employee sends the latest engineering pictures from their personal email account, copies, and pastes product info into a tweet, or saves an in-progress sales report to their public cloud storage. So, the challenge for you is that while you need to keep employees productive, you must also do what you can to prevent both intentional and unintentional company data leaks.

While conditional access policies allow you to make sure only compliant devices and users can access email, there is still the question of protecting the emails themselves along with any attached files. How do you stop that content from being copied, moved, saved to a different location, or shared with others? Intune solves this problem by using Mobile Application Management (MAM) policies for iOS and Android devices and Windows Information Protection (WIP) policies for Windows 10 PCs and mobile devices.  

### MAM for managed iOS and Android mobile devices
You can use Intune mobile app management (MAM) policies to help protect company data that is accessed by your users' iOS and Android devices. By implementing these app-level policies, you are able to control how company data is used and shared by employees.

> [!TIP]
> Intune MAM policies can be used independent of any mobile-device management (MDM) solution as long as the user has been assigned an Intune license. This  means that you can protect your company’s data with or without enrolling devices into Intune management or even if a non-Microsoft MDM service manages the device.

As an admin, you [configure Intune MAM app policy settings from the Azure admin portal](https://docs.microsoft.com/intune/deploy-use/create-and-deploy-mobile-app-management-policies-with-microsoft-intune). The two types of settings included in MAM policies are *data relocation* and *access* settings. Data relocation policies define how data from a protected app can be used. For example, you can prevent “Save As” or cut, copy, paste functions. Access policy settings determine the level of device security you think is necessary for employees to use the app. With these settings you can require an additional app PIN or keep the app from even running on jailbroken or rooted devices.

The following screen shots show some ways to protect an app using Intune MAM policies. In this example a PIN is required to access the app (an access setting) and company data is protected by denying pasting company information to unmanaged apps (data relocation setting):

1.	The first time the managed app (Yammer for iOS in this example) is started, the user is prompted to create a PIN to access the app. Afterwards, they'll have to enter that PIN every time the app starts.
2.	The user can copy company data like Yammer conversations and paste it into other managed apps.
3.	However, when the user tries to paste that content into a text message (or any other unmanaged app) the paste function will not be available.  

![Images showing how MAM policies work](..\Solutions\media\protect-office365-data-with-intune\protect-office365-data-with-intune-fig3.png)

### Windows Information Protection (WIP) for managed Windows 10 PCs and mobile devices
Intune's WIP policies help protect against potential data leaks from managed Windows 10 devices. Best of all, these policies work without interfering with the employee experience or requiring changes to your network environment or other apps.

Here's how it works: enterprise data is automatically encrypted after it’s loaded on a managed Windows device from an enterprise source or if an employee marks the data as work (versus personal). When enterprise data is written to disk, WIP uses the Windows-provided Encrypting File System (EFS) to protect it and associate it with your enterprise identity. When you make an Intune WIP policy, you define a list of trusted apps that are allowed to access and modify company data. Next, AppLocker functionality works in the background with the operating system to control what apps can run as well as how company data can be accessed and shared. Allowed apps don’t have to be modified to open company data because they're on the list that allows Windows to grant them access to company data.

> [!TIP]
> When WIP policies are protecting apps and company data, end-users will see “Managed” in addition to each of the allowed app names in the Start Menu on their devices. App shortcuts and saved files will also show the WIP briefcase icon in addition to the standard app icons.
<img src="..\Solutions\media\protect-office365-data-with-intune\protect-office365-data-with-intune-fig4.png" alt="Image showing how WIP policies affect the Start Menu and files" style="width:376px;height:112x;">

[WIP configuration policy settings](https://docs.microsoft.com/intune/deploy-use/microsoft-intune-policy-reference#windows-configuration-policies) allow you to set different levels of control and auditing from within the Intune administrator console. Data protection levels range from **Silent** (log WIP activity only) to **Block** which will completely stop users from sharing any content from protected apps. **Override** is a middle setting that will enable users to share company data to unprotected apps with a warning, but also log all such actions for later review.

This is how Intune WIP policies can help protect company data on managed Windows 10 devices:
1.	A new WIP policy is created and deployed to users from the Intune administrator console.
2.	In this example, the AppLocker information for Microsoft Word is used to add Word 2016 to the list of allowed apps, the policy restriction level is set to Override, and the policy is deployed to users.
3.	A user attempts to paste company data copied from a protected Word 2016 document into a new, unprotected instance of Notepad. They are immediately prompted to verify this change from work to personal classification is planned and that the action will be tracked.

![Images showing how WIP policies work](..\Solutions\media\protect-office365-data-with-intune\protect-office365-data-with-intune-fig5.png)

## Selectively wipe company data
When a device is no longer needed for work, is being repurposed, or maybe has just gone missing, you need to be able to remove company apps and data from it. To do this you can leverage Intune's selective wipe and full wipe capabilities. Your users can also remotely wipe their own personally owned devices they've enrolled into management from the Intune Company Portal.

Rather than doing a [full wipe](https://docs.microsoft.com/intune/deploy-use/use-remote-wipe-to-help-protect-data-using-microsoft-intune#full-wipe) that restores a device to its factory default settings and removes user data and settings, you can use [selective wipe](https://docs.microsoft.com/intune/deploy-use/use-remote-wipe-to-help-protect-data-using-microsoft-intune#selective-wipe) functionality to only remove company data from the device while leaving users’ personal data intact.

Performing a selective wipe of a device is as easy as right-clicking a device name, selecting **Retire/Wipe**, and then the **Selectively wipe the device**:

![Image of the selective wipe options in the Intune console](..\Solutions\media\protect-office365-data-with-intune\protect-office365-data-with-intune-fig6.png)

Once initiated, the device will immediately begin the selective wipe process to be removed from management. When the process is complete, all company data is deleted and the device name will be removed from the Intune administrator console completing the device management lifecycle.

### Learn more
[Start using Enterprise Mobility + Security](https://docs.microsoft.com/enterprise-mobility/solutions/ems-get-started)

[Microsoft Enterprise Mobility](https://www.microsoft.com/en-us/cloud-platform/enterprise-mobility)
