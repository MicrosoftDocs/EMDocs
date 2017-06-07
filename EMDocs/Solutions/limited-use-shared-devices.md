---
# required metadata

title: Enable a limited-use shared device solution | Microsoft Docs
description:
keywords:
author: jeffgilb
manager: angrobe
ms.date: 6/7/2017
ms.topic: solution
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: d78e2b94-8ad3-4703-b7f0-db070288a20b

# optional metadata

#ROBOTS: NOINDEX,NOFOLLOW
#audience:
#ms.devlang:
ms.reviewer: vlpetros
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---
# Enable a limited-use shared device solution with Intune
Sometimes employees need to share devices to access apps and company data to complete basic task work where only specific settings and apps are required. This is commonly seen in retail stores, manufacturing floors, and transportation industries. Other times, it’s not employees, but customers who need to interactively access resources using publicly accessible devices at locations like conferences, hotel lobbies, schools, or libraries. In some case, you might only need to display a self-running presentation or provide static information to people walking by.

Running an app full-screen, with no other options, can be done to provide a secure, interactive Kiosk user experience while also protecting your company assets from suspicious user activities. This ability enables IT to provide more security along with a customizable experience that keeps employees productive and meets customer needs.

## How can Enterprise Mobility + Security help you?
EMS enables you to provide capabilities and experiences that create a productive workplace and satisfies customer needs, anywhere. Whether using iOS, Mac OS, Android, or Windows Mobile company-owned devices, Microsoft Intune can help you deliver productivity to your people and information to your customers while keeping company data secure.

### Recommended solution
With Intune, you can leverage Kiosk mode configuration policy settings for iOS or Android mobile devices and assigned access for Windows Mobile phones to lock down a device so that only certain apps or features work. Intune configuration policies are groups of settings that control features on mobile devices and computers. You create policies by using templates that contain recommended or custom settings, and then you deploy them to device or user groups. For example, you can deploy Kiosk mode configuration policies to devices that allow them to run only one managed app that you specify or you can disable the volume buttons on a device. These settings might be used for a demonstration model of a device, or a device that is dedicated to performing only one function, such as a point-of-sale device.

### How to implement this solution
The rest of this solution is divided into the following sections that show you how to configure:
- **Kiosk mode for iOS**. This section shows you how to lock down iOS devices using Kiosk mode Intune configuration policy settings.
- **Kiosk mode for Android**. This section shows you how to lock down Android devices using Kiosk mode Intune configuration policy settings for Samsung KNOX devices.
- **Assigned access policies for Windows**. This section describes how the EnterpriseAssignedAccess Configuration Service Provider (CSP) is used to lock down Windows 10 Mobile devices to provide an Assigned Access experience.

## Kiosk mode for iOS
Intune supplies a range of built-in general settings that you can configure on iOS devices, including Kiosk mode configuration settings that allow you to lock down managed iOS devices.  

