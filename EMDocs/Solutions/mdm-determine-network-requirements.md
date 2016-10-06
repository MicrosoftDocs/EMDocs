---
# required metadata

title: Determine network requirements
description:
keywords:
author: andredm7
manager: swadhwa
ms.date: 10/3/2016
ms.topic: solution
ms.prod:
ms.service: 
ms.technology:
ms.assetid: 77e7cab9-2fae-4857-be5d-2b6f57e981be

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: 
ms.suite: ems
#ms.tgt_pltfrm:
ms.custom: microsoft-intune

---

# Determine network requirements

>[!NOTE]
>This topic is part of a larger design considerations guide. If you'd like to start at the beginning of the guide, check out the [main topic](mdm-design-considerations-guide.md). To get a downloadable copy of this entire guide, visit the [TechNet Gallery](https://gallery.technet.microsoft.com/Mobile-Device-Management-7d401582).

Enabling secure, managed access to a wide variety of corporate resources by mobile devices is an important feature of a mobile device management solution. While these resources have typically been located in on-premises networks, it’s more common now for resources to be hosted in addition on cloud-based web services and external networks.</para><para>How mobile devices connect to corporate email platforms, virtual private networks (VPNs), and corporate wireless (Wi-Fi) networks all play an important role in keeping corporate data and other resources protected from unauthorized access. Equally important is making it convenient and easy for mobile device users to have secure access these resources to avoid users finding a more convenient but not secure method of storing or accessing resources.</para></content>


## Email management
Corporate email is typically the primary data resource most users need access to on a corporate network, whether from a personally-owned or a company-owned mobile device. Accessing to email is also typically the connection that triggers initial mobile device enrollment. Being able to manage email access for mobile devices across both your existing non-mobile device management solution and the mobile device management solution helps avoid device coverage gaps and increases the protection for data stored on email servers.

Most mobile device management solutions provide email access protection by using one or both of the following features:

- **Email profiles:** By setting up and deploying email profiles, administrators can automatically configure mobile devices with appropriate email server information for users to connect to their email mailboxes. This helps users connect to the correct email server without having to remember the right email server endpoint names or network addresses. In addition, by removing an email profile, administrators can remove email from devices as part of device reset or selective wipe process. Email profile management can be a feature in non-mobile device management solution, or can be integrated with a mobile device management solution.
- **Conditional email access:** Conditional email access, or “managed” email access, typically focuses on security and compliance for accessing email on a mobile device rather than which endpoint the mobile device connects to. With conditional email access, a compliance policy is defined and assigned to individual users or devices or groups of users and/or devices. The policy outlines the prerequisites that have to be in place before a mobile device can connect to an email resource; for example, a PIN might be required on the device. The policy is typically enforced when the device first enrolls, but remains in place and active as long as the mobile device is enrolled in the mobile device management system.

###Email management planning questions

 Answer the following planning questions about email management:

- How will mobile devices connect to your existing on-premises or cloud-hosted email system?
- Will administrators or users (or a combination of both) be responsible for connecting mobile devices to your email system? If users will be connecting mobile devices to the email system, how will they:
 - Choose the proper connection point to access their email mailbox?
 - Choose the proper connection protocol or connection method?
- Will mobile devices need to meet certain security and compliance standards before and while remaining connected to your email system?
- Do you need the ability to create custom email security and compliance connection policies? If so, what are the specific requirements?
- Will you need the ability to import or export email security and compliance connection policies?
- How do you need to manage connections to your email system?
 - By device user?
 - By device type?
 - By device OS?
 - By user group or role?
- When a mobile device needs to be disconnected from your email system, how will email data be deleted from the mobile device?
- Will both administrators and users need the ability to delete email data or the connection to the email system?
- How will confirmation of email data deletion be verified or confirmed?
- If you’re using both an on-premises and cloud-based email system, how do they integrated with the mobile device management solution? 
- Are email profiles or managed access policies administered the same or differently from the IT perspective? Is the user email connection experience the same or different depending on where their mailbox is hosted?

## Network connectivity management

Mobile devices typically connect to corporate networks and resources by using the following access technologies:

