---
title: Foundation - Data Ingestion - From unknown to known on the website
description: Foundation - Data Ingestion - From unknown to known on the website
kt: 5342
audience: Data Engineer, Data Architect
doc-type: tutorial
activity: develop
exl-id: 64b731f9-8fc1-458b-bb58-27f6c8ca63d0
---
# 2.1 - From unknown to known on the website

## Context

The journey from unknown to known is one of the most important topics amongst brands these days, as is the customer journey from acquisition to retention. 

Adobe Experience Platform plays a huge role in this journey. Platform is the brains for communication, the experience system of record.

Platform is an environment in which the word **customer** is broader than just the **known**-customers. This is a very important thing to mention when speaking to brands: an unknown visitor on the website is also a customer from Platform's perspective and as such, all of the behavior as an unknown visitor is also sent to Platform. Thanks to that approach, when this customer eventually becomes a known customer, a brand can visualize what happened before that moment as well. This helps from an attribution and experience optimization perspective.

## What are you going to do

You will now ingest data into Adobe Experience Platform and that data will be linked to identifiers like ECIDs and email-addresses. The goal of this is to understand the business context of what you're about to do from a configuration perspective. In the next exercise, you'll start configuring everything you need to make all that data ingestion possible in your own sandbox environment.

### Customer Journey flow

For every demonstration, you'll need to use a fresh, incognito browser window. After opening a fresh, incognito browser window, go to [https://public.aepdemo.net/](https://public.aepdemo.net/).

* You'll be redirected to this page:

![DSN](./images/web1.png)

* Enter the Configuration ID you created in the previous step. Click **Load Configuration**.

![DSN](./images/web2.png)

* You'll then see this:

![DSN](./images/web3.png)

* Scroll down so you can see the **Save Configuration** button. Click **Save Configuration**.

![DSN](./images/web4.png)

* After a couple of seconds you'll be redirected to the Admin homepage and you'll see this:

![DSN](./images/cfg6a.png)

* Go to **Select LDAP** in the left side menu, select your LDAP in the list and click **Save**.

![DSN](./images/web61.png)

* Go to **Select Brand** in the left side menu, select a brand of choice and click **Save**.

![DSN](./images/web7.png)

* You'll now see a similar Admin homepage. Click the brand logo to go to the demo website.

![DSN](./images/web8.png)
  
* Click the **Luma**-logo to go to the demo website. You'll then see this:
  
![Demo](../module2/images/lb_home.png)
  
* Have a look at the X-ray panel and the Real-time Customer Profile:
  * **ECID** as the internal Adobe identifier
      
![Demo](../module2/images/lb_home_xup.png)

* You'll also see Experience Events

![Demo](../module2/images/lb_home_xee.png)
  
* Scroll down on the page until you see the products, click on the product **Nadia Elements Shell**.
  
![Demo](../module2/images/lb_homep.png)
  
* Have a look at the product. An Experience Event of type **Product View** has been sent by to Adobe Experience Platform. 
  
![Demo](../module2/images/lb_els_dtl.png)
  
* Next, open the X-ray panel and have a look at your **Experience Events**.
  
![Demo](../module2/images/lb_home1.png)
  
* Go back to the **Home** page, and click another product. Another Experience Event has been sent to Adobe Experience Platform. 
  
![Demo](../module2/images/lb_babars.png)
  
* Open the X-ray panel. You'll now see 2 Experience Events of type **Product View**. While the behavior is anonymous, we're able to track every click and store it in in Adobe Experience Platform. Once the anonymous customer becomes known, we'll be able to merge all anonymous behavior automatically to the know profile.
  
![Demo](../module2/images/lb_home2.png)

* Go to the Register/Login page. Fill out your registration details and click **CREATE ACCOUNT**.
  
![Demo](../module2/images/lb_register_dtl.png)
  
* After clicking **Create Account**, you'll be redirected to the homepage. Open the X-ray panel and go to Real-time Customer Profile. On the X-ray panel, you should see all of your personal data displayed.
  
![Demo](../module2/images/lb_x_loggedin.png)

* On the X-ray panel, go to Experience Events. You should see the 2 products that you viewed before on the X-ray panel.

![Demo](../module2/images/lb_home_xee_dtl.png)
  
You've now ingested data into Adobe Experience Platform and you've linked that data to identifiers like ECIDs and email-addresses. The goal of this is to understand the business context of what you're about to do. In the next exercise, you'll start configuring everything you need to make all that data ingestion possible.

Next Step: [2.2 Configure Schemas and Set Identifiers](./ex2.md)

[Go Back to Module 2](./data-ingestion.md)

[Go Back to All Modules](../../overview.md)
