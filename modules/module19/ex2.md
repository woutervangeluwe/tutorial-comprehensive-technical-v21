---
title: Adobe Experience Platform and ServiceNow - Install and configure the integration between ServiceNow and Adobe Experience Platform through Adobe I/O
description: Adobe Experience Platform and ServiceNow - Install and configure the integration between ServiceNow and Adobe Experience Platform through Adobe I/O
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
exl-id: c29befaf-8ffe-4b8a-863e-643b741b77c4
---
# 19.2 Install and configure the integration between ServiceNow and Adobe Experience Platform through Adobe I/O

Make sure you're successfully logged in to your ServiceNow instance.

![ServiceNow](./images/snow17.png)

## 19.2.1 Install the Adobe Experience Platform Spoke in ServiceNow

As part of the productized integration of Adobe Experience Platform in ServiceNow, a spoke was created.

To install the **Adobe Experience Platform Spoke**, type **System Applications** in the **Filter Navigator**. Then, click **All**.

![ServiceNow](./images/spoke1.png)

You'll then see this.

![ServiceNow](./images/spoke2.png)

In the search field, enter **Adobe Experience Platform**. Next, click **Install**.

![ServiceNow](./images/spoke3.png)

You'll then see this. Click **Install** again.

![ServiceNow](./images/spoke4.png)

You'll then see this progress bar. Installing the spoke may take up to 5 minutes.

![ServiceNow](./images/spoke5.png)

Once you see this, click **Close**. You can now continue with the next step.

![ServiceNow](./images/spoke6.png)

## 19.2.2 Your Adobe I/O Project

In module 3, during exercise [3.3.2 - Setup your Adobe I/O Project](./../module3/ex3.md), you created your own Adobe I/O project. When you created that Adobe I/O project, a certificate pair was created. You will need to use that certificate pair during this exercise. If you don't have it anymore, follow the steps outlined in exercise [3.3.2 - Setup your Adobe I/O Project](./../module3/ex3.md) to create either a new project, or simply to generate a new certificate pair.

Either way, before you continue you need to have these files ready:

- private.key
- certificate_pub.crt

These were generated during the setup of your Adobe I/O project, and they were automatically downloaded to your computer in a zip-file that is named **config.zip**.

Additionally, you'll need to open your Adobe I/O project to retrieve other important information of your **Service Account (JWT)** like Client ID, Client Secret and more.

To do so, go to [https://console.adobe.io/projects](https://console.adobe.io/projects). You'll then see this.

![ServiceNow](./images/io1.png)

Go to **Projects** in the top navigation. Open you project, which should be named **Platform API ldap**.

![ServiceNow](./images/io2.png)

After opening your project, you'll have a similar view. Click **Service Account (JWT)** to view the credentials of your Adobe I/O project.

![ServiceNow](./images/io3.png)

You'll then see this. Keep this screen open during the next 2 steps as you'll need to enter these credentials in the ServiceNow user interface while setting up the integration.

![ServiceNow](./images/io4.png)

## 19.2.3 Create your Java Key Store

One of the requirements to set up the Adobe Experience Platform spoke inside ServiceNow is that your certificate pair needs to be part of a Java Key Store (JKS) file.

At this moment, you need these 2 files:

- private.key
- certificate_pub.crt

Create a new folder on your desktop and name it **JKS**.

![ServiceNow](./images/jks1.png)

Open the **JKS** folder and copy/paste the 2 certificate files into this folder.

![ServiceNow](./images/jks2.png)

Open a new Terminal window.

![ServiceNow](./images/jks3.png)

![ServiceNow](./images/jks4.png)

Navigate to the **JKS** folder on your desktop, by entering a command similar to this:

```javascript
cd desktop/JKS
```

![ServiceNow](./images/jks5.png)

You'll then see this.

![ServiceNow](./images/jks6.png)

>[!NOTE]
>
>If you're using Microsoft Windows, make sure to have **OpenSSL** installed on your computer before continuing. You can find [instructions to install OpenSSL here](../module5/install-openssl.md).

Next, enter the following command in Terminal:

```javascript
openssl pkcs12 -export -inkey private.key -in certificate_pub.crt -out aep.p12
```

You'll have to enter an **Export Password** - you can choose whichever password you prefer but choose something that is easy to remember as you'll need to use that password several times in the next steps. Also, make sure to have a minimum of 6 characters for your password as that's required by Java Keystore.

![ServiceNow](./images/jks7.png)

Your Terminal window should now look like this.

![ServiceNow](./images/jks8.png)

A this moment, after the previous command, you should now see a new file in your **JKS** folder named **aep.p12**.

![ServiceNow](./images/jks9.png)

>[!NOTE]
>
>If you're using Windows, the below command won't work yet. You need to install Java JDK first, which you can find here: [https://www.oracle.com/de/java/technologies/javase-jdk15-downloads.html](https://www.oracle.com/de/java/technologies/javase-jdk15-downloads.html). 

Next, enter the following command in Terminal:

**On macOS:**

```javascript
keytool -v -importkeystore -srckeystore aep.p12 -srcstoretype PKCS12 -destkeystore aep.jks -deststoretype JKS
```

**On Windows:**

```javascript
"C:\Program Files\Java\jdk-15.0.2\bin\keytool.exe" -v -importkeystore -srckeystore aep.p12 -srcstoretype PKCS12 -destkeystore aep.jks -deststoretype JKS
```

>[!NOTE]
>
> The path to your Java JDK directory may be different depending on what version of Java JDK you have installed. If this command doesn't work, verify the full path exists and update as needed.

![ServiceNow](./images/jks10.png)

You then need to enter the **Destination Password**. Please use the same password as the one you used while executing the previous command.

![ServiceNow](./images/jks11.png)

Confirm your password.

![ServiceNow](./images/jks12.png)

You now need to enter the **Source Password**. This is the password you entered while executing the previous command to create the file **aep.p12**.

![ServiceNow](./images/jks13.png)

Finally, you should see this after executing this command.

![ServiceNow](./images/jks14.png)

And you should now also have a file named **aep.jks**.

![ServiceNow](./images/jks15.png)

If you see the file **aep.jks**, you can continue with the next exercise.

Next Step: [19.3 Setup your ServiceNow environment](./ex3.md)

[Go Back to Module 19](./call-center-servicenow.md)

[Go Back to All Modules](./../../overview.md)
