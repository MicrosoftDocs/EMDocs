---
title: Network connectivity management options
ms.custom: na
ms.reviewer: na
ms.service: multiple
ms.suite: na
ms.technology: na 
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid:  
author: robmazz
---
# Network connectivity management options

>[!NOTE]
>This topic is part of a larger design considerations guide. If you'd like to start at the beginning of the guide, check out the [main topic](mdm-design-considerations-guide.md). To get a downloadable copy of this entire guide, visit the [TechNet Gallery](https://gallery.technet.microsoft.com/Mobile-Device-Management-7d401582).

Depending on your infrastructure, mobile devices might be able to connect to corporate resources from a variety of Internet connectivity services, which are often secured by VPN-protected endpoints.

By using <externalLink><linkText>Intune</linkText><linkUri>https://technet.microsoft.com/library/dn818903.aspxv</linkUri></externalLink> or a <externalLink><linkText>hybrid deployment</linkText><linkUri>https://technet.microsoft.com/library/dn261221.aspx</linkUri></externalLink> with <token>ConfigMgr</token>, you can deploy Wi-Fi profiles to provision Wi-Fi networks, so a device can auto-connect to the network when it is in range. For example, mobile devices can be configured to connect to a Wi-Fi network segmented to a conference room, but then switch to connect to a Wi-Fi network segment when roaming to a different location. Users don’t have to enter passwords or choose a network; the connection works automatically.

Intune</linkText><linkUri>https://technet.microsoft.com/library/dn818905.aspx</linkUri></externalLink> and <externalLink><linkText>ConfigMgr</linkText><linkUri>https://technet.microsoft.com/library/dn261217.aspx</linkUri></externalLink> can also deploy VPN profiles directly to mobile devices, to let user access internal corporate resources without extra configuration or manual work. Additionally, Intune can configure mobile devices to automatically start a VPN connection that is based on the type resource or method of access. Be aware, however, that there are different configuration requirements for doing this for different types of mobile device operating systems.

Your answers to the questions in Task 3 can help you determine how you want devices to be connect to corporate resources. Be aware that currently, <token>MDM for Office 365</token> doesn’t support managing wireless and VPN network resources for mobile devices.

Table 10 below lists the advantages and disadvantages of managing wireless and VPN networks using <token>Intune</token> standalone and hybrid <token>Intune</token> with <token>ConfigMgr</token>.

Table 10</legacyBold></para><table border="1"><thead><tr><TD><para>Network management options</para></TD><TD><para>Advantages</para></TD><TD><para>Disadvantages</para></TD></tr></thead><tbody><tr><TD><para><token>Intune</token> (standalone)</para></TD><TD><list class="bullet"><listItem><para>Supports wireless and VPN profiles on all major mobile device operating systems (Android, iOS, Windows 10, Windows 8.x, and Windows Phone) </para></listItem><listItem><para>Supports industry leading VPN connection types, including Cisco, Juniper, Dell SonicWall, Checkpoint, and others</para></listItem><listItem><para>Wireless and VPN profiles can be integrated with SCEP certificate profiles for increased security</para></listItem><listItem><para>Supports configuring customized wireless and VPN profiles for different types of users, devices, device operating systems, or user groups and roles</para></listItem><listItem><para>DNS name-based initiation support for Windows 10, Windows 8.1, <token>Windows Phone</token> 8.1 and iOS</para></listItem><listItem><para>Application ID based initiation support for Windows 10 and Windows 8.1</para></listItem></list></TD><TD><list class="bullet"><listItem><para>To support VPN profiles, you’ll need to deploy and maintain an on-premises VPN infrastructure</para></listItem></list></TD></tr><tr><TD><para><token>MDM for Office 365</token></para></TD><TD><list class="bullet"><listItem><para>	Not available</para></listItem></list></TD><TD><list class="bullet"><listItem><para>Not available</para></listItem></list></TD></tr><tr><TD><para>Hybrid (<token>Intune</token> with <token>ConfigMgr</token>)</para></TD><TD><list class="bullet"><listItem><para>All the advantages of <token>Intune</token> standalone, plus the following:</para><list class="bullet"><listItem><para>VPN profiles are supported by your existing on-premises enterprise VPN infrastructure</para></listItem></list></listItem></list></TD><TD><list class="bullet"><listItem><para>To support VPN profiles, you’ll need to deploy and maintain an on-premises VPN infrastructure </para></listItem><listItem><para>Specific security permissions must be granted to manage <externalLink target="_blank"><linkText>Wi-Fi profiles</linkText><linkUri>https://technet.microsoft.com/library/dn408646.aspx</linkUri></externalLink> and <externalLink target="_blank"><linkText>VPN profiles</linkText><linkUri>https://technet.microsoft.com/library/dn408643.aspx</linkUri></externalLink> in <token>ConfigMgr</token></para></listItem></list></TD></tr></tbody></table><para>

Explore the details about mobile device email configuration management options by reviewing the following:</para><list class="bullet"><listItem><para>Intune: Enable <externalLink><linkText>wireless</linkText><linkUri>https://technet.microsoft.com/library/dn818903.aspx</linkUri></externalLink> and <externalLink><linkText>VPN</linkText><linkUri>https://technet.microsoft.com/library/dn818905.aspx</linkUri></externalLink> profiles</para></listItem><listItem><para>ConfigMgr: Enabling <externalLink><linkText>wireless</linkText><linkUri>https://technet.microsoft.com/library/dn261221.aspx</linkUri></externalLink> and <externalLink><linkText>VPN</linkText><linkUri>https://technet.microsoft.com/library/dn261217.aspx</linkUri></externalLink> profiles</para></listItem></list></content>

