---
# required metadata

title: App requirements
description: Common requirements when deploying apps in a BYOD scenario.
keywords:
author: YuriDio
manager: swadhwa
ms.date: 10/18/2016
ms.topic: solution
ms.prod:
ms.service: 
ms.technology:
ms.assetid: 0c1313b9-361f-4732-a92c-23d0dac07733

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: 
ms.suite: ems
#ms.tgt_pltfrm:
ms.custom: microsoft-intune

---

# App requirements

Every organization uses a variety of technical capabilities to enable their workforce to perform their tasks in an optimized manner, and most of the time, the primary tool is an app. These capabilities could be combined in a multiplatform approach in which different technologies are used to achieve a certain goal or by creating a custom app that will be able to perform a task or automate certain processes. Apps are important to consider when designing the BYOD strategy. Users will use different form factors to consume these apps; therefore, you need to consider the variety of capabilities that these apps should support. Figure below shows how users and devices use apps to consume data and the considerations for each component of the Apps subdomain.

![App requirements](./media/BYOD_Figure5.png)

The next section contains questions about app requirements that you will need to answer in order to formulate the requirements for your solution design.

## Questions to ask

app requirements are categorized in six areas:

- Experience
- Platform
- Deployment
- Storage
- Network
- Security


### Experience

- Do you plan to preserve the same user experience, regardless of the devices on which apps will run?
- Do the apps require Internet access from users’ devices?
- Do the apps require input via keyboard?
- Do the apps collect any user information, such as geographic location?
	- If so, do the apps inform users about privacy issues and data collection while being installed?
- Do the apps require integration with cloud services?
- Which types of apps do you plan to make available for BYOD users (such as web-based apps and modern apps)?
- Were the apps developed to run on a specific operating system, or are they capable of running on any operating system?
- Do you plan to enable users to use apps via Remote Desktop from their own devices?
- Do the apps require full-time access to corporate resources, or can they run in offline mode?
- Do the apps have any integration with social networks?


### Platform

- What type of back-end platform is necessary for these apps to run?
- Do you foresee any increase in activity with the BYOD adoption that will require upgrading the back-end platform for the apps that you plan to allow remote users to use?
- Is the back-end platform that will support the apps located in the same infrastructure as the other servers?
- Is the platform that will support these apps fully on-premises, or are there also servers located in the cloud?


### Deployment

- Do you know which apps will be available to BYOD users?
- How do you plan to deploy these apps to users’ devices?
- What are the deployment options for these apps?
- Does the installation requirement vary according to the target device, or is it the same?
- Do the apps require any mobile device management (MDM) in order to work properly?
- Will you use the Windows Store or any other app store to deploy these apps?
- Do the apps install any digital certificates during the deployment?
	- If so, which certificate authority will be used (private or public)?
- Do users need to be physically connected to the corporate network to perform the installation, or is it possible to install the app via the Internet?

### Storage

- How much space in a target device is necessary in order to install each app?
- Do the apps encrypt the data located in a device’s storage?
- Is it possible to install the apps in external storage on a target device?
- Do you foresee any increase in storage activity on the back-end app server with the BYOD adoption?
	- If so, do you have plans to extend the app server’s storage capacity?
- Is the data consumed by apps located in storage on-premises, in the cloud, or in both locations?
- Is the data consumed by apps encrypted in datacenter storage or in the cloud?

### Network

- What are the network requirements for the apps that you plan to deploy for BYOD users?
- Do the apps encrypt the data before transmitting it through the network from the users’ devices to the app server on the back end?
	- If so, which encryption method do the apps use?
- Do you foresee any increase in network activity with the BYOD adoption?
- Do the apps require full network connectivity in order to work?
- Do the apps work in a low-latency network?
- Can the apps be remotely uninstalled via the network, or do they need to be uninstalled via the devices’ consoles?

### Security

- Were the apps developed using any security development method?
- Do the apps provide authentication capabilities?
	- If so, which authentication method do the apps use?
- Does the authentication method leverage cloud services?
- Do the apps provide authorization capabilities?
	- If so, what levels of authorization do the apps provide?
- Do the apps leverage the existing infrastructure to handle authorization?
- Do the apps provide logging capabilities?
	- If so, what data do they log? Is it possible to control the logging level?
- Do the apps provide input validation?
- Do the company’s policies have specific standards for input validation and handling?
	- If so, will the apps be compliant with such requirements?
- Is there a common input validation or sanitization subsystem that processes data from outside the system?
- Will those apps consume any external library such as JavaScript Library?
	- If so, did you perform a security risk assessment for these external calls?
- Were the apps validated using the [STRIDE](https://msdn.microsoft.com/library/ee823878.aspx) (Spoofing, Tampering, Repudiation, Information Disclosure, Denial of Service, and Elevation of Privilege) method?
- Will the apps handle personally identifiable data?
- Did you perform any privacy analysis for these apps?
- Will the apps use live tiles?
	- If so, could these live tiles inadvertently cause information disclosure?

