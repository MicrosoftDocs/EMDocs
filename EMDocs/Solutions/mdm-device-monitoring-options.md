---
title: Device monitoring options
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
# Device monitoring options

>[!NOTE]
>This topic is part of a larger design considerations guide. If you'd like to start at the beginning of the guide, check out the [main topic](mdm-design-considerations-guide.md). To get a downloadable copy of this entire guide, visit the [TechNet Gallery](https://gallery.technet.microsoft.com/Mobile-Device-Management-7d401582).

Monitoring and understanding the status and configuration of all mobile devices managed by your organization helps you discover problems and non-compliance, and manage device inventory. Without detailed reports on hardware, software, and compliance status, it’s impossible to make sure that your device policies are actually in place and working correctly. Proactive monitoring helps mitigate small problems before they become larger and more costly.

[Intune](/Intune/deployuse/monitoring-and-reports-with-microsoft-intune), [MDM for Office 365](https://technet.microsoft.com/library/faa7d8e5-645d-4d59-839c-c8d4c1869e4a(v=technet.10).aspx), and a [hybrid deployment](https://technet.microsoft.com/library/gg699377.aspx) of Intune and ConfigMgr all include monitoring and reporting to help manage devices, users, and compliance with your organization’s policies and procedures. Using built-in reports together with customized reports, you can monitor mobile device management in areas such as:

- Update reports for software
- Software inventory reports
- Hardware inventory reports
- Licensing reports
- Non-compliance reports

Depending on how your infrastructure is set up, you may be able to create a variety of reports to help you monitor your organization. Intune-based monitoring and reporting capabilities are the backbone for reports in MDM for Office 365, as well as Intune standalone deployments. These reports can also be tightly integrated with the reporting capabilities of ConfigMgr when it’s connected to Intune in a hybrid deployment. Each product, as shown below, has different but complementary reporting capabilities. It’s important to explore the nuances of the reporting capabilities of each mobile device management solution to help make sure you choose a solution that has the reports that you need.

![Integrated mobile device monitoring and reporting](./media/MDM_Figure_05.png)

**Integrated mobile device monitoring and reporting**

The answers you gave to the questions in Task 2 can help you determine your monitoring and reporting needs for your mobile devices. The lists below show the advantages and disadvantages of the monitoring and reporting features in each MDM solution.

## Intune (standalone)

**Advantages**

- Monitoring overview/dashboard
- Alerts when errors are detected on direct managed network devices
- An Intune service RSS feed can notify you about problems with the service and upcoming maintenance
- Three levels of alerts (critical, warning, Informational) with thresholds and email alert notifications
- Can filter alerts by device type
- Can review the status of any managed device
- Provides reports on devices that do not meet IT policy
- Can monitor details in the following areas:
 - System
 - OS
 - Storage
 - Exchange ActiveSync
 - System enclosure
 - Network
 - Service

**Disadvantages**

- Email alerts only, no text-based or voice alerts

## MDM for Office 365

**Advantages**

- Monitoring overview/dashboard
- Three levels of alerts (critical, warning, Informational) with thresholds and email alert notifications
- Can filter alerts by device type
- Can review the status of any managed device
- Provides reports on devices that do not meet IT policy

**Disadvantages**

- Mobile device compliance status reports only

## Hybrid (Intune with ConfigMgr)

**Advantages**

- All the monitoring and reporting features of Intune standalone, plus the following:
 - Comprehensive, threshold-based, consolidated monitoring and reporting for all your organization’s devices, including non-mobile and non-Intune enrolled devices
 - Advanced reporting capabilities of SQL Server Reporting Services (SSRS) and the rich authoring experience provided by Reporting Services Report Builder

**Disadvantages**

- Requires additional configuration to connect Intune with the on-premises ConfigMgr infrastructure
- For organizations that don’t have a current ConfigMgr infrastructure configured, it will need to be planned, installed and configured prior to integrating with Intune

Explore the details about mobile device monitoring options by reviewing the following:

- Intune: **[How to monitor mobile devices](https://technet.microsoft.com/library/jj733634.aspx)** and [manage reporting](/Intune/deployuse/monitoring-and-reports-with-microsoft-intune)
- ConfigMgr: [Monitoring mobile devices](https://technet.microsoft.com/library/gg682128.aspx) and [manage reporting](https://technet.microsoft.com/library/gg699377.aspx)
- MDM for Office 365: [Overview and device management tasks](https://technet.microsoft.com/en-us/library/ms.o365.cc.devicepolicy.aspx)