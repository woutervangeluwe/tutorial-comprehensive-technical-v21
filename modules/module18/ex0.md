---
title: Segment Activation to Microsoft Azure Event Hub - Configure your Microsoft Azure environment
description: Segment Activation to Microsoft Azure Event Hub - Configure your Microsoft Azure environment
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
exl-id: f5a4ed02-67f4-45be-9edd-497dca629530
---
# 18.0 Configure your environment

## 18.0.1 Create an Azure Subscription

>[!NOTE]
>
>If you already have an Azure Subscription, you can skip this step. Please continue with exercise 18.0.2 in that case.

Go to [https://portal.azure.com](https://portal.azure.com) and login with your Azure account. If you don't have one, please use your personal email address to create your Azure account.

![02-azure-portal-email.png](./images/02-azure-portal-email.png)

After successful login you'll see the following screen:

![03-azure-logged-in.png](./images/03-azure-logged-in.png)

Click on the to left menu and select **All Resources**, the Azure subscription screen will appear if you are not yet subscribed. In that case select **Start with an Azure free Trial**. 

![04-azure-start-subscribe.png](./images/04-azure-start-subscribe.png)

Fill in the Azure subscription form, provide your mobile phone and credit card for activation (you will have a free tier for 30 days and you will not be charged, unless you upgrade):

![05-azure-subscription-form.png](./images/05-azure-subscription-form.png)

When the subscription process is finished you are good to go: 

![06-azure-subscription-ok.png](./images/06-azure-subscription-ok.png)


## 18.0.2 Install Visual Code Studio

You'll use Microsoft Visual Code Studio to manage your Azure Project. You can download it via [this link](https://code.visualstudio.com/download). Follow the installation instructions for your specific OS on that same website.

## 18.0.3 Install Visual Code Extensions

Install the Azure Functions for Visual Studio Code from [https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-azurefunctions](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-azurefunctions). Click the install button:

![07-azure-code-extension-install.png](./images/07-azure-code-extension-install.png)

Install Azure Account and Sign-In for Visual Studio Code from [https://marketplace.visualstudio.com/items?itemName=ms-vscode.azure-account](https://marketplace.visualstudio.com/items?itemName=ms-vscode.azure-account). Click the install button:

![08-azure-account-extension-install.png](./images/08-azure-account-extension-install.png)

## 18.0.4 Install node.js

>[!NOTE]
>
>If you already have node.js installed, you can skip this step. Please continue with exercise 18.0.5 in that case.

### macOS

Make sure to have [Homebrew](https://brew.sh/) installed first. Follow the instructions [here](https://brew.sh/).

![Node](./images/brew.png)

Once you've installed Homebrew, run this command:

```javascript
brew install node
```

### Windows

Download the [Windows Installer](https://nodejs.org/en/#home-downloadhead) directly from the [nodejs.org](https://nodejs.org/en/) web site.

## 18.0.5 Verify node.js version

For this module, you need to have node.js version 12 installed. Any other version of node.js may cause issues with exercise 18.5.

Before you continue, please verify your version of node.js now.

Run this command to verify your node.js version:

```javascript
node -v
```

If your version is below or above 12, you need to upgrade or downgrade.

### Upgrade/Downgrade node.js version on macOS

Ensure that you have the package **n** installed.

To install the package **n**, run this command:

```javascript
sudo npm install -g n
```

If you version is below or above version 12, run this command to upgrade or downgrade:

```javascript
sudo n 12.6.0
```

### Upgrade/Downgrade node.js version on Windows

Uninstall node.js from Windows > Control Panel > Add or remove programs.

Installing the required version from the [nodejs.org](https://nodejs.org/en/) website.

## 18.0.6 Install NPM package: request

You need to install the package **request** as part of your node.js setup.

To install the package **request**, run this command:

```javascript
npm install request
```


Next Step: [18.1 Configure your Microsoft Azure EventHub environment](./ex1.md)

[Go Back to Module 18](./segment-activation-microsoft-azure-eventhub.md)

[Go Back to All Modules](./../../overview.md)
