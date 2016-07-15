---
# required metadata

title: End-user experience of conditional access on Android devices
description: The end-user experience of enrolling an Android device.
keywords:
author: craigcaseyMSFT
manager: swadhwa
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service:
ms.technology:
ms.assetid: 0b5e4330-6fa5-445c-b73e-86ce5b9c7964

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer:
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Android

The enrollment process and the screens the user sees will be slightly different depending on the version of OS running on the end-user device. This topic describes the end-user experience for enrolling Android devices.

## Enrolling

1.  When they try to access email, the user first receives a quarantine email similar to this sample:

    ![Screenshot showing the quarantine email user receives on an Android device](./media/ProtectEmail/EUX-Android-quarantine-Email.png)

    The user clicks **Get started now** to begin enrolling their device.

    > [!NOTE]
    > If a user has not set a default browser for their device, they will be prompted during device enrollment and during enrollment activation to allow a link to open a browser window. When prompted, they must select the same browser each time or the enrollment process will fail.

2.  The user is prompted to install the Intune Company Portal app from the respective app store.

    ![Screenshot showing the Intune Company Portal on an Android device](./media/ProtectEmail/EUX-Android-Portal.png)

    After it installs, the user opens the app and signs in using their company credentials.

3.  On the Company Access Setup screen, the user clicks **Begin** to start setting up their device and checking whether it is compliant.

    ![Screenshot showing the Company Access Setup screen on an Android device](./media/ProtectEmail/EUX-Android-company-Access-Setup.PNG)

4.  On the Device Enrollment screen, the user clicks **Enroll** to start enrolling their device.

    ![Screenshot showing the Device Enrollment screen on an Android device](./media/ProtectEmail/EUX-Android-device-Enroll.png)

5.  Users must activate the device administrator by clicking **Activate** when prompted or the device enrollment procedure will cancel.

    ![Screenshot showing that the user must activate the device administrator on an Android device](./media/ProtectEmail/EUX-Android-activate-DeviceAdmin.PNG)

    Device enrollment begins. Depending on the device, a certificate installation prompt or a Samsung KNOX Privacy Policy prompt might appear during enrollment. These are necessary to allow you, the IT administrator, to remotely manage the device. The device is enrolled to Intune and establishes a device identity with Azure Active Directory.

    ![Screenshot showing that device enrollment begins on an Android device](./media/ProtectEmail/EUX-Android-enrolling-Device.png)

6.  After enrollment is completed successfully, the user clicks **Continue** to start checking compliance on the device.

    ![Screenshot showing that device enrollment is successful on an Android device](./media/ProtectEmail/EUX-Android-enroll-Success.png)

    If there is a compliance issue, the user is prompted to resolve the issue (such as creating a valid password) and to then click **Check Compliance** to continue.

    ![Screenshot showing that user must resolve compliance issues on an Android device](./media/ProtectEmail/EUX-Android-resolve-Compliance-Issues.png)

7.  After the device is fully compliant, the user clicks **Continue** to initiate enrollment activation. This will connect the AAD device identity with the EAS ID provided by Exchange.

    > [!NOTE]
    > On Android, the default browser will appear for a few seconds during enrollment activation. If the user has not already selected a default browser, they are prompted to choose a browser. While completing Company Access Setup, the same browser must be selected by the user whenever prompted.

    ![Screenshot showing that Android device is compliant](./media/ProtectEmail/EUX-Android-compliance-Successful.PNG)

8.  Enrollment activation will complete and the user clicks **Done** to exit the enrollment and compliance verification process.

    ![Screenshot showing that company access setup is completed on an Android device](./media/ProtectEmail/EUX-Android-all-Successful2.PNG)

    After the user is enrolled and compliance is verified, email access should become available within a few minutes.

If the user follows those steps to enroll and become compliant and still cannot access their email on their mobile device, they can follow these additional steps to try and fix the issue:

1.  First, verify that their device is enrolled. If not, the user follows the steps above.

2.  Verify that the device is compliant by clicking **Check Compliance**. If a compliance error is identified, the user can follow the instructions specific to their mobile device about how to resolve it, such as resetting their password.

3.  Call the help desk.

## Issues and Solutions
Every 8 hours by default, devices are checked to ensure that they are still compliant. If a device that was previously compliant is later deemed to be noncompliant (for example, a compliance policy was added or changed), the user can follow these steps to get their device back in compliance:

1.  The user receives notification in email or on their device that the device is noncompliant. At this time, the device is quarantined in Exchange.

2.  When the user tries to access email, they see a quarantine email informing them that compliance issues must be fixed before they can get access. When the user clicks on the hyperlink in the quarantine email, it redirects them to the Company Access Setup screen in the Intune Company portal (via default browser and Google Play) where it shows that the device is not compliant.

    ![Screenshot showing that Android device became non-compliant](./media/ProtectEmail/EUX-Android-outOfCompliance.png)

3.  The user clicks **Continue** and is shown the compliance issue that is preventing them from accessing email.

    ![Screenshot showing that user must resolve compliance issues on an Android device](./media/ProtectEmail/EUX-Android-resolve-Compliance-Issues.png)

4.  After they have fixed the issue, they click **Check Compliance** to verify that the problem is resolved.

5.  If the issue is fixed, the user clicks **Continue** to complete the process. Email access should become available again within a few minutes.

### Where to go from here
The end-user experience is slightly different on other mobile devices. You can learn more about the end-user experience for [iOS](end-user-experience-conditional-access-ios.md) and [Windows Phone](end-user-experience-conditional-access-winphone.md).
