---
title: Use conditional access with Microsoft Intune and Exchange Online
ms.custom: na
ms.reviewer: na
ms.service:
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid:
author: craigcaseyMSFT
---
# Deploy Exchange Online with Intune

Now that you've read through the [architecture guidance for protecting company email and documents](../Solutions/architecture-guidance-for-protecting-company-email-and-documents.md), you are ready to proceed with deploying a solution.

For Intune to directly manage mobile devices, users need to enroll devices into Intune.

## Deployment Steps
Follow these steps to deploy the Exchange Online with Intune solution:

### Step 1: Create compliance policies and deploy to users.
Compliance policies define the rules and settings that a device must comply with in order to be considered compliant by conditional access polices. Follow the steps at [Create a compliance policy in Microsoft Intune](https://stage.docs.microsoft.com/en-us/intune/deployuse/create-a-device-compliance-policy-in-microsoft-intune) to create and deploy compliance policies.

If you want the ability to remove all corporate email from an iOS device after it is no longer part of your company, you must create and deploy an email profile and then set the compliance policy that specifies that email profiles are managed by Intune. You must deploy the email profile to the same set of users that you target with this compliance policy.

![Screenshot showing the "Rules" page of the Create Compliance Policy Wizard where you can specify that an email profile must be managed by Intune.](./media/ProtectEmail/Hybrid-Onprem-ExchSrvr-Wizard6.PNG)

If you specify this compliance policy, a user who has already set up their email account must manually remove it and then Intune will add it back in through the registration process described in [End-user experience of conditional access](../Solutions/end-user-experience-conditional-access.md).

> [!IMPORTANT]
> If you have not deployed a compliance policy and then enable an Exchange conditional access policy, all targeted devices will be allowed access.

### Step 2: Evaluate the effect of the conditional access policy.
If you have configured a connection between Intune and Exchange by using the [Microsoft Intune service to service connector](https://stage.docs.microsoft.com/en-us/intune/deployuse/intune-service-to-service-exchange-connector), you can use the **Mobile Device Inventory Reports** to identify EAS mail clients that will be blocked from accessing Exchange after you configure the conditional access policy.

Follow the instructions at [Evaluate the effect of the conditional access policy](https://stage.docs.microsoft.com/en-us/intune/deployuse/restrict-access-to-exchange-online-with-microsoft-intune#configure-conditional-access) to identify those users who will be impacted by conditional access policy.

### Step 3: Configure user groups for the conditional access policy.
You target conditional access policies to different groups of users depending on the policy types. These groups contain the users that will be targeted, or exempt from the policy. When a user is targeted by a policy, each device they use must be compliant in order to access email.

For more information, see [Configure user groups for the conditional access policy](https://stage.docs.microsoft.com/en-us/intune/deployuse/restrict-access-to-exchange-online-with-microsoft-intune#configure-conditional-access).

### Step 4: Configure conditional access policy.
The following flow is used by conditional access policies for Exchange Online to evaluate whether to allow or block devices.

![Flowchart showing how conditional access policies for Exchange Online evaluate whether to allow or block devices.](./media/ProtectEmail/conditional-access-8-1.png)

Follow the information provided under [Configure the conditional access policy](https://stage.docs.microsoft.com/en-us/intune/deployuse/restrict-access-to-exchange-online-with-microsoft-intune#configure-conditional-access) to set up your conditional access policy.



## Reporting

### Monitor the compliance and conditional access policies
To view devices that are blocked from Exchange:

On the Intune dashboard, click the **Blocked Devices from Exchange** tile to show the number of blocked devices and links to more information.
![Screenshot showing the "Blocked Devices from Exchange" tile on the Intune dashboard.](./media/ProtectEmail/intune-sa-6blocked-devices.PNG)



## Where to go from here
After you have deployed a solution for protecting corporate email and email data on mobile devices, you can learn more about the [end-user experience of conditional access](../Solutions/end-user-experience-conditional-access.md). This will help prepare you for issues that might arise when end users enroll their specific devices.
