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
ms.service: ems
ms.technology:
ms.assetid: 9938ab0e-19b8-49a2-91b5-61d69eb3dc01

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: mhamerof
ms.suite: ems
#ms.tgt_pltfrm:
ms.custom: active-directory,advanced-threat-analytics,cloud-app-security,information-protection,microsoft-identity-manager,microsoft-intune,rights-management

experimental: true
experiment_id: "jeffgilb-length-20161110"
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
Everything starts with cloud identity so the first thing you’ll need to do to get started is to establish your organization’s [Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-whatis/) presence. Use Microsoft’s platform and security graph to protect your identities, cloud apps, and on premises environment from advanced threats.

You can do this completely from the cloud or [synchronize your current Windows Server Active Directory objects with Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect/) to leverage your current investments in on-premises identity management.


### Protect your organization at the front door
Traditional security solutions used to be enough to protect your business. But that was before the mobility industry grew, which created a larger attack landscape, and the transition to the cloud made employees' interactions with other users, devices, apps, and data more complex. To truly protect your business now, you need to [take a more holistic and innovative approach to security](https://docs.microsoft.com/enterprise-mobility-security/solutions/protect-front-door), one that can protect, detect, and respond to threats of all kinds on-premises as well as in the cloud.

### Start managing devices
Most information workers are mobile these days, making productivity on mobile devices an imperative to be competitive. These employees need seamless access to all corporate apps and data, at any time, wherever they are. You need to ensure corporate data is secure and administrative costs are low. IT needs to manage device complexity in the enterprise ranging from company-owned Choose Your Own Device (CYOD) to Bring Your Own Device (BYOD) personally owned devices used at work.

