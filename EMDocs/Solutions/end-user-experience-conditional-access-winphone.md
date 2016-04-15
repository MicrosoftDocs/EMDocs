---
# required metadata

title: End-user experience of conditional access on Windows Phone
description:
keywords:
author: craigcaseyMSFT
manager: swadhwa
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service:
ms.technology:
ms.assetid: 3e186dd2-e17c-40d8-b160-48038b2c6593

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer:
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Windows Phone

The enrollment process and the screens the user sees will be slightly different depending on the version of OS running on the end-user device.  This topic describes the end-user experience for Windows Phones.

## Enrolling

1.  If a user is already enrolled in Intune and is compliant, they will see no difference on Windows devices; they will continue to get access to email. Users who have not yet enrolled in Intune will receive a quarantine email similar to this sample:

    ![Screenshot showing the quarantine email user receives on a Windows Phone](./media/ProtectEmail/EUX-Windows-quarantineEmail.png)

    The user clicks **Get started now** to begin enrolling their device.

2.  On the Company Access Setup screen, the user clicks **Begin** to start setting up their device and checking whether it is compliant.

    ![Screenshot showing the Company Access Setup screen a Windows Phone](./media/ProtectEmail/EUX-Windows1-company-Access-Setup.png)

3.  On the Enroll Your Device screen, the user clicks **Confirm Enrollment** to start enrolling their device.

    ![Screenshot showing the Device Enrollment screen on a Windows Phone](./media/ProtectEmail/EUX-Windows3-enroll-Device.png)

    During enrollment, the Mobile Device Management profile is installed to allow you, the IT administrator, to remotely manage the device. The user might be prompted to accept a certificate authorizing Workplace Join.

    ![Screenshot showing Workplace Join on a Windows Phone](./media/ProtectEmail/EUX-Windows4-workplaceJoin1.png)

4.  The user signs in using their email address they use with Office. After they are signed in, they might need to click **Confirm Enrollment** once more to continue enrolling their device.

    ![Screenshot showing Workplace Join in progress on a Windows Phone](./media/ProtectEmail/EUX-Windows5-workplaceJoin2.png)

    The device is checked to verify that it is enrolled.

    ![Screenshot showing that device enrollment begins on a Windows Phone](./media/ProtectEmail/EUX-Windows6-checking-Enrollment.png)

5.  The user then completes the enrollment process by selecting their device and clicking **Select**. If their device is not displayed, they can select **I don’t see my device listed** to try again.

    ![Screenshot showing that user must confirm their device for a Windows Phone](./media/ProtectEmail/EUX-Windows7-confirm-Device.png)

    The device is checked to verify that it is complaint with company policies.

    ![Screenshot showing that a Windows Phone is being checked for compliance](./media/ProtectEmail/EUX-Windows9-checking-Compliance.png)

6.  If there is a compliance issue, the user is prompted to resolve the issue (such as creating a valid password) and to then click **Check Compliance** to continue.

    ![Screenshot showing that user must resolve compliance issues on a Windows Phone](./media/ProtectEmail/EUX-Windows13-resolve-Compliance.png)

    After compliance is verified, the user sees that enrollment is being activated.

    ![Screenshot showing that enrollment activation begins on a Windows Phone](./media/ProtectEmail/EUX-Windows10-activating-Enrollment.png)

7.  Enrollment is activated and the user clicks **Continue** to complete the process. The user then clicks **Done** to exit setup.

    ![Screenshot showing that company access setup is completed on a Windows Phone](./media/ProtectEmail/EUX-Windows11-COMPLETE.png)

    After the user is enrolled and compliance is verified, email access should become available within a few minutes.

If the user follows those steps to enroll and become compliant and still cannot access their email on their mobile device, they can follow these additional steps to try and fix the issue:

-   First, verify that their device is enrolled. If not, the user follows the steps above.

-   Verify that the device is compliant by clicking **Check Compliance**. If a compliance error is identified, the user can follow the instructions specific to their mobile device about how to resolve it, such as resetting their password.

-   Call the help desk.

## Issues and Solutions
Every 8 hours by default, devices are checked to ensure that they are still compliant. If a device that was previously compliant is later deemed to be noncompliant (for example, a compliance policy was added or changed), the user can follow these steps to get their device back in compliance:

1.  The user receives notification in email or on their device that the device is noncompliant. At this time, the device is quarantined in Exchange.

2.  If the user tries to access email, they are redirected back to the Company Access Setup screen from the Intune Company portal where it shows that they are out of compliance.

    ![Screenshot showing that a Windows Phone became non-compliant](./media/ProtectEmail/EUX-Windows14-OutOfCompliance.png)

3.  The user clicks **Continue** and is shown the compliance issue that is preventing them from accessing email.

4.  After they have fixed the issue, they click **Check Compliance** to verify that the problem is resolved.

5.  If the issue is fixed, the user clicks **Continue** to complete the process. Email access should become available again within a few minutes.

### Where to go from here
The end-user experience is slightly different on other mobile devices. You can learn more about the end-user experience for [Android](../Solutions/end-user-experience-conditional-access-android.md) and
[iOS](../Solutions/end-user-experience-conditional-access-ios.md).
