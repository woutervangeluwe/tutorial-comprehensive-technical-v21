---
title: Adobe Experience Platform and ServiceNow - Setup your ServiceNow UI
description: Adobe Experience Platform and ServiceNow - Setup your ServiceNow UI
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
exl-id: 7fde17de-f9e0-4882-9617-3b532296c8ea
---
# 19.4 Setup your ServiceNow UI

## 19.4.1 Import XML templates

You'll now import two predefined XML templates which will help speed up the implementation process in ServiceNow by loading a number of predefined settings.

First of all, download the required XML templates which you can find [here](./../../assets/servicenow/AEP-ServiceNow-Integration.zip) to the desktop of your computer and unzip it.

![ServiceNow](./images/ui1.png)

In that directory, you'll now have two XML template files:

- AEPWidget.xml
- CSM-AEP-E2E-Flow.xml

These two files need to be imported in ServiceNow.

In ServiceNow, in the Filter Navigator, enter the search term **Retrieved Update Sets**. Click **Retrieved Update Sets**.

![ServiceNow](./images/ui2.png)

You'l then see this. Click **Import Update Set from XML**.

![ServiceNow](./images/ui3.png)

You'll then see this. Click **Choose File**.

![ServiceNow](./images/ui4.png)

In the popup, navigate to the folder on your desktop and select the file **AEPWidget.xml**. Click **Open**.

![ServiceNow](./images/ui5.png)

Next, click **Upload**.

![ServiceNow](./images/ui6.png)

You'll then see this. Click **Import Update Set from XML** again.

![ServiceNow](./images/ui7.png)

You'll then see this. Click **Choose File**.

![ServiceNow](./images/ui4.png)

In the popup, navigate to the folder on your desktop and select the file **CSM-AEP-E2E-Flow.xml**. Click **Open**.

![ServiceNow](./images/ui8.png)

Next, click **Upload**.

![ServiceNow](./images/ui9.png)

You'll then see this. You've now imported both XML files.

![ServiceNow](./images/ui10.png)

## 19.4.2 Preview and Commit Update Sets

Next, you need to preview and commit the XML Update Sets that you just uploaded.

![ServiceNow](./images/ui11.png)

Click the Update Set **AEP Widget on Agent Workspace** to open it. 

You'll then see this. Click **Preview Update Set**.

![ServiceNow](./images/ui12.png)

You'll then see a similar popup after a couple of seconds. The error message is expected. Click **Close**.

![ServiceNow](./images/ui13.png)

Click **Accept remote update**.

![ServiceNow](./images/ui14.png)

You'll then see this. Click **Commit Update Set**.

![ServiceNow](./images/ui15.png)

You'll then see another popup. Wait until it completes and then, click **Close**.

![ServiceNow](./images/ui16.png)

You'll then be back on the overview screen of your Retrieved Update Set. Click the **back** button to go back to all Retrieved Update Sets.

![ServiceNow](./images/ui17.png)

You'll then see this. Click the Update Set **E2E CSM+AEP Integration** to open it.

![ServiceNow](./images/ui18.png)

You'll then see this. Click **Preview Update Set**.

![ServiceNow](./images/ui19.png)

You'll then see a similar popup after a couple of seconds. Click **Close**.

You might get an error message. In that case, be sure to click **Accept remote update** on every error, just like you did in the previous exercise.

![ServiceNow](./images/ui20.png)

You'll then see this. Click **Commit Update Set**.

![ServiceNow](./images/ui21.png)

You'll then see another popup. Wait until it completes and then, click **Close**.

![ServiceNow](./images/ui22.png)

You'll then be back on the overview screen of your Retrieved Update Set. Click the **back** button to go back to all Retrieved Update Sets.

![ServiceNow](./images/ui23.png)

## 19.4.3 Create Adobe-specific fields in ServiceNow Case table

In ServiceNow, in the Filter Navigator, enter the search term **Case**. Click **All**.

![ServiceNow](./images/case1.png)

You'l then see this. 

![ServiceNow](./images/case2.png)

Right-click on the Table header as indicated. Go to **Configure** > **Table**.

![ServiceNow](./images/case3.png)

You'll then see this. Click **New**.

![ServiceNow](./images/case4.png)

You'll then see an empty form.

![ServiceNow](./images/case5.png)

Fill out the form fields as follows:

