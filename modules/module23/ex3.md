---
title: Adobe Journey Optimizer - Configure a trigger-based journey - Order Confirmation
description: In this section you will configure a trigger-based journey - Order Confirmation
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
exl-id: e52537c1-9909-49f2-9aeb-7701acfe95c4
---
# 23.3 Configure a trigger-based journey - Order Confirmation

Login to Adobe Experience Cloud by going to [Adobe Experience Cloud](https://experience.adobe.com). Click **Adobe Journey Optimizer**.

![Journey Optimizer](./images/23.1-1.png)

You'll be redirected to the **Home** view in Journey Optimizer.

![Journey Optimizer](./images/23.1-3.png)

Before you continue, you need to select a **sandbox**. The sandbox to select is named ``--aepSandboxId--``. You can do this by clicking the text **[!UICONTROL Production Prod]** in the blue line on top of your screen.

![Journey Optimizer](./images/23.1-3a.png)

## 23.3.1 Create your order confirmation message

In the menu, click **Messages**. 

On the Messages screen, you’ll see a view similar to this. Click **Create Message**.

![Journey Optimizer](./images/oc1.png)

Give your Message a title following this naming convention **ldap  - Order Confirmation Email** and replace **ldap** by your own ldap, select the **CJM Alpha Preset** and enable the **Email** channel. 

![Journey Optimizer](./images/oc2.png)

Click **Create** to create your Order Confirmation Email message.

The next screen is the message dashboard. On the right-hand side are the Email properties, make sure that the 2 checkboxes under **Optional features** are checked. If not, please **make sure they are both activated**. 

![Journey Optimizer](./images/oc3.png)

Click the **Subject line** text field.

![Journey Optimizer](./images/oc4.png)

In the text area start writing **Thanks for your order,**

![Journey Optimizer](./images/oc5.png)

The subject line is not done yet. Next you need to bring in the personalization token for the field **First name** which is stored under `profile.person.name.firstName`. In the left menu, scroll down to find the **Person** > **Full name** >  **First name** field and click on the **+** icon to add the personalization token into the subject line. Click **Save**.

![Journey Optimizer](./images/oc6.png)

You'll then be back here. Click **Email Designer** to create the email's content. 

![Journey Optimizer](./images/oc7.png)

In the next screen, click **Design from scratch**.

![Journey Optimizer](./images/oc8.png)

In the left menu, you'll find the structure components that you can use to define the structure of the email (rows and columns).

Drag and drop 8 times a **1:1 column** on the canvas, which should give you this:

![Journey Optimizer](./images/oc9.png)

Go to **Content Components**.

![Journey Optimizer](./images/oc10.png)

Drag and drop an **HTML** component on the first row. Click the HTML component and then click **Show the source code**.

![Journey Optimizer](./images/oc11.png)

Paste this code there: `<img src="{%= profile._experienceplatform.demoEnvironment.brandLogo %}" width="100px%">`. Click **Save**.

![Journey Optimizer](./images/oc12.png)

You're now back here:

![Journey Optimizer](./images/oc13.png)

Go to **Content Components** and drag and drop an **Image** component on the second row. Select the **Image component** but DON'T click Browse.

![Journey Optimizer](./images/oc14.png)

Paste this image URl in the field **Source**: `https://parsefiles.back4app.com/hgJBdVOS2eff03JCn6qXXOxT5jJFzialLAHJixD9/29043bedcde632a9cbe8a02a164189c9_preparing.png`. This image is hosted outside of Adobe.

![Journey Optimizer](./images/oc15.png)

When you change the scope to another field, the image will be rendered and you'll see this:

![Journey Optimizer](./images/oc16.png)

Next, go to **Content Components** and drag and drop a **Text** component on the third row. 

![Journey Optimizer](./images/oc17.png)

Select the default text in that component **Please type your text here.** and replace it by the below text:

```javascript
You’re one step closer!

Hi 

We've received your order details!

We will also send you a separate email containing your VAT Invoice.

We'll be back in touch with you as soon as we've finished packing your package. Please read carefully the Order Information detailed below.
```

![Journey Optimizer](./images/oc18.png)

Put the cursor next to the text **Hi** and click **Add Personalization**.

![Journey Optimizer](./images/oc19.png)

Navigate to the **Person** > **Full name** > **First name** field and click on the **+** icon to add the personalization token into the subject line. Click **Save**.

![Journey Optimizer](./images/oc20.png)

You'll then see this:

![Journey Optimizer](./images/oc21.png)

Next, go to **Content Components** and drag and drop a **Text** component on the fourth row. 

![Journey Optimizer](./images/oc22.png)

Select the default text in that component **Please type your text here.** and replace it by the below text:

`Order Information`

Change the font size to **26px** and center your text in this cell. You'll then have this:

![Journey Optimizer](./images/oc23.png)

Next, go to **Content Components** and drag and drop an **HTML** component on the fifth row. Click the HTML component and then click **Show the source code**.

![Journey Optimizer](./images/oc24.png)

In the **Edit HTML** popup, paste this HTML:

```<table><tbody><tr><td><b>Items purchased</b></td><td></td><td><b>Quantity</b></td><td><b>Subtotal</b></td></tr><tr><td colspan="4" width="500"><hr></td></tr></tbody></table>```

Click **Save**.

![Journey Optimizer](./images/oc25.png)

You'll then have this. Click **Save** to save your progress.

![Journey Optimizer](./images/oc26.png)

Go back to the message dashboard by clicking the **arrow** next to the subject line text in the top-left corner.

![Journey Optimizer](./images/oc27.png)

You'll then see this:

![Journey Optimizer](./images/oc28.png)

Click **Publish** twice to publish your message so you can use it in a journey.

![Journey Optimizer](./images/oc29.png)

In the next steps of creating your **Order Confirmation Email Message**, you'll need to use contextual event data. This contextual event data is provided from within the **Journey**. So before you can add that context, you'll need to setup an **Event** to trigger the journey, and build out the **Journey**. Once that's done, you'll come back to the **Message Designer** to update your message.

## 23.3.2 Create your event

In the menu, go to **Configurations** and click **Manage** under **Events**.

![Journey Optimizer](./images/oc30.png)

On the **Events** screen, you'll see a view similar to this. Click **Create Event**.

![Journey Optimizer](./images/oc31.png)

You'll then see an empty event configuration.

![Journey Optimizer](./images/oc32.png)

First of all, give your Event a Name like this: `ldapPurchaseEvent` and replace `ldap` with your ldap.

![Journey Optimizer](./images/oc33.png)

Next, add a description like this `Purchase Event`.

![Journey Optimizer](./images/oc34.png)

Next is the **Event Type** selection. Select **Unitary**.

![Journey Optimizer](./images/eventidtype1.png)

Next is the **Event ID Type** selection. Select **System Generated**

![Journey Optimizer](./images/eventidtype.png)

Next is the Schema selection. A schema was prepared for this exercise. Please use the schema `Demo System - Event Schema for Website (Global v1.1) v.1`.

![Journey Optimizer](./images/oc35.png)

After selecting the Schema, you'll see a number of fields being selected in the **Payload** section. Click the **Edit/Pencil** icon to add additional fields to this event.

![Journey Optimizer](./images/oc36.png)

You'll then see this popup. You now need to check additional checkboxes in order to access additional data when this event gets triggered.

![Journey Optimizer](./images/oc37.png)

First of all, check the checkbox on the line `--aepTenantId--`.

![Journey Optimizer](./images/oc38.png)

Next, scroll down and check the checkbox on the line `productListItems`. 

![Journey Optimizer](./images/oc39.png)

Next, scroll down and check the checkbox on the line `commerce`. 

![Journey Optimizer](./images/oc391.png)

Next, click **Ok**.

You'll then see that additional fields have been added to the event. Click **Save**.

![Journey Optimizer](./images/oc40.png)

Your new event is then shared and you'll see your event in the list of available events now.

Click on your event again to open up the **Edit Event** screen again. 
Hover over the **Payload** field again to see the 3 icons again. Click on the **View Payload** icon. 

![Journey Optimizer](./images/oc41.png)

You'll now see an example of the expected payload. Your event has a unique orchestration eventID, which you can find by scrolling down in that payload until you see `_experience.campaign.orchestration.eventID`.

![Journey Optimizer](./images/oc42.png)

The event ID is what needs to be sent to Adobe Journey Optimizer in order to trigger the journey that you'll build in the next step. Write down this eventID, as you'll need it in one of the next steps.
`"eventID": "d168c11ce1b5bb96fc793421fbcc3ec54b3116fa13242b05d9a54b1251ecb94e"`

Click **Ok**, followed by **Cancel**.

Your event is now configured and ready to be used.

## 23.3.3 Create your journey

In the menu, go to **Journeys** and click **Create Journey**.

![Journey Optimizer](./images/oc43.png)

You'll then see this.

![Journey Optimizer](./images/oc44.png)

Give your journey a name. Use **ldap - Order Confirmation journey** and replace **ldap** by your ldap. Click **OK**.

![Journey Optimizer](./images/oc45.png)

First, you need to add your event as the starting point of your journey. Search for your event **ldapPurchaseEvent** and drag and drop it onto the canvas. Click **OK**.

![Journey Optimizer](./images/oc46.png)

Next, under **Actions**, search for the **Message** action.

![Journey Optimizer](./images/oc47.png)

Drag and drop the **Message** action onto the canvas and click the **edit** icon to select your message.

![Journey Optimizer](./images/oc48.png)

Select the message you created in the previous step, **ldap - Order Confirmation Email**. Click **Select**.

![Journey Optimizer](./images/oc49.png)

You then have this. Click **Ok**.

![Journey Optimizer](./images/oc50.png)

Search for the orchestration type **End** and drag and drop it onto the canvas. Click **OK**.

![Journey Optimizer](./images/oc51.png)

Click **Publish** to publish journey.

![Journey Optimizer](./images/oc511.png)

Click **Publish** again.

![Journey Optimizer](./images/oc512.png)

Go back to the Journeys overview.

![Journey Optimizer](./images/oc513.png)

Your journey is now published. Before you can use the journey, you still need to finish configuring your Order Confirmation Email message. To do that, you now need to provide the context of this journey to your message.

## 23.3.4 Use journey context in email message

From the Journeys overview, open your **ldap - Order Confirmation journey** again.

![Journey Optimizer](./images/oc513.png)

Select the **Message** action again. Hover over the **Message** field and you'll see this option. Click **Open the message**.

![Journey Optimizer](./images/oc52.png)

You'll then be redirected here. Click **Modify**.

![Journey Optimizer](./images/oc53.png)

Click **Confirm**.

![Journey Optimizer](./images/oc54.png)

Click **Email Designer**.

![Journey Optimizer](./images/oc55.png)

You'll then be back in the Email Designer.

![Journey Optimizer](./images/oc56.png)

Go to **Content Components** and drag and drop an **HTML** component on the sixth row. Click the HTML component and then click **Show the source code**.

![Journey Optimizer](./images/oc57.png)

In the **Edit HTML** popup, paste this HTML:

```{{#each xxx as |item|}}<table width="500"><tbody><tr><td><img src="{{item.--aepTenantId--.core.imageURL}}" width="100"></td><td><table><tbody><tr><td><b>{{item.name}}</b><br>{{item.--aepTenantId--.core.subCategory}}<br><b>{{item.priceTotal}}</b><br>&nbsp;<br>Article no: {{item.SKU}}</td></tr></tbody></table></td><td>{{item.quantity}}</td><td><b>{{item.priceTotal}}</b></td></tr></tbody></table>{{/each}}```

You'll then have this:

![Journey Optimizer](./images/oc58.png)

You now have to replace **xxx** by a reference to the productListItems object that is part of the event that triggers the journey.

![Journey Optimizer](./images/oc59.png)

First, delete **xxx** in your HTML code first.

![Journey Optimizer](./images/oc60.png)

Open the dropdown that says **Profile**. In that dropdown, select **Context**. This context is passed to the message from the journey.

![Journey Optimizer](./images/oc601.png)

You'll then see this. Click the arrow next to **Journey Orchestration** to drill deeper.

![Journey Optimizer](./images/oc61.png)

Click the arrow next to **Events** to drill deeper.

![Journey Optimizer](./images/oc62.png)

Click the arrow next to **ldapPurchaseEvent** to drill deeper.

![Journey Optimizer](./images/oc63.png)

Click the **+** icon next to **productListItems** to add it to the HTML code.

![Journey Optimizer](./images/oc64.png)

You'll then have this. You now need to remove the **ticks** around the event ID.

![Journey Optimizer](./images/oc65.png)

You'll then have this. Click **Save**.

![Journey Optimizer](./images/oc66.png)

You'll be back in the Email Designer now. Click **Save** to save your progress.

![Journey Optimizer](./images/oc67.png)

Next, go to **Content Components** and drag and drop an **HTML** component on the seventh row. Click the HTML component and then click **Show the source code**.

![Journey Optimizer](./images/oc68.png)

In the **Edit HTML** popup, paste this HTML:

```<table><tbody><tr><td><b>Subtotal</b><br>Delivery charge (included)</td><td align="right"><b>xxx</b><br><b>5</b></td></tr><tr><td colspan="2" width="500"><hr></td></tr><tr><td><b>Total including VAT</b></td><td align="right"><b>xxx</b></td></tr></tbody></table>```

There are 2 references of **xxx** in this HTML code. You now have to replace each **xxx** by a reference to the productListItems object that is part of the event that triggers the journey.

![Journey Optimizer](./images/oc69.png)

First, delete **xxx** in your HTML code on line 10.

![Journey Optimizer](./images/oc71.png)

Navigate to **Context**.

![Journey Optimizer](./images/oc711.png)

Click the arrow next to **Journey Orchestration** to drill deeper.

![Journey Optimizer](./images/oc72.png)

Drill deeper into the object **ldapPurchaseEvent**. Click the arrow next to **Commerce** to drill deeper.

![Journey Optimizer](./images/oc73.png)

Click the arrow next to **Order** to drill deeper.

![Journey Optimizer](./images/oc74.png)

Click the **+** icon next to **Price Total** to add that to the canvas.

![Journey Optimizer](./images/oc75.png)

Delete **xxx** in your HTML code on line 23. 

![Journey Optimizer](./images/oc76.png)

Click the **+** icon next to **Price Total** again to add that to the canvas.

![Journey Optimizer](./images/oc77.png)

You can also add the field **Currency** from within the **Order** object onto the canvas, as you can see here:

![Journey Optimizer](./images/oc771.png)

When you're done, click **Save** to save your changes.

You'll then be back in the Email Designer. Click **Save** again.

![Journey Optimizer](./images/oc78.png)

Go back to the message dashboard by clicking the **arrow** next to the subject line text in the top-left corner.

![Journey Optimizer](./images/oc79.png)

You'll then see this:

![Journey Optimizer](./images/oc80.png)

Click **Publish** twice to publish your message so you can use it in a journey.

![Journey Optimizer](./images/oc81.png)

After making a change to the email message, you need to republish the journey so that it picks up the new fields and changes.

To do so, go to **Journeys**. Click to open your journey **ldap - Order Confirmation journey**.

![Journey Optimizer](./images/oc83.png)

Click to open the dropdown next to **Duplicate** and select **Create a new version**.

![Journey Optimizer](./images/oc84.png)

Click **Create a new version** again.

![Journey Optimizer](./images/oc85.png)

You'll then have a new version of your journey. Click **Publish** twice.

![Journey Optimizer](./images/oc86.png)

Your journey is now published and can be triggered. Before you can trigger it though, you need to update the data element in your Adobe Experience Platform Data Collection Client property.

## 23.3.5 Update your Adobe Experience Platform Data Collection Client property

Go to [https://experience.adobe.com/#/data-collection/](https://experience.adobe.com/#/data-collection/). In the left menu, make sure you're in **Client**. Search for your Client properties, and open the property for **Web**.

![Journey Optimizer](./images/oc90.png)

Go to **Data Elements**. Search and open the data element **rulePurchaseConfirmation**.

![Journey Optimizer](./images/oc91.png)

You'll then see this. Navigate to the field **_experience.campaign.orchestration.eventID** and fill out your eventID here. The eventID to fill out here, is the eventID you created as part of exercise 23.3.2.

![Journey Optimizer](./images/oc92.png)

Save your changes in your Client property, and then publish your changes by updating your development library.

![Journey Optimizer](./images/oc93.png)

Your changes are now deployed and can be tested.

## 23.3.6 Test your order confirmation email using the demo website

Let's test the updated journey by buying a product on the demo website.

Open a new, clean incognito browser window and go to [https://public.aepdemo.net](https://public.aepdemo.net). 

You'll then see this. 

![Launch Setup](./images/cdemo1.png)

Enter your Configuration ID and click **Load Configuration**. Your configuration is then loaded.

![Launch Setup](./images/cdemo2.png)

Scroll down and click **Save Configuration**.

![Launch Setup](./images/cdemo3.png)

You'll then be redirected to the Admin homepage. Go to **Select LDAP**. Select your LDAP and click **Save**.

![Launch Setup](./images/cdemo5.png)

You'll then be redirected to the Admin homepage. Go to **Select Brand** and select the brand **Luma**, click **Save**.

![Launch Setup](./images/cdemo7.png)

You'll then be redirected to the Admin homepage. Click the **Luma** logo.

![Launch Setup](./images/cdemo8.png)

You'll then see the Luma homepage.

![Launch Setup](./images/cdemo9.png)

Go to **Login/Register**. Fill out the form and click **Create Account**. Don't forget to check the checkbox for **Test Profile**.

![Journey Optimizer](./images/23.2-18.png)

Within a few seconds you'll receive the new Account Creation email served by Journey Optimizer in your inbox as you configured in the previous exercise.

![Journey Optimizer](./images/23.2-17.png)

Go back to the homepage of the demo website and click any product.

![Journey Optimizer](./images/oc94.png)

You'll then see the product detail page. Click **Add to cart**.

![Journey Optimizer](./images/oc95.png)

Go to your cart.

![Journey Optimizer](./images/oc96.png)

Select your **payment type** and **delivery preference**, and then click **Purchase**.

![Journey Optimizer](./images/oc97.png)

You'll then receive your order confirmation email within seconds.

![Journey Optimizer](./images/oc98.png)

You have finished this exercise.

Next Step: [23.4 Configure a batch-based newsletter journey](./ex4.md)

[Go Back to Module 23](./journeyoptimizer.md)

[Go Back to All Modules](../../overview.md)
