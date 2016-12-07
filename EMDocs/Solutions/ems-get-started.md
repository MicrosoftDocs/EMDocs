---
# required metadata

title: Start using Enterprise Mobility + Security | Microsoft Docs
description:
keywords:
author: jeffgilb
manager: swadhwa
ms.date: 11/10/2016
ms.topic: solution
ms.prod:
ms.service: active-directory
ms.technology:
ms.assetid: 1df56825-c0d1-48ac-a294-5ebd1667bc38

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: mhamerof
ms.suite: ems
#ms.tgt_pltfrm:
ms.custom: advanced-threat-analytics,cloud-app-security,information-protection,microsoft-identity-manager,microsoft-intune,rights-management

experimental: true
experiment_id: jeffgilb-length-20161110

---
# Start using Enterprise Mobility + Security

Organizations going through digital transformation need to protect themselves from new threats and challenges while IT is continually being asked to drive efficiency and do more with less. In addition, in a cloud-first, mobile-first world users expect to be productive from anywhere and on any device. With EMS you get holistic solutions to help you:

- **Control identity + access in the cloud**. Centrally manage identities and secure single sign-on across devices, your datacenter, and the cloud.
- **Get identity-driven security**. Comprehensive, intelligent protection against today's advanced attacks.
- **Manage mobile devices + apps**. Securely manage apps and data on iOS, Android, and Windows from one place.
- **Protect your information**. Intelligently safeguard your corporate data and enable secured collaboration.

Read on to learn about how EMS empowers IT to confidently deliver secure, borderless productivity that people love. These example scenarios will help you get started with EMS as you transition from on-premises to the cloud, leverage cloud security and protection, and finally provide full service IT from the cloud.

## Transition from on-premises to the cloud
EMS is comprised of many services and functionality that you can use depending on your business needs and as you become more familiar with their capabilities.

### Establish Azure AD identity
Everything starts with cloud identity so the first thing you’ll need to do to get started is to establish your organization’s [Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-whatis/) presence. You can do this completely from the cloud or [synchronize your current Windows Server Active Directory objects with Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect/) to leverage your current investments in on-premises identity management.

### Protect your organization at the front door
Traditional security solutions used to be enough to protect your business. But that was before the mobility industry grew, which created a larger attack landscape, and the transition to the cloud made employees' interactions with other users, devices, apps, and data more complex. To truly protect your business now, you need to [take a more holistic and innovative approach to security](https://docs.microsoft.com/enterprise-mobility-security/solutions/protect-front-door), one that can protect, detect, and respond to threats of all kinds on-premises as well as in the cloud.

### Start managing devices
Ensuring corporate data is secure and administrative costs are low, while also managing device complexity in the enterprise, can be challenging for traditional IT. EMS makes it easy for you to support many different device management scenarios ranging from company-owned Choose Your Own Device (CYOD) to Bring Your Own Device (BYOD) personally owned devices used at work.

