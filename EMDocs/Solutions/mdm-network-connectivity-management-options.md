---
# required metadata

title: Network connectivity management options
description:
keywords:
author: robmazz
manager: swadhwa
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service:
ms.technology:
ms.assetid: bc7cdb8f-3485-45ae-9493-f840ad9ed3ea

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: 
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Network connectivity management options

>[!NOTE]
>This topic is part of a larger design considerations guide. If you'd like to start at the beginning of the guide, check out the [main topic](mdm-design-considerations-guide.md). To get a downloadable copy of this entire guide, visit the [TechNet Gallery](https://gallery.technet.microsoft.com/Mobile-Device-Management-7d401582).

Depending on your infrastructure, mobile devices might be able to connect to corporate resources from a variety of Internet connectivity services, which are often secured by VPN-protected endpoints.

By using [Intune](/Intune/deployuse/wi-fi-connections-in-microsoft-intune) or a [hybrid deployment](https://technet.microsoft.com/library/dn261221.aspx) with ConfigMgr, you can deploy Wi-Fi profiles to provision Wi-Fi networks, so a device can auto-connect to the network when it is in range. For example, mobile devices can be configured to connect to a Wi-Fi network segmented to a conference room, but then switch to connect to a Wi-Fi network segment when roaming to a different location. Users don’t have to enter passwords or choose a network; the connection works automatically.

[Intune](/Intune/deployuse/vpn-connections-in-microsoft-intune) and [ConfigMgr](https://technet.microsoft.com/library/dn261217.aspx) can also deploy VPN profiles directly to mobile devices, to let user access internal corporate resources without extra configuration or manual work. Additionally, Intune can configure mobile devices to automatically start a VPN connection that is based on the type resource or method of access. Be aware, however, that there are different configuration requirements for doing this for different types of mobile device operating systems.

Your answers to the questions in Task 3 can help you determine how you want devices to be connect to corporate resources. Be aware that currently, <token>MDM for Office 365</token> doesn’t support managing wireless and VPN network resources for mobile devices.

The lists below outline the advantages and disadvantages of managing wireless and VPN networks using Intune standalone and hybrid Intune with ConfigMgr.

## Intune (standalone)

**Advantages**

- Supports wireless and VPN profiles on all major mobile device operating systems (Android, iOS, Windows 10, Windows 8.x, and Windows Phone) 
- Supports industry leading VPN connection types, including Cisco, Juniper, Dell SonicWall, Checkpoint, and others
- Wireless and VPN profiles can be integrated with SCEP certificate profiles for increased security
- Supports configuring customized wireless and VPN profiles for different types of users, devices, device operating systems, or user groups and roles
- DNS name-based initiation support for Windows 10, Windows 8.1, Windows Phone 8.1 and iOS
- Application ID based initiation support for Windows 10 and Windows 8.1
- Select apps that automatically connect to your corporate network over VPN in VPN profiles

**Disadvantages**

- To support VPN profiles, you’ll need to deploy and maintain an on-premises VPN infrastructure

## MDM for Office 365

Support for Wi-Fi and VPN policies aren't supported in MDM for Office 365.

## Hybrid (Intune with ConfigMgr)

**Advantages**

- All the advantages of Intune standalone, plus the following:
	- VPN profiles are supported by your existing on-premises enterprise VPN infrastructure

**Disadvantages**

- To support VPN profiles, you’ll need to deploy and maintain an on-premises VPN infrastructure 
- Specific security permissions must be granted to manage [Wi-Fi profiles](https://technet.microsoft.com/library/dn408646.aspx) and [VPN profiles](https://technet.microsoft.com/library/dn408643.aspx) in ConfigMgr

Explore the details about mobile device email configuration management options by reviewing the following:

- Intune: Enable [wireless](/Intune/deployuse/wi-fi-connections-in-microsoft-intune) and [VPN](/Intune/deployuse/vpn-connections-in-microsoft-intune) profiles
- ConfigMgr: Enable [wireless](https://technet.microsoft.com/library/dn261221.aspx) and [VPN](https://technet.microsoft.com/library/dn261217.aspx) profiles