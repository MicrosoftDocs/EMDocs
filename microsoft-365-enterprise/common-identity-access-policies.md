---
title: Common identity and device access policy recommendedations - Microsoft 365 Enterprise | Microsoft Docs
description: Describes the policies for Microsoft recommendations about how to apply common Microsoft 365 Enterprise policies and configurations.
author: jeffgilb
manager: femila
ms.prod: microsoft-365-enterprise
ms.topic: article
ms.date: 08/01/2017
ms.author: jeffgilb
ms.reviewer: jsnow
ms.custom: it-pro
---

# Deploy common identity and device access policies
This section discusses how to deploy the recommended policies in a newly provisioned environment. Setting up these policies in a separate lab environment allows you to understand and evaluate the recommended policies before staging the rollout to your pre-production and production environments. Your newly provisioned environment may be cloud-only or Hybrid.  

To successfully deploy the recommended polices, you need to take actions in the Azure portal to meet the prerequisites stated earlier. Specifically, you need to:
* Configure named networks, to ensure Azure Identity Protection can properly generate a risk score
* Require all users to register for multi-factor authentication (MFA)
* Configure password sync and self-service password reset to enable users to be able to reset passwords themselves

You can target both Azure AD and Intune policies towards specific groups of users. We suggest rolling out the policies defined earlier in a staged way. This way you can validate the performance of the policies and your support teams relative to the policy incrementally.

## Baseline conditional access policy

To create a new conditional access policy, log in to the Microsoft Azure portal with your administrator credentials. Then navigate to **Azure Active Directory > Security > Conditional access**. 

You can add a new policy (+Add) as shown in the following screen shot:

![Baseline CA policy](./media/secure-email/baseline-ca-policy.png)

The following tables describe the appropriate settings necessary to express the policies required for each level of protection.

### Medium and above risk requires MFA

The following table describes the conditional access policy settings to implement for this policy.

|Categories|Type|Properties|Values|Notes|
|:---------|:---|:---------|:-----|:----|
|**Assignments**|Users and groups|Include|Select users and groups – Select specific security group containing targeted users|Start with security group including pilot users.|
|||Exclude|Exception security group; service accounts (app identities)|Membership modified on an as needed temporary basis|
||Cloud apps|Include|Select apps -  Select Office 365 Exchange Online||
||Conditions|Configured|Yes|Configure specific to your environment and needs|
||Sign-in risk|Risk level|High, medium|Check both|
|**Access controls**|Grant|Grant access|True|Selected|
|||Require MFA|True|Check|
|||Require compliant devices|False||
|||Require domain joined devices|False||
|||Require all the selected controls|True|Selected|
|**Enable policy**|||On|Deploys conditional access policy|


## Sensitive conditional access policy

### Low and above risk requires MFA
The following table describes the conditional access policy settings to implement for low- and above-risk policies.

|Categories|Type|Properties|Values|Notes|
|:---------|:---|:---------|:-----|:----|
|**Assignments**|Users and groups|Include|Select users and groups – Select specific security group containing targeted users|Start with security group including pilot users|
|||Exclude|Exception security group; service accounts (app identities)|Membership modified on an as needed temporary basis|
||Cloud apps|Include|Select apps -  Select Office 365 Exchange Online||
||Conditions|Configured|Yes|Configure specific to your environment and needs|
||Sign-in risk|Configured|Yes|Configure specific to your environment and needs|
|||Risk level|Low, medium, high|Check all three|
|**Access controls**|Grant|Grant access|True|Selected|
|||Require MFA|True|Check|
|||Require compliant devices|False||
|||Require domain joined device|False||
|||Require all the selected controls|True|Selected|
|**Enable policy**|||On|Deploys conditional access policy|

### Require a compliant or domain joined device
(See baseline instructions)

### Mobile application management conditional access for Exchange online

(See baseline instructions)

#### Apply to

Once the pilot project has been completed, these policies should be applied to users in your organization who require access to email considered sensitive.

## Highly regulated conditional access policy
### MFA required

The following table describes the conditional access policy settings to implement for the highly regulated policy.

|Categories|Type|Properties|Values|Notes|
|:---------|:---|:---------|:-----|:----|
|**Assignments**|Users and groups|Include|Select users and groups – Select specific security group containing targeted users|Start with security group including pilot users|
|||Exclude|Exception security group; service accounts (app identities)|Membership modified on an as needed temporary basis|
||Cloud apps|Include|Select apps -  Select Office 365 Exchange Online||
|**Access controls**|Grant|Grant access|True|Selected|
|||Require MFA|True|Check|
|||Require complaint devices|False|Check|
|||Require domain joined device|False||
|||Require all the selected controls|True|Selected|
|**Enable policy**|||On|Deploys conditional access policy|

### Require a compliant or domain joined device
(See baseline instructions)
### Mobile application management conditional access for Exchange online
(See baseline instructions)
#### Apply to
Once the pilot project has been completed, these policies should be applied to users in your organization who require access to email considered highly regulated.

## User risk policy
### High risk users must change password
To ensure that all high-risk users compromised accounts are forced to perform a password change when signing-in, you must apply the following policy. 

Log in to the [Microsoft Azure portal (http://portal.azure.com)](http://portal.azure.com/) with your administrator credentials, and then navigate to **Azure AD Identity Protection > User Risk Policy**.

|Categories|Type|Properties|Values|Notes|
|:---------|:---|:---------|:-----|:----|
|**Assignments**|Users|Include|All users|Selected|
|||Exclude|None||
||Conditions|User risk|High|Selected|
|**Controls**|Access|Allow access|True|Selected|
||Access|Require password change|True|Check|
|**Review**|N/A|N/A|N/A|N/A|
|**Enforce policy**|||On|Starts enforcing policy|