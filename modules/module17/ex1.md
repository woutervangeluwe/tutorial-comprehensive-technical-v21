---
title: Create your Microsoft Dynamics 365 account
description: Create your Microsoft Dynamics 365 account
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
exl-id: 780a50a7-cd60-4394-9a6b-53434c534a43
---
# 17.1 Create your Microsoft Dynamics 365 account

In this exercise you'll create your Microsoft Azure and Dynamics 365 account.

## Context - What is Microsoft Dynamics 365?

Microsoft Dynamics 365 is a cloud-based business applications platform that combines components of customer relationship management (CRM) and enterprise resource planning (ERP), along with productivity applications and artificial intelligence tools. 

You'll be using an out of the box entity called **Contact**, you'll learn how to customize it for your business use case and then in later exercises you'll leverage it.

## Context - What is Microsoft Azure?

Azure is a public cloud computing platform—with solutions including Infrastructure as a Service (IaaS), Platform as a Service (PaaS), and Software as a Service (SaaS) that can be used for services such as analytics, virtual computing, storage, networking, and much more.

You'll use Microsoft Azure components like Azure Active Directory which will help you in integrating Microsoft tools and applications with Adobe Experience Platform.


## 17.1.1 Setup Azure and Dynamics account

Open your browser of choice in incognito mode.

![Setup account](./images/incognito.png)

