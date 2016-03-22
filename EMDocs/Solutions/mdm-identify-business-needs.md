---
title: Identify Business Needs
ms.custom: na
ms.reviewer: na
ms.service: multiple
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 32ef7e4e-41b6-4e40-b9d9-6d2bfb464a99
author: YuriDio
---
# Identify your business needs

>[!NOTE]
>This topic is part of a larger design considerations guide. If you'd like to start at the beginning of the guide, check out the [main topic](mdm-design-considerations-guide.md). To get a downloadable copy of this entire guide, visit the [TechNet Gallery](https://gallery.technet.microsoft.com/Mobile-Device-Management-7d401582).

Each company will have different requirements. Even if these companies are part of the same industry, the real business requirements might vary. You can still leverage best practices from the industry, but ultimately it’s the company’s business needs that will identify the requirements for the mobile device management solution. 
To help identify your business needs, answer the following questions:

- **Device ownership**: You must understand the device ownership policy for your company.
	- Who owns the mobile device? 
		- The employee?
		- The company?  
		- Both?
- **Platforms**: Understanding which mobile device operating systems will be used by the company is very important for adoption and supportability decisions.
	- Which mobile device operating systems will be supported?
		- Android?
		- iOS?
		- Windows?
		- Windows Phone?
		- All of them?
		- A mix of the above options?
	- Which mobile OS version will be supported?
		- Only the latest?
		- Current -1 (current version plus the previous version)?
- **Applications**: Since the main reason to embrace mobility is to increase productivity, the applications (apps) used by employees must be able to run in all the mobile device operating systems used in your organization. This is an important point to consider, because while some companies might have their most important apps fully portable to run in a mobile environment, others might need to understand what options are available that can help them to deploy their apps to mobile devices. To assist you identifying individual app requirements, ask yourself the following questions.
	- Do the apps require Internet access from users’ devices? 
	- Do the apps collect any user personal information?
		- If so, do the apps inform users about privacy issues and data collection while being installed?
	- Do the apps require integration with cloud services?
		- Were the apps developed to run on a specific operating system, or are they capable of running on any operating system?
	- Do you plan to enable users to use apps via remote desktop from their own devices?
	- Do the apps require full-time access to corporate resources, or can they run in offline mode?
	- Do the apps have any integration with social networks?
	- Will all apps be available to BYOD users?
	- How do you plan to deploy these apps to users’ devices?
	- What are the deployment options for these apps?
	- Does the installation requirement vary according to the target device, or is it the same?
	- How much space in a target device is necessary in order to install each app? 
	- Do the apps encrypt the data before transmitting it through the network from the users’ devices to the app server on the back end?
	- Can the apps be remotely uninstalled via the network, or do they need to be uninstalled via the devices’ consoles?
	- Does your company needs to provide access to SaaS apps data for their partners?
	- Do the apps work in a low-latency network? 
	- Do the apps provide authentication capabilities?
		- If so, which authentication method do the apps use?
•	**Users**: One of the main points in embracing mobility is to put the user at the center of the mobility solution and enabling the user to be more productive, while keeping company data secure and available. This is important to understand what the user’s requirements are.
	- Will the user be able to bring their own device and access company’s resources?
		- If yes, what are the requirements to access company’s resources?
	- Does your company have different user’s needs?
		- If yes, how each user’s profile will impact the mobility strategy?
	- Will users be able to access all apps that they have access to in the on-premises environment via their mobile device?
		- If not, which apps will be available for the users?
			- Are those apps available for all supported mobile device platforms?
			- Will be necessary to modify or update any apps in order to run them on all supported mobile device platforms?
	- Do your users only need basic access to email (including calendar, contacts, and tasks) features?

During this task, you should also evaluate if the company has existing management and compliance policies in place for mobile devices and how these policies might affect the mobile device management solution selection.

>[!NOTE] Make sure to take notes of each answer and understand the rationale behind the answer. Next section will go over the available options and advantages/disadvantages of each option.  By having answered these questions, you’ll be able to select which solution best suits your business needs.


