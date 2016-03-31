---
title: Client privacy
ms.custom: na
ms.reviewer: na
ms.service: multiple
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c799a6c4-fe0a-4148-8e75-29e6ffdb7e6e
author: YuriDio
---
#Client privacy

>[!NOTE]
>This topic is part of a larger design considerations guide. If you'd like to start at the beginning of the guide, check out the [main topic](mdm-design-considerations-guide.md). To get a downloadable copy of this entire guide, visit the [TechNet Gallery](https://gallery.technet.microsoft.com/Mobile-Device-Management-7d401582).

When your company rolls out mobile device management, it’s important to be aware of the boundaries between user privacy and organization privacy. Ideally, your organization should already have a clear privacy policy stating what’s expected from users regarding data privacy. Since mobile devices might store company data and these devices will be traveling around with the user, it’s important that boundaries are well defined, and that your users know upfront what their role is to maintain privacy for your organization.
  
Another consideration is how you will make sure users are aware of what to expect when they enroll their devices in your organization’s MDM solution. Using [Microsoft Intune Company Portal](https://technet.microsoft.com/library/dn646957.aspx), you can customize your company’s privacy statement to include a URL that has the description of what will be collected from users when they use managed devices.
 
You can also publish terms and conditions that your users will see when they first use the company portal from their devices, whether or not the device is enrolled in the MDM solution. Users must accept the terms before they can access the company portal. When you update the terms and conditions and want users to see and accept the new terms, you can mark the new terms and conditions as a new version, and users will go through the same acceptance process the next time they visit the company portal. 

The same capability for requiring acceptance of terms and conditions is also available when you have a hybrid environment with ConfigMgr connected with Intune. In addition, ConfigMgr can use compliance settings to determine whether devices comply with configuration items that you deployed using configuration baselines. Some settings can be automatically fixed if they’re out of compliance. 

Compliance information is sent to the site server by the management point and stored in the site database. This information is encrypted when devices send it to the management point, but it’s not stored in an encrypted format in the site database. Information is retained in the database until the site maintenance task *Delete Aged Configuration Management Data* deletes it every 90 days.  You also have the capability to configure the deletion interval. This compliance information is not sent to Microsoft.

Since Intune and Office 365 are cloud-based services, users might also want to be aware of how Microsoft handles user privacy for these services. You can provide pointers to privacy information about these services, such as the following:

- Office 365 Trust Center
- Microsoft Intune Trust Center

Privacy is important for both users and your organization, and the MDM solution that you use must appropriately balance privacy needs as well as inform users about your organization’s privacy policy and expectations. The table below compares options for assisting with privacy requirements in different MDM solutions to assist you choosing the MDM option that best fits your organization’s privacy requirements.

## Intune (standalone)

**Advantages**

- Uses the Intune Company Portal to publish your organization’s privacy statement

**Disadvantages**

- It doesn’t have a template for a privacy policy. There is an assumption that your organization has a privacy policy in place and the Company Portal is only going to advertise this policy that is stored in another location

## Office 365 with MDM

**Advantages**

- No features for publishing privacy statements

**Disadvantages**

- No features for publishing privacy statements

## Hybrid (Intune with ConfigMgr)

**Advantages**

- Uses the Intune Company Portal to publish your organization’s privacy statement
- Single management console for mobile devices registered from the cloud and on-premises devices

**Disadvantages**

- If the organization does not have a current on-premises ConfigMgr infrastructure, it will require to plan, install and configure this platform prior to the integration

