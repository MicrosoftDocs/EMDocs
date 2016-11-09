---
# required metadata

title: Develop your mobile device management adoption strategy
description: Design considerations for adopting mobile device management. 
keywords:
author: YuriDio
ms.author: yurid
manager: swadhwa
ms.date: 10/18/2016
ms.topic: solution
ms.prod:
ms.service: 
ms.technology:
ms.assetid: 10172816-b52d-4a55-8803-6a6805126fab

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: 
ms.suite: ems
#ms.tgt_pltfrm:
ms.custom: microsoft-intune

---

# Develop your mobile device management adoption strategy

>[!NOTE]
>This topic is part of a larger design considerations guide. If you'd like to start at the beginning of the guide, check out the [main topic](mdm-design-considerations-guide.md). To get a downloadable copy of this entire guide, visit the [TechNet Gallery](https://gallery.technet.microsoft.com/Mobile-Device-Management-7d401582).

In this task, you’ll develop the mobile device management adoption strategy that will meet the business requirements that you identified in Tasks 1 and 2. 

## Device ownership

After reviewing your organization’s current policy and strategy to manage devices, you should have a list of scenarios that your organization plans to implement. The section below will help you understand the advantages and disadvantages of each scenario:

## Employee owns the device (BYOD)

**Advantages** 

- Your company does not need to buy mobile devices for the employees
- Usually allows employees to be more productive since they will be using the mobile device of their choice
- Support costs may decrease since the organization will have limited support over the mobile devices

**Disadvantages**

- Increases the amount of security considerations to protect company’s data located on personal devices
- Increases likelihood of data leakage, especially when appropriate security controls aren’t in place
- Limited management capability due to privacy restrictions

## Company-owned device

**Advantages** 

- Full management capability, including device hardening and security controls
- More control over mobile devices
- Capability of defining which mobile devices will be used by employees

**Disadvantages**

- Potential increases in support costs, since the organization will maintain the mobile devices
- Less flexibility for end users, which may affect their productivity
- Cost increases, since the organization will have to buy mobile devices

In some scenarios, organizations will embrace both models: BYOD and company-owned devices. In that case, the device management platform must be able to manage multiple platforms while integrating with current on-premises infrastructure. If your organization fits in this scenario, also make sure your security policies are able to cover both models from the compliance perspective. Different requirements may apply for each model and your mobile device management solution should be able to handle both while enabling IT to stay in control.

## Supported mobile device platforms

The decision you made regarding device ownership will help you identify which mobile device platforms you’ll support. The mobile device management solution that you choose will have to accommodate this decision. In a single mobile device platform scenario, the platform choice will not be as relevant as in the multi-platform scenario. Use the section below to help you choose the mobile device management solution for a multi-platform scenario:

### Intune (standalone)

**Advantages**

