---
title: Voice Assistant - Walkthrough of Demo Scenario, now including Alexa
description: Voice Assistant - Walkthrough of Demo Scenario, now including Alexa
kt: 5342
audience: Application Developer
doc-type: tutorial
activity: develop
exl-id: 6ff6e173-5b9e-4624-b359-83c2f10d60e5
---
# 4.4 Walkthrough of Demo Scenario, now including Alexa

In order to use the demo website, follow the steps in [0.4.2 - Start with a new incognito browser window](../module0/ex4.md) and load the demo brand **Luma**.

## Demo flow

### Step 1 - Unknown visitor browses the Luma website

Go to the Luma Homepage.
  
![Demo](./images/lb_home.png)
  
Have a look at the X-ray panel and the Real-time Customer Profile.
      
![Demo](./images/lb_home_xup.png)

Verify that your Experience Events overview is empty.

![Demo](./images/lb_home_xee.png)
  
Scroll down on the page until you see the products, click on the product **Nadia Elements Shell**.
  
![Demo](./images/lb_els_dtl.png)
  
Have a look at the product. An Experience Event of type **Product View** has now been sent to Platform. Click on the **+ Add To Cart** button.
  
![Demo](./images/lb_addtocart.png)
  
An Experience Event of type **Add To Cart** has been sent to Platform. Next, click on the cart icon in the top right corner of your screen to visualize the cart.
  
![Demo](./images/lb_cart.png)
  
Open the X-Ray panel and go to Experience Events. You'll now see an Experience Event as Browse Activity and also an Experience Event as Add To Cart Activity.
  
![Demo](./images/lb_cartee.png)
  
While the behavior is anonymous, Luma is able to track every click and store in in Platform. Once the anonymous customer becomes known, Luma will be able to merge all anonymous behavior automatically to the known profile.
  
### Step 2 - Unknown visitor registers on the Luma website

As a best practice, please use the following convention for identifiers:

- Email Address identifier: **email**+**DDMMYY**-**number**@domain.com
- Mobile Nr identifier: **yourmobilenumber**+**DDMMYY**-**number**

As an example, for the ldap **vangeluw**:

On Friday Dec 11 2020, this should be the first set of identifiers of the day.
  
- Email Address identifier: **woutervangeluwe**+**12122020**-**1**@gmail.com
- Mobile Nr identifier: **0473622044**+**11122020**-**1**

Go to the Login/Register page and enter your details.
  
![Demo](./images/lb_register_dtl.png)
 
Fill out your registration details and opt-in preferences and click **CREATE ACCOUNT**.
  
After login, go to the Homepage of the Luma website and open the X-ray panel, go to Real-time Customer Profile. On the X-ray panel, you should see all of your personal data displayed.
  
![Demo](./images/lb_x_loggedin.png)

On the X-ray panel, go to Experience Events. You should see the Browse Activity and the Add To Cart activity that was there before.

![Demo](./images/lb_x_loggedin_ee.png)

After becoming a known customer, it's time to install the mobile app on your iPhone and then login to the app. 

### Step 3 - Known visitor logs in on the mobile app

In order to use the demo website, follow the steps in [0.5 - Use the mobile app](../module0/ex5.md) and load the demo brand **Luma**.

Open the app.
  
![Demo](./images/app_hp.png)

Go to the Account-screen.
  
![Demo](./images/app_acc.png)

Login with the email address you used in the previous exercise and the password of 1234.
  
![Demo](./images/app_acc_login.png)

See your Real-time Customer Profile data appear in the application, along with your Desktop Browse Activity

![Demo](./images/app_up.png)

Go to the app's Homepage
  
![Demo](./images/app_hp.png)

Go to the **Mens**-category
  
![Demo](./images/app_men_cat.png)

Click on the product **Proteus Fitness Jackshirt (Orange)** and view the product.
  
![Demo](./images/app_proteus.png)

Go back to the previous screen
  
![Demo](./images/app_men_cat.png)

Go to the Account-screen and your Real-time Customer Profile data will be refreshed, after which you'll see the **Proteus Fitness Jackshirt (Orange)** product be part of your recent browse activity. 
  
![Demo](./images/app_after_proteus.png)

- Now go back to your desktop computer and refresh the Luma homepage, after which you'll see the **Proteus Fitness Jackshirt (Orange)** product also appear there. Please note the fact that the channel on which the browse activity happened is being shown now.
  
![Demo](./images/lb_x_aftermobile.png)

### Step 4 - Known visitor interacts with Alexa skill

Let's put Alexa into the story.

Open the Alexa simulator and make sure you only have the option **Device Display** activated. Deselect **Skill I/O**.
  
![Demo](./images/alexa_sim.png)

Enter the command **Ask Adobe Experience Platform** by either typing it or speaking it (to record your voice, click and hold the microphone-icon, release when you've finished speaking).
  
![Demo](./images/alexa_sim_mic.png)

![Demo](./images/alexa_ask.png)

Enter the command **Get Products** by either typing it or speaking it (to record your voice, click and hold the microphone-icon, release when you've finished speaking). 
  
![Demo](./images/alexa_sim_mic.png)

![Demo](./images/alexa_ask_getproducts.png)

Enter the command **Get Product 3** by either typing it or speaking it (to record your voice, click and hold the microphone-icon, release when you've finished speaking). 

![Demo](./images/alexa_sim_mic.png)

![Demo](./images/alexa_ask_getproduct3.png)

Enter the command **Add Product To Cart** by either typing it or speaking it (to record your voice, click and hold the microphone-icon, release when you've finished speaking). 
  
![Demo](./images/alexa_sim_mic.png)

![Demo](./images/alexa_ask_addtocart.png)

Enter the command **Purchase Product** by either typing it or speaking it (to record your voice, click and hold the microphone-icon, release when you've finished speaking). 
  
![Demo](./images/alexa_sim_mic.png)

![Demo](./images/alexa_ask_purchase.png)

Now go back to your desktop computer and refresh the Luma homepage, after which you'll see the **Zeppelin Yoga Pant** product also appear there, in Browse Activity, Add To Cart and Purchase. Please note the fact that the channel on which the activity happened is being shown, so you can clearly indicate which Experience Event happened on which device.
  
![Demo](./images/lb_x_afteralexa.png)
  
### Step 5 - Call the most personal Call Center ever

To access the Call Center Dashboard, click on the 3-dots in the desktop site's menu and select **Call Center**.

![Demo](./images/callcenter.png)
  
In the Call Center, you'll notice that the Mobile Number you used to register on the Luma - website has been filled out automatically for you. You can also enter any other mobile number of choice to retrieve the customer profile. 
  
![Demo](./images/callcenter_id.png)
  
Click the **Check** button. After 1-2 seconds, your Real-time Customer Profile data is being shown to the call center employee, including your browsing behavior from the last couple of seconds.
  
![Demo](./images/callcenter_response.png)
  
With this, you've successfully completed this exercise.

Next Step: [Summary and benefits](./summary.md)

[Go Back to Module 4](./data-ingestion-amazon-alexa.md)

[Go Back to All Modules](./../../overview.md)
