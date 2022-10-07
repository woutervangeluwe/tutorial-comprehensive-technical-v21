---
title: Connect Dynamics to Adobe Experience Platform via RTCDP and Journey Orchestration
description: Connect Dynamics to Adobe Experience Platform via RTCDP and Journey Orchestration
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
exl-id: ff5db388-6ae2-44ed-a30a-b5127e6cbd31
---
# 17.2 Connect Dynamics to Adobe Experience Platform via RTCDP and Journey Orchestration

## 17.2.1 Update the Contact Entity in Microsoft Dynamics 365

Login to your Microsoft Dynamics 365 account. The URL of your Microsoft Dynamics 365 account looks like this: https://**NAME**.**REGION**.dynamics.com, for instance, https://demosystemvangeluw101.crm4.dynamics.com.

You'll then see this. Click on **Dynamics 365 - custom**.

![iFrame](./images/azure21.png)

You'll then see this. Click the **gear** icon.

![iFrame](./images/azure22.png)

In the menu, click **Advanced Settings**.

![iFrame](./images/iframe-01.png)

A new browser tab will open. You'll see this.

![iFrame](./images/iframe-01a.png)

In the top menu, click **Settings**, then click **Customizations**.

![iFrame](./images/iframe-02.png)

Next, click **Customize the System**.

![iFrame](./images/iframe-03.png)

A new browser tab will open. In the left menu, click to expand **Entities**.

![iFrame](./images/iframe-04.png)

Scroll down to **Contact**. Click to expand **Contact**.

![iFrame](./images/iframe-04a.png)

Click **Forms**.

![iFrame](./images/iframe-05.png)

Click **Contact**.

![iFrame](./images/iframe-06.png)

A new browser tab will open to display the Contact Entity form fields.

![iFrame](./images/iframe-07.png)

In the panel **Contact Information** you'll add another field called **Sentiment**, right under the **Address** field.

Click **New Field**.

![iFrame](./images/newfield-01.png)

A new browser tab will appear.

![iFrame](./images/newfield-02.png)

Enter the following details:

- Display Name: **Sentiment**
- Data type: **Option Set**

You'll then have this:

![iFrame](./images/newfield-02a.png)

In the Options list, enter the below values. Click the green **+** icon.

| Label | Value |
|--- |--- |
| Neutral | 1 |
| Positive | 2 |
| Negative | 0 |

- Option: Neutral

  ![iFrame](./images/neutral.png)

  **NOTE** When entering a single digit into the Value field the following popup will appear. You can click OK to continue:

  ![iFrame](./images/newfield-031.png)

- Option: Positive

  ![iFrame](./images/positive.png)

  **NOTE** When entering a single digit into the Value field the following popup will appear. You can click OK to continue:

  ![iFrame](./images/newfield-031.png)

- Option: Negative

  ![iFrame](./images/negative.png)

  **NOTE** When entering a single digit into the Value field the following popup will appear. You can click OK to continue:

  ![iFrame](./images/newfield-031.png)

After adding the three option values, click **Save and Close**.

![iFrame](./images/newfield-04.png)

Go back to the Contact Entity Form. Click **Save**.

![iFrame](./images/newfield-04a.png)

Refresh the browser window.

After refreshing the browser window, go to the Field Explorer on the right and select **Custom Fields**.

You now see the new field called **Sentiment** in the list of Custom Fields.

![D365](./images/newfield-06.png)

Now drag your new field **Sentiment** from the Field Explorer window to below the **Address** field.

![D365](./images/newfield-addsentiment.gif)

Click **Save**.

![iFrame](./images/newfield-05.png)

This will take a few seconds and there will be no warning when completed.

Once your changes have been saved, click **Publish**.

![D365](./images/newfield-07.png)

This will take a few seconds. You will see the following message but there will be no warning when completed.

![D365](./images/newfield-08.png)

Once your changes have been published, you can now close this window.

You'll then be back here, close this window as well.

![D365](./images/newfield-09.png)

Return to your Microsoft Dynamics 365 dashboard.

In the left menu, click **Contact**. 

![D365](./images/cthome1.png)

You now see your list of Contacts. Instead of only showing **My Active Contacts**, change that to **All Contacts**.