Go to [https://trials.dynamics.com/](https://trials.dynamics.com/).

Choose **Sales**.

![Setup account](./images/choosesales.png)

Scroll down and click **Sign up here**.

![Setup account](./images/selectsales.png)

In the popup, click **No, continue signing up**.

![Sign in](./images/signinno.png)

You'll then see this. Enter your email address and click **Next**.

![Sign in](./images/signinno-01.png)

If you already have already created a Microsoft Account, select the option to **Create a New Account**.

![Sign in](./images/signinno-02.png)

Enter your personal information in the next screen, and click **Next**.

![Sign in](./images/signinno-03.png)

You're now asked to verify your account through a text message. Select **Text me**, and click "Send Verification Code**.

![Sign in](./images/signinno-04a.png)

Enter the code that has been texted to you and click **Verify**

![Sign in](./images/signinno-04b.png)

You now need to create your business identity.  The first step is create a custom domain for your business. 

![Sign in](./images/signinno-05a.png)

For the domain, follow this naming convention:

- demosystem**ldap**X

Replace **ldap** by your ldap.

Replace X by a number. For instance, 101.

In this example, the custom domain has been named: **demosystemvangeluw101**. 

![Sign in](./images/signinno-05b.png)

If your custom domain is available, click **Next**.

For the **User ID**, enter **admin**.

For the password, use: **Password_1234**

![Sign in](./images/signinno-06.png)

Click **Sign up**.

Wait for a couple of minutes without refreshing or closing the window until you see this screen.

![Sign in](.images/../images/signinno-07.png)

Store the user id in a text file on your computer for future reference as you'll need this in future exercises.

**Note:** You will receive an email with details of your trial subscription, including your custom domain and user ID. You should keep this mail, or make sure that you record the domain information for use later in this exercise.

![Sign in](./images/signinno-07a.png)

Back in the browser, click **Get Started**.

You may be asked to sign-in. If you need to sign in, make sure to use the User ID you received by email.

You will be brought to the Power platform admin center where you can see the environment that has been created for you. In this case it is called Adobe (default).

![Sign in](.images/../images/signinno-08.png)

You now need to create your Microsoft Dynamics Environment that will be used in this exercise. 
In the right hand side enter the New environment settings.

For the name, use the same name as before, in this case: **demosystemvangeluw101**.

![Sign in](./images/signinno-08a.png)

Leave the other settings as the defaults and click **Next**.

You can now choose your database settings. 

For the URL again use the custom domain you created earlier - in this case **demosystemvangeluw101**. Note the whole URL **demosystemvangeluw101.crm4.dynamics.com** as this is how you will access Microsoft Dynamics.

Enable the toggle for **Enable Dynamics 365 apps** and select **All enterprise applications** from the list under **Automatically deploy these apps**.

![Sign in](./images/signinno-08b.png)

Click **Save**. Your account is then being set up. This may take a 3-4 minutes.  Wait until the state changes from **PreparingInstance** to **Ready**.

![Sign in](./images/signinno-08c.png)

When the status changes to **Ready**, click the name of your environment after which you are brought to a screen with all your environment details.

![Sign in](./images/signinno-08d.png)

Click **Open environment** in the top bar. This will open a new tab with your Microsoft Dynamics 365 account.

You'll then see this. Click **Dynamics 365 – custom**.

![Sign in](./images/select-dynamics.png)

Finally, you're now logged in to your Microsoft Dynamics 365 account.

![Sign in](./images/dynamics-view.png)

## 17.1.2 Create Microsoft Azure app

Next, you'll create the Microsoft Azure app that will be used by the Custom Action in Journey Orchestration to create the Contact in Dynamics 365.

Inside the same browser window, open a new tab and go to the Microsoft Azure Portal [https://portal.azure.com/](https://portal.azure.com/).

You'll then see this. Click **Maybe later** on the popup window.

![App](./images/azure.png)

Open the Microsoft Azure menu by clicking the hamburger icon in the top left corner of your screen.

![App](./images/azure1.png)

Click **Azure Active Directory**.

![App](./images/app-01.png)

You'll then see this. Click **App registrations**..

![Create Azure App](./images/azureappregistrations01.png)

Click **New registration**.

![Create Azure App](./images/azurenewregistrations02.png)

You'll then see this.

![Create Azure App](./images/azurenewregistrations02a.png)

Fill out the **Register an application** form like this:

- Name: enter **SyncContact**
- Supported account types: select **Accounts in any organizational directory (Any Azure AD directory - Multitenant)**
- Redirect URI : **https://public.aepdemo.net**

![Create Azure App](./images/azurenewregistrations03.png)

Click **Register**.

![Create Azure App](./images/azurenewregistrationsRegister.png)

You'll then see this.

![Create Azure App](./images/azurenewregistrationsRegister1.png)

Next, you need to setup authentication.

Click **Authentication**.

![Create Azure App](./images/app-Auth-01.png)

You'll then see this.

![Create Azure App](./images/app-Auth-01a.png)

Setup authentication like this:

- Implicit grant: check the checkbox for **ID tokens**
- Supported account types: check the checkbox for **Accounts in any organizational directory (Any Azure AD directory - Multitenant)**
- Advanced settings: select **Allow public client flows** and set the toggle to **Yes**.

![Create Azure App](./images/app-Auth-04.png)

Click **Save**.

![Create Azure App](./images/app-Auth-05.png)

Next, you need to setup the **API permissions**.

Click **API permissions**.

![Create Azure App](./images/app-Auth-06.png)

You'll then see this. You now need to add the Microsoft Dynamics 365 CRM API. Click **Add a permission**.

![Create Azure App](./images/app-Auth-06a.png)

The **Request API permissions** panel will appear on the right. Click **Dynamics CRM**.

![Create Azure App](./images/app-Auth-07.png)

You'll then see this.

![Create Azure App](./images/app-Auth-08.png)

Select these options:

- Select **Delegated permissions**
- Check the checkbox for **user_impersonation**

![Create Azure App](./images/app-Auth-10.png)

Click **Add permissions**.

![Create Azure App](./images/app-Auth-11.png)

You now need to add the Microsoft Dynamics 365 Export Data. Click **Add a permission**.

![Create Azure App](./images/app-Auth-06b.png)

The **Request API permissions** panel will appear on the right again. Click **Data Export Service for Microsoft Dynamics 365**.

![Create Azure App](./images/app-Auth-07b.png)

You'll then see this.

![Create Azure App](./images/app-Auth-08b.png)

Select these options:

- Select **Delegated permissions**
- Check the checkbox for **user_impersonation**

![Create Azure App](./images/app-Auth-10b.png)

Click **Add permissions**.

![Create Azure App](./images/app-Auth-11.png)

You'll now see this. Click **Grant admin consent for Adobe**.

![Create Azure App](./images/app-Auth-11a.png)

Confirm your choice by clicking **Yes**.

![Create Azure App](./images/app-Auth-12.png)

You'll now have the following settings. Click **Certificates & secrets**.

![Create Azure App](./images/app-Auth-13.png)

You will now create the client secret that will be used to connect this as a source to Adobe Experience Platform. We will use this secret to create a Microsoft Dynamics User (with permissions to this App) and then use the same credential to connect to the source from Adobe Experience Platform.

Click **New client secret**.

![Create Azure App](./images/app-Auth-cs1.png)

Add a description of **Demo System Integration**, and set the field **Expires** to 24 months.

![Create Azure App](./images/app-Auth-cs2.png)

Click **Add**.

![Create Azure App](./images/app-add.png)

You will then see the generated Value and ID. Copy these to a file on your computer and keep them safe. You will need them later in the exercise.

>[!NOTE]
>
>You cannot come back to the Azure Portal to retrieve the value of the client secret. If you forget or lose the secret, you can simply re-do this step to create a new one for use.

You will now see this. Click on **Overview**.

![Create Azure App](./images/app-Auth-cs3.png)

You'll now find a number of important variables which you'll need in future exercises.
Make sure to copy the following values in a text file on your computer:

- **Application (client) ID**
- **Directory (tenant) ID**

![Create Azure App](./images/azure-details.png)

Now you have all the details you need to connect to Dynamics 365 from Adobe Experience Platform. Please make sure to keep these details handy as they will be used in upcoming section for setting up the integration between Adobe Experience Platform and Microsoft Dynamics 365.

Finally, here's an overview of all the information you now have:

| Attribute | Description | Example |
|----------|-------------|-------------|
| Web API URL | https://**NAME**.**REGION**.dynamics.com/api/data/v9.1/ |https://demosystemjoconnor1312.crm4.dynamics.com/api/data/v9.1/|
| Authority URL | https://login.microsoftonline.com/**Directory (tenant) ID**/oauth2/token |https://login.microsoftonline.com/1d602863-cb0f-4988-b039-f2b29b868dea/oauth2/token|
| Resource | The URL of the Dynamics instance, for example https://**NAME**.**REGION**.dynamics.com |https://demosystemjoconnor1312.crm4.dynamics.com|
| Username | The username you use to connect to Microsoft Dynamics 365|admin@demosystemjoconnor1312.onmicrosoft.com|
| Password | The password you use to connect to Microsoft Dynamics 365|Password_1234|
| Application (client) ID | The **Application (client) ID** of the Azure SyncContact app |2e62d7e7-ffdb-41f5-8457-d2d1f3676546|
Client Secret ID | The Client Secret ID | 7651719a-7f3e-4bc5-af8f-679ead1d2730 |
Client Secret Value | The value of the client secret. Also knows as the Service Principal Credential Key | .Ycc20krN~k5dpCQFv6_Di4-HNQq.rjpt

Where to find these variables?

- **NAME**

  Have a look at the URL of your Microsoft Dynamics 365 homepage. In this example, the URL is **https://demosystemvangeluw101.crm4.dynamics.com**. In this case, the field **NAME** is equal to **demosystemvangeluw101**.
  
  ![Create Azure App](./images/durl.png)

- **REGION**

  Have a look at the URL of your Microsoft Dynamics 365 homepage. In this example, the URL is **https://demosystemvangeluw101.crm4.dynamics.com**. In this case, the field **REGION** is equal to **crm4**.
  
  ![Create Azure App](./images/durl.png)

- **Directory (tenant) ID** and **Application (client) ID**

  You can find the **Directory (tenant) ID** and the **Application (client) ID** in your Azure app SyncContact on the overview page.
  
  ![Create Azure App](./images/azure-details.png)

  **Client Secret and Value**

  If you have lost this, you can generate a new secret in **Certificates & secrets**

![Create Azure App](./images/app-Auth-13.png)
  
Next Step: [17.2 Connect Microsoft Dynamics 365 to Adobe Experience Platform via a Source Connector](./ex2.md)

[Go Back to Module 17](./adobe-experience-platform-microsoft-dynamics-365.md)

[Go Back to All Modules](./../../overview.md)
