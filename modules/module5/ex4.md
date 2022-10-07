---
title: Extract, Transform, Load data using a 3rd party ETL-tool - Ingest Offline Order Events into Adobe Experience Platform
description: Extract, Transform, Load data using a 3rd party ETL-tool - Ingest Offline Order Events into Adobe Experience Platform
kt: 5342
audience: Data Engineer, Data Architect
doc-type: tutorial
activity: develop
exl-id: 581e6d91-66da-4177-a2bd-1c724d5f93eb
---
# 5.4 Ingest Offline Order Events into Adobe Experience Platform

In this exercise, you'll learn how to import order data into Informatica, join datasets and ingest transformed data into Adobe Experience Platform as Experience Events.

## Learning Objectives

- Learn how to load data in Informatica
- Learn how to create a mapper workflow in Informatica. 
- Understand the process to join data sets, enrich data and ingest it in Platform.

## Lab Resources

- Informatica: [https://usw5.dm-us.informaticacloud.com/diUI/products/integrationDesign/main/home](https://usw5.dm-us.informaticacloud.com/diUI/products/integrationDesign/main/home)
- Adobe Experience Platform: [https://experience.adobe.com/platform/](https://experience.adobe.com/platform/)

## Lab Tasks

- Load CSV files from your S3 bucket into Informatica for Offline Orders and Loyalty Program Profiles
- Create a mapper workflow to join the above data sets, enrich and filter the data.
- Run the job to ingest the data into Adobe Experience Platform

## Business Context: Using Informatica to ingest offline orders events into Platform

Luma is a fashion brand and in addition to its online presence, has brick and mortar stores all over the world. So far the marketing team has struggled to make use of the offline orders data to optimize their online experience. Recently, they introduced a new loyalty program that allows customers to collect points when purchasing in-store using their loyalty card. The marketing team receives regularly a flat file with all the offline orders. They also have a record of all customers who have joined the loyalty program. With the help of Informatica, we will join the two data sources, enrich the result so that it can be ingested into Adobe Experience Platform, and then hydrate the profile with the offline order events.

## Exercise 5.3.1 - Create Sources in a Mapping Workflow

In this exercise, you'll load two CSV files from your S3 bucket into Informatica: 

- offline_orders.csv
- loyalty_data.csv

Go to [https://apse1.dm-ap.informaticacloud.com/cloudshell/showProducts](https://apse1.dm-ap.informaticacloud.com/cloudshell/showProducts). 

Login using the credentials that were sent to you by email.

![ETL](./images/infhome.png)

You'll then see the Informatica homepage. Go to **Data Integration**.

![ETL](./images/inf1.png)

On the Informatica homepage, click the **+ New...** button.

![ETL](./images/2map1.png)

You'll then see this popup.

![ETL](./images/2map2.png)

In the left menu in the popup, select **Mappings**. Next, select **Mapping**.

![ETL](./images/2map3.png)

Click **Create** to start creating your mapping workflow.

![ETL](./images/2map4.png)

You'll then see this screen:

![ETL](./images/2map5.png)

Let's start by configuring the name of your mapping. For the name of your mapping, use **LDAP - ex3**. In this example, the name is **vangeluw - ex3**.

![ETL](./images/2map6.png) 

Click **Save** in the upper right corner of the screen to save your changes.

![ETL](./images/save.png) 

Next, let's start the creation of your mapping workflow. Your workflow looks like this at the moment.

![ETL](./images/2wf1.png) 

Let's start by removing the **Target** object for the moment. Select the **Target** object and click the **Delete** icon.

![ETL](./images/2wf2.png) 

Click **Delete** on the popup window.

![ETL](./images/2wf3.png)

Your workflow now looks like this.

![ETL](./images/2wf4.png)

Select the **Source** object. After selecting the **Source** object, you'll see a Properties window at the bottom of your screen.

![ETL](./images/2wf5.png)

In the **Properties** window, click **Source**.

![ETL](./images/2wf6.png)

Open the **Connection** dropdown, locate your **S3 - LDAP** connection and select it.

![ETL](./images/2wf7.png)

You'll then see this.

![ETL](./images/2wf8.png)

Click **Select...**.

![ETL](./images/2wf9.png)

You'll then see a popup window, which shows your S3-connection. In the **Packages** column, you'll see your bucket name. Click your bucket name to select it.

![ETL](./images/2wf10.png)

After selecting your bucket name, you'll see the four CSV files that you uploaded into your S3 bucket in Exercise 5.1. 

Select the file **offline_orders.csv** and click OK.

![ETL](./images/2wf11.png)

You'll then see this.

![ETL](./images/2wf12.png)

In the **Format** dropdown, change the Format Type from **None** to **Delimited**.

![ETL](./images/2wf14.png)

Click **Formatting Options**.

![ETL](./images/2wf15.png)

On the Properties screen, click **Data Preview**.

![ETL](./images/2wf16.png)

You should then see a preview just like this one. Click **Done** to close the preview window.

![ETL](./images/2wf17.png)

The file that you just loaded as a source, has these columns:

| Column     | Description                           |
|:----       | :--------                             |
| id         | Row number                            |
| timestamp  | Timestamp when product was purchased  |
| account_id | Loyalty program account id            |
| product    | Product SKU                           |
| price      | Product price                         |
| currency   | Currency of the product price         |

As you can see in the preview, there are several empty lines so you'll have to do some cleaning of the file before ingesting it into Adobe Experience Platform.

Next, you'll set up a second **Source** object on the mapping workflow.

Drag an drop the **Source** object from the left menu in the Design Overview onto the canvas.

![ETL](./images/2wf18.png)

You should now have this Design:

![ETL](./images/2wf19.png)

Select the second **Source** object. After selecting the second **Source** object, you'll again see a Properties window at the bottom of your screen.

In the **Properties** window, click **Source**.

![ETL](./images/2wf20.png)

Open the **Connection** dropdown, locate your **S3 - LDAP** connection and select it.

![ETL](./images/2wf21.png) 

You'll then see this.

![ETL](./images/2wf22.png)

Click **Select...**.

![ETL](./images/2wf9.png)

You'll then see a popup window, which shows your S3-connection. In the **Packages** column, you'll see your bucket name. Click your bucket name to select it.

![ETL](./images/2wf23.png)

After selecting your bucket name, you'll see the four CSV files that you uploaded into your S3 bucket in exercise 1. 

Select the file **loyalty_data.csv** and click OK.

![ETL](./images/2wf24.png)

You'll then see this.

![ETL](./images/2wf25.png)

In the **Format** dropdown, change the Format Type from **None** to **Delimited**.

![ETL](./images/2wf13.png)

You'll then have this.

![ETL](./images/2wf14a.png)

Click **Formatting Options**.

![ETL](./images/2wf15.png)

On the Properties screen, click **Data Preview**.

![ETL](./images/2wf16.png)

You should then see a preview just like this one. Click **Done** to close the preview window.

![ETL](./images/2wf26.png)

The file that you just loaded as a source, has these columns:

| Column     | Description                           |
|:----       | :--------                             |
| account_id | Loyalty program account id            |
| first_name | Customer's first name                 |
| last_name  | Customer's last name                  |
| email      | Customer's email address              |
| gender     | Customer's gender                     |
| points     | Customer's number of collected points |

You have now created the Source connectors required for this exercise!

## Exercise 5.3.2 - Join Sources

In this exercise, you'll join the above created Sources.

Your mapping workflow looks like this currently:

![ETL](./images/2wf30.png)

You now need to join those 2 datasets. The way to do that is using a **Joiner**. In the Design-menu, scroll down until you see the **Joiner** object. 

![ETL](./images/2wf31.png)

Drag and drop the **Joiner** object on the canvas.

![ETL](./images/2wf32.png)

Next, you have to connect the two Sources to the Joiner.

Click the orange **+** icon on the Joiner. You'll now see a **Master** and a **Detail** node.

![ETL](./images/2wf33.png)

Connect Source to Master and Source 1 to detail as indicated below.

![ETL](./images/2wf34.png)

Let's define the Properties of the Joiner now.

![ETL](./images/2wf40.png)

Go to the menu option **Incoming Fields**. You'll see a notification message that certain fields from the two Sources have the same name. Let's fix that first.

Click on **Resolve Field Name Conflicts**.

![ETL](./images/2wf41.png)

You'll see this window now.

![ETL](./images/2wf42.png)

For Master > Source, open the dropdown list for **Bulk Rename Options** and select **Prefix**. 

Enter the prefix **m_**. 

Click **OK**.

![ETL](./images/2wf43.png)

In the Incoming Fields screen, you can now scroll down and you'll see that all fields form the Master Source now have an `m_`-prefix and the error message is gone.

![ETL](./images/2wf44.png)

Next, you have to define the **Join Condition**. Click on **Join Condition** in the left menu.

You'll then see this.

![ETL](./images/2wf45.png)

Click the little **+** icon.

You'll then see a Join Condition appear.

![ETL](./images/2wf46.png)

Connect these 2 fields to each other:

`m_account_id (string)` = `account_id (string)`

![ETL](./images/2wf47.png)

When done, click **Save**

![ETL](./images/2wf48.png)

Your two Sources are now joined with each other.

Don't forget to click **Save** to save your mapping's current state.

![ETL](./images/savemapping.png)

## Exercise 5.3.3 - Filter Data

The next step is filtering data. Specifically, you need to remove potential empty lines like in the case of having an empty account_id.

In order to filter data, you need to add a **Filter** object onto the canvas. You can find the **Filter** object in the left menu on the Design workflow.

![ETL](./images/filter1.png)

Drag and drop the **Filter** object onto the canvas.

![ETL](./images/filter2.png)

Next, have a look at the **Properties** window.

![ETL](./images/filter3.png)

In the left menu, go to **Filter**.

Click the **+** icon on the right side to add a Filter.

![ETL](./images/filter4.png)

Change the **Filter Condition** to **Advanced**.

![ETL](./images/filter5.png)

Click the **Edit Filter Condition** button.

![ETL](./images/filter6.png)

In the **Edit Filter**-popup, paste this filter: 
`IIF(ISNULL(account_id),FALSE,TRUE)`

![ETL](./images/filter7.png)

Click **OK** to save your Filter.

You've now defined your Filter, let's enrich your data.

Don't forget to click **Save** to save your mapping's current state.

![ETL](./images/savemapping.png)

## Exercise 5.3.4 - Enrich Data

In the enrichment phase, you can add additional fields to your dataset. In this example, we need to provide a unique `hitId` to Adobe Experience Platform when ingesting Experience Event-data. This `hitId` isn't part of the dataset yet, so you'll add it now using an **Expression**.

In order to enrich data, you need to add an **Expression** object onto the canvas. You can find the **Expression** object in the left menu on the Design workflow.

![ETL](./images/enrich1.png)

Drag and drop the **Expression** object onto the canvas.

![ETL](./images/enrich2.png)

Next, have a look at the **Properties** window.

In the left menu, go to **Expression**.

Click the **+** icon on the right side to add a Field/Expression.

![ETL](./images/enrich3.png)

You'll then see this popup:

![ETL](./images/enrich4.png)

In the popup, define the field Name and Type:

- Name: `hitId`
- Type: `bigint` 

![ETL](./images/enrich5.png)

Click **OK** to save your field.

You'll then see this:

![ETL](./images/enrich5a.png)

Click **Configure...**

In the **Edit Expression**-popup, paste this expression: 
`rand() * 1000000000000`

![ETL](./images/enrich6.png)

Click **OK** to save your expression.

You've now defined your Expression, let's output your data to Adobe Experience Platform.

Don't forget to click **Save** to save your mapping's current state.

![ETL](./images/savemapping.png)

## Exercise 5.3.5 - Output Data to Target

The last step is to add the **Target** object to the workflow. From the left menu, drag and drop the **Target** object onto the canvas.

![ETL](./images/target1.png)

Connect the **Expression** object to the **target** object.

![ETL](./images/target2.png)

Have a look at the **Properties** windows.

![ETL](./images/target3.png)

In the left menu, go to **Target**. In the Connection dropdown, select the Adobe Experience Platform connector you created previously.

![ETL](./images/target4.png)

You'll then have this:

![ETL](./images/target5.png)

Click the **Select** button to select the Adobe Experience Platform dataset to use.

Enter the search term `ETL` and click **Search**. You'll then see these datasets being returned.

Select the dataset `Demo System - Event Dataset for ETL (Global v1.1)`.

![ETL](./images/target6.png)

In the left menu of the Properties window, go to **Field Mapping**.

![ETL](./images/target7.png)

Map the Output to the Schema attributes as per below:

| Field       | Element Name |
| :---------  | :---  |
| m_timestamp | timestamp   |
| m_product   | productListItemsArray.productListItems.name   |
| m_product   | productListItemsArray.productListItems.SKU   |
| m_currency  | commerce.order.currencyCode      |
| email       | ``--aepTenantId--``.identification.core.email |
| hitID       | _id  |

Your Field Mapping should look like this (don't forget about the mapping for m_email).

![ETL](./images/target8a.png)

Click **Save**.

![ETL](./images/savemapping.png)

You now have a finished workflow which can be **Run**.

![ETL](./images/run1.png)

Click the **Run** button in the top right corner of the screen.

![ETL](./images/run0.png)

After 30 seconds, you'll then see this popup. (Note: it can take a long time, please just wait)

![ETL](./images/run2.png)

You need to change the **Runtime Environment** to the Runtime Environment you created in the previous exercise, just like in the screenshot. (If you don't select the correct Runtime Environment, your job won't run successfully)

![ETL](./images/run3.png)

Click **Run**.

![ETL](./images/run4.png)

After 20-30 seconds, your Job will be executing.

You can review the status of your Job by going to the left menu option **My Jobs**.

![ETL](./images/run5.png)

Locate your Job in the list and click it to open it.

![ETL](./images/run6.png)

You'll then see something like this:

![ETL](./images/run7.png)

Click the **Refresh** button to see updates.

![ETL](./images/run8.png)

Once your job has finished successfully, your data will be ingested in Adobe Experience Platform.

![ETL](./images/run14.png)

Log in to [Adobe Experience Platform](https://experience.adobe.com/platform).

After logging in, you'll land on the homepage of Adobe Experience Platform.

![Data Ingestion](./images/home.png)

Before you continue, you need to select a **sandbox**. The sandbox to select is named ``--aepSandboxId--``. You can do this by clicking the text **[!UICONTROL Production Prod]** in the blue line on top of your screen.

![Data Ingestion](./images/sb1.png)

After selecting the appropriate sandbox, you'll see the screen change and now you're in your dedicated sandbox.

![Data Ingestion](./images/sb2.png)

Go to Datasets and enter the search term `ETL`. You'll then see these datasets:

![ETL](./images/run9.png)

Open the dataset `Demo System - Event Dataset for ETL (Global v1.1)`. Scroll down until you see the Batch IDs and locate your specific batch. 

![ETL](./images/run12.png)

You can now continue with the next exercise.

Next Step: [5.5 Ingest 2nd and 3rd party data into Adobe Experience Platform](./ex5.md)

[Go Back to Module 5](./data-ingestion-informatica-etl.md)

[Go Back to All Modules](../../overview.md)
