---
title: Customer Journey Analytics - Visualization using Customer Journey Analytics
description: Customer Journey Analytics - Visualization using Customer Journey Analytics
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
exl-id: cebf5d69-11b5-4c34-8506-9dfa5b3d10a0
---
# 13.5 Visualization using Customer Journey Analytics

## Objectives

- Understand Analysis Workspace UI
- Learn some feature that make Analysis Workspace so different.
- Learn how to analyze in CJA using Analysis Workspace

## Context

In this exercises you will use Analysis Workspace within CJA to analyze product views, product funnels, churn etc.

We will cover some of the queries done in  Module 7 - Query Service so you can see how easy is to run the same queries and more but without using SQL and relying only on the drag and drop philosophy of Analysis Workspace.

Let's use the project you created in [Exercise 13.4 - Data Preparation in Analysis Workspace](./ex4.md), so go to [https://analytics.adobe.com](https://analytics.adobe.com).

![demo](./images/prohome.png)

Open your project `ldap - Omnichannel Analysis`.

With your project opened and the Data View `ldap - Omnichannel Analysis` selected, you're ready to start building your first visualizations.

![demo](./images/prodataView1.png)

## How many product views do we have on a daily basis

First of all, we need to select the right dates to analyze the data. Go to the calendar dropdown on the right side of the canvas. Click on it and select the applicable date range.

![demo](./images/pro1.png)

In the left side menu (components area), find the Calculated Metric **Product Views**. Select it and drag and drop it in to the canvas, on the top right within the freeform table.

![demo](./images/pro2.png)

Automatically the dimension **Day** will be added to create your first table. Now you can see your question answered on the fly. 

![demo](./images/pro3.png)

Next, right-click on the metric summary.

![demo](./images/pro4.png)

Click on **Visualize** and then select **Line** as visualization.

![demo](./images/pro5.png)

You’ll see your products views by hour.  

![demo](./images/pro6.png)

You can change the time scope to day by clicking on **Settings** within the visualization.

![demo](./images/pro7.png)

Click on the dot next to **Line** to **Manage the Data Source**.

![demo](./images/pro7a.png)

Next, click **Lock Selection** and select **Selected Items** to lock this visualization so that it always displays a timeline of Product Views.

![demo](./images/pro7b.png)

## Top 5 Products Viewed

What are the top 5 products viewed?

Remember to save project every now and then.

|  OS        | Short cut   | 
| ----------------- |-------------| 
| Windows | Control + S          | 
| Mac | Command + S          |

Let's start finding the top 5 products viewed. In the left side menu, find the **Product Name** - Dimension.

![demo](./images/pro8.png)

Now drag and drop **Product Name** to replace the **Day** dimension:

This will be the result

![demo](./images/pro10a.png)

Next, try to breakdown one of the products by Brand Name. Search for **brandName** and drag it under the first product name.

![demo](./images/pro13.png)

Next, do a breakdown using the User Agent. Search for **User Agent** and drag it under the brand name.

![demo](./images/pro15.png)

You'll then see this:

![demo](./images/pro15a.png)

Finally you can add more visualizations. On the left side, under visualizations, search for `Donut`. Take `Donut`, drag-and-drop it on the canvas under the **Line** visualization. It will automatically show all **Product Names**.

![demo](./images/pro18.png)

Next, in the Table, select the first 5 **User Agent**  rows from the breakdown we did under **Google Pixel XL 32GB Black Smartphone** > **Citi Signal**. While selecting the 3 rows, hold the **CTRL** button (on Windows) or the **Command** button (on Mac).

![demo](./images/pro20.png)

You'll see the donut chart changed:

![demo](./images/pro21.png)

You can even adapt the design to be more readable, by making both the **Line** graph and the **Donut** graph a bit smaller so they can fit next to each other:

![demo](./images/pro22.png)

Click on the dot next to **Donut** to **Manage the Data Source**.

![demo](./images/pro22a.png)

Next, click **Lock Selection** to lock this visualization so that it always displays a timeline of Product Views.

![demo](./images/pro22b.png)

Find out more about visualizations using Analysis Workspace here: 

