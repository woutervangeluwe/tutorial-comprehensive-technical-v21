---
title: Customer Journey Analytics - Data preparation in Analysis Workspace
description: Customer Journey Analytics - Data preparation in Analysis Workspace
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
exl-id: 1cad6d76-11c0-4a94-a1d6-059a4f633c72
---
# 13.4 Data preparation in Analysis Workspace

## Objectives

- Understand the Analysis Workspace UI in CJA
- Understand the concepts of data preparation in Analysis Workspace
- Learn how to do data calculations

## Exercise 13.4.1 Analysis Workspace UI in CJA

Analysis Workspace removes all of the typical limitations of a single Analytics report. It provides a robust, flexible canvas for building custom analysis projects. Drag-and-drop any number of data tables, visualizations, and components (dimensions, Metrics, segments, and time granularities) to a project. Instantly create breakdowns and segments, create cohorts for analysis, create alerts, compare segments, do flow and fallout analysis, and curate and schedule reports for sharing with anyone in your business.

Customer Journey Analytics brings this solution on top of Platform data. We highly recommend watching this four-minute overview video:

>[!VIDEO](https://video.tv.adobe.com/v/35109?quality=12&learn=on)

If you haven't used Analysis Workspace before, we highly recommend watching this video:

>[!VIDEO](https://video.tv.adobe.com/v/26266?quality=12&learn=on)

### Create Your Project

Now it's time to create your first CJA project. Go to the projects tab inside of CJA. 

![demo](./images/prmenu.png)

Click on create a new project.

![demo](./images/prprojects.png)

You'll then see an empty project.

![demo](./images/premptyprojects.png)

First, make sure to select the correct Data View in the upper right corner of your screen. In this example, the Data View to select is `vangeluw - Omnichannel Data View`.

![demo](./images/prdv.png)

Next, you'll save your project and give it a name. You can use the following command to save:

|  OS        | Short cut   | 
| ----------------- |-------------| 
| Windows | Control + S          | 
| Mac | Command + S          | 

You'll see this popup: 

![demo](./images/prsave.png)

Please use this naming convention:

|  Name       | Description   | 
| ----------------- |-------------| 
| ldap - Omnichannel Analysis| ldap - Omnichannel Analysis|

Next, click **Save Project**.

![demo](./images/prsave2.png)

## Exercise 13.4.2 Calculated Metrics

Although we have organized all the components in the Data View, you still need to adapt some of them, so that business users are ready to start their analysis.

If you remember, we didn't specifically bring in Metrics such us Add to Cart, Product View or Purchases into the Data View. 
However, we do have a dimension called: **Product Interaction Type**. So, let's derive these interaction types by creating 3 calculated Metrics.

Back in module 7, [Query Service](./../../modules/module7/query-service.md), you created a SQL query to get the interactions funnel:

**Query & Result**

```text
aepenablementfy21:all=> select eventType, count(*)
aepenablementfy21:all-> from   demo_system_event_dataset_for_website_global_v1_1
aepenablementfy21:all-> where  --aepTenantId--.demoEnvironment.brandName IN ('Luma Telco', 'Citi Signal')
aepenablementfy21:all-> and    eventType is not null
aepenablementfy21:all-> and    eventType <> ''
aepenablementfy21:all-> group  by eventType;
          eventType           | count(1) 
------------------------------+----------
 commerce.productViews        |     2297
 commerce.productListAdds     |      494
 commerce.purchases           |      246
(3 rows)
```

The goal in CJA is to avoid using SQL queries, but still have access to the same components using real analytics power through a User Interface.

### Product Views

Let's start with first Metric: **Product Views**. Click on the **+** to create your first calculated Metric.

![demo](./images/pradd.png)

The **Calculated Metric Builder** will show up:

![demo](./images/prbuilder.png)

Within the components, on the left side, please search **Event Type**.

![demo](./images/pr14.png)

Then drag and drop it in to the Calculated Metric's **Definition** canvas.

You'll now see a popup. In the popup, in the dropdown, find and select **commerce.productViews** (or enter it manually and click Enter). 

![demo](./images/pr12.png)

Next, click **Done**.

![demo](./images/prdone.png)

Now we must quantify this interaction. To do this select the Metric **Events (occurrences)**, then drag and drop it inside the filter. This will allow us to understand how many times the **commerce.productViews** event has occurred.

![demo](./images/pr11.png)

To finish, add a name and description.

| Title         | Description|    
| ----------------- |-------------| 
| Product Views | Product Views     |   

You'll then see this:

![demo](./images/pr10.png)

Click **Save** to save your calculated Metric.

![demo](./images/pr9.png)

Next, repeat the same process for **commerce.productListAdds** and **commerce.purchases**.

### Add to Cart

| Event Type | Name         | Description| 
| ----------------- |-------------| -------------|
| commerce.productListAdds|Add to Carts | Add to Carts     |

The Metric definition should look like this:

![demo](./images/praddtocart.png)

### Purchases

| Product Interaction Type | Name         | Description| 
| ----------------- |-------------| -------------|
| commerce.purchases|Purchases | Purchases   |

The Metric definition should look like this:

![demo](./images/prpurchase.png)

Don't forget to **Save** each Calculated Metric.

![demo](./images/pr9.png)

### Conversion Rate

To finish this exercise, let's create a last calculated Metric: **Conversion Rate**.

Find the **Purchase** Calculated Metric we've just created in the list of Metrics in the left side menu. Click on the **info** icon.

![demo](./images/prmetricinfo.png)

Now click on the **edit** icon.

Typically, conversion rate means **Conversions / Sessions**. So let's do the same calculation in the calculated Metric definition canvas. Find the **Sessions** metric and drag and drop it into the definition builder.

![demo](./images/pr6.png)

Notice that the division operator is automatically selected.

![demo](./images/pr5.png)

![demo](./images/pr4.png)

The conversion rate is commonly represented in percentage. So, let's change the format to be percentage and also select 2 decimals.

![demo](./images/pr2.png)

Change the name and description:

| Name         | Description|    
| ----------------- |-------------| 
| Conversion Rate | Conversion Rate      | 

![demo](./images/pr1.png)

Now click **Save As** to save your new Calculated Metric without overwriting the original one..

![demo](./images/prsaveas.png)

## Exercise 13.4.3 Calculated Dimensions: Filters (segmentation) & Date Ranges

### Filters: Calculated Dimensions

Calculations are not meant to be only for Metrics. Before starting any analysis it's also interesting to create some **Calculated Dimensions**. This basically meant **segments** back in Adobe Analytics. In Customer Journey Analytics, these segments are called **Filters**. 

![demo](./images/prfilters.png)

Creating filters will help business users to start the analysis with some valuable calculated dimensions. This will automate some tasks as well as helping on the adoption part. Here are some examples:

1. Own Media, Paid Media, 
2. New vs Returning visits
3. Customers with Abandoned Cart

These filters can be created before or during the analysis part (which you'll do in the next exercise). 

### Date Ranges: Calculated Time Dimensions

Time Dimensions are another type of calculated dimensions. Some are already create, but you also have the ability to create your own custom Time Dimensions at the data preparation phase. 

These Calculated Time Dimensions we will help analysts and business users to remember important dates and use them to filter and change the reporting time. Typical questions and doubts that come to our minds when we do analysis:

- When was Black Friday last year? 21th-29th?
- When did we run that TV campaign in December?
- From when to when did we do the 2018 Summer Sales? I want to compare it against 2019. By the way, do you know the exact days in 2019? 

![demo](./images/timedimensions.png)

You've now finished the data preparation exercise using CJA Analysis Workspace.

Next Step: [13.5 Visualization using Customer Journey Analytics](./ex5.md)

[Go Back to Module 13](./customer-journey-analytics-build-a-dashboard.md)

[Go Back to All Modules](./../../overview.md)
