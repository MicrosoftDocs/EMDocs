---
title: Learn how to deploy a solution for protecting company email and documents
ms.custom: na
ms.reviewer: na
ms.service: microsoft-intune
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2e10af43-3138-45c0-b2f7-14a1d2bfb237
author: karthikaraman
---
# Learn how to deploy a solution for protecting company email and documents
More and more, companies are allowing employees to increase their productivity by accessing email, documents, and company resources through their mobile devices. However, the amount of confidential data that is stored within corporate emails and documents presents a significant security risk for companies.

This guide is intended for you, the IT professional, to help determine and then deploy the best solution for your company to enforce conditional access in one of the configurations as described below. This will let employees use their mobile devices to access corporate email while still protecting your company’s data.

> [!TIP]
> Get a downloadable copy of this entire topic at the [TechNet Gallery](https://gallery.technet.microsoft.com/Deploying-Enterprise-16499404).

## Introduction
Protecting your company's data is vitally important, and is an increasingly challenging task as more employees are using their mobile devices to access company resources, including email and email attachments. As an IT administrator, you want to make sure that company data is protected even when those mobile devices are not within the company’s physical location.

The Microsoft Enterprise Mobility Suite (EMS) solves this challenge by delivering comprehensive protection of corporate email and documents across four layers – Identity, Device, Application, and Data. Among other capabilities, EMS ensures that employees can access corporate email only from devices that are managed by Microsoft Intune and compliant with IT policies.

Protecting corporate email involves two main objectives:

-   **Allow only compliant devices to access your company’s email:** An important step to protecting corporate data is restricting access to devices that don’t use a strong password, are not jailbroken, or not encrypted.  Microsoft Intune gives you the ability to set conditions that your users must meet to gain access to your company resources. This is known as conditional access.

-   **Protecting the content in email and attachments:** While conditional access allows you to make sure only compliant devices are able to access email, there is still the question of protecting the content in the email and email attachments.  The content can be copied, moved, saved to a different location, or shared with another user.  EMS solves this problem using mobile application management policies.

    Managed apps are apps that have mobile application management policies applied to them that make them compliant with your company’s security requirements. With these apps, you have direct control over deployment, ongoing management like inventory or updates, and selective wipe of the apps and their associated data. Additionally, through a set of mobile application management (MAM) policies, Intune lets you modify the functionality of apps, and restrict sharing of data. For more details on how this solution works including architecture details see [Protect corporate email and documents](https://technet.microsoft.com/en-us/library/mt574220.aspx).

    > [!NOTE]
    > You can create and deploy an email profile, then set a compliance policy that specifies that email profiles must be managed by Intune (recommended). This gives you the ability to wipe email from retired devices, and it ensures that for iOS, attachments can only be opened in applications managed by Intune. See [Step 5: Create compliance policies and deploy to users.](../Topic/Use-conditional-access-with-Intune-and-Configuration-Manager.md#Step_5) for more information.

### <a name="Step_5"></a>Solutions covered in this article
This section provides a  high-level overview of each solution – Configuration Manager with Intune implementation, Intune by itself, mobile application management, and Azure rights management service.

-   Manage access to email using Conditional access

    You can use a hybrid of Configuration Manager with Intune, or just use Intune by itself, along with Exchange Online or Exchange Server on-premises to manage and enforce conditional access on all types of PCs and mobile devices, regardless of their location. Enforcing conditional access in this type of environment lets you enable the user to be more productive, while still keeping company data secure.

-   Protect email attachments and data using the MAM solution

    You can enforce mobile application management (MAM) policies in Intune to modify the functionality of apps that you deploy in your company. For example, you can restrict cut, copy and paste operations within a managed app, or configure an app to open all web links inside a managed browser. This ensures that these apps are in line with your company compliance and security policies.

-   Azure rights management service for data loss prevention policies

    Azure Rights Management (Azure RMS) uses encryption, identity, and authorization policies to help secure your files and email across multiple devices, such as phones, tablets, and PCs. Information can be protected both within your company and outside your company because protection remains with the data, even when it leaves your company’s boundaries.

### Evaluating your desired implementation
With all of the different design and configuration options for managing mobile devices, it’s difficult to determine which combination will best meet the needs of your company. The [Mobile Device Management Design Considerations Guide](https://technet.microsoft.com/en-us/library/mt143180.aspx) helps you understand mobile device management design requirements and details a series of steps and tasks that you can follow to design a solution that best fits the business and technology needs for your company.

### High level end-user experience
After the solution is implemented, end-users will only be able to access the company email on managed **and** compliant devices. Once they have the ability to access the email on the devices, the company data is protected and contained within the app ecosystem and only available to the intended users. Access can be revoked at any time if the device becomes noncompliant.

Specifically, the conditional access policies set in Intune ensure that the devices can only access email if they are compliant with the compliance policies you set. Actions such as copy and paste or saving to personal cloud storage services can be restricted using mobile application management policies. Azure Rights Managements service can be used to ensure that the sensitive email data, and forwarded attachments, can only be read by intended recipients. The end-user experience is described in more detail in [End-user experience of conditional access](../Topic/End-user-experience-of-conditional-access.md).

## See Also
[Use conditional access with Intune and Configuration Manager](../Topic/Use-conditional-access-with-Intune-and-Configuration-Manager.md)
[End-user experience of conditional access](../Topic/End-user-experience-of-conditional-access.md)