![D365](./images/cthome2a.png)

You'll then have this. Click any contact to view the Contact record.

![D365](./images/cthome2.png)

You should see the new Sentiment field:

![D365](./images/newfield-incontact.png)

## 17.2.3 Create a Microsoft Dynamics 365 User that has permission to access the Azure Sync Contact App via external System

Adobe Experience Platform uses source connectors to synchronize data from systems such as Microsoft Dynamics 365. In the previous exercise we created an Azure application called SyncContact. As part of this we created permissions on this app, including a client secret. We need to create a user that can use this credential - such a user is called an **Application User**.

Return to your Microsoft Dynamics 365 dashboard. You'll then see this. Click the **gear** icon.

![iFrame](./images/azure22.png)

In the menu, click **Advanced Settings**.

![iFrame](./images/iframe-01.png)

A new browser tab will open. You'll see this.

![iFrame](./images/iframe-01a.png)

In the top menu, click **Settings**, then click **Security**.

![iFrame](./images/iframe-security.png)

You will see this. Click on **Users**.

![iFrame](./images/iframe-security-users.png)

You will be brought to this screen. You will need to change the view from **Enabled Users** to **Application Users**.

![iFrame](./images/iframe-security-enabledusers.png)

![iFrame](./images/iframe-security-applicationusers.png)

In this view - click **New**.

![iFrame](./images/iframe-security-applicationusers1.png)

If selector in the top left does not say **USER: APPLICATION USER** select this from the drop down.

![iFrame](./images/iframe-security-usersnew.png)

Enter your Application ID. This is the Application (Client) ID that you created in the previous exercise. This can be found on the overview screen of the SyncContact app you created and looks like this: **1dc2c2a1-ca26-4ab7-afa7-057acf441415**.

![iFrame](./images/appuserappid.png)

Click **Save**.

![iFrame](./images/iframe-security-usersnew2.png)

After clicking save, it'll take 1-2 minutes (don't close your window, just wait). You'll then see that several other fields are populated automatically.

![iFrame0](./images/iframe-security-usersnew3.png)

You must now assign a user role. Start by clicking **Manage Roles**.

![iFrame0](./images/iframe-security-roles.png)

Select appropriate roles for your user. In this case **System Administrator** has been selected.

![iFrame0](./images/iframe-security-roles1.png)

Click **OK**.  Wait for the role to be updated.

![iFrame0](./images/iframe-security-roles2.png)

Your user has now been set up, and you can close this window.

## 17.2.3 Connect Adobe Experience Platform to Microsoft Dynamics 365

