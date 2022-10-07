---
title: Data Ingestion using Google Tag Manager and Google Analytics - Setup Google Analytics & link it to GTM
description: Data Ingestion using Google Tag Manager and Google Analytics - Setup Google Analytics & link it to GTM
kt: 5342
audience: Data Engineer, Data Architect
doc-type: tutorial
activity: develop
exl-id: 5fb87cab-b7b3-4945-8dd0-9d85b6a99979
---
# 9.2 Setup Google Analytics & link it to GTM

Go to [https://analytics.google.com/](https://analytics.google.com/) and login with your Google Account.

If this is the first time you do this, your screen will look like this.

![Google Analytics setup](./images/ga1-blank.png)

Click on **Start measuring**.

![Google Analytics setup](./images/ga1-blank-start.png)

You'll need to fill in some Account details about the website you want to analyze. Please use **Demo System - ldap**, and leave the fields checked, unless you have a specific reason to uncheck them.

![Google Analytics setup](./images/ga2-accountdetails.png)

Click **Next** to proceed to **Property setup**.

![Google Analytics setup](./images/ga3-next.png)

Give your property a name. Please use **Demo System - ldap**.  If you wish you can change the timezone and currency to reflect where you are based.

![Google Analytics setup](./images/ga4-property.png)

Click **Next** to proceed to **About your business**.

![Google Analytics setup](./images/ga3-next.png)

Select anything you wish in this page.

![Google Analytic setup](./images/ga4-aboutbusiness.png)

Click **Create**.

![Google Analytics setup](./images/ga4-create.png)

The Google Analytics Terms of Service Agreement pops up.  Select the country where you are based. 

![Google Analytics setup](./images/ga4-acceptagreement.png)

Accept the terms by clicking the checkboxes and clicking **I accept**.

![Google Analytics setup](./images/ga4-create-accepttci.png)

You are now brought to the **Data Streams** section within **Admin**. This is where you can detail what you want to measure.

![Google Analytics setup](./images/ga4-datastream.png)

Select **Web**.


Provide the website URL of **www.aepdemo.net**, and the Steam Name of **Demo System - ldap**.

![Google Analytics setup](./images/ga4-setupdatastream.png)


Click **Create stream**.

![Google Analytics setup](./images/ga4-createstream.png)

You'll now see the details of the data stream you have just created.

![Google Analytics setup](./images/ga4-webstreamdetails.png)

You need to copy the **Measurement ID**. This value can be used by Google Tag Manager to manage the Google Analytics tags.

![Google Analytics setup](./images/ga4-measurementid.png)

So let's go back to GTM to store the Measurement ID there.

Go to [https://tagmanager.google.com/](https://tagmanager.google.com/) by following the URL or by clicking the **Product Switcher** item at the top right of the screen.

![Google Analytics setup](./images/ga10-switchproducts.png)

Next choose Tag Manager at the bottom of the list.

![Google Analytics setup](./images/ga11-gtm.png)

You might need to login again, then choose the container in GTM for **www.aepdemo.net**.

![Google Analytics setup](./images/ga12-gtmstart.png)

You are now on the overview page of GTM where nothing has been added yet.

![Google Analytics setup](./images/ga12-gtmoverviewsstart.png)

If you're familiar to Adobe Launch you use **Extensions**, **Data elements** and **Rules**. In GTM you use in more or less the same way **Tags**, **Variables** and **Triggers**.
We're going to create a **Tag** for Google Analytics, then a **Trigger** when to fire the Google Analytics tag.

Create the tag by clicking **New Tag**.

![Google Analytics setup](./images/ganewtag.png)

You'll then see this screen:

![Google Analytics setup](./images/ga13-gtmnewtagempty.png)

Give this tag a name by changing **Untitled Tag** into **Universal Analytics**:

| Form field                | Value               |
|:-------------------------------------------| :------------------ |
|Tag Name|Google Analytics 4|

Then press **Tag Configuration**, where you can choose from a list of available tags.

![Google Analytics setup](./images/ga14-choosetag1.png)

Choose **Google Analytics: GA4 Configuration**. You'll then see this screen:

![Google Analytics setup](./images/ga14-choosetag2.png)

This selection gives you a next screen where you can enter as a Measurement ID the one you copied earlier from Google Analytics.

You now need to choose at least one trigger which tells GTM where this tag will fire. Later we will add additional triggers. But for now we will tell it to fire on each page view. Click the **Triggering** element in your screen.

![Google Analytics setup](./images/ga15-yourtrackingid.png)

You will see the following screen with one trigger that you can choose called **All Pages**. Later we will define new triggers for specific pages. 

![Google Analytics setup](./images/ga15-choosetrigger.png)

Click **All Pages**.

You are brought back to the main screen with your tag configuration displayed.

![Google Analytics setup](./images/ga15-tagconfig.png)

Click **Save** to proceed.

![Google Analytics setup](./images/gasave.png)

You are now again on the overview page, but here you see that there is one change to be published in the workflow.

![Google Analytics setup](./images/ga15-gtmoverview.png)

Click **Submit**.

![Google Analytics setup](./images/gasubmit.png)

First you see this screen where you can fill in descriptive information about the change you're going to publish. Add a short description and a more describing one.

![Google Analytics setup](./images/ga17-publish2.png)

Now click **Publish**.

![Google Analytics setup](./images/gapublish.png)

You're then seeing the versions tab in GTM, showing you the summary of what you just published. This will not be active yet, since we have not yet implemented the GTM tag on the Platform Demo website. We'll be doing that in a later exercise.

![Google Analytics setup](./images/ga-publish3.png)

From here you can click back to the **Workspace** tab, where you can add more Tags, Triggers and Variables, which we'll be doing in the next Exercise.

![Google Analytics setup](./images/gaworkspace.png)

Next Step: [9.3 Configure GTM Variables](./ex3.md)

[Go Back to Module 9](./data-ingestion-using-google-tag-manager-and-google-analytics.md)

[Go Back to All Modules](../../overview.md)
