---
title: Journey Optimizer Create your journey
description: Journey Optimizer Create your journey
kt: 5342
audience: developer
doc-type: tutorial
activity: develop
exl-id: 43010729-1e1b-482b-95a4-1e1077986158
---
# 6.3 Create your journey

In this exercise, you'll configure the journey that needs to be triggered when someone creates an account on the demo website.

Login to Adobe Journey Optimizer by going to [Adobe Experience Cloud](https://experience.adobe.com). Click **Journey Optimizer**.

![ACOP](./images/acophome.png)

You'll be redirected to the **Home**  view in Journey Optimizer.

![ACOP](./images/acoptriglp.png)

First, make sure you're using the correct sandbox. The sandbox to use is called `--aepSandboxId--`. To change from one sandbox to another, click on **PRODUCTION Prod (VA7)** and select the sandbox from the list. In this example, the sandbox is named **AEP Enablement FY21**.

![ACOP](./images/sb.png)

You'll then be in the **Home** view of your sandbox `--aepSandboxId--`.

![ACOP](./images/home.png)

In the left menu, click **Journeys**. Next, click **Create Journey** to create a new journey.

![ACOP](./images/createjourney.png)

You'll then see an empty Journey screen.

![ACOP](./images/journeyempty.png)

In the previous exercise, you created a new **Event**. You named it like this `ldapAccountCreationEvent` and replaced `ldap` with your ldap. This was the result of the Event creation:

![ACOP](./images/eventdone.png)

You now need to take this event as the start of this Journey. You can do this by going to the left side of your screen and searching for your event in the list of events.

![ACOP](./images/eventlist.png)

Select your event, drag and drop it on the Journey canvas. Your Journey now looks like this:

![ACOP](./images/journeyevent.png)

As the second step in the journey, you need to add a short **Wait** step. Go to the left side of your screen to the **Orchestration** section to find this. You'll be using profile attributes and need to make sure they are populated into the Real-time Customer Profile.

![ACOP](./images/journeywait.png)

Your journey now looks like this. On the right side of the screen you need to configure the wait time. Set it to 20 seconds. This will give plenty of time for the profile attributes to be available after the event fires.

![ACOP](./images/journeywait1.png)

Click **Ok** to save your changes.

As the third step in the journey, you need to add a **Message** action. Go to the left side of your screen to **Actions**, select the **Message** action, then drag and drop it on the second node in your journey.

![ACOP](./images/journeyactions.png)

On the right side of your screen, you now need to configure the email. Click the **Edit** icon.

![ACOP](./images/emptymsg.png)

You'll then see the **Select a message** popup. In that list, you need to select the template with the name **ldap - Registration Email**.

![ACOP](./images/emailmsglist.png)

You'll then see this. Click **OK**.

![ACOP](./images/jomsg1.png)

For this exercise, our Journey is fine like it is now.

Let's add an Orchestration Event to **End** the Journey. In the left side of the screen, go to **Orchestration** and select **End**. Drag and Drop this onto the 3rd step of the Journey.

![ACOP](./images/orch.png)

You still need to give your Journey a Name. You can do that by clicking the **Properties** icon in the top right side of your screen.

![ACOP](./images/journeyname.png)

You can then enter the Journey's name here. Please use `ldap - Account Creation Journey` as a naming convention and replace `ldap` with your LDAP.
  
![ACOP](./images/journeyname1.png)

Click **OK** to save your changes.

![ACOP](./images/ok.png)

You can now publish your journey by clicking **Publish**.

![ACOP](./images/publishjourney.png)

Click **Publish** again.

![ACOP](./images/publish1.png)

You'll then see a green confirmation bar saying that your Journey is now Published.

![ACOP](./images/published.png)

You've now finished this exercise.

Next Step: [6.4 Update your Configuration ID and Test your Journey](./ex4.md)

[Go Back to Module 6](./journey-orchestration-create-account.md)

[Go Back to All Modules](../../overview.md)
