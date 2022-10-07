---
title: Offer Decisioning - Test your Decision using the demo website
description: Test your Decision using the demo website
kt: 5342
audience: Data Engineer, Data Architect, Orchestration Engineer, Marketer
doc-type: tutorial
activity: develop
exl-id: 0febdc53-66eb-44c4-aa0b-5569cc496901
---
# 14.4 Test your Decision using the demo website

## 14.4.1 Load website and brand

Open a new, clean incognito browser window and go to [https://public.aepdemo.net](https://public.aepdemo.net). 

You'll then see this. 

![Launch Setup](./images/demo1.png)

Enter your Configuration ID and click **Load Configuration**. Your configuration is then loaded.

![Launch Setup](./images/demo2.png)

Scroll down and click **Save Configuration**.

![Launch Setup](./images/demo3.png)

You'll then be redirected to the Admin homepage. Go to **Select LDAP**. Select your LDAP and click **Save**.

![Launch Setup](./images/demo5.png)

You'll then be redirected to the Admin homepage. Go to **Select Brand** and select the brand **Luma**, click **Save**.

![Launch Setup](./images/demo7.png)

You'll then be redirected to the Admin homepage. Click the **Luma** logo.

![Launch Setup](./images/demo8.png)

## 14.4.2 Customer browses the website

You'll then see the Luma homepage. You should immediately see your hero image change, and you should see the Fallback Offer that was defined as part of your Decision.

![Launch Setup](./images/demo9.png)

Go to the page **Login/Register**. Fill out the fields and then click **CREATE ACCOUNT** to create your account.

![Launch Setup](./images/demo10.png)

As part of the configuration of your Personalized Offers, you defined offers for either male customers or female customers. Based on the gender selection you made on the **Login/Register** page, you'll now see another offer on the Luma homepage. This time it isn't a Fallback Offer anymore, but instead a Personalized Offer.

In this example, the gender selection is male. For male customers, the highest priority offer is the offer for the Zeppelin Yoga Pant.

![Launch Setup](./images/demo11.png)

Thanks to the integration between Web SDK and Adobe Experience Platform, offers can be delivered in a nice and easy way, with a limited amount of configuration.

![Launch Setup](./images/demo12.png)

In the next exercise, you'll see how to work with offers using the API.

Next Step: [14.5 Test your Decision using the API](./ex5.md)

[Go Back to Module 14](./offer-decisioning.md)

[Go Back to All Modules](./../../overview.md)
