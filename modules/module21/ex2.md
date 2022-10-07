---
title: Adobe Experience Platform Data Collection & Real-time Server Side Forwarding - Update your Datastream to make data available to your Adobe Experience Platform Data Collection Server property
description: Update your Datastream to make data available to your Adobe Experience Platform Data Collection Server property
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
exl-id: bfae4690-d75b-4ee7-936b-578198b2cabb
---
# 21.2 Update your Datastream to make data available to your Adobe Experience Platform Data Collection Server property

## 21.2.1 Update your Datastream

In [Exercise 0.2](./../../modules/module0/ex2.md), you created your own **[!UICONTROL Datastream]**. You then used the name **ldap - Demo System Datastream** and replaced **ldap** with your ldap.

In this exercise, you need to configure that **[!UICONTROL Datastream]** to work with your **[!DNL Adobe Experience Platform Data Collection Server property]**.

To do that, go to [https://experience.adobe.com/#/data-collection/](https://experience.adobe.com/#/data-collection/). You'll then see this. In the left menu, click **[!UICONTROL Datastreams]**.

![WebSDK](./images/websdk0.png)

Search for your **[!UICONTROL Datastream]**. Click your **[!UICONTROL Datastream]** to open it.

![WebSDK](./images/websdk2.png)

You'll then see this. Click **[!UICONTROL Development Environment]**.

![WebSDK](./images/websdk3.png)

In the **[!UICONTROL Development Environment]**, you'll see your Adobe Experience Platform configuration. 

![WebSDK](./images/websdk4.png)

Scroll down to **[!DNL Launch Server Side]** and toggle the button to turn [!DNL Launch Server Side] on.

![WebSDK](./images/websdk4a.png)

You can then select your **[!DNL Launch Server Side Property ID]** from the dropdown list. Search and select the **[!DNL Launch Server Side property]** you created in the previous step.

![WebSDK](./images/websdk5.png)

After selecting the **[!DNL Launch Server Side property]**, you need to select the Environment ID. Select **[!DNL Development]**.

![WebSDK](./images/websdk7.png)

Click **[!DNL Save]**.

![WebSDK](./images/websdk8.png)

You'll then be back here.

![WebSDK](./images/websdk8a.png)

Next, repeat the above steps for the other environments.

This should be your configuration for the **[!DNL Staging Environment]**.

![WebSDK](./images/websdk9.png)

And this should be your configuration for the **[!DNL Production Environment]**.

![WebSDK](./images/websdk10.png)

Your Datastream is now ready to work with your **[!DNL Launch Server Side property]**.

Next Step: [21.3 Create and configure a custom webhook](./ex3.md)

[Go Back to Module 21](./aep-data-collection-ssf.md)

[Go Back to All Modules](./../../overview.md)
