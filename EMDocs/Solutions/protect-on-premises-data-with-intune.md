---
# required metadata

title: Protect on-premises company data with Microsoft Intune | Microsoft Docs
description: With Enterprise Mobility + Security (EMS) you'll be able to keep your employees productive with their favorite apps and devices while also keeping your on-premises company data protected.
keywords:
author: jeffgilb
manager: swadhwa
ms.date: 12/12/2016
ms.topic: solution
ms.prod:
ms.service: ems
ms.technology:
ms.assetid: ebf7be63-4ac2-4158-9772-58f15416ccb7

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: vlpetros
ms.suite: ems
#ms.tgt_pltfrm:
ms.custom: microsoft-intune,active-directory

---
# Protect on-premises company data with Intune
Firewalls alone can no longer provide an adequate corporate security boundary. Today, security boundaries must include the end-user and how they access, use, and share company data. Whether working on their smart phones, tablets, or laptops, information workers expect frictionless access to resources from anywhere, on any device, and whenever they need it. Enabling access and protection capabilities for users can be a challenge for IT administrators who also need to make sure company data is protected. With Enterprise Mobility + Security (EMS) you'll be able to keep your employees productive with their favorite apps and devices while also keeping your on-premises company data protected. Continue reading to see how.

## How can Enterprise Mobility + Security (EMS) help you?
Enterprise Mobility + Security (EMS) is the only comprehensive cloud solution that natively protects corporate data on the device itself and beyond with four layers of protection across identities, devices, apps, and data. With EMS, your employees will get secure and seamless access to corporate email and documents while IT is confident that company data is protected.

## Recommended solution
Using Microsoft Intune, you can remotely configure resource access profile policies to auto-provision email accounts, access profiles like WiFi or VPN settings, and provide certificate profiles that ensure devices accept and install only trusted configurations.

In addition to providing access, Intune’s conditional access to on-premises Microsoft Exchange 2010, or later, servers ensures that only managed and compliant devices can access company email. Expanding management beyond the devices themselves, you can also use Intune’s Cisco Identity Services Engine (ISE), and soon other partners, to restrict access to the company network to only devices that are enrolled into management with Intune and compliant with company policies. You can even provide secure access to on-premises applications without VPNs, DMZs, or on-premises reverse proxies by leveraging the Azure Active Directory Application Proxy. Best of all, all of this can be done without installing or maintaining additional on-premises infrastructure or opening your company firewall to route traffic through it.

Here's a short video to give you a quick introduction about how conditional access with EMS provides a seamless experience for employees to access your company data securely from iOS, Android, and Windows devices:

<iframe width="675" height="480" src="https://youtube.com/embed/fvCT7Y3nlAY" frameborder="0" allowfullscreen></iframe>

