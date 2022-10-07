---
title: Foundation - Real-time Customer Profile - From unknown to known on the website
description: Foundation - Real-time Customer Profile - From unknown to known on the website
kt: 5342
audience: Data Engineer, Data Architect, Marketer
doc-type: tutorial
activity: develop
exl-id: b1bd9a23-d8fb-41dd-bc9f-2ad0f0a80ea0
---
# 3.1 From unknown to known on the website

## **Context**

The journey from unknown to known is one of the most important topics amongst brands these days, as is the customer journey from acquisition to retention. 

Adobe Experience Platform plays a huge role in this journey. Platform is the brains for communication, the "experience system of record."

Platform is an environment in which the word *customer* is broader than just the *known*-customers. An unknown visitor on the website is also a customer from Platform's perspective and as such, all of the behavior as an unknown visitor is also sent to Platform. Thanks to that approach, when this visitor eventually becomes a known customer, a brand can visualize what happened before that moment as well. This helps from an attribution and experience optimization perspective.

## **What are you going to do?**

You will now ingest data into Adobe Experience Platform and that data will be linked to identifiers like ECIDs and email-addresses. The goal of this exercise is to understand the business context of what you're about to do from a configuration perspective. In the next exercise, you'll start configuring everything you need to make all that data ingestion possible in your own sandbox environment.

## **Customer journey flow**

For every demonstration, you'll need to use a fresh, incognito browser window. After opening a fresh, incognito browser window, go to [https://public.aepdemo.net/](https://public.aepdemo.net/).

You'll be redirected to this page:

![DSN](./images/web1.png)

Enter the Configuration ID you created in the previous step. Click **Load Configuration**.

![DSN](./images/web2.png)

You'll then see this:

![DSN](./images/web3.png)

Scroll down so you can see the **Save Configuration** button. Click **Save Configuration**.

![DSN](./images/web4.png)

After a couple of seconds you'll be redirected to the Admin homepage and you'll see this:

![DSN](./images/cfg6a.png)

Go to **Select LDAP** in the left side menu, select your LDAP in the list and click **Save**.

![DSN](./images/web61.png)

Go to **Select Brand** in the left side menu, select a brand of choice and click **Save**.

![DSN](./images/web7.png)

You'll now see a similar Admin homepage. Click the brand logo to go to the demo website.

![DSN](./images/web8.png)
  
Click the **Luma**-logo to go to the demo website. You'll then see this:
  
![Demo](./images/lb_home.png)
  
### Navigate the website

Have a look at the X-ray panel and the Real-time Customer Profile:
  
* **Experience Cloud ID (ECID)** is the internal Adobe identifier
      
![Demo](../module2/images/lb_home_xup.png)

You'll also see **Experience Events**

![Demo](../module2/images/lb_home_xee.png)
  
Scroll down on the page until you see the products, click on the product **Nadia Elements Shell**.
  
![Demo](../module2/images/lb_homep.png)
  
Have a look at the product. An experience event of type **Product View** has been sent to Adobe Experience Platform. 
  
![Demo](../module2/images/lb_els_dtl.png)
  
Next, go to the Homepage. Open the X-ray panel and have a look at your **Experience Events**.
  
![Demo](../module2/images/lb_home1.png)
  
On the Homepage, click another product. Another Experience Event has been sent to Adobe Experience Platform. 
  
![Demo](../module2/images/lb_babars.png)
  
Go back to the Homepage and open the X-ray panel. You'll now see 2 experience events of type **Product View**. While the behavior is anonymous, we're able to track every click and store it in in Adobe Experience Platform. Once the anonymous customer becomes known, we'll be able to merge all anonymous behavior automatically to the known profile.
  
![Demo](../module2/images/lb_home2.png)

Go to the Register/Login page. Fill out your registration details and click **CREATE ACCOUNT**.
  
![Demo](../module2/images/lb_register_dtl.png) 
  
After clicking **Create Account**, you'll be redirected to the homepage. Open the X-ray panel and go to Real-time Customer Profile. On the X-ray panel, you should see all of your personal data displayed.
  
![Demo](../module2/images/lb_x_loggedin.png)

On the X-ray panel, go to Experience Events. You should see the two products that you viewed previously on the X-ray panel.

![Demo](../module2/images/lb_home_xee_dtl.png)

### Navigate the mobile app

After becoming a known customer, it's time to start using the mobile app. Open the mobile app on your iPhone and then login to the app. 

If you don't have the app installed anymore, or if you can't remember how to install it, please have a look here: [0.5 Use the mobile app](../module0/ex5.md)

After installing the app as instructed, you'll see the landing page of the app with the Luma brand loaded.
  
![Demo](./images/app_hp.png)

Go to the Account screen.
  
![Demo](./images/app_acc.png)

Click Login and then login with the email address you used in the website steps and the password of 1234.
  
![Demo](./images/app_acc_login.png)

You'll now see your Real-time Customer Profile data appear in the mobile application, along with your Desktop Product Views.

![Demo](./images/app_up.png)

Go to the app's Home screen.
  
![Demo](./images/app_hp.png)

Go to any category.
  
![Demo](./images/app_men_cat.png)

Click on a product to view it.
  
![Demo](./images/app_carst.png)

Go back to the previous screen
  
![Demo](./images/app_men_cat.png)

Go to the Account screen and your Real-time Customer Profile data will be refreshed, after which you'll see the product you just viewed in the **Your recent browse** section.
  
![Demo](./images/app_after_carst.png)

Now go back to your desktop computer and refresh the homepage, after which you'll see the product appear there, too.
  
![Demo](./images/lb_x_aftermobile.png)
  
You've now ingested data into Adobe Experience Platform and you've linked that data to identifiers like ECIDs and email addresses. The goal of this exercise was to understand the business context of what you're about to do. You've now effectively built a real-time, cross-device customer profile. In the next exercise, you'll go ahead and visualize your profile in Adobe Experience Platform.

Next Step: [3.2 Visualize your own real-time customer profile - UI](./ex2.md)

[Go Back to Module 3](./real-time-customer-profile.md)

[Go Back to All Modules](../../overview.md)
