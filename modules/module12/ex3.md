---
title: Adobe Journey Optimizer - External Weather API, SMS Action & more - Define Custom Actions
description: Adobe Journey Optimizer - External Weather API, SMS Action & more - Define Custom Actions
kt: 5342
audience: Data Engineer, Data Architect, Orchestration Engineer, Marketer
doc-type: tutorial
activity: develop
exl-id: a8d6077e-e386-427c-a797-c279ad1ab504
---
# 12.3 Define a custom action

In this exercise, you'll create two custom actions by making use of Adobe Journey Optimizer in combination.

Login to Adobe Journey Optimizer by going to [Adobe Experience Cloud](https://experience.adobe.com). Click **Journey Optimizer**.

![ACOP](./images/acophome.png)

You'll be redirected to the **Home**  view in Journey Optimizer.

![ACOP](./images/acoptriglp.png)

First, make sure you're using the correct sandbox. The sandbox to use is called `--aepSandboxId--`. To change from one sandbox to another, click on **PRODUCTION Prod (VA7)** and select the sandbox from the list. In this example, the sandbox is named **AEP Enablement FY21**.

![ACOP](./images/sb.png)

You'll then be in the **Home** view of your sandbox `--aepSandboxId--`.

![ACOP](./images/home.png)

In the left menu, scroll down and click **Configurations**. Next, click the **Manage** button under **Actions**.

![Demo](./images/menuactions.png)

You'll then see the **Actions** list.

![Demo](./images/acthome.png)

You'll define two actions:

- One action that sends an SMS using an external application, Twilio
- One action that sends a text to a Slack channel

## 12.3.1 Action: Send SMS using Twilio

Twilio is a 3rd party provider of SMS Messages. It has an easy-to-use API and we'll use Adobe Journey Optimizer to trigger their API.

![Demo](./images/twilio.png)

Click **Create Action** to start adding your action.

![Demo](./images/adda.png)

You'll see an empty Action popup.

![Demo](./images/emptyact.png)

As a Name for the Action, use `ldapSmsTwilio` and replace `Ldap` with your LDAP. In this example, the Action Name is `joconnorSmsTwilio`.

Set Description to: `Send SMS using Twilio`.

![Demo](./images/twilioname.png)

For the **URL Configuration**, use this:

- URL: `https://l1uikl5kog.execute-api.us-west-2.amazonaws.com/prod/`
- Method: **POST**

You don't need to change the Header Fields.

![Demo](./images/twiliourl.png)

>[!NOTE]
>
>For transparency, we're using an AWS API Gateway and AWS Lambda function that sits behind the above URL to handle the authentication and sending of SMSs to Twilio.

**Authentication** should be set to **No Authentication**.

![Demo](./images/twilioauth.png)

For the **Action Parameters**, you need to define which fields should be sent towards Twilio. Logically, we want Adobe Journey Optimizer and Adobe Experience Platform to be the brain of personalization, so the SMS Message Text and the Mobile Number to send the SMS towards should be defined by Adobe Journey Optimizer and then sent to Twilio for execution.

So for the **Action Parameters**, click the **Edit Payload** icon.

![Demo](./images/twiliomsgp.png)

You'll then see an empty popup-window.

![Demo](./images/twiliomsgpopup.png)

Copy the below text and paste it in the empty popup-window.

```json
{
 "body": {
  "textMessage": {
   "toBeMapped": true,
   "dataType": "string",
   "label": "textMessage"
  },
  "to": {
   "toBeMapped": true,
   "dataType": "string",
   "label": "mobileNr"
  }
 }
}
```

FYI: by specifying the below fields, these fields will become accessible from your Customer Journey and you'll be able to populate them dynamically from the Journey:

**"toBeMapped": true,**

**"dataType": "string",**

**"label": "textMessage"** and **mobileNr**

You'll then see this:

![Demo](./images/twiliomsgpopup1.png)

Click **Save**.

![Demo](./images/twiliomsgpopup2.png)

Scroll up and click **Save** one more time to save your custom Action.

![Demo](./images/twiliomsgpopup3.png)

Your custom Action is now part of the **Actions** list.

![Demo](./images/twiliodone.png)

Let's define your second action now.

## 12.3.2 Action: Send Text to Slack Channel

We'll now use an existing Slack Channel and send messages to that Slack Channel. Slack has an easy-to-use API and we'll use Adobe Journey Optimizer to trigger their API.

![Demo](./images/slack.png)

Click **Create Action** to start adding a new action.

![Demo](./images/adda.png)

You'll see an empty Action popup.

![Demo](./images/emptyact.png)

As a Name for the Action, use `ldapTextSlack` and replace `ldap` with your LDAP. In this example, the Action Name is `joconnorTextSlack`.

Set Description to: `Send Text to Slack`.

![Demo](./images/slackname.png)

For the **URL Configuration**, use this:

- URL: `https://2mnbfjyrre.execute-api.us-west-2.amazonaws.com/prod`
- Method: **POST**

>[!NOTE]
>
>The above URL refers to an AWS Lambda function which will then forward your request to the Slack channel as mentioned above. This is done to protect access to an Adobe-owned Slack channel. If you have your own Slack channel, you should create a Slack App through [https://api.slack.com/](https://api.slack.com/), you then need to create an Incoming Webhook in that Slack App, and then replace the above URL by your Incoming Webhook URL.

You don't need to change the Header Fields.

![Demo](./images/slackurl.png)

**Authentication** should be set to **No Authentication**.

![Demo](./images/slackauth.png)

For the **Action Parameters**, you need to define which fields should be sent towards Slack. Logically, we want Adobe Journey Optimizer and Adobe Experience Platform to be the brain of personalization, so the text to send to Slack should be defined by Adobe Journey Optimizer and then sent to Slack for execution.

So for the **Action Parameters**, click the **Edit Payload** icon.

![Demo](./images/slackmsgp.png)

You'll then see an empty popup-window.

![Demo](./images/slackmsgpopup.png)

Copy the below text and paste it in the empty popup window.

```json
{
 "text": {
  "toBeMapped": true,
  "dataType": "string",
  "label": "textToSlack"
 }
}
```

FYI: by specifying the below fields, these fields will become accessible from your Customer Journey and you'll be able to populate them dynamically from the Journey:

**"toBeMapped": true,**

**"dataType": "string",**

**"label": "textToSlack"**

You'll then see this:

![Demo](./images/slackmsgpopup1.png)

Click **Save**.

![Demo](./images/twiliomsgpopup2.png)

Scroll up and click **Save** one more time to save your custom Action.

![Demo](./images/slackmsgpopup3.png)

Your custom Action is now part of the **Actions** list.

![Demo](./images/slackdone.png)

You've defined events, an external data sources and actions. Now let's consolidate all of that in one journey.

Next Step: [12.4 Design a trigger-based journey](./ex4.md)

[Go Back to Module 12](journey-orchestration-external-weather-api-sms.md)

[Go Back to All Modules](../../overview.md)
