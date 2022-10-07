---
title: Adobe Experience Platform and ServiceNow - Setup your ServiceNow Flow
description: Adobe Experience Platform and ServiceNow - Setup your ServiceNow Flow
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
exl-id: 45257399-ea99-426e-a8cc-d0ce9658a1b5
---
# 19.5 Setup your ServiceNow Flow

## 19.5.1 Open the Flow 

In ServiceNow, in the Filter Navigator, enter the search term **Flow Designer**. Click **Flow Designer**.

![ServiceNow](./images/flow1.png)

You'll then see this.

![ServiceNow](./images/flow2.png)

Click the **Search** icon and search for the flow that is named **ServiceNow CSM Case ingestion to AEP**.

Click to open the flow **ServiceNow CSM Case ingestion to AEP**.

![ServiceNow](./images/flow3.png)

You'll then see this:

![ServiceNow](./images/flow4.png)

Your flow already has all the required building blocks, you now need to complete this configuration.

It's important to understand that this flow will be triggered when a customer service management case is created or updated. A case is created or updated when a Customer Service Agent has had an interaction with a customer.

## 19.5.2 Action 1 - Get Entity Information

Click to open Action 1 - Get Entity Information. This configuration was created by importing the XML file in one of the previous exercises. This action should look like this:

- **Entity**: XDM Individual Profile
- **Identity Field**: Email
- **Identity Value**: Trigger > Case Record > Consumer > Email

![ServiceNow](./images/flow5.png)

The goal of this action is to verify if the customer that contacted the Service Center, already exists in Adobe Experience Platform. Based on the response from Adobe Experience Platform, a different next action will be triggered.

Action 2 in this flow verifies if the customer was found or not. If the customer was found in Adobe Experience Platform, the next action will be Action 3. If the customer wasn't found in Adobe Experience Platform, the next action will be Action 4, which will actually create the customer in Adobe Experience Platform.

If your configuration corresponds with the above image, continue with the next action.

## 19.5.3 Action 3 - Update Consumer Record

Click to open Action 3 - Update Consumer Record. You'll then see this.

![ServiceNow](./images/flow6.png)

The goal of this step is to read the response from Adobe Experience Platform, and filter out the values for a couple of fields. In this use case, you need to collect the values for the fields **Churn Value**, **Product Affinity** and **Product Usage** from the response from Adobe Experience Platform.

This configuration was copied from the XML template that you imported before, and its configuration isn't correct. You need to verify the mapping for each of the below three fields.

![ServiceNow](./images/flow7.png)

First, click the **X** icon on each of those three mapped fields to remove the current mapping. You'll then have this:

![ServiceNow](./images/flow7a.png)

In order to link the field **Churn Value**, click the **f(x)** button as indicated.

Paste the below code in the editor:

```javascript
/*
**Access Flow/Action data using the fd_data object. Script must return a value.
**example: var shortDesc = fd_data.trigger.current.short_description;
**return shortDesc;
*/
var churnSc = fd_data._1__get_entity_information.entityinformation._experienceplatform.individualScoring.churn.churnPrediction;
var res = churnSc.toString();
return res;
```

You'll then have this:

![ServiceNow](./images/flow7b.png)

Next, for the field **Product Affinity**, click the **data pill** icon. You'll then see this:

![ServiceNow](./images/flow8.png)

Next, click **Get Entity Information**. You'll then see this:

![ServiceNow](./images/flow9.png)

Next, click the little arrow icon on the field **Entity Information**. You'll then see this:

![ServiceNow](./images/flow10.png)

Next, click the little arrow icon on the field `--aepTenantId--`. You'll then see this:

![ServiceNow](./images/flow11.png)

Next, scroll down and click the little arrow icon on the field **individualScoring**. You'll then see this:

![ServiceNow](./images/flow12.png)

Next, scroll down and click the little arrow icon on the field **product**. You'll then see this:

![ServiceNow](./images/flow12a.png)

Finally, click to select the field **affinity**.

Repeat this process to select the value for the field **Product Usage**.

- Product Usage should be linked to the field `--aepTenantId--`.**individualScoring**.**product**.**usage**.

![ServiceNow](./images/flow14.png)

Finally, action 3 should look like this now. Click **Done** first, followed by **Save**.

![ServiceNow](./images/flow15.png)

## 19.5.4 Action 4 - Load Entity Data

Click to open Action 4 - Load Entity Data. You'll then see this.

![ServiceNow](./images/flow20.png)

This is the step that will create a customer profile in Adobe Experience Platform, if the customer profile doesn't exist yet in Adobe Experience Platform.

You now need to make a selection for the fields Data Inlet, Dataset and Schema:

- Data Inlet: select **Demo System Next Streaming Endpoint**
- Dataset: select **Demo System - Profile Dataset for Website (Global v1.1)**
- Schema: select **Demo System - Profile Schema for Website (Global v1.1)**

