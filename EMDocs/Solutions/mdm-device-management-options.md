---
title: Device management options
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
# Device management options

>[!NOTE]
>This topic is part of a larger design considerations guide. If you'd like to start at the beginning of the guide, check out the [main topic](mdm-design-considerations-guide.md). To get a downloadable copy of this entire guide, visit the [TechNet Gallery](https://gallery.technet.microsoft.com/Mobile-Device-Management-7d401582).

Managing mobile devices with Intune and ConfigMgr centers around management policies. Policies define groups of settings for mobile devices and can be either created from templates or customized for specific devices, users, or groups. The best management practice is to create management policies before mobile devices are enrolled in the management solution. This insures that the devices are immediately managed in accordance with the policies and processes defined in your IT strategy. Both solutions allow for configuring the following policy types:

- Configuration policies: Configuration policies are used to define the general organizational settings for each enrolled mobile device. This may include device password, application, cloud policy, and encryption settings, but can include **[many other device settings](https://technet.microsoft.com/library/dn743712.aspx)** for different management areas. Additionally, configuration policies are applied and configured differently for different types of mobile device operating systems by using device enrollment profiles.

>[!TIP]
>When creating different policies for different types of devices, users, or groups – it’s easy to have conflicting policy settings applied to the same device. Be sure that you understand **[how conflicting policy settings are applied](https://technet.microsoft.com/library/dn743712.aspx)**.

- **Compliance policies:** Compliance policies enforce your organization’s requirements for mobile devices to access (or be denied access) to company resources or services. This can also include device password and encryption settings, as well as determining if the mobile device is rooted (“jailbroken”). As with configuration policies, Intune and [ConfigMgr](https://technet.microsoft.com/library/dn376523.aspx) compliance policy options also vary by mobile device operating system type. If you’re creating compliance policies in ConfigMgr, it’s important to note that increased granularity can be configured as part of a multi-part process:

 1. Creating [configuration items](https://technet.microsoft.com/library/gg712331.aspx?WT.mc_id=Blog_EntMob_Showcase_PCIT)
 2. Creating [configuration baselines](https://technet.microsoft.com/library/gg712268.aspx?WT.mc_id=Blog_EntMob_Showcase_PCIT)
 3. Deploying the [configuration baselines](https://technet.microsoft.com/library/hh219289.aspx?WT.mc_id=Blog_EntMob_Showcase_PCIT) to ConfigMgr user or device collections

- **Conditional access policies:** Conditional access policies define how access to email is managed and can be used separately or in conjunction with compliance policies. Connections to your on-premises Exchange Server or Exchange Online service must be configured in [Intune](https://docs.microsoft.com/intune/deployuse/restrict-access-to-email-and-o365-services-with-microsoft-intune.html) or in [ConfigMgr](https://technet.microsoft.com/library/dn919655.aspx) before conditional access policies can be deployed. Conditional access can also be configured for Office 365 and SharePoint Online services.

Your answers the questions in Step 1 can help you determine how you want devices to be enrolled in the mobile device management solution. The lists below will help you understand the advantages and disadvantages of each management scenario.

## Intune (standalone)

**Advantages**

- Supports simplified policy control for managing users and devices, now separated by device platform.
- Supports Android, iOS, Windows 10https://technet.microsoft.com/library/mt147406.aspx, Windows 8.x, and Windows Phone platforms, as well as support for Exchange ActiveSync.
- Provides a simple, web-based administration & management console that is accessible from any location
- Supports group-based policies, making it easier to manage large numbers and diverse types of mobile devices
- Supports advanced mobile device compliance features and functionality, including device root and jailbreak detection
- Allows for selective wipe or full factory reset for all mobile devices
- Includes a customizable Company portal, allowing the managed and secure distribution of internal and 3rd party mobile applications
- Deploy certificates to mobile devices
- Allows organizations to prevent cut/copy/paste functions in mobile applications
- Supports enforcing the use of managed browsers
- Supports using device IMEI numbers to identify and tag corporate-owned devices to separate policy assignments from personal-owned devices

**Disadvantages**

- Additional licensing requirements and costs for user accounts enrolling devices in the Intune service

## MDM for Office 365

**Advantages**

- Integrated web-based administration and management console within Office 365 tenants
- Supports group-based policies, making it easier to manage large numbers and diverse types of mobile devices
- Supports advanced mobile device compliance features and functionality, including device root and jailbreak detection
- Allows selective wipe or full factory reset for all mobile devices

**Disadvantages**

- Advanced mobile device management features aren’t supported, including:
 - Provisioning and managing certificates, email, VPN, wireless profiles
 - Enrolling and managing collections of devices
- Some mobile application management features and functionality aren’t supported:
 - Deploying line of business applications to mobile devices
 - Enabling secure data access to Office mobile applications
 - Extending corporate data securely to line of business apps for mobile devices
 - Managed browsers or other content viewing applications

## Hybrid (Intune with ConfigMgr)

**Advantages**

- All the advantages of Intune standalone, plus the following:
 - Provides a single pane of glass view for managing the corporate estate, including flexibility for role-based administration and scripting (through PowerShell)

**Disadvantages**

- Requires additional configuration to connect Intune with the on-premises ConfigMgr infrastructure
- For organizations that don’t have a current ConfigMgr infrastructure configured, it will need to be planned, installed and configured prior to integrating withIntune
- VPN and email profiles for Android devices aren’t currently supported
- Managed browser support isn’t currently supported