---
title: Adobe Experience Platform and ServiceNow - Setup your ServiceNow Flow
description: Adobe Experience Platform and ServiceNow - Setup your ServiceNow Flow
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
exl-id: 27a89a57-14f4-452c-99ca-72b13a94523e
---
# 19.6 Prepare End-to-end Demo

For the end-to-end demo in the next exercise, you'll be using the demo website from the URL [https://public.aepdemo.net](https://public.aepdemo.net).

On that website, you'll create your account as part of the demo script and when that happens, that same account needs to be created in ServiceNow. To do that, the website will use the [ServiceNow REST API](https://docs.servicenow.com/bundle/paris-application-development/page/integrate/inbound-rest/concept/consumer-api.html#consumer-api). To make that possible, you need to enable a CORS rule in ServiceNow to allow communication from the URL [https://public.aepdemo.net](https://public.aepdemo.net), and you'll have to update your Configuration ID with your ServiceNow connection variables.

## 19.6.1 ServiceNow CORS setup 

In ServiceNow, in the Filter Navigator, enter the search term **Cors**. Click **CORS Rules**. 

![ServiceNow](./images/cors1.png)

You'll then see this. Click **New**.

![ServiceNow](./images/cors2.png)

You'll then see an empty CORS Rule form. 

![ServiceNow](./images/cors3.png)

Fill out the fields as follows:

- Name: **public.aepdemo.net**
- REST API: **Consumer [now/consumer]**
- Domain: https://public.aepdemo.net
- Enable the checkboxes for **GET** and **POST**

![ServiceNow](./images/cors4.png)

Click **Submit** to save your changes.

## 19.6.2 Update your Configuration ID

Before you can test your end-to-end demonstration, you'll need to update your Configuration ID settings and update the fields for **ServiceNow Instance URL**, **ServiceNow Username** and **ServiceNow Password** on the **Update Configuration ID** page of the AEP Demo website Admin pages.

Go to [https://public.aepdemo.net/admin_configuration_update.html](https://public.aepdemo.net/admin_configuration_update.html).

You'll then see this:

![Launch Setup](./images/cfgid1.png)

Enter your Configuration ID and then click **Load Configuration**. You'll see your Configuration ID values being loaded.

![Launch Setup](./images/cfgid2.png)

Scroll down until you see the fields **ServiceNow Instance URL**, **ServiceNow Username** and **ServiceNow Password**.

![Launch Setup](./images/cfgid2a.png)

You now need to enter the values for these three fields.

- **ServiceNow Instance URL** can be found in the URL of your browser. The URL looks like this: **https://devXXXXX.service-now.com**.

  ![Launch Setup](./images/cfgid3.png)

  Copy the ServiceNow Instance URL and paste it in the corresponding field on your Configuration ID update page. Add this to the URL: **/api/now/consumer**.

  ![Launch Setup](./images/cfgid4.png)

- **ServiceNow Username** should be **admin**. Enter **admin** in the corresponding field on your Configuration ID update page.

  ![Launch Setup](./images/cfgid5.png)

- **ServiceNow Password** is the password you entered in [Exercise 19.1.1](./ex1.md) when creating your ServiceNow developer instance. It was sent to you by email:

  ![Launch Setup](./images/snow13e.png)
  
  Enter your admin password in the corresponding field on your Configuration ID update page.
  
  ![Launch Setup](./images/cfgid6.png)
  
>[!NOTE]
>
>If you forgot your admin password, you can reset it by going to [https://developer.servicenow.com/dev.do#!/home](https://developer.servicenow.com/dev.do#!/home), click Manage on **Your Instance** and select **Reset admin password**.

  ![Launch Setup](./images/resetpw.png)

Next, on the Update Configuration ID page, scroll down and click **Update Configuration ID**.

![Launch Setup](./images/cfgid7.png)

After this change, your Configuration ID is ready for the end-to-end demonstration!

Next Step: [19.7 End-to-end Demo](./ex7.md)

[Go Back to Module 19](./call-center-servicenow.md)

[Go Back to All Modules](./../../overview.md)