## Enroll mobile devices and Windows PCs into management
Enrolling devices and PCs into management with Intune ensures all the policies and access profiles you’ve configured for managed devices can be applied. Before you can enroll devices, you will first need to [prepare the Intune service](https://docs.microsoft.com/intune/deploy-use/get-ready-to-enroll-devices-in-microsoft-intune) itself by assigning licenses to users, setting the mobile device management authority, and satisfy the various enrollment requirements for the different device types that you want to manage. While you are at it, you should probably also [customize the company portal](https://docs.microsoft.com/intune/deploy-use/get-ready-to-enroll-devices-in-microsoft-intune#configure-the-intune-company-portal) with support information and company-specific branding to provide a trusted enrollment and support experience for your users.

After preparing the Intune service, the process to enroll devices into management is straightforward, but differs slightly for the various device types:

-   **iOS and Mac devices**. You'll need to get an Apple Push Notification service (APNs) certificate to enroll iPads, iPhones, or Mac OS X devices. After you've [uploaded your APNs certificate to Intune](https://docs.microsoft.com/en-us/intune/deploy-use/set-up-ios-and-mac-management-with-microsoft-intune), users can [enroll iOS devices](https://docs.microsoft.com/intune/enduser/enroll-your-device-in-intune-ios) using the Company Portal app and use the Company Portal website to [enroll Mac OS X devices](https://docs.microsoft.com/intune/enduser/enroll-your-device-in-intune-mac-os-x).
-   **Android devices**. There's nothing you need to do to get the Intune service ready to enroll Android devices. Users can just [enroll their Android devices](https://docs.microsoft.com/intune/deploy-use/set-up-android-management-with-microsoft-intune) into management using the Company Portal app available from Google Play.
-   **Android for Work**. To [set up Android for Work](https://docs.microsoft.com/intune/deploy-use/set-up-android-for-work) for Android 5.0 Lollipop and later devices that support work profiles to be managed by Intune, your organization needs to sign up for Android for Work with Google and then configure Android for Work settings in the ADMIN node of the Intune administration console.
-   **Windows Phones and PCs**. You should [set a DNS alias for the enrollment server](https://docs.microsoft.com/intune/deploy-use/set-up-windows-phone-management-with-microsoft-intune) to make enrolling Windows devices easier. Otherwise, you can [enroll Windows devices](https://docs.microsoft.com/intune/enduser/enroll-your-w10-phone-or-w10-pc-windows) by adding a work or school account.

> [!TIP]
> You can make enrolling Windows devices even easier for your users by [enabling the automatic enrollment](https://docs.microsoft.com/intune/deploy-use/set-up-windows-device-management-with-microsoft-intune#azure-active-directory-enrollment) feature in your Azure AD (Premium). When you do that, devices will automatically be enrolled into management with Intune when a user adds a work or school account to register their personal device or a company owned device joins your organization’s Azure AD.

## Access and protect company email
The first thing most employees want on their mobile device is access to company email and documents. And they expect to set it up without going through complex steps or calling the help desk. Microsoft Intune makes it easy for you to create and deploy email settings for native email apps that are pre-installed on mobile devices used by your organization.

Using Intune Conditional Access policies for Exchange on-premises, you can be sure that only managed, and policy compliant, devices registered in Azure Active Directory can access your company’s on-premises Exchange Server information.

### Configure Exchange email settings for native email apps on managed devices
You can easily [configure native email app settings](https://docs.microsoft.com/intune/deploy-use/configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune) on the following devices by creating email profile configuration policies and deploying them to users:

-   Windows Phone (8 and later).
-   Windows 10 Desktop and Mobile
-   iOS (8.0 and later)
-   Android (Samsung Knox Standard 4.0 and later or Android for Work)
> [!NOTE]
> Intune supports Android for Work email profile configuration for the Gmail and Nine Work email apps found in the Google Play store.

### Protect access to your on-premises Exchange Server
In addition to using Intune to provide email configuration settings to connect to on-premises Exchange servers, you can also use Intune to [control email access to an on-premises Exchange Servers](https://docs.microsoft.com/intune/deploy-use/restrict-access-to-exchange-onpremises-with-microsoft-intune) (2010 or later) through the Intune [on-premises Exchange connector](https://docs.microsoft.com/intune/deploy-use/intune-on-premises-exchange-connector).

If a device is not enrolled or compliant with company policies, the user is presented with information about how to either enroll their device into management or how to remediate compliance issues blocking their access to email.

> [!TIP]
> Have a look at these [example scenarios](https://docs.microsoft.com/intune/deploy-use/restrict-email-access-example-scenarios#all-ios-devices-that-access-exchange-on-premises-must-be-managed-by-intune) for more ideas about how you can use Intune conditional access to protect your company’s Exchange email.

You can [configure a conditional access policy to Exchange on-premises](https://docs.microsoft.com/intune/deploy-use/restrict-access-to-exchange-onpremises-with-microsoft-intune#configure-a-conditional-access-policy) for the following device types in use by your organization:

-   Windows Phone (8.1 and later)
-   iOS (8.0 and later)
-   Android (4.0 or later and Samsung Knox Standard 4.0)
-   Android for Work (currently only supported for Gmail and Nine Work app email profiles)
-   The Mail application on managed Windows PCs

> [!NOTE]
> Intune conditional access policies only work with the native email apps on devices except for the Gmail and Nine Work email apps in the work profile for Android for Work. The Microsoft Outlook app for Android and iOS is currently not supported, but planned to be supported in the future.

## Provide access to other on-premises company resources
In addition to email, EMS also helps you control access and protect on-premises company data being accessed from outside traditional corporate security boundaries. Microsoft Intune Wi-Fi, VPN, and email profiles work together to help your users gain access to the files and resources that they need to do their work wherever they are. Your company's web applications and services hosted on-premises can also be securely accessed and protected using the Azure Active Directory Application Proxy and conditional access.

### Deploy Wi-Fi settings to managed devices
Intune Wi-Fi configuration policies make it easy for you to [deploy wireless network settings to your users](https://docs.microsoft.com/intune/deploy-use/wi-fi-connections-in-microsoft-intune). These settings make it easy for your users to connect to the corporate network without manually configuring Wi-Fi settings on any of the following supported devices:

-   Android (4.0 and later, Samsung KNOX Standard, and Android for Work)<sup>1</sup>
-   iOS (8.0 and later)<sup>1</sup>
-   Mac OS X (10.9 and later)<sup>1</sup>
-   Windows devices (Windows 8.1 and later PCs, Windows Phone 8.1 or Windows 10 Mobile and later)<sup>2</sup>

> <sup>1</sup>You can use a built-in Intune Wi-Fi configuration policy.

> <sup>2</sup>You can [import a previously exported Wi-Fi settings .xml](https://docs.microsoft.com/intune/deploy-use/wi-fi-connections-in-microsoft-intune#export-or-import-a-wi-fi-configuration-profile-for-windows-devices) configuration profile.

### Deploy VPN settings to managed devices
VPN connections are used when your users need to remotely connect to company resources on their mobile devices. With Intune, you can [create and deploy VPN configuration profiles](https://docs.microsoft.com/intune/deploy-use/vpn-connections-in-microsoft-intune#create-a-vpn-profile) that enable users to easily and securely access the corporate network resources without manually configuring VPN server or authentication method information.

You can configure VPN settings for the many [VPN connection types supported by Intune](https://docs.microsoft.com/intune/deploy-use/vpn-connections-in-microsoft-intune#vpn-connection-types) on the following kinds of devices:

-   Android (4.0 and later, Samsung KNOX Standard, and Android for Work)
-   iOS (8.0 and later)
-   Mac OS X (10.9 and later)
-   Windows devices (Windows 8.1 and later PCs, Windows Phone 8.1 and Windows 10 mobile and later)

### Protect network access
Just like allowing access company Exchange information to only managed and compliant devices, you can use [Cisco Identity Services Engine (ISE)](http://www.cisco.com/c/en/us/td/docs/security/ise/2-1/admin_guide/b_ise_admin_guide_21/b_ise_admin_guide_20_chapter_00.html) network policies to secure access to your network environment. Cisco ISE is a policy-based network access control system that can be deployed across enterprise infrastructures supporting 802.1X wired, wireless, and VPNs.

Rather than configure settings in the Intune administration console, device access to Cisco ISE managed networks is configured on the Cisco ISE server. All you need to do is [give the Cisco ISE server permissions to access your Intune tenant](https://docs.microsoft.com/intune/deploy-use/restrict-access-to-networks) and then use Cisco ISE policies to allow access to your network environment to only managed and compliant devices.

> [!IMPORTANT]
> [Cisco ISE licenses](http://www.cisco.com/c/en/us/td/docs/security/ise/2-1/admin_guide/b_ise_admin_guide_21/b_ise_admin_guide_20_chapter_0110.html), not included with EMS, are required to leverage this protection.

You can also enable single sign-on (SSO) and conditional access to secure remote access for web applications hosted on-premises using the Azure AD Application Proxy. The Azure AD Application Proxy makes it easy for your uses to access web applications hosted on-premises like SharePoint sites, Outlook Web Access, or other LOB web applications without requiring a VPN. Connections to Web APIs to support different devices and apps hosted behind a Remote Desktop Gateway can also be secured.

[Setting up the Azure Active Directory Application Proxy](https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-enable) is easy to do. Just enable the feature in Azure AD (Basic or Premium), install a small Windows Server service called a connector inside your network, and then publish applications to it. There’s no need to open any inbound firewall ports or put anything in a DMZ. Once you have it set up, access to on-premises web applications is provided by single sign on to Azure AD. [Conditional Access rules](https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-conditional-access), like requiring multi-factor authentication or blocking access when employees aren’t at work, provide additional safeguards

## Use certificates to secure company resource access
When you give users access to corporate resources through VPN, Wi-Fi, or email profiles, you can [secure that access by using a certificate](https://docs.microsoft.com/intune/deploy-use/configure-intune-certificate-profiles) that is installed on each user device rather than depend on a simple user name and password for authentication.

You can create and deploy either a **PKCS \#12 (.PFX)** or **Simple Certificate Enrollment Protocol (SCEP)** certificate profile to be used by devices requesting authentication certificates on these device platforms:

-   iOS (8.0 and later)
-   Mac OS X (10.9 and later)
-   Android (4.0 and later, and Android for Work)
-   Windows 10 (desktop and mobile) and later

You can only use a **SCEP Certificate Profile** for devices running these platforms:

-   Window 8.1 (and later)
-   Windows Phone (8.1 and later)

Although you need an Enterprise Certification Authority (CA) to do any certificate-based authentication for you company, there are other prerequisites that must be met before using either SCEP or .PFX certificates to secure access to company resources.

-   Before you can use Intune to create and deploy SCEP certificate profiles, you must first [configure the certificate infrastructure for SCEP](https://docs.microsoft.com/intune/deploy-use/configure-certificate-infrastructure-for-scep). This step requires configuring several on-premises servers including an Enterprise Certification Authority (CA), a Network Device Enrollment Server (NDES), and the Microsoft Intune Certificate Connector servers.
-   To [use .PFX certificate profiles](https://docs.microsoft.com/intune/deploy-use/configure-certificate-infrastructure-for-pfx) (trusted mobile device certificates) in addition to the Enterprise Certification Authority, you need the Intune Certificate Connector (can be installed on the CA). NDES is not required.

> [!NOTE]
> A web application proxy (WAP) server is optional for use with both SCEP and .PFX certificates to enable devices to receive and renew certificates using an internet connection.

When you [deploy certificate profiles](https://docs.microsoft.com/intune/deploy-use/configure-intune-certificate-profiles) to users, the trusted CA certificate is installed on their device. The device then uses the SCEP or .PFX certificate profile to create a certificate request for itself. When the certificate request is competed, you can use certificates to authenticate Wi-Fi, VPN, and email profile configuration policies by selecting the certificates (instead of username and password) policy authentication method option.

### Learn more

[Start using Enterprise Mobility + Security](https://docs.microsoft.com/enterprise-mobility/solutions/ems-get-started)

[Microsoft Enterprise Mobility](https://www.microsoft.com/cloud-platform/enterprise-mobility)
