---
# required metadata

title: Managed mobile productivity scenarios
description: Microsoft's modern approach to EMM provides unmatched management of Office 365 apps and allows your people to do their best work on any device, while keeping company data secure.
keywords:
author: jeffgilb
manager: swadhwa
ms.date: 09/16/2016
ms.topic: article
ms.prod:
ms.service: ems
ms.technology:
ms.assetid: 452d7991-fa90-4100-afc4-47c4e7b18949

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer:
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# EMS managed mobile productivity scenarios
Microsoft Enterprise Mobility + Security embraces a modern approach to mobility management, and provides unmatched management of Office 365 mobile apps to allow your people to do their best work on any device, while keeping company data secure. Of course, before diving into implementation tasks you should know what you want to do. To get started implementing EMS for mobile productivity scenarios, you'll need to have some well-defined business goals and an understanding of how EMS services and features can help you meet those goals. This is important whether you are brand new to enterprise mobility or migrating from another product.

The best way to align EMS implementation tasks with business goals is to express what you want to accomplish in terms of the scenarios you want to enable for your employees, partners and IT.  Below are short introductions to the most common managed mobile productivity scenarios that rely on Intune, along with links to more information about how to actually implement each of them.

>[!NOTE]
>Do you want to know how Microsoft IT uses Intune to enable Microsoft employees to access corporate resources on their mobile devices while also keeping corporate data protected? [Read this technical case study](https://www.microsoft.com/itshowcase/Article/Content/588) to see in detail how Microsoft IT uses Intune and other services to manage identity, devices, and apps, and data.

## Secure access and protect Office 365 company data on managed devices with Microsoft Intune
Using Intune to protect corporate data stored in Office 365 (email, documents, instant messages, etc.)  could not be much easier for you or more seamless for your users. Intune provides a uniquely integrated conditional access solution that ensures users can't access Office 365 data unless they meet your company’s compliance requirements (things like having performed multi-factor authentication (MFA), enrolled their device with Intune, using managed apps, supported OS version, device pin, etc.). The Office 365 mobile apps available in their respective app stores are shipped with data containment features specifically designed to be configured by Intune. These features enable you to prevent data from being shared with apps (e.g. native email app) and storage locations (e.g. Dropbox) that aren’t managed by IT. All this functionality is built directly into Office 365 so you do not have to deploy or manage any additional infrastructure to get this value.

<!-- Learn more -->


## Secure access and protect on-premises company data with Intune
Most enterprise mobility strategies begin with a plan to enable employee mobile devices to securely access company email and on-premises data stored in application servers, like Microsoft Exchange, hosted on their corporate network. Intune provides a uniquely integrated conditional access solution for Exchange Server that ensures no mobile apps can access email until the device is enrolled with Intune and compliant with company policies. And it does it without you having to deploy another gateway machine to the edge of your corporate network!

Going beyond email, Intune supports enabling access to mobile apps that require secure access to on-premises data, like a line of business app server. This is typically done using Intune-managed certificates for access control combined with a standard VPN gateway or proxy in the perimeter such as Microsoft Azure AD Application Proxy. In these cases, the only way to access the corporate data is to enroll the device into management. Once enrolled, Intune ensures that devices accessing corporate data are compliant with your policies.  Additionally, Intune’s App Wrapping Tool and App SDK can be used to help contain the accessed data within your line of business app, so it can’t pass corporate data to any unmanaged consumer apps or services.

<!-- Learn more -->


## Secure access and protect Office 365 company data on unmanaged devices with Intune
A common Office 365 deployment practice is to require devices to enroll into management if they need to be fully provisioned with corporate apps/certs/Wi-Fi/VPN configurations, which is often the case for corporate-owned devices. However, if the user simply needs to access company email and documents, which is often the case for personally owned devices, they can just use the Office 365 mobile apps and skip enrolling their device altogether! In this situation, Intune can be used to enable your employees, vendors, and partners to effortlessly and securely access company data from their unmanaged devices.

Intune's data restriction policies for unmanaged devices help you keep control of who and what apps can access Office 365 data with powerful data loss prevention capabilities. It doesn't even matter if the device is already being managed by a non-Microsoft MDM solution. In fact, you can keep using that if you'd like and still be able to add the advanced Office 365 mobile app access control and data loss prevention capabilities that Intune provides on top. Either way, by protecting company data without requiring enrollment, you'll save money without the need to maintain servers and also achieve a higher percentage of users who comply with company policies without them having to allow IT to manage their personal devices.

<!-- Learn more -->


## Enable a BYOD program in your organization
BYOD continues to grow in popularity among organizations as a means to reduce hardware costs and increase mobile productivity choices for employees. Just about everyone has a personal smart phone these days so why put another one in their pocket? The main challenge has always been to convince employees to enroll their personal device into management because they are fearful of what their IT department will be able to see and do to their device. When device enrollment is not a viable option, Intune offers an alternative BYOD approach of simply managing the apps that contain corporate data. Intune protects the corporate data even if the app in question accesses both corporate and personal data, as is the case for Office mobile apps.  As an administrator, you can require users to access Office 365 from the Office mobile apps and configure the apps with policies that keep the data protected (encrypted, pin protected, etc.).

<!-- Learn more -->


## Manage company owned devices with Intune
Most information workers are mobile these days and need to productive when using company-owned mobile devices. These employees need seamless access to all corporate apps and data, at any time, wherever they may be while you need to ensure corporate data is secure and administrative costs are kept low.

For IT, trying to keep up by manually enrolling many corporate-owned mobile devices one at a time can be a tough challenge. To help solve this problem, Intune offers bulk provisioning and management solutions that are integrated with the major corporate device management platforms on the market; including the Apple Device Enrollment Program and the Samsung KNOX mobile security platform.  Centralized authoring of device configurations with Intune makes provisioning of corporate devices something that can be highly automated and save you a lot of time.

Intune makes it easy for you to issue an employee a brand new corporate-owned device that walks them through a corporate-branded setup flow when turned on that seamlessly configures the device with security policies to protect company resources (encrypt hard drive, device pin, etc.), configuration policies that help keep them productive (email/Wi-Fi/VPN/certificate profiles), and a baseline set of apps. Afterwards, the employee can use the Intune Company Portal app to access optional corporate apps available to them. And best of all, this is all done without you doing anything after you hand it to them.

<!-- Learn more -->

## Align an EMS Windows 10 deployment and management strategy with business needs
EMS gives you the flexibility, through both modern and traditional management lifecycle processes, to choose how to best deploy and manage Windows 10 in your organization. You can keep using System Center Configuration Manager to deploy and manage Windows 10 devices with advanced policy controls or manage them from the cloud with just Intune for modern device management. In fact, you could even use both with Hybrid MDM and have some devices using agent-based management with Configuration Manager while others are managed by Intune via OMA-DM and MDM.

<!-- Learn more -->


## Enable a limited-use, shared device solution with Intune
Sometimes your employees need to use devices, apps, or browsers that you can’t manage, such as the public computers at trade shows and hotel lobbies. Should you allow your employees to access corporate email from them? Task workers are also increasingly making use of mobile technologies. For example, shared tablets are now commonplace for retail store employees. Protecting company data and simplicity of the user experience is critical in this cases. For this reason, tablets are usually handed to employees in a limited-use mode, such that a single line-of-business app is the only thing the employee can interact with. Intune enables you to bulk provision, secure, and centrally manage these kiosk or shared iOS and Android tablets by configuring them to run in this limited-use mode.

<!-- Learn more -->

### Learn more
