---
title: Install OpenSSL for Windows
description: Install OpenSSL for Windows
kt: 5342
audience: Data Engineer, Data Architect
doc-type: tutorial
activity: develop
exl-id: c2042aaa-988f-45a7-9d6a-e7a72839f9e3
---

# Install OpenSSL for Windows

In this exercise, you'll learn how to install OpenSSL for Windows.

Download OpenSSL from this link: [https://slproweb.com/products/Win32OpenSSL.html](https://slproweb.com/products/Win32OpenSSL.html)

Select the appropriate download, in this case: **Win64 OpenSSL v3.0.0**.

![SSL](./images/ssl0.png)

After downloading OpenSSL, you'll find the executable in your Downloads folder. Double-click to run the installer.

![SSL](./images/ssl1.png)

You might see this message. Click **More Info**.

![SSL](./images/ssl2.png)

Click **Run anyway**.

![SSL](./images/ssl3.png)

Select **I accept the agreement** and click **Next**.

![SSL](./images/ssl4.png)

Leave the default setting and click **Next**.

![SSL](./images/ssl5.png)

Leave the default setting and click **Next**.

![SSL](./images/ssl6.png)

Leave the default setting and click **Next**.

![SSL](./images/ssl7.png)

Click **Install**.

![SSL](./images/ssl8.png)

After the installation finish, uncheck the donation checkbox and click **Finish**.

![SSL](./images/ssl9.png)

In the Windows search field, enter **systempropertiesadvanced** and hit **Enter**.

![SSL](./images/ssl10.png)

Click **Environment Variables**.

![SSL](./images/ssl11.png)

Select **Path** and click **Edit...**.

![SSL](./images/ssl12.png)

Add the environment variable with the path **C:\Program Files\OpenSSL-Win64\bin**. Click **OK** twice to save your changes.

![SSL](./images/ssl12a.png)

You now have to reboot your Windows machine to ensure that the above new path variable is taken into account by the system.

After the system has rebooted, open a command prompt and enter the command `openssl version`. You should get a response like the one below.

![SSL](./images/ssl13.png)

If you have a similar response, that means that OpenSSL is successfully installed and you can now execute commands to create certificates using OpenSSL.

[Go Back to Module 5](./data-ingestion-informatica-etl.md)

[Go Back to All Modules](../../overview.md)
