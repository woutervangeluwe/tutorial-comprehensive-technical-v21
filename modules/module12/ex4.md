---
title: Adobe Journey Optimizer - External Weather API, SMS Action & more - Design a trigger-based Customer Journey
description: Adobe Journey Optimizer - External Weather API, SMS Action & more - Design a trigger-based Customer Journey
kt: 5342
audience: Data Engineer, Data Architect, Orchestration Engineer, Marketer
doc-type: tutorial
activity: develop
exl-id: 6bec303b-b58a-4b9f-8ded-5e7354cf06b6
---
# 12.4 Design a trigger-based journey

In this exercise, you'll create a journey by making use of Adobe Journey Optimizer.

Login to Adobe Journey Optimizer by going to [Adobe Experience Cloud](https://experience.adobe.com). Click **Journey Optimizer**.

![ACOP](./images/acophome.png)

You'll be redirected to the **Home**  view in Journey Optimizer.

![ACOP](./images/acoptriglp.png)

First, make sure you're using the correct sandbox. The sandbox to use is called `--aepSandboxId--`. To change from one sandbox to another, click on **PRODUCTION Prod (VA7)** and select the sandbox from the list. In this example, the sandbox is named **AEP Enablement FY21**.

![ACOP](./images/sb.png)

You'll then be in the **Home** view of your sandbox `--aepSandboxId--`.

![ACOP](./images/home.png)

Click **Create** to start creating your Journey.

![Demo](./images/jocreate.png)

In the left menu, go to **Journeys**. Next, click **Create Journey**.

![Demo](./images/jonew.png)

You should first name your Journey.

As a Name for the Journey, use `ldap Geofence Entry Journey` and replace `ldap` with your ldap. In this example, the Journey Name is `vangeluw Geofence Entry Journey`. No other values must be set at this moment.

![Demo](./images/joname.png)

Click **OK**.

![Demo](./images/jonameok.png)

On the left side of your screen, have a look at **Events**. You should see your previously created event in that list. Select it, then drag and drop it on the journey canvas. Your journey then looks like this:

![Demo](./images/joevents.png)

Next, click on **Orchestration**. You now see the available **Orchestration** capabilities. Select **Condition**, then drag and drop it on the Journey Canvas.

![Demo](./images/jo2.png)

You now have to define three conditions:

- It's colder than 10° Celsius
- It's between 10° and 25° Celsius
- It's warmer than 25° Celsius

Let's define the first condition.

## Condition 1: Colder than 10° Celsius

Click on the **Condition**.  Click on **Path1** and edit the name of the path to **Colder than 10 C**. Click on the **Edit** icon for the expression of Path1.

![Demo](./images/jo5.png)

You'll then see an empty **Simple Editor** screen. Your query will be a bit more advanced, so you'll need the **Advanced Mode**. Click **Advanced Mode**.

![Demo](./images/jo7.png)

You'll then see the **Advanced Editor** which allows code entry.

![Demo](./images/jo9.png)

Select the below code and paste it in the **Advanced Editor**.

`#{ldapWeatherApi.ldapWeatherByCity.main.temp} <= 10` (replace ldap by your ldap)

You'll then see this.

![Demo](./images/jo10.png)

In order to retrieve the temperature as part of this condition, you need to provide the city in which the customer currently is.
The **City** needs to be linked to the dynamic parameter `q`, just like we saw previously in the Open Weather API Documentation.

Click the field **dynamic val: q** as indicated in the screenshot.

![Demo](./images/jo11.png)

You then need to find the field that contains the current city of the customer in one of the available Data Sources.

![Demo](./images/jo12.png)

You can find the field by navigating to ```ldapGeofenceEntry.placeContext.geo.city``` (replace ldap by your ldap).

By clicking that field, it will be added as the dynamic value for the parameter `q`. This field will be populated by for instance the geolocation-service that you've implemented in your mobile app. In our case we will simulate this with the admin console of the demo website. Click **OK**.

![Demo](./images/jo13.png)

## Condition 2: Between 10° and 25° Celsius

After having added the first condition, you'll see this screen. Click **Add Path**.

![Demo](./images/joc2.png)

Double click on **Path1** and edit the path name to **Between 10 and 25 C**. Click the **Edit** icon for the expression this path.

![Demo](./images/joc6.png)

You'll then see an empty **Simple Editor** screen. Your query will be a bit more advanced, so you'll need the **Advanced Mode**. Click **Advanced Mode**.

![Demo](./images/jo7.png)

You'll then see the **Advanced Editor** which allows code entry.

![Demo](./images/jo9.png)

Select the below code and paste it in the **Advanced Editor**.

`#{ldapWeatherApi.ldapWeatherByCity.main.temp} > 10 and #{ldapWeatherApi.ldapWeatherByCity.main.temp} <= 25` (Replace ldap by your ldap)

You'll then see this.

![Demo](./images/joc10.png)

In order to retrieve the temperature as part of this Condition, you need to provide the city in which the customer currently is.
The **City** needs to be linked to the dynamic parameter **q**, just like we saw previously in the Open Weather API Documentation.

Click the field **dynamic val: q** as indicated in the screenshot.

![Demo](./images/joc11.png)

You then need to find the field that contains the current city of the customer in one of the available Data Sources.

![Demo](./images/jo12.png)

You can find the field by navigating to ```ldapGeofenceEntry.placeContext.geo.city``` (Replace ldap by your LDAP). By clicking that field, it will be added as the dynamic value for the parameter **q**. This field will be populated by for instance the geolocation-service that you've implemented in your mobile app. In our case we will simulate this with the admin console of the demo website. Click **OK**.

![Demo](./images/jo13.png)

Next, you'll add the 3rd condition.

## Condition 3: Warmer than 25° Celsius

After having added the second condition, you'll see this screen. Click **Add Path**.

![Demo](./images/joct2.png)

Double click on Path1 to change the name to **Warmer than 25 C**. 
Then click on the **Edit** icon for the expression this path.

![Demo](./images/joct6.png)

You'll then see an empty **Simple Editor** screen. Your query will be a bit more advanced, so you'll need the **Advanced Mode**. Click **Advanced Mode**.

![Demo](./images/jo7.png)

You'll then see the **Advanced Editor** which allows code entry.

![Demo](./images/jo9.png)

Select the below code and paste it in the **Advanced Editor**.

`#{ldapWeatherApi.ldapWeatherByCity.main.temp} > 25` (Replace ldap by your LDAP)

You'll then see this.

![Demo](./images/joct10.png)

In order to retrieve the temperature as part of this Condition, you need to provide the city in which the customer currently is.
The **City** needs to be linked to the dynamic parameter **q**, just like we saw previously in the Open Weather API Documentation.

Click the field **dynamic val: q** as indicated in the screenshot.

![Demo](./images/joct11.png)

You then need to find the field that contains the current city of the customer in one of the available Data Sources.

![Demo](./images/jo12.png)

You can find the field by navigating to ```ldapGeofenceEntry.placeContext.geo.city```. By clicking that field, it will be added as the dynamic value for the parameter **q**. This field will be populated by for instance the geolocation-service that you've implemented in your mobile app. In our case we will simulate this with the admin console of the demo website. Click **OK**.

![Demo](./images/jo13.png)

You now have three configured paths. Click **Ok**.

![Demo](./images/jo3path.png)

As this is a journey for learning purpose, we'll now configure a couple of actions to showcase the variety of options marketeers now have to deliver messages.

## Send messages for path Colder than 10° Celsius

For each of the temperature contexts, we'll attempt to send an SMS Message to our customer. We can only send an SMS if we have a Mobile Number available for a customer, so we'll first have to verify that we do.

Let's focus on **Colder than 10 C**.

![Demo](./images/p1steps.png)

Let's take another **Condition** element and drag it as indicated in the screenshot below. We'll verify if for this customer, we have a mobile number available.

![Demo](./images/joa1.png)

As this is just an example, we are only configuring the option where the customer has a mobile number available. Add a label of **Has mobile?**.

Click on the **Edit** icon for the Expression for the **Path1** path.

![Demo](./images/joa2.png)

In the Data Sources shown on the left, navigate to **ExperiencePlatform.ProfileFieldGroup.profile.mobilePhone.number**. You're now reading the mobile phone number directly from Adobe Experience Platform's Real-time Customer Profile.

![Demo](./images/joa3.png)

Select the field **Number**, then drag and drop it to the Condition Canvas.

Select the operator **is not empty**. Click **Ok**.

![Demo](./images/joa4.png)

You'll then see this:

![Demo](./images/joa6.png)

Your journey will then look like this. Click on **Actions** as indicated in the screenshot.

![Demo](./images/joa8.png)

Select the action `ldapSmsTwilio` (verify your ldap), then drag and drop it after the condition you just added.

![Demo](./images/joa9.png)

You'll see a panel on the right hand side where you can configure the action.

![Demo](./images/joa10.png)

Navigate to the **Action Parameters**. Click on the **Edit** icon for the Action Parameter **TEXTMESSAGE**.

![Demo](./images/joa11.png)

You'll then see this. Click on **Advanced Mode**.

![Demo](./images/joa12.png)

Select the below code, copy it and paste it in the **Advanced Mode Editor**. Click **OK**.

`"Brrrr..." + #{ExperiencePlatform.ProfileFieldGroup.profile.person.name.firstName} + " It's freezing. 20% discount on Jackets today!"`

![Demo](./images/joa14.png)

You'll then be back here. Click on the **Edit** icon for the Action Parameter **MOBILENR**.

![Demo](./images/joa15.png)

You'll see a popup with the **Simple Mode Editor**. Click on **Advanced Mode**.

![Demo](./images/joasm.png)

Paste this code in the **Advanced Mode Editor**. Click **OK**.

`substr(#{ExperiencePlatform.ProfileFieldGroup.profile.mobilePhone.number}, 0, 12)`

>[!NOTE]
>
>This code is intended to work with mobile phone numbers that have 12 digits (including the +), like this one: +32463622044. Several other countries have 13-digit phone numbers. If your mobile phone number has 13 digits (including the +), you need to update this code to:

`substr(#{ExperiencePlatform.ProfileFieldGroup.profile.mobilePhone.number}, 0, 13)`

![Demo](./images/joa16.png)

You'll now see your completed action. Click **Ok**.

![Demo](./images/joa17.png)

In the left menu, go back to **Actions**, select the Action **ldapTextSlack**, then drag and drop it after the **ldapSmsTwilio**-Action (Replace ldap by your ldap).

![Demo](./images/joa18.png)

Go to **Action Parameters** and click the **Edit** icon for the parameter `TEXTTOSLACK`.

![Demo](./images/joa19.png)

In the popup-window, click **Advanced Mode**.

![Demo](./images/joa20.png)

Select the below code, copy it and paste it in the **Advanced Mode Editor**. Click **Ok**.

`"Brrrr..." + #{ExperiencePlatform.ProfileFieldGroup.profile.person.name.firstName} + " It's freezing. 20% discount on Jackets today!"`

![Demo](./images/joa21.png)

You will see your completed action. Click **Ok**.

![Demo](./images/joa22.png)

In the left menu, go to **Orchestration**, select **End**, then drag and drop **End** after the `ldapTextSlack` action.

![Demo](./images/joa23.png)

## Send messages for path Between 10° and 25° Celsius

For each of the temperature contexts, we'll attempt to send an SMS Message to our customer. We can only send an SMS if we have a Mobile Number available for a customer, so we'll first have to verify that we do.

Let's focus on **Between 10 and 25 C** path.

![Demo](./images/p2steps.png)

Let's take another **Condition** element and drag it as indicated in the screenshot above. We'll verify if for this customer, we have a mobile number available.

![Demo](./images/jop1.png)

As this is just an example, we are only configuring the option where the customer has a mobile number available. Add a label of **Has mobile?**.

Click on the **Edit** icon for the Expression for the **Path1** path.

![Demo](./images/joa2p2.png)

In the Data Sources shown on the left, navigate to **ExperiencePlatform.ProfileFieldGroup.profile.mobilePhone.number**. You're now reading the mobile phone number directly from Adobe Experience Platform's Real-time Customer Profile.

![Demo](./images/joa3.png)

Select the field **Number**, then drag and drop it to the Condition Canvas.

Select the operator **is not empty**. Click **Ok**.

![Demo](./images/joa4.png)

You'll then see this. Click **Ok**.

![Demo](./images/joa6.png)

Your journey will then look like this. Click on **Actions** as indicated in the screenshot.

![Demo](./images/jop8.png)

Select the action `ldapSmsTwilio` (verify your ldap), then drag and drop it after the condition you just added.

![Demo](./images/jop9.png)

You'll see a panel on the right hand side where you can configure the action.

![Demo](./images/joa10.png)

Navigate to the **Action Parameters**. Click on the **Edit** icon for the Action Parameter **TEXTMESSAGE**. 

![Demo](./images/joa11.png)

In the popup you'll see, click on **Advanced Mode**.

![Demo](./images/joa12.png)

Select the below code, copy it and paste it in the **Advanced Mode Editor**.

`"What nice weather for the time of year, " + #{ExperiencePlatform.ProfileFieldGroup.profile.person.name.firstName} + " 20% discount on Sweaters today!"`

![Demo](./images/jop14.png)

Click **OK**.

Click on the **Edit** icon for the Action Parameter **MOBILENR**.

![Demo](./images/jop15.png)

You'll see a popup with the **Simple Mode Editor**. Click on **Advanced Mode**.

![Demo](./images/joasm.png)

Paste this code in the **Advanced Mode Editor**. Click **OK**.

`substr(#{ExperiencePlatform.ProfileFieldGroup.profile.mobilePhone.number}, 0, 12)`

>[!NOTE]
>
>This code is intended to work with mobile phone numbers that have 12 digits (including the +), like this one: **+32463622044**. Several other countries have 13-digit phone numbers. If your mobile phone number has 13 digits (including the +), you need to update this code to:

`substr(#{ExperiencePlatform.ProfileFieldGroup.profile.mobilePhone.number}, 0, 13)`

![Demo](./images/joa16.png)

Click **Ok**.

![Demo](./images/jop17.png)

In the left menu, go back to **Actions**, select the Action **ldapTextSlack**, then drag and drop it after the **ldapSmsTwilio**-Action (Replace ldap by your LDAP).

![Demo](./images/jop18.png)

Go to **Action Parameters** and click the **Edit** icon for the parameter `TEXTTOSLACK`.

![Demo](./images/joa19.png)

In the popup-window, click **Advanced Mode**.

![Demo](./images/joa20.png)

Select the below code, copy it and paste it in the **Advanced Mode Editor**. Click **Ok**.

`"What nice weather for the time of year, " + #{ExperiencePlatform.ProfileFieldGroup.profile.person.name.firstName} + " 20% discount on Sweaters today!"`

![Demo](./images/jop21.png)

You will see your completed action. CLick **Ok**.

![Demo](./images/jop22.png)

In the left menu, go to **Orchestration**, select **End**, then drag and drop **End** after the `joconnorTextSlack` action.

![Demo](./images/jop23.png)

## Send messages for path Warmer than 25° Celsius

For each of the temperature contexts, we'll attempt to send an SMS Message to our customer. We can only send an SMS if we have a Mobile Number available for a customer, so we'll first have to verify that we do.

Let's focus on **Warmer than 25 C** path.

![Demo](./images/p3steps.png)

Let's take another **Condition** element and drag it as indicated in the screenshot above. You'll verify if for this customer, you have a mobile number available.

![Demo](./images/jod1.png)

As this is just an example, we are only configuring the option where the customer has a mobile number available. Add a label of **Has mobile?**.

Click on the **Edit** icon for the Expression for the **Path1** path.

![Demo](./images/joa2p3.png)

In the Data Sources shown on the left, navigate to **ExperiencePlatform.ProfileFieldGroup.profile.mobilePhone.number**. You're now reading the mobile phone number directly from Adobe Experience Platform's Real-time Customer Profile.

![Demo](./images/joa3.png)

Select the field **Number**, then drag and drop it to the Condition Canvas.

Select the operator **is not empty**. Click **Ok**.

![Demo](./images/joa4.png)

You'll then see this. Click **OK**.

![Demo](./images/joa6.png)

Your journey will then look like this. Click on **Actions** as indicated in the screenshot.

![Demo](./images/jod8.png)

Select the action `ldapSmsTwilio` (verify your ldap), then drag and drop it after the condition you just added.

![Demo](./images/jod9.png)

You'll see a panel on the right hand side where you can configure the action.

![Demo](./images/joa10.png)

Navigate to the **Action Parameters**. Click on the **Edit** icon for the Action Parameter **TEXTMESSAGE**.

![Demo](./images/joa11.png)

In the popup you'll see, click on **Advanced Mode**.

![Demo](./images/joa12.png)

Select the below code, copy it and paste it in the **Advanced Mode Editor**. Click **OK**.

`"So warm, " + #{ExperiencePlatform.ProfileFieldGroup.profile.person.name.firstName} + "! 20% discount on swimwear today!"`

![Demo](./images/jod14.png)

Click on the **Edit** icon for the Action Parameter **MOBILENR**.

![Demo](./images/jod15.png)

You'll see a popup with the **Simple Mode Editor**. Click on **Advanced Mode**.

![Demo](./images/joasm.png)

Paste this code in the **Advanced Mode Editor**. Click **OK**.

`substr(#{ExperiencePlatform.ProfileFieldGroup.profile.mobilePhone.number}, 0, 12)`

>[!NOTE]
>
>This code is intended to work with mobile phone numbers that have 12 digits (including the +), like this one: **+32463622044**. Several other countries have 13-digit phone numbers. If your mobile phone number has 13 digits (including the +), you need to update this code to:

`substr(#{ExperiencePlatform.ProfileFieldGroup.profile.mobilePhone.number}, 0, 13)`

![Demo](./images/joa16.png)

Click **OK**.

![Demo](./images/jod17.png)

In the left menu, go back to **Actions**, select the Action **ldapTextSlack**, then drag and drop it after the **ldapSmsTwilio**-Action (Replace ldap by your ldap).

![Demo](./images/jod18.png)

Go to **Action Parameters** and click the **Edit** icon for the parameter `TEXTTOSLACK`.

![Demo](./images/joa19.png)

In the popup-window, click **Advanced Mode**.

![Demo](./images/joa20.png)

Select the below code, copy it and paste it in the **Advanced Mode Editor**. Click **Ok**.

`"So warm, " + #{ExperiencePlatform.ProfileFieldGroup.profile.person.name.firstName} + "! 20% discount on swimwear today!"`

![Demo](./images/jod21.png)

You will see your completed action. Click **Ok**.

![Demo](./images/jod22.png)

In the left menu, go to **Orchestration**, select **End**, then drag and drop **End** after the `ldapTextSlack` action.

![Demo](./images/jod23.png)

Your journey is now fully configured.

![Demo](./images/jodone.png)

Click **Publish** again.

![Demo](./images/jopublish1.png)

Your journey is now published.

![Demo](./images/jopublish2.png)

In the next exercise, you'll be able to test your Journey.

Next Step: [12.5 Trigger your journey](./ex5.md)

[Go Back to Module 12](journey-orchestration-external-weather-api-sms.md)

[Go Back to All Modules](../../overview.md)
