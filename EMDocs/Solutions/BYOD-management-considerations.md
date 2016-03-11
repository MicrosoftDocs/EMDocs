---
title: Management considerations
ms.custom: na
ms.reviewer: na
ms.service: multiple
ms.suite: na
ms.technology: na 
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0000
author: YuriDio
---
# Management considerations

A management domain is mandatory in an infrastructure that supports a BYOD model. In order to fully support BYOD demands, the management domain must be able to enable IT to monitor resources, provide reporting capabilities, manage compute and storage resources, enable device configuration and automation, and manage apps deployment and provisioning.

## Monitoring

One of the roles of the management domain is to monitor compliance settings, not only for corporate assets but also for mobile devices owned by users. Considerations regarding compliance should be evaluated according to the company line of business. Some companies might allow corporate data to reside on users’ devices only if it is encrypted. Security settings must be controlled by IT in order to enforce those policies.

The level of management in users’ devices will vary according to company policy and the BYOD infrastructure that the company will adopt. If the company establishes that it is necessary to provide full-wipe capability in order to have access to company resources, IT must enforce this setting on all monitored devices. IT also needs the ability to reset devices to the manufacturer’s defaults, wiping all personal settings and data if necessary. Use the section that follows to determine the monitoring options that will be required for your BYOD infrastructure.

### Monitoring options — advantages and disadvantages

Use the list below to understand the advantages and disadvantages of each monitoring option:

- Management agent installed on users’ devices
	- Advantages
		- More control over users’ devices
		- Remote wipe capability
		- Selective wipe capability
		- Faster app deployment and life cycle management
	- Disadvantages
		- Need to install a management agent in users’ devices
		- More intrusive from users’ perspective
		- Requires a back-end management infrastructure to support the agent
- Management agent not installed
	- Advantages
		- No management agent is installed on users’ devices
		- Policy enforcement available only from the app perspective (for example, ActiveSync)
	- Disadvantage
		- Limited options available for IT to manage devices

As you can see in the preceding table, when designing the BYOD infrastructure solution, you will need an agent installed on users’ devices if you want to enforce company policy.

If the company chooses to support different types of devices, you need to understand the devices’ capabilities, such as storage encryption, VPN connectivity options, and supported programming languages. Evaluate what can be implemented to be in compliance with company policies. Monitoring devices in order to meet compliance can be done by enforcing policies. Consider enabling device encryption while data is at rest in users’ devices; this can assist you in your data leakage strategy. Enforcing policies such as password unlock, password history, and strong passwords can lend similar security across on-premises and mobile devices.

Compliance settings in Configuration Manager allow IT to manage the configuration and compliance of servers, laptops, desktop computers, and mobile devices in the enterprise. Consider using the default compliance settings built into Configuration Manager for mobile devices as a baseline, and from there, customize according to your company’s needs. For more information about compliance settings in Configuration Manager, see Introduction to Compliance Settings in Configuration Manager.

By using Windows Selective Wipe, IT can secure the enterprise’s corporate data that is dispersed to corporate or personal devices. Developers can create apps to use a Windows Selective Wipe policy on data and protect it on an Internet domain that is owned by the enterprise. For more information about Windows Selective Wipe, see Windows Selective Wipe for Device Data Management.

## Reporting

Reporting device capabilities or simply understanding how these devices are behaving is fundamental to IT keeping control of known devices. Reports can be used to better understand the current environment. Here are some questions that will arise when you are trying to understand not only the environment, but also the capabilities of some mobile devices:

- How many iOS devices are in use in your organization?
- Which iOS versions are those devices running?
- Which corporate apps are installed on the devices?
- Are any devices in your organization jailbroken?

Consider using a management solution that can provide device inventory and customizable reports. By choosing this option, you will enable a more flexible approach for IT when they need to discover more information about users’ devices. IT must be able to have reports about all devices that were registered on-premises and in the cloud. Reporting capability for the management system can be located on-premises or in the cloud—or it can be a mix of both, which is called a hybrid solution. Use the following table to determine which reporting option is appropriate for your company.

### Reporting options — advantages and disadvantages

Use the list below to understand the advantages and disadvantages of each reporting option:

- On-premises
	- Advantages
		- Centralized report
		- Full controlled by IT
		- Customizable
		- Security controls managed on-premises
	- Disadvantages
		- Unable to natively enumerate devices that are located off-premises
		- Higher administrative overhead, when compared to cloud-based solutions
- Cloud based
	- Advantages
		- Capability to report devices that are joined to the cloud service
		- Cost effective
		- Reporting availability (create and view reports from anywhere)
		- Lower administrative cost, when compared to an on-premises solution
	- Disadvantages
		- Unable to natively enumerate devices that are located on-premises
		- Usually requires monthly subscription to the service
- Hybrid
	- Advantages
		- Capability to report devices that are joined to the cloud service
		- Cost effective
		- Reporting availability (create and view reports from anywhere)
		- Integration with on-premises management solution
	- Disadvantages
		- Usually requires monthly subscription to the service.

By combining Microsoft Intune with System Center 2012 R2, you can have reporting from on-premises and cloud-based devices. Configuration Manager includes many ready-to-use, built-in reports for UDM, including reports for apps, hardware inventory, and settings management. You do not need to create custom reports or separate reports for PC and mobile-device management; these functions can be integrated.

