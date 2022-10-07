---
title: Real-time CDP - Build a segment and take action - Configure an Advertising Destination like Google DV360
description: Real-time CDP - Build a segment and take action - Configure an Advertising Destination like Google DV360
kt: 5342
audience: Data Architect, Orchestration Engineer, Marketer
doc-type: tutorial
activity: develop
exl-id: 4ca8f6da-2252-4b29-8e05-8f3b8d7b5781
---
# 11.2 Configure an Advertising Destination like Google DV360

>[!IMPORTANT]
>
>The below content is intended as FYI - You do **NOT** have to configure a new destination for DV360. The destination has already been created and you can use it in the next exercise.

Log in to [Adobe Experience Platform](https://experience.adobe.com/platform).

After logging in, you'll land on the homepage of Adobe Experience Platform.

![Data Ingestion](./images/home.png)

Before you continue, you need to select a **sandbox**. The sandbox to select is named ``--aepSandboxId--``. You can do this by clicking the text **[!UICONTROL Production Prod]** in the blue line on top of your screen.

![Data Ingestion](./images/sb1.png)

After selecting the appropriate sandbox, you'll see the screen change and now you're in your dedicated sandbox.

![Data Ingestion](./images/sb2.png)

In the left menu, go to **Destinations**, then go to **Catalog**. You'll then see the **Destinations Catalog**.

![RTCDP](./images/rtcdp.png)

In **Destinations**, click on **Google Display & Video 360** and then click **+ Configure**.

![RTCDP](./images/rtcdpgoogle.png)

You'll then see this. Click the data icon.

![RTCDP](./images/rtcdpgooglecreate1.png)

Click **Configure new destination**.

![RTCDP](./images/rtcdpgooglecreate2.png)

In the next screen, you'll see the Self-Service UI to configure your destination to Google DV360.

![RTCDP](./images/rtcdpgooglecreatedest.png)

Enter a value in the fields **Name** and **Description**.

The field **Account ID** is the **Advertiser ID** of the DV360 Account. You can find that here:

![RTCDP](./images/rtcdpgoogledv360advid.png)

The **Account Type** should be set to **Invite Advertiser**.

Now you have this. Click **Next**.

![RTCDP](./images/rtcdpgoogldv360new.png)

>[!NOTE]
>
>Google needs to allow-list Adobe in order for Adobe Experience Platform to send data to Google DV360. Contact your Google Account Manager to enable this dataflow.

After creating the destination, you'll see this. You can optionally select a data governance policy. Next, click **Create**.

![RTCDP](./images/rtcdpcreatedest1.png)

You'll then see a list of available destinations. 
In the next exercise, you'll connect the segment you built in the previous to the Google DV360 destination.

Next Step: [11.3 Take Action: send your segment to DV360](./ex3.md)

[Go Back to Module 11](./real-time-cdp-build-a-segment-take-action.md)

[Go Back to All Modules](../../overview.md)
