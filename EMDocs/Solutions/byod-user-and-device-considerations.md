---
# required metadata

title: User and device considerations
description:
keywords:
author: YuriDio
manager: swadhwa
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service:
ms.technology:
ms.assetid: e7838e5f-8946-4e69-b287-9e53f97f136c

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: 
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# User and device considerations

The first user and device issue you need to address is how the technologies in place will affect the user experience when securely accessing company resources. Addressing the user experience across different devices can be challenging, not only from a security point of view, but also from the perspective of app development. The communication channel between the device and company resources must be considered for the proper level of network security required to avoid data leakage while data is in transit.
The sections that follow are based on components for the Users and Devices subdomain shown in Figure 1 in BYOD Problem Definition, which is the conceptual diagram for the BYOD problem domain.

## Profiles

Understanding users’ needs and requirements to perform their jobs from the devices of their choice is essential when designing your BYOD infrastructure solution. Not all users will have the same requirements; some users will always access data on-premises, and policy enforcement for them can be different. Remote workers will be accessing company data from a variety of locations and circumstances. You must consider the options available to address these needs. Determine each user’s profile according to their needs:

- Do they need to access apps only?
- Do they need to access folders located on a file server?

Though the following table suggests a set of requirements for each user’s profile, you can customize this table by adding or removing requirements based on your company’s needs. The rationale of each profile category compared to what it should contain is based on the resources it consumes. For example, the light profile means low utilization of resources on the device and low network requirements. Ensure that you understand each user’s profile footprint; this will allow you to make more appropriate choices throughout the rest of the design process.

The user profile proposed in this guide are:

- **Light**
	- Access to web-based apps on-premises or in the cloud
	- Access to corporate mobile apps
- **Moderate**
	- Access to web-based apps on-premises or in the cloud
	- Access to corporate mobile apps
	- Access to virtualized business apps
	- Access to files located in file servers on-premises
	- Access to files located in the cloud
- **Heavy**
	- Access to web-based apps on-premises or in the cloud
	- Access to corporate mobile apps
	- Access to files located in file servers on-premises
	- Access to files located in the cloud
	- Access to computers using Remote Desktop
	- Access to other computers located on-premises

You will need to determine which user profile is more suitable for your BYOD infrastructure solution. You might consider establishing multiple users’ profiles according to their job requirements. Ideally, the technology that you use to implement your BYOD infrastructure solution should be able accommodate all user profiles, because the requirements might vary according to each individual. 

## Devices

IT must determine if it requires knowledge of devices. For example, one BYOD scenario is hourly employees checking their time sheets or reviewing corporate notices or social sites when out of the office. In many organizations, these requirements were traditionally LAN-only services, but now they may be opened to personal devices. Does someone checking their schedule require device management? Understanding the devices’ footprints will help IT to:

- Track which user is registering devices: a user registering a number of devices every week might indicate suspicious activity.
- Understand devices’ footprints: knowing which types of devices are in use on the network can help IT support those devices.

Consider having the link between the device and the user stored in a central location that can be later used by IT when performing auditing or reporting. IT needs to move from an unknown device state to a known device state to enable BYOD. This will allow IT to have more control of devices that are corporate assets. Usually, companies approach this requirement in three different ways:

- Approach 1: Installing a management agent in each user’s device.
- Approach 2: Registering each device in a central repository without installing a management agent.
- Approach 3 (1+2): Registering and installing a management agent in each user’s device.


### Unknown-to-known device options — advantages and disadvantages

Use the list below to understand the advantages and disadvantages of unknown-to-known device options:

- Installing a management agent in each user’s device
	- Advantages
		- More control of users’ devices
		- Remote wipe capability
		- App deployment capability
		- More security controls available for IT to control the device
	- Disadvantages
		- Requires users to install a management agent
		- Management agent must be installable on different devices’ platforms
		- More administrative overhead
- Registering each device in a central repository without installing a management agent
	- Advantages
		- No management agent required
		- Less administrative overhead
		- Second-factor authentication of devices
		- Validation of the link between users and devices
	- Disadvantages
		- Less control of users’ devices
		- Fewer security controls available
		- Lack of capability to perform remote wipe and app deployment
- Registering and installing a management agent in each user’s device
	- Advantages
		- More control of users’ devices
		- Remote wipe capability
		- App deployment capability
		- More security controls
		- Second-factor authentication of devices
		- Validation of the link between users and devices
	- Disadvantages
		- Requires users to install a management agent
		- Management agent must be installable on different devices’ platforms
		- More administrative overhead

