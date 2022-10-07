---
title: Data Ingestion using Google Tag Manager and Google Analytics - Configure Google Tag Manager Variables
description: Data Ingestion using Google Tag Manager and Google Analytics - Configure Google Tag Manager Variables
kt: 5342
audience: Data Engineer, Data Architect
doc-type: tutorial
activity: develop
exl-id: 96a5ab1f-0ebb-469b-99c0-8efb4ea012e2
---
# 9.3 Configure Google Tag Manager Variables

Go to [https://tagmanager.google.com/](https://tagmanager.google.com/) and login with your personal login details.

After creating and configuring the Google Analytics tag, we're now ready to configure Google Tag Manager Variables (like the Data Elements we use in Adobe Launch).

In the Google Tag Manager UI, go to **Variables**. You'll see the list of built-in Variables.

![Google Tag Manager Setup](./images/dataelements.png)

The first Variable we need to add is called `customerEmail`. When a customer creates a profile on the Platform Demo website, we'll link the customer's email address to his or her customer profile in Platform.
In the Platform Demo website, information is often stored in localStorage. To access this we need a Custom Javascript to populate the Google Tag Manager Variable.

In the **User-Defined Variables** - section, click **New**:

![Google Tag Manager Setup](./images/cenew.png)

![Google Tag Manager Setup](./images/cemail.png)

First rename "Untitled Variable" into a more descriptive name:

| Untitled Variable |
| ------------- |
| customerEmail |

Then click in the Configuration part, this lets you choose a variable type.

![Google Tag Manager Setup](./images/cemailconfiguration.png)

Choose this one.

| Variable Type     |
|-------------|
| Custom Javascript |

![Google Tag Manager Setup](./images/cemail1a.png)

This is the custom code to enter in the screen below:

```javascript
function() {
  var email = localStorage.getItem("email");
  return email;
}
```

So after pasting the code your screen looks like this.
![Google Tag Manager Setup](./images/cemail2.png)

Click **Save** to save your new Variable.

![Google Tag Manager Setup](./images/gasave.png)

You're screen will look like this.

![Google Tag Manager Setup](./images/cemailfinal.png)

For the next variables, you'll repeat this process:

* In the **User-Defined Variables** section, click **New**.
* Rename the `Untitled Variable`
* Select **Custom JavaScript** as the Configuration Type
* Paste the Java-Script code
* Click **Save** to save your new Variable.

The next Variable will be `customerMobileNr`. When a customer creates a profile on the Platform Demo website, we'll link the customer's Mobile Number to his or her customer profile in Platform.

In the **User-Defined Variables** - section, click **New**.

* Rename `Untitled Variable` to `customerMobileNr`
* Choose **Custom Javascript** as Variable Type
* Paste this Custom JavaScript code:

```javascript
function() {
  var mobilenr = localStorage.getItem("mobilenr");
  return mobilenr;
}
```

Your screen should look like this.

![Google Tag Manager Setup](./images/mobilenr.png)

Click **Save** to save your new Variable.

![Google Tag Manager Setup](./images/gasave.png)

The next Variable will be `customerFirstName`. When a customer creates a profile on the Platform Demo website, we'll link the customer's first name to his or her customer profile in Platform.

In the **User-Defined Variables** - section, click **New**.

* Rename `Untitled Variable` to `customerFirstName`
* Choose **Custom Javascript** as Variable Type
* Paste this Custom JavaScript code:

```javascript
function() {
  var firstname = localStorage.getItem("firstname");
  return firstname;
}
```

Your screen should look like this.

![Google Tag Manager Setup](./images/firstname2.png)

Click **Save** to save your new Variable.

![Google Tag Manager Setup](./images/gasave.png)

Next: `customerLastName`. When a customer creates a profile on the Platform Demo website, we'll link the customer's last name to his or her customer profile in Platform.

In the **User-Defined Variables** - section, click **New**.

* Rename `Untitled Variable` to `customerLastName`
* Choose **Custom Javascript** as Variable Type
* Paste this Custom JavaScript code:

```javascript
function() {
  var lastname = localStorage.getItem("lastname");
  return lastname;
}
```

Your screen should look like this.

![Google Tag Manager Setup](./images/lastname.png)

Click **Save** to save your new Variable.

![Google Tag Manager Setup](./images/gasave.png)

Next: `aepTenantId`. When a customer creates a profile on the Platform Demo website, we'll link the customer's last name to his or her customer profile in Platform.

In the **User-Defined Variables** - section, click **New**.

* Rename `Untitled Variable` to `aepTenantId`
* Choose **Custom Javascript** as Variable Type
* Paste this Custom JavaScript code:

```javascript
function() {
  var aepTenantId = localStorage.getItem("aepTenantId");
  return aepTenantId;
}
```

Your screen should look like this.

![Google Tag Manager Setup](./images/aeptenantid.png)

Click **Save** to save your new Variable.

![Google Tag Manager Setup](./images/gasave.png)

Next: `customerLoggedIn`. When a customer is logged in on the Platform Demo website, we'll set this variable to Yes and use that condition in a Launch Rule configuration.

In the **User-Defined Variables** - section, click **New**.

* Rename `Untitled Variable` to `customerLoggedIn`
* Choose **Custom Javascript** as Variable Type
* Paste this Custom JavaScript code:

```javascript
function() {
  var loggedin = localStorage.getItem("loggedin");
  return loggedin;
}
```

Your screen should look like this.
![Google Tag Manager Setup](./images/loggedin2.png)

Click **Save** to save your new Variable.

![Google Tag Manager Setup](./images/gasave.png)

Next: `brandName`. When you select a brand to demo from the **Admin** - menu, the brandName will be sent to Adobe Experience Platform.

In the **User-Defined Variables** - section, click **New**.

* Rename `Untitled Variable` to `brandName`
* Choose **Custom Javascript** as Variable Type
* Paste this Custom JavaScript code:

```javascript
function() {
  var brandName = localStorage.getItem("brandName");
  return brandName;
}
```

Your screen should look like this.
![Google Tag Manager Setup](./images/debrandname.png)

Click **Save** to save your new Variable.

![Google Tag Manager Setup](./images/gasave.png)

The next Variables will be created in the same process, but with a little different code.

The next Variable we need is called `productProductView`. When a customer view a product, this Variable will store the product view information.

In the **User-Defined Variables** - section, click **New**.

* Rename `Untitled Variable` to `productProductView`
* Choose **Custom Javascript** as Variable Type
* Paste this Custom JavaScript code:

```javascript
function() {
  var productview = JSON.parse(localStorage.getItem("thisProductView"));
  return productview;
}
```

Your screen should look like this.

![Google Tag Manager Setup](./images/deppv.png)

Click **Save** to save your new Variable.

![Google Tag Manager Setup](./images/gasave.png)

The next Variable is called `return1`. We'll use this Variable to return a Number-value of 1 when needed.

In the **User-Defined Variables** - section, click **New**.

* Rename `Untitled Variable` to `return1`
* Choose **Custom Javascript** as Variable Type
* Paste this Custom JavaScript code:

```javascript
function() {
  return 1;
}
```

Your screen should look like this.

![Google Tag Manager Setup](./images/dere1cc.png)

Click **Save** to save your new Variable.

![Google Tag Manager Setup](./images/gasave.png)

Had we worked with Adobe applications, we would have to capture the ECID. Since we will showcase, that we can also do this with a **Google-only** approach to platform we'll store a unique Google identifier, from Google Analytics. We'll assign the value of the client-side id to this Variable.

The next Variable is called `gaClientId`. We'll use this Variable to as a key for all Google Analytics data.

In the **User-Defined Variables** - section, click **New**.

* Choose **1st-Party Cookie** as Variable Type

![Google Tag Manager Setup](./images/gaClientId.png)

* Choose `_ga` as Cookie Name

![Google Tag Manager Setup](./images/gaClientId2.png)

Click **Save** to save your new Variable.

![Google Tag Manager Setup](./images/gasave.png)

Next: `pageTimeStamp`. We need a unique timestamp on every call to Platform.

In the **User-Defined Variables** - section, click **New**.

* Rename `Untitled Variable` to `pageTimeStamp`
* Choose **Custom Javascript** as Variable Type
* Paste this Custom JavaScript code:

```javascript
function() {
var date = new Date();

var month = date.getUTCMonth();
var day = date.getUTCDate();
var hour = date.getUTCHours();
var min = date.getUTCMinutes();
var sec = date.getUTCSeconds();

month = (month < 9 ? "0" : "") + (month+1);
day = (day < 10 ? "0" : "") + day;
hour = (hour < 10 ? "0" : "") + hour;
min = (min < 10 ? "0" : "") + min;
sec = (sec < 10 ? "0" : "") + sec;

var str = date.getFullYear() + "-" + month + "-" + day + "T" +  hour + ":" + min + ":" + sec + ".000Z";

return str;
}
```

![Google Tag Manager Setup](./images/timestamp.png)

Click **Save** to save your new Variable.

![Google Tag Manager Setup](./images/gasave.png)

Next: `pageHitId`. We need a unique HitId on every call to Platform.

In the **User-Defined Variables** - section, click **New**.

* Rename `Untitled Variable` to `pageHitId`
* Choose **Custom Javascript** as Variable Type
* Paste this Custom JavaScript code:

```javascript
function() {
  var min = 111111111;
  var max = 9999999999999;
  var randomNumber = Math.random() * (max - min) + min;
  return String(randomNumber);
}
```

![Google Tag Manager Setup](./images/hitid.png)

Save your code fragment and then click **Save** again to save your Variable configuration.

![Google Tag Manager Setup](./images/gasave.png)

Next we'll be capturing some Variables that are available to Google Tag Manager without custom code, by referencing JavaScript objects.

To do that, follow these four steps:

In the **User-Defined Variables** - section, click **New**.

* Rename the `Untitled Variable`
* Choose **JavaScript Variable** as Variable type
* Enter the JavaScript Variable name
* Click **Save** to save your new Variable.

First: `customerLanguage`. We'll capture the customer's preferred language by taking it from the browser's settings.

In the **User-Defined Variables** - section, click **New**.

* Rename the `Untitled Variable` to `customerLanguage`.
* Choose  **JavaScript Variable** as Variable type.

![Google Tag Manager Setup](./images/clanguage.png)

* Enter the JavaScript Variable name: `navigator.language`.
Your screen should now look like this:

![Google Tag Manager Setup](./images/clanguage2.png)

* Click **Save** to save your new Variable.

![Google Tag Manager Setup](./images/gasave.png)

Next: `pageType`. On every new page load, we need to capture the type of the page.

In the **User-Defined Variables** - section, click **New**.

* Rename the `Untitled Variable` to `pageType`.
* Choose  **JavaScript Variable** as Variable type.
* Enter the JavaScript Variable name: `digitalData.category.siteSection`.

Your screen should now look like this:
![Google Tag Manager Setup](./images/ptype.png)

* Click **Save** to save your new Variable.

![Google Tag Manager Setup](./images/gasave.png)

Next: `productCategory`. For every product view, we need to capture the product's category and send it to Platform.

In the **User-Defined Variables** - section, click **New**.

* Rename the `Untitled Variable` to `productCategory`.
* Choose  **JavaScript Variable** as Variable type.
* Enter the JavaScript Variable name: `digitalData.product.category`.

Your screen should now look like this:
![Google Tag Manager Setup](./images/pcat.png)

* Click **Save** to save your new Variable.

![Google Tag Manager Setup](./images/gasave.png)

Next: `productName`. For every product view, we need to capture the product's name and send it to Platform.

In the **User-Defined Variables** - section, click **New**.

* Rename the `Untitled Variable` to `productName`.
* Choose  **JavaScript Variable** as Variable type.
* Enter the JavaScript Variable name: `digitalData.product.name`.

Your screen should now look like this:
![Google Tag Manager Setup](./images/pname.png)

* Click **Save** to save your new Variable.

![Google Tag Manager Setup](./images/gasave.png)

Next: `productPrice`. For every product view, we need to capture the product's price and send it to Platform.

In the **User-Defined Variables** - section, click **New**.

* Rename the `Untitled Variable` to `productPrice`.
* Choose  **Custom Javascript** as Variable type.
* Enter the custom javascript by pasting the code below:

``` javascript
function() {
  var price = Number(digitalData.product.price);
  return price;
}
```

Your screen should now look like this:
![Google Tag Manager Setup](./images/pprice.png)

* Click **Save** to save your new Variable.

![Google Tag Manager Setup](./images/gasave.png)

Next: `productImageUrl`. For every product view, we need to capture the product's image URL and send it to Platform.

In the **User-Defined Variables** - section, click **New**.

* Rename the `Untitled Variable` to `productImageUrl`.
* Choose  **JavaScript Variable** as Variable type.
* Enter the JavaScript Variable name: `digitalData.product.imageUrl`.

Your screen should now look like this:
![Google Tag Manager Setup](./images/pimg.png)

* Click **Save** to save your new Variable.

![Google Tag Manager Setup](./images/gasave.png)

Next: `productInteraction`. For every product view, we need to capture the type of interaction (View, Add To Cart, Purchase, etc) and send it to Platform.

In the **User-Defined Variables** - section, click **New**.

* Rename the `Untitled Variable` to `productInteraction`.
* Choose  **JavaScript Variable** as Variable type.
* Enter the JavaScript Variable name: `digitalData.product.interaction`.

Your screen should now look like this:
![Google Tag Manager Setup](./images/de_interaction.png)

* Click **Save** to save your new Variable.

![Google Tag Manager Setup](./images/gasave.png)

Next: `pageUserAgent`. For every page view, we need to capture the user device type and Operating System and send it to Platform. We use the User Agent to derive this information. More info on User Agent can be found here: [https://en.wikipedia.org/wiki/User_agent](https://en.wikipedia.org/wiki/User_agent)

In the **User-Defined Variables** - section, click **New**.

* Rename the `Untitled Variable` to `pageUserAgent`.
* Choose  **JavaScript Variable** as Variable type.
* Enter the JavaScript Variable name: `navigator.userAgent`.

Your screen should now look like this:
![Google Tag Manager Setup](./images/ua.png)

* Click **Save** to save your new Variable.

![Google Tag Manager Setup](./images/gasave.png)

Almost done, now time for : `pageName`. On every new page load, we need to capture the page name and send it to AA, AAM and Platform.

In the **User-Defined Variables** - section, click **New**.

* Rename the `Untitled Variable` to `pageName`.
* Choose  **JavaScript Variable** as Variable type.
* Enter the JavaScript Variable name: `document.title`.

Your screen should now look like this:
![Google Tag Manager Setup](./images/pagename.png)

* Click **Save** to save your new Variable.

![Google Tag Manager Setup](./images/gasave.png)

And the final one: `pageUrl`. On every new page load, we need to capture the URL to send it to other solutions.
Page URL is already a built-in variable in Google Tag Manager, so we do not really need to define this. But for consistency with other information on Platform we'll define pageUrl anyway.

In the **User-Defined Variables** - section, click **New**.

* Rename the `Untitled Variable` to `pageUrl`.
* Choose  **URL** as Variable type.

![Google Tag Manager Setup](./images/pageurltype.png)

Your screen should now look like this:
![Google Tag Manager Setup](./images/pageurl.png)

* Click **Save** to save your new Variable.

![Google Tag Manager Setup](./images/gasave.png)

You've finished configuring all required Google Tag Manager Variables!

Next Step: [9.4 Retrieve Platform Datasets](./ex4.md)

[Go Back to Module 9](./data-ingestion-using-google-tag-manager-and-google-analytics.md)

[Go Back to All Modules](../../overview.md)
