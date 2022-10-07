---
title: Real-time CDP - Build a segment and take action - Send your segment to Adobe Target
description: Real-time CDP - Build a segment and take action - Send your segment to Adobe Target
kt: 5342
audience: Data Architect, Orchestration Engineer, Marketer
doc-type: tutorial
activity: develop
exl-id: 07b597dd-81f3-4241-a075-afed29ee5f45
---
# 11.5 Take Action: send your segment to Adobe Target

Log in to [Adobe Experience Platform](https://experience.adobe.com/platform).

After logging in, you'll land on the homepage of Adobe Experience Platform.

![Data Ingestion](./images/home.png)

Before you continue, you need to select a **sandbox**. The sandbox to select is named ``--aepSandboxId--``. You can do this by clicking the text **[!UICONTROL Production Prod]** in the blue line on top of your screen.

![Data Ingestion](./images/sb1.png)

After selecting the appropriate sandbox, you'll see the screen change and now you're in your dedicated sandbox.

![Data Ingestion](./images/sb2.png)


## 11.5.1 Verify your Datastream

The Adobe Target destination in Real-Time CDP is connected to the datastream that is used to ingest data into the Adobe edge network. If you want to setuo your Adobe Target destination, you first need to verify whether your datastream is already enabled for Adobe Target. Your datastram was configured in [Exercise 0.2 Create your Datastream](./../module0/ex2.md) and was named ``--demoProfileLdap--`` - Demo System Datastream.

Go to [https://experience.adobe.com/#/data-collection/](https://experience.adobe.com/#/data-collection/), then click **Datastreams**.

![Data Ingestion](./images/atdestds1.png)

in Datastreams, search for your datastream which is named ``--demoProfileLdap--`` - Demo System Datastream. Click your datastream to open it.

![Data Ingestion](./images/atdestds3.png)

Next, click the **Developement Environment** to open it.

![Data Ingestion](./images/atdestds4.png)

Scroll down to Adobe Target, enable the toggle for Adobe Target and fill out your Adobe Target client code. Click **Save**.

>[!NOTE]
>
> Adobe Target client code is an IMS Org-specific field. Please verify what your Adobe Target client code is and fill out the correct client code.

![Data Ingestion](./images/atdestds5.png)

Your datastream is now configured for Adobe Target.

## 11.5.2 Configure your Adobe Target destination

Adobe Target is available as a destination from Real-Time CDP. To setup your Adobe Target integration, go to **Destinations**, to **Catalog**.

![AT](./images/atdest1.png)

Click **Personalization** in the **Categories** menu. You'll then see the **Adobe Target** destination card. Click **Activate Segments**.

![AT](./images/atdest2.png)

Click **+ Configure new destination**.

![AT](./images/atdest3.png)

You'll then see this.

![AT](./images/atdest4.png)

In the **Configure new destination** screen, you need to configure two things:

- Name: use the name ``--demoProfileLdap--`` - Adobe Target (Web), which should look like this: **vangeluw - Adobe Target (Web)**.
- Datastream ID: you need to select the datastream that you configured in [Exercise 0.2 Create your Datastream](./../module0/ex2.md). The name of your datastream should be: ``--demoProfileLdap--`` - Demo System Datastream.

![AT](./images/atdest5.png)

Click **Next**.

In the next screen, you can optionally select a governance policy. It's not required to select one, in this case there's no need to select one, so click **Create**.

![AT](./images/atdest6.png)

Your destination is now created and will be shown in the list. Select your destination and click **Next** to start sending segments to your destination.

![AT](./images/atdest7.png)

In the list of available segmennts, select the segment you created in [Exercise 11.1 Create a segment](./ex1.md), which is named `--demoProfileLdap-- - Interest in Zeppelin Yoga Pant`. Then, click **Next**.

![AT](./images/atdest8.png)

On the next page, click **Next**.

![AT](./images/atdest9.png)

Click **Finish**. 

![AT](./images/atdest10.png)

Your segment is now activated towards Adobe Target.

![AT](./images/atdest11.png)

>[!IMPORTANT]
>
>When you've just created your Adobe Target destination in Real-Time CDP, it may take up to an hour for the destination to be live. This is a one-off wait time, due to the setup of the backend configuration. Once the initial 1 hour wait time and backend configuration is done, newly added edge segments that are sent to the Adobe Target destination will be available for targeting in real-time.

## 11.5.3 Configure your Adobe Target form-based activity 

Now that your Real-Time CDP segment is configured to be sent to Adobe Target, you can configure your Experience Targeting activity in Adobe Target. In this exercise you'll configre a Form-based activity.

Go to the Adobe Experience Cloud homepage by going to [https://experiencecloud.adobe.com/](https://experiencecloud.adobe.com/). Click **Target** to open it.

![RTCDP](./images/excl.png)

On the **Adobe Target** homepage, you'll see all existing Activities.

![RTCDP](./images/exclatov.png)

Click **+ Create Activity** to create a new Activity.

![RTCDP](./images/exclatcr.png)

Select **Experience Targeting**.

![RTCDP](./images/exclatcrxt.png)

Select **Form** and select **No Property Restrictions**. Click **Next**. 

![RTCDP](./images/exclatcrxtdtlform.png)

You're now in the Form-based activity composer.

![RTCDP](./images/atform1.png)

For the field **LOCATION 1**, select **target-global-mbox**.

![RTCDP](./images/atform2.png)

The default audience is currently **All Visitors**. Click on the **3 dots** next to **All Visitors** and click **Change Audience**.

![RTCDP](./images/atform3.png)

You're now seeing the list of available audiences, and the Adobe Experience Platform segment that you created earlier and sent to Adobe Target is now part of this list. Select the segment you previously created in Adobe Experience Platform. Click **Assign Audience**.

![RTCDP](./images/exclatvecchaud.png)

Your Adobe Experience Platform segment is now part of this Experience Targeting Activity.

![RTCDP](./images/atform4.png)

Let's now change the Hero Image on the homepage of the website. Click to open the dropdown list next to **Default Content** and click **Create HTML Offer**.

![RTCDP](./images/atform5.png)

Paste the following code. Then, click **Next**.

```javascript
<script src="https://code.jquery.com/jquery-3.5.1.min.js"></script>
<script>
// Change src attribute of image
$("#brandhero").attr("src", "https://parsefiles.back4app.com/hgJBdVOS2eff03JCn6qXXOxT5jJFzialLAHJixD9/e3b3bb0797b22276eeb0cf4fa0ead75e_Luma%20-%20Product%20-%20Zepplin%20-%20Hero%20Banner.png");
</script>
```

![RTCDP](./images/atform6.png)

You'll then see the new experience with the new image, for your selected Audience.

![RTCDP](./images/atform7.png)

Click the title of your Activity in the upper left corner to rename it.

![RTCDP](./images/exclatvecname.png)

For the name, please use:

- `--demoProfileLdap-- - RTCDP - XT (Form)`

![RTCDP](./images/atform8.png)

Click **Next**.

![RTCDP](./images/exclatvecnamenext.png)

On the **Goals & Settings** - page, go to **Goal Metrics**.

![RTCDP](./images/atform9.png)

Set the Primary Goal to **Engagement** - **Time On Site**.

![RTCDP](./images/vec3.png)

Click **Save & Close**.

![RTCDP](./images/vecsave.png)

You're now on the **Activity Overview** page. You still need to activate your Activity.

![RTCDP](./images/atform10.png)

Click on the field **Inactive** and select **Activate**.

![RTCDP](./images/atform11.png)

You'll then get a visual confirmation that your activity is now live.

![RTCDP](./images/atform12.png)

Your activity is now live and can be tested on the demo website.

>[!IMPORTANT]
>
>When you've just created your Adobe Target destination in Real-Time CDP, it may take up to an hour for the destination to be live. This is a one-off wait time, due to the setup of the backend configuration. Once the initial 1 hour wait time and backend configuration is done, newly added edge segments that are sent to the Adobe Target destination will be available for targeting in real-time.

If you now go back to your demo website and visit the product page for Zeppelin Yoga Pant, you'll then instantly qualify for the segment that you created, and you'll see the Adobe Target activity be displayed on the home page in real-time.

![RTCDP](./images/atform13.png)

### (Optional) Configure your Adobe Target activity using the Visual Experience Composer

>[!IMPORTANT]
>
>The below exercise is optional in the context of the tutorial and is intended for informational purpose mainly.

Now that your Real-Time CDP segment is configured to be sent to Adobe Target, you can configure your Experience Targeting activity in Adobe Target.

Go to the Adobe Experience Cloud homepage by going to [https://experiencecloud.adobe.com/](https://experiencecloud.adobe.com/). Click **Target** to open it.

![RTCDP](./images/excl.png)

On the **Adobe Target** homepage, you'll see all existing Activities.

![RTCDP](./images/exclatov.png)

Click **+ Create Activity** to create a new Activity.

![RTCDP](./images/exclatcr.png)

Select **Experience Targeting**.

![RTCDP](./images/exclatcrxt.png)

>[!IMPORTANT]
>
> Due to the nature of the demo website, which always redirects every visit to the Admin-page, it's important to already have the demo website open and your brand already selected in another tab in the same browser-window as the one where you're going to define your Adobe Target Activity. If you don't have the brand already selected in another tab in the same browser window, you won't be able to continue with the next step.

Fill out the details, like the **Activity URL**. 

![RTCDP](./images/exclatcrxtdtl.png)

Click **Next**.

![RTCDP](./images/exclatcrxtdtlnext.png)

You're now in the Visual Experience Composer, and should see the demo website with the brand that you already selected.

![RTCDP](./images/exclatvec.png)

The default audience is currently **All Visitors**. Click on the **3 dots** next to **All Visitors** and click **Change Audience**.

![RTCDP](./images/exclatveccha.png)

You're now seeing the list of available audiences, and the Adobe Experience Platform segment that you created earlier and sent to Adobe Target is now part of this list. Select the segment you previously created in Adobe Experience Platform. Click **Assign Audience**.

![RTCDP](./images/exclatvecchaud.png)

Your Adobe Experience Platform segment is now part of this Experience Targeting Activity.

![RTCDP](./images/exclatvecchaok.png)

Let's now change the Hero Image. Click the Hero Image, go to **Replace Content**, then click **Image**.

![RTCDP](./images/exclatveccta.png)

You'll then see all available images. Pick an image.

![RTCDP](./images/exclatvecctaimg.png)

Click **Save**.

![RTCDP](./images/exclatvecctaimgsave.png)

You'll then see the new experience with the new image, for your selected Audience.

![RTCDP](./images/exclatvecctaimgsaved.png)

Click the title of your Activity in the upper left corner to rename it.

![RTCDP](./images/exclatvecname.png)

For the name, please use:

- `--demoProfileLdap-- - RTCDP - XT`

Replace **ldap** with your ldap.

![RTCDP](./images/exclatvecnamen.png)

Click **Next**.

![RTCDP](./images/exclatvecnamenext.png)

On the next screen, click **Next**.

![RTCDP](./images/vec1.png)

On the **Goals & Settings** - page, go to **Goal Metrics**.

![RTCDP](./images/vec2.png)

Set the Primary Goal to **Engagement** - **Time On Site**.

![RTCDP](./images/vec3.png)

Click **Save & Close**.

![RTCDP](./images/vecsave.png)

You're now on the **Activity Overview** page.

![RTCDP](./images/vecsave.png)

You still need to activate your Activity.

![RTCDP](./images/vec5.png)

Click on the field **Inactive** and select **Activate**.

![RTCDP](./images/vec6.png)

You'll then get a visual confirmation that your activity is now live.

![RTCDP](./images/veclive.png)

Next Step: [Summary and benefits](./summary.md)

[Go Back to Module 11](./real-time-cdp-build-a-segment-take-action.md)

[Go Back to All Modules](../../overview.md)
