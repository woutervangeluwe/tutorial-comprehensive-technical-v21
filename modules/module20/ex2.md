---
title: AI-Driven Chat Apps and Live Chat powered by Stackchat - Build your Luma Bot
description: In this exercise you'll build your Luma bot.
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
exl-id: 90a6e3c3-2aaf-4e61-8053-6367aeef8110
---
# 20.2 Build your Luma Bot

## 20.2.1 Create a new bot

Open the Bots page by clicking the bot icon in the global menu.

![demo](./images/sc9-crunch.png)

Create a new bot by selecting the **Create Bot** button

![demo](./images/ui_create_bot-button.png)

Name your new bot **Luma Bot**, select the **Empty Bot** template and click **Create**.

![demo](./images/ui_create_bot-crunch.png)

## 20.2.2 Create Slots to Capture Data

**Slots** are used to capture data from users, so you'll need to create a slot for each field you'd like to capture. Click the **Slots** button in the bot menu to bring up the Slots Screen.

![demo](./images/ui_slots-crunch.png)

Your Luma Bot will ask the user for their details, such as name and email address. This will allow you to help with them with their order, remember what products they've viewed and will allow them to provide feedback on their experience with Luma. Each slot in the below table enables you to capture one of these data points from the user.

Go ahead and create a slot for each entry in the table below:

| Slot Name       | Slot Type       |
|-----------------|-----------------|
| FirstName       | Text            |
| Email           | Email Address   |
| OrderId         | Text            |
| NpsScore        | Multiple Choice |
| NpsFeedback     | Multiple Choice |
| NPSFeedbackText | Text            |
| viewed_products | Text            |

Your screen should now look like this:

![demo](./images/ui_slots_created-crunch.png)

>[!NOTE]
>
>Note that the final **viewed_products** uses a different naming convention to the other slots. This is because the **viewed_products** slot is only used by cloud functions to store internal state. It's never directly used in conversation with the user, so it uses snake case instead of camel case as a convention to differentiate it from the other slots.

## 20.2.3 Learn CDML Basics

CDML stands for Conversation Design Markup Language. Just like HTML is markup that renders into webpages, CDML is markup that renders into conversations. To see how CDML works, let's create a simple flow and message thread.

Open the Bot Builder screen from the bot menu.

![demo](./images/ui_bot_builder-crunch.png)

Hit the **Create Flow** button and give your flow any name you like. As an example, use **Test Flow**.

![demo](./images/ui_bot_builder_flow-crunch.png)

Click on your flow to open it up and view its children. We just created this flow, so it's empty, but let's change that! Hit the **Create Element** button and choose **Message Thread**.

![demo](./images/ui_flow_details-crunch.png)

Click on your message thread and add a **Text** message by hitting the **+** button in the flyout menu.

![demo](./images/ui_create_message_thread-crunch.png)

Add some words to your test message.

![demo](./images/ui_write_text_message-crunch.png)

Listen up, I'm going to let you in on a little secret. While you were busy creating this message thread, Stackchat Studio was actually storing the underlying conversation data in the form of a CDML file which you can directly view and edit! It sounds like magic and that's because it is - let's take a look!

Your text will be saved automatically, so close the message thread menu and then click the **Edit CDML** button in the top right of the bot builder screen.

![demo](./images/ui_cdml_button-crunch.png)

You will now see that the entire conversation you just created is represented by something that looks a bit like this:

```ruby
bot:
  format: chat
  flows:
    - name: Test Flow
      entry_flow: true
      flow_elements:
        - message_thread:
            name: My Test Message Thread
            entry_element: true
            messages:
              - text:
                  text: Is what I'm writing really going to be represented as CDML?

```

Try re-writing some of your text message and renaming your flow or message thread, then close the CDML editor and you'll see that your changes are represented in the Stackchat Studio UI.

Having a CDML representation of your bot provides the following advantages:

- Portability: easily export/import bots and share them with others
- Auditability: store a history of your bot's content in.version-control to know exactly what state your bot was in at a given point in time.
- Debugging: often times it's much easier to track down and fix issues in your bot using the CDML editor.

## 20.2.4 Import Luma Bot CDML

Lucky for you, we've already created the Luma Bot content and can share it with you as CDML. 

First, download [the latest release of the Stackchat assets here, as a zip file](https://github.com/stackchat-ai/adobe-experience-league-module/releases) to your local desktop and unzip it. 

![demo](./images/cloudfunctionszip1a.png)

After unzipping it you'll have this:

![demo](./images/cloudfunctionszip.png)

Open the folder **adobe-experience-league-module-X.X.X**. 

![demo](./images/cloudfunctionszip3.png)

Next, open the folder **cdml**.

![demo](./images/cloudfunctionszip4.png)

In there, you'll find a file named **luma-bot.cdml**. Open it using any Text Editor of choice.

![demo](./images/cdmlzip1.png)

Open the CDML editor of your Luma Bot, delete all the existing CDML and replace it with the content of **luma-bot.cdml**.

Your bot will now have a few errors, but don't worry! Stackchat Studio's validation engine has kicked in and is just telling you that your bot is referencing cloud functions that don't exist yet. You'll fix this in the next step.

![demo](./images/ui_cdml_paste-crunch.png)

Click the **back** button in the editor and you'll see that your bot builder is now filled with lots of Luma Bot flows. The size of the flow indicates how many children the flow contains. Feel free to explore the various flows and elements to understand how the conversation flows work.

![demo](./images/ui_luma_flows-crunch.png)

Next, let's continue to improve your bot with Cloud Functions...

Next Step: [20.3 Build your Luma Bot - Cloud Functions](./ex3.md)

[Go Back to Module 20](./ai-driven-chat-apps-stackchat.md)

[Go Back to All Modules](./../../overview.md)
