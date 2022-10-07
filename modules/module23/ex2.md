---
title: Adobe Journey Optimizer - Configure a trigger-based journey - Account Creation
description: This exercise updates the existing registration journey created in Module 6 to serve the confirmation email using Journey Optimizer instead of ACS
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
exl-id: a6a5d752-ffc5-4b18-8401-003a3e7f6781
---
# 23.2 Configure a trigger-based journey - Account Creation

Login to Adobe Experience Cloud by going to [Adobe Experience Cloud](https://experience.adobe.com). Click **Adobe Journey Optimizer**.

![Journey Optimizer](./images/23.1-1.png)

You'll be redirected to the **Home** view in Journey Optimizer.

![Journey Optimizer](./images/23.1-3.png)

Before you continue, you need to select a **sandbox**. The sandbox to select is named ``--aepSandboxId--``. You can do this by clicking the text **[!UICONTROL Production Prod]** in the blue line on top of your screen.

![Journey Optimizer](./images/23.1-3a.png)

## 23.2.1 Configure your trigger-based journey

Go to **Journeys**.

![Journey Optimizer](./images/23.2-1.png)

Search for your **ldap**.

![Journey Optimizer](./images/23.2-2.png)

Search and find the Account Creation Journey that you created in [Module 6 - Journey Orchestration](../module6/journey-orchestration-create-account.md) and which you updated in [Module 17 - Adobe Experience Platform and Microsoft Dynamics 365](../module17/adobe-experience-platform-microsoft-dynamics-365.md). It should be named **ldap - Account Creation Journey**. Click the journey name to open it.

![Journey Optimizer](./images/23.2-2.png)

In the top-right corner, find the **Duplicate** button and click on the arrow next to it. Click **Create a new version**.

![Journey Optimizer](./images/23.2-4.png)

Click on the **Create a new version** button in the pop-up window. Your journey will now be editable. 

![Journey Optimizer](./images/23.2-5.png)

Select the **Email** action in your journey, this will display a menu on the right side of the screen. This **Email** action relies on Adobe Campaign Standard to send out emails. In this exercise, that now needs to change to use Journey Optimizer for sending email messages.

Click **Delete**.

![Journey Optimizer](./images/23.2-6.png)

Confirm the Delete action by clicking a second time on that button.

![Journey Optimizer](./images/23.2-7.png)

You now need to replace this action by a **Message** action. In the left menu, find the **Actions** section and drag and drop a **Message** action in the circle which is now empty in your journey.

![Journey Optimizer](./images/23.2-8.png)

Link the rest of your journey to the outbound transition of the **Message** activity that you just drag and drop. 

![Journey Optimizer](./images/23.2-9.png)

Click on the **Message** activity to display the menu on the right side. Click **Select a message**.

![Journey Optimizer](./images/23.2-10.png)

Enter your **ldap** to see your messages.

![Journey Optimizer](./images/23.2-12.png)

Select the new message you created in the previous exercise, which is named **ldap - Registration Email**. Click **Select**.

![Journey Optimizer](./images/23.2-13.png)

You'll then see this. Click **Ok**.

![Journey Optimizer](./images/23.2-14.png)

Your updated Account Creation Journey is now ready to be published. Click **Publish**.

![Journey Optimizer](./images/23.2-15.png)

Click **Publish** again.

![Journey Optimizer](./images/23.2-16.png)

Your Account Creation Journey has now been successfully updated and from now on will deliver the account registration email using a Journey Optimizer message.

![Journey Optimizer](./images/jourpub.png)

## 23.2.2 Configure/Verify Test Profile creation

In the next exercise, you'll test your trigger-based journey and to do so, you'll create a new profile in Adobe Experience Platform.
In order to test and preview messages built in Journey Optimizer, you need to mark that profile as a **Test Profile**. As you can see, marking a profile as Test Profile has been facilitated by adding a checkbox on the **Create Account** screen of the demo website. When you check that checkbox, Adobe Experience Platform will mark a profile as Test Profile.

![Journey Optimizer](./images/test1.png)

To make this work, you need to verify the setup of your Adobe Experience Platform Data Collection Client property, and more specifically, the **All Authenticated Pages** rule. Click **Custom Code**.

![Journey Optimizer](./images/test2.png)

You'll see this. Click **Open Editor**.

![Journey Optimizer](./images/test3.png)

You'll then see this.

![Journey Optimizer](./images/test4.png)

Scroll down to line 24, you should have this line of code there. If you don't have it, copy the below line of code and paste it on line 24 as indicated.

`"testProfile": Boolean(localStorage.getItem("testProfile")),`

![Journey Optimizer](./images/test5.png)

Scroll down to line 59, you should have this line of code there. If you don't have it, copy the below line of code and paste it on line 59 as indicated.

`"brandLogo": _satellite.getVar('brandLogo'),`

![Journey Optimizer](./images/test6.png)

Click **Save** followed by clicking **Keep Changes** and then click **Save** again.

Don't forget to publish the changes by going to **Publishing Flow**, adding the changes to your **Development** library and then click **Save & Build to Development**.

## 23.2.3 Test your trigger-based journey

Let's test the updated journey by creating a new account on the demo website.

Open a new, clean incognito browser window and go to [https://public.aepdemo.net](https://public.aepdemo.net). 

You'll then see this. 

![Launch Setup](./images/cdemo1.png)

Enter your Configuration ID and click **Load Configuration**. Your configuration is then loaded.

![Launch Setup](./images/cdemo2.png)

Scroll down and click **Save Configuration**.

![Launch Setup](./images/cdemo3.png)

You'll then be redirected to the Admin homepage. Go to **Select LDAP**. Select your LDAP and click **Save**.

![Launch Setup](./images/cdemo5.png)

You'll then be redirected to the Admin homepage. Go to **Select Brand** and select the brand **Luma**, click **Save**.

![Launch Setup](./images/cdemo7.png)

You'll then be redirected to the Admin homepage. Click the **Luma** logo.

![Launch Setup](./images/cdemo8.png)

You'll then see the Luma homepage.

![Launch Setup](./images/cdemo9.png)

Go to **Login/Register**. Fill out the form and click **Create Account**. Don't forget to check the checkbox for **Test Profile**.

![Journey Optimizer](./images/23.2-18.png)

Within a few seconds you'll receive the new Account Creation email served by Journey Optimizer in your inbox.

![Journey Optimizer](./images/23.2-17.png)

You'll also notice that when you change brands on the demo website, that the brand logo and brand name in the email will also dynamically change:

![Journey Optimizer](./images/testemail2.png)

You have finished this exercise.

Next Step: [23.3 Configure a trigger-based journey - Order Confirmation](./ex3.md)

[Go Back to Module 23](./journeyoptimizer.md)

[Go Back to All Modules](../../overview.md)