Before you can configure an iOS (8.0 and later) device for Kiosk mode, you must first use the [Apple Configurator tool](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) on a Mac device or deploy an enrollment profile to [enroll iOS devices that were bought through The Apple Device Enrollment Program (DEP)](https://docs.microsoft.com/intune/deploy-use/ios-device-enrollment-program-in-microsoft-intune) to put the device into supervised mode. After that’s done, you can deploy Kiosk mode configuration settings to control app and device settings using an Intune configuration policy.

In the Intune administrator console, just navigate to the POLICY node of the Intune administration console, then iOS, create a new **iOS General Configuration (iOS 8.0 and later)** policy, and define Kiosk mode settings. The most important of these settings is defining the managed app that will be allowed to run when the device is placed in Kiosk mode.

![iOS Kiosk mode policy settings](..\Solutions\media\limited-use-devices\kiosk-mode-policy.png)

You can specify a managed app or an app from the Apple app store, but no other apps will be able to run on the device after the kiosk mode policy is applied. Also, remember that when the policy is deployed, it will only take effect on iOS devices in supervised mode.

> [!NOTE]
> If the app that you specify is installed after you deploy the configuration policy, the device will not enter kiosk mode until after it is restarted.

## Kiosk mode for Android
Locking down Android KNOX Standard (4.0 and later) devices is done in similar fashion to putting iOS devices in Kiosk mode. In the Intune administrator console, just navigate to the POLICY node of the Intune administration console, then Android, create a new **General Configuration (Android 4 and later, Samsung KNOX Standard 4.0 and later)** policy, and then define Kiosk mode settings.

There are less settings available to configure with Android KNOX devices, but still the most important is the managed app that will be allowed to run while in Kiosk mode. Store apps are not supported for these devices and the policy that you deploy will run on any Samsung KNOX device the policy is received on—including BYOD personal devices if you aren’t careful. For that reason, you should only deploy Kiosk mode settings for Android devices to the person who manages bulk enrollment for your corporate owned devices that need to be managed as Kiosk devices.

> [!NOTE]
> If the app that you specify is installed after you deploy the configuration policy, the device will not enter kiosk mode until after it is restarted.

## Assigned access policies for Windows
Windows 10 Mobile (version 1511 and later) devices can also be configured as Kiosk devices, but instead of a general configuration policy, a custom Windows configuration policy is used. These kinds of policies allow you to leverage [Windows 10 OMA-URI settings](https://docs.microsoft.com/intune/deploy-use/windows-10-policy-settings-in-microsoft-intune#Windows-10-URI-settings) to manage device configuration settings with Intune.

> [!TIP]
> [Configuration Service Providers (CSPs)](https://technet.microsoft.com/itpro/windows/manage/how-it-pros-can-use-configuration-service-providers) expose OMR-URI device configuration settings in Windows 10.

The [EnterpriseAssignedAccess CSP](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/enterpriseassignedaccess-csp) is used to lock down Windows 10 devices to provide an Assigned Access experience. You can also use that CSP to configure other settings like language, themes, or configure custom layouts on a device.

To create the policy for Windows devices, you need to go to the POLICY node of the Intune administration console, then Windows, create a new **Custom Configuration (Windows 10 Desktop and Mobile and later)** policy. From there, you need to provide the CSP information and import a valid XML file that defines the settings to be applied to Windows devices targeted by the deployment of this policy.  

![OMA-URI settings](..\Solutions\media\limited-use-devices\settings.png)

To create a simple assigned access policy, provide the basic metadata of name, description, set the data type to **String (XML)**, and enter **./Vendor/MSFT/EnterpriseAssignedAccess/AssignedAccess/AssignedAccessXml** for the *case-sensitive* OMA-URI value. In the following example .XML, the device will be locked down so that only the applications specified in an Allow list (Microsoft Edge in this case) are available to use on the device. Apps not identified by their [Windows 10 Mobile app product IDs](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/customize/mdm/enterpriseassignedaccess-csp#productid) in the Allow list remain installed on the device, but are hidden from view and blocked from launching. To enter the required .XML data, just import a new .XML file containing the following sample information or copy and paste it as a single line formatted XML into the **Value** text area:


> [!IMPORTANT]
> When pasting the formatted XML sample provided into the values box, be sure that the entire XML is formatted into a single line.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<HandheldLockdown version="1.0">
   <Default>
      <ActionCenter enabled="false" />
      <Apps>
         <!-- Microsoft Edge -->
         <Application productId="{395589FB-5884-4709-B9DF-F7D558663FFD}" autoRun="true">
            <PinToStart>
               <Size>Medium</Size>
               <Location>
                  <LocationX>0</LocationX>
                  <LocationY>0</LocationY>
               </Location>
            </PinToStart>
         </Application>
      </Apps>
      <Buttons>
         <ButtonLockdownList>
            <!-- Lockdown all buttons -->
            <Button name="Search">
               <ButtonEvent name="Press" />
               <ButtonEvent name="PressAndHold" />
            </Button>
            <Button name="Camera">
               <ButtonEvent name="Press" />
               <ButtonEvent name="PressAndHold" />
            </Button>
         </ButtonLockdownList>
         <ButtonRemapList />
      </Buttons>
      <MenuItems>
         <DisableMenuItems />
      </MenuItems>
      <Settings>
         <System name="Microsoft.WiFi" />
         <System name="Microsoft.About" />
         <System name="Microsoft.Feedback" />
         <System name="Microsoft.CompanyAccount" />
         <System name="Microsoft.VPN" />
      </Settings>
      <StartScreenSize>Small</StartScreenSize>
   </Default>
</HandheldLockdown>

```
After the policy is successfully created, deploy it to a group of Windows devices that you want to be configured as Kiosk devices.

> [!IMPORTANT]
> Ensure that the assigned access policy is deployed to the correct group. There is no way to reverse an assigned access policy other than factory resetting the device.

### Learn more
[Start using Enterprise Mobility + Security](https://docs.microsoft.com/enterprise-mobility/solutions/ems-get-started)

[Microsoft Enterprise Mobility](https://www.microsoft.com/en-us/cloud-platform/enterprise-mobility)
