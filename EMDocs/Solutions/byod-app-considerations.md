---
# required metadata

title: App considerations
description:
keywords:
author: YuriDio
manager: swadhwa
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service:
ms.technology:
ms.assetid: 4b871c74-fec8-45e2-8b45-6ef0e62f7cc6

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: 
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


# App considerations

App considerations for BYOD can vary according to company goals, constraints, and resources. Companies should evaluate their current apps, the technologies that were used to develop the apps, the requirements for the apps to run on any device, and which apps are essential for the users to be able to access from any location. Though modern apps are not as resource intensive to provision and deploy as Windows-based apps, a cost is still associated with developing and maintaining them.

Patterns exist for apps developed specifically for BYOD scenarios, and you must evaluate if your current apps have those patterns and decide if you will adapt these apps to a BYOD scenario or provide a legacy experience for users to access them from their devices. You can use the following list to identify these patterns:

- Understand the user: which problem are you trying to resolve with this app? Is the problem relevant to the user? The user experience with the app and what users will accomplish by using the app are key considerations.
- Simplicity: users must feel comfortable learning to use apps autonomously and with minimal guidance. Users must be able to navigate through options without getting lost.
- Agility to upgrade: the strategy for mobile apps is to give users the chance to use them right away and provide feedback to enhance the apps. Shipping a perfect app in its first release is not feasible for mobile apps. You must make your release cycle more agile and respond quickly to feedback. Ship now and make continual changes throughout the app life cycle.
- Performance: though traditional Windows-based apps can be more robust because they run on PCs, users tend to assume that Windows-based apps use more resources. Mobile apps must be designed to save resources. You must focus on what you need to make available to the user to deliver the best user experience possible.

