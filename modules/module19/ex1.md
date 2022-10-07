---
title: Adobe Experience Platform and ServiceNow 
description: Adobe Experience Platform and ServiceNow
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
exl-id: ee5893bd-fac9-45a3-a647-a5393635ef03
---
# 19.1 Setup your ServiceNow developer instance

## 19.1.1 Create your ServiceNow account and instance

Go to [https://developer.servicenow.com/dev.do#!/home](https://developer.servicenow.com/dev.do#!/home) and select **Sign up and start building**. 

![ServiceNow](./images/snow1.png)

You'll then see this. 

![ServiceNow](./images/snow2.png)

Fill out the fields and click **Sign Up**.

![ServiceNow](./images/snow3.png)

You'll then see this. 

![ServiceNow](./images/snow4.png)

Next, check your email for a link to activate your account. Click the link.

![ServiceNow](./images/snow5.png)

You'll then see this. Click **Sign In**.

![ServiceNow](./images/snow6.png)

Enter your email and click **Next**.

![ServiceNow](./images/snow7.png)

Enter your password and click **Next**.

![ServiceNow](./images/snow8.png)

You'll then see this. Scroll down until you reach the end of the document.

![ServiceNow](./images/snow9.png)

Check the checkbox to accept the ServiceNow Developer Agreement and click **Submit**.

![ServiceNow](./images/snow10.png)

You'll then see the developer homepage of ServiceNow. Click **Request Instance** to get your own personal ServiceNow instance.

![ServiceNow](./images/snow11.png)

You'll then see this popup.

![ServiceNow](./images/snow11a.png)

Your instance is now being created, which might take a couple of minutes. After closing the popup, you'll see this on your Developer homepage.

![ServiceNow](./images/snow12.png)

After a couple of seconds/minutes, you'll see this message. You can see that the username for logging in to your ServiceNow developer instance is **admin**, and you'll also see a default password which you'll need in the next step. You'll have to change that default password in the next step. You'll also get a confirmation email with your login credentials and Service URL. Keep this email as you'll need it in one of the next exercises.

![ServiceNow](./images/snow13e.png)

Click **Open Instance**.

![ServiceNow](./images/snow13.png)

You've now successfully logged in to your ServiceNow instance. 

![ServiceNow](./images/snow17.png)

>[!NOTE]
>
>You now have access to a ServiceNow developer instance. A developer instance is intended for testing and development. If you don't use your instance for 10 days, your instance will be reclaimed by ServiceNow and you'll lose access to it. If you want to keep using your ServiceNow instance, you'll have to make sure to log in to [https://developer.servicenow.com/](https://developer.servicenow.com/) at least once every 10 days and then click the **Refresh Status** button.

![ServiceNow](./images/snow17a.png)

## 19.1.2 Activate Customer Service Management in ServiceNow

You now need to activate the **Customer Service Management** plugin in ServiceNow.

To install the **Customer Service Management** plugin, type **System Applications** in the **Filter Navigator**. Then, click **All**.

![ServiceNow](./images/csmplugin1.png)

You'll then see this. Search for the plugin **Customer Service Management** and click **Install**.

![ServiceNow](./images/csmplugin2.png)

You'll then see this popup. Scroll down until you see the **Activate** button.

![ServiceNow](./images/csmplugin2a.png)

You'll then see a confirmation window. Click **Activate**.

![ServiceNow](./images/csmplugin2b.png)

You'll then see a progress bar. 

![ServiceNow](./images/csmplugin3a.png)

After a couple of minutes, the **Customer Service Management** plugin will be activated and available. Click **Close & Reload Form**.

![ServiceNow](./images/csmplugin4.png)

## 19.1.3 Activate ServiceNow IntegrationHub Enterprise Pack Installer

Go back to [https://developer.servicenow.com/dev.do#!/home](https://developer.servicenow.com/dev.do#!/home). In the **Your Instance** panel, click **Manage** and then click **Activate Plugin**.

![ServiceNow](./images/snow18.png)

In the list of available plugins, search and find the plugin named **ServiceNow IntegrationHub Enterprise Pack Installer**. Click **Activate**.

![ServiceNow](./images/snow19.png)

You'll then see this. Close this window and wait until you receive an email to confirm that the **ServiceNow IntegrationHub Enterprise Pack** plugin has been activated. This may take 10 minutes.

![ServiceNow](./images/snow20.png)

Once you've received this email, you can continue with the next exercise.

![ServiceNow](./images/snow21.png)

Next Step: [19.2 Install and configure the integration between ServiceNow and Adobe Experience Platform through Adobe I/O](./ex2.md)

[Go Back to Module 19](./call-center-servicenow.md)

[Go Back to All Modules](./../../overview.md)