For more information about Configuration Manager reporting capabilities, see [Introduction to Reporting in Configuration Manager](https://technet.microsoft.com/library/gg682105.aspx).

## Compute and storage

After new apps are developed and accessed remotely by users using their own devices, app performance might suffer if the solution has not been well planned. Though this design considerations guide does not intend to offer you a deeper look into performance considerations, questions about the management infrastructure must be answered:

- Is the current management solution that your company uses able to manage storage and compute resources for the platform that supports the apps accessed from users’ devices? 
- Does the current management solution that your company uses have the capability to increase compute and storage resources for the platform that supports app access from users’ devices according to a set of preestablished rules?
If the management solution that is currently in place is not capable of addressing those two requirements, consider using a management solution that can manage compute and storage by addressing the two core requirements shown in the following table.

### Compute and storage management capabilities — advantages and disadvantages

Use the list below to understand the advantages and disadvantages of each storage management capability:

- Resource pooling
	- Advantages
		- Able to allocate compute and storage pooling resources from different locations
		- High level of availability.
		- More robust than solutions that are not able to leverage resource pooling
	- Disadvantages
		- Few management solutions are able to take advantage of resource pooling
		- Initial overhead to implement could be higher if the company is not yet using cloud computing principles in its datacenter
- Elasticity
	- Advantages
		- Able to dynamically allocate compute and storage pooling resources based on demand
		- High level of availability
		- Easier to manage after it is implemented
	- Disadvantages
		- Few management solutions are able to take advantage of elasticity capability
		- Initial overhead to implement could be higher if the company is not yet using cloud computing principles in its datacenter

System Center 2012 R2 has the capability to use resource pooling and the elasticity to manage storage and compute. System Center 2012 R2 also integrates storage with optimization of differencing disks to reduce storage requirements by allowing a large percentage of disk data to be shared among multiple virtual disks, which optimizes storage costs. Servers that are virtualized using System Center 2012 R2 and will be consumed by apps used by remote users can take advantage of this technology.

For more information about System Center 2012 R2 storage capabilities, see [What's New in VMM in System Center 2012 R2](https://technet.microsoft.com/library/dn246490.aspx). 

## Automation

Automation can be employed to remediate noncompliant devices, and IT can assign different levels of noncompliance severity. You should consider the use of automation in different areas of BYOD; for example, how should you automate the deployment of new services that will be consumed by mobile devices? And how should you automate the authorization process for mobile devices?

Although you will see that all BYOD subdomains presented can take advantage of automation, the responsibility to automate resources is owned by the management subdomain. Automation can be built into the operating system; however, the management solution that the company will adopt is responsible for extending these capabilities and providing ways to alleviate daily IT tasks while monitoring and reporting results from the automation.
The most powerful automation option in System Center 2012 R2 is Windows PowerShell. For more information about System Center 2012 R2 automation, see [System Center Automation with Windows PowerShell](https://technet.microsoft.com/library/dn507037(v=sc.20).aspx). However, another option is available that provides a simpler but not very robust form of automating tasks: task sequence. Use the following table to evaluate the advantages and disadvantages of each option.

### Automation options — advantages and disadvantages

Use the list below to understand the advantages and disadvantages of each automation option:

- Windows PowerShell
	- Advantage
		- Integrated with Windows operating system
		- More robust than task sequence
		- Can be scripted
		- Can use programming principles such as procedures, loops, and arrays
		- Provides capabilities beyond the management platform
	- Disadvantages
		- Requires more technical skills in order to use it
		- Depending on the task at hand, developing the initial automation script might require more time
- Task sequence
	- Advantages
		- Easy to use
		- Native capability available in System Center
	- Disadvantages
		- Limited functionality
		- Not scriptable
		- Capabilities are limited to some tasks within System Center itself

## Deployment and provisioning

The next step is to understand the considerations for deploying and provisioning apps to remote devices. Two key questions should be answered:

- How will users access apps from their own devices?
- How will IT provision these apps to users in a friendly and effective manner?

The management solution that will be adopted by the company is also responsible for addressing software distribution and provisioning, regardless of the platform that the user is using. Users should be able to securely access a centralized location from their devices and install the apps that they are authorized to use to perform their work.

One challenge in this area is to be able to manage different platforms and preserve a centralized management interface that allows IT to quickly identify devices that are connected on-premises and in the cloud. You must consider the adoption of a management platform that can consolidate both (on-premises and cloud), and also a management platform that is capable of managing Windows and non-Windows systems.

For centralized management on-premises, you can use Configuration Manager. By using this option, IT can leverage the Enterprise Enrollment capability to enroll devices with the company’s Configuration Manager Server. For more information about how to manage devices using Configuration Manager, see How to Manage Mobile Devices by Using Configuration Manager and Microsoft Intune.

To manage other platforms that are not Windows-based devices, you can leverage the Microsoft Intune cloud service. The Microsoft Intune Company Portal can be used to enroll, manage, and install licensed apps. Users can have easy access to apps and install them on their devices. For more information about Microsoft Intune, see [Microsoft Intune Direct Management](https://technet.microsoft.com/library/jj733620.aspx). For more information about the Microsoft Intune Company Portal, see [The Microsoft Intune Company Portal](https://technet.microsoft.com/library/jj676642.aspx).

Though these are two distinct options, you can integrate both in order to provide app deployment and provisioning from a single location. Use the following table to identify which option fits your BYOD design.

| **Design requirements**                                             | **Deployment and provisioning options**                |
|---------------------------------------------------------------------|--------------------------------------------------------|
| Deploy and provision apps to devices located on-premises only.      | Microsoft System Center 2012                           |
| Deploy and provision apps to devices located outside the company.   | Microsoft Intune                                       |
| Deploy and provision apps to non-Windows devices.                   | Microsoft Intune                                       |
| Deploy and provision apps to devices located on-premises only, deploy and provision apps to devices located outside the company or deploy and provision apps to non-Windows devices.       | Microsoft Intune integrated with Configuration Manager
                                                                    
