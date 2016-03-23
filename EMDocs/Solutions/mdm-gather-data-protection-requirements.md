---
title: Gather your data protection requirements
ms.custom: na
ms.reviewer: na
ms.service: multiple
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5dffb570-dd1a-4beb-aa1e-7c0b51393704
author: YuriDio
---
# Gather your data protection requirements

>[!NOTE]
>This topic is part of a larger design considerations guide. If you'd like to start at the beginning of the guide, check out the [main topic](mdm-design-considerations-guide.md). To get a downloadable copy of this entire guide, visit the [TechNet Gallery](https://gallery.technet.microsoft.com/Mobile-Device-Management-7d401582).

To help define your organization’s data protection requirements for mobile devices, it helps to first think about data protection requirements that your organization already has in place. For example, perhaps your company has to comply with specific regulations, or you might already have a policy regarding data protection. 

Make note of these high-level requirements first, and then you’ll have a basis for asking more granular questions that will help lead you to better design decisions for your MDM solution.  When defining these requirements, consider the following:

- Data encryption at rest: As shown in Figure 8, company data will be stored on the user’s mobile device. Consider if the following is important to your company: 
	- Does the MDM solution support encrypting the entire mobile device disk and SD cards?
		- If yes, for which operating systems?
	- Does the MDM solution support app data encryption?
		- If yes, for which operating systems?
		- If yes, for which apps?
- Data encryption in transit: Regardless who owns the data, at some point during data communication, the data is in transit between the mobile device and a company server (or web service). You must understand what capabilities the MDM solution has in order to protect data in transit. Consider if the following is important to your company: 
	- Does the MDM solution support data encryption in transit?
		- If yes, for which operating systems?
		- If yes, which capabilities are available?
	- What options does the MDM solution have to protect data while in transit?
- Data segregation: It’s also important to understand if your company’s data should be treated differently from the user’s data. Segregation, separation, or isolation are some terms that can be used to describe this capability. When designing your MDM solution, consider:
	- Does the MDM solution support data separation?
		- If yes, is it possible to erase your company’s data, while preserving the mobile device user’s data?
	- Does the MDM data separation capability ensure that only trusted apps can access data located on the mobile device?
	- Does the MDM solutions support data separation according to the user’s identity?
	- Does the MDM solution support containerization?
		- If so, is it possible to encrypt data located in a particular container?
- Hardening mobile devices: Since there might be different mobile device platforms used in your organization, you should understand what hardening capabilities are available in each mobile device platform. Each mobile device platform may control and harden devices using different methods and at different levels of granularity. If one set of mobile devices has a more granular set of configuration than others, you’ll need a common set of options to harden the devices while using custom policies to enhance the security for each mobile device platform that your organization supports. 

The list below includes common options that should be supported by the MDM solution to harden mobile devices:

- Requiring a password to unlock mobile devices
- Requiring a password type – minimum number of characters and character types
- Minimum password length
- Number of repeated sign-in failures to allow before the mobile device is wiped
- Minutes of inactivity before the device screen turns off
- Remembering password history – preventing the reuse of previous passwords
- Password expiration (days)
- Requiring encryption on the mobile device
- Requiring encryption on storage cards
- Allowing idle return without a password

>[!TIP] In Windows Phone 8.1, the policy Allow idle return without password can be configured using [Windows Phone 8.1 Enterprise Device Management Protocol](http://download.microsoft.com/download/C/A/0/CA091018-1A43-4063-B70B-20B9901F4D10/Windows Phone 8.1 MDM Protocol.pdf).