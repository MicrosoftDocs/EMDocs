---
title: Device enrollment options
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

# Device enrollment options

>[!NOTE]
>This topic is part of a larger design considerations guide. If you'd like to start at the beginning of the guide, check out the [main topic](mdm-design-considerations-guide.md). To get a downloadable copy of this entire guide, visit the [TechNet Gallery](https://gallery.technet.microsoft.com/Mobile-Device-Management-7d401582).

Enrolling devices in <token>Microsoft Intune</token>, whether standalone or when connected to <token>System Center 2012 R2 Configuration Manager</token> (ConfigMgr), requires that you prepare the service for the devices. Enrolling mobile devices in <token>MDM for Office 365</token> also requires that you activate MDM, configure basic settings, and include each user in a <externalLink target="_blank"><linkText>security policy</linkText><linkUri>https://technet.microsoft.com/library/ms.o365.cc.newdevicepolicy.aspx</linkUri></externalLink> respond to an enrollment message the next time they sign in to <token>Office 365</token> on their mobile device. They must complete the enrollment and activation steps on each mobile device they will use to access <token>Office 365</token> email and documents.

Intune</token> standalone needs to be configured to define the Mobile Device Management Authority solution, which can be either <token>Intune</token> or an on-premises <token>ConfigMgr</token> infrastructure. This simply means “which management platform do you want to use to manage <token>Intune</token>-enrolled devices – <token>Intune</token> <legacyItalic>or</legacyItalic> <token>ConfigMgr</token>?” It’s <legacyItalic>very important</legacyItalic> to understand the <externalLink><linkText>impact of choosing the best option</linkText><linkUri>https://technet.microsoft.com/library/dn646962.aspx</linkUri></externalLink> for your organization, as the management solution cannot be easily changed once chosen. If you need to change this configuration later, you’ll have to contact <token>Microsoft</token> Support for assistance.

For most organizations that are already using <token>ConfigMgr</token> to manage PCs, servers, and other devices, connect the on-premises solution with <token>Intune</token> and managing devices with  <token>ConfigMgr</token>  is usually the best choice. To assign the mobile device management authority to ConfigMgr, you’ll create an <externalLink target="_blank"><linkText>Intune subscription from within the ConfigMgr console </linkText><linkUri>https://technet.microsoft.com/library/jj884158.aspx</linkUri></externalLink>and select the option to allow ConfigMgr to manage the Intune subscription and <token>Intune</token>-enrolled devices.

Additionally, before you can enroll certain types of mobile devices running different types of mobile operating systems, you’ll need to prepare the <token>Intune</token> service or <token>MDM for Office 365</token> with specific configuration requirements. For example, if you plan to enroll Apple iOS-based devices, you’ll need to <externalLink target="_blank"><linkText>configure Intune with an Apple Push Notification (APN) service certificate</linkText><linkUri>https://technet.microsoft.com/library/dn408185.aspx</linkUri></externalLink> prior to enrolling iOS-based devices. If this isn’t configured, <token>Intune</token> can’t communicate with the APN service and iOS-based devices. Mobile devices running <externalLink><linkText>Android</linkText><linkUri>https://technet.microsoft.com/library/dn764960.aspx</linkUri></externalLink> or <externalLink target="_blank"><linkText>Windows Phone</linkText><linkUri>https://technet.microsoft.com/library/dn764959.aspx</linkUri></externalLink> operating systems have separate enrollment requirements

Your answers to the questions in Task 1 will help you decide how you want devices to be enrolled in your mobile device management solution. Table 5 below compares the advantages and disadvantages of each enrollment scenario.

</para><para><legacyBold>Table 5</legacyBold></para><table>
<thead><tr><TD><para>Enrollment scenario</para></TD><TD><para>Advantages</para></TD><TD><para>Disadvantages</para></TD></tr></thead><tbody><tr><TD><para>Administrators enroll all mobile devices</para></TD><TD><list class="bullet"><listItem><para>Administrators closely control the enrollment of all devices, effectively pre-screening any device or user at the beginning of the enrollment process</para></listItem><listItem><para>Each device is enrolled without any user interaction, reducing device enrollment errors</para></listItem><listItem><para>Easier to support more complex, automated, bulk, or highly customized device enrollment processes</para></listItem><listItem><para>Support/help desk costs may decrease since experienced administrators are performing the device enrollments</para></listItem></list></TD><TD><list class="bullet"><listItem><para>If supporting a BYOD strategy, increased likelihood that administrators may see or expose sensitive user personal information if appropriate security controls are not in place</para></listItem><listItem><para>Users may have to arrange times with you to drop off and pick up mobile devices, requiring device enrollment scheduling and tracking</para></listItem><listItem><para>Modern mobile device users may feel that this centralization is cumbersome and inconvenient, leading to user-defined workarounds that may compromise enrollment security and compliance processes</para></listItem></list></TD></tr>
<tr><TD><para>User self-enrolls mobile devices</para></TD><TD><list class="bullet"><listItem><para>More convenient and flexible for device owners/users.</para></listItem><listItem><para>Quicker device enrollment than a centralized enrollment process in most cases</para></listItem><listItem><para>Offloads relatively simple administration tasks from you to your users, saving time, scheduling, tracking, and administration overhead costs</para></listItem></list></TD><TD><list class="bullet"><listItem><para>Potential increase in support costs or help desk calls, less-experienced users may need personal help with enrollment</para></listItem></list></TD></tr>
</tbody></table>

Your organization might want to allow both of these enrollment scenarios, taking a flexible approach to permit different methods for different departments or situations. If so, your mobile device management solution must be able to support both scenarios.