Go to [Adobe Experience Platform](https://experience.adobe.com/platform/home).  Make sure you are in the correct sandbox.

![demo](./images/home.png)

In the left menu, go to Sources.

![demo](./images/sources1.png)

You'll then see the **Sources** homepage. In the **Sources** menu, click on **CRM**.

![demo](./images/sourceshome.png)

Click **Configure** on the **Microsoft Dynamics** card or click **Add Data** (which you see depends on whether you are the first to use this card). This will bring you to the Microsoft Dynamics account connection screen. Make sure the **New account** radio button is selected.

![Connect](./images/connect-newaccount.png)

Next, you have to enter your Microsoft Dynamics 365 details.

Enter your details like this:

| Key | Description| Example|
|--- |--- |--- |
| Account name | **ldap** Demo System Dynamics 365 Account | vangeluw Demo System Dynamics 365 Account | 
| Description | **ldap** Demo System Dynamics 365 Account | vangeluw Demo System Dynamics 365 Account | 
| Authentication type | How to connect to Dynamics | Service-principal and key authentication |
| serviceUri | https://**NAME**.**REGION**.dynamics.com/ | https://demosystemjoconnor1312.crm4.dynamics.com/| 
| Service principal ID | The Application (Client) ID that you created in the previous exercise. You can see this in the Overview screen for the SyncContact App | 7651719a-7f3e-4bc5-af8f-679ead1d2730 | 
| Service principal key | The Client secret value you created in the previous exercise | .Ycc20krN~k5dpCQFv6_Di4-HNQq.rjpt | 

After filling out all the fields, click **Connect to source**.

![Connect](./images/connect04.png)

Wait for the connection to be made. When successful you should see:

![Connect](./images/connect06.png)

Click **Next**.

![Connect](./images/connect-next.png)

You now see this. The next step is to select the data from Microsoft Dynamics 365.

![Connect](./images/connect08a.png)

From the list of **Table Names**, you need to select **Contact**. Given that the list of **Table Names** isn't sorted in an alphabetical way, the best way to find **Contact** is to use the search functionality of your browser and search for the word **Contact**.

![Connect](./images/connect07a.png)

Here's the table name you need. Select **Contact**, and after a couple of seconds you should see a preview of the table on the right side of your screen.

![Connect](./images/connect07.png)

Click **Next**.

![Connect](./images/connect-next.png)

You'll now see this. Next, you'll need to setup the mapping between the Microsoft Dynamics 365 fields and Adobe Experience Platform's Experience Data Model (XDM).

![Connect](./images/connect08.png)

For this exercise, a dataset has already been created. Click **Existing dataset**.

Next, click the **database** icon.

![Connect](./images/contact-existingdataset.png)

Search and select the **Demo System - Profile Dataset for Dynamics 365 (Global v1.1)** dataset.

![Connect](./images/contact-existingdataset-db.png)

Click **Confirm**.

![Connect](./images/connect-confirm.png)

You now need to map the fields in the Contacts Entity in Microsoft Dynamics 365 to the **AEP Demo - MSFT Dynamics Profile Schema** in Adobe Experience Platform.

First, click **Clear all mappings** as you don't need to map all the fields.

![Connect](./images/connect-clearmappings.png)

Next, you need to add the following seven fields from the **Contact** table and map then with the schema for your selected dataset.

For each of the required mappings, click the **Add new mapping** button.

![Connect](./images/connect-clearmappings1.png)

| Source Field | Target Field|
|--- |--- |
| contactid |`--aepTenantId--`.identification.core.d365|
| emailaddress1 |`--aepTenantId--`.identification.core.email|
| emailaddress1 |personalEmail.address|
| firstname |person.name.firstName|
| lastname |person.name.lastName|
| birthdate |person.birthDate|
| mobilephone |mobilePhone.number|
| new_sentiment |`--aepTenantId--`.individualScoring.sentiment|

Your final mapping should look like:

![Connect](./images/connect-mapping-list.png)

If your mapping looks like the above screenshot, click **Next**.

![Connect](./images/connect-next.png)

Next, you need to setup the **Scheduling**.

Define the following fields like this:

- Set **Frequency** to every 15 minutes.
- Make sure that **Backfill** is toggled on.
- Set **Load incremental data by** to **modifiedon**.

![Connect](./images/connect-modifiedon.png)

Click **Next**.

![Connect](./images/connect-next.png)

Now you will need to name your **Flow**.

Set the **Dataflow name** to: **ldap Dynamics Contact Dataflow**. For instance, in this example, the Dataflow Name is **vangeluw Dynamics Contact Dataflow**.

![Connect](./images/connect-dataset.png)

Click **Next**.

![Connect](./images/connect-next.png)

Review your configuration

![D365](./images/connect-review.png)

Click **Finish**.

![Connect](./images/connect-finish.png)

After clicking Finish, you'll see this:

![Connect](./images/connect-finish1.png)

Once you click on finish, it may take up to 15 minutes to ingest the data from Microsoft Dynamics 365 into the **Demo System - Profile Dataset for Dynamics 365** dataset in Adobe Experience Platform.

But, if you go to the **Dataflows** tab later, you should see something like this, to indicate success.

![Connect](./images/msdsourcesuccess.png)

And you can click through to see the batches of data that have been brought through the dataflow to the **Demo System - Profile Dataset for Dynamics 365 (Global v1.1)** dataset.

![Connect](./images/msd-dataset.png)

Next Step: [17.3 Create a Contact in Microsoft Dynamics 365 using Adobe Journey Optimizer & Import data from Microsoft Dynamics](./ex3.md)

[Go Back to Module 17](./adobe-experience-platform-microsoft-dynamics-365.md)

[Go Back to All Modules](./../../overview.md)
