---
title: Data classification
ms.custom: na
ms.reviewer: na
ms.service: multiple
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5dffb570-dd1a-4beb-aa1e-7c0b51393704
author: YuriDio
---
# Data classification

>[!NOTE]
>This topic is part of a larger design considerations guide. If you'd like to start at the beginning of the guide, check out the [main topic](mdm-design-considerations-guide.md). To get a downloadable copy of this entire guide, visit the [TechNet Gallery](https://gallery.technet.microsoft.com/Mobile-Device-Management-7d401582).

Most companies already have a [data classification](http://blogs.microsoft.com/cybertrust/2014/01/28/the-importance-of-data-classification/) policy in place, and you’ll need to understand how deploying a mobile device management solution will affect this policy. If your company does not have a current data classification policy, you should introduce this capability in conjunction with planning your mobile device management solution. Some organizations perform on-premises data classification at the file server level using [Active Directory Rights Management Services (ADRMS)](https://technet.microsoft.com/windowsserver/dd448611.aspx). Another tool some companies use is the [Microsoft Data Classification Toolkit](http://www.microsoft.com/download/details.aspx?id=27123), helping organizations to identify, classify, and protect data on their file servers. 

Office 365 provides some automatic data classification of email that can help surface sensitive information that should be protected. Office 365 uses transport rules, incorporated into mail flow processing, to detect sensitive information. Then the [DLP feature](http://blogs.office.com/2013/10/28/office-365-compliance-controls-data-loss-prevention/) performs deep content analysis through keyword matches, dictionary matches, regular expression evaluation, internal functions such as validate checksum on credit card numbers, and other content examination to detect specific content types within the message body or attachments. 

Intune and ConfigMgr don’t have data classification built in, so they rely on cloud-based classification using Azure RMS or on-premises using ADRMS. Another option is to use the [Enterprise Mobility Suite (EMS)](http://www.microsoft.com/server-cloud/enterprise-mobility/overview.aspx) as your MDM solution. With EMS, you’ll have access to [Azure AD Premium](https://msdn.microsoft.com/library/azure/dn532272.aspx) and [Azure RMS](https://technet.microsoft.com/library/jj585026.aspx), which can be used to classify data. Data classification using Azure RMS can be integrated with an on-premises management solution in a hybrid environment. 

Intune enables IT to comply with policies by using compliance policies, which is set of rules and settings that a device must comply with in order to be considered compliant by conditional access polices. You can also use compliance policies to monitor and remediate compliant issues with devices independently of conditional access. Read [Manage device compliance policies for Microsoft Intune](https://technet.microsoft.com/library/dn705843.aspx) for more information.

Use the table below as a reference to assist you choosing the MDM option that best fits your organization’s *data classification* requirements.

| **MDM option**                 | **Advantages**                                                                                                                                                                                      | **Disadvantages**                                                                                                                           |
|--------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------|
| **Intune (standalone)**            | Not available                                                                                                                                                                                       | Not available                                                                                                                               |
| **MDM for Office 365**             | Exchange Transport rules can be used to detect sensitive information                                                                                                                                | Data classification is not carried with the file itself. Once the file is located at the mobile device, it can be used without restrictions |
|                                | Leverages [data loss prevention (DLP)](https://technet.microsoft.com/library/ms.o365.cc.DLPLandingPage.aspx) policy in the Compliance Center to identify sensitive information across many location |                                                                                                                                             |
| **Hybrid (Intune with ConfigMgr)** | Not available                                                                                                                                                                                       | Not available                                                                                                                               |
| **Enterprise Mobility Suite**      | Leverages Azure RMS to perform data classification                                                                                                                                                  | Not available for customers that are not adopting cloud-based solution                                                                      |
|                                | Azure RMS subscription is included with EMS                                                                                                                                                         |                                                                                                                                             |
|                                | Doesn’t require an on-premises infrastructure for data classification                                                                                                                               |                                                                                                                                             |
|                                | Can be integrated with existing on-premises AD RMS solution                                                                                                                                         |                                                                                                                                             |
|                                | Protection is located in the file itself, which means that the file will keep its classification even if it was saved in a different location                                                       |                                                                                                                                             |

