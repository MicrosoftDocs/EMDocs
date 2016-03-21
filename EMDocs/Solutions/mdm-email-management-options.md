---
title: Email management options
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
# Email management options

>[!NOTE]
>This topic is part of a larger design considerations guide. If you'd like to start at the beginning of the guide, check out the [main topic](mdm-design-considerations-guide.md). To get a downloadable copy of this entire guide, visit the [TechNet Gallery](https://gallery.technet.microsoft.com/Mobile-Device-Management-7d401582).

The main reason for implementing a mobile device management solution is usually to provide managed access to corporate email from mobile devices. For example, in <token>MDM for Office 365</token>, you can create a <externalLink><linkText>security policy</linkText><linkUri>https://technet.microsoft.com/library/ms.o365.cc.newdevicepolicy.aspx</linkUri></externalLink> that provide basic managed access to email mailboxes hosted in <token>Exchange Online</token> or access through Office apps (on iOS and Android). This policy enforces basic mobile device compliance settings, such as requiring a device password and device encryption, before the device is allowed to connect to a user mailbox.

You follow a similar process to configure email management options in <token>Intune</token>, and hybrid <token>Intune</token> and <token>ConfigMgr</token> deployments. The primary difference is that you can implement more advanced email management options than you can in <token>MDM for Office 365</token>. For example, using <token>Intune</token> standalone, you can configure conditional email access to allow access mailboxes hosted on both <token>Exchange Online</token> and Exchange on-premises, as well as configure customized email profiles. <token>Intune</token> enables these features by using configuration and compliance policies.  Hybrid <token>Intune</token> and <token>ConfigMgr</token> deployments also supports conditional email access, but only for mailboxes hosted on <token>Exchange Online

In the scenario shown below in Figure 6, the user has enrolled their device in <token>Intune</token> and is now trying to access their corporate email using <token>Office 365</token> or Exchange on-premises. Based on the settings defined by the IT administrator at their company, <token>Intune</token> runs a policy verification process. In this scenario, the user’s access is granted if the device is encrypted, a passcode is set, and the device isn’t jail broken or rooted. If a user tries to access corporate email and their device is not enrolled, or not compliant based upon settings defined by the IT admin, the user will receive an email explaining why their access has been blocked along with steps for how to resolve the issue. 

![Conditional access](./media/MDM_Figure_06.png)

**Conditional access**

Your answers to the questions in Task 1 can help you determine how you want devices to be managed in the mobile device management solution. Table 9 below lists the advantages and disadvantages of email management in each MDM solution.

</para><para><legacyBold>Table 9</legacyBold></para><table border="1"><thead><tr><TD><para>Email management option</para></TD><TD><para>Advantages</para></TD><TD><para>Disadvantages</para></TD></tr></thead><tbody><tr><TD><para><token>Intune</token> (standalone)</para></TD><TD><list class="bullet"><listItem><para>Supports email management for all major mobile device operating systems (Android, iOS, Windows 10, Windows 8.x, and Windows Phone)</para></listItem><listItem><para>Can leverage native mobile device email applications via integration with <token>Exchange ActiveSync</token></para></listItem><listItem><para>Integration with <token>Exchange Online</token> via the Service-to-Service connector to allow cross-platform monitoring and reporting between <token>Intune</token> and <token>Office 365</token></para></listItem><listItem><para>Supports configuration of email profiles for managing <token>Exchange ActiveSync</token>-based settings on mobile devices</para></listItem><listItem><para>Conditional email access to resources</para></listItem></list></TD><TD><list class="bullet"><listItem><para>	Email profiles aren’t supported for Android-based mobile devices</para></listItem></list></TD></tr><tr><TD><para><token>MDM for Office 365</token></para></TD><TD><list class="bullet"><listItem><para>Allows <token>Exchange ActiveSync</token> support for password, encryption, rooted device compliance</para></listItem><listItem><para>Allows device management policies and requiring device enrollment before access is granted to Office and OneDrive for Business apps (iOS and Android)</para></listItem><listItem><para>Conditional email access to resources</para></listItem></list></TD><TD><list class="bullet"><listItem><para>	Some advanced email management options aren’t supported  </para></listItem><listItem><para>Deploying email profiles isn’t supported (except iOS)</para></listItem></list></TD></tr><tr><TD><para>Hybrid (<token>Intune</token> with <token>ConfigMgr</token>)</para></TD><TD><list class="bullet"><listItem><para><token>Intune</token> On-premises Connector for hybrid connectivity with <token>Exchange Online</token></para></listItem><listItem><para>Integration with <token>Exchange ActiveSync</token> (most strict policy setting is enforced)</para></listItem><listItem><para>Email profiles</para></listItem><listItem><para>Conditional access to restrict email access to <token>Exchange Online</token></para></listItem><listItem><para>Compliance policies to define the rules and settings the device must comply with in order to be allowed access to the services</para></listItem><listItem><para>Conditional access policies for each service, define rules for security groups, <token>Intune</token> groups, or how unenrolled devices are managed</para></listItem></list></TD><TD><list class="bullet"><listItem><para>Managed access to email only available for mailboxes hosted on <token>Exchange Online</token>, not mailboxes hosted on Exchange on-premises</para></listItem><listItem><para>Configuring the service-to-service connector should not be configured if you enable conditional access for both <token>Exchange Online</token> and Exchange on-premises</para></listItem></list></TD></tr></tbody></table><para>

Explore the details about mobile device email configuration management options by reviewing the following:

- Intune: How to [enable email profiles](https://technet.microsoft.com/library/dn800672.aspx) and [conditional email access](https://technet.microsoft.com/library/dn818907.aspx)
- ConfigMgr: Enabling [email profiles](https://technet.microsoft.com/library/dn554227.aspx)  and [conditional email access](https://technet.microsoft.com/library/dn919655.aspx)
- MDM for Office 365: [Capabilities of mobile device management](https://technet.microsoft.com/library/ms.o365.cc.devicepolicysupporteddevice.aspx)