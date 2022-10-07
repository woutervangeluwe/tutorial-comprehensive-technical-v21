---
title: Introduction to Journey Optimizer
description: This section describes the overall Journey Optimizer user interface and explains how to create email messages. An account creation email will be created and used for the triggered journey, a newsletter email will be created and used in a batch email campaign in a later exercise.
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
exl-id: bcc6ef9f-fc99-492b-8721-5d05f04b7f54
---
# 23.1 Introduction to Adobe Journey Optimizer: build an email message

Login to Adobe Experience Cloud by going to [Adobe Experience Cloud](https://experience.adobe.com). Click **Adobe Journey Optimizer**.

![Journey Optimizer](./images/23.1-1.png)

You'll be redirected to the **Home** view in Journey Optimizer.

![Journey Optimizer](./images/23.1-3.png)

Before you continue, you need to select a **sandbox**. The sandbox to select is named ``--aepSandboxId--``. You can do this by clicking the text **[!UICONTROL Production Prod]** in the blue line on top of your screen.

![Journey Optimizer](./images/23.1-3a.png)

The top of the home page shows the recent objects you have been working on so you can quickly go back to a particular one. 

![Journey Optimizer](./images/23.1-4.png)

The left-hand side shows the navigation menu which will bring you to different places in Journey Optimizer.

- **Home**: The page you are currently on.
- **Journeys**: Overview of existing journeys, create new journeys
- **Messages**: Overview of existing messages (email, push,...), create new messages and find an overview of message execution in the last 24 hours.
- **Assets**: Redirects you to Adobe Experience Manager Assets Essentials where files like images can be uploaded to be used in messages.
- **Segments**: Access and create segments.
- **Datasets & Schemas**: Provides you an overview of all schemas and datasets.
- **Configurations**: Manage custom events, external data sources and actions to be used in the journeys.

![Journey Optimizer](./images/23.1-5.png)

In the menu, click **Messages**. 

On the Messages screen, you’ll see a view similar to this. Click **Create Message**.

![Journey Optimizer](./images/23.1-6.png)

Give your Message a title following this naming convention **ldap - Registration Email** and replace **ldap** by your own ldap, select the **CJM Alpha Preset** and enable the **Email** channel. 

![Journey Optimizer](./images/23.1-7.png)

Click on the **Create** button to create your Registration Email message.

The next screen is the message dashboard, from there you will be able to see the email thumbnail when the content will be provided

![Journey Optimizer](./images/23.1-8.png)

On the right-hand side are the Email properties:

- **From email**: the email address from whom the recipient will receive email message. Note that this value is specified by the **preset** given in the previous step and is read-only.
- **From name**: the sender name  from whom the recipient will receive email message. Note that this value is specified by the **preset** given in the previous step and is read-only.
- **Subject line**: the mandatory subject of the message which will be edited in the next step. 
- **Body**: a button brings you to the Email Designer to create and edit the email content.
- **Optional features**: these two checkboxes allow to disable the tracking of the email's opens and email's clicks and therefore, prevent the message from measuring metrics like open rate, click-through rate,...

First, make sure that the 2 checkboxes under **Optional features** are checked. If not, please **make sure they are both activated**. 

![Journey Optimizer](./images/23.1-8bis.png)

Click the **Subject line** text field.

![Journey Optimizer](./images/23.1-9.png)

In the text area start writing **Hi**

![Journey Optimizer](./images/23.1-10.png)

The subject line is not done yet. Next you need to bring in the personalization token for the field **First name** which is stored under `profile.person.name.firstName`. In the left menu, scroll down to find the **Person** element and click on the arrow to go a level deeper.

![Journey Optimizer](./images/23.1-11.png)

Now find the **Full name** element and click on the arrow to go a level deeper.

![Journey Optimizer](./images/23.1-12.png)

Finally, find the **First name** field and click on the **+** sign next to it. You'll then see the personalization token appear in the text field.

![Journey Optimizer](./images/23.1-13.png)

Next, add the text **,thank you for signing up!**. Click **Save**.

![Journey Optimizer](./images/23.1-14.png)

You'll then be back here. Click **Email Designer** to create the email's content. 

![Journey Optimizer](./images/23.1-15.png)

In the next screen you will be prompted with 3 different methods to provide the email's content:

- **Design from scratch**: Start with a blank canvas and use the WYSIWYG-editor to drag and drop structure and content components to visually build up the email's content.
- **Code your own**: Create your own email template by coding it using HTML
- **Import HTML**: Import an existing HTML template, which you'll be able to edit.

Click **Design from scratch**.

![Journey Optimizer](./images/23.1-16.png)

In the left menu, you'll find the structure components that you can use to define the structure of the email (rows and columns).

![Journey Optimizer](./images/23.1-18.png)

Drag and drop a **1:2 column Left** from the menu into the canvas. This will be the placeholder for the logo image.

![Journey Optimizer](./images/23.1-19.png)

Drag and drop a **1:1 column** underneath the previous component. This will be the banner block.

![Journey Optimizer](./images/23.1-20.png)

Drag and drop a **1:2 column Left** underneath the previous component. This will be the actual content with an image on the left side and text on the right side.

![Journey Optimizer](./images/23.1-21.png)

Next, drag and drop a **1:1 column** underneath the previous component. This will be email's footer. Your canvas should now look like this:

![Journey Optimizer](./images/23.1-22.png)

Now let's use Content Components to add content inside these blocks. Click on the **Content Components** menu item

![Journey Optimizer](./images/23.1-23.png)

Drag and drop an **HTML** component in the first cell on the first row. 

![Journey Optimizer](./images/23.1-24.png)

Click the HTML component and then click **Show the source code**.

![Journey Optimizer](./images/23.1-25.png)

You'll then see this:

![Journey Optimizer](./images/sourcecode1.png)

Paste this code there: `<img src="{%=  %}" width="100px%">`.

![Journey Optimizer](./images/sourcecode2.png)

Then put the cursor, as indicated in the screenshot:

![Journey Optimizer](./images/sourcecode3.png)

Next, navigate to the field `--aepTenantId--.demoEnvironment.brandLogo`. Click the **+** icon to insert the personalization token. Next, click **Save**.

![Journey Optimizer](./images/sourcecode4.png)

You've now configured this HTML component to dynamically take the image URL from a field within Adobe Experience Platform's Real-time Customer Profile.

You're now back here:

![Journey Optimizer](./images/sourcecode5.png)

Go to **Content Components** and drag and drop an **Image** component in the first cell on the first row. 

![Journey Optimizer](./images/sourcecode6.png)

Click **Browse**.

![Journey Optimizer](./images/sourcecode7.png)*

In the **Assets** pop-up, double-click the **module-23** folder. In this folder, you'll find all assets previously prepared and uploaded by the creative team.

![Journey Optimizer](./images/23.1-26.png)

Select **module23-thankyou-new.png** and click **Select**. 

![Journey Optimizer](./images/23.1-27.png)

You'll then have this:

![Journey Optimizer](./images/23.1-28a.png)

Select your image and in the right menu, scroll down until you see the **Size** width slider component.

![Journey Optimizer](./images/23.1-29.png)

Use the slider to change the width to f.i. **60%**.

![Journey Optimizer](./images/23.1-30.png)

Next, go to **Content Components** and drag and drop a **Text** component in the structure component on the fourth row. 

![Journey Optimizer](./images/23.1-30a.png)

You'll then see this:

![Journey Optimizer](./images/textacc.png)

Select the default text **Please type your text here.** as you would do with any text editor. Write **Dear** instead. Notice the text toolbar displayed when you are in text mode.

![Journey Optimizer](./images/23.1-31.png)

In the toolbar click the **Add personalization** icon.

![Journey Optimizer](./images/23.1-32.png)

Next, you need to bring the **First name** personalization token which is stored under `profile.person.name.firstName`. In the menu, find the **Person** element, drill down to the **Full Name** element, and then click the **+** icon to add the First Name field onto to expression editor.

Click **Save**.

![Journey Optimizer](./images/23.1-33.png)

You'll now notice how the personalization field has been added to your text. 

![Journey Optimizer](./images/23.1-36.png)

In the same text field, hit **Enter** twice to add two lines and write **Thank you for signing up for**.

![Journey Optimizer](./images/23.1-37.png)

Click **Add personalization** again.

![Journey Optimizer](./images/23.1-38.png)

Next, you need to bring in the **Brand Name** personalization token which is stored under `--aepTenantId--.demoEnvironment.brandName`. In the left hand-side list find the `--aepTenantId--` element and click on the arrow to go a level deeper.

![Journey Optimizer](./images/23.1-39.png)

Next, find the **demoEnvironment** element and click the arrow to go a level deeper.

![Journey Optimizer](./images/23.1-40.png)

Finally, find the field **brandName** and click on the **+** sign next to it. You'll then see the personalization token appear in the text field. Click **Save**.

![Journey Optimizer](./images/23.1-41.png)

You'll now notice how the personalization field has been added to your text. 

![Journey Optimizer](./images/23.1-43.png)

In the left menu, go back to **Structure Components**.

Drag and drop a **1:1 column** underneath the previous component. This will be the banner block.

![Journey Optimizer](./images/strucnew.png)

Next, go to **Content Components** and drag and drop a **Text** component in the fifth row.

![Journey Optimizer](./images/23.1-44.png)

Replace the default text by **Not interested anymore? Unsubscribe instantly.**

![Journey Optimizer](./images/23.1-45.png)

Now select the word **Unsubscribe** and click on the **Insert link** icon in the toolbar.

![Journey Optimizer](./images/23.1-46.png)

In the Link type dropdown select **Unsubscription link** and put the following url inside the Unsubscription page URL textfield **https://www.optout.adobe.com**. Click **Save**.

![Journey Optimizer](./images/23.1-47.png)

The registration confirmation email now has content, for deliverability (best practices around email sending to ensure they land in the recipient's mailbox instead of the Spam folder) purposes it is also important that this email has a text version.

Click the **Plain text** button at the top of the Email Designer to see how Journey Optimizer has automatically synchronized the HTML with the text version, so you don't have to write the text one more time.

![Journey Optimizer](./images/23.1-49.png)

The final check to perform to ensure your email is ready is to preview it, click on the **Preview** button.

![Journey Optimizer](./images/23.1-50.png)

Start by identifying which profile you want to use for the preview. Select the **email** namespace by clicking on the icon next to **Enter identity namespace** field.

![Journey Optimizer](./images/23.1-51.png)

In the list of identity namespaces, select the **Email** namespace. Click **Select**.

![Journey Optimizer](./images/23.1-52.png)

In the **Identity value** field, enter the email address of a previous demo profile that is already stored in the Real-time Customer Profile. For example **woutervangeluwe+31052021-10@gmail.com** and click on the **Find Test Profile** button

![Journey Optimizer](./images/23.1-54.png)

Once your profile shows up in the table, click on the **Preview** tab to access the preview screen.

When the preview is ready, validate that the personalization is correct in the subject line, the body text as well as the unsubscription link is highlighted as an hyperlink.

Click **Close** to close the preview.

![Journey Optimizer](./images/23.1-56.png)

Click **Save** to save your message.

![Journey Optimizer](./images/23.1-58.png)

Go back to the message dashboard by clicking the **arrow** next to the subject line text in the top-left corner.

![Journey Optimizer](./images/23.1-59.png)

You've now completed the draft version of your registration email. Click **Publish** to publish your message so you can use it in a journey.

![Journey Optimizer](./images/23.1-60.png)

Click **Publish** again.

![Journey Optimizer](./images/23.1-61.png)

Wait until you see a green confirmation pop-up at the bottom of the screen indicating that the message is published. 

![Journey Optimizer](./images/23.1-62.png)

You have finished this exercise.

Next Step: [23.2 Configure a trigger-based journey - Account Creation](./ex2.md)

[Go Back to Module 23](./journeyoptimizer.md)

[Go Back to All Modules](../../overview.md)
