---
title: Intelligent Services
description: Intelligent Services
kt: 5342
audience: Data Engineer, Data Architect, Data Scientist
doc-type: tutorial
activity: develop
exl-id: f669c46d-55be-4a3c-ae5f-8f63a8faa9f5
---
# 10. Intelligent Services

**Authors: [Diptiman Badajena](https://www.linkedin.com/in/diptiman-badajena-1b178019/), [Wouter Van Geluwe](https://www.linkedin.com/in/woutervangeluwe/)**

In this module, you'll learn how to setup, configure and use Adobe Experience Platform Intelligent Services.

## Learning Objectives

- Become familiar with Adobe Experience Platform
- Configure Schema / Dataset for use with Intelligent Services
- Create a new Customer AI instance
- Scoring dashboard and segmentation

## Prerequisites

- Access to Adobe Experience Platform: [https://experience.adobe.com/platform](https://experience.adobe.com/platform)

>[!IMPORTANT]
>
>This tutorial was created to facilitate a particular workshop format. It uses specific systems and accounts to which you might not have access. Even without access, we think you can still learn a lot by reading through this very detailed content. If you're a participant in one of the workshops and need your access credentials, please contact your Adobe representative who will provide you with the required information.

## Architecture Overview

Have a look at the below architecture, which highlights the components that will be discussed and used in this module.

![Architecture Overview](../../assets/images/architecturem10.png)

## Sandbox to use

For this module, please use this sandbox: `--module10sandbox--`.

>[!NOTE]
>
>Don't forget to install, configure and use the Chrome Extension as referenced in [0.6 - Install the Chrome extension for the Experience League documentation](../module0/ex6.md)

## Exercises

[10.1 Customer AI - Data Preparation (Ingest)](./ex1.md)

Customer data is ingested and transformed with the Experience Data Model (XDM) on Adobe Experience Platform. Specifically, all datasets that are used in Intelligent Services must conform to the Consumer ExperienceEvent (CEE) XDM schema.

[10.2 Customer AI - Create a New Instance (Configure)](./ex2.md)

The marketing analyst configures the desired predictions by specifying business rules and identifying relevant data. After configuring the model, schedule executions and review scores.

[10.3 Customer AI - Scoring Dashboard and Segmentation (Predict & Take Action)](./ex3.md)

After the models have finished training and scoring, the scores are written back into Platform. You can decide what actions to take with the predictions, such as defining segments, building custom dashboards etc.

>[!NOTE]
>
>Thank you for investing your time in learning all there is to know about Adobe Experience Platform. If you have questions, want to share general feedback of have suggestions on future content, please contact Wouter Van Geluwe directly, by sending an email to **vangeluw@adobe.com**.

[Go Back to All Modules](../../overview.md)