- Type: **String**
- Column label: **Timestamp for AEP**
- Column name: **u_timestamp_for_aep**
- Max Length: 100

When the above form fields are filled out, right-click on the form header and click **Save**.

![ServiceNow](./images/case6.png)

Next, click the **back** button as indicated below.

![ServiceNow](./images/case7.png)

You'll then see this. Click **New**.

![ServiceNow](./images/case8.png)

You'll then see an empty form.

![ServiceNow](./images/case9.png)

Fill out the form fields as follows:

- Type: **String**
- Column label: **ID for AEP**
- Column name: **u_id_for_aep**
- Max Length: 100

When the above form fields are filled out, right-click on the form header and click **Save**.

![ServiceNow](./images/case10.png)

Next, click the **back** button as indicated below.

![ServiceNow](./images/case11.png)

Your form fields are now defined, you can now continue with setting up the business rules needed to populate those fields.

## 19.4.4 Create Adobe-specific business rules in ServiceNow Case table

In ServiceNow, in the Filter Navigator, enter the search term **Case**. Click **All**.

![ServiceNow](./images/case1.png)

Right-click on the table headers. You'll then see a menu appear. Navigate to **Configure** > **Business Rules**.

![ServiceNow](./images/case12.png)

You'll then see this. Click **New**.

![ServiceNow](./images/case13.png)

You'll then see this.

![ServiceNow](./images/case14.png)

Fill out the form fields as follows:

- Name: **Populate Random ID For AEP**
- Table: **Case [sn_customerservice_case]**
- Check the checkbox for **Advanced**
- In **When to run**, make sure to:
  - Check the checkbox for **INSERT**
  - Check the checkbox for **UPDATE** 
  - Set the Filter Condition to **Consumer** is not empty

You should now have this. Go to **Advanced** (green arrow).

![ServiceNow](./images/case15.png)

In the **Script** form, enter the following code:

```javascript
(function executeRule(current, previous /*null when async*/) {

  var randNumber = (Math.floor(Math.random() * 100000000000) + 1).toString();
    current.u_id_for_aep = randNumber;

})(current, previous);
```

Click **Submit**.

![ServiceNow](./images/case16.png)

You'll then be back here. Click **New** again.

![ServiceNow](./images/case17.png)

You'll then see this.

![ServiceNow](./images/case18.png)

Fill out the form fields as follows:

- Name: **Populate Timestamp For AEP**
- Table: **Case [sn_customerservice_case]**
- Check the checkbox for **Advanced**
- In **When to run**, make sure to:
  - Check the checkbox for **INSERT**
  - Check the checkbox for **UPDATE** 
  - Set the Filter Condition to **Consumer** is not empty

You should now have this. Go to **Advanced** (green arrow).

![ServiceNow](./images/case19.png)

In the **Script** form, enter the following code:

```javascript
(function executeRule(current, previous /*null when async*/) {

  current.u_timestamp_for_aep =  new Date().toISOString();

})(current, previous);
```

Click **Submit**.

![ServiceNow](./images/case20.png)

## 19.4.5 Enable Adobe Experience Platform Ribbon on Consumer Overview

You now need to run a script to ensure that a specific component will be shown on the Consumer Case Overview.

In ServiceNow, in the Filter Navigator, enter the search term **Scripts - Background**. Click **Scripts - Background**.

![ServiceNow](./images/scr1.png)

You'l then see this.

![ServiceNow](./images/scr2.png)

Copy the below code and paste it in the **Run Script** input form.

```javascript
var grSULSS = new GlideRecord('sys_ux_lib_source_script'); if (grSULSS.get('5acc97d956dc670d624ef4a31f70b919')) {   grSULSS.inner_components = "223be0881a4988fcbe7112c23bf93c75,38a40eb364f0ac980c697fa64444f1e8,c817fad3b052fbd2443137d58b9b5024,3f9425191bf9c41091bf0d8cdc4bcb2e";   grSULSS.update(); }
```

![ServiceNow](./images/scr3.png)

Click **Run script**. You'll then see this.

![ServiceNow](./images/scr4.png)

You've now defined all the required components to visualize Adobe Experience Platform data in the ServiceNow User Interface, and in the other direction, to send case data from ServiceNow into Adobe Experience Platform.

Next Step: [19.5 Setup your ServiceNow Flow](./ex5.md)

[Go Back to Module 19](./call-center-servicenow.md)

[Go Back to All Modules](./../../overview.md)
