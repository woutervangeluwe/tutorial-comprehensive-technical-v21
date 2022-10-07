---
title: Adobe Journey Optimizer - Setup and use push notifications for iOS
description: Setup and use push notifications for iOS
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
exl-id: 4e840ab2-fae8-4b34-91fa-bbdbfcc9c8cd
---
# 23.6 Setup and use push notifications for iOS

## 23.6.1 Retrieve Dataset IDs for Journey Optimizer Push Messaging

Login to Adobe Experience Cloud by going to [Adobe Experience Cloud](https://experience.adobe.com). Click **Adobe Journey Optimizer**.

![ACOP](./images/23.1-1.png)

You'll be redirected to the **Home** view in Journey Optimizer.

![ACOP](./images/23.1-3.png)

Before you continue, you need to select a **sandbox**. The sandbox to select is named ``--aepSandboxId--``. You can do this by clicking the text **[!UICONTROL Production Prod]** in the blue line on top of your screen.

![ACOP](./images/23.1-3a.png)

In Journey Optimizer, click on **[!UICONTROL Datasets]** in the menu on the left side of your screen.

![Data Ingestion](./images/menudsjo.png)

### Journey Optimizer Push Profile Dataset

Next, you need to retrieve the dataset ID of the dataset named **Journey Optimizer Push Profile Dataset**. Select that dataset in the list of datasets to see the dataset ID.

![Data Ingestion](./images/menudsexists.png)

Write down the Dataset ID, as you'll need it in a next exercise. The Dataset ID for the Journey Optimizer Push Profile Dataset in this example is **601c407f82be44194a3c5c54**.

### Journey Optimizer Push Tracking Experience Event Dataset

Next, you need to retrieve the dataset ID of the dataset named **Journey Optimizer Push Tracking Experience Event Dataset**. Select that dataset in the list of datasets to see the dataset ID.

![Data Ingestion](./images/ds2exists.png)

Write down the Dataset ID, as you'll need it in a next exercise. The Dataset ID for the Journey Optimizer Push Tracking Experience Event Dataset in this example is **601c407d9d7e98194b61d352**.

## 23.6.2 Create Data Inlet for Journey Optimizer Push Messaging

In Adobe Experience Platform, click on **[!UICONTROL Sources]** in the menu on the left side of your screen.

![Data Ingestion](./images/menusources.png)

In the Sources Catalog, scroll down until you see the Source Connector for **HTTP API** and click **Add data**.

![Data Ingestion](./images/src1.png)

Next, select **New Account** and fill out the details as follows:

- Account Name: **ldap - HTTP API Inlet** (replace ldap by your ldap)

Check the checkbox for **XDM compatible**.

Click **Connect to source**.

![Data Ingestion](./images/src2.png)

You'll then quickly see a confirmation message **Connected**. Click **Next**.

![Data Ingestion](./images/src3.png)

Under **Target dataset**, select **Existing dataset** and browse to find the dataset **Journey Optimizer Push Profile Dataset**. You'll then have this.

Click **Next**.

![Data Ingestion](./images/src4.png)

Give your flow a name like this: **ldap - Journey Optimizer Push Inlet Flow**. Click **Next**.

![Data Ingestion](./images/src5.png)

Click **Finish**.

![Data Ingestion](./images/src6.png)

Your HTTP API connector is now created. You need to write down the **Streaming endpoint URL** as you'll need it in a next exercise. The URL in this example is **https://dcs.adobedc.net/collection/105495ebb6e9c98a2d010ddb51599c7f942edd4f1724deb779ec81bbcdd6fd2f**.

![Data Ingestion](./images/src7.png)

You can now continue setting up your Datastream and Adobe Experience Platform Data Collection Client property.

## 23.6.3 Create Datastream for Mobile

Go to [https://experience.adobe.com/#/data-collection/](https://experience.adobe.com/#/data-collection/). 

Open the dropdown menu and click **[!UICONTROL Datastream]**.

![Click Datastream icon in the left navigation](./images/edgeconfig1a.png)

Click **[!UICONTROL New Datastream]**.

![Click Datastream icon in the left navigation](./images/edgeconfig1.png)

For the **[!UICONTROL Friendly Name]**, and for the optional description, enter **ldap - Demo System Datastream (Mobile)** and replace **ldap** with your ldap.
Click the **[!UICONTROL Save]** button.

![Name the Datastream and save](./images/edgeconfig2.png)

You'll then see this:

![Name the Datastream and save](./images/edgeconfig3.png)

Toggle on **[!UICONTROL Adobe Experience Platform]** which will expose additional fields. You'll then see this:

![Name the Datastream Configuration and save](./images/edgeconfig4.png)

For **[!UICONTROL Sandbox]**, select your sandbox name.

>[!NOTE]
>
> You can find your IMS Org ID, Org Name and your Adobe Experience Platform sandbox name on your company's github repository that was set up by your Adobe contact. If you don't know which sandbox to use, verify if you can see a sandbox named **AEP Enablement FY21**. If you can see that sandbox, please select it.

![Name the Datastream Configuration and save](./images/edgeconfig5.png)

For Event Dataset, select **Demo System - Event Dataset for Mobile App (Global v1.1)** and for Profile Dataset, select **Demo System - Profile Dataset for Mobile App (Global v1.1)**. Click **Save**.

![Name the Datastream Configuration and save](./images/edgeconfig7.png)

You'll then see that your Datastream consists of 3 environments.

![Name the Datastream Configuration and save](./images/edgeconfig9.png)

Your Datastream is now ready to be used in your Adobe Experience Platform Data Collection Client property for Mobile.

## 23.6.4 Create a new Adobe Experience Platform Data Collection Client property for Mobile

Go to [https://experience.adobe.com/#/data-collection/](https://experience.adobe.com/#/data-collection/). After completing previous modules, you already have two Adobe Experience Platform Data Collection Client properties: one for web and one for mobile.

![DSN](./images/launchprop.png)

You've been using these Adobe Experience Platform Data Collection Client properties already as part of previous modules. In this module, you'll create a new Adobe Experience Platform Data Collection Client property for Mobile which will be compatible with the new AEP SDKs for Edge, Messaging and Assurance (Griffon).

Click **New Property** to create a new Adobe Experience Platform Data Collection Client property.

![Adobe Experience Platform Data Collection](./images/launchprop1.png)

As a name, use **ldap - Demo System (DD/MM/YYYY) (mobile - Edge)** and select the **Platform**: **Mobile**. Click **Save**.

![Adobe Experience Platform Data Collection](./images/launchprop2.png)

Open your newly created Adobe Experience Platform Data Collection Client property.

![Adobe Experience Platform Data Collection](./images/launchprop3.png)

Go to **Extensions**. You'll see that the extensions **Mobile Core** and **Profile** are already installed.

![Adobe Experience Platform Data Collection](./images/launchprop4.png)

Go to **Catalog** and click **Install** on the extension **Adobe Experience Platform Edge Network**.

![Adobe Experience Platform Data Collection](./images/launchprop5.png)

You'll then see this. 

![Adobe Experience Platform Data Collection](./images/launchprop6.png)

Open the dropdown and select the Datastream you created in one of the previous exercises. Click **Save**.

>[!NOTE]
>
> Due to a bug in Adobe Experience Platform Data Collection, only the first 100 Datastreams are shown in the dropdown list. You'll need to rename your Datastream to start with an `A` or a `0` so that it is shown in the list.

![Adobe Experience Platform Data Collection](./images/launchprop7.png)

You'll then be back back here. Go to **Catalog** again.

![Adobe Experience Platform Data Collection](./images/launchprop8.png)

Search for the extension **AEP Assurance** and click **Install**.

![Adobe Experience Platform Data Collection](./images/launchprop9.png)

>[!NOTE]
>
> AEP Assurance helps you inspect, proof, simulate, and validate how you collect data or serve experiences in your mobile app. You can read more about AEP Assurance and Project Griffon here [https://aep-sdks.gitbook.io/docs/beta/project-griffon](https://aep-sdks.gitbook.io/docs/beta/project-griffon).

There's nothing specific to configure in the **AEP Assurance** extension, so you'll be back at the extension view directly.

![Adobe Experience Platform Data Collection](./images/launchprop10.png)

Go to **Publishing Flow** and click **Add New Library**.

![Adobe Experience Platform Data Collection](./images/launchprop11.png)

Give your Library a name, select the Environment: **Development**, click **Add All Changed Resources** and then click **Save & Build to Development**.

![Adobe Experience Platform Data Collection](./images/launchprop12.png)

Your library then starts building, and should be built within a couple of seconds.

![Adobe Experience Platform Data Collection](./images/launchprop13.png)

Go to **Environments** and click the **Install** icon for your **Development** environment.

![Adobe Experience Platform Data Collection](./images/launchprop14.png)

You'll then see this. Click the **copy** icon next to your **Environment File ID**.

![Adobe Experience Platform Data Collection](./images/launchprop15.png)

Your Environment File ID looks like this: **b754ed1bed61/7712c63caf43/launch-2914570360f6-development**.

You'll need to use this in the next step, to update your iOS app.

## 23.6.5 Update your Configuration ID

Open an incognito browser window and go to [https://public.aepdemo.net/admin_configuration_update.html](https://public.aepdemo.net/admin_configuration_update.html).

You'll see the **Update Configuration ID** page. Enter your personal Configuration ID and click **Load Configuration**.

![DSN](./images/confighome.png)

You now see your own personal Configuration ID and its current settings. The goal of this exercise is to update the **Launch Mobile App Tag URL** by the **Environment File ID** you created in the previous exercise.

![DSN](./images/confighome1launch.png)

Replace the current value by the new value.

![DSN](./images/confighome2launch.png)

Scroll down until you see the fields for **Messaging Inlet ID**, **Messaging Use APNSSandbox**, **Messaging Profile Dataset ID**, **Messaging Event Dataset ID**.

You need to update these fields using the variables you collected in the previous exercises.

- **Messaging Inlet ID** is the URL of the HTTP API Source Connector you created in exercise 23.5.2, which looks like this: **https://dcs.adobedc.net/collection/cfd54050618a515dc1f7320ae39afd082ec8e8bf0e94abd9ac3ea805fdb07378**
- **Messaging Use APNSSandbox** should be set to **false**
- **Messaging Profile Dataset ID** is the dataset ID of the dataset named **Journey Optimizer Push Profile Dataset**, which you retrieved in exercise 23.5.1
- **Messaging Event Dataset ID** is the dataset ID of the dataset named **Journey Optimizer Push Tracking Experience Event Dataset**, which you retrieved in exercise 23.5.1

![DSN](./images/confighome3launch.png)

Scroll down and click **Update Configuration ID**.

![DSN](./images/confighome3.png)

Your Configuration ID has now been updated.

Whichever option you choose, once you've made the change, you can test your setup with the iOS app.

## 23.6.6 Configure your iOS app

The mobile application that is used in the context of this demo and enablement environment is only available for **iOS**.

Take your **iOS** device, open the **AppStore** and search for **Platform - Edge**. Click the **DOWNLOAD/INSTALL** button.

![DSN](./images/mobileapp1.png)

Next, click **OPEN**.

![DSN](./images/mobileapp1a.png)

You'll now see this screen. You can either manually enter the **Configuration ID** you created, or else, you can click the **QR code scan** icon to scan a QR code.

![DSN](./images/mobileapp8.png)

On the Admin homepage of your demo website, you'll find a QR code you can scan. 

![DSN](./images/adminhomeqr.png)

After clicking the **QR code scan** in the app, you'll see this. Click **OK** to scan a QR code.

![DSN](./images/mobileapp9.png)

After scanning the QR code, you'll be back in this screen, with the Configuration ID filled out for you. Click **Load Configuration**.

![DSN](./images/mobileapp10.png)

You'll then see a confirmation of which environment you'll be loading. Click **Save Configuration**.

![DSN](./images/mobileapp11.png)

After a couple of seconds, you'll be presented with the **Select LDAP** screen. Select your LDAP and click **Save**.

![DSN](./images/mobileapp12.png)

After a couple of seconds, you'll see that the demo brand **Luma** is being loaded automatically.

![DSN](./images/mobileapp13.png)

And finally, you'll see the Luma homepage in the app.

![DSN](./images/mobileapp14a.png)

Kill the app by swiping the app up, and swiping it up completely so that the app is killed.

![DSN](./images/griffon2.png)

>[!NOTE]
>
> After restarting the app, you'll be asked to accept up to 3 permission prompts. Accept those prompts by clicking **OK**, **Allow while using the app** or **Allow** as they are required by the app.

![DSN](./images/prompt1.png)
![DSN](./images/prompt2.png)
![DSN](./images/prompt3.png)

Open the app again.

On the homepage of the app, click the **...** button in the top. left corner. Then select AEP Assurance.

![Adobe Experience Platform Data Collection](./images/ipadPushTest7.png)

You'll then see this:

![Adobe Experience Platform Data Collection](./images/ipadPushTest8.png)

You now need to scan a QR code to connect your iOS device to your AEP Assurance session. 

To start an AEP Assurance session, go to [https://experience.adobe.com/#/@experienceplatform/griffon](https://experience.adobe.com/#/@experienceplatform/griffon). Click **Create Session**.

![Adobe Experience Platform Data Collection](./images/griffon3.png)

Click **Start**.

![Adobe Experience Platform Data Collection](./images/griffon4.png)

Fill out the values:

- Session Name: use **ldap - iOS & Push debugging** and replace ldap by your ldap
- Base URL: use **com.adobe.platform.edge://default**

Click **Next**.

![Adobe Experience Platform Data Collection](./images/griffon5.png)

You'll then see a QR code on your screen, which you should scan with your iOS device.

![Adobe Experience Platform Data Collection](./images/griffon6.png)

On your iOS device, click the **QR Code** icon and scan the QR code that is displayed by AEP Assurance.

![Adobe Experience Platform Data Collection](./images/ipadPushTest8a.png)

After scanning the QR code, you'll see that the AEP Assurance session URL is displayed on your iOS device. Click **Start AEP Assurance**.

![Adobe Experience Platform Data Collection](./images/ipadPushTest9.png)

You'll then see a popup screen, asking you to enter the PIN-code. Copy the PIN-code from your AEP Assurance screen and click **Connect**.

![Adobe Experience Platform Data Collection](./images/ipadPushTest11.png)

You'll then be connected from your iPad or iPhone to the AEP Assurance session.

![Adobe Experience Platform Data Collection](./images/griffon7.png)

Kill the app by swiping the app up, and swiping it up completely so that the app is killed.

![Adobe Experience Platform Data Collection](./images/griffon2.png)

When the iOS app stops, it'll disconnect from the AEP Assurance session.

![Adobe Experience Platform Data Collection](./images/griffon8.png)

When the iOS app starts again, you'll see that the app connects to AEP Assurance automatically, and you'll see a list of events being loaded immediately.

![Adobe Experience Platform Data Collection](./images/griffon9.png)

>[!NOTE]
>
> If you don't see the options **Data Elements**, **Shared States**, **ConfigurationViewer**, **Push Debug** in the left menu then please add them by clicking the **Configure** button. Next, click the **+** icon as indicated below, followed by **Save**.

![Adobe Experience Platform Data Collection](./images/griffon10.png)

Go to **Push Debug**. You'll see something like this.

Some explanation:

- The first column, **Client**, shows the available identifiers on your iOS device. You'll see an ECID and a Push Token.
- The second column shows **Profile** information, with additional info on what platform the Push Token lives in (APNS or APNSSandbox). If you click the **Inspect Profile** button, you'll be taken to Adobe Experience Platform and you'll see the full Real-time Customer Profile.
- The 3rd column shows the **App Configuration**, which was set up as part of exercise **23.5.4 Create App Configuration in Launch**

![Adobe Experience Platform Data Collection](./images/griffon11.png)

To test your Push configuration setup, click the **Send Push Notification** button. 

You need to make sure that the **Platform** app isn't open at the time of clicking the  **Send Push Notification** button, because if the app is open, the Push Notification might be received in the background and wouldn't be visible.

![Adobe Experience Platform Data Collection](./images/ipadPush1.png)

You'll then see a Push Notification like this one appear on your iOS device.

>[!NOTE]
>
>The timestamp in the push notification that you'll receive will show the UTC/GMT time which might be different from your current time. This is normal and expected, and the difference in time will be equal to the difference in timezone between where you are, and what the current UTC/GMT time is.

![Adobe Experience Platform Data Collection](./images/ipadPush2.png)

If you've received the Push Notification, that means that your setup is correct and working fine.

## 23.6.7 Create a push message

To configure a Push message, go to Journey Optimizer.

![Push](./images/bp1.png)

Make sure to select your sandbox, which should be `--aepTenantId--`.

![Push](./images/ssb1.png)

Go to **Messages**. Click **Create Message**.

![Push](./images/bp2.png)

In the **Preset** dropdown, select the Preset you'd like to use. In this case, the preset named **CJM Alpha Preset for Mobile (APNS)** is the one to select. 

![Push](./images/bp3.png)

Fill out the name using this convention: **ldap - Welcome to store**.

Don't forget to check the checkbox for **Push Notification**. Click **Create**.

![Push](./images/bp4.png)

You'll then see this. Click the **pencil** icon for the **Title** field.

![Push](./images/bp5.png)

You'll then see this. You can now select any Profile attribute from the Real-time Customer Profile directly.

![Push](./images/bp6.png)

Scroll down until you see **Person**. Click the **arrow** to go a level deeper.

![Push](./images/bp7.png)

Click the **arrow** next to **Full Name**.

![Push](./images/bp8.png)

Finally, click the **+** icon next to the field **First Name**. You'll then see the personalization token for First Name being added: **{{profile.person.name.firstName}}**.

![Push](./images/bp9.png)

Next, add the text **, welcome to our store!** behind **{{profile.person.name.firstName}}**.

Click **Save**.

![Push](./images/bp10.png)

You now have this. Click the **pencil** icon for the **Body** field.

![Push](./images/bp11.png)

Enter this text **Click here to get a 10% discount when you buy today!** and click **Save**.

![Push](./images/bp12.png)

Your Push message is now ready. Click **Publish** to publish your message.

![Push](./images/bp13.png)

Click **Publish** again.

![Push](./images/bp14.png)

Your message is now ready and can be used in a journey.

![Push](./images/bp15.png)

## 23.6.8 Create a new event

In the menu, go to **Journey Administration** and click **Manage** under **Events**.

![ACOP](./images/acopmenu.png)

On the **Events** screen, you'll see a view similar to this. Click **Create Event**.

![ACOP](./images/add.png)

You'll then see an empty event configuration.

![ACOP](./images/emptyevent.png)

First of all, give your Event a Name like this: `ldapStoreEntryEvent` and replace `ldap` with your ldap.

![ACOP](./images/eventname.png)

Next, add a description like this `Store Entry Event`.

![ACOP](./images/eventdescription.png)

Next is the **Event Type** selection. Select **Unitary**.

![ACOP](./images/eventidtype1.png)

Next is the **Event ID Type** selection. Select **System Generated**

![ACOP](./images/eventidtype.png)

Next is the Schema selection. A schema was prepared for this exercise. Please use the schema `Demo System - Event Schema for Mobile App (Global v1.1) v.1`.

![ACOP](./images/eventschema.png)

After selecting the Schema, you'll see a number of fields being selected in the **Payload** section. Your event is now fully configured.

![ACOP](./images/eventpayload.png)

You should then see this. Click **Save**.

![ACOP](./images/eventsave.png)

Your Event is now configured and saved. Click on your event again to open up the **Edit Event** screen again.

![ACOP](./images/eventdone.png)

Hover over the **Payload** field again to see the 3 icons again.

![ACOP](./images/hover.png)

Click on the **View Payload** icon. You'll now see an example of the expected payload.

![ACOP](./images/fullpayload.png)

Your Event has a unique orchestration eventID, which you can find by scrolling down in that payload until you see `_experience.campaign.orchestration.eventID`.

![ACOP](./images/payloadeventID.png)

The event ID is what needs to be sent to Adobe Experience Platform in order to trigger the Journey that you'll build in the next step. Write down this eventID, as you'll need it in the next step.
`"eventID": "ff88e8f5d9405230327afb1a81275996a6e01948059b8109c49fd19ccc01722a"`

Click **Ok**, followed by **Cancel**.

In order to use your event for the test and demo at the end of this exercise, you need to enter your Store Entry Event ID into your Configuration ID.

To do that, open an incognito browser window and go to [https://public.aepdemo.net/admin_configuration_update.html](https://public.aepdemo.net/admin_configuration_update.html).

You'll see the **Update Configuration ID** page. Enter your personal Configuration ID and click **Load Configuration**.

![DSN](./images/confighome.png)

You now see your own personal Configuration ID and its current settings. The goal of this exercise is to update the field **EventID - Beacon** with the **Event ID** you just created. Scroll down to find the field **EventID - Beacon**.

![DSN](./images/confighome1.png)

Replace the current value by the new value.

![DSN](./images/confighome2.png)

Scroll down and click **Update Configuration ID**.

![DSN](./images/confighome3.png)

Your Configuration ID has now been updated.

## 23.6.9 Use your event and push message in a journey

In the menu, go to **Journeys** and click **Create Journey**.

![DSN](./images/sjourney1.png)

You'll then see this.

![DSN](./images/sjourney2.png)

Give your journey a name. Use **ldap - Store Entry journey** and replace **ldap** by your ldap. Click **OK**.

![DSN](./images/sjourney3.png)

First, you need to add your event as the starting point of your journey. Search for your event **ldapStoreEntryEvent** and drag and drop it onto the canvas. CLick **OK**.

![DSN](./images/sjourney4.png)

Next, under **Actions**, search for the **Message** action.

![DSN](./images/sjourney5.png)

Drag and drop the **Message** action onto the canvas and click the **edit** icon to select your message.

![DSN](./images/sjourney6.png)

Select the push message you created in the previous step. Click **Select**.

![DSN](./images/sjourney7.png)

You then have this. Click **OK**.

![DSN](./images/sjourney8.png)

Search for the orchestration type **End** and drag and drop it onto the canvas. Click **OK**.

![DSN](./images/sjourney9.png)

Click **Publish** twice.

![DSN](./images/sjourney10.png)

Your journey is now published.

![DSN](./images/sjourney11.png)

## 23.6.10 Test your journey and push message

To test your journey using the mobile app, you first need to delete the app, reinstall it and load your configuration ID again. This is to ensure that your changes to your configuration ID will be loaded in the app.

![DSN](./images/demo1.png)

Follow the steps described in exercise 23.5.6 to install the app again and load your Configuration ID.

![DSN](./images/mobileapp14a.png)

Login into the app with an account you created on the website.

![DSN](./images/demo1a.png)

Make sure your profile is showing into the app.

![DSN](./images/demo1b.png)

Go back to the app's homepage.

Once you're back at the app's home screen, click the **bluetooth** icon in the upper left corner. Clicking this icon will generate an experience event to Edge and Adobe Experience Platform which contains your event's EventID. This will kick off your journey, and you should receive a push message within seconds.

![DSN](./images/demo2.png)

Make sure to close the app immediately after clicking the **bluetooth** icon, otherwise the push message won't be shown.

After a couple of seconds, you'll see the message appear.

![DSN](./images/demo3.png)

You have finished this exercise.

Next Step: [23.7 Create a business event journey](./ex7.md)

[Go Back to Module 23](./journeyoptimizer.md)

[Go Back to All Modules](../../overview.md)
