---
title: Management requirements
ms.custom: na
ms.reviewer: na
ms.service: multiple
ms.suite: na
ms.technology: na 
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c576a1be-c706-4a12-a2e2-b3d85e632afa
author: YuriDio
---
# Management requirements

Device management is one of the foundations of any people-centric strategy, and it must be evaluated against a company’s requirements. Depending on the maturity level of the company, a management system might be in place already that will need to be expanded to cover the BYOD scenarios that the company is adopting. Figure 4 shows management interactions when managing users, devices, and data. Considerations must be made for each component of the Management subdomain.

![Management requirements](./media/BYOD_Figure4.png)

When considering management capability requirements, you should start by asking the questions listed in the next section.

## Questions to ask

Management requirements questions are categorized in seven areas:

- Monitoring
- Reporting
- Configuration
- Compute
- Storage
- Automation
- Deployment and provisioning


### Monitoring

- Does your company need to monitor compliance settings such as password, camera, and encryption on users’ devices?
- Does your company want to differentiate device ownership (company-owned devices versus user-owned devices)?
- Does your company want to allow users to reset their passwords from their own devices?
- Does your company need to have logging capability built into the management system?
- Does your company need auditing capabilities built into the management system?
- Does your company aggregate this type of logging in a single repository?

### Reporting

- Does your company need reporting capabilities for its BYOD model?
	- If so, which types of reports (such as updates, software installed, and inventory) will be necessary?
- Does the management system in place have these reporting requirements?
	- If so, is it possible to customize them?
- Is there any differentiation in the reporting requirements for domain-joined devices and non-domain joined devices?
	- If so, what are the requirements for each scenario?

### Configuration

- Does your company need a management system that requires users’ devices to be domain-joined in order to be managed?
- Does your company need a management system that integrates with your current directory?
- Does your company need a management system that manages just apps, or should it also manage the operating system running on users’ devices?
- Does your company need a management system that can enforce policies on users’ devices?
- Does your company need a management system that can be integrated with cloud services?
- Does your company plan to perform selective wipe in case a user no longer needs access to the apps that were installed?
	- If so, does the management system in place support selective wipe capability?

### Compute

- What are the compute capabilities required to run the management system on back-end servers?
- What are the compute capabilities required to run the management system on users’ devices?
- Does the management system support leveraging cloud capability to expand on-premises compute resources?

### Storage

- What are the storage requirements to run the management system on back-end servers?
- What are the storage requirements to run the management system on users’ devices?
- Does the management system support leveraging cloud capabilities to expand on-premises storage resources?
- Does the company need to manage external storage drives that are added to users’ devices?
- Does the company need a management system that is also capable of integrating with cloud storage?

### Automation

- Which operations does your company plan to automate for BYOD scenarios?
- What are the automation requirements for the management system that your company plans to adopt?
- Does your current management system support built-in command-line or script automation?
- Does your company have a management system that integrates with cloud services and provides automation capabilities?

### Deployment and Provisioning

- What are the requirements for management agent deployment for your current management system?
- Will any services be offered to remote users that can be instantly provisioned via a portal?
- Are personal devices registered with the company by IT, or are they registered personally?
- Will a plan be in place to allow users to provision services using their own devices?
	- If so, does the management system natively enable users to perform this operation from their devices?