For more information about general considerations when creating mobile apps, read [10 considerations when creating mobile apps for business](https://www.microsoft.com/en-gb/developers/articles/week01jan14/10-considerations-when-creating-mobile-apps-for-business).

## Experience

To provide a better user experience based on the platform that the apps will run and the deployment strategy, the company must identify which apps would be published and how. If it is identified that there is a heterogeneous environment and some devices will be supported by the company, one strategy would be to publish the apps via the Company Portal. Ultimately, business decisions will drive the considerations for the user experience. Is the company willing to develop apps that will provide the same experience regardless of the platform? Or will the company provide training to users to use those apps in different platforms without having the same experience?
Consider the cost and the return on investment for each case mentioned in the previous paragraph. It could be feasible to consolidate all apps in a main web portal page that provides the same experience, but the apps would behave differently according to the platform.

Considering that apps for remote users should run on more than one platform, be as light as possible, and require minimum access to users’ devices, you should narrow your options to web-based apps and modern apps. The section that follows will assist you to determine which app experience should be used for your solution.

### App experience options — advantages and disadvantages

Use the list below to understand the advantages and disadvantages of each app experience option:

- Web based
	- Advantages
		- Widely available in many platforms
		- Encryption available using HTTPS protocol
		- Mature technology
		- Easy to use
		- Does not have to be installed on users’ devices
	- Disadvantages
		- Does not have the native look and feel of a mobile app
		- Could require third-party components (such as Flash) to be installed on users’ devices
		- Susceptible to browser vulnerabilities
- Modern
	- Advantages
		- Modern look and feel
			- Richer experience for end users
			- Security controls are established by the developer
			- Leverages the local operating system’s APIs
			- Able to run on different platforms
			- Does not rely on the web browser to run
	- Disadvantages
		- Requires installation on users’ devices.
		- Requires a back-end infrastructure to deploy apps to users’ devices.
		- Might require developers to ramp up their knowledge to develop apps using this new format.


### App requirements — considerations

Evaluate the apps that will be adjusted in order to be used by remote users from their devices, and ensure that these requirements are presented to the users. Below you have a list of app requirements and considerations for each requirement:

- **Internet access/cloud service access** if apps require Internet access in order to work, consider the following points:
	- Apps must be able to transfer encrypted data.
	- Apps should consume minimal bandwidth.
	- Evaluate the possibility of using Windows Push Notification Services for updates.
	- Apps should be able to interact with a proxy server in case the enterprise uses this type of technology to allow Internet access.
	- Apps should be able to use the mobile devices’ Wi-Fi connection.
- **Collect user information** if apps require the collection of users’ information in order to work, consider the following points:
	- Apps should state in detail what information will be collected from users, and users must agree with this collection.
	- If private information is going to be transferred, ensure that the data is encrypted.
	- If private information will be stored on users’ devices, ensure that the data is encrypted.
- **Integration with social networks** if apps require integration with social networks in order to run, consider the following points:
	- Evaluate the authentication method that will be used to enable apps to authenticate with social networks.
	- Verify the integration level with social networks in order to avoid data leakage to a broader audience.
	- Ensure that apps state in detail which information will be shared by the user on the social network in question.
	- Ensure that the data sent to the social network provider is encrypted.

To enhance the user experience, you should also categorize all apps according to your development team’s standards for reducing the need for users to scroll through hundreds of apps.

## Platform

When dealing with user experience, it is normal to evaluate different platforms and determine what your company is willing to support. Many times, enabling users to use their own devices means having a heterogeneous ecosystem, and IT might not be ready to support such an ecosystem.

Each platform has different requirements for signing and publishing apps, which directly impact IT resources because IT needs to evaluate the entire life cycle for apps running on a specific platform. You also need to access the apps’ platform requirements for a BYOD infrastructure solution. The section that follows includes key considerations about app platform requirements.

### App platform requirements — considerations

Below you have a list of app platform requirements and considerations for each requirement:

- Back-end infrastructure
	- Evaluate if extending apps for use by remote users will impact the overall performance of the app server.
	- Based on this evaluation, verify the need to upgrade servers, increase the number of servers, or virtualize servers.
- Supportability
	- Define which platforms (such as Windows, iOS, and Android) will be supported by the company.
		- If the company decides to embrace all platforms, define the supportability boundaries for each platform.
	- Establish the scenarios that are supported and not supported by the company. For example: your company might decide to not support devices that have been jailbroken.
- Operating system platform
	- Define the constraints of each operating system in order to run the company’s apps.
	- Define minimum requirements for apps on each operating system that the company decides to support.
	- Test apps on each operating system to verify if the apps have similar behavior on each. Document the differences.

As part of the strategy to support multiple platforms, you must define how apps will be consumed by those platforms. By using Microsoft Intune, you can enable users to consume apps by using the [Company Portal](http://apps.microsoft.com/windows/app/company-portal/4b1dff1a-e76f-4fdd-a993-9c59048c3768). This capability is not only available for Windows, but also for other [platforms](http://blogs.technet.com/b/windowsintune/archive/2013/11/25/windows-intune-company-portals-for-ios-and-android-now-available.aspx). When considering which apps should be accessed by users via the Company Portal, take into account the two types of apps that can be available via the Company Portal:

- Sideloaded apps: modern LOB apps developed and published to the Company Portal where the content is hosted.
- Deep-link apps: links to apps in the Microsoft Store (or Apple Marketplace for iOS apps) stored in Configuration Manager, which users access via the Company Portal.

Deep-link apps can reduce administrative overhead, by redirecting users to the Windows Store for the latest version, instead of having to manage and publish updates to the Company Portal. The use of the Microsoft Store to deploy apps can also raise some questions, such as:

- Can you use your current infrastructure to deploy these apps via the Windows Store?
- What role does the Windows Store play in the app deployment process?
- Do all apps need to come from the Windows Store?

The answers will vary according to the current state of the company deployment strategy and how this needs to evolve if they choose to use the Windows Store. Keep in mind that the Windows Store is a digital distribution system and is the primary distribution platform for modern apps in Windows 10, Windows 8.1, Windows 8, and Windows RT. However, it is possible to use the Windows Store to list desktop apps certified to run on Windows 8–based devices. For more information about sideloaded apps, see [Try It Out: Sideload Windows Store Apps](https://technet.microsoft.com/windows/jj874388.aspx).

## Deployment

In order to address the considerations about apps that will be deployed to users, it is necessary to understand the requirements regarding corporate access. Deployment scenarios include apps that need to be always connected to company resources, even though users do not need to have access to other corporate resources or do not need full access to all corporate resources while inside the corporate network. Verify the deployment options for each app and evaluate which method is preferred for your company. The section that follows includes the most common deployment options that you can use as part of a decision baseline.

### Deployment options — advantages and disadvantages

Use the list below to understand the advantages and disadvantages of each deployment option:

- On-premises based
	- Advantages
		- All security controls are physically located on-premises, and IT has full control
		- IT can perform hardening of the server that holds the deployment role
		- Provides more granular auditing, logging, and reporting capabilities
	- Disadvantages
		- Higher cost to maintain, when compared to a cloud solution
		- Lack of integration with cloud services
		- Difficult to deploy apps for nonmanaged devices
		- Difficult to control deployment options for devices that are not on-premises
- Cloud based
	- Advantages
		- Apps can be installed from anywhere
		- Multiplatform deployment capability
		- Easier to deploy apps to nonmanaged devices than an on-premises solution
	- Disadvantages
		- Limited reporting capabilities for on-premises devices consuming apps
		- Lack of centralized management and deployment control
- Hybrid (part on-premises and part in the cloud)
	- Advantages
		- Easier to deploy apps to nonmanaged devices than an on-premises solution.
		- IT still has full control over the on-premises portion of the deployment role.
		- Integration between on-premises devices and cloud-managed devices in a single location.
		- Easier to control the deployment options across multiple platforms than an on-premises solution.
	- Disadvantages
		- Usually requires a cloud-service subscription.
		- Integration with the on-premises deployment solution might vary according to the cloud service.

### App deployment requirements — considerations

You also need to access the apps’ deployment requirements for a BYOD infrastructure solution. The list below includes some key app deployment considerations:

- Permissions
	- Ensure that the level of permissions users must have to install apps is not intrusive. For example, you should not require a user to be the administrator of a device in order to install apps.
	- If an app uses temporary files or folders, ensure that it does not require administrative-level permissions to handle those objects.
- Certificate
	- If app deployment requires a certificate in users’ devices, ensure that the devices are able to access the certificate revocation list (CRL) to validate the authenticity of the certificate.
	- If a certificate is installed during the app installation process, ensure that users are aware of this and are prompted for consent.
	- Define which certificate will be used. If the certificate was issued by an internal certification authority (CA), ensure that users’ devices have the CA certificate installed first, and then install the apps’ certificates. If the certificate was issued by a third-party public CA, ensure that the device is capable of validating this certificate through the Internet. If validation fails, ensure that users are aware why it failed and avoid the installation for security reasons.
- Mobile Device Management (MDM) Agent
	- If apps require an MDM agent to be installed on users’ devices prior to the apps’ installation, ensure that the users are aware of this and are prompted for consent.
	- If the MDM agent needs to be installed, ensure that the installation process is easy to follow and will use minimal system resources.

Using System Center 2012 R2 Configuration Manager, IT can identify and license specific users via user discovery capability in Configuration Manager and then add users to a custom collection that will synchronize these user accounts with Microsoft Intune. This will also assist in the deployment of these apps.
App updating should also be included in the considerations for app deployment. After apps are installed, updates to apps should be automatically detected and the users notified of them in the Windows Store app. System Center 2012 R2 offers capabilities for enterprises to have their own enterprise app store and enable users to install LOB apps from this store. For more information about the enterprise app store, see Design case study: Enterprise line of business Windows Store app.

[Autotriggered VPN in Windows 10](http://blogs.technet.com/b/canitpro/archive/2016/01/26/step-by-step-enabling-apps-to-auto-trigger-vpns-in-windows-10.aspx) can be used to enable apps to access corporate resources. This feature enables IT to set a list of predefined apps to automatically connect to corporate networks by opening a VPN connection when the app is started. You can define the apps you want to make available for autotriggering and restrict remote access based on user identity and computer identity from which the user is accessing the resource. For more information about autotriggered VPN, see [What's New in Remote Access in Windows Server 2012 R2](https://technet.microsoft.com/library/dn383589.aspx).

If your company is adopting Windows Phone and wants to enable users to use LOB apps for this platform, you should start by understanding the app enrollment process. Companies must follow some steps to establish a company account, enroll devices, and distribute apps to their enrolled devices. For more information about Windows Phone App deployment, see [Company app distribution for Windows Phone](https://msdn.microsoft.com/library/windowsphone/develop/jj206943(v=vs.105).aspx).

## Storage and network

Storage and network app considerations can have an impact on both app servers and devices. The following questions will arise when you start considering these two core components for apps:

- Will the apps store anything in users’ storage?
	- If so, what are the storage requirements for apps when storing information on users’ devices? Is the data encrypted by the apps or by the operating system?
- Will the apps handle sensitive information while in transit through the wired or wireless network?
	- If so, will the data be encrypted?

The section that follows includes key considerations for app storage and network requirements.

### App storage and network requirements—considerations

Use the list below to understand the advantages and disadvantages of each app storage and network requirements and considerations:

- Disk space
	- If the app deployment process needs to use more space than the app requires (because of temporary files), ensure that this is well documented, users are aware of it, and users are prompted for consent.
	- Ensure that all the temporary files and folders that were stored on users’ storage devices during the deployment process are removed after an app is installed.
- Data privacy
	- If an app stores private information from the company or from the user in users’ device storage, ensure that users are aware and prompted for consent.
		- If the app does store private information, ensure that the files are encrypted on users’ devices.
	- If apps transfer private information from the company or users via the network, ensure that the transfer process is encrypted.
- Backup
	- If apps store temporary files in users’ device storage during normal operation to later commit to the server’s database, ensure that there is a backup mechanism to save the files in case the apps crash, the device runs out of power, and preparations are made for any other unknown circumstance that might lead to data loss.
	- Ensure that backed-up data is also protected against unauthorized users or processes.
	- If the user network loses connectivity with the app server, ensure that apps have a backup process to avoid data loss.
- Back-end infrastructure
	- Evaluate the needs to upgrade, expand, or virtualize back-end storage servers.
	- Ensure that the back-end infrastructure has multiple network paths to access users’ devices.
	- Ensure that the on-premises edge solution is able to handle multiple ISPs to avoid users that are coming from the cloud losing connectivity with on-premises app servers.

When considering apps to be used in your BYOD infrastructure, you can also leverage Windows Server 2012 R2 Virtual Desktop Infrastructure (VDI). Users can remotely run Windows 8 apps as though they were running on their local device, including video clips, movies, streaming videos, and graphically intensive apps. The user experience can be enhanced in Windows Server 2012 R2 with Microsoft RemoteFX. Windows Server 2012 R2 includes codec and media streaming improvements, and it delivers the best possible user experience under varying network conditions, trading off resolution of experience with bandwidth available when required. Furthermore, with the Microsoft Remote Desktop app, users can connect to their corporate data and apps from a variety of platforms, including Windows, Windows RT, iOS, Mac OS X, and Android.

If you consider using VDI to enable BYOD users to access company apps, you should first understand the types of deployments that are available for VDI:

- Virtual machine based: Windows 8 virtual machines running in a Hyper-V infrastructure. In this case, you use Remote Desktop Services to provide users with remote connectivity to virtual machines. You can use the virtual machine–based deployment scenario with pooled or personal virtual machine collections.
- Session based: users connect to Remote Desktop Services (RDS) in Windows Server 2012 R2 and run their apps in Windows Server 2012 R2 sessions. Only RDS is required for this type of deployment.
The storage experience for VDI is improved in Windows Server 2012 R2 with storage tiering and online data deduplication. This functionality enables IT to create storage volumes that automatically optimize locations of data across disks and locate the most frequently accessed data blocks on the highest performing disks. You can also leverage the following storage capabilities in Windows Server 2012 R2 for VDI:
- Multiple storage options: supports direct-attached, network-attached, clustered, or SAN storage of virtual machines; utilizes online disk deduplication to greatly reduce storage requirements.
- Fair Share: dynamically distributes bandwidth, CPU, and disk use across other virtual machines and sessions, ensuring that no single virtual machine or session monopolizes resources or degrades the experience for other users on the system.


For more information about VDI in Windows Server 2012 R2, see [What's New in Remote Desktop Services in Windows Server 2012 R2](https://technet.microsoft.com/library/dn283323.aspx).

The decision of which app deployment and experience will be used for your BYOD infrastructure design should be balanced with the total cost of ownership (TCO). To better understand the TCO for VDI adoption, we recommend that you read [VDI TCO Analysis for Office Worker Environments](http://www.intel.in/content/www/in/en/data-center-efficiency/data-center-efficiency-vdi-tco-analysis-for-office-worker-environments-report.html).

## Security

Consider using a security development life cycle for all apps that will be consumed by users who are using their own devices. Security must be embedded in all phases of the development process, and all potential threats should be taken into consideration. [STRIDE](https://msdn.microsoft.com/magazine/cc163519.aspx) and other security strategies can be incorporated into the development life cycle by using the [Microsoft Security Development Lifecycle (SDL)](https://www.microsoft.com/security/sdl/process/requirements.aspx). How the current infrastructure will be integrated with the overall security strategy for BYOD is an important consideration. Is the current environment able to provide a secure foundation for apps? Does the company need to acquire third-party secure solutions to mitigate any potential vulnerability that this new adoption will create?

Security considerations are important for apps that will be consumed by users using their own devices. It is recommended that you use custom collections based on Active Directory security groups to limit the targeted users for a few apps with specific access requirements, limiting which users can install them. Security also can be leveraged to enhance the user experience by allowing users to use the same user name and password to access corporate resources, which can be accomplished using AD FS. Security is also important when designing the deployment for these apps. You should acquire and deploy certificates and sideloading keys before enabling user enrollment. Work in coordination with other teams to streamline the app certification process.