- [https://experienceleague.adobe.com/docs/analytics/analyze/analysis-workspace/visualizations/freeform-analysis-visualizations.html](https://experienceleague.adobe.com/docs/analytics/analyze/analysis-workspace/visualizations/freeform-analysis-visualizations.html)
- [https://experienceleague.adobe.com/docs/analytics/analyze/analysis-workspace/visualizations/t-sync-visualization.html](https://experienceleague.adobe.com/docs/analytics/analyze/analysis-workspace/visualizations/t-sync-visualization.html)

## Product Interaction funnel, from viewing to buying

There are many ways to solve this question. One of them is to use Product Interaction Type and use it on a freeform table. Another way is to use a **Fallout Visualization**. Let's use the last one as we want to visualize and analyze at the same time.

Close the current panel we have by clicking here:

![demo](./images/pro23.png)

Now add a new blank panel by clicking on **+ Add Blank Panel**.

![demo](./images/pro24.png)

Click the visualization **Fallout**.

![demo](./images/pro25.png)

Select the same date range as in the previous exercise.

![demo](./images/prodatef.png)

You'll then see this.

![demo](./images/prodatefa.png)

Find the dimension **Event Type** under the components on the left side:

![demo](./images/pro26.png)

Click on the arrow to open the dimension:

![demo](./images/pro27.png)

You'll see all available Product Interaction Types. Select the item **commerce.productViews** and drag and drop it onto the **Add Touchpoint** field inside the **Fallout Visualization**.

![demo](./images/pro28.png)

![demo](./images/pro29.png)

Do the same with **commerce.productListAdds** and **commerce.purchases** and drop them onto the **Add Touchpoint** field inside the **Fallout Visualization**. You'll then have this:

![demo](./images/props1.png)

Your visualization will now look like this:

![demo](./images/pro30.png)

You can do many things here. Some examples: compare over time, compare each step by device or compare by loyalty. However, if we want to analyze interesting things like why customers don't purchase after adding an item to their cart, we can use the best tool in CJA: right-click.

Right click on the touchpoint **commerce.productListAdds**. Then click on **Breakdown fallout at this touchpoint**.

![demo](./images/pro32.png)

A new freeform table will be created to analyze what the people did if they didn't purchase. 

![demo](./images/pro33.png)

Change the **Event Type** by **Page Name**, in the new freeform table, to see which pages they are going instead of the Purchase Confirmation Page.

![demo](./images/pro34.png)

## What do people do on the site before reaching the Cancel Service page?

Again, there are many ways to perform this analysis. However, let's use the flow analysis to start the discovery part.

Close the current panel by clicking here:

![demo](./images/pro0.png)

Now add a new blank panel by clicking on **+ Add Blank Panel**.

![demo](./images/pro0a.png)

Click the visualization **Flow**.

![demo](./images/pro35.png)

You'll then see this:

![demo](./images/pro351.png)

Select the same date range as in the previous exercise.

![demo](./images/pro0b.png)

Find the dimension **Page Name** under the components on the left side:

![demo](./images/pro36.png)

Click on the arrow to open the dimension:

![demo](./images/pro37.png)

You'll find all pages viewed. Find the page name: **Cancel Service**.

![demo](./images/pro38.png)

Drag and drop **Cancel Service** into the Flow Visualization on the middle field:

![demo](./images/pro39.png)

You'll then see this:

![demo](./images/pro40.png)

Let's now analyze if customers who visited the **Cancel Service** page on the website also called the callcenter, and what the outcome was.

Under the dimensions, go back and then find **Call Interaction Type**. 

![demo](./images/pro43.png)

Drag and drop **Call Interaction Type** to replace the first interaction on the right within the **Flow Visualization**. You're now seeing which customers called the call center after visiting the **Cancel Service** page.

![demo](./images/pro44.png)

Next, under the dimensions, search for **Call Feeling**.  Drag and drop it to replace the first interaction on the right within the **Flow Visualization**.

![demo](./images/pro46.png)

You'll then see this:

![demo](./images/flow.png)

As you can see, we have run an omnichannel analysis using the Flow Visualization. Thanks to that we have found it seems that some customers that were thinking of canceling their service, had a positive feeling after calling the callcenter. Have we maybe changed their minds with a promotion? 


## How are customers with a Positive Callcenter contact performing against the main KPIs?

Let's first segment the data to get only users with **positive** calls. In CJA, Segments are called Filters. Go to filters within the component area (on the left-side) and click **+**.

![demo](./images/pro58.png)

Inside the Filter builder, give a name to the filter

|  Name        | Description    | 
| ----------------- |-------------| 
| Call Feeling - Positive | Call Feeling - Positive          | 

![demo](./images/pro47.png)

Under the components (inside the Filter Builder), find **Call Feeling** and drag and drop it into the Filter Builder Definition.

![demo](./images/pro48.png)

Now select **positive** as value for the filter.

![demo](./images/pro49.png)

Change the scope to be **Person** level.

![demo](./images/pro50.png)

To finish, simply click **Save**.

![demo](./images/pro51.png)

You'll then be back here. If not done yet, close the previous panel.

![demo](./images/pro0c.png)

Now add a new blank panel by clicking on **+ Add Blank Panel**.

![demo](./images/pro24c.png)

Select the same date range as in the previous exercise.

![demo](./images/pro24d.png)

Click on **Freeform table**.

![demo](./images/pro52.png)

Now drag and drop the filter you've just created.

![demo](./images/pro53.png)

Time to add some metrics. Start with **Product Views**. Drag and drop into the freeform table. You can also delete the **Events** metric.

![demo](./images/pro54.png)

Do the same with **People**,  **Add to Cart** and **Purchases**. You'll end up with a table like this.

![demo](./images/pro55.png)

Thanks to the first flow analysis, a new question came to mind. So we decided to create this table and check some KPIs against a segment to answer that question. As you can see, time to insight is much faster than using SQL or using other BI solutions.

## Attribution

Attribution in CJA enables business users to understand each touch in the customer journey. Attribution showcases how customers move from one touchpoint to another and brands use it to understand how advertising (banners on the website), content, products, etc... impact the customer journey.

With the omnichannel data that is available in Adobe Experience Platform, we can now provide attribution insights across online and offline channels to understand that for instance, a customer became interested in a product through an offline store visit, that the customer called the call-center for information and that the sale was done on the website. 

Attribution in Customer Journey Analytics is one of the key differentiators from other BI solutions. Let's see how it works.

We can define attribution logic in almost any metric (except things like **People** or **Sessions**). You can even use it with calculated metrics.

Open the calculated metric you created, called **Purchases**. On the **Events** metric, filtered by **Event Type**, click on settings.

![demo](./images/a.png)

The default attribution model is **Last Touch**. Check the checkbox for **Use non-default attribution model**.

![demo](./images/b.png)

After checking the checkbox for **Use non-default attribution model**, you'll see this popup:

![demo](./images/c.png)

Here you can change the model and the Look-back Window.

You'll now see all available attribution models. To understand the differences between the attribution models, read this: [Adobe Analytics Attribution](https://www.adobe.com/content/dam/acom/en/data-analytics-cloud/analytics/pdfs/Adobe.Analytics.Attribution.Solution_Brief_Sept.2017.pdf)

As already mentioned, you can even change the reporting look-back window. Depending on the model you'll have different options.

![demo](./images/f.png)

Make your choice and click **Apply**.

![demo](./images/apply.png)

## Cohort Analysis

The **Cohort Table** allows you to understand how segments of users behave over a certain period of time. With CJA, this complicated query is made easy. With Cohort Analysis, you can now understand key KPIs such as **MAU** (Monthly Active Users) or **WAU** (Weekly Active Users).

![demo](./images/cohortAnalysis2.png)

Using the omnichannel data that is available thanks to Adobe Experience Platform, the following questions can now be answered:

- How many people who bought offline, came back to buy online after? How long does it take for them to come back?
- What is the retention of people after having interactions with our call-center? Are they coming back more or less?
- Since the launch of our Alexa App, how do our customers interact with the various available interaction channels (digital, point of sales, etc.)?

Example:

![demo](./images/cohortAnalysis.png)

## Customer Journey Analytics and Analysis Workspace recap

As you've learned in this lab, Analysis Workspace stitches data from all channels together to analyze the full customer journey. Also, remember that you can bring in data to the same workspace that is not stitched to the journey. 
It can be really useful to bring disconnected data into your analysis to give context to the journey. Some examples include things like NPS data, surveys, Facebook Ads events or offline interactions (non identified).

Next Step: [Summary & benefits](./summary.md)

[Go Back to Module 13](./customer-journey-analytics-build-a-dashboard.md)

[Go Back to All Modules](./../../overview.md)