You should then see this:

![ServiceNow](./images/flow21.png)

Next, you need to add attribute fields to this action by clicking the **+ Add Field Value** button.

These fields need to be added:

| Key |  Value |
|---|---|
| `--aepTenantId--` > identification > core > email | 3 - Update Record > Consumer Record > Email |
| `--aepTenantId--` > identification > core > phoneNumber | 3 - Update Record > Consumer Record > Mobile Phone |
| Person > Full Name > First Name | 3 - Update Record > Consumer Record > First Name |
| Person > Full Name > Last Name | 3 - Update Record > Consumer Record > Last Name |
| Identifier | Trigger - Record Created or Updated > Case Record > ID for AEP|

Here's how to find the above fields to map (values in the above table):

- 3 > Consumer Record > Email

  ![ServiceNow](./images/flow22.png)

- 3 > Consumer Record > Mobile Phone

  ![ServiceNow](./images/flow23.png)

- 3 > Consumer Record > First Name

  ![ServiceNow](./images/flow24.png)

- 3 > Consumer Record > Last Name

  ![ServiceNow](./images/flow25.png)

- Trigger > Case Record > ID for AEP
  
  ![ServiceNow](./images/flow26.png)
  
Finally, action 4 should look like this now. Click **Done** first, followed by **Save**.

![ServiceNow](./images/flow27.png)

## 19.5.5 Action 5 - Load Entity Data

Click to open Action 5 - Load Entity Data. You'll then see this.

![ServiceNow](./images/flow30.png)

This is the step that will send a service center interaction event to Adobe Experience Platform, when the Service Agent has created or updated a case in ServiceNow.

You now need to make a selection for the fields Data Inlet, Dataset and Schema:

- Data Inlet: select **Demo System Next Streaming Endpoint**
- Dataset: select **Demo System - Event Dataset for Call Center (Global v1.1)**
- Schema: select **Demo System - Event Schema for Call Center (Global v1.1)**

You should then see this:

![ServiceNow](./images/flow31.png)

Next, you need to add attribute fields to this action by clicking the **+ Add Field Value** button.

These fields need to be added:

| Key |  Value |
|---|---|
| `--aepTenantId--` > interactionDetails > core > callCenterAgent > callFeeling | Trigger - Record Created or Updated > Case Record > Call Feeling |
| `--aepTenantId--` > interactionDetails > core > callCenterAgent > call ID | Trigger - Record Created or Updated > Case Record > Number |
| `--aepTenantId--` > interactionDetails > core > callCenterAgent > call Topic | Trigger - Record Created or Updated > Case Record > Short Description |
| `--aepTenantId--` > interactionDetails > core > callCenterAgent > callChannel | Trigger - Record Created or Updated > Case Record > Channel |
| `--aepTenantId--` > interactionDetails > core > callCenterAgent > callPriority | Trigger - Record Created or Updated > Case Record > Priority |
| `--aepTenantId--` > identification > core > phoneNumber | Trigger - Record Created or Updated > Case Record > Consumer > Mobile Phone |
| `--aepTenantId--` > identification > core > email | Trigger - Record Created or Updated > Case Record > Consumer > Email |
| Event Type | serviceNow_CSMCase |
| Identifier | Trigger - Record Created or Updated  > Case Record > ID for AEP |
| Timestamp | Trigger - Record Created or Updated  > Case Record > Timestamp for AEP |

Here's how to find the above fields to map (values in the above table):
  
- Trigger > Case Record > Call Feeling
  
  ![ServiceNow](./images/flow33.png)
  
- Trigger > Case Record > Number
  
  ![ServiceNow](./images/flow34.png)
  
- Trigger > Case Record > Short Description
  
  ![ServiceNow](./images/flow35.png)
  
- Trigger > Case Record > Channel
  
  ![ServiceNow](./images/flow36.png)
  
- Trigger > Case Record > Priority
  
  ![ServiceNow](./images/flow37.png)
  
- Trigger > Case Record > Consumer > Mobile Phone
  
  ![ServiceNow](./images/flow39.png)
  
- Trigger > Case Record > Consumer > Email
  
  ![ServiceNow](./images/flow38.png)
  
- Trigger > Case Record > ID for AEP
  
  ![ServiceNow](./images/flow40.png)
  
- Trigger > Case Record > Timestamp for AEP
  
  ![ServiceNow](./images/flow41.png)
  
Finally, action 4 should look like this now. Click **Done** first, followed by **Save**.

![ServiceNow](./images/flow45.png)

You've now completed the configuration of your flow. Click **Activate**.

![ServiceNow](./images/flow46.png)

Next Step: [19.6 Prepare End-to-end Demo](./ex6.md)

[Go Back to Module 19](./call-center-servicenow.md)

[Go Back to All Modules](./../../overview.md)
