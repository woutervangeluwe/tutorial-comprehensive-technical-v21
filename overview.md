---
title: Overview
description: Starting point for Data Engineers, Data Analysts, Data Architects, Data Scientists, Orchestration Engineers and Marketers to gain a full understanding of the business value of Adobe Experience Platform and all of its Application Services.
doc-type: multipage-overview
exl-id: b63230ec-4820-4851-ad45-ea2b0f3e5d54
---
# Comprehensive Technical Tutorial for Adobe Experience Platform

## Overview

This tutorial is the perfect starting point for Data Engineers, Data Analysts, Data Architects, Data Scientists, Orchestration Engineers and Marketers to gain a full understanding of the business value of Adobe Experience Platform and all of its application services. Each lesson focuses on a real challenge businesses face in today's complex ecosystem of personalization and breaks down how Experience Platform solves that challenge in various hands-on exercises. Have a look at this video to understand the problems Adobe Experience Platform will help you solve.

>[!VIDEO](https://video.tv.adobe.com/v/344237?quality=12&enable=on)

This tutorial is very diverse and offers clear insights in the following applications:

- Adobe Experience Platform
- Adobe Experience Platform Data Collection
- Real-time CDP
- Adobe Journey Optimizer
- Customer Journey Analytics
- Offer Decisioning

This tutorial doesn't just focus on Adobe applications, but takes into account the broader ecosystem in which brands operate. In order to do that, in some lessons there is a focus on how _non-Adobe_ applications integrate with Adobe Experience Platform. As such, you'll gain a deep understanding in how the following applications will work together with Adobe Experience Platform:

- Amazon: AWS Lambda, AWS S3, AWS Kinesis, AWS SQS, Alexa
- Google: Google Tag Manager, Google Analytics, Google Cloud Platform, Google BigQuery, Google Display&Video 360, Google AdWords
- Microsoft: Power BI, Azure EventHub, Azure Blob Storage, Dynamics 365
- Salesforce: Tableau
- Apache Kafka
- Postman
- Informatica
- ServiceNow
- Stackchat
- ...

After completing this tutorial, you will be able to:

- Configure Schemas, Mixins, Datasets, and Identities
- Configure an Adobe Experience Platform Data Collection property and setup the new Web SDK extension in Adobe Experience Platform Data Collection
- Stream data into Adobe Experience Platform in real-time using Adobe Experience Platform Data Collection, Google Tag Manager or Amazon Alexa
- Batch ingest data into Adobe Experience Platform using a workflow or by using an extract, transform, load (ETL) application
- Visualize and use the Real-time Customer Profile in Adobe Experience Platform
- Create segments
- Consume several Adobe Experience Platform APIs
- Use SQL to query your data in Adobe Experience Platform
- Configure, Train and Score Machine Learning Models in Adobe Experience Platform
- Use Journey Orchestration to configure real-time, trigger-based journeys
- Use Real-time CDP to take action by activating a segment to various destinations
- Use Customer Journey Analytics to report on omnichannel customer data from various sources, including Google BigQuery

## Prerequisites

- Access to Adobe Experience Platform: [https://experience.adobe.com/platform](https://experience.adobe.com/platform)
- Access to Adobe Experience Platform Data Collection: [https://experience.adobe.com/#/data-collection/](https://experience.adobe.com/#/data-collection/)
- Access to the demo website on [https://public.aepdemo.net](https://public.aepdemo.net)

>[!IMPORTANT]
>
>This tutorial was created to facilitate a particular workshop format. It uses specific systems and accounts to which you might not have access. Even without access, we think you can still learn a lot by reading through this very detailed content. If you're a participant in one of the workshops and need your access credentials, please contact your Adobe representative who will provide you with the required information.

## About this tutorial

In these lessons, you will implement Adobe Experience Platform and Application Services into a Platform Demo website which supports multiple demo industries. The Platform Demo website and mobile app have a rich data layer and functionality that will allow you to build a realistic implementation. It provides access to demo brands such as **Luma**, **Citi Signal**, **EXP News**, **MUTUAL365**, **Carvelo** and several others. You will build your own Adobe Experience Platform Data Collection Client property, in your own Experience Cloud organization, and map it to our hosted Platform Demo website using the Experience Platform Debugger. This will then generate data that is sent into your own Adobe Experience Platform instance. For an introduction to the Platform Demo website, have a look at the below video.

>[!VIDEO](https://video.tv.adobe.com/v/35137?quality=12&enable=on)

## Architecture

Before you start with the hands-on exercises, have a look at the Architecture behind this tutorial. As you can see in the above Overview, this tutorial will go deep on a number of features and functionalities of Adobe Experience Platform, but will also discuss multiple integrations across a variety of Sources and Destinations. In order for you to properly understand the architecture behind this tutorial and the overall positioning of Adobe Experience Platform into your Enterprise ecosystem, start by reviewing the architecture video and diagram.

Go to [Architecture](./architecture.md).

## Videos

![Videos](./assets/images/yt.jpeg)

You can find a lot of interesting videos from our Tech Academy events, from Bootcamps and more on our [Experience Makers Community YouTube channel](https://www.youtube.com/channel/UCUKG2dkZ9pYuZUPebQ21jUw).

Several videos have been created that showcase elements of the enablement and powerful integrations between Adobe Experience Platform and non-Adobe applications. Click the below link to find an overview of those videos.

Go to [Videos](./videos.md).

## How is your completion of the Comprehensive Technical Tutorial for Adobe Experience Platform measured?

If you're participating in this tutorial as an Adobe partner or Adobe employee, you need to submit your progress after completing every enablement module.

You can find the requirements and process for submitting completion here: [Measuring Completion](./completion.md)

## Content

[0. Getting started](./modules/module0/getting-started.md)

- **Audience:** All participants of the Comprehensive Technical Tutorial for Adobe Experience Platform
- **Prerequisites:** Access to Demo System Next, Adobe Experience Platform and Adobe Experience Platform Data Collection. Access to the default Configuration ID of your Adobe Experience Platform environment.
- **Description:** In this foundational module, you will setup everything so that you can access and use the demo environment.
- **Time Investment:** 20 minutes

[1. Foundation - Setup of Adobe Experience Platform Data Collection & Web SDK](./modules/module1/data-ingestion-launch-web-sdk.md)

- **Audience:** Data Engineer, Data Architect
- **Prerequisites:** Access to Adobe Experience Platform and Adobe Experience Platform Data Collection.
- **Description:** In this foundational module, you will learn about Adobe Experience Platform Data Collection and the new Web SDK extension.
- **Time Investment:** 30 minutes

[2. Foundation - Data Ingestion](./modules/module2/data-ingestion.md)

- **Audience:** Data Engineer, Data Architect
- **Prerequisites:** Access to Adobe Experience Platform and Adobe Experience Platform Data Collection.
- **Description:** In this foundational module, you will ingest data from the website into Platform
- **Time Investment:** 120 minutes

[3. Foundation - Real-time Customer Profile](./modules/module3/real-time-customer-profile.md)

- **Audience:** Data Engineer, Data Architect, Marketer
- **Prerequisites:** Access to Adobe Experience Platform and Postman
- **Description:** In this foundational module, you will explore the Real-time Customer Profile in Adobe Experience Platform by making use of the UI and API.
- **Time Investment:** 90 minutes
- **Download these assets**: 
  - [Postman collections](./assets/postman/postman_module3.zip)

[4. Voice Assistant - Amazon Alexa](./modules/module4/data-ingestion-amazon-alexa.md)

- **Audience:** Developer
- **Prerequisites:** Access to Adobe Experience Platform, AWS Lambda and Amazon Alexa
- **Description:** In this module, you'll add an Amazon Alexa Skill to your live demo environment.
- **Time Investment:** 60 minutes
- **Download these assets**: 
  - [AWS Alexa Interaction Model](./assets/aws-alexa/aepskillinteractionmodel.json)
  - [AWS Alexa Lambda Code](./assets/aws-lambda/aepskill.zip)

[5. Extract, Transform, Load data using a 3rd party ETL-tool](./modules/module5/data-ingestion-informatica-etl.md)

- **Audience:** Data Engineer, Data Architect
- **Prerequisites:** Access to Adobe Experience Platform, Informatica ETL
- **Description:** In this module, you'll use an ETL-tool to extract, transform and load data in Adobe Experience Platform.
- **Time Investment:** 60 minutes
- **Download these assets**: 
  - [CSV files](./assets/csv/module5/csvfiles.zip)

[6. Adobe Journey Optimizer: Orchestration](./modules/module6/journey-orchestration-create-account.md)

- **Audience:** Data Engineer, Data Architect, Orchestration Engineer
- **Prerequisites:** Access to Adobe Experience Platform and Adobe Journey Optimizer
- **Description:** In this module, you'll use Adobe Journey Optimizer to build out a trigger-based journey.
- **Time Investment:** 60 minutes

[7. Query Service](./modules/module7/query-service.md)

- **Audience:** Data Engineer, Data Architect, Data Analyst, BI Expert
- **Prerequisites:** Access to Adobe Experience Platform, Query Service, Power BI or Tableau
- **Description:** In this module, you'll learn how to use Adobe Experience Platform Query Service.
- **Time Investment:** 90 minutes
- **Download these assets**: 
  - [JSON - Sample Data: Demo System - Event Dataset for Website](./assets/json/m7_ee.json)
  - [JSON - Sample Data: Demo System - Event Dataset for Call Center](./assets/json/m7_callcenter.json)
  - [JSON - Sample Data: Demo System - Profile Dataset for Loyalty](./assets/json/m7_loyalty.json)

[8. Intelligent Services](./modules/module10/intelligent-services.md)

- **Audience:** Data Engineer, Data Architect, Data Scientist
- **Prerequisites:** Access to Adobe Experience Platform, Intelligent Services
- **Description:** In this module, you'll learn how to setup, configure and use Adobe Experience Platform Intelligent Services.
- **Time Investment:** 60 minutes

[9. RTCDP - Build a segment and take action](./modules/module11/real-time-cdp-build-a-segment-take-action.md)

- **Audience:** Data Architect, Orchestration Engineer, Marketer
- **Prerequisites:** Access to Adobe Experience Platform, Real-time CDP, Adobe Audience Manager, Adobe Target, AWS S3
- **Description:** In this module, you'll configure a segment, enable it for Streaming Segmentation and activate the segment to several destinations, including Google DV360, Google AdWords, Adobe Audience Manager, Adobe Target and S3-destinations like Salesforce Marketing Cloud.
- **Time Investment:** 90 minutes

[10. Adobe Journey Optimizer: External data sources and custom actions](./modules/module12/journey-orchestration-external-weather-api-sms.md)

- **Audience:** Data Engineer, Data Architect, Orchestration Engineer, Marketer
- **Prerequisites:** Access to Adobe Experience Platform, Adobe Journey Optimizer, Open Weather API, Twilio
- **Description:** In this module, you'll use Adobe Journey Optimizer to listen to customer behavior, both online and offline, and respond to it in an intelligent, contextual and real-time way over various channels.
- **Time Investment:** 90 minutes

[11. Customer Journey Analytics - Build a dashboard using Analysis Workspace on top of Adobe Experience Platform](./modules/module13/customer-journey-analytics-build-a-dashboard.md)

- **Audience:** Data Engineer, Data Architect, Data Analyst
- **Prerequisites:** Access to Adobe Experience Platform and Customer Journey Analytics
- **Description:** In this module, you'll get Online to Offline insights by configuring a dashboard containing omni-channel data like Website Interactions, Mobile App Interactions, Call Center Interactions, In-Store Interactions and much more.
- **Time Investment:** 120 minutes

[12. Adobe Journey Optimizer: Offer Decisioning](./modules/module14/offer-decisioning.md)

- **Audience:** Data Engineer, Data Architect, Orchestration Engineer, Marketer
- **Prerequisites:** Access to Adobe Experience Platform and Offer Decisioning
- **Description:** In this module, you'll use the Adobe Experience Platform - Offers/Decisioning application service in a hands-on way to configure Personalized Offers and your own Offer Activity.
- **Time Investment:** 120 minutes

[13. Ingest & Analyze Google Analytics data in Adobe Experience Platform with the BigQuery Source Connector](./modules/module16/customer-journey-analytics-bigquery-gcp.md)

- **Audience:** Data Engineer, Data Architect, Data Analyst
- **Prerequisites:** Access to Adobe Experience Platform, Customer Journey Analytics, Google Cloud Platform, Google BigQuery
- **Description:** In this module, you'll set up your own instance of Google Cloud Platform, load demo data in Google Cloud Platform and you'll then use the BigQuery Source Connector to ingest that data from Google Cloud Platform into Adobe Experience Platform. Finally, you'll use Customer Journey Analytics to visualize that data.
- **Time Investment:** 120 minutes
- **Download these assets**: 
  - [JSON - Sample Data: Demo - Loyalty Data (M16)](./assets/json/m16_bqLoyalty.json)

[14. Adobe Experience Platform and Microsoft Dynamics 365](./modules/module17/adobe-experience-platform-microsoft-dynamics-365.md)

- **Audience:** Data Engineer, Data Architect, Data Analyst
- **Prerequisites:** Access to Adobe Experience Platform, Customer Journey Analytics, Microsoft Dynamics 365 and Microsoft Azure
- **Description:** In this module, you'll set up your instance of Dynamics 365 for Sales and load sample customer data. You will then use the Dynamics 365 Source Connector in Adobe Experience Platform to ingest that data from Microsoft Dynamics 365 into Adobe Experience Platform. Finally, you'll use Journey orchestration to connect directly with Microsoft Dynamics 365 APIs to create a contract record from the demo website and you'll configure Journey orchestration to communicate directly to a customer based on the on a change in sentiment. In addition, you'll also learn how to set up and configure Microsoft Power Automate (Flow) and trigger a custom action directly into Journey Orchestration based on the Contact record change in Microsoft Dynamics 365. 
- **Time Investment:** 90 minutes

[15. Segment Activation to Microsoft Azure Event Hub](./modules/module18/segment-activation-microsoft-azure-eventhub.md)

- **Audience:** Data Engineer, Data Architect, Data Analyst
- **Prerequisites:** Access to Adobe Experience Platform, Real-time CDP and Microsoft Azure
- **Description:** In this module, you'll setup a Microsoft Azure EventHub destination as a real-time destination for Adobe Experience Platform Real-time CDP. You will also setup and deploy an Azure function that will be triggered in real-time whenever Adobe Experience Platform delivers a segment payload to your Azure EventHub destination. The Azure Function that you'll trigger will show the mechanism of Adobe Experience Platform Real-time CDP's activation capabilities.
As part of this module you will also get an understanding of what triggers Real-time CDP to actually deliver a payload to a specified destination. We will also discuss the status of a segment qualification and how it relates to activation.
- **Time Investment:** 90 minutes

[16. Adobe Experience Platform and ServiceNow: connecting service to marketing and sales](./modules/module19/call-center-servicenow.md)

- **Audience:** Data Engineer, Data Architect, Data Analyst
- **Prerequisites:** Access to Adobe Experience Platform
- **Description:** In this module you'll implement the bi-directional integration between Adobe Experience Platform and ServiceNow. 
- **Time Investment:** 120 minutes

[17. AI-Driven Chat Apps & Live Chat powered by Stackchat](./modules/module20/ai-driven-chat-apps-stackchat.md)

- **Audience:** Data Engineer, Data Architect, Data Analyst
- **Prerequisites:** Access to Adobe Experience Platform, a Facebook and / or WeChat account
- **Description:** In this module, you'll build your own chatbot using Stackchat's AI-Driven Chat Apps & Live Chat
- **Time Investment:** 120 minutes

[18. Data Collection & Real-time Event Forwarding with Adobe Experience Platform Data Collection](./modules/module21/aep-data-collection-ssf.md)

- **Audience:** Data Engineer, Data Architect, Data Analyst
- **Prerequisites:** Access to Adobe Experience Platform Data Collection, Tags and Event Forwarding properties
- **Description:** In this module, you'll use the previously configured datasets, schemas and Adobe Experience Platform Data Collection property to collect data, and then forward that data server-side to an endpoint of choice.
- **Time Investment:** 90 minutes

[19. Build your own real-time dashboard using Adobe I/O - Project Firefly and Adobe Experience Platform](./modules/module22/adobe-io-firefly.md)

- **Audience:** Data Engineer, Data Architect, Data Analyst, Developer
- **Prerequisites:** Access to Adobe Experience Platform and Adobe I/O Runtime
- **Description:** In this module, you'll use Adobe I/O - Project Firefly to build your own real-time dashboard that consumes data from Adobe Experience Platform in real-time. 
- **Time Investment:** 90 minutes

[20. Adobe Journey Optimizer: event-based journeys](./modules/module23/journeyoptimizer.md)

- **Audience:** Email Marketer, Orchestration Specialist, Data Engineer, Data Architect, Data Analyst
- **Prerequisites:** Access to Adobe Experience Platform and Journey Optimizer
- **Description:** In this module, you'll learn everything there is to know about Journey Optimizer, which helps companies design and deliver connected, contextual, and personalized experiences to their customers.
- **Time Investment:** 120 minutes

[21. Stream data from Apache Kafka into Adobe Experience Platform](./modules/module24/aep-apache-kafka.md)

- **Audience:** Data Analyst, Data Engineer, Data Architect
- **Prerequisites:** Access to Adobe Experience Platform
- **Description:** In this module, you'll learn how to setup your own Apache Kafka cluster, define topics, producers and consumers and stream data into Adobe Experience Platform using the Adobe Experience Platform Sink Connector for Kafka Connect.
- **Time Investment:** 90 minutes

>[!NOTE]
>
>Thank you for investing your time in learning all there is to know about Adobe Experience Platform. If you have questions, want to share general feedback of have suggestions on future content, please contact Wouter Van Geluwe directly, by sending an email to **vangeluw@adobe.com**.
