---
title: Identify SaaS connectivity requirements
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
# Identify SaaS connectivity requirements

>[!NOTE]
>This topic is part of a larger design considerations guide. If you'd like to start at the beginning of the guide, check out the [main topic](mdm-design-considerations-guide.md). To get a downloadable copy of this entire guide, visit the [TechNet Gallery](https://gallery.technet.microsoft.com/Mobile-Device-Management-7d401582).

How you connect your on-premises infrastructure will impact of how user and device identity is managed with all MDM solutions: Intune, MDM for Office 365, and hybrid Intune and ConfigMgr deployments. Both Intune and MDM for Office 365 leverage the directory services architecture provided by Azure Active Directory Services. This integration with Azure gives you a lot of flexibility when you're designing identity management support in your mobile device management solution.

As shown in the Figure 15 below, connecting your on-premises directory services with Azure is the key requirement for enabling single sign-on and unified directory account management. Single sign-on makes it much easier for your users to connect to company resources that are on-premises and in the cloud. Having a single place to manage accounts makes it easier for administrators. For mobile access, synchronizing directory account attributes and credentials between Azure and on-premises directory services allows users to authenticate on their mobile devices for accessing resources that are managed by either MDM for Office 365 or Intune.

![Overview of integrated identity management](./media/MDM_Figure_15.png)

**Overview of integrated identity management**

Depending on how you answered the questions in Task 2, you should be able to determine how the SaaS solution needs to connect to your on-premises client management platform for your mobile device management solution. Table 21 below will help you understand the advantages and disadvantages of connecting your on-premises infrastructure with a SaaS solution:</para><para><legacyBold>Table 21</legacyBold></para><table border="1"><thead><tr><TD><para>Connectivity options</para></TD><TD><para>Advantages</para></TD><TD><para>Disadvantages</para></TD></tr></thead><tbody><tr><TD><para><token>Intune</token> (standalone)</para></TD><TD><list class="bullet"><listItem><para>Tightly integrated with <token>Azure Active Directory</token> for managing user and device identity and authentication</para></listItem><listItem><para>Supports user credential self-management and single sign-on experiences that can leverage existing on-premises account credentials</para></listItem><listItem><para>Supports single sign-on access to  thousands of pre-integrated SaaS applications</para></listItem><listItem><para>Supports application access security by enforcing rules-based multifactor authentication (MFA) for both on-premises and cloud applications</para></listItem></list></TD><TD><list class="bullet"><listItem><para>Advanced directory services connectivity features and functionality require pairing with <token>Azure Active Directory</token> Premium</para></listItem></list></TD></tr><tr><TD><para><token>MDM for Office 365</token></para></TD><TD><list class="bullet"><listItem><para>Integrated with <token>Office 365</token> tenants, which use the <token>Azure Active Directory</token> backbone for managing user and device identity and authentication</para></listItem><listItem><para>On-premises directory services can be connected as a part of connecting services with <token>Office 365</token></para></listItem><listItem><para>Supports user self-management and single sign-on experiences that can leverage existing on-premises account credentials</para></listItem></list></TD><TD><list class="bullet"><listItem><para>Doesn’t support mobile application management integration with other SaaS solutions or applications</para></listItem><listItem><para>Doesn’t support multi-factor authentication</para></listItem></list></TD></tr><tr><TD><para>Hybrid (<token>Intune</token> with <token>ConfigMgr</token>)</para></TD><TD><list class="bullet"><listItem><para>All the advantages of <token>Intune</token> standalone, plus the following:</para><list class="bullet"><listItem><para>Direct integration with on-premises directory services through <token>ConfigMgr</token> infrastructure</para></listItem></list></listItem></list></TD><TD><list class="bullet"><listItem><para>For organizations that don’t have a current <token>ConfigMgr</token> infrastructure configured, it will need to be planned, installed and configured prior to integrating with <token>Intune</token></para></listItem><listItem><para>Requires additional on-premises deployment requirements and configuration changes for organizations with <token>ConfigMgr</token></para></listItem></list></TD></tr></tbody></table></content>
</section></sections></section><section>



