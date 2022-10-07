---
title: Segment Activation to Microsoft Azure Event Hub - Setup the Event Hub RTCDP destination in Adobe Experience Platform
description: Segment Activation to Microsoft Azure Event Hub - Setup the Event Hub RTCDP destination in Adobe Experience Platform
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
exl-id: e50979df-b416-4f18-8d0e-f73e2d9bd163
---
# 18.2 Configure your Azure Event Hub Destination in Adobe Experience Platform

## 18.2.1 Identify Required Azure Connection parameters

To define an Event Hub destination in Adobe Experience Platform you need your:

- Event Hubs namespace
- Event Hub
- Azure SAS Key name
- Azure SAS Key

Event Hub and EventHub namespace have been defined in the previous exercise: [Exercise 1 - Setup Event Hub in Azure](./ex1.md)

### Event Hubs Namespace
  
To lookup the above information in Azure Portal, navigate to [https://portal.azure.com/#home](https://portal.azure.com/#home). Make sure that you are using the correct Azure account.

Select **All Resources** in Azure Portal:

![2-01-azure-all-resources.png](./images/2-01-azure-all-resources.png)

### Event Hub

Look for a resource with resource type **Event Hubs Namespace**, if you followed the naming conventions used in the previous exercise you Event Hubs Namespace will be **ldap-aep-enablement**, for example **mmeewis-aep-enablement**. Take a note of it, you will need it in the next exercise.

![2-02-select-event-hubs-namespace.png](./images/2-02-select-event-hubs-namespace.png)

Click on the Event Hubs Namespace name to get the details:

![2-03-select-event-hub.png](./images/2-03-select-event-hub.png)

Select **Event Hubs** to get a list of Event Hubs defined in your Event Hubs Namespace, if you followed the naming conventions used in the previous exercise you will find an Event Hub named **ldap-aep-enablement-event-hub**, for example **mmeewis-aep-enablement-event-hub**. Take a note of it, you will need it in the next exercise.
  
![2-04-event-hub-selected.png](./images/2-04-event-hub-selected.png)

### SAS Key Name

Select **Shared access policies** for your **Event Hubs Namespace**

![2-05-select-sas.png](./images/2-05-select-sas.png)

You will see a list of Shared access policies. The SAS Key that we are looking for is **RootManageSharedAccessKey**. This is the SAS Key name. Write it down.

![2-06-sas-overview.png](./images/2-06-sas-overview.png)

### SAS Key Value

Click on the **RootManageSharedAccessKey** to get the SAS Key Value. And press the **Copy to clipboard** icon to copy the **Primary key**:

![2-07-sas-key-value.png](./images/2-07-sas-key-value.png)

### Destination Values Summary

At this point you should have identified all the values needed to define the Azure Event Hub destination in Adobe Experience Platform Real-time CDP.

| Destination Attribute Name |  Destination Attribute Value | Example Value |
|---|---|---|
|sasKeyName|SAS Key Name|RootManageSharedAccessKey|  
|sasKey|SAS Key Value|srREx9ShJG1Rv7f/... |
|namespace|Event Hubs Namespace|mmeewis-aep-enablement|
|eventHubName|Event Hub|mmeewis-aep-enablement-event-hub| 

## 18.2.2 Create Azure Event Hub Destination in Adobe Experience Platform

Log in to Adobe Experience Platform by going to this URL: [https://experience.adobe.com/platform](https://experience.adobe.com/platform).

After logging in, you'll land on the homepage of Adobe Experience Platform.

![Data Ingestion](./images/home.png)

Before you continue, you need to select a **sandbox**. The sandbox to select is named ``--aepSandboxId--``. You can do this by clicking the text **[!UICONTROL Production Prod]** in the blue line on top of your screen.

![Data Ingestion](./images/sb1.png)

After selecting the appropriate sandbox, you'll see the screen change and now you're in your dedicated sandbox.

![Data Ingestion](./images/sb2.png)

After selecting the appropriate sandbox, you'll see the screen change and now you're in your dedicated sandbox. Go to **Destinations**. 

![Data Ingestion](./images/sb2a.png)

Select **Cloud Storage** and go to **Azure Event Hubs** and click **Configure**:

![2-08-list-destinations.png](./images/2-08-list-destinations.png)

Fill in the destination values that you have collected in the previous exercise. Next, click **Connect to Destination**.

![2-09-destination-values.png](./images/2-09-destination-values.png)

If your credentials were correct, you'll see a confirmation: **Connected**. 

![2-09-destination-values.png](./images/2-09-destination-valuesa.png)

Click **Next**.

In the next screen, enter the name and description in the format **ldap-aep-enablement**. Enter **eventHubName** (see previous exercise) and click **Create destination**.
  
![2-10-create-destination.png](./images/2-10-create-destination.png)

You can skip segment activation for now. You can hit the **Save &amp; exit** button:

![2-11-save-exit-activation.png](./images/2-11-save-exit-activation.png)

Your destination is now created and available in Adobe Experience Platform.

![2-12-destination-created.png](./images/2-12-destination-created.png)

Next Step: [18.3 Create a Streaming Segment](./ex3.md)

[Go Back to Module 18](./segment-activation-microsoft-azure-eventhub.md)

[Go Back to All Modules](./../../overview.md)