- **Issue corporate owned devices**. Intune offers bulk provisioning and management solutions to help you [issue corporate-owned devices](https://docs.microsoft.com/intune/deploy-use/manage-corporate-owned-devices) in your organization that are integrated with the major corporate device management platforms on the market today, including the Apple Device Enrollment Program and the Samsung KNOX mobile security platform.
- **Enable a limited-use shared device solution**. Task workers are increasingly making use of mobile technologies. Whether used to process a sale or instantly check inventory, tablets that might only run a single line-of-business app, are usually handed to employees in a limited-use mode. Intune enables you to bulk provision, secure, and centrally manage these shared iOS and Android tablets that can be configured to run in this limited-use mode.
- **Enable a BYOD program in your organization**. BYOD continues to grow in popularity among organizations as a means to reduce hardware expenditures or increase mobile productivity choices for employees. As enterprises move away from the traditional model of corporate-owned devices, they must [decide how to implement a BYOD program](https://docs.microsoft.com/enterprise-mobility-security/solutions/byod-design-considerations-guide) to allow employees use their personal devices for some of their work tasks.
- **Align Windows 10 deployment and management strategy to business, end-user, and IT needs**. Windows 10 provides new deployment capabilities, scenarios, and tools by building on technologies introduced in Windows 7, and Windows 8.1, while at the same time introducing new Windows as a service concepts to keep the operating system up to date. Together, these changes require that you [rethink the traditional deployment process](https://technet.microsoft.com/itpro/windows/plan/windows-10-deployment-considerations). After you have deployed Windows 10, you will also need to [determine how to best manage Windows 10 PCs](https://docs.microsoft.com/intune/get-started/choose-how-to-manage-devices) using Intune to meet your end-user productivity and business needs. You have two choices: enroll the Windows 10 PC as a mobile device or install the Intune software client to manage the device as a computer.

### Manage and protect company data
Most information workers are mobile these days and making productivity on mobile devices is an imperative to be competitive. These employees need seamless access to all corporate apps and data, at any time, wherever they are and EMS makes this easy to do, whether on-premises or in the cloud.
- **Protect on-premises company data**. Most enterprise mobility strategies begin with a plan to enable secure access to email for employees with mobile devices out on the internet, but you also need to be able to [securely access on-premises company data](https://docs.microsoft.com/enterprise-mobility-security/solutions/conditional-access-intune-exchange) being accessed by mobile devices. For example, many organizations still have on-premises data and application servers, like Microsoft Exchange, hosted on their corporate network.
- **Protect Office 365 company data**. [Protecting corporate data in Office 365 (email, documents, instant messages, etc.)](https://docs.microsoft.com/enterprise-mobility-security/solutions/protect-office365-data-with-intune) could not be easier for you or more seamless for your users. Office 365 and EMS provide a uniquely integrated conditional access solution that ensures no users, apps, or devices can access Office 365 data unless they meet your company’s compliance requirements (performed multi-factor authentication, enrolled with Intune, using managed app, supported OS version, device pin, low user risk profile, etc.).
- **Secure access to Office 365 and protect data on unmanaged devices**. A common Office 365 deployment practice is to require devices to enroll into management, but that is not always necessary. If a user simply needs to access corporate email and documents, which is often the case for personally owned devices, then you can just use the Office mobile apps ([which you have applied app restriction policies to](https://docs.microsoft.com/intune/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune)) and skip enrolling the device altogether.

## Leverage cloud security and protection
EMS provides an identity-driven security solution that offers a holistic approach to the security challenges in this mobile-first, cloud-first era. With EMS, you can not only protect your shared organizational data, but also identify security breaches before they have a chance to cause damage.

### Securely share data
Nowadays information sharing is taking place from multiple devices and across organizational boundaries. Companies are challenged to identify what data needs protection and what data does not. To meet this challenge, you can [classify, label and protect sensitive data](https://docs.microsoft.com/enterprise-mobility-security/solutions/infoprotect-secure-classify-scenario) with [Azure Information Protection](https://docs.microsoft.com/information-protection/understand-explore/what-is-information-protection) to ensure that critical corporate data is not compromised while enabling users to securely share what’s important for them to get their jobs done.

### Identify and protect against threats
<!-- Detect advanced threats on-premises and in the cloud (ATA, Azure AD, Cloud App Security) -->
As more organizations move to an assume breach posture, EMS helps you identify attackers in your organization using innovative behavioral analytics and anomaly detection technologies―on-premises with [Microsoft Advanced Threat Analytics](http://www.microsoft.com/ata) and in the cloud with [Azure Active Directory](http://www.microsoft.com/identity) and [Cloud App Security](http://www.microsoft.com/cloudappsecurity). Our threat intelligence is enhanced with the Microsoft Intelligent Security Graph driven by vast datasets and machine learning in the cloud.

## Full service IT from the cloud
As organizations complete their digital transformation, full service IT from the cloud will become business as usual. Companies with mature cloud implementations will look to take advantage of the capabilities provided by EMS to enable long-term, end-to-end identity and data protection scenarios.

### Identity management from hire to retire
Microsoft has been securing cloud-based identities for over a decade, and with Azure Active directory, Microsoft is making these same protection systems available to enterprise customers, to ensure user’s and administrator’s accountability with better security and governance.
- **Thousands of Apps, one Identity**. Azure AD is a cloud identity and access management solution that can provide organizations with access to everything they need from everywhere. Azure Active Directory (Azure AD) makes your users more productive by [providing a common identity for users of software as a service (SaaS) applications](https://docs.microsoft.com/enterprise-mobility-security/solutions/thousands-apps-one-identity) accessing both cloud and on-premises resources.
- **Enable business without borders**. Organizations need to [empower their employees to access all their data and applications from every device and every location](https://docs.microsoft.com/enterprise-mobility-security/solutions/enable-business-without-borders). Users need to collaborate with each other and with partners, and connect with customers.
- **Manage access at scale**. Azure AD provides a set of tools to automate [advanced user lifecycle management](https://docs.microsoft.com/enterprise-mobility-security/solutions/manage-access-at-scale) by leveraging, dynamic group membership rules, and application management capabilities.
- **Cloud-powered protection**. Azure AD Identity Protection is a security service that provides a [consolidated view into risk events and potential vulnerabilities](https://docs.microsoft.com/enterprise-mobility-security/solutions/cloud-powered-protection) affecting your organization’s identities.

### Protect shared files and SaaS apps with policies and tracking
EMS seamlessly integrates advanced company data protection into the rhythm of your business to make it easy to safeguard company information from both purposeful and accidental data loss.
- **Share sensitive data internally and externally**. While many data breaches are due to cyberattacks, experts agree that many more are the result of human error, otherwise known as “oops” moments that happen when employees inadvertently leak sensitive business data. [With the right security information and data loss prevention protocols in place](https://docs.microsoft.com/enterprise-mobility-security/solutions/share-sensitive-data), nearly all of these kinds of breaches are avoidable.
- **Track usage of shared data and respond to data abuse**. [Azure Information Protection](https://docs.microsoft.com/information-protection/understand-explore/what-is-information-protection) is a cloud-based solution that helps an organization to classify, label, and protect its documents and emails. This can be done automatically by administrators who define rules and conditions, manually by users, or a combination where users are given recommendations.
- **Manage your data your way with flexible deployment and key management options**. Instead of Microsoft managing your tenant key (the default), you might want to [manage your own Azure Information Protection tenant key](https://docs.microsoft.com/en-us/information-protection/plan-design/plan-implement-tenant-key) to comply with specific regulations that apply to your organization. Managing your own tenant key is also referred to as bring your own key, or BYOK.
- **Sanction and manage SaaS applications for employees**. Use [Cloud App Security](https://docs.microsoft.com/cloud-app-security/what-is-cloud-app-security) to sanction/unsanction applications, enforce data loss prevention (DLP), control permissions and sharing, and generate custom reports and alerts.
- **Protect your data from user mistakes**. We provide deep visibility into user and data activity, so you can [protect your company when users make poor choices](https://docs.microsoft.com/enterprise-mobility-security/solutions/protect-data-user-mistake) as they work with critical company data. Microsoft Cloud App Security provides visibility and controls for cloud apps, including Office 365. With Azure Information Protection, we have brought together classification and labeling with persistent data protection to enable secure file sharing, internally and externally.


### Learn more

[Visit the Microsoft Enterprise Mobility + Security page](http://go.microsoft.com/fwlink/?LinkId=816837)

[Learn about Enterprise Mobility + Security](learn-about-ems.md)

[Try out EMS for free](https://www.microsoft.com/en-us/cloud-platform/enterprise-mobility-security-trial)