- **Wi-Fi:** Wireless access to corporate resources is typically provided as an on-premises network extension service for devices that are in close physical proximity to the on-premises network. This usually involves allowing mobile devices to connect to network resources as users roam from location-to-location in an on-premises office, such as conference and meeting rooms, different offices, or other on-premises areas. It can also include wireless access from remote locations over non-corporate managed wireless network access points, such as the user’s home network or a public wireless access point. To simplify connections to wireless networks, administrators usually manage these connections using wireless profiles that outline the specific settings mobile devices must have in place before they can connect to the wireless network. This may include automatically configuring a custom network name, network Service Set Identifier (SSID), security settings, network proxy, and whether or not the device should automatically connect to the wireless network when the device is in range.
- **Virtual Private Network (VPN):** Secure remote access to corporate resources often includes using a defined VPN connection type from the mobile device. This is often vendor-specific and includes the installation of a VPN application on the mobile device. Additionally, these VPN applications often use either digital certificates or separately managed user account credentials to authenticate the VPN connection. To simplify connections to VPNs, administrators can usually manage these connections using VPN profiles or the VPN management tools included with the VPN solution. Depending on integration support, managing VPN connections with the mobile device management solution may or may not be an option with certain VPN platforms.

>[!NOTE]
>You may have other web-based resources, such as SharePoint, that leverage secure access via Secure Socket Layer (SSL) or Transport Layer Security (TLS). Be sure you understand how mobile devices will access these resources or resources with separate VPN or secure access methods.

### Network connectivity management planning questions

Answer the following planning questions about network connectivity management:
 
- What type of VPN platform do you have deployed in your on-premises network?
- Is the VPN platform supported or able to be integrated with the mobile device management solution?
- If the VPN platform is already integrated or support by an existing non-mobile device management solution – does the mobile device management solution integrate with both systems?
- Will your Wi-Fi infrastructure require updating to accommodate increased device connections and increased bandwidth demands?
- How will mobile devices connect to your existing on-premises wireless or VPN platform?
- If mobile devices are already connecting to your existing wireless or VPN platform, what connection type or protocol are the devices using to connect?
- Will changes to these connections be needed if the devices are enrolled in a mobile device management solution?
- Will administrators or users (or a combination of both) be responsible for connecting mobile devices to your wireless or VPN platform? If users will be connecting mobile devices to the wireless or VPN platform, how will they:
 - Choose the proper connection point to access the corporate network?
 - Choose the proper connection protocol or connection method?
 - Choose the proper digital certificate for the connection method?
- Do you want to automatically configure wireless and VPN connection properties and settings on user’s mobile devices?
 - Do you need to provide different wireless network configuration or security settings to different types of users, devices, device operating systems, or user groups and roles?
 - Will you need the ability to import or export wireless and/or VPN configuration or security connection policies?

## Certificate management

Digital certificates, either self-signed or issued from a third party Certificate Authorities (CAs), may be used to authenticate mobile devices to network connections or specific network resources. To simplify managing digital certificates, administrators usually manage certificates using certificate profiles. This allows a uniform, centralized method for managing certificates, including how they are created, issued, and renewed. This also helps users connect to corporate resource without having to request and install certificates manually or by using a non-approved security process.</para><para>However, using certificates for this type of authentication often requires additional on-premises infrastructure requirements. This may include all or some of the following network components, depending on the level of integration supported by the mobile device management solution:

- **Directory services:** Directory services, such as Microsoft Active Directory, are usually required to securely connect and manage all other network components.
- **Certification Authority (CA) server:** If you’re issuing self-signed certificates for your organization, you’ll need a certification authority to create, issue, manage and renew digital certificates.
- **Network Device Enrollment Service (NDES) server:** This server allows software and mobile devices to obtain certificates based on the Simple Certificate Enrollment Protocol (SCEP).
- **Proxy server:** Depending on your on-premises network configuration, you may require a proxy server that allows mobile devices to receive certificates using an Internet connection and without directly connecting to your internal corporate network.

### Certificate management planning questions

Answer the following planning questions about certificate management:

- Does your organization already require or use digital certificates to authenticate access to network resources?
- Do you have an existing enterprise public key infrastructure (PKI)?
- Do you need to automatically issue digital certificates to mobile devices?
- How are digital certificates created, issued, renewed, or revoked from mobile devices?
- Are digital certificates centrally managed by an on-premises or third party Certification Authority (CA)?
- Do you need to have different certificates assigned for access to different network services? Is this dependent on the type of mobile device accessing the network?

>[!TIP]
>Make sure to take notes of each answer and understand the rationale behind the answer. Later tasks will go over the options available and advantages/disadvantages of each option.  Answering these questions will help you select the option that best suits your business needs.