- Always-on cloud service that supports the latest MDM features and updates
- Supports provisioning all major mobile device operating systems (Android, iOS, Windows 8, Windows 10, and Windows Phone)
- Allows you to manage any mobile device from any location
- More advanced management options for mobile devices
- [Mobile application management](http://blogs.technet.com/b/microsoftintune/archive/2015/06/18/now-available-intune-mobile-application-management-and-conditional-access-for-outlook.aspx)

**Disadvantages**

- Lack of integration with current device management solution located on-premises will introduce an additional management interface for you to use
- Policies created using the on-premises MDM solution are not replicated to the cloud service

### MDM for Office 365

**Advantages**

- Integrated with Office 365
- If you’re already using Office 365, the MDM capabilities are easily leveraged to manage mobile devices
- If you’re already using Office 365, you won’t need to use another console to manage mobile devices

**Disadvantages**

- Limited set of capabilities (see the note that follows this table) to manage mobile devices
- Lack of integration with current device management solution located on-premises will introduce an additional management interface for you to use

### Hybrid (Intune with ConfigMgr)

**Advantages**

- Native integration between Intune and ConfigMgr
- Allows you to use a centralized console to deploy policies and manage on-premises PCs, servers, and mobile devices

**Disadvantages** 

- Requires additional configuration steps to connect Intune and ConfigMgr
- If the organization does not have a current ConfigMgr infrastructure on-premises, it will require to plan, install and configure this platform prior to the integration

If you only need to manage access to work email, calendar, contacts, and tasks from mobile devices, learn about the [Exchange ActiveSync device management capabilities available in Office 365](https://technet.microsoft.com/library/dn792010.aspx#tasks).

## Application requirements

Based on the requirements that were defined in Task 1, you can choose which mobile device management solution best fits your organization. Use the table below to compare the MDM options, and advantages and disadvantages of each option.


### Intune (standalone)

**Advantages**

- Allows you to manage mobile apps through their lifecycle, including app deployment from installation files and app stores, detailed monitoring of app status, and app removal. Read Deploy software to mobile devices in Microsoft Intune for more information.
- Allows you to specify a list of compliant apps that users are allowed to install and noncompliant apps, which must not be installed by users. Read Manage devices using configuration policies with Microsoft Intune for more information.
- Allows you to set restrictions for apps by using a mobile application management policy. This helps you to increase the security of your company data by restricting operations such as copy and paste, external data backup, and the transfer of data between apps. Read Control apps using mobile application management policies with Microsoft Intune for more information.
- Supports different mobile platforms. Read about supported mobile devices at Mobile device management capabilities in Microsoft Intune for more information.
- Control which apps are available for VPN users. You can select apps that automatically connect to your corporate network over VPN by creating a list of apps when you set up the VPN profile
- Supports mobile application management (MAM) policies that help prevent corporate data from being leaked to consumer apps or services.
- Intune MAM helps IT enable secure access to corporate SaaS (such as Office 365) data for partners, contractors and vendors without managing their devices.


**Disadvantages**

- Lacks integration with on-premises device management solutions, which introduces an additional management interface for you to use when managing mobile devices if you have an on-premises solution. 
- Policies created using an on-premises MDM platform aren’t replicated to the cloud service, requiring two sets of management and compliance policies (if you have ab on-premises MDM solution)


### MDM for Office 365

**Advantages**

- Provides MDM capabilities across OS platforms such as password requirements                                                                                                                                                                                                                                                                                                                                                           

**Disadvantages**

- Limited set of capabilities to control apps
- Lacks integration with on-premises device management solutions, which introduces an additional management interface for you to use when managing mobile devices if you have an on-premises solution.
- No ability to deploy apps and apply mobile application management capabilities


### Hybrid (Intune with ConfigMgr)

**Advantages**

- Inherits app control settings from Intune standalone
- Provides an integrated management experience (between Intune and ConfigMgr)
- Leverages Configuration Manager App management capabilities. Read Application Management in Configuration Manager for more information.
- Leverages Configuration Manager App management capabilities. Read Application Management in Configuration Manager for more information.
- Allows you to use a single console to deploy policies and manage application policies for on-premises PCs, servers, and mobile devices
- Control which apps are available for VPN users. You can select apps that automatically connect to your corporate network over VPN by creating a list of apps when you set up the VPN profile.

**Disadvantages**

- Requires additional steps to set up the integration
- If your organization does not have a current on-premises ConfigMgr infrastructure, you must plan, install, and configure the ConfigMgr platform first
- Without integration with Intune, ConfigMgr has a limited mobile device management solution based on supported mobile device platforms. Read Determine How to Manage Mobile Devices in Configuration Manager for more information.


## Track requirements

Understanding user behavior and being able to identify their location are important factors to include in your mobile device management strategy. How devices will be tracked will vary according to your business requirements and needs.  Different tracking capabilities are available in each mobile operating system so the mobile device platforms you choose to support will impact your options. For example, compliance requirements may influence you to prioritize adopting mobile devices platforms that allow you to track user’s location and use geofencing.

>[!TIP] 
> Geofencing allows you to monitor a mobile device’s geographic location and enable/disable device and network resources based on that location. For example, Windows 8.1 supports allows an app to define a geographical region and have the system alert the app when the device it's running on enters or exits that area. For more information about this feature in Windows 8.1, read [Geofencing, start to finish (XAML)](https://msdn.microsoft.com/library/windows/apps/xaml/dn342943.aspx). 


