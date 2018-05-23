---
# required metadata

title: How to manage your password
description: How to manage your own password
keywords:
author: NathBarn
ms.author: NathBarn
manager: angrobe
ms.date: 02/01/2017
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 162e59f3-33a2-44b5-a59f-24612dc743f3

# optional metadata

#ROBOTS: noindex
#audience:
#ms.devlang:
ms.reviewer:
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# How to manage your own password

If you're a user (not an admin) in an organization that uses Office 365 or Microsoft Accounts to access work resources, read the sections below to learn how to fix common problems with your password.

## How to register for password reset
The fastest way to register for password reset is to go to [http://aka.ms/ssprsetup](http://aka.ms/ssprsetup).

1.	Navigate to [http://aka.ms/ssprsetup](http://aka.ms/ssprsetup).
2.	Enter your username and password.
3.	Choose an option to register for by clicking **set it up now**. In this case, I'll demonstrate registering my **authentication phone**.
![Screenshot showing blahblah](./media/ft-mngPW-1-setup.png)
4.	Select your country code from the dropdown and enter your full phone number with area code.
![Screenshot showing how to select a country code. ](./media/ft-mngPW-2-enterNumber.png)![Screenshot showing where to enter a phone number.](./media/ft-mngPW-3-enterNumber2.png)
5.	Select one of the **text me** or **call me** options. In this case, I'll select **text me**, which will send a 6 digit code to my phone. Wait for the code to arrive on your phone.  
![Screenshot showing a 6-digit code that has been sent to a phone.](./media/ft-mngPW-4-textCode.png)
6.	Once the code arrives, enter it into the input box, then click "verify".
7.	When you see **thanks**, that's it! Now you can use what you registered for to reset your password at any time by going to [https://passwordreset.microsoftonline.com](https://passwordreset.microsoftonline.com).
![Screenshot showing the thank you message received when registration is completed.](./media/ft-mngPW-5-thanks.png)

> [!IMPORTANT]
> If your admin lets you register for more than one option, we highly recommend you also register a back-up option in case you lose your phone or access to your email.

## How to reset your password
Follow the steps below to reset your work or school account password from any work or school account sign-in screen.

> [!IMPORTANT]
> This feature is only available to you if your admin has turned it on. If it's not turned on, you'll see a message indicating your account is not enabled for this feature. You can use the "contact your administrator" link in this case to get in touch with your admin to unlock your account.
> 
> If your admin has enabled you for this feature, you'll first need to sign up before you can use it. You can do that here: [http://aka.ms/ssprsetup](http://aka.ms/ssprsetup).

1. On the any work or school account sign-in page, click on one of the "can't access your account?" or "forgot your password?" links, or navigate to [https://passwordreset.microsoftonline.com](https://passwordreset.microsoftonline.com) directly.
   ![Screenshot showing the first message a user receives if their user ID or password is not recognized.](./media/ft-mngPW-6-resetPWbegin.png)
2. On the "who are you?" page, enter your work or school account ID and prove you aren't a robot by passing the captcha.
   ![Screenshot prompting the user to enter their user ID and the captcha code displayed.](./media/ft-mngPW-7-enterID.png)
3. Click **Next**.
4. Choose an option to reset your password. Depending on how your admin has configured the system, you might see one or more of the following choices:
   - **Email my alternate email** - sends an email with a 6 digit code to either your alternate email or authentication email (you choose).
   - **Text my mobile phone** - texts your phone with a 6 digit code to either your mobile phone or authentication email (you choose).
   - **Call my mobile phone** - calls your mobile phone or authentication phone (you choose) - press the # key to verify the call.
   - **Call my office phone** - calls your office phone - press the # key to verify the call.
   - **Answer my security questions** - displays your pre-registered security questions for you to answer.
   ![Screenshot prompting user to choose the method in which they want to be contacted for verification.](./media/ft-mngPW-8-answerQuestions.png)
5. We'll use the **text my mobile phone** option as an example. If you are using a phone-based option, you'll need to verify your phone number before we'll send a text. Enter your full phone number and then click **Next** to verify it's correct and send a text.
   ![Screenshot showing that user needs to enter phone number where they will receive the verification text message.](./media/ft-mngPW-9-textNumber.png)
6. When you receive the text, make sure you use the verification code in the message body, not the number the code was sent from. It might take a few minutes to get the text, so grab a coffee!  
   ![Screenshot showing the verification code that was received.](./media/ft-mngPW-10-verificationCode.png)
7. Now, enter the code you just received on your phone into the input box on the page.
   ![Screenshot showing that user must enter the verification code they just received.](./media/ft-mngPW-11-enterCode.png)
8. Your admin may require a second verification step, in which case repeat step 4 with a different option selected.
9. On the "choose a new password" screen, select a new password and confirm your choice, then click **Finish**.
   ![Screenshot showing that the user must enter and then confirm a new password.](./media/ft-mngPW-12-clickFinish.png)
10.	Once you see the success page, you are good to go! You can now sign in with your new password.
    ![Screenshot showing that the password reset process is completed.](./media/ft-mngPW-13-success.png)
    Run into a problem resetting your password? Read about [common problems and their solutions](https://azure.microsoft.com/documentation/articles/active-directory-passwords-update-your-own-password/#common-problems-and-their-solutions).

### Want to learn more?
See [Enterprise Mobility + Security](https://www.microsoft.com/en-us/server-cloud/enterprise-mobility/overview.aspx).
