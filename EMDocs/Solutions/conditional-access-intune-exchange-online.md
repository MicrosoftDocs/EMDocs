---
# required metadata

title: Use conditional access with Microsoft Intune and Exchange Online | Enetrprise Mobility Suite
description:
keywords:
author: craigcaseyMSFT
manager: swadhwa
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service:
ms.technology:
ms.assetid: 8cfe421b-52c9-4d44-8df1-15c82375c335

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: 
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Deploy Exchange Online with Intune

Now that you've read through the [architecture guidance for protecting company email and documents](../Solutions/architecture-guidance-for-protecting-company-email-and-documents.md), you are ready to proceed with deploying a solution.

For Intune to directly manage mobile devices, users need to enroll devices into Intune.

## Deployment Steps
Follow these steps to deploy the Exchange Online with Intune solution:

### Step 1: Create compliance policies and deploy to users.
Compliance policies define the rules and settings that a device must comply with in order to be considered compliant by conditional access polices. Follow the steps at [Create a compliance policy in Microsoft Intune](https://stage.docs.microsoft.com/en-us/intune/deployuse/create-a-device-compliance-policy-in-microsoft-intune) to create and deploy compliance policies.

If you want the ability to remove all corporate email from an iOS device after it is no longer part of your company, you must create and deploy an email profile and then set the compliance policy that specifies that email profiles are managed by Intune. You must deploy the email profile to the same set of users that you target with this compliance policy.

![](./media/ProtectEmail/Hybrid-Onprem-ExchSrvr-Wizard6.PNG)

If you specify this compliance policy, a user who has already set up their email account must manually remove it and then Intune will add it back in through the registration process described in [End-user experience of conditional access](./Solutions/end-user-experience-conditional-access.md).

> [!IMPORTANT]
> If you have not deployed a compliance policy and then enable an Exchange conditional access policy, all targeted devices will be allowed access.

### Step 2: Evaluate the effect of the conditional access policy.
If you have configured a connection between Intune and Exchange by using the [Microsoft Intune service to service connector](https://stage.docs.microsoft.com/en-us/intune/deployuse/intune-service-to-service-exchange-connector), you can use the **Mobile Device Inventory Reports** to identify EAS mail clients that will be blocked from accessing Exchange after you configure the conditional access policy.

Follow the instructions at [Evaluate the effect of the conditional access policy](https://technet.microsoft.com/en-us/library/dn705841.aspx#bkmk_Eval_FX_CAP) to identify those users who will be impacted by conditional access policy.

### Step 3: Configure user groups for the conditional access policy.
You target conditional access policies to different groups of users depending on the policy types. These groups contain the users that will be targeted, or exempt from the policy. When a user is targeted by a policy, each device they use must be compliant in order to access email.

For more information, see [Configure user groups for the conditional access policy](https://technet.microsoft.com/en-us/library/dn705841.aspx#BKMK_configUserGroups).

### Step 4: Configure conditional access policy.
The following flow is used by conditional access policies for Exchange Online to evaluate whether to allow or block devices.

![](./media/ProtectEmail/conditional-access-8-1.png)

Follow the information provided under [To enable the Exchange Online policy](https://technet.microsoft.com/en-us/library/dn705841.aspx#BKMK_ExoCA) to set up your conditional access policy.



## Reporting

### Monitor the compliance and conditional access policies
To view devices that are blocked from Exchange:

On the Intune dashboard, click the **Blocked Devices from Exchange** tile to show the number of blocked devices and links to more information.
![IntuneSA6BlockedDevices](./media/ProtectEmail/intune-sa-6blocked-devices.PNG)



## Where to go from here
After you have deployed a solution for protecting corporate email and email data on mobile devices, you can learn more about the [end-user experience of conditional access](../Solutions/end-user-experience-conditional-access.md). This will help prepare you for issues that might arise when end users enroll their specific devices.