**Issue corporate owned devices**. Intune offers bulk provisioning and management solutions to help you [issue corporate-owned devices](https://docs.microsoft.com/intune/deploy-use/manage-corporate-owned-devices) in your organization that are integrated with the major corporate device management platforms on the market today, including the Apple Device Enrollment Program and the Samsung KNOX mobile security platform. Centralized authoring of device configurations with Intune makes provisioning of corporate devices something that can be highly automated.

Picture this: hand an employee an unopened iPhone box. The employee powers it on and is walked through a corporate-branded setup flow where they must authenticate themselves. The iPhone is seamlessly configured with security policies (encrypt hard drive, device pin, etc.), email/Wi-Fi/VPN/certificate profiles, and a baseline set of apps. Then, the employee launches the Intune Company Portal app to access optional corporate apps available to them.

**Enable a limited-use shared device solution**. Task workers are increasingly making use of mobile technologies. For example, shared tablets are now commonplace for retail store employees. Whether used to process a sale or instantly check inventory, tablets help create great customer interactions. Simplicity of the user experience is critical in this case. For this reason, tablets are usually handed to employees in a limited-use mode, such that a single line-of-business app is the only thing the employee can interact with. Intune enables you to bulk provision, secure, and centrally manage these shared iOS and Android tablets that can be configured to run in this limited-use mode.

**Enable a BYOD program in your organization**. BYOD continues to grow in popularity among organizations as a means to reduce hardware expenditures or increase mobile productivity choices for employees. As enterprises move away from the traditional model of corporate-owned devices, they must [decide how to implement a BYOD program](https://docs.microsoft.com/enterprise-mobility-security/solutions/byod-design-considerations-guide) to allow employees use their personal devices for some of their work tasks.

Just about everyone has a personal phone these days so why put another one in their pocket? The main challenge has always been to convince employees to enroll their personal device into management, as they are fearful of what their IT department will be able to see and do with their device. When device enrollment is not a viable option, Intune offers an alternative BYOD approach of simply [managing the apps that contain corporate data](https://docs.microsoft.com/intune/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune). Intune protects the corporate data even if the app in question accesses both corporate and personal data, as is the case for Office mobile apps.

**Align Windows 10 deployment and management strategy to business, end-user, and IT needs**. Windows 10 provides new deployment capabilities, scenarios, and tools by building on technologies introduced in Windows 7, and Windows 8.1, while at the same time introducing new Windows as a service concepts to keep the operating system up to date. Together, these changes require that you [rethink the traditional deployment process](https://technet.microsoft.com/itpro/windows/plan/windows-10-deployment-considerations).

After you have deployed Windows 10, you will also need to [determine how to best manage Windows 10 PCs](https://docs.microsoft.com/intune/get-started/choose-how-to-manage-devices) using Intune to meet your end-user productivity and business needs. You have two choices: enroll the Windows 10 PC as a mobile device or install the Intune software client to manage the device as a computer.

### Manage and protect company data
Most information workers are mobile these days and making productivity on mobile devices is an imperative to be competitive. These employees need seamless access to all corporate apps and data, at any time, wherever they are and EMS makes this easy to do, whether on-premises or in the cloud.

**Protect on-premises company data**. Most enterprise mobility strategies begin with a plan to enable secure access to email for employees with mobile devices out on the internet, but you also need to be able to [securely access on-premises company data](https://docs.microsoft.com/enterprise-mobility-security/solutions/conditional-access-intune-exchange) being accessed by mobile devices. For example, many organizations still have on-premises data and application servers, like Microsoft Exchange, hosted on their corporate network. Intune and the Microsoft Enterprise Mobility + Security (EMS) provide a uniquely integrated conditional access solution for Exchange Server that ensures no mobile apps will be able to access email until the device is enrolled with Intune, all without deploying another gateway machine to the edge of your corporate network!

Beyond email, Intune supports enabling access to mobile apps that require secure access to on-premises data, like a line of business app server. This is typically done using Intune-managed certificates for access control combined with a standard VPN gateway or proxy in the perimeter such as Microsoft Azure AD Application Proxy. In these cases, the only way to access the corporate data is to enroll the device into management. Once enrolled, Intune ensures that devices accessing corporate data are compliant with your policies.

**Protect Office 365 company data**. [Protecting corporate data in Office 365 (email, documents, instant messages, etc.)](https://docs.microsoft.com/enterprise-mobility-security/solutions/protect-office365-data-with-intune) could not be easier for you or more seamless for your users. Intune and Microsoft Enterprise Mobility + Security provide a uniquely integrated conditional access solution that ensures no users, apps, or devices can access Office 365 data unless they meet your company’s compliance requirements (performed multi-factor authentication, enrolled with Intune, using managed app, supported OS version, device pin, low user risk profile, etc.). The Office mobile apps in their respective app stores are ready to go with data containment policies you can configure via Intune, enabling you to prevent data from being shared with apps (e.g. native email app) and storage locations (e.g. Dropbox) that aren’t managed by IT. All this functionality is built into Office 365 and EMS. You do not have to deploy additional infrastructure to get this value.

**Secure access to Office 365 and protect data on unmanaged devices**. A common Office 365 deployment practice is to require devices to enroll into management, but that is not always necessary. If a user simply needs to access corporate email and documents, which is often the case for personally owned devices, then you can just use the Office mobile apps ([which you have applied app restriction policies to](https://docs.microsoft.com/intune/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune)) and skip enrolling the device altogether.

## Leverage cloud security and protection
EMS provides an identity-driven security solution that offers a holistic approach to the security challenges in this mobile-first, cloud-first era. With EMS, you can not only protect your shared organizational data, but also identify security breaches before they have a chance to cause damage.

### Securely share data
Nowadays information sharing is taking place from multiple devices and across organizational boundaries. Companies are challenged to identify what data needs protection and what data does not. To meet this challenge, you can [classify, label and protect sensitive data](https://docs.microsoft.com/enterprise-mobility-security/solutions/infoprotect-secure-classify-scenario) with [Azure Information Protection](https://docs.microsoft.com/information-protection/understand-explore/what-is-information-protection) to ensure that critical corporate data is not compromised while enabling users to securely share what’s important for them to get their jobs done.

Azure Information Protection lets organizations classify, label, and protect data at the time of creation or modification. With Azure Information Protection, users can:
- Classify data based on sensitivity, and add labels—manually or automatically
- Protect data using encryption, authentication and use rights
- Enable intuitive, non-intrusive experience for end users

### Identify and protect against threats
<!-- Detect advanced threats on-premises and in the cloud (ATA, Azure AD, Cloud App Security) -->
As more organizations move to an assume breach posture, EMS helps you identify attackers in your organization using innovative behavioral analytics and anomaly detection technologies―on-premises with [Microsoft Advanced Threat Analytics](http://www.microsoft.com/ata) and in the cloud with [Azure Active Directory](http://www.microsoft.com/identity) and [Cloud App Security](http://www.microsoft.com/cloudappsecurity). Our threat intelligence is enhanced with the Microsoft Intelligent Security Graph driven by vast datasets and machine learning in the cloud.

Advanced Threat Analytics continuously learns from the behavior of users, devices, and resources and adjusts to reflect the changes in your rapidly evolving enterprise. As tactics get more sophisticated, Advanced Threat Analytics uses behavioral analytics to help you adapt and respond.

## Full service IT from the cloud
As organizations complete their digital transformation, full service IT from the cloud will become business as usual. Companies with mature cloud implementations will look to take advantage of the capabilities provided by EMS to enable long-term, end-to-end identity and data protection scenarios.

### Identity management from hire to retire
Microsoft has been securing cloud-based identities for over a decade, and with Azure Active directory, Microsoft is making these same protection systems available to enterprise customers, to ensure user’s and administrator’s accountability with better security and governance.

**Thousands of Apps, one Identity**. Get single sign-on to thousands of cloud apps and access to web apps that you run on-premises with Azure Active Directory Premium. Built for ease of use, Azure Active Directory management tools enable collaboration and deliver holistic identity protection and adaptive access control.

Azure AD is a cloud identity and access management solution that can provide organizations with access to everything they need from everywhere. Azure Active Directory (Azure AD) makes your users more productive by [providing a common identity for users of software as a service (SaaS) applications](https://docs.microsoft.com/enterprise-mobility-security/solutions/thousands-apps-one-identity) accessing both cloud and on-premises resources.

**Enable business without borders**. Organizations need to [empower their employees to access all their data and applications from every device and every location](https://docs.microsoft.com/enterprise-mobility-security/solutions/enable-business-without-borders). Users need to collaborate with each other and with partners, and connect with customers.

This new world introduces challenges and advanced threats that cannot be mitigated with traditional tools. There is no point in protecting just your network while the new boundary is the user. The key to be productive and protected in this environment is a strong identity solution.

**Manage access at scale**. Azure AD provides a set of tools to automate [advanced user lifecycle management](https://docs.microsoft.com/enterprise-mobility-security/solutions/manage-access-at-scale) by leveraging, dynamic group membership rules, and application management capabilities.

Azure AD Premium not only provides identity that takes you everywhere, but it also provides a set of tools to automate, secure, and manage IT within your organization. Even after the advent of cloud-computing, there is still demand to manage and control IT operations like helpdesk calls to reset user passwords, user group management, and application requests.

**Cloud-powered protection**. Azure AD Identity Protection is a security service that provides a [consolidated view into risk events and potential vulnerabilities](https://docs.microsoft.com/enterprise-mobility-security/solutions/cloud-powered-protection) affecting your organization’s identities.

Azure Active directory identity protection is unique. It uses machine learning to analyze more than 10TB of behavioral and contextual data every day, which provides visibility over suspicious activity, and allows you to take immediate action if necessary.

In addition, Azure AD conditional access rules allows customers to control access to online services, based on attributes such as device compliance or network location. The following may be distinguished:
- Azure AD MFA-based conditional access
- Azure AD Location-based conditional access
- Azure AD Device-based conditional access

### Protect shared files and SaaS apps with policies and tracking
EMS seamlessly integrates advanced company data protection into the rhythm of your business to make it easy to safeguard company information from both purposeful and accidental data loss.

**Share sensitive data internally and externally**. While many data breaches are due to cyberattacks, experts agree that many more are the result of human error, otherwise known as “oops” moments that happen when employees inadvertently leak sensitive business data. [With the right security information and data loss prevention protocols in place](https://docs.microsoft.com/enterprise-mobility-security/solutions/share-sensitive-data), nearly all of these kinds of breaches are avoidable.

EMS allows IT Administrators to leverage Azure Rights Management policy template to email usage. Usage rights are attached to the message itself so that protection occurs online and offline as well as inside and outside of the organization’s firewall.

**Track usage of shared data and respond to data abuse**. [Azure Information Protection](https://docs.microsoft.com/information-protection/understand-explore/what-is-information-protection) is a cloud-based solution that helps an organization to classify, label, and protect its documents and emails. This can be done automatically by administrators who define rules and conditions, manually by users, or a combination where users are given recommendations.

You use Azure Information Protection labels to apply classifcation to documents and emails. When you do this, the classification is identifiable at all times, regardless of where the data is stored or with whom it’s shared. The persistent labels include visual markings such as a header, footer, or watermark. Metadata is added to files and email headers in clear text so that other services (such as data loss prevention solutions) can identify the classification and take appropriate action.

**Manage your data your way with flexible deployment and key management options**. Instead of Microsoft managing your tenant key (the default), you might want to [manage your own Azure Information Protection tenant key](https://docs.microsoft.com/en-us/information-protection/plan-design/plan-implement-tenant-key) to comply with specific regulations that apply to your organization. Managing your own tenant key is also referred to as bring your own key, or BYOK.

**Sanction and manage SaaS applications for employees**. Use [Cloud App Security](https://docs.microsoft.com/cloud-app-security/what-is-cloud-app-security) to sanction/unsanction applications, enforce data loss prevention (DLP), control permissions and sharing, and generate custom reports and alerts.

 Cloud App Security is a comprehensive solution that helps organizations take full advantage of the promise of cloud applications while maintaining control with improved visibility into activity. It also increases protection of critical data across cloud applications. With tools to help uncover Shadow IT, assess risk, enforce policies, investigate activities and stop threats, organizations can safely move to the cloud while maintaining control of critical data.

**Protect your data from user mistakes**. While the transition to mobility and the cloud has substantially increased employee productivity, the complex interaction between users, devices, apps, and data – on-premises as well as in the cloud – has generated new blind spots for IT teams. Even though organizations may not embrace this transition, employees already are. As the interactions between these components and the sophistication of attack vectors increases, security remains a top challenge for enterprises. IT staffs struggle to maintain visibility, control, and protection of corporate data.

Cloud App Security provides deep visibility into user and data activity, so you can [protect your company when users make poor choices](https://docs.microsoft.com/enterprise-mobility-security/solutions/protect-data-user-mistake) as they work with critical company data. In addition, you get visibility and controls for cloud apps, including Office 365. With Azure Information Protection, we have brought together classification and labeling with persistent data protection to enable secure file sharing, internally and externally.

### Learn more

[Visit the Microsoft Enterprise Mobility + Security page](http://go.microsoft.com/fwlink/?LinkId=816837)

[Learn about Enterprise Mobility + Security](learn-about-ems.md)

[Try out EMS for free](https://www.microsoft.com/cloud-platform/enterprise-mobility-security-trial)
