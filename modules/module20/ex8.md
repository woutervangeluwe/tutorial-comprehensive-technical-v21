---
title: AI-Driven Chat Apps and Live Chat powered by Stackchat - Test the WeChat Integration (Optional)
description: In this exercise you'll test the WeChat Integration
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
exl-id: 4d6ce5f6-c28b-43cd-bcc5-d19a2f595a0d
---
# 20.8 Test the WeChat Integration (Optional)

![WeChat-logo](./images/wechat-logo-crunch.png)

In this exercise we will be walking through the WeChat Mobile App, so you will need access to the app and a WeChat account.

## Notes

- The creation and configuration of WeChat Official Accounts to host the chatbot can be time consuming and require specific approval processes, so for the purposes of this tutorial we will only be looking at a pre-built version of the chat bot with minimal interactions built in.
- Unlike the Web experience, which picks up our configuration ID automatically, including the **brandID**, we will need to submit them at the beginning of the chatbot experience when prompted.


>[!NOTE]
>
>Hot Tip! The following commands have been secretly 'baked in' to our chat bot:
>
>- **/debug** - this confirms which AEP instance the chat bot is currently connected to
>- **/reset** - This allows you to start the conversation again from scratch
>
>So at any point you can confirm the integration or reset the conversation, respectively. If you're curious, see if you can find these keyword configurations in the Studio UI or the CDML editor - they are configured using regular expressions!

## 20.8.1 Add Adobe's WeChat Official Account to your contacts

Open your WeChat mobile app to the contacts page

![WeChat_Contacts page](./images/WeChat_Home_Contacts_anon.jpeg)

Add a new contact by selecting the icon in the top right of the screen

![WeChat_Add_Contact_btn](./images/WeChat_Add_Contect_btn.jpeg)

On the **Add Contacts** screen, select the **Scan QR Code** option

![WeChat_Add_Contact_anon](./images/WeChat_Add_Contact_anon.jpeg)

Select the **Scan QR Code** option

![WeChat_ScanQRcode](./images/WeChat_ScanQRcode.jpeg)

If you haven't already done so, allow the app access to your camera. You should now have the ability to scan the following QR code

![WeChat_Adobe_OfficialAccount_QRcode](./images/WeChat_Adobe_OfficialAccount_QRcode.jpg)

Once you scan, you should now see the following screen. Select **Follow** to add the Adobe Official Account

![WeChat_AdobeOfficialAccount_Follow](./images/WeChat_AdobeOfficialAccount_Follow.jpeg)

You should now the the following screen.

![WeChat_AdobeOfficialAccount_HP](./images/WeChat_AdobeOfficialAccount_HP.jpeg)

Now you have added the Adobe Official Account you will be able to find it at any time via your **Contact** page. Try it yourself by navigating back to your **Contact** page and selecting **Official Accounts**

![WeChat_Contacts page](./images/WeChat_Home_Contacts_anon.jpeg)

Select **Official Accounts**

![WeChat_OfficialAccounts_btn](./images/WeChat_OfficialAccounts_btn.jpeg)

You should now see a list of Official Accounts you have added.

![WeChat_OfficialAccounts](./images/WeChat_OfficialAccounts.jpeg)

Select the Adobe Official Account

![WeChat_Adobe_OfficialAccount_select](./images/WeChat_Adobe_OfficialAccount_select.jpeg)

## 20.8.2 Interact with the chatbot within WeChat

To initiate the chat bot, on the Adobe Official account page, press the following icon, located centre bottom of the screen

![wechat_brandid](./images/WeChat_AdobeOfficialAccount_Chat_btn.jpeg)

This will open the chat bot for which you will see an automated greeting asking you to submit your configID

![WeChat_AdobeOfficialAccount_Chat_initiated](./images/wechat_configid.jpeg)

Next submit your brand ID, this can be found in your configuration [admin page](https://public.aepdemo.net/admin.html), once you have selected your brand. 

![WeChat_AdobeOfficialAccount_Chat_privacySubmit](./images/wechat_brandid.jpeg)

For this tutorial we will remain with Luma Retail, which is brand ID = 2. enter **2** and submit. You will see our Luma Bot load, presenting us with several options. Within WeChat we are unable to tap the options, so instead will submit the option number into the chat. 

![wechat_brandid_luma](./images/wechat_brandid_luma.jpeg)

enter **1** for 'I need ideas' and submit. Before showing you the product options, Luma bot will present a link to the policies and ask for confirmation you are ok to share you email. This is just one example of how we can introduce things like consent management and customer satisfaction checks into our chat app experiences. submit **1** to accept, continue to submit your email and confirm submission by submitting **1** again.

![wechat_email-confirm](./images/wechat_email-confirm.jpeg)

Now we've given consent and provided our email, Luma bot will list all the product cards available for Luma Retail. Here you may tap any product, which will take you to the Luma web site to begin your onsite experience. You'll notice there's not as many options or interactions as we found within the web and/or Facebook experience, but this may change in future.

![WeChat_AdobeOfficialAccount_Chat_BrowseCollection](./images/WeChat_AdobeOfficialAccount_Chat_BrowseCollection.jpeg)

Tap on any product and you will be taken to the product page of the Luma website

>[!NOTE]
>
>The first time you do this you will be taken to your demo admin page and asked for your configuration ID, ldap & brand before proceeding. Your settings will be remembered for any subsequent product taps within the WeChat chatbot.

![WeChat_AdobeOfficialAccount_Chat_productClickThrough](./images/WeChat_AdobeOfficialAccount_Chat_productClickThrough.jpeg)

Congratulations! You've now completed the module and have explored the wonderful world of Chat Apps! We highly recommend you now read through the [Summary & benefits](./summary.md) pages where we will run through some more sample use cases and benefits chat apps can deliver to your business.

Next Step: [Summary and benefits](./summary.md)

[Go Back to Module 20](./ai-driven-chat-apps-stackchat.md)

[Go Back to All Modules](./../../overview.md)
