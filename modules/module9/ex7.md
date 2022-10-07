---
title: Data Ingestion using Google Tag Manager and Google Analytics - Implement Google Tag Manager Tag on Platform Demo website
description: Data Ingestion using Google Tag Manager and Google Analytics - Implement Google Tag Manager Tag on Platform Demo website
kt: 5342
audience: Data Engineer, Data Architect
doc-type: tutorial
activity: develop
exl-id: a5f9597a-2c4c-452b-a71c-76b2f3c403e1
---
# 9.7 Implement Google Tag Manager Tag on Platform Demo website

Go to [https://tagmanager.google.com/](https://tagmanager.google.com/) and login with your personal login details.

In the Google Tag Manager UI, navigate to the menu option **Admin**.

![Launch Setup](./images/gtmadmin.png)

Go to **Install Google Tag Manager**.

![Launch Setup](./images/gtminstall.png)

You now see two code fragments that need to be implemented on your Platform Demo website.

You'll need to update your Configuration ID settings and enter those two code fragments on the **Update Configuration ID** page of the AEP Demo website Admin pages.

Go to [https://public.aepdemo.net/admin_configuration_update.html](https://public.aepdemo.net/admin_configuration_update.html).

You'll then see this:

![Launch Setup](./images/cfgid1.png)

Click **Load Configuration**. After clicking **Load Configuration**, scroll down until you see the fields **GTM Head Tag** and **GTM Body Tag**.

![Launch Setup](./images/cfgid2.png)

Go back to Google Tag Manager. First of all, copy the first code fragment.

![Launch Setup](./images/gtmjs1.png)

Paste this into the text editor of your choice:

![Launch Setup](./images/gtmjstextedit.png)

Rename **dataLayer** (as indicated) to **googleDataLayer** as shown below:

![Launch Setup](./images/gtmjstextedit1.png)

Go back to the **Update Configuration ID** screen and paste the code that you have in the text editor into the field **GTM Head Tag**.

![Launch Setup](./images/cfgid3.png)

Next, go back to Google Tag Manager.

Copy the second code fragment.

![Launch Setup](./images/gtmjs2.png)

Go back to the **Update Configuration ID** screen and paste the code that you copied in the field **GTM Body Tag**.

![Launch Setup](./images/cfgid4.png)

Next, scroll down and click **Update Configuration ID**.

![Launch Setup](./images/cfgid5.png)

After this change, your website and configuration are ready for Production!

Next Step: [9.8 Verify Data Ingestion from website into Platform](./ex8.md)

[Go Back to Module 9](./data-ingestion-using-google-tag-manager-and-google-analytics.md)

[Go Back to All Modules](../../overview.md)