In Windows Server 2012 R2, the new concept of [Workplace Join](https://technet.microsoft.com/library/dn280945.aspx) allows IT to move the device from an unknown state to a known state. The device can also be used as second-factor authentication and single sign-on to workplace resources and apps. Workplace Join is natively available in Windows 10, but it is also supported in other platforms such as iOS and Android. Workplace Join leverages the Device Registration Service (DRS). For more information about DRS, read [Configure a federation server with Device Registration Service](https://technet.microsoft.com/library/dn486831.aspx). Workplace Join is new technology and works with specific use cases. See [Secure access to company resources from any location on any device](https://technet.microsoft.com/library/dn550982.aspx) for more information about a solution that leverages Workplace Join with single sign-on.

If you consider using DRS, understand that this feature does not provide management capabilities. If your company needs more security controls in order to have more options available to control users’ devices, consider using DRS in conjunction with [mobile device enrollment](https://technet.microsoft.com/library/jj733620.aspx) as the management agent solution. However, if you choose this option, you must have a Microsoft Intune subscription. For more information about Microsoft Intune, see [Start using Microsoft Intune](https://technet.microsoft.com/library/dn646953.aspx).

## Network

Corporate network access from the user and device perspective must be addressed. How will users access company data while using their own devices? Most BYOD infrastructure solutions focus only minimally on remote access from users’ devices; however, from a people-centric approach, you must consider where users are physically located. You should focus on not only remote access, but also how users will access the data while on-premises. In addition, you will need to consider regulatory issues specific to your organization's geopolitical alignment. For example, how can users that are physically located in a different country have personalized network access?

If your company has resources in the public cloud that will be accessible via the Internet from users’ devices, you must consider how traffic will be handled. Consider using encryption while the data is in flight from users’ devices to the cloud provider. When users are accessing internal resources, you should also use data encryption.

### Network connectivity options — advantages and disadvantages

Use the list below to understand the advantages and disadvantages of the connectivity options:

- Traditional VPN
	- Advantages
		- Mature technology
		- Easy to configure
		- Widely available on many platforms
	- Disadvantages
		- Protocol overhead from VPN and encryption protocols
		- Must be launched before launching apps
		- Requires user interaction to establish the connection
- Microsoft Direct Access
	- Advantages
		- Seamless experience for users (always on)
		- Supports selected server access and IPsec authentication with an Internet network server
		- Supports end-to-end authentication and encryption
	- Disadvantages
		- Requires an on-premises infrastructure to support this capability
		- Troubleshooting can be challenging
		- Higher administrative overhead
		- Not available on all platforms
- Automatic Trigger VPN
	- Advantages
		- Easy to configure
		- Connection to on-premises server is launched when an app needs access to corporate resources
	- Disadvantages
		- Protocol overhead from VPN and encryption protocols
		- Not available on all platforms
- Remote Desktop with VDI
	- Advantages
		- Seamless user experience
		- More control over the desktop (hardening)
		- Widely available on many platforms
	- Disadvantages
		- Requires an on-premises infrastructure to support this capability
		- Capacity planning for network, storage and compute must be carefully performed to avoid a performance bottleneck
		- Each device requires a remote access client app
- Web access
	- Advantages
		- Widely available on many platforms
		- Encryption available using HTTPS
		- Mature technology
		- Easy to configure
	- Disadvantage
		- Requires certificates
		- If the certificate infrastructure is internal, it requires a PKI infrastructure
		- Requires an edge infrastructure to securely publish apps

After you define the design for remote network access, consider how user-owned devices will connect to your network while they are physically connected to it. Users who bring their devices to work will likely be using Wi-Fi capabilities to connect to corporate resources. You should consider using network segmentation (physical or logical) for users’ devices in order to isolate them.

You can also segment the devices that will connect to the Wi-Fi network according to the platform they run. Also consider how to secure their communication and authorization while they are on-premises accessing corporate resources.

You can choose a physical segmentation on your wireless access point and network components (switches and routers) to isolate users who are connecting by using their own devices. You can also implement this type of segmentation by using [Wi-Fi Profiles in Configuration Manager](https://technet.microsoft.com/library/dn261221.aspx). A wide range of security settings is available, such as certificates for server validation and client authentication that have been provisioned by using [Configuration Manager certificate profiles](https://technet.microsoft.com/library/dn270540.aspx).


### Wi-Fi network segmentation options - advantages and disadvantages

Use the list below to understand the advantages and disadvantages of the Wi-Fi segmentation options:

- Physical segmentation
	- Advantages
		- Lower-level security segmentation
		- Relatively easy to configure
		- Abstracts itself from the platform (operating system)
	- Disadvantages
		- Manageability may vary according to the vendor
		- Integration among different hardware vendors could be challenging
		- Higher cost to implement and maintain
- Logical segmentation (Wi-Fi profiles)
	- Advantages
		- Seamless experience for users.
		- Easier to manage (when compared to physical segmentation)
		- Lower cost to implement (when compared to physical segmentation)
		- Abstracts itself from the hardware used to connect devices
		- Supports multiple platforms (operating systems)
	- Disadvantages
		- Does not provide the lower-level security segmentation that the hardware solution does
- Dynamic Segmentation
	- Advantages
		- Wireless Access Points use a common infrastructure and SSID
		- End-user and device attributes dynamically provision network access
	- Disadvantages
		- Requires IPsec for Implementation using [Microsoft Network Access Protection (NAP)](https://technet.microsoft.com/library/cc731276(v=ws.10).aspx), which can be a problem in a BYOD scenario that requires support for “any device.”

> [!NOTE] For more information about Wi-Fi Profiles in Configuration Manager, see [Introduction to Wi-Fi Profiles in Configuration Manager](https://technet.microsoft.com/library/dn261224.aspx).

Network location plays an important role for user and device considerations. You can leverage multi-factor access control in AD FS to enable per-application authorization policies, whereby you can permit or deny access based on user, device, and network location. See [Manage Risk with Multi-Factor Access Control](https://technet.microsoft.com/library/dn280936.aspx) for more information about how to set up an environment to validate this capability.